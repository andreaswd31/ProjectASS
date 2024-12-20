# ProjectASS


1.  Update dan Install MySQL di VM Database
# Update repository dan install MySQL:
sudo apt update && sudo apt upgrade -y
sudo apt install mysql-server -y

# Cek status Mysql
sudo systemctl status mysql

#mengaktifkan mysql dan memastikan sql sudah berjalan
sudo systemctl enable mysql
sudo systemctl start mysql


2. Konfigurasi MySQL untuk Remote Access
# login mysql
sudo mysql -u root

# Buat user baru untuk remote access
CREATE DATABASE laravel_db;
CREATE USER 'laravel_user'@'%' IDENTIFIED BY 'ProjekASS123@';
GRANT ALL PRIVILEGES ON laravel_db.* TO 'laravel_user'@'%';
FLUSH PRIVILEGES;
EXIT;

# Edit file konfigurasi MySQL untuk mengizinkan remote access
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
    ganti bind-address = 0.0.0.0

# restrat Mysql
sudo systemctl restart mysql

# Memastikan  port  3306 terbuka di farewall
sudo ufw allow 3306

3. Monitoring Database dan Melihat Order
# login ke Mysql
sudo mysql
USE laravel_db;
SHOW TABLES;
SELECT * FROM orders;
















