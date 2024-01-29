```sql 
select os.ORDER_ID, os.ORDER_ITEM_SEQ_ID, oitm.PRODUCT_ID, os.STATUS_DATETIME, os.STATUS_ID, 
oh.PRODUCT_STORE_ID, pt.PRODUCT_TYPE_ID, pt.IS_DIGITAL, pt.IS_PHYSICAL, oh.SALES_CHANNEL_ENUM_ID, oh.ORDER_TYPE_ID, oh.ORDER_DATE, oh.ENTRY_DATE
from order_header as oh 
join order_item as oitm 
on oitm.ORDER_ID = oh.ORDER_ID 
Join order_status as os
on oitm.ORDER_ITEM_SEQ_ID = os.ORDER_ITEM_SEQ_ID AND oitm.order_id = os.ORDER_ID
join product as p
on  p.product_id = oitm.product_id
join product_type as pt
on pt.PRODUCT_TYPE_ID = p.PRODUCT_TYPE_ID
where  oh.ORDER_TYPE_ID = 'SALES_ORDER'
AND os.STATUS_ID = 'ITEM_COMPLETED'  
AND oh.PRODUCT_STORE_ID = 'SM_STORE'
AND pt.IS_DIGITAL = 'N' 
AND pt.IS_PHYSICAL = 'Y';

'''
![Screenshot from 2024-01-29 12-59-39](https://github.com/Khushboop14/Training_assignment/assets/126051670/021bfc93-2a4d-47e9-9f98-7d5751febc5c)
