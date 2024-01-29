7 Fetch all the physical items ordered in the month of September 2023.
```sql
SELECT ,oitm.order_id AS order_id ,
oitm.order_item_seq_id AS order_item,
p.product_id AS product,
p.product_name AS product_name
FROM order_item as oitm
JOIN product as p
ON p.product_id = oitm.product_id
JOIN product_type as pt
ON pt.product_type_id = p.product_type_id 
JOIN order_status as os
ON os.order_id = oitm.order_id AND os.order_item_seq_id = oitm.order_item_seq_id
WHERE pt.is_physical = 'Y'
AND os.status_id = 'ITEM_CREATED'
AND os.status_datetime >= '2023-09-01' and os.status_datetime <=  '2023-09-30';

```
![Screenshot from 2024-01-29 17-25-47](https://github.com/Khushboop14/Training_assignment/assets/126051670/fbbf0013-456c-4797-85ab-483094625f31)
