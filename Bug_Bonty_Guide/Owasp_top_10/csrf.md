 ## CSRF(Cross-site request forgery)
   Cross-Site Request Forgery (CSRF) is an attack that forces an end user to execute unwanted actions on a web application
   in which they’re currently authenticated. With a little help of social engineering (such as sending a link via email or chat), 
   an attacker may trick the users of a web application into executing actions of the attacker’s choosing. If the victim is a normal user, 
   a successful CSRF attack can force the user to perform state changing requests like transferring funds, changing their email address, and so forth. 
   If the victim is an administrative account, CSRF can compromise the entire web application.

   ## Resource 
   
     https://corneacristian.medium.com/top-25-csrf-bug-bounty-reports-ffb0b61afa55


  ## How to test for CSRF
   A good methodology to identify CSRF vulnerabilities would be to discover all the endpoints through which the application initiates and executes actions,   and apply tests for all three types of Cross-Site Request Forgery described above.



  ## CSRF type
  
   1. Basic
    
    Find CSRF
    email change functionality is vulnerable to CSRF
    Burp intercept request and manualy revewo 
    
 BURP request 
 
     POST /my-account/change-email HTTP/1.1
Host: 0a98002a031dc494c0bb490d002b0039.web-security-academy.net
Cookie: session=Xi4wUL9QBc5WIvwtzoN7dwzzJdwtDVi5
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 22
Origin: https://0a98002a031dc494c0bb490d002b0039.web-security-academy.net
Referer: https://0a98002a031dc494c0bb490d002b0039.web-security-academy.net/my-account
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close

email=nasir%40khan.com
