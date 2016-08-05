


## /rpc/register

```shell
curl -X "POST" "https://api.coindroids.com/rpc/register" \
	-H "Content-Type: text/plain" \
	-d $'{ 
	"username":"Abstract",
	"password":"password",
	"email":"josh@coindroids.com",
	"invite_code":"37764f2a-da1b-40ea-a054-ef1c8021196a"

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



This function is used to create new players in the system. Create your player first, otherwise you won't be able to create a droid.

### Parameters

|Name | Type | Description|
|----|----|---|
|username |Character Varying||
|password |Character Varying||
|email |Character Varying||
|invite_code|Character Varying||
|accept_terms|Boolean||


### Response Details

|Name | Description|
|----|----|
|Profile| The user profile as if queried by the /player object |
|Token| The JWT authorization token for API requests|



