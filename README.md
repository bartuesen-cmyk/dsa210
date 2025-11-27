# 🎬 DSA 210 Data Science Project: Film Financial Success Prediction

**Student:** Bartu Ege Esen (29557)  
**Course:** DSA 210 - Introduction to Data Science  
**Term:** Fall 2024-2025

---

## Project Overview

The aim of this project is to forecast the financial success of a movie (ROI > 1.5 or 150% return) prior to its release by using machine learning classification models developed on historical TMDb movie data.

### Core Research Question
Can a movie's financial success be predicted using only pre-release data such as budget, genre, the director's historical performance (ROI), cast popularity, and release timing?

---

## Project Objectives and Methodology

### Main Objective
The main objective is to design a classification model which will divide films into two categories:
- **High ROI** (>150% return)
- **Low ROI** (<150% return)

### Key Project Milestones

| Deadline | Deliverable | Status |
|----------|-------------|--------|
| 31 October | Project proposal submission | ✅ Completed |
| **28 November** | **Data collection, EDA, hypothesis testing** | ✅ **Completed** |
| 02 January | Machine learning model implementation | 🔄 In progress |
| 09 January | Final project submission | ⏳ Planned |

---

## Data Source and Feature Engineering

### Primary Data Source
- **Origin:** The Movies Dataset retrieved from TMDb (via Kaggle)
- **Initial Size:** 45,466 movies
- **Cleaned Size:** 5,393 movies (after screening out records with zero/missing budget/revenue)
- **Time Period:** 1915-2017

### Data Enrichment: Director and Cast Historical ROI (Key Innovation)

**Original Plan:** Incorporate external critic scores (Metacritic/Rotten Tomatoes) using web scraping.

**Change of Implementation and Justification:**

The initial strategy was replaced since critic scores present a threat of data leakage, as they are released close to the film's release date. Instead, we focused on calculating **Director and Cast Historical ROI**. This approach is entirely based on pre-release data and contributes significantly to model performance and reliability.

---

## Major Features Designed (41 Features Total)

### Director Features (3)
- **Past average ROI:** Calculated only from the director's previous films
- **Success rate:** Percentage of past films with ROI > 1.5
- **Experience:** Number of previous films directed
- *Temporal validation used to avoid data leakage*

### Cast Features (2)
- Average revenue of the top 3 billed actors (historically and temporally validated)
- Log-transformed cast revenue

### Financial Features (4)
- Log-transformed budget
- Budget ratio compared to annual average
- Budget category (Low/Medium/High)
- Raw budget

### Genre Features (21)
- One-hot encoding for 20 unique genres
- Genre count per film

### Time Features (4)
- Release year, month, quarter
- Summer release flag (May-August)

### Production Company Features (3)
- Company's past average ROI
- Company success rate
- Company experience

### Other Metadata (4)
- Runtime, vote average, vote count, popularity

---

## Exploratory Data Analysis (EDA) - 28 November Deliverable

### EDA Highlights
- The dataset recorded an overall success rate (ROI > 1.5) of **42.6%**
- The distribution of ROI was identified to be extremely right-skewed, justifying the application of non-parametric statistical tests
- Release timing analysis indicates that films released during the summer season (May-August) have higher average profitability in visual analysis
- **Budget Paradox:** Low-budget films show higher success rates (49.8%) compared to high-budget films (41.4%)

### EDA Deliverables
Six comprehensive visualizations were created:
1. ROI distribution histogram
2. Success rate by release month (bar chart)
3. Genre-wise success comparison
4. Budget vs Revenue scatter plot (log-scale, color-coded by success)
5. Feature correlation heatmap
6. ROI trend over decades (line plot)

---

## Hypothesis Testing - 28 November Deliverable

Three hypothesis tests were conducted to statistically prove the main assumptions of the project. Detailed results and interpretations are documented in the notebook file (`film_analysis.ipynb`).

### H1: Summer Season Releases

**Hypothesis to be Tested:** The mean ROI of films released in summer season (May-August) is statistically higher compared to the mean ROI of films released during the rest of the year.

**Applied Test:** Independent t-test

### H2: Budget Category / Financial Success Relationship

**Hypothesis to be Tested:** The budget category of the film (Low/Medium/High) is statistically connected with the financial success of the film (ROI > 1.5).

**Applied Test:** Chi-square test of independence

### H3: Director Experience / Success Relationship

**Hypothesis to be Tested:** The probability of a film being financially successful is greater when the number of films that the director has made (experience) is higher.

**Applied Test:** Mann-Whitney U test

*Complete test results, statistical tables, p-values, and interpretations are available in `film_analysis.ipynb`*

---

## Machine Learning Implementation - 02 January Deliverable (Planned)

### Modeling Goal
The second phase of the project will involve the creation of classification models to estimate the film's Financial_Success status (1 or 0) based on the 41 designed pre-release features.

### Models to be Trained
1. Logistic Regression
2. Random Forest
3. XGBoost

### Evaluation Criteria
- **Accuracy:** Overall prediction correctness
- **ROC-AUC:** Receiver Operating Characteristic – Area Under Curve
- **Feature Importance Analysis:** Identify the most important pre-release factors in the prediction process to generate valuable business insights

---

## Project Files
```
📂 Project Repository
├── 📄 README.md - Project overview and progress documentation
├── 📓 film_analysis.ipynb - Complete analysis notebook
├── 📊 *.png - EDA visualization outputs (6 graphs)
├── 📁 movies_metadata.csv - Primary dataset
├── 📁 credits.csv - Cast/crew enrichment data
├── 📄 requirements.txt - Python dependencies
```

---

## AI Assistance Disclosure

Per the DSA 210 project guidelines, I confirm that AI tools (Large Language Models) were utilized for assistance in code generation and documentation.

### Specific Use Cases:
- **Complex Pandas Code:** LLMs were used to generate the complex Pandas code for Historical Director and Cast ROI feature engineering, ensuring temporal validation integrity to prevent data leakage.
- **Statistical Interpretations:** LLMs assisted in drafting statistical interpretations of hypothesis test results and optimizing the structure of visualizations.
- **Documentation:** LLMs helped structure the README and ensure clarity in technical explanations.

### Student Contribution:
All AI-generated code and text were:
1. Reviewed and fully understood before inclusion
2. Tested and validated on the actual dataset
3. Modified based on project-specific requirements and domain knowledge

Detailed AI interaction documentation is included as comments within the `film_analysis.ipynb` notebook for complete transparency.

