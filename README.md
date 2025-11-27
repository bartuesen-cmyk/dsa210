🎬 DSA 210 Data Science Project: Film Financial Success Prediction

Student: Bartu Ege Esen (29557)  
Course: DSA 210 - Introduction to Data Science  
Term: Fall 2024-2025

Project Overview

This project aims to predict whether a movie will be financially successful (ROI > 1.5 or 150% return) before its release, utilizing machine learning classification models trained on historical TMDb film data.

Core Research Question

Can a film's financial success be accurately predicted using only pre-release data, such as budget, genre, director's historical performance (Historical ROI), and release timing?

Project Goals and Methodology (Current Objectives)

The primary goal of this project is to create a classification model that separates films into two distinct categories: High ROI (> 150%) and Low ROI (< 150%).

The project is structured around the following key delivery milestones:

Proposal Submission: This phase was completed on 31 October (Completed) with the submission of the initial plan to GitHub.

Data Collection, EDA & Hypothesis Testing: This critical phase was completed on 28 November (Completed). It successfully included all necessary data collection, cleaning, feature engineering, and the execution of statistical hypothesis tests.

ML Application: The next planned stage is the application of machine learning algorithms (specifically Logistic Regression, Random Forest, and XGBoost) for model training and performance evaluation, scheduled for 02 January (Planned).

Final Submission: The project will conclude with the final submission on 09 January (Planned).

Dataset and Feature Engineering

Primary Data Source

Origin: The Movies Dataset sourced from TMDb (via Kaggle).

Cleaned Size: 5,393 movies remaining after filtering out all entries with zero/missing budget or revenue.

Data Enrichment: Director and Cast Historical ROI (Key Innovation)

Original Plan: To include external critic scores (Metacritic/Rotten Tomatoes) via web scraping.

Implementation Change and Justification:
The original plan was substituted because critic scores pose a data leakage risk, as they are published too close to the release date. Instead, we focused on calculating Director and Cast Historical ROI. This feature relies exclusively on pre-release data and significantly enhances model performance and reliability.

Key Features Engineered (41 Total Features)

To boost the project's predictive power, 41 leading features have been engineered:

Director Features: Average profitability (Past average ROI) and success rate calculated only from the director's previous films. (Temporal validation prevents data leakage.)

Cast Features: The historical average revenue of the top 3 actors (also calculated temporally).

Financial Features: Factors such as log-transformed budget and budget ratio relative to the yearly average.

Exploratory Data Analysis (EDA) and Hypothesis Testing (28 November Deliverable)

EDA Highlights (Exploratory Data Analysis)

A general success rate (ROI > 1.5) of 42.6% was observed in the dataset.

The ROI distribution was found to be severely right-skewed, confirming the need to utilize non-parametric statistical tests.

The analysis of release timing suggests that films released in the summer months (May–August) visually exhibit higher average profitability.

Hypothesis Testing Plan

Three distinct hypothesis tests will be applied to statistically validate the project's core assumptions. The detailed results and interpretations of these tests will be presented in the Notebook file.

H1: Summer Season Releases

Hypothesis to be Tested: The average ROI of films released in the summer season (May–August) is statistically higher than the average ROI of films released during the rest of the year.
Applied Test: Independent t-test

H2: Relationship Between Budget Category and Financial Success

Hypothesis to be Tested: The film's budget category (Low/Medium/High) is statistically related to its financial success (ROI > 1.5).
Applied Test: Chi-square test of independence

H3: Relationship Between Director Experience and Success

Hypothesis to be Tested: The number of films a director has made (Experience) increases the probability of the current film achieving financial success.
Applied Test: Mann-Whitney U Test

Machine Learning Implementation (02 January Deliverable Plan)

Modeling Goal

In the next stage of the project, classification models will be developed to predict the film's Financial_Success status (1 or 0) using the 41 engineered pre-release features.

Models and Metrics

Models to be Applied: Logistic Regression, Random Forest, and XGBoost algorithms will be tested.

Evaluation Criteria: Model performance will be measured using Accuracy and ROC-AUC (Receiver Operating Characteristic - Area Under Curve) scores.

Feature Importance Analysis: The analysis will determine which pre-release factors play the most crucial role in prediction, leading to valuable Business Insights.

AI Assistance Disclosure

Per the DSA 210 project guidelines, I confirm that AI tools (Large Language Models) were utilized for assistance in code generation and documentation.

LLMs were used to generate the complex Pandas code for Historical Director and Cast ROI feature engineering, ensuring temporal validation integrity.

LLMs assisted in drafting statistical interpretations and optimizing the structure of the final report.
