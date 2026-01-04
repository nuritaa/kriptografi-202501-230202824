# Laporan Praktikum Kriptografi
Minggu ke-: 5
Topik: cipher klasik
Nama: nurita ahadhini
NIM: 230202824
Kelas: 5IKRA  

---

## 1. Tujuan
1.Menerapkan algoritma Caesar Cipher untuk enkripsi dan dekripsi teks.
2.Menerapkan algoritma Vigenère Cipher dengan variasi kunci.
3.Mengimplementasikan algoritma transposisi sederhana.
4.Menjelaskan kelemahan algoritma kriptografi klasik.

---

## 2. Dasar Teori
Caesar Cipher adalah metode penyandian paling sederhana yang bekerja dengan cara menggeser setiap huruf pada pesan asli sejauh beberapa langkah dalam alfabet. Misalnya, huruf A digeser tiga langkah menjadi D. Cara ini mudah dipahami dan digunakan, tetapi sangat tidak aman karena jumlah kuncinya sedikit dan polanya mudah ditebak, sehingga bisa dipecahkan dengan cepat menggunakan brute force.

Vigenère Cipher merupakan pengembangan dari Caesar Cipher yang menggunakan sebuah kata kunci. Setiap huruf pada pesan dienkripsi dengan pergeseran yang berbeda-beda sesuai huruf pada kunci, sehingga hasil sandinya terlihat lebih acak dibanding Caesar. Meskipun lebih kuat, Vigenère tetap bisa dipecahkan jika penyerang mendapatkan cukup banyak ciphertext, terutama karena pola kunci akan berulang.

Cipher Transposisi adalah metode penyandian yang tidak mengubah huruf, tetapi hanya mengubah urutan huruf dalam pesan berdasarkan pola atau kunci tertentu. Karena huruf aslinya tetap sama, frekuensi huruf tidak berubah, sehingga cipher ini masih bisa dianalisis dan dipecahkan. Transposisi biasanya dianggap lebih aman jika dikombinasikan dengan metode substitusi.


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
def caesar_encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char
    return result

def caesar_decrypt(ciphertext, key):
    return caesar_encrypt(ciphertext, -key)

# Contoh uji
msg = "CLASSIC CIPHER"
key = 3
enc = caesar_encrypt(msg, key)
dec = caesar_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)
def vigenere_encrypt(plaintext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in plaintext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base + shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

def vigenere_decrypt(ciphertext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in ciphertext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base - shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

# Contoh uji
msg = "KRIPTOGRAFI"
key = "KEY"
enc = vigenere_encrypt(msg, key)
dec = vigenere_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)
def transpose_encrypt(plaintext, key=5):
    ciphertext = [''] * key
    for col in range(key):
        pointer = col
        while pointer < len(plaintext):
            ciphertext[col] += plaintext[pointer]
            pointer += key
    return ''.join(ciphertext)

def transpose_decrypt(ciphertext, key=5):
    num_of_cols = int(len(ciphertext) / key + 0.9999)
    num_of_rows = key
    num_of_shaded_boxes = (num_of_cols * num_of_rows) - len(ciphertext)
    plaintext = [''] * num_of_cols
    col = 0
    row = 0
    for symbol in ciphertext:
        plaintext[col] += symbol
        col += 1
        if (col == num_of_cols) or (col == num_of_cols - 1 and row >= num_of_rows - num_of_shaded_boxes):
            col = 0
            row += 1
    return ''.join(plaintext)

# Contoh uji
msg = "TRANSPOSITIONCIPHER"
enc = transpose_encrypt(msg, key=5)
dec = transpose_decrypt(enc, key=5)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)

---

## 6. Hasil dan Pembahasan


![Hasil Eksekusi](screenshots/kriptoweek5.png)


---

## 7. Jawaban Pertanyaan
1. Caesar Cipher memiliki kelemahan utama pada jumlah kunci yang sangat sedikit, sehingga mudah dipecahkan dengan brute force hanya dengan mencoba semua kemungkinan pergeseran. Selain itu, pola pergeseran yang tetap membuat hasil sandinya mudah dikenali. Vigenère Cipher memang lebih kuat karena menggunakan kata kunci, tetapi tetap memiliki kelemahan karena pola kunci yang berulang. Jika penyerang memperoleh ciphertext yang cukup panjang, panjang kunci dapat ditebak dan pesan bisa dipecahkan dengan analisis statistik.
2. Cipher klasik umumnya bekerja pada level huruf dan tidak menyembunyikan pola statistik bahasa. Huruf yang sering muncul dalam bahasa asli tetap sering muncul pada ciphertext, hanya dalam bentuk yang berbeda. Akibatnya, penyerang dapat membandingkan frekuensi huruf pada ciphertext dengan frekuensi huruf pada bahasa yang digunakan, sehingga struktur pesan dan kunci bisa ditebak.
3. Cipher substitusi memiliki kelebihan karena mengubah identitas huruf, sehingga pesan tidak langsung terbaca. Namun, kelemahannya adalah pola frekuensi huruf masih terlihat, sehingga dapat dipecahkan dengan analisis frekuensi. Cipher transposisi sebaliknya, tidak mengubah huruf tetapi hanya mengubah urutan, sehingga frekuensi huruf tetap sama persis seperti plaintext dan mudah dianalisis. Substitusi lebih baik dalam menyamarkan isi pesan, sedangkan transposisi lebih baik dalam menyamarkan struktur, dan keduanya akan lebih aman jika dikombinasikan.
---

## 8. Kesimpulan
Dari hasil program terlihat bahwa cipher transposisi berhasil mengenkripsi dan mendekripsi pesan dengan benar, di mana plaintext dapat dikembalikan lagi secara utuh setelah proses dekripsi. Ciphertext yang dihasilkan hanya mengalami perubahan urutan huruf, bukan perubahan huruf itu sendiri. Hal ini menunjukkan bahwa cipher transposisi mampu menyamarkan pesan, tetapi masih memiliki kelemahan karena pola huruf aslinya tetap ada, sehingga keamanannya masih terbatas dan tidak cukup kuat jika digunakan tanpa dikombinasikan dengan metode lain.

---



## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: nurita ahadini <ahadininurita31@gmail.com>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
