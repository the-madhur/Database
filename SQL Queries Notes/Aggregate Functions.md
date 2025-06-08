# 📘 Aggregate Queries in MySQL

Aggregate functions perform **calculations on multiple rows** and return a **single result**.

---

### 🔹 1. `MAX()` – Maximum Value

```sql
SELECT MAX(rental_duration) FROM film;
```

- ✅ **Purpose**: Finds the **highest value** in the `rental_duration` column.
- 🔸 **Output**: `7`
- 📌 **Use Case**: To find the **longest rental duration** of any film.

---

### 🔹 2. `MIN()` – Minimum Value

```sql
SELECT MIN(rental_duration) FROM film;
```

- ✅ **Purpose**: Finds the **lowest value** in the `rental_duration` column.
- 🔸 **Output**: `3`
- 📌 **Use Case**: To find the **shortest rental duration** among all films.

---

### 🔹 3. `AVG()` – Average Value

```sql
SELECT AVG(rental_duration) FROM film;
```

- ✅ **Purpose**: Calculates the **average** of all `rental_duration` values.
- 🔸 **Output**: `4.9850`
- 📌 **Use Case**: To get an idea of the **typical rental duration**.

---

### 🔹 4. `SUM()` – Total Sum

```sql
SELECT SUM(rental_duration) FROM film;
```

- ✅ **Purpose**: Returns the **total sum** of all values in the column.
- 🔸 **Output**: `4985`
- 📌 **Use Case**: To know the **combined total rental duration** across all films.

---

### 🔹 5. `COUNT(DISTINCT ...)` – Count Unique Values

```sql
SELECT COUNT(DISTINCT DISTRICT) FROM address;
```

- ✅ **Purpose**: Counts the **number of unique values** in the `DISTRICT` column.
- 🔸 **Output**: `378`
- ⚠️ **Common Error**:  
  Avoid typos like `DISCTRICT` which will give an error.

---

### 🔹 6. `COUNT(*)` – Total Rows

```sql
SELECT COUNT(*) FROM address;
```

- ✅ **Purpose**: Counts **all rows** in the `address` table.
- 🔸 **Output**: `603`
- 📌 **Use Case**: To find the **total number of addresses**.

---

## ✅ Summary Table

| Function              | Purpose                  | Example                      |
|-----------------------|--------------------------|------------------------------|
| `MAX(column)`         | Finds highest value      | `MAX(rental_duration)`       |
| `MIN(column)`         | Finds lowest value       | `MIN(rental_duration)`       |
| `AVG(column)`         | Calculates average       | `AVG(rental_duration)`       |
| `SUM(column)`         | Adds all values          | `SUM(rental_duration)`       |
| `COUNT(*)`            | Counts all rows          | `COUNT(*)`                   |
| `COUNT(DISTINCT col)` | Counts unique values     | `COUNT(DISTINCT district)`   |
