# MKV ke Teks

Static web app untuk mengekstrak subtitle teks yang tertanam di file MKV langsung di browser.

## Fitur
- Pilih / drag-and-drop banyak MKV sekaligus
- Proses berurutan (batch queue)
- Pilih subtitle stream ke-1, ke-2, atau ke-3
- Output ASS, SRT, atau TXT
- Tidak mengunggah video ke server
- Responsive untuk desktop, tablet, dan mobile

## Cara kerja
Aplikasi memakai FFmpeg WebAssembly di browser. Setiap MKV dimasukkan ke filesystem virtual FFmpeg, subtitle stream dipilih, lalu diekstrak sebagai ASS. ASS dapat dikonversi menjadi SRT atau TXT di browser.

## Batasan penting
- Versi ini ditujukan untuk subtitle berbasis teks seperti ASS/SSA/SRT/WebVTT yang dapat dikonversi FFmpeg.
- PGS/VobSub adalah subtitle berbasis gambar dan membutuhkan OCR, jadi belum didukung sebagai teks.
- FFmpeg.wasm perlu membaca file MKV ke memori virtual. MKV yang sangat besar dapat gagal di browser/perangkat dengan RAM terbatas. Arsitektur streaming/chunked demuxer akan diperlukan untuk versi yang lebih tahan terhadap file multi-GB.
- Download batch saat ini memicu satu download per file, belum ZIP.

## Jalankan
Karena menggunakan ES modules, jalankan melalui static hosting atau local HTTP server. Repo dapat dipasang langsung ke GitHub Pages/Cloudflare Pages tanpa proses build.
