 ## CSRF(Cross-site request forgery)
   Cross-Site Request Forgery (CSRF) is an attack that forces an end user to execute unwanted actions on a web application
   in which they’re currently authenticated. With a little help of social engineering (such as sending a link via email or chat), 
   an attacker may trick the users of a web application into executing actions of the attacker’s choosing. If the victim is a normal user, 
   a successful CSRF attack can force the user to perform state changing requests like transferring funds, changing their email address, and so forth. 
   If the victim is an administrative account, CSRF can compromise the entire web application.

   ## Resource 
   
          https://corneacristian.medium.com/top-25-csrf-bug-bounty-reports-ffb0b61afa55


  ## How to test for CSRF
   A good methodology to identify CSRF vulnerabilities would be to discover all the endpoints through which the application initiates and executes actions, and apply tests for all three types of Cross-Site Request Forgery described above.
