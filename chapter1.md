

# 1 SELECT

# 2 WHERE
# 3 AND, OR, NOT
# 4 IN
```roomsql
SELECT * 
FROM sql_store.customers
WHERE first_name IN ('elka', 'ambur');
```
# 5 BETWEEN
# 6 LIKE
```roomsql
-- % any number of characters
SELECT * 
FROM sql_store.customers
WHERE last_name like '%b%';
```
```roomsql
-- _ single character
SELECT * 
FROM sql_store.customers
WHERE last_name like '_y';
```
# 7 REGEXP

```
-- ^ beginning
-- $ end
-- | logical or
-- [abcd]
-- [a-f]
```

```roomsql
SELECT * 
FROM sql_store.customers
WHERE last_name REGEXP 'ey$|on$';

```

```roomsql
---method1: use regex
--customers last name start with my or contains se
SELECT * 
FROM sql_store.customers
WHERE last_name REGEXP '^my|se';
```

```roomsql
--- method2: use like
SELECT * 
FROM sql_store.customers
WHERE last_name like '%se%' OR last_name LIKE 'my%';
```
```roomsql
--- last name contains b and followed by r or u
SELECT * 
FROM sql_store.customers
WHERE last_name REGEXP 'b[ru]';
```
# 8 NULL
```roomsql
SELECT * 
FROM sql_store.customers
WHERE phone IS NULL;
```
```roomsql
--- get the orders that are not shipped
SELECT * 
FROM sql_store.orders
WHERE shipped_date IS NULL;
```

# 9 ORDER BY
```roomsql
SELECT * 
FROM customers
ORDER BY first_name DESC
```
```roomsql
SELECT * 
FROM customers
ORDER BY state, first_name
```

```roomsql
SELECT * 
FROM sql_store.order_items
WHERE order_id = 2
ORDER BY quantity * unit_price DESC;
```

# 10 LIMIT
should always come at the end 
```roomsql
SELECT * 
FROM sql_store.customers
ORDER BY points DESC
LIMIT 3;
```