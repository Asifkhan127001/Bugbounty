## Access control vulnerabilities
Access control (or authorization) is the application of constraints on who (or what) 
can perform attempted actions or access resources that they have requested. 
In the context of web applications, access control is dependent on authentication and session management: 

## Parameter-based access control methods
Some applications determine the user's access rights or role at login, and then store this information in a user-controllable location,
such as a hidden field, cookie, or preset query string parameter. 
The application makes subsequent access control decisions based on the submitted value

## For Example

    https://insecure-website.com/login/home.jsp?admin=true
    https://insecure-website.com/login/home.jsp?role=1
