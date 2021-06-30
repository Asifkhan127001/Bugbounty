               ## STORE PASSWORD & File Permissions
            


 ### history
 ### ls -la
 ### cat .bash_history
 ### history | grep pass
 ### grep --color=auto -rnw '/' -ie "PASSWORD" --color=always 2> /dev/null
 ### find . -type f -exec grep -i -I "PASSWORD" {} /dev/null \;
 ### /etc/security/opasswd
 
 
 
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














