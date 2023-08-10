## Vocabulary: 

* geo "unit" vs "level"?
* convert_geolevel() instead of convert_level()?
* "standardize" vs "harmonize"?
* harmonize_time_to() instead of standardize_time()?

## Add section on 25 included census variables? 

* table of usual suspects

One table for each geo? We would have X tables (number of supported geos). 

* var (rows)
* years (columns)
* census table:varname (cells)
* blank if not available
* _these would represent pulls from census, not conversions_

## recommend_methodology() Function

* from glevel; to glevel
* from year; to year

standardize place over time
* from_level = place
* to_level = place
* to_year = X
* from_year = 2010:2020? 

## Documentation:

* harmonization file sources
* harmonization methodologies
* how to document supported geos?
  - diagram
  - base unit (block or tract)
  - number in US
  - iq range of people per unit?
  - unsupported variables?
* census APIs
  - talk about differences between dicennial and acs vars, dicennial varname changes, etc. 

 
## Coverage Report: 

User gives:
* glevel (tract)
* years (2000-2010)
* vars (pop, pov, unempl)

Create a table of variable coverage.  

| **VAR**   | **2000** | **2001** | **2002** | **2003** | **2004** | **2005** | **2006** | **2007** | **2008** |
|:----------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
| **pop**    | X        |          |          |          |          | X        | X        | X        | X        |
| **pov**    | X        |          |          |          |          | X        | X        | X        | X        |
| **unempl** | X        |          |          |          |          | X        | X        | X        | X        |

