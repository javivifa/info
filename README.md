# COMANDOS MAS COMUNES PENTESTING 🚀

## Estabilizar shell 🔧
```
/usr/bin/script -qc /bin/bash /dev/null
Ctrl+z
stty raw -echo;fg
```
## NMAP básico 🔧
nmap -sC -sV -oN initial $IP

## Escalar priveligios 📖
```
cat /etc/crontab
```
Buscamos ficheros que con permiso SUID
	
SUID bits can be dangerous, some binaries such as passwd need to be run with elevated privileges (as its resetting your password on the system), however other custom files could that have the SUID bit can lead to all sorts of issues.
```
find / -perm -u=s -type f 2>/dev/null
```
https://gtfobins.github.io/#

## Reverse shell 📖
https://ironhackers.es/herramientas/reverse-shell-cheat-sheet/

## Técnicas varias 🔧
_Abrir terminal con python: python -c 'import pty;pty.spawn("/bin/bash")'
_Uso de hydra: hydra -L fsocity.dic -p test 10.10.192.186 http-post-form '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In&redirect_to=http%3A%2F%2F10.10.192.186%2Fwp-admin%2F&testcookie=1:F=Invalid username' otra opción final: /S=302'
