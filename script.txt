$(document).ready(function() {
  reload_user();

});

function reload_user(){
    $.ajax({
    method: "get",
    url: "http://dummy.restapiexample.com/api/v1/employees",
    datatype: "json",
    success: function(data) {
		var rs = data.data;
		if(rs){
			var txt = "";
			rs.forEach(function(d){
				txt += "<tr>";
				txt += "<td>"+d.id+"</td>"
				txt += "<td>"+d.employee_name+"</td>";
				txt += "<td>"+d.employee_salary+"</td>";
				txt += "<td>"+d.employee_age+"</td>";
				txt += "</tr>";
			});
			$("#table").html(txt);	
		}
    },
    error: function() {
      alert("error");
    },
    complete: function(){
      console.log("Completed");
    }
  });  
}