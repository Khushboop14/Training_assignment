5. Fetch the following data for completed order items in July of 2023
- ORDER_ID
- ORDER_ITEM_SEQ_ID
- SHOPIFY_ORDER_ID
- SHOPIFY_PRODUCT_ID

```sql

SELECT 
    oitm.order_id,
    oitm.order_item_seq_id,
    gid.ID_VALUE AS shopify_prod_id,
    oid.ID_VALUE AS shopify_ord_id
FROM
    order_item AS oitm
        JOIN
    order_identification AS oid ON oid.order_id = oitm.order_id 
    AND oid.order_identification_type_id = 'SHOPIFY_ORD_ID'
    
        JOIN
    good_identification AS gid ON gid.product_id = oitm.product_id AND gid.good_identification_type_id = 'SHOPIFY_PROD_ID'

        JOIN
    order_status AS os ON os.order_id = oitm.order_id      
        AND os.order_item_seq_id = oitm.order_item_seq_id AND  OS.status_id = 'ITEM_COMPLETED' 
WHERE
		YEAR(os.status_datetime) = '2023'
        AND MONTH(os.status_datetime ) =  '7';



```
OUTPUT:
![Alt text](<Screenshot from 2024-02-28 15-34-29.png>)


QUERY COST:
![Alt text](<Screenshot from 2024-02-28 15-53-43.png>)