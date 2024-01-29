12. Get all the appeasements in July month.
```sql
SELECT oh.order_id, rh.return_id, ra.amount,
ra.return_adjustment_type_id, ra.comments,
rh.entry_date, rh.return_date, oh.product_store_id
FROM return_header as rh
JOIN return_adjustment as ra
ON ra.return_id = rh.return_id
JOIN order_header as oh
ON oh.order_id = ra.order_id
WHERE ra.RETURN_ADJUSTMENT_TYPE_ID = 'APPEASEMENT'
AND rh.RETURN_DATE BETWEEN '2023-07-01' and '2023-07-30';
```
![Screenshot from 2024-01-29 20-28-52](https://github.com/Khushboop14/Training_assignment/assets/126051670/1acc8cbe-a2e5-44db-8b6a-ba8947dab30d)


