***
## Data Bank Case Study
## Business Goal
Data Bank is a new banking platform that 

**Entity Relationship Diagram**

<img width="631" alt="130343339-8c9ff915-c88c-4942-9175-9999da78542c" src="https://github.com/dannyjkim37/SQL/assets/160215128/3bd9b3e7-c0e7-40fe-a09f-3daf28360f78">


**Table 1: regions**

'regions' table contains the `region_id` and their corresponding `region_name` values.
````sql
SELECT region_id, region_name
FROM data_bank.regions;
````
![t1](https://github.com/dannyjkim37/SQL/assets/160215128/2898ec26-748f-4a5f-b753-ee018e6d2304)


**Table 2: customer_nodes**

'customer_nodes' table showing
````sql
SELECT customer_id, region_id, node_id, start_date, end_date
FROM data_bank.customer_nodes;
````
![t2](https://github.com/dannyjkim37/SQL/assets/160215128/eb5375c1-8411-47b1-a08a-13d85a386aa0)


**Table 3: customer_transactions**

'customer_transactions' table shows customer deposits, withdrawals and purchases made using their Data Bank debit card
````sql
SELECT customer_id, txn_date, txn_type, txn_amount
FROM data_bank.customer_transactions;
````
![t3](https://github.com/dannyjkim37/SQL/assets/160215128/a536bf98-53e0-497c-94fb-416e7598b6ab)


***
## Answering Questions and Data Exploration 
**Customer Nodes Exploration**
1. How many unique nodes are there on the Data Bank system?
