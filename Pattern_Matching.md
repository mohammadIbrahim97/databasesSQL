# Pattern Matching
## Understanding `LIKE` Operator

The most basic form of Pattern Matchingin SQL is through the `like` Operator. This Operator allows you to match a string against a Pattern using wildcard characters.

**wildcard**
`% (percent): matches any sequence of characters(including zero characters).`

`_ (Underscore): Matches any single character.`

**Syntax of `LIKE` Operator:**
```SQL
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE Pattern;
```

#### Finding Product where the Second character of Brand Name is 's'
```SQL
SELECT * FROM products where brand_name LIKE "_s%";
```
