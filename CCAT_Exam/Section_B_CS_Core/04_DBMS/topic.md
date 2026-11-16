# Topic: DBMS — Complete CCAT Level
# Section B — CS Core

---

## Study Order (follow exactly)

---

### STEP 1: DBMS Basics
Read: https://www.geeksforgeeks.org/dbms/introduction-to-dbms/

Must know:
- DBMS vs File System: DBMS handles concurrent access, integrity, security
- Types: Relational (SQL), NoSQL (MongoDB), Hierarchical, Network
- Schema: logical design of database
- Instance: actual data at a point in time

---

### STEP 2: ER Model
Read: https://www.geeksforgeeks.org/dbms/introduction-of-er-model/

Must know:
- Entity: real-world object (Student, Course)
- Attribute: property of entity (Name, Age)
- Relationship: association between entities (Student enrolls in Course)
- Cardinality: 1:1, 1:N, M:N
- Weak entity: cannot exist without another entity

---

### STEP 3: Keys
Read: https://www.geeksforgeeks.org/dbms/types-of-keys-in-relational-model-candidate-super-primary-alternate-and-foreign/

Must know all key types:
| Key | Definition |
|-----|------------|
| Super key | Any set of attributes that uniquely identifies a row |
| Candidate key | Minimal super key (no redundant attributes) |
| Primary key | Chosen candidate key (NOT NULL, UNIQUE) |
| Alternate key | Candidate keys not chosen as primary key |
| Foreign key | References primary key of another table |
| Composite key | Primary key made of multiple columns |

---

### STEP 4: Normalization
Read: https://www.geeksforgeeks.org/dbms/introduction-of-database-normalization/
Read: https://www.geeksforgeeks.org/dbms/normal-forms-in-dbms/
Read: https://www.geeksforgeeks.org/dbms/what-is-functional-dependency-in-dbms/

Must know each normal form:
| NF | Rule |
|----|------|
| 1NF | No repeating groups, atomic values only |
| 2NF | 1NF + no partial dependency (every non-key attribute fully depends on primary key) |
| 3NF | 2NF + no transitive dependency (non-key attribute doesn't depend on another non-key) |
| BCNF | 3NF + for every FD X→Y, X must be a superkey |

Functional dependency: X → Y means X determines Y

---

### STEP 5: SQL
Read: https://www.geeksforgeeks.org/sql/sql-tutorial/
Read: https://www.geeksforgeeks.org/sql/sql-join-set-1-inner-left-right-and-full-joins/

Must know SQL commands by category:
| Category | Commands |
|----------|----------|
| DDL | CREATE, ALTER, DROP, TRUNCATE |
| DML | INSERT, UPDATE, DELETE, SELECT |
| DCL | GRANT, REVOKE |
| TCL | COMMIT, ROLLBACK, SAVEPOINT |

Must know JOINs:
- INNER JOIN: rows matching in BOTH tables
- LEFT JOIN: all rows from left, matching from right (NULL if no match)
- RIGHT JOIN: all rows from right, matching from left
- FULL OUTER JOIN: all rows from both, NULL where no match
- SELF JOIN: table joined with itself

Must know SQL clauses:
- WHERE: filter rows
- GROUP BY: group rows by column
- HAVING: filter after GROUP BY (like WHERE but for aggregates)
- ORDER BY: sort results
- DISTINCT: remove duplicates

Aggregate functions: COUNT, SUM, AVG, MAX, MIN

---

### STEP 6: Transactions and ACID
Read: https://www.geeksforgeeks.org/dbms/acid-properties-in-dbms/

Must know ACID:
| Property | Meaning |
|----------|---------|
| Atomicity | All or nothing — transaction fully completes or fully rolls back |
| Consistency | Database moves from one valid state to another |
| Isolation | Concurrent transactions don't interfere with each other |
| Durability | Committed data persists even after crash |

Transaction states: Active → Partially Committed → Committed / Failed → Aborted

---

## Practice Links

IndiaBIX DBMS:
https://www.indiabix.com/database/questions-and-answers/

GFG DBMS Quiz:
https://www.geeksforgeeks.org/dbms/quiz-on-database-management-system/

GFG SQL Practice:
https://www.geeksforgeeks.org/sql/sql-interview-questions/

---

## Daily Target
- Do 10 DBMS MCQs + 5 SQL queries on IndiaBIX/GFG
- Normalize a sample table to 3NF once — good practice
