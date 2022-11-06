#laravel #laravelauth 
# Laravel Frontend Preset

# Tailwind CSS

```php
composer require laravel-frontend-presets/tailwindcss --dev 
```

## Preset without Auth

```php
php artisan ui tailwindcss
```

## Preset with Auth

```php
php artisan ui tailwindcss --auth

npm install && npm run dev

php artisan migrate

php artisan serve
```

---

# TALL (Tailwind, Alpine.js,Laravel, Livewire)

-   [Tailwind CSS](https://tailwindcss.com/)
-   [Alpine.js](https://alpinejs.dev/)
-   [Laravel](https://laravel.com/)
-   [Livewire](https://laravel-livewire.com/)

## Preset without Auth

```php
composer require livewire/livewire laravel-frontend-presets/tall

php artisan ui tall

npm install

npm run dev
```

## Preset withAuth

```php
composer require livewire/livewire laravel-frontend-presets/tall

php artisan ui tall --auth

npm install

npm run dev
```

## Pagination

```php
use Illuminate\Pagination\Paginator;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    public function boot()
    {
        Paginator::defaultView('pagination::default');

        Paginator::defaultSimpleView('pagination::simple-default');
    }
}
```