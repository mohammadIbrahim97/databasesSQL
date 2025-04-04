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


## Update data in a table

**Table name**: `people`

| person_id | name      |
|-----------|-----------|
| 1         | John Doe  |

---

<<<<<<< HEAD
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

```SQL
-- Show all columns from the products table
SELECT * FROM products;
```

### **Selecting Specific Columns**

```SQL
-- Show only product_name and brand_name columns
SELECT product_name, brand_name FROM products;
```

### **Selecting Specific Columns in a Different Order**

```SQL
-- Show brand_name first, followed by product_name
SELECT brand_name, product_name FROM products;
```

### **Creating a New Column with Mathematical Functions (Discounted Amount)**

```SQL
-- Calculate discounted_amount as the difference between marked_price and discounted_price
SELECT product_name, brand_name, marked_price, discounted_price, marked_price - discounted_price AS discounted_amount
FROM products;
```

### **Creating a New Column with Mathematical Functions (Rating Filter)**

```SQL
-- Calculate rating_filter by multiplying rating and rating_count
SELECT product_name, brand_name, rating, rating_count, rating * rating_count AS rating_filter
FROM products;
```

### **Creating a New Column with Mathematical Functions (Discount Percentage)**

```SQL
-- Calculate discounted_percent as the percentage discount
SELECT product_name, brand_name, marked_price, discounted_price, ((marked_price - discounted_price) / marked_price) * 100 AS discounted_percent
FROM products;
```

### **Finding Unique Values**

```SQL
-- Find unique brand_names in the products table
SELECT DISTINCT(brand_name) AS unique_brands
FROM products;
```

### **Adding a WHERE Clause**

```SQL
-- Show products with marked_price and discounted_price from Adidas brand
SELECT product_name, brand_name, marked_price, discounted_price
FROM products
WHERE brand_tag = 'Adidas';
```

### **Using DISTINCT with WHERE (Unique Products Served by Adidas)**

```SQL
-- Show distinct product_tags associated with Adidas brand
SELECT DISTINCT(product_tag), brand_name
FROM products
WHERE brand_tag = 'Adidas';
```

### **Counting Distinct Values**

```SQL
-- Count distinct product_tags associated with Adidas brand
SELECT COUNT(DISTINCT(product_tag))
FROM products
WHERE brand_tag = 'Adidas';
```

### **Using Multiple Conditions with AND**

```SQL
-- Show Adidas products with discounted_price greater than 5000
SELECT product_name, brand_name, marked_price, discounted_price
FROM products
WHERE brand_tag = 'Adidas' AND discounted_price > 5000;

-- Show products with discounted_price between 5000 and 8000
SELECT product_name, brand_name, marked_price, discounted_price
FROM products
WHERE discounted_price BETWEEN 5000 AND 8000;
```

### **Adding More Filters**

```SQL
-- Show Adidas products with discounted_price between 5000 and 8000, rating > 4, and rating_count > 10
SELECT product_name, brand_tag, marked_price, discounted_price
FROM products
WHERE (discounted_price BETWEEN 5000 AND 8000)
    AND brand_tag = 'Adidas'
    AND rating > 4
    AND rating_count > 10;
```

### **Using OR Condition**

```SQL
-- Show products from Adidas or Puma brands with discounted_price between 3000 and 5000
SELECT product_name, product_tag, brand_tag, discounted_price
FROM products
WHERE (brand_tag = 'Adidas' OR brand_tag = 'Puma') AND discounted_price BETWEEN 3000 AND 5000;
```

### **Using NOT Condition**

```SQL
-- Show products not from Adidas or Puma brands with discounted_price between 3000 and 5000
SELECT product_name, product_tag, brand_tag, discounted_price
FROM products
WHERE NOT (brand_tag = 'Adidas' OR brand_tag = 'Puma') AND discounted_price BETWEEN 3000 AND 5000;
```

### **Using IN Condition**

```SQL
-- Show products from Adidas or Puma brands with discounted_price between 3000 and 5000
SELECT product_name, product_tag, brand_tag, discounted_price
FROM products
WHERE brand_tag IN ('Adidas', 'Puma') AND discounted_price BETWEEN 3000 AND 5000;
```

### **Using NOT IN Condition**

```SQL
-- Show products not from Adidas or Puma brands with discounted_price between 3000 and 5000
SELECT product_name, product_tag, brand_tag, discounted_price
FROM products
WHERE brand_tag NOT IN ('Adidas', 'Puma') AND discounted_price BETWEEN 3000 AND 5000;
```
