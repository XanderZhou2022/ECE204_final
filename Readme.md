# Predicting Academic Paper Citation Impact from Peer Review Data

## Overview
This project explores the relationship between peer review evaluations and the long-term citation impact of academic papers. By analyzing reviewer comments, evaluation scores, and paper metadata, the project aims to identify early indicators of scientific influence that emerge during the peer review process. The findings could provide valuable insights for editorial decisions and improve our understanding of what constitutes impactful research.

---

## Repository Structure

```
ECE204_final/
├── code/
│   ├── final_report.ipynb       # Main analysis and report notebook
│   ├── pre_processing.ipynb     # Data cleaning and preprocessing steps
│   └── data/
│       ├── all_title.txt        # List of paper titles used in the dataset
│       ├── cleaned_data.csv     # Cleaned dataset used for analysis
├── ECE204_Final_Project.pdf     # Slides providing an overview of the project
└── README.md                    # Project documentation (this file)

```

---

## Key Files and Notebooks

### 1. `final_report.ipynb`
- **Purpose**: Contains the main analysis, modeling, and visualizations.
- **Sections**:
  - **Introduction**: Overview of the project and problem statement.
  - **Descriptive Analysis**: Explores patterns in reviewer feedback and citation outcomes using techniques like PCA and clustering.
  - **Predictive Modeling**: Implements and evaluates various machine learning models (e.g., SVR, XGBoost, Random Forest).
  - **Ethical Considerations**: Discusses biases and ethical implications of using predictive models in editorial decisions.
  - **Conclusion**: Summarizes findings, limitations, and future directions.

### 2. `pre_processing.ipynb`
- **Purpose**: Handles data cleaning and preprocessing.
- **Key Steps**:
  - Removes incomplete or inconsistent entries.
  - Standardizes reviewer scores and text data.
  - Converts categorical variables (e.g., presentation format) into numerical values.
  - Saves the cleaned dataset as `cleaned_data.csv`.

### 3. `ECE204_Final_Project.pdf`
- **Purpose**: Provides a high-level overview of the project, including objectives, methodology, and key findings.

---

## Key Findings

1. **Descriptive Analysis**:
   - Reviewer confidence has the strongest positive correlation with citation count.
   - PCA reveals that reviewer assessments capture multiple dimensions of paper quality.

2. **Predictive Modeling**:
   - Support Vector Regression (SVR) and XGBoost performed best among tested models.
   - All models struggled to predict high citation counts accurately, with negative R² values indicating limited predictive power.

3. **Ethical Considerations**:
   - Potential biases in the dataset (e.g., selection bias, citation bias).
   - Risks of reinforcing biases or devaluing innovative research if models are used in editorial decisions.

---

## Key Assumptions

1. Reviewer scores are unbiased and reflective of paper quality.
2. Citation counts are a reliable proxy for scientific impact.
3. All papers had equal exposure opportunities for citations.
4. The relationship between review scores and citation counts is stable over time.

---

## How to Run the Project

1. **Install Dependencies**:
   - Python 3.9+
   - Required libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `xgboost`

   Install dependencies using:
   
   `pip install -r requirements.txt`

2. **Run Preprocessing**:
   - Open `pre_processing.ipynb` and execute all cells to clean and preprocess the data.

3. **Run Analysis**:
   - Open `final_report.ipynb` and execute all cells to reproduce the analysis and visualizations.

---

## Future Directions

1. **Incorporating Textual Analysis**:
   - Analyze reviewer comments for deeper insights into citation outcomes.

2. **Multi-Modal Prediction**:
   - Combine review data with author metrics, institution information, and topic modeling.

3. **Alternative Impact Metrics**:
   - Explore other measures of impact, such as downloads or policy citations.

---

## Data Source

The dataset used in this project is from the PeerRead dataset:
```
@inproceedings{kang18naacl,
  title = {A Dataset of Peer Reviews (PeerRead): Collection, Insights and NLP Applications},
  author = {Dongyeop Kang and Waleed Ammar and Bhavana Dalvi and Madeleine van Zuylen and Sebastian Kohlmeier and Eduard Hovy and Roy Schwartz},
  booktitle = {Meeting of the North American Chapter of the Association for Computational Linguistics (NAACL)},
  address = {New Orleans, USA},
  month = {June},
  url = {https://arxiv.org/abs/1804.09635},
  year = {2018}
}
```

---

## Contributors

- **Yixi Zhou**
- **Yifan Huang**
- **Qianyi Gong**

---

## License

This project is for educational purposes only. Please refer to the PeerRead dataset license for data usage terms.