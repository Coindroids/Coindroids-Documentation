---
title: Testnet Stats
tags: [objects]
keywords: stats, currency, droids
last_updated: November 21, 2015
summary: "Some stats for testnet"

---


<br \>


<div class="row">
          <div class="col-md-4"><span class='big_number' id='largest_payout'></span><div class="kbCaption">Largest Payout</div></div>
          <div class="col-md-4"><span class='big_number' id='overall_purse_sum'></span><div class="kbCaption">Overall Purse Sum</a></div></div>
          <div class="col-md-4"><span class='big_number' id='total_droids'></span><div class="kbCaption">Number of Droids</div></a></div>
</div>
<p>&nbsp;</p>
<div class="row">
          <div class="col-md-4"><span class='big_number' id='total_number_of_attacks'></span><div class="kbCaption"># of Attacks</div></a></div>
          <div class="col-md-4"><span class='big_number' id='total_amount_of_attacks'></span><div class="kbCaption">Sum of All Attacks</div></a></div>
          <div class="col-md-4"><span class='big_number' id='total_number_of_item_purchases'></span><div class="kbCaption"># of Item Purchases</div></a></div>
</div>


<br \>

<script> 
$(document).ready(function(){


		jQuery.ajax({
		    url: "https://api.coindroids.com/currency?id=eq.1",
		    type: "GET",
		    processData: false,
		       contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			

				$("#largest_payout").html(formatNumber(data[0].largest_payout/100) + '&nbsp;bits' );
				$("#overall_purse_sum").html(formatNumber(data[0].overall_purse_sum/100) + '&nbsp;bits' );
				$("#total_droids").html(data[0].total_droids);
				$("#total_number_of_attacks").html(data[0].total_number_of_attacks);
				$("#total_amount_of_attacks").html(formatNumber(data[0].total_amount_of_attacks/100) + '&nbsp;bits' );
				$("#total_number_of_item_purchases").html(data[0].total_number_of_item_purchases);
				
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


function formatNumber (num) {
    return num.toString().replace(/(\d)(?=(\d{3})+(?!\d))/g, "$1,")
}


</script>
    