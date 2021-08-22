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
  
  
  
  
  
