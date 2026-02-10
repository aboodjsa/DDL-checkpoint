## 📌 Relational Database Model – SQL Checkpoint

This project implements a relational database model using **SQL** with constraints based on the given checkpoint requirements.


 CUSTOMER TABLE
CREATE TABLE Customer (
    Customer_id   VARCHAR2(20) PRIMARY KEY,
    Customer_Name VARCHAR2(20),
    Customer_Tel  NUMBER
);

 PRODUCT TABLE
CREATE TABLE Product (
    Product_id   VARCHAR2(20) PRIMARY KEY,
    Product_name VARCHAR2(20),
    Price        NUMBER CHECK (Price > 0)
);

 ORDERS TABLE
CREATE TABLE Orders (
    Customer_id  VARCHAR2(20),
    Product_id   VARCHAR2(20),
    Quantity     NUMBER,
    Total_amount NUMBER,

    CONSTRAINT pk_orders PRIMARY KEY (Customer_id, Product_id),
    CONSTRAINT fk_orders_customer FOREIGN KEY (Customer_id)
        REFERENCES Customer(Customer_id),
    CONSTRAINT fk_orders_product FOREIGN KEY (Product_id)
        REFERENCES Product(Product_id)
);




  ADD Category column
ALTER TABLE Product
ADD Category VARCHAR2(20);

  ADD OrderDate column with default value
ALTER TABLE Orders
ADD OrderDate DATE DEFAULT SYSDATE;


# Notes

* **Primary Keys** uniquely identify records.
* **Foreign Keys** link tables together.
* **Composite Primary Key** means two columns together uniquely identify a record.
* `SYSDATE` automatically stores the current system date.

---

# How to Run

1. Open Oracle SQL Developer / SQL*Plus / any SQL Online tool.
2. Run the table creation scripts.
3. Run the ALTER TABLE commands.

---

# 👨‍💻 Author

**Abood Jamal**

Database Checkpoint Project
