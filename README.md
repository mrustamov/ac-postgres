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
  \copyright                    for distribution terms
  \h                            for help with SQL commands
  \?                            for help with psql commands
  \g                            or terminate with semicolon to execute query
  \q                            to quit

  Most common commands: 

  \l                            list of databases
  \d                            list of relations
  \dt                           list of (only) tables
  \t                            Tuples only (e.g. table headers etc.) is off/on.
  \c databasename               Connect to database
  \i /path/to/filename.sql      Execute command from file
```

- Insert records into tables:
```
INSERT INTO table_name(
  column_name
)
VALUES('value');

e.g.: 

INSERT INTO person(
  first_name,
  last_name,
  gender,
  date_of_birth
)
VALUES('Anne', 'Smith', 'FEMALE', DATE '2000-01-01');
```

- Read and manipulate data:
```
Select * from table_name;   # SELECT FROM 
Select columnt_name from table_name;   # SELECT FROM 


Select * from table_name ORDER BY column_name;   # ORDER BY (default: ASC)
Select * from table_name ORDER BY column_name DESC;   # ORDER BY


Select DISCTINCT column_name from table_name ORDER BY column_name;   # DISCTINCT


select * from person WHERE column_name='CLAUSE/String';   # WHERE CLAUSE and AND
select * from person WHERE column_name='CLAUSE1' AND column_name2='CLAUSE2';   # WHERE CLAUSE and AND
select * from person WHERE column_name='CLAUSE1' AND (column_name2='CLAUSE2' OR column_name3='CLAUSE3');   # WHERE CLAUSE and AND


SELECT 1 > 1 OR 1 >= 1 OR 1 <> 1 OR 1 <= 1 OR 'ONE'='TWO' # COMPARISON OPERATIONS
```
- Limit, Offset & Fetch:
```
SELECT * FROM table_name LIMIT 10;                              # select first 10 entries


SELECT * FROM table_name OFFSET 5;                              # select entries after 5th entry
SELECT * FROM table_name OFFSET 5 LIMIT 10;                     # select first 10 entries after 5th entry


SELECT * FROM table_name OFFSET 5 FETCH FIRST 10 ROW ONLY;      # select first 10 entries after 5th entry. Similar to limit but FETCH is SQL standard query command
```

- IN - used to define a quantity or an array of values to be matched: 
```
SELECT * FROM table_name WHERE column_name IN ('String1', 'String2'); # Or equivalent of query with OR: 'SELECT * FROM table_name where culumn_name='String1' OR culumn_name='String2''
```

- BETWEEN - used to define a range:
```
SELECT * FROM table_name WHERE column_name BETWEEN DATE 'value_from' AND 'value_until';

e.g.:
SELECT * FROM PERSON WHERE date_of_birth BETWEEN DATE '2000-01-01' AND '2020-10-30';
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

[1. Mockaroo - Data generation tool.](https://www.mockaroo.com/)