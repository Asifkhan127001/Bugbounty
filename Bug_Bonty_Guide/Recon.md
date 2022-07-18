    
 ## Amass
 
  Amass use for brutrforce and find subdomain
  
    amass enum -df Root-domain.txt -max-dns-queries 100 -w wordlist.txt -o output.txt
    
 ## Crtsh
 
 Find manualy 
 
    crt.sh

## Google Dorks

Use Google Dorking Find Subdomain like 

    site:google.com 
   
 Also suppose if a page is coming may time and you don’t want to see that in results like xyz.google.com, you can use “-” to remove that page
 
 Search will be now- site:google -xyz.google.com and the results will include pages from google.com but not xyz.google.com.


## Sublist3r
   Sublist3r enumerates subdomains using many search engines such as Google, Yahoo, Bing, Baidu and Ask.
   Sublist3r also enumerates subdomains using Netcraft, Virustotal, ThreatCrowd, DNSdumpster and ReverseDNS.
   
    sublist3r -d <domain> -o <output>
 
  ## subfinder
  Subfinder is a subdomain discovery tool that discovers valid subdomains for websites by using passive online sources.
  
    subfinder -all -silent -d <Domain> -o <output>
    
  ## assetfinder
  Find domains and subdomains potentially related to a given domain
  
     assetfinder --subs-only <domain>
   
  
 ### httprobe
  Take a list of domains and probe for working http and https servers
    
     cat subdomain.txt | httprobe > httprobe
 
 ## httpx 
 httpx is a fast and multi-purpose HTTP
 
    cat domain.txt | httpx -title -tech-detect -status-code  -mc 200,301,403
    
## dontgo403
dontgo403 is a tool to bypass 40X errors

    dontgo403 -u domain.com
    
 ## 4-zero-3
 4-ZERO-3 Tool to bypass 403/401
 
    ./403-bypass.sh -u domain.com --exploit
  
 ## subzy
 Subdomain takeover tool which works based on matching response fingerprints from can-i-take-over-xyz

    subzy  -hide_fails -targets subdomain.txt
    
 ## Step 1 
 check whiche hosting probide in website 
    
 ## Check Subdomain Vulnerable ,Not vulnerable
 
     https://github.com/EdOverflow/can-i-take-over-xyz
    
  ## SubDomainizer
  SubDomainizer is a tool designed to find hidden subdomains and secrets present is either webpage, Github
  
    python3 SubDomainizer.py -u example.com -san same 
    
 ## Fast-Google-Dorks-Scan
 The main idea of which is to collect all the possible Google dorks search combinations 
 
     ./FGDS.sh example.com
 
 ## Google Hacking 
 Google dork tools
 
     https://pentest-tools.com/information-gathering/google-hacking
 
    
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
     
  ## LinkFinder 
  LinkFinder is a python script written to discover endpoints and their parameters in JavaScript files
    
      
      
   ## meg 
   Find Hidden Endpoint use brute-force
   
     meg --verbose wordlist hosts.txt 
     
  ### Arjun 
  Arjun can find query parameters for URL endpoints
  
    arjun -i urls
    
  ## SubDomainizer
  SubDomainizer is a tool designed to find hidden subdomains and secrets present is either webpage, Github, and external
  javascripts present in the given URL. This tool also finds S3 buckets, cloudfront URL's
  
     python3 SubDomainizer.py -l url.txt 
     
  ## Gdorklinks.sh
  This tool is github-dorking
  
     Gdorklinks.sh domain.com 
     
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
