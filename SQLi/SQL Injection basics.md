**SQL Injection** - Vulnerability that consists of an attacker interfering with the SQL queries that an application makes to a database.


**Impact:**
	**Unauthorized access to sensitive data**
		- ***C**onfidentiality* - SQLi can be used to view sensitive information, such as application usernames and passwords
		- ***I**ntegrity* - SQLi can be used to alter data in the database
		- ***A**vailability* - SQLi can be used to delete data in the database
	**Remote code execution on the operating system**

**Types of SQL Injections** :
		**In-Band**:
			- *Error* - Techniqe where you force the databe to generate an error giving information how things operate at the backend.
			- *Union* -  Techniqe that leverages the union operator to combine the results of 2 queries into a single result set.
		**Inferential**:
			- Boolean - Asking the database true or false questions.
			- Time - Causing the database to pause for specified time.
		**Out-of-Band** 
			Occurs when the attacker is unable to use the same channel to launch the attack and gather the results of the attack. Usually relies on the ability of the application to make a network connection.

**Deep dive into the types of SQLi**:
	**In-Band SQLi**:
		- In-band SQLi occurs when the attacker uses the same communication channel to both launch the attack and gather the result of the attack.  
		- Retrieved data is presented directly in the application web page.  
		- Easier to exploit than other categories of SQLi  
		- Two common types of in-band SQLi  
			- **Error-based SQLi** 
				- Error-based SQLi is an in-band SQLi technique that forces the database to generate an error, giving the attacker information upon which to refine their injection.   
				- Example: 
					- **Input**: *blahblah.sth?id='*  
					- **Output**: *You have an error in your SQL sytax, check the manual that corresponds to your MySQL server version…*  
			- **Union-based SQLi**
				- Union-based SQLI is an in-band SQLi technique that leverages the UNION SQL operator to combine the results of two queries into a single result set.
				- Example:
					- **Input**: *blahblah.sth?id=' UNION SELECT username, password FROM users--*  
					- **Output**: 
						- carlos
						- admin
						- Alex
	**Inferential SQLi**:
		- SQLi vulnerability where there is no actual transfer of data via the web application.  
		- Just as dangerous as in-band SQL injection.  
		- Attacker able to reconstruct the information by sending particular requests and observingthe resulting behavior of the DB Server.  
		- Takes longer to exploit than in-band SQL injection.   
		- Two common types of blind SQLi:
			- **Boolean-based SQLi**:
				- Boolean-based SQLi is a blind SQLi technique that uses Boolean conditions to return a different result depending on whether the query returns a TRUE or FALSE result.  
			- **Time-based SQLi**:
				- Time-based SQLi is a blind SQLi technique that relies on the database pausing for a specified amount of time, then returning the results, indicating a successful SQL query execution.  
				- Example:
					- If the first character of the administrator’s hashed password is an ‘a’, wait for 10 seconds.
						 → response takes 10 seconds → first letter is ‘a’  
						 → response doesn’t take 10 seconds → first letter is not ‘a’
	**Out-of-Band SQLi**:
		- Vulnerability that consists of triggering an out-of-band network connection to a system that you control.  
		- Not common.  
		- A variety of protocols can be used (ex. DNS, HTTP)  
		- Example:
			- *'; exec master..xp_dirtree '//burpcollaborator.net/a'--*
