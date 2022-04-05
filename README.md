<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Laravel 9 Rest API CRUD Example Tutorial

Konfigurasi dasar saat menggunakan passport

### Step 1: Download Laravel 9 App

`composer create-project --prefer-dist laravel/laravel nama_projek`

### Step 2: Configure Database with App

Buka file **.env** dan ubah bagian DB_CONNECTION menjadi sqlite hapus, alternatif agar tidak perlu menjalankan mysql dan buat database di dalamnya.

```
DB_CONNECTION=sqlite 
DB_HOST=127.0.0.1 
DB_PORT=3306
```

Buat file **database.sqlite** di dalam folder **database**

### Step 3: Install Passport Auth

`composer require laravel/passport`

Buka file **config/app.php** dan tambahkan **PassportServiceProvider::class** di providers

```php
'providers' =>[
    ...
    Laravel\Passport\PassportServiceProvider::class,
],
```

Generate kunci enkripsi passport

`php artisan passport:install`

### Step 4: Passport Configuration

Tambahkan **HasApiTokens** di model **App/Models/User.php**

```php

use Laravel\Passport\HasApiTokens;

class User extends Authenticatable {

    use HasFactory, Notifiable, HasApiTokens;

    ...
}
```

Daftarkan passport routes di **App/Providers/AuthServiceProvider.php**

```php
use Laravel\Passport\Passport;

class AuthServiceProvider extends ServiceProvider {

    ...

    public function boot()
    {
        $this->registerPolicies();
        Passport::routes();
    }
}
```

Tambahkan skrip di bawah di file **config/auth.php**

```php
'guards' => [
    ..., 
        'api' => [ 
            'driver' => 'passport', 
            'provider' => 'users', 
        ],
],
```

### Step 5: Create Product Table and Model
### Step 6: Create Auth and CRUD APIs Route
### Step 7: Create Passport Auth and CRUD Controller
### Step 8: Test Laravel 9 REST CRUD API with Passport Auth in Postman