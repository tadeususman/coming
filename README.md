# Coming soon: giakediri.org

Halaman kejutan HUT GIA Kediri ke-41 (Minggu, 18 Oktober 2026, 07.00 WIB). Satu halaman statis tanpa build, tanpa database.

Berkas: `index.html`, `logo-gia.png`, `sora-latin.woff2`.

## Cara melihat

```bash
python3 -m http.server 8099
```

Buka http://localhost:8099

## Kendali pembawa acara

Buka alamat dengan kode: `https://giakediri.org/?panggung41`. Di pojok kanan bawah muncul dua tombol:

- **▶** (atau Enter / spasi): hitungan 3-2-1, lalu ucapan selamat dan nyala bara.
- **↺** (atau tombol R): kembali ke hitung mundur (untuk gladi).

Tanpa kode itu tombol tidak tampil. Uji tanpa menunggu tanggal: `?panggung41&uji=selesai` (hitung mundur sudah nol) atau `?panggung41&uji=menit` (satu menit lagi).

## Pasang di server (nginx)

```nginx
server {
    listen 80;
    server_name giakediri.org www.giakediri.org;
    root /var/www/coming;   # folder hasil git clone repo ini
    index index.html;
    location / { try_files $uri /index.html; }
}
```

Lalu `sudo nginx -t && sudo systemctl reload nginx` dan `sudo certbot --nginx -d giakediri.org -d www.giakediri.org`.
