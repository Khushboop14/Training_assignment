10. Fetch all the order items that are in the created status and the order type should be a sales order
- ORDER_ID 
- PRODUCT_TYPE_ID 
- ORDER_LINE_ID  
- EXTERNAL_ID 
- SALES_CHANNEL 
- QUANTITY 
- ITEM_STATUS 
- PRODUCT_ID 
- BILL_CITY 
- BILL_COUNTRY
- BILL_POSTALCODE
- BILL_ADDRESS1
- BILL_ADDRESS2 
- SHIP_CITY 
- SHIP_COUNTRY 
- SHIP_POSTALCODE  
- SHIP_ADDRESS1  
- SHIP_ADDRESS2  

```sql

SELECT 
    oitm.order_id,
    oitm.order_item_seq_id,
    oitm.product_id,
    p.product_type_id,
    oitm.external_id,
    oitm.quantity,
    oitm.status_id,
    oh.sales_channel_enum_id,
    pb.address1 AS Billing_Address1,
    pb.address2 AS Billing_Address2,
    pb.city AS Billing_City,
    pb.postal_code AS Billing_code,
    pb.country_geo_id AS Billing_country,
    ps.address1 AS Shipping_Address1,
    ps.address2 AS Shipping_Address2,
    ps.city AS Shipping_City,
    ps.postal_code AS Shipping_code,
    ps.country_geo_id AS Shipping_country
FROM
    order_header AS oh
        JOIN
    order_item AS oitm ON oh.order_id = oitm.order_id
        AND oitm.status_id = 'ITEM_CREATED'
        JOIN
    order_contact_mech AS ocmb ON ocmb.order_id = oh.order_id
        AND ocmb.contact_mech_purpose_type_id = 'BILLING_LOCATION'
        JOIN
    order_contact_mech AS ocms ON ocmb.order_id = oh.order_id
        AND ocms.contact_mech_purpose_type_id = 'SHIPPING_LOCATION'
        JOIN
    postal_address AS pb ON pb.contact_mech_id = ocmb.contact_mech_id
        JOIN
    postal_address AS ps ON ps.contact_mech_id = ocms.contact_mech_id
        JOIN
    product AS p ON p.product_id = oitm.product_id
WHERE
    oh.order_type_id = 'SALES_ORDER';

```
OUTPUT:

![Alt text](<Screenshot from 2024-02-28 20-22-54.png>)

![Alt text](<Screenshot from 2024-02-28 20-22-54-1.png>)

![Alt text](<Screenshot from 2024-02-28 20-26-02.png>)

QUERY COST: 

![Alt text](<Screenshot from 2024-02-28 20-23-41.png>)

![Alt text](<Screenshot from 2024-02-28 20-24-02.png>)
