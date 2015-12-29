#### Checking if certain port is being used
##### 1. Using netstat command
- **netstat**: *show network status*
- it shows the contents of various network-related data structures.

``` shell
# Using "netstat" command
netstat -aln protocol | grep <port_number>

```
##### 2. Using lsof command
- **losf** : *list open files*
- open file may be regular file, a directory, a block special file, a character special file, an executing text reference, a library, **a stream or a network file (Internet socket, NFS file or UNIX domain socket)**
``` shell
# Using "lsof" command
# -i option: selects  the  listing  of  files  any  of  whose Internet address matches the address specified in i
lsof -i :8080
```

#### HotKeys within Terminal
1. **Ctrl-A**: moving cursor the the first character of current command
2. **Ctrl-E**: moving cursor to the end of character of current command
3. Deleting the current line: Ctrl-U or Ctrl-C
4. Finishing “ssh” session: exit
5. Showing most CPU consuming process: top -o cpu -n 10 -s 2 -i 2
6. Showing most memory consuming process: top -o mem -n 10 -s 2 -i 2
7. Showing which application using certain port: sudo lsof -i -P | grep <port_number>
