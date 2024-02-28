1. Fetch the following columns for completed order items for sales orders of SM_STORE product store and that are physical items.
- ORDER_ID
- ORDER_ITEM_SEQ_ID
- PRODUCT_ID
- PRODUCT_TYPE_ID
- IS_PHYSICAL
- IS_DIGITAL
- SALES_CHANNEL_ENUM_ID
- ORDER_DATE
- ENTRY_DATE
- STATUS_ID
- STATUS_DATETIME
- ORDER_TYPE_ID
- PRODUCT_STORE_ID 

```sql


SELECT 
    os.ORDER_ID,
    os.ORDER_ITEM_SEQ_ID,
    oitm.PRODUCT_ID,
    os.STATUS_DATETIME,
    os.STATUS_ID,
    oh.PRODUCT_STORE_ID,
    pt.PRODUCT_TYPE_ID,
    pt.IS_DIGITAL,
    pt.IS_PHYSICAL,
    oh.SALES_CHANNEL_ENUM_ID,
    oh.ORDER_TYPE_ID,
    oh.ORDER_DATE,
    oh.ENTRY_DATE
FROM
    order_header AS oh
        JOIN
    order_item AS oitm ON oitm.ORDER_ID = oh.ORDER_ID
        JOIN
    order_status AS os ON oitm.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID
        AND oitm.order_id = os.ORDER_ID
        JOIN
    product AS p ON p.product_id = oitm.product_id
        JOIN
    product_type AS pt ON pt.PRODUCT_TYPE_ID = p.PRODUCT_TYPE_ID
WHERE
    oh.ORDER_TYPE_ID = 'SALES_ORDER'
        AND os.STATUS_ID = 'ITEM_COMPLETED'
        AND oh.PRODUCT_STORE_ID = 'SM_STORE'
        AND pt.IS_PHYSICAL = 'Y';

```
OUTPUT: 

![Alt text](<Screenshot from 2024-02-28 14-29-05.png>)


![Alt text](<Screenshot from 2024-02-28 14-29-17.png>)

QUERY COST:

![Alt text](<Screenshot from 2024-02-28 14-34-21.png>)