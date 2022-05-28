  ## IDOR (Insecure direct object references)
  
  ## An IDOR Example  
  
   Step-1
  
   click the url and see the information profile 
     
      http://online-service.thm/profile?user_id=1305 
       
   step-2 
    
   And Change the url ID 
       
       http://online-service.thm/profile?user_id=1000
        
   And see another user information This is idor vulnerability  
