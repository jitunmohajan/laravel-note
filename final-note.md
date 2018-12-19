## Serve:
php artisan serve
php artisan --port=8002 or anything
__________________________________________________________________________________
## Create project:
composer create-project laravel/laravel project-name
__________________________________________________________________________________
## Create model:
php artisan make:model model-name -m
__________________________________________________________________________________
## Create Controller:
php artisan make:comtroller ControllerName
__________________________________________________________________________________
## Create Controller & resources:
php artisan make:comtroller ControllerName --resource
__________________________________________________________________________________
## show routelist:
php artisan route:list
__________________________________________________________________________________
## template copy>>
	backend file>>
	write it in the middle where you need to change
```
  @yield('content') 
```
main file >>
```
		@extends('layout.layout')   //this define the file name ==layout.layout
```
		@section('content')
			write here 	
		@endsection // or you can use @stop

__________________________________________________________________________________
## LOGIN::>>>>
* step 1:
```html
<form method="post" action="{{ URL::to('postlogin' )}}">
            {{csrf_field()}}
<button type="submit" class="btn btn-primary btn-block">Register</button>	
```
* step 2:
```php
Route::get('/','HomeController@login');
Route::post('postlogin','HomeController@postlogin');
```
** step 3:
```php
public function postlogin(Request $req){
    	$email=$req->email;
    	$password=$req->password;
    	$obj=User::where('email','=',$email)
    			 ->where('password','=',$password)
    			 ->first();
    	if($obj){
    		Session::put('userid',$obj->id);//this pass the variable
    		return redirect('index');
    	}
    	else 
    		return "wrong";		 
    }
```
* step 4:
```php
use App\User;
use Session; //when you use session function
```
__________________________________________________________________________________
## Protecting Routes via Middleware
* step 1: Creating middleware: 
```git
php artisan make:middleware IsLoggedIn 
//Middleware will be created inside project_folder/app/Http/Middleware
```
*step 2:
Go inside project_folder/app/Http/Middleware the file created. Put the following code snippet inside handle method:
```php
public function handle($request, Closure $next)
    {
        if(!Session::has('userid')){
            return redirect()->route('login');
        }
        return $next($request);
    }
```
step 3:
Don’t forget to import use Session; before the class
```php
use Illuminate\Support\Facades\Session;
//use Illuminate\Support\Facades\Redirect;  //use it when you use redirect function
```
* step 4:
Go to app/http/kernel.php and add this line: inside $routeMiddleware array 
```
'checkloggedin' => \App\Http\Middleware\IsLoggedIn::class,
```
* step 5:
Now we can use checkloggedin as the middleware as below:
```php
Route::group(['middleware' => 'checkloggedin'], function(){
	YOUR ROUTES HERE
});
```

__________________________________________________________________________________
## LogOut::>>
* step 1:
```php
Route::get('logout','HomeController@logout');
```
* step 2:
```php
public function logout(Request $req)
    {
    	$req->session()->flush();
    	return redirect('/');
    	
    }
```
__________________________________________________________________________________
## REGISTER::>>
* step 1:
```html
<form method="post" action="{{ URL::to('store' )}}">
            {{csrf_field()}}
<button type="submit" class="btn btn-primary btn-block">Register</button>
```
 * step 2:
```php
Route::get('register','HomeController@register');
Route::post('store','HomeController@store');
```
* step 3:
```php
public function store(Request $req){
    	$obj=new User();
    	$obj->firstName=$req->firstName;

    	if($obj->save()){
    		return view('backend.login');
    	}
}
```
* step 4:
```php
use App\User;
```
__________________________________________________________________________________


## Seeder::::::>>>>>
* firstly create a model if model didnt create before

* step 1:

php artisan make:seeder UsersTableSeeder
* step 2:

goto database/factory/UserFactory
add fakers according to your need

* step 3:

goto database/seeds/DatabaseSeeder.php
```php
public function run()
    {
         $this->call(UsersTableSeeder::class);
    }
```
* step 4:

goto database/seeds/UsersTableSeeder.php
```php
public function run()
    {
        factory(App\Sample::class,15)->create();
    }
```

* step 5:

php artisan migrate --seed
_________________________________________________-

