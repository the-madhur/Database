# Multiple Joins

In SQL, **multiple joins** refer to the process of combining data from more than two tables based on related columns. You can use different types of joins (e.g., `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `FULL JOIN`, `CROSS JOIN`) to retrieve meaningful results.

### **Example Scenario**

Consider three tables:

1. **Customers** (`customer_id`, `name`)
2. **Orders** (`order_id`, `customer_id`, `order_date`)
3. **Products** (`product_id`, `order_id`, `product_name`)

### **Query using multiple joins**

```sql

SELECT
    c.customer_id,
    c.name,
    o.order_id,
    o.order_date,
    p.product_name
FROM Customers c
INNER JOIN Orders o ON c.customer_id = o.customer_id
INNER JOIN Products p ON o.order_id = p.order_id;

```

### **Explanation**

- `Customers` is joined with `Orders` using `customer_id`
- `Orders` is joined with `Products` using `order_id`
- Only matching records from all three tables are returned (`INNER JOIN`)

### **Other Join Types in Multiple Joins**

- Use `LEFT JOIN` if you want all customers, even those without orders.
- Use `RIGHT JOIN` if you want all products, even those without orders.
- Use `FULL JOIN` if you want all customers and all products, even if they don’t match.