1. How many single-item orders were fulfilled from warehouses in the last month?
```sql
SELECT oitm.order_id
FROM order_item AS oitm
JOIN order_item_ship_group_assoc AS oisga
ON oitm.order_id = oisga.order_id AND oitm.order_item_seq_id = oisga.order_item_seq_id
JOIN order_item_ship_group AS oisg
ON oitm.order_id = oisg.order_id
JOIN order_status AS ost
ON ost.order_id = oitm.order_id AND ost.order_item_seq_id = oitm.order_item_seq_id 
JOIN facility AS f
ON f.facility_id = oisg.facility_id
WHERE f.facility_type_id = 'WAREHOUSE'
AND ost.status_datetime >= DATE_SUB(curdate(), INTERVAL 1 MONTH)  
AND oitm.STATUS_ID = 'ITEM_COMPLETED'
GROUP BY oitm.order_id 
HAVING count(oitm.order_item_seq_id) = 1; 
```
![Screenshot from 2024-02-27 10-43-02](https://github.com/Khushboop14/Training_assignment/assets/126051670/238f7434-24e4-4a7d-a534-63952f7662c2)
