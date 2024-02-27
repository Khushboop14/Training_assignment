11. Fetch all the customers created in June 2023.
```sql
SELECT p.party_id AS party_id , p.created_date as created_date
FROM party as p
JOIN party_role as pr
ON p.party_id = pr.party_id 
WHERE pr.role_type_id = 'CUSTOMER' 
AND p.STATUS_ID = 'PARTY_ENABLED'
AND p.created_date BETWEEN '2023-06-01' and '2023-06-30'
```
![Screenshot from 2024-01-29 17-51-33](https://github.com/Khushboop14/Training_assignment/assets/126051670/b898140f-bd59-4677-a2e6-cc60388449cb)
