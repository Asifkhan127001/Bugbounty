### What Is Recon

 It refers to the process of collecting as much information as possible about the target system to find ways to penetrate into the system

### SUBDOMAIN TOOLS
   
## amass
    
    
### Knock
   Knockpy is a python3 tool designed to quickly enumerate subdomains on a target domain through dictionary attack 
   
    python3 knockpy.py domain.com -w /home/asifk/secLists/Discovery/DNS/dns-Jhaddix.txt -o /home/
    
## Sublist3r
   Sublist3r enumerates subdomains using many search engines such as Google, Yahoo, Bing, Baidu and Ask.
   Sublist3r also enumerates subdomains using Netcraft, Virustotal, ThreatCrowd, DNSdumpster and ReverseDNS.
   
    sublist3r.py -d example.com
    sublist3r.py -b -d example.com
     
  ## subfinder
  Subfinder is a subdomain discovery tool that discovers valid subdomains for websites by using passive online sources.
  
    subfinder -all -silent -d <Domain>
 

  ## crtsh
  find subdomain use Certificate transparency 
  
    crtsh -q <domain> -o > [filename]
    
  ## assetfinder
  Find domains and subdomains potentially related to a given domain
  
     assetfinder [--subs-only] <domain>
  
 ## dnsgen
 This tool generates a combination of domain names from the provided input
 
     cat domain.txt | dnsgen - > output
  
### Subdomain Take over tools
  
 ## subzy
 Subdomain takeover tool which works based on matching response fingerprints from can-i-take-over-xyz

    subzy -targets list.txt
   
 ### MassDNS
MassDNS is a simple high-performance DNS stub resolver tool

     ./massdns -r ../lists/resolvers.txt  subdomain.txt -o S -w output.txt
     cat massdns.txt | sed 's/A.*// ; s/CN.*// ; s/\..$//' > output.txt
   
  ### httprobe
  Take a list of domains and probe for working http and https servers
    
     cat subdomain.txt | httprobe > httprobe
   
  ## waybackurls
   waybackurls find subdomain,Endpoints,Tokens & secrets,IDs and secret files
    
     cat subdomain.txt | waybackurls > [filename]
    
   ### gospider
   that helps you to enumerate all endpoints on your target!
    
     gospider -S sites.txt -o output 
     
    
  ### Aquatone is a tool for visual inspection of websites across a large amount of hosts and is convenient 
  ### for quickly gaining an overview of HTTP-based attack surface.
  
      cat domains-endpoints.txt | aquatone
      
  ### Find Hidden Endpoint use meg Tools
  
   ## meg 
   Endpoint scan the masses
   
     meg --verbose wordlist hosts.txt 
     
  ### Arjun 
  Arjun can find query parameters for URL endpoints
  
   arjun -i urls
     
  ### EyeWitness is designed to take screenshots of websites provide some server header info, and identify default credentials if known
  
     eyewitness
    
  
  ### analyze web technologiess 
  
     Wappalyzer
     Netcraft
     Built with
     What web
     Whois
