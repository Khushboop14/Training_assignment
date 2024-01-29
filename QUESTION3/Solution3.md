```sql
SELECT  ocm.order_id, ocm.contact_mech_id, ocm.contact_mech_purpose_type_id
FROM order_contact_mech as ocm
JOIN order_status as os
ON ocm.order_id = os.order_id 
WHERE os.status_id = 'ORDER_COMPLETED'
AND ocm.contact_mech_purpose_type_id = 'SHIPPING_LOCATION'
AND os.status_datetime >=  '2023-07-01' and os.status_datetime <=  '2023-07-31';

```
![Screenshot from 2024-01-29 16-38-55](https://github.com/Khushboop14/Training_assignment/assets/126051670/1680ff3a-1c52-4439-8efe-243b0e868518)
