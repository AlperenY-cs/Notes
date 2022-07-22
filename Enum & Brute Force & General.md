### Nmap 
```
sudo nmap -sS -sV -n -vv -Pn -p- $IP
```

```
sudo nmap --script [paket]-* $IP
```

```
sudo nmap -p- --min-rate 1000 $IP
```

### WPScan

```
wpscan --url [url] -e u
```

```
 wpscan --url [url] -U [user] -P /usr/share/wordlists/rockyou.txt --password-attack wp-login -t 100
```

### FFUF
```
ffuf -w /usr/share/seclists/Discovery/DNS/namelist.txt -H 'Host: FUZZ.[url]' -u [url] -fs 2395
```

```
ffuf -w /usr/share/seclists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u [url] -mr "[message from login form]"
```

```
ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u [url] -fc 200
```

### Shell Stab
```
python3 -c 'import pty; pty.spawn("/bin/sh")'
python3 -c 'import pty; pty.spawn("/bin/bash")'

python3 -c 'import pty; pty.spawn("/bin/bash")'
export TERM=xterm

CTRL-z
stty raw -echo;fg
stty rows 55 columns 116
```

```
Without Python
usr/bin/script -qc /bin/bash /dev/null
```

### Hydra
```
hydra -l admin -P /usr/share/wordlists/rockyou.txt [ip] http-post-form "/admin/:user=^USER^&pass=^PASS^&LOGIN=Login:Username or password invalid"
```

```
hydra -l [user] -P [wordlist] [ip] [attack port/service]
```

### Capabilities 
```
getcap -r / 2>/dev/null
```

### Find Suid
```
find / -type f -perm -4000 2>/dev/null
```

```
find / -type f -user [user] -name "*file*" 2>/dev/null
```

```
find / -uid 0 -perm -4000 -type f 2>/dev/null
```

