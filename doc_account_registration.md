---
title: Account Registration
tags: [starting, droids, model]
keywords: starting, droid, models 
last_updated: November 21, 2015
summary: "Registration and droid creation"

---


Before you can create your first droid, you will need a Coindroids user account. If you need an Invite Code, come visit us at #coindroids in freenode. 


<div id='RegistrationFormContent'>
<form class="pure-form" id="registration-form">
				<fieldset class="form-group">
					<div>
						<label for='Username'> Username: </label><input class="form-control" name='Username' id='Username' type='text'>
					</div>
				</fieldset>
						
				<fieldset class="form-group">
					<div>		
						<label for='Email'>Email:</label><input class="form-control" name='Email' id='Email' type='text'>
					</div>
				</fieldset>
				<fieldset class="form-group">	
					<div>
						<label for='Password'>Password:</label><input class="form-control" name='Password' id='Password' type='password' placeholder="Make it good!">
						<input  name='RepeatPassword' id='RepeatPassword' class="form-control" type='password' placeholder="Then type it again">
					</div>
				</fieldset>
				<fieldset class="form-group">
					<div>
						<label for='InviteCode'>Invite Code: </label> <input class="form-control" name='InviteCode' id='InviteCode' type='text' placeholder="Invite Code">
					</div>
				</fieldset>
				
				<button type="submit" id="submit-registration">Sign Up</button>
				<button type="button"  id="submit-registration-hidden" disabled>
					<span class='fa fa-gear fa-spin'></	span>
				</button>
</form>
 

</div>

<script> 
$(document).ready(function(){
$("#submit-registration-hidden").hide();
});
</script>

<script>
$("#submit-registration").click(function( event ) {
   $("#submit-registration").hide();
   $("#submit-registration-hidden").show();
   event.preventDefault();


   if ($("#Password").val() == $("#RepeatPassword").val()) {
		   var registrationData = {
		           "username" : $("#Username").val(),
		           "password" : $("#Password").val(),
		           "email" : $("#Email").val(),
		           "invite_code":$("#InviteCode").val() 
		       };
		   jQuery.ajax({
		    url: "https://api.coindroids.com/rpc/register",
		    type: "POST",
		    processData: false,
		       contentType: 'application/json',
		    data: JSON.stringify(registrationData)
			})
		.done(function(data, textStatus, jqXHR) {

		    localStorage.Username = $("#Username").val();
		    localStorage.AuthToken = 'Bearer ' + data.token;
		    
		    
		    $("#RegistrationFormContent").html("<p>Registration Complete!</p>");
		    $("#RegistrationFormContent").append("<p><textarea disabled>"+ data.token +"</textarea> <br> You will need this token for any authorized API requests. You can also always generate a new token with the identify call.  </p>"); 
		    

		    
		    console.log("HTTP Request Succeeded: " + jqXHR.status);
		    console.log(data);
		})
		.fail(function(jqXHR, textStatus, errorThrown) {
		    console.log("HTTP Request Failed");
		})
		.always(function() {
		    /* ... */
		});

	}
   
});

</script>   

<br />

After you submit this form, it will yield an authentication token that will be active for 24 hours of play. You will need this string for future actions within Coindroids, so don't forget to copy/paste it somewhere safe!

If you lose it, don't fret. Your username and password can be used at any time to grab another authentication token to keep you playing for day. You can also renew the length of an existing token once per day to keep playing with it indefinitely

<br />

