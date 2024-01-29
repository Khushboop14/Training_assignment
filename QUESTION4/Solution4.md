4. Fetch the following columns for created orders. These should be sales orders.
ORDER_ID
TOTAL_AMOUNT
PAYMENT_METHOD
SHOPIFY_ORDER_NAME
NOTE: 
The total amount represents the total amount of the order.
The payment method is the method by which payment was made, like Cash, mastercard, visa, paypal, etc.

```sql
SELECT oid.order_id, oh.grand_total, pmt.PAYMENT_METHOD_CODE,  oid.id_value
FROM order_header as oh 
JOIN order_identification as oid
ON oid.order_id = oh.order_id
JOIN order_payment_preference as opp
ON opp.order_id = oh.order_id
join payment_method_type pmt
on pmt.PAYMENT_METHOD_TYPE_ID= opp.PAYMENT_METHOD_TYPE_ID
WHERE oh.status_id = 'ORDER_CREATED'
AND oh.ORDER_TYPE_ID = 'SALES_ORDER'
AND oid.order_identification_type_id = 'SHOPIFY_ORD_NAME';

```
![Screenshot from 2024-01-29 17-14-13](https://github.com/Khushboop14/Training_assignment/assets/126051670/b7f751e3-c3e2-4196-82e3-4f5ac6329202)


