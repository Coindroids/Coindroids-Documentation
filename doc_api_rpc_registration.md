---
title: /rpc/registration
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "This function is used to register users to the system"

---

## Response Details

|Name | Description|
|----|----|
|Token| The JWT authorization token for API requests|

## Examples

### HTTP Request


```HTTP
POST https://api.coindroids.com/registration
{ 
	"username":"Abstract",
	"password":"password",
	"email":"josh@coindroids.com",
	"invite_code":"37764f2a-da1b-40ea-a054-ef1c8021196a"
}
```


### Javascript


This is a working example of the Registration RPC call. If you need an Invite Code to pass, come visit us at #coindroids in freenode. 

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


```javascript
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
		    $("#RegistrationFormContent").html("<p>Registration Complete!</p>");
		    $("#RegistrationFormContent").append("<p><textarea disabled>"+ data.token +"</textarea></p>"); 
		    
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
```

### Python

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Register a player
    # POST https://api.coindroids.com/rpc/register

    try:
        response = requests.post(
            url="https://api.coindroids.com/rpc/register",
            data="{ 
	\"username\":\"Abstract\",
	\"password\":\"password\",
	\"email\":\"josh@coindroids.com\",
	\"invite_code\":\"37764f2a-da1b-40ea-a054-ef1c8021196a\"

}"
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

```



