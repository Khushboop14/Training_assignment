15. Find all the orders that have more than one return.
```sql
SELECT ri.order_id, ri.order_item_seq_id, ri.return_item_seq_id
FROM return_item as ri
JOIN order_item as oitm
ON ri.order_id = oitm.order_id
GROUP BY order_id, order_item_seq_id
HAVING COUNT(return_item_seq_id) > 1;
```
![Screenshot from 2024-01-29 20-01-13](https://github.com/Khushboop14/Training_assignment/assets/126051670/9399a03e-4fe1-4358-be8e-4c8e4672ba52)

