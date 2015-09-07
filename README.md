<!-- admin.php-->
<html>
<head>
<title>Restaurant</title>
<link rel="stylesheet" href="css/style1.css" type="text/css" media="screen" />


<script type="application/javascript">

  function num(evt)
      {
         var charCode = (evt.which) ? evt.which : event.keyCode
         if (charCode > 31 && (charCode < 48 || charCode > 57))
            return false;

         return true;
      }

</script>

</head>
<body>

<form method = "post" action = "<?php $_SERVER['PHP_SELF']; ?>"
<div id="maincontainer">
<div id="header">Restaurant Details</div>
<div id="body">
<br><div class="rest-outer">
<center>
<br><h2><font color="#806517">Enter The  Following Details:</font></h2><br><br> 
<table>
<ul>
<tr><td><b><font color="#000653"><li>Name :</li></font></td><td><input type="text" name="name" value="<?php echo getvalue('name'); ?>" /> <font color="#000653"></font></b></td></tr>
<tr><td><b><font color="#000653"><li>Address:</li></font></td><td><textarea name="add" rows="3" cols="22"  value="<?php echo getvalue('add'); ?>" > </textarea> </b></td><tr>
<tr><td><b><font color="#000653"><li>Mobile:</li></font></td><td><input type="text" name="mob" onkeypress="return num(event)" maxlength="11" value="<?php echo getvalue('mob'); ?>" /></b></td><tr>
<tr><td><b><font color="#000653"><li>Phone Number:</li></font></td><td><input type="text" onkeypress="return num(event)" maxlength="11"  name="pno" value="<?php echo getvalue('pno'); ?>" /><b><font color="#000653"> </font></b></td><td></br><br>
<tr><td><b><font color="#000653"><li>E-mail Id:</li></font></td><td><input type="email" name="email" value="<?php echo getvalue('email'); ?>" /><b><font color="#000653"></font></b></td><td>
</table>
</ul>
</center>
<div class="submit-margin">
<br><br><input type="submit" value="submit" name="submit"></br></div>
</form>


<?php

if(isset($_POST['submit']))
{ 

$name=$_POST['name'];
$add=$_POST['add'];
$mob=$_POST['mob'];
$pno=$_POST['pno'];
$email=$_POST['email'];

$host="localhost";
$user="root";
$pass="";
$db="rest";


$connection = mysql_connect($host,$user,$pass) or die("unable to connect");

mysql_select_db($db) or die("unable to connect");

mysql_select_db("$db", $connection);




if(($name == NULL) || ($add == NULL) ||($mob == NULL) ||($pno == NULL) ||($email == NULL) )
{
?><center><FONT COLOR="red"><?php echo"field cannot remain empty";?></FONT></center><?php

}
else
{

	?><center><FONT COLOR="red"><?php echo"Thanks for details";?></FONT></center><?php
	mysql_query("INSERT INTO restdetails (name,add,mob,pno,email) VALUES('$name','$add','$mob','$pno','$email')");

}
}
function getvalue($val)
{
if(isset($_POST[$val]))
{
return $_POST[$val];
}
else
{
return "";
}
}


?>
<br><br><center><a href="login.php">LOGOUT</a></center>

                </center>


</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</body>
</html>

