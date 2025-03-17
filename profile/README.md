# Screetner Organization

Welcome to the Screetner project! Screetner is an end-to-end system designed to assist local governments in scanning and identifying assets using video recordings from mobile devices. The project consists of several repositories, each serving a specific purpose within the overall architecture.

## Project Repositories

| Repository Name       | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **scn-mobile-app**    | Mobile application for capturing video recordings and uploading data.       |
| **scn-elysia-backend**| Backend service providing APIs, authentication, and data management.        |
| **scn-next-frontend** | Frontend web application for data visualization and system management.      |
| **scn-detection**     | Object detection and analysis service using YOLOv8 model.                   |
| **scn-logs**          | Centralized logging service to manage and monitor application logs.         |
| **scn-tusd-server**   | Upload server to handle large file uploads with support for resumable uploads.|

# Deployment

In this project was divied deployment into three main part.
- Backend Services
- Frontend WebSite
- Azure Cloud Services
- Mobile Application

## Backend Services

Enter Git repository name `scn-deployment` insite that will contain docker compose file each component that nesessary to use. each docker compose file need to be changed an image name and EVN, so that If you need to build that image for each docker compose services you need to go to that repository services that you want then read `Readme.md` file to build that service.

### What Backend Services thtat needed
- kong-gw : using for API gateway between `main service` and `log service` you need config them by yourself base on because it base on your custom configguration of docker compose file.
- scn-logs : logs service for this project
- scn-main-backend : main service for this project
- tusd-server : resumeable uplaod service for mobile aplication to upload file to cloud

## Frontend WebSite

For the website as you know this project build an website using NextJs 14. but in our repository doen't has any `Dockerfile` to build an image because we use other deploy service for frontend call `Heroku`, so that will make you can't build you own image If you need that you can create `DockerFile` by your self to try to build this Frontend wesite.

# Azure Cloud Services

This project use many Azure Cloud services for each part that needed you need to create all of this that I listed to you to make this project run properly
- Azure Blob Storage : using for store videos file that upload from mobile through Tusd-Server
- Azure Logic App : To auto scaling processing unit
- Azure Communication Service : to send an email to user

After create all of these compoenent you need to grap some secret value then fill it on ENV file for some backend service such `Access token for Blob` , `API Endpoint to request create processing unit in Logic App`, `Token to send email`.

For Azure Logic App after you created that you need to create an workflow of auto scaling processing unit, by the way I also created that workflow for you, you can see it on repository name `scn-detection : branch logic app` then you can copy and paste it on azure service to create an workflow.

## Mobile Application

# Videos for deployment step
