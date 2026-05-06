# React Project Setup and Deployment Guide for Windows

This guide provides step-by-step instructions for setting up a React project.

## 1. Go to Frontend

```shell
cd Easycrud/frontend/
```


## 2. edit .env file

To edit the following file, run the following command:

```shell
nano .env
```
change the ip address

## 3. Build docker image

**Build Docker Image**

```bash
docker build -t frontend:v1 
```

## 4. Create container from the docker image

```shell
docker run -d -p 80:80 --name frontend frontend:v1
```

You can access the application on http://localhost:80
