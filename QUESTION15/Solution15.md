15. Find all the orders that have more than one return.

```sql

SELECT 
    ri.order_id
FROM
    return_item AS ri
WHERE
    ri.status_id = 'RETURN_COMPLETED'
GROUP BY order_id , order_item_seq_id
HAVING COUNT(return_item_seq_id) > 1;


```

OUTPUT:

![Alt text](<Screenshot from 2024-02-28 18-05-56.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 18-06-08.png>)