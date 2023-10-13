# GROUP 6 - dillards-project

## Weekly updates

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
- Come up with business questions
- Continue data exploration and data cleaning

Jialong (Mark):  
**Explore Databricks**  

As a software-as-a-service (SaaS) platform, Databrick offers cost-effective and convenient data science solutions, rapidly becoming one of the leading cloud-based data warehousing platforms. Compared to Snowflake, Databrick seamlessly integrates with Apache Spark for large-scale data processing and provides well-around support for entire machine learning lifecycle [1]. Given that we have a large dataset, and machine learning methods are required to include in our project, Databrick might be an ideal tool for us to achieve our objectives.  

**Reference**  
[1] [Why use Databricks for machine learning and deep learning?](https://docs.databricks.com/en/machine-learning/index.html)



