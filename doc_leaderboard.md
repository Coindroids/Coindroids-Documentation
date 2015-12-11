---
title: The Leaderboard
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
		    url: "https://api.coindroids.com/droid?order=purse_current.desc,level.asc",
		    type: "GET",
		    processData: false,
		       contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			
			
			current_droid = '';
			for (index = data.length - 1; index >= 0; --index) { 
				if (current_droid != data[index].id) {
					$("#droid_list").prepend("<div id='"+data[index].droid_id+"'><div class='row'><div class='col-lg-2' ><b>"+data[index].name+"</b> <i>Level "+data[index].level+" </i></div><div class='col-lg-6 text-right' ></div></div></div>")

					$("#"+data[index].block_hash).append("<div class='row'><div class='col-lg-4'>Purse "+create_progress_bar((data[index].purse_current/10000),(data[index].purse_max/10000))+"</div><div class='col-lg-4 '>Health "+create_progress_bar(data[index].health_current,data[index].health_max)+"</div></div>");

					
					$("#"+data[index].block_hash).append("<div class='row'><div class='col-lg-8 text-center'>"+((data[index].attack_address == null)?'Inactive':('<img src="https://chart.googleapis.com/chart?cht=qr&chl='+data[index].attack_address+'&chs=180x180&choe=UTF-8&chld=L|2" alt="">'+data[index].attack_address+'</p>'))+"</div></div>");

						
					$("#"+data[index].block_hash).append("<div class='row'><div class='col-lg-8'><hr></div></div>");	
					
					current_droid = data[index].id;
					
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


function create_progress_bar(now, max){
	
	return '<div class="progress"><div class="progress-bar" role="progressbar"  style=" color: black; width: ' + Math.round((now/max)*100) + '%;" ><span style="min-width: 100px; overflow:visible; ">' + now+'/'+max +'</span></div></div>';

}

</script>


<div class="container" id='droid_list'>

</div>



<br />

