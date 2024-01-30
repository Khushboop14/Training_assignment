3. In the period following the New Year, what is the number of orders shipped from stores in the first 25 days?
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
![Screenshot from 2024-01-30 12-26-40](https://github.com/Khushboop14/Training_assignment/assets/126051670/aae73bed-0aab-425a-ac56-007dddd85b3e)
