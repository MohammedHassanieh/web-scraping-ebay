# Web-Scraping-Automation-2

## eBay Tech Deals Data Pipeline

## Overview

This project builds a complete data pipeline that scrapes, processes, and analyzes technology deals from the eBay Global Tech Deals page.

The system continuously collects product data, cleans the dataset, and performs exploratory data analysis (EDA) to find patterns in pricing, discounts, and shipping options.


## Methodology

### 1. Web Scraping

A Selenium-based scraper (scraper.py) was created to extract product information from the eBay Global Tech Deals page.

The scraper collects the following fields:

- timestamp
- title
- price
- original_price
- shipping
- item_url

The script scrolls through the page to trigger lazy loading so that all product cards are loaded.

The collected data is appended to:
ebay_tech_deals.csv


### 2. Automation with GitHub Actions

The scraper is automated using GitHub Actions and runs every 3 hours.

Cron schedule used:
0 */3 * * *

Each run adds new deals to the dataset, allowing the project to build time-series data over multiple runs.


### 3. Data Cleaning

The script clean_data.py processes the raw data by:

- Removing "US $" and commas from price values
- Converting prices to numeric format
- Handling missing original_price values
- Cleaning missing shipping values
- Creating a new column called discount_percentage

The cleaned dataset is saved as:
cleaned_ebay_deals.csv


### 4. Exploratory Data Analysis

EDA was performed in the notebook:
EDA.ipynb

The analysis includes:

- Time series analysis of deals per hour
- Price distribution
- Original vs discounted price comparison
- Discount percentage distribution
- Shipping option frequency
- Keyword analysis in titles
- Price difference analysis
- Top 5 highest discounts

Visualizations were created using Matplotlib and Seaborn.


## Key Findings

Some general observations:

- Most deals fall within a specific price range.
- Many products have large discounts compared to original price.
- Some keywords and brands (like Apple and Samsung) appear frequently.
- Free shipping is the most common shipping option.


## Challenges Faced

Several issues were encountered:

- The page loads dynamically, so scrolling was required.
- Selenium sometimes loaded a different layout than the browser.
- Some product cards were missing fields, so validation was needed.


## Possible Improvements

Future improvements may include:

- Removing duplicate products between runs
- Collecting more fields like rating or reviews
- Running the scraper longer for better trend analysis
- Using an API instead of scraping if available


## Technologies Used

- Python
- Selenium
- Pandas
- Matplotlib
- Seaborn
- GitHub Actions
