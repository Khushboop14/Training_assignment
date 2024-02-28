6. Fetch all the physical items completed from Warehouse in September of 2023.

```sql
SELECT 
    oitm.order_id AS order_id,
    oitm.order_item_seq_id AS order_item
FROM
    order_item AS oitm
        JOIN
    order_status AS os ON os.order_id = oitm.order_id
        AND os.order_item_seq_id = oitm.order_item_seq_id
        AND os.status_id = 'ITEM_COMPLETED'
        JOIN
    order_item_ship_group AS oisg ON oisg.order_id = oitm.order_id
        JOIN
    facility AS f ON f.facility_id = oisg.facility_id
        AND f.facility_type_id = 'WAREHOUSE'
        JOIN
    product AS p ON p.product_id = oitm.product_id
        JOIN
    product_type AS pt ON pt.product_type_id = p.product_type_id
        AND pt.is_physical = 'Y'
WHERE
    os.status_datetime BETWEEN '2023-09-01' AND '2023-09-30';

```
OUTPUT:

![Alt text](<Screenshot from 2024-02-28 16-00-45.png>)

QUERY OUTPUT:

![Alt text](<Screenshot from 2024-02-28 16-00-52.png>)