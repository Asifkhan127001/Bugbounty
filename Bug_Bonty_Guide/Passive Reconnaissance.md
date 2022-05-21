## -[Information Gathering](https://dnsdumpster.com/)

## Information Gathering

 ## Whois 
 
    whois Domain.com
    
    
 ## Nslookup 
  nslook find IP v4 and IP V6 Cname, MX, TXT Record and Start of Authority
  
    nslookup OPTIONS DOMAIN_NAME SERVER

 Find Ip V4 Domain.com 
  
    nslookup -type=A Domain.com 1.1.1.1
    
  Find IP V6 domain.com
  
     nslookup -type=AAAA Domain.com 1.1.1.1 
     
  Find Email in Domai.com
  
     nslookup -type=MX Domain.com 1.1.1.1
     
   Find Cname in Domain.com
   
      dig domain.com
