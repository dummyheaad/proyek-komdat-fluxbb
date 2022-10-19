# Proyek Komdat FluxBB
# ![Logo](http://fluxbb.org/files/images/logo_large.png)
[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:

| NIM | Nama | 
| ----- | ----- | 
| G6401201023 | Albarra Zikrillah |
| G6401201099 | Ridho Kartoni Pasaribu        |
| G6401201087 | Aysuka Ansari      |


## Sekilas Tentang
**FluxBB** adalah aplikasi forum _open-source_ yang dirilis dibawah GNU General Public Licence dan dapat diunduh dengan gratis. **FluxBB** dirancang sebagai alternatif yang lebih ringan dan cepat untuk beberapa aplikasi forum tradisional yang berat dengan mengurangi fitur-fitur yang "tidak terlalu penting" namun tetap memiliki fitur-fitur yang esensial untuk sebuah aplikasi forum. **FluxBB** mudah digunakan dan sudah memiliki _track record_ yang baik untuk kestabilan dan keamanan sehingga bisa menjadi pilihan aplikasi forum yang ideal untuk website Anda.

## Instalasi

#### Kebutuhan Sistem :
* Sebuah _webserver_
* PHP versi terbaru
* Sebuah DBMS, yaitu MySQL (bisa juga menggunakan DBMS yang lain)

#### Proses Instalasi :
1. Sediakan sebuah Virtual Machine yang akan digunakan sebagai _server_. Disini kami menggunakan sebuah VM Engine Instance dari Google Cloud.
![image](https://user-images.githubusercontent.com/99653989/196697873-ff9dea01-5ca5-42a9-92a3-d8256b265251.png)
2. Lakukan login ke _server_ menggunakan SSH.
![image](https://user-images.githubusercontent.com/99653989/196698169-6009ff6b-2cd9-4946-8e0a-8853f2aaeb8a.png)
3. Lakukan _update_ terhadap semua aplikasi dan sistem pada server.
```
sudo apt update
sudo apt upgrade
```
4. _Install_ kebutuhan sistem, sebagai contoh di sini kami menggunakan **Apache** sebagai _webserver_ dan **MySQL** sebagai DBMS.
```
sudo apt install apache2 php mysql-server
sudo apt install php-mysql php-gd php-mbstring php-xml php-curl
sudo service apache2 restart
```
5. Setelah kebutuhan sistem sudah ter-_install_, sebuah _database_ dan _user_ dibuat untuk aplikasi.
```
sudo mysql -u root -ve "
  CREATE DATABASE fluxbb;
  CREATE USER fluxadmin IDENTIFIED BY 'inipaswort';
  GRANT ALL PRIVILEGES ON fluxbb.* TO fluxadmin;
```
6. Unduh berkas instalasi **FluxBB** ke Virtual Machine. Versi **FluxBB** yang akan digunakan adalah versi _stable_ yaitu versi `1.5.11`.
```
sudo wget "https://fluxbb.org/download/releases/1.5.11/fluxbb-1.5.11.tar.gz"
```
7. Ekstrak berkas yang telah diunduh.
```
tar -xvzf fluxbb-1.5.11.tar.gz -C .
```
8. Pindahkan berkas yang sudah diekstrak ke direktori _webroot_
```
sudo mv fluxbb-1.5.11 /var/www/html/fluxbb
```
9. Ubah otorisasi kepemilikan ke _user_ `www-data` (_webserver_)
```
sudo chown -R www-data:www-data /var/www/html/fluxbb
```
10. Buka laman [FluxBB](http://34.128.79.83 "FluxBB") untuk melanjutkan proses instalasi **FluxBB**.
![image](https://user-images.githubusercontent.com/99653989/196703305-1aae9dfc-7645-4fea-aa3f-aa5aa2732708.png)
11. Jika tidak ada masalah maka akan muncul pemberitahuan seperti di bawah ini yang menandakan bahwa **FluxBB** telah berhasil di-_install_.
![image](https://user-images.githubusercontent.com/99653989/196703781-907a2e1b-c3df-463c-8ba2-6aec23346785.png)
12. Sekarang halaman _index_ dari forum **FluxBB** sudah bisa diakses.
![image](https://user-images.githubusercontent.com/99653989/196704056-14f939a7-0d4b-4a62-9eb1-d4673908fc52.png)
13. Terakhir file instalasi dihapus untuk alasan keamanan.
```
sudo rm -rf /var/www/html/fluxbb/install.php
```
## Konfigurasi
Untuk meningkatkan kinerja aplikasi, kita dapat melakukan hal-hal berikut seperti yang tercantum di [laman pengembangan **FluxBB**](https://github.com/fluxbb/fluxbb#recommendations).
- Gunakan PHP *accelerator* seperti **APC** atau **XCache** untuk mempercepat waktu eksekusi kode `PHP`.
- Pastikan PHP sudah ter-*install* modul **zlib** agar **FluxBB** dapat membuat output `gzip`.

Ada beberapa modifikasi yang dapat ditambahkan untuk **FluxBB**, yaitu [**Styles**](#styles), [**Language Packs**](#language-packs), dan [**Plugins**](#plugins).
### Styles
**Styles** berfungsi untuk mengubah tampilan atau tema pada aplikasi forum kita, *package-package* untuk modifikasi **Styles** ini dapat diunduh dari [laman *repository* **FluxBB**](http://fluxbb.org/resources/styles/).

Untuk meng-*install* **Styles** cukup unduh *file* `css` yang diinginkan lalu pindahkan ke folder `/var/www/html/fluxbb/style
`.

### Language Packs
**Language Packs** berfungsi untuk menambah opsi bahasa yang bisa digunakan pada aplikasi forum kita, **Language Packs** dapat diunduh dari [laman *repository* **FluxBB**](http://fluxbb.org/resources/translations/).

### Plugins
**Plugins** di **FluxBB** hanya bisa menambahkan fitur untuk *administrator* (dan *moderator* untuk beberapa **Plugins**) saja, **Plugins** berguna untuk menyederhanakan *task administrator* atau menambah fitur yang tidak bisa disediakan oleh **FluxBB** (karena filosofinya). **Plugins** dapat diunduh dari [laman *repository* **FluxBB**](https://github.com/fluxbb/plugins) atau bisa juga kita buat sendiri, *template*-nya dapat diakses di [laman *website* **FluxBB**](https://fluxbb.org/docs/v1.5/plugins). **Plugins** yang dapat digunakan oleh *administrator* diawali dengan `AP`, sedangkan yang dapat digunakan oleh *administrator* dan *moderator* diawali dengan `AMP`.

## Cara Pemakaian

## Referensi
