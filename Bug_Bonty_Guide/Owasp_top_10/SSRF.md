## SSRF(Server-side request forgery)

  Server-side request forgery (also known as SSRF) is a web security vulnerability 
  that allows an attacker to induce the server-side application to make requests to an unintended location. 
  
  In a typical SSRF attack, the attacker might cause the server to make a connection to internal-only services within the organization's infrastructure.
  In other cases, they may be able to force the server to connect to arbitrary external systems,potentially 
  leaking sensitive data such as authorization credentials. 


 ## How To Find SSRF 
 
  First check the all url rquest in burp proxy, and observe that request, 2 url first server and secand server to call secand server request
  here is posible SSRF vulnerability 
  
     GET /?url=http://google.com/ HTTP/1.1
     Host: example.com
