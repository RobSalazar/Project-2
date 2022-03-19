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
* The final dataset was created when we realized we needed to change our state names to abbreviations; to do this we found this [github](https://gist.github.com/mshafrir/) and we made a json request to get this.
* Pandas python module was used to further format, rearrange, and to save new clean .csv files from the dataframes we created.
* We then imported the clean and ready dataframes into a PostgreSQL database using Pandas.

## Technical Reasonings
The transforming of the data began simple enough. We first pathed the .csv files to be able to read them in and create workable dataframes. From there a list of all the column dates were put into a list just in case they were needed in the future. After this, the main objective was to remove rows that were not needed and format the dataframe in a way that matched the data (loosely) to our unemplyment data. To do this we used the Pandas function 'transpose' to unstack and restack our data accordingly: for the unemployment data we used the pivot function to be able to match the housing data. From there we thought it wise to convert our current string format date into a datetime object to be usable in our database. The unemployment data also had its year and month columns converted into a datetime object for the same reason. Once we had the housing and unemployment data clean and ready we noticed that they used different methods to name the states, so we found a github belonging to Michael Shafrir, and used his uploaded .json to be able to create a reference between the state name and its abbreviation. Once all this was done we used psycopg2 and we created a path and engine to get our dataframes loaded into PostgeSQL. Indices were included for both the housing and unemployment data but deemed it unnecessary for the state abbreviations. Linked below is the jupyter notebook that we used to do all this on and some screenshots of our database after the upload was complete.

Here are the before and afters for how our data looked before transforming with pandas:
* Zillow [Before](https://github.com/RobSalazar/Project-2/blob/main/data/original/zillow_data.csv) and [After](https://github.com/RobSalazar/Project-2/blob/main/data/zillow.csv)
* BLS unemployment data [Before](https://github.com/RobSalazar/Project-2/blob/main/data/original/state_unem_rate.csv) and [After](https://github.com/RobSalazar/Project-2/blob/main/data/unemployment_pivot.csv)
* State name abbreviations[Before](https://gist.githubusercontent.com/mshafrir/2646763/raw/8b0dbb93521f5d6889502305335104218454c2bf/states_titlecase.json)and [After](https://github.com/RobSalazar/Project-2/blob/main/data/state_abbreviations.csv)

The data files were subjected to various forms of transformations through such as: merges, group bys, pivots, column renaming and rearranging, and trimming all through the power of Pandas! Don't believe me? Take a [look](https://github.com/RobSalazar/Project-2/blob/main/data_cleaning.ipynb) for yourself.
- - -
## End Result
Once we had enough fun transforming the data, we loaded our dataframes into our database where they can live rent free until and not worry about housing prices.
- - -
![housing_data_db.PNG](https://github.com/RobSalazar/Project-2/blob/main/images/housing_data_db.PNG)
![unemplyment_data_db.PNG](https://github.com/RobSalazar/Project-2/blob/main/images/unemplyment_data_db.PNG)
![state_abbrv_db.PNG](https://github.com/RobSalazar/Project-2/blob/main/images/state_abbrv_db.PNG)
