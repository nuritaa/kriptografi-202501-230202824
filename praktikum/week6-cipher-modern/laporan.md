# Laporan Praktikum Kriptografi
Minggu ke-: 6
Topik: cipher modern 
Nama: nurita ahadhini
NIM: 230202824
Kelas: 5IKRA

---

## 1. Tujuan
1.Mengimplementasikan algoritma DES untuk blok data sederhana.
2.Menerapkan algoritma AES dengan panjang kunci 128 bit.
3.Menjelaskan proses pembangkitan kunci publik dan privat pada algoritma RSA.

---

## 2. Dasar Teori
DES (Data Encryption Standard) adalah algoritma enkripsi lama yang bekerja dengan satu kunci rahasia untuk mengunci dan membuka pesan. Dulu DES dianggap aman, tetapi sekarang sudah tidak digunakan lagi karena panjang kuncinya pendek, sehingga bisa dibobol dengan brute force dalam waktu relatif cepat.
AES (Advanced Encryption Standard) adalah algoritma enkripsi modern yang juga memakai satu kunci rahasia, tetapi dengan ukuran kunci yang jauh lebih besar. AES cepat, kuat, dan aman, sehingga sampai sekarang dipakai untuk mengamankan data penting seperti file, Wi-Fi, dan transaksi digital.
RSA adalah algoritma kriptografi kunci publik yang menggunakan dua kunci berbeda, yaitu kunci publik untuk mengunci pesan dan kunci privat untuk membukanya. RSA sangat berguna untuk pertukaran kunci dan keamanan komunikasi, tetapi lebih lambat dibanding AES sehingga biasanya digunakan bersama algoritma simetris.
Intinya, DES sudah usang, AES adalah standar keamanan data saat ini, dan RSA berperan penting dalam pengamanan komunikasi dan pertukaran kunci.

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
from Crypto.Cipher import DES
from Crypto.Random import get_random_bytes

key = get_random_bytes(8)  # kunci 64 bit (8 byte)
cipher = DES.new(key, DES.MODE_ECB)

plaintext = b"ABCDEFGH"
ciphertext = cipher.encrypt(plaintext)
print("Ciphertext:", ciphertext)

decipher = DES.new(key, DES.MODE_ECB)
decrypted = decipher.decrypt(ciphertext)
print("Decrypted:", decrypted)
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

key = get_random_bytes(16)  # 128 bit key
cipher = AES.new(key, AES.MODE_EAX)

plaintext = b"Modern Cipher AES Example"
ciphertext, tag = cipher.encrypt_and_digest(plaintext)

print("Ciphertext:", ciphertext)

# Dekripsi
cipher_dec = AES.new(key, AES.MODE_EAX, nonce=cipher.nonce)
decrypted = cipher_dec.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())
from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP

# Generate key pair
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Enkripsi dengan public key
cipher_rsa = PKCS1_OAEP.new(public_key)
plaintext = b"RSA Example"
ciphertext = cipher_rsa.encrypt(plaintext)
print("Ciphertext:", ciphertext)

# Dekripsi dengan private key
decipher_rsa = PKCS1_OAEP.new(private_key)
decrypted = decipher_rsa.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())

---

## 6. Hasil dan Pembahasan

![Hasil Eksekusi](screenshots/kriptoweek6.png)

---

## 7. Jawaban Pertanyaan
1. DES dan AES adalah algoritma simetris, artinya proses enkripsi dan dekripsi menggunakan kunci yang sama. Perbedaannya, DES memiliki kunci yang pendek sehingga keamanannya sudah tidak memadai, sedangkan AES menggunakan kunci yang jauh lebih panjang dan kompleks sehingga sangat aman. RSA berbeda karena merupakan algoritma asimetris, yang menggunakan dua kunci berbeda, yaitu kunci publik dan kunci privat, sehingga cara pengamanan dan tingkat keamanannya juga berbeda.
2. AES lebih banyak digunakan karena jauh lebih aman dan efisien. Panjang kunci AES yang besar membuat serangan brute force menjadi tidak realistis, sementara DES sudah terbukti dapat dipecahkan dengan cepat menggunakan perangkat modern. Selain itu, AES lebih cepat dan cocok untuk berbagai perangkat, dari komputer hingga ponsel, sehingga menjadi standar enkripsi saat ini.
3. RSA disebut algoritma asimetris karena menggunakan sepasang kunci yang berbeda tetapi saling berkaitan, yaitu kunci publik dan kunci privat. Proses pembangkitan kunci RSA dimulai dengan memilih dua bilangan prima besar, kemudian dikalikan untuk menghasilkan bilangan baru yang menjadi dasar kunci publik. Kunci privat dihitung secara matematis dari nilai tersebut dan hanya diketahui oleh pemiliknya. Keamanan RSA bergantung pada sulitnya memfaktorkan bilangan besar, sehingga meskipun kunci publik diketahui, kunci privat tetap aman.
---

## 8. Kesimpulan
Dari hasil percobaan terlihat bahwa algoritma RSA bekerja dengan konsep dua kunci, yaitu kunci publik untuk mengenkripsi pesan dan kunci privat untuk mendekripsinya kembali. Program menunjukkan bahwa pesan asli berhasil dikembalikan setelah proses dekripsi, sehingga membuktikan prinsip dasar kriptografi asimetris. Namun, muncul error ModuleNotFoundError: No module named 'Crypto' yang menunjukkan bahwa library kriptografi belum terpasang di Python, sehingga perlu instalasi modul terlebih dahulu agar program dapat berjalan. Secara konsep, contoh ini menegaskan bahwa RSA aman untuk pertukaran data, tetapi implementasinya bergantung pada konfigurasi dan lingkungan yang benar.


---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Nurita ahadhini <ahadininurita31@gmail.com>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
