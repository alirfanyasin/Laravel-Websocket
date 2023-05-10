# Laravel Websocket
WebSocket adalah teknologi canggih untuk membuat koneksi antara klien dan server (browser dan server) dan memungkinkan komunikasi antara mereka secara real-time. Perbedaan utama dengan WebSocket adalah memungkinkan Anda menerima data tanpa harus mengirim permintaan terpisah, seperti yang terjadi di HTTP. Setelah koneksi terjalin, data akan datang dengan sendirinya tanpa perlu mengirim request. Ini adalah keuntungan menggunakan protokol WebSocket dalam obrolan atau laporan stok, di mana Anda perlu menerima informasi yang terus diperbarui. Protokol dapat menerima dan mengirim informasi secara bersamaan, memungkinkan komunikasi dua arah dupleks penuh, yang menghasilkan pertukaran informasi yang lebih cepat.

Sedangkan laravel adalah sebuah framework yang digunakan untuk menjalankan websocket tersebut.

## Install Laravel
```
composer create-project laravel/laravel example-app
```

## Install Websocket
Dokumentasi lengkapnya silahkan klik link [ini](https://beyondco.de/docs/laravel-websockets/getting-started/introduction)
```
composer require beyondcode/laravel-websockets
```
Atau
```
composer require beyondcode/laravel-websockets --with-all-dependencies
```
Opsi ini akan mengizinkan composer untuk meng-upgrade, meng-downgrade, atau menghapus paket lain yang mungkin bertentangan dengan dependensi yang ada.

### Install Package
Install Service Provider Migration
```
php artisan vendor:publish --provider="BeyondCode\LaravelWebSockets\WebSocketsServiceProvider" --tag="migrations"
```
Buat database di PhpMyAdmin, Konfigurasi file `.env` untuk mengubah nama databsenya
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nama_database
DB_USERNAME=root
DB_PASSWORD=
```
Jalankan migrasi
```
php artisan migrate
```

Install Service Provider Config
```
php artisan vendor:publish --provider="BeyondCode\LaravelWebSockets\WebSocketsServiceProvider" --tag="config"
```





