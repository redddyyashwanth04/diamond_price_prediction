# Diamond Price Prediction Web App

A Python-based machine learning project for predicting diamond prices using a Flask web application. The project includes an end-to-end pipeline for data ingestion, preprocessing, model training, model evaluation, artifact storage, and a browser-based prediction form.

## Project Overview

This repository implements a diamond price prediction system using scikit-learn models and a Flask user interface. It covers:
- data ingestion and train/test split
- feature transformation with ordinal encoding and scaling
- training multiple regression models
- selecting the best model by R² score
- logging evaluation metrics with MLflow
- serving predictions through a simple web interface

## Key Features

- Diamond price prediction from carat, depth, table, dimensions, cut, color, and clarity
- Data transformation pipeline with ordinal encoding and standard scaling
- Model training support for Linear Regression, Lasso, Ridge, and ElasticNet
- MLflow logging for model metrics and experiment tracking
- Flask web UI for entering diamond attributes and viewing predicted price

## Tech Stack

- Python
- Flask
- pandas
- numpy
- scikit-learn
- MLflow
- XGBoost (listed in requirements)

## Repository Structure

- `app.py` - Flask application entry point for serving the prediction interface
- `src/components/` - pipeline components
  - `data_ingestion.py` - ingest and split diamond dataset
  - `data_transformation.py` - preprocess numeric and categorical features
  - `model_trainer.py` - train and select the best regression model
  - `model_evaluation.py` - evaluate the trained model and log metrics
- `src/pipelines/`
  - `train_pipeline.py` - orchestrates the full training workflow
  - `predict_pipeline.py` - loads artifacts and performs prediction
- `src/utils/utils.py` - helper utilities for saving/loading artifacts and model evaluation
- `src/logger/logging.py` - logging setup
- `src/exception/exception.py` - custom exception handling
- `artifacts/` - output folder for `raw.csv`, `train.csv`, `test.csv`, `preprocessor.pkl`, and `model.pkl`
- `templates/` - Flask UI templates: `index.html`, `form.html`, `result.html`
- `requirements.txt` - runtime dependencies
- `requirements_dev.txt` - development dependencies

## Setup

1. Clone the repository:
   ```bash
   git clone <repo-url>
   cd learn_mlops
   ```

2. Create a Python environment and install dependencies:
   ```bash
   python -m venv venv
   venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. Ensure the diamond dataset is available.

   The current data ingestion step reads from a hard-coded local path:
   `C://Users//yashw//Downloads//archive (6)//Diamonds Prices2022.csv`.
   Update `src/components/data_ingestion.py` to point to a local CSV path if needed.

## Training the Model

Run the training pipeline to ingest data, preprocess features, train models, and save artifacts:

```bash
python src/pipelines/train_pipeline.py
```

This creates the following artifacts under `artifacts/`:
- `raw.csv`
- `train.csv`
- `test.csv`
- `preprocessor.pkl`
- `model.pkl`

## Running the Web App

Start the Flask web server:

```bash
python app.py
```

Open your browser at:

```text
http://0.0.0.0:8000/
```

Use the form to enter diamond attributes and receive a predicted price.

## Notes

- If `app.py` fails because artifacts are missing, run the training pipeline first.
- The current project expects a diamonds dataset CSV in a local path. Update `src/components/data_ingestion.py` to use a dataset file available in your environment.
- MLflow is configured to log metrics. The default tracking URI is the local MLflow file store.

## Suggested GitHub Description

Diamond price prediction app using Flask, scikit-learn, and MLflow with an end-to-end training pipeline and web-based prediction interface.

## Suggested GitHub Topics

`diamond-price-prediction`, `machine-learning`, `flask`, `scikit-learn`, `mlflow`, `python`, `data-science`, `regression`
