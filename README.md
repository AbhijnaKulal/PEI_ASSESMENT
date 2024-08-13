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


