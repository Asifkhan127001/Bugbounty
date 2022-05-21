## Nmap
You can also provide a file as input for your list of targets,
  
    nmap -iL list_of_hosts.txt

Find Subnet

    nmap -sL -n ip
    
 Live Hoste Discover
 
    sudo nmap -PR -sn -iL ip.txt

 Nmap Host Discovery Using ICMP 
 
     sudo nmap -PE -sn 10.10.68.220/24


  ## WAF Baypass Ports
  
   FIN Scan
   
    sudo nmap -sF IP
        
        
   NULL SCAN 
    
    sudo nmap -sN IP
         
 ## Service Detection 
      
     nmap -sV IP   
        
 ## Nmap OS Detection
 
     nmap -sS -O IP
     
 ## Traceroute
  Nmap to find the routers between you and the target, just add --traceroute
  
     sudo nmap -sS --traceroute IP
      
 ## Nmap Scripting Engine
 find script 
 
     ls -la /usr/share/nmap/scripts | grep "ftp"

## Service Enumeration 

 telnet 
  
     sudo telnet IP
     username 
     password
     
     
  FTP
  
     sudo ftp IP
     username 
     password
     
  downlods file command 
  
      get filename
      
  
      
      
      
      
      
    
     
      
      
      
       
        
        
