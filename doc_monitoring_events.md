---
title: Monitoring Events
tags: [starting, droids, model]
keywords: starting, droid, models 
last_updated: November 21, 2015
summary: "Watching the events scroll by"

---


<script> 
$(document).ready(function(){

});

</script>
 

<script> 
$(document).ready(function(){

	
		jQuery.ajax({
		    url: "https://api.coindroids.com/event?order=block_height.desc,action_type.desc",
		    type: "GET",
		    processData: false,
		       contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			
			
			current_block = '';
			for (index = data.length - 1; index >= 0; --index) { 
				if (current_block != data[index].block_hash) {
					$("#event_log").prepend("<div id='"+data[index].block_hash+"'><div class='row'><div class='col-lg-1' ><b>"+data[index].block_height+"</b></div><div class='col-lg-7 text-right'>("+data[index].block_hash+")</div></div></div>")
					current_block = data[index].block_hash;
				}
 
				$("#"+data[index].block_hash).append("<div class='row'><div class='col-md-2'>"+ data[index].droid_name + " ("+ data[index].player_username+")</div><div class='col-md-1'>"+ data[index].action_type + "</div><div class='col-md-1'>"+ data[index].value/100000000 + "TBTC</div><div class='col-md-6 text-right'>" + data[index].txid +"</div><div class='col-md-1 text-left'><i>Vout "+data[index].tx_vout+ "</i></div></div>");
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
		
});		

</script>

<div class="container" id='event_logs'>


</div>


<div class="container" id='event_log'>

</div>

<br />
<hr />
