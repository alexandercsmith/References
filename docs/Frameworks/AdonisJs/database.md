# Adonis.js | Database

> Node.js MVC Framework

* Configuration
* Query Builder
* Migrations
* Seeds & Factories
* Redis

AdonisJs uses [Knex.js](https://knexjs.org/) as a Data Provider.

---

## Configuration

### Supported Databases

| Database   | NPM Driver                      |
|:-----------|:--------------------------------|
| MariaDB    | `npm i mysql` or `npm i mysql2` |
| MSSQL      | `npm i mssql`                   |
| MySQL      | `npm i mysql` or `npm i mysql2` |
| Oracle     | `npm i oracledb`                |
| PostgreSQL | `npm i pg`                      |
| SQLite3    | `npm i sqlite3`                 |

### Setup

Installation
```bash
$ adonis install @adonisjs/lucid
```

Register Lucid Provider in `start/app.js`
```js
const providers = [
  '@adonisjs/lucid/providers/LucidProvider'
]
const aceProviders = {
  '@adonisjs/lucid/providers/MigrationsProvider'
}
```

Configure Database in `config/database.js`
```js
module.exports = {
  connection: 'mysql'
}
```

### Usage
```js
const Database = use('Database')
Route.get('/', async () => {
  return await Database.table('users').select('*')
})
```

---

## Query Builder

---

## Migrations

---

## Seeds & Factories

---

## Redis
