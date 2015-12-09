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
					$("#event_log").prepend("<div id='"+data[index].block_hash+"'><h2>"+data[index].block_hash+" ("+data[index].block_height+")</h2></div>")
					current_block = data[index].block_hash;
				} 
				$("#"+data[index].block_hash).append("<div>"+ data[index].action_type + " (" + data[index].txid +","+data[index].tx_vout+ ")</div>");
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


<div class="container" id='event_log'>

</div>

<br />
<hr />
