12. Get all the appeasements in July month.
- RETURN_ID 
- ENTRY_DATE 
- RETURN_ADJUSTMENT_TYPE_ID
- AMOUNT 
- COMMENTS 
- ORDER_ID 
- ORDER_DATE  
- RETURN_DATE
- PRODUCT_STORE_ID 

```sql

SELECT 
    oh.order_id,
    rh.return_id,
    ra.amount,
    ra.return_adjustment_type_id,
    ra.comments,
    rh.entry_date,
    rh.return_date,
    oh.product_store_id
FROM
    return_header AS rh
        JOIN
    return_adjustment AS ra ON ra.return_id = rh.return_id
        JOIN
    order_header AS oh ON oh.order_id = ra.order_id
WHERE
    ra.RETURN_ADJUSTMENT_TYPE_ID = 'APPEASEMENT'
        AND YEAR(rh.RETURN_DATE) = '2023'
		AND MONTH(rh.RETURN_DATE) = '7' ;
```
OUTPUT:

![Alt text](<Screenshot from 2024-02-28 16-35-17.png>)

![Alt text](<Screenshot from 2024-02-28 16-35-35.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 16-36-35.png>)


