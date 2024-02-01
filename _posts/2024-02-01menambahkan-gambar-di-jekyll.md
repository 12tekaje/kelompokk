---
layout: post
title: "menambahkan gambar di jekyll"
date: 20-01-25 13:45:49 +0800
categories: github
---



Persiapkan Proyek Jekyll:
Pastikan proyek Jekyll Anda sudah dibuat dan konfigurasi dasarnya sudah selesai. Jika belum, Anda dapat membuatnya dengan perintah:

bash
Copy code
jekyll new namaproyek
Masuk ke direktori proyek:

bash
Copy code
cd namaproyek
Buat Folder untuk Gambar:
Buat folder di direktori proyek Anda untuk menyimpan gambar. Misalnya, buat folder "images" di dalam direktori "assets":

bash
Copy code
mkdir assets/images
Salin Gambar ke Folder:
Salin atau pindahkan gambar-gambar yang ingin Anda tambahkan ke dalam folder "images".

Edit Halaman atau Posting:
Buka halaman atau posting Markdown tempat Anda ingin menambahkan gambar. Anda dapat menemukan file tersebut di direktori "_posts" untuk posting atau di folder "_pages" untuk halaman.

Gunakan Markup Gambar:
Gunakan markup HTML atau Markdown untuk menyematkan gambar. Contoh:

markdown
Copy code
![Deskripsi Gambar](/assets/images/namafilegambar.jpg)
Pastikan untuk mengganti "Deskripsi Gambar" dengan teks deskripsi yang sesuai dan "namafilegambar.jpg" dengan nama file gambar yang sebenarnya.

Jalankan Jekyll:
Jalankan server Jekyll untuk melihat perubahan:

bash
Copy code
bundle exec jekyll serve
Buka browser dan kunjungi http://localhost:4000 untuk melihat situs Jekyll Anda.
