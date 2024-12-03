# sisadmin.git.io
FInal Project OS Server dan Sistem Admin 

Domain : Kai.my.id

OS : Ubuntu Server 22.04.5 LTS


Layanan server yang sudah berhasil diinstall
1. OpenSSH
2. Apache2
3. Mysql


Langkah-langkah menginstall LAMP
1. Update
```bash
"sudo apt update && upgrade -y"
```
2. Menginstall Apache2
```bash
sudo apt install apache2
```
3. Melihat App List
```
sudo ufw app list
```
Maka Akan Muncul Output :
```bash
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
```
4.Menghidupkan Port Untuk Apache2
```bash
sudo ufw allow in "Apache"
```
5. Menghidupkan Firewall
```bash
sudo ufw enable
```
6. Mengecek Status App
```bash
sudo ufw status
```
7. Check Melalui Website
```bash
http://localhost / http://IP Address
```
