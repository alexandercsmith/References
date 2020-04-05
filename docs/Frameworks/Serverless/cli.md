# Serverless Framework CLI

> Serverless Framework Command-line Interface

* `create`
* `install`
* `package`
* `deploy`
* `deploy function`
* `deploy list`
* `invoke`
* `invoke local`
* `logs`
* `login`
* `metrics`
* `info`
* `rollback`
* `rollback function`
* `remove`
* `plugin list`
* `plugin search`
* `plugin install`
* `plugin uninstall`
* `print`

---

## `create`

### Create Service in Current Directory
```bash
$ serverless create -t aws-nodejs
```

### Create Service in New Directory
```bash
$ serverless create -t aws-nodejs -p myNewService
```

**Options**
| Option            | Tag  | Description                          |
|:------------------|:----:|:-------------------------------------|
| `--template`      | `-t` | Serverless Service Template          |
| `--template-url`  | `-u` | Remote Template URL                  |
| `--template-path` | -    | Local Template Path                  |
| `--path`          | `-p` | Path where to create new Service     |
| `--name`          | `-n` | Name of Service for `serverless.yml` |

---

## `install`

### Install Service from Git URL
```bash
$ serverless install --url https://github.com/some/service
```

**Options**
| Option   | Tag  | Description      |
|:---------|:----:|:-----------------|
| `--url`  | `-u` | Git URL          |
| `--name` | `-n` | Name for Service |

**Supported Platforms**
* GitHub
* GitHub Enterprise
* GitLab
* BitBucket
* BitBucket Server

---

## `package`

### Package Serverless Service for Deployment
```bash
$ serverless package

$ serverless package --stage production --region us-east-1
```

**Options**
| Option      | Tag  | Description                        |
|:------------|:----:|:-----------------------------------|
| `--stage`   | `-s` | Stage of Service to Deploy         |
| `--region`  | `-r` | Region of Service to Deploy        |
| `--package` | `-p` | Path to Custom Packaging Directory |

---

## `deploy`

### Deploy a Service
```bash
$ serverless deploy
```

**Options**
| Option                   | Tag  | Description                                                              |
|:-------------------------|:----:|:-------------------------------------------------------------------------|
| `--config`               | `-c` | Name of Configuration File                                               |
| `--stage`                | `-s` | Name of Stage to Deploy Service                                          |
| `--region`               | `-r` | Name of Region to Deploy Service                                         |
| `--package`              | `-p` | Path of Pre-packaged Directory, Skip Package Step                        |
| `--verbose`              | `-v` | Shows all stack events during Deployment                                 |
| `--force`                | -    | Force a Deployment                                                       |
| `--function`             | `-f` | Invoke `deploy function`                                                 |
| `--conceal`              | -    | Hides Secrets from Output                                                |
| `--aws-s3-accelerate`    | -    | Enables S3 Transfer Acceleration making uploading artifacts much faster. |
| `--no-aws-s3-accelerate` | -    | Explicitly disables S3 Transfer Acceleration.                            |

---

## `deploy function`

### Deploy Individual Function
```bash
$ serverless deploy function -f functionName
```

**Options**
| Option            | Tag  | Description                                    |
|:------------------|:----:|:-----------------------------------------------|
| `--function`      | `-f` | Name of Function to Deploy                     |
| `--stage`         | `-s` | Name of Stage to Deploy Service                |
| `--region`        | `-r` | Name of Region to Deploy Service               |
| `--update-config` | `-u` | Pushes only Lambda-level Configuration changes |

## `deploy list`

### View Deployments Information
```bash
$ serverless deploy list
```

### View Deployed Functions
```bash
$ serverless deploy list functions
```

**Options**
| Option     | Tag  | Description                      |
|:-----------|:----:|:---------------------------------|
| `--stage`  | `-s` | Name of Stage to Deploy Service  |
| `--region` | `-r` | Name of Region to Deploy Service |

---

## `invoke`

### Invoke Deployed Function
```bash
# Invoke Function
$ serverless invoke --function functionName

# Invoke Function with Data
$ serverless invoke --function functionName --data "Hello"

# Invoke Function with Passing Data
$ serverless invoke --function functionName --path lib/data.json
```

**Options**
| Option        | Tag  | Description                                              |
|:--------------|:----:|:---------------------------------------------------------|
| `--function`  | `-f` | Name of Function to Invoke                               |
| `--stage`     | `-s` | Name of Stage to Invoke Function                         |
| `--region`    | `-r` | Name of Region to Invoke Function                        |
| `--qualifier` | `-q` | Version Number or Alias                                  |
| `--data`      | `-d` | String of Data to Pass to Function                       |
| `--raw`       | -    | Pass data as raw string                                  |
| `--path`      | `-p` | Path of JSON file with input data                        |
| `--type`      | `-t` | Type of invocation: `RequestResponse`, `Event`, `DryRun` |
| `--log`       | `-l` | If `true`, Type is `RequestResponse`                     |

---

## `invoke local`

### Invoke Function Locally
```bash
$ serverless invoke local --function functionName
```

**Options**
| Option           | Tag  | Description                               |
|:-----------------|:----:|:------------------------------------------|
| `--function`     | `-f` | Name of Function to Invoke                |
| `--path`         | `-p` | Path of JSON file with input data         |
| `--data`         | `-d` | String of Data to Pass to Function        |
| `--raw`          | -    | Pass data as raw string                   |
| `--contextPath`  | `-x` | Path of JSON file with input data         |
| `--context`      | `-c` | String of data to be passed to Function   |
| `--env`          | `-e` | String representing Environment variables |
| `--docker`       | -    | Enable Docker support                     |
| `--docker-arg`   | -    | Pass Docker arguments                     |
| `--skip-package` | -    | Use last packaged files                   |

---

## `logs`

### Watch Function Logs
```bash
$ serverless logs -f helloFunc

# Tail logs
$ serverless logs -f helloFunc -t

# Tail logs & Start Time past `5` hours
$ serverless logs -f helloFunc -t --startTime 5h
```

**Options**
| Option        | Tag  | Description                       |
|:--------------|:----:|:----------------------------------|
| `--function`  | `-f` | Name of Function to Invoke        |
| `--stage`     | `-s` | Name of Stage to Invoke Function  |
| `--region`    | `-r` | Name of Region to Invoke Function |
| `--startTime` | -    | Specific starting point for logs  |
| `--filter`    | -    | Specific filter String            |
| `--tail`      | `-t` | Tail logs                         |
| `--interval`  | `-i` | Interval to poll logs             |

---

## `login`

### Login User to Serverless Dashboard `https://dashboard.serverless.com`
```bash
$ serverless login
```

---

## `metrics`

### Watch Function Metrics
```bash
$ serverless metrics

# Specified Time Period
$ serverless metrics --startTime 2016-01-01 --endTime 2016-01-02

# Function Metrics for Time Period
$ serverless metrics -f helloFunc --startTime 2016-01-01 --endTime 2016-01-02
```

**Options**
| Option        | Tag  | Description                       |
|:--------------|:----:|:----------------------------------|
| `--function`  | `-f` | Name of Function to Invoke        |
| `--stage`     | `-s` | Name of Stage to Invoke Function  |
| `--region`    | `-r` | Name of Region to Invoke Function |
| `--startTime` | -    | Specified Starting Time           |
| `--endTime`   | -    | Specified Ending Time             |

---

## `info`

### Serverless Service Information
```bash
$ serverless info
```

**Options**
| Option      | Tag  | Description                       |
|:------------|:----:|:----------------------------------|
| `--stage`   | `-s` | Name of Stage to Invoke Function  |
| `--region`  | `-r` | Name of Region to Invoke Function |
| `--verbose` | `-v` | All stack output                  |

---

## `rollback`

### Rollback Service to Specific Deployment
```bash
$ serverless rollback --timestamp timestamp
```

**Options**
| Option        | Tag  | Description             |
|:--------------|:----:|:------------------------|
| `--timestamp` | `-t` | Deployment for Rollback |
| `--verbose`   | `-v` | All stack output        |

---

## `rollback function`

### Rollback Function to Specific Deployment
```bash
$ serverless rollback function --function funcName --version funcVersion
```

**Options**
| Option       | Tag  | Description                        |
|:-------------|:----:|:-----------------------------------|
| `--function` | `-f` | Name of Function to Invoke         |
| `--version`  | `-v` | Version of Deployment for Rollback |

---

## `remove`

### Remove Deployed Service
```bash
$ serverless remove
```

**Options**
| Option      | Tag  | Description                       |
|:------------|:----:|:----------------------------------|
| `--stage`   | `-s` | Name of Stage to Invoke Function  |
| `--region`  | `-r` | Name of Region to Invoke Function |
| `--verbose` | `-v` | All stack output                  |

---

## `plugin list`

### List All Plugins
```bash
$ serverless plugin list
```

---

## `plugin search`

### Search for Plugin
```bash
$ serverless plugin search --query query
```

**Options**
| Option    | Tag  | Description      |
|:----------|:----:|:-----------------|
| `--query` | `-q` | Query for Search |

---

## `plugin install`

### Install Plugin
```bash
$ serverless plugin install --name pluginName
```

**Options**
| Option   | Tag  | Description            |
|:---------|:----:|:-----------------------|
| `--name` | `-n` | Plugin Name to Install |

---

## `plugin uninstall`

### Uninstall Plugin
```bash
$ serverless plugin uninstall --name pluginName
```

**Options**
| Option   | Tag  | Description              |
|:---------|:----:|:-------------------------|
| `--name` | `-n` | Plugin Name to Uninstall |

---

## `print`

### Print Configuration from `serverless.yml`
```bash
$ serverless print
```

**Options**
| Option      | Description           |
|:------------|:----------------------|
| `format`    | Print configuration   |
| `path`      | Period separated Path |
| `transform` | Transform Function    |
