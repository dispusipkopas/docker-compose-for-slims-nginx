docker composer ini akan menginstall images nginx, php-fpm 8.1, mariadb 11.3. Sebelum menggunakan docker compose ini lakukan git clone pada repository slims 9
'git clone https://github.com/slims/slims9_bulian.git public_html'
'chmod -R 777 public_html/{config,repository,images,files} '

Directory public_html adalah source code dari aplikasi slims, pada docker images **Dockerphp** sudah terdapat konfigurasi untuk menginstall php extension gd, mbstring, gettext, pdo, pdo_mysql, intl. Pada **Dockernginx** terdapat konfigurasi untuk membuat vhost, vhost-ssl (pastikan mengcopy file ssl (yourssl.crt dan yoursslkey.key) pada directory ssl.

'docker-compose up -d --build'
'docker container logs (nama images : php-fpm, nginx, mariadb) # untuk melihat error log pada saat running docker'
