# Laporan Praktikum Kriptografi
Minggu ke-: 7
Topik: diffie hellman  
Nama: nurita ahdhini
NIM: 230202824 
Kelas: 5IKRA 

---

## 1. Tujuan
1.Melakukan simulasi protokol Diffie-Hellman untuk pertukaran kunci publik.
2.Menjelaskan mekanisme pertukaran kunci rahasia menggunakan bilangan prima dan logaritma diskrit.
3.Menganalisis potensi serangan pada protokol Diffie-Hellman (termasuk serangan Man-in-the-Middle / MITM).

---

## 2. Dasar Teori
Diffie–Hellman Key Exchange adalah metode untuk berbagi kunci rahasia secara aman melalui jaringan yang tidak aman. Cara kerjanya mirip seperti dua orang menyepakati resep rahasia di tempat umum tanpa pernah mengucapkan resep aslinya. Keduanya terlebih dulu menyepakati angka umum, lalu masing-masing menggabungkannya dengan rahasia pribadi. Hasil yang dipertukarkan aman untuk dilihat siapa pun, tetapi ketika digabungkan kembali, kedua pihak akhirnya mendapatkan kunci rahasia yang sama. Kunci inilah yang kemudian dipakai untuk enkripsi data, misalnya dengan AES, tanpa pernah mengirim kunci rahasia secara langsung.
Selain itu, keamanan Diffie–Hellman bergantung pada kesulitan perhitungan matematika tertentu, yaitu masalah logaritma diskret, yang sangat sulit dipecahkan meskipun nilai yang dipertukarkan diketahui oleh penyerang. Karena itu, Diffie–Hellman banyak digunakan dalam komunikasi modern seperti HTTPS dan VPN untuk membangun koneksi aman di awal komunikasi. Namun, Diffie–Hellman sendiri tidak mengenkripsi pesan, melainkan hanya digunakan untuk membuat kunci bersama, sehingga tetap perlu dikombinasikan dengan algoritma enkripsi lain.



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
import random

# parameter umum (disepakati publik)
p = 23  # bilangan prima
g = 5   # generator

# private key masing-masing pihak
a = random.randint(1, p-1)  # secret Alice
b = random.randint(1, p-1)  # secret Bob

# public key
A = pow(g, a, p)
B = pow(g, b, p)

# exchange public key
shared_secret_A = pow(B, a, p)
shared_secret_B = pow(A, b, p)

print("Kunci bersama Alice :", shared_secret_A)
print("Kunci bersama Bob   :", shared_secret_B)

---

## 6. Hasil dan Pembahasan

![Hasil Eksekusi](screenshots/kriptoweek7.png)


---

## 7. Jawaban Pertanyaan
1. Diffie–Hellman memungkinkan pertukaran kunci di saluran publik karena yang dikirimkan bukan kunci rahasia, melainkan hasil perhitungan matematika dari kunci rahasia tersebut. Meskipun nilai-nilai yang dipertukarkan dapat dilihat oleh siapa pun, penyerang tetap tidak bisa menghitung kunci rahasia akhir karena harus memecahkan masalah matematika yang sangat sulit, yaitu logaritma diskret.
2. Kelemahan utama Diffie–Hellman murni adalah tidak menyediakan autentikasi. Artinya, protokol ini tidak memastikan siapa sebenarnya pihak yang sedang diajak berkomunikasi. Akibatnya, penyerang dapat menyamar sebagai perantara dan membuat dua kunci berbeda dengan masing-masing pihak tanpa disadari.
3. Serangan MITM dapat dicegah dengan menambahkan mekanisme autentikasi, misalnya menggunakan sertifikat digital, tanda tangan digital, atau menggabungkan Diffie–Hellman dengan protokol keamanan seperti TLS/HTTPS. Dengan autentikasi ini, kedua pihak dapat memverifikasi identitas satu sama lain, sehingga penyerang tidak dapat menyisipkan diri dalam proses pertukaran kunci.
---

## 8. Kesimpulan
Dari hasil program terlihat bahwa Diffie–Hellman berhasil menghasilkan kunci rahasia yang sama untuk Alice dan Bob meskipun mereka hanya bertukar nilai publik. Ini membuktikan bahwa pertukaran kunci dapat dilakukan melalui saluran publik tanpa mengirimkan kunci rahasia secara langsung. Contoh ini juga menunjukkan prinsip dasar Diffie–Hellman, yaitu keamanan diperoleh dari perhitungan matematika, meskipun pada contoh digunakan angka kecil untuk tujuan pembelajaran.


---


## 10. Commit Log

Author: Nurita ahadhini <ahadininurita31@gmail.com>
Date:   2025-09-20

   week7-diffie-hellman
```
