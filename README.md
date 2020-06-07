
[![Build Status](https://travis-ci.com/ruhulamingp/udagram-capstone.svg?branch=master)](https://travis-ci.com/ruhulamingp/udagram-capstone)

# GitHub Repository Link:

https://github.com/ruhulamingp/udagram-capstone

# Application Link:

http://capston-todo.s3-website.us-east-1.amazonaws.com/

# Project Proposal & Approaches:

The idea is to build a simple serverless application by utilizing my combined learning methodology from this nano-degree program.

1. Servrless technology has been used to build the backend using AWS Lambda
2. The client has been built on React Application
3. Create an application build and host it on a static website inside AWS S3 bucket
4. Build and deployed to AWS using TravisCI on each push. A .travis.yml is located at the root of the project
5. The Jenkinsfile is located at the project root. This can be configured to be built and deployed on each commit/ pull request using github hooks.
6. Build process can be configured for multiple environments e.g dev, uat, prod etc. But for the simplicity, here one environment has been demonstrated

# Functionality of the application

This application will allow CRUD actions. Each TODO item can optionally have an attachment image. Each user only has access to TODO items associated to the creator.

# Backend

The backend folder contains the AWS lamda functions which provide the Serverless Todo API. 

It is built and deployed to AWS using TravisCI on each push. .travis.yml is located at the root of the project

# Endpoints

- GET - https://{{apiid}}.execute-api.us-east-1.amazonaws.com/dev/todos
- POST - https://{{apiid}}.execute-api.us-east-1.amazonaws.com/dev/todos
- PATCH - https://{{apiid}}.execute-api.us-east-1.amazonaws.com/dev/todos/{todoId}
- PUT - https://{{apiid}}.execute-api.us-east-1.amazonaws.com/dev/todos/{todoId}
- DELETE - https://{{apiid}}.execute-api.us-east-1.amazonaws.com/dev/todos/{todoId}
- POST - https://{{apiid}}.execute-api.us-east-1.amazonaws.com/dev/todos/{todoId}/attachment
	
# Frontend

The client folder contains a web application that can uses the API for Serverless Todo.

The Jenkinsfile is located at the project root. This can be configured to be built and deployed on each commit/ pull request using github hooks.

# Authentication

Here auth0 has been used for authentication purpose

# How to run the application

# Backend

To deploy an application we need to run the following commands:

```
cd backend
npm install
sls deploy -v
```

# Frontend

To run a client application first you need to edit the client/src/config.ts file to set the correct parameters. And then run the following commands:

```
cd client
npm install
npm run start
```

This should start a development server with the React application that will interact with the serverless TODO application.

## CI/CD

Here we have added jenkins file which contains stages of deploying frontend app in S3.
