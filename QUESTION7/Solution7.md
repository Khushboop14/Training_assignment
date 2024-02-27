7. On a city-wise basis, what is the analysis of returns?
QUERY:
```sql
SELECT pa.city, count(rh.return_id) AS returns
FROM return_header AS rh
JOIN return_contact_mech AS rcm
ON rcm.return_id = rh.return_id
JOIN postal_address AS pa
ON pa.contact_mech_id = rcm.contact_mech_id 
GROUP BY pa.city;
```
OUTPUT:

![Screenshot from 2024-02-01 10-06-27](https://github.com/Khushboop14/Training_assignment/assets/126051670/3579f8e5-0673-4841-af4d-c273909f3c61)


QUERY COST:

![Screenshot from 2024-02-27 10-57-14](https://github.com/Khushboop14/Training_assignment/assets/126051670/59eee927-2e92-4a11-94de-fac8a19e030a)
