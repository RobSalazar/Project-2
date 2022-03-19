# Average Housing Price vs Unemployment Rates in the United States
<p align="center">
  <img src="https://github.com/RobSalazar/Project-2/blob/main/images/house_price.PNG" />
</p>

## Purpose
The purpose of this project was to demonstrate our interpretation of the ETL process. For this, housing price data was obtained from [Zillow](https://www.zillow.com/research/data/) and the unemployment data was gathered from the [Bureau of Labor Statistics](https://www.bls.gov/web/laus.supp.toc.htm). We believed there could be an interesting connection between the prices of houses across the United States and how unemployment rates may or may not have some kind of effect on price.
Once gathered the data was cleaned using python code implementing the pandas module. Afterword, the data was uploaded into a structured database. The reasoning behind this was the fact that strucured databases have been around for longer and have a more diverese pool of tools available for modeling and analysis.
- - -
![etl_process.jpg](https://irt.rowan.edu/_images/banners/catalog/etl-banner.jpg)
## Process
 ![erd.PNG](https://github.com/RobSalazar/Project-2/blob/main/images/ERD.png)
 
Listed below are the summarized steps we followed in order to extract, transform, and load our data:
* It was important for us to begin with figuring out which question we could come up with that could lead to intersting analysis and models.
* Our Zillow housing data was a large file in .csv format so we reigned in the most intersting months available and got rid of the rest.
* Similarly, the BLS data had a range going back as far as 1976 so the data was also trimmed on the front end to match our housing data and was converted into a .csv.
* The final dataset was created when we realized we needed to change our state names to abbreviations; to do this we found this [github](https://gist.githubusercontent.com/mshafrir/2646763/raw/8b0dbb93521f5d6889502305335104218454c2bf/states_titlecase.json) and we made a json request to get this.
* Pandas python module was used to further format, rearrange, and to save new clean .csv files from the dataframes we created.
* We then imported the clean and ready dataframes into a PostgreSQL database using Pandas.

Here are the before and afters for how our data looked before transforming with pandas:
* Zillow [Before](https://github.com/RobSalazar/Project-2/blob/main/data/original/zillow_data.csv) and [After](https://github.com/RobSalazar/Project-2/blob/main/data/zillow.csv)
* BLS unemployment data [Befpre](https://github.com/RobSalazar/Project-2/blob/main/data/original/state_unem_rate.csv) and [After](https://github.com/RobSalazar/Project-2/blob/main/data/unemployment_pivot.csv)
* State name abbreviations[Before](https://gist.githubusercontent.com/mshafrir/2646763/raw/8b0dbb93521f5d6889502305335104218454c2bf/states_titlecase.json)and [After](https://github.com/RobSalazar/Project-2/blob/main/data/state_abbreviations.csv)

The data files were subjected to various forms of transformations through such as: merges, group bys, pivots, column renaming and rearranging, and trimming all through the power of Pandas! Don't believe me? Take a [look](https://github.com/RobSalazar/Project-2/blob/main/data_cleaning.ipynb) for yourself.
