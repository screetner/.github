# Screetner Organization

Welcome to the Screetner project! Screetner is an end-to-end system designed to assist local governments in scanning and identifying assets using video recordings from mobile devices. The project consists of several repositories, each serving a specific purpose within the overall architecture.

## Project Repositories

| Repository Name        | Description                                                                    |
| ---------------------- | ------------------------------------------------------------------------------ |
| **scn-mobile-app**     | Mobile application for capturing video recordings and uploading data.          |
| **scn-elysia-backend** | Backend service providing APIs, authentication, and data management.           |
| **scn-next-frontend**  | Frontend web application for data visualization and system management.         |
| **scn-detection**      | Object detection and analysis service using YOLOv8 model.                      |
| **scn-logs**           | Centralized logging service to manage and monitor application logs.            |
| **scn-tusd-server**    | Upload server to handle large file uploads with support for resumable uploads. |

# Deployment

This project's deployment is divided into three main parts:

- Backend Services
- Frontend Website
- Azure Cloud Services
- Mobile Application

## Backend Services

The Git repository named `scn-deployment` contains docker compose files for each necessary component. Each docker compose file needs to have its image name and environment variables configured. If you need to build an image for any of these services, go to the specific repository and read the `Readme.md` file for build instructions.

### Required Backend Services

- kong-gw: API gateway between `main service` and `log service`. You need to configure this based on your custom configuration in the docker compose file.
- scn-logs: Logging service for this project
- scn-main-backend: Main service for this project
- tusd-server: Resumable upload service for mobile applications to upload files to the cloud

## Frontend Website

The website is built using NextJs 14. Our repository doesn't include a `Dockerfile` as we use Heroku for frontend deployment. If you need to build your own image, you'll need to create a `Dockerfile` yourself to build the Frontend website.

## Azure Cloud Services

This project uses several Azure Cloud services. You need to create all of the following to make the project run properly:

- Azure Blob Storage: Used to store video files uploaded from mobile devices through the Tusd-Server
- Azure Logic App: Used for auto-scaling processing units
- Azure Communication Service: Used to send emails to users

After creating these components, you'll need to gather certain secret values and add them to the ENV file for the backend services, such as `Access token for Blob`, `API Endpoint to request create processing unit in Logic App`, and `Token to send email`.

For Azure Logic App, you'll need to create a workflow for auto-scaling processing units. We've created a workflow for you, which can be found in the repository `scn-detection` on the `logic app` branch. You can copy and paste this workflow into your Azure service.

## Mobile Application

## Videos for deployment step
