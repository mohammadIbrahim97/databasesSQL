Klar! Ich habe dein Markdown überarbeitet und korrigiert – inklusive Grammatik, SQL-Syntax und Formatierung. Schau dir das Ergebnis hier an:

---

# Databases: SQL

## Keys in SQL

**Primary Key**: A primary key is always `NOT NULL` and must contain a unique value.

```sql
CREATE TABLE IF NOT EXISTS Employee (
    Employee_id SERIAL PRIMARY KEY,
    name VARCHAR(50)
);
```

## Composite Key

A **composite key** is a combination of two or more columns used to uniquely identify a row.

```sql
CREATE TABLE IF NOT EXISTS Orders (
    order_ID SERIAL,
    customer_ID INT,
    PRIMARY KEY (order_ID, customer_ID)
);
```

## Constraints in SQL

**Foreign Key**: A foreign key is a column that establishes a link between two tables. It ensures referential integrity by making sure that the value in the foreign key column exists in the referenced primary key column.

```sql
CREATE TABLE IF NOT EXISTS Orders (
    order_ID SERIAL PRIMARY KEY,
    customer_ID INT,
    order_date DATE,
    FOREIGN KEY (customer_ID) REFERENCES Employee(Employee_id)
);
```

## UNIQUE Constraint

A **UNIQUE** constraint ensures that all values in a column are distinct.

```sql
CREATE TABLE IF NOT EXISTS Employee (
    Employee_id SERIAL PRIMARY KEY,
    email VARCHAR(50) UNIQUE,
    name VARCHAR(50),
    department VARCHAR(50)
);
```

## CHECK Constraint

The **CHECK** constraint is used to limit the range of values for a column.

```sql
CREATE TABLE IF NOT EXISTS Employee (
    Employee_id SERIAL PRIMARY KEY,
    email VARCHAR(50) UNIQUE,
    age INT CHECK (age >= 18),
    phone BIGINT UNIQUE,
    name VARCHAR(50),
    department VARCHAR(50),
    UNIQUE (email, phone)
);
```



---

## Update data in a table

**Table name**: `people`

| person_id | name      |
|-----------|-----------|
| 1         | John Doe  |

---

```sql
Update people
SET name = "Mohammad" WHERE person_id = 1;
```
**Table name**: `people`

| person_id | name      |
|-----------|-----------|
| 1         | Mohammad  |


*Conclusion:* The *UPDATE* in SQL is powerful tool for modifying existing data in a table. it allows you to update specific rows based on conditions
and can be used to change multiple columns in a single statement using this examples, you can see how versatile and essential the update statement
is for maintaining and managing data your data in your database.

# Delete data from a table
## Syntax
```sql
DELETE FROM table_name
WHERE condition;
```

*example:*
```SQL
DELETE FROM people where person_id = 1;
```

# SQL in ACTION
### **Dataset Overview: Products Table**

Consider a hypothetical dataset named products containing information about various products. Each product has attributes such as product_name, brand_name, marked_price, discounted_price, rating, rating_count, brand_tag, and product_tag.

### **Query Examples:**

### **Displaying the Dataset**

```
-- Show all columns from the products table
SELECT * FROM products;
```

### **Selecting Specific Columns**

```
-- Show only product_name and brand_name columns
SELECT product_name, brand_name FROM products;
```

### **Selecting Specific Columns in a Different Order**

```
-- Show brand_name first, followed by product_name
SELECT brand_name, product_name FROM products;
```

### **Creating a New Column with Mathematical Functions (Discounted Amount)**

```
-- Calculate discounted_amount as the difference between marked_price and discounted_price
SELECT product_name, brand_name, marked_price, discounted_price, marked_price - discounted_price AS discounted_amount
FROM products;
```

### **Creating a New Column with Mathematical Functions (Rating Filter)**

```
-- Calculate rating_filter by multiplying rating and rating_count
SELECT product_name, brand_name, rating, rating_count, rating * rating_count AS rating_filter
FROM products;
```

### **Creating a New Column with Mathematical Functions (Discount Percentage)**

```
-- Calculate discounted_percent as the percentage discount
SELECT product_name, brand_name, marked_price, discounted_price, ((marked_price - discounted_price) / marked_price) * 100 AS discounted_percent
FROM products;
```
