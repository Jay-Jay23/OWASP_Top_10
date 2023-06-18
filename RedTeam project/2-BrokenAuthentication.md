#  Broken Authentication

<p>This occurs when there are flaws in the authentication and session management mechanisms of a web application. This can lead to attackers gaining unauthorized access to user accounts and sensitive data</p>

### Remediation:
<p>The best way to prevent this vulnerability is to use strong passwords, implement multi-factor authentication, and use secure session management techniques such as session expiration and token-based authentication. 
</p>

## Broken Authentication example:

### Access other user:
<p>First login in to an account </p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/Broken.png" alt="broken">
<p>Logged In</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/Broken1.png" alt="broken">

<p>Once logged in either using MITM application such as burp Suite capture the traffic to review <b>Post</b> or <b>Get </b> traffic or do it manually by looking that the URL tab on the browser</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/Broken3.png" alt="broken">

<p>Pay attention to the parameter at the end of the URL which is <b>student 1</B> which tell us that current user but also begs the question whether the is a <b>student 2</B> </p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/Broken3.png" alt="broken">

<p>By modifing the parameter to <b>student 2</B> lets see what happens</p>
<p><b>Auction.f5demo.com/user_menu.php?nick=student2</b></p>

<p>Results is we get access to other student user account without the need to know their password </p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/Broken4.png" alt="broken">




