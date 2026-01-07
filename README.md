# 🎬 DSA 210 Data Science Project: Film Financial Success Prediction

**Student:** Bartu Ege Esen (29557)  
**Course:** DSA 210 - Introduction to Data Science  


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
| 02 January | Machine learning model implementation | ✅ Completed |
| 09 January | Final project submission | ⏳ Planned |

---

## Data Source and Feature Engineering

### Primary Data Source
- **Origin:** The Movies Dataset retrieved from TMDb (via Kaggle)
- **Initial Size:** 45,466 movies
- **Cleaned Size:** 5,393 movies (after screening out records with zero/missing budget/revenue)
- **Time Period:** 1915-2017
  ### Secondary: IMDB-NEW
- **Files:** title.basics.tsv (1.0 GB), title.ratings.tsv (27 MB)
- **New Features:** IMDB rating, vote count, rating tier
- **Merge:** By title and release year

### Data Enrichment: Director and Cast Historical ROI (Key Innovation)

**Original Plan:** Incorporate external critic scores (Metacritic/Rotten Tomatoes) using web scraping.

**Change of Implementation and Justification:**

The initial strategy was replaced since critic scores present a threat of data leakage, as they are released close to the film's release date. Instead, we focused on calculating **Director and Cast Historical ROI**. This approach is entirely based on pre-release data and contributes significantly to model performance and reliability.

---

## Major Features Designed (44 Features Total)

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

### IMDB Features (3) - NEW
- **IMDB Rating:** Average user rating (1-10 scale)
- **IMDB Votes:** Number of user votes (popularity indicator)
- **IMDB Popularity:** Log-transformed vote count

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
## Machine Learning Implementation - 02 January Deliverable ✅

### Models Trained
Three classification models were trained and evaluated:
1. **Logistic Regression** - Baseline linear model
2. **Random Forest** - Ensemble tree-based model
3. **XGBoost** - Gradient boosting model (best performance)

### Evaluation Results
- **Best Model:** XGBoost
- **Accuracy:** 76.55%
- **ROC-AUC:** 0.8396
- **Cross-Validation AUC:** 0.8370 (±0.018)
- **Precision/Recall/F1:** Comprehensive metrics in notebook

### Feature Importance
XGBoost analysis revealed:
- Director's historical ROI is the strongest predictor
- IMDB ratings (from secondary data) significantly improve predictions
- Budget optimization matters more than absolute budget size
- Release timing and cast popularity are moderate predictors
---

## Project Files
```
📂 Project Repository
├── 📄 README.md - Project overview and progress documentation
├── 📓 film_analysis.ipynb - Complete analysis notebook
├── 📊 *.png - Visualization outputs (9 graphs: 6 EDA + 2 IMDB + 1 ROC)
├── 📁 title.basics.tsv - IMDB dataset (1.0 GB)
├── 📁 title.ratings.tsv - IMDB ratings (27 MB)
├── 📁 movies_metadata.csv - Primary dataset
├── 📁 credits.csv - Cast/crew enrichment data
├── 📄 requirements.txt - Python dependencies
```

---
---

## 🔍 Key Findings

Through comprehensive analysis of 45,876 films, we discovered several critical success factors:

### Main Discoveries
1. **Director Track Record is Critical**
   - Director's historical ROI is the strongest single predictor
   - Proven directors show significantly higher success rates

2. **IMDB Ratings Predict Success**
   - Films rated 8.5+: 35.9% success rate
   - Films rated <6.0: 6.2% success rate
   - Early audience ratings are reliable indicators

3. **Budget Optimization Matters**
   - Films aligned with category norms outperform extreme outliers
   - Strategic budget allocation > absolute budget size

4. **Strategic Release Timing**
   - Summer releases show 8-12% higher success rates
   - Timing significantly impacts ROI

5. **Model Performance**
   - XGBoost achieves 76.55% accuracy with 44 features
   - 0.84 ROC-AUC demonstrates strong predictive power
   - Pre-release prediction is feasible and reliable

---

## ⚠️ Limitations & Future Work

### Current Limitations
- **Survivorship Bias:** Dataset includes only released films; cancelled projects not captured
- **IMDB Match Rate:** 70.6% merge success means 29.4% films lack rating data
- **Missing Variables:** Marketing spend, social media buzz, release competition not included
- **Binary Classification:** Success definition (ROI > 1.5) simplifies complex spectrum
- **Temporal Scope:** Data limited to 1960-2017; post-2017 streaming era not reflected

### Future Improvements
**Short-term (Next 3 months):**
- Hyperparameter tuning for optimal model performance
- Feature interaction analysis (e.g., director × budget)
- Ensemble methods combining multiple models

**Long-term (6-12 months):**
- Integrate social media sentiment data (Twitter, Reddit)
- Add marketing spend and competition analysis
- Develop real-time prediction API for industry use
- Analyze streaming era dynamics (post-2017)
- Investigate genre-specific prediction models

---

## 🚀 How to Run This Project

### Prerequisites
- Python 3.9+
- 2GB free disk space (for IMDB datasets)

### Installation Steps

1. **Clone repository**
```bash
git clone https://github.com/bartuesen-cmyk/dsa210.git
cd dsa210
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Download IMDB datasets**
- Visit: https://datasets.imdbws.com/
- Download: `title.basics.tsv.gz` and `title.ratings.tsv.gz`
- Extract and place in project root directory

4. **Launch Jupyter Notebook**
```bash
jupyter notebook film_analysis.ipynb
```

5. **Execute analysis**
- In Jupyter: `Kernel` → `Restart & Run All`
- Processing time: ~5 minutes

### Expected Outputs
- 9 visualization PNG files
- Comprehensive model performance metrics
- Feature importance analysis
- Statistical test results

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

