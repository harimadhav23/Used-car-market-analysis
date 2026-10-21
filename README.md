# Used Car Market Analysis

## Project Overview

Used Car Market Analysis is an end-to-end data analytics project that
collects selected used-car listings from Cars24, cleans the scraped
data, and explores listing-price patterns across brands, cities, vehicle
age, kilometres driven, fuel type, and transmission.

> **Scope note:** This project uses selected listing pages, not the
> complete Cars24 inventory. Listed prices are asking prices, not
> verified transaction prices.

## Objectives

-   Collect selected Cars24 listings using Python.
-   Parse semi-structured HTML into a structured dataset.
-   Clean text, numeric, and categorical fields.
-   Create features such as car age and mileage/price categories.
-   Explore patterns using visualizations.
-   Answer business questions and develop data-supported
    recommendations.

## Tools and Technologies

-   Python
-   Requests --- retrieve webpage HTML
-   BeautifulSoup --- parse HTML listing cards
-   Pandas and NumPy --- data cleaning and analysis
-   Regular expressions (`re`) --- extract and normalize values
-   Matplotlib and Seaborn --- visualizations
-   Google Colab / Jupyter Notebook --- development environment

## Workflow

1.  Select brand- and city-specific Cars24 URLs.
2.  Fetch webpage HTML and check response status.
3.  Parse listing cards with BeautifulSoup.
4.  Store extracted records in a Pandas DataFrame and export the raw
    CSV.
5.  Clean text and categories, parse years/kilometres/prices, inspect
    missing values, and remove exact duplicates.
6.  Create features such as `Car_Age`, `KM_Category`, `Age_Category`,
    and `Price_Category` where available.
7.  Perform exploratory data analysis (EDA).
8.  Answer business questions and summarize recommendations.

## Dataset and Collection Scope

The collected sample contains **232 listings** across four brands:
Toyota, Hyundai, Tata, and Honda.

### Listings by city

  City          Listings
  ----------- ----------
  Hyderabad           80
  Bangalore           80
  Chennai             72
  Delhi                0

Delhi target URLs returned HTTP 404 during the recorded collection run.
Successful pages returned at most 20 listing-card containers per
brand-city URL, so the sample does not represent the complete inventory.

### Main fields

  Field                 Description
  --------------------- ----------------------------------------------
  `Car_Name`            Listing name / model and variant
  `Brand`               Vehicle brand
  `City`                Target city used for collection
  `Location`            Listing locality, when available
  `Model_Year`          Parsed model year
  `Kilometers_Driven`   Distance driven in kilometres
  `Fuel_Type`           Fuel category
  `Transmission`        Transmission category
  `Price`               Listed price converted to numeric rupees
  `Owner_Type`          Owner information, when available
  `URL`                 Source listing URL
  `Car_Age`             Derived vehicle age
  `KM_Category`         Derived mileage group
  `Age_Category`        Derived age group
  `Price_Category`      Derived price group
  `Price_per_10k_KM`    Derived price-to-distance ratio, if included

Missing `Owner_Type` values are retained as unavailable rather than
guessed. Exact columns depend on the final data-preparation notebook.

## Exploratory Data Analysis: 10 Visualizations

1.  Price distribution histogram.
2.  Model year distribution.
3.  Kilometres driven distribution.
4.  Average price by city.
5.  Average price by brand.
6.  Price distribution by fuel type.
7.  Price by transmission (manual vs automatic).
8.  Brand--city average price heatmap.
9.  Car age vs price scatter plot.
10. Kilometres vs price scatter plot and Pearson correlation.

## Business Questions

1.  Which city has the highest average listed price?
2.  Which brand has the highest average listed price?
3.  Which brand has the most listings?
4.  Which fuel type has the highest average listed price?
5.  What is the average listed price by transmission type?
6.  How does average price vary by vehicle-age category?
7.  What is the correlation between kilometres driven and listed price?
8.  Which brand has the highest average kilometres driven?
9.  Which city has the most listings?
10. Which brand--city combination has the highest average listed price?

## Key Findings from the Current EDA Run

The recorded notebook run reported these results for the collected
sample: - **Bangalore** had the highest average listed price among
observed cities: approximately **₹725,850**. - **Toyota** had the
highest average listed price among selected brands: approximately
**₹745,904**. - **Hyundai** had the most listings in the cleaned sample:
**60**. - Automatic listings averaged approximately **₹840,093**,
compared with approximately **₹570,281** for manual listings. - Pearson
correlation between kilometres driven and price was approximately
**−0.233**, a weak negative linear association. - **Toyota in
Bangalore** had the highest average price among observed brand--city
combinations: approximately **₹808,900**. - Hybrid listings had the
highest reported average price, but there were only four hybrid records,
so this result should be treated cautiously.

These findings are descriptive, not causal. Refresh them by rerunning
the EDA notebook against the final cleaned dataset.

## Business Recommendations

-   Compare vehicles within similar brand, model, age, mileage, fuel,
    and transmission groups.
-   Use city-specific benchmarks as a starting point, not as definitive
    market prices.
-   Consider distributions and group counts alongside averages.
-   Review missing values and outliers before drawing conclusions.
-   Expand collection coverage with pagination and valid URLs for
    additional cities.
-   Rerun collection and analysis periodically if tracking market
    changes.

## Limitations

-   Only selected listing pages were collected.
-   Delhi target URLs returned HTTP 404 in the recorded run.
-   Page depth was limited.
-   `Owner_Type` was unavailable in the scraped data.
-   Website HTML structure and selectors may change.
-   Listed prices may differ from final transaction prices.
-   Small categories and unequal group sizes make some averages less
    stable.
-   The sample may not represent the entire used-car market.

## Suggested Repository Structure

``` text
used-car-market-analysis/
├── README.md
├── scraping_and_cleaning.ipynb
├── eda_and_business_insights.ipynb
├── data/
│   ├── raw_used_cars.csv
│   └── cleaned_used_cars.csv
├── visualizations/
│   └── (exported EDA charts, if saved)
└── presentation/
    └── Used_Car_Market_Analysis_Presentation.pptx
```

Adjust filenames and folders to match the actual repository.

## How to Run

1.  Open the scraping and cleaning notebook in Google Colab or Jupyter
    Notebook.
2.  Run the cells in order to collect listings and create the cleaned
    CSV.
3.  Open the separate EDA notebook.
4.  Upload or select `cleaned_used_cars.csv`.
5.  Run all cells to generate visualizations, business-question answers,
    and insights.
6.  Review charts and results before using them in a report or
    presentation.

Respect website access rules, terms, and rate limits. Webpage structure
and availability can change, so scraping code may require maintenance.

## Future Enhancements

-   Add pagination and collect more listing pages.
-   Expand coverage to additional cities and brands.
-   Improve logging, retries, and data-quality checks.
-   Automate periodic collection and analysis.
-   Build an interactive Power BI dashboard.
-   Explore price prediction after collecting a sufficiently broad and
    representative dataset.

## Author

**Hari Madhav Konduru**

This project demonstrates a practical analytics workflow involving web
scraping, data cleaning, feature engineering, exploratory analysis,
visualization, and business interpretation.
