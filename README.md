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
6. Unduh berkas instalasi **FluxBB** ke Virtual Machine. Versi **FluxBB** yang akan digunakan adalah versi _stable_ yaitu versi `1.5.11`
```
sudo wget "https://fluxbb.org/download/releases/1.5.11/fluxbb-1.5.11.tar.gz"
```
## Otomatisasi

## Cara Pemakaian

## Referensi
