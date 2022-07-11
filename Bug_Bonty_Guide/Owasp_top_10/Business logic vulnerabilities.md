## Business logic vulnerabilities

Business logic vulnerabilities need manual intervention as No tool can detect these and they can vary from application to application and very hazardous. 
We have to understand application logic, application functionality, implementations, and business requirements. Whenever we intercept the request,
we have to manipulate specific parameters in the request or so to test for the business logic vulnerability


 ## Some common example of business logic:
 
 Manipulation in the product price in the request so we can purchase products in less amount during the online shopping.
 
 Manipulation in user-supplied input (too much quantity or –ve quantity) and not checked from the server-side.
 
 Manipulation in intended flow (2FA).
 
 ## 1. Manipulation in the product price in the request so we can purchase products in less amount during the online shopping.
 
 With Burp running, log in and attempt to buy the leather jacket. The order is rejected because you don't have enough store credit. 
 
 In Burp, go to "Proxy" > "HTTP history" and study the order process. Notice that when you add an item to your cart,
 the corresponding request contains a price parameter. Send the POST /cart request to Burp Repeater. 
 
 ## Request 
 
     POST /cart HTTP/1.1
Host: 0a5d00c0038b8062c09a11d7009700cc.web-security-academy.net
Cookie: session=VQHFrZjrndyN8kEb1ivgOD4X9YydBrGB
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 49
Origin: https://0a5d00c0038b8062c09a11d7009700cc.web-security-academy.net
Referer: https://0a5d00c0038b8062c09a11d7009700cc.web-security-academy.net/product?productId=1
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close

productId=1&redir=PRODUCT&quantity=1&price=133700
