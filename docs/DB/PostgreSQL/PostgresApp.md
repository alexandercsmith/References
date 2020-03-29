# PostgresApp Database Client

> Object-relational Database Management System (ORDBMS)

* Documentation
* GUI Clients
* Installation
* CLI
* Tools
* Connection

---

## Documentation

* [PostgreSQL Documentation](https://www.postgresql.org/docs/current/index.html)
* [Postgres.app](https://postgresapp.com/)

---

## GUI Clients

* [Postico](https://eggerapps.at/postico/)

---

## Installation

1. Navigate to [Postgres.app Download](https://postgresapp.com/downloads.html) and Download Latest Release.
2. Move Application to Application's Folder on Machine.
3. Click `Initialize` to create a new Server.

### Configuration

| -------- | ------------------------ |
| Host     | `localhost`              |
| Port     | 5432                     |
| User     | `System User Name`       |
| Database | `Same as User`           |
| Password | `none`                   |
| URL      | `postgresql://localhost` |

---

## CLI

### Configure `$PATH`

1. Execute following command
```
$ sudo mkdir -p /etc/paths.d &&
$ echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp
```

2. Edit `.profile` on System

### CLI Options

| Command      | Description                     |
| ------------ | ------------------------------- |
| `psql`       | Connect directory to PostgreSQL |
| `which psql` | Check PostgreSQL $PATH          |
| `man psql`   | Access PostgreSQL Documentation |

---

## Tools

### PostgreSQL

### PROJ.4

### GDAL

### PostGIS
