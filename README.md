# Optimizing an ML Pipeline in Azure
Part of the Udacity Azure ML Nanodegree 🧠

## Summary
💸 The dataset used is related to bank marketing. It contains data about respondents to marketing phone calls, and whether or not they accepted an offer for a deposit.

📊 The presented task is binary classification, where we aim to predict whether a person would accept a deposit offer, being given its profile.

⚙ The best performing model for this task was a voting ensemble classifier, consisting of multiple gradient-boosted tree-based classifiers, with an accuracy of 0.9166.

## Scikit-learn Pipeline
🧠 For the Scikit-Learn part of the pipeline, the chosen estimator was a simple **logistic regressor**, and its hyperparmeters were tuned using HyperDrive. The two hyperparameters were **C** (the inverse of the regularization strenght), and **max_iter** (the number of maximum gradient iterations).  

🏃‍♂️ A random parameter sampling method is faster than a grid search, and yields a similar best selection of hyperparameters in a fracion of time compared to the grid search.

🤚 Bandit early-stopping policy stops a model training if its accuracy is not within the specified slack factor/amount when compared to the best performing model.

## AutoML
⚗️ The pipelines used in the AutoML experiments included two steps, usually a preprocessor and an estimator.
  * Preprocessors: MaxAbsScaler, SparseNormalizer, StandardScalerWrapper, etc.
  * Estimators: Usually gradient-boosted tree-based classifiers (XGBoost, LightGBM, Random Forests), ensemble methods, but also Logistic Regression. 
More details about the parameters for the AutoML run can be found [here](https://gist.github.com/radandreicristian/c42bda8e0b60320162ac7bda38edd399), and the according documentation can be foudn [here](https://docs.microsoft.com/en-us/python/api/azureml-train-automl-client/azureml.train.automl.automlconfig.automlconfig).

## Pipeline comparison
🧪 The test accuracies reported by the two pipelines are:
  * **0.9094** for Logistic Regression after hyperparameter tuning.
  * **0.9174** for the Voting Ensemble classifier selected by AutoML.

🌳 Tree-based models are known to be state-of-the-art for many datasets, and this one was no exception. These models are more advanced and complex, and are able to capture better dependencies and relationships between variables.

## Future work
📈 As the model part of the task has been optimized (selected best model, performed cross-validation), it is likely that in order to further improve the performance the data needs to be improved. This can be done either by adding more data, feature engineering, selection. Adding more data could help the model generalize more and avoid overfitting, which generally increases performance, while feature engineering and selection could provide better variables for classification.
