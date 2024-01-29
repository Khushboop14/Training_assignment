14. Fetch the inventory variances of the products where the reason is ‘VAR_LOST’ or VAR_DAMAGED.
```sql
SELECT invitm.inventory_item_id , invitm.product_id
From inventory_item as invitm
JOIN inventory_item_detail as indet
ON invitm.inventory_item_id = indet.inventory_item_id
WHERE indet.reason_enum_id IN ('VAR_DAMAGED' , 'VAR_LOST');
```
![Screenshot from 2024-01-29 20-01-13](https://github.com/Khushboop14/Training_assignment/assets/126051670/200f8379-b1bd-4d5a-91fc-cd5bab66eee4)
