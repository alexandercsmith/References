# AWS QLDB

> Amazon Quantum Ledger Database

[Amazon Quantum Ledger](https://docs.aws.amazon.com/qldb/index.html)

* Amazon Quantum Ledger Database is a fully managed ledger database owned by a central trusted authority that provides a transparent, immutable, and cryptographically verifiable transaction log of all your application changes.
* Amazon QLDB tracks every application data change and maintains a complete verifiable history of changes over time.

---

## Overview
- The `Journal` is the core of the database.
  - The `Journal` is immutable.
  - Append-only Data Structure, that stores transaction data with associated metadata.
  - All `write` transactions (create, update, delete) are committed to the journal first.
  - The `Journal` handles concurrency, sequencing, cryptographic verification, and availability of the ledger.
- QLDB uses the `Journal` to determine the current state.

### Immutable
- QLDB is append-only, it keeps a full record of all changes and transactions and cannot be modified, deleted or overwritten.
- No exposed API to manipulate committed data. Full access to ledger history.
- QLDB writes one or more `Blocks` to the `Journal` in each transaction.
  - Each `Block` contains entry objects that represent documents that you manipulate along with statements to execute for commit.
  - `Blocks` are sequenced and hash-chained to guarantee data integrity.

### Cryptographically Verifiable
- `Journal` `Blocks` are sequenced and chained together with cryptographic hashing, similar to blockchain.
- Using a `Digest` [A Hash value representing a Journals full hash chain in a point of time] and a `Merkle Audit Proof` [A mechanism that proves the validity of any node within a binary hash tree].

### SQL Compatible and Document Flexible
- QLDB uses `PartiQL` as its query language and `Amazon Ion` as its document-oriented data model.
- `PartiQL` is a open-source and SQL-compatible query language that has been extended to work with `Ion`.
- `PartiQL` allows for insert, query and management of data with similar SQL operators.
- `Amazon Ion` is a superset of JSON.
- `Amazon Ion` is open-source and document-based data format.

---

## Relational to Ledger

### Components

| RDBMS      |     | QLDB                |
|:----------:|:---:|:-------------------:|
| Database   | ->  | Ledger              |
| Table      | ->  | Table               |
| Index      | ->  | Index               |
| Table Row  | ->  | Amazon Ion Document |
| Column     | ->  | Document Attribute  |
|            |     |                     |
| SQL        | ->  | PartiQL             |
| Audit Logs | ->  | Journal             |

### Features

| Operation              | RDBMS                                           | QLDB |
| ---------------------- | ----------------------------------------------- | ---- |
| Create Tables          | `CREATE TABLE` Defining Column names and types  | `CREATE TABLE` not defining Tables attributes or types                             |
| Create Indexes         | `CREATE INDEX` Statement                        | `CREATE INDEX` can execute on empty Table or Single field                          |
| Insert Data            | `INSERT` specifying values in a new row/tuple   | `INSERT` specify values within new Document in valid `Ios` format                  |
| Query Data             | `SELECT-FROM-WHERE` Statement                   | `SELECT-FROM-WHERE` same SQL syntax on flat Documents                              |
| Update Data            | `UPDATE-SET-WHERE` Statement                    | `UPDATE-SET-WHERE` same SQL syntax on flat Documents                               |
| Delete Data            | `DELETE-FROM-WHERE` Statement                   | `DLETE-FROM-WHERE` same SQL syntax on flat Documents                               |
| Nesting                | Flat rows or tuples only                        | Documents any structured, semi-structured or nested `Ion`/`PartiQL` formatted data |
| Query Metadata         | No built-in metadata                            | `SELECT` querying from built-in committed view of Table                            |
| Query Revision History | No built-in metadata                            | `SELECT` querying from built-in history function                                   |
| Cryptographic Verify   | No built-in cryptography or immutability        | APIs returning digest of `Journal` and verified proof of Integrity                 |
