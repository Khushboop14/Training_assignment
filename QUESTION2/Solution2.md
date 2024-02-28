2.Fetch the following columns for completed return items of SM_STORE for ecom return channel.  
- RETURN_ID 
- ORDER_ID
- PRODUCT_STORE_ID 
- STATUS_DATETIME
- ORDER_NAME 
- FROM_PARTY_ID 
- RETURN_DATE 
- ENTRY_DATE
- RETURN_CHANNEL_ENUM_ID
  

```sql 
SELECT 
    oh.order_id,
    oh.order_name,
    oh.product_store_id,
    rh.return_id,
    rh.return_channel_enum_id,
    rh.ENTRY_DATE,
    rh.RETURN_DATE,
    rh.FROM_PARTY_ID,
    rs.status_datetime
FROM
    return_header AS rh
        JOIN
    return_item AS ri ON rh.return_id = ri.return_id
        AND ri.status_id = 'RETURN_COMPLETED'
        AND rh.RETURN_CHANNEL_ENUM_ID = 'ECOM_RTN_CHANNEL'
        JOIN
    return_status AS rs ON ri.return_id = rs.return_id
        AND ri.return_item_seq_id = rs.return_item_seq_id
        JOIN
    order_header AS oh ON oh.order_id = ri.order_id
        AND oh.PRODUCT_STORE_ID = 'SM_STORE';

```

OUTPUT: 

![Alt text](<Screenshot from 2024-02-28 15-04-38.png>)


![Alt text](<Screenshot from 2024-02-28 15-04-10.png>)


QUERY COST:

![Alt text](<Screenshot from 2024-02-28 15-04-17.png>)

