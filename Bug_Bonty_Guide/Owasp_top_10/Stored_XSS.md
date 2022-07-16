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

A blog post website and comment post function like post command name email website name so fill the fome and sand the request and intercept the request and send it to Burp Repeater.  

## Step 2.

Click The username and intercept the request and Observe that the website name is Reflected so This is vulnerably website name fill the fome here inject the paylods JavaScript Code 

