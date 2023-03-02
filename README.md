# End to End MLOPS Project - Wine Quality Prediction  

## Table of Content
  * [Demo](#demo)
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Objectives and Key Features](#objectives-and-key-features)
  * [Dataset](#dataset)
  * [Installation](#installation)
  * [Deployement on Heroku](#deployement-on-heroku)
  * [Directory Tree](#directory-tree)
  * [Bug / Feature Request](#bug---feature-request)
  * [Technologies Used](#technologies-used)
  * [Credits](#credits)


## Demo
Link: [https://winequality.herokuapp.com/](https://winequality.herokuapp.com/)

[![](https://drive.google.com/uc?id=15YtHu0fg6ilhgAnEK1VpHidqv1g3udVW)](https://winequality.herokuapp.com/)


## Overview
This is a simple wine quality prediction website application trained base on Elastic Net algorithm. The trained model takes 11 features about wine as input (e.g Fixed acidity, Free sulfur dioxide etc.) and predict the quality of the wine with a score from 0 to 10. The main focus of the project is building an automated MLOPS pipelines. 

In addition, if you are interested in building this pipeline from scratch, please find the specification document to guide you through here. (https://github.com/dandi0220/-simple-dvc-demo/blob/main/Project_Manual.pdf)

## Motivation
I am very keen on improving my data science skills in MLOPS pipelines. Therefore I decided to produce this end to end MLOPS model on wine quality prediction. 

## Objectives and Key Features
The objective of this project is to implement an automated MLOPS pipelines as shown in the following diagram:
![image](https://drive.google.com/uc?id=1qXpcVaURkewln-X-uemR3JV-Ss2MXFhu)
- In order to achieve the goal, the following features are designed:

    - Version control of the code (by using git commit)
    - Data and model version control (by using DVC)
    - Create virtual environment to standardize the testing of the project (by using tox and pytest)
    - In the main branch, model is saved as a joblib file and reports of the parameters and metrics results are generated at /report in order to find the production model. In the main-mlflow branch, MLflow is being used to keep track of all the fine-tuning models results
    - Produce a web application to make the prediction of wine quality with flask on Heroku, and restrict the input values to specific range based on the training dataset
    - deployment of the pipeline by using MLflow and GitHub Actions

## Dataset

I have used Kaggle's [Red Wine Quality dataset](https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009) for this project.

The dataset is in csv format, and there are in total 1600 lines of data with 11 columns of input variables and 1 column of label variable. 

The quality of a wine is determined by 11 input variables:
- Fixed acidity
- Volatile acidity
- Citric acid
- Residual sugar
- Chlorides
- Free sulfur dioxide
- Total sulfur dioxide
- Density
- pH
- Sulfates
- Alcohol

And the quality of the wine is measured in the column 'TARGET' with a score from 0 to 10. 

## Installation
The Code is written in Python 3.7. If you don't have Python installed you can find it [here](https://www.python.org/downloads/). If you are using a lower version of Python you can upgrade using the pip package, ensuring you have the latest version of pip. To install the required packages and libraries, run this command in the project directory:

```bash
pip install -r requirements.txt
```

## Deployement on Heroku
    1. Create Procfile
    2. .Github/workflows/ci-cd.yaml is created for github actions and Heroku deployment
    3. In Heroku, create a new app, choose the deployment method as GitHub and fill in the linked GitHub repository name

![](https://drive.google.com/uc?id=1KXyGq4ZWAyRE5MN59poVjWVUpnSsQDO8)
![](https://drive.google.com/uc?id=1QN0JwLYqATXIxS6jciLH1MtrBGXGtMxu)

    4.Update the HEROKU_APP_NAME and HEROKU_API_TOKEN in github Actions secrets setting 

## Directory Tree 
```
├── .gitignore         <- programs to be ignored
├── app.py             <- python file to run the web app
├── dvc.yaml           <- run dvc command
├── params.yaml        <- parameters and file paths
├── procfile           <- specifies the commands that are executed by the app on
├── README.md          <- The top-level README for developers using this project.
├── requirements.txt   <- The requirements file for reproducing the analysis environment, 
│                         e.g. generated with `pip -r requirements.txt`
├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
├── template.py        <- To be used initially to create structure of the project   
├── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io
├── .github\workflows   	
│   ├── ci-cd.yaml     <- to build CI/CD workflows with GitHub Actions
├── .tox
├── artifacts          <- MLflow use
├── data
│   ├── processed      <- The final, canonical data sets for modeling.
│   │   └── .gitkeep
│   └── raw            <- The original, immutable data dump.
│       └── .gitkeep
├── data_given	       <- The original data source	
│   ├── .gitignore
│   ├── winequality.csv	
│   ├── winequality.csv.dvc <-dvc tracking of the csv file
├── notebooks          <- Jupyter notebooks. 
│   └── .gitkeep
├── prediction_service
│   └──model
│    └──model.joblib   <- saved model
│   ├── __init__.py
│   ├── prediction.py  <- functions defined for web application use
    ├── schema_in.json <- the restricted input feature value range is defined here
├── report            <- reports of parameters and metrics results of the model
│   └── params.json    <- model tuning parameters
│   └── scores.json    <- Model metrics result
├── saved_models       <- Trained and serialized models, model predictions, or model summaries
│   └── .gitkeep
├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
├── src                <- Source code for use in this project.
│   ├── .gitkeep
│   ├── __init__.py    <- Makes src a Python module
│   ├── get_data.py    <- source code to read params and process the data and return dataframe
│   ├── load_data.py   <- read the data from data source and save it in the data/raw for further process
│   ├── log_production_model.py  <- keep track of all the models on mlflow and rules defined to find the production model
│   ├── split_data.py  <- to split the train and test data before the model training stage
│   ├── train_and_evaluate.py    <- train and evaluate the model
├── tests                <- tests of functions for web app
│   ├── __init__.py     
│   ├── conftest.py
│   ├── schema_in.json
│   ├── test_config.py
├── webapp                <- webpage files 
│   └──static
│    └──css
│     └──main.css
│    └──scripts
│     └──index.js
│   └──templates
│    └──404.html
│    └──base.html
│    └──index.html

```

## Bug / Feature Request
If you find a bug (the website couldn't handle the query and / or gave undesired results), kindly open an issue [here](https://github.com/dandi0220/-simple-dvc-demo/issues/new) by including your search query and the expected result.

If you'd like to request a new function, feel free to do so by opening an issue [here](https://github.com/dandi0220/-simple-dvc-demo/issues/new). Please include sample queries and their corresponding results.

## Technologies Used
![](https://forthebadge.com/images/badges/made-with-python.svg)

[<img target="_blank" src="https://pandas.pydata.org/static/img/pandas.svg" width=200>](https://pandas.pydata.org/docs/)&ensp;&ensp;&ensp; [<img target="_blank" src="https://mlflow.org/docs/latest/_static/MLflow-logo-final-black.png" width=170>](https://mlflow.org/docs/latest/index.html)&ensp;&ensp;&ensp;[<img target="_blank" src="https://flask.palletsprojects.com/en/1.1.x/_images/flask-logo.png" width=170>](https://flask.palletsprojects.com/en/1.1.x/)&ensp;&ensp;&ensp; [<img target="_blank" src="https://number1.co.za/wp-content/uploads/2017/10/gunicorn_logo-300x85.png" width=280>](https://gunicorn.org) 

[<img target="_blank" src="https://tox.wiki/en/latest/_static/tox.svg" width=200>](https://tox.wiki/en/latest/index.html)&ensp;&ensp;&ensp; [<img target="_blank" src="https://scikit-learn.org/stable/_static/scikit-learn-logo-small.png" width=200 >](https://scikit-learn.org/stable/user_guide.html)&ensp;&ensp;&ensp; [<img target="_blank" src="https://cdn.iconscout.com/icon/free/png-512/heroku-11-1175214.png?f=avif&w=256" width=100>](https://devcenter.heroku.com/)&ensp;&ensp;&ensp; [<img target="_blank" src="https://repository-images.githubusercontent.com/135934107/7d1b9580-c328-11eb-931b-d46c26e29959" width=170>](https://dvc.org/)&ensp;&ensp;&ensp; [<img target="_blank" src="https://upload.wikimedia.org/wikipedia/commons/b/ba/Pytest_logo.svg" width=170>](https://docs.pytest.org/en/7.2.x/) 

## Credits
- The webiste html source code is based on Mr SUNNY BHAVEEN CHANDRA's tutorial on youtube.https://www.youtube.com/watch?v=-KmOlVSEKWg


