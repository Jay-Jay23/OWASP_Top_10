# XML External Entity (XXE)

## Sensitive Data Exposure
<p>Is a vulnerability that abuses features of XML parsers/data. It often allows an attacker to interact with any backend or external systems that the application itself can access and can allow the attacker to read the file on that system.</p>

### Remediation:
<p>The best way to prevent this vulnerability is to disable XML external entities, use a different parser or library that is not vulnerable to XXE attacks, and validate and sanitize all user input.</p>

## XML External Entity (XXE) example:

### XXE Payload:
<p>Having a look around the webapp. </p>
<p>On the source code on the <b>/login page</b>. found a note mentioning a directory</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/xml.png" alt="XML">

<p>Navigating to the directory found, one file stood out as being likely to contain sensitive data, which i download for further deep dive</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/xml1.png" alt="XML">
t
<p>We can see that the downloaded <b>DB</b> is an SQlite database </p>
<p>To access it we will use: <b>sqlite3 <database-name>:</b></p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/xml2.png" alt="XML">

<p>From here we can see the tables in the database by using the <b>.tables</B> command: </p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/xml3.png" alt="XML">

<p>At this point we can dump all of the data from the table, but we won't necessarily know what each column means unless we look at the table information. First let's use <b>PRAGMA table_info(customers);</b> to see the table information, then we'll use <b>SELECT * FROM customers;</b> to dump the information from the table:</p>
<p>We can see from the table information that there are four columns: userID, username, and password.</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/xml4.png" alt="XML">
