#laravel #auth #package 
# Laravel UI
![[UI.png]]

While Laravel does not dictate which JavaScript or CSS pre-processors you use, it does provide a basic starting point using [Bootstrap](https://getbootstrap.com/), [React](https://reactjs.org/), and / or [Vue](https://vuejs.org/) that will be helpful for many applications. By default, Laravel uses [NPM](https://www.npmjs.org/) to install both of these frontend packages.

[Laravel UI Github](https://github.com/laravel/ui)

```php
composer require laravel/ui
```

# Bootstrap, Vue and React

## Without Auth

```php
php artisan ui bootstrap

php artisan ui vue

php artisan ui react
```

## With Auth

```php
php artisan ui bootstrap --auth

php artisan ui vue --auth

php artisan ui react --auth
```

## Finalizing The Installation

```php
npm install

npm run dev
```