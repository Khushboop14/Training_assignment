6.  In the past month, which store has the highest number of one-day shipped orders?
```sql
SELECT oh.PRODUCT_STORE_ID, COUNT(s.PRIMARY_ORDER_ID) AS shipped_order_count
FROM shipment s
JOIN  shipment_status ss ON ss.SHIPMENT_ID = s.SHIPMENT_ID
JOIN order_header oh ON s.PRIMARY_ORDER_ID = oh.ORDER_ID
WHERE
    s.SHIPMENT_METHOD_TYPE_ID = 'NEXT_DAY'
    AND ss.STATUS_ID = 'SHIPMENT_SHIPPED'
    AND ss.STATUS_DATE >= CURDATE() - INTERVAL 1 MONTH
GROUP BY
    oh.PRODUCT_STORE_ID;

```
OUTPUT:
![Alt text](<Screenshot from 2024-03-01 10-50-35.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-03-01 10-50-44.png>)
