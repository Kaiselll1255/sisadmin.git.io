# sisadmin.git.io
FInal Project OS Server dan Sistem Admin 

Domain : Kai.my.id

OS : Ubuntu Server 22.04.5 LTS


Layanan server yang sudah berhasil diinstall
1. OpenSSH ( 30 November 2024)
2. Apache2 ( 30 November 2024)
3. Mysql ( 03 Desember 2024)
4. PHP ( 03 Desember 2024)
5. Grafana ( 12 Desember 2024)
6. Prometheus (16 Desember 2024 )

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

Langkah-langkah Menginstall Grafana
1. Download Grafana GPG key
   ```bash
   wget -q -O - https://packages.grafana.com/gpg.key | gpg --dearmor | sudo tee /usr/share/keyrings/grafana.gpg > /dev/null
   ```
2. Menambahkan Repository Grafana
   ```bash
   echo "deb [signed-by=/usr/share/keyrings/grafana.gpg] https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
   ```
3. Update Sistem
   ```bash
   sudo apt update
   ```
4. Menginstall Grafana
   ```bash
   sudo apt install grafana
   ```
5. Menghidupkan Grafana
   ```bash
   sudo systemctl start grafana-server
   ```
6. Mengecek Status Grafana
   ```bash
   sudo systemctl status grafana-server
   ```
   Maka akan muncul Output seperti Berikut
   ![image](https://github.com/user-attachments/assets/812e6a48-e4d7-45a3-af30-90e3bfd12cc7)
   Yang menandakan apabila grafana sudah berhasil Hidup

Langkah-langkah Menginstall Prometheus
1. Update Sistem
```bash
sudo apt update
```
2. Buat group dan user sistem untuk prometheus
```bash
sudo groupadd --system prometheus
sudo useradd -s /sbin/nologin --system -g prometheus prometheus
```
Pic :![image](https://github.com/user-attachments/assets/e179cbd0-67ff-41ea-97d5-2a3af67b4c82)

3. Buat direktori untuk prometheus
```bash
sudo mkdir /etc/prometheus
sudo mkdir /var/lib/prometheus
```
Pic :![image](https://github.com/user-attachments/assets/9720e423-1da1-4cdc-aace-79bb1a381067)

4. Download prometheus
```bash
wget https://github.com/prometheus/prometheus/releases/download/v3.0.1/prometheus-3.0.1.linux-amd64.tar.gz
```
Pic :![image](https://github.com/user-attachments/assets/6b71ac05-ec4e-4fc4-892b-3245b685b760)

Ekstrak File nya
```bash
tar vxf prometheus*.tar.gz
```
Pic :![image](https://github.com/user-attachments/assets/df4fdc6c-9d2c-45ec-b557-a8089aa2f49b)
5. Pindah direktori ke dalam Prometheus
```bash
cd prometheus*/
```
Pic :![image](https://github.com/user-attachments/assets/a2196a8b-427a-4481-a0b0-b6abc8f540d3)        
6. Pindahkan file dan Konfigurasi Owner
```bash
sudo mv prometheus /usr/local/bin
sudo mv promtool /usr/local/bin
sudo chown prometheus:prometheus /usr/local/bin/prometheus
sudo chown prometheus:prometheus /usr/local/bin/promtool
```
Pic :![image](https://github.com/user-attachments/assets/02589510-8a2e-4246-bc8b-a3a6d84bda19)
7. Pindahkan file konfigurasi dan setting owner
```bash
sudo mv consoles /etc/prometheus
sudo mv console_libraries /etc/prometheus
sudo mv prometheus.yml /etc/prometheus
sudo chown prometheus:prometheus /etc/prometheus
sudo chown -R prometheus:prometheus /etc/prometheus/consoles
sudo chown -R prometheus:prometheus /etc/prometheus/console_libraries
sudo chown -R prometheus:prometheus /var/lib/prometheus
```
Pic :![image](https://github.com/user-attachments/assets/5fa59a33-f5a8-48b7-abb0-bf38edcdfc79)
8. Check Konfigurasi masing masing file
```bash
sudo nano /etc/prometheus/prometheus.yml
```
Untuk hasil defaultnya maka harus seperti 
```bash
# my global config
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: "prometheus"

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
      - targets: ["localhost:9090"]
```
9. Buatlah System service Prometheus
```bash
sudo nano /etc/systemd/system/prometheus.service
```
Masukkan konfigurasi berikut dan kemudian save & exit
```bash
[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=simple
ExecStart=/usr/local/bin/prometheus \
    --config.file /etc/prometheus/prometheus.yml \
    --storage.tsdb.path /var/lib/prometheus/ \
    --web.console.templates=/etc/prometheus/consoles \
    --web.console.libraries=/etc/prometheus/console_libraries

[Install]
WantedBy=multi-user.target
```
10. Reload dan Start Prometheus dan Check statusnya
```bash
sudo systemctl daemon-reload
sudo systemctl enable prometheus
sudo systemctl start prometheus
```
Check Statusnya
```bash
sudo systemctl status prometheus
```
Ouputnya :
![image](https://github.com/user-attachments/assets/fc8d7ab5-faaf-44b5-9d93-cc0869bdb9ce)


