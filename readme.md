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

Terminal keyboard shortcuts:  
`CTRL-A` : move to the start of line  
`CTRL-E` : move to the end of line  
`CTRL-U` : delete whole line backward

Search manual by keyword:  
`$ man -k keyword `  

Detail and conceptucal documentation:  
`$ info command`

Redirect to file:  
overwrite file: `$ command > file`  
append to file: `$ command >> file` 

Redirect stdout to outfile and stderr to errorfile:  
`$ command > outfile 2> errorfile `  

Redirect stderr to same as stdout:  
`$ command > logfile 2>&1`  

double dollar gives the pid of current shell  
`$ ps u $$`  

freeze the process  
`$ kill -STOP pid`  
resume the process  
`$ kill -CONT pid`  

suspended processes  
`$ jobs `  
resume by bringing to foreground  
`$ fg`  
resume in background  
`$ bg`  

compress  
`$ gzip file`  
decompress  
`$ gunzip file.gz`  
archive  
`$ tar cvf archive.tar file1 file2 file3 ..`  
unpack archive  
`$ tar xvf archive.tar`  

decompressing compressed archive  
`$ gunzip archive.tar.gz`  
check what files are there in archive  
`$ tar tvf archive.tar`  
extract from archive  
`$ tar xvf archive.tar`  

pipelined way of decompressing compressed archive  
`$ gunzip -c archive.tar.gz | tar xvf -`  

## Chapter 3: Devices  

device files:  
*b* : block device (eg. disks)  
*c* : character device (eg. printer)  
*p* : pipe device  
*s* : socket device   