# Analysis of rent-stabilized buildings with highest cap rates — 2020 to 2022
 
This repository contains data, analytic code, and findings on the capitalization rates of buildings across New York City. This is an important metric that is used to ascertain how much money a building is generating, and is used as a proxy for the riskiness of a real estate investment.


## Data

This analysis is based on three spreadsheets.

The spreadsheets come from the following sources:

  - [`acris_sales_2020-2022.csv`](data/acris_sales_2020-2022.csv): Raw data on 2,003 building sales in New York City from the years 2020-2022. These data are based on the BIP Database from the University Neighborhood Housing Program. 
  - [`file_201_data_sm_tract.csv`](file_201_data_sm_tract.csv): Raw data from the Tax Commission Income & Expenses forms, submitted by building owners to the tax commission seeking revisions on their tax payments. This file contains information from 26,887 forms submitted to the tax commission in the year 2021.
  - [`buildings addresses.csv`](data buildings addresses.csv): This raw data compiled from the New York Department of Finance contains the addresses for the 17 buildings found to have the highest cap rates across New York City. The data file also includes information on the dates these buildings were last sold, sales prices, and the limited liability companies (LLCs) they are registered under.


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

##### Part 3: Honing in on the buildings with the largest cap rates:

3A) Using this data on the 241 buildings in the dataset, we found that there was an average cap rate of 59%, but the top 17 buildings were the ones most responsible for raising the average higher. Within the dataset, buildings in Brooklyn have the overall highest cap rates, which we chose to zero in on.
  
3B) The first four buildings in this list stood out in particular for all having cap rates well-over 90%, which would suggest that the landlords should have been able to recover the cost of their investment within a year if accurate. In addition to the top four, the following thirteen all have cap rates over 10%, which is higher than the average that is usually considered profitable for investors.

3C) The top five buildings in this list share a set of commonalities: they were sold together on the same date (12/28/2020) potentially as a packet, and they are owned by a set of LLCs that share the same owners. This would suggest that the highest cap rates in the dataset are being driven largely by just one duo of landlords; Robert Izsak, who is included in the New York City Public Advocate's list of Worst Landlords in 2022, and Maxwell Rovt, the son of Alexander Rovt, a politically well-connected billionaire.

## Outputs

The output folder contains the merged data from the two spreadsheets, and the capitalization rate for 241 buildings represented on both sheets: output/capitalizationrates.csv. Another file, output/ResultsByBoro.csv contains the mean and median capitalization rates for buildings in this analysis, sorted by borough. The final folder out/allbuildingsplusbbl contains all of the building as well as “borough building lot” data.

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

- Python 3
- Pandas
- Jupyter Notebooks

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

This analysts serves as a previous one done in collaboration with Andrew Ancheta (andrew.ancheta@gmail.com): [https://github.com/2ndrew2ncheta/Advanced-Data-Group-Project-3](url)

Contact: 
  - Nicholas Morgan at nikolaimorgan@protonmail.com.
  - Impu Sehgal at impu.sehgal42@journalism.cuny.edu.
  - Jonnathan Pulla Velecela at j.pullavelecela32@journalism.cuny.edu. 
