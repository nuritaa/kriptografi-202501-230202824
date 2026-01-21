# Laporan Praktikum Kriptografi
Minggu ke-: 13  
Topik: tinychain  
Nama: nurita ahdhini 
NIM: 230202824
Kelas: 5IKRA  

---

## 1. Tujuan
Menjelaskan peran hash function dalam blockchain.
Melakukan simulasi sederhana Proof of Work (PoW).
Menganalisis keamanan cryptocurrency berbasis kriptografi.

---

## 2. Dasar Teori
Pembelajaran TinyChain bertujuan untuk memperkenalkan konsep dasar teknologi blockchain dalam skala sederhana. Peserta mempelajari bagaimana data dicatat dalam bentuk blok, dihubungkan secara berantai, serta dijaga keamanannya menggunakan mekanisme kriptografi. Melalui TinyChain, peserta dapat memahami prinsip transparansi, integritas data, dan desentralisasi secara praktis dan mudah dipahami.

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
import hashlib
import time

class Block:
    def __init__(self, index, previous_hash, data, timestamp=None):
        self.index = index
        self.timestamp = timestamp or time.time()
        self.data = data
        self.previous_hash = previous_hash
        self.nonce = 0
        self.hash = self.calculate_hash()

    def calculate_hash(self):
        value = str(self.index) + str(self.timestamp) + str(self.data) + str(self.previous_hash) + str(self.nonce)
        return hashlib.sha256(value.encode()).hexdigest()

    def mine_block(self, difficulty):
        while self.hash[:difficulty] != "0" * difficulty:
            self.nonce += 1
            self.hash = self.calculate_hash()
        print(f"Block mined: {self.hash}")
        class Blockchain:
    def __init__(self):
        self.chain = [self.create_genesis_block()]
        self.difficulty = 4

    def create_genesis_block(self):
        return Block(0, "0", "Genesis Block")

    def get_latest_block(self):
        return self.chain[-1]

    def add_block(self, new_block):
        new_block.previous_hash = self.get_latest_block().hash
        new_block.mine_block(self.difficulty)
        self.chain.append(new_block)

# Uji coba blockchain
my_chain = Blockchain()
print("Mining block 1...")
my_chain.add_block(Block(1, "", "Transaksi A → B: 10 Coin"))

print("Mining block 2...")
my_chain.add_block(Block(2, "", "Transaksi B → C: 5 Coin"))

---

## 6. Hasil dan Pembahasan


![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)

---

## 7. Jawaban Pertanyaan
1. Fungsi hash sangat penting karena berfungsi untuk menjaga integritas dan keamanan data dalam blockchain. Setiap blok memiliki hash unik yang dihasilkan dari data blok tersebut dan hash blok sebelumnya. Jika data diubah sedikit saja, nilai hash akan berubah drastis sehingga manipulasi data dapat langsung terdeteksi. Selain itu, hash juga digunakan dalam proses penambangan (mining) dan pengikatan antarblok agar rantai blockchain tidak dapat diubah sembarangan.
2. Proof of Work mencegah double spending dengan cara memastikan setiap transaksi divalidasi dan dicatat hanya satu kali dalam blockchain. Untuk menambahkan blok baru, penambang harus menyelesaikan perhitungan kriptografi yang sulit dan memakan waktu. Karena blockchain menggunakan rantai terpanjang (longest chain rule) sebagai versi yang sah, sangat sulit bagi penyerang untuk menggandakan transaksi tanpa menguasai mayoritas kekuatan komputasi jaringan (serangan 51%).
3. Kelemahan utama PoW adalah konsumsi energi yang sangat besar. Proses penambangan membutuhkan daya komputasi tinggi dan berjalan terus-menerus, sehingga boros listrik dan berdampak negatif terhadap lingkungan. Selain itu, PoW cenderung tidak efisien dan mahal, serta berpotensi menyebabkan sentralisasi karena hanya pihak dengan perangkat dan modal besar yang mampu melakukan mining secara efektif.
---

## 8. Kesimpulan
Teknologi blockchain mengandalkan fungsi hash dan mekanisme Proof of Work untuk menjaga keamanan dan keandalan sistem. Fungsi hash memastikan integritas data dan mencegah perubahan informasi secara tidak sah, sedangkan Proof of Work berperan dalam memvalidasi transaksi dan mencegah terjadinya double spending. Namun, meskipun efektif dari sisi keamanan, Proof of Work memiliki kelemahan utama berupa konsumsi energi yang tinggi dan efisiensi yang rendah. Oleh karena itu, diperlukan pengembangan atau alternatif mekanisme konsensus yang lebih ramah energi tanpa mengurangi tingkat keamanan blockchain.

---



## 10. Commit Log

Author: nurita ahdhini <ahadininurita31@gmail.com>
Date:   2025-09-20

    week13-tinychain
```
