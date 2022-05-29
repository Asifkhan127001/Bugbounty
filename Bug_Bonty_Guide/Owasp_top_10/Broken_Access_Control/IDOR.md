  ## IDOR (Insecure direct object references)
  
   ## What is IDOR
   IDOR stands for Insecure Direct Object Reference and it is a vulnerability in which
   an attacker can access sensitive information by making unauthorized references. 
   For example, an user would retrieve his personal and confidential data by sending a request to the following URL:
      
  ## An IDOR Example  
  
   Step-1
  
   click the url and see the information profile 
     
    http://online-service.thm/profile?user_id=1305 
       
   step-2 
    
   And Change the url ID 
       
    http://online-service.thm/profile?user_id=1000
        
   And see another user information This is idor vulnerability  
