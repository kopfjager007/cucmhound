# cucmhound

cucmHound is a tool to test Cisco UCM servers and Cisco VoIP phones for common misconfigurations.  

## Requirements  

You'll need `xmllint` from `libxml2-dev`.  

```bash
sudo apt install libxml2-dev
```

## Usage  

```text
                            _   _                       _ 
                           | | | |                     | |
   ___ _   _  ___ _ __ ___ | |_| | ___  _   _ _ __   __| |
  / __| | | |/ __| '_ ` _ \|  _  |/ _ \| | | | '_ \ / _` |
 | (__| |_| | (__| | | | | | | | | (_) | |_| | | | | (_| |
  \___|\__,_|\___|_| |_| |_\_| |_/\___/ \__,_|_| |_|\__,_|
                                                         
                                   github.com/kopfjager007
  Usage:
    -m      Mode
              (Attack)
              configthief - Enumerates Cisco IP Phones and CUCM server, then pulls configs 
                            and parses stored SSH credentials.
                             *Requires target CSV file as "-i <FILE>.csv".
              getusersuds - Enumerates AD users from the User Data Service API.
                             *Requires "-c <CUCM_IP>"

              (Recon/Probing)
              findcucm    - Idenify CUCM servers. 
                            Will also look for "ConfigFileCacheList.txt" on CUCM server.
                             *Requires target CSV file as "-i <FILE>.csv"
              cucmversion - Enumerates the CUCM version.
                             *Requires "-c <CUCM_IP>"
              cachelist   - Attempt to retrieve the ConfigFileCacheList.txt from a CUCM Server.
                             *Requires "-c <CUCM_IP>"
              
    -i      CSV Infile (see attack modes for needed file).
              
    -c      CUCM Server IP Address. 
              
    -h      Print this help and exit. 
              
  Examples: 
    1. Run ConfigThief mode to find CUCM servers and Cisco Phones and pull down configs if found.
       $ cucmHound -m configthief -i int-targets.csv 
              
    2. Enumerate AD users from CUCM UDS API. 
       $ cucmHound -m getusersuds -c <CUCM_IP> 
              
  Note: Targets file "<FILE.csv>" used with the "-i" flag can be obtained by parsing Nmap
        and should be in the following format, one target per line.
 
        IP Address,Host Name,Operating System,Services
        10.10.10.10,Unknown,Unknown,TCP80; TCP443;
```  
