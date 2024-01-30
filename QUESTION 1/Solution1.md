How many single-item orders were fulfilled from warehouses in the last month?
```sql
SELECT distinct oitm.order_id
FROM order_item as oitm
JOIN order_item_ship_group as oisg
ON oitm.order_id = oisg.order_id
JOIN order_status as ost
ON ost.order_id = oitm.order_id AND ost.order_item_seq_id = oitm.order_item_seq_id 
JOIN facility as f
ON f.facility_id = oisg.facility_id
WHERE f.facility_type_id = 'WAREHOUSE'
AND ost.status_datetime >= DATE_SUB(curdate(), INTERVAL 1 MONTH)  
GROUP BY oitm.order_id 
HAVING count(oitm.order_item_seq_id) = 1;
```
![Screenshot from 2024-01-30 11-24-18](https://github.com/Khushboop14/Training_assignment/assets/126051670/e1b675c8-1bf0-4dc3-98b9-bc6de87c5174)
