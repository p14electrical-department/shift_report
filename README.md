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
