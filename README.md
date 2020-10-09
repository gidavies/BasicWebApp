# BasicWebApp
A basic web application to demonstrate release pipelines in Azure DevOps.

This repo includes a simple .NET Core Web App together with a pipeline definition YAML file to show:

- Continuous Integration, set to trigger when the main branch is updated.
- Continuous Deployment to Azure, includiing provisioning a dev, test and production instance of an Azure App Service (Free Tier) and then deploying the web app into those.
- Tasks to check accessibility standards are being met in the web pages.
