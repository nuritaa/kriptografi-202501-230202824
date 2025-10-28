# Laporan Praktikum Kriptografi
Minggu ke-: 3  
Topik : Modular Math (Aritmetika Modular, GCD, Bilangan Prima, Logaritma Diskrit)
Nama: Nurita Ahadhini
NIM: 230202824 
Kelas: 5IKRA  

---

## 1. Tujuan
Menyelesaikan operasi aritmetika modular. Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor). Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi
---

## 2. Dasar Teori
Dalam kriptografi, Modular Math mencakup konsep aritmetika modular, GCD, bilangan prima, dan logaritma diskrit yang saling berkaitan dalam proses enkripsi. Aritmetika modular adalah sistem perhitungan dengan batas tertentu (modulus) yang menjaga hasil operasi tetap dalam rentang tertentu dan digunakan pada algoritma seperti RSA. GCD (Greatest Common Divisor) membantu memastikan dua bilangan bersifat relatif prima, penting untuk pembentukan kunci kriptografi. Bilangan prima menjadi dasar keamanan karena sulit difaktorkan, sehingga digunakan untuk membangun kunci publik dan privat. Sementara itu, logaritma diskrit berkaitan dengan kesulitan mencari nilai eksponen dalam sistem modular, yang menjadi landasan keamanan pada algoritma seperti Diffie-Hellman dan ElGamal. Keempat konsep ini bersama-sama mendukung keamanan dan efisiensi sistem kriptografi modern.


---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  

---

## 4. Source Code
1. aritmatika modular

 def mod_add(a, b, n): return (a + b) % n
 def mod_sub(a, b, n): return (a - b) % n
 def mod_mul(a, b, n): return (a * b) % n
 def mod_exp(base, exp, n): return pow(base, exp, n)  # eksponensiasi modular

 print("7 + 5 mod 12 =", mod_add(7, 5, 12))
 print("7 * 5 mod 12 =", mod_mul(7, 5, 12))
 print("7^128 mod 13 =", mod_exp(7, 128, 13))

2. GCD & Algoratmika Euclidean

  def gcd(a, b):
     while b != 0:
         a, b = b, a % b
     return a

 print("gcd(54, 24) =", gcd(54, 24))

 3. Extended Euclidean Algorithm

  def egcd(a, b):
if a == 0:
    return b, 0, 1
g, x1, y1 = egcd(b % a, a)
return g, y1 - (b // a) * x1, x1

def modinv(a, n):
    g, x, _ = egcd(a, n)
    if g != 1:
        return None
    return x % n

print("Invers 3 mod 11 =", modinv(3, 11))  # hasil: 4

4. Logaritma Diskrit

   def discrete_log(a, b, n):
     for x in range(n):
         if pow(a, x, n) == b:
             return x
     return None

 print("3^x ≡ 4 (mod 7), x =", discrete_log(3, 4, 7))  # hasil: 4
 
---

## 5. Hasil dan Pembahasan

### **Hasil dan Pembahasan**

Pada praktikum ini dilakukan beberapa operasi dasar kriptografi menggunakan bahasa Python, yaitu perhitungan **modular**, **pangkat modular**, **GCD (Greatest Common Divisor)**, **invers modular**, serta **logaritma diskrit**.

1. **Operasi Modular**
   Dari hasil program terlihat contoh seperti `7 + 5 mod 12 = 0` dan `7 * 5 mod 12 = 11`. Ini menunjukkan bagaimana operasi penjumlahan dan perkalian dilakukan dalam sistem modular, di mana hasil selalu dibatasi oleh nilai modulus (dalam hal ini 12). Operasi semacam ini menjadi dasar dalam perhitungan kunci kriptografi agar hasil tetap dalam rentang tertentu.

2. **Perpangkatan Modular**
   Perhitungan `7^128 mod 13 = 3` menunjukkan bahwa meskipun pangkatnya besar, hasil akhirnya tetap kecil karena dibatasi oleh modulus. Operasi perpangkatan modular ini sangat penting dalam algoritma seperti **RSA** dan **Diffie-Hellman**, karena memungkinkan enkripsi dengan bilangan besar tanpa menyebabkan overflow.

3. **GCD (Greatest Common Divisor)**
   Nilai `gcd(54, 24) = 6` menunjukkan bahwa bilangan 54 dan 24 memiliki faktor persekutuan terbesar 6. Konsep ini penting dalam menentukan apakah dua bilangan bersifat **relatif prima**, yang menjadi syarat untuk menghasilkan kunci valid dalam sistem kriptografi.

4. **Invers Modular**
   Hasil `Invers 3 mod 11 = 4` menunjukkan bahwa 4 adalah invers dari 3 dalam modulus 11, karena (3 × 4 ≡ 1 \pmod{11}). Invers modular digunakan untuk mencari kunci dekripsi dalam sistem kriptografi simetris dan asimetris.

5. **Logaritma Diskrit**
   Hasil akhir `3^x ≡ 4 (mod 7), x = 4` menunjukkan bahwa nilai x yang memenuhi persamaan tersebut adalah 4. Ini berarti (3^4 \equiv 4 \pmod{7}). Proses mencari nilai x ini disebut **masalah logaritma diskrit**, yang sulit diselesaikan untuk bilangan besar dan menjadi dasar keamanan pada algoritma **Diffie-Hellman** serta **ElGamal**.

Secara keseluruhan, hasil eksekusi program menunjukkan bahwa operasi-operasi matematika dasar seperti modular, GCD, dan logaritma diskrit tidak hanya penting dalam teori, tetapi juga menjadi inti dari sistem keamanan kriptografi. Melalui percobaan ini, dapat dipahami bagaimana konsep matematika sederhana dapat membentuk dasar enkripsi yang menjaga kerahasiaan data di dunia digital.




---

### **Hasil dan Pembahasan**

Dari hasil praktikum yang dilakukan, dapat dipahami bahwa konsep **Modular Math** memiliki peran penting dalam sistem kriptografi. Saat melakukan operasi aritmetika modular, seperti (17 \mod 5 = 2), terlihat bahwa hasil perhitungan selalu dibatasi oleh nilai modulus. Hal ini menunjukkan bagaimana sistem modular menjaga hasil tetap stabil meskipun operasi dilakukan dengan bilangan besar — prinsip yang juga digunakan dalam proses enkripsi data.

Pada bagian **GCD**, perhitungan dengan metode Euclidean seperti GCD(48, 18) = 6 membuktikan cara menentukan bilangan yang relatif prima. Konsep ini penting karena dalam pembentukan kunci kriptografi, bilangan yang digunakan harus tidak memiliki faktor bersama agar sistem enkripsi lebih aman.

Sementara itu, **bilangan prima** terbukti menjadi pondasi utama dalam kriptografi modern. Bilangan prima besar sulit untuk difaktorkan, sehingga digunakan sebagai dasar dalam algoritma pembentukan kunci publik dan privat. Semakin besar bilangan primanya, semakin tinggi pula tingkat keamanannya.

Kemudian pada **logaritma diskrit**, percobaan menunjukkan bahwa mencari nilai eksponen dalam sistem modular sangat sulit, terutama untuk bilangan besar. Kesulitan inilah yang dimanfaatkan dalam algoritma seperti **Diffie-Hellman** dan **ElGamal**, yang mengandalkan prinsip bahwa operasi eksponensial mudah dilakukan, tetapi kebalikannya hampir mustahil dihitung tanpa kunci khusus.

Secara keseluruhan, praktikum ini memperlihatkan bagaimana **Modular Math** menjadi dasar dari banyak mekanisme keamanan dalam kriptografi. Dengan memahami operasi sederhana seperti modulus, GCD, bilangan prima, dan logaritma diskrit, kita dapat melihat bagaimana matematika berperan langsung dalam melindungi data digital di dunia nyata.



---

## 7. Jawaban Pertanyaan


### **1. Peran Aritmetika Modular dalam Kriptografi Modern**

Aritmetika modular menjadi dasar utama dalam hampir semua algoritma kriptografi modern. Sistem ini memastikan semua operasi matematika seperti penjumlahan, perkalian, dan perpangkatan tetap berada dalam batas nilai tertentu (*modulus*).
Dengan sifat ini, aritmetika modular memungkinkan pengolahan bilangan yang sangat besar tanpa menyebabkan hasilnya tak terbatas. Dalam kriptografi, hal ini digunakan untuk menjaga kerahasiaan kunci dan hasil enkripsi agar tetap aman, efisien, dan tidak mudah ditebak.
Contoh penerapannya ada pada algoritma **RSA**, **Diffie-Hellman**, dan **ElGamal**, yang semuanya menggunakan operasi modular dalam proses pembentukan dan penggunaan kunci.

---

### **2. Mengapa Invers Modular Penting dalam Algoritma Kunci Publik (seperti RSA)**

Invers modular digunakan untuk menemukan **kunci privat (d)** yang menjadi pasangan dari **kunci publik (e)** dalam algoritma RSA.
Dalam RSA, kunci privat dihitung dengan rumus:
[
d \equiv e^{-1} \pmod{\varphi(n)}
]
Artinya, (d) adalah invers dari (e) terhadap (\varphi(n)).
Tanpa invers modular, proses dekripsi tidak bisa dilakukan, karena kita tidak dapat “membalikkan” hasil enkripsi. Jadi, invers modular memastikan pesan yang telah dienkripsi dengan kunci publik hanya bisa dibuka oleh pemilik kunci privat.

---

### **3. Tantangan Utama dalam Menyelesaikan Logaritma Diskrit untuk Modulus Besar**

Masalah logaritma diskrit sangat sulit diselesaikan ketika modulusnya besar (misalnya ratusan atau ribuan bit). Tidak ada algoritma efisien yang dapat menghitungnya dengan cepat — satu-satunya cara yang diketahui hanyalah mencoba setiap kemungkinan secara brute force, yang membutuhkan waktu sangat lama.
Kesulitan inilah yang menjadi **pondasi keamanan** algoritma kriptografi seperti **Diffie-Hellman** dan **ElGamal**. Dengan modulus besar, bahkan komputer modern pun membutuhkan waktu bertahun-tahun untuk menemukan solusinya, sehingga sistem tetap aman dari serangan.


---

## 8. Kesimpulan
Dari hasil praktikum yang dilakukan, dapat dipahami bahwa konsep **Modular Math** memiliki peran penting dalam sistem kriptografi. Saat melakukan operasi aritmetika modular, seperti (17 \mod 5 = 2), terlihat bahwa hasil perhitungan selalu dibatasi oleh nilai modulus. Hal ini menunjukkan bagaimana sistem modular menjaga hasil tetap stabil meskipun operasi dilakukan dengan bilangan besar — prinsip yang juga digunakan dalam proses enkripsi data.

Pada bagian **GCD**, perhitungan dengan metode Euclidean seperti GCD(48, 18) = 6 membuktikan cara menentukan bilangan yang relatif prima. Konsep ini penting karena dalam pembentukan kunci kriptografi, bilangan yang digunakan harus tidak memiliki faktor bersama agar sistem enkripsi lebih aman.

Sementara itu, **bilangan prima** terbukti menjadi pondasi utama dalam kriptografi modern. Bilangan prima besar sulit untuk difaktorkan, sehingga digunakan sebagai dasar dalam algoritma pembentukan kunci publik dan privat. Semakin besar bilangan primanya, semakin tinggi pula tingkat keamanannya.

Kemudian pada **logaritma diskrit**, percobaan menunjukkan bahwa mencari nilai eksponen dalam sistem modular sangat sulit, terutama untuk bilangan besar. Kesulitan inilah yang dimanfaatkan dalam algoritma seperti **Diffie-Hellman** dan **ElGamal**, yang mengandalkan prinsip bahwa operasi eksponensial mudah dilakukan, tetapi kebalikannya hampir mustahil dihitung tanpa kunci khusus.

Secara keseluruhan, praktikum ini memperlihatkan bagaimana **Modular Math** menjadi dasar dari banyak mekanisme keamanan dalam kriptografi. Dengan memahami operasi sederhana seperti modulus, GCD, bilangan prima, dan logaritma diskrit, kita dapat melihat bagaimana matematika berperan langsung dalam melindungi data digital di dunia nyata.

---


## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Nurita Ahadhini <ahadininurita31@ggmail.com>
Date:   2025-09-20

    week3-modmath: implementasi dan laporan )
```
