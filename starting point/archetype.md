Machine: Archetype
OS: windows
Machine Ip; 10.10.10.27
-----------------------------------------------------------------------------------------------------------------------
ENUM
#######################################################################################################################

                                              nmap

135/tcp  open  msrpc        Microsoft Windows RPC
139/tcp  open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds Windows Server 2019 Standard 17763 microsoft-ds
1433/tcp open  ms-sql-s     Microsoft SQL Server 2017 14.00.1000.00; RTM
| ms-sql-ntlm-info: 
|   Target_Name: ARCHETYPE
|   NetBIOS_Domain_Name: ARCHETYPE
|   NetBIOS_Computer_Name: ARCHETYPE
|   DNS_Domain_Name: Archetype
|   DNS_Computer_Name: Archetype
|_  Product_Version: 10.0.17763
| ssl-cert: Subject: commonName=SSL_Self_Signed_Fallback
| Not valid before: 2021-09-28T19:53:22
|_Not valid after:  2051-09-28T19:53:22
|_ssl-date: 2021-09-28T23:09:18+00:00; +25m13s from scanner time.
Aggressive OS guesses: Microsoft Windows 10 1709 - 1909 (93%), Microsoft Windows Vista SP1 (92%), Microsoft Windows Longhorn (92%), Microsoft Windows Server 2012 (92%), Microsoft Windows 10 1709 - 1803 (91%), Microsoft Windows 10 1809 - 1909 (91%), Microsoft Windows Server 2012 R2 (91%), Microsoft Windows Server 2012 R2 Update 1 (91%), Microsoft Windows Server 2016 build 10586 - 14393 (91%), Microsoft Windows 7, Windows Server 2012, or Windows 8.1 Update 1 (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 1h49m13s, deviation: 3h07m51s, median: 25m12s
| ms-sql-info: 
|   10.10.10.27:1433: 
|     Version: 
|       name: Microsoft SQL Server 2017 RTM
|       number: 14.00.1000.00
|       Product: Microsoft SQL Server 2017
|       Service pack level: RTM
|       Post-SP patches applied: false
|_    TCP port: 1433
| smb-os-discovery: 
|   OS: Windows Server 2019 Standard 17763 (Windows Server 2019 Standard 6.3)
|   Computer name: Archetype
|   NetBIOS computer name: ARCHETYPE\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2021-09-28T16:09:07-07:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-09-28T23:09:08
|_  start_date: N/A

TRACEROUTE (using port 587/tcp)
HOP RTT       ADDRESS
1   211.65 ms 10.10.14.1
2   211.82 ms 10.10.10.27
#######################################################################################################################
               
                                                            smbsclient
                                                            
  cat prod.dtsConfig                                              
<DTSConfiguration>
    <DTSConfigurationHeading>
        <DTSConfigurationFileInfo GeneratedBy="..." GeneratedFromPackageName="..." GeneratedFromPackageID="..." GeneratedDate="20.1.2019 10:01:34"/>
    </DTSConfigurationHeading>
    <Configuration ConfiguredType="Property" Path="\Package.Connections[Destination].Properties[ConnectionString]" ValueType="String">
        <ConfiguredValue>Data Source=.;Password=M3g4c0rp123;User ID=ARCHETYPE\sql_svc;Initial Catalog=Catalog;Provider=SQLNCLI10.1;Persist Security Info=True;Auto Translate=False;</ConfiguredValue>
    </Configuration>
</DTSConfiguration> 
\


 crendentials  sql_svc:M3g4c0rp123
 
 
 
 -----------------------------------------------------------------------------------------------------------------------
                                                    FOOTHOLD
 #######################################################################################################################
 
 mssqlclient.py
 userid=ARCHETYPE/sql_svc
 passwd=M3g4c0rp123
 #######################################################################################################################
 
 roor.txt 
 b91ccec3305e98240082d4474b848528
 user.txt
 3e7b102e78218e935bf3f4951fec21a3
 
 -----------------------------------------------------------------------------------------------------------------------
 
 -----------------------------------------------------------------------------------------------------------------------
 
