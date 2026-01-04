# Laporan Praktikum Kriptografi
Minggu ke-: 4
Topik: Entropy UNicity  
Nama: Nurita Ahadhini  
NIM: 230202824 
Kelas: 5IKRA  

---

## 1. Tujuan
1.Menyelesaikan perhitungan sederhana terkait entropi kunci.
2.Menggunakan teorema Euler pada contoh perhitungan modular & invers.
3.Menghitung unicity distance untuk ciphertext tertentu.
4.Menganalisis kekuatan kunci berdasarkan entropi dan unicity distance.
5.Mengevaluasi potensi serangan brute force pada kriptosistem sederhana.

---

## 2. Dasar Teori
Cipher klasik adalah metode penyandian pesan yang digunakan sebelum era komputer modern, dengan cara mengganti atau menggeser huruf berdasarkan aturan tertentu. Contohnya adalah Caesar Cipher, di mana setiap huruf pada pesan asli digeser beberapa langkah ke kanan dalam alfabet, misalnya huruf H menjadi K jika digeser tiga langkah. Cipher klasik umumnya bekerja dengan huruf A sampai Z dan mudah dihitung secara manual, tetapi tingkat keamanannya rendah karena pola perubahannya mudah dikenali.Dalam cipher klasik digunakan konsep modular aritmetika, yaitu cara berhitung berdasarkan sisa pembagian. Karena alfabet berjumlah 26 huruf, maka perhitungan biasanya menggunakan modulo 26. Modular aritmetika memungkinkan pergeseran huruf tetap berjalan meskipun sudah melewati huruf Z, sehingga kembali lagi ke A. Misalnya, huruf Z yang digeser satu langkah akan menjadi A karena hasil perhitungannya dibagi dengan 26 dan diambil sisanya.

Selain Caesar Cipher, terdapat juga substitution cipher, yaitu metode penyandian dengan mengganti setiap huruf dengan huruf lain secara tetap tetapi tidak berurutan. Walaupun terlihat lebih rumit, cipher ini masih memiliki kelemahan karena pola kemunculan huruf dalam bahasa tetap terlihat, sehingga dapat dipecahkan dengan analisis frekuensi huruf.Konsep entropy dalam kriptografi digunakan untuk mengukur tingkat ketidakpastian atau keacakan dari sebuah kunci. Semakin besar entropy, semakin sulit kunci tersebut ditebak. Sebaliknya, jika entropy kecil, maka kunci lebih mudah diprediksi. Cipher klasik umumnya memiliki entropy yang rendah karena jumlah kemungkinan kuncinya terbatas.

Unicity distance berkaitan erat dengan entropy dan menunjukkan jumlah minimum ciphertext yang dibutuhkan oleh penyerang untuk dapat menentukan kunci secara unik. Pada cipher dengan entropy rendah seperti Caesar Cipher, unicity distance sangat pendek, sehingga hanya diperlukan sedikit ciphertext untuk memecahkan kuncinya. Inilah alasan mengapa cipher klasik dianggap tidak aman dan sudah tidak digunakan dalam sistem kriptografi modern.


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

![Hasil Eksekusi](screenshots/kriptow.png)


---

## 7. Jawaban Pertanyaan
1.Nilai entropy menunjukkan seberapa sulit kunci ditebak. Semakin besar entropy, semakin banyak kemungkinan kunci yang harus dicoba oleh penyerang, sehingga kunci semakin kuat. Kunci dengan entropy rendah (misalnya pendek atau pola mudah ditebak) cepat ditemukan, sedangkan kunci dengan entropy tinggi membutuhkan usaha dan waktu yang jauh lebih besar untuk ditebak.
2.Unicity distance penting karena menunjukkan berapa banyak ciphertext yang dibutuhkan penyerang untuk bisa menentukan kunci secara pasti. Jika unicity distance kecil, maka dengan sedikit data saja kunci sudah bisa ditemukan, sehingga cipher tidak aman. Cipher yang baik memiliki unicity distance besar, artinya penyerang membutuhkan sangat banyak ciphertext sebelum bisa memecahkan kunci.
3.Brute force tetap menjadi ancaman karena keamanan tidak hanya bergantung pada algoritma, tetapi juga pada kunci. Jika kunci terlalu pendek, mudah ditebak, atau dihasilkan secara tidak acak, brute force bisa berhasil meskipun algoritmanya kuat. Selain itu, peningkatan kemampuan komputasi dan penggunaan GPU atau sistem paralel membuat proses mencoba semua kemungkinan kunci menjadi semakin cepat.
---

## 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )


---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Nurita Ahadhini <Ahadininurita31@gmail.com>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
