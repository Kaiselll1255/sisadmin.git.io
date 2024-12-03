# sisadmin.git.io
FInal Project OS Server dan Sistem Admin 

Domain : Kai.my.id

OS : Ubuntu Server 22.04.5 LTS


Layanan server yang sudah berhasil diinstall
1. OpenSSH ( 30 November 2024)
2. Apache2 ( 30 November 2024)
3. Mysql ( 03 Desember 2024)
4. PHP ( 03 Desember 2024)

Langkah-langkah menginstall OpenSSH
1. Update
```bash
sudo apt update
```
2.Meninstall OpenSSH
```bash
sudo apt install openssh-server
```
3. Mengecheck Status SSH
```bash
sudo systemctl status ssh
```
4. Menghidupkan Port 22
```bash
sudo systemctl enable
```


Langkah-langkah menginstall Apache2
1. Update
```bash
sudo apt update && upgrade -y
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

Langkah-langkah menginstall Mysql
1. Update
```bash
sudo apt update
```
2. Menginstall Mysql
```bash
sudo apt install mysql-server
```
3. Membuat User dan Password untuk Mysql Server
```bash
sudo mysql
```
Kemudian Setelah Masuk ke dalam Mysql
```bash
mysql> ALTER USER 'USERNAME'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PASSWORD';
```
Setelah Mengganti Username dan Password 
```bash
mysql> exit
```

Langkah-langkah menginstall PHP
1. Update
```bash
sudo apt update
```
2. Menginstall PHP
```bash
sudo apt install php libapache2-mod-php php-mysql
```
3. Check Versi PHP
```bash
php -v
```
4. Mengkonfigurasi File
```bash
cd /var/www/html
```
```bash
ls
```
maka akan muncul output :
```bash
index.html
```
Langkah Selanjutnya membuat sebuah file kosong dengan extension PHP
```bash
sudo nano index.php
```
File tersebut diisi dengan
```bash
<?php
phpinfo();
```
Kemudian Save File tersebut
5. Mengecheck apakah file tersebut sudah berhasil atau belum
```bash
http://localhost/index.php / http://IP_Address/index.php
```
![image](https://github.com/user-attachments/assets/4bb0260a-9ec2-49fa-92b4-1dbd598624bb)
Contoh apabila sudah berhasil terinstall
