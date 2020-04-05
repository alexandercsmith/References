# Adonis.js | Installation, Configuration & Directory

> Node.js MVC Framework

* Installation
* Configuration
* Directory Structure

---

## Installation

### Install AdonisJs CLI
```bash
$ npm install -g @adonisjs/cli
```

### Initialize New Application
```bash
$ adonis new <app-name>
```
### Start Development Server
  * `localhost:3333`
```bash
$ adonis serve --dev
```

* Server starts with port defined in `.env` file.

---

## Configuration

* AdonisJS uses the `config` directory where all files are loaded at boot time.

### Config Provider

Access configuration values using the **Config Provider**
```js
const Config = use('Config')
const appSecret = Config.get('app.appSecret')
```

Provide Default Value
```js
Config.get('database.psql.host', '127.0.0.1')
```

Change **In-memory** configuration values using `Config.set`
```js
Config.set('database.psql.host', 'db.example.com')
```

### ENV Provider

* AdonisJs uses dotenv configuration for `.env` files.

Access ENV Variables
```js
const Env = use('Env')
const appSecret = Env.get('APP_SECRET')
```

Provide Default Value
```js
Env.get('DB_USER', 'root')
```

Throw Error
```js
Env.getOrFail('APP_SECRET')
```

---

## Directory Structure

### Standard AdonisJs Directory Structure

```
|
+-+ app/
  +- ...
+-+ config/
  +- app.js
  +- auth.js
  +- ...
+-+ database/
  ++ migrations/
  ++ seeds/
  +- factory.js
+-+ public/
+-+ resources/
  +- ...
  ++ views/
+-+ storage/
+-+ start/
  +- app.js
  +- kernel.js
  +- routes.js
+-+ test/
+- ace
+- server.js
+- package.json
```

### Root Directories

| Directory   | Description                                            |
|:------------|:-------------------------------------------------------|
| `app`       | Home of Application logic. Autoload `App`              |
| `config`    | Application configuration                              |
| `database`  | Database related files                                 |
| `public`    | Static assets                                          |
| `resources` | Presentational files. Templates. LESS/SASS, Js, Images |
| `start`     | Files to be loaded on start of Application.            |
| `test`      | Application tests                                      |

### App Directories

| Directory         | Description                      | Create                          |
|:------------------|:---------------------------------|:--------------------------------|
| `app/Commands`    | CLI Commands                     | `adonis make:command <name>`    |
| `app/Controllers` | `Http` & `WebSocket` controllers | `adonis make:controller <name>` |
| `app/Exceptions`  | Global exception handler         | `adonis make:exception <name>`  |
| `app/Listeners`   | Event Listeners                  | `adonis make:listener <name>`   |
| `app/Middleware`  | Middleware                       | `adonis make:middleware <name>` |
| `app/Models`      | Models                           | `adonis make:model <name>`      |
| `app/Validators`  | Route Validators                 | `adonis make:validator <name>`  |
