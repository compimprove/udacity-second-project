# Overview

[![Python application](https://github.com/compimprove/udacity-second-project/actions/workflows/python-app.yml/badge.svg)](https://github.com/compimprove/udacity-second-project/actions/workflows/python-app.yml)

This is a Python flask application built for predicting housing prices in Boston. The purpose of this project was to build the Continuous Integration with Github Actions and Continuous Delivery with Azure Pipelines.

## Project Plan

Trello board:
https://trello.com/b/y0hQygX6/flask-ml-project

Project plan:
https://docs.google.com/spreadsheets/d/1RXGPpRsCIVKpKzjdlAmtzqkob6O6YIhufm-Th8IdugM/edit?usp=sharing


## Instructions

![Architectural Diagram](image/Azure%20CI_CD.jpg)

### Fork this project to your personal github account
### Clone it to Azure Cloud Shell
Open your Azure Cloud Shell and clone this project
![Clone project](image/clone%20udacity%20second.png)
### Create python virtual environment and source it
Running these commands in Azure Cloud Shell 
```
python3 -m venv ~/.<your-clone-repo-name>
source ~/.<your-clone-repo-name>/bin/activate
```
### Passing the test
Next, you'll run the `make all` command in your repo to install dependencies and validate your code passing linting and testing
![Testing](image/testing.png)

### Deploy the app to Azure App Service
After passing the test, you want to deploy the application to the Azure App Service. Let's run this command
`az webapp up -g <your-resource-group-name> -n <your-webapp-name`
The result will be like this
![Deploying](image/deploy%20to%20azure%20app%20service.png)
Navigate to the home page of the application, you'll see this
![Testing](image/homepage-az-webapp-deploy.png)


### Build Azure Pipeline for automatic deployment
1. Create your Azure Devops Organization if you didn't have yet.
2. Create a new project
3. Create a new Pipeline, select the forked project in your github account, config it as Python to Linux Web App on Azure and run the pipeline. For more detail about creating the Azure Pipeline for Python Webapp, read the official documentation [here](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops).

![Build pipeline](image/build%20pipeline.png)

4. After build the pipeline successfully, check the app service and home page again to validate it's working

![App Service](image/app%20service.png)

![Validate again](image/validate_again.png)

5. Change your app name in [this file](make_predict_azure_app.sh), and execute it to see the prediction result

![Prediction Result](image/make_prediction.png)

### Check the stream log
Running `az webapp log tail`, you'll see the stream log of the application
![Testing](image/log%20tail.png)

## Enhancements

In the future, this project can extend to use docker container in Azure Container Instances, adding the UI for easy of use, or adding test to the pipeline to make sure the application working properly.

## Demo 

https://youtu.be/kAb7Nr3Oduw


