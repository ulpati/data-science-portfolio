# 🎓 Portuguese Final Grade Prediction

Machine learning project predicting student performance in Portuguese language courses using Random Forest, Decision Trees, KNN, and SVR models.

[![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](../LICENSE)
[![Feedback](https://img.shields.io/badge/Feedback-1400%2F1500-green.svg)]()
[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)]()
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)]()

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Installation](#-installation)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Methodology](#-methodology)
- [Results](#-results)
- [Acknowledgements](#-acknowledgements)

## 🎯 Overview

This capstone project for the start2impact Data Science Master program applies machine learning techniques to predict final Portuguese language grades (G3) for secondary school students in Portugal. Using data from 649 students across two schools (Gabriel Pereira and Mousinho da Silveira), the project identifies the most influential factors affecting academic performance.

The Portuguese grading system ranges from 0 to 20, with classifications from "Poor" (0-3.4) to "Excellent" (17.5-20). The analysis explores 33 features including demographic information, family background, study habits, social activities, and health status to build predictive models that help understand student success factors.

**Score: 1400/1500**

## ✨ Features

- **Comprehensive EDA** - Exploratory data analysis focused on final grades (G3) with multivariate insights
- **Multiple ML Models** - Random Forest, Decision Tree, K-Nearest Neighbors, Support Vector Regressor
- **Hyperparameter Tuning** - RandomizedSearchCV for optimal model configuration
- **Feature Importance Analysis** - Identification of key factors influencing student performance
- **Model Comparison** - Performance evaluation using R², MAE, MSE metrics
- **Academic Context** - Analysis aligned with Portuguese education system grading scale

## 🚀 Installation

### Prerequisites

```bash
pip install jupyter numpy pandas seaborn matplotlib scikit-learn
```

### Setup

```bash
# Clone repository
git clone https://github.com/ulpati/data-science-portfolio.git
cd data-science-portfolio/final_project

# Launch Jupyter Notebook
jupyter notebook final_project.ipynb
```

## 💻 Usage

### Quick Start

Open the Jupyter Notebook and execute cells sequentially:

```bash
jupyter notebook final_project.ipynb
```

### Analysis Workflow

1. **Data Loading** - Import student-por.csv dataset (649 students, 33 features)
2. **EDA** - Visualize distributions, correlations, and patterns in student data
3. **Data Preprocessing** - Feature scaling, train-test split (70/30), standardization
4. **Model Training** - Train RF, DT, KNN, SVR with hyperparameter optimization
5. **Evaluation** - Compare models using R², MAE, MSE metrics
6. **Feature Analysis** - Interpret which factors most impact final grades

### Dataset Features

**33 variables** including:
- **Demographic:** school, sex, age (15-22), address (urban/rural)
- **Family:** parent education (0-4), parent jobs, family size, cohabitation status
- **Academic:** study time, past failures, educational support, extra classes
- **Social:** going out frequency, romantic relationships, alcohol consumption
- **Health:** health status (1-5), absences (0-93)
- **Grades:** G1 (first period), G2 (second period), G3 (final grade, target variable)

### Portuguese Grading Scale

| Grade Range | Qualification |
|-------------|---------------|
| 17.5-20     | Excellent     |
| 15.5-17.4   | Very good     |
| 13.5-15.4   | Good          |
| 9.5-13.4    | Sufficient    |
| 3.5-9.4     | Weak          |
| 0-3.4       | Poor          |

## 📁 Project Structure

```
final_project/
├── README.md                 # This file
├── final_project.ipynb      # Main analysis notebook
└── student-por.csv          # Student dataset (649 records, 33 features)
```

## 🔬 Methodology

### Models Implemented

1. **Random Forest (RF)** - Ensemble method aggregating multiple decision trees
2. **Decision Tree (DT)** - Single tree-based classifier with interpretable splits
3. **K-Nearest Neighbors (KNN)** - Instance-based learning using proximity
4. **Support Vector Regressor (SVR)** - Kernel-based regression with margin optimization

### Hyperparameter Optimization

- **Technique:** RandomizedSearchCV with cross-validation
- **Metrics:** R² score, Mean Absolute Error (MAE), Mean Squared Error (MSE)
- **Validation:** K-fold cross-validation for robust performance estimation

### Evaluation Metrics

- **R² Score** - Proportion of variance explained by the model
- **MAE** - Average absolute difference between predictions and actual values
- **MSE** - Squared average of errors (penalizes larger errors)

## 📊 Results

### Key Findings

**Most Influential Features:**
- **Previous Grades** - G1 (first period) and G2 (second period) are strongest predictors
- **Study Time** - Weekly hours dedicated to studying significantly impact final grades
- **Past Failures** - Number of previous class failures negatively correlates with performance
- **Family Education** - Parent education level (especially mother's) shows positive correlation
- **Absences** - School absences demonstrate negative impact on final grades

**Model Performance:**
- Random Forest achieved the best balance of accuracy and generalization
- Decision Tree provided high interpretability but lower generalization
- SVR showed strong performance with proper kernel selection
- KNN performance varied significantly with neighborhood size (k parameter)

### Insights

- Students with consistent performance (high G1/G2) tend to maintain high G3 scores
- Educational support from family and school positively influences outcomes
- Social factors (alcohol consumption, romantic relationships, going out) show moderate negative correlation
- Urban vs. rural residence shows minimal direct impact on grades
- Study time quality matters more than just quantity of hours

## 🤝 Acknowledgements

This project was developed as the **Final Capstone Project** for the **start2impact Data Science Master Program**.

**Data Source:** [Student Alcohol Consumption Dataset (Kaggle)](https://www.kaggle.com/datasets/uciml/student-alcohol-consumption?select=student-por.csv)  
**Original Research:** UCI Machine Learning Repository - Student Performance Dataset  
**Academic Context:** Portuguese Secondary Schools (Gabriel Pereira and Mousinho da Silveira)

**Institution:** start2impact University  
**Program:** Data Science Master