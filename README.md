# geocrosswalk

This memo outlines the proposed purpose and structure of the `geocrosswalk` package.

The purpose of this package is to allow researchers to easily crosswalk their data from one geographic designation to another. Data can be transformed across geographic level for the same time period (e.g., census tract to census place), or transformed for the same geographic level across time (e.g. 2000 census tracts to 2010 census tracts).

## `convert_level`

The **convert_level** function will use crosswalks available publicly to approximate data from one geographic level (in the same vintage) to another. 
	
> **Usage Example**: A researcher has data at the Census Tract level that they would like to transform to the Census Place level. They would be able to use this function to transform their data. The input would be data at the 2010 tract level; the output would be data approximated at the 2010 place level.


Proposed parameters are:

  - **.data**: `data.frame` or `tibble`. 
  - **.from**: `character`specifying the geographic designation the data is currently in. See `geocrosswalk::supported_geos` for geographic options.
  - **.to**: `character`specifying the geographic designation the data will be transformed to. See `geocrosswalk::supported_geos`  for geographic options.
  - **.year**: `numeric` specifying the year of the geographic boundaries. Options include `1990`, `2000`, `2010`, and `2020`. 
  - **.weight**: `character` specifying what to use to represent the size of the intersection between `.from` and `.to` geographies. Options are `population`, `land areas`, and `housing units`. 
  - **.geoid**: `character` specifying the geographic ID of the `.from` geometry. 
  - **.count_variables**: `character` vector of variable names to adjust that represent `count` data. This represents any data that can be counted (e.g. 1 person, 2 people, ect.)
  - **.non_count_variables**: `character` vector of variable names to adjust that represent non-count data. This could represent data that is a median or average for a particular geography, or any statistic that cannot be counted. 
  - **.non_count_weights**: `character` vector of variable names that represent `count` metrics that can be used to weight the `.non_count_variables` during geographic conversion. For example, if the statistic is `median_household_income`, the `.non_count_weights` could be `total_households_reporting_income`. Vector must be in the same order as `.non_count_variables`.


## `standardize_time`

The **standardize_time** function will use crosswalks available publicly to approximate data from the same geographic level to a different year of release. 

> **Usage Example**: A researcher is doing a longitudinal analysis using data at the census tract level. The need to standardize their data over time as census tracts boundaries change. This function standardizes that data to reflect consistent boundaries over time. The input would be a census tract level dataset over time. The output would be that same dataset with standard boundaries over time.

Proposed parameters are:

- **.data**: `data.frame` or `tibble`.  `
- **.geography**: `character` geographic level of data. Current options are in `geocrosswalk::standard_geos`.
- **.from**: `numeric` geographic vintage of the original data. Current options are 1990, 2000, 2010, and 2020. If no years or multiple years provided, will do a check to determine what vintage geoids are most likely in.
- **.to**: `numeric` geographic vintage of the year you are standardizing to. 
- **.geoid**: `character` specifying the geographic ID of the `.from` geometry. 
- **.method**: method used to standardize data. Current options are `ltdb`, and `nhgis` for tracts, `nhgis` and `census` for all other geographies.
- **.count_variables**: `character` vector of variable names to adjust that represent `count` data. This represents any data that can be counted (e.g. 1 person, 2 people, ect.)
- **.non_count_variables**: `character` vector of variable names to adjust that represent `non-count` data. This could represent data that is a median or average for a particular geography, or any statistic that cannot be counted. 
 - **.non_count_weights**: `character` vector of variable names that represent `count` metrics that can be used to weight the `non_count_variables` during geographic conversion. For example, if the statistic is `median_household_income`, the `.non_count_weight` could be `total_households_reporting_income`.

## `guess_vintage`

This function will attempt to guess the geographic vintage of data.They can also check if data is a specific geographic vintage and guess the vintage by another variable (such as year).

> **Usage Example**: A researcher has data but is unclear about which geographic vintage the data is in. Will also be used internally as an input into the `standardize_time` function.

Proposed parameters are:

- **.data**: `data.frame` or `tibble`.  
- **.geography**: `character` geographic level of data. Current options are in `geocrosswalk::standard_geos`.
- **.geoid**: `character` specifying the variable name of the geographic ID to be checked.  
- **.by**: `character` specifying the name of the variable to run this guess by (such as a year variable)


