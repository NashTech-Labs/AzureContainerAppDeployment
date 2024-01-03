# Container App Deployment Template

This template provides a streamlined way to deploy a containerized application to Azure Container Apps using Azure Pipelines.

## Parameters

**imageToDeploy (type: string)**: The name of the Docker image to be deployed.<br>
**dockerImageTag (type: string)**: The tag of the Docker image. <br>
**azureSubscription (type: string)**: The name of the Azure subscription service connection. <br>
**resourceGroup (type: string)**: The name of the Azure Resource Group where the container app will be deployed. <br>
**containerAppName (type: string)**: The desired name for the Azure Container App. <br>

## Usage

```yaml
resources:
  repositories:
    - repository: exampleApp
      type: github
      name: GitHubUserName/repoName
      ref: 'respective-branch-name'            //branch where your template exists
      endpoint: 'ServiceConnectionForgitHub'
 
jobs:
  - job: Deployment
    steps:
    - template: path/to/your/template/containerAppTemplate.yml@exampleApp
      parameters:
        imageToDeploy: <your docker image name>
        dockerImageTag: <tag of docker image>
        azureSubscription: <azure subscription service connection>
        resourceGroup: <name of resource group of container app>
        containerAppName: <your container app name>
```
