# PRAKTIKUM MODUL 4

#### SISTEM ADMINISTRASI SERVER 

KELOMPOK 2

- NABILA NUR AMALIA_1202190013
- EVYRA RIZKI SAFITRI_1202190015
- M. PRADATA YUDA P_1202190061

##### Soal Praktikum

1. Terapkan loadbalancer untuk /blog dan /app dengan ketentuan

   I. /blog menggunakan least_conn

   II. /app menggunakan ip hash

   III. disarakan menggunakan ansible untuk instalasi

2. Gunakan apache Jmeter untuk menganalisa perbedaan antara /, /app, /blog dengan loadbalancer dan tanpa loadbalancer pada traffic 50, 100 dan 150 users. Analisa dari segi waktu saja. Tulis langkah testing dan analisa dengan bahasa sendiri.

##### PRAKTIKUM

##### Container APP (PHP5)

- Cek konfigurasi 

  dengan perintah 

  ```
  sudo lxc-ls -f
  ```

![0.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/0.PNG?raw=true)

- Langkah kedua, Salin/copy container debian_php5.6 untuk menjaga backup container. kemudian jalankan container salinan tersebut.

  ```
  sudo lxc-copy -n debian_php5.6 -N debian_php5.6_2 -sKD		 // untuk mengclone container
  sudo lxc-copy -n debian_php5.6 -N debian_php5.6_3 -sKD
  sudo lxc-start -n debian_php5.6_2	          // untuk menjalankan Container
  sudo lxc-start -n debian_php5.6_3
  sudo lxc-ls -f						
  ```

![1.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/1.PNG?raw=true)

- #### Masuk pada Container debian_php5.6_2 lakukan configurasi IP 

```
sudo lxc-attach debian_php5.6 6_2
```

![2.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/2%20(setelah%20pic%20no%201)/2%20(setelah%20pic%20no%201)/2.PNG?raw=true)

- Kemudian lakukan konfigurasi pada hosts,tambahkan domain serta nama domain container kita.

  Masuk ke 'ubuntu_php5.6_2', lalu ubah IP address menjadi '10.0.3.122' agar berbeda dengan 'ubuntu_php5.6'. 

![3.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/2%20(setelah%20pic%20no%201)/2%20(setelah%20pic%20no%201)/3.PNG?raw=true)

- Kemudian lakukan konfigurasi pada hosts,tambahkan domain serta nama domain container kita.

  ```
  nano /etc/host
  ```

![4.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/2%20(setelah%20pic%20no%201)/2%20(setelah%20pic%20no%201)/4.PNG?raw=true)

- Lalu masuk directory sites-avalaible, di folder tersebut kita lakukan edit domain file tersebut dengan mengganti name servernya. jangan lupa restart containernya

  ```
   nano /etc/nginx/sites-available/lxc_php5.dev
  ```

![5.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/2%20(setelah%20pic%20no%201)/2%20(setelah%20pic%20no%201)/5.PNG?raw=true)

#### Masuk pada Container debian_php5.6_3 lakukan configurasi IP 

```
sudo lxc-attach debian_php5.6_3
```

![4.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/3%20(setelah%20folder%202)/3%20(setelah%20folder%202)/4.PNG?raw=true)

- Kemudian lakukan konfigurasi pada hosts,tambahkan domain serta nama domain container kita.

  Masuk ke 'ubuntu_php5.6_3', lalu ubah IP address menjadi '10.0.3.112' agar berbeda dengan 'ubuntu_php5.6'. 

  ![5.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/3%20(setelah%20folder%202)/3%20(setelah%20folder%202)/5.PNG?raw=true)

- Kemudian lakukan konfigurasi pada hosts,tambahkan domain serta nama domain container kita.

  ```
  nano /etc/host
  ```

![6.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/3%20(setelah%20folder%202)/3%20(setelah%20folder%202)/6.PNG?raw=true)

- Lalu masuk directory sites-avalaible, di folder tersebut kita lakukan edit domain file tersebut dengan mengganti name servernya. jangan lupa restart containernya

  ```
   nano /etc/nginx/sites-available/lxc_php5.dev
  ```

![7.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/3%20(setelah%20folder%202)/3%20(setelah%20folder%202)/7.PNG?raw=true)

#### Container BLOG (PHP7)

#### Masuk pada Container ubuntu_php7.4_2 lakukan configurasi IP 

- Salin/copy container ubuntu_php7.4. kemudian jalankan container salinan tersebut.

  ```
  lxc-copy -n ubuntu_php7.4 -N ubuntu_php7.4_2 -sKD		 
  lxc-copy -n ubuntu_php7.4 -N ubuntu_php7.4_3 -sKD
  sudo lxc-start -n ubuntu_php7.4_2						
  sudo lxc-start -n ubuntu_php7.4_3
  Sudo lxc-ls -f										   
  ```

  ![11.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/11.PNG?raw=true)

  ![12.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/12.PNG?raw=true)

  

- Pada Container debian_php7.4_2 lakukan configurasi IP

```
sudo lxc-attach debian_php7.4_2
```

![0.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/4%20(setelah%20pic%20no%2012)/4%20(setelah%20pic%20no%2012)/0.PNG?raw=true)

- Lakukan Konfigurasi IP 

  ![1.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/4%20(setelah%20pic%20no%2012)/4%20(setelah%20pic%20no%2012)/1.PNG?raw=true)

- kemudian lakukan konfigurasi pada hosts. tambahkan domain serta nama domain container kita.

  ```
  nano /etc/hosts
  ```

  ![2.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/4%20(setelah%20pic%20no%2012)/4%20(setelah%20pic%20no%2012)/2.PNG?raw=true)

- Lalu masuk directory sites-avalaible, di folder tersebut kita lakukan edit domain file tersebut dengan mengganti name servernya. jangan lupa restart containernya

  ```
   nano /etc/nginx/sites-available/lxc_php7.dev
   exit											
  ```

  ![3.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/4%20(setelah%20pic%20no%2012)/4%20(setelah%20pic%20no%2012)/3.PNG?raw=true)



#### Masuk pada Container ubuntu_php7.4_3 lakukan configurasi IP 

- masuk 'ubuntu_php7.4_3' and ubah IP address to '10.0.3.111'. 

![0.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/5%20(setelah%20folder%204)/5%20(setelah%20folder%204)/0.PNG?raw=true)

- daftarkan Register 'lxc_php7_3.dev' at /etc/hosts

  ![1.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/5%20(setelah%20folder%204)/5%20(setelah%20folder%204)/1.PNG?raw=true)

- ubah nama server,kemudian ulangi langkah yang sama untuk 'ubuntu_php7.4_3'. jangan lupa restart containernya

![2.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/5%20(setelah%20folder%204)/5%20(setelah%20folder%204)/2.PNG?raw=true)



#### VM UTAMA

- Masuk pada host 

  ```
  sudo nano /etc/hosts
  ```

  ![13.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/13.PNG?raw=true)



- Masuk pada /etc/hosts kemudian Masukkan semua Kontainer pada php5 dan php7

![14.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/14.PNG?raw=true)



- Jalankan Jmeter. Ubah nomer dari threads user akses dari from 50, 100, 150

  *user 50*

![15.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/15.PNG?raw=true)

![16.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/16.PNG?raw=true)

![17.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/17.PNG?raw=true)

![18.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/18.PNG?raw=true)

*user 100*

![19.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/19.PNG?raw=true)

![20.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/20.PNG?raw=true)

![21.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/21.PNG?raw=true)

![22.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/22.PNG?raw=true)



*user 150*

![23.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/23.PNG?raw=true)

![24.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/24.PNG?raw=true)

![25.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/25.PNG?raw=true)

![26.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/26.PNG?raw=true)



- Kemudian kembali ke VM 

```
/etc/nginx/sites-available/vm.local
```

- tambah upstream landing, php5 dan php7

  ![27.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/27.PNG?raw=true)

- ubah proxy_pass

  ![28.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/28.PNG?raw=true)

- lalu kembali pada Jmeter dan ulangi lagi

  *user 50*

  ![29.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/29.PNG?raw=true)

  ![30.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/30.PNG?raw=true)

​		![31.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/31.PNG?raw=true)

![32.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/32.PNG?raw=true)



*User 100*

![33.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/33.PNG?raw=true)

![34.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/34.PNG?raw=true)

![35.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/35.PNG?raw=true)

![36.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/36.PNG?raw=true)



*user 150*

![37.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/37.PNG?raw=true)

![38.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/38.PNG?raw=true)

![39.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/39.PNG?raw=true)

![40.PNG](https://github.com/nabill13/Praktikum-modul-4-SAS/blob/main/40.PNG?raw=true)

<h3> Analisa Software Jmeter </h3>

**50 Pengguna**

Ketika terdapat 50 Pengguna, Rata-Rata Waktu yang dibutuhkan pengguna dalam mengakses masing-masing halaman.

Tidak Menggunakan Load Balancer

- Landing (50 Pengguna) : 275 mdtk / 0,275 detik

- Blog (50 Pengguna) : 404 mdtk / 0,404 detik

- App (50 Pengguna) : 415 mdtk / 0,415 detik 

- Rata-Rata Keseluruhan Halaman(150 Pengguna) : 365 mdtk / 0,365 detik

  Menggunakan Load Balancer

- Landing (50 Pengguna) : 232 mdtk / 0,232 detik

- Blog (50 Pengguna) : 446 mdtk / 0,446 detik

- App (50 Pengguna) : 394 mdtk / 0,394 detik 

- Rata-Rata Keseluruhan Halaman(150 Pengguna) : 357 mdtk / 0,357 detik

**100 Pengguna**

- Ketika terdapat 100 Pengguna, Rata-Rata Waktu yang dibutuhkan pengguna dalam mengakses masing-masing halaman.

Tidak Menggunakan Load Balancer

- Landing (100 Pengguna): 507 mdtk / 0,507 detik

- Blog (100 Pengguna) : 827 mdtk / 0,827 detik

- App (100 Pengguna) : 778 mdtk / 0,778 detik 

- Rata-Rata Keseluruhan Halaman(300 Pengguna) : 704 mdtk / 0,704 detik

Menggunakan Load Balancer
- Landing (100 Pengguna) : 479 mdtk / 0,479 detik
- Blog (100 Pengguna) : 800 mdtk / 0,8 detik
- App (100 Pengguna) : 867 mdtk / 0,867 detik 
- Rata-Rata Keseluruhan Halaman(150 Pengguna) : 714 mdtk / 0,714 detik

**150 Pengguna**

Ketika terdapat 150 Pengguna, Rata-Rata Waktu yang dibutuhkan pengguna dalam mengakses masing-masing halaman.

Tidak Menggunakan Load Balancer

- Landing (150 Pengguna): 709 mdtk / 0,709 detik

- Blog (150 Pengguna) : 1383 mdtk / 1,383 detik

- App (150 Pengguna) : 1271 mdtk / 1,271 detik 

- Rata-Rata Keseluruhan Halaman(450 Pengguna) : 1121 mdtk / 0,078 detik

  Menggunakan Load Balancer

- Landing (150 Pengguna): 688 mdtk / 0,688 detik

- Blog (150 Pengguna) : 1245 mdtk / 1,245 detik

- App (150 Pengguna) : 1235 mdtk / 1,235 detik 

- Rata-Rata Keseluruhan Halaman(450 Pengguna) : 1056 mdtk / 1,056 detik

 Dari Jumlah Pengguna(50,100,150), Disini kita dapat mengetahui bahwa rata-rata waktu pengguna mengakses web kita lebih cepat (Tidak Menggunakan Load balancer) dibandingkan jika kita menggunakan load balancer.



**Throughput (kecepatan/rate transfer data efektif, yang diukur dalam bps).***

**50 Pengguna**

Ketika terdapat 50 Pengguna, melakukan transfer data dalam masing-masing halaman.

Tanpa Menggunakan Load Balancer

- Landing (50 Pengguna) : 101,2/detik

- Blog (50 Pengguna) : 58,8/detik

- App (50 Pengguna) : 61,6/detik 

- Total Throughput Keseluruhan Halaman(150 Pengguna) : 114,2/detik

Menggunakan Load Balancer

- Landing (50 Pengguna) : 87,4/detik

- Blog (50 Pengguna) : 53,1/detik

- App (50 Pengguna) : 61,2/detik 

- Total Throughput Keseluruhan Halaman(150 Pengguna) : 117/detik

**100 Pengguna**

- Ketika terdapat 100 Pengguna, melakukan transfer data dalam masing-masing halaman.

Tidak Menggunakan Load Balancer

- Landing (100 Pengguna) : 102,6/detik

- Blog (100 Pengguna) : 60,8/detik

- App (100 Pengguna) : 60,9/detik 

- Total Throughput Keseluruhan Halaman(300 Pengguna) : 199,7/detik

Menggunakan Load Balancer

- Landing (100 Pengguna) : 112,7/menit

- Blog (100 Pengguna) : 57,7/menit

- App (100 Pengguna) : 59,6/menit 

- Total Throughput Keseluruhan Halaman(300 Pengguna) : 117/detik

**150 Pengguna**

 Ketika terdapat 150 Pengguna, melakukan transfer data dalam masing-masing halaman.

 Tidak Menggunakan Load Balancer

 - Landing (150 Pengguna) : 101,4/detik

 - Blog (150 Pengguna) : 57,3/detik

 - App (150 Pengguna) : 56,9/detik 

 - Total Throughput Keseluruhan Halaman(450 Pengguna) : 109,4/detik

 Menggunakan Load Balancer

 - Landing (150 Pengguna) : 101,7/detik

 - Blog (150 Pengguna) : 61,1/detik

 - App (150 Pengguna) : 60,4/detik 

 - Total Throughput Keseluruhan Halaman(450 Pengguna) : 116/detik

Dari Jumlah Pengguna(50,100,150), Disini kita dapat mengetahui bahwa kecepatan transfer data pada web lebih besar jika tidak menggunakan Load balancer dibandingkan menggunakan load balancer.
