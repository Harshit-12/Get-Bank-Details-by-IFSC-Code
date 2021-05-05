# Get-Bank-Details-by-IFSC-Code
<!DOCTYPE html>
<html>
<head>
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style type="text/css">
	body{
		 background-color: #33A8FF;
		 background-size: auto;
	
		 }
input[type=text] 
{
	width: 80%;
}
input[type=submit] {
  width: 80%;
  background-color: #4CAF50;
  color: white;

  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
input[type=submit]:hover {
  background-color: #45a049;
}
div {
	margin-top: 70px;
opacity: 1.0;
width: 80%;
 border-radius: 20px;
 background-color: #f2f2f2;
 padding: 20px;
}
</style>
</head>
<body>
	<br>
	<br>

	<center>
	<div>
	<h1>Get Bank Details by IFSC Code </h1>
	<br>

	<form method="post" action="Bank.php" id="theForm">
		<b>Enter IFSC Code </b>
		<br>
		<input type="text" name='ifsc'>
		<br>
		
		<input type="submit" id="formSubmit">
	
	</form>
</div>
</center>
</body>

</html>
<!DOCTYPE html>
<html>
<head>
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Bank Detai</title>
<style type="text/css">
body{
		 background-color: #33A8FF;
		 background-size: auto;
	
	}

.header {
	background-color: #66ff33;
	width: 40%;
 border-radius: 20px;
}
	div {
	margin-top: 70px;
opacity: 1.0;
width: 90%;
 border-radius: 20px;
 background-color: #f2f2f2;
 padding: 20px;
}
</style>
</head>
<body>
<center>
	<br><br>

<div class="header"> <h1>Bank Details</h1> </div>
<div>
<?php
if(isset($_POST['ifsc'])) {
	$ifsc = $_POST['ifsc'];
	$json = @file_get_contents(
		"https://ifsc.razorpay.com/".$ifsc);
	$arr = json_decode($json);

	if(isset($arr->BRANCH)) {
		echo '<pre>';
		echo "<b>Bank:-</b>".$arr->BANK;
		echo "<br/>";
		echo "<b>Branch:-</b>".$arr->BRANCH;
		echo "<br/>";
		echo "<b>Centre:-</b>".$arr->CENTRE;
		echo "<br/>";
		echo "<b>District:-</b>".$arr->DISTRICT;
		echo "<br/>";
		echo "<b>State:-</b>".$arr->STATE;
		echo "<br/>";
		echo "<b/>Address:-</b>".$arr->ADDRESS;
		echo "<br/>";
	}
	else {
		echo "Invalid IFSC Code";
	}
}
?>
</div>
</center>
</body>
</html>

