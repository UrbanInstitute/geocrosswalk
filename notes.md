Vocabulary: 

* geo "unit" vs "level"?
* convert_geolevel() instead of convert_level()?
* "standardize" vs "harmonize"?
* harmonize_to() instead of standardize_time()?

Add section on 25 included census variables? 

One table for each geo? We would have X tables (number of supported geos). 

* var (rows)
* years (columns)
* census table:varname (cells)
* blank if not available
* _these would represent pulls from census, not conversions_


Documentation:

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
 
