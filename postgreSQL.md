# PostgreSQL

## DataTypes

**PostgreSQL supports a rich set of data types, allowing for a wide range of data storage needs. Here's an overview of the primary data types in PostgreSQL:**

**1. Numeric Types**
* smallint: 2 bytes, range from -32,768 to 32,767.
8 integer (or int): 4 bytes, range from -2,147,483,648 to 2,147,483,647.
* bigint: 8 bytes, range from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.
* decimal (or numeric): Variable storage, user-defined precision and scale.
* real: 4 bytes, single precision floating-point number.
* double precision: 8 bytes, double precision floating-point number.
* serial: Auto-incrementing integer (4 bytes).
* bigserial: Auto-incrementing bigint (8 bytes).

**2. Monetary Types**
* money: 8 bytes, stores currency amounts with a fixed fractional precision.

**3. Character Types**
* character varying(n) (or varchar(n)): Variable-length string with a limit of n characters.
* character(n) (or char(n)): Fixed-length string, padded with spaces if necessary.
* text: Variable-length string without a specific length limit.

**4. Binary Data Types**
* bytea: Variable-length binary string.
  
**5. Date/Time Types**

* timestamp [ (p) ] [ without time zone ]: Date and time (no time zone).
* timestamp [ (p) ] with time zone: Date and time, including time zone.
* date: Calendar date (year, month, day).
* time [ (p) ] [ without time zone ]: Time of day (no time zone).
* time [ (p) ] with time zone: Time of day, including time zone.
* interval [ fields ] [ (p) ]: Time span.

**6. Boolean Type**

* boolean: Stores TRUE, FALSE, or NULL.

**7. Enumerated Types**

* enum: User-defined list of values.

**8. Geometric Types**

* point: A geometric point (x, y).
* line: Infinite line.
* lseg: Line segment.
* box: Rectangular box.
* path: Geometric path (open or closed).
* polygon: Polygon (a closed path).
* circle: Circle.

**9. Network Address Types**

* cidr: IPv4 or IPv6 network.
* inet: IPv4 or IPv6 host address.
* macaddr: MAC address.

**10. Bit String Types**

* bit [ (n) ]: Fixed-length bit string.
* bit varying [ (n) ] (or varbit): Variable-length bit string.

**11. Text Search Types**

* tsvector: Text search vector.
* tsquery: Text search query.

**12. UUID Type**

* uuid: Universally Unique Identifier.

**13. JSON Types**

* json: Textual JSON data.
* jsonb: Binary JSON data (decomposed binary format).

**14. Array Types**

* array: Allows storage of multiple values of a specified data type.

**15. Composite Types**

* composite: Row type (a structure with multiple fields of varying types).

**16. Range Types**

* int4range: Range of integer.
* int8range: Range of bigint.
* numrange: Range of numeric.
* tsrange: Range of timestamp without time zone.
* tstzrange: Range of timestamp with time zone.
daterange: Range of date.


