## What Is An XSS Vulnerability ?

If you can execute your javascript code into a web page you’ve got an xss.
There are basically three types of xss :reflected , stored and DOM-based .
in this article we re going to talk about the DOM-based type.

## What Is Dom XSS ?

it’s a client side vulnerability which happens when javascript code takes the source and mishandling
it in a way that causes execution of it in sink(execution function).

## When we talk about javascript there are mainly 4 categories of sources 

 URL-Based sources such as : document.url , document.location.hash
 
 Navigation based sources such as : document.referer , window.name
 
 communication sources such as : ajax , websockets and webmessaging
 
 storages sources such as : cookies , localstorage ,session storage.
 
 ## And 4 main categories of sinks 
 
  javascript execution sinks as : eval(payload) , setTimout(payload,100) , <div onclick=”payload”>
  
  HTML execution sinks as : htmlElement.innerHTML= payload , document.write(payload)
  
  javascript URI sinks as : document.location = payload , location.href = payload
  
  HTML modification to behaviour change : (element).src or (element).href (in certain elements)
