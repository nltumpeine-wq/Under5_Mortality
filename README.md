# Under5_Mortality
Prediction of under_five_mortality
UNDER-FIVE MORTALITY ANALYSIS
Exploring Historical Trends and Predicting Child Mortality Using Health and Socioeconomic Indicators
A Data Science Project Aligned with Sustainable Development Goal 3: Good Health and Well-being
Tools: Python, Pandas, NumPy, Matplotlib, Scikit-learn, TensorFlow/Keras
Data source: World Bank Open Data
Project category: Data Analysis | Exploratory Data Analysis | Machine Learning
________________________________________
SLIDE 1: TITLE SLIDE
UNDER-FIVE MORTALITY ANALYSIS
Exploring Historical Trends and Predicting Child Mortality Using Health and Socioeconomic Indicators
Sustainable Development Goal 3: Good Health and Well-being
Presented by: Tumpeine Noel Lerrian
Technologies used:
	Python 
	Pandas and NumPy 
	Matplotlib 
	Scikit-learn 
	TensorFlow/Keras 
Project objective: To explore historical under-five mortality patterns and evaluate how effectively selected health and socioeconomic indicators can predict under-five mortality rates.
Suggested visual: Include a relevant child-health image alongside the SDG 3 icon.
________________________________________
SLIDE 2: BUSINESS UNDERSTANDING
Background and Problem Statement
Under-five mortality is an important indicator of child health and the broader health conditions of a population. Understanding its historical patterns can help researchers explore changes in child survival and investigate factors associated with mortality.
Health and socioeconomic conditions may be associated with differences in under-five mortality across countries and years.
However, identifying patterns in historical data and accurately predicting mortality are challenging because countries differ in their health systems, socioeconomic conditions, data availability, and other relevant circumstances.
This project uses historical World Bank data to examine under-five mortality trends and investigate whether selected indicators can help predict mortality rates.
Research problem
How can historical data and machine learning techniques be used to explore under-five mortality patterns and predict mortality rates using selected health and socioeconomic indicators?
________________________________________
SLIDE 3: PROJECT OBJECTIVES
Main Objective
To explore historical under-five mortality patterns and evaluate the predictive performance of selected regression models using health and socioeconomic indicators.
Specific Objectives
	Examine historical patterns in under-five mortality across countries and years. 
	Explore the relationship between under-five mortality and selected health and socioeconomic indicators. 
	Develop regression models to predict under-five mortality rates. 
	Compare model performance using appropriate regression evaluation metrics. 
	Investigate prediction errors and identify limitations of the models and dataset. 
Research significance
The project demonstrates how data science can be applied to public health data to explore historical patterns and investigate the potential of machine learning for mortality prediction.
It aligns with UN Sustainable Development Goal 3, which promotes good health and well-being.
________________________________________
SLIDE 4: DATA SOURCES AND FEATURES
Data Sources and Dataset Description
The project uses historical indicators obtained from World Bank data.
The datasets were combined to create a country-year dataset covering the period 2000–2024.
Each observation represents a country in a particular year.
Target Variable
Under-five mortality rate (Under5_Mortality)
The target measures the probability of a child dying before reaching five years of age, expressed as deaths per 1,000 live births in the relevant indicator.
Selected Predictors
Feature	Description
Basic_Sanitation	Access to basic sanitation services
Basic_Water	Access to basic drinking water services
Immunization_DPT	DPT immunization coverage
Health_Expenditure	A selected health expenditure indicator
These features were selected to investigate whether the indicators could help predict under-five mortality.
Dataset dimensions: 4,425 rows × 10 columns in the complete modeling dataset.
Note: Before final submission, verify the exact World Bank indicator code and measurement unit for Health_Expenditure from the notebook or source metadata. Its precise definition should not be assumed from the column name alone.
________________________________________
SLIDE 5: DATA UNDERSTANDING
Exploratory Data Analysis (EDA)
Exploratory Data Analysis was conducted to understand the dataset's structure, identify data-quality issues, and examine historical patterns before model development.
Activities Performed
	Examined dataset dimensions, column names, and data types. 
	Investigated missing values. 
	Explored annual under-five mortality averages. 
	Examined data availability across years. 
	Compared actual and predicted mortality values. 
	Investigated differences in model performance. 
Key Finding
The average under-five mortality rate across available country-year observations generally declined between 2000 and 2023.
The analysis also revealed differences in data availability across years.
Important Interpretation
The annual averages were calculated from available country-year observations. They should not be interpreted as official population-weighted global mortality estimates.
The modeling dataset contained only 22 complete observations for 2024, compared with 176 for 2023. Consequently, the low 2024 average should not be interpreted as evidence of a sudden global decline in under-five mortality.
Suggested visual: Include the historical under-five mortality trend line chart.
________________________________________
SLIDE 6: DATA PREPARATION AND CLEANING
Data Preparation
Data preparation was necessary to combine the different datasets and produce usable observations for analysis and machine learning.
1. Data Loading and Inspection
The datasets were imported using Python and Pandas.
Their dimensions, column names, data types, and missing values were examined to understand their structure and identify data-quality issues.
2. Data Transformation
The data was organized into a country-year format, where each row represented a particular country in a particular year.
The mortality data was combined with the selected health and socioeconomic indicators using country identifiers and years to match observations.
3. Handling Missing Values
Missing values were investigated during data preparation.
For the modeling dataset, complete observations for the target and selected predictors were retained.
This made the dataset easier to use for the initial modeling exercise, but it also reduced the number of available observations.
4. Training and Testing Split
The dataset was divided chronologically.
Dataset	Period	Observations
Training set	2000–2020	3,868
Testing set	2021–2024	557
Total	2000–2024	4,425
The training set was used to fit the models, while the testing set was used to evaluate predictions on later observations.
This approach better reflects the task of using historical data to predict later observations than a random split would.
Limitation: Countries may appear in both the training and testing sets. Therefore, this evaluation does not establish how well the models would perform on entirely unseen countries.
________________________________________
SLIDE 7: MODELING
Machine Learning Modeling and Methodology
Models Developed and Evaluated
Regression models were used because the target variable, under-five mortality, is numerical.
Four main model families were explored.
1. Linear Regression
Linear Regression models a linear relationship between the selected predictors and the target variable.
It provides a useful baseline for understanding how a relatively simple regression approach performs on the dataset.
2. Decision Tree Regression
A Decision Tree learns decision rules that divide observations into groups and uses those divisions to generate predictions.
It can capture nonlinear relationships but may overfit if not appropriately controlled.
3. Random Forest Regression
Random Forest combines predictions from multiple decision trees.
By aggregating predictions across trees, it can capture complex patterns and often provides more stable predictions than a single decision tree.
4. Artificial Neural Network (ANN)
An Artificial Neural Network uses interconnected computational units to learn patterns from data.
ANNs can represent complex relationships, although their performance depends on appropriate preprocessing, architecture, training, and model selection.
Model Development Process
	Selected four predictors and the mortality target. 
	Divided the dataset chronologically into training and testing sets. 
	Trained the regression models. 
	Evaluated model predictions. 
	Tuned selected models. 
	Compared performance using MAE, RMSE, and R². 
	Investigated individual prediction errors. 
The project also explored hyperparameter tuning and time-aware cross-validation for Random Forest.
________________________________________
SLIDE 8: EVALUATION 
Evaluation Metrics
Three principal metrics were used to compare regression model performance.
1. Mean Absolute Error (MAE)
MAE measures the average absolute difference between actual and predicted values.
A lower MAE indicates smaller average absolute prediction errors.
For the tuned Random Forest, the recorded MAE was approximately 8.73 deaths per 1,000 live births.
2. Root Mean Squared Error (RMSE)
RMSE measures prediction error while giving greater weight to larger errors.
A lower RMSE indicates better performance according to this metric.
The tuned Random Forest recorded an RMSE of approximately 18.83.
3. Coefficient of Determination (R²)
R² measures how well the model explains variation in the target relative to a mean-based baseline.
Its value can be negative, zero, or positive, with higher values generally indicating better performance.
The tuned Random Forest recorded:
R^2=0.6563

This indicates that the model explained approximately 65.6% of the variation in the test-set target relative to the test-set mean baseline, according to the standard R² interpretation.
It does not mean that 65.6% of the individual predictions were correct.
________________________________________
SLIDE 9: MODEL COMPARISON AND RESULTS
Regression Model Performance Comparison
The evaluated models produced different levels of predictive performance.
The following results are from our recorded model comparison.
Model	MAE	RMSE	R²
Tuned Random Forest	8.73	18.83	0.656
Random Forest	9.21	19.48	0.632
Tuned Decision Tree	10.31	20.13	0.607
ANN v2	10.44	20.23	0.603
ANN v1	10.48	20.29	0.601
Decision Tree	10.87	23.51	0.464
Linear Regression	11.22	20.22	0.603
Baseline	26.97	34.32	-0.142
Key Findings
	The tuned Random Forest achieved the lowest recorded MAE. 
	It also achieved the lowest recorded RMSE and highest R². 
	The tuned Random Forest outperformed the untuned Random Forest on the recorded test metrics. 
	The baseline performed substantially worse than the other models. 
Best-Performing Model
The tuned Random Forest was the strongest-performing model in the recorded comparison.
Its MAE of 8.73 indicates that its predictions differed from the actual mortality values by an average absolute amount of approximately 8.73 deaths per 1,000 live births.
However, the model's prediction errors varied across observations.
Suggested visual: Use the horizontal MAE comparison chart you created. A lower bar indicates a smaller average absolute prediction error.
Final verification needed: Before presenting this table as definitive, confirm in the notebook that every model was evaluated on the same test observations and that the baseline was defined consistently.
________________________________________
SLIDE 10: ERROR ANALYSIS AND MODEL LIMITATIONS
Understanding Prediction Errors
After comparing the models, individual predictions were examined to identify where the model performed well and where it struggled.
Error Analysis
The residual was calculated as:
"Residual"="Actual"-"Predicted" 

A positive residual indicates that the model underestimated mortality, while a negative residual indicates that it overestimated mortality.
Key Observations
	Prediction errors varied across countries and years. 
	Some observations with exceptionally high mortality were substantially underestimated. 
	Some observations were overestimated. 
	Overall performance did not guarantee equally accurate predictions for every country-year observation. 
For example, one of the observations examined for the Central African Republic in 2022 had an actual mortality rate of approximately 424.6, while a model prediction was substantially lower.
Observations from Papua New Guinea in 2022 and 2023 also illustrated substantial overprediction.
These examples demonstrate why individual prediction errors should be investigated alongside summary metrics.
Project Limitations
1. Missing data: Complete-case filtering reduced the number of usable observations.
2. Uneven data coverage: Only 22 complete observations were available for 2024.
3. Limited predictors: The models used only four selected indicators, although many other factors may be associated with under-five mortality.
4. Generalization: Countries appeared in both training and testing data, so the evaluation did not test performance on entirely unseen countries.
5. Prediction versus causation: The models identified predictive relationships but did not establish that the selected indicators caused changes in mortality.
Conclusion
Although the models captured useful patterns, their predictions should be interpreted cautiously, particularly for observations with exceptionally high mortality.
________________________________________
SLIDE 11: KEY FINDINGS AND CONCLUSION
Key Findings
Historical Trends
The average under-five mortality rate across available country-year observations generally declined between 2000 and 2023.
However, differences in data availability mean that the trend should not be treated as an official population-weighted global estimate.
Model Performance
The tuned Random Forest achieved the strongest overall performance among the models in the recorded comparison, with:
	MAE: 8.73 
	RMSE: 18.83 
	R²: 0.656 
These results suggest that the model captured meaningful predictive patterns in the test data.
Prediction Errors
The model's errors varied across countries and years, with substantial errors for some observations with exceptionally high mortality.
This demonstrates the importance of investigating model limitations rather than relying exclusively on average performance metrics.
Overall Conclusion
This project demonstrated how historical health data, exploratory data analysis, and machine learning can be used to investigate under-five mortality patterns and evaluate predictive models.
The tuned Random Forest performed best among the models compared, but its predictions were not uniformly accurate.
The results also highlighted the importance of data completeness, representative observations, appropriate evaluation methods, and careful interpretation of predictive performance.
The project illustrates how data science can contribute to the exploration of public health challenges aligned with Sustainable Development Goal 3: Good Health and Well-being.
________________________________________
SLIDE 12: FUTURE IMPROVEMENTS AND RECOMMENDATIONS
Future Work
Several improvements could be explored in future versions of the project.
1. Improve Data Quality and Coverage
	Investigate patterns of missingness. 
	Explore appropriate missing-data methods. 
	Seek more complete and consistent country-year observations. 
2. Include Additional Predictors
Investigate other relevant health and socioeconomic indicators, such as nutrition, maternal health, healthcare access, and broader socioeconomic conditions, where reliable data is available.
3. Improve Model Evaluation
	Ensure all models are evaluated using the same test observations. 
	Continue using time-aware validation where appropriate. 
	Test generalization to countries not represented in training data. 
4. Investigate Prediction Errors
	Examine errors across different mortality ranges. 
	Investigate why the models struggle with exceptionally high mortality values. 
	Determine whether suitable transformations or alternative approaches improve performance. 
5. Explore Alternative Models
Compare additional regression algorithms and tuning strategies to determine whether they offer better predictive performance.
Expected Benefit
These improvements could help establish whether the models can produce more reliable predictions across countries and years and clarify the settings in which the models are most useful.
________________________________________
SLIDE 13: THANK YOU
THANK YOU!
Questions and Discussion
Under-Five Mortality Analysis
Exploring Historical Trends and Predictive Modeling
Sustainable Development Goal 3: Good Health and Well-being
Thank you for your time and consideration.

