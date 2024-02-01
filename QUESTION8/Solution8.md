8.  How many orders with a single return were recorded in the last month?

```sql
SELECT ritm.order_id as ORDER_ID , ritm.return_id as SINGLE_RETURN_ORDERS 
FROM return_header as rh
JOIN return_item as ritm
ON ritm.return_id = rh.return_id
WHERE rh.entry_date >= DATE_SUB(CURDATE(), INTERVAL 1 MONTH)
GROUP BY ritm.order_id 
HAVING count(ritm.return_id) = 1;
![Screenshot from 2024-02-01 10-49-37](https://github.com/Khushboop14/Training_assignment/assets/126051670/de42a2a1-d3cb-436c-be15-9fe78823c3db)
