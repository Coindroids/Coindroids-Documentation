
# API Functions

All API functions are accessed via POST calls to the API. 

<aside class='notice'>
You will noticed that our list of functions is actually quite short. Most of the interaction you will do with the Coindroids universe is through cryptocurrency transactions. 
</aside>

|Function| Endpoint|
|---|---|
|create_droid(Model, Currency ID, Droid Name ) | /rpc/create_droid |
|get_droid_registration_address(Droid ID) | /rpc/get_droid_registration_address | 
|identify()| /rpc/identify |
|register(Username, Password, Email, Invite Code, Acceptance of Terms) | /rpc/register |
|set_droid_build(Droid ID, Build Details) | /rpc/set_droid_build |

## /rpc/create_droid

```shell
curl -X "POST" "https://api.coindroids.com/rpc/create_droid" \
	-H "Authorization: Bearer eyJhbGciO...DSzsybGFgk" \
	-H "Content-Type: application/json" \
	-d "{\"name\":\"Droidy McDroidface\",\"currency_id\":\"1\",\"model\":\"Assault Training\"}"
```

```javascript
jQuery.ajax({
    url: "https://api.coindroids.com//rpc/create_droid",
    type: "POST",
    headers: {
        "Authorization": "Bearer eyJhbGc...sybGFgk",
        "Content-Type": "application/json",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "name": "Droidy McDroidface",
        "model": "Assault Training",
        "currency_id": "1"
    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```python
# Install the Python Requests library:
# `pip install requests`

import requests
import json


def send_request():
  try:
        response = requests.post(
            url="https://api.coindroids.com/rpc/create_droid",
            headers={
                "Authorization": "Bearer eyJhbGciOiJI...zsybGFgk",
                "Content-Type": "application/json",
            },
            data=json.dumps({
                "name": "Droidy McDroidface",
                "model": "Droidy McDroidface",
                "currency_id": "1"
            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>


### Parameters

|Name | Type | Description|
|----|----|---|
|name | CHARACTER VARYING| Your droids new classy moniker|
|model| Model | See the list of models available for new droids below | 
|currency_id | Bigint | See the /currency endpoint for available currencies|

### Response Details

|Name | Description|
|----|----|
|Droid| The droid object as if called through the /droid endpoint. |

## /rpc/get_droid_registration_address

```shell
curl -X "POST" "https://api.coindroids.com/rpc/get_droid_registration_address" \
	-H "Authorization: Bearer eyJhbGciOiJIUzI...2lXGhuBjtQ8Q" \
	-H "Content-Type: text/plain" \
	-d "{ \"droid_id\":YourDroidID }"
```

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>


This function is used to grab a new wallet sync address for a droid.

<aside class='notice'>
If you notice that the Coindroids universe is no longer recognizing your transactions, you likely need to call this function and use the address returned to re-sync your wallet. 
</aside>



## /rpc/identify


> Username & Password Authentication

```shell
curl -X "POST" "https://api.coindroids.com/rpc/identify" \
	-H "Content-Type: application/json" \
	-d "{\"username\":\"YourUsername\",\"password\":\"YourPassword\"}"

```

```javascript
// Identify (POST https://api.coindroids.com/rpc/identify)

jQuery.ajax({
    url: "https://api.coindroids.com/rpc/identify",
    type: "POST",
    processData: false,
    data: "{\"username\":\"Abstract\", \"password\":\"password\"}",
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});

```


```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Identify
    # POST https://api.coindroids.com/rpc/identify

    try:
        response = requests.post(
            url="https://api.coindroids.com/rpc/identify",
            data="{\"username\":\"Abstract\", \"password\":\"password\"}"
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

```


> Token Authorization

```shell
curl -X "POST" "https://api.coindroids.com/rpc/identify" \
	-H "Authorization: Bearer eyJhbGciOiJ...4bn4gYu2gs"
```

```javascript
// Identify (update with authenticate session) (POST https://api.coindroids.com/rpc/identify)

jQuery.ajax({
    url: "https://api.coindroids.com/rpc/identify",
    type: "POST",
    headers: {
        "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp...-tV89N7sPiz4bn4gYu2gs",
    },
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});

```

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Identify (update with authenticate session)
    # POST https://api.coindroids.com/rpc/identify

    try:
        response = requests.post(
            url="https://api.coindroids.com/rpc/identify",
            headers={
                "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoicGxheWVycyIsImlkIjoiY2ZmYzZkYzQtMDY0ZS00OWRiLTllODgtNzgwNjY4ZjQ0ZTBjIn0.05yM5ihI5gyoh6bQoG6Kus-tV89N7sPiz4bn4gYu2gs",
            },
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')


```


To start a new session, pass the username and password paramters. If you are extending a session, no paramters are needed but the transaction must include an authorization header. 


### Parameters 

#### Username & Password Authentication

|Name | Type | Description|
|----|----|---|
|username| Character Varying | The player name|
|password| Chacter Varying | The player password|


#### Token Authentication

|Name |Type| Description|
|----|----|---|
|-|-| _No paramters needed for token based identification_|



### Response Details

|Name | Description|
|----|----|
|Token| The JWT authorization token for API requests|




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
|Token| The JWT authorization token for API requests|





## /rpc/set_droid_build

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>

Your droid is an ever evolving beast and the Coindroids universe is no different. Ensure your droid is always built to impress (and annihilate) through the set_droid_build call. 

<aside class='notice'>
Builds are not updated immediately, they are validated and put into a pending state. Droid builds are applied during the Block Processing procedures.
</aside>

### Parameters

|Name | Type | Description|
|----|----|---|
|droid_id|Bigint| The ID of the droid being updated|
|build|JSONB||



### Response Details

|Name | Description|
|----|----|
|Droid| The droid object as if called through the /droid endpoint. |




