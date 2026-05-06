# STUDENT MANAGEMENT SYSTEM (DOCKERIZED)
## 1. About the Project
## Project Overview
The Student Application Project is a full-stack web application designed to manage student records (ID, name, email, course, etc.).
It serves as a practical implementation of a microservices-lite architecture, where the frontend and backend are decoupled and managed as independent units.
## Core Components=
      Frontend (React): A dynamic user interface that allows users to interact with student data. It is served via an Nginx-style container on port 80.
      Backend (Spring Boot): A Java-based REST API that handles the business logic and communicates with the database.
      Database (MySQL/MariaDB): A relational database used for persistent storage of student information.
      
## step 1.Install Docker Engine
Docker is the core engine used to build and run your frontend and backend images.

Check Installation:
```bash
docker -version
```  

Installation (on Ubuntu):

```bash
sudo apt update && sudo apt install docker.io -y
```

## step 2.Install Database Client
Since your project uses an external/separate MySQL/MariaDB database, you need a client on your local machine to initialize the tables before the backend connects.

Command:

```bash
sudo apt install mysql-client -y
```

## step 3. Clone the Project Repository
Bring the source code from GitHub to your local environment.

Command:
```bash
git clone https://https://github.com/Rohit-1920/EasyCRUD-Updated.git
```

## step 4. Database Setup & Configuration
Before the backend can start, the database must be reachable and the schema (table structure) must be created.
 ## 1.Accessing the Database
 First, log in to your MySQL/MariaDB instance using the terminal:

```bash
 mysql -h <your-database-endpoint> -u admin -p
```

 (Replace <your-database-endpoint> with your actual DB host IP or URL).

 ## 2.Creating the Schema
Run these commands to prepare the environment for the Student Application:

-- Create the dedicated database
```bash
CREATE DATABASE student_db;
```

-- Create a user and grant permissions
```bash
GRANT ALL PRIVILEGES ON student_db.* TO 'username'@'localhost' IDENTIFIED BY 'your_password';
```

-- Switch to the new database
```bash
USE student_db;
```

-- Create the Student table structure
```bash
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
) ENGINE=InnoDB AUTO_INCREMENT=80 DEFAULT CHARSET=latin1;
```

## step 5: BACKEND DEPLOYMENT (SPRING BOOT)
The backend acts as the intermediary between the user (Frontend) and the data (Database).
Configure Database Credentials
Before building the image, the backend needs to know where the database is located.

## Navigate to the backend directory:
```bash
cd backend
```
## Open the configuration file:
```bash
nano src/main/resources/application.properties
```
## Update the following bold values to match your Step 2 setup:
```bash
spring.datasource.url=jdbc:mariadb://<YOUR_DB_IP>:3306/student_db
spring.datasource.username=<YOUR_USER>
spring.datasource.password=<YOUR_PASSWORD>
```

## Build the Docker Image

This command reads the Dockerfile in the backend folder and creates an executable image named backend:v1.
```bash
docker build . -t backend:v1
```

## Run the Backend Container
```bash
docker run -d -p 8080:8080 --name backend-container backend:v1
```
-d: Runs the container in "Detached" mode (background).

-p 8080:8080: Maps port 8080 of the container to port 8080 of your host machine.

## step 6: FRONTEND DEPLOYMENT (REACT)
The frontend is built using React, a JavaScript library for building user interfaces.
Configure the Backend IP
The frontend needs to know exactly where the backend API is running.

## Navigate to the frontend directory:
```bash
cd frontend
```

## open or create the .env file:
```bash
nano .env
```
## Update the IP address to point to your Backend Server:
REACT_APP_API_URL=http://<YOUR_BACKEND_IP>:8080

## Build the Docker Image
```bash
docker build -t frontend:v1 .
```

## Run the Frontend Container
```bash
docker run -d -p 80:80 --name frontend-container frontend:v1
```
-p 80:80: This allows you to access the app by simply typing your IP into a browser without adding a port number.






















 
