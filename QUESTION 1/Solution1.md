1. How many single-item orders were fulfilled from warehouses in the last month?
```sql

SELECT COUNT(*) FROM (
SELECT 
    count(oitm.order_id)
FROM
    order_item AS oitm
        JOIN
    order_item_ship_group_assoc AS oisga ON oisga.order_id = oitm.order_id
        AND oisga.order_item_seq_id = oitm.order_item_seq_id
        JOIN
    order_item_ship_group AS oisg ON oisga.SHIP_GROUP_SEQ_ID = oisg.SHIP_GROUP_SEQ_ID
        AND oisga.order_id = oisg.order_id
        JOIN
    order_status AS ost ON ost.order_id = oitm.order_id
        AND ost.order_item_seq_id = oitm.order_item_seq_id
        JOIN
    facility AS f ON f.facility_id = oisg.facility_id
WHERE
    f.facility_type_id = 'WAREHOUSE'
        AND ost.status_datetime >= DATE_SUB(CURDATE(), INTERVAL 1 MONTH)
        AND ost.STATUS_ID = 'ITEM_COMPLETED'
GROUP BY oitm.order_id
HAVING COUNT(oitm.order_item_seq_id) = 1
) AS count_of_orders;

```

Note: 

order_item: order_id, order_item_seq_id
order_item_ship_group_assoc: order_id, order_item_seq_id
order_item_ship_group: order_id
order_status: status_datetime, status_id
facility: facility_id, facility_type_id


OUTPUT:

![Alt text](<Screenshot from 2024-02-29 10-23-22.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-29 10-28-15.png>)