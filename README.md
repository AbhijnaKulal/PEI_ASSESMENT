# PEI_ASSESMENT

This sales project contians the analysis of sales data using Tableau and the comprehensive document which has all the details
about the data, data model, data discrepancy and the sugegested data model.

Creating Order Table in SQL:
CREATE TABLE sales_order (
    Order_ID INT PRIMARY KEY,
    Item INT,
    Amount DECIMAL(10, 2),
    Customer_ID INT,
    FOREIGN KEY (Customer_ID) REFERENCES sales_customer(Customer_ID)
);

Creating sales_customer Table:
CREATE TABLE sales_customer (
    Customer_ID INT PRIMARY KEY,
    First VARCHAR(50),
    Last VARCHAR(50),
    Age INT,
    Country VARCHAR(50)
);

Creating sales_shipping:
CREATE TABLE sales_shipping (
    Shipping_ID INT PRIMARY KEY,
    Status VARCHAR(20),
    Customer_ID INT,
    FOREIGN KEY (Customer_ID) REFERENCES sales_customer(Customer_ID)
);


pyhton code to upload the data 

import pandas as pd
from sqlalchemy import create_engine
import os 
import json

print(os.getcwd())

# creating dataframes using the files provided
sales_customer =pd.read_csv('../customer.csv')
sales_order =pd.read_csv('../order.csv')
sales_shipping =pd.read_json('../shipping.json')


# Database connection
engine = create_engine('postgresql+psycopg2://username:password@localhost:5432/mydatabase')

# Append DataFrames to existing PostgreSQL tables
sales_customer.to_sql('orders', engine, if_exists='append', index=False)
sales_order.to_sql('customers', engine, if_exists='append', index=False)
sales_shipping.to_sql('sales_shipping', engine, if_exists='append', index=False)

print("DataFrames appended successfully!")


