# 📧 PANDUAN SETUP EMAIL OTOMATIS
## E-Form Deposito BPR Gracia Mandiri

---

## Apa yang perlu disiapkan?

Agar setiap kali nasabah mengisi form, datanya **otomatis terkirim ke email BPR**, 
kita menggunakan layanan gratis **EmailJS**.

- ✅ Gratis hingga 200 email/bulan
- ✅ Tidak perlu server atau coding backend
- ✅ Setup hanya sekali, langsung jalan selamanya

---

## LANGKAH 1 — Daftar di EmailJS

1. Buka: **https://www.emailjs.com**
2. Klik **Sign Up** (pojok kanan atas)
3. Isi email dan password → klik **Create Account**
4. Cek email Anda → klik link verifikasi

---

## LANGKAH 2 — Hubungkan Akun Gmail BPR

1. Login ke dashboard EmailJS
2. Di menu kiri, klik **Email Services**
3. Klik **Add New Service**
4. Pilih **Gmail**
5. Klik **Connect Account**
6. Login dengan: `bgraciamandiri@gmail.com` + password Gmail BPR
7. Klik **Allow** untuk izinkan akses
8. Beri nama service: `BPR Gracia Mandiri`
9. Klik **Create Service**
10. ⚠️ **Catat Service ID** — contoh: `service_abc12345`

> **Catatan:** Pastikan akun Gmail tidak mengaktifkan verifikasi 2 langkah (2FA), 
> atau aktifkan **App Password** di pengaturan Google jika 2FA menyala.

---

## LANGKAH 3 — Buat Template Email

1. Di menu kiri, klik **Email Templates**
2. Klik **Create New Template**
3. Isi bagian-bagian berikut:

### To
```
{{to_email}}
```

### Subject
```
{{subject}}
```

### Body (isi pesan email)
```
Yth. {{to_name}},

Berikut adalah data formulir deposito yang telah diisi dan diverifikasi:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RINGKASAN PENGAJUAN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
No. Referensi : {{ref_number}}
Tanggal       : {{tanggal}}
Nasabah       : {{nama_nasabah}}
NIK           : {{nik}}
Nominal       : {{nominal}}
Jangka Waktu  : {{jangka}}
Instruksi     : {{instruksi}}
Bayar Bunga   : {{bayar_bunga}}
No. HP        : {{hp}}
Email Nasabah : {{email_nas}}
Profil Risiko : {{profil_risiko}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DETAIL LENGKAP FORMULIR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
{{isi_form}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Nasabah telah mengunduh PDF formulir ke perangkatnya.
Form ini dikirim otomatis dari E-Form Elektronik BPR Gracia Mandiri.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

4. Klik **Save**
5. ⚠️ **Catat Template ID** — contoh: `template_xyz98765`

---

## LANGKAH 4 — Ambil Public Key

1. Di menu kiri, klik **Account** → **General**
2. Di bagian **API Keys**
3. ⚠️ **Catat Public Key** — contoh: `AbCdEfGhIjKlMnOp`

---

## LANGKAH 5 — Edit file index.html

1. Buka file `index.html` menggunakan **Notepad** (Windows) atau **TextEdit** (Mac)
2. Tekan **Ctrl+F** (Windows) atau **Cmd+F** (Mac)
3. Cari teks: `const EJS =`
4. Anda akan menemukan bagian seperti ini:

```javascript
const EJS = {
  publicKey : 'STPEarXVzifQiNP3V',
  serviceId : 'service_bprgracia',
  templateId: 'template_deposito_bpr'
};
```

5. **Ganti** ketiga nilai dengan yang Anda catat:

```javascript
const EJS = {
  publicKey : 'AbCdEfGhIjKlMnOp',      // ← Public Key Anda
  serviceId : 'service_abc12345',        // ← Service ID Anda
  templateId: 'template_xyz98765'        // ← Template ID Anda
};
```

6. Simpan file (**Ctrl+S**)

---

## LANGKAH 6 — Upload Ulang ke GitHub

1. Buka repository GitHub Anda
2. Klik file `index.html`
3. Klik ikon **pensil** (Edit)
4. Hapus semua isi lama
5. Copy-paste isi file `index.html` yang sudah diedit
6. Klik **Commit changes**

Atau bisa juga:
1. Klik **Add file** → **Upload files**
2. Upload `index.html` yang baru
3. Klik **Commit changes**

---

## ✅ Test Email

Setelah setup selesai:
1. Buka link form GitHub Pages Anda
2. Isi form sampai selesai
3. Masukkan kode OTP yang dikirim ke email nasabah
4. Cek email `bgraciamandiri@gmail.com` — harusnya ada email masuk

---

## ❓ Troubleshooting

| Masalah | Solusi |
|---------|--------|
| OTP tidak masuk ke email | Cek folder Spam / Junk |
| Email tidak terkirim ke BPR | Pastikan Service ID, Template ID, Public Key benar |
| Gmail menolak koneksi EmailJS | Aktifkan App Password di pengaturan Google Account |
| Tombol "Lanjut" tidak berfungsi | Pastikan semua field wajib sudah diisi |
| Foto KTP tidak bisa diupload | Pastikan ukuran foto < 5MB |
| Tanda tangan tidak muncul di PDF | Coba gambar ulang tanda tangan |

---

## 📞 Bantuan EmailJS

Dokumentasi resmi: https://www.emailjs.com/docs/  
Support: https://www.emailjs.com/contact/

---

*Panduan ini dibuat khusus untuk BPR Gracia Mandiri.*
