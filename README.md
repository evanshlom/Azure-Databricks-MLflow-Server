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

The next step is to implement an infrastructure-as-code pipeline using Azure Pipelines from an Azure DevOps repository, where as so far this project represents an initial prototype for rapid training, deployment and reiteration. There are also more opportunities for automation which goes hand-in-hand with growing the codebase and reducing reliance on low-code infrastructure.

## Dependencies
The required dependencies are pre-installed in a regular Databricks workspace.

## Installation
In some Databricks Python notebooks, the mlflow module must be installed using `!pip install mlflow` in the code of the notebook before the module is called.

## Code Structure
```
Azure-Databricks-MLflow-Server
├── mlruns/0/
│   ├── meta.yaml
├── model/
│   ├── model_MLmodel.json
│   ├── model_conda.yaml
│   ├── model_input_example.json
│   ├── model_model.pkl
│   ├── model_python_env.yaml
│   ├── model_requirements.txt
├── notebooks/
│   ├── Routine-Test-Endpoint-Model-HousingPrices-v4.ipynb
│   ├── data_exploration_notebook.ipynb
│   ├── model_highest_performance_notebook.ipynb
│   ├── model_training_notebook.ipynb
├── scheduled_workflows/
│   ├── Routine-Test-Endpoint-Model-HousingPrices-v4.ipynb
│   ├── ...
├── server/test/
│   ├── model_endpoint_test1_result.csv
│   ├── query.py
│   ├── request.json
├── README.md
└── estimator.html
```

## Key Features
In the `model` folder, you can see the artifacts from the deployed model. After training an initial batch of XGBoost models, I chose this model for multiple model scoring metrics (MAPE and F1 scores) and registered it to the model registry which saved the model artifacts.

In the `notebooks` folder, you can see the training notebook for the highest performing model from the initial training batch. Additionally, you can see the scheduled Python notebooks. I am planning to post the EDA and Training notebooks (2) to the scheduled_workflows folder after I solve workflow automation bugs for those two notebooks. The Test Endpoint notebook is running live and you can find the same notebook in the `scheduled_workflows` folder.

In the `server/test` folder, you can see the results from the first model endpoint test. I used the test dataset in an API call, and the model returned reasonable predictions through the server endpoint.

## Acknowledgments
Thanks to Zach Spain, Steven Sprott, and the rest of the Databricks Team for inspiring me to get started with Databricks, and for your ongoing support.

Also thanks to Arne Arnesen and the Snowflake Team for inspiring me to explore the cloud more thoroughly which helped me realize how fun and easy it is to explore different cloud features.

Abhishek Gupta and the Microsoft Capacity Team provided excellent support when I need to scale my cloud computing cluster.
