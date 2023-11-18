# ML Pipeline Steps
In this project, we will be using a dataset containing bone marrow transplantation characteristics for pediatric patients from UCI’s Machine Learning Repository.

We will use the dataset (http://archive.ics.uci.edu/ml/machine-learning-databases/abalone/abalone.data), to build a pipeline, containing all preprocessing and data cleaning steps, and then select the best classifier to predict patient survival.

## 1. Preprocessing 

### (a). Numeric Data Cleaning 
#### Output:

pipeline_arr == scaled_tx_arr : True

|pipeline_arr_med - scaled_tx_arr_med| = 43.36075966952346
  
### (b). Categorical Data Cleaning 
#### Output:

pipeline_arr == scaled_tx_arr : True      

### (c). Column Transformer -> numerical & categorical

#### Preprocess transformer to training data: 

 ColumnTransformer(transformers=[('num_preprocess',
                                 Pipeline(steps=[('imputer', SimpleImputer()),
                                                 ('scale', StandardScaler())]),
                                 Index(['length', 'diam', 'height', 'whole', 'shucked', 'viscera', 'shell'], dtype='object')),
                                ('cat_preprocess',
                                 Pipeline(steps=[('imputer',
                                                  SimpleImputer(strategy='most_frequent')),
                                                 ('ohe',
                                                  OneHotEncoder(drop='first',
                                                                sparse=False))]),
                                 Index(['sex'], dtype='object'))])

### Store transformed test data: 

  [[ 0.20638521  0.15779273  0.35112392 ...  0.68293021  0.
   1.] [-0.21953343 -0.10120617 -0.47557388 ... -0.34880017  1.
   0.] [ 0.8026713   0.72759029  0.35112392 ...  0.55533104  0.
   1.] ...[-0.2621253  -0.10120617 -0.47557388 ... -0.37432     0.
   1.] [ 0.97303876  1.03838897  0.70542298 ...  1.22249238  0.
   1.] [ 0.67489571  0.67579052  0.58732329 ...  0.84334058  0.
   0.]]

## 2. Adding Linear Regression Model

#### Output: R^2 score

pipeline score: 0.4879020616816332

sklearn metric: 0.4879020616816332

## 3. Hyperparameter Tuning GridSearchCV:

#### Output: best_score_, best_params_

GridSearchCV best score: -5.409647741106873

GridSearchCV best params: {'regr__fit_intercept': True}

## 4. Final Pipeline:

#### Output: best_regression_model, hyperparameters_of_regression_model, hyperparameters_of_imputer

The best_regression_model is:
Ridge(alpha=1)

The hyperparameters_of_regression_model are:
{'alpha': 1, 'copy_X': True, 'fit_intercept': True, 'max_iter': None, 'normalize': False, 'random_state': None, 'solver': 'auto', 'tol': 0.001}

The hyperparameters_of_imputer are:
{'add_indicator': False, 'copy': True, 'fill_value': None, 'missing_values': nan, 'strategy': 'most_frequent', 'verbose': 0}

## 5. Custom Imputer:
### Check custom imputer (replace missing value with mean) with 'fillna(mean):
### Output:
"check custom imputer & fillna": True

     

       
       
   
         
    
   
