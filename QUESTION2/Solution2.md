2.  Leading up to the New Year, what is the count of orders shipped from stores in the 25 days preceding the New Year?

```sql
SELECT 
    COUNT(DISTINCT oship.order_id) AS TOTAL_ORDERS
FROM
    order_shipment AS oship
        JOIN
    shipment AS s ON s.shipment_id = oship.shipment_id
        JOIN
    shipment_status AS st ON st.shipment_id = s.shipment_id
        JOIN
    facility AS f ON f.facility_id = s.origin_facility_id
        JOIN
    facility_type AS ft ON ft.facility_type_id = f.facility_type_id
WHERE
    ft.PARENT_TYPE_ID = 'PHYSICAL_STORE'
        AND st.status_id = 'SHIPMENT_SHIPPED'
        AND st.status_date BETWEEN DATE_SUB('2024-01-01', INTERVAL 25 DAY) AND CURDATE();

```
OUTPUT:

![Alt text](image.png)