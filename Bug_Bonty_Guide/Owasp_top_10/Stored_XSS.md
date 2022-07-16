## What Is An XSS Vulnerability ?

If you can execute your javascript code into a web page you’ve got an xss.
There are basically three types of xss :reflected , stored and DOM-based .
in this article we re going to talk about the DOM-based type

## What is a stored-XSS?

Stored XSS is when the XSS payload, or the malicious script, is stored on a server before being retrieved by the victim’s browser.

When an application accepts user input, stores it in its servers, 
and uses it to construct webpages without proper precautions, malicious JavaScript code can make its way into the database and then to victims’ browsers.
