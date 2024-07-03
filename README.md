## Project 5 - Create CRUD API Using Flask and Docker

# Tools yang disiapkan:

- docker
- postman
- visual code

# API yang dibuat:

- create user
- update user
- get user
- delete user

# Tugas:

Membuat pipeline untuk mentransfer data yang ada di database operational MySQL ke database data_warehouse di PostgreSQL

# Langkah pengerjaan:

1.	Menjalankan perintah `docker-compose up`

![image](https://github.com/dzzzzrca/project5/assets/153365739/49812ed3-2e8d-4de9-966a-d6e7a334ae0f)

Dalam hal ini, file docker-compose.yml berisi dua services: satu untuk MySQL dan satu untuk PostgreSQL.

 ![image](https://github.com/dzzzzrca/project5/assets/153365739/3f89cea0-34f7-475e-aee6-32dff8547c97)

Gambar diatas untuk memastikan bahwa container sudah terbuat dan berjalan.

2.	Memasuki terminal container db-mysql di Docker Dekstop

![image](https://github.com/dzzzzrca/project5/assets/153365739/00b00cae-728e-4ac6-88ab-08128bffa599)

Gambar diatas untuk masuk kedalam direktori yang sama dengan file csv berisikan data yang akan di import.

3.	Memasuki MySQL Database

![image](https://github.com/dzzzzrca/project5/assets/153365739/897dcba0-5c9e-4910-a894-96fdfea66cc8)

Gambar diatas langkah masuk ke database MySQL yang bernama operational menggunakan username=root dan password=mysql. Penjelasan kueri yang digunakan sebagai berikut:
-	--local-infile=1: Mengaktifkan pemuatan data dari file lokal ke dalam database.
-	-uroot: Menentukan nama pengguna root.
-	-pmysql: Menentukan kata sandi mysql.
-	operational: Menentukan nama database yang akan dihubungi.
 
4.	Membuat table youtube
a.	Menggunakan database operational dan mengaktifkan ulang local_infile agar dapat memuat data dari file lokal ke dalam database
b.  Karena belum ada table pada database operational, maka langkah selanjutnya membuat table dengan nama `youtube`
 
d.	Membuat table `youtube` sesuai query DDL yang ada pada file init.sql
 
 
e.	Table `youtube` sudah berhasil dibuat
 
7.	Mengimpor data ke dalam table youtube
a.	Karena table `youtube` masih kosong, langkah selanjutnya mengimpor data dari local dari pada file global_youtube_stat.csv
 
b.	Mengimpor data ke dalam table `youtube`
 
c.	Data berhasil di impor
 
8.	Membuat dan mengaktifkan virtual environment & menginstal python requirements.txt
 
-	python -m venv env: membuat virtual environment bernama env di dalam direktori saat ini, yang bertujuan untuk mengisolasi dependensi proyek dan mencegah konflik dengan instalasi Python lainnya.
-	env/Scripts/activate: mengaktifkan virtual environment
-	pip install -r requirements.txt: menginstal module yang dibutuhkan
9.	Memasuki PostgreSQL Database
 
Gambar diatas langkah masuk ke PostgreSQL Database yang dengan username=root
10.	Membuat database di PostgreSQL
 
Perintah `\l` bertujuan untuk menampilkan semua database yang tersedia dalam instansi PostgreSQL.
 
Perintah `create database data_warehouse` untuk membuat database baru dengan nama = data_warehouse.
 
-	Perintah `\c data_warehouse` untuk masuk ke dalam database data_warehouse.
-	Perintah `\d` menampilkan semua tabel dalam database data_warehouse.
11.	Mengimpor dan memverifikasi data dari MySQL ke PostrgeSQL
a.	Proses pengimporan data
Kode yang disediakan dalam file etl.py akan membaca data dari basis data MySQL dan menuliskannya ke basis data PostgreSQL. Kode tersebut menggunakan perpustakaan pandas untuk membaca dan menulis data, serta perpustakaan mysql.connector dan sqlalchemy untuk terhubung ke basis data. Kode pertama-tama terhubung ke basis data MySQL dan membaca data dari tabel youtube. Kemudian, ia terhubung ke basis data PostgreSQL dan menulis data ke tabel bernama youtube_etl. Jika terjadi pengecualian, kode menangkapnya dan mencetak pesan kesalahan.
 
b.	Memverifikasi data
Setelah masuk kembali ke dalam PostgreSQL pada database data_warehouse, sudah terlihat ketika perintah `\d` dijalankan kembali terdapat table dengan nama youtube_etl.
 
