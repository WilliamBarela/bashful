# bashful
## Useful Bash commands.

## How to get ip from ifconfig
```ifconfig | grep -oP "[\d]{1,3}\.[\d]{1,3}\.[\d]{1,3}\.[\d]{1,3}" | sed -n "1p"```
