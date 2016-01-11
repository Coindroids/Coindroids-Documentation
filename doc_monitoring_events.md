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
 
				// [Amount] [TXID, index]
				// [Droid 1] has attacked [Droid 2], performing [Net Damage]. [Droid 2] was destroyed in the attack.
				// [Droid 1] has attacked [Droid 2], but the attack was evaded.
				// [Droid X] Leveled up to [new level]
				
			
				
				oc =  processOutcomes(data[index].outcomes);
				
				if (data[index].action_type == 'Attack') {
						if (data[index].droid_id != null) {
						   if (oc[data[index].target_id]['Droid destroyed'] != null) {
							if (oc[data[index].target_id]['Droid destroyed'] == true) {
								var destroyed_text = data[index].target_name + ' was destroyed in the attack.';
							} else {
								var destroyed_text = '';
							}
							} else {
								var destroyed_text = '';
							}
					
							$("#"+data[index].block_hash).append("<div class='row'><div class='col-md-9 text-left'>"+ data[index].droid_name + " ("+ data[index].player_username+") has attacked "+ data[index].target_name + " performing "+oc[data[index].target_id]['Net damage taken']+" of damage. "+destroyed_text+"</div></div>");
						} else {
							$("#"+data[index].block_hash).append("<div class='row'><div class='col-md-9 text-left'>some droid has tried to attack "+ data[index].target_name + ", but they attacked anonymously. Refund performed</div></div>");
						}
				} 
				
				
				if (data[index].action_type == 'Item Purchase') {
				
						$("#"+data[index].block_hash).append("<div class='row'><div class='col-md-9 text-left'>"+ data[index].droid_name + " ("+ data[index].player_username+") has bought item: " +data[index].target_id+ "</div></div>");
				} 				
				
				if (data[index].action_type == 'Registration') {
						
				
						$("#"+data[index].block_hash).append("<div class='row'><div class='col-md-9 text-left'>"+ data[index].droid_name + " ("+ data[index].player_username+") has joined the fight!</div></div>");
				} 

				if (data[index].action_type == 'Change') {
						
				
						$("#"+data[index].block_hash).append("<div class='row'><div class='col-md-9 text-left'>Coindroids Settlement Transaction</div></div>");
				} 
				
					$("#"+data[index].block_hash).append("<div class='row'><div class='col-md-1'>"+ data[index].value/100 + "&nbsp;bits</div><div class='col-md-8'><a href='https://www.blocktrail.com/tBTC/tx/" + data[index].txid +"'>" + data[index].txid +" ("+data[index].tx_vout+ ")</i></a></div></div>");
				
				$("#"+data[index].block_hash).append("<div id='tx_po_" + data[index].txid + data[index].tx_vout+"' class='container'></div><div id='tx_po_" + data[index].txid +"' class='container'></div>");
				
								$("#"+data[index].block_hash).append("<div id='tx_oc_" + data[index].txid + data[index].tx_vout+"' class='container'></div><div id='tx_po_" + data[index].txid +"' class='container'></div>");

			if (data[index].outcomes != null) {
				for (outcome_index = data[index].outcomes.length - 1; outcome_index >= 0; --outcome_index) {
					$("#tx_oc_"+data[index].txid + data[index].tx_vout).append("<div class='row'><div class='col-md-1'></div><div class='col-md-3 '>"+ data[index].outcomes[outcome_index].outcome_type+ " </div><div class='col-md-1 '>Droid&nbsp;ID:"+ data[index].outcomes[outcome_index].droid_id+ "  </div><div class='col-md-1 '>"+ data[index].outcomes[outcome_index].value_to+ "</div></div>");

				}
			}

				if (data[index].payouts != null){
					for (payout_index = data[index].payouts.length - 1; payout_index >= 0; --payout_index) {
						$("#tx_po_"+data[index].txid + data[index].tx_vout).append("<b>Payout</b> (ID "+ data[index].payouts[payout_index].payout_id+ ")<div class='row'><div class='col-md-4 '>"+ data[index].payouts[payout_index].address+ " </div><div class='col-md-2 '>Player ID:"+ data[index].payouts[payout_index].player_id+ "  </div><div class='col-md-1 text-left'>Amount:"+ (data[index].payouts[payout_index].amount/100)+ "bits</div></div>");
						}
				}
			

$("#"+data[index].block_hash).append("<div>&nbsp;<br \></div>");
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

function processOutcomes (outcomes) {
	var oc = {};
	var tmp = {};
	if (outcomes != null) {
		for (outcome_index = outcomes.length - 1; outcome_index >= 0; --outcome_index) {

			if (outcomes[outcome_index].droid_id != null) {
				droid_id = outcomes[outcome_index].droid_id;
			} else {
				droid_id ='Unregistered';
			}
			
			if (oc[outcomes[outcome_index].droid_id] != null) {
				tmp = oc[droid_id];
			}
			
			if (outcomes[outcome_index].value_to != null) {
				tmp[outcomes[outcome_index].outcome_type] = outcomes[outcome_index].value_to;
				oc[droid_id] = tmp;  
			} else {
				tmp[outcomes[outcome_index].outcome_type] = true;
				oc[droid_id] = tmp;
			}
		}
	}
	return oc;
}
		

</script>


<div class="container" id='event_log'>

</div>

<br />
<hr />
