8. Find all the orders whose two or more items are completed but the orders are still in the approved status.
```sql
SELECT oh.order_id , 
oitm.order_item_seq_id AS order_item_id ,
oh.status_id AS order_status,
oitm.status_id AS item_status
FROM order_header as oh
JOIN order_item as oitm
ON oitm.order_id = oh.order_id 
JOIN order_status as os
ON os.order_id = oitm.order_id AND os.order_item_seq_id = oitm.order_item_seq_id AND os.STATUS_ID = 'ITEM_COMPLETED'
WHERE oh.status_id = 'ORDER_APPROVED' 
GROUP BY oitm.order_id
HAVING count(os.order_id) >= 2 ;

```
![Screenshot from 2024-01-29 17-35-00](https://github.com/Khushboop14/Training_assignment/assets/126051670/a046b4d5-6df8-420b-89e1-f435a60806be)
