🎬 DSA 210 Data Science Project: Film Financial Success Prediction

Student: Bartu Ege Esen (29557)  
Course: DSA 210 - Introduction to Data Science  


Project Overview
The aim of the project is to forecast the success of a movie financially (ROI > 1.5 or 150 percent return) prior to its release by using machine learning classification models developed on past TMDb movie data.
Core Research Question
Does a movie have the financial success or can it be predicted only with the help of the pre-release data, like the budget, the genre, the previous performance of the director (Historical ROI), and the time of year at which it is released?
Project Objectives and Methodology (Existing Objectives)
The main objective of the given project is to design a classification model, which will divide the films into two different categories:
Strong ROI (> 150%)
Weak ROI (< 150%)
Key Project Milestones
Proposal Submission: This step was done on 31 October (Completed) and the first plan had been submitted to GitHub.
Data Collection, EDA and Hypothesis Testing: This was a critical phase which was done on 28 November (Completed). It was able to cover all the data collection, cleaning and feature engineering activities, as well as the calculation of statistical tests of hypothesis.
ML Application: The second step will be to train model with the help of machine learning algorithms (Logistic Regression, Random Forest, and XGBoost) and test its performance (Planned 02 January).
Final Submission: Final submission of project will be done on 09 January (Planned).
Feature Engineering and Data Engineering
Primary Data Source
Origin: The Movies Dataset retrieved in TMDb (through Kaggle).
Cleaned Size: The total number of movies left after screening out all records with zero/missing budget/revenue is 5,393.
Data Enrichment: Director and Cast Historical ROI (Key Innovation)
Original Plan:
We were going to incorporate external critic scores (Metacritic/Rotten Tomatoes) using web scraping.
Change of Implementation and Justification:
The initial strategy was replaced since critic scores present a threat of data leakage, since they are released too soon. Rather we concentrated on computing Director and Cast Historical ROI. The aspect is entirely based on pre-release data and contributes significantly to the model performance and reliability.
The Major Features Designed (41 Features in Total)
Director Features:
This is the average profitability (Past average ROI), and the success rate of the director but only on movies that he has done.
(Temporal validation is used to avoid data leakage.)
Cast Features:
The average revenue of the 3 most popular actors historically (and time-wise).
Financial Features:
The cost of log-transformed budget
Budget ratio compared to the annual average
Exploratory Data Analysis (EDA) and Hypothesis Testing (28 November Deliverable)
EDA Highlights
The dataset recorded a general success rate (ROI > 1.5) of 42.6% of success.
The distribution of ROI was identified to be extremely skewed towards the right and hence the application of non-parametric tests in statistics was justified.
The release timing analysis indicates that motion pictures that are released during the summer season (May to August) have higher average profitability in visual form.
Hypothesis Testing Plan
There are three hypothesis tests that will be used in order to statistically prove the main assumptions of the project. These tests will be carried out in detail and their results and interpretation will be found in the Notebook file.
H1: Summer Season Releases
Hypothesis to be Tested:
The mean ROI of the films released in summer season (May–August) has statistically higher ROI as compared to the mean ROI of the films released during the remaining of the year.
Applied Test: Independent t-test.
H2: Budget Category / Financial Success Relationship
Hypothesis to be Tested:
The type of budget used in the film (Low/Medium/High) is statistically connected with the financial success of the film (ROI > 1.5).
Applied Test: Test of independence Chi-square.
H3: Director Experience / Success Relationship
Hypothesis to be Tested:
The probability of the current film being financially successful is greater when the number of films that the director has made (Experience) is high.
Applied Test: Mann-Whitney U Test.
Machine Learning Implementation (02 January Deliverable Plan)
Modeling Goal
The second phase of the project will involve the creation of classification models to estimate the status of the film in Financial_Success (1 or 0) based on the 41 designed pre-release features.
Models and Metrics
Models
Logistic Regression
Random Forest
XGBoost
Evaluation Criteria
Accuracy
ROC-AUC (Receiver Operating Characteristic – Area Under Curve)
Feature Importance Analysis
The analysis will establish the most important pre-release factors in the prediction process to come up with valuable Business Insights.
AI Assistance Disclosure

Per the DSA 210 project guidelines, I confirm that AI tools (Large Language Models) were utilized for assistance in code generation and documentation.

LLMs were used to generate the complex Pandas code for Historical Director and Cast ROI feature engineering, ensuring temporal validation integrity.

LLMs assisted in drafting statistical interpretations and optimizing the structure of the final report.
