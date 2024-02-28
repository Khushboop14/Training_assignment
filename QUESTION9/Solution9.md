9.Find all the orders whose two or more items are canceled but the orders are still in the approved status.

```sql
SELECT 
    oh.order_id AS orders, 
    oitm.order_item_seq_id AS order_item
FROM
    order_header AS oh
        JOIN
    order_item AS oitm ON oitm.order_id = oh.order_id AND oitm.status_id = 'ITEM_CANCELLED'
        JOIN
    order_status AS os ON os.order_id = oitm.order_id
        AND os.order_item_seq_id = oitm.order_item_seq_id
        AND os.status_id = 'ITEM_CANCELLED'
WHERE
    oh.status_id = 'ORDER_APPROVED'
GROUP BY oitm.order_id
HAVING COUNT(os.order_id) >= 2;

```
OUTPUT:

![Alt text](<Screenshot from 2024-02-28 16-20-09.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 16-20-20.png>)
