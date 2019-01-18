# RESPONSI TEKNOLOGI CLOUD TERAPAN 

## Dockerfile

### a. Pengertian 
Dockerfile sendiri merupakan skrip yang terdiri dari serangkaian perintah, intruksi (argumen) yang akan dieksekusi secara 
otomatisasi dan berurutan untuk membangun sebuah image. Jadi akan mempermudah kita untuk tidak selalu mengetikkan perintah setiap kali kita 
akan menjalankan container. Jadi Docker dapat membuat image secara otomatis dengan membaca instruksi dari Dockerfile.

### b. Perintah yang ada pada dockerfile :
1. ADD
Perintah ADD digunakan untuk mengcopy file dari suatu direktori ke direktori tujuan.
Jika direktori asal adalah sebuah URL, perintah add akan mendownloadnya dan menempatkannya ke direktori tujuan.

2. CMD
Perintah CMD hampir sama dengan perintah RUN, CMD digunakan untuk mengeksekusi perintah yang lebih spesifik, 
seperti pada saat proses pembuatan container pada image.

3. ENTRYPOINT
ENTRYPOINT adalah argumen untuk mengeset default aplikasi yang digunakan setiap kali sebuah container dibuat menggunakan image.

4. ENV
ENV digunakan untuk mengeset environment variables.

5. FROM
FROM argument mendefinisikan sebuah base image yang akan digunakan untuk memulai membangun proses pada setiap docker image 
apakah itu di repositori ataupun di host kita sendiri.

6. WORKDIR
WORKDIR direktif digunakan untuk mengatur di mana perintah didefinisikan dengan CMD yang akan dieksekusi.

7. RUN
RUN adalah perintah yang digunakan untuk membangun docker images yang terpusat untuk mengeksekusi Dockerfiles.

8. MAINTAINER
MAINTAINER adalah perintah yang tidak dijalankan tetapi di deklarasikan sebagai author field dari images.

9. USER
USER direktif digunakan untuk mengatur UID (atau nama pengguna) yang menjalankan sebuah container berdasarkan dari image yang sedang dibangun.

10. VOLUME
Perintah VOLUME digunakan untuk mengaktifkan akses dari kontainer kita ke direktori pada mesin host.

11. EXPOSE
Perintah EXPOSE digunakan untuk menghubungkan port tertentu untuk mengaktifkan network antara proses yang berjalan di dalam container dan mesin host

### Cara Membuat Container menggunakan Dockerfile

1. Untuk  membuat container yang berisi Nginx web server, Pertama buat dulu file dockerfile dengan editor.
2. Kemudian kita tambahkan konfigurasi docker yang didalamnya terdapat perintah dan argument untuk membuat container Nginx web server. 
   Base image yang digunakan adalah ubuntu. 
   Konfigurasinya adalah seperti di bawah ini :
      ![w]((https://github.com/ayuwidyainggit/ujian-tct/blob/master/images/w.png))
3. build image nya dengan menggunakan dockerfile diatas, untuk mulai membuild jalankan perintah berikut :
    docker build -t nginx_webserver .
	![2.1](https://github.com/ayuwidyainggit/ujian-tct/blob/master/images/2.1.png)
	
4. cek hasilnya dengan perintah :
    docker images
	![2.2](https://github.com/ayuwidyainggit/ujian-tct/blob/master/images/2.2.png)
	disitu terlihat dengan image ID 5d62ac5f7514
	
5. Membuat sebuah Docker Container
Dengan menggunakan image ubuntu yang kita build, kita akan membuat sebuah container yang berjalan didalam 
instance web server Nginx. Jalankan perintah berikut :
     docker run –name nginx_webserver_instance -p 80:80 -d nginx_webserver
	![2.3](https://github.com/ayuwidyainggit/ujian-tct/blob/master/images/2.3.png)
Gambar di atas kita telah berhasil membuat container Nginx dan memforwardnya ke port 80. 
Untuk mengeceknya gunakan perintah di bawah ini :
      docker ps -a
	 ![2.4](https://github.com/ayuwidyainggit/ujian-tct/blob/master/images/2.4.png) 
Untuk menjalankan perintah curl ke localhost adalah dengan perintah :
     curl localhost
	  ![2.5](https://github.com/ayuwidyainggit/ujian-tct/blob/master/images/2.5.png) 
container Nginx  web server telah berjalan base image ubuntu, atau coba buka browser, buka alamat ip kita
untuk menjalankannya buka browser dengan alamat ip kita :
      ![2.6](https://github.com/ayuwidyainggit/ujian-tct/blob/master/images/2.6.png) 
cara menghentikan container yang sedang berjalan :
      docker stop <container id> 
	  
	