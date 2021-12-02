# **# PRAKTIKUM MODUL II **

# **SISTEM ADMINISTRASI SERVER**

#### KELOMPOK II

#### -> Evyra Rizki Safitri   

#### -> Nabila Nur Amalia

#### -> M. Pradata Yuda P



**1. Rubah LXC landing dengan ubuntu focal (destroy n create, same ip, same name)**

1. Setting network machine ke bridge adapter
2. Cek lxc yang ada, dengan perintah : 

```
sudo lxc-ls -f
```

 ![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/1.PNG?raw=true)

3.  Harap menghentikan lxc yang akan di hapus terlebih dahulu lalu destroy lxc ubuntu landing dan ubuntu php 7.4, dengan perintah  

```
sudo lxc-destroy (nama lxc yg akan di hapus)
```

![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/2.PNG?raw=true)

4.  Cek apakah lxc yang sudah di hapus masih ada atau tidak dengan perintah

```
 sudo lxc-ls -f
```

![3.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/3.PNG?raw=true)

5. Membuat lxc focal_sas02

   ```
   sudo lxc-create -n focal_sas02 -t download --dist ubuntu --release xenial --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
   ```

   ![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/4.PNG?raw=true)

6. Membuat lxc focal_sas02-2

   ```
   sudo lxc-create -n focal_sas02 -t download --dist ubuntu --release bionic --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
   ```

    ![5.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/5.PNG?raw=true)

7. Cek apakah lxc sudah terinstall atau belum

   ```
   sudo lxc-ls -f
   ```

   ![6.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/6.PNG?raw=true)

8.  Jalankan lxc focal_sas02 dan focal_sa

   ```
   sudo lxc-start -n focal_sas02
   sudo lxc-start -n focal_sas02-2
   sudo lxc-ls-f
   ```

   

   ![7.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/7.PNG?raw=true)

9. Masuk ke focal_sas02

   ```
   sudo lxc-attach -n focal_sas02
   ```

   ![8.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8.PNG?raw=true)

10. Install nginx dengan perintah

```
apt install nginx nginx-extras
```

![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/0.PNG?raw=true)

11. Install netplan

```
apt install nano net-tools curl
```

![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/1.PNG?raw=true)

12. Cek ip

    ```
    ifconfig
    ```

    ![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/2.PNG?raw=true)

13. Setting ip ke static pada focal_sas02

    ![3.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/3.PNG?raw=true)

14. Jalankan perintah tersebut lalu start dan masuk kembali ke focal_sas02 dan cek ip apakah sudah berganti atau belum

    ```
    sudo lxc-start -n focal_sas02
    
    sudo lxc-attach -n focal_sas02
    ```

    ![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/4.PNG?raw=true)

15.  Lalu ketikkan perintah

    ```
    apt install software-properties
    ```

    ![5.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/5.PNG?raw=true)

16. Lalu install curl unzip

    ```
    apt install curl unzip -y
    ```

    ![6.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/6.PNG?raw=true)

17. Setting konfigurasi dengan perintah 

    ```
    nginx -t
    ```

    ![7.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/7.PNG?raw=true)

18. add apt repository dengan perintah

    ```
    add-apt-repository ppa:ondrej/php
    ```

    ![8.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/8.PNG?raw=true)

19.  kemudian muncul seperti ini

    ![8-1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/8-1.PNG?raw=true)

20. Lalu update dengan perintah 

    ```
    apt update
    ```

    ![9.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8/9.PNG?raw=true)

21. Install nginx  dengan perintah 

    ```
    apt install nginx nginx-extras
    ```

    ![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/9/0.PNG?raw=true)

22. Install nano net-tools curl

    ```
    apt install nano net-tools curl
    ```

    ![1.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/9/1.PNG?raw=true)

23. cek ifconfig

    ```
    ifconfig
    ```

![2.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/9/2.PNG?raw=true)

24. cek netplan pada perintah 

    ```
    etc/netplan/10.lxc.yaml
    ```

    ![3.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/9/3.PNG?raw=true)



25. masuk pada netplan dengan perintah

    ```
    sudo netplan apply
    ifconfig
    ```

    ![4.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/9/4.PNG?raw=true)

26. apt install software-properties-common

    ```
    apt install software-properties-common
    ```

    ![5.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/9/5.PNG?raw=true)

<h2> NO 1</h2>

![0.PNG](https://github.com/nabill13/praktikum-SAS-modul-II/blob/main/8.1/0.PNG?raw=true)
<img width="242" alt="0" src="https://user-images.githubusercontent.com/92932656/144352518-d1a50c0c-eece-4921-8069-2a7294e2c064.PNG">
<img width="242" alt="1" src="https://user-images.githubusercontent.com/92932656/144352518-d1a50c0c-eece-4921-8069-2a7294e2c064.PNG">
<img width="366" alt="4" src="https://user-images.githubusercontent.com/92932656/144352584-38ca7eca-7bc4-4f29-a7b5-275d89f26a15.PNG">
<img width="212" alt="5" src="https://user-images.githubusercontent.com/92932656/144352593-824713d7-1449-4605-a566-b632fd49940c.PNG">
<img width="373" alt="6" src="https://user-images.githubusercontent.com/92932656/144352594-258364ba-189a-4c04-9d24-0893ef8e3a51.PNG">
<img width="203" alt="7" src="https://user-images.githubusercontent.com/92932656/144352596-791f4a81-ad80-4603-ae55-b5b8d1607f17.PNG">
<img width="324" alt="8" src="https://user-images.githubusercontent.com/92932656/144352598-744097a3-95a7-4d2c-9c36-b7c43346f95f.PNG">
<img width="326" alt="2" src="https://user-images.githubusercontent.com/92932656/144352601-cef51507-1749-452e-be86-3425066ab8c3.PNG">
<img width="267" alt="3" src="https://user-images.githubusercontent.com/92932656/144352605-323d764f-e95e-47c6-9e16-94de0d6da847.PNG">

<h2> NO 2</h2>
<img width="319" alt="0" src="https://user-images.githubusercontent.com/92932656/144352655-ec3d125d-9798-4919-bc9b-e04662f8212e.PNG">
<img width="401" alt="1" src="https://user-images.githubusercontent.com/92932656/144352657-35bd0bc1-0257-4a75-b7e5-f78ff94d3c04.PNG">
<img width="232" alt="2" src="https://user-images.githubusercontent.com/92932656/144352659-e00c67f5-3ec8-45f2-be50-c24afad5b120.PNG">
<img width="360" alt="3" src="https://user-images.githubusercontent.com/92932656/144352662-70be253c-da96-4ea4-9cd8-8d7406c8185b.PNG">
<img width="258" alt="4" src="https://user-images.githubusercontent.com/92932656/144352665-b2f912af-e5e9-4fc7-b7f0-6bdc54ea5123.PNG">
<img width="385" alt="5" src="https://user-images.githubusercontent.com/92932656/144352666-3a50749f-d237-4ee1-ab1c-ba88e1c8f9a3.PNG">
<img width="240" alt="6" src="https://user-images.githubusercontent.com/92932656/144352668-1b563390-06d6-4e6f-a1c9-7b4b820da15d.PNG">
<img width="336" alt="7" src="https://user-images.githubusercontent.com/92932656/144352669-15f01c2f-2566-4107-a4be-b2563d44306f.PNG">
<img width="185" alt="8" src="https://user-images.githubusercontent.com/92932656/144352671-4b869694-25cd-402a-ab31-88f436c7a49a.PNG">
<img width="331" alt="9" src="https://user-images.githubusercontent.com/92932656/144352673-6baab403-b9d9-460d-b104-aac5624fcc81.PNG">

<h2> NO 3</h2>
1. Masuk ke ansible dan buat folder laravel
  <img width="159" alt="0" src="https://user-images.githubusercontent.com/93085602/144352881-fd49b1b4-1907-42e8-8287-6d38678c25bb.PNG">

2. membuat file hosts
  <img width="400" alt="1" src="https://user-images.githubusercontent.com/93085602/144352908-d29022c2-08c7-4351-ba75-89f9ec8662a2.PNG">

3. membuat file nginxiphp 
  <img width="390" alt="2" src="https://user-images.githubusercontent.com/93085602/144352916-8f412fd5-7278-4a58-bf0a-bec88957c05e.PNG">

  ```
  ---
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

  

4. install nginx php
  <img width="303" alt="3" src="https://user-images.githubusercontent.com/93085602/144352922-29ecc499-79fd-456a-83d7-7f7e90409950.PNG">

5. error yang didapatkan
  <img width="403" alt="err" src="https://user-images.githubusercontent.com/93085602/144352926-6444a6c0-e6f7-4157-854c-02983f32e9fd.PNG">

6. membuat file composer

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

   
