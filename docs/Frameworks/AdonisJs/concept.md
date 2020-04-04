# Adonis.js | Concept

> Node.js MVC Framework

* Request Lifecycle
* IoC Container
* Service Providers
* Ignitor

---

## Request Lifecycle

### Request Flow
  * HTTP requests sent from a client are handled by the AdonisJs `Server` module, executing all **server level middleware**.
  * Request Termination executes the AdonisJs `Router`. If `Router` cannot find a matching URL, `RouteNotFound` exeception thrown.
  * Matching Route, **global middleware** are executed followed by and **middleware** defined for the Route.
  * Request must be terminated in Route handler. After, AdonisJs executes all **downstream middleware** and send the response.

### HTTP Context
  * AdonisJs provides a **HTTP Context** object to each Route handler.
  * **HTTP Content** {}
    * `request`
    * `response`
    * `view`

---

## IoC Container

> Inversion of Control

IoC container is a relatively simple idea that controls the composition and resolution of modules.

### `ioc.bind()`
Bind `Redis` class to the IoC container as `My/Redis`
```js
const { ioc } = require('@adonisjs/fold')
const Redis = require('./Redis')

ioc.bind('My/Redis', function(app) {
  const Config = app.use('Adonis/Src/Config')
  return new Redis(Config)
})
```
Usage
```js
// Provide namespace to resolve
const redis = ioc.use('My/Redis')

// Also - Use global `use`
const redis = use('My/Redis')
```
Parameters
  * `name` - Name of the Binding
  * `function` - Executing function to return final value of Binding

### `ioc.singleton()`
Cache the IoC container value on initialization and reuse
```js
ioc.singleton('My/Redis', function(app) {
  const Config = app.use('Adonis/Src/Config')
  return new Redis(Config)
})
```

---

## Service Providers

> Pure ES6 classes with lifecycle methods used to register and bootstrap bindings

### Usage
```js
// Load `ServiceProvider`
const { ServiceProvider } = require('@adonisjs/fold')

// Extend Target class with `ServiceProvider`
class MyProvider extends ServiceProvider {
  register() {
    // register bindings
  }
  boot() {
    // optional initial config/setup
  }
}

// Export Module
module.exports = MyProvider
```

### Methods
  * `register` - Register bindings. Never use any other bindings inside this method.
  * `boot` - After Registration, exiting bindings to application state.

### Global View
```js
boot() {
  const View = this.app.use('Adonis/Src/View')
  View.global('time', () => new Date().getTime())
}
```

### Initialize NPM Package with Config

All application specific providers live inside the `providers` directory in the root of the app.
```
+-+ app
+-+ providers
  +-+ Queue
    - index.js
    - Provider.js
+-+ start
```

### Service Provider + IoC Container
Configuration
* `providers/Queue/Provider.js`
```js
const { Service Provider } = require('@adonisjs/fold')

class QueueProvider extends ServiceProvider {
  register() {
    this.app.singleton('Bee/Queue', () => {
      const Config = this.app.use('Adonis/Src/Config')
      return new (require('.'))(Config)
    })
  }
}

module.exports = QueueProvider
```

Registration
* `start/app.js`
```js
const providers = [
  path.join(__dirname, '..', 'providers', 'Queue/Provider')
]
```

---

## Ignitor

> Ignitor powers bootstrapping of an AdonisJs application

### Hooks
  * Hooks are registered inside the `start/hooks.js`.

Usage
  * `hooks.before._` - Before Hook Event
  * `hooks.after._` - After Hook Event
```js
const { hooks } = require('@adonisjs/ignitor')

hooks.after.providersBooted(() => {
  const View = use('View')
  View.global('time', () => new Date().getTime())
})
```

| Hook Event            | Description                              |
|:----------------------|:-----------------------------------------|
| `providersRegistered` | before/after all providers registered    |
| `providersBooted`     | before/after all providers booted        |
| `preloading`          | before/after preloading registered files |
| `httpServer`          | before/after HTTP server has started     |
| `aceCommand`          | before/after ace command is executed     |

### Preloading Files
  * Preload Files after the HTTP server has started.
  * Modify `server.js` and add `preLoad` method.
  * `preLoad` method accepts a relative application root path or absolute path.

```js
// `preLoad` Single
new Ignitor(require('@adonisjs/fold'))
    .appRoot(__dirname)
    .preLoad('start/example-function')
    .fireHttpServer()
    .catch(console.error)

// `preLoad` Multiple
new Ignitor(require('@adonisjs/fold'))
    .preload('')
    .preload('')
    // etc
```

### Ignitor Methods

Usage: `ignitor._method()`

| Ignitor Method                             | Description                                             |
|:-------------------------------------------|:--------------------------------------------------------|
| `.appRoot(__dirname)`                      | Define absolute path to application root                |
| `.modulesRoot(path.join(__dirname, '..'))` | Define absolute path to `node_modules` parent directory |
| `.appFile('start/app.js')`                 | Define relative path to app file                        |
| `.loadCommands()`                          | Load Ace Provider commands                              |
