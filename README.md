Please Visit : https://rdmsoftwaresolutions.com/dev/auto_fill_api/
------------------------------------------------------------------------------------------------------------------------------------

1) add your domain to property and verify it. sign in required  - https://rdmsoftwaresolutions.com/dev/auto_fill_api/add-property/
====================================================================================================================================
2) Insert this script into <head></head> tags
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
====================================================================================================================================
3) add this 'id' and 'list' attributes to your city <input> tag
<input  id="city" list="list_by_RDMSoftwareSolutions" />
====================================================================================================================================
4) add this DIV after the city textbox (<input> tag)
<div id="suggestions"></div>
====================================================================================================================================
5) add this 'id' to your postal code <input> tag
<input  id="postal-code"  />
====================================================================================================================================
6) add this code before </body> tag

<script>
$(document).ready(function(){
    var api = "https://rdmsoftwaresolutions.com/dev/auto_fill_api/api.php"
  $("#city").keyup(function(){
      var txt = $("#city").val();
      $.ajax({
        url:api,
        method:"POST",
        data:{suggest:txt},
        success:function(data)
        {
         $("#suggestions").html(data);
      }
     })
  });
    $("#city").blur(function(){
      var txt = $("#city").val();
      $.ajax({
        url:api,
        method:"POST",
        data:{postal_code:txt},
        success:function(data)
        {
         $("#postal-code").val(data);
      }
     })
  });
});
</script>