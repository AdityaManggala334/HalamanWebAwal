**Sistem Monitoring Irigasi Sawah Berbasis Sensor**

Website SM Irigasi adalah landing page simulasi sistem monitoring irigasi sawah berbasis sensor yang dibuat menggunakan HTML, CSS, dan JavaScript.
Project ini dibuat sebagai tugas Praktikum Pemrograman Web pada Program Studi D3 Teknik Informatika.

Website ini menampilkan data sensor irigasi secara dinamis serta menyediakan fitur pelaporan kendala oleh pengguna.

Latar Belakang
Sektor pertanian di Indonesia masih banyak mengandalkan pengelolaan irigasi secara manual. Hal ini sering menyulitkan petani atau petugas irigasi untuk memantau kondisi air secara real-time, terutama pada malam hari atau saat cuaca ekstrem. 
Melalui project ini dibuat sebuah landing page sistem monitoring irigasi yang menggambarkan bagaimana teknologi web dapat digunakan untuk membantu proses pemantauan kondisi saluran air secara digital.

Project ini dibuat untuk:
-Menerapkan dasar pemrograman web menggunakan HTML, CSS, dan JavaScript
-Memahami struktur dokumen HTML semantik
-Mengatur tampilan web menggunakan CSS
-Membuat website interaktif dengan JavaScript
-Menerapkan konsep separation of concerns (memisahkan HTML, CSS, dan JavaScript)

Project ini dibuat untuk:
-Menerapkan dasar pemrograman web menggunakan HTML, CSS, dan JavaScript
-Memahami struktur dokumen HTML semantik
-Mengatur tampilan web menggunakan CSS
-Membuat website interaktif dengan JavaScript

Menerapkan konsep separation of concerns (memisahkan HTML, CSS, dan JavaScript)

**PENJELASAN**
index.html
Berisi struktur utama halaman website seperti:
**-Head :**
<!DOCTYPE html>	  -Memberitahu browser menggunakan HTML5
<html lang="id">	-Bahasa halaman adalah Bahasa Indonesia
<meta charset>	  -Mendukung karakter seperti huruf Indonesia
<meta viewport>	  -Membuat website responsif
<title>	          -Judul halaman di tab browser
<link>	          -Menghubungkan file CSS
  
**-Navbar:**
<nav>
<div class="nav-container">
<div class="nav-logo">SM Irigasi</div>

<ul class="nav-menu">
<li><a href="#tentang">Tentang</a></li>
<li><a href="#fitur">Fitur</a></li>
<li><a href="#monitoring">Monitoring</a></li>
<li><a href="#lapor">Laporan</a></li>
</ul>

</div>
</nav>

Fungsi: Navbar adalah menu navigasi website.
Analogi: Navbar = daftar isi buku, ketika user klik menu: href="#monitoring" Browser akan scroll ke bagian monitoring.

-Informasi sistem
**-Tabel monitoring sensor**
<table id="tabel-data">

<thead>
<tr>
<th>No</th>
<th>ID Sensor</th>
<th>Lokasi</th>
<th>Debit Air</th>
<th>TMA</th>
<th>Status</th>
</tr>
</thead>

<tbody id="isi-tabel">
</tbody>

</table>

Penjelasan:
Tag	            Fungsi
<table>	        Membuat tabel
<thead>	        Bagian judul tabel
<tbody>	        Isi tabel
id="isi-tabel"	Penanda agar JavaScript bisa mengisi data

tbody kosong. Karena data akan diisi oleh JavaScript secara otomatis


**-Form laporan pengguna**
<input type="text" id="nama-pelapor">

<select id="jenis-kendala">
<option value="">Pilih Kendala</option>
<option>Debit air kecil</option>
<option>Saluran tersumbat</option>
</select>

<button onclick="kirimLaporan()">
Kirim Laporan
</button>

Ketika tombol ditekan: onclick="kirimLaporan()" Browser akan menjalankan fungsi JavaScript bernama: kirimLaporan()

style.css
Mengatur tampilan visual website seperti:
-Layout halaman
-Warna navbar
-Styling tabel monitoring
-Responsivitas tampilan

scripts.js
Berisi logika JavaScript seperti:
-Data sensor irigasi
-Render tabel monitoring
-Simulasi pembaruan data sensor
-Validasi form laporan

**FITUR WEBSISITE**
Website ini memiliki beberapa fitur utama:

1️⃣ Navbar Navigasi
Navigasi utama yang berisi menu:
-Tentang Sistem
-Fitur
-Monitoring
-Laporan
Navbar dibuat sticky sehingga tetap terlihat saat halaman di-scroll.

2️⃣ Hero Section
Bagian awal halaman yang menampilkan:
-Judul sistem monitoring
-Deskripsi singkat sistem
-Tombol navigasi ke bagian monitoring

3️⃣ Informasi Sistem
Menampilkan informasi dasar mengenai sistem irigasi seperti:
-Nama sistem
-Jumlah sensorJenis sensor
-Interval pembaruan data

4️⃣ Monitoring Sensor
Bagian utama website berupa tabel monitoring sensor yang menampilkan:
-ID sensor
-Lokasi sensor
-Debit air
-Tinggi muka air (TMA)
-Suhu
-Kelembapan
-Status kondisi air
-Waktu pembaruan

Data tabel diperbarui secara otomatis menggunakan JavaScript setiap beberapa detik untuk mensimulasikan kondisi real-time.

5️⃣ Form Laporan Kendala
Pengguna dapat mengirim laporan terkait masalah irigasi seperti:
-Debit air terlalu kecil
-Saluran tersumbat
-Kendala lainnya

Form dilengkapi dengan validasi input menggunakan JavaScript.


**CARA KERJA WEBSITE INI**
Alur sederhana sistem pada website ini:
-Data sensor disimpan di JavaScript
-Fungsi renderTabel() membuat tabel HTML secara dinamis
-Fungsi perbaruiSensor() mensimulasikan perubahan data sensor
-Browser menjalankan pembaruan data secara berkala
-Tabel monitoring diperbarui secara otomatis
