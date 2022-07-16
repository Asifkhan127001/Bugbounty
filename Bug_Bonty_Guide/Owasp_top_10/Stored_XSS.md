## What Is An XSS Vulnerability ?

If you can execute your javascript code into a web page you’ve got an xss.
There are basically three types of xss :reflected , stored and DOM-based .
in this article we re going to talk about the DOM-based type

## What is a stored-XSS?

Stored XSS is when the XSS payload, or the malicious script, is stored on a server before being retrieved by the victim’s browser.

When an application accepts user input, stores it in its servers, 
and uses it to construct webpages without proper precautions, malicious JavaScript code can make its way into the database and then to victims’ browsers.


## 1. Stored XSS into anchor href attribute with double quotes HTML-encoded

## Step 1.

A blog post website and comment post function like post comment, name, email, and  website name so fill the fome and sand the request and intercept the request and send it to Burp Repeater.

## Request

    POST /post/comment HTTP/1.1
    Host: 0a5b002604a3359bc0c50a8f00660024.web-security-academy.net
    Cookie: session=Yxv1m3QuJvuaQUEGHIvYdvlqhJ25XhVt
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 126
    Origin: https://0a5b002604a3359bc0c50a8f00660024.web-security-academy.net
    Referer: https://0a5b002604a3359bc0c50a8f00660024.web-security-academy.net/post?postId=2
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

    csrf=L7OfJwLWiH4FitnL2hKcZ7FMTBnfAUAs&postId=2&comment=hello+bro&name=nasir&email=nasir%40khan.com&website=asifkhan

## Step 2.

Click The username and intercept the request and Observe that the website name is Reflected so This is vulnerably website name fill the fome here inject the paylods JavaScript Code 

    GET /asifkhan HTTP/1.1
    Host: 0a5b002604a3359bc0c50a8f00660024.web-security-academy.net
    Cookie: session=Yxv1m3QuJvuaQUEGHIvYdvlqhJ25XhVt
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://0a5b002604a3359bc0c50a8f00660024.web-security-academy.net/post?postId=2
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close

