7. On a city-wise basis, what is the analysis of returns?
```sql
SELECT pa.city, count(rh.return_id) AS returns
FROM return_header as rh
JOIN return_contact_mech as rcm
ON rcm.return_id = rh.return_id
JOIN postal_address as pa
ON pa.contact_mech_id = rcm.contact_mech_id 
GROUP BY pa.city;
```
![Screenshot from 2024-02-01 10-06-27](https://github.com/Khushboop14/Training_assignment/assets/126051670/3579f8e5-0673-4841-af4d-c273909f3c61)
