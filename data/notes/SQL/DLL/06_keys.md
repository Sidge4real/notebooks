# KEYS

Keys are used to uniquely identify rows in a table. There are several types of keys in SQL, including:

- **Primary Key:** A primary key is a column or a set of columns that uniquely identifies each row in a table. A table can have only one primary key, and it cannot contain NULL values.
- **Foreign Key:** A foreign key is a column or a set of columns that refers to the primary key of another table. It is used to establish a relationship between two tables.
- **Candidate Key:** A candidate key is a column or a set of columns that can uniquely identify each row in a table. A table can have multiple candidate keys, but only one is chosen as the primary key.
- **Surrogate Key:** A surrogate key is an artificial key that is used to uniquely identify each row in a table. It is typically an auto-incremented integer and is not derived from the data itself.

```mermaid
flowchart TD
    A["KEYS"] --> B["Primary Key"]
    A --> C["Foreign Key"]
    A --> D["Candidate Key"]
    A --> E["Surrogate Key"]
```

**Example:**

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);
```
In this example, the `id` column is the primary key for the `employees` table, ensuring that each employee has a unique identifier. The `department_id` column is a foreign key that references the `id` column in the `departments` table, establishing a relationship between the two tables.