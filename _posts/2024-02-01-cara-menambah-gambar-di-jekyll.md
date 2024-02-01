---
layout: post
title: "menambah gambar di jekyll"
date: 2024-02-01 13:45:49 +0800
categories: github
---


Untuk menambahkan gambar di situs web Jekyll, Anda dapat mengikuti langkah-langkah berikut:

Tempatkan Gambar di Direktori yang Tepat:
Pastikan gambar yang ingin Anda tambahkan berada di direktori yang sesuai di dalam struktur proyek Jekyll Anda. Direktori umum untuk menyimpan gambar adalah assets/images/.

Gunakan Markup HTML atau Markdown:

HTML: Jika Anda menggunakan markup HTML, gunakan tag <img> dengan atribut src untuk menunjukkan lokasi gambar. Contohnya:

html
Copy code
<img src="/assets/images/nama-gambar.jpg" alt="Deskripsi Gambar">
Markdown: Jika Anda lebih suka menggunakan Markdown, Anda dapat menggunakan sintaks berikut:

markdown
Copy code
![Alt Text](/assets/images/nama-gambar.jpg)
Berikan Deskripsi Alternatif (Alt Text):
Penting untuk menyediakan deskripsi alternatif untuk gambar dengan menggunakan atribut alt. Deskripsi ini membantu aksesibilitas dan SEO. Gantilah "Deskripsi Gambar" atau "Alt Text" dengan deskripsi yang relevan.

Periksa Tautan Gambar:
Pastikan bahwa tautan gambar mengacu pada lokasi yang benar dan bahwa gambar tersebut dapat diakses dari halaman Jekyll Anda.

Jalankan Jekyll secara Lokal (Opsional):
Sebelum menerapkan perubahan ke situs web yang di-host, mungkin Anda ingin menjalankan Jekyll secara lokal untuk memastikan bahwa gambar ditampilkan dengan benar. Gunakan perintah bundle exec jekyll serve dan buka situs di browser lokal Anda.

Perbarui dan Terapkan Perubahan:
Setelah memastikan bahwa gambar ditambahkan dengan benar, perbarui proyek Jekyll Anda dan terapkan perubahan ke server atau platform hosting Anda.

