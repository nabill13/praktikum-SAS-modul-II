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

26. 
