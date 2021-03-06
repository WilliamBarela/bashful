# bashful
## Useful Bash commands.

### How to get ip from ifconfig
```
  ifconfig | grep -oP "[\d]{1,3}\.[\d]{1,3}\.[\d]{1,3}\.[\d]{1,3}" | sed -n "1p"
```

### ssh gateway port forwarding to scp data behind firewall 
```
  # In first terminal, port forward, just use eraider password, do not continue with hostname
  ssh -L 2222:my_server.ttu.edu:22 eraider_username@ssh.ttu.edu
  
  # In second terminal (with first open), localhost is now my_server
  # When prompted for scp, enter password for user on my_server
  scp -P 2222 username_on_my_server@localhost:~/code/test.txt ./
  
  # Alternatively, you can just leave the port forwarded ssh tunnel open.
  # And then you can just ssh in using the port listed:
  ssh -p 2222 username_on_my_server@localhost
```

## declaring an array in bash of ls of directories, safeguarding for spaces in directory names
```bash
  # declare \n as the input field separator, assign output of ls directories (ls -d), delimited with new line character (ls -1) and quoting directories
  IFS=$'\n' a=("$(ls -1 -d */)")
  
  # looping through array to demonstrate result of above
  for i in ${a[@]}; do echo $i; done
```
