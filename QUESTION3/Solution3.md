3.Fetch the order id and contact mech id for the shipping address of the orders completed in October of 2023.
	
```sql
SELECT 
    ocm.order_id, ocm.contact_mech_id
FROM
    order_contact_mech AS ocm
        JOIN
    order_status AS os ON ocm.order_id = os.order_id
        AND ocm.contact_mech_purpose_type_id = 'SHIPPING_LOCATION'
WHERE
    os.status_id = 'ORDER_COMPLETED'
        AND YEAR(os.status_datetime) = 2023
        AND MONTH(os.status_datetime) = 8;

```
OUTPUT: 

![Alt text](<Screenshot from 2024-02-28 15-14-04.png>)

QUERY COST: 

![Alt text](<Screenshot from 2024-02-28 15-15-06.png>)
