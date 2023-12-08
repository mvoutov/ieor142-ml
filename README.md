## Documentation for San Francisco Crime Data Analysis Code

This Python script performs an in-depth analysis of crime data in San Francisco, focusing on predictive modeling to identify patterns related to arrests. The script uses various libraries such as Pandas, NumPy, scikit-learn, Statsmodels, Folium, Seaborn, and Matplotlib for data manipulation, visualization, and machine learning.

# Onboarding
1. Copy the repo on your local machine
2.  Download the data from the website provided in the section **Data Acquisition** and save it in the folder `data` with the name `SF_Crime_Reports.csv`
3. First run model about predicting arrests in `arrests_random_forest.ipynb`. This model will generate a new csv file with cleaned data to use for the second model
4. Run second model in`crime_hot_spots.ipynb` that predicts crime hotspot neighborhoods

# Libraries Used
#### Any dependencies can be installed by runing the first cell in each nobebook

- Pandas & NumPy: For data manipulation and numerical computations.
- scikit-learn: Provides tools for machine learning, including data splitting, classifiers, and model evaluation metrics.
- Statsmodels: Used for statistical modeling.
- Folium: A library for creating interactive maps.
- Seaborn & Matplotlib: For data visualization.
- imblearn: Provides the SMOTE algorithm for handling imbalanced datasets.
- Socrata: Used for accessing data from the Socrata Open Data API.

# Data Acquisition and Preparation
1. Data Retrieval:

- Utilizes the Socrata client to fetch public data from "data.sfgov.org".
- Downloads the first 2000 records of San Francisco crime data (dataset ID: "wg3w-h783") and converts them to a Pandas DataFrame.
- Police crime data for San Francisco can be obtained from: https://data.sfgov.org/Public-Safety/Police-Department-Incident-Reports-2018-to-Present/wg3w-h783

2. Data Loading:

- Loads an additional crime dataset from a CSV file.
- Selects relevant columns and drops missing values.

3. Data Transformation:

- Creates a copy of the dataset and extracts 'Month' and 'Day' from 'Incident Date'.
- Converts 'Incident Time' to a datetime format and calculates the time in minutes.
- Performs one-hot encoding on selected categorical columns.
- Standardizes column names, removing spaces and special characters.

4. Time-Based Feature Engineering:

- Defines morning, afternoon, and night based on time in minutes and creates corresponding binary features.
- Creates an 'Is_Arrest' column as a binary indicator of whether an arrest occurred.

5. Rolling Sum and Lag Features:

- Calculates a rolling 7-day sum and the previous day's arrests.
- Maps these calculations back to the DataFrame as new features.

# Predictive Modeling
1. Data Splitting:

- Splits the dataset into training and testing sets.

2. Model Definition and Training:

- Defines a Random Forest Classifier and parameter grid for hyperparameter tuning.
- Uses GridSearchCV for model selection based on cross-validation.
- Fits the model to the training data.

3. Model Evaluation:

- Predicts on the test data using the best model from GridSearchCV.
- Evaluates the model using accuracy, classification report, and confusion matrix.
- Prints the best hyperparameters and the accuracy score.

4. Feature Importance Analysis:

- Extracts and visualizes the feature importances from the best model.

# Conclusion

This script provides a comprehensive approach to analyzing and predicting crime incidents in San Francisco. It combines data acquisition, preprocessing, exploratory data analysis, feature engineering, and machine learning to derive insights and build predictive models.