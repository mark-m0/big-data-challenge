# big-data-challenge

This challenge takes in Big Data from Amazon and pushes it to an RDS database. 
Level 1 of the challenge is attempted and successfully run. 

The first step in this process is to create 2 RDS databases using AWS. This will help generate the databases in PostgreSQL. Initially, an attempt was made to put everything into a single database, but it was found that some users that purchased video games also purchased pet supplies. In order to accomodate this, a second database instance was instantiated.


2 review datasets are pulled in to 2 seperate Jupyter Notebooks. The first dataset looks at video game reviews. The second dataset looks at pet product reviews. Both datasets are read in. This involves defining the delimiter to be a tab and a header is identified. 

From here, the number of rows in each dataset were counted. The video game dataset contained 1,785,997 records, and the pet products dataset contained 2,643,619 records. The data types were then pulled out, showing that every value was read in as a string, which did not match the schema generated for our tables. As such, each column's data type was evaluated and changed into its respective type. The data types are then incorporated into the dataframe that will be utilized for the remainder of the code.


The columns are now pulled from this new dataframe into what will become the tables for our databases. The products table required unique product IDs and titles, which was straightforward on the video game set. The pet products contained multiple product IDs that were the same, but had different product titles. The first product ID and product description were kept. 

The customers column required a groupBy function and a renaming of the resulting row. Upon checking the data type on the newly generated row, it was generated to be a "bigint". The "cast" function was utilized to change this row back into a simple "int", as a "bigint" was unnecessary in this case.


At this point, the schema.sql file is put into the 2 databases to create the empty tables that will eventually hold our data.


Finally, configuration settings for the RDS are put together. In the final document, you will see that the password and AWS endpoint are both marked as "<REDACTED>" for the sake of security. The tables are then fed the data, creating production-ready tables for the 2 datasets.
