# Laporan Praktikum Kriptografi
Minggu ke-: 10  
Topik: PKI
Nama: nurita ahadhini 
NIM: 230202824 
Kelas: 5IKRA

---

## 1. Tujuan
1.Membuat sertifikat digital sederhana.
2.Menjelaskan peran Certificate Authority (CA) dalam sistem PKI.
3.Mengevaluasi fungsi PKI dalam komunikasi aman (contoh: HTTPS, TLS).

---

## 2. Dasar Teori
(Ringkas teori relevan (cukup 2–3 paragraf).  
Contoh: definisi cipher klasik, konsep modular aritmetika, dll.  )

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
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
from cryptography import x509
from cryptography.x509.oid import NameOID
from cryptography.hazmat.primitives import hashes, serialization
from cryptography.hazmat.primitives.asymmetric import rsa
from datetime import datetime, timedelta

# Generate key pair
key = rsa.generate_private_key(public_exponent=65537, key_size=2048)

# Buat subject & issuer (CA sederhana = self-signed)
subject = issuer = x509.Name([
    x509.NameAttribute(NameOID.COUNTRY_NAME, u"ID"),
    x509.NameAttribute(NameOID.ORGANIZATION_NAME, u"UPB Kriptografi"),
    x509.NameAttribute(NameOID.COMMON_NAME, u"example.com"),
])

# Buat sertifikat
cert = (
    x509.CertificateBuilder()
    .subject_name(subject)
    .issuer_name(issuer)
    .public_key(key.public_key())
    .serial_number(x509.random_serial_number())
    .not_valid_before(datetime.utcnow())
    .not_valid_after(datetime.utcnow() + timedelta(days=365))
    .sign(key, hashes.SHA256())
)

# Simpan sertifikat
with open("cert.pem", "wb") as f:
    f.write(cert.public_bytes(serialization.Encoding.PEM))

print("Sertifikat digital berhasil dibuat: cert.pem")


---

## 6. Hasil dan Pembahasan

![Hasil Eksekusi](screenshots/kriptoweek10.png)

---

## 7. Jawaban Pertanyaan
1. Certificate Authority (CA) berfungsi sebagai pihak tepercaya yang memverifikasi identitas suatu entitas (orang, organisasi, atau server) dan kemudian menerbitkan sertifikat digital. Sertifikat ini menghubungkan identitas tersebut dengan kunci publik, sehingga pihak lain dapat yakin bahwa kunci publik yang digunakan benar-benar milik entitas yang sah.
2. Self-signed certificate hanya ditandatangani oleh pemiliknya sendiri, sehingga tidak ada pihak ketiga yang menjamin keasliannya. Dalam sistem produksi, hal ini berbahaya karena pengguna atau klien tidak dapat memastikan apakah sertifikat tersebut benar atau palsu. Akibatnya, self-signed certificate rentan terhadap serangan peniruan identitas dan biasanya hanya cocok untuk uji coba atau lingkungan lokal, bukan untuk sistem yang digunakan publik.
3. Public Key Infrastructure (PKI) mencegah serangan Man-in-the-Middle (MITM) dengan cara memastikan bahwa kunci publik server telah diverifikasi oleh CA tepercaya. Saat klien terhubung melalui TLS/HTTPS, sertifikat server diperiksa keabsahannya melalui rantai kepercayaan CA. Jika sertifikat valid, klien yakin bahwa ia terhubung ke server yang benar, sehingga penyerang tidak bisa menyisipkan diri dan mengganti kunci publik tanpa terdeteksi.
---

## 8. Kesimpulan
Program tersebut menunjukkan proses pembuatan sertifikat digital menggunakan library cryptography di Python. Program membangkitkan pasangan kunci, menyusun informasi identitas sertifikat (subject dan issuer), menentukan masa berlaku, lalu menandatangani sertifikat dengan private key sehingga menghasilkan sertifikat bertipe self-signed certificate. Sertifikat kemudian disimpan dalam format PEM dan dapat digunakan untuk kebutuhan pengujian keamanan, pembelajaran PKI, atau simulasi TLS. Program ini menegaskan konsep dasar Public Key Infrastructure (PKI), khususnya peran tanda tangan digital dalam menjamin keaslian dan integritas sertifikat.


---



## 10. Commit Log

Author: Nurita ahadhini <ahadininurita31@gmail.com>
Date:   2025-09-20

   week10-pki
```
