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




 
 
