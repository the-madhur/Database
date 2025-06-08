### 🔹 What is `DISTINCT` in SQL?

The `DISTINCT` keyword is used to **remove duplicate values** from the result set of a `SELECT` query.

---

### ✅ **Syntax**

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

- It returns **only unique combinations** of the specified columns.

---

### 🔹 Example Table: `workers`

| Firstname | Gender |
| --- | --- |
| Sophie | Female |
| Raman | Male |
| Gautam | Male |
| Ayush | Male |
| Shivam | Male |

---

### 🔸 1. **Single Column DISTINCT**

```sql
SELECT DISTINCT Gender FROM workers;
```

🟢 **Output:**

Gender

---

Female

---

Male

---

- **Explanation**: Returns only unique values from the `Gender` column.

---

### 🔸 2. **Multiple Columns DISTINCT**

```sql
SELECT DISTINCT Firstname, Gender FROM workers;
```

- Returns unique **row combinations** of `Firstname` and `Gender`.

---

### ⚠️ Important Notes

- `DISTINCT` applies to **all selected columns**.
- If any **column combination is unique**, it is considered **distinct**.
- `DISTINCT` can **slow down performance** if used on large datasets—use it only when needed.

---

### 🔍 Tip

If you're just checking how many **unique values** are there, combine `DISTINCT` with `COUNT()`:

```sql
SELECT COUNT(DISTINCT dept_id) FROM workers;
```

---

## ✅ Summary

| Feature | Description |
| --- | --- |
| `DISTINCT` usage | Removes duplicate rows |
| Works on | Single or multiple columns |
| Common with | `SELECT`, `COUNT`, `ORDER BY` |
| Don't use when | You want **all rows**, including duplicates |