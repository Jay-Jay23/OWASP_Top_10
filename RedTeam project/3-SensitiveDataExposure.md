## Sensitive Data Exposure
<p>When a webapp accidentally divulges sensitive data, we refer to it as "Sensitive Data Exposure". This is often data directly linked to customers (e.g. names, dates-of-birth, financial information, etc), but could also be more technical information, such as usernames and passwords.</p>

### Remediation:
<p></p>

## Sensitive Data Exposure example:

### Dumping data from a database & cracking hashes:
<p>Having a look around the webapp. </p>
<p>On the source code on the <b>/login page</b>. found a note mentioning a directory</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/SDE.png" alt="SDE">

<p>Navigating to the directory found, one file stood out as being likely to contain sensitive data, which i download for further deep dive</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/SDE1.png" alt="SDE">

<p>We can see that the downloaded <b>DB</b> is an SQlite database </p>
<p>To access it we will use: <b>sqlite3 <database-name>:</b></p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/SDE2.png" alt="SDE">

<p>From here we can see the tables in the database by using the <b>.tables</B> command: </p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/SDE3.png" alt="SDE">

<p>At this point we can dump all of the data from the table, but we won't necessarily know what each column means unless we look at the table information. First let's use <b>PRAGMA table_info(customers);</b> to see the table information, then we'll use <b>SELECT * FROM customers;</b> to dump the information from the table:</p>
<p>We can see from the table information that there are four columns: userID, username, and password.</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/SDE4.png" alt="SDE">

<p>We have the <b>userName (admin)</b>, and a <b>password hash (6eea9b7ef19179a06954edd0f6c05ceb)</b> </p>
<p>we will be using the online tool: <a href="https://crackstation.net/">Crackstation<a></a>. As it is extremely good at cracking weak password hashes. For more complicated hashes we would need more sophisticated tools such as <b>hashcat</b> etc</p>
<p>When we navigate to the website we are met with the following interface:</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/SDE5.png" alt="SDE">
<p>Paste in the password hash for <b>admin</b> which we found and click the "Crack Hashes" button</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/SDE6.png" alt="SDE">
<p>Hash was successfully broken, and that the user's password was <b>"qwertyuiop"</b> and can now login to  the webapp as Admin</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/SDE7.png" alt="SDE">
