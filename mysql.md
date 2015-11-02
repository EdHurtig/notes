# MySQL

## Install

From scratch (Ubuntu)

```bash
sudo apt-get install mysql-server
```

Then follow the prompts to lock down the server

```bash
mysql_secure_installation
```

## Login

Login as root user to localhost (unix socket)

```bash
mysql -uroot -p
```

Login as root user to remote host

```bash
mysql -uroot -p -h123.123.123.123
```

## Databases

Show the databases

```sql
SHOW DATABASES;
```

Create a database named mydb

```sql
CREATE mydb;
```

Select a database for autocompletion and query scope
```sql
USE mydb;
```

## Users

List out all the user entries

```sql
SELECT User FROM mysql.user;
```

Create a new user.

* User accounts have a username and a remote host (localhost, %, ect). There are sometimes 2 root accounts
* Always specify an `IDENTIFIED BY` otherwise that user can login without a password

```sql
# All access, only allowed to login from localhost
CREATE USER 'monty'@'localhost' IDENTIFIED BY 'some_pass';
GRANT ALL PRIVILEGES ON *.* TO 'monty'@'localhost' WITH GRANT OPTION;

# All access, allowed to login from anywhere
CREATE USER 'monty'@'%' IDENTIFIED BY 'some_pass';
GRANT ALL PRIVILEGES ON *.* TO 'monty'@'localhost' WITH GRANT OPTION;

# give certain privs to a specific user account
GRANT RELOAD,PROCESS ON *.* TO 'admin'@'localhost';
```
## Privledges

| Privilege               | Column                | Context                               |
|-------------------------|-----------------------|---------------------------------------|
| CREATE                  | Create_priv           | databases, tables, or indexes         |
| DROP                    | Drop_priv             | databases, tables, or views           |
| GRANT OPTION            | Grant_priv            | databases, tables, or stored routines |
| LOCK TABLES             | Lock_tables_priv      | databases                             |
| REFERENCES              | References_priv       | databases or tables                   |
| EVENT                   | Event_priv            | databases                             |
| ALTER                   | Alter_priv            | tables                                |
| DELETE                  | Delete_priv           | tables                                |
| INDEX                   | Index_priv            | tables                                |
| INSERT                  | Insert_priv           | tables or columns                     |
| SELECT                  | Select_priv           | tables or columns                     |
| UPDATE                  | Update_priv           | tables or columns                     |
| CREATE TEMPORARY TABLES | Create_tmp_table_priv | tables                                |
| TRIGGER                 | Trigger_priv          | tables                                |
| CREATE VIEW             | Create_view_priv      | views                                 |
| SHOW VIEW               | Show_view_priv        | views                                 |
| ALTER ROUTINE           | Alter_routine_priv    | stored routines                       |
| CREATE ROUTINE          | Create_routine_priv   | stored routines                       |
| EXECUTE                 | Execute_priv          | stored routines                       |
| FILE                    | File_priv             | file access on server host            |
| CREATE USER             | Create_user_priv      | server administration                 |
| PROCESS                 | Process_priv          | server administration                 |
| RELOAD                  | Reload_priv           | server administration                 |
| REPLICATION CLIENT      | Repl_client_priv      | server administration                 |
| REPLICATION SLAVE       | Repl_slave_priv       | server administration                 |
| SHOW DATABASES          | Show_db_priv          | server administration                 |
| SHUTDOWN                | Shutdown_priv         | server administration                 |
| SUPER                   | Super_priv            | server administration                 |
| ALL [PRIVILEGES]        |                       | server administration                 |
| USAGE                   |                       | server administration                 |

_see also: https://dev.mysql.com/doc/refman/5.1/en/privileges-provided.html_

# Queries

Follows pretty standard SQL syntax... `SELECT column FROM table WHERE table.foo='bar' LIMIT 12`


