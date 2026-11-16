# Shift Report Electrical P14

Aplikasi web satu halaman (HTML) untuk mengisi Shift Report Electrical Department P14
dan menghasilkan laporan siap unduh (PNG, JPG, atau PDF), lengkap dengan lampiran
Electric (UPS & DC Panel) atau Instrument (Analyzer Preheater / Coal Mill).

## Fitur
- Form isian ramah smartphone dengan pratinjau laporan langsung
- Lampiran opsional: Electric atau Instrument, menyatu dalam satu halaman dengan laporan
- Sorotan kuning otomatis untuk kata "FU" / "follow up" dan "Temuan Masalah Lain"
- Unduh PNG, JPG, atau PDF
- Data tersimpan otomatis di browser (localStorage); bisa disimpan/dibuka lewat file .json

## Cara pakai
Buka `index.html` di browser, atau akses lewat GitHub Pages.

## Catatan
Halaman memuat pustaka html2canvas dan jsPDF dari cdnjs.cloudflare.com, serta font
IBM Plex Sans dari Google Fonts, sehingga memerlukan koneksi internet.

## Unggah otomatis ke Supabase Storage
Setiap kali tombol **Unduh File** dipakai, file hasil unduhan juga diunggah ke Supabase Storage
di folder sesuai tanggal laporan, contoh: `shift-reports/02-11-2026/Shift B Report-02112026-153012.pdf`.

### Persiapan di Supabase
1. Buat bucket (Storage → New bucket), misalnya `shift-reports`. Disarankan **Private**.
2. Jalankan SQL berikut di SQL Editor agar halaman boleh mengunggah (tanpa boleh membaca/menghapus):

```sql
create policy "anon upload shift reports"
on storage.objects for insert to anon
with check (bucket_id = 'shift-reports');
```

3. Ambil **Project URL** dan **anon public key** di Project Settings → API.

### Konfigurasi
Unggah otomatis selalu aktif dan tidak dapat dimatikan dari aplikasi. Nilai koneksi diatur di `index.html`
pada variabel `SBD` (`url`, `key` publishable/anon, `bucket`).

Catatan keamanan: anon key bersifat publik. Siapa pun yang membuka halaman dapat mengunggah ke bucket,
jadi jangan beri policy select/update/delete untuk `anon`. Gunakan service role key **jangan pernah** di halaman ini.
