# DSA 210 Data Science Project Proposal: Global Film Industry Financial Success Prediction

**Bartu Ege Esen** (29557)

## Project Concept and Motivation (Outline of Proposal)

The project will be used to forecast the financial success (Return on Investment - ROI) of Global Cinema Films utilizing publicly accessible pre-release data.

Core Question:How far can factors of production such as budget, genre, cast and director coupled with pre-release critic ratings accurately predict whether a movie will be a profitable box office?

Significance: The model obtained will give film producers and investors concrete information that will assist them to evaluate the financial risks and optimize their marketing plans of films of the same feature.

### Project Goals and Methodology

Purpose:The purpose of this is to come up with a model that classifies the films and groups them into two categories: High ROI (e.g., > 150% return) and Low ROI (e.g., < 150% return).

Applied ML Method: The first Classification algorithms that we will test are Logistic Regression and Random Forest.

Analysis Stages: To generate insights, data gets collected and cleaned, feature engineering takes place, correlation analysis, model training, hyperparameter optimization, and insights are presented.

## Data Source and Enrichment

### Primary Data

Origin:The Movies Dataset (fixed on TMDb data, which is accessible on open platforms such as Kaggle/analogous sources). This data offers a movie performance perspective all over the world.

Content: Thousands of films produced after the year 1980 with metadata, such as production budget (budget), revenue (revenue), genre, lead actors, director and date of release.

### Enrichment Data (Needed by Public Datasets)

In order to address the need of enhancing the publicly available data, two other sets of data will be included:

Critic Scores:To elicit a pre-release perception. Results will be scraped (with Python applications, such as Requests and BeautifulSoup) or aided through API by film title and release year with critic websites, such as Metacritic or Rotten Tomatoes.
Historical Cast/Director Success: To incorporate the historical behavior of the key creatives in the model. Each lead actor and director will have the average career ROI calculated based on the filmography of the primary dataset. This calculated value will be provided in the main dataset in the form of a new feature.

## Data Preparation and Collection Plan

### Data Collection Method

Primary Data: TMDb-based data will be downloaded publicly and movies, whose budget/revenue data is missing, will be filtered.

Critic Scores:Python libraries (Requests, BeautifulSoup) will be used to do the web scraping and collect the scoring of the websites of interest.

Merging: The three datasets will be combined into one primary DataFrame with the help of a common identifier, e.g. a film ID, or a proper combination of a title/release year.

### EDA and Hypothesis Testing Plan (Due November 28)

Exploratory Data Analysis (EDA): Findings of missing values and outliers.

Hypothesis Test:The core hypothesis will be the following one and tested:
> A film with a high budget (> $100M) whose director has had average ROI of high rankings in the past will be more likely to make above-average profit, although pre-release critic scores might be low.

T-test or ANOVA will be used to test this hypothesis on related sub-groups.
