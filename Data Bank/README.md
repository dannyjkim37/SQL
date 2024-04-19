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
````sql
SELECT COUNT(DISTINCT node_id) AS unique_nodes
FROM data_bank.customer_nodes;
````
![q1](https://github.com/dannyjkim37/SQL/assets/160215128/1bbac3b9-2de4-4a29-963b-045dcf9d5bf1)

2. What is the number of nodes per region?
````sql
SELECT
  regions.region_name, 
  COUNT(DISTINCT customers.node_id) AS node_count
FROM data_bank.regions
JOIN data_bank.customer_nodes AS customers
  ON regions.region_id = customers.region_id
GROUP BY regions.region_name;
````
![q2](https://github.com/dannyjkim37/SQL/assets/160215128/ccaa68dd-97b1-463e-b49c-36ebf1c3762a)

3. How many customers are allocated to each region?
````sql
SELECT 
  region_id, 
  COUNT(customer_id) AS customer_count
FROM data_bank.customer_nodes
GROUP BY region_id
ORDER BY region_id;
````
![q3](https://github.com/dannyjkim37/SQL/assets/160215128/3e3cbe64-9653-4a0b-b9a1-1a2d5427e8ca)

4. How many days on average are customers reallocated to a different node?
````sql
WITH node_days AS (
  SELECT 
    customer_id, 
    node_id,
    end_date - start_date AS days_in_node
  FROM data_bank.customer_nodes
  WHERE end_date != '9999-12-31'
  GROUP BY customer_id, node_id, start_date, end_date
) 
, total_node_days AS (
  SELECT 
    customer_id,
    node_id,
    SUM(days_in_node) AS total_days_in_node
  FROM node_days
  GROUP BY customer_id, node_id
)

SELECT ROUND(AVG(total_days_in_node)) AS avg_node_reallocation_days
FROM total_node_days;
````
![q4](https://github.com/dannyjkim37/SQL/assets/160215128/50746606-2f94-4621-b2bc-5ced620e2655)

## B. Customer Transactions
1. What is the unique count and total amount for each transaction type?
````sql
SELECT
  txn_type, 
  COUNT(customer_id) AS transaction_count, 
  SUM(txn_amount) AS total_amount
FROM data_bank.customer_transactions
GROUP BY txn_type;
````
![qq1](https://github.com/dannyjkim37/SQL/assets/160215128/43711a89-7e54-4ee6-9a50-6a96f90ff9e4)
