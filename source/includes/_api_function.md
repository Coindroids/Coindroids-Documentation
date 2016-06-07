
# API Functions

All API functions are accessed via POST calls to the API. 

<aside class='notice'>
You will noticed that our list of functions is actually quite short. Most of the interaction you will do with the Coindroids universe is through cryptocurrency transactions. 
</aside>

|Function| Endpoint| Method |
|---|---|---|
|create_droid(Model, Currency ID, Droid Name ) | /rpc/create_droid |POST|
|get_droid_registration_address(Droid ID) | /rpc/get_droid_registration_address |POST| 
|identify()| /rpc/identify |POST|
|register(Username, Password, Email, Invite Code, Acceptance of Terms) | /rpc/register |POST|
|set_droid_build(Droid ID, Build Details) | /rpc/set_droid_build |POST|
