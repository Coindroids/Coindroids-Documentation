---
title: Droid Management
tags: [starting, droids, model]
keywords: starting, droid, models 
last_updated: November 21, 2015
summary: "Droid management"

---


<br />

<script> 
$(document).ready(function(){
$("#submit-creation-hidden").hide();
$("#submit-login-hidden").hide();
$("#user-box").hide();
$("#reg-warning").hide();
$("#droid_details_1").hide();
$("#droid_details_2").hide();

});

</script>

 


<div id='user-box'>
<i>Currently signed in as <span id='username_display'></span></i>
</div>

<div id='reg-warning'>
If you haven't already, first head over to the Registration section and create your player account. Players have droids, droids belong to players. 

If you have Registered already, then you can also login here:

<form class="pure-form" id="login-form">
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

		    localStorage.Username = $("#Username").val();
		    localStorage.AuthToken = 'Bearer ' + data.token;
		    
		    
		       $("#reg-warning").hide();
		       	$("#user-box").show();
			   	$("#username_display").html(localStorage.Username)
		    

		 	$("#login-form").submit();
		    
		    
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
	
	$("#droid_details_1").show();
	$("#droid_details_2").show();
		    
	
		jQuery.ajax({
		    url: "https://api.coindroids.com/droid?username=eq."+localStorage.Username,
		    type: "GET",
		    processData: false,
		       contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			
			 tmp = '';
			 for (index = data.length - 1; index >= 0; --index) { 
				if (index == 0 ) {tmp = 'selected'} else { tmp = '';}
				$("#droid_name").append("<option value="+data[index].id+" "+tmp+">"+data[index].name+" ("+data[index].currency_code+")</option>");

			}
			
			  index = 0;
				$("#droid_class").html(data[index].droid_class);
				$("#droid_experience").html(data[index].experience);
				$("#droid_level").html(data[index].level);
				$("#droid_purse").html((data[index].purse_current/10000000) + "/" + (data[0].purse_max/10000000)+ " TBTC");
		  	    $("#droid_health").html(data[index].health_current + "/" + data[0].health_max);
		  	    
		  	    if (data[index].attack_address == null) {
		  	    	$("#droid_attack_address").html("<i>Your attack address has not be assigned. You need to complete you first wallet syncronization process first.");
		  	    } else {
		  	    	$("#droid_attack_address").html(data[index].attack_address + "<br><img src='https://chart.googleapis.com/chart?cht=qr&chl="+data[index].attack_address+"&chs=180x180&choe=UTF-8&chld=L|2' alt=''>")
		  	    }
		  	    
		  		for (build_index = data[index].build.length - 1; build_index >= 0; --build_index) {
		  			$("#droid_build").append("<tr><th>"+data[index].build[build_index].name+"<td>"+data[index].build[build_index].item_type+"<td>"+data[index].build[build_index].damage+"<td>"+data[index].build[build_index].accuracy+"<td>"+data[index].build[build_index].defense+"<td>"+data[index].build[build_index].evasion+"<td>"+data[index].build[build_index].counter_attack+"<td>"+data[index].build[build_index].health_increase);
		  		}
		  		
		  		if (data[index].inventory != null) {
			  		for (inventory_index = data[index].inventory.length - 1; inventory_index >= 0; --inventory_index) {
			  			$("#droid_inventory").append("<tr><th>"+data[index].inventory[inventory_index].name+"<td>"+data[index].inventory[inventory_index].item_type+"<td>"+data[index].inventory[inventory_index].damage+"<td>"+data[index].inventory[inventory_index].accuracy+"<td>"+data[index].inventory[inventory_index].defense+"<td>"+data[index].inventory[inventory_index].evasion+"<td>"+data[index].inventory[inventory_index].counter_attack+"<td>"+data[index].inventory[inventory_index].health_increase);
			  		}
		  		} else {
		  		$("#droid_inventory").append("<th> Inventory is empty. <td><td><td><td><td><td><td> ");
		  		}
	
		 	get_reg_qr(data[index].id);
		 	

		    console.log("HTTP Request Succeeded: " + jqXHR.status);
		    console.log(data);
		})
		.fail(function(jqXHR, textStatus, errorThrown) {
		    console.log("HTTP Request Failed");
		})
		.always(function() {
		       $("#submit-lookup").show();
			   $("#submit-lookup-hidden").hide();
		});
	
		
	}

});




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
	
	    $("#droid_wallet_sync").html(data[0].get_droid_registration_address + "<br><br><img src='https://chart.googleapis.com/chart?cht=qr&chl="+data[0].get_droid_registration_address+"&chs=180x180&choe=UTF-8&chld=L|2' alt=''></p>");
	
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


</script>

<br>

<div class="container"  id='droid_details_1'>

 <div class="row">
 	<div >
		 <select id='droid_name' style='text-transform:capitalize; font: large;' class='form-control-lg'></select>
		
		 <div>Class: <span id='droid_class'></span></div>
		
		 
		 <div>Level: <span id='droid_level'></span></div>
		 <div>Experience: <span id='droid_experience'></span></div>
		
		 <div>Health: <span id='droid_health'></span></div>
		
		 <div>Purse: <span id='droid_purse'></span></div>
	 </div>
	 <div >
		<h3>Attack Address - What your enemies use to attack you</h3>
		<span id='droid_attack_address'></span>
		<br>This address is very public. Attacks are a good thing!	 	
	 </div>	
	 <div >
	 	<h3>Wallet Sync Address - What you use to add another wallet address</h3>
		<span id='droid_wallet_sync'></span>
		<br>This Address should only be used if your attacks and purchases are not being associated with your player. You may notice this when trying to attack or purchase an item, only to have your money returned to you minus the transaction fee. Sending 1 token here will syncronize your wallet with our servers again. If this is your first time registering a wallet, it will also activate your droid and assign it an attack address. 
		
	 </div>
  <div>
  
</div>
<div class="container" id='droid_details_2'>
 <div class="row">
 <h3>Build</h3>
 <table id='build'>
 <thead>
 	  <tr>
   <th id="n"> Name
   <th> Type
   <th> Damage	
   <th> Accuracy	
   <th> Defense	
   <th> Evasion	
   <th> Counter Attack	
   <th> Health Increase
 </thead>
 <tbody id='droid_build'>
   
 </tbody>
 </table>

 
 <h3>Perishable Inventory</h3>
 <table id='inventory'>
 <thead>
 	  <tr>
   <th id="n"> Name
   <th> Class
   <th> Damage	
   <th> Accuracy	
   <th> Defense	
   <th> Evasion	
   <th> Counter Attack	
   <th> Health Increase
 </thead>
 <tbody id='droid_inventory'>
   
 </tbody>
 </table> 
 </div>
</div>

<br />
<hr />


<script>

$("#droid_name").change(function( event ) {

		jQuery.ajax({
		    url: "https://api.coindroids.com/droid?id=eq."+$("#droid_name").val(),
		    type: "GET",
		    processData: false,
		       contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			
	
			
			  index = 0;
				$("#droid_class").html(data[index].droid_class);
				$("#droid_experience").html(data[index].experience);
				$("#droid_level").html(data[index].level);
				$("#droid_purse").html((data[index].purse_current/10000000) + "/" + (data[0].purse_max/10000000)+ " TBTC");
		  	    $("#droid_health").html(data[index].health_current + "/" + data[0].health_max);
		  	    
		  	    if (data[index].attack_address == null) {
		  	    	$("#droid_attack_address").html("<i>Your attack address has not be assigned. You need to complete you first wallet syncronization process first.");
		  	    } else {
		  	    	$("#droid_attack_address").html(data[index].attack_address + "<br><img src='https://chart.googleapis.com/chart?cht=qr&chl="+data[index].attack_address+"&chs=180x180&choe=UTF-8&chld=L|2' alt=''>")
		  	    }
		  	    
		  	    $("#droid_build").empty();
		  		for (build_index = data[index].build.length - 1; build_index >= 0; --build_index) {
		  			$("#droid_build").append("<tr><th>"+data[index].build[build_index].name+"<td>"+data[index].build[build_index].item_type+"<td>"+data[index].build[build_index].damage+"<td>"+data[index].build[build_index].accuracy+"<td>"+data[index].build[build_index].defense+"<td>"+data[index].build[build_index].evasion+"<td>"+data[index].build[build_index].counter_attack+"<td>"+data[index].build[build_index].health_increase);
		  		}
		  		
		  		$("#droid_inventory").empty();
		  		if (data[index].inventory != null) {
			  		for (inventory_index = data[index].inventory.length - 1; inventory_index >= 0; --inventory_index) {
			  			$("#droid_inventory").append("<tr><th>"+data[index].inventory[inventory_index].name+"<td>"+data[index].inventory[inventory_index].item_type+"<td>"+data[index].inventory[inventory_index].damage+"<td>"+data[index].inventory[inventory_index].accuracy+"<td>"+data[index].inventory[inventory_index].defense+"<td>"+data[index].inventory[inventory_index].evasion+"<td>"+data[index].inventory[inventory_index].counter_attack+"<td>"+data[index].inventory[inventory_index].health_increase);
			  		}
		  		} else {
		  		$("#droid_inventory").append("<th> Inventory is empty. <td><td><td><td><td><td><td> ");
		  		}
	
		 	get_reg_qr(data[index].id);
		    
		    console.log("HTTP Request Succeeded: " + jqXHR.status);
		    console.log(data);
		})
		.fail(function(jqXHR, textStatus, errorThrown) {
		    console.log("HTTP Request Failed");
		})
		.always(function() {
		       $("#submit-lookup").show();
			   $("#submit-lookup-hidden").hide();
		});

});

</script>


