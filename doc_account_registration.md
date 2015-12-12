---
title: Account Registration
tags: [starting, droids, model]
keywords: starting, droid, models 
last_updated: November 21, 2015
summary: "Registration and droid creation"

---


Before you can create your first droid, you will need a Coindroids user account... and before you can create a Coindroids user account, you will need to accept the terms and conditions for alpha testing.

If you need an Invite Code, come visit us at #coindroids in freenode. 

```
You are registering for a gameplay account with the Coindroids Alpha System.

In order to register, you must agree to the following:
1. I acknowledge that this is a highly-experimental system that is still under development
2. I have no expectation of quality of service, quality of gameplay, enjoyment, understanding, or any other adjective with respect to any part of the Coindroids Alpha System.
3. I acknowledge that every single cryptocurrency token sent into the Coindroids Alpha System (regardless of which currency or what amount) may be irretrievably lost due to any one or combination of my errors, programming errors, administrative errors, blockchain errors, database resets, sun spots, black cats, or any number of other reasons.
4. I will not hold anyone involved with Coindroids responsible for any loss, damage, missed opportunity, harm, pain, discomfort, confusion, perplexity, lack of understanding, or any other negative occurrence as a result of my use of the Coindroids Alpha System. This includes executives, officers, game designers, blockchain engineers, developers, programmers, designers, illustrators, investors, marketing personnel, secretaries, administrative assistants, executive assistants, assistants, aides, apprentices, adjuncts, associates, attendants, or right-hand persons (people).
5. I accept that at any time, the Coindroids Alpha System may change as a result of developer updates that could alter the behaviour of the Coindroids Alpha System to something that is completely different than what I expected.
6. I accept that gameplay rules, calculations, character levels, experience points, damage points, bonuses, modifiers, and all other numbers used by the system can change at any time without prior warning or post apology.
7. I accept that at any time my player account can disappear (intentionally or accidentally), including all characters that I have created, all items that I have purchased, and all experience points, purse amounts, and in-game statistics that my characters have earned.
8. I have no expectation of reward, remuneration, payment, reimbursement, or any other compensation as a result of my use of the Coindroids Alpha System.
9. I am of the age-of-majority in my jurisdiction, am not mentally impaired, and am able to legally make decisions for myself without reservation and without the consent of any other person.
10. I am registering for a gameplay account with the Coindroids Alpha System through my own free will and understand 100% what I am getting into.
```


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
				<input type="checkbox" id="accept_terms" name="accept_terms" value="true"> Accept Alpha Terms & Conditions
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
		           "invite_code" : $("#InviteCode").val(),
		           "accept_terms" : $("#accept_terms").attr('checked')
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

