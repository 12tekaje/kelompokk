---
layout: post
title: "membuat web dinamis dengan node.js,mysql,crud,biodata siswa"
date: 2024-02-05 13:45:49 +0800
categories: github
---


Untuk membuat web dinamis dengan Node.js, MySQL, dan CRUD (Create, Read, Update, Delete) operasi pada biodata siswa, ikuti langkah-langkah berikut:

1. Persiapkan Database MySQL:

Pastikan MySQL sudah terinstal di komputer Anda.

Buat database dan tabel untuk menyimpan biodata siswa. Misalnya:

sql
Copy code
CREATE DATABASE siswa_db;
USE siswa_db;

CREATE TABLE siswa (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nama VARCHAR(255),
    umur INT,
    alamat VARCHAR(255)
);
2.Instal Modul Node.js dan MySQL:
Instal modul express dan mysql:

bash
Copy code
npm install express mysql
3.Buat Server Express:
Buat file app.js dan tambahkan kode untuk menghubungkan Node.js dengan MySQL:

javascript
Copy code
const express = require('express');
const mysql = require('mysql');
const bodyParser = require('body-parser');

const app = express();
const port = 3000;

app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

const db = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'password',
    database: 'siswa_db'
});

db.connect((err) => {
    if (err) {
        console.error('Koneksi ke MySQL gagal: ' + err.stack);
        return;
    }
    console.log('Terhubung ke MySQL dengan ID ' + db.threadId);
});

// Rute untuk menampilkan semua data siswa
app.get('/siswa', (req, res) => {
    const query = 'SELECT * FROM siswa';

    db.query(query, (err, result) => {
        if (err) {
            console.error('Error saat mengambil data siswa: ' + err.stack);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        res.json(result);
    });
});

// Rute untuk menampilkan detail siswa berdasarkan ID
app.get('/siswa/:id', (req, res) => {
    const { id } = req.params;
    const query = 'SELECT * FROM siswa WHERE id = ?';

    db.query(query, [id], (err, result) => {
        if (err) {
            console.error('Error saat mengambil data siswa: ' + err.stack);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        if (result.length === 0) {
            res.status(404).send('Data siswa tidak ditemukan.');
            return;
        }

        res.json(result[0]);
    });
});

// Rute untuk menambahkan data siswa
app.post('/siswa', (req, res) => {
    const { nama, umur, alamat } = req.body;

    const query = 'INSERT INTO siswa (nama, umur, alamat) VALUES (?, ?, ?)';
    db.query(query, [nama, umur, alamat], (err, result) => {
        if (err) {
            console.error('Error saat menambahkan data siswa: ' + err.stack);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        res.send('Data siswa berhasil ditambahkan!');
    });
});

// Rute untuk mengupdate data siswa
app.put('/siswa/:id', (req, res) => {
    const { id } = req.params;
    const { nama, umur, alamat } = req.body;

    const query = 'UPDATE siswa SET nama = ?, umur = ?, alamat = ? WHERE id = ?';
    db.query(query, [nama, umur, alamat, id], (err, result) => {
        if (err) {
            console.error('Error saat mengupdate data siswa: ' + err.stack);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        res.send('Data siswa berhasil diupdate!');
    });
});

// Rute untuk menghapus data siswa
app.delete('/siswa/:id', (req, res) => {
    const { id } = req.params;
    const query = 'DELETE FROM siswa WHERE id = ?';

    db.query(query, [id], (err, result) => {
        if (err) {
            console.error('Error saat menghapus data siswa: ' + err.stack);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        res.send('Data siswa berhasil dihapus!');
    });
});

// Jalankan server
app.listen(port, () => {
    console.log(`Server berjalan di http://localhost:${port}`);
});
4.Jalankan Server:
Jalankan server dengan perintah:

bash
Copy code
node app.js
Buka browser dan uji rute CRUD:

GET: http://localhost:3000/siswa
GET by ID: http://localhost:3000/siswa/1
POST: http://localhost:3000/siswa (gunakan Postman atau tool serupa untuk mengirim data POST)
PUT: http://localhost:3000/siswa/1 (gunakan Postman atau tool serupa untuk mengirim data PUT)
DELETE: http://localhost:3000/siswa/1 (gunakan Postman atau tool serupa untuk mengirim data DELETE)
Dengan langkah-langkah ini, Anda telah membuat aplikasi CRUD sederhana dengan Node.js, Express, dan MySQL untuk mengelola biodata siswa. Pastikan untuk menjaga keamanan aplikasi Anda dan melakukan validasi input untuk mencegah potensi masalah keamanan.






