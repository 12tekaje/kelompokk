---
layout: post
title:  "instal jekyll"
date:   2024-01-23 13:45:49 +0800
categories: jekyll update
---
Instalasi Jekyll di Windows melibatkan beberapa langkah. Berikut adalah panduan langkah demi langkah untuk menginstal Jekyll di sistem operasi Windows:

Langkah 1: Persiapkan Prasyarat

Sebelum menginstal Jekyll, pastikan Anda telah menginstal prasyarat berikut:

Ruby: Jekyll membutuhkan Ruby untuk berjalan. Anda dapat mengunduh RubyInstaller dari rubyinstaller.org dan ikuti panduan instalasinya.

DevKit: Jekyll membutuhkan DevKit agar dapat menginstal beberapa gem yang diperlukan. Unduh DevKit dari rubyinstaller.org dan ikuti panduan instalasinya.

Langkah 2: Instal Jekyll

Setelah memasang Ruby dan DevKit, lanjutkan dengan menginstal Jekyll:

Buka Command Prompt: Buka Command Prompt atau PowerShell dengan hak akses administrator.

Instal Bundler: Gunakan perintah berikut untuk menginstal bundler, yang membantu mengelola dependensi proyek Ruby.

bash
Copy code
gem install bundler
Instal Jekyll: Navigasikan ke direktori proyek Anda atau buat direktori baru untuk proyek Jekyll, lalu buat file Gemfile dengan teks berikut:

ruby
Copy code
source "https://rubygems.org"

gem "jekyll", "~> 3.9.0"
Simpan file Gemfile, dan kembali ke Command Prompt. Jalankan perintah berikut:

bash
Copy code
bundle install
Perintah ini akan menginstal Jekyll dan dependensinya.

Langkah 3: Buat dan Jalankan Situs Jekyll

Setelah menginstal Jekyll, buat proyek Jekyll baru dan jalankan server pengembangan. Pindah ke direktori proyek Anda dan ketik perintah berikut:

bash
Copy code
jekyll new myblog
cd myblog
bundle exec jekyll serve
Buka browser dan akses http://localhost:4000 untuk melihat situs Jekyll Anda. Server pengembangan akan menyajikan perubahan secara otomatis saat Anda menyunting konten.

Itulah langkah-langkah umum untuk menginstal Jekyll di Windows. Pastikan untuk membaca dokumentasi resmi Jekyll untuk informasi lebih lanjut: Jekyll Official Documentation.





