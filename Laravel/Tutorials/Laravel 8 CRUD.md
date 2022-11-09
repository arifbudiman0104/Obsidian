---
tags: laravel, tutorial, crud
---
# Laravel 8 CRUD Mahasiswa
![[Laravel 8 CRUD.png]]
Membuat Laravel CRUD Mahasiswa tanpa Auth dan tanpa relasi DB

## Buat project baru

Buat project baru dengan mana project **mahasiswa** dan setup DB pada `.env` sebagai berikut

```php
APP_URL=http://mahasiswa.test/
DB_DATABASE=mahasiswa
DB_USERNAME=root
DB_PASSWORD=                #kosongkan kalau tidak ada password
```

![[laravel8crud1.png]]

## Membuat Model, Migration, Controller dan Factory
Membuat Model dan Migration dengan perintah berikut:
`php artisan make:model Mahasiswa -m` membuat model dan migration
`php artisan make:controller MahasiswaController` membuat controller
`php artisan make:factory MahasiswaFactory` membuat factory
akan ada 4 file baru pada:
`database\migrations\2022_09_20_073456_create_mahasiswas_table.php`
`app\Models\Mahasiswa.php`
`app\Http\Controllers\MahasiswaController.php`
`database\factories\MahasiswaFactory.php`

![[laravel8crud2.png]]

## Edit Migration Mahasiswa
Buka file migration Mahasiswa dan ubah menjadi

```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('mahasiswas', function (Blueprint $table) {
            $table->id();
            $table->string('nim');
            $table->string('nama');
            $table->string('alamat');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('mahasiswas');
    }
};

```

lakukan migration dengan `php artisan migrate` dan pastikan sudah ada tabel baru yaitu **mahasiswa**

## Edit Model Mahasiswa

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Mahasiswa extends Model
{
    use HasFactory;
    protected $fillable = [
        'nim',
        'nama',
        'alamat',
    ];
}
```

## Edit Factory MahasiswaFactory

```php
<?php

namespace Database\Factories;

use Illuminate\Database\Eloquent\Factories\Factory;

/**
 * @extends \Illuminate\Database\Eloquent\Factories\Factory<\App\Models\Mahasiswa>
 */
class MahasiswaFactory extends Factory
{
    /**
     * Define the model's default state.
     *
     * @return array<string, mixed>
     */
    public function definition()
    {
        return [
            'nama' => fake()->name(),
            'nim' => fake()->unique()->numberBetween(20220101000, 20220101999),
            'alamat' => fake()->address(),
        ];
    }
}
```

## Edit DatabaseSeeder

```jsx title="database\seeders\DatabaseSeeder.php"
<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        // \App\Models\User::factory(10)->create();
        // highlight-start
        \App\Models\Mahasiswa::factory(100)->create();
        // highlight-end
        // \App\Models\User::factory()->create([
        //     'name' => 'Test User',
        //     'email' => 'test@example.com',
        // ]);
    }
}

```

lakukan perintah `php artisan db:seed` cek phpMyAdmin maka ada 100 data yang masuk, jika ingin menghapus semua data bisa menggunakan `php artisan migrate:fresh` kalau ingin melakukan hapus data sekaligus membuat data bisa menggunakan `php artisan migrate:fresh --seed`

## Edit Route

```php
<?php

use App\Http\Controllers\MahasiswaController;
use App\Models\Mahasiswa;
use Illuminate\Support\Facades\Route;

/*
|--------------------------------------------------------------------------
| Web Routes
|--------------------------------------------------------------------------
|
| Here is where you can register web routes for your application. These
| routes are loaded by the RouteServiceProvider within a group which
| contains the "web" middleware group. Now create something great!
|
*/

Route::get('/', function () {
    return view('welcome');
});

Route::get('/mahasiswa', [MahasiswaController::class, 'index'])->name('mahasiswa.index'); // View Mahasiswa
Route::get('/mahasiswa/create', [MahasiswaController::class, 'create'])->name('mahasiswa.create'); // Create Mahasiswa
Route::post('/mahasiswa', [MahasiswaController::class, 'store'])->name('mahasiswa.store'); // Create Mahasiswa
Route::get('/mahasiswa/{mahasiswa}/edit', [MahasiswaController::class, 'edit'])->name('mahasiswa.edit'); // Edit Mahasiswa
Route::put('/mahasiswa/{mahasiswa}', [MahasiswaController::class, 'update'])->name('mahasiswa.update'); // Edit Mahasiswa
Route::delete('/mahasiswa/{mahasiswa}delete', [MahasiswaController::class, 'destroy'])->name('mahasiswa.destroy'); // Delete Mahasiswa
```

## Edit Controller MahasiswaController

```php
<?php

namespace App\Http\Controllers;

use App\Models\Mahasiswa;
use Illuminate\Http\Request;

class MahasiswaController extends Controller
{
    // View Mahasiswa
    public function index()
    {
        $mahasiswa = Mahasiswa::orderBy('id', 'desc')->paginate(10);
        return view('mahasiswa.index', compact('mahasiswa'));
    }

    // Create Mahasiswa
    public function create()
    {
        return view('mahasiswa.create');
    }

    public function store(Request $request)
    {
        $request->validate([
            'nama' => 'required',
            'nim' => 'required|max:11',
            'alamat' => 'required',
        ]);

        Mahasiswa::create($request->post());

        return redirect()->route('mahasiswa.index')->with('success', 'Mahasiswa has been created successfully.');
    }

    // Edit Mahasiswa
    public function edit(Mahasiswa $mahasiswa)
    {
        return view('mahasiswa.edit', compact('mahasiswa'));
    }

    public function update(Request $request, Mahasiswa $mahasiswa)
    {
        $request->validate([
            'nama' => 'required',
            'nim' => 'required|max:11',
            'alamat' => 'required',
        ]);

        $mahasiswa->fill($request->post())->save();

        return redirect()->route('mahasiswa.index')->with('success', 'Mahasiswa Has Been updated successfully');
    }

    // Delete Mahasiswa
    public function destroy(Mahasiswa $mahasiswa)
    {
        $mahasiswa->delete();
        return redirect()->route('mahasiswa.index')->with('success', 'Mahasiswa has been deleted successfully');
    }
}


```

## index.blade.php

Membuat index.blade.php di folder view/mahasiswa

```php
</html>
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Laravel CRUD Mahasiswa</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>

<body>
    <div class="container mt-2">
        <div class="row">
            <div class="col-lg-12 margin-tb">
                <div class="pull-left">
                    <h2>Laravel CRUD Mahasiswa</h2>
                </div>
                <div class="pull-right mb-2">
                    <a class="btn btn-success" href="{{ route('mahasiswa.create') }}"> Create Mahasiswa</a>
                </div>
            </div>
        </div>
        @if ($message = Session::get('success'))
        <div class="alert alert-success">
            <p>{{ $message }}</p>
        </div>
        @endif
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Nama</th>
                    <th>NIM</th>
                    <th>Alamat</th>
                    <th width="200px">Action</th>
                </tr>
            </thead>
            <tbody>
                @foreach ($mahasiswa as $data)
                <tr>
                    <td>{{ $data->id }}</td>
                    <td>{{ $data->nama }}</td>
                    <td>{{ $data->nim }}</td>
                    <td>{{ $data->alamat }}</td>
                    <td>
                        <form action="{{ route('mahasiswa.destroy', $data->id) }}" method="Post">
                            <a class="btn btn-primary" href="{{ route('mahasiswa.edit',$data->id) }}">Edit</a>
                            @csrf
                            @method('DELETE')
                            <button type="submit" class="btn btn-danger">Delete</button>
                        </form>
                    </td>
                </tr>
                @endforeach
            </tbody>
        </table>
        {!! $mahasiswa->links() !!}
    </div>
</body>
</html>
```

## create.blade.php

Membuat create.blade.php di folder view/mahasiswa

```php
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Add Mahasiswa</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>

<body>
    <div class="container mt-2">
        <div class="row">
            <div class="col-lg-12 margin-tb">
                <div class="pull-left mb-2">
                    <h2>Add Mahasiswa</h2>
                </div>
                <div class="pull-right">
                    <a class="btn btn-primary" href="{{ route('mahasiswa.index') }}"> Back</a>
                </div>
            </div>
        </div>
        @if(session('status'))
        <div class="alert alert-success mb-1 mt-1">
            {{ session('status') }}
        </div>
        @endif
        <form action="{{ route('mahasiswa.store') }}" method="POST" enctype="multipart/form-data">
            @csrf
            <div class="row">
                <div class="col-xs-12 col-sm-12 col-md-12">
                    <div class="form-group">
                        <strong>Nama</strong>
                        <input type="text" name="nama" class="form-control" placeholder="Nama">
                        @error('nama')
                        <div class="alert alert-danger mt-1 mb-1">{{ $message }}</div>
                        @enderror
                    </div>
                </div>
                <div class="col-xs-12 col-sm-12 col-md-12">
                    <div class="form-group">
                        <strong>NIM</strong>
                        <input type="number" name="nim" class="form-control" placeholder="NIM">
                        @error('nim')
                        <div class="alert alert-danger mt-1 mb-1">{{ $message }}</div>
                        @enderror
                    </div>
                </div>
                <div class="col-xs-12 col-sm-12 col-md-12">
                    <div class="form-group">
                        <strong>Alamat</strong>
                        <input type="text" name="alamat" class="form-control" placeholder="Alamat">
                        @error('alamat')
                        <div class="alert alert-danger mt-1 mb-1">{{ $message }}</div>
                        @enderror
                    </div>
                </div>
                <button type="submit" class="btn btn-primary ml-3">Submit</button>
            </div>
        </form>
    </div>
</body>
</html>
```

## edit.blade.php

Membuat edit.blade.php di folder view/mahasiswa

```php
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Edit Company Form - Laravel 9 CRUD Tutorial</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>

<body>
    <div class="container mt-2">
        <div class="row">
            <div class="col-lg-12 margin-tb">
                <div class="pull-left">
                    <h2>Edit Company</h2>
                </div>
                <div class="pull-right">
                    <a class="btn btn-primary" href="{{ route('mahasiswa.index') }}" enctype="multipart/form-data">
                        Back</a>
                </div>
            </div>
        </div>
        @if(session('status'))
        <div class="alert alert-success mb-1 mt-1">
            {{ session('status') }}
        </div>
        @endif
        <form action="{{ route('mahasiswa.update',$mahasiswa->id) }}" method="POST" enctype="multipart/form-data">
            @csrf
            @method('PUT')
            <div class="row">
                <div class="col-xs-12 col-sm-12 col-md-12">
                    <div class="form-group">
                        <strong>Nama</strong>
                        <input type="text" name="nama" value="{{ $mahasiswa->nama }}" class="form-control"
                            placeholder="Nama">
                        @error('nama')
                        <div class="alert alert-danger mt-1 mb-1">{{ $message }}</div>
                        @enderror
                    </div>
                </div>
                <div class="col-xs-12 col-sm-12 col-md-12">
                    <div class="form-group">
                        <strong>NIM</strong>
                        <input type="number" name="nim" class="form-control" placeholder="NIM"
                            value="{{ $mahasiswa->nim }}">
                        @error('nim')
                        <div class="alert alert-danger mt-1 mb-1">{{ $message }}</div>
                        @enderror
                    </div>
                </div>
                <div class="col-xs-12 col-sm-12 col-md-12">
                    <div class="form-group">
                        <strong>Alamat</strong>
                        <input type="text" name="alamat" value="{{ $mahasiswa->alamat }}" class="form-control"
                            placeholder="Alamat">
                        @error('alamat')
                        <div class="alert alert-danger mt-1 mb-1">{{ $message }}</div>
                        @enderror
                    </div>
                </div>
                <button type="submit" class="btn btn-primary ml-3">Submit</button>
            </div>
        </form>
    </div>
</body>

</html>

```

## Edit AppServiceProvider

Mengedit AppServiceProvider agar bisa menggunakan paginate

```php
<?php

namespace App\Providers;

use Illuminate\Pagination\Paginator;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     *
     * @return void
     */
    public function register()
    {
        //
    }

    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        Paginator::useBootstrap();
    }
}

```

## Hasil

jika tidak ada eror maka akan muncul pada http://mahasiswa.test/mahasiswa

### Index

![[laravel8crud3.png]]

### Create

![[laravel8crud4.png]]
![[laravel8crud5.png]]

### Edit

![[laravel8crud6.png]]
![[laravel8crud7.png]]

### Delete

![[laravel8crud8.png]]
