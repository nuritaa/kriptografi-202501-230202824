Minggu ke-: 2
Topik: crypto system  
Nama: Nurita Ahadhini  
NIM: 230202824 
Kelas: 5IKRA  

---

## 1. Tujuan
Mempelajari prinsip-prinsip matematika yang digunakan dalam sistem kriptografi seperti kunci publik, kunci privat, RSA, AES, dan lain-lain.

## 2. Dasar Teori
Kriptografi berasal dari bahasa Yunani, yaitu “kryptos” (rahasia) dan “graphien” (menulis), yang berarti menulis secara rahasia.
Dalam ilmu komputer, kriptografi adalah teknik untuk mengamankan informasi atau pesan agar tidak dapat dibaca oleh pihak yang tidak berwenang.
Proses dalam kriptografi melibatkan dua langkah utama:
Enkripsi (Encryption): proses mengubah pesan asli (plaintext) menjadi bentuk sandi (ciphertext).
Dekripsi (Decryption): proses mengembalikan ciphertext menjadi plaintext menggunakan kunci tertentu

## 4. source code

# file: praktikum/week2-cryptosystem/src/simple_crypto.py

def encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char
    return result

def decrypt(ciphertext, key):
    result = ""
    for char in ciphertext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift - key) % 26 + shift)
        else:
            result += char
    return result

if __name__ == "__main__":
    message = "<nim><nama>"
    key = 5

    enc = encrypt(message, key)
    dec = decrypt(enc, key)

    print("Plaintext :", message)
    print("Ciphertext:", enc)
    print("Decrypted :", dec)

## 6. Hasil dan Pembahasan

Hasil Eksekusi :


![Hasil Eksekusi](screenshots/kriptooooooooo.png)


## 7. Jawaban Pertanyaan

1. 1. pliantext
   2. chipertext
   3. encryption algorithm
   4. descrypthon algorithm
2. Apa kelebihan dan kelemahan sistem simetris dibandingkan asimetris? Kriptografi simetris menggunakan satu kunci yang sama untuk enkripsi dan dekripsi, sedangkan asimetris menggunakan dua kunci berbeda (publik dan privat).
Sistem simetris memiliki kelebihan yaitu proses enkripsi dan dekripsi yang lebih cepat dan efisien, sehingga cocok untuk mengamankan data dalam jumlah besar. Namun, sistem ini memiliki kelemahan utama pada distribusi kunci, karena kunci yang sama harus dikirim ke penerima dan berisiko disadap oleh pihak ketiga.
Sebaliknya, kriptografi asimetris lebih aman dalam distribusi kunci karena menggunakan pasangan kunci publik dan privat, tetapi prosesnya lebih lambat dan membutuhkan sumber daya lebih besar.
Dengan demikian, sistem simetris unggul dalam kecepatan, sedangkan sistem asimetris unggul dalam keamanan distribusi kunci.
3. Mengapa distribusi kunci menjadi masalah utama dalam kriptografi simetris? Distribusi kunci menjadi masalah utama dalam kriptografi simetris karena pengirim dan penerima harus menggunakan kunci yang sama untuk enkripsi dan dekripsi. Kunci tersebut harus dikirim terlebih dahulu melalui jaringan, sehingga berisiko disadap atau dicuri oleh pihak yang tidak berwenang. Jika kunci bocor, maka keamanan seluruh sistem dapat terancam.

## 8. Klasifikasi simetris & asimetris

Kriptografi merupakan ilmu yang digunakan untuk menjaga keamanan data dengan cara mengubah informasi asli menjadi bentuk yang tidak dapat dibaca oleh orang lain. Berdasarkan cara penggunaan kuncinya, kriptografi dibagi menjadi dua jenis utama, yaitu kriptografi simetris dan kriptografi asimetris.
Pada kriptografi simetris, proses enkripsi dan dekripsi menggunakan satu kunci yang sama. Artinya, pengirim dan penerima pesan harus memiliki kunci rahasia yang identik agar pesan dapat dibuka. Kelebihan dari sistem ini adalah proses enkripsi dan dekripsinya lebih cepat serta efisien, sehingga cocok digunakan untuk mengamankan data dalam jumlah besar. Namun, kelemahannya terletak pada distribusi kunci. Jika kunci dikirim melalui jaringan yang tidak aman dan berhasil disadap, maka seluruh pesan dapat dengan mudah dibaca oleh pihak yang tidak berwenang.
Contoh algoritma yang termasuk dalam kriptografi simetris adalah AES (Advanced Encryption Standard) dan DES (Data Encryption Standard). AES banyak digunakan dalam keamanan jaringan seperti HTTPS, sedangkan DES merupakan algoritma yang lebih lama dan kini jarang dipakai karena keamanannya sudah dianggap lemah.
Sementara itu, kriptografi asimetris menggunakan dua kunci berbeda tetapi saling berpasangan, yaitu kunci publik dan kunci privat. Kunci publik digunakan untuk mengenkripsi pesan dan dapat dibagikan secara bebas, sedangkan kunci privat digunakan untuk mendekripsi pesan dan harus dijaga kerahasiaannya oleh pemilik. Sistem ini jauh lebih aman dalam hal distribusi kunci, karena tidak ada keharusan mengirim kunci rahasia melalui jaringan. Meskipun prosesnya lebih lambat dibandingkan sistem simetris, kriptografi asimetris lebih unggul dalam keamanan dan sering digunakan untuk autentikasi serta tanda tangan digital.
Contoh algoritma kriptografi asimetris antara lain RSA (Rivest-Shamir-Adleman) dan ECC (Elliptic Curve Cryptography). RSA banyak digunakan pada sertifikat keamanan situs web, sedangkan ECC lebih efisien dan cocok untuk perangkat dengan kapasitas terbatas seperti ponsel.
Secara sederhana, perbedaan utama antara kriptografi simetris dan asimetris terletak pada jumlah kunci yang digunakan serta tingkat keamanannya. Kriptografi simetris lebih cepat namun memiliki risiko pada distribusi kunci, sedangkan kriptografi asimetris lebih aman tetapi memerlukan waktu dan sumber daya komputasi yang lebih besar.

