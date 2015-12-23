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
function calculateFocus(blockHash, droidID) {
    var focus_input = blockHash + 'FOCUS' + droidID.toString();
    var focus_hash = CryptoJS.SHA256(focus_input).toString(CryptoJS.enc.Hex);
    var first_byte = parseInt(focus_hash.substring(0, 2), 16);

    return first_byte / 255.0;
};

function calculateEnergy(blockHash, droidID) {
    var energy_input = blockHash + 'ENERGY' + droidID.toString();
    var energy_hash = CryptoJS.SHA256(energy_input).toString(CryptoJS.enc.Hex);
    var first_byte = parseInt(energy_hash.substring(0, 2), 16);

    return first_byte / 255.0;
};

function makeGradientColor(color1, color2, percent) {
    var newColor = {};

    function makeChannel(a, b) {
        return(a + Math.round((b-a)*(percent/100)));
    }

    function makeColorPiece(num) {
        num = Math.min(num, 255);   // not more than 255
        num = Math.max(num, 0);     // not less than 0
        var str = num.toString(16);
        if (str.length < 2) {
            str = "0" + str;
        }
        return(str);
    }

    newColor.r = makeChannel(color1.r, color2.r);
    newColor.g = makeChannel(color1.g, color2.g);
    newColor.b = makeChannel(color1.b, color2.b);
    newColor.cssColor = "#" + 
                        makeColorPiece(newColor.r) + 
                        makeColorPiece(newColor.g) + 
                        makeColorPiece(newColor.b);
    return(newColor);
}

$(document).ready(function(){
        var current_blockhash;
        jQuery.ajax({
        	url: "https://api.coindroids.com/currency?id=eq.1",
		    type: "GET",
		    processData: false,
		    contentType: 'application/json'
        })
        .done(function(data, textStatus, jqXHR) {
            current_blockhash = data[0].last_ingested.block_hash;
        });
	
		jQuery.ajax({
		    url: "https://api.coindroids.com/droid?is_active=is.true&order=purse_current.desc,level.asc",
		    type: "GET",
		    processData: false,
		    contentType: 'application/json',
			})
		.done(function(data, textStatus, jqXHR) {
			current_droid = '';
			for (index = data.length - 1; index >= 0; --index) { 
				if (current_droid != data[index].id) {

                    var droidID = data[index].id;
					$("#droid_list").prepend("<div id='droid_"+droidID+"'><div class='row'><div class='col-lg-2' ><b>"+data[index].name+"</b> id: " + data[index].id + ", <i>Level "+data[index].level+" </i></div><div class='col-lg-6 text-right' ></div></div></div>")

					$("#droid_"+droidID).append("<div class='row'><div class='col-lg-4'>Purse "+create_progress_bar((data[index].purse_current/100),(data[index].purse_max/100))+"</div><div class='col-lg-4 '>Health "+create_progress_bar(data[index].health_current,data[index].health_max)+"</div></div>");

                    var focus_name = "focusChart_" + droidID.toString();
                    var energy_name = "energyChart_" + droidID.toString();
					var qrtext = encodeURIComponent("bitcoin://" + data[index].attack_address + "?message=Attack " + data[index].name);

					$("#droid_"+droidID).append("<div class='row'><div class='col-lg-8 text-center'>"+((data[index].attack_address == null)?'Inactive':('<img src="https://chart.googleapis.com/chart?cht=qr&chl='+qrtext+'&chs=180x180&choe=UTF-8&chld=L|2" alt="">'+data[index].attack_address+'<canvas id="'+focus_name+'" width="100" height="100"></canvas>&nbsp;&nbsp;<canvas id="'+energy_name+'" width="100" height="100"></canvas></p>'))+ '</div></div>');

                    var red = {r:255, g:0, b:0};
                    var green = {r:0, g:255, b:0};

                    var focus = Math.round(calculateFocus(current_blockhash, droidID) * 100);
                    var energy = Math.round(calculateEnergy(current_blockhash, droidID) * 100);

                    var focusColor = makeGradientColor(red, green, focus);
                    var energyColor = makeGradientColor(red, green, energy);


					var focusData = [{value: 100-focus,color:"white"},{value: focus,color:focusColor.cssColor,label:"Focus"}];
					var energyData = [{value: 100-energy,color:"white"},{value: energy,color:energyColor.cssColor,label:"Energy"}];

					var doughnutOptions = {segmentShowStroke: true, segmentStrokeColor: '#000000', segmentStrokeWidth: 1, animationEasing: "easeOutBounce"};

					var focus_ctx = document.getElementById(focus_name).getContext("2d");
					var focusChart = new Chart(focus_ctx).Doughnut(focusData, doughnutOptions);

					var energy_ctx = document.getElementById(energy_name).getContext("2d");
					var energyChart = new Chart(energy_ctx).Doughnut(energyData, doughnutOptions);

					$("#droid_"+droidID).append("<div class='row'><div class='col-lg-8'><hr></div></div>");	
					
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
	
	return '<div class="progress"><div class="progress-bar" role="progressbar"  style=" color: black; width: ' + Math.round((now/max)*100) + '%;" ><span style="min-width: 100px; overflow:visible; ">' + now.toLocaleString('en')+'/'+max.toLocaleString('en') +' bits</span></div></div>';

}

</script>


<div class="container" id='droid_list'>

</div>



<br />

