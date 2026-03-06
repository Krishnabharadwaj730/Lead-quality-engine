# Lead Quality Engine

A Python-based data quality pipeline that validates, deduplicates, and
scores sales leads to help sales teams prioritize high-value prospects.

The system analyzes lead datasets (CSV format) and assigns a quality
score (0--100) based on email validity, phone validity, company
information, data completeness, and job title relevance.

The goal is simple: reduce time spent on low-quality leads and allow
teams to focus on the highest probability opportunities.

------------------------------------------------------------------------

# Problem

Sales datasets often contain large amounts of low-quality data such as:

-   Duplicate records
-   Invalid or disposable email addresses
-   Fake or placeholder phone numbers
-   Generic company information
-   Missing or incomplete data

Manual filtering of this data is time-consuming and error-prone. Sales
teams frequently spend hours reviewing leads before meaningful outreach
can begin.

------------------------------------------------------------------------

# Solution

Lead Quality Engine automates lead validation and prioritization.

The system:

-   Validates email, phone, and company data
-   Detects and removes duplicate leads
-   Computes a lead quality score (0--100)
-   Classifies leads into priority tiers
-   Exports ranked datasets for sales outreach

The entire pipeline runs locally and processes thousands of leads within
seconds.

------------------------------------------------------------------------

# Key Features

## Lead Validation

Checks the integrity of critical fields:

-   Email format validation
-   Disposable email domain detection
-   Generic email detection
-   Phone number format verification
-   Fake number pattern detection
-   Company name quality checks

## Duplicate Detection

Identifies duplicate leads using fuzzy matching and removes redundant
records.

## Lead Quality Scoring

Each lead receives a score between **0 and 100** based on weighted
features.

## Lead Prioritization

Leads are categorized into outreach tiers to guide sales teams.

## CSV Export

The system generates structured outputs that can be imported into CRM
platforms.

------------------------------------------------------------------------

# Scoring Methodology

The overall lead quality score is calculated using weighted attributes:

  Feature                Weight
  ---------------------- --------
  Email Quality          30%
  Phone Quality          15%
  Company Quality        20%
  Data Completeness      25%
  Decision-Maker Title   10%

Higher scores indicate higher lead reliability and outreach priority.

------------------------------------------------------------------------

# Output Files

The tool generates three CSV files.

## Priority Contacts

Leads with score **85+**

Recommended for immediate outreach.

## High Quality Leads

Leads with score **70--84**

Suitable for follow-up campaigns.

## All Leads with Scores

Complete dataset including validation results and lead quality score.

------------------------------------------------------------------------

# Example Input

CSV input format:

    first_name,last_name,email,phone,company,title
    John,Smith,john@acme.com,+1-555-123-4567,Acme Corp,VP Sales
    Sarah,Johnson,sarah@gmail.com,555-987-6543,TechCorp,CEO

The system automatically detects common column variations such as:

-   email_address
-   phone_number
-   company_name

------------------------------------------------------------------------

# Example Output

    first_name,last_name,email,quality_score,email_valid,phone_valid,company_valid
    John,Smith,john@acme.com,92,True,True,True
    Sarah,Johnson,sarah@gmail.com,65,True,True,True

------------------------------------------------------------------------

# Installation

Clone the repository:

``` bash
git clone https://github.com/yourusername/lead-quality-engine.git
cd lead-quality-engine
```

Install dependencies:

``` bash
pip install -r requirements.txt
```

------------------------------------------------------------------------

# Usage

Run the pipeline on a CSV dataset:

``` bash
python main.py your_leads.csv -o results/
```

Output files will be generated in the `results` directory.

------------------------------------------------------------------------

# Jupyter Notebook Demo

You can also run the system interactively:

``` bash
pip install jupyter
jupyter notebook
```

Open:

    ENTERPRISE_SOLUTION_FIXED.ipynb

------------------------------------------------------------------------

# Sample Dataset

A sample dataset is included:

    sample_leads.csv

Test the pipeline using:

``` bash
python main.py sample_leads.csv -o results/
```

------------------------------------------------------------------------

# System Workflow

The pipeline executes the following steps:

1.  Load input dataset
2.  Clean and normalize lead fields
3.  Validate email, phone, and company data
4.  Detect duplicates
5.  Compute lead quality score
6.  Rank and categorize leads
7.  Export prioritized results

------------------------------------------------------------------------

# Performance

Typical runtime performance:

  Dataset Size    Runtime
  --------------- ---------------
  1,000 leads     \<5 seconds
  10,000 leads    \~20 seconds
  100,000 leads   a few minutes

------------------------------------------------------------------------

# Limitations

This tool focuses on **data quality validation**, not lead enrichment.

Supported features:

-   Data format validation
-   Duplicate detection
-   Lead scoring based on data quality

Not included:

-   Email inbox verification
-   Phone carrier lookup
-   Lead intent prediction
-   External data enrichment

------------------------------------------------------------------------

# Possible Future Enhancements

Potential improvements include:

-   Email MX record verification
-   Phone carrier validation
-   CRM integration (Salesforce, HubSpot)
-   Custom scoring rules
-   Machine learning based scoring
-   Web interface

------------------------------------------------------------------------

# Tech Stack

-   Python
-   Pandas
-   NumPy
-   FuzzyWuzzy
-   python-Levenshtein
-   Jupyter Notebook

------------------------------------------------------------------------

# License

MIT License

------------------------------------------------------------------------

# Summary

Lead Quality Engine is a lightweight data validation and prioritization
pipeline designed to help sales teams identify high-quality prospects
quickly and efficiently.

By automating lead verification and ranking, teams can reduce time spent
filtering data and focus on high-value outreach.
