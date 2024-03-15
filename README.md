# Azure-Databricks-MLflow-Server
## Table of Contents
- [Project Description](#project-description)
- [Dependencies](#dependencies)
- [Installation](#installation)
- [Code Structure](#code-structure)
- [Key Features](#key-features)
- [Acknowledgments](#acknowledgments)

## Project Description
Using Azure Databricks, I registered an ML model to an MLflow model registry and deployed the model into production with CI/CD pipeline using Databricks Workflow. The Workflow includes scheduled jobs that re-run weekly EDA on the latest data, re-train a new batch of models, and test the server endpoint of the 
current model in production.

The weekly training batch returns 50 regression models with evaluation metrics, trained on the Kaggle train/test dataset with 80 features from the ongoing Housing Prices competition.  

The next step is to implement an infrastructure-as-code pipeline using Azure Pipelines from an Azure DevOps repository, where as so far this project represents an initial prototype for rapid training, deployment and reiteration. There are also more opportunities for automation which goes hand-in-hand with growing the codebase grows and reducing reliance on low-code infrastructure.

## Dependencies
The required dependencies are pre-installed in a regular Databricks workspace.

## Installation
In some Databricks Python notebooks, the mlflow module must be installed using `!pip install mlflow` in the code of the notebook before the module is called.

## Code Structure
[Explanation of the code structure and logic, with code snippets as examples]

## Key Features
[List of key features, with explanations and screenshots or GIFs]

## Acknowledgments
Thanks to Zach Spain, Steven Sprott, and the rest of the Databricks Team for inspiring me to get started with Databricks, and for your ongoing support.

Also thanks to Arne Arnesen and the Snowflake Team for inspiring me to explore the cloud more thoroughly which helped me realize how fun and easy it is to explore different cloud features.

Abhishek Gupta and the Microsoft Capacity Team provided excellent support when I need to scale my cloud computing cluster.
