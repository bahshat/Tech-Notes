
---

## 🗄️ Database Interview Notes

### 1. **Types of Databases**

| Type                    | Description                                                                        |
| ----------------------- | ---------------------------------------------------------------------------------- |
| **Relational (RDBMS)**  | Structured data with tables, rows, and columns. SQL-based. e.g., PostgreSQL, MySQL |
| **Document DB (NoSQL)** | Stores data as JSON-like documents. e.g., MongoDB                                  |
| **File-based DB**       | Lightweight, embedded. e.g., SQLite                                                |
| **Server-based DB**     | Requires client-server architecture. e.g., PostgreSQL                              |

---

### 2. **PostgreSQL vs SQLite**

| Feature     | PostgreSQL              | SQLite                                |
| ----------- | ----------------------- | ------------------------------------- |
| Type        | Server-based RDBMS      | File-based RDBMS                      |
| Concurrency | High (multi-user)       | Limited (single-user apps)            |
| ACID        | Yes                     | Yes                                   |
| Performance | High for large systems  | Lightweight, fast for small use-cases |
| Use-case    | Web apps, microservices | Mobile, embedded apps                 |

---

### 3. **PostgreSQL Tools**

* `psql`: PostgreSQL interactive terminal
* **pgAdmin**: Web-based GUI for managing PostgreSQL

---

### 4. **SQL Concepts**

```sql
-- Basic Queries
SELECT * FROM users WHERE age > 18;
INSERT INTO users (name, email) VALUES ('Alice', 'a@x.com');
UPDATE users SET active = true WHERE id = 5;
DELETE FROM users WHERE id = 5;

-- Joins
SELECT a.name, b.order_date
FROM customers a
JOIN orders b ON a.id = b.customer_id;

-- Aggregate Functions
SELECT department, COUNT(*) FROM employees GROUP BY department;
```

#### Key Topics:

* **DDL**: `CREATE`, `ALTER`, `DROP`
* **DML**: `SELECT`, `INSERT`, `UPDATE`, `DELETE`
* **DCL**: `GRANT`, `REVOKE`
* **TCL**: `COMMIT`, `ROLLBACK`

---

### 5. **Transactions**

* Ensure atomic operations.

```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

#### ACID Properties:

* **Atomicity**: All-or-nothing
* **Consistency**: Valid state transitions
* **Isolation**: No interference between transactions
* **Durability**: Persisted after commit

---

### 6. **SQLAlchemy (Python ORM)**

* Used to interact with relational DBs in Python code.
* Two main styles:

  * **Declarative ORM**:

    ```python
    class User(Base):
        __tablename__ = 'users'
        id = Column(Integer, primary_key=True)
        name = Column(String)
    ```
  * **Core (SQL Expression Language)**:

    ```python
    users = Table('users', metadata, autoload_with=engine)
    select(users).where(users.c.name == "Alice")
    ```

#### SQLAlchemy Components:

* `Engine` – DB connection
* `Session` – Unit of work
* `Model` – Python class mapping to DB table
* `Query` – Abstraction over SQL

---

### 7. **Document DB Basics (MongoDB)**

* Uses BSON (binary JSON)
* Example:

  ```json
  { "name": "Alice", "age": 25, "hobbies": ["reading", "gaming"] }
  ```

---

### 8. **Normalization**

* Organizing data to reduce redundancy
* **1NF**: Atomic values
* **2NF**: No partial dependencies
* **3NF**: No transitive dependencies

---

### 9. **Indexing**

* Speeds up query performance

```sql
CREATE INDEX idx_name ON users(name);
```

> Trade-off: Faster reads, but slower writes.

---

### 10. **Interview Questions**

* What are ACID properties?
* Difference between JOIN and UNION?
* How to handle schema migrations in production?
* Compare SQLite and PostgreSQL.
* What is ORM? Pros and Cons?
* What is the difference between WHERE and HAVING?
* How do indexes work?

---