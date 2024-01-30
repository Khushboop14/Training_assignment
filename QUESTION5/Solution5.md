5. In New York, which product has the highest sales?
```sql
SELECT oitm.PRODUCT_ID,(oitm.QUANTITY *oitm.UNIT_PRICE) AS TOTAL_SALES
FROM order_item as oitm
JOIN order_contact_mech as ocm
ON ocm.order_id = oitm.ORDER_ID
JOIN postal_address as pa  
ON pa.contact_mech_id = ocm.contact_mech_id
WHERE pa.CITY = 'NEW YORK'
GROUP BY oitm.product_id
ORDER BY TOTAL_SALES DESC 
LIMIT 1;
```
![Screenshot from 2024-01-30 14-31-58](https://github.com/Khushboop14/Training_assignment/assets/126051670/1cfa8b4a-af14-48a7-81de-f908dc56b545)
