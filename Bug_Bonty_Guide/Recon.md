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
   
    sublist3r -d <domain> -o <output>
 
  ## subfinder
  Subfinder is a subdomain discovery tool that discovers valid subdomains for websites by using passive online sources.
  
    subfinder -all -silent -d <Domain> -o <output>
 

  ## crtsh
  find subdomain use Certificate transparency 
  
    python3 crtsh.py -d example.com -r -w
    
  ## assetfinder
  Find domains and subdomains potentially related to a given domain
  
     assetfinder --subs-only <domain>
  
 ## dnsgen
 This tool generates a combination of domain names from the provided input
 
     cat domain.txt | dnsgen - > output
     
   ## shosubgo
   Small tool to Grab subdomains using Shodan api.
    
    ./shosubgo_linux -d target.com -s YourAPIKEY
  
 ### httprobe
  Take a list of domains and probe for working http and https servers
    
     cat subdomain.txt | httprobe > httprobe
 
 ## httpx 
 httpx is a fast and multi-purpose HTTP
 
    cat domain.txt | httpx -title -tech-detect -status-code  -mc 200,301

### Subdomain Take over tools
  
 ## subzy
 Subdomain takeover tool which works based on matching response fingerprints from can-i-take-over-xyz

    subzy  -hide_fails -targets subdomain.txt
    
  ## SubDomainizer
  SubDomainizer is a tool designed to find hidden subdomains and secrets present is either webpage, Github
  
    python3 SubDomainizer.py -u example.com -san same 
    
 ## Linked Discovery use Burp Suite
    
    burp-suite spider
    
  ## Hakrawler
   Fast golang web crawler for gathering URLs and JavaSript file locations. 
   This is basically a simple implementation of the awesome Gocolly library.
    
      cat urls.txt | hakrawler
    
  ## waybackurls
   waybackurls find subdomain,Endpoints,Tokens & secrets,IDs and secret files
    
     cat subdomain.txt | waybackurls -no-subs > [filename]
    
   ### gospider
   that helps you to enumerate all endpoints on your target!
    
     gospider -S sites.txt -o output 
      
   ## meg 
   Find Hidden Endpoint use meg Tools
   
     meg --verbose wordlist hosts.txt 
     
  ### Arjun 
  Arjun can find query parameters for URL endpoints
  
    arjun -i urls
     
 ### Aquatone 
 aqutone is a tool for visual inspection of websites across a large amount of hosts and is convenient  for quickly gaining an overview of HTTP-based     attack surface.
   
      cat domains-endpoints.txt | aquatone  
   
  ### EyeWitness 
  eyewitness is designed to take screenshots of websites provide some server header info, and identify default credentials if known
  
     eyewitness
    
 ### Nuclei 
 vulnerability scanner
 
     nuclei -update-templates
     nuclei -l url -o vulnerability 
     nuclei -l url -t </template/> path
     
  ### analyze web technologiess 
  
     Wappalyzer
     Netcraft
     Built with
     What web
     Whois
