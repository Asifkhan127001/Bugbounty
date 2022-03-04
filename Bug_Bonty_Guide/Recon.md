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
  
  ### analyze web technologiess 
  
     Wappalyzer
     Netcraft
     Built with
     What web
     Whois
