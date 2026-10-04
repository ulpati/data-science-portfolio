# 📊 Data Manipulation and Visualization Project

Environmental impact analysis of global food and feed production exploring the relationship between food production, population growth, and climate change.

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
- [Key Findings](#-key-findings)
- [Acknowledgements](#-acknowledgements)

## 🎯 Overview

This project was completed as part of the Data Science Master program at start2impact. It analyzes the environmental impact of global food and feed production and distribution, exploring how agriculture influences climate change and population growth. The analysis follows a structured data science workflow from discovery to visualization, examining trends from 1961 to 2013.

The project addresses critical questions: What foods were most produced over the years? Which countries led production? Which foods generated the highest emissions? How much land was used? These insights help understand the sustainability challenges of feeding a growing global population projected to reach 9.7 billion by 2050.

**Score: 500/500**

## ✨ Features

- **Comprehensive EDA** - Six-phase analysis: Discovery, Data Selection, Cleaning, Transformation, Exploration, Visualization
- **Multiple Datasets** - Integration of FAO food production, temperature, population, and environmental impact data
- **Interactive Visualizations** - Plotly charts, raceplotly animations, and seaborn statistical plots
- **Climate Analysis** - Correlation between food production trends and global temperature changes
- **Sustainability Metrics** - Emissions analysis, land use patterns, and per-capita environmental impact

## 🚀 Installation

### Prerequisites

```bash
pip install jupyter numpy pandas seaborn matplotlib plotly country-converter raceplotly scikit-learn nbformat
```

### Setup

```bash
# Clone repository
git clone https://github.com/ulpati/data-science-portfolio.git
cd data-science-portfolio/data_vis

# Launch Jupyter Notebook
jupyter notebook data_vis.ipynb
```

## 💻 Usage

### Quick Start

**Option 1: View Interactive Charts Online (Recommended)**

View the notebook with all Plotly interactive visualizations rendered on nbviewer:

🔗 **[Open in nbviewer](https://nbviewer.org/github/ulpati/data-science-portfolio/blob/main/data_vis/data_vis.ipynb)**

**Option 2: Run Locally**

Open the Jupyter Notebook and run cells sequentially to reproduce the analysis:

```bash
jupyter notebook data_vis.ipynb
```

### Analysis Phases

1. **Discovery** - Problem identification and research questions formulation
2. **Data Selection** - Loading FAO, Food Production, Population, and Temperature datasets
3. **Data Cleaning** - Handling missing values, duplicate removal, country standardization
4. **Data Transformation** - Feature engineering, data reshaping, country code conversion
5. **Data Exploration** - Statistical analysis, correlation studies, trend identification
6. **Data Visualization** - Interactive charts, animated race plots, geographical maps

### Key Datasets

- **FAO.csv** - Global food/feed production (245+ countries, 1961-2013)
- **Food_Production.csv** - Environmental impact metrics per food type
- **Population.csv** - Historical population data by country
- **Temperature.csv** - Global temperature trends over time

## 📁 Project Structure

```
data_vis/
├── README.md                  # This file
├── data_vis.ipynb            # Main analysis notebook
└── csv/                       # Data files
    ├── FAO.csv               # Food and Agriculture Organization data
    ├── Food_Production.csv   # Environmental impact data
    ├── Population.csv        # Population statistics
    ├── Taiwan.csv            # Taiwan-specific data
    └── Temperature.csv       # Temperature records
```

## 📊 Key Findings

### Production Trends
- **Cereals Dominance** - Most produced food category until 1995, then surpassed by vegetables
- **Dietary Shift** - Significant increase in vegetable production since 1990 reflects changing preferences
- **Feed Evolution** - Cereals and maize maintained importance in livestock farming throughout the period

### Environmental Impact
- **High-Emission Foods** - Beef, lamb, and dairy products generate the highest greenhouse gas emissions
- **Land Use Patterns** - Animal products require disproportionately more land per calorie produced
- **Supply Chain Emissions** - Environmental impact extends beyond production to processing, transportation, packaging, and retail

### Regional Analysis
- **Leading Producers** - China, India, and USA consistently top production rankings
- **Climate Correlation** - Strong relationship between agricultural expansion and temperature increase
- **Per Capita Variations** - Significant differences in food production efficiency across countries

## 🤝 Acknowledgements

This project was developed for the **start2impact Data Science Master Program**.

**Data Sources:**
- [FAO Dataset (Kaggle)](https://www.kaggle.com/dorbicycle/world-foodfeed-production) - UN Food and Agriculture Organization
- [Food Production Environmental Impact (Kaggle)](https://www.kaggle.com/selfvivek/environment-impact-of-food-production)

**Academic Context:** Data Science Master - start2impact University