# BasicWebApp
A basic web application to demonstrate release pipelines in Azure DevOps.

This repo includes a simple .NET Core Web App together with a pipeline definition YAML file to show:

- Continuous Integration, set to trigger when the main branch is updated.
- Continuous Deployment to Azure, includiing provisioning a dev, test and production instance of an Azure App Service (Free Tier) and then deploying the web app into those.
- Tasks to check accessibility standards are being met in the web pages.

## Instructions

### Create an Azure resource group

Create a new resource group via the Azure Portal or Azure CLI:

```cmd
az group create --name mynewresourcegroup-rg --location uksouth
```
### Create a new Azure DevOps Project

Ensure that the version control type is git.

### Add a service connection

In the Azure DevOps project:
- Select the project settings cog in the bottom left corner. 
- Add a new service connection.
- Select the Azure Resource Manager option.
- Select Service principal (automatic).
- Select the subscription and resource group you created above.
- Give the service connection a name and remember/copy the name.

### Import this git repo into the project

In Azure DevOps, select repos and then import a repo. Enter the url for this repo [https://github.com/gidavies/BasicWebApp.git](https://github.com/gidavies/BasicWebApp.git).

### Configure the pipelines.yaml file

In Azure DevOps, select pipelines and add the existing pipeline.yaml file from the imported project (i.e. choose the Azure Repos option). Edit the variables at the top of the yaml file to set:

- Change AppResourceGroup: 'BasicWebAppRG' to the resource group you created above.
- Edit AzureSub: 'SERVICECONNECTIONNAME' to use the name of the service connection you created above. 
- Customise WebAppNameRoot: 'BasicWebApp' to a unique value that will be used as the URL (e.g. basicwebapp.azurewebsites.net). Add your initials and/or date for example to reduce the chance of a clash.

That's it - now save the yaml file, which will trigger the pipeline. The web app will be built and then there will be an accessibility error deploying to the dev environment.