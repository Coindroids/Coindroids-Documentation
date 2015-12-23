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
		    headers:  {
			"Range": "0-15"
		    },
		    type: "GET",
		    processData: false,
		       contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			
			
			current_block = '';
			for (index = data.length - 1; index >= 0; --index) { 
				if (current_block != data[index].block_hash) {
	
					$("#event_log").prepend("<div id='"+data[index].block_hash+"'><div class='row'><div class='col-lg-1' ><b><a href='https://www.blocktrail.com/tBTC/block/"+data[index].block_hash+"'>"+data[index].block_height+"</a></b></div><div class='col-lg-7 text-right'></div></div></div>")
					current_block = data[index].block_hash;
				}
 
				$("#"+data[index].block_hash).append("<div class='row'><div class='col-md-2'>"+ data[index].droid_name + " ("+ data[index].player_username+")</div><div class='col-md-1'>"+ data[index].action_type + "</div><div class='col-md-2'>"+ data[index].value/100 + " bits</div><div class='col-md-2'><a href='https://www.blocktrail.com/tBTC/tx/" + data[index].txid +"'>" + data[index].txid.substring(1,10) +" ("+data[index].tx_vout+ ")</i></a></div><div class='col-md-1 text-left'></div></div><div id='tx_oc_" + data[index].txid +"' class='container'></div><div id='tx_po_" + data[index].txid +"' class='container'></div>");

				for (outcome_index = data[index].outcomes.length - 1; outcome_index >= 0; --outcome_index) {
					$("#tx_oc_"+data[index].txid).append("<div class='row'><div class='col-md-1'></div><div class='col-md-2 '>"+ data[index].outcomes[outcome_index].outcome_type+ " </div><div class='col-md-1 '>Droid ID:"+ data[index].outcomes[outcome_index].droid_id+ "  </div><div class='col-md-1 '>"+ data[index].outcomes[outcome_index].value_to+ "</div></div>");

				}

				if (data[index].payouts != null){
					for (payout_index = data[index].payouts.length - 1; payout_index >= 0; --payout_index) {
						$("#tx_po_"+data[index].txid).append("<b>Payout</b> (ID "+ data[index].payouts[payout_index].payout_id+ ")<div class='row'><div class='col-md-4 '>"+ data[index].payouts[payout_index].address+ " </div><div class='col-md-2 '>Player ID:"+ data[index].payouts[payout_index].player_id+ "  </div><div class='col-md-1 text-left'>Amount:"+ (data[index].payouts[payout_index].amount/100)+ " bits</div></div>");
						}
				}
			

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
