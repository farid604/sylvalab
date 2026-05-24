# SylvaLab — Panduan Deployment
**Lab Kehutanan Universitas Sulawesi Barat**

---

## Isi Paket Ini

| File | Keterangan |
|------|-----------|
| `GAS_V8_PASTE_KE_APPSCRIPT.js` | Kode backend terbaru (paste ke Google Apps Script) |
| `login.html` | Halaman login |
| `index.html` | Katalog alat (halaman mahasiswa) |
| `admin.html` | Dashboard admin |

---

## LANGKAH 1 — Update Google Apps Script

1. Buka Google Sheets Anda: https://docs.google.com/spreadsheets/d/1Dhr1UH_x-0ri4qKM4IC_FDVQp8HAZmza1mKiHlNpKA4
2. Klik menu **Ekstensi → Apps Script**
3. **Hapus semua kode lama** di editor
4. Buka file `GAS_V8_PASTE_KE_APPSCRIPT.js`, **copy semua isinya**, dan **paste** ke editor
5. Klik ikon **Simpan** (Ctrl+S)
6. Klik tombol **Terapkan → Kelola Deployment → Edit (ikon pensil) → Versi Baru → Terapkan**
7. URL tidak berubah ✓

---

## LANGKAH 2 — Tambahkan User Pertama (Admin)

Karena tab Users masih kosong, Anda perlu menambahkan user SUPER_ADMIN secara manual dulu:

1. Buka Google Sheets tab **Users**
2. Di baris 2, isi:
   ```
   A: ADMIN001
   B: Nama Anda
   C: SUPER_ADMIN
   D: 0
   E: admin123
   ```
3. Simpan

Setelah ini Anda bisa login ke `admin.html` dengan NIM: `ADMIN001`, Password: `admin123`

---

## LANGKAH 3 — Deploy ke GitHub Pages

### Cara A: Via GitHub Web (Mudah)

1. Buka https://github.com dan login (buat akun jika belum ada)
2. Klik tombol **+ New Repository**
3. Nama repository: `sylvalab` (atau nama lain)
4. Centang **Public**, klik **Create Repository**
5. Klik **uploading an existing file**
6. Upload ke-4 file HTML (login.html, index.html, admin.html) — **jangan upload file .js**
7. Klik **Commit Changes**
8. Buka tab **Settings → Pages → Branch: main → Save**
9. URL Anda akan jadi: `https://[username-github].github.io/sylvalab/login.html`

### Cara B: Domain Kampus

Setelah GitHub Pages aktif, hubungi Pusat Komputer Unsulbar dan minta subdomain:
```
labkehutanan.unsulbar.ac.id → diarahkan ke [username].github.io/sylvalab
```

---

## LANGKAH 4 — Perbaiki URL Foto di Google Sheets

Beberapa URL foto di data Anda bermasalah. Perbaiki di tab Equipments:

| ID | URL Foto yang Direkomendasikan |
|----|-------------------------------|
| ALT-001 (Mikroskop) | https://images.unsplash.com/photo-1576319155264-99536e0be1ee?w=400 |
| ALT-002 (Solder) | https://images.unsplash.com/photo-1518770660439-4636190af475?w=400 |
| ALT-003 (Multimeter) | https://images.unsplash.com/photo-1611532736597-de2d4265fba3?w=400 |
| ALT-004 (Jangka Sorong) | https://images.unsplash.com/photo-1581092918056-0c4c3acd3789?w=400 |
| ALT-005 (Osiloskop) | https://images.unsplash.com/photo-1518770660439-4636190af475?w=400 |

---

## Alur Sistem Setelah Deploy

```
Mahasiswa → login.html → (masuk) → index.html → pilih alat → checkout → PENDING di Sheets
Admin → login.html → (masuk) → admin.html → klik Setujui → DIPINJAM → stok berkurang
Admin → admin.html → klik Terima Alat → DIKEMBALIKAN → stok kembali + Green Score +10 poin
```

---

## Fitur yang Sudah Berfungsi

- ✅ Login dengan NIM + Password (dari tab Users)
- ✅ Katalog alat real-time dari Google Sheets
- ✅ Keranjang peminjaman dengan pilih tanggal
- ✅ Submit permohonan → langsung tulis ke Sheets (PENDING)
- ✅ Dashboard Admin: lihat permohonan PENDING
- ✅ Setujui / Tolak permohonan
- ✅ Proses pengembalian alat
- ✅ CRUD Inventaris Alat (tambah/edit/hapus)
- ✅ Kelola Pengguna (SUPER_ADMIN)
- ✅ Publikasi artikel Jurnal Kanopi
- ✅ Green Score +10 setiap pengembalian
- ✅ Proteksi stok (tidak negatif, tidak melebihi total)
- ✅ Redirect otomatis berdasarkan role (Admin → admin.html, Mahasiswa → index.html)

---

## Teknologi

| Komponen | Teknologi | Biaya |
|---------|-----------|-------|
| Database | Google Sheets | Gratis |
| Backend API | Google Apps Script | Gratis |
| Frontend | HTML + CSS + Vanilla JS | Gratis |
| Hosting | GitHub Pages | Gratis |
| **Total** | | **Rp 0/bulan** |
