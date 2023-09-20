# Workflow
- Import data from any source by configuring [[MySQL remote connecion]]
- Transform data
	- find the GB column 
	- duplicate the GB column by right clicking the column
	- Split Column by Non-Digit to Digit
	- [[Data cleaning for Power BI]]
	- Remove null values and remove duplicates in sGBID column
	- Merge Queries and pick the GB from both the tables. Make sure the relationship from Master to subset data is 1:1


## Error
### 1. Error regarding OldGuids option when connecting to MySQL can be solved by adding a new data source with Blank Query 
```
= MySQL.Database(“myservername”, “catalogname”, [Query=”select * from calls”, ReturnSingleDatabase=true, OldGuids=true])
```

### 2. Relationship error : unable to set 1:1 relation. Defaults to 1:\* relation.
- Check for duplicate value in both tables
- Remove null values
- Make sure you clean to data so that Subset does not have records that's not in the master - superset.

### 3. Error when adding sGBIC column to a table
```
SQL Error [1292] [22001]: Data truncation: Incorrect date value: '0000-00-00' for column 'LastUpdated' at row 1
```
Solution :
> **SET** sql_mode = '';
