---
layout: post
title: "membuat web dinamis dengan node.js,sqllite,crud,biodata siswa"
date: 2024-02-05 13:45:49 +0800
categories: github
---



Untuk membuat web dinamis dengan Node.js, SQLite, dan CRUD operasi pada biodata siswa, Anda dapat mengikuti langkah-langkah berikut:

Instal Modul Node.js dan SQLite:
Instal modul express dan sqlite3:

bash
Copy code
npm install express sqlite3
Buat Server Express:
Buat file app.js dan tambahkan kode untuk menghubungkan Node.js dengan SQLite:

javascript
Copy code
const express = require('express');
const sqlite3 = require('sqlite3').verbose();
const bodyParser = require('body-parser');

const app = express();
const port = 3000;

app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

const db = new sqlite3.Database('siswa.db', (err) => {
    if (err) {
        console.error('Koneksi ke SQLite gagal: ' + err.message);
        return;
    }
    console.log('Terhubung ke SQLite.');
});

// Buat tabel siswa jika belum ada
db.run(`
    CREATE TABLE IF NOT EXISTS siswa (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        nama TEXT,
        umur INTEGER,
        alamat TEXT
    )
`);

// Rute untuk menampilkan semua data siswa
app.get('/siswa', (req, res) => {
    const query = 'SELECT * FROM siswa';

    db.all(query, (err, rows) => {
        if (err) {
            console.error('Error saat mengambil data siswa: ' + err.message);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        res.json(rows);
    });
});

// Rute untuk menampilkan detail siswa berdasarkan ID
app.get('/siswa/:id', (req, res) => {
    const { id } = req.params;
    const query = 'SELECT * FROM siswa WHERE id = ?';

    db.get(query, [id], (err, row) => {
        if (err) {
            console.error('Error saat mengambil data siswa: ' + err.message);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        if (!row) {
            res.status(404).send('Data siswa tidak ditemukan.');
            return;
        }

        res.json(row);
    });
});

// Rute untuk menambahkan data siswa
app.post('/siswa', (req, res) => {
    const { nama, umur, alamat } = req.body;

    const query = 'INSERT INTO siswa (nama, umur, alamat) VALUES (?, ?, ?)';
    db.run(query, [nama, umur, alamat], function (err) {
        if (err) {
            console.error('Error saat menambahkan data siswa: ' + err.message);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        res.send(`Data siswa berhasil ditambahkan dengan ID: ${this.lastID}`);
    });
});

// Rute untuk mengupdate data siswa
app.put('/siswa/:id', (req, res) => {
    const { id } = req.params;
    const { nama, umur, alamat } = req.body;

    const query = 'UPDATE siswa SET nama = ?, umur = ?, alamat = ? WHERE id = ?';
    db.run(query, [nama, umur, alamat, id], function (err) {
        if (err) {
            console.error('Error saat mengupdate data siswa: ' + err.message);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        if (this.changes === 0) {
            res.status(404).send('Data siswa tidak ditemukan.');
            return;
        }

        res.send('Data siswa berhasil diupdate!');
    });
});

// Rute untuk menghapus data siswa
app.delete('/siswa/:id', (req, res) => {
    const { id } = req.params;
    const query = 'DELETE FROM siswa WHERE id = ?';

    db.run(query, [id], function (err) {
        if (err) {
            console.error('Error saat menghapus data siswa: ' + err.message);
            res.status(500).send('Terjadi kesalahan pada server.');
            return;
        }

        if (this.changes === 0) {
            res.status(404).send('Data siswa tidak ditemukan.');
            return;
        }

        res.send('Data siswa berhasil dihapus!');
    });
});

// Jalankan server
app.listen(port, () => {
    console.log(`Server berjalan di http://localhost:${port}`);
});
Jalankan Server:
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
Dengan langkah-langkah ini, Anda telah membuat aplikasi CRUD sederhana dengan Node.js, Express, dan SQLite untuk mengelola biodata siswa. Pastikan untuk menjaga keamanan aplikasi Anda dan melakukan validasi input untuk mencegah potensi masalah keamanan.