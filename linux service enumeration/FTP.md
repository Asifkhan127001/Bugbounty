 ### WHAT IS FTP 

The File Transfer Protocol is a standard communication protocol used for the transfer of computer files from a server to a client on a computer network. FTP is built on a client–server model architecture using separate control and data connections between the client and the server.
  

 ## FTP ENUMERATION
  
 ## STEP 1
  Use Nmap Find Information
  
    nmap -A -p21 IP
   
 ### STEP 2
 
 first Cheack Anonymous Login use nmap script 
   
    ftp-anon.nse
    
 ### Step 3
 use some nmap script just like 
 
    ftp-anon.nse
    ftp-brute.nse
    tftp-enum.nse
    ftp-syst.nse
    etc.....    
     
  ### STEP 4
  use Metasploit auxiliary  
  
    auxiliary/scanner/ftp/anonymous
    auxiliary/scanner/ftp/ftp_version
    auxiliary/scanner/ftp/ftp_login
    etc....
    
  ## STEP 5
  ## BANNER GRABBING
   Banner Grabbing is Find Service Version Information
   
     telnet IP 21
     nmap -sV --script=banner IP
     nc IP 21
    
  ### STEP 6
  search exploit like
  
    google.com
    searchsploit
    cve
    github
    etc.....
    
  ## STEP 7
   Ftp Login
  
    ftp Ip
   
 ## FTP CONFIG FILE 
 
    /etc/vsftpd.conf
   
  
  
  
  
  
  
     
