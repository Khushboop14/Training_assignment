4. Fetch the following columns for created orders. These should be sales orders.
- ORDER_ID
- TOTAL_AMOUNT
- PAYMENT_METHOD
- SHOPIFY_ORDER_NAME

NOTE: The total amount represents the total amount of the order.
The payment method is the method by which payment was made, like Cash, mastercard, visa, paypal, etc.

```sql
SELECT 
    oid.order_id AS ORDER_ID,
    oh.grand_total AS TOTAL_AMOUNT,
    pmt.PAYMENT_METHOD_CODE AS PAYMENT_METHOD_CODE ,
    oid.id_value AS SHOPIFY_ORDER_NAME
FROM
    order_header AS oh
        JOIN
    order_identification AS oid ON oid.order_id = oh.order_id
        JOIN
    order_payment_preference AS opp ON opp.order_id = oh.order_id
        JOIN
    payment_method_type pmt ON pmt.PAYMENT_METHOD_TYPE_ID = opp.PAYMENT_METHOD_TYPE_ID
WHERE
    oh.status_id = 'ORDER_CREATED'
        AND oh.ORDER_TYPE_ID = 'SALES_ORDER'
        AND oid.order_identification_type_id = 'SHOPIFY_ORD_NAME';

```
OUTPUT: 
![Alt text](<Screenshot from 2024-02-28 15-27-38.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 15-28-07.png>)




