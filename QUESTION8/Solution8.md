8. Find all the orders whose two or more items are completed but the orders are still in the approved status.

```sql

SELECT 
    oh.order_id, count(oitm.order_item_seq_id)
FROM
    order_header AS oh
        JOIN
    order_item AS oitm ON oitm.order_id = oh.order_id
        JOIN
    order_status AS os ON os.order_id = oitm.order_id
        AND os.order_item_seq_id = oitm.order_item_seq_id
        AND os.STATUS_ID = 'ITEM_COMPLETED'
WHERE
    oh.status_id = 'ORDER_APPROVED'
GROUP BY oitm.order_id
HAVING COUNT(os.order_id) >= 2;

```
OUTPUT:

![Alt text](<Screenshot from 2024-02-28 20-28-23.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 20-28-34.png>)
