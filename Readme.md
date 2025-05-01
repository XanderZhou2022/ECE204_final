# Predicting Academic Paper Citation Impact from Peer Review Data

## Overview
This project explores the relationship between peer review evaluations and the long-term citation impact of academic papers. By analyzing reviewer comments, evaluation scores, and paper metadata, the project aims to identify early indicators of scientific influence that emerge during the peer review process. The findings could provide valuable insights for editorial decisions and improve our understanding of what constitutes impactful research.

## Describe of the dataset

### original data

The original review data is sourced from JSON files located in the `original_data/data` directory. This directory is organized by conference name (e.g., `acl_2017`, `conll_2016`) and paper type (`train`, `dev`, `test`). Within each conference folder, the `reviews` subdirectory contains the JSON files, where each file corresponds to a specific paper. These JSON files include metadata such as the paper title, review scores (e.g., `IMPACT`, `SUBSTANCE`, `ORIGINALITY`), reviewer comments, and other evaluation metrics. This structure allows for systematic extraction and analysis of peer review data.

### processed data

All the files in the `data` folder that were processed during the project:

1. **`accepted_clean.pkl`**  
   - **Description**: A cleaned dataset containing only accepted papers with all missing values removed and non-numerical fields converted to numerical values. The `comments` column has been dropped for simplicity.  
   - **Purpose**: Used as the final cleaned dataset for analysis and modeling.

2. **`accepted_clean.csv`**  
   - **Description**: The same as `accepted_clean.pkl`, but as the required of the ECE204 we change the format to `.csv`.  
   - **Purpose**: Provides a human-readable version of the cleaned dataset.

3. **`acl_2017.pkl`**  
   - **Description**: A DataFrame containing raw review data for papers from the ACL 2017 conference. This includes metadata, review scores, and reviewer comments extracted from JSON files.  
   - **Purpose**: Serves as an intermediate dataset before filtering for accepted papers.

4. **`acl_accepted.pkl`**  
   - **Description**: A filtered dataset containing only accepted papers from ACL 2017, with citation counts added from the `citation.json` file.  
   - **Purpose**: Used to analyze accepted papers from ACL 2017 and their citation impact.

5. **`all_title.txt`**  
   - **Description**: A text file containing the titles of all papers (from both ACL 2017 and CoNLL 2016) extracted from the JSON files.  
   - **Purpose**: Used as input for querying citation and acceptance information via external tools like GPT and Google Scholar.

6. **`citation.json`**  
   - **Description**: A JSON file containing information about whether each paper was accepted and its citation count. This data was collected using GPT and Google Scholar based on the titles in `all_title.txt`.  
   - **Purpose**: Provides citation and acceptance data to merge with the review datasets.

7. **`cleaned_data.csv`**  
   - **Description**: Another version of the cleaned dataset, similar to `accepted_clean.csv`, saved for compatibility with different tools.  
   - **Purpose**: Used as the final dataset for analysis and modeling.

8. **`combined_accepted.pkl`**  
   - **Description**: A combined dataset of accepted papers from both ACL 2017 and CoNLL 2016, including citation counts and review scores.  
   - **Purpose**: Used for unified analysis of accepted papers across both conferences.

9. **`conll_2016.pkl`**  
   - **Description**: A DataFrame containing raw review data for papers from the CoNLL 2016 conference. This includes metadata, review scores, and reviewer comments extracted from JSON files.  
   - **Purpose**: Serves as an intermediate dataset before filtering for accepted papers.

10. **`conll_accepted.pkl`**  
    - **Description**: A filtered dataset containing only accepted papers from CoNLL 2016, with citation counts added from the `citation.json` file.  
    - **Purpose**: Used to analyze accepted papers from CoNLL 2016 and their citation impact.


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

### Statement on the Use of AI Assistance

This report's structure and language were refined using GPT-based language models. The AI assistance was used to:

1. Improve the organization and flow of the report sections
2. Enhance clarity and readability through grammar and style improvements
3. Help formulate clearer interpretations of the analytical results
4. Ensure technical accuracy in describing machine learning approaches

All data analysis, code implementation, and primary insights were developed independently prior to AI assistance. The use of AI was limited to improving the communication of results rather than generating the analytical findings themselves.

Initial Prompt to GPT:
```
I am doing the data analysis of the review and citation, My project aims to predict the future citation impact of academic papers based on peer review text and metadata. I'll analyze how reviewer comments, evaluation scores, and paper characteristics correlate with long-term citation counts. The core problem I'm addressing is identifying early indicators of scientific impact hidden within the peer review process. I have already finish the main code and you need help me to finish checking the grammar and structure on the final report The final report notebook (final_report.ipynb) should contain the following sections in my code part.
```


---

## Contributors

- **Yixi Zhou**
- **Yifan Huang**
- **Qianyi Gong**

---
