# ALTER

The `ALTER` statement is used to modify an existing table in SQL. The syntax for altering a table is as follows:

```sql
ALTER TABLE table_name
    ADD column_name datatype constraints,
    MODIFY column_name datatype constraints,
    DROP COLUMN column_name;
```

```mermaid
flowchart TD
    A["ALTER TABLE table_name"] --> B["Choose Action"]
    B --> C["ADD column_name datatype constraints"]
    B --> D["MODIFY column_name datatype constraints"]
    B --> E["DROP COLUMN column_name"]

    C --> F["Table Updated"]
    D --> F
    E --> F
```

- `table_name`: The name of the table you want to modify.
- `ADD column_name datatype constraints`: Adds a new column to the table.
- `MODIFY column_name datatype constraints`: Modifies the data type or constraints of an existing column.
- `DROP COLUMN column_name`: Removes a column from the table.

**Example:**

```sql
ALTER TABLE employees
    ADD email VARCHAR(255),
    MODIFY salary DECIMAL(12, 2),
    DROP COLUMN position;
```

<table>
  <tr>
    <td>

```mermaid
erDiagram
    EMPLOYEES {
        INT id PK
        VARCHAR name
        VARCHAR position
        DECIMAL salary "10,2"
    }
```

    </td>
    <td>

```mermaid
erDiagram
    EMPLOYEES {
        INT id PK
        VARCHAR name
        VARCHAR email
        DECIMAL salary "12,2"
    }
```

    </td>

  </tr>
</table>
