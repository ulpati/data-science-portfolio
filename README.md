# 📊 Data Science Portfolio

Comprehensive portfolio of data science projects completed during the start2impact Master program, showcasing skills in SQL, Python, data visualization, machine learning, and statistical analysis.

[![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)]()
[![SQL](https://img.shields.io/badge/SQL-PostgreSQL-blue.svg)]()
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)]()

## 📋 Table of Contents

- [Overview](#-overview)
- [Projects](#-projects)
- [Technologies](#️-technologies)
- [Installation](#-installation)
- [Project Structure](#-project-structure)
- [Skills Demonstrated](#-skills-demonstrated)
- [Acknowledgements](#-acknowledgements)

## 🎯 Overview

This repository contains five comprehensive data science projects completed during the start2impact Data Science Master program. Each project demonstrates proficiency in different areas of data science, from foundational programming and SQL to advanced machine learning and visualization techniques. The projects achieved consistently high scores (500/500 or 1400/1500), reflecting strong technical execution and analytical depth.

The portfolio spans the complete data science workflow: data acquisition, cleaning, exploratory analysis, statistical modeling, machine learning, and insight communication. Projects address real-world problems including environmental sustainability, education analytics, travel safety, wine quality classification, and automated file management.

## 📁 Projects

### 🗺️ [SQL - Travel Safety Analysis](./psql_travel)

**Score: 500/500**

PostgreSQL project analyzing U.S. Department of State data to compare travel warnings with actual American tourist fatality rates (2009-2016). Reveals significant discrepancies between perceived and actual danger.

**Key Technologies:** PostgreSQL, Complex Joins, Statistical Analysis  
**Key Findings:** 
- Mexico, Mali, and Israel receive most warnings but Thailand, Pakistan, and Philippines have higher per capita death rates
- Strong correlation between warnings and deaths overall, but notable exceptions
- Per capita analysis provides more accurate risk assessment than absolute counts

**Skills:** Complex SQL joins (INNER/LEFT), aggregate functions, CASE statements, per capita calculations, COALESCE for null handling

[View Project →](./psql_travel)

---

### 🗂️ [Python & NumPy - File Organizer](./file_organizer)

**Score: 500/500**

Automated file management system that organizes files by type (audio, documents, images) into categorized subfolders with CSV tracking. Implements both batch processing (Jupyter) and CLI interfaces.

**Key Technologies:** Python, os, shutil, csv, argparse  
**Features:**
- Automatic categorization by file extension
- Dynamic folder creation
- CSV logging with file metadata (name, type, size)
- Incremental updates without overwriting
- Command-line interface for selective processing

**Skills:** File I/O operations, CSV handling, CLI argument parsing, automated directory management, error handling

[View Project →](./file_organizer)

---

### 📊 [Data Manipulation & Visualization - Food Production Impact](./data_vis)

**Score: 500/500**

Comprehensive analysis of global food and feed production's environmental impact (1961-2013), exploring relationships between agriculture, population growth, and climate change. Integrates multiple datasets with interactive visualizations.

**Key Technologies:** Python, Pandas, NumPy, Seaborn, Matplotlib, Plotly, country-converter, raceplotly  
**Datasets:** FAO production (245+ countries), environmental impact, population, temperature  
**Key Insights:**
- Cereals dominated until 1995, then surpassed by vegetables
- Beef, lamb, dairy generate highest emissions
- Strong correlation between agricultural expansion and temperature increase

**Skills:** Data cleaning/transformation, multi-dataset integration, EDA, interactive visualization, time series analysis, geographical mapping

[View Project →](./data_vis) | [Open Notebook in nbviewer →](https://nbviewer.org/github/ulpati/data-science-portfolio/blob/main/data_vis/data_vis.ipynb)

---

### 🍷 [Machine Learning - Wine Classification](./machine_learning)

**Score: 500/500**

Random Forest classifier predicting Italian wine types based on 13 chemical features. Demonstrates hyperparameter tuning with GridSearchCV achieving ~99% validation accuracy.

**Key Technologies:** scikit-learn, Random Forest, GridSearchCV, Matplotlib  
**Dataset:** 178 wine samples, 3 classes, 13 chemical features  
**Model Performance:**
- Best parameters: max_depth=None, max_features=1, n_estimators=50
- Validation accuracy: ~99.2%
- 10-fold cross-validation

**Skills:** Multi-class classification, ensemble methods, hyperparameter optimization, model evaluation (accuracy, precision, recall, F1), decision tree visualization

[View Project →](./machine_learning)

---

### 🎓 [Final Project - Portuguese Grade Prediction](./final_project)

**Score: 1400/1500**

Capstone project applying multiple ML regression models (Random Forest, Decision Tree, KNN, SVR) to predict student final grades in Portuguese language courses. Analyzes 33 features across 649 students to identify success factors.

**Key Technologies:** scikit-learn, RandomizedSearchCV, Pandas, NumPy, Seaborn, Matplotlib  
**Dataset:** 649 students, 33 features (demographic, family, academic, social, health)  
**Key Findings:**
- Previous grades (G1, G2) strongest predictors of final grade (G3)
- Study time, past failures, parent education significantly impact performance
- Social factors (alcohol, relationships) show moderate negative correlation

**Skills:** Regression modeling, hyperparameter tuning, feature importance analysis, EDA, multi-model comparison, stratified sampling

[View Project →](./final_project)

---

## 🛠️ Technologies

### Languages
- **Python 3.7+** - Primary programming language
- **SQL (PostgreSQL)** - Database queries and analysis

### Data Analysis & Manipulation
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computing
- **csv** - CSV file handling

### Visualization
- **Matplotlib** - Static plotting
- **Seaborn** - Statistical visualization
- **Plotly** - Interactive charts
- **raceplotly** - Animated race plots

### Machine Learning
- **scikit-learn** - ML algorithms and evaluation
  - Random Forest, Decision Trees, KNN, SVR
  - GridSearchCV, RandomizedSearchCV
  - StandardScaler, train_test_split

### Tools & Libraries
- **Jupyter Notebook** - Interactive development
- **argparse** - CLI argument parsing
- **os, shutil** - File system operations
- **country-converter** - Geographic data standardization

## 🚀 Installation

### Prerequisites

```bash
# Python 3.7 or higher
python --version

# PostgreSQL (for psql_travel project)
psql --version
```

### Clone Repository

```bash
git clone https://github.com/ulpati/s2i_datascience.git
cd s2i_datascience
```

### Install Python Dependencies

```bash
# All projects
pip install jupyter numpy pandas matplotlib seaborn scikit-learn

# data_vis project
pip install plotly country-converter raceplotly nbformat

# No additional packages needed for file_organizer (uses standard library)
```

### Launch Jupyter

```bash
# Navigate to project folder
cd data_vis  # or machine_learning, final_project, file_organizer

# Start Jupyter Notebook
jupyter notebook
```

## 📁 Project Structure

```
data-science-portfolio/
├── README.md                      # This file
├── psql_travel/                   # SQL travel safety analysis
│   ├── README.md                 # Project documentation
│   ├── psql_travel.sql          # SQL queries
│   ├── psql_travel.pdf          # Report
│   └── csv_files/               # Data files
├── file_organizer/                # Python file management
│   ├── README.md                 # Project documentation
│   ├── fileorganizer.ipynb      # Batch processing notebook
│   ├── addfile.py               # CLI script
│   └── files/                    # Target directory
├── data_vis/                      # Data visualization project
│   ├── README.md                 # Project documentation
│   ├── data_vis.ipynb           # Main analysis
│   └── csv/                      # Datasets (FAO, Food, Population, Temperature)
├── machine_learning/              # Wine classification
│   ├── README.md                 # Project documentation
│   └── machine_learning.ipynb   # Model training and evaluation
└── final_project/                 # Student grade prediction
    ├── readme.md                 # Project documentation
    ├── final_project.ipynb      # Comprehensive ML analysis
    └── student-por.csv          # Student dataset
```

## 💡 Skills Demonstrated

### Data Science Workflow
- **Data Acquisition** - CSV loading, dataset integration, API usage
- **Data Cleaning** - Missing value handling, duplicate removal, standardization
- **Exploratory Analysis** - Statistical summaries, correlation analysis, pattern identification
- **Feature Engineering** - Data transformation, encoding, scaling
- **Modeling** - Algorithm selection, training, validation
- **Evaluation** - Metrics selection, performance assessment, model comparison
- **Communication** - Visualization, reporting, insight delivery

### Technical Skills
- **SQL Proficiency** - Complex joins, aggregations, subqueries, CTEs, window functions
- **Python Programming** - Object-oriented design, functional programming, error handling
- **Statistical Analysis** - Hypothesis testing, correlation, distribution analysis
- **Machine Learning** - Classification, regression, ensemble methods, hyperparameter tuning
- **Data Visualization** - Static plots, interactive charts, dashboards, geographical maps
- **Version Control** - Git, GitHub, documentation best practices

### Domain Knowledge
- **Environmental Science** - Food production sustainability, climate impact
- **Education Analytics** - Student performance prediction, success factor identification
- **Risk Assessment** - Travel safety analysis, statistical risk quantification
- **Chemistry** - Wine quality classification based on chemical composition
- **Software Engineering** - CLI tools, automated workflows, modular design

### Soft Skills
- **Problem Solving** - Breaking complex problems into manageable tasks
- **Critical Thinking** - Questioning assumptions, validating results
- **Communication** - Clear documentation, visual storytelling
- **Attention to Detail** - Code quality, edge case handling, thorough testing

## 🤝 Acknowledgements

All projects were developed for the **start2impact Data Science Master Program**.

**Institution:** start2impact University  
**Program:** Data Science Master  
**Period:** 2023-2024  
**Average Score:** 500/500 (four projects), 1400/1500 (final project)

**Data Sources:**
- U.S. Department of State (Travel Safety Data)
- UN Food and Agriculture Organization (FAO)
- UCI Machine Learning Repository (Wine, Student Performance datasets)
- Kaggle (Environmental impact, temperature, population datasets)

**Special Thanks:**
- start2impact mentors and instructors
- Open-source data science community
- Dataset providers and maintainers
