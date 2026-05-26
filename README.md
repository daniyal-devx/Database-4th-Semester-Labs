# 🗄️ Database — 4th Semester Labs

> **BS Data Science | Fall 2024**  
> DDL · DML · Joins · Subqueries · Aggregate Functions · String Functions

---

## 👤 Author

**Daniyal Usman**  
Roll No: BSDSF24A025  
Program: BS Data Science (Fall 2024, Afternoon)  
GitHub: [@daniyal-devx](https://github.com/daniyal-devx)

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **SQLite** | Database engine |
| **DB Browser for SQLite** | GUI for writing & running queries |

---

## 📋 Labs Overview

| # | Lab | Topics Covered |
|---|-----|---------------|
| 02 | **DDL, DML & Constraints** | CREATE, INSERT, UPDATE, DELETE, FOREIGN KEY, CASCADE |
| 03 | **Schema Setup — EMP/DEPT** | Classic Oracle EMP dataset setup in SQLite |
| 04 | **Joins, Functions & DECODE** | INNER JOIN, String Functions, Math Functions, DECODE |
| 05 | **Subqueries, GROUP BY & Dates** | Subqueries, GROUP BY, HAVING, Self Join, Date Functions |

---

## 🔬 Lab Details

### Lab 02 — DDL, DML & Constraints

**Schema:** `STUDENTS` and `COURSES` tables

**Concepts covered:**
- `CREATE TABLE` with data types and constraints (`PRIMARY KEY`, `NOT NULL`, `FOREIGN KEY`)
- `ON DELETE CASCADE` behavior
- `INSERT`, `UPDATE`, `DELETE` operations
- `SELECT` with `WHERE`, `BETWEEN`, `IS NULL`

---

### Lab 03 — EMP/DEPT Schema Setup

**Schema:** Classic Oracle `EMP`, `DEPT`, `SALGRADE`, `BONUS` tables

This is the foundational dataset used in Labs 04 and 05. Includes 14 employees across 4 departments with salary grade ranges.

| Table | Rows | Description |
|-------|------|-------------|
| EMP | 14 | Employee records with job, salary, manager |
| DEPT | 4 | Department names and locations |
| SALGRADE | 5 | Salary grade ranges |
| BONUS | 0 | Bonus table (empty, for practice) |

---

### Lab 04 — Joins, String Functions & DECODE

**Concepts covered:**
- `INNER JOIN` using implicit syntax
- Cartesian product (cross join)
- Multi-table joins with conditions
- `ROUND()`, `TRUNC()`, `LOWER()` functions
- `DECODE` for conditional logic
- `DISTINCT`, `IS NOT NULL`

**Sample queries:**
```sql
-- Employee with their salary grade
SELECT e.ENAME, s.GRADE
FROM emp e, SALGRADE s
WHERE e.SAL BETWEEN s.LOSAL AND s.HISAL;

-- Annual salary rounded
SELECT ENAME, SAL, ROUND(SAL * 12, 0) AS "Annual Salary" FROM EMP;
```

---

### Lab 05 — Subqueries, GROUP BY & Date Functions

**Concepts covered:**
- Single-row and multi-row subqueries
- `ANY` / `ALL` operators
- Self join (employee ↔ manager)
- `GROUP BY` with `HAVING`
- `SUM()`, `AVG()`, `COUNT()`, `MAX()`
- `LAST_DAY()`, `ADD_MONTHS()` date functions
- `LPAD()`, `SUBSTR()`, `LENGTH()` string functions

**Sample queries:**
```sql
-- Employees earning more than avg salary of dept 20
SELECT ename, sal FROM emp
WHERE sal > (SELECT AVG(sal) FROM emp WHERE deptno = 20);

-- Total salary per department
SELECT d.dname, SUM(e.sal) AS "Total Salary"
FROM dept d, emp e
WHERE d.deptno = e.deptno
GROUP BY d.dname
ORDER BY "Total Salary" DESC;
```

---

## 📁 Repository Structure

```
Database-4th-Semester-Labs/
│
├── README.md
│
├── Lab-02/
│   ├── Lab_02.sql        ← DDL, DML, Constraints
│   └── Lab_2.db          ← SQLite database file
│
├── Lab-03/
│   ├── Lab_03.sql        ← EMP/DEPT schema + data
│   └── Lab_03.db         ← SQLite database file
│
├── Lab-04/
│   ├── Lab_04.sql        ← Joins, Functions, DECODE
│   └── Lab_04.db         ← SQLite database file
│
└── Lab-05/
    ├── Lab_05.sql        ← Subqueries, GROUP BY, Dates
    └── Lab_05.db         ← SQLite database file
```

---

## 🚀 How to Run

### Option 1 — DB Browser for SQLite (Recommended)
1. Download [DB Browser for SQLite](https://sqlitebrowser.org/)
2. Open the `.db` file for the lab you want
3. Go to **Execute SQL** tab
4. Paste queries from the `.sql` file and run

### Option 2 — Command Line (SQLite3)
```bash
sqlite3 Lab-03/Lab_03.db

# Then run queries directly:
sqlite> SELECT * FROM EMP;
sqlite> .quit
```

### Option 3 — Run SQL file directly
```bash
sqlite3 Lab-03/Lab_03.db < Lab-03/Lab_03.sql
```

---

## 🏷️ Topics

`sql` `sqlite` `database` `ddl` `dml` `joins` `subqueries`
`aggregate-functions` `group-by` `bs-data-science` `FAST-NUCES`

---

*Course: Database Systems | BS Data Science | Fall 2024*
