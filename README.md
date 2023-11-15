# GROUP 6 - dillards-project

## Weekly updates

### Team members:
* Muhammet Ali Büyüknacar
* Zhiwei Gu
* Jialong (Mark) Li
* Siyan Li

### Week1 -> Oct.13

- Set up Github repo
- Connected to the NU resource servers
- Uploaded datasets into database schema
- Figured out SQL connection in Python
- Explored datasets in Python and R

  deptinfo: 60 rows, 2 columns

  skstinfo: 39230146 rows, 4 columns. There is no null values. For COST, mean 24.16, min 0.00, median 15.36, max 2700.00. For RETAIL, mean 43.33, min 0.00, median 24.50, max 6017.00.
  There are 3423 SKU with COST equals to 0, but when COST is 0, RETAIL might not be 0. The correlation between COST and RETAIL is 0.896.
  For difference between COST and RETAIL, mean 19.17, min -864.18, median 9.75, max 3977.46.

  skuinfo: include 8148 rows with extra columns. Since the number of rows with extra column is relatively small compared with total number of rows, it is reasonable to drop these.
  After dropping, there are 1556030 rows, 10 columns, there is no null values.

  strinfo: 453 rows, 4 columns


### Week2: -> Oct.20
- Figured out the correct sequence of columns in the csv files and successfully set primary keys and correct data type for all SQL tables. Maked sure that there are no duplicated primary keys.
- Dropped all unknown columns that do not appear on the schema from all SQL tables.
- Brainstormed on business and further analysis questions, can be seen on Analysis and Business Questions.Rmd
- Come up with ways to incorporate external data to enrich the dataset: state population data, weather, holiday, weekend. Can be seen on External Data and Domain Info.Rmd
- Imported states.csv to the database to access the region and division of a state
- Continued data exploration and data cleaning
- Uploaded a "DatasetGenerator" R file, to write out after-cleanning or after-sampling dataset.

  dept-sku: merge dept with sku dataset, perform exploration on each column. We generated bar plots to visualize the distribution of the number of rows within each DEPT, STYLE, COLOR, SIZE, VENDOR, and BRAND. Most of these bar plots skew to the right, with a majority of relatively low values with a few exceptionally high values. COLOR and SIZE column have many similar values, so they require further grouping if needed in the analysis.

  skstinfo: created histogram between number of SKU in each store, the distribution is relatively normal, the mean is 109888.36 and the median is 114042.00

  strinfo: merge with outside dataset on state region and division, find number of stores in each state, region, division. Most stores are in the South region.

  trnsact: sample 1/1000 from original dataset, column 9 and 10 are exactly the same, column 13 is binary without clear meaning, so drop column 10 and 13. Rename remaining columns, the order from the data schema is incorrect. Plot the relationship between ORIGPRICE and AMT, and the correlation is 0.80320634. In over 50% of cases, ORIPRICE > AMT, so calculate discount from AMT / ORIGPRICE. A minority of rows have AMT > ORIPRICE which requires further investigation. 

### Week3: -> Oct.27

- Proposed a new business question that will be consulted to the Professor and the TA

**Classifying the transactions with high chance of return**

The reason of a refund for a product can depend on many reasons such as a defected product supplied by the vendor, the time/season of the purchase, change in the price point after the sale, products that it was bought together with external economic factors or any other product specification. This would allow the firm to have a better understanding of the returns with a help of an explainable model and the inventory management can be managed according to this. The classification will be based on whether the product will be returned or not.

- Brainstormed about possible features and transformations

Mapping colors into higher groups

ProductID / Vendor / Brand / Department

Discount Flag / Price Difference

Sale Date / Holiday&Weekend Flag

Store Number / City Location / ZIP Code

Date Difference (RefundDate - SaleDate)

Dependent Variable: Return Flag (0/1)

Grouping Sale and Refund data and transforming it in a way that it could be fed to a classification model


### Week4: -> Nov.03

- Discussing the business problem with the professor and the TA
- Catch up on the feature transformations that are delegated among the group
- Explore other features that could be useful for the model and feature importance
- Look for ways to find out pairs of Sale and Return of a single transaction-possibly by a same ID such as transactionID
- Did EDAs for features that we want to use to find out whether a transaction would be returned
- Discussed about the possible benefits of solving our proposed business problems
- Cleaned the color names on SKUINFO table and did an LLM demo to map the specific colors to higher groups on "Color Grouping.ipynb" file
- Created weekend_flag, holiday_flag features, join location and cost into transaction table 

### Week5: -> Nov.10

- Continue to work on our current business problem, cousult with professor and TA
- Cleaned color names, group colors into 13 big categories
- Compared weekday vs weekend_flag vs holiday_flag and state vs region, select more appropriate features for modeling
- Managed to work out the sale-and-return pairs based on non-zero "InterID", and create a full table of all transactions with non-zero "InterID" joining with all other tables for future use.
- Constructed a query to match refunds and purchases


### Week6: -> Nov.17

- Continue to work on our current business problem
- Conduct literature review to explore method of useful
- Consider grouping other features such as size, department for modeling

Business Assumpation:
Revenue = AMT - COST
If AMT < ORGPRICE, the product is on sale (discount).

