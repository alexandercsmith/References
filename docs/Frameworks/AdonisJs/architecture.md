# Adonis.js | Architecture

> Node.js MVC Framework

* Routing
* Middleware
* Request
* Response
* Views
* Sessions
* Validator
* Error Handling
* Logging

---

## Routing

* Routes are registered in `start/routes.js`

### Basic Routing & Methods

Simple Route
```js
Route.get('/', () => 'Hello Adonis')
```

Controller Route
```js
Route.get('posts', 'PostsController.index')
```

| HTTP   | Method                       |
|:-------|:-----------------------------|
| GET    | `Route.get(url, closure)`    |
| POST   | `Route.post(url, closure)`   |
| PUT    | `Route.put(url, closure)`    |
| PATCH  | `Route.patch(url, closure)`  |
| DELETE | `Route.delete(url, closure)` |

Multiple Routes to Single Endpoint using `.route()`
```js
Route.route('/', () => { .. }, ['GET', 'POST', 'PUT'])
```

Directly Render Static View
```js
// ~/resources/view/welcome.edge
Route.on('/').render('welcome')
```

### Routing Parameters

Dynamic Routes - Required Parameters
```js
Route.get('posts/:id', ({ params }) => {
  return `Post ${params.id}`
})
```

Optional Parameters
```js
Route.get('make/drink?', ({ params }) => {
  const drink = params.drink || 'coffee'
  return `One ${drink}, coming right up!`
})
```

### Wildcard Routes

Render Single View for Frontend Framework
```js
// Define specific routes before Wildcard

// Use `.any` for Wildcard routes
Route.any('*', ({ view }) => view.render('...'))
```

### Named Routes

Use `as()` to assign route a unique name
```js
Route.get('users', closure).as('users.index')

Route.get('posts/:id', closure).as('posts.show')
```

Using `as()` enables Route Helpers
```html
<a href="{{ route('users.index') }}">Users</a>

<a href="{{ route('posts.show', { id: 1 }) }}">Post One</a>
```

```js
sampleFunc({ response }) {
  return response.route('users.index')
}
```

### Route Formats

Return View or Data based on Request
```js
Route.get('users', async ({ request, view }) => {
  const users = await User.all()

  if (request.format() === 'json') { return users }

  return view.render('users.index', { users })
}).formats(['json'])
```

Disable Default URL Formatting
```js
Route.get('users', closure).formats(['json','html'], true)
```

### CRUD Resources

Define CRUD Operations in one method `.resource()`
```js
Route.resource('users', 'UserController')
```

List of Defined Routes with `.resource()`
```js
Route.get('users', 'UserController.index').as('users.index')
Route.get('users/create', 'UserController.create').as('users.create')
Route.get('users/:id', 'UserController.show').as('users.show')
Route.get('users/:id/edit', 'UserController.edit').as('users.edit')
Route.post('users', 'UserController.store').as('users.store')
Route.put('users/:id', 'UserController.update').as('users.update')
Route.patch('users/:id', 'UserController.update')
Route.delete('users/:id', 'UserController.destroy').as('users.destroy')
```

Define CRUD Operations for Nested Resources
```js
Route.resource('posts.comments', 'PostCommentsController')
```

### Filter Resources

Limit the routes assigned by `Route.resource` by method chaining.

* `.apiOnly`
  * Removes `GET resource/create` and `GET resource/:id/edit` routes
```js
Route.resource('users', 'UserController').apiOnly()
```

* `.only()`
  * Keeps only passed routes
```js
Route.resource('users', 'UserController').only(['index','show'])
```

* `.except()`
  * Keep all routes except the passed routes
```js
Route.resource('users', 'UserController').middleware(['auth'])
```

* `.middleware()`
  * Specify which Resource routes to pass Middleware
```js
Route.resource('users', 'UserController')
  .middleware(new Map([
    [['store','update','destroy'], ['auth']]
  ]))
```

* `.formats()`
  * Define response formats
```js
Route.resource('users', 'UserController').formats(['json'])
```

### Route Domains
  * Domains can be Static `blog.site.com` or Dynamic `:user.site.com`
```js
Route.group(() => {
  Route.get('/', ({ subdomains }) => {
    return `The username is ${subdomains.user}`
  })
}).domain(':user.site.com')
```

### Route Groups

```js
// Ungrouped
Route.get('api/v1/users', closure)
Route.get('api/v1/users', closure)

// Grouped
Route.group(() => {
  Route.get('users', closure)
  Route.post('users', closure)
}).prefix('api/v1')

// Grouped Middleware
// Grouped Middleware executes before Route Middleware
Route.group(() => {
  ...
}).middleware(['auth'])
```

### Namespace

Prefix the Namespace
```js
Route.group(() => {
  // Binds '/users' to 'App/Controllers/Http/Admin/UserController'
  Route.resource('/users', 'UserController')
}).namespace('Admin')
```

Define Group Formats
```js
Route.group(() => {
  ...
}).formats(['json','html'], true)
```

Define Group Domain
```js
Route.group(() => {
  ...
}).domain('blog.site.com')
```

---

## Middlware

* Middleware hook into the request/response lifecycle of the application.
* Middleware executes a sequence of functions to transform the request/response.
* Middleware has 3 Categories:
  * **Server**: Executes before request reaches Routing system.
  * **Global**: Executes after requested route has been found.
  * **Named**: Assigned to specific route or route group.

### Create Middleware

Command-line Generator
```bash
$ adonis make:middleware CountryDetector
```

~/app/Middleware/CountryDetector.js
```js
`use strict`

const geoip = require('geoip-lite')

class CountryDetector {
  async handle({ request }, next) {
    const ip = request.ip()
    request.country = geoip.lookup(ip).country
    // Placement `next()` - Upstream(after) & Downstream(before) the executing code
    await next()
  }
}

module.exports = CountryDetector
```

### Registering Middleware
  * All middleware is registered inside `start/kernel.js`

Server Middleware
```js
const serverMiddleware = [
  'Adonis/Middleware/Static',
  'Adonis/Middleware/Cors'
]
```

Global Middleware
  * Global middleware executes in the order they are defined.
```js
const globalMiddleware = [
  'Adonis/Middleware/BodyParser'
]
```

Named Middleware
```js
// start/kernel.js
const namedMiddleware = {
  auth: 'Adonis/Middleware/Auth'
}

// start/routes.js
Route.get(url, closure).middleware(['auth'])
```

### Middleware Properties

Define specific properties for Middleware on Routes with `:`
```js
// Use `session` scheme of `auth`
Route.post(url, closure).middleware('auth:session')

// Use `JWT` scheme of `auth`
Route.post(url, closure).middleware('auth:jwt')
```

Pass multiple properties for Middleware
  * Chain with `,`
```js
Route.post(url, closure).middleware(['auth:session,jwt'])
```

Passed properties are available as a third argument in the middleware `handle`
```js
async handle(context, next, properties) {
  // function
}
```

---

## Controllers

Controllers attach to one or many routes, grouping related request handling logic into single files for common interaction points of models, views and other services.

### Create Controllers
```bash
# HTTP Controller
$ adonis make:controller User --type http

# WS Controller
$ adonis make:controller User --type ws

# Use `Admin` subfolder
$ adonis make:controller Admin/User
```

Created Boilerplate
```js
'use strict'

class UserController { .. }

module.exports = UserController
```

### Using Controller
```js
// app/routes.js
Route.get(url, 'UserController.index')
```

Organizing Controller methods to Routes
```js
// app/Controllers/Http/UserController -> index()
Route.get(url, 'UserController.index')

// app/Controllers/Http/Admin/UserController -> store()
Route.post(url, 'Admin/UserController.store')

// app/CustomControllers/UserController -> index()
Route.post(url, 'App/CustomControllers/UserController.index')
```

### Defining Controller Functions
```js
'use strict'

class UserController {
  index({ request, response }) {
    //
  }
}

module.exports = UserController
```

---

## Request

* AdonisJs passes current HTTP request object as part of Context to Route handler.
* Node.js raw `req` object can be accessed via `request.request`

```js
Route.get('/', ({ request }) => {
  // function
})
```

### Request Body Parse

Install `BodyParser`
```bash
$ adonis install @adonisjs/bodyparser
```

Register Provider in `start/app.js`
```js
const providers = [
  '@adonisjs/bodyparser/providers/BodyParserProvider'
]
```

Register Global Middleware in `start/kernel.js`
```js
const globalMiddleware = [
  'Adonis/Middleware/BodyParser'
]
```

### Request Body Methods

* **all**: Returns an Object of all request data.
  * `const all = request.all()`
* **get**: Returns an Object containing query params.
  * `const query = request.get()`
* **post**: Returns an Object containing request body data.
  * `const body = request.post()`
* **raw**: Returns raw body data as string.
  * `const raw = request.raw()`
* **only**: Returns an Object with only specified keys.
  * `const data = request.only(['username','email','name'])`
* **except**: Returns an Object with everything except specified keys.
  * `const data = request.except(['csrf_token','submit'])`
* **input**: Get value of given Key
  * `const drink = request.input('drink')`
  * `const drink = request.input('drink', 'coffee')` - Default value

### Request Collection
  * When sending Multiple Form Items, use `request.collect()` to format groups.

```js
const users = request.collect(['username','age'])

// => [{ username: 'name', age: 20 }, { username: 'name', age: 30 }]

// Save to DB
await User.createMany(users)
```

### Headers

Retrieve Header by Key
```js
var auth = request.header('authorization')

// Default Value
const other = request.header('other-token', 'token')
```

Retrieve Object of All Header Data
```js
const headers = request.headers()
```

### Cookies

Retrieve Cookie by Key
```js
const cartTotal = request.cookie('cart_total')

// Client-side
const jsCookie = request.plainCookie('cart_total')
```

Retrieve Object of All Cookie Data
```js
const cookies = request.cookies()

// Client-side
const plainCookies = request.plainCookies()
```

### Content Negotiation
  * Avoid creating separate URL's for Content-Type
  * Construct specific format in response with `accepts` and `language`

Accepts
```js
const bestFormat = request.accepts(['json','html'])

if (bestFormat === 'json') { return response.json(users) }

return view.render('users.list', { users })
```

Language
```js
const language = request.language(['en','fr'])
```

### Request Methods

* **url**: Returns current request URL.
  * `const url = request.url()`
* **originalUrl**: Returns full current request URL with query strings.
  * `const url = request.originalUrl()`
* **method**: Returns HTTP request method.
  * `const method = request.method()`
* **intended**: Fetch actual method.
  * `const method = request.intended()`
* **ip**: Returns IP address for User
  * `const ip = request.ip()`
* **ips**: Returns array of `ips`
  * `const ips = request.ips()`
* **subdomains**: Returns list of request subdomains
  * `const subdomains = request.subdomains()`
* **ajax**: Checks `X-Requested-With` Header to determine if ajax
  * `if (request.ajax()) { .. }`
* **pjax**: aka Turbolinks, Checks `X-PJAX` Header to determine if pjax
  * `if (request.pjax()) { .. }`
* **hostname**: Return request Hostname
  * `const hostname = request.hostname()`
* **protocol**: Return Request Protocol
  * `const protocol = request.protocol()`
* **match**: Returns whether passed expressions match current request URL.
  * `request.match(['posts/:id'])` -> `true`
* **hasBody**: Boolean indicating if request has Post Body
  * `if (request.hasBody()) { .. }`
* **is**: Returns best matching `Content-Type` for current request. Checks `Content-Type` Header.
  * `request.is(['json','html'])` -> `json`
  * `request.id(['application/*'])` -> `application/json`

### Extend Request

Extend `Request` prototype and add custom methods

```js
const Request = use('Adonis/Src/Request')

Request.macro('cartValue', function() {
  return this.cookie('cartValue', 0)
})
```

---

## Response

* AdonisJs passes current HTTP request object as part of Context to Route handler.

```js
Route.get('/', ({ response }) => {
  // Use `send` or `json` to return Data in `response`
  response.send('hello world')
})

Route.get('/users', async ({ response }) => {
  response.json(await User.all())
})
```

### Making a Response

Use `return` without `response` as well from Route or Controller
```js
Route.get('/', async () => {
  return await User.all()
})
```

Avoid Callbacks
  * AdonisJs discourages the usage of callbacks.
  * Use `promisify` for your callback and assign `await`
  * Continue using callbacks by setting the function not to end **implicitly**
```js
// Wont work in AdonisJs
Route.get('/', async ({ response }) => {
  rs.readFile('someFile', (error, data) => {
    response.send(data)
  })
})
```
```js
// Use `promisify` and `await`
const fs = use('fs')
const Helpers = use('Helpers')
const readFile = Helpers.promisify(fs.readFile)

Route.get('/', async ({ response }) => {
  return await readFile('someFile')
})
```
```js
// Do not end implicitly
Route.get('/', async ({ response }) => {
  response.implicitEnd = false

  fs.readFile('someFile', (error, data) => {
    response.send(data)
  })
})
```

### Headers

Set and Remove Headers

* **header**: Set a Header value
  * `reponse.header('Content-Type', 'application/json')`
* **safeHeader**: Only set a header value if it does not already exist
  * `response.safeHeader('Content-Type', 'application/json')`
* **removeHeader**: Remove an existing Header value
  * `response.removeHeader('Content-Type')`
* **type**: Set the `Content-Type` Header
  * `response.type('application/json')`

### Cookies

Set and Remove Cookies

* **cookie**: Set a Cookie value
  * `response.cookie('cartTotal', 20)`
* **clearCookie**: Remove an existing Cookie value (Set Expiration in Past)
  * `response.clearCookie('cartTotal')`
* **plainCookie**: Frontend Client-side Cookie not Encrypted or Signed
  * `response.plainCookie('cartTotal', 20)`

### Redirects

Redirect Requests to different URLs

**redirect(url, [sendParams = false], [status = 302])**
```js
response.redirect('/url')
// or
response.redirect('/url', false, 301)
// Send Current Request Parameters to Redirect
response.redirect('/url', true)
```

**route(route, [data], [domain], [sendParams = false], [status = 302])**
```js
Route.get('users/:id', 'UserController.show').as('profile')

// Route name
response.route('profile', { id: 1 })

// Controller method
response.route('UserController.show', { id: 1})

// URL Specific
response.route('posts', { id: 1}, 'blog.site.com')
```

### Attachments

Stream Files from Server to Client

**download(filePath)**
```js
// Does not force Download - May display in new window
response.download(Helpers.tmpPath('uploads/avatar.jpg'))
```

**attachment(filePath, [name], [disposition])**
```js
// Force Download
response.attachment(Helpers.tmpPath('uploads/avatar.jpg'))

// Download with Custom Name
response.attachment(Helpers.tmpPath('uploads/avatar.jpg'), 'myAvatar.jpg')
```

### Descriptive Methods

Use Alias Methods for HTTP Responses

```js
response.unauthorized('Login First')
// same as
response.status(401).send('Login First')
```

**100**

| HTTP  | Method               |
|:-----:|:---------------------|
| `100` | `continue`           |
| `101` | `switchingProtocols` |

**200**

| HTTP  | Method                        |
|:-----:|:------------------------------|
| `200` | `ok`                          |
| `201` | `created`                     |
| `202` | `accepted`                    |
| `203` | `nonAuthoritativeInformation` |
| `204` | `noContent`                   |
| `205` | `resetContent`                |
| `206` | `partialContent`              |

**300**

| HTTP  | Method              |
|:-----:|:--------------------|
| `300` | `multipleChoices`   |
| `301` | `movedPermanently`  |
| `302` | `found`             |
| `303` | `seeOther`          |
| `304` | `notModified`       |
| `305` | `useProxy`          |
| `307` | `temporaryRedirect` |

**400**

| HTTP  | Method                         |
|:-----:|:-------------------------------|
| `400` | `badRequest`                   |
| `401` | `unauthorized`                 |
| `402` | `paymentRequired`              |
| `403` | `forbidden`                    |
| `404` | `notFound`                     |
| `405` | `methodNotAllowed`             |
| `406` | `notAcceptable`                |
| `407` | `proxyAuthenticationRequired`  |
| `408` | `requestTimeout`               |
| `409` | `conflict`                     |
| `410` | `gone`                         |
| `411` | `lengthRequired`               |
| `412` | `preconditionFailed`           |
| `413` | `requestEntityTooLarge`        |
| `414` | `requestUriTooLong`            |
| `415` | `unsupportedMediaType`         |
| `416` | `requestedRangeNotSatisfiable` |
| `417` | `expectationFailed`            |
| `422` | `unprocessableEntity`          |
| `429` | `tooManyRequests`              |

**500**

| HTTP  | Method                    |
|:-----:|:--------------------------|
| `500` | `internalServerError`     |
| `501` | `notImplemented`          |
| `502` | `badGateway`              |
| `503` | `serviceUnavailable`      |
| `504` | `gatewayTimeout`          |
| `505` | `httpVersionNotSupported` |

### Extending Response

Use `Providers` or `Ignitor Hooks` to extend since it only needs to execute once.

```js
const Response = use('Adonis/Src/Response')

Response.macro('sendStatus', function(status) {
  this.status(status).send(status)
})
```

---

## Views

* AdonisJs uses [Edge](https://edge.adonisjs.com/) as its Templating engine.
* Features of Edge:
  * Layouts & Partials
  * Components
  * Runtime debugging using Chrome Dev Tools
  * Logical Tags, and many others.
* `ViewProvider` must be registered as a provider in `start/app.js`.
* All Views have access to the current `request` Object.


### Register `ViewProvider`
```js
const providers = [
  '@adonisjs/framework/providers/ViewProvider'
]
```

### Generate Views
```bash
$ adonis make:view hello-world
#> create resources/views/hello-world.edge
```

### Render View in Route
  * The `view.render()` method takes the relative path `resources/views`
  * No need to type `.edge` extension
```js
Route.get('hello-world', ({ view }) => {
  return view.render('hello-world')
})
```

### Nested Views
  * Use `.` Dot notation to access subfolders in Views
```js
// ~/resources/views/my/nested/view.edge
view.render('my.nested.view')
```

### Request Object in Views
```js
`The request URL is ${request.url()}`
// or
`The request URL is ${url}`
```

### Globals

* **style**: Adds `link` tag to a CSS file.
  * `{{ style('style') }}` -> '/style.css'
* **script**: Adds `script` tag to a JavaScript file.
  * `{{ script('app') }}` -> '/app.js'
* **assetsUrl**: Returns file path to `public` Directory.
  * `<img src="{{ assetsUrl('images/logo.png') }}" />`
* **route**: Returns URL for Route.
  * `<a href="{{ route('profile', { id: 1}) }}">Link</a>`
  * `<a href="{{ route('UserController.show', { id: 1 }) }}">Link</a>`
* **url**: Returns current URL request.
  * `The request URL is {{ url }}`
* **auth**: AuthProvider - Current User
  * `{{ auth.user }}`
* **CSRF**: ShieldMiddleware - CSRF Token and input field.
  * `{{ csrfToken }}`
  * `{{ csrfField }}`
  * `{{ cspMeta() }}`

### Tags

Logical building blocks and functions of **Edge** templates.

**loggedIn**
* `loggedIn` allows you to write `if/else` conditional
```js
@loggedIn
  Logged In!
@else
  <a href="/login">Login</a>
@endloggedIn
```

**inlineSvg**
* Renders SVG file relative to `public` Directory
```js
@inlineSvg('lock')
```

### Extending Views

**Globals**
```js
const View = use('View')

View.gloabl('currentTime', function() {
  return new Date().getTime()
})

// Usage
{{ currentTime() }}
```

**Scope**
```js
// `this` in a Global is bound to the View context
// `safe` returns HTML that is not escaped
View.global('button', function(text) {
  return this.safe(`<button type="submit">${text}</button>`)
})
```

---

## Sessions

* AdonisJs has first-class session support with inbuilt drivers to manage store sessions.

### Setup

Install Session Provider
```bash
# Download Session Provider
$ adonis install @adonisjs/session
#> created ~/config/sessions.js
```

Register Session Provider in `start/app.js`
```js
const providers = [
  '@adonisjs/session/providers/SessionProvider'
]
```

Register Session Middleware in `start/kernel.js`
```js
const globalMiddleware = [
  'Adonis/Middleware/Session'
]
```

### Usage
  * The `session` Object is passed with HTTP context.
```js
Route.get('/', ({ session, response }) => {
  session.put('username', 'John')
  response.redirect('/username')
})

Route.get('/username', ({ session }) => {
  return session.get('username') // John
})
```

### Session Methods

* **put(key, value)**
  * Add a key/value pair to session store.
  * `session.put('username', 'john')`
* **get(key, [default])**
  * Return value for given key (accepts optional default value)
  * `session.get('username')`
  * `session.get('username', 'defaultName')`
* **all**
  * Everything from Session store Object.
  * `session.all()`
* **increment(key, [steps])**
  * Increment value for given key (validate Number type)
  * `session.increment('counter')`
  * `session.increment('counter', 5)`
* **decrement(key, [steps])**
  * Decrement value for given key (validate Number type)
  * `session.decrement('counter')`
  * `session.decrement('counter', 5)`
* **forget(key)**
  * Remove key/value pair from Session store.
  * `session.forget('username')`
* **pull(key, [default])**
  * Return and remove key/value pair from Session store.
  * `const username = session.pull('username')`
* **clear**
  * Empty Session store.
  * `session.clear()`

---

## Validator

### Setup
```bash
$ adonis install @adonisjs/validator
```

### Register Validator Provider
```js
const providers = [
  '@adonisjs/validator/providers/ValidatorProvider'
]
```

### Validate User Data
```js
const { validate } = use('Validator')

class UserController {
  async store({ request, session, response }) {
    const rules = {
      email: 'required|email|unique:users,email',
      password: 'required'
    }
    const validation = await validate(request.all(), rules)
    if (validation.fails()) {
      session.withErrors(validation.messages()).flashExcept(['password'])
      return response.redirect('back')
    }
    return 'Validation passed.'
  }
}

module.exports = UserController
```

---

## Error Handling

---

## Logging
