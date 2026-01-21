# Laporan Praktikum Kriptografi
Minggu ke-: 14  
Topik: analisis serangan 
Nama: nuirta ahdhini  
NIM: 230202824 
Kelas: 5IKRA

---

## 1. Tujuan
Mengidentifikasi jenis serangan pada sistem informasi nyata.
Mengevaluasi kelemahan algoritma kriptografi yang digunakan.
Memberikan rekomendasi algoritma kriptografi yang sesuai untuk perbaikan keamanan.

---

## 2. Dasar Teori
Materi analisis serangan membahas berbagai jenis ancaman dan serangan yang dapat terjadi pada sistem informasi, khususnya pada jaringan dan teknologi blockchain. Peserta mempelajari karakteristik serangan, tujuan penyerang, serta celah keamanan yang sering dimanfaatkan, seperti manipulasi data, serangan double spending, dan serangan 51%. Dengan memahami pola dan mekanisme serangan, peserta dapat mengidentifikasi risiko yang mungkin muncul dalam sebuah sistem.

Selain itu, materi ini menekankan pentingnya teknik analisis dan mitigasi serangan untuk menjaga keamanan dan keandalan sistem. Peserta diajak untuk menganalisis dampak serangan terhadap integritas, ketersediaan, dan kerahasiaan data, serta merancang strategi pencegahan yang tepat. Dengan demikian, analisis serangan menjadi dasar penting dalam pengembangan sistem yang aman dan tahan terhadap ancaman.

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
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

```python
# contoh potongan kode
def encrypt(text, key):
    return ...
```
)

---

## 6. Hasil dan Pembahasan
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
1. Banyak sistem lama masih rentan karena menggunakan algoritma hash atau enkripsi yang sudah usang (misalnya MD5 atau SHA-1) dan kebijakan kata sandi yang lemah, seperti password pendek atau umum. Selain itu, sistem lama sering tidak menerapkan salt, rate limiting, atau account lockout, sehingga penyerang dapat mencoba banyak kombinasi kata sandi tanpa hambatan. Keterbatasan pembaruan dan kompatibilitas juga membuat sistem tersebut sulit ditingkatkan ke standar keamanan modern.
2. Kelemahan algoritma adalah masalah yang melekat pada desain algoritma kriptografi itu sendiri, misalnya algoritma yang secara matematis sudah dapat dipecahkan atau tidak lagi aman.
Kelemahan implementasi terjadi karena kesalahan dalam penerapan algoritma yang sebenarnya aman, seperti penggunaan kunci yang terlalu pendek, pengelolaan kunci yang buruk, atau kesalahan konfigurasi sistem.
3. Organisasi dapat menjaga keamanan sistem kriptografi dengan mengikuti standar kriptografi terbaru, melakukan pembaruan dan audit keamanan secara berkala, serta menggunakan algoritma yang direkomendasikan secara internasional. Selain itu, penerapan manajemen kunci yang baik, penggunaan multi-factor authentication, dan perencanaan crypto agility (kemampuan mengganti algoritma dengan cepat jika ditemukan kelemahan) sangat penting agar sistem tetap aman menghadapi ancaman di masa depan.
   
---

## 8. Kesimpulan
Banyak sistem lama masih rentan terhadap serangan brute force dan dictionary attack akibat penggunaan algoritma usang, kebijakan kata sandi yang lemah, serta minimnya mekanisme pengamanan tambahan. Perbedaan antara kelemahan algoritma dan kelemahan implementasi menunjukkan bahwa keamanan tidak hanya bergantung pada algoritma yang digunakan, tetapi juga pada cara penerapannya. Oleh karena itu, organisasi perlu menerapkan standar kriptografi terbaru, melakukan pembaruan dan audit secara berkala, serta memiliki strategi keamanan jangka panjang agar sistem kriptografi tetap aman dan adaptif terhadap perkembangan ancaman di masa depan.

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log

Author: Nurita ahadhini <ahadininurita31@gmail.com>
Date:   2025-09-20

    week14-analisis-serangan
```
