# 🗺️ Travel Safety Analysis with SQL

PostgreSQL project analyzing U.S. Department of State data to determine if countries labeled as dangerous match actual American tourist fatality rates.

[![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](../LICENSE)
[![Feedback](https://img.shields.io/badge/Feedback-500%2F500-brightgreen.svg)]()
[![SQL](https://img.shields.io/badge/SQL-PostgreSQL-blue.svg)]()
[![Analysis](https://img.shields.io/badge/Analysis-Travel%20Safety-orange.svg)]()

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Installation](#-installation)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Key Findings](#-key-findings)
- [SQL Queries](#-sql-queries)
- [Acknowledgements](#-acknowledgements)

## 🎯 Overview

This project was developed for the SQL module of the start2impact Data Science Master program. It challenges common perceptions about travel safety by analyzing actual American tourist death data (2009-2016) against government travel warnings. The analysis reveals significant discrepancies between perceived and actual danger, using PostgreSQL to perform complex joins, aggregations, and statistical calculations.

The project addresses a critical question: Are the countries with the most travel warnings actually the most dangerous for American tourists? Using data from the U.S. Department of State, it compares warning frequencies with per-capita death rates, cause-of-death breakdowns, and terrorism-related fatalities.

**Score: 500/500**

## ✨ Features

- **Complex SQL Joins** - Multi-table INNER/LEFT JOIN operations across four datasets
- **Statistical Analysis** - Per capita death rate calculations accounting for traveler volume
- **Cause of Death Breakdown** - Detailed analysis of fatality causes by country
- **Terrorism Analysis** - Percentage calculations for terrorism-related deaths
- **Data Validation** - Verification of published research statements using SQL queries
- **Null Handling** - COALESCE for missing traveler data (e.g., Mali)

## 🚀 Installation

### Prerequisites

```bash
# PostgreSQL 9.5 or higher
psql --version

# CSV data files included in csv_files/ directory
```

### Setup

```bash
# Clone repository
git clone https://github.com/ulpati/data-science-portfolio.git
cd data-science-portfolio/psql_travel

# Connect to PostgreSQL
psql -U your_username -d your_database

# Execute SQL script (update file paths in script first)
\i psql_travel.sql
```

**Important:** Before running, edit `psql_travel.sql` and replace `<file_path>` with your actual CSV file locations.

## 💻 Usage

### Quick Start

Run the complete analysis:

```sql
-- Execute all queries in sequence
\i psql_travel.sql
```

### Individual Query Execution

Execute specific analyses by copying sections from `psql_travel.sql`:

```sql
-- Example: Get top 15 countries by death count
SELECT a.country AS "country", a.freq AS "deaths", 
       b.sdwarnings_df_nwarnings AS "warnings"
FROM deaths_ranking a
INNER JOIN warnings_ranking b
ON a.country = b.sdwarnings_df_country
ORDER BY a.freq DESC LIMIT 15;
```

### Data Import

The script creates three main tables:
1. **deaths_ranking** - Country-level death frequency
2. **warnings_ranking** - Government warning counts per country
3. **deaths_per_capital** - Per capita death rates with traveler data
4. **sdamerican_deaths_abroad_10_09_to_06_16** - Individual death records

## 📁 Project Structure

```
psql_travel/
├── README.md              # This file
├── psql_travel.sql       # Complete SQL analysis script
├── psql_travel.pdf       # Project report/documentation
└── csv_files/            # Data files
    ├── DeathsPerCapita.csv         # Per capita death rates
    ├── DeathsRanking.csv           # Country death frequencies
    ├── SDamerican_deaths_abroad_10_09_to_06_16.csv  # Individual records
    └── WarningsRanking.csv         # Warning counts
```

## 📊 Key Findings

### Main Discovery

**Significant relationship exists between per capita American deaths abroad and warning frequencies**, but with notable exceptions:

### Perception vs. Reality

**Most Warned Countries:**
- **Mexico** - Flagged by most warning agencies
- **Mali** - High warning count
- **Israel** - Frequent warnings

**Actually Most Dangerous (per capita deaths):**
- **Thailand** - Higher death rate than warning count suggests
- **Pakistan** - Most dangerous country by per capita deaths
- **Philippines** - Elevated death rate despite fewer warnings

### Statistical Insights

**Deaths by Volume:**
- High absolute death counts don't always mean high danger (correlation with tourist volume)
- Mexico has high deaths but also highest American traveler volume
- Per capita analysis reveals true risk levels

**Cause of Death - Pakistan (Most Dangerous):**
- Detailed breakdown shows primary causes in highest-risk country
- Terrorism, accidents, natural causes, medical issues analyzed
- Percentage calculations for terrorism-related fatalities

**Safest Countries:**
- Countries with lowest per capita death rates (excluding zero-death countries)
- Minimum threshold: at least one recorded death for statistical validity

## 🔍 SQL Queries

### Query 1: Top 15 Countries by Deaths

```sql
SELECT a.country, a.freq AS "deaths", 
       b.sdwarnings_df_nwarnings AS "warnings"
FROM deaths_ranking a
INNER JOIN warnings_ranking b
ON a.country = b.sdwarnings_df_country
ORDER BY a.freq DESC LIMIT 15;
```

**Purpose:** Identify countries with highest absolute death counts and compare with warnings.

### Query 2: Top 15 Countries by Warnings

```sql
SELECT a.country, b.sdwarnings_df_nwarnings AS "warnings",
       a.freq AS "deaths"
FROM deaths_ranking a
INNER JOIN warnings_ranking b
ON a.country = b.sdwarnings_df_country
ORDER BY b.sdwarnings_df_nwarnings DESC LIMIT 15;
```

**Purpose:** Find most-warned countries and check actual death rates.

### Query 3: Per Capita Death Rates

```sql
SELECT a.validctrys AS "country", a.percap AS "per_capita",
       a.ndeaths AS "deaths", a.ntravelers AS "travelers",
       b.sdwarnings_df_nwarnings AS "warnings"
FROM deaths_per_capital a
INNER JOIN warnings_ranking b
ON a.validctrys = b.sdwarnings_df_country
ORDER BY a.percap DESC;
```

**Purpose:** Calculate true danger by normalizing deaths against traveler volume.

### Query 4: Article Statement Verification

```sql
SELECT a.sdwarnings_df_country AS "country", 
       COALESCE(b.percap,0) AS "per_capita",
       b.ntravelers AS "travelers", c.freq AS "deaths", 
       a.sdwarnings_df_nwarnings AS "warnings"
FROM warnings_ranking a
LEFT JOIN deaths_per_capital b ON a.sdwarnings_df_country = b.validctrys
INNER JOIN deaths_ranking c ON c.country = a.sdwarnings_df_country
WHERE a.sdwarnings_df_country IN ('Mexico', 'Mali', 'Israel', 'Thailand', 'Pakistan', 'Philippines')
ORDER BY "per_capita" DESC;
```

**Purpose:** Verify published statement about warning vs. danger discrepancies.  
**Technique:** COALESCE handles Mali's missing traveler data (sets to 0 for sorting).

### Query 5: Cause of Death Analysis

```sql
SELECT cause_of_death, COUNT(cause_of_death) AS "number_of_deaths"
FROM sdamerican_deaths_abroad_10_09_to_06_16
WHERE country LIKE 'Pakistan'
GROUP BY cause_of_death
ORDER BY "number_of_deaths" DESC;
```

**Purpose:** Break down fatality causes in highest-risk country.

### Query 6: Safest Countries

```sql
SELECT a.validctrys AS "country", a.percap AS "per_capita",
       a.ndeaths AS "deaths", a.ntravelers AS "travelers",
       b.sdwarnings_df_nwarnings AS "warnings"
FROM deaths_per_capital a
INNER JOIN warnings_ranking b ON a.validctrys = b.sdwarnings_df_country
WHERE a.ndeaths > 0
ORDER BY a.percap ASC;
```

**Purpose:** Identify statistically safest destinations (minimum 1 death for validity).

### Query 7: Terrorism Analysis

```sql
SELECT country,
       SUM(CASE WHEN cause_of_death LIKE 'Terrorist%' THEN 1 ELSE 0 END) AS "terrorism_deaths",
       COUNT(*) AS "total_deaths",
       CASE
           WHEN COUNT(*) > 0 THEN
               ROUND((SUM(CASE WHEN cause_of_death LIKE 'Terrorist%' THEN 1 ELSE 0 END))::numeric / 
                     (COUNT(*)::numeric) * 100, 2)
           ELSE 0.0
       END AS "percentage"
FROM sdamerican_deaths_abroad_10_09_to_06_16
GROUP BY country
ORDER BY "percentage" DESC;
```

**Purpose:** Calculate terrorism-related death percentages by country.  
**Techniques:** 
- CASE WHEN for conditional counting
- Type casting (::numeric) for float division
- ROUND for two decimal places
- Zero-division protection

## 🤝 Acknowledgements

This project was developed for the **start2impact Data Science Master Program**.

**Data Source:** U.S. Department of State - American Deaths Abroad (2009-2016)  
**Analysis Period:** October 2009 - June 2016  
**Countries Analyzed:** 100+ destinations with recorded American tourist deaths

**Institution:** start2impact University  
**Course:** SQL and Database Management  
**Project Type:** Exploratory Data Analysis with PostgreSQL
