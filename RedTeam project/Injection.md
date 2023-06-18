# Injection
<p>Injection Vulnerability occurs when an attacker can inject untrusted data into a web application. This can Happen when user input is not properly validated or sanitized, allowing the attacker to inject malicious code. The most common type of injection vulnerabilities are SQL injection and command injection</P>

## SQL injection example:

### Retrieving hidden data:
<p>SQL injection vulnerability in WHERE clause allowing retrieval of hidden data</p>
<img src="" alt="sql">
<p>By adding an a single parathesis (') to test for SQL vulnerability <b>/category=Gifts’</b> server gives us an error relaying that the isnt a parameterized queries or prepared statement in the code </p>
<img src="" alt="sql2">
<p>Adding the following SQL code <b>/category=Gifts’+OR+1=1—</b> the sites shows hidden products not yet published</P>
''' SQL
Select * from product where category= 'Gitfts' OR 1=1
'''
<img src="" alt="sql3">


