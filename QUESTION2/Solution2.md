17.  Leading up to the New Year, what is the count of orders shipped from stores in the 25 days preceding the New Year?

```sql
SELECT count(distinct oship.order_id)
FROM order_shipment as oship
JOIN shipment as s
ON s.shipment_id = oship.shipment_id
JOIN shipment_status as st
ON st.shipment_id = s.shipment_id
JOIN facility as f
ON f.facility_id = s.origin_facility_id
JOIN facility_type as ft
ON ft.facility_type_id = f.facility_type_id
WHERE ft.PARENT_TYPE_ID = 'PHYSICAL_STORE'
AND st.status_id = 'SHIPMENT_SHIPPED'
AND st.status_date between "2023-12-01" AND "2023-12-25";

```
![Screenshot from 2024-01-30 12-23-50](https://github.com/Khushboop14/Training_assignment/assets/126051670/5d20c37e-8a33-4ad2-ac6f-93683f077948)
