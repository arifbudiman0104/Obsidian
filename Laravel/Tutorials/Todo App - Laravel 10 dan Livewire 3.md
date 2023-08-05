---
telegraph_page_url: https://telegra.ph/Todo-App---Laravel-10-dan-Livewire-3-08-05
telegraph_page_path: Todo-App---Laravel-10-dan-Livewire-3-08-05
---
# Create Project Laravel
Pembuatan laravel project saya akan menerangkan menggunakan 2 cara yaitu laragon dan laravel installer.
## Laragon
#### Create Project Laravel
- Buka laragon, Start All

![Laragon](https://github.com/arifbudimanarrosyid/Obsidian/blob/master/Laravel/Tutorials/Assets/Todo%20App%20-%20Laravel%2010%20dan%20Livewire%203/laragon.png)

- Buka Menu > Quick App > Laravel
- Masukkan nama project "todo-livewire-breeze", tunggu sampai selesai
- Buka project laravel yang telah dibuat di Text Editor atau IDE php
#### Install Laravel Breeze
- Buka terminal dan eksekusi code berikut
```bash
composer require
```
- ad
#### Install Livewire 3
### Laravel Installer
#### Create Project Laravel
```bash
laravel new todo-livewire-breeze
```
#### Install Livewire 3
# Setup Database
## Env
#### MySQL/PgSQL
#### SQLite
## Migration
```
php artisan migrate
```

# Setup app layout dan navigation

## App layout
- Buka file `app.blade.php`
- Ubah menjadi seperti code berikut
```php
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="csrf-token" content="{{ csrf_token() }}">

    <title>{{ config('app.name', 'Laravel') }}</title>

    <!-- Fonts -->
    <link rel="preconnect" href="https://fonts.bunny.net">
    <link href="https://fonts.bunny.net/css?family=Inter:400,500,600&display=swap" rel="stylesheet" />

    <!-- Scripts -->
    @vite(['resources/css/app.css'])
    @livewireStyles
    <style>
        [x-cloak] {
            display: none;
        }
    </style>
</head>

<body class="font-sans antialiased">
    <div class="min-h-screen bg-gray-100 dark:bg-gray-900">
        @include('layouts.navigation')

        <!-- Page Heading -->
        @if (isset($header))
            <header class="bg-white dark:bg-gray-800 shadow">
                <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
                    {{ $header }}
                </div>
            </header>
        @endif

        <!-- Page Content -->
        <main>
            {{ $slot }}
        </main>
    </div>
    @livewireScripts
</body>

</html>

```
## Navigation
- Buka file `navigation.blade.php`
- Ubah menjadi seperti code berikut
```html
lorem
```