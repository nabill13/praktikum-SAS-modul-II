# **# PRAKTIKUM MODUL II **

# **SISTEM ADMINISTRASI SERVER**

#### KELOMPOK II

#### -> Evyra Rizki Safitri   

#### -> Nabila Nur Amalia

#### -> M. Pradata Yuda P



### <h2> 1. Rubah LXC landing dengan ubuntu focal (destroy n create, same ip, same name)</h2>

- Setting network machine ke bridge adapter

1. Cek lxc yang ada, dengan perintah : 

```
sudo lxc-ls -f
```

 ![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/0.PNG?raw=true)

2. Harap menghentikan lxc yang akan di hapus terlebih dahulu lalu destroy lxc ubuntu landing dan ubuntu php 7.4, dengan perintah  

```
rm /var/lib/lxc/ubuntu_landing/lxc_snapshots
sudo lxc-destroy (nama lxc yg akan di hapus)
```

![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/1.PNG?raw=true)

![1-1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/1-1.PNG?raw=true)

3. Cek apakah lxc yang sudah di hapus masih ada atau tidak dengan perintah

```
 sudo lxc-ls -f
```

![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/2.PNG?raw=true)

4. Create ubuntu_landing

```
sudo lxc-create -n ubuntu_landing -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
```

![3.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/3.PNG?raw=true)

5.  Jalankan ubuntu_landing. Jika ubuntu_landing berhasil dijalankan, maka langkah selanjutnya yaitu install net-tools

```
lxc-start ubuntu_landing
lxc-attach ubuntu_landing
```

![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/4.PNG?raw=true)

```
apt install nano net-tools curl
```

![4-1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/4-1.PNG?raw=true)

6. Atur IP, dengan perintah 

```
nano /etc/netplan/10-lxc.yaml
```

![5.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/5.PNG?raw=true)

7. Lalu mengganti IP, dengan perintah

```
netplan apply
```

```
ip r
```

![6.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/6.PNG?raw=true)

8. Keluar terlebih dahulu, dengan perintah 

   ```
   exit
   ```

   ![7.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/7.PNG?raw=true)

9. Install SSH pada Server

```
apt install openssh-server python -y
```

![8.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/8.PNG?raw=true)

10. Kemudian, masuk sshd_config untuk mengatur permit login, dengan perintah 

```
nano sshd_config
```

![9.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/9.PNG?raw=true)

11. Jika telah masuk pada sshd_config maka setting password ssh atau buat password baru

```
service sshd restart
```

```
passwd
```

![10.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/10.PNG?raw=true)

12. Cek ssh

    ```
    ssh root@10.0.3.103
    ```

    ![11.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1/11.PNG?raw=true)



<h2> 2. Rubah LXC php7 dengan ubuntu focal (destroy n create, same ip, same name)</h2>

1. Cek lxc yang ada, dengan perintah :

```
lxc-ls -f
```

![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/0.PNG?raw=true)

2. Menghapus container ubuntu php 7.4

```
lxc-stop ubuntu_php7.4
rm /var/lib/lxc/ubuntu_php7.4/lxc_snapshots
lxc-destroy ubuntu_php7.4 
lxc-ls -f
```

![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/1.PNG?raw=true)

3. membuat lxc ubuntu versi focal

```
sudo lxc-create -n ubuntu_php7.4 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
```

![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/2.PNG?raw=true)

4. Jalankan Ubuntu_php7.4

```
lxc-start ubuntu_php7.4
lxc-attach ubuntu_php7.4
apt install openssh-server -y
```

![3.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/3.PNG?raw=true)

5. Install nano net-tools curl 

```
apt install nano net-tools curl
```

![3-1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/3-1.PNG?raw=true)

6. Setting IP Static

```
nano /etc/netplan/10-lxc.yaml
```

![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/4.PNG?raw=true)

7. Untuk menampilkan IP Root nya 

```
netplan apply
ip r
```

![5.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/5.PNG?raw=true)

stop ubuntu_php7.4

```
lxc-stop ubuntu_php7.4
```

![6.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/6.PNG?raw=true)

8. Kemudian install open ssh server 

```
apt-get install openssh-server -y
```



9. Konfigurasi SSH 

```
nano /etc/ssh/sshd_config
```

![7.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/7.PNG?raw=true)

10. Restart ssh dan buat password baru

```
service sshd restart

passwd
```

![8.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/8.PNG?raw=true)

11. Cek ssh

```
ssh root@10.0.3.103
```

![9.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2/9.PNG?raw=true)



<h2> 3. vm.local/</h2>

1. Create directory laravel 8 pada lxc_landing   

```
mkdir laravel
```

```
cd laravel
```

![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/0.PNG?raw=true)

2. Menentukan identitas ssh keygen untuk remote instalasi

   ![00.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/00.PNG?raw=true)

3. Atur konfigurasi ansible pada nano host dan nano nginxphp.yml

```
nano hosts
```

```
[landing]
ubuntu_landing ansible_host=lxc_landing.dev ansible_ssh_user=root ansible_become_pass=1234
```

![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/1.PNG?raw=true)

```
nano nginxphp.yml
```

```
ap---
- hosts: all
  become : yes
  tasks:
    - name: install nginx nginx extras
      apt:
       pkg:
         - nginx
         - nginx-extras
       state: latest
    - name: start nginx
      service:
       name: nginx
       state: started
    - name: menginstall tools
      apt:
       pkg:
         - curl
         - software-properties-common
         - unzip
       state: latest
    - name: "Repo PHP 7.4"
      apt_repository:
        repo="ppa:ondrej/php"
    - name: "Updating the repo"
      apt: update_cache=yes
    - name: Installation PHP 7.4
      apt: name=php7.4 state=present
    - name: install php untuk laravel
      apt:
       pkg:
          - php7.4-fpm
          - php7.4-mysql
          - php7.4-mbstring
          - php7.4-xml
          - php7.4-bcmath
          - php7.4-json
          - php7.4-zip
          - php7.4-common
       state: present
```

![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/2.PNG?raw=true)

4. Jalankan ansible playbook nginxphp.yml

```
ansible-playbook -y hosts nginxphp.yml -k
```

![3.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/3.PNG?raw=true)

5. Buat file installcomposer.yml

```
nano installcomposer.yml
```

```
---
 -hosts: all
  become : yes
  tasks:
   - name: Download and install Composer
     shell: curl -sS https://getcomposer.org/installer | php
     args:
      chdir: /usr/src/
      creates: /usr/local/bin/composer
      warn: false
   - name: Add Composer to global path
     copy:
      dest: /usr/local/bin/composer
      group: root
      mode: '0755'
      owner: root
      src: /usr/src/composer.phar
      remote_src: yes
   - name: Composer create project
     become_user: root
     composer:
      command: create-project
      arguments: laravel/laravel landing 
      working_dir: /var/www/html
      prefer_dist: yes
     environment:
        COMPOSER_NO_INTERACTION: "1"
   - name: mengkopi file .env.example jadi .env
     copy:
      dest: /var/www/html/landing/.env.example
      src: /var/www/html/landing/.env
      remote_src: yes
   - name: mengganti konfigurasi .env
     lineinfile:
      path: /var/www/html/landing/.env
      regexp: "{{ item.regexp }}"
      line: "{{ item.line }}"
      backrefs: yes
     loop:
      - { regexp: '^(.)DB_HOST(.)$', line: 'DB_HOST=10.0.3.200' }
      - { regexp: '^(.)DB_DATABASE(.)$', line: 'DB_DATABASE=landing' }
      - { regexp: '^(.)DB_USERNAME(.)$', line: 'DB_USERNAME=admin' }
      - { regexp: '^(.)DB_PASSWORD(.)$', line: 'DB_PASSWORD= ' }
      - { regexp: '^(.)APP_URL(.)$', line: 'APP_URL=http://vm.local' }
      - { regexp: '^(.)APP_NAME=(.)$', line: 'APP_NAME=landing' }
   - name: Composer install ke landing
     composer:
       command: install
       working_dir: /var/www/html/landing
     environment:
       COMPOSER_NO_INTERACTION: "1"
   - name: generate php artisan
     args:
      chdir: /var/www/html/landing
     shell: php artisan key:generate
   - name: mengganti permission storage
     file:
      path: /var/www/html/landing/storage
      mode: 0777
      recurse: yes

```

![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/4.PNG?raw=true)

6. Jalankan ansible playbook installcomposer.yml

   ```
   ansible-playbook -i hosts installcomposer.yml -k
   ```

   ![5.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/5.PNG?raw=true)

7. Setting lxc_landing.dev

   ```
   nano lxc_landing.dev
   ```

   ```
   server {
           listen 80;
   
           root /var/www/html/landing/public;
           index index.php index.html index.htm;
           server_name lxc_landing.dev;
   
           error_log /var/log/nginx/landing_error.log;
           access_log /var/log/nginx/landing_access.log;
   
           client_max_body_size 100M;
           location / {
                   try_files $uri $uri/ /index.php$args;
           }
           location ~\.php$ {
                   include snippets/fastcgi-php.conf;
                   fastcgi_pass unix:run/php/php7.4-fpm.sock;
                   fastcgi_param SCRIPTFILENAME $document_root$fastcgi_script_name;
           }
   }
   
   ```

   ![6.0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/6.0.PNG?raw=true)

   

   8. Setting config.yml

      ```
      nano config.yml
      ```

      ```
      ---
      - hosts: all
        become : yes
        vars:
          domain: 'lxc_landing.dev'
        tasks:
         - name: stop apache2
           service:
            name: apache2
            state: stopped
            enabled: no
         - name: Write {{ domain }} to /etc/hosts
           lineinfile:
            dest: /etc/hosts
            regexp: '.*{{ domain }}$'
            line: "127.0.0.1 {{ domain }}"
            state: present
         - name: ensure nginx is at the latest version
           apt: name=nginx state=latest
         - name: start nginx
           service:
            name: nginx
            state: started
         - name: copy the nginx config file 
           copy:
            src: ~/ansible/laravel/lxc_landing.dev
            dest: /etc/nginx/sites-available/lxc_landing.dev
         - name: Symlink lxc_landing.dev
           command: ln -sfn /etc/nginx/sites-available/lxc_landing.dev /etc/nginx/sites-enabled/lxc_landing.dev
           args:
            warn: false
         - name: restart nginx
           service:
            name: nginx
            state: restarted
         - name: restart php7
           service:
            name: php7.4-fpm
            state: restarted
         - name: curl web
           command: curl -i http://lxc_landing.dev
           args:
            warn: false
      
      ```

      

   ![6.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/6.PNG?raw=true)



9. Coba lakukan Instalasi lagi

   ```
    ansible-playbook -i hosts config.yml -k
   ```

   ![7.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/7.PNG?raw=true)



10. Coba Akses url vm.local

    ![8.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3/8.PNG?raw=true)

    

<h2> 4.  vm.local/blog</h2>

1. Masuk ke ansible dan buat Install laravel
    
    ```
    cd ~/ansible/
    mkdir wordoress/
    cd wordpress/
    ```
    
    ![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/0.PNG?raw=true)
    
2. Menentukan identitas ssh keygen untuk remote instalasi
    
    ![00.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/00.PNG?raw=true)
    
2. Cek ssh
    
    ```
    ssh root@10.0.3.103
    ```
    
    ![000.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/000.PNG?raw=true)
    
2. Cek ssh root@lxc_php7.4.dev
    
    ```
    ssh root@lxc_php7.dev
    ```
    
    ![0000.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/0000.PNG?raw=true)
    
    
    
2. Membuat hosts untuk lxc
    
    ```
    nano host
    ```
    
    ![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/1.PNG?raw=true)
    
    
    
6. Setting nano installwordpress.ym

```
nano installwordpress.yml
```

```
---
- hosts: all
  vars:
    domain: 'lxc_php7.dev'
  tasks:
   - name: delete apt chache
     become: yes
     become_user: root
     become_method: su
     command: rm -vf /var/lib/apt/lists/*

   - name: install requirement
     become: yes
     become_user: root
     become_method: su
     apt: name={{ item }} state=latest update_cache=true
     with_items:
      - nginx
      - nginx-extras
      - curl
      - wget
      - php7.4
      - php7.4-fpm
      - php7.4-curl
      - php7.4-xml
      - php7.4-gd
      - php7.4-opcache
      - php7.4-mbstring
      - php7.4-zip
      - php7.4-json
      - php7.4-cli
      - php7.4-mysqlnd
      - php7.4-xmlrpc
      - php7.4-curl

   - name: wget wordpress
     shell: wget -c http://wordpress.org/latest.tar.gz

   - name: tar latest.tar.gz
     shell: tar -xvzf latest.tar.gz

   - name: copy folder wordpress
     shell: cp -R wordpress /var/www/html/blog

   - name: chmod
     become: yes
     become_user: root
     become_method: su
     command: chmod 775 -R /var/www/html/blog/

   - name: copy .wp-config.conf
     copy:
      src=~/ansible/wordpress/wp.conf
      dest=/var/www/html/blog/wp-config.php

   - name: copy wordpress.conf
     copy:
      src=~/ansible/wordpress/wordpress.conf
      dest=/etc/nginx/sites-available/{{ domain }}
     vars:
      servername: '{{ domain }}'

   - name: Symlink wordpress.conf
     command: ln -sfn /etc/nginx/sites-available/{{ domain }} /etc/nginx/sites-enabled/{{ domain }}
   
   - name: restart nginx
     become: yes
     become_user: root
     become_method: su
     action: service name=nginx state=restarted

   - name: Write {{ domain }} to /etc/hosts
     lineinfile:
      dest: /etc/hosts
      regexp: '.*{{ domain }}$'
      line: "127.0.0.1 {{ domain }}"
      state: present

   - name: enable module php mbstring
     command: phpenmod mbstring

   - name: restart php
     become: yes
     become_user: root
     become_method: su
     action: service name=php7.4-fpm state=restarted

   - name: restart nginx
     become: yes
     become_user: root
     become_method: su
     action: service name=nginx state=restarted

```

![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/2.PNG?raw=true)



7. Kemudian setting nano wp.conf 

   ```
   nano wp.conf
   ```

   ```
   <?php
   /**
    * The base configuration for WordPress
    *
    * The wp-config.php creation script uses this file during the installation.
    * You don't have to use the web site, you can copy this file to "wp-config.php"
    * and fill in the values.
    *
    * This file contains the following configurations:
    *
    * * MySQL settings
    * * Secret keys
    * * Database table prefix
    * * ABSPATH
    *
    * @link https://wordpress.org/support/article/editing-wp-config-php/
    *
    * @package WordPress
    */
   
   define( 'WP_HOME', 'http://vm.local/blog' );
   define( 'WP_SITEURL', 'http://vm.local/blog' );
   
   // * MySQL settings - You can get this info from your web host * //
   /** The name of the database for WordPress */
   define( 'DB_NAME', 'blog' );
   
   /** MySQL database username */
   define( 'DB_USER', 'admin' );
   
   /** MySQL database password */
   define( 'DB_PASSWORD', 'SysAdminSas0102' );
   
   /** MySQL hostname */
   define( 'DB_HOST', '10.0.3.200:3306' );
   
   /** Database charset to use in creating database tables. */
   define( 'DB_CHARSET', 'utf8' );
   
   /** The database collate type. Don't change this if in doubt. */
   define( 'DB_COLLATE', '' );
   
   /**#@+
    * Authentication unique keys and salts.
    *
    * Change these to different unique phrases! You can generate these using
    * the {@link https://api.wordpress.org/secret-key/1.1/salt/ WordPress.org secret-key service}.
    *
    * You can change these at any point in time to invalidate all existing cookies.
    * This will force all users to have to log in again.
    *
    * @since 2.6.0
    */
   define( 'AUTH_KEY',         'put your unique phrase here' );
   define( 'SECURE_AUTH_KEY',  'put your unique phrase here' );
   define( 'LOGGED_IN_KEY',    'put your unique phrase here' );
   define( 'NONCE_KEY',        'put your unique phrase here' );
   define( 'AUTH_SALT',        'put your unique phrase here' );
   define( 'SECURE_AUTH_SALT', 'put your unique phrase here' );
   define( 'LOGGED_IN_SALT',   'put your unique phrase here' );
   define( 'NONCE_SALT',       'put your unique phrase here' );
   
   /*#@-/
   
   /**
    * WordPress database table prefix.
    *
    * You can have multiple installations in one database if you give each
    * a unique prefix. Only numbers, letters, and underscores please!
    */
   $table_prefix = 'wp_';
   
   /**
    * For developers: WordPress debugging mode.
    *
    * Change this to true to enable the display of notices during development.
    * It is strongly recommended that plugin and theme developers use WP_DEBUG
    * in their development environments.
    *
    * For information on other constants that can be used for debugging,
    * visit the documentation.
    *
    * @link https://wordpress.org/support/article/debugging-in-wordpress/
    */
   define( 'WP_DEBUG', false );
   
   /* Add any custom values between this line and the "stop editing" line. */
   
   
   
   /* That's all, stop editing! Happy publishing. */
   
   /** Absolute path to the WordPress directory. */
   if ( ! defined( 'ABSPATH' ) ) {
           define( 'ABSPATH', _DIR_ . '/' );
   }
   
   /** Sets up WordPress vars and included files. */
   require_once ABSPATH . 'wp-settings.php';
   
   ```

   ![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/4.PNG?raw=true)



8. Kemudian setting pada nano wordpress.conf

   ```
   nano wordpress.conf
   ```

   ```
   server {
        listen 80;
        listen [::]:80;
   
        # Log files for Debugging
        access_log /var/log/nginx/wordpress-access.log;
        error_log /var/log/nginx/wordpress-error.log;
   
        # Webroot Directory for Laravel project
        root /var/www/html/blog;
        index index.php index.html index.htm;
   
        # Your  Name
        server_name lxc_php7.dev;
   
        location / {
                try_files $uri $uri/ /index.php?$query_string;
        }
   
        # PHP-FPM Configuration Nginx
        location ~ \.php$ {
                try_files $uri =404;
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                fastcgi_pass unix:/run/php/php7.4-fpm.sock;
                fastcgi_index index.php;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                include fastcgi_params;
        }
   }
   
   ```

   ![5.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/5.PNG?raw=true)



9. Lalu coba memanggil hosts installwordpress.yml

```
sudo ansible-playbook -i hosts installwordpress.yml -k
```

![6.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/6.PNG?raw=true)



10. Mencoba Akses Url vm.local/blog

    walah, hasilnya sebagai berikut

![7.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/7.PNG?raw=true)



11. Coba Create akun wordpress atau sign in  yang berisi title (judul), username dan juga password

    ![8.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/8.PNG?raw=true)



12. Jika sudah Create Account atau sign in, maka akan muncul tampilin seperti gambar di bawah ini, dimana mengartikan sukses Create Account atau sign in, dan telah berada pada dashboard 

    

![9.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/9.PNG?raw=true)



13. Lalu coba refresh pada vm.local/blog, Maka akan muncul tampilan seperti berikut :

![10.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4/10.PNG?raw=true)





<h2> Soal Tambahan</h2>

<h2> 5. Rubah konfigurasi php7.4 yang semula menggunakan socket menjadi menggunakan port (127.0.0.1:9001)</h2>



#### ***Untuk vm.local (laravel)***

1. Masuk pada nano lxc_landing.dev -> mengubah konfigurasi pada nano lxc_landing.dev dengan port 127.0.0.1:9001

```
nano lxc_landing.dev
```

![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/0.PNG?raw=true)

2. Cek lxc_landing.dev

![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/1.PNG?raw=true)



3. Membuat file dengan memberikan nama soal2.yml. 

   Setelah itu masuk ke file soal2.yml yang sudah dibuat tadi untuk mengganti `listen nya menjadi 127.0.0.1:9001

   ```
   ---
   - hosts: all
     become : yes
     tasks:
      - name: mengganti php sock
        lineinfile:
         path: /etc/php/7.4/fpm/pool.d/www.conf
         regexp: '^(.*)listen =(.*)$'
         line: 'listen = 127.0.0.1:9001'
         backrefs: yes
      - name: copy the nginx config file 
        copy:
         src: ~/ansible/laravel/lxc_landing.dev
         dest: /etc/nginx/sites-available/lxc_landing.dev
      - name: Symlink lxc_landing.dev
        command: ln -sfn /etc/nginx/sites-available/lxc_landing.dev /etc/nginx/sites-enabled/lxc_landing.dev
        args:
         warn: false
      - name: restart nginx
        service:
         name: nginx
         state: restarted
      - name: restart php7
        service:
         name: php7.4-fpm
         state: restarted
      - name: curl web
        command: curl -i http://lxc_landing.dev
        args:
         warn: false
   
   ```

   ![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/2.PNG?raw=true)



4. Lalu coba menjalankan ansible playbook hosts soal2.yml

```
ansible-playbook -i hosts soal2.yml -k
```

![3.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/3.PNG?raw=true)



5. Jika telah berhasil menjalankan ansible playbook hosts soal2.yml, maka coba untuk mengakses url vm.local

   ![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/4.PNG?raw=true)





***Untuk vm.local/blog (wordpress)***



1. Masuk pada nano wordpress.conf -> mengubah konfigurasi pada nano wordpress.confdengan port 127.0.0.1:9001

   ```
   nano wordpress.conf
   ```

   ![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/soal%20tambah%202/0.PNG?raw=true)



2. Cek wordpress.conf

   ![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/soal%20tambah%202/1.PNG?raw=true)



3. Membuat file dengan memberikan nama soal2.yml. 

   Setelah itu masuk ke file soal2.yml yang sudah dibuat tadi untuk mengganti `listen nya menjadi 127.0.0.1:9001

```
nano soal2.yml
```

```
---
- hosts: all
  become : yes
  tasks:
   - name: mengganti php sock
     lineinfile:
      path: /etc/php/7.4/fpm/pool.d/www.conf
      regexp: '^(.*)listen =(.*)$'
      line: 'listen = 127.0.0.1:9001'
      backrefs: yes
   - name: copy the nginx config file 
     copy:
      src: ~/ansible/wordpress/wordpress.conf
      dest: /etc/nginx/sites-available/lxc_php7.dev
   - name: Symlink lxc_php7.dev
     command: ln -sfn /etc/nginx/sites-available/lxc_php7.dev /etc/nginx/sites-enabled/lxc_php7.dev
     args:
      warn: false
   - name: restart nginx
     service:
      name: nginx
      state: restarted
   - name: restart php7
     service:
      name: php7.4-fpm
      state: restarted
   - name: curl web
     command: curl -i http://lxc_php7.dev
     args:
      warn: false

```

![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/soal%20tambah%202/2.PNG?raw=true)



4. Lalu coba menjalankan ansible playbook hosts soal2.yml

```
sudo ansible-playbook -i hosts soal2.yml -k
```

![3.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/soal%20tambah%202/3.PNG?raw=true)



5. Jika telah berhasil menjalankan ansible playbook hosts soal2.yml, maka coba untuk mengakses url vm.local/blog

   ![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/soal%20tambahan/soal%20tambah%202/4.PNG?raw=true)