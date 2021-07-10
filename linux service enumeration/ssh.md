   ### WHAT IS SSH 
   
   The Secure Shell Protocol is a cryptographic network protocol for operating network services securely over an unsecured network. Typical applications include remote command-line, login, and remote command execution, but any network service can be secured 


  ## SSH ENUMERATION
  
   STEP 1
    
   use nmap find information
   
    nmap -A -p22 IP
       
   STEP 2
  
  Use nmap Script Just Like
    
    ssh2-enum-algos.nse
    ssh-brute.nse

   STEP 3
   
   Use Metasploit auxiliary Find Information
    
    auxiliary/scanner/ssh/ssh_enumusers
    auxiliary/scanner/ssh/ssh_version
    auxiliary/scanner/ssh/ssh_login 
    auxiliary/scanner/ssh/ssh_login_pubkey
      
   ## STEP 4 
     
   Find Version Search Exploit
    
    google
    searchsploit
    github
    exploitdb
    cve
    
    
    
    
    
    
