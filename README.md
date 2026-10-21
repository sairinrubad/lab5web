LAPORAN PRAKTIKUM PEMROGRAMAN WEB
PERTEMUAN 6: JAVASCRIPT DASAR DAN MANIPULASI HTML
DISUSUN OLEH : SAIRIN BIN RUBAD
NIM : 312510134
KELAS : I 25 2A
PROGRAM STUDI TEKNIK INFORMATIKA
FAKULTAS TEKNIK
UNIVERSITAS PELITA BANGSA
CIKARANG 2026
I. TUJUAN PRAKTIKUM
1. Memahami sintaks dasar JavaScript dan teknik menyisipkan JavaScript pada HTML.
2. Menggunakan variabel, tipe data, operator, percabangan, perulangan, dan fungsi.
3. Menampilkan informasi luaran melalui console, alert, prompt, dan manipulasi elemen 
HTML.
4. Memanipulasi konten serta gaya visual elemen HTML menggunakan JavaScript 
(DOM Manipulation).
5. Membuat interaksi interaktif pada form HTML dan melakukan validasi input.
6. Mendokumentasikan dan menyusun laporan hasil praktikum secara sistematis.
II. DASAR TEORI
1. Pengenalan JavaScript & ECMAScript
JavaScript adalah bahasa pemrograman tingkat tinggi yang dieksekusi di sisi klien (client￾side) untuk mengatur interaktivitas halaman web. Standar bahasa JavaScript diatur oleh 
ECMAScript (ECMA-262). JavaScript mampu mengubah konten HTML, mengubah gaya 
CSS, memvalidasi input form, serta menangani berbagai event pengguna.
2. Metode Output dan Dialog
• console.log(): Mengirimkan instruksi/pesan ke konsol pengembang (Developer 
Tools). Digunakan terutama untuk proses debugging.
• alert(): Menampilkan jendela dialog peringatan sederhana kepada pengguna.
• prompt(): Menampilkan dialog input interaktif yang mengembalikan nilai berupa 
string.
• textContent / innerHTML: Properti DOM yang digunakan untuk mengubah konten 
teks atau HTML dari sebuah elemen secara terstruktur setelah halaman dimuat.
3. Variabel dan Tipe Data
JavaScript menyediakan kata kunci modern untuk deklarasi variabel:
• const: Deklarasi variabel dengan nilai tetap (immutable binding).
• let: Deklarasi variabel yang nilainya dapat diubah kembali (mutable).
Tipe data dasar meliputi string, number, boolean, undefined, null, object, dan symbol.
4. DOM (Document Object Model)
DOM adalah antarmuka pemograman untuk dokumen HTML. Melalui DOM, JavaScript 
dapat mengakses, menambah, menghapus, atau mengubah elemen dan atribut HTML 
menggunakan metode seperti document.getElementById() atau document.querySelectorAll().
III. LANGKAH KERJA DAN IMPLEMENTASI KODE
1. Persiapan Folder Kerja
Membuat struktur folder bernama Lab5Web yang memuat dua berkas utama: index.html dan 
script.js.
2. Implementasi index.html
<!DOCTYPE html>
<html lang="id">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Praktikum 5 - JavaScript Dasar</title>
 <style>
 body {
 font-family: Arial, sans-serif;
 margin: 20px;
 padding: 20px;
 background-color: #f9f9f9;
 }
 .container {
 max-width: 800px;
 margin: auto;
 background: #fff;
 padding: 20px;
 border-radius: 8px;
 box-shadow: 0 0 10px rgba(0,0,0,0.1);
 }
 section {
 margin-bottom: 25px;
 padding-bottom: 15px;
 border-bottom: 1px solid #ddd;
 }
 button {
 padding: 8px 15px;
 margin-right: 5px;
 cursor: pointer;
 }
 input[type="number"], input[type="text"] {
 padding: 6px;
 margin: 5px 0;
 }
 .hasil {
 font-weight: bold;
 color: #2c3e50;
 margin-top: 10px;
 }
 </style>
</head>
<body>
 <div class="container">
 <h1>Praktikum JavaScript Dasar & DOM</h1>
 
 <!-- Latihan 1 & 2 -->
 <section id="sec-latihan1">
 <h2>Latihan 1 & 2: Output, Alert, dan Prompt</h2>
 <p id="pesan">Konten awal halaman.</p>
 <button type="button" onclick="jalankanLatihan2()">Jalankan Prompt 
Nama</button>
 </section>
 <!-- Latihan 4 -->
 <section>
 <h2>Latihan 4: Cek Kelulusan (if-else)</h2>
 <button type="button" onclick="cekKelulusan()">Cek Nilai Kelulusan</button>
 </section>
 <!-- Latihan 5 -->
 <section>
 <h2>Latihan 5: Konversi Angka ke Teks (switch)</h2>
 <button type="button" onclick="konversiAngka()">Pilih Angka (1-5)</button>
 </section>
 <!-- Latihan 6 -->
 <section>
 <h2>Latihan 6: Cek Bilangan Genap/Ganjil</h2>
 <label for="bilangan">Masukkan bilangan bulat: </label>
 <input type="number" id="bilangan" step="1">
 <button type="button" onclick="cekBilangan()">Periksa</button>
 <p id="hasilBilangan" class="hasil"></p>
 </section>
 <!-- Latihan 7 -->
 <section>
 <h2>Latihan 7: Ubah Warna Latar Halaman</h2>
 <button type="button" onclick="ubahWarnaLatar('lightgreen')">Latar Hijau</button>
 <button type="button" onclick="ubahWarnaLatar('white')">Latar Putih</button>
 <button type="button" onclick="ubahWarnaLatar('lightyellow')">Latar 
Kuning</button>
 </section>
 <!-- Latihan 8 -->
 <section>
 <h2>Latihan 8: Checkbox Menu Makanan</h2>
 <h3>Daftar Menu Makanan</h3>
 <label><input type="checkbox" class="menu" value="5000"> Ayam Goreng 
(Rp5.000)</label><br>
 <label><input type="checkbox" class="menu" value="500"> Tempe 
(Rp500)</label><br>
 <label><input type="checkbox" class="menu" value="2500"> Telur Dadar 
(Rp2.500)</label><br>
 <label><input type="checkbox" class="menu" value="3000"> Es Teh Manis 
(Rp3.000)</label><br>
 <p>Total: Rp<span id="total">0</span></p>
 </section>
 <!-- Mini Project -->
 <section>
 <h2>Mini Project: Kalkulator Nilai Mahasiswa</h2>
 <form id="formNilai">
 <label>Nilai Tugas (30%): </label><br>
 <input type="number" id="inputTugas" min="0" max="100" required><br>
 <label>Nilai UTS (30%): </label><br>
 <input type="number" id="inputUTS" min="0" max="100" required><br>
 <label>Nilai UAS (40%): </label><br>
 <input type="number" id="inputUAS" min="0" max="100" required><br><br>
 <button type="button" onclick="prosesKalkulatorNilai()">Hitung Nilai</button>
 </form>
 <div id="hasilKalkulator" class="hasil"></div>
 </section>
 </div>
 <script src="script.js"></script>
</body>
</html>
3. Implementasi script.js
// ==========================================
// Latihan 1: Output pada DOM dan Console
// ==========================================
document.getElementById("pesan").textContent = "Hello World";
console.log("Hello World");
// ==========================================
// Latihan 2: Alert dan Prompt
// ==========================================
function jalankanLatihan2() {
 const namaPengguna = prompt("Masukkan nama Anda:", "");
 if (namaPengguna && namaPengguna.trim() !== "") {
 alert("Halo, " + namaPengguna + "!");
 document.getElementById("pesan").textContent = "Selamat datang, " + namaPengguna 
+ ".";
 } else {
 alert("Nama belum diisi.");
 }
}
// ==========================================
// Latihan 3: Function dan Operasi Aritmetika
// ==========================================
function operasiDasar(a, b) {
 console.log("--- Latihan 3: Hasil Operasi Aritmetika ---");
 console.log("Penjumlahan:", a + b);
 console.log("Pengurangan:", a - b);
 console.log("Perkalian:", a * b);
 console.log("Pembagian:", b !== 0 ? a / b : "Tidak dapat dibagi nol");
 console.log("Modulus:", a % b);
}
// Eksekusi fungsi Latihan 3
operasiDasar(9, 4);
// ==========================================
// Latihan 4: Seleksi Kondisi if-else
// ==========================================
function cekKelulusan() {
 const inputNilai = prompt("Masukkan nilai (0-100):");
 if (inputNilai === null) return; // User menekan cancel
 const nilaiMahasiswa = Number(inputNilai);
 if (
 inputNilai.trim() === "" ||
 Number.isNaN(nilaiMahasiswa) ||
 nilaiMahasiswa < 0 ||
 nilaiMahasiswa > 100
 ) {
 alert("Input nilai tidak valid.");
 } else if (nilaiMahasiswa >= 60) {
 alert("Lulus");
 } else {
 alert("Belum lulus");
 }
}
// ==========================================
// Latihan 5: Seleksi Kondisi switch
// ==========================================
function konversiAngka() {
 const inputPilihan = prompt("Masukkan angka 1-5:");
 if (inputPilihan === null) return;
 switch (inputPilihan) {
 case "1": alert("Bilangan satu"); break;
 case "2": alert("Bilangan dua"); break;
 case "3": alert("Bilangan tiga"); break;
 case "4": alert("Bilangan empat"); break;
 case "5": alert("Bilangan lima"); break;
 default: alert("Pilihan tidak tersedia");
 }
}
// ==========================================
// Latihan 6: Form Bilangan Genap atau Ganjil
// ==========================================
function cekBilangan() {
 const input = document.getElementById("bilangan").value;
 const angka = Number(input);
 const hasil = document.getElementById("hasilBilangan");
 if (input.trim() === "" || !Number.isInteger(angka)) {
 hasil.textContent = "Masukkan bilangan bulat yang valid.";
 } else if (angka % 2 === 0) {
 hasil.textContent = "Bilangan genap";
 } else {
 hasil.textContent = "Bilangan ganjil";
 }
}
// ==========================================
// Latihan 7: Mengubah Warna Halaman
// ==========================================
function ubahWarnaLatar(warna) {
 document.body.style.backgroundColor = warna;
}
// ==========================================
// Latihan 8: DOM dan Checkbox Menu Makanan
// ==========================================
const daftarMenu = document.querySelectorAll(".menu");
daftarMenu.forEach((item) => {
 item.addEventListener("change", hitungTotal);
});
function hitungTotal() {
 let total = 0;
 daftarMenu.forEach((item) => {
 if (item.checked) {
 total += Number(item.value);
 }
 });
 document.getElementById("total").textContent = total.toLocaleString("id-ID");
}
// ==========================================
// Mini Project: Kalkulator Nilai Mahasiswa
// ==========================================
function hitungNilaiAkhir(tugas, uts, uas) {
 return (tugas * 0.30) + (uts * 0.30) + (uas * 0.40);
}
function tentukanPredikat(nilai) {
 if (nilai >= 85) return "A";
 if (nilai >= 75) return "B";
 if (nilai >= 60) return "C";
 if (nilai >= 50) return "D";
 return "E";
}
function prosesKalkulatorNilai() {
 const rawTugas = document.getElementById("inputTugas").value;
 const rawUTS = document.getElementById("inputUTS").value;
 const rawUAS = document.getElementById("inputUAS").value;
 const tugas = Number(rawTugas);
 const uts = Number(rawUTS);
 const uas = Number(rawUAS);
 const elemHasil = document.getElementById("hasilKalkulator");
 // Validasi input
 if (
 rawTugas === "" || rawUTS === "" || rawUAS === "" ||
 isNaN(tugas) || isNaN(uts) || isNaN(uas) ||
 tugas < 0 || tugas > 100 ||
 uts < 0 || uts > 100 ||
 uas < 0 || uas > 100
 ) {
 elemHasil.innerHTML = "<span style='color:red;'>Harap masukkan nilai valid rentang 
0-100!</span>";
 return;
 }
 const nilaiAkhir = hitungNilaiAkhir(tugas, uts, uas);
 const predikat = tentukanPredikat(nilaiAkhir);
 const status = nilaiAkhir >= 60 ? "Lulus" : "Belum Lulus";
 elemHasil.innerHTML = `
 <br>--- Hasil Perhitungan ---<br>
 Nilai Akhir: {nilaiAkhir.toFixed(2)} <br>
 Predikat: {predikat} <br>
 Status Kelulusan: <strong>${status}</strong>
 `;
}
IV. HASIL DAN PEMBAHASAN
1. Analisis Perilaku Program Per Latihan
• Latihan 1: Pesan "Hello World" berhasil ditampilkan langsung di elemen HTML 
dengan ID pesan via textContent dan pada Console browser melalui console.log().
• Latihan 2: prompt() mengambil masukan string dari pengguna. Jika pengguna 
mengisi nama, alert() menyapa dan teks DOM diperbarui. Jika dibatalkan atau 
dikosongkan, aplikasi memicu alert penanganan kondisi kosong.
• Latihan 3: Fungsi operasiDasar(9, 4) mengeksekusi perhitungan matematika dan 
memberikan keluaran konsol secara tepat (9 + 4 = 13, 9 % 4 = 1, dst.).
• Latihan 4 & 5: Penerapan percabangan if-else memvalidasi konversi tipe data dari 
string ke number sebelum mengevaluasi status batas lulus ($60$). Sedangkan switch￾case mencocokkan input masukan string angka ke dalam representasi teks.
• Latihan 6: Memanfaatkan operator aritmetika Modulus (% 2). Bila sisa bagi bernilai
$0$, bilangan didefinisikan sebagai genap.
• Latihan 7: Manipulasi properti gaya melalui sintaks 
document.body.style.backgroundColor berhasil mengubah warna latar belakang 
halaman secara instan.
• Latihan 8: Implementasi addEventListener('change', ...) secara dinamis memantau 
perubahan status checkbox dan menjumlahkan nilai (value) menu terpilih.
2. Pengujian Mini Project (Kalkulator Nilai)
Dilakukan pengujian dengan $3$ skenario masukan yang berbeda:
Skenario
Nilai 
Tugas
Nilai 
UTS
Nilai 
UAS
Nilai 
Akhir
Predikat
Status 
Kelulusan
Skenario 
1
85
80 90 85.50
A Lulus
Skenario 
2
65
60 55 59.50
D Belum Lulus
Skenario 
3
105 -10 80 Error 
Validasi
-
Ditolak 
(Input tidak 
valid)
V. JAWABAN PERTANYAAN DAN TUGAS
1. Jelaskan perbedaan console.log(), alert(), prompt(), dan 
textContent/innerHTML.
o console.log(): Menampilkan data ke konsol pengembang browser, tidak 
mengganggu antarmuka pengguna.
o alert(): Menampilkan pop-up dialog peringatan satu arah yang memblokir 
interaksi hingga tombol 'OK' ditekan.
o prompt(): Menampilkan dialog pop-up yang meminta masukan teks (input) 
dari pengguna.
o textContent/innerHTML: Digunakan untuk mengubah isi dari elemen DOM. 
textContent hanya menyisipkan teks polos, sedangkan innerHTML dapat 
memproses dan menerjemahkan tag HTML.
2. Apa perbedaan let dan const? Berikan contoh.
o let: Mendeklarasikan variabel tingkat blok (block-scoped) yang nilainya dapat 
diubah kembali (reassignable).
o const: Mendeklarasikan variabel bernilai konstan yang tidak dapat diubah 
kembali setelah diinisialisasi.
3. let umur = 20;
4. umur = 21; // Valid
5.
6. const pi = 3.14;
7. pi = 3.14159; // Error: Assignment to constant variable.
8. Apa perbedaan operator == dan ===?
o == (Abstract Equality): Membandingkan dua nilai setelah melakukan konversi 
tipe data secara otomatis (type coercion).
o === (Strict Equality): Membandingkan dua nilai sekaligus tipe datanya tanpa 
melakukan konversi otomatis. Contoh: '5' == 5 bernilai true, sedangkan '5' 
=== 5 bernilai false.
9. Jelaskan fungsi if-else dan switch. Kapan masing-masing dapat digunakan?
o if-else: Digunakan untuk pengujian kondisi yang kompleks, bernilai boolean, 
menggunakan operator logika (&&, ||), atau pengujian berbasis rentang nilai 
(contoh: nilai >= 80).
o switch: Digunakan jika terdapat banyak cabang kondisi diskrit yang 
didasarkan pada perbandingan ketersediaan satu nilai/variabel tunggal secara 
pasti (sama dengan).
10. Apa fungsi parameter dan return dalam function?
o Parameter: Variabel penampung nilai masukan (input) yang dikirimkan ke 
dalam fungsi untuk diolah.
o Return: Kata kunci untuk menghentikan eksekusi fungsi dan mengembalikan 
suatu nilai hasil olahan kembali ke pemanggil fungsi.
11. Bagaimana JavaScript memilih elemen HTML menggunakan 
document.getElementById()?
o Fungsi tersebut mencari elemen tunggal di dalam dokumen HTML yang 
atribut id-nya cocok dengan string argumen yang diberikan, kemudian 
mengembalikan objek elemen DOM tersebut.
12. Script Validasi Form (Nama Tidak Kosong & Nilai 0-100):
13. function validasiForm(nama, nilai) {
14. if (!nama || nama.trim() === "") {
15. console.log("Validasi Gagal: Nama tidak boleh kosong.");
16. return false;
17. }
18. const numNilai = Number(nilai);
19. if (isNaN(numNilai) || numNilai < 0 || numNilai > 100) {
20. console.log("Validasi Gagal: Nilai harus berupa angka rentang 0 - 100.");
21. return false;
22. }
23. console.log("Validasi Berhasil!");
 return true;
}
VI. KESIMPULAN 
Praktikum ini memberikan pemahaman dasar mendalam mengenai penggunaan JavaScript 
pada lingkungan browser web. Melalui praktikum ini, dapat disimpulkan bahwa:
1. JavaScript memungkinkan pembuatan halaman web yang dinamis dan interaktif 
melalui manipulasi elemen Document Object Model (DOM).
2. Penerapan struktur data, variabel (let/const), logika percabangan, serta fungsi yang 
terstruktur menjadi kunci utama dalam membangun alur program web yang aman.
3. Penggunaan validasi input sangat krusial untuk memastikan data masukan pengguna 
sesuai dengan kriteria yang diharapkan sebelum diproses lebih lanjut.
