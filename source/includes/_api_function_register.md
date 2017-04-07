


## /rpc/register

```shell
curl -X "POST" "https://api.coindroids.com/rpc/register" \
	-H "Content-Type: text/plain" \
	-d $'{ 
	"username":"Abstract",
	"password":"password",
	"email":"josh@coindroids.com",
	"invite_code":"37764f2a-da1b-40ea-a054-ef1c8021196a",
	"accept_terms":"t"

}'
```

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
		           "invite_code":$("#InviteCode").val(),
		           "accept_terms":$("#AcceptedTerms").val() 
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
				\"invite_code\":\"37764f2a-da1b-40ea-a054-ef1c8021196a\",
				\"accept_terms\":\"t\"

			}"
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

```



This function is used to create new players in the system. Create your player first, otherwise you won't be able to create a droid.

### Parameters

|Name | Type | Description|
|----|----|---|
|username |String||
|password |String||
|email |String||
|invite_code|UUID||
|accept_terms|Boolean||


### Response Details

|Name | Type|  Description|
|----|---|---|
|profile| Player Profile| The player object with the following attributes (profile.*)|
|profile.id| Whole Number| The players ID |
|profile.username| String| The Players Username|
|profile.email|Email|Email address belonging to the player|
|errors| Error[] |An array of errors with the following attributes (errors[].*)|
|errors[].field| String| Error Label|
|errors[].message| String | Error descrption| 
|token| JWT | The JWT authorization token for API requests|


### Potential Errors

| Field | Message |
|----|----|
|accept_terms|You must accept the terms and conditions to register|
|invite_code|Invite code was invalid|
|username|Invalid username format. Must be letters, numbers and underscores only.|
|password|Password cannot be blank|
|email|Email address cannot be blank|
|general|Error during player registration|