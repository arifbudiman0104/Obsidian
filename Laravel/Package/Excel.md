# Laravel Excel
![[Excel.png]]

[Laravel Excel Documentation](https://docs.laravel-excel.com/3.1/getting-started/installation.html)

# Installation

For Laravel 8
````shell
composer require maatwebsite/excel
````

Laravel 9
````shell
composer require psr/simple-cache:^2.0 maatwebsite/excel
````

# Publish Config

```shell
php artisan vendor:publish --provider="Maatwebsite\Excel\ExcelServiceProvider" --tag=config
```

This will create a new config file named `config/excel.php`
