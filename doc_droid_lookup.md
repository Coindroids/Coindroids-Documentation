---
title: Droid Lookup
tags: [starting, droids, model]
keywords: starting, droid, models 
last_updated: November 21, 2015
summary: "Droid Lookup"

---


<br />

<script> 
$(document).ready(function(){
$("#submit-creation-hidden").hide();
$("#droid_details_1").hide();
$("#droid_details_2").hide();

});

</script>

 

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
		    url: "https://api.coindroids.com/droid",
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
				$("#droid_purse").html((data[index].purse_current/100) + "/" + (data[0].purse_max/100)+ " bits");
		  	    $("#droid_health").html(data[index].health_current + "/" + data[0].health_max);
		  	    
		  	    if (data[index].attack_address == null) {
		  	    	$("#droid_attack_address").html("<i>Attack address has not be assigned. This droid has not been synced with a wallet.");
		  	    } else {
		  	    	var qrtext = encodeURIComponent("bitcoin://" + data[index].attack_address + "?message=Attack " + data[index].name);
		  	    	$("#droid_attack_address").html(data[index].attack_address + "<br><img src='https://chart.googleapis.com/chart?cht=qr&chl="+qrtext+"&chs=180x180&choe=UTF-8&chld=L|2' alt=''>")
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
		
		 <div>Purse: <span id='droid_purse'  title="100 bits = 10000 satoshis = 0.0001 XTN"></span></div>
	 </div>
	 <div >
		<h3>Attack Address </h3>
		<span id='droid_attack_address'></span>
		<br>	
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
				$("#droid_purse").html((data[index].purse_current/100) + "/" + (data[0].purse_max/100)+ " bits");
		  	    $("#droid_health").html(data[index].health_current + "/" + data[0].health_max);
		  	    
		  	    if (data[index].attack_address == null) {
		  	    	$("#droid_attack_address").html("<i>Attack address has not be assigned. This droid has not been synced with a wallet.");
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


