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
$("#submit-login-hidden").hide();
$("#user-box").hide();
$("#reg-warning").hide();
});

</script>

 

<div id='creation-section'>

<div id='user-box'>
<i>Currently signed in as <span id='username_display'></span></i> <form ><button type='submit' id='log_out'>Log Out</button></form>
</div>

<div id='reg-warning'>
If you haven't already, first head over to the Registration section and create your player account. Players have droids, droids belong to players. 

If you have Registered already, then you can also login here:

<form class="pure-form" id="login-form" >
				<fieldset class="form-group">
					<div>
						<label for='Username'> Username: </label><input class="form-control" name='Username' id='Username' type='text'>

						<label for='Password'>Password:</label><input class="form-control" name='Password' id='Password' type='password' placeholder="">
						
					</div>
				</fieldset>

				
				<button type="submit" id="submit-login">Login</button>
				<button type="button"  id="submit-login-hidden" disabled>
					<span class='fa fa-gear fa-spin'></	span>
				</button>
</form>

<script>
$("#submit-login").click(function( event ) {
   $("#submit-login").hide();
   $("#submit-login-hidden").show();
   event.preventDefault();



		   var registrationData = {
		           "username" : $("#Username").val(),
		           "password" : $("#Password").val()
		       };
		   jQuery.ajax({
		    url: "https://api.coindroids.com/rpc/identify",
		    type: "POST",
		    processData: false,
		       contentType: 'application/json',
		    data: JSON.stringify(registrationData)
			})
		.done(function(data, textStatus, jqXHR) {

		$("#Password").val('');
		$("#Username").val('');

		    localStorage.Username = $("#Username").val();
		    localStorage.AuthToken = 'Bearer ' + data.token;
		    
		    
		       $("#reg-warning").hide();
		       	$("#user-box").show();
			   	$("#username_display").html(localStorage.Username)
		    

		    
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

$("#log_out").click(function( event ) {
	localStorage.clear();

});
</script>  
</div>

<script> 
$(document).ready(function(){

if (localStorage.Username == null)
{
	$("#reg-warning").show();
	$("#user-box").hide();
	
} else {
	$("#reg-warning").hide();
	$("#user-box").show();
	$("#username_display").html(localStorage.Username)
}

});

</script>



<h2> Choosing your Droid Model </h2>

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
		<div id='' class='col-md-2'>
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
				<option value='2'> Defcoin </option> 
			</select>
		</div>
	</div>

	<div class="form-group row">
		<label for='Model' class="col-md-2 form-control-label text-right">Model:</label>
		<div class="col-sm-10">				
			<select class="form-control" name='Model' id='Model'  type='text' >
				<option value='3'> Base Assault  </option> 
				<option value='4'> Base Artillery </option> 
				<option value='5'> Base Scout </option> 
			</select>
		</div>
	</div>

		<div class="form-group row">
		<div class="col-sm-offset-2 col-md-10">
				<button type="button" id="submit-creation">Create</button>
				<button type="button"  id="submit-creation-hidden" disabled>
					<span class='fa fa-gear fa-spin'></	span>
				</button>
		</div>
	</div>
		
</form>
</div>
</div>
</div>
</div>
<hr />

<script>

function get_reg_qr(droid_id){
	 var qrData = {
	           "droid_id" : droid_id
	       };


    jQuery.ajax({
	    url: "https://api.coindroids.com/rpc/get_droid_registration_address",
	    headers:  {
			"Authorization": localStorage.AuthToken
		},
	    type: "POST",
	    contentType: 'application/json',
	    data: JSON.stringify(qrData)
		})
	.done(function(data, textStatus, jqXHR) {
	    var qrtext = encodeURIComponent("bitcoin://" + data[0].get_droid_registration_address + "?amount=0.0001&message=Droid%20Registration");
	    $("#creation-section").append("<p>Your registration address is: " + data[0].get_droid_registration_address + "<br>Sending 0.0001 to this address will sync your wallet to the Coindroids sytstem, allowing it to monitor for actions such as attacks and item purchases. Your droid will not be active until this is step is complete. <br><img src='https://chart.googleapis.com/chart?cht=qr&chl="+qrtext+"&chs=180x180&choe=UTF-8&chld=L|2' alt=''></p>");
	
		console.log("HTTP Request Succeeded: " + jqXHR.status);
	    console.log(data);
	})
	.fail(function(jqXHR, textStatus, errorThrown) {
		    $("#CreationFormContent").html("<p>Creation Failed!</p>");
	    console.log("HTTP Request Failed");
	})
	.always(function() {
	    /* ... */
	});

}

$("#submit-creation").click(function( event ) {
   $("#submit-creation").hide();
   $("#submit-creation-hidden").show();
   event.preventDefault();

	 var creationData = {
	           "name" : $("#Name").val(),
	           "currency_id" : $("#Currency").val(),
	           "model_id" : $("#Model").val() 
	       };


    jQuery.ajax({
	    url: "https://api.coindroids.com/rpc/create_droid",
	    headers:  {
			"Authorization": localStorage.AuthToken
		},
	    type: "POST",
	    contentType: 'application/json',
	    data: JSON.stringify(creationData)
		})
	.done(function(data, textStatus, jqXHR) {
	
	    $("#creation-section").html("<p>Creation Complete!</p>");
	
		get_reg_qr(data[0].id);
	
	    console.log("HTTP Request Succeeded: " + jqXHR.status);
	    console.log(data);
	})
	.fail(function(jqXHR, textStatus, errorThrown) {
		    $("#CreationFormContent").html("<p>Creation Failed!</p>");
	    console.log("HTTP Request Failed");
	})
	.always(function() {
	    /* ... */
	});
});

</script>  

