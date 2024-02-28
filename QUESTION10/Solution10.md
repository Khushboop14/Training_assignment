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
```
OUTPUT:

![Screenshot from 2024-02-22 19-48-33](https://github.com/Khushboop14/Training_assignment/assets/126051670/cbe5610b-eaeb-44cb-9b1d-4651bb54f639)

![Screenshot from 2024-02-22 19-50-32](https://github.com/Khushboop14/Training_assignment/assets/126051670/0031d37a-dc16-43df-a5bd-403ad9c17e4c)

![Screenshot from 2024-02-22 19-50-55](https://github.com/Khushboop14/Training_assignment/assets/126051670/ccda8d94-becf-4f1c-9caf-485720d0b396)

QUERY COST: 

![Alt text](<Screenshot from 2024-02-28 16-26-48.png>)


