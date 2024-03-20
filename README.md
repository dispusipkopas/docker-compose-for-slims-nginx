# Docker Composer For Slims Nginx
docker ini merupakan custom konfigurasi build dengan nginx, php-fpm 8.1 dan mariadb 11.3

# Feature Composer For Slims Nginx
- date (Asia/Jakarta) pada setiap images docker
- nginx (Dockernginx)
  - privelege nginx:nginx pada directory nginx
- php-fpm (Dockerphp)
  - instalasi extensi intl, mbstring, gd, gettext, pdo, pdo_mysql, yaz
  - upload_max_filesize = 32M, post_max_size = 16M
  - php-vhost.conf di gunakan untuk custom pm.max_children = 50 (pada php-fpm)

## Installation
Sebelum menggunakan docker composer for slims nginx, lakukan git clone terlebih dahulu dari official repo [slims9_bulian](https://github.com/slims/slims9_bulian/) dan outputkan directory public_html
```sh
git clone https://github.com/slims/slims9_bulian.git public_html
chmod -R 777 public_html/{config,repository,images,files} ' = 16M
```
copy semua file ssl anda pada directory ssl

## Production
sebelum running ke production, pastikan konfigurasi pada directory nginx/conf/ terdapat file 
 - vhost.conf
   - vhost ini di gunakan untuk konfigurari port 80 pada nginx, sesuaikan namadomain.com dengan domain public anda
 - vhost-ssl.conf
   - vhost ini di gunakan untuk konfigurasi port 443 pada nginx, sesuaikan nama file ssl dengan ssl web anda terlebih dahulu (yourssl.crt dan yoursslkey.key)

Jalankan docker berikut ini
```sh
docker-compose up -d --build
docker container logs (nama images : php-fpm, nginx, mariadb) # untuk melihat error log pada saat running docker
```