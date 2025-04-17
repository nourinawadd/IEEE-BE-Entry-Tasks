Indexes:
1. Composite index on order_date DESC </br>
- helps in dashboard loading last 20 orders
- DESC order matches the query pattern
- fulfills the reporting job's date filtering needs

2. Index on product_id, order_date </br>
- optimizes the daily revenue report by produt
- better than seperate indexes due to the combines query pattern
- composite index allows efficient filtering on both product_id and date range

3. Index on customer_id
- fulfills the analytic system's customer behaviour analysis
- frequently filtered column in queries
