### Some Important link:

* [laravel 5.8](https://laravel.com)
* [anik sir(laravel note)](https://docs.google.com/document/d/1NJSldZ6a2Fs4q4q7KgH2llKdtLe4hylUwi10lKTGNDQ/edit?fbclid=IwAR1HTl96WSO_Xire6B3BXxoA-DwYH_qtqVJi-CWPXAYnpFEFBfQaFCS-hNc)
* [theme 1](https://colorlib.com/wp/free-bootstrap-admin-dashboard-templates/)
* [template monster](https://www.templatemonster.com/bootstrap-website-templates/)
* [Bootstrap](https://getbootstrap.com)
* [Bootsnip](https://bootsnipp.com)
* [Vue.js](https://vuejs.org)

## Topic
* [Run laravel project from github](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#run-laravel-project-from-github)

* [create project](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#create-project)
* [create Model](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md)
* [Create Controller](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#create-controller)
* [Create Controller with resources](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#create-controller--resources)
* [show routelist](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#show-routelist)
* [Mastering the template in Laravel](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#template-copy)
* [Login](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#login)
* [log out](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#logout)
* [Show successful message](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#showing-successfull-massage)
* [Change validation name](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#to-change-validation-name-)
* [Show previous text after finding invalid data](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#for-showing-previous-text-after-finding-invalid-data)
* [Review the image when we upload the image](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#review-the-image-when-we-take-image-as-input)
* [Middleware](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#protecting-routes-via-middleware)

* [Validation](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#validation)
* [Register](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#register)
* [Seeder](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#seeder)
* [show all post](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#all-post-show-all-data)
* [Edit](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#edit)
* [Delete](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#delete)
* [Adding image or upload image](https://github.com/jitunmohajan/laravel-note/blob/master/laravel%20project%20final%20note.md#adding-image)

## laravel tutorial:
1.[Bangla tutorial](https://www.youtube.com/watch?v=l6R5oZe20bA&list=PLH246IZCIBeA-k6OeV4zw7MyhzzrQPyyL)

## Serve:
php artisan serve
php artisan --port=8002 or anything
_________________________________________________________________________________



## Run laravel project from github:

* first open git bash on the path where you want to run the laravel project

* step 1:git clone project-URL-link
* step 2:cd repositoryname
* step 3:composer install
* step 4:cp .env.example .env
* step 5:php artisan key:generate
* step 6: create a database then change database name on .env file 
* step 7:php artisan migrate
__________________________________________________________________________________
## Create project:

* online creation:

composer create-project laravel/laravel project-name

* offline setup::
setup for ofline
composer global require laravel/installer

create new project in ofline>

laravel new project-name
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


______________________________________________________________________updated part______

## showing successfull massage:

* step 1:

```php
return redirect()->back()->with('msg','Successfully inserted');
```
* step 2:

```html
@if(Session::has('msg'))
	<div class="alert alert-success">{{Session::get('msg')}}</div>
@endif
```

## To change validation name :
(like if you want to change filename to image that means when it shows me error it show invalid image)

* step 1:resources->lang->en->validation
change attributes array>
```php
'attributes' => [
        'filename' => 'Image'
    ],
```
## for showing previous text after finding invalid data:
* step 1: 
add this-(value="{{old('email')}}") on input like down below
```htnl
<input class="form-control" type="email" value="{{old('email')}}" name="email" placeholder="Enter Email">
```
or
```html
<textarea type="text" name="description" class="input--style-5" id="" cols="55" rows="5">{{old('description')}}</textarea>
```
# Review the image when we take image as input
* step 1:
```php
<input type="file" accept="image/*" onchange="loadFile(event)">
<img id="output" width="100px"/>
<script>
  var loadFile = function(event) {
    var output = document.getElementById('output');
    output.src = URL.createObjectURL(event.target.files[0]);
  };
</script>
```
# [FOR MORE HELP VISIT for image review](https://stackoverflow.com/questions/4459379/preview-an-image-before-it-is-uploaded?fbclid=IwAR1GXOkRFIix0ucXCUZPIdctNirQkX9Ep6hq0hHey9spI3ulhLF_1JGn2Ik)



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


______________________________________________


## Validation:::::>>>>>

* step 1:
```php
   public function store(Request $req){

    	 $validatedData = $req->validate([
        'fname' => 'required',
        'lname' => 'required',
        'email' => 'required|email',
        'password' => 'required',
	//'password' => 'required|exists:users,password|min:6',//here users=table_name and password coloum name 
    	]);

    	$obj=new Sample();
    	$obj->fname=$req->fname;
    	$obj->lname=$req->lname;
    	$obj->email=$req->email;
    	$obj->password=$req->password;
    	

    	if($obj->save()){
    		return view('frontend.login');
    	}

}
```
#OR

paste this code after input tag for showing single input error(like email invalid or invalid password)

```php
<span style="color: red;">{{ $errors->first('email') }}</span>
```


* step 2:
```php
<h1>Create Post</h1>

@if ($errors->any())
    <div class="alert alert-danger">
        <ul>
            @foreach ($errors->all() as $error)
                <li>{{ $error }}</li>
            @endforeach
        </ul>
    </div>
@endif
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

## ALL post show all data::>>

* step 1:
```html
@extends('backend.layout')
@section('content')
     <div class="container">
  <h2>All Post</h2>            
  <table class="table">
    <thead>
      <tr>
        <th>ID</th>
        <th>Title</th>
        <th>Description</th>
        <th>Action</th>
      </tr>
    </thead>
    <tbody>
      @if(count($data)>0)
        @foreach($data as $d)
          <tr>
            <td>{{ $d->id }}</td>
            <td>{{ $d->title }}</td>
            <td>{{ $d->description }}</td>
           <td>
              <a href="{{ URL::to('edit',['id'=>$d->id]) }}" class="btn btn-info">Edit</a>
              <a href="{{ URL::to('edit',['id'=>$d->id]) }}" class="btn btn-info">Delete</a>
            </td>
           
          </tr>
        @endforeach
      @else

      @endif
     
      
    </tbody>
  </table>
</div>

@stop
````

* step 2:
```php
Route::get('allpost','HomeController@allpost');
```

* step 3:
```php
 public function allpost(){
        $obj = Sample::all();  //Sample is the model name 
            return view('frontend.allpost', ['data'=>$obj]);

    }
```

* step 4:
```html
<td><a href="{{ URL::to('edit/{$samples->id}') }}"  type="button" class="btn btn-primary">Edit</a></td>
```


_______________________________________________________

## Edit::>>

* step 1:
```html
@extends('backend.layout')
@section('content')
      <div class="card-body">


            <form id="signup-form" class="signup-form" method="post" action="{{ URL::to('update',['id'=>$data->id]) }}">
                {{csrf_field()}}
                 <div class="form-row">
                  <div class="form-group col-md-6">
                    <label>Title</label>
                    <input type="text" value="{{ $data->title }}" class="form-control" name="title" placeholder="Title">
                  </div>
                </div>
                <div class="form-group">
                  <label>Description</label>
                  <textarea name="description" class="form-control" rows="5">{{ $data->description }}</textarea>
                </div>
                          
                <button type="submit" class="btn btn-primary">Add</button>
              </form>
            </div>

@stop
```
* step 2:
```php
Route::post('update/{id}','HomeController@update');
```
* step 3:
```php
  public function update(Request $req,$id){
       
        $obj = Sample::find($id);       
        $obj->title = $req->title;
        $obj->description = $req->description;
         if($obj->save())
        {
             //Session::put('message', 'Successfully Updated...!!');
            return redirect('allpost');
        }
       // return view('frontend.edit',['data'=>$sample]);
    }

```



___________________________________________________________-

## Delete:::>>>

* step 1:
```html
<a href="{{ URL::to('del',['id'=>$d->id]) }}" class="btn btn-info">Delete</a>
```
* step 2:
```php
Route::get('del/{id}','HomeController@del');
```
* step 3:
```php
 public function del($id){
       
        $sample = Sample::find($id)->delete();       
       
         return redirect('allpost');
    }
```

_______________________________________________________________________________________________________


# Adding image:>>

* step 1:add on database table>>

```php
 $table->string('filename');
 ```
* step 2:
```php
	composer require intervention/image
```

* step 3:

	copy paste here following things config >> app.php
	
```php
	'providers' => [
        // ...
        Intervention\Image\ImageServiceProvider::class,
    	]
```


```php
	'aliases' => [
        // ...
        'Image' => Intervention\Image\Facades\Image::class,
   	 ]
```


* step 4: create file in public folder and name in
	 images and thumbnail


* step 5:


```php
use App\ImageModel;
use Image;

public function store(Request $request)
    {
       
        $originalImage= $request->file('filename');
        $thumbnailImage = Image::make($originalImage);
        $thumbnailPath = public_path().'/thumbnail/';
        $originalPath = public_path().'/images/';
        $thumbnailImage->save($originalPath.time().$originalImage->getClientOriginalName());
        $thumbnailImage->resize(150,150);
        $thumbnailImage->save($thumbnailPath.time().$originalImage->getClientOriginalName()); 

        $obj= new ImageModel();//ImageModel=Model name here
        $imagemodel->filename=time().$originalImage->getClientOriginalName();
        $obj->save();//obj=object name that we create

        return back()->with('success', 'Your images has been successfully Upload');
    }
```


* sep 6: add this into store function validation if needed


```php
$this->validate($request, [
            'filename' => 'image|required|mimes:jpeg,png,jpg,gif,svg'
  ]);
```

* step 7:

```hmtl
<html lang="en">
<head>
  <title>Laravel  Image Intervention</title>
  <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.js"></script>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
</head>
<body>
  
  <div class="container">
    <h3 class="jumbotron">Laravel  Image Intervention </h3>
    <form method="post" action="{{url('create')}}" enctype="multipart/form-data">
        @csrf
        <div class="row">
          <div class="col-md-4"></div>
          <div class="form-group col-md-4">
          <input type="file" name="filename" class="form-control">
          </div>
        </div>
        <div class="row">
          <div class="col-md-4"></div>
          <div class="form-group col-md-4">
          <button type="submit" class="btn btn-success" style="margin-top:10px">Upload Image</button>
          </div>
        </div>     
  </form>
  </div>
</body>
</html>
```

step 8:

```php
php artisan make:controller ImageController
```



