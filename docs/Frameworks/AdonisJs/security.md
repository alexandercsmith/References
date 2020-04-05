# Adonis.js | Security

> Node.js MVC Framework

* Authentication
* CORS
* CSRF Protection
* Encryption & Hashing
* Shield Middleware

**Session Security**
* AdonisJs encrypts and signs all cookies using `appKey` in `config/app.js`

**Session Configuration**
* `httpOnly` : Boolean(true) - Makes cookies accessible to JavaScript `document.cookie`
* `sameSite` : Boolean(true) - Ensuring Session Cookie is not visible/accessible to different domains.

**File Uploads**
```js
// Set Upload Max Size
uploads: {
  maxSize: '2mb'
}
```

---

## Authentication

* AdonisJs auth provider is a fully featured system to authenticate HTTP requests.
* Authentication configuration is in `config/auth.js`
* Authentication Schemes:
  * `session` : Session
  * `basic` : Basic Auth
  * `jwt` : JWT
  * `api` : Personal API Tokens
* Serializers:
  * `lucid` : Lucid
  * `database` : Database
* Categories:
  * **Stateful**: Session-based Auth
  * **Stateless**: Transactional Auth per Request

### Setup
```bash
$ adonis install @adonisjs/auth
```

### Register Auth Provider
```js
// ~/start/app.js
const providers = [
  '@adonisjs/auth/providers/AuthProvider'
]
```

### Register Auth Middleware
```js
// ~/start/kernel.js
const globalMiddleware = [
  'Adonis/Middleware/AuthInit'
]
const namedMiddleware = {
  auth: 'Adonis/Middleware/Auth',
  guest: 'Adonis/Middleware/AllowGuestOnly'
}
```

### Usage

**Add Routes**
```js
// ~/start/routes.js
Route
  .post('login', 'UserController.login')
  .middleware('guest')

Route
  .get('users/:id', 'UserController.show')
  .middleware('auth')
```

**Controller**
```bash
$ adonis make:controller User
```

```js
// ~/app/Controllers/Http/UserController.js
class UserController {
  async login({ auth, request }) {
    const { email, password } = request.all()
    await auth.attempt(email, password)
    return 'Logged in successfully'
  }

  show({ auth, params }) {
    if (auth.user.id !== Number(params.id)) {
      return "You cannot see someone else's profile"
    }
    return auth.user
  }
}
```

### Session

Session Configuration
```js
module.exports = {
  authenticator: 'session',
  session: {
    serializer: 'Lucid',
    scheme: 'session',
    model: 'App/Models/User',
    uid: 'email',
    password: 'password'
  }
}
```

| Key          | Values                           | Description                                          |
|:-------------|:---------------------------------|:-----------------------------------------------------|
| `serializer` | `lucid`, `database`              | Serializer fetches user from DB                      |
| `scheme`     | `session`, `basic`, `jwt`, `api` | Scheme fetches and authenticates User creds          |
| `uid`        | DB Field Name                    | Database field used as unique identifier             |
| `password`   | DB Field Name                    | Database field used to verify password               |
| `model`      | Model Namespace                  | Model used to query DB                               |
| `table`      | DB TableName                     | `database` Serializer                                |

### Session Methods

* **attempt(uid, password)**
  * Login via `uid` and `password` throwing exception if not found or invalid.
  * `await auth.attempt(uid, password)`
* **login(user)**
  * Login via `user` model.
  * `await auth.login(user)`
* **loginViaId(id)**
  * Login via `id`, querying to ensure existence
  * `await auth.loginViaId(1)`
* **remember**
  * When calling `attempt`, `login`, `loginViaId`, and chain `remember`
  * `await auth.remember(true).attempt(email, password)`
* **check**
  * Check if User logged in.
  * `try { await auth.check() } catch(error) { response.send('Not logged in') }`
* **getUser**
  * Returns the logged in User Instance via `check`
  * `try { return await auth.getUser() } catch(error) { response.send('Not logged in') }`
* **logout**
  * Logout User
  * `await auth.logout()`

### JWT [JSON Web Tokens]
  * Header: `Authorization: Bearer <token>`

**JWT Configuration**
```js
module.exports = {
  authenticator: 'jwt',
  jwt: {
    serializer: 'Lucid',
    model: 'App/Models/User',
    scheme: 'jwt',
    uid: 'email',
    password: 'password',
    options: {
      secret: Config.get('app.appKey')
    }
  }
}

// Provide Secret and Public Keys to Encrypt and Verify
const fs = use('fs');
module.exports = {
  authenticator: 'jwt',
  jwt: {
    ...
    options: {
      algorithm: 'RS256',
      secret: fs.readFileSync('path-to-file.pem'),
      public: fs.readFileSync('path-to-file.pem')
    }
  }
}
```

| Key         | Values                  | Default | Description                 |
|:------------|:------------------------|:--------|:----------------------------|
| `algorithm` | `HS256`,`HS384`,`RS256` | `HS256` | Generate Tokens             |
| `expiresIn` | Time: Seconds + Milli   | `null`  | Expire Tokens               |
| `notBefore` | Time: Seconds + Milli   | `null`  | Minimum time to keep Tokens |
| `audience`  | String                  | `null`  | `aud` Claim                 |
| `issuer`    | Array or String         | `null`  | `iss` Claim                 |
| `subject`   | String                  | `null`  | `sub` Claim                 |
| `public`    | String                  | `null`  | `public` Key to Verify      |

### JWT Methods

**attempt(uid, password, [jwtPayload], [jwtOptions])**
* Validate User credentials and generate JWT
```js
await auth.attempt(uid, password)

// {
//   type: 'type',
//   token: '.....',
//   refreshToken: '.....'
// }
```

**generate(user, [jwtPayload], [jwtOptions])**
* Generate JWT for User
```js
const user = await User.find(1)
await auth.generate(user)
```

**withRefreshToken**
* Generate Refresh Token
```js
await auth.withRefreshToken().attempt(uid, password)
```

**generateForRefreshToken(refresh_token, [jwtPayload])**
* Generate a new JWT using a refresh token.
```js
const refreshToken = request.input('refresh_token')
await auth.generateForRefreshToken(refreshToken, true)
```

**newRefreshToken**
* Generate a new Refresh Token, Auth provider does not refresh by default.
```js
await auth.newRefreshToken().generateForRefreshToken(refreshToken)
```

**check**
* Checks if valid JWT sent in `Authorization` Header
```js
try {
  await auth.check()
} catch(error) {
  response.send('Missing or invalid JWT token.')
}
```

**getUser**
* Returns logged in User
```js
try {
  return await auth.getUser()
} catch(error) {
  response.send('Missing or invalid JWT token.')
}
```

**listTokens**
* Lists all JWT refresh tokens for User
```js
await auth.listTokens()
```

---

## CORS

---

## CSRF Protection

---

## Encryption & Hashing

---

## Shield Middleware
