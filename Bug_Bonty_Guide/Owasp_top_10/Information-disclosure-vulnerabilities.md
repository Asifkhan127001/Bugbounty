## Information-disclosure-vulnerabilities

Information disclosure, also known as information leakage, is when a website unintentionally reveals sensitive information to its users. 
Depending on the context, websites may leak all kinds of information to a potential attacker, including: 

## 1. web crawlers

Many websites provide files at /robots.txt and /sitemap.xml to help crawlers navigate their site. Among other things,
these files often list specific directories that the crawlers should skip, for example, because they may contain sensitive information. 

## Example

Open Burp suite intercept the request and sand the SCAN and select scan mode like Crawl

## 2. Find Old Information 

1. Use Search engines
2. Web archives

Search engines such as Google, Yahoo, and MSN. These maintain a fine grained index of all content that their powerful spiders have discovered,
and also cached copies of much of this content, which persists even after the original content has been removed.

archives that contain a full snapshot of files within (or indeed outside) the web root, 
possibly enabling you to easily identify all content and functionality within the application.

## 3. Directory listings

Web servers can be configured to automatically list the contents of directories that do not have an index page present.
This can aid an attacker by enabling them to quickly identify the resources at a given path, 
and proceed directly to analyzing and attacking those resources. 
It particularly increases the exposure of sensitive files within the directory that are not intended to be accessible to users, 
such as temporary files and crash dumps

Directory listings themselves are not necessarily a security vulnerability. However, if the website also fails to implement proper access control, 
leaking the existence and location of sensitive resources in this way is clearly an issue. 

## 4. Brute-Force Techniques

Use Brute-Force and find hidden file and directory 

## . Developer comments

During development, in-line HTML comments are sometimes added to the markup.
These comments are typically stripped before changes are deployed to the production environment. However, comments can sometimes be forgotten, missed,
or even left in deliberately because someone wasn't fully aware of the security implications. 
Although these comments are not visible on the rendered page, they can easily be accessed using Burp, or even the browser's built-in developer tools. 

Occasionally, these comments contain information that is useful to an attacker. For example, 
they might hint at the existence of hidden directories or provide clues about the application logic. 

## . Error messages

One of the most common causes of information disclosure is verbose error messages. As a general rule, 
you should pay close attention to all error messages you encounter during auditing. 

The content of error messages can reveal information about what input or data type is expected from a given parameter. 
This can help you to narrow down your attack by identifying exploitable parameters. 
It may even just prevent you from wasting time trying to inject payloads that simply won't work. 

Verbose error messages can also provide information about different technologies being used by the website. 
For example, they might explicitly name a template engine, database type, or server that the website is using, along with its version number.
This information can be useful because you can easily search for any documented exploits that may exist for this version. Similarly, 
you can check whether there are any common configuration errors or dangerous default settings that you may be able to exploit.
Some of these may be highlighted in the official documentation. 

## . Debugging data

For debugging purposes, many websites generate custom error messages and logs that contain large amounts of information about the application's behavior.
While this information is useful during development, it is also extremely useful to an attacker if it is leaked in the production environment. 

Debug messages can sometimes contain vital information for developing an attack, including: 

1.  Values for key session variables that can be manipulated via user input 
2.  Hostnames and credentials for back-end components 
3.  File and directory names on the server 
4.  Keys used to encrypt data transmitted via the client

 Debugging information may sometimes be logged in a separate file. If an attacker is able to gain access to this file,
 it can serve as a useful reference for understanding the application's runtime state. 
 It can also provide several clues as to how they can supply crafted input to manipulate the application state and control the information received.
 
 ## . Source code disclosure via backup files
 
 Obtaining source code access makes it much easier for an attacker to understand the application's behavior and construct high-severity attacks.
 Sensitive data is sometimes even hard-coded within the source code. 
 Typical examples of this include API keys and credentials for accessing back-end components. 
 
 If you can identify that a particular open-source technology is being used, this provides easy access to a limited amount of source code. 
 
 Occasionally, it is even possible to cause the website to expose its own source code. When mapping out a website,
 you might find that some source code files are referenced explicitly. Unfortunately, requesting them does not usually reveal the code itself. 
 When a server handles files with a particular extension, such as .php, it will typically execute 
 
 the code, rather than simply sending it to the client as text. However, in some situations,
 you can trick a website into returning the contents of the file instead. For example, 
 text editors often generate temporary backup files while the original file is being edited. 
 These temporary files are usually indicated in some way, such as by appending a tilde (~) 
 
 to the filename or adding a different file extension. Requesting a code file using a backup file extension can sometimes allow you 
 to read the contents of the file in the response. 
 
 ## 8. Information disclosure due to insecure configuration
 
 Websites are sometimes vulnerable as a result of improper configuration. This is especially common due to the widespread use of third-party technologies,
 whose vast array of configuration options are not necessarily well-understood by those implementing them. 
 
 In other cases, developers might forget to disable various debugging options in the production environment.
 For example, the HTTP TRACE method is designed for diagnostic purposes. If enabled, the web server will respond to 
 
 requests that use the TRACE method by echoing in the response the exact request that was received. 
 This behavior is often harmless, but occasionally leads to information disclosure, 
 such as the name of internal authentication headers that may be appended to requests by reverse proxies. 
 
 ## . Version control history
 
 Virtually all websites are developed using some form of version control system, such as Git. By default,
 a Git project stores all of its version control data in a folder called .git. Occasionally, 
 websites expose this directory in the production environment. In this case, you might be able to access it by simply browsing to /.git. 
 
 While it is often impractical to manually browse the raw file structure and contents, 
 there are various methods for downloading the entire .git directory.
 You can then open it using your local installation of Git to gain access to the website's version control history. 
 This may include logs containing committed changes and other interesting information. 
 
 This might not give you access to the full source code, but comparing the diff will allow you to read small snippets of code. 
 As with any source code, you might also find sensitive data hard-coded within some of the changed lines. 
 
