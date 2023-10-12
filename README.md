# GROUP 6 - dillards-project

## Weekly updates

### Oct 13

- Set up Github repo
- Connected to the NU resource servers
- Uploaded datasets into database schema
- Explored datasets in Python and R

  deptinfo: 60 rows, 2 columns

  skstinfo: 39230146 rows, 4 columns. There is no null values. For COST, mean 24.16, min 0.00, median 15.36, max 2700.00. For RETAIL, mean 43.33, min 0.00, median 24.50, max 6017.00.
  There are 3423 SKU with COST equals to 0, but when COST is 0, RETAIL might not be 0. The correlation between COST and RETAIL is 0.896.
  For difference between COST and RETAIL, mean 19.17, min -864.18, median 9.75, max 3977.46.

  skuinfo: include 8148 rows with extra columns. Since the number of rows with extra column is relatively small compared with total number of rows, it is reasonable to drop these.
  After dropping, there are 1556030 rows, 10 columns, there is no null values.

  strinfo: 453 rows, 4 columns

Next week:
- Finish uploading datasets into database schema
- Figure out SQL connection in Python
- Come up with business questions
- Continue data exploration and data cleaning
