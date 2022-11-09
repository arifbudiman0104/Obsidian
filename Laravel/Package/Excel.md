---
tags: laravel, export, package
---

# Laravel Excel
![[Excel.png]]

[Laravel Excel Documentation](https://docs.laravel-excel.com/3.1/getting-started/installation.html)

# Installation

```php
composer require maatwebsite/excel
//for laravel <=8

composer require psr/simple-cache:^2.0 maatwebsite/excel
// for laravel 9
```

# Publish Config

```php
php artisan vendor:publish --provider="Maatwebsite\Excel\ExcelServiceProvider" --tag=config
```

This will create a new config file named `config/excel.php`
