10. Fetch all the order items that are in the created status and the order type should be a sales order(INCOMPLETE)
```sql
SELECT oitm.order_id, oitm.order_item_seq_id, oitm.product_id, p.product_type_id,
oitm.external_id, oitm.quantity, oitm.status_id, 
oh.sales_channel_enum_id, 
pb.address1 AS Billing_Address1 , pb.address2 AS Billing_Address2 , pb.city AS Billing_City, pb.postal_code AS Billing_code , pb.country_geo_id AS Billing_country,
ps.address1 AS Shipping_Address1 , ps.address2 AS Shipping_Address2 , ps.city AS Shipping_City, ps.postal_code AS Shipping_code , ps.country_geo_id AS Shipping_country
FROM order_header as oh
JOIN order_item as oitm
	ON oh.order_id = oitm.order_id
JOIN order_contact_mech as ocm
	ON ocm.order_id = oitm.order_id 
LEFT JOIN postal_address as pb
	ON pb.contact_mech_id = ocm.contact_mech_id AND ocm.contact_mech_id AND ocm.contact_mech_purpose_type_id = 'BILLING_LOCATION'
Left JOIN postal_address as ps
	ON ps.contact_mech_id = ocm.contact_mech_id AND ocm.contact_mech_purpose_type_id = 'SHIPPING_LOCATION'
JOIN product as p
	ON p.product_id = oitm.product_id
WHERE oh.order_type_id = 'SALES_ORDER' AND oitm.status_id = 'ITEM_CREATED';
``   
![Screenshot from 2024-02-22 19-48-33](https://github.com/Khushboop14/Training_assignment/assets/126051670/199eabc1-2cea-4710-89e1-2a0bfbed4cf5)

![Screenshot from 2024-02-22 19-50-32](https://github.com/Khushboop14/Training_assignment/assets/126051670/5ec884a4-08ef-40fe-b62c-a0a168c1e578)

![Screenshot from 2024-02-22 19-50-55](https://github.com/Khushboop14/Training_assignment/assets/126051670/da13b359-1932-4281-9c35-9659a6c7fbe0)

