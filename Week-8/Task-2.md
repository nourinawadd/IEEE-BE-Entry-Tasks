1. Query: SELECT * FROM sales WHERE id = 5; </br>
Index used: clustered index </br>
Lookups: 1 </br>
2. Query: SELECT * FROM sales WHERE rental_date = "2021-01-01"; </br>
Index used: secondary index </br>
Lookups: 2 per matching row </br>
3. Query: SELECT inventory_id FROM sales WHERE rental_date = "2021-01-01"; </br>
Index used: secondary index </br>
Lookups: 1 </br>
4. Query: SELECT rental_date FROM sales WHERE inventory_id = 126; </br>
Index used: full scan of secondary index? </br>
Lookups: many </br>
5. Query: SELECT * FROM sales WHERE inventory_id = 126 and rental_date = "2021-01-01"; </br>
Index used: secondary index </br>
Lookups: 2 (per matching row if there are multiple matching rows) </br>
