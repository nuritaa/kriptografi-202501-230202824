# Laporan Praktikum Kriptografi
Minggu ke-: 11 
Topik: secret sharing 
Nama: nurita ahadhini  
NIM: 230202824 
Kelas: 5IKRA 

---

## 1. Tujuan
1.Menjelaskan konsep Shamir Secret Sharing (SSS).
2.Melakukan simulasi pembagian rahasia ke beberapa pihak menggunakan skema SSS.
3.Menganalisis keamanan skema distribusi rahasia.


---

## 2. Dasar Teori
Shamir’s Secret Sharing adalah metode untuk membagi sebuah rahasia menjadi beberapa bagian, sehingga rahasia tersebut tidak bisa diketahui oleh satu orang saja. Rahasia asli hanya bisa dipulihkan jika sejumlah bagian minimum (misalnya 3 dari 5 bagian) digabungkan. Jika jumlah bagian yang dikumpulkan kurang dari batas tersebut, rahasia tetap tidak bisa ditebak.

Dengan cara ini, keamanan jadi lebih tinggi karena tidak ada satu pihak yang memegang rahasia sepenuhnya. Shamir’s Secret Sharing sering digunakan untuk menyimpan kunci penting, sistem keamanan, atau data sensitif agar tetap aman meskipun sebagian bagian bocor atau hilang.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan

1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.

---

## 5. Source Code
from secrets import randbelow

P = 208351617316091241234326746312124448251235562226470491514186331217050270460481

def split_secret(secret, k, n):
    secret = int.from_bytes(secret.encode(), 'big')
    coeffs = [secret] + [randbelow(P) for _ in range(k - 1)]
    shares = []
    for i in range(1, n + 1):
        y = sum(coeffs[j] * pow(i, j, P) for j in range(k)) % P
        shares.append((i, y))
    return shares

def recover_secret(shares):
    secret = 0
    for j, (xj, yj) in enumerate(shares):
        prod = 1
        for m, (xm, _) in enumerate(shares):
            if m != j:
                prod *= xm * pow(xm - xj, -1, P)
                prod %= P
        secret += yj * prod
        secret %= P
    return secret

secret = "KriptografiUPB2025"
shares = split_secret(secret, 3, 5)
print("Shares:", shares)

recovered = recover_secret(shares[:3])
print("Recovered secret:", recovered.to_bytes((recovered.bit_length()+7)//8,'big').decode())


---

## 6. Hasil dan Pembahasan


![Hasil Eksekusi](screenshots/kriptoweek11.png)


---

## 7. Jawaban Pertanyaan
1. SSS lebih aman karena satu bagian kunci tidak dapat mengungkapkan rahasia, berbeda dengan salinan kunci langsung yang bocor jika satu salinan diketahui.
2. Threshold menentukan jumlah minimum share yang diperlukan untuk merekonstruksi rahasia; jika kurang dari k, rahasia tidak bisa diperoleh.
3. SSS digunakan untuk menyimpan kunci master server perusahaan agar tidak dapat diakses oleh satu orang saja dan tetap aman jika sebagian pihak tidak tersedia.
---

## 8. Kesimpulan
Berdasarkan hasil pengujian, sistem berhasil membagi sebuah rahasia menjadi lima bagian (shares) dengan ambang batas tiga bagian menggunakan metode Shamir Secret Sharing. Proses rekonstruksi rahasia menunjukkan bahwa rahasia asli dapat dikembalikan secara utuh hanya dengan menggunakan tiga shares, sesuai dengan prinsip dasar algoritma Shamir Secret Sharing. Hal ini membuktikan bahwa implementasi algoritma berjalan dengan benar.

---



## 10. Commit Log

Author: Nurita ahadhini <ahadininurita31@gmail.com>
Date:   2025-09-20

    week11-secret-sharing
```
