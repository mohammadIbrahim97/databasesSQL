# databasesSQL
## Keys in SQL
Primary key:  is alwys not NULL and must contain a value.

´´´ SQL
Create tabele if exist Employee (
    Employee_id SERIAL Primary key,
    name VARCHAR(50)
  )

´´´

## Composite Key

´´´SQL
CREATE TABLE ORDERS (

    order_ID SERIAL,
    customer_ID INT,
    Primary KEY (order_ID, customer_ID)
  )
´´´

## Constraints in SQL

Forign Key: is a column that establish a linke between Two Tables. It ensure referential integrity by making sure that the value in the
Forign key column exists in the referenced Primary key column.

´´´SQL
CREATE TABLE ORDERS (
    order_ID SERIAL PRIMARY KEY,
    customer_ID int,
    order_data DATE,
    FOREIGN KEY (customer_ID ) REFERENCES Employee (Employee_id)
  )
  ´´´

## UNIQUE Constraint
A UNIQUE Constraint ensure that all values in a column are distinct.

´´´SQL
CREATE TABLE IF NOT EXISTS Employee (
    Employee_id SERIAL PRIMARY KEY,
    email VARCHAR(50) UNIQUE,
    name VARCHAR(50),
    department VARCHAR(50)
  )
´´´

## Check Constraint

´´´SQL
CREATE TABLE IF NOT EXISTS Employee(
    Employee_id SERIAL PRIMARY Key,
    email VARCHAR() UNIQUE,
    age INT CHECK (age >= 18),
    phone INT UNIQUE,
    name VARCHAR(50),
    department VARCHAR(50),
    UNIQUE (email, phone)
  );
  ´´´

# Updata data from a table

table name: people

| person_id      | name           |
| :------------- | :------------- |
|      1         | John Doe       |
