  ## IDOR (Insecure direct object references)
  
   ## What is IDOR
   IDOR stands for Insecure Direct Object Reference and it is a vulnerability in which
   an attacker can access sensitive information by making unauthorized references. 
   For example, an user would retrieve his personal and confidential data by sending a request to the following URL:
      
      https://example.com/account.php?id=24
      
   The request collects the user ID from the URL parameter and then displays the information.
   But what happens when the user with ID of 24 sends the next request?
   
      https://example.com/account.php?id=11
      
   If the data belonging to the user with ID of 11 is returned then it is an IDOR issue.
   
   ## Types of IDOR
   1.Blind IDOR: The type of IDOR in which the results of the exploitation cannot be seen in the server response. 
   For example modifying other user private data without accessing it.
   
   2.Generic IDOR: The type of IDOR in which the results of the exploitation can be seen 
   in the server response. For example accessing confidential data or files belonging to another user.
   
   3.IDOR with Reference to Objects: Used to access or modify an unauthorized object. 
   For example accessing bank account information of other users by sending such a request
   
    →example.com/accounts?id={reference ID}
      
   4.IDOR with Reference to Files: Used to access an unauthorized file. 
   For example a live chat server stores the confidential conversations in files with names as 
   incrementing numbers and any conversation can be retrieved by just sending requests like this
   
    →example.com/1.log, example.com/2.log, example.com/3.log 
    
   and so on.
   
  ## An IDOR Example  
  
   Step-1
  
   click the url and see the information profile 
     
    http://online-service.thm/profile?user_id=1305 
       
   step-2 
    
   And Change the url ID 
       
    http://online-service.thm/profile?user_id=1000
        
   And see another user information This is idor vulnerability  
