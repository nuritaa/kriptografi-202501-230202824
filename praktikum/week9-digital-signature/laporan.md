# Laporan Praktikum Kriptografi
Minggu ke-: 9
Topik: digital signature  
Nama: nurita ahadhini
NIM: 230202824
Kelas: 5IKRA

---

## 1. Tujuan
1.Mengimplementasikan tanda tangan digital menggunakan algoritma RSA/DSA.
2.Memverifikasi keaslian tanda tangan digital.
3.Menjelaskan manfaat tanda tangan digital dalam otentikasi pesan dan integritas data.

---

## 2. Dasar Teori
Digital Signature adalah cara untuk membuktikan keaslian dan keutuhan sebuah pesan atau dokumen secara digital. Dengan algoritma seperti RSA atau DSA, pengirim menandatangani pesan menggunakan kunci privat, lalu penerima memverifikasinya menggunakan kunci publik. Jika tanda tangan valid, berarti pesan benar berasal dari pengirim dan isinya tidak diubah.

RSA dan DSA sama-sama digunakan untuk tanda tangan digital, tetapi prinsipnya tetap sama : bukan untuk menyembunyikan isi pesan, melainkan untuk menjamin identitas pengirim dan integritas data. Digital signature banyak digunakan pada email, transaksi online, dan dokumen elektronik agar penerima bisa yakin bahwa data tersebut aman dan terpercaya.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
from Crypto.PublicKey import RSA
from Crypto.Signature import pkcs1_15
from Crypto.Hash import SHA256

# Generate pasangan kunci RSA
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Pesan yang akan ditandatangani
message = b"Hello, ini pesan penting."
h = SHA256.new(message)

# Buat tanda tangan dengan private key
signature = pkcs1_15.new(private_key).sign(h)
print("Signature:", signature.hex())
try:
    pkcs1_15.new(public_key).verify(h, signature)
    print("Verifikasi berhasil: tanda tangan valid.")
except (ValueError, TypeError):
    print("Verifikasi gagal: tanda tangan tidak valid.")
    # Modifikasi pesan
fake_message = b"Hello, ini pesan palsu."
h_fake = SHA256.new(fake_message)

try:
    pkcs1_15.new(public_key).verify(h_fake, signature)
    print("Verifikasi berhasil (seharusnya gagal).")
except (ValueError, TypeError):
    print("Verifikasi gagal: tanda tangan tidak cocok dengan pesan.")

---

## 6. Hasil dan Pembahasan

![Hasil Eksekusi](screenshots/kriptoweek9.png)

---

## 7. Jawaban Pertanyaan
1. Pada enkripsi RSA, tujuan utamanya adalah kerahasiaan. Pesan dienkripsi menggunakan kunci publik penerima agar hanya penerima yang memiliki kunci privat yang bisa membuka pesan tersebut. Sebaliknya, pada tanda tangan digital RSA, tujuannya bukan menyembunyikan isi pesan, melainkan membuktikan siapa pengirimnya dan memastikan pesan tidak diubah. Tanda tangan dibuat menggunakan kunci privat pengirim dan diverifikasi dengan kunci publik pengirim.
2. Tanda tangan digital menjamin integritas karena tanda tangan dibuat dari hasil hash pesan. Jika isi pesan diubah sedikit saja, nilai hash akan berubah dan verifikasi akan gagal. Tanda tangan digital juga menjamin otentikasi karena hanya pemilik kunci privat yang bisa membuat tanda tangan tersebut, sehingga penerima dapat yakin bahwa pesan benar-benar berasal dari pengirim yang sah.
3. Certificate Authority (CA) berperan sebagai pihak tepercaya yang memverifikasi identitas pemilik kunci publik. CA menerbitkan sertifikat digital yang menghubungkan identitas seseorang atau organisasi dengan kunci publiknya. Dengan adanya CA, penerima pesan tidak perlu menebak-nebak apakah kunci publik tersebut asli, karena keasliannya sudah dijamin oleh CA. Ini membuat sistem tanda tangan digital modern dapat dipercaya dan aman.
---

## 8. Kesimpulan
Program tersebut menunjukkan cara kerja digital signature dengan RSA. Pesan asli ditandatangani menggunakan private key, lalu tanda tangan berhasil diverifikasi menggunakan public key, yang berarti pesan benar berasal dari pengirim dan tidak diubah. Ketika isi pesan dimodifikasi, proses verifikasi gagal, sehingga membuktikan bahwa digital signature mampu mendeteksi perubahan data. Ini menegaskan fungsi utama digital signature, yaitu menjaga keaslian (autentikasi) dan keutuhan (integritas) pesan, bukan untuk menyembunyikan isi pesan.
---


## 10. Commit Log

Author: Nurita ahadhini <ahadininurita31@gmail.com>
Date:   2025-09-20

    week9-digital-signature
```
