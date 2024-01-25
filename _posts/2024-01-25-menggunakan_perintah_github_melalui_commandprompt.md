---
layout: post
title: "menggunakan_perintah_github_melalui_commandprompt"
date: 20-01-25 13:45:49 +0800
categories: github
---
1. Instalasi Git:
Pastikan Git sudah terinstal di komputer Anda. Jika belum, Anda dapat mengunduhnya dari situs resmi Git. Ikuti langkah-langkah instalasi yang disediakan.


2. Buka Command Prompt atau Terminal:

Pada Windows, tekan Win + R, ketik cmd, dan tekan Enter.
Pada Linux atau macOS, buka Terminal.


3. Periksa Instalasi Git:
Pastikan Git sudah diinstal dengan menjalankan perintah berikut:

bash
git --version


4. Konfigurasi Nama dan Email:
Sebelum menggunakan Git, Anda perlu mengkonfigurasi nama pengguna dan alamat email. Lakukan ini dengan perintah berikut:

bash
git config --global user.name "Nama Anda"
git config --global user.email "email@anda.com"


5. Clone Repository:
Untuk mengunduh salinan repositori dari GitHub ke komputer Anda, gunakan perintah git clone. Gantilah URL dengan URL repositori yang ingin Anda klona.

bash
git clone https://github.com/nama-akun/nama-repositori.git


6. Buat Perubahan:
Pindah ke direktori repositori lokal dengan menggunakan perintah cd. Buat dan simpan perubahan pada file Anda.

bash
cd nama-repositori


7. Status Perubahan:
Untuk melihat status perubahan yang belum dikommit, gunakan perintah berikut:

bash
git status


8. Tambahkan Perubahan ke Staging:
Gunakan perintah git add untuk menambahkan perubahan ke staging area.

bash
git add nama-file


9. Kommit Perubahan:
Setelah menambahkan perubahan ke staging area, gunakan perintah git commit untuk membuat komit.

bash
git commit -m "Pesan komit"


10. Push ke GitHub:
Untuk mengirim perubahan Anda ke repositori GitHub, gunakan perintah git push.

bash
git push origin nama-branch


11. Pull dari GitHub:
Jika ada perubahan di repositori GitHub, Anda dapat mengunduhnya ke komputer Anda menggunakan perintah git pull.

bash
git pull origin nama-branch



