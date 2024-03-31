## Data Bank Case Study
## Business Goal
Data Bank is a new banking platform that 

**Entity Relationship Diagram**

<img width="631" alt="130343339-8c9ff915-c88c-4942-9175-9999da78542c" src="https://github.com/dannyjkim37/SQL/assets/160215128/3bd9b3e7-c0e7-40fe-a09f-3daf28360f78">

**Table 1: `regions`**

'regions' table contains the `region_id` and their corresponding `region_name` values.
````sql
SELECT region_id, region_name
FROM data_bank.regions;
````
![Screenshot 2024-03-31 171500](https://github.com/dannyjkim37/SQL/assets/160215128/6babc4d9-b177-434a-9854-34d40c6ce935)


**Table 2: `customer_nodes`**

'customer_nodes' table showing
````sql
SELECT *
FROM data_bank.customer_nodes;
````
![Screenshot 2024-03-31 181310](https://github.com/dannyjkim37/SQL/assets/160215128/f60469a1-3d01-4a90-8121-b7cd112d2e3b)
