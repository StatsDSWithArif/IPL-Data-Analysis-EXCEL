# SQL Short Notes

---

## 1. GROUP BY
Groups rows with the same value into one row, so you can apply aggregate functions (SUM, COUNT, AVG, MAX, MIN) on each group.

```sql
SELECT department, COUNT(*) 
FROM employees
GROUP BY department;
```
👉 **Rule:** Every non-aggregated column in SELECT must be in GROUP BY.
👉 Use **HAVING** to filter groups (not WHERE).

```sql
SELECT department, AVG(salary)
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

---

## 2. SUBQUERIES
A query inside another query. Runs first, result used by outer query.

**Types:**
- **Single-row** → returns 1 value (`=`, `>`, `<`)
- **Multi-row** → returns many values (`IN`, `ANY`, `ALL`)
- **Correlated** → inner query depends on outer query row

```sql
-- Simple subquery
SELECT name FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

-- Correlated subquery
SELECT e1.name FROM employees e1
WHERE salary > (SELECT AVG(salary) FROM employees e2 
                WHERE e2.department = e1.department);
```
👉 Subquery in FROM = "derived table". Subquery in SELECT = "scalar subquery".

---

## 3. JOINS
Combine rows from two or more tables based on a related column.

| Join Type | What it does |
|---|---|
| **INNER JOIN** | Only matching rows in both tables |
| **LEFT JOIN** | All rows from left + matched from right (NULL if no match) |
| **RIGHT JOIN** | All rows from right + matched from left |
| **FULL JOIN** | All rows from both, matched where possible |
| **SELF JOIN** | Table joined with itself |
| **CROSS JOIN** | Every row of table A with every row of table B |

```sql
SELECT a.name, b.department
FROM employees a
INNER JOIN departments b ON a.dept_id = b.id;
```

---

## 4. WINDOW FUNCTIONS
Perform calculations **across a set of rows related to the current row**, without collapsing rows (unlike GROUP BY).

Syntax: `FUNCTION() OVER (PARTITION BY ... ORDER BY ...)`

```sql
SELECT name, department, salary,
       RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS rnk
FROM employees;
```

**Common window functions:**
- `ROW_NUMBER()` – unique sequential number
- `RANK()` – rank with gaps for ties
- `DENSE_RANK()` – rank without gaps
- `SUM()/AVG()/COUNT() OVER()` – running totals/averages
- `LEAD()/LAG()` – next/previous row value

👉 **PARTITION BY** = like GROUP BY but doesn't merge rows.

---

## 5. CTE (Common Table Expression)
A temporary named result set, defined using `WITH`, used to make complex queries simpler and readable.

```sql
WITH high_earners AS (
    SELECT name, salary FROM employees WHERE salary > 60000
)
SELECT * FROM high_earners WHERE salary < 100000;
```
👉 Exists only for that one query. Can chain multiple CTEs with commas.

---

## 6. RECURSIVE CTE
A CTE that **refers to itself**, used for hierarchical/tree data (like org charts, categories, number series).

**Structure:**
1. **Anchor member** – base result (starting point)
2. **Recursive member** – refers back to CTE, repeats until no more rows
3. **UNION ALL** joins them

```sql
WITH RECURSIVE emp_hierarchy AS (
    -- Anchor: top-level manager
    SELECT id, name, manager_id
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    -- Recursive: find employees reporting to previous level
    SELECT e.id, e.name, e.manager_id
    FROM employees e
    INNER JOIN emp_hierarchy eh ON e.manager_id = eh.id
)
SELECT * FROM emp_hierarchy;
```
👉 Used for: org charts, category trees, generating number sequences.

---

## Quick Comparison Cheat Sheet

| Concept | Use case |
|---|---|
| GROUP BY | Summarize data into groups |
| SUBQUERY | Query inside a query |
| JOIN | Combine data from multiple tables |
| WINDOW FUNCTION | Calculate across rows without collapsing them |
| CTE | Simplify complex/nested queries |
| RECURSIVE CTE | Handle hierarchical/tree-like data |
