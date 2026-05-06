# docker-project
Full-stack student application project with Dockerized frontend and backend.
# MySQL Setup and Configuration Guide (Windows / Ubuntu)

This guide explains how to set up mysql, create a database, and Create Database User

## 1. Installing mysql

Installing mysql on Ubntu

```bash
apt update && apt install mysql-client -y
```

## 2. Securing mysql

Open the Command Prompt as Administrator and run the following command to secure your installation:

```bash

mysql_secure_installation
```

Follow the prompts to:
Set a root password.
Remove insecure default users and test databases.
Disable remote root login.

## 3. Setting Up the Database

Open terminal and login to MariaDB:

```bash

mysql -h (endpoint of database) -u admin -p
```

Enter the root password when prompted.

Create a new database and user:

```sql
CREATE DATABASE student_db;
GRANT ALL PRIVILEGES ON springbackend.* TO 'username'@'localhost' IDENTIFIED BY 'your_password';
```
Replace username and your_password with your desired username and password.



## 4. You will need Database Credentials to Connect Backend with Database
1. DB_HOST
2. DB_USER
3. DB_PASS
4. DB_PORT

5. DB_NAME

```sh
USE student_db;
```
```sh
CREATE TABLE `students` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `email` varchar(255) DEFAULT NULL,
  `course` varchar(255) DEFAULT NULL,
  `student_class` varchar(255) DEFAULT NULL,
  `percentage` double DEFAULT NULL,
  `branch` varchar(255) DEFAULT NULL,
  `mobile_number` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=80 DEFAULT CHARSET=latin1 COLLATE=latin1_swedish_ci;
```
EXIT FROM DATABASE
```sql

EXIT;
```


