# 🍷 Wine Classification with Random Forest

Machine learning project using Random Forest classifier to predict Italian wine types based on chemical analysis with hyperparameter optimization.

[![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](../LICENSE)
[![Feedback](https://img.shields.io/badge/Feedback-500%2F500-brightgreen.svg)]()
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

This project was developed for the Machine Learning module of the start2impact Data Science Master program. It implements a Random Forest classification model to predict wine types produced by three different Italian winemakers based on chemical composition analysis. The dataset contains 13 chemical features derived from wine samples, making it an ideal multi-class classification problem.

The project demonstrates key machine learning concepts including train-test splitting, hyperparameter tuning with GridSearchCV, model evaluation with multiple metrics, and decision tree visualization for interpretability.

**Score: 500/500**

## ✨ Features

- **Multi-Class Classification** - Predicts wine type from three Italian producers
- **Random Forest Model** - Ensemble learning with multiple decision trees
- **Hyperparameter Optimization** - GridSearchCV with 10-fold cross-validation
- **Comprehensive Evaluation** - Accuracy score, classification report, confusion matrix
- **Model Interpretability** - Decision tree visualization from the trained forest
- **Stratified Sampling** - Ensures representative class distribution in train/test splits

## 🚀 Installation

### Prerequisites

```bash
pip install jupyter numpy pandas matplotlib scikit-learn
```

### Setup

```bash
# Clone repository
git clone https://github.com/ulpati/data-science-portfolio.git
cd data-science-portfolio/machine_learning

# Launch Jupyter Notebook
jupyter notebook machine_learning.ipynb
```

## 💻 Usage

### Quick Start

Open the Jupyter Notebook and run cells sequentially:

```bash
jupyter notebook machine_learning.ipynb
```

### Analysis Workflow

1. **Data Loading** - Load Wine dataset from scikit-learn
2. **Data Preparation** - Split into training (70%) and test (30%) sets with stratification
3. **Model Definition** - Initialize Random Forest classifier with random_state=42
4. **Hyperparameter Tuning** - GridSearchCV to find optimal parameters
5. **Model Training** - Train best model on training data
6. **Evaluation** - Test set performance assessment
7. **Visualization** - Extract and plot decision tree from forest

### Dataset Features (13 Chemical Properties)

- **Alcohol** - Alcohol content
- **Malic Acid** - Malic acid concentration
- **Ash** - Ash content
- **Alcalinity of Ash** - Alkalinity of ash
- **Magnesium** - Magnesium content
- **Total Phenols** - Total phenolic compounds
- **Flavanoids** - Flavanoid content
- **Nonflavanoid Phenols** - Non-flavanoid phenolic compounds
- **Proanthocyanins** - Proanthocyanin content
- **Color Intensity** - Color intensity measurement
- **Hue** - Hue value
- **OD280/OD315** - Protein content dilution ratio
- **Proline** - Proline amino acid content

### Target Classes

Three wine types from Italian producers (encoded as 0, 1, 2)

## 📁 Project Structure

```
machine_learning/
├── README.md                    # This file
└── machine_learning.ipynb      # Main analysis notebook
```

## 🔬 Methodology

### Model: Random Forest Classifier

Random Forest is an ensemble learning method that constructs multiple decision trees during training and outputs the class that is the mode of individual tree predictions. This approach:
- Reduces overfitting compared to single decision trees
- Handles high-dimensional data effectively
- Provides feature importance rankings
- Robust to outliers and noise

### Train-Test Split

- **Training Set:** 70% of data (stratified by target class)
- **Test Set:** 30% of data (stratified by target class)
- **Stratification:** Ensures representative class distribution in both sets
- **Random State:** Fixed at 42 for reproducibility

### Hyperparameter Optimization

**GridSearchCV Configuration:**
- **Cross-Validation:** 10-fold CV
- **Scoring Metric:** Accuracy
- **Parameters Tuned:**
  - `max_depth`: [None, 5, 10, 20] - Maximum tree depth
  - `min_samples_split`: [2, 5, 10] - Minimum samples to split a node
  - `min_samples_leaf`: [1, 2, 4] - Minimum samples in leaf node
  - `n_estimators`: [50, 75, 100] - Number of trees in forest
  - `max_features`: [1 to 13] - Features considered per split

### Evaluation Metrics

- **Accuracy Score** - Overall classification correctness
- **Classification Report** - Precision, recall, F1-score per class
- **Confusion Matrix** - Visual representation of true vs. predicted labels

## 📊 Results

### Optimal Hyperparameters

**Best Model Configuration:**
- `max_depth`: None (fully expanded trees)
- `max_features`: 1 (only one feature per split)
- `min_samples_leaf`: 1 (minimum one sample per leaf)
- `min_samples_split`: 2 (minimum two samples to split)
- `n_estimators`: 50 (50 decision trees in forest)

**Validation Performance:** ~99.2% accuracy during cross-validation

### Model Interpretation

The optimal configuration creates a forest of 50 fully-expanded decision trees, where each tree uses only a single feature to make splitting decisions. This aggressive feature selection (`max_features=1`) combined with multiple trees ensures high diversity in the ensemble, leading to robust predictions and reduced overfitting.

### Key Insights

- **High Accuracy:** Random Forest achieved ~99% accuracy on validation set
- **Minimal Overfitting:** Ensemble approach prevents overfitting despite fully expanded trees
- **Feature Diversity:** Using only one feature per split forces trees to explore different aspects
- **Reproducibility:** Fixed `random_state=42` ensures consistent results across runs
- **Small Forest Size:** Only 50 trees needed for excellent performance due to simple dataset

### Decision Tree Visualization

The notebook extracts a single tree from the trained forest and visualizes its structure, showing:
- Split conditions at each node
- Sample distributions at each node
- Class predictions at leaf nodes
- Feature importance in decision-making

## 🤝 Acknowledgements

This project was developed for the **start2impact Data Science Master Program**.

**Dataset:** [Wine Recognition Dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_wine.html)  
**Source:** UCI Machine Learning Repository  
**Context:** Chemical analysis of wines from three Italian cultivars  
**Samples:** 178 wine samples with 13 chemical features

**Institution:** start2impact University  
**Course:** Machine Learning  
**Project Type:** Multi-Class Classification