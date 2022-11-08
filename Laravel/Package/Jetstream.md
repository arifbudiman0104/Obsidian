#laravel #auth #package 
# Laravel Jetstream
![[Jetstream.png]]

Laravel Jetstream is a beautifully designed application starter kit for Laravel and provides the perfect starting point for your next Laravel application. Jetstream provides the implementation for your application's login, registration, email verification, two-factor authentication, session management, API via [Laravel Sanctum](https://github.com/laravel/sanctum), and optional team management features.

[Laravel Jetstream Documentation](https://jetstream.laravel.com/2.x/introduction.html)
[Laravel Jetstream Github](https://github.com/laravel/jetstream)

```php
composer require laravel/jetstream
```

## Jetstream with [[Livewire]]

```php
php artisan jetstream:install livewire

php artisan jetstream:install livewire --teams
// with teams
```

### Publish Livewire Blade Component

```php
php artisan vendor:publish --tag=jetstream-views
```

`resources/views/vendor/jetstream/components/application-logo.blade.php`

`resources/views/vendor/jetstream/components/authentication-card-logo.blade.php`

`resources/views/vendor/jetstream/components/application-mark.blade.php`

## Jetstream with Inertia

```php
php artisan jetstream:install inertia

php artisan jetstream:install inertia --teams
// with teams

php artisan jetstream:install inertia --ssr
// with SSR support
```

### Customizing Component

`resources/js/Components/AuthenticationCardLogo.vue`

`resources/js/Components/ApplicationLogo.vue`

`resources/js/Components/ApplicationMark.vue`

```php
npm run build
```

## Finalizing The Installation

```php
npm install

npm run build

php artisan migrate
```
