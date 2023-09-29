<h1> Update a file through a Python algorithm </h1>

<h2>Description</h2>
At my organization, access to restricted content is controlled with an allow list of IP addresses. The "allow_list.txt" file identifies these IP addresses. A separate remove list identifies IP addresses that should no longer have access to this content. I created an algorithm to automate updating the "allow_list.txt" file and remove these IP addresses that should no longer have access. 
<br />

<h2> Open the file that contains the allow list:</h2>
For the first part of the algorithm, I opened the "allow_list.txt" file. First, I assigned this file name as a string to the import_file variable:
<br/>
 <img src="https://i.imgur.com/HfNgfc9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
Then, I used a with statement to open the file:
<br/>
 <img src="https://i.imgur.com/87MWrnT.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
In my algorithm, the with statement is used with the .open() function in read mode to open the allow list file for the purpose of reading it. The purpose of opening the file is to allow me to access the IP addresses stored in the allow list file. The with keyword will help manage the resources by closing the file after exiting the with statement. In the code with open(import_file, "r") as file:, the open() function has two parameters. The first identifies the file to import, and then the second indicates what I want to do with the file. In this case, "r" indicates that I want to read it. The code also uses the as keyword to assign a variable named file; file stores the output of the .open() function while I work within the with statement.
 
<h2> Read the file contents: </h2>
 In order to read the file contents, I used the .read() method to convert it into the string.
<br/>
<br/>
<img src="https://i.imgur.com/PWtsHT0.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
When using an .open() function that includes the argument "r" for “read,” I can call the .read() function in the body of the with statement. The .read() method converts the file into a string and allows me to read it. I applied the .read() method to the file variable identified in the with statement. Then, I assigned the string output of this method to the variable ip_addresses. <br/>
In summary, this code reads the contents of the "allow_list.txt" file into a string format that allows me to later use the string to organize and extract data in my Python program.

 <h2> Read the file contents: </h2>

 
After investigating the organization’s data on login attempts, I believe there is an issue with the login attempts that occurred outside of Mexico. These login attempts should be investigated. <br/>
The following code demonstrates how I created a SQL query to filter for login attempts that occurred outside of Mexico:
<br/>
<br/>
<img src="https://i.imgur.com/ELRUin1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all login attempts that occurred in countries other than Mexico. First, I started by selecting all data from the log_in_attempts table. Then, I used a WHERE clause with NOT to filter for countries other than Mexico. I used LIKE with MEX% as the pattern to match because the dataset represents Mexico as MEX and MEXICO. The percentage sign (%) represents any number of unspecified characters when used with LIKE. 

<p align="center">
Retrieve employees in Marketing: <br/>
 
My team wants to update the computers for certain employees in the Marketing department. To do this, I have to get information on which employee machines to update.
<br/>
The following code demonstrates how I created a SQL query to filter for employee machines from employees in the Marketing department in the East building.
<br/>
 <img src="https://i.imgur.com/KDTLkdd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all employees in the Marketing department in the East building. First, I started by selecting all data from the employees table. Then, I used a WHERE clause with AND to filter for employees who work in the Marketing department and in the East building. I used LIKE with East% as the pattern to match because the data in the office column represents the East building with the specific office number. The first condition is the department = 'Marketing' portion, which filters for employees in the Marketing department. The second condition is the office LIKE 'East%' portion, which filters for employees in the East building.
 
<p align="center">
Retrieve employees in Finance or Sales: <br/>
 
The machines for employees in the Finance and Sales departments also need to be updated. Since a different security update is needed, I have to get information on employees only from these two departments.<br/>
The following code demonstrates how I created a SQL query to filter for employee machines from employees in the Finance or Sales departments.
<br/>
 <img src="https://i.imgur.com/bOHzPTz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br/>
 <br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all employees in the Finance and Sales departments. First, I started by selecting all data from the employees table. Then, I used a WHERE clause with OR to filter for employees who are in the Finance and Sales departments. I used the OR operator instead of AND because I want all employees who are in either department. The first condition is department = 'Finance', which filters for employees from the Finance department. The second condition is department = 'Sales', which filters for employees from the Sales department.

 <p align="center">
Retrieve all employees not in IT: <br/>
 
My team needs to make one more security update on employees who are not in the Information Technology department. To make the update, I first have to get information on these employees.<br/>
The following demonstrates how I created a SQL query to filter for employee machines from employees not in the  Information Technology department.
<br/>
 <img src="https://i.imgur.com/02gOC9n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
The first part of the screenshot is my query, and the second part is a portion of the output. The query returns all employees not in the Information Technology department. First, I started by selecting all data from the employees table. Then, I used a WHERE clause with NOT to filter for employees not in this department.

<p align="center">
Summary: <br/>
 
I applied filters to SQL queries to get specific information on login attempts and employee machines. I used two different tables, log_in_attempts and employees. I used the AND, OR, and NOT operators to filter for the specific information needed for each task. I also used LIKE and the percentage sign (%) wildcard to filter for patterns.
<br/>
<br/>

 
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
