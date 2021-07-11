# ac-postgres [![Documentation Status](https://readthedocs.org/projects/ansicolortags/badge/?version=latest)](http://ansicolortags.readthedocs.io/?badge=latest)

Amigoscode's PostgreSQL tutorial notes

## Contents

- [Create commands](#Create-commands)
- [Database Management Tool](#Database-Management-Tool)
  - [Adminer](#Adminer)
- [References](#References)

## Create commands

- Connect to database server using psql command

```
psql -h hostname -p port -U username databasename
```

- Create database:

```
CREATE DATABASE __database_name__;
```

- Delete database:

```
DROP DATABASE __database_name__;
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

## Placeholder20

Placeholder test...

### Placeholder21

Placeholder test...

## References

[1. Source A.](link)
