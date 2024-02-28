14. Fetch the inventory variances of the products where the reason is ‘VAR_LOST’ or VAR_DAMAGED.
```sql
SELECT 
    invitm.inventory_item_id, invitm.product_id
FROM
    inventory_item AS invitm
        JOIN
    inventory_item_detail AS indet ON invitm.inventory_item_id = indet.inventory_item_id
WHERE
    indet.reason_enum_id IN ('VAR_DAMAGED' , 'VAR_LOST');

```
OUTPUT:

![Alt text](<Screenshot from 2024-02-28 16-45-13.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 16-44-11.png>)