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
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
