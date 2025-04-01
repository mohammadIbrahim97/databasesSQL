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

> Hinweis: Ich habe `phone` in `BIGINT` geändert, da Telefonnummern meist mehr Stellen haben als ein normaler `INT` speichern kann. Außerdem fehlte bei `VARCHAR()` die Länge – das habe ich ergänzt.

---

## Update data in a table

**Table name**: `people`

| person_id | name      |
|-----------|-----------|
| 1         | John Doe  |

---

Wenn du möchtest, kann ich auch noch `UPDATE`-Beispiele oder `INSERT`-Statements hinzufügen. Sag einfach Bescheid!
