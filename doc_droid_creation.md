---
title: Droid Creation
tags: [starting, droids, model]
keywords: starting, droid, models 
last_updated: November 21, 2015
summary: "Registration and droid creation"

---


<br />

<script> 
$(document).ready(function(){
$("#submit-creation-hidden").hide();
});
</script>

<script>
$("#submit-creation").click(function( event ) {
   $("#submit-creation").hide();
   $("#submit-creation-hidden").show();
   event.preventDefault();

	   var creationData = {
	           "name" : $("#Name").val(),
	           "currency" : $("#Currency").val(),
	           "Model" : $("#Model").val() 
	       };

	   jQuery.ajax({
	    url: "http://api.coindroids.com:3000/rpc/register",
	    type: "POST",
	    processData: false,
	       contentType: 'application/json',
	    data: JSON.stringify(creationData)
		})
	.done(function(data, textStatus, jqXHR) {
	
	    $("#CreationFormContent").html("<p>Creation Complete!</p>");
	
		
	
	    console.log("HTTP Request Succeeded: " + jqXHR.status);
	    console.log(data);
	})
	.fail(function(jqXHR, textStatus, errorThrown) {
	    console.log("HTTP Request Failed");
	})
	.always(function() {
	    /* ... */
	});
});

</script>   



## Choosing your Droid Model

When creating a new droid, you have the option to chosoe from three different base models. These are all basically the same currently but that will change as the game evolves. 

<div class="container">
 
  <div class="row">
    <div class="col-md-2">
	</div>
    <div class="col-md-2 text-center">
    	<img src='https://thumbnail.invisionapp.com/resize?location=https%3A%2F%2Finvisionapp%2Dcdn%2Ecom%2Fstorage%2Einvisionapp%2Ecom%2Fboards%2Ffiles%2F37703702%2Epng%3Fx%2Damz%2Dmeta%2Dck%3D3a96b0ca1cac7b356e364a74c78c74fc%26x%2Damz%2Dmeta%2Div%3D1%26AWSAccessKeyId%3DAKIAJFUMDU3L6GTLUDYA%26Expires%3D1451624400%26Signature%3Dw%252Be9e47WIGcedSmaZhifLDwxXNs%253D&width=150' />
	</div>
    <div class="col-md-2 text-center">
    <img src='https://thumbnail.invisionapp.com/resize?location=https%3A%2F%2Finvisionapp%2Dcdn%2Ecom%2Fstorage%2Einvisionapp%2Ecom%2Fboards%2Ffiles%2F37599865%2Epng%3Fx%2Damz%2Dmeta%2Dck%3D3a96b0ca1cac7b356e364a74c78c74fc%26x%2Damz%2Dmeta%2Div%3D1%26AWSAccessKeyId%3DAKIAJFUMDU3L6GTLUDYA%26Expires%3D1451624400%26Signature%3DZIQwaKhaUVRNXTcInvgj6YCcj4k%253D&width=150' style='opacity:.1;'/>
    </div>
    <div class="col-md-2 text-center">
    	<img src='https://thumbnail.invisionapp.com/resize?location=https%3A%2F%2Finvisionapp%2Dcdn%2Ecom%2Fstorage%2Einvisionapp%2Ecom%2Fboards%2Ffiles%2F37599865%2Epng%3Fx%2Damz%2Dmeta%2Dck%3D3a96b0ca1cac7b356e364a74c78c74fc%26x%2Damz%2Dmeta%2Div%3D1%26AWSAccessKeyId%3DAKIAJFUMDU3L6GTLUDYA%26Expires%3D1451624400%26Signature%3DZIQwaKhaUVRNXTcInvgj6YCcj4k%253D&width=150' />
    </div>
  </div>
  
    <div class="row">
    <div class="col-md-2">
	</div>

    <div class="col-md-2 text-center"><h3>Base Scout</h3></div>
    <div class="col-md-2 text-center"><h3>Base Artillery</h3></div>
    <div class="col-md-2 text-center"><h3>Base Assault</h3></div>
	</div>


    <div class="row">

    <div class="col-md-2 text-right">
		Registration 
	</div>

    <div class="col-md-2 text-center">
    0.0001 TBTC 
    </div>
    <div class="col-md-2 text-center">
    0.0001 TBTC
    </div>
    <div class="col-md-2 text-center">
    0.0001 TBTC
    </div>
  </div>
  
  
    <div class="row">

    <div class="col-md-2 text-right">
		Purse Size
	</div>

    <div class="col-md-2 text-center">
    100
    </div>
    <div class="col-md-2 text-center">
    100
    </div>
    <div class="col-md-2 text-center">
    100
    </div>
  </div>
  
  
      <div class="row">

    <div class="col-md-2 text-right">
		Health
	</div>

    <div class="col-md-2 text-center">
    100
    </div>
    <div class="col-md-2 text-center">
    100
    </div>
    <div class="col-md-2 text-center">
    100
    </div>
  </div>
  
  
      <div class="row">

    <div class="col-md-2 text-right">
		Strength
	</div>

    <div class="col-md-2 text-center">
    Evasion
    </div>
    <div class="col-md-2 text-center">
    Attack
    </div>
    <div class="col-md-2 text-center">
    Defense
    </div>
  </div>

</div>

<br />

<div class="container">
<div class="row">
<div id='CreationFormContent' class='col-md-2'>
</div>

<div id='CreationFormContent' class='col-md-6'>
<form id="creation-form">
	<div class="form-group row">
		<label for='Name' class="col-md-2 form-control-label text-right">Name:</label>
		<div class="col-sm-10">
			<input class="form-control" name='Name' id='Name' type='text'>
		</div>
	</div>
	<div class="form-group row">
		<label for='Currency' class="col-md-2 form-control-label text-right">Currency:</label>
		<div class="col-sm-10">				
			<select class="form-control" name='Currency' id='Currency'  type='text' >
				<option value='1'> Bitcoin Testnet </option> 
				<option value='2'> Dogecoin </option> 
				<option value='3'> Bitcoin </option> 
				<option value='4'> Defcoin </option> 
			</select>
		</div>
	</div>
		<div class="form-group row">
		<div class="col-sm-offset-2 col-md-10">
				<button type="submit" id="submit-creation">Create</button>
				<button type="button"  id="submit-creation-hidden" disabled>
					<span class='fa fa-gear fa-spin'></	span>
				</button>
		</div>
	</div>
		
</form>
</div>
</div>
</div>
<hr />