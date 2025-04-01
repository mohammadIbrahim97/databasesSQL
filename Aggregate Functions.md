# ***Aggregate Functions***

## `Count()`: counting Rows
**Example:** Finding the number of Products in dataset
To find the total number of product in a dataset, the `COUNT()` function is used. This function counts the number of rows that match a specific criteria.

```sql
SELECT count(*) as total_costs_of_products from Products;
```

```sql
-- This query counts the number of non-null product_name entire in the products table. If any product names are missing(null), they will not be included in the count.
SELECT count(product_name) as total_products FROM Products;
```
***********************************
## `AVG()`: Calculating the Average
*The AVG() function Calculates the average value of numeric column*

**Example:** Finding the average discounted price of Products.

```sql
SELECT AVG(discounted_price) AS Average_price FROM products;
```

## `MAX()`: Finding the Maximum value
The MAX() function returns the highest value in a column
**Example:** Finding the 
