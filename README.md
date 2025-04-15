# Email Marketing Campaign Analysis

This repository contains a Jupyter Notebook analyzing an email marketing campaign for an e-commerce site to optimize future email sends. The analysis measures performance, builds a predictive model for link clicks, estimates improvements, and identifies user segment patterns.

## Table of Contents
- [Overview](#overview)
- [Questions Answered](#questions-answered)
- [Results Summary](#results-summary)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [Notes and Assumptions](#notes-and-assumptions)
- [Future Improvements](#future-improvements)
- [License](#license)

## Overview
The goal is to evaluate an email campaign using data on sent emails, opens, and link clicks, then provide actionable insights to maximize click-through rates. The analysis uses Python, pandas, scikit-learn, and matplotlib in a Jupyter Notebook.

**Data**:
- `email_table.csv`: Email details (ID, text, version, send hour, weekday, user country, past purchases).
- `email_opened_table.csv`: Emails opened (by email ID).
- `link_clicked_table.csv`: Emails with link clicks (by email ID).

*Note*: Data is assumed to be in CSV format. For database sources, modify the data loading step (e.g., use `pd.read_sql`).

## Questions Answered
The notebook addresses four key questions:
1. **What percentage of users opened the email and clicked the link?**
2. **Can we build a model to optimize emails for maximum link clicks?**
3. **How much would the model improve click-through rate, and how to test it?**
4. **Are there interesting patterns in performance by user segments?**

## Results Summary
- **Q1: Open and Click Rates**
  - Open rate: 10.35% (moderate engagement).
  - Click-through rate: 2.12% (typical for email campaigns).
- **Q2: Predictive Model**
  - A Random Forest Classifier predicts clicks with 97% accuracy but low recall for clicks (1%) due to data imbalance (453 clicks vs. 19,547 non-clicks).
- **Q3: Model Improvement**
  - Baseline click rate: 2.12% (random sending).
  - Model-targeted rate: 4.13% (top 20% users by predicted probability).
  - Improvement: 94.67% relative increase, testable via A/B test.
- **Q4: Segment Patterns**
  - Top segments: Short, personalized emails to US (3.60%) and UK (3.58%) users.
  - Key drivers: Send hour (42% importance), past purchases (29%), weekday (19%).
  - Visualization: Bar chart of click rates by country highlights US/UK strength.

*Comment*: Low click recall suggests room for model improvement, but the targeting strategy shows significant potential.
*Note*: Data files are required to run the notebook. If unavailable, replace with your own or use database queries.

## Setup Instructions
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/alishba25/Email-Marketing-Campaign-Analysis.git
   cd email-marketing-campaign-analysis

2. **Install Dependencies**: Ensure Python 3.6+ is installed, then set up a virtual environment:
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install pandas scikit-learn matplotlib jupyter

3. **Verify Data**:
   Place email_table.csv, email_opened_table.csv, and link_clicked_table.csv in the root folder.
   Alternatively, update the notebook’s data loading cell (e.g., pd.read_csv) to point to your data source.

*Comment*: If using a database, install sqlalchemy and adjust the data loading code (e.g., pd.read_sql('SELECT * FROM email_table', conn)).

## Usage
1. Launch Jupyter Notebook
2. Open Email Marketing Campaign Analysis.ipynb.
3. Run cells sequentially to:
   - Load data and calculate rates (Q1).
   - Train the Random Forest model (Q2).
   - Estimate improvement (Q3).
   - Analyze segments and view the country click rate plot (Q4).
4. Review the conclusion section for insights and recommendations.
*Note: The notebook is self-contained with Markdown explanations. Outputs (e.g., 10.35% open rate) are displayed inline and summarized in Markdown.*

## Notes and Assumptions
1. Data Assumptions:
   - CSVs contain complete, clean data with columns as described.
   - No missing values or outliers were handled (assumed pre-cleaned).
   - Features like subject lines or user demographics weren’t available.
2. Model Limitations:
   - Low click recall (1%) due to imbalanced data (2.12% click rate).
   - Random Forest was chosen for robustness; other models (e.g., XGBoost) weren’t tested.
3. Generalization:
   - Results are specific to this campaign; new campaigns may vary.
   - Country-level patterns (e.g., US/UK strength) may reflect market size or preferences.
*Comment: For production use, validate the model with fresh data and consider additional features (e.g., email subject, user age).*

## Future Improvements
1. Model Enhancement:
   - Address data imbalance with oversampling (e.g., SMOTE) or alternative models.
   - Test feature engineering (e.g., hour bins, purchase recency).
2. Testing:
   - Run the proposed A/B test (random vs. model-targeted emails) for 4 weeks.
   - Experiment with send times based on hour/weekday importance.
3. Analysis:
   - Add visualizations (e.g., click rates by hour or weekday).
   - Incorporate new data (e.g., subject lines, open times) for richer insights.
4. Deployment:
   - Integrate the model into an email platform for real-time targeting.
   - Automate data pipelines for continuous analysis.
*Note: These steps align with optimizing future campaigns, as per the VP’s goal to avoid random sending.*

## License

This project is licensed under the MIT License. See  for details.

*Comment: Feel free to modify or replace the license based on your preferences.*
