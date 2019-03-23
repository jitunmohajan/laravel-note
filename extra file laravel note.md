____showing successfull massage:

step 1:
return redirect()->back()->with('msg','Successfully inserted');

step 2:

@if(Session::has('msg'))
	<div class="alert alert-success">{{Session::get('msg')}}</div>
@endif


___To change validation name :(like if you want to change filename to image that means when it shows me error it show invalid image)
step 1:resources->lang->en->validation
change attributes array>

'attributes' => [
        'filename' => 'Image'
    ],





____for showing previous text after finding invalid data:
step 1: add this-(value="{{old('email')}}") on input like down below

<input class="form-control" type="email" value="{{old('email')}}" name="email" placeholder="Enter Email">
or
<textarea type="text" name="description" class="input--style-5" id="" cols="55" rows="5">{{old('description')}}</textarea>
_________review the image when we take image as input
step 1:
<input type="file" accept="image/*" onchange="loadFile(event)">
<img id="output" width="100px"/>
<script>
  var loadFile = function(event) {
    var output = document.getElementById('output');
    output.src = URL.createObjectURL(event.target.files[0]);
  };
</script>
link:https://stackoverflow.com/questions/4459379/preview-an-image-before-it-is-uploaded?fbclid=IwAR1GXOkRFIix0ucXCUZPIdctNirQkX9Ep6hq0hHey9spI3ulhLF_1JGn2Ik
______________
new account

nicher line ta kete dibe

copy right

unique:table_name,colum_name

