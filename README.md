# Container App Deployment Template

This template provides a streamlined way to deploy a containerized application to Azure Container Apps using Azure Pipelines.

## Parameters

imageToDeploy (type: string): The name of the Docker image to be deployed.
dockerImageTag (type: string): The tag of the Docker image.
azureSubscription (type: string): The name of the Azure subscription service connection.
resourceGroup (type: string): The name of the Azure Resource Group where the container app will be deployed.
containerAppName (type: string): The desired name for the Azure Container App.
