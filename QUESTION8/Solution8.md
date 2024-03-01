8.  How many orders with a single return were recorded in the last month?


QUERY:

```sql
SELECT 
   count( ritm.order_id) AS ORDER_ID
FROM
    return_header AS rh
        JOIN
    return_item AS ritm ON ritm.return_id = rh.return_id
WHERE
    rh.entry_date >= DATE_SUB(CURDATE(), INTERVAL 1 MONTH)
GROUP BY ritm.order_id
HAVING COUNT(ritm.return_id) = 1) AS orders;
```

OUTPUT: 

![Alt text](<Screenshot from 2024-03-01 09-38-48.png>)


QUERY COST:


![Alt text](<Screenshot from 2024-03-01 09-39-03.png>)