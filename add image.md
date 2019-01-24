# Adding image:>>

* step 1:add on database>>
``` 
 $table->string('filename');
```php

* step 2:

```
	composer require intervention/image
```

* step 3:

	copy paste here following things config >> app.php
	
	```
	'providers' => [
        // ...
        Intervention\Image\ImageServiceProvider::class,
    	]
```php

```
	'aliases' => [
        // ...
        'Image' => Intervention\Image\Facades\Image::class,
   	 ]
```php

* step 4: create file in public folder and name in
	 images and thumbnail

* step 5:

```
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
```php

* sep 6: add this into store function validation if needed

```
$this->validate($request, [
            'filename' => 'image|required|mimes:jpeg,png,jpg,gif,svg'
  ]);
```php

* step 7:

```
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
```html

step 8:

```
php artisan make:controller ImageController
```
