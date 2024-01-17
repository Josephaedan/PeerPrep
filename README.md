![image](https://github.com/Josephaedan/PeerPrep/assets/48595194/fdf7e4da-5a48-4cb9-8244-2d7edfc99e12)


# PeerPrep

PeerPrep is a collaborative coding platform for users to communicate and collaborate together on Data Structures and Algorithms Interview Questions with a real-time collaboration environment. It is built with a Microservices Architecture for the backend and developed as part of the [CS3219 Software Engineering Principles and Patterns](https://nusmods.com/courses/CS3219/software-engineering-principles-and-patterns) module from NUS. This project was built and developed by:
- [Joseph Aedan Marcus](https://github.com/Josephaedan)
- [Rayner Loh Jian Ming](https://github.com/raynerljm)
- [Zechary Au Jun Wen](https://github.com/zechajw)
- [Shem Maleriado Limos](https://github.com/sheimoria)
- [Joel Wong Jun Yong](https://github.com/joelwongjy)

## Joseph Aedan Marcus's Contributions

- **Question Service Scraper (`/backend/question-service/lambda`):** Developed a web scraper lambda function that would scrape Leetcode for its questions as a CRON job.
- **Question Service Server (`/backend/question-service/server`):** Developed a FastAPI server that serves Leetcode questions through HTTP endpoints, allowing for CRUD operations and pagination.
- **Communication Service (`/backend/communication-service`):** Developed the Communication Service, an ExpressJS application that allows users to communicate with one another in real-time via a chat function using Websockets
- **PeerPrep UI (`/frontend`):** Developed features and UI elements on the frontend to serve users.

## 1. Instructions to set up the services for local development

- To run all the services together, please follow the setup instructions for ALL the services.
- **This is needed to run the assignments as well.** (To view specific instructions for assignments, view the `ASSIGNMENTS.md` file in the root of the project)

### 1.1. Frontend (`/frontend`)

1. In the `/frontend/app` directory, copy the `.env.example` file and rename it to `.env.development`
   - For any missing env vars, check with the team to retrieve the secrets from the vault

### 1.2. API Gateway (`/backend/api-gateway`)

1. In the `/backend/api-gateway/app` directory, copy the `.env.example` file and rename it to `.env.development`
   - For any missing env vars, check with the team to retrieve the secrets from the vault

### 1.3. User service (`/backend/user-service`)

1. In the `/backend/user-service/app` directory, copy the `.env.example` file and rename it to `.env.development`
   - For any missing env vars, check with the team to retrieve the secrets from the vault

### 1.4. Question service (`/backend/question-service/server`)

1. In the `/backend/question-service/server/app` directory, copy the `.env.example` file and rename it to `.env.development`
   - For any missing env vars, check with the team to retrieve the secrets from the vault

### 1.5. Matching service (`/backend/matching-service`)

1. In the `/backend/matching-service/app` directory, copy the `.env.example` file and rename it to `.env.development`
   - For any missing env vars, check with the team to retrieve the secrets from the vault

### 1.6. Collaboration service (`/backend/collaboration-service`)

1. In the `/backend/collaboration-service/app` directory, copy the `.env.example` file and rename it to `.env.development`
   - For any missing env vars, check with the team to retrieve the secrets from the vault

### 1.7. Communication service (`/backend/communication-service`)

1. In the `/backend/communication-service/app` directory, copy the `.env.example` file and rename it to `.env.development`
   - For any missing env vars, check with the team to retrieve the secrets from the vault

## 2. Instructions to run services locally

### Pre-requisites

- Ensure you have Docker Desktop (>= v4.22.2) installed (https://docs.docker.com/desktop/install/mac-install/)
- Ensure you have followed the instructions above to setup the services for local development

### 2.1 To run all the services at the same time

1. In the root of the project, run `docker compose up`
2. Visit the following endpoints for the respective services
   - Frontend: http://localhost:8000
   - API gateway service: http://localhost:8001
   - Users service: http://localhost:8002
   - Questions service: http://localhost:8003
   - Matching service: http://localhost:8004
   - Collaboration service: http://localhost:8005
   - Communication service: http://localhost:8006

### Known issues

- Installing new dependencies causes the Docker image to not build properly. If this happens, run `docker compose down` and then `docker compose up --build` again.

## 3. Instructions to deploy services to AWS locally

- You should not have to do this as the GitHub actions will automatically deploy your changes to AWS
- However, if you do have a need to test deployment from locally quickly without having to wait for the GitHub actions to run, you can follow the instructions below

### Pre-requisites

- Ensure you have completed the instructions above to set up the services for local development
- [Install and setup Pulumi](https://www.pulumi.com/docs/clouds/aws/get-started/begin/)

### 3.1. Instructions

1. Move to infra directory of the service you want to deploy (e.g. `/<service>/infra` directory)
2. Ensure you are on the stack you want to test a deploy from (it should usually be `staging`)
   - You can verify this by running `pulumi stack`
   - If you are not on the right stack, run `pulumi stack select <stack-name>` to switch to the right stack
3. Run `pulumi up` to preview the changes and then deploy them

## 4. Instructions to create your own service

- Please refer to the [README.md](./backend/template-service/README.md) in the `/backend/template-service` directory for instructions to create your own service
