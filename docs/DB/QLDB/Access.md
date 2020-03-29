# AWS QLDB: Access

> Accessing Amazon QLDB Access

[AWS QLDB: Access](https://docs.aws.amazon.com/qldb/latest/developerguide/accessing.html)

* Console
* AWS CLI
* Amazon QLDB Shell
* API

---

## Console

Console Abilities:
* Create, Delete, Describe and List Ledgers.
* Create a Table and Indexes.
* Insert, Update, and Delete data.
* Run queries.
* Cryptographically Verify Documents.
* Export Journal Blocks.

---

## AWS CLI

Access Amazon QLDB using the AWS CLI

```bash
# Run Operation
$ aws qldb <operation>

# Reference Operations
$ aws qldb help
```

---

## Amazon QLDB Shell

* Amazon QLDB command line shell interacts with the Transaction data plane.
* Amazon QLDB Shell is written in Python and executes `PartiQL` statements on Ledger data.
* Amazon QLDB Shell only supports `qldb-session` transaction data API.
  * Only used for `PartiQL` statements.

### Shell Setup

```bash
# Install using Python pip3
$ pip3 install qldbshell
```

Dependencies:
* `pyqldb`
* `amazon.ion`
* `boto3`

### Invoke Shell

```bash
$ qldbshell --ledger <ledger-name>
```

### Shell Parameters

Usage

```bash
$ qldbshell -l <ledger-name> [-v] [-p PROFILE] [-r REGION] [-s QLDB_ENDPOINT]
```

| Argument      | Short     | Full                      | Description                                          |
|:-------------:|:---------:|:-------------------------:| ---------------------------------------------------- |
| LEDGER_NAME   | `-l`      | `--ledger`                | Name of Ledger for Shell connection                  |
| VERBOSE       | `-v`      | `--verbose`               | Increases output verbosity in Shell                  |
| PROFILE       | `-p`      | `--profile`               | AWS Credential Profile for Authentication            |
| REGION        | `-r`      | `--region`                | AWS Region code of QLDB Ledger                       |
| QLDB_ENDPOINT | `-s`      | `--qldb-session-endpoint` | Specifies `qldb-session` API endpoint for connection |

### Parameter File

Input Parameters separated by lines in a configuration file to access when running Amazon QLDB Shell.

```bash
$ qldbshell @params.conf
```

### Exit Shell

```bash
qldbshell > exit
```

### Example

```bash
$ qldbshell --ledger test-ledger --region us-east-1
-
qldbshell > CREATE TABLE TestTable
qldbshell > INSERT INTO TestTable \`{"Name": "John Doe"}\`
qldbshell > SELECT * FROM TestTable
qldbshell > DROP TABLE TestTable
qldbshell > exit
```

---

## API

Create API transactions from Custom Framework Applications.

[Get Started with Amazon QLDB Driver](https://docs.aws.amazon.com/qldb/latest/developerguide/accessing.html)
