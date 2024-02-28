7 Fetch all the physical items ordered in the month of September 2023.

```sql
SELECT 
    oitm.order_id AS order_id,
    oitm.order_item_seq_id AS order_item
FROM
    order_item AS oitm
        JOIN
    product AS p ON p.product_id = oitm.product_id
        JOIN
    product_type AS pt ON pt.product_type_id = p.product_type_id 
        JOIN
    order_status AS os ON os.order_id = oitm.order_id
        AND os.order_item_seq_id = oitm.order_item_seq_id
WHERE
    pt.is_physical = 'Y'
        AND os.status_id = 'ITEM_CREATED'
        AND os.created_stamp BETWEEN '2023-09-01' AND '2023-09-30';

```
OUTPUT: 

![Alt text](<Screenshot from 2024-02-28 16-04-21.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 16-05-28.png>)