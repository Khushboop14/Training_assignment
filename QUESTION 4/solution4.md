4. What is the total number of orders originating from New York?

- For shipping location:
```sql 
SELECT count(distinct ocm.order_id)
FROM order_contact_mech as ocm
JOIN postal_address as pa  
ON pa.contact_mech_id = ocm.contact_mech_id
WHERE pa.CITY = 'NEW YORK'
AND ocm.CONTACT_MECH_PURPOSE_TYPE_ID = 'SHIPPING_LOCATION';
```
- For Billing location:

```sql
SELECT count(*)
FROM order_contact_mech as ocm
JOIN postal_address as pa  
ON pa.contact_mech_id = ocm.contact_mech_id
WHERE pa.CITY = 'NEW YORK'
AND ocm.CONTACT_MECH_PURPOSE_TYPE_ID = 'BILLING_LOCATION';

```
Output for Shipping location:
![Alt text](<Screenshot from 2024-02-29 15-48-13.png>)

Query Cost for shipping location:

![Alt text](<Screenshot from 2024-02-29 15-48-45.png>)

Output for Billing location:

![Alt text](<Screenshot from 2024-02-29 15-48-55.png>)

Query Cost for Billing location:
![Alt text](<Screenshot from 2024-02-29 15-49-03.png>)