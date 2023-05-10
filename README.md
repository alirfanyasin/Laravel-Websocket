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

Configurasi phuser di file `.env` dengan menggunakan `ID, KEY, SECRET, HOST` sembarang saja, `PORT=6001` dan `SCHEME=http`
```php
PUSHER_APP_ID=testwebsocket
PUSHER_APP_KEY=DNndkshs
PUSHER_APP_SECRET=123
PUSHER_HOST=localhost
PUSHER_PORT=6001
PUSHER_SCHEME=http
PUSHER_APP_CLUSTER=mt1
```

Install Phuser
```
composer require pusher/pusher-php-server 
```

Atur `BROADCAST_DRIVER` di dalam file `.env`
```
BROADCAST_DRIVER=pusher
```
Ini adalah konten default dari file konfigurasi yang akan dipublikasikan sebagai `config/websocket.php`:
```php
'apps' => [
   [
     'id' => env('PUSHER_APP_ID'),
     'name' => env('APP_NAME'),
     'key' => env('PUSHER_APP_KEY'),
     'secret' => env('PUSHER_APP_SECRET'),
     'enable_client_messages' => false,
     'enable_statistics' => true,
   ],
],
```
Ini adalah konten default dari file konfigurasi yang ada di `config/broadcasting.php`
```php
'pusher' => [
       'driver' => 'pusher',
       'key' => env('PUSHER_APP_KEY'),
       'secret' => env('PUSHER_APP_SECRET'),
       'app_id' => env('PUSHER_APP_ID'),
       'options' => [
          'host' => env('PUSHER_HOST') ?: 'api-'.env('PUSHER_APP_CLUSTER', 'mt1').'.pusher.com',
          'port' => env('PUSHER_PORT', 443),
          'scheme' => env('PUSHER_SCHEME', 'https'),
          'encrypted' => true,
          'useTLS' => env('PUSHER_SCHEME', 'https') === 'https',
       ],
      'client_options' => [
      // Guzzle client options: https://docs.guzzlephp.org/en/stable/request-options.html
   ],
],
```

## Debug Websocket
Route default untuk debug websokect `/laravel-websockets`
```
http://127.0.0.1:8000/laravel-websockets
```









