# 🏦 E-Form Deposito Berjangka — BPR Gracia Mandiri

Form elektronik pembukaan rekening deposito berjangka yang dapat diakses calon nasabah langsung dari browser HP/laptop.

## 🔗 Link Form (setelah deploy)
```
https://NAMA_AKUN_GITHUB.github.io/bpr-gracia-deposito/
```

---

## 🚀 Cara Upload ke GitHub Pages (Langkah demi Langkah)

### LANGKAH 1 — Buat Akun GitHub
1. Buka https://github.com dan klik **Sign Up**
2. Daftar dengan email dan buat username (contoh: `bprgracia`)

### LANGKAH 2 — Buat Repository Baru
1. Setelah login, klik tombol **+** (pojok kanan atas) → **New repository**
2. Isi nama: `bpr-gracia-deposito`
3. Pilih **Public**
4. Klik **Create repository**

### LANGKAH 3 — Upload File
1. Di halaman repository, klik **uploading an existing file**
2. Seret/drop file `index.html` ke area upload
3. Klik **Commit changes**

### LANGKAH 4 — Aktifkan GitHub Pages
1. Klik tab **Settings** di repository
2. Di menu kiri, klik **Pages**
3. Di bagian **Branch**, pilih `main` → folder `/ (root)`
4. Klik **Save**
5. Tunggu 1–2 menit, lalu link form akan muncul:
   ```
   https://NAMA_AKUN.github.io/bpr-gracia-deposito/
   ```

---

## 📧 Cara Aktifkan Email Otomatis ke BPR

Setelah form diisi nasabah, PDF otomatis terkirim ke `bpr_gracia_mandiri@yahoo.com`.  
Gunakan layanan **EmailJS** (gratis, 200 email/bulan).

### LANGKAH 1 — Daftar EmailJS
1. Buka https://www.emailjs.com → **Sign Up Free**
2. Verifikasi email Anda

### LANGKAH 2 — Tambah Email Service
1. Di dashboard EmailJS → **Email Services** → **Add New Service**
2. Pilih **Yahoo Mail**
3. Masuk dengan akun Yahoo BPR: `bpr_gracia_mandiri@yahoo.com`
4. Klik **Connect Account**
5. Catat **Service ID** (contoh: `service_abc123`)

### LANGKAH 3 — Buat Email Template
1. Di dashboard → **Email Templates** → **Create New Template**
2. Isi template seperti ini:

**To Email:** `{{to_email}}`  
**Subject:** `{{subject}}`  
**Body:**
```
Yth. {{to_name}},

{{isi_form}}

---
Nomor Referensi : {{ref_number}}
Tanggal         : {{tanggal}}
Nasabah         : {{nama_nasabah}}
NIK             : {{nik}}
Nominal         : {{nominal}}
Jangka          : {{jangka}}

Email ini dikirim otomatis dari E-Form Deposito BPR Gracia Mandiri.
```

3. Klik **Save** — catat **Template ID** (contoh: `template_xyz789`)

### LANGKAH 4 — Ambil Public Key
1. Di dashboard → **Account** → **General**
2. Catat **Public Key** (contoh: `user_AbCdEfGhIj`)

### LANGKAH 5 — Edit file index.html
Buka `index.html` dengan Notepad, cari bagian ini (sekitar baris 650):

```javascript
const EJS = {
  publicKey : 'STPEarXVzifQiNP3V',    // ← Ganti dengan Public Key Anda
  serviceId : 'service_bprgracia',     // ← Ganti dengan Service ID Anda
  templateId: 'template_deposito_bpr' // ← Ganti dengan Template ID Anda
};
```

Ganti ketiga nilai tersebut, simpan, lalu **upload ulang** ke GitHub.

---

## 📱 Cara Bagikan ke Calon Nasabah

Setelah deploy, bagikan link ini:
```
https://NAMA_AKUN.github.io/bpr-gracia-deposito/
```

Bisa dibagikan via:
- 💬 **WhatsApp** — kirim link langsung
- 📘 **Facebook** — posting di halaman BPR
- 📧 **Email** — sertakan dalam email promosi
- 🖨️ **Cetak QR Code** — generate di https://qr.io lalu cetak di brosur

---

## ✅ Fitur Lengkap

| Fitur | Keterangan |
|-------|-----------|
| 📋 5-step form | Data produk, data diri, alamat, profil risiko, verifikasi |
| 🔐 Verifikasi OTP | Kode 6 digit dikirim ke email nasabah |
| 📷 Upload KTP | Foto KTP + selfie memegang KTP |
| ✍️ Tanda Tangan Digital | Canvas touchscreen, sah per UU ITE No.11/2008 |
| 📄 Generate PDF | PDF profesional format A4 dengan semua data terisi |
| 📧 Email Otomatis | PDF dan data terkirim ke bpr_gracia_mandiri@yahoo.com |
| 📱 Mobile Friendly | Tampilan optimal di HP Android & iPhone |
| ⚖️ Legal | Sesuai POJK 23/2019, UU ITE, PP 71/2019 |

---

## ⚖️ Dasar Hukum Keabsahan

| Regulasi | Ketentuan |
|----------|-----------|
| UU ITE No. 11/2008 | Tanda tangan elektronik diakui sah |
| PP No. 71/2019 | Penyelenggara sistem elektronik |
| POJK 23/POJK.03/2019 | KYC / CDD lembaga keuangan |
| POJK 12/POJK.01/2017 | APU/PPT perbankan |
| UU PDP No. 27/2022 | Perlindungan data pribadi nasabah |

---

## 📞 Bantuan

Jika ada kendala teknis, hubungi pengembang atau cek dokumentasi EmailJS di:  
https://www.emailjs.com/docs/
