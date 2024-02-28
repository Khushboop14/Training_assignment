11. Fetch all the customers created in June 2023.
```sql
SELECT 
    p.party_id AS party_id, p.created_date AS created_date
FROM
    party AS p
        JOIN
    party_role AS pr ON p.party_id = pr.party_id
WHERE
    pr.role_type_id = 'CUSTOMER'
        AND p.STATUS_ID = 'PARTY_ENABLED'
        AND p.created_date BETWEEN '2023-06-01' AND '2023-06-30';
```
OUTPUT:

![Screenshot from 2024-01-29 17-51-33](https://github.com/Khushboop14/Training_assignment/assets/126051670/b898140f-bd59-4677-a2e6-cc60388449cb)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 16-28-30.png>)
