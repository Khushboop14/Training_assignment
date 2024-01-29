12. Get all the appeasements in July month.
```sql
SELECT oh.order_id, rh.return_id, ra.amount,
ra.return_adjustment_type_id, ra.comments,
rh.entry_date, rh.return_date, oh.product_store_id
FROM return_header as rh
JOIN return_adjustment as ra
ON ra.return_id = rh.return_id
JOIN return_status as rs
ON ra.return_id = rs.return_id AND rs.STATUS_ID = 'RETURN_COMPLETED'
JOIN order_header as oh
ON oh.order_id = ra.order_id
WHERE ra.RETURN_ADJUSTMENT_TYPE_ID = 'APPEASEMENT'
AND rs.STATUS_DATETIME BETWEEN '2023-07-01' and '2023-07-30';
```
![Screenshot from 2024-01-29 17-53-02](https://github.com/Khushboop14/Training_assignment/assets/126051670/33f858fb-e5b2-449b-9ce8-3f7e5f598dac)

