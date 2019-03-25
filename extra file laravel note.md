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




