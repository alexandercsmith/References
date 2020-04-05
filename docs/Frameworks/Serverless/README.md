# Serverless Framework

> Develop, Deploy, Monitor and Secure Serverless applications on any cloud.

* [Serverless Framework](https://serverless.com/)
* [Serverless - AWS](https://serverless.com/framework/docs/providers/aws/)


## Directory
* [Serverless CLI](./cli.md)
* [Serverless Events](./events.md)

---

## Installation
```bash
# Install
$ npm install -g serverless

# Upgrade
$ npm update -g serverless
```

## Credentials
```bash
$ serverless config credentials --provider provider --key key --secret secret
```
* `--provider` - `-p` : Provider (AWS)
* `--key` - `-k` : Key (aws_access_key_id)
* `--secret` - `-s` : Secret (aws_secret_access_key)
* `--profile` - `-n` : Name of Profile
* `--overwrite` - `-o` : Overwrite Profile

## Functions
```js
module.exports.myFunctionName = function(event, context, callback) {
  // function logic
}
```
