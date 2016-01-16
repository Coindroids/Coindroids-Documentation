---
title: Item Lookup
tags: [starting, droids, model]
keywords: starting, droid, models 
last_updated: November 21, 2015
summary: "Item Lookup"

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
		    url: "https://api.coindroids.com/item?order=item_type.asc,level_required.asc",
		    type: "GET",
		    processData: false,
		       contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			
			 tmp = '';
			 current_item_type = '';
			 for (index = 0; index < data.length; index++) { 
				if (index == 0 ) {tmp = 'selected'} else { tmp = '';}
				if (current_item_type != data[index].item_type)
				{ 
					if (current_item_type != '') {
						$("#item_name").append("</optgroup>");	
					}
					$("#item_name").append("<optgroup label='"+data[index].item_type+"'>");	
					current_item_type = data[index].item_type;
				}
				$("#item_name").append("<option value="+data[index].id+" "+tmp+">"+data[index].name+"</option>");

			}
			
			  index = 0;
		
		  			//$("#droid_class").html(data[index].droid_class);
		  			$("#item_type").html(data[index].item_type);
		  			$("#description").html(data[index].description);
		  			$("#level_required").html(data[index].level_required);
		  			$("#damage").html(data[index].damage);
		  			$("#accuracy").html(data[index].accuracy);
		  			$("#defense").html(data[index].defense);
		  			$("#evasion").html(data[index].evasion);
		  			$("#counter_attack").html(data[index].counter_attack);
		  			$("#health_increase").html(data[index].health_increase);
		  			$("#lasts").html(data[index].lasts);
		  			$("#stages").html(data[index].stages);
		  			$("#stage_damage_modifier").html(data[index].stage_damage_modifier);
		  			$("#drop_scope").html(data[index].drop_scope);
		  			$("#equip_scope").html(data[index].equip_scope);
		  			
		  			var price = data[index].pricing[0].amount /100000000;
		  			var price_bits = data[index].pricing[0].amount / 100;
		  			var qrtext = encodeURIComponent("bitcoin://" + data[index].pricing[0].address + "?amount=" + price + "&message=Item%20Purchase");
		  			$("#pricing").html("To purchase, send " + price_bits + "bits to: " + data[index].pricing[0].address + "<br><img src='https://chart.googleapis.com/chart?cht=qr&chl="+qrtext+"&chs=180x180&choe=UTF-8&chld=L|2' alt=''>");

		  			//data[index].pricing[0].address
		  			//data[index].pricing[0].amount 
		  		
	
	

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



function formatNumber (num) {
    return num.toString().replace(/(\d)(?=(\d{3})+(?!\d))/g, "$1,")
}



</script>

<br>

<div class="container"  id='droid_details_1'>
<br>

 <div class="row">
 	<div >
		 <select id='item_name' style='text-transform:capitalize; font: large;' class='form-control-lg' size=5></select>
	</div>
</div>
<br>		  	
<div>
	<span id='description'></span>
</div>
<br>

<div id='pricing'></div>
<br>
 
<div>
	<table>
	
		<tr>
			<td>Item Type</td>
			<td id='item_type'></td>
		</tr>
		<tr>
			<td>Level Required*</td>
			<td id='level_required'></td>
		</tr>
		<tr>
			<td>Damage</td>
			<td id='damage'></td>
		</tr>
		<tr>
			<td>Accuracy</td>
			<td id='accuracy'></td>
		</tr>
		<tr>
			<td>Defense</td>
			<td id='defense'></td>
		</tr>
		<tr>
			<td>Evasion</td>
			<td id='evasion'></td>
		</tr>
		<tr>
			<td>Counter Attack</td>
			<td id='counter_attack'></td>
		</tr>
		<tr>
			<td>Health Increase</td>
			<td id='health_increase'></td>
		</tr>
		<tr>
			<td>Lasts</td>
			<td id='lasts'></td>
		</tr>
		<tr>
			<td>Stages</td>
			<td id='stages'></td>
		</tr>
		<tr>
			<td>Stage Damage Modifier</td>
			<td id='stage_damage_modifier'></td>
		</tr>
		<tr>
			<td>Drop Scope</td>
			<td id='drop_scope'></td>
		</tr>
		<tr>
			<td>Equip Scope</td>
			<td id='equip_scope'></td>
		</tr>
	</table>
</div>

<br \>

<i>* Level requirements are currently intentionally ignored.</i> 

<br />
<hr />


<script>

$("#item_name").change(function( event ) {

		jQuery.ajax({
		    url: "https://api.coindroids.com/item?id=eq."+$("#item_name").val(),
		    type: "GET",
		    processData: false,
		       contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			
	
			
			  index = 0;
			    
			    
			    		  			//$("#droid_class").html(data[index].droid_class);
		  			$("#item_type").html(data[index].item_type);
		  			$("#description").html(data[index].description);
		  			$("#level_required").html(data[index].level_required);
		  			$("#damage").html(data[index].damage);
		  			$("#accuracy").html(data[index].accuracy);
		  			$("#defense").html(data[index].defense);
		  			$("#evasion").html(data[index].evasion);
		  			$("#counter_attack").html(data[index].counter_attack);
		  			$("#health_increase").html(data[index].health_increase);
		  			$("#lasts").html(data[index].lasts);
		  			$("#stages").html(data[index].stages);
		  			$("#stage_damage_modifier").html(data[index].stage_damage_modifier);
		  			$("#drop_scope").html(data[index].drop_scope);
		  			$("#equip_scope").html(data[index].equip_scope);
		  			
		  			var price = data[index].pricing[0].amount /100000000;
		  			var price_bits = data[index].pricing[0].amount / 100;
		  			var qrtext = encodeURIComponent("bitcoin://" + data[index].pricing[0].address + "?amount=" + price + "&message=Item%20Purchase");
		  			$("#pricing").html("To purchase, send " + price_bits + "bits to: " + data[index].pricing[0].address + "<br><img src='https://chart.googleapis.com/chart?cht=qr&chl="+qrtext+"&chs=180x180&choe=UTF-8&chld=L|2' alt=''>");
			    
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


