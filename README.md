# multi-select-to-set-desired-values-as-selected-on-any-event
multi select to set desired values as selected on any event using javascript

function onView() {
		
		
		var userGrp = $("#userGrp option:selected").val();
		var userList = $('#userList');
		
		if(null==userGrp || userGrp=="")
		 {
		 $('input[type="submit"]').prop('disabled', true);
		 }
		else
			{
			 $('input[type="submit"]').prop('disabled', false);
			}
		$.getJSON(
				'getUserList.action',
				{
					userGrp : userGrp
				},
				function(jsonResponse) {
				
				$("#userList option:selected").prop("selected", 0);
				$("#userList option:selected").removeProp("selected");
				
				$.each(jsonResponse, function(key, value) {	
						
						 $("#userList").find("option[value="+value+"]").prop('selected', 1);
				});
			});
	}
	
