# ac-postgres [![Documentation Status](https://readthedocs.org/projects/ansicolortags/badge/?version=latest)](http://ansicolortags.readthedocs.io/?badge=latest)

Amigoscode's PostgreSQL tutorial notes

## Contents

- [Getting started with PostgreSQL](#Getting-started-with-PostgreSQL)
- [Database Management Tool](#Database-Management-Tool)
  - [Adminer](#Adminer)
- [PostgreSQL Server](#PostgreSQL-Server)
- [References](#References)

## Getting started with PostgreSQL

- Connect to database server using psql command

```
psql -h hostname -p port -U username databasename
```
- Open psql, the command-line interface to PostgreSQL, e.g. inside the postgres docker container:

```
psql -U username
```

- Create database:

```
CREATE DATABASE __database_name__;
```

- Delete database:

```
DROP DATABASE __database_name__;
```
- Create Table:

```
CREATE TABLE table_name(
  Column name + data type + constraints if any
)

e.g. with constraints: 

CREATE TABLE person(
  id BIGSERIAL NOT NULL PRIMARY KEY, 
  first_name VARCHAR(50) NOT NULL,
  last_name VARCHAR(50) NOT NULL,
  gender VARCHAR(6) NOT NULL,
  date_of_birth DATE NOT NULL,
  email VARCHAR(150)
);
```
- Delete Table:
```
DROP TABLE table_name;
```

- [Data types](https://www.postgresql.org/docs/13/datatype.html) in PostgreSQL.

- psql command-line interface commands:
```
  \copyright    for distribution terms
  \h            for help with SQL commands
  \?            for help with psql commands
  \g            or terminate with semicolon to execute query
  \q            to quit
```

- Insert records into tables:
```
INSERT INTO person(
  first_name,
  last_name,
  gender,
  date_of_birth
)
VALUES('Anne', 'Smith', 'FEMALE', DATE '2000-01-01')
```


## Database Management Tool

### Adminer

Open Adminer (http://localhost:8080). Then complete the form :
```
“System” : select “PostgresSQL” ;
“Server” : type “dbPostgres” ; # i.e. service name from docker-compose.yml
“Username” : type “postgres” ;
“Password” : type “postgres” ;
“Database” : type “postgres” ;
Click “login” button.
```

## PostgreSQL Server

Start/Stop postgres server as docker container using properties defined in docker-compose.yml
```
docker compose up -d
docker compose down
```

Start postgres commind-line inside a docker container:

```
docker exec -ti $(docker ps -a | grep db | awk '{ print $1 }') psql -U postgres
```

### Placeholder21

Placeholder test...

## References

[1. Source A.](link)
