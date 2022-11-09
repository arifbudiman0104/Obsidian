# Laravel Breeze

![[Breeze.png]]

Breeze provides a minimal and simple starting point for building a Laravel application with authentication. Styled with Tailwind, Breeze publishes authentication controllers and views to your application that can be easily customized based on your own application's needs.

Laravel Breeze is powered by Blade and Tailwind. If you're looking for a more robust Laravel starter kit that includes two factor authentication, Livewire / Inertia support, and more, check out [Laravel Jetstream](https://jetstream.laravel.com/).

[Laravel Breeze Documentation](https://laravel.com/docs/9.x/starter-kits)

[Laravel Breeze Github](https://github.com/laravel/breeze)

## Install for Vite

```shell
composer require laravel/breeze --dev 
```

## Install for Mix

```shell
composer require laravel/breeze:1.9.4 
```

default use blade

````shell
php artisan breeze:install
````

if want to install with vue or react

````shell
php artisan breeze:install vue
php artisan breeze:install react
````

if want to instal with vue or react use SSR (Server Side Rendering) and SPA (Single Page App)

````shell
php artisan breeze:install vue --ssr
php artisan breeze:install react --ssr
````

## Finishing

````shell
php artisan migrate
npm install
npm run dev 
````


