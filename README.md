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
            <div class="nav-logo">💧 SM Irigasi</div>
            <ul class="nav-menu">
                <li><a href="#tentang">Tentang</a></li>
                <li><a href="#fitur">Fitur</a></li>
                <li><a href="#monitoring">Monitoring</a></li>
                <li><a href="#lapor">Laporan</a></li>
            </ul>
        </div>
    </nav>

Penjelasan: Tag <nav> adalah elemen semantik HTML5 untuk navigasi. Di dalamnya terdapat logo website dan daftar menu menggunakan <ul> dan <li>. Setiap menu menggunakan href=”#id” untuk scroll ke bagian tertentu di halaman (anchor link). 

-Informasi sistem

**-Tabel monitoring sensor**
<table id="tabel-data">
                <thead>
                    <tr>
                        <th>No</th>
                        <th>ID Sensor</th>
                        <th>Lokasi</th>
                        <th>Debit Air (L/dtk)</th>
                        <th>TMA (cm)</th>
                        <th>Suhu (°C)</th>
                        <th>Kelembapan (%)</th>
                        <th>Status</th>
                        <th>Waktu</th>
                    </tr>
                </thead>
                <tbody id="isi-tabel">
                   
  </tbody>
</table>

Penjelasan: Tag <table> membuat tabel data sensor. Bagian <thead> berisi judul kolom yang dituliskan statis. Bagian <tbody id=”isi-tabel”> sengaja dikosongkan karena akan diisi secara dinamis oleh JavaScript menggunakan fungsi renderTabel(). ID “isi-tabel” digunakan sebagai penanda agar JavaScript bisa menemukan elemen ini melalui document.getElementById(). 

**-Form laporan pengguna**
 <div id="lapor">
            <h2>Laporan Kendala Irigasi</h2>
            <p>Petani atau petugas dapat melaporkan masalah irigasi melalui formulir berikut:</p>

            <div class="form-section">
                <label for="nama-pelapor" style="display:block; margin-bottom:10px;">Masukkan Nama Anda:</label>
                <input type="text" id="nama-pelapor" name="nama" placeholder="Contoh: Pak Yusuf" required>

                <label for="lokasi-kendala" style="display:block; margin-bottom:10px; margin-top:10px;">Lokasi Kendala:</label>
                <input type="text" id="lokasi-kendala" name="lokasi" placeholder="Contoh: Saluran Ngalor D">

                <label for="jenis-kendala" style="display:block; margin-bottom:10px; margin-top:10px;">Jenis Kendala:</label>
                <select id="jenis-kendala" name="kendala">
                    <option value="">-- Pilih Jenis Kendala --</option>
                    <option>Debit air terlalu kecil</option>
                    <option>Debit air terlalu besar / banjir</option>
                    <option>Sensor tidak terbaca</option>
                    <option>Saluran tersumbat</option>
                    <option>Pintu air rusak</option>
                    <option>Lainnya</option>
                </select>

                <button type="button" onclick="kirimLaporan()">Kirim Laporan</button>
            </div>

            <div id="pesan-form"></div>
        </div>

Penjelasan: Form terdiri dari input teks untuk nama, dropdown <select> untuk memilih jenis kendala, dan tombol submit. Atribut onclick="kirimLaporan()" pada tombol akan memanggil fungsi JavaScript setiap kali tombol diklik. Atribut for pada <label> menghubungkan label dengan input berdasarkan id. 

style.css
Mengatur tampilan visual website seperti:
-Layout halaman
-Warna navbar
-Styling tabel monitoring
-Responsivitas tampilan

Reset dan Body :
 *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f7f6;
    color: #333;
}

Penjelasan: Selector * berlaku untuk semua elemen. margin: 0 dan padding: 0 menghapus jarak bawaan browser agar tampilan konsisten. box-sizing: border-box memastikan padding tidak menambah lebar elemen. background-color menggunakan kode hex #f4f7f6 untuk warna abu-abu muda. 

**Styling Tabel**
table { 
width: 100%; 
border-collapse: collapse; 
table, th, td { 
border: 1px solid #ddd; 
} 

th, td { 
padding: 10px 14px; 
text-align: left; 
} 

th { 
background-color: #2e7d32; 
color: #ffffff; 
} 

tr:nth-child(even) { 
background-color: #f2f2f2; 
} 

tr:hover { 
background-color: #e8f5e9; 
} 

.status-normal { color: #2e7d32; font-weight: bold; } 
.status-kritis { color: #b71c1c; font-weight: bold; } 

Penjelasan: border-collapse: collapse menggabungkan garis tepi sel agar tidak double. Padding memberikan jarak dalam sel agar teks tidak terlalu rapat. Header tabel berwarna hijau dengan teks putih. Selector tr:nth-child(even) memberikan efek zebra stripe (warna bergantian pada baris genap) untuk memudahkan pembacaan data. Class .status-normal dan .status-kritis mengatur warna teks kolom status sesuai kondisi sensor. 


**scripts.js**
Berisi logika JavaScript seperti:
-Data sensor irigasi
-Render tabel monitoring
-Simulasi pembaruan data sensor
-Validasi form laporan

var dataSensor = [ 

{ id: "SNS-01", lokasi: "Saluran Induk Ngidul", debit: 12.4, tma: 42, suhu: 26.8, lembap: 68, status: "normal" }, 
{ id: "SNS-02", lokasi: "Percabangan Blok A", debit: 8.7, tma: 35, suhu: 27.1, lembap: 72, status: "normal" }, 
{ id: "SNS-03", lokasi: "Saluran Blok B", debit: 3.2, tma: 18, suhu: 28.3, lembap: 45, status: "rendah" }, 
{ id: "SNS-04", lokasi: "Bak Penampungan C1", debit: 18.9, tma: 71, suhu: 26.2, lembap: 80, status: "tinggi" }, 
{ id: "SNS-05", lokasi: "Saluran Ngalor D", debit: 6.5, tma: 28, suhu: 27.8, lembap: 63, status: "normal" }, 
{ id: "SNS-06", lokasi: "Saluran Ngetan E", debit: 1.1, tma: 10, suhu: 29.0, lembap: 31, status: "kritis" }, 
{ id: "SNS-07", lokasi: "Saluran Petak 12", debit: 9.3, tma: 38, suhu: 26.5, lembap: 70, status: "normal" }, 
{ id: "SNS-08", lokasi: "Embung Ngulon", debit: 7.8, tma: 32, suhu: 27.4, lembap: 66, status: "normal" } 

]; 

Penjelasan: dataSensor adalah sebuah array berisi 8 objek JavaScript. Setiap objek mewakili satu titik sensor dengan properti id (kode sensor), lokasi, debit air, tinggi muka air (tma), suhu, kelembapan (lembap), dan status. Array ini berfungsi sebagai database sementara yang disimpan di memori browser. 

**Fungsi renderTabel() - Manipulasi DOM**
unction renderTabel() { 

var tbody = document.getElementById("isi-tabel"); 

var html = ""; 


for (var i = 0; i < dataSensor.length; i++) { 

var s = dataSensor[i]; 

var classStatus = "status-" + s.status; 

html += "<tr>"; 

html += "<td>" + (i + 1) + "</td>"; 

html += "<td>" + s.id + "</td>"; 

html += "<td>" + s.lokasi + "</td>"; 

html += "<td>" + s.debit.toFixed(1) + "</td>"; 

html += "<td>" + s.tma + "</td>"; 

html += "<td>" + s.suhu.toFixed(1) + "</td>"; 

html += "<td>" + s.lembap + "</td>"; 

html += "<td><span class='" + classStatus + "'>" + labelStatus + "</span></td>"; 

html += "<td>" + waktuSekarang() + "</td>"; 

html += "</tr>"; 

} 

tbody.innerHTML = html; 

hitungRingkasan(); 

} 

Penjelasan: Fungsi ini mengisi tabel HTML dengan data dari array dataSensor. document.getElementById() mencari elemen berdasarkan id. Perulangan for membaca setiap objek sensor dan membangun kode HTML baris tabel secara dinamis. Metode toFixed(1) membulatkan angka desimal menjadi 1 digit. innerHTML = html memasukkan seluruh HTML yang telah dibangun ke dalam tabel halaman. 

**Fungsi perbarui Sensor() - Simulasi Real-Time **
unction perbaruiSensor() { 

for (var i = 0; i < dataSensor.length; i++) { 
var s = dataSensor[i]; 

s.debit = Math.max(0.5, s.debit + (Math.random() - 0.5)); 
s.tma = Math.max(5, s.tma + Math.round((Math.random() - 0.5) * 3)); 
s.lembap = Math.min(100, Math.max(10, s.lembap + Math.round((Math.random() - 0.5) * 2))); 
if (s.tma < 15) s.status = "kritis"; 
else if (s.tma < 25) s.status = "rendah"; 
else if (s.tma > 65) s.status = "tinggi"; 
else s.status = "normal"; 
} 
renderTabel(); 
} 

setInterval(perbaruiSensor, 4000); 

Penjelasan: Fungsi ini mensimulasikan perubahan data sensor secara acak untuk meniru kondisi real-time. Math.random() menghasilkan angka acak antara 0 dan 1, dikurangi 0.5 agar hasilnya bisa positif atau negatif sehingga data naik-turun alami. Math.max() mencegah nilai turun di bawah batas minimum. Logika if-else mengubah status berdasarkan nilai TMA: kritis (<15 cm), rendah (<25 cm), tinggi (>65 cm), atau normal. setInterval() meminta browser menjalankan fungsi ini setiap 4000 ms (4 detik). 

**Fungsi Kirim Laporan() -Validasi Form**
function kirimLaporan() { 

var nama = document.getElementById("nama-pelapor").value.trim(); 

var lokasi = document.getElementById("lokasi-kendala").value.trim(); 

var jenis = document.getElementById("jenis-kendala").value; 

var pesanEl = document.getElementById("pesan-form"); 

 

if (!nama || !lokasi || !jenis) { 

pesanEl.style.color = "#c0392b"; 

pesanEl.textContent = "Mohon isi semua kolom sebelum mengirim laporan."; 

return; 

} 

Penjelasan: Fungsi ini berjalan saat tombol diklik. Nilai input diambil dengan .value dan dibersihkan spasi dengan .trim(). Kondisi if (!nama || !lokasi || !jenis) memeriksa apakah ada field yang kosong. Tanda ! berarti 'bukan' dan || berarti 'atau', sehingga if aktif jika salah satu field kosong. Jika validasi gagal, fungsi berhenti dengan return sebelum sampai ke pesan sukses. 

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
