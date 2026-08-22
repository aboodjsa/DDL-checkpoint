##  Relational Database Model – SQL Checkpoint

This project implements a relational database model using **SQL** with constraints based om the actual given checkpoint requirements.

---

# Database Structure

The database contains **three tables**:

###  Customer Table

Stores customer information.

| Column        | Data Type    | Constraint  |
| ------------- | ------------ | ----------- |
| Customer_id   | VARCHAR2(20) | Primary Key |
| Customer_Name | VARCHAR2(20) | -           |
| Customer_Tel  | NUMBER       | -           |

---

###  Product Table

Stores product information.

| Column       | Data Type    | Constraint        |
| ------------ | ------------ | ----------------- |
| Product_id   | VARCHAR2(20) | Primary Key       |
| Product_name | VARCHAR2(20) | -                 |
| Price        | NUMBER       | CHECK (Price > 0) |

---

###  Orders Table

Stores orders made by customers.

| Column       | Data Type    | Constraint             |
| ------------ | ------------ | ---------------------- |
| Customer_id  | VARCHAR2(20) | Foreign Key → Customer |
| Product_id   | VARCHAR2(20) | Foreign Key → Product  |
| Quantity     | NUMBER       | -                      |
| Total_amount | NUMBER       | -                      |

- Composite Primary Key: (Customer_id, Product_id)

---

#  SQL Implementation

```sql
-- CUSTOMER TABLE
CREATE TABLE Customer (
    Customer_id   VARCHAR2(20) PRIMARY KEY,
    Customer_Name VARCHAR2(20),
    Customer_Tel  NUMBER
);

-- PRODUCT TABLE
CREATE TABLE Product (
    Product_id   VARCHAR2(20) PRIMARY KEY,
    Product_name VARCHAR2(20),
    Price        NUMBER CHECK (Price > 0)
);

-- ORDERS TABLE
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
```

---

#  Creating New Columns

### Create Category column in Product table

```sql
ALTER TABLE Product
ADD Category VARCHAR2(20);
```

### Create OrderDate column in Orders table with default value

```sql
ALTER TABLE Orders
ADD OrderDate DATE DEFAULT SYSDATE;
```

---

#  Notes

* **Primary Key:** Unique identifier for each record.
* **Foreign Key:** Link to another table.
* **Composite Primary Key:** Two columns combined identify unique record.
* `SYSDATE`: Automatically adds current date.

---

#  How to Execute

1. Open Oracle SQL Developer / SQL*Plus / SQL Online etc..
2. Execute the table creation queries.
3. Execute the ALTER TABLE statements.

---

Database Checkpoint Project

