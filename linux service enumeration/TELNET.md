   ### WHAT IS TELNET
   Telnet is an application protocol used on the Internet or local area network to provide a bidirectional interactive text-oriented communication facility using a virtual terminal connection
   
   ## TELNET ENUMERATION
     
   ## STEP 1  
   Use nmap Find Information
   
    nmap -A -p23 IP
     
   ## STEP 2
    RUN SOME NMAP SCRIPT 
    
    telnet-brute.nse
    telnet-ntlm-info.nse
    telnet-encryption.nse

   ## STEP 3 
   Use Metasploit Enumeration
   
    auxiliary/scanner/telnet/telnet_version
    auxiliary/scanner/telnet/telnet_login
    etc.....
    
  ## STEP 4 
   Banner Grabbing
   
    nc -vn IP 23
    
  ## STEP 5
  Telnet Login 
   
    telnet IP
    
  ## STEP 6 
   Telnet Config File
   
     /etc/inetd.conf
    /etc/xinetd.d/telnet
    /etc/xinetd.d/stelnet
    
    
    
    
    
      
 
