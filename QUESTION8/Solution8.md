8.  How many orders with a single return were recorded in the last month?


QUERY:

```sql
SELECT ritm.order_id AS ORDER_ID 
FROM return_header AS rh
JOIN return_item AS ritm
ON ritm.return_id = rh.return_id
WHERE rh.entry_date >= DATE_SUB(CURDATE(), INTERVAL 1 MONTH)
GROUP BY ritm.order_id 
HAVING count(ritm.return_id) = 1;
```
OUTPUT: 

![Screenshot from 2024-02-27 10-50-02](https://github.com/Khushboop14/Training_assignment/assets/126051670/ce02ce81-77e8-47d5-9549-715ca1f01684)

```
QUERY COST:
![Screenshot from 2024-02-27 10-51-00](https://github.com/Khushboop14/Training_assignment/assets/126051670/a412412b-4d2f-4871-b01a-c7ef98ceaa20)

