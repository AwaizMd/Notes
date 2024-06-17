# PostgreSQL

## DataTypes

**PostgreSQL supports a rich set of data types, allowing for a wide range of data storage needs. Here's an overview of the primary data types in PostgreSQL:**

**1. Numeric Types**
* **smallint**: 2 bytes, range from -32,768 to 32,767.
  * Example: `smallint_col SMALLINT = 12345`
* **integer** (or **int**): 4 bytes, range from -2,147,483,648 to 2,147,483,647.
  * Example: `integer_col INTEGER = 2147483647`
* **bigint**: 8 bytes, range from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.
  * Example: `bigint_col BIGINT = 9223372036854775807`
* **decimal** (or **numeric**): Variable storage, user-defined precision and scale.
  * Example: `decimal_col DECIMAL(10, 2) = 12345.67`
* **real**: 4 bytes, single precision floating-point number.
  * Example: `real_col REAL = 1.2345`
* **double precision**: 8 bytes, double precision floating-point number.
  * Example: `double_precision_col DOUBLE PRECISION = 1.23456789012345`
* **serial**: Auto-incrementing integer (4 bytes).
  * Example: `serial_col SERIAL`
* **bigserial**: Auto-incrementing bigint (8 bytes).
  * Example: `bigserial_col BIGSERIAL`

**2. Monetary Types**
* **money**: 8 bytes, stores currency amounts with a fixed fractional precision.
  * Example: `money_col MONEY = '$1234.56'`

**3. Character Types**
* **character varying(n)** (or **varchar(n)**): Variable-length string with a limit of n characters.
  * Example: `varchar_col VARCHAR(50) = 'Hello World'`
* **character(n)** (or **char(n)**): Fixed-length string, padded with spaces if necessary.
  * Example: `char_col CHAR(10) = 'Hello '`
* **text**: Variable-length string without a specific length limit.
  * Example: `text_col TEXT = 'This is a long text string.'`

**4. Binary Data Types**
* **bytea**: Variable-length binary string.
  * Example: `bytea_col BYTEA = '\\xDEADBEEF'`
  
**5. Date/Time Types**
* **timestamp [ (p) ] [ without time zone ]**: Date and time (no time zone).
  * Example: `timestamp_col TIMESTAMP = '2024-06-03 12:34:56'`
* **timestamp [ (p) ] with time zone**: Date and time, including time zone.
  * Example: `timestamptz_col TIMESTAMPTZ = '2024-06-03 12:34:56+00'`
* **date**: Calendar date (year, month, day).
  * Example: `date_col DATE = '2024-06-03'`
* **time [ (p) ] [ without time zone ]**: Time of day (no time zone).
  * Example: `time_col TIME = '12:34:56'`
* **time [ (p) ] with time zone**: Time of day, including time zone.
  * Example: `timetz_col TIMETZ = '12:34:56+00'`
* **interval [ fields ] [ (p) ]**: Time span.
  * Example: `interval_col INTERVAL = '1 year 2 months 3 days'`

**6. Boolean Type**
* **boolean**: Stores TRUE, FALSE, or NULL.
  * Example: `boolean_col BOOLEAN = TRUE`

**7. Enumerated Types**
* **enum**: User-defined list of values.
  * Example: `enum_col my_enum = 'value1'`
    ```sql
    CREATE TYPE my_enum AS ENUM ('value1', 'value2', 'value3');
    ```

**8. Geometric Types**
* **point**: A geometric point (x, y).
  * Example: `point_col POINT = '(1,2)'`
* **line**: Infinite line.
  * Example: `line_col LINE = '{1,2,3}'`
* **lseg**: Line segment.
  * Example: `lseg_col LSEG = '[(1,2),(3,4)]'`
* **box**: Rectangular box.
  * Example: `box_col BOX = '((1,2),(3,4))'`
* **path**: Geometric path (open or closed).
  * Example: `path_col PATH = '[(1,2),(3,4),(5,6)]'`
* **polygon**: Polygon (a closed path).
  * Example: `polygon_col POLYGON = '((1,2),(3,4),(5,6))'`
* **circle**: Circle.
  * Example: `circle_col CIRCLE = '<(1,2),3>'`

**9. Network Address Types**
* **cidr**: IPv4 or IPv6 network.
  * Example: `cidr_col CIDR = '192.168.100.0/24'`
* **inet**: IPv4 or IPv6 host address.
  * Example: `inet_col INET = '192.168.100.1'`
* **macaddr**: MAC address.
  * Example: `macaddr_col MACADDR = '08:00:2b:01:02:03'`

**10. Bit String Types**
* **bit [ (n) ]**: Fixed-length bit string.
  * Example: `bit_col BIT(4) = B'1010'`
* **bit varying [ (n) ]** (or **varbit**): Variable-length bit string.
  * Example: `varbit_col VARBIT(10) = B'1010'`

**11. Text Search Types**
* **tsvector**: Text search vector.
  * Example: `tsvector_col TSVECTOR = 'a fat cat sat on a mat and ate a fat rat'`
* **tsquery**: Text search query.
  * Example: `tsquery_col TSQUERY = 'fat & rat'`

**12. UUID Type**
* **uuid**: Universally Unique Identifier.
  * Example: `uuid_col UUID = '550e8400-e29b-41d4-a716-446655440000'`

**13. JSON Types**
* **json**: Textual JSON data.
  * Example: `json_col JSON = '{"name": "John", "age": 30, "city": "New York"}'`
* **jsonb**: Binary JSON data (decomposed binary format).
  * Example: `jsonb_col JSONB = '{"name": "John", "age": 30, "city": "New York"}'`

**14. Array Types**
* **array**: Allows storage of multiple values of a specified data type.
  * Example: `array_col INTEGER[] = ARRAY[1, 2, 3]`

**15. Composite Types**
* **composite**: Row type (a structure with multiple fields of varying types).
  * Example:
    ```sql
    CREATE TYPE my_composite AS (
        name TEXT,
        age INTEGER
    );
    ```
    `composite_col my_composite = ROW('John', 30)`

**16. Range Types**
* **int4range**: Range of integer.
  * Example: `int4range_col INT4RANGE = '[1,10)'`
* **int8range**: Range of bigint.
  * Example: `int8range_col INT8RANGE = '[100,1000)'`
* **numrange**: Range of numeric.
  * Example: `numrange_col NUMRANGE = '[10.5,20.5)'`
* **tsrange**: Range of timestamp without time zone.
  * Example: `tsrange_col TSRANGE = '[2024-06-01 00:00:00, 2024-06-02 00:00:00)'`
* **tstzrange**: Range of timestamp with time zone.
  * Example: `tstzrange_col TSTZRANGE = '[2024-06-01 00:00:00+00, 2024-06-02 00:00:00+00)'`
* **daterange**: Range of date.
  * Example: `daterange_col DATERANGE = '[2024-06-01, 2024-06-10)'`




# Table Level Queries

Common table-level queries, including creating a table, altering a table, and dropping a table.

## 1. Create Table

To create a new table in PostgreSQL, use the `CREATE TABLE` statement.

```sql
CREATE TABLE table_name (
    column1 data_type constraint,
    column2 data_type constraint,
    column3 data_type constraint,
    ...
    table_constraints
);
```

## 2. Alter Table

To modify an existing table, use the ALTER TABLE statement.

```sql

ALTER TABLE table_name ADD COLUMN column_name data_type constraint;
ALTER TABLE employees ADD COLUMN department_id INTEGER;

ALTER TABLE table_name DROP COLUMN column_name;
ALTER TABLE employees DROP COLUMN department_id;

ALTER TABLE table_name RENAME COLUMN old_name TO new_name;
ALTER TABLE employees RENAME COLUMN hire_date TO start_date;

-- Modify Column Data Type
ALTER TABLE table_name ALTER COLUMN column_name TYPE new_data_type;
ALTER TABLE employees ALTER COLUMN salary TYPE DECIMAL(18, 2);

-- Add a Constraint
ALTER TABLE table_name ADD CONSTRAINT constraint_name constraint_definition;
ALTER TABLE employees ADD CONSTRAINT email_unique UNIQUE (email);

-- Drop a constraint
ALTER TABLE table_name DROP CONSTRAINT constraint_name;
ALTER TABLE employees DROP CONSTRAINT email_unique;

```
## 3. Drop Table
To delete a table and all its data, use the DROP TABLE statement.

```sql

DROP TABLE table_name;
DROP TABLE employees;

```
## 4. Rename Table
To rename an existing table, use the RENAME TO statement.

```sql

ALTER TABLE old_table_name RENAME TO new_table_name;
ALTER TABLE employees RENAME TO staff;

```

## 5. Truncate Table
To remove all data from a table without dropping the table itself, use the TRUNCATE statement.

```sql

TRUNCATE TABLE table_name;
TRUNCATE TABLE employees;

```

## 6. Adding Foreign Key Constraint
To add a foreign key constraint, use the ADD CONSTRAINT clause within ALTER TABLE.

```sql

ALTER TABLE table_name ADD CONSTRAINT constraint_name FOREIGN KEY (column_name) REFERENCES other_table_name (column_name);
ALTER TABLE employees ADD CONSTRAINT fk_department FOREIGN KEY (department_id) REFERENCES departments (department_id);

```

## 7. Creating an Index
To create an index on a table column, use the CREATE INDEX statement.

```sql

CREATE INDEX index_name ON table_name (column_name);
CREATE INDEX idx_last_name ON employees (last_name);

```

## 8. Dropping an Index
To drop an index, use the DROP INDEX statement.

```sql

DROP INDEX index_name;
DROP INDEX idx_last_name;

```


# Record Level Queries

Common record-level queries, including inserting records, updating records, deleting records, and selecting records.

## Insert Records

To insert a new record into a table, use the `INSERT INTO` statement.

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

INSERT INTO employees (first_name, last_name, email, hire_date, salary)
VALUES ('John', 'Doe', 'john.doe@example.com', '2024-01-15', 60000);

```

## Update Records
To update existing records in a table, use the UPDATE statement.


UPDATE table_name
```sql
SET column1 = value1, column2 = value2, ...
WHERE condition;

UPDATE employees
SET salary = 65000
WHERE employee_id = 1;

```

## Delete Records

To delete records from a table, use the DELETE FROM statement.

```sql

DELETE FROM table_name
WHERE condition;

DELETE FROM employees
WHERE employee_id = 1;

```
## Select Records
To retrieve records from a table, use the SELECT statement.

```sql

SELECT column1, column2, column3, ...
FROM table_name
WHERE condition;

SELECT first_name, last_name, email
FROM employees
WHERE salary > 50000;

```

## Select All Records
To retrieve all records from a table, use the SELECT * statement.

```sql

SELECT * FROM table_name;

SELECT * FROM employees;

```

## Select with Ordering
To retrieve records in a specific order, use the ORDER BY clause.

```sql

SELECT column1, column2, column3, ...
FROM table_name
ORDER BY column_name [ASC|DESC];

SELECT first_name, last_name, salary
FROM employees
ORDER BY salary DESC;

```

## Select with Limit
To retrieve a specific number of records, use the LIMIT clause.

```sql

SELECT column1, column2, column3, ...
FROM table_name
LIMIT number;

SELECT first_name, last_name, email
FROM employees
LIMIT 10;

```

## Select with Join
To retrieve records from multiple tables, use the JOIN clause.

```sql

SELECT table1.column1, table2.column2, ...
FROM table1
JOIN table2
ON table1.common_column = table2.common_column;

SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
JOIN departments
ON employees.department_id = departments.department_id;

```
