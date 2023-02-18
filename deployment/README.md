> # Hosting a Full-Stack Application Documentation

> ## Preparing Source Code Infrastructure For Deployment

- No environment variables that change from the development environment and production are present in the source code.
- A central configuration file is used in order to set the environment variables and make them available to the code and it lives [here](../udagram-api/src/config/config.ts).
- No authentication strings are hard-coded in the source code.
- A project-level package.json file contains All the necessary scripts for installing, building, testing, deploying both the frontend and the backend is added and it lives [here](../package.json).
- Screenshots of the AWS console indicate that RDS, EB and S3 are properly set up are available here [here](./AWS/).
- The app is accessible via [this link](http://myawsbucket7777777.s3-website-us-east-1.amazonaws.com).


> ## Configuring Continuous Integration Pipeline with Github
- I linked the Udagram project in github to circleci and added the `config.yml` file of the circleci containing all the orbs, jobs and workflows for running the pipeline automatically after every commit on the master branch.

> ## Diagrams
- The submission contains a simple diagram giving a high-level and another diagram showing overview of the pipeline. The diagram Includes the different AWS services used for hosting the DB, API and
UI, A representation of the communication between the services is present in the diagrams (ex: arrows between services).

> ## Pipeline Process Inside Circleci.
### Continuous integration:
- The scripts needed for installing, testing and building the frontend and backend of the application are found in the package.json files in `udagram-api & udagram-frontend` folders.
- The scripts are called in the project-level package.json.
- Jobs are added in the `.circleci/config.yml` file for running these scripts in the following order:-
  - install frontend
  - install backend
  - build backend
  - build backend
  - test frontend
  - test backend

### Continuous Deployment:
- The scripts needed for deploying the frontend and backend of the application are found in the package.json files in `udagram-api & udagram-frontend` folders.
- The scripts are called in the project-level package.json.
- Jobs are added in the `.circleci/config.yml` file for running these scripts in the following order:-
  - deploy frontend
  - deploy backend

> ## Used Amazon Web Services
- `RDS` to create a postgreSQL database.
- `EB` to run a server and create a production Application and link it with the production environment and host the backend files.
  - I have added the environment variables in the production environment.
  - I have linked the database with the backend.
  - I have linked the backend with the frontend.
- `S3` to create a bucket for hosting the frontend files.