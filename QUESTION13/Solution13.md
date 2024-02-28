
13. Fetch the following details for orders completed in August of 2023.
- PRODUCT_ID 
- PRODUCT_TYPE_ID 
- PRODUCT_STORE_ID 
- TOTAL_QUANTITY 
- INTERNAL_NAME  
- FACILITY_ID 
- EXTERNAL_ID 
- FACILITY_TYPE_ID  
- ORDER_HISTORY_ID 
- ORDER_ID 
- ORDER_ITEM_SEQ_ID 
- SHIP_GROUP_SEQ_ID 

```sql

SELECT 
    p.product_id,
    p.product_type_id,
    oh.product_store_id,
    oitm.quantity,
    p.internal_name,
    f.facility_id,
    oh.external_id,
    f.facility_type_id,
    ohis.order_history_id,
    oh.order_id,
    oitm.order_item_seq_id,
    oisg.ship_group_seq_id
FROM
    order_header AS oh
        JOIN
    order_item AS oitm ON oitm.order_id = oh.order_id AND Oh.status_id = 'ORDER_COMPLETED'
        JOIN
    order_item_ship_group_assoc AS oisga ON oisga.order_id = oitm.order_id
        AND oisga.order_item_seq_id = oitm.order_item_seq_id
        JOIN
    order_item_ship_group AS oisg ON oisga.SHIP_GROUP_SEQ_ID = oisg.SHIP_GROUP_SEQ_ID
        AND oisga.order_id = oisg.order_id
        JOIN
    order_history AS ohis ON ohis.order_id = oitm.order_id
        AND ohis.ORDER_ITEM_SEQ_ID = oitm.ORDER_ITEM_SEQ_ID
        JOIN
    product AS p ON p.product_id = oitm.product_id
        JOIN
    facility AS f ON f.facility_id = oisg.facility_id
        JOIN
    order_status AS os ON os.order_id = oh.order_id
WHERE
        YEAR(os.status_datetime) = 2023
        AND MONTH(os.status_datetime) = 8;

```
OUTPUT: 
![Alt text](<Screenshot from 2024-02-28 16-41-58.png>)

![Alt text](<Screenshot from 2024-02-28 16-42-14.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 16-40-40.png>)

![Alt text](<Screenshot from 2024-02-28 16-40-46.png>)
