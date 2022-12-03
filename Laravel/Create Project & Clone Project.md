# Create Project & Clone Project
## Create Project

Create with composer
````shell
composer create-project laravel/laravel example-app --prefer-dist
````

atau jika ingin custom version

```shell
composer create-project laravel/laravel="8.6.*" appname --prefer-dist
```

> **composer** ~~create-project laravel/laravel example-app~~ : memanggil function composer

> ~~composer~~ **create-project** ~~laravel/laravel example-app~~ : key word untuk membuat project

> ~~composer create-project~~ **laravel/laravel** ~~example-app~~ : mengambil dari packagist dengan Packages dari laravel yang bernama laravel

> ~~composer create-project laravel/laravel~~ **example-app** : nama app yang akan dibuat, diharuskan string

> ~~composer create-project --prefer-dist laravel/laravel:~~**^8.0** ~~blog~~ : yang paling tinggi

> ~~composer create-project --prefer-dist laravel/laravel~~=**"5.1.\*"** ~~blog~~ : custom versi laravel yang ingin diinstal untuk versi laravel yang disupport bisa di lihat di [Packagist](https://packagist.org/packages/laravel/laravel)

> ~~composer create-project~~ **--prefer-dist** ~~laravel/laravel example-app~~ : hanya mendownload file yang dibutuhkan tanpa mengunduh VCS dependencies

## Clone Project

Clone project from github
````shell
git clone [link]
````
Install package yang dibutuhkan
````shell
npm install
````
Buat DB baru dan edit `.env` file  
````
DB_DATABASE=db-name
DB_USERNAME=root
DB_PASSWORD=password
````
Generate key dan migrate DB
````shell
php artsisan key:generate
php artisan migrate
````

