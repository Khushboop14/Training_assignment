5. Fetch the following data for completed order items in July of 2023
ORDER_ID
ORDER_ITEM_SEQ_ID
SHOPIFY_ORDER_ID
SHOPIFY_PRODUCT_ID
```sql

SELECT oitm.order_id, oitm.order_item_seq_id ,
gid.ID_VALUE as shopify_prod_id, oid.ID_VALUE as shopify_ord_id
FROM order_item as oitm
JOIN order_identification as oid
ON oid.order_id = oitm.order_id 
JOIN good_identification as gid
ON gid.product_id = oitm.product_id 
JOIN order_status as os
ON os.order_id = oitm.order_id AND os.order_item_seq_id = oitm.order_item_seq_id
WHERE os.STATUS_ID = 'ITEM_COMPLETED'
AND oid.order_identification_type_id = 'SHOPIFY_ORD_ID' 
AND gid.good_identification_type_id = 'SHOPIFY_PROD_ID'
AND os.status_datetime >=  '2023-07-01' and os.status_datetime <=  '2023-07-31' ;

```
![Screenshot from 2024-01-29 17-19-54](https://github.com/Khushboop14/Training_assignment/assets/126051670/4e3cc15a-6703-48a8-9ac2-f08855bb9233)

