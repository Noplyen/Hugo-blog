---
title: "Bagaimana Cara Mengkoneksikan Lebih Dari 1 Database Di Codeigniter 4"
date: 12 jan 2024
draft: false
slug: "how-to-connect-multiple-database-at-codeigniter-4"
description: "How To Connect Multiple Database At Codeigniter 4"
thumbnail: "codeigniter"
author:
    email:
    name: "Standartorz-Poggly"
    image:
---

### Pendahuluan

Terkadang kita ingin memisahkan table pada kasus aplikasi kita pada database
berbeda untuk lebih terorganisir, contohnya kita memiliki aplikasi e-commerce 
terdapat data user dan produk, akan menjadi sulit dan tidak terorganisir 
ketika table user seperti privilege, role, user bergabung dengan produk seperti
produk category, produk detail bahkan user order. 

### Langkah - langkah
1. Pastikan anda telah membuat database beserta table yang diperlukan.
2. Buat konfigurasi koneksi ke database, anda boleh menggunakan `.env` 
atau pada `app\Config\Database.php`.

_contoh dengan `.env`_

```php
     database.default.hostname = localhost
     database.default.database = user_db
     database.default.username = root
     database.default.password = root
     database.default.DBDriver = MySQLi
     database.default.DBPrefix =
     database.default.port = 3306

     database.product.hostname = localhost
     database.product.database = product_db
     database.product.username = root
     database.product.password = root
     database.product.DBDriver = MySQLi
     database.product.DBPrefix =
     database.product.port = 3306
```


_contoh dengan  `app\Config\Database.php`_

```php
 public array $default = [
        'DSN'          => '',
        'hostname'     => 'localhost',
        'username'     => 'root',
        'password'     => 'root',
        'database'     => 'user_db',
        'DBDriver'     => 'MySQLi',
        'DBPrefix'     => '',
        'pConnect'     => false,
        'DBDebug'      => true,
        'charset'      => 'utf8mb4',
        'DBCollat'     => 'utf8mb4_general_ci',
        'swapPre'      => '',
        'encrypt'      => false,
        'compress'     => false,
        'strictOn'     => false,
        'failover'     => [],
        'port'         => 3306,
        'numberNative' => false,
        'dateFormat'   => [
            'date'     => 'Y-m-d',
            'datetime' => 'Y-m-d H:i:s',
            'time'     => 'H:i:s',
        ],
    ];

    public array $product = [
        'DSN'          => '',
        'hostname'     => 'localhost',
        'username'     => 'root',
        'password'     => 'root',
        'database'     => 'product_db',
        'DBDriver'     => 'MySQLi',
        'DBPrefix'     => '',
        'pConnect'     => false,
        'DBDebug'      => true,
        'charset'      => 'utf8mb4',
        'DBCollat'     => 'utf8mb4_general_ci',
        'swapPre'      => '',
        'encrypt'      => false,
        'compress'     => false,
        'strictOn'     => false,
        'failover'     => [],
        'port'         => 3306,
        'numberNative' => false,
        'dateFormat'   => [
            'date'     => 'Y-m-d',
            'datetime' => 'Y-m-d H:i:s',
            'time'     => 'H:i:s',
        ],
    ];
```


{{< callout >}}

jika anda menggunakan konfigurasi `.env` anda masih
perlu menuliskan array **tanpa** konfigurasi/value di array tersebut.
Pastikan nama array sama dengan nama konfigurasi pada `.env`, contoh
jika `.env` `database.product.hostname` maka buat array dengan nama `$product`
kosongkan isi `username`,`password` dan `database` pada array tersebut.

{{< /callout >}}

3. Selanjutnya jika anda menggunakan class model anda perlu menambahkan `protected $DBGroup = "nama_konfigurasi";`
atau jika anda menggunakan query builder anda perlu menambah nama group konfigurasi koneksi `\Config\Database::connect("product");`.

_contoh :_

```php
class UserModel extends Model 
{
    protected $table            = 'users';
    protected $primaryKey       = 'id';
    protected $allowedFields    =
        [
            "id",
            "email","password",
        ];
    protected $DBGroup = "default";
```

### Penjelasan
1. Penggunaan `.env`  sebagai konfigurasi sebenarnya akan di load
oleh codeigniter dan value akan di passing ke array pada `app\Config\Database.php`.
