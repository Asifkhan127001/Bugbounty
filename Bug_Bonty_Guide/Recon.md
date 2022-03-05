### What Is Recon

 It refers to the process of collecting as much information as possible about the target system to find ways to penetrate into the system

### Subdomain 

   TOOLS
   
    amass
    SubBrute
    Knock
    DNSRecon
    Sublist3r
    subfinder
    Wayback Machine 
    crtsh
    assetfinder
    shodan
  
  ### Find HTTP server and HTTPS server 
  
    cat subdomain.txt | httprobe -p http:81 -p http:3000 -p https:3000 -p http:3001 -p https:3001 -p http:8000 -p http:8080 -p https:8443 -c 50 
    | tee online-domains.txt
    
  ### If you already have a list of domains and what to see if there are new ones
  
    cat new-output.txt | anew old-output.txt | httprobe
    
    
  ### This tool generates a combination of domain names from the provided input
  
    cat subdomain.txt | dnsgen - | httprobe
    
  ### Aquatone is a tool for visual inspection of websites across a large amount of hosts and is convenient 
  ### for quickly gaining an overview of HTTP-based attack surface.
  
      cat domains-endpoints.txt | aquatone
      
  ### Find Hidden Endpoint use meg Tools
  
     meg 
     
  ### EyeWitness is designed to take screenshots of websites provide some server header info, and identify default credentials if known
  
     eyewitness
     
  ### that helps you to enumerate all endpoints on your target!
    gospider
    
  ### Arjun designed to look for hidden HTTP parameters
  
    arjun
  
  ### analyze web technologiess 
  
     Wappalyzer
     Netcraft
     Built with
     What web
     Whois
