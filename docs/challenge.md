# Exploration Review

During the review of the DS exploration, it became evident that certain key elements were missing in the creation process. To rectify this, I added the necessary dummies. However, upon running the feature importance analysis, it was observed that these additions did not rank among the most crucial features.

Upon evaluating the scoring values of various models, it was noted that both logistic regression and XGBoost, when balanced and utilizing the most representative features, demonstrated similar performance metrics. However, the F1 score indicated a slightly superior performance for XGBoost, leading to its selection as the preferred model.

## Model Operationalization

For operationalizing the model, I developed a 'pre_process' class to encompass all essential functions required for processing the features to be used in training and prediction.

- `preprocess`: This function prepares the data for either training or prediction. It accepts a DataFrame, along with the selected "target" value, and returns a tuple with both values or just the prepared DataFrame.

- `fit`: Using the processed DataFrame, this function trains the model to identify the best features and subsequently retrains it for improved scoring.

- `predict`: This function employs the preprocessed DataFrame and exclusively utilizes the top X features selected for the best model.

## Model Testing

In the testing phase, modifications were made concerning validation. I introduced a function that always searches for the best X features when fitted, ensuring flexibility in feature selection instead of being confined to a specific set.

## FastAPI Endpoints

- `GET /health`: Provides information on whether the model is trained and ready to generate predictions.

- `GET /train`: Trains the model using all available data from the files.

- `POST /predict`: If the model is trained, this endpoint offers predictions for the entered values.
