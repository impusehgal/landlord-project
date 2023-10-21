# Analysis of TK data set — MM/YYYY to MM/YYYY

This repository contains data, analytic code, and findings that support portions of the article, “[TKTKTKTK](https://www.google.com),” published Month Date, Year. Please read that article, which contains important context and details, before proceeding.

## Data

This analysis is based on three spreadsheets.

The spreadsheets come from the following sources:

  - [`acris_sales_2020-2022.csv`](data/acris_sales_2020-2022.csv): Raw data on 2,003 building sales in New York City from the years 2020-2022. These data are based on the BIP Database from the University Neighborhood Housing Program. 
  - [`file_201_data_sm_tract.csv`](file_201_data_sm_tract.csv): Raw data from the Tax Commission Income & Expenses forms, submitted by building owners to the tax commission seeking revisions on their tax payments. This file contains information from 26,887 forms submitted to the tax commission in the year 2021.
  -   - [`buildings addresses.csv`] This raw data compiled from the New York Department of Finance contains the addresses for the 17 buildings found to have the highest cap rates across New York City. The data file also includes information on the dates these buildings were last sold, sales prices, and the LLCs they are registered under.


These spreadsheets contain, among others, the following columns relevant to the analysis:

- `price_per_bldg` — The sale price of the buildings represented in the acris file.
- `TOTAL INCOME FROM REAL ESTATE` — The annual business income for building owners in the 201 file, including rents, billboards, and ancillary services. 
- `TOTAL EXPENSES` — The total annual expenses for owners represented in the 201 file, such as maintenance and management expenses.
- Borough, Block, and Lot: both files contain information on the BBL of each building, a unique identifier for property plots in New York City.



## Methodology

The notebook [101023_Fall Analysis.ipynb] performs the following analyses:

##### Part 1: Import and Cleaning Data

Both spreadsheets were imported into Python and cleaned of duplicates. Both files contained unexpected duplicates--perhaps due to erroneous filings or multiple sales within the two-year period. In order to simplify the analysis, we omitted these data using the drop_duplicates() function.

##### Part 2: Calculating the cap rates

The two data sets were merged into a single data frame for the 241 unique BBLs that are represented on both data sets. Buildings that do not have enough information to calculate a capitalization rate were dropped using the dropna() function. Using the combined dataframe, the columns for income, expenses, and building cost were used to calculate the capitalization ratio for each building, using the formula CR=(I-E)/PPE.

##### Part 3: Honing in on the buildings with the largest cap-rates


## Outputs

The notebooks output this spreadsheet which contains TKTK: [`output/tktktk.csv`](output/tktktk.csv).

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

- Python 3
- Pandas
- Jupyter Notebooks

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact: 
  - Nicholas Morgan at nikolaimorgan@protonmail.com.
  - Impu Sehgal at impu.sehgal42@journalism.cuny.edu.
  - Jonnathan Pulla Velecela at j.pullavelecela32@journalism.cuny.edu. 
