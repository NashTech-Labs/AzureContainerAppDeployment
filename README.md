# Container App Deployment Template

This template provides a streamlined way to deploy a containerized application to Azure Container Apps using Azure Pipelines.

## Parameters

**imageToDeploy (type: string)**: The name of the Docker image to be deployed.<br>
**dockerImageTag (type: string)**: The tag of the Docker image. <br>
**azureSubscription (type: string)**: The name of the Azure subscription service connection. <br>
**resourceGroup (type: string)**: The name of the Azure Resource Group where the container app will be deployed. <br>
**containerAppName (type: string)**: The desired name for the Azure Container App. <br>

## Usage

To use this template, include the following YAML snippet in your Azure Pipelines:

```yaml
resources:
  repositories:
    - repository: exampleApp
      type: github
      name: GitHubUserName/repoName
      ref: 'respective-branch-name'            
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
Make sure to replace the placeholders (<...>) with your specific values.

## Steps

**Azure Container Apps Deployment:** This step utilizes the AzureContainerApps task to deploy the specified Docker image to Azure Container Apps.<br> It requires the Azure subscription, resource group, container app name, and the fully qualified image name with the specified tag.

```yaml
- task: AzureContainerApps@1
  inputs:
    azureSubscription: ${{ parameters.azureSubscription }}
    containerAppName: ${{ parameters.containerAppName }}
    resourceGroup: ${{ parameters.resourceGroup }}
    imageToDeploy: ${{ parameters.imageToDeploy }}:${{ parameters.dockerImageTag }}
```

## Notes

- Ensure that the necessary Azure service connection (**ServiceConnectionForgitHub**) is set up in your Azure Pipelines project.<br>
- Customize the repository and branch information in the resources section according to your GitHub repository setup.<br>

Adapt and extend this template to suit your specific deployment needs.
