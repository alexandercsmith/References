# AWS SDK - DynamoDB

> Node.js

[AWS SDK QLDB Documentation](https://docs.aws.amazon.com/qldb/latest/developerguide/getting-started.nodejs.html)

---

## Installation: Driver

Dependencies
```bash
# pkg: amazon-qldb-driver-nodejs
$ npm install amazon-qldb-driver-nodejs

# pkg: aws-sdk
$ npm install aws-sdk

# pkg: ion-js
$ npm install ion-js
```

## Connect to Ledger

```ts
import { PooledQldbDriver, QldbSession } from "amazon-qldb-driver-nodejs";

const testServiceConfigOptions = {
  region: "us-east-1"
};

const qldbDriver: PooledQldbDriver = new PooledQldbDriver("testLedger", testServiceConfigOptions);
const qldbSession: QldbSession = await qldbDriver.getSession();

for (const table of await qldbSession.getTableNames()) {
  console.log(table);
}
```
