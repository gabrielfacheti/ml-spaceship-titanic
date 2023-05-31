<!DOCTYPE html>
<html>
		
<body>

<h1>Machine Learning Challenge: Spaceship Titanic</h1>
I developed this notebook using Python and its libraries as a part of a Kaggle challenge. The objective is to predict whether a passenger was transported to an alternate dimension during a collision with a spacetime anomaly. The data is available <a href="https://www.kaggle.com/competitions/spaceship-titanic">here</a> (also in this repository).<br>
The dataset covers information from almost 13,000 passengers on board.

<h2>Methodology</h2>

<h3>Dataset Information</h3>
The dataset provided for this challenge is divided into two sets: the train set and the test set. The train set contains 8,693 rows and 14 columns, while the test set contains 4,277 rows and 13 columns. Both sets include information about all the passengers in the spaceship, such as Id, Home Planet, Name, Cabin, and more.

<h3>Exploratory Data Analysis and Feature Engineering</h3>
To gain insights into the data and prepare it for modeling, Exploratory Data Analysis (EDA) and Feature Engineering techniques were applied. EDA involved analyzing the dataset's characteristics, distribution, and relationships among variables. Feature Engineering aimed to create new features or transform existing ones to improve the predictive power of the models.


<h3>Handling Missing Values</h3>
Missing values in the dataset were addressed using own data. Mean, median, and mode were utilized to fill in the missing values based on the nature of the features.<br>
<i>Big thanks to Samuel Cortinhas here for the guide he provided. It helped a lot to handle the missing values. You can find his profile on Kaggle <a href="https://www.kaggle.com/samuelcortinhas">here</a>.</i>

<h3>Data Preprocessing</h3>
The following preprocessing steps were performed on the dataset before training the models:
<ul>
	<li>Continuous features were preprocessed using a log-transform to handle skewness in their distributions.</li>
	<li>Numerical features were standardized using <code>StandardScaler</code>, and categorical features were encoded using <code>OneHotEncoder</code>. This was achieved using <code>Pipeline</code> and <code>ColumnTransformer</code> to ensure consistent and efficient preprocessing.</li>
</ul>

<h3>Train-Test Split and Validation Set</h3>
To evaluate the models' performance during training, the train set was further divided into a train-validation split using the <code>train_test_split</code> function. This allowed the creation of a separate validation set for assessing model performance and tuning hyperparameters.

<h3>Model Selection and Evaluation</h3>
Several models were tried using <code>GridSearchCV</code> to find the best hyperparameters for each model. The models evaluated included <code>LogisticRegression</code>, <code>CatBoost</code>, <code>LGBM</code>, <code>SVC</code>, and others. The evaluation metrics used to assess their performance included Accuracy, ROC AUC, and F1 Score.

<h3>Cross-Validation</h3>
The two best-performing models were selected and further assessed using cross-validation. <code>StratifiedKFold</code> was employed to ensure consistent and representative splits of the data. This cross-validation approach allowed for a more robust estimation of the models' performance.

<h3>Stacked Ensemble</h3>
In the final stage, the probabilities of predictions from all models were stacked, and their mean was taken. This process resulted in producing the most confident predictions for the classification task at hand.

<h2>Results</h2>
<p>The following images show us the metrics of all models after the grid search.</p>

![image](https://github.com/gfacheti/ML-Spaceship-Titanic/assets/106284497/72073040-ff20-4306-8980-282efe5bd303)
![image](https://github.com/gfacheti/ML-Spaceship-Titanic/assets/106284497/ff9ba1b0-ccaf-420e-ae8d-808ae66f23f5)
		
<p>LGBM and CatBoost were selected to do cross-validation. The stacked probabilities are shown below.</p>
		
![image](https://github.com/gfacheti/ML-Spaceship-Titanic/assets/106284497/f2e07847-0b7f-4881-ae67-0510595766f9)

<p>Finally, the probabilities were converted into True or False, plotted in a pie chart, and compared with the target.</p>
	
![image](https://github.com/gfacheti/ML-Spaceship-Titanic/assets/106284497/c809fc29-a9e8-4d77-b029-dc061fb514e7)
	
<p>It's visible how the model overestimate a bit the number of transported passengers in the test set, but the results are pretty good.</p>

</body>
</html>
