# AWS QLDB: PartiQL

> Accessing Amazon QLDB PartiQL

[AWS QLDB: PartiQL](https://docs.aws.amazon.com/qldb/latest/developerguide/ql-reference.html)

**PartiQL** provides SQL-compatible query access across multiple data stores containing structured data, semistructured data, and nested data.

* PartiQL Data Types
* QLDB Documents
* Ion Querying with PartiQL
* PartiQL Statements
* PartiQL Functions
* PartiQL Operators
* Reserved Words

---

## PartiQL Data Types

* Amazon QLDB stores documents in `Amazon Ion` format.
* `Amazon Ion` is a data serialization format. Superset of JSON.

| Data Type   | Description                                         |
|:-----------:| --------------------------------------------------- |
| `null`      | A generic null value                                |
| `bool`      | Boolean values                                      |
| `int`       | Singed Integers of arbitrary size                   |
| `decimal`   | Decimal-encoded real numbers of arbitrary precision |
| `float`     | Binary-encoded floating point number (64-bit IEEE)  |
| `timestamp` | Date/Time/Timezone moments of arbitrary precision   |
| `string`    | Unicode text literals                               |
| `symbol`    | Unicode symbolic atoms (identifiers)                |
| `blob`      | Binary data of user-defined encoding                |
| `clob`      | Text data of user-defined encoding                  |
| `struct`    | Unordered collections of name-value pairs           |
| `list`      | Ordered heterogeneous collections of values         |

---

## QLDB Documents

* Amazon QLDB stores data records as `Documents`.
* `Documents` are just __Amazon Ion__ `struct` objects for insertion to Tables.

### Ion Document Structure

* QLDB Documents are composed of name-value pairs.
  * Names are symbol tokens
  * Values are unrestricted
  * Each name-value pair is called a `Field`
  * The value of a `Field` can be any Ion Data Types, including Container Types: Nested Structs, Lists, and Lists of Structs

Format
```
{
    name1: value1,
    name1: value2,
    ...
    nameN: valueN
}
```

Example
```
{
    VIN: "1N4AL11D75C109151",
    LicensePlateNumber: "LEWISR261LL",
    State: "WA",
    City: "Seattle",
    PendingPenaltyTicketAmount: 90.25,
    ValidFrom: 2017-08-21T,
    ValidTo: 2020-05-11T,
    Owners: {
        PrimaryOwner: { PersonId: "294jJ3YUoH1IEEm8GSabOs" },
        SecondaryOwners: [{ PersonId: "5Ufgdlnj06gF5CWcOIu64s" }]
    }
}
```

---

## PartiQL Statements

### `CREATE INDEX`

Syntax: `CREATE INDEX ON table (field)`

| Parameter | Description                      |
| --------- | -------------------------------- |
| `table`   | Table to create Index            |
| `field`   | Table Field Name to create Index |

Examples
* `CREATE INDEX ON VehicleRegistration (LicensePlateNumber)`
* `CREATE INDEX ON Vehicle (VIN)`

### `CREATE TABLE`

Syntax: `CREATE TABLE table`

| Parameter | Description                                                            |
| --------- | ---------------------------------------------------------------------- |
| `table`   | 1-128 alphanumeric characters. First character Letter. Case-sensitive. |

Examples
* `CREATE TABLE VehicleRegistration`

### `DROP TABLE`

Syntax: `DROP TABLE table`

| Parameter | Description           |
| --------- | --------------------- |
| `table`   | Name of Table to Drop |

Examples
* `DROP TABLE VehicleRegistration`

### `UNDROP TABLE`

Syntax: `UNDROP TABLE "table-id"`

| Parameter  | Description                                            |
| ---------- | ------------------------------------------------------ |
| `table-id` | Unique Table ID within Quotation. Must be __Inactive__ |

Examples
* `UNDROP TABLE "5PLf9SXwndd63lPaSIa0O6"`

### `DELETE`

Syntax:
```
DELETE FROM table [ AS table_alias ]
[ WHERE condition ]
```

| Parameter        | Description                                          |
| ---------------- | ---------------------------------------------------- |
| `table`          | Table containing data to be deleted                  |
| AS `table_alias` | Optional-A user-defined alias that ranges over Table |
| `condition`      | Selection criteria for Document deletion             |

Examples
```
DELETE FROM VehicleRegistration AS r
WHERE r.VIN = '1HVBBAANXWH544237'
```

### `FROM`

Syntax:
__INSERT__
```
FROM table [ AS table_alias ] [ BY id_alias ]
[ WHERE condition ]
INSERT INTO element VALUE data [ AT key_name ]
```

__DELETE__
```
FROM table [ AS table_alias ] [ BY id_alias ]
[ WHERE condition ]
REMOVE element
```

__UPDATE__
```
FROM table [ AS table_alias ] [ BY id_alias ]
[ WHERE condition ]
SET element = data [, element = data, ... ]
```

__NESTED__
```
FROM VehicleRegistration r, @r.Owners.SecondaryOwners o
WHERE r.VIN = '1N4AL11D75C109151' AND o.PersonId = 'abc123'
SET o.PersonId = 'def456'
```
* You can declare an Alias for each collection and then use it in both `SET` & `WHERE`

| Parameter        | Description                                                                                    |
| ---------------- | ---------------------------------------------------------------------------------------------- |
| `table`          | Table containing data to be modified                                                           |
| AS `table_alias` | Optional-A user-defined alias that ranges over Table                                           |
| BY `id_alias`    | Optional-A user-defined alias that binds the `id` metadata field of the Document to the result |
| `condition`      | Selection criteria for Document deletion                                                       |
| `element`        | An element within the Documents to be created or modified                                      |
| `data`           | A new value for the `element`                                                                  |
| AT `key_name`    | A key name to be added within the Documents to be modified. Specify `VALUE` along with key     |


Examples
```
FROM Vehicle AS v
WHERE v.Color = 'Silver'
SET v.Color = 'Shiny Gray'
```

```
FROM VehicleRegistration AS r
WHERE r.VIN = '1N4AL11D75C109151'
INSERT INTO r.Owners.SecondaryOwners VALUE { 'PersonId' : 'abc123' }
```

### `INSERT`

Syntax:
__Single__: `INSERT INTO table VALUE doc`

__Multiple__: `INSERT INTO table << doc, doc, ... >>`

| Parameter | Description              |
| --------- | ------------------------ |
| `table`   | Table to insert the data |
| `doc`     | Specify valid document   |

Examples
__Single__
```
INSERT INTO VehicleRegistration VALUE
{
    'VIN' : 'KM8SRDHF6EU074761', --string
    'RegNum' : 1722, --integer
    'State' : 'WA',
    'City' : 'Kent',
    'PendingPenaltyTicketAmount' : 130.75, --decimal
    'Owners' : { --nested struct
        'PrimaryOwner' : { 'PersonId': '294jJ3YUoH1IEEm8GSabOs' },
        'SecondaryOwners' : [ --list of structs
            { 'PersonId' : '1nmeDdLo3AhGswBtyM1eYh' },
            { 'PersonId': '1nmeDdLo3AhGswBtyM1eYh' }
        ]
    },
    'ValidFromDate' : `2017-09-14T`, --Ion timestamp literal with day precision
    'ValidToDate' : `2020-06-25T`
}
```

__Multiple__
```
INSERT INTO Person <<
{
    'FirstName' : 'Raul',
    'LastName' : 'Lewis',
    'DOB' : `1963-08-19T`,
    'GovId' : 'LEWISR261LL',
    'GovIdType' : 'Driver License',
    'Address' : '1719 University Street, Seattle, WA, 98109'
},
{
    'FirstName' : 'Brent',
    'LastName' : 'Logan',
    'DOB' : `1967-07-03T`,
    'GovId' : 'LOGANB486CG',
    'GovIdType' : 'Driver License',
    'Address' : '43 Stockert Hollow Road, Everett, WA, 98203'
},
{
    'FirstName' : 'Alexis',
    'LastName' : 'Pena',
    'DOB' : `1974-02-10T`,
    'GovId' : '744 849 301',
    'GovIdType' : 'SSN',
    'Address' : '4058 Melrose Street, Spokane Valley, WA, 99206'
}
>>
```

### `SELECT`

Syntax:
```
SELECT [ VALUE ] expression [ AS field_alias ] [, ...]
FROM source [ AS source_alias ] [ AT idx_alias ] [ BY id_alias ] [, source, ...]
[ WHERE condition ]
```

| Parameter | Description |
| --------- | ----------- |
|

Examples
* ``
* ``

### `UPDATE`

Syntax:
```
UPDATE table [ AS table_alias ] [ BY id_alias ]
SET element = data [, element = data, ... ]
[ WHERE condition ]
```

| Parameter        | Description                                                                                    |
| ---------------- | ---------------------------------------------------------------------------------------------- |
| `table`          | Table containing data to be modified                                                           |
| AS `table_alias` | Optional-A user-defined alias that ranges over Table                                           |
| BY `id_alias`    | Optional-A user-defined alias that binds the `id` metadata field of the Document to the result |
| `condition`      | Selection criteria for Document deletion                                                       |
| `element`        | An element within the Documents to be created or modified                                      |
| `data`           | A new value for the `element`                                                                  |

Examples
```
UPDATE Person AS p
SET p.LicenseNumber = 'HOLLOR123ZZ'
WHERE p.FirstName = 'Rosemarie' AND p.LastName = 'Holloway'
```

---

## PartiQL Functions

### `AVG`

### `CAST`

### `CHAR_LENGTH`

### `CHARACTER_LENGTH`

### `COALESCE`

### `COUNT`

### `DATE_ADD`

### `DATE_DIFF`

### `EXISTS`

### `EXTRACT`

### `LOWER`

### `MAX`

### `MIN`

### `NULLIF`

### `SIZE`

### `SUBSTRING`

### `SUM`

### `TO_STRING`

### `TO_TIMESTAMP`

### `TRIM`

### `TXID`

### `UPPER`

### `UTCNOW`

### Timestamp Format Strings

---

## PartiQL Operators

---

## Reserved Words
