6. Fetch all the physical items completed from Warehouse in September of 2023.

```sql
SELECT oitm.order_id AS order_id ,
oitm.order_item_seq_id AS order_item, 
f.facility_type_id AS location_type , 
os.status_id AS order_status, 
os.STATUS_DATETIME AS date_time
FROM order_item as oitm
JOIN order_status as os
ON os.order_id = oitm.order_id AND os.order_item_seq_id = oitm.order_item_seq_id
JOIN order_item_ship_group as oisg
ON oisg.order_id = oitm.order_id 
JOIN facility as f
ON f.facility_id = oisg.facility_id 
JOIN product as p
ON p.product_id = oitm.product_id
JOIN product_type as pt
ON pt.product_type_id = p.product_type_id 
WHERE pt.is_physical = 'Y'
AND f.facility_type_id = 'WAREHOUSE'
AND os.status_id = 'ITEM_COMPLETED'
AND os.status_datetime BETWEEN '2023-09-01'AND '2023-09-30';

```
![Screenshot from 2024-01-29 17-23-32](https://github.com/Khushboop14/Training_assignment/assets/126051670/1b6abe6f-032b-45c4-85a9-cf61abffd386)

