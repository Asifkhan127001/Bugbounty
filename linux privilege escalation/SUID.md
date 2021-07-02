   ## Enumeration
    
        find / -perm -u=s -type f 2>/dev/null
        find / -type f -perm -04000 -ls 2>/dev/null
        
        
   ## Resource 
   
       https://gtfobins.github.io/
       
  ## Shared Object Injection
  
       find / -type f -perm -04000 -ls 2>/dev/null
       strace <PATH=2>&1>
       
       
  ## TYPE COMMAND 
  
       strace /usr/local/bin/suid-so 2>&1 | grep -i -E "open|access|no such file"
  
  
  ## OUTPUT
 
         
         
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



   










     
    