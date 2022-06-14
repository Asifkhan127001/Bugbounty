## Direct bypass
Fuck the 2FA, just try to access the next endpoint directly (you need to know the path of the next endpoint).


## Ex 1
 
 1. Loging Account use username and password 
 2. Please enter your 4-digit security code 
 
  3. Check The Email and use the code and loging
  4. check the url parameter
  
         https://aca11f651ff1ebfac0cc7137009500a3.web-security-academy.net/my-account
         /my-account is end-point
         
 5. loging Vicatm Account and send the 4 digit code 

 6. This is Url in Vicatam account
 
        https://aca11f651ff1ebfac0cc7137009500a3.web-security-academy.net/login2
        
 7. And add the end-point parameter
 
        /my-account
        https://aca11f651ff1ebfac0cc7137009500a3.web-security-academy.net/my-account
 
 ## Finally Hack The Vicatam Account
 
 ## EX 2 2FA broken logic
 1.loging Account and intercept the request
 
    POST /login HTTP/1.1
    Host: acca1fb51e222ae1c096b0ee00130073.web-security-academy.net
    Cookie: session=Gkb38gS5iSHtopTvzjmVcGodyR7nbjoY
    Content-Length: 27
    Cache-Control: max-age=0
    Sec-Ch-Ua: "(Not(A:Brand";v="8", "Chromium";v="99"
    Sec-Ch-Ua-Mobile: ?0
    Sec-Ch-Ua-Platform: "Linux"
    Upgrade-Insecure-Requests: 1
    Origin: https://acca1fb51e222ae1c096b0ee00130073.web-security-academy.net
    Content-Type: application/x-www-form-urlencoded
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.74 Safari/537.36
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
    Sec-Fetch-Site: same-origin
    Sec-Fetch-Mode: navigate
    Sec-Fetch-User: ?1
    Sec-Fetch-Dest: document
    Referer: https://acca1fb51e222ae1c096b0ee00130073.web-security-academy.net/login
    Accept-Encoding: gzip, deflate
    Accept-Language: en-US,en;q=0.9
    Connection: close

    username=asif&password=khan
 
