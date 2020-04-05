# Serverless Framework Events

> Serverless AWS Events for Function Invocation

* API Gateway
* HTTP API
* WebSocket
* Kinesis & DynamoDB
* S3
* Schedule
* SNS
* SQS
* Application Load
* Alexa Skill
* Alexa Smart Home
* IoT
* CloudWatch Event
* CloudWatch Log
* EventBridge Event
* CloudFront
* Cognito User Pool

---

## API Gateway

[Serverless: AWS API Gateway](https://serverless.com/framework/docs/providers/aws/events/apigateway/)

### Configuration
```yml
# serverless.yml
# General Function with CORS
functions:
  create:
    handler: handler.myFunc
    events:
      - http:
          path: myFunc
          method: get
          cors:
            origins:
              - http://*.site.com

# Cognito User Authorization
functions:
  create:
    handler: posts.create
    events:
      - http:
          path: posts/create
          method: post
          authorizer:
            arn: arn:aws:cognito-idp:us-east-1:xxx:userpool/us-east-1_ZZZ
            scopes:
              - my-app/read
```

### Function
```js
// handler.js
module.exports.myFunc = function(event, context, callback) {
  console.log(event);
  const response = {
    statusCode: 200,
    headers: {
      'x-custom-header': 'VALUE'
    },
    body: JSON.stringify({ message: 'Hello' })
  };
  callback(null, response);
};
```

---

## HTTP API

---

## WebSocket

---

## Kinesis & DynamoDB

---

## S3

---

## Schedule

---

## SNS

---

## SQS

---

## Application Load

---

## Alexa Skill

---

## Alexa Smart Home

---

## IoT

---

## CloudWatch Event

---

## CloudWatch Log

---

## EventBridge Event

---

## CloudFront

---

## Cognito User Pool
