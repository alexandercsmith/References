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

---

## Core Concepts

### Ledger Structure
* QLDB data is organized into Tables of `Amazon Ion` documents.
* Tables are collections of `Document Revisions`.
* A `Document Revision` represents a single iteration of the Documents full dataset.
* Amazon QLDB stores the complete change history of your data.
* __Documents__ -> `Document Revision`

### Write Transactions
* Modification of QLDB Document data requires a Database Transaction.
* Transaction: Data is read from Ledger, Updated, and Committed to the `Journal`
* The `Journal` represents the complete immutable history of all data changes.
* QLDB writes one or more chained `Blocks` to the `Journal` in a transaction.
* Each `Block` contains `Entry` objects to represent `Document Revisions` to Insert, Update and Delete, along with `PartiQL` statements to commit.
* Each `Block` is hashed and chained to subsequent `Blocks` for verification.
* A `Strand` is a partition of your ledger's `Journal`. QLDB supports `Journals` with a single `Strand` only.

### Querying your Data
* Amazon QLDB addresses high-performance online transaction processing workloads. (`OLTP`)
* A Ledger provides queryable views of data based on transaction information committed to the `Journal`.
* A `View` in QLDB is a projection of data in a Table.
* Query `Views` using **PartiQL** `SELECT` statements.
  * **User**: The latest non-deleted revision of Application-defined data. [Default]
  * **Committed**: The latest non-deleted revision of both data and system-generated metadata.
* `History Function` returns both data and associated metadata in the same schema as the `Committed View`.

### Data Storage
* `Journal Storage`
  * The disk space that is used by a Ledger's `Journal`.
  * `Journals` are append-only and contain the complete, immutable, and verifiable history of changes.
* `Indexed Storage`
  * The disk space that is used by  a Ledger's `Tables`, `Indexes`, and `Indexed History`.
  * `Indexed Storage` consists of Ledger data that is optimized for high-performace queries.
