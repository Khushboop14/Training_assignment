6.  In the past month, which store has the highest number of one-day shipped orders?
```sql
SELECT ps.PRODUCT_STORE_ID, oh.order_id AS TOTAL_ORDERS
FROM order_header as oh 
JOIN product_store as ps
ON oh.product_store_id = ps.product_store_id
JOIN product_store_shipment_meth as pssm 
ON ps.product_store_id = pssm.product_store_id
JOIN shipment as s
ON s.shipment_method_type_id = pssm.shipment_method_type_id
WHERE s.shipment_method_type_id = 'NEXT_DAY' OR 'SAME_DAY'
AND s.status_id = 'SHIPMENT_SHIPPED'
AND oh.status_id = 'ORDER_COMPLETED'
AND pssm.SHIPMENT_METHOD_TYPE_ID IN ('NEXT_DAY', 'SAME_DAY')
ORDER BY TOTAL_ORDERS DESC;
```
