# Notes of "How Linux Works 2nd Edition"

## Chapter 1: The Big Picture

General linux system organization:
- User Processes (GUI, servers, shell)
- Linux Kernel (system calls, process mgmt, memory mgmt, device drivers)
- Hardware (cpu, ram, disks, network ports)

kernel mode: no restrictions to cpu and memory  
user mode: parts of memory + safe cpu operations  

kernel's job:
- manage process
- manage memory
- system calls
- device drivers

kernel keeps the snapshot of memory and cpu state  during context switch.  
 cpu runs in kernel mode to switch processes for cpu to work on  

 `fork()` -> create a copy of the process  
 `exec()` -> replace the process with new one  

 all user process in linux starts with `fork()` except for `init` process  

`ls` in shell works like this:  
- shell `fork()` creating a copy of shell
- that copy `exec(ls)` replacing the process with `ls` 

## Chapter 2: Basic Commands and Directory Hierarchy

```
ioli@bipin:~$ find /usr/share -name words  
/usr/share/dict/words
```

`grep`, `find`, `diff`, `file`  

making shell variable an env variable:  
`$ VARIABLE=value`  
`$ export VARIABLE`  

modifying PATH env variable:  
`PATH=$PATH:newdir`  
appends the PATH variable  


