# LandingPage
A coming soon page, also known as a pre-launch page before a website can go live

<?php

/* connect to the DB using PDO (PHP PDO) I will give you the host, user and password.

*/

// Host Name
$dbhost = 'localhost';

//Port Name

$port = '3306';

// Database Name
$dbname = 'fashiony_ogs';

// Database Username
$dbuser = 'root';

// Database Password
$dbpass = '';


	$pdo = new PDO("mysql:host={$dbhost};port={$port};dbname={$dbname}", $dbuser, $dbpass);
	$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);


$pdo = new PDO('mysql:host=localhost;port=3306;dbname=fashiony_ogs', 'root', '');
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);


#create one page to connect the the test db using PDO, do a query, and display the result. 


$statement = $pdo->prepare('SELECT * FROM tbl_product WHERE  p_name LIKE a%');
$statement->execute();
$products = $statement->fetchAll(PDO::FETCH_ASSOC);
foreach ($products as $row)
{
  echo $row['p_name']. '<br>';  
}


$pdo = new PDO('mysql:host=localhost;port=3306;dbname=products_crud', 'root', '');
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

$statement = $pdo->prepare('SELECT * FROM products ORDER BY create_date DESC');
$statement->execute();
$products = $statement->fetchAll(PDO::FETCH_ASSOC);




$statement = $pdo->prepare('DELETE FROM products WHERE id = :id');
$statement->bindValue(':id', $id);
$statement->execute();

// Saving data into the main table tbl_color
$statement = $pdo->prepare("INSERT INTO tbl_color (color_name) VALUES (?)");
$statement->execute(array($_POST['color_name']));


// updating into the database
$statement = $pdo->prepare("UPDATE tbl_color SET color_name=? WHERE color_id=?");
$statement->execute(array($_POST['color_name'],$_REQUEST['id']));

$success_message = 'Color is updated successfully.';


// Delete from tbl_color
$statement = $pdo->prepare("DELETE FROM tbl_color WHERE color_id=?");
$statement->execute(array($_REQUEST['id']));

// Order by
$statement = $pdo->prepare("SELECT * FROM tbl_color ORDER BY color_id ASC");
            	$statement->execute();
            	$result = $statement->fetchAll(PDO::FETCH_ASSOC);	

 $statement = $pdo->prepare("UPDATE tbl_product SET p_qty=? WHERE p_id=?");
  $statement->execute(array($final,$row1['product_id']));

  $statement = $pdo->prepare("SELECT * FROM tbl_product WHERE p_is_active=? ORDER BY p_id DESC LIMIT ".$total_latest_product_home);
  $statement->execute(array(1));
  $result = $statement->fetchAll(PDO::FETCH_ASSOC);                            
          foreach ($result as $row)
                 {
                    
                 }


/*

SELECT * FROM Customers
WHERE Country = 'Mexico';

UPDATE Customers
SET PostalCode = 00000
WHERE Country = 'Mexico';

SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';

SELECT * FROM Customers
WHERE CustomerName LIKE '%or%';

SELECT * FROM Customers
ORDER BY Country;

SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country;

The SQL query below says "return only 10 records, start on record 16 (OFFSET 15)":

$sql = "SELECT * FROM Orders LIMIT 10 OFFSET 15";



Assume we wish to select all records from 1 - 30 (inclusive) from a table called "Orders"

$sql = "SELECT * FROM Orders LIMIT 30";



*/




#Also some scripts to debug (where we use print_r, var_dump) 
$a = array("red", "green", "blue");
print_r($a);

echo "<br>";

$b = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
print_r($b);


#var_dump Dump information about different variables:

$a = 32;
echo var_dump($a) . "<br>";

$b = "Hello world!";
echo var_dump($b) . "<br>";

$c = 32.5;
echo var_dump($c) . "<br>";

$d = array("red", "green", "blue");
echo var_dump($d) . "<br>";

$e = array(32, "Hello world!", 32.5, array("red", "green", "blue"));
echo var_dump($e) . "<br>";

// Dump two variables
echo var_dump($a, $b) . "<br>";

#checking array count - Return the number of elements in an array:

$cars=array("Volvo","BMW","Toyota");
echo count($cars);

#foreach of arrays

$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $value) {
  echo "$value <br>";
}

$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

foreach($age as $x => $val) {
  echo "$x = $val<br>";
}

#how to start and use object arrays

class Motorcycle
{
    public $name;
    public $type;
}

$bike1 = new Motorcycle();
$bike1->name = 'Husqvarna';
$bike1->type = 'dirt';
$bike2 = new Motorcycle();
$bike2->name = 'Goldwing';
$bike2->type = 'touring';
$bikes = array($bike1, $bike2);

print_r($bikes);

#stdClass is a another great PHP feature. You can create a anonymous PHP class. Lets check an example.



$objArr = new StdClass(); 
$objArr->name = 'Walter';
$objArr->age = '20';

foreach($objArr as $elements) { 
echo $element; 

}

echo $objArr->age; 


#Loop Through an Associative Array
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

foreach($age as $x => $x_value) {
  echo "Key=" . $x . ", Value=" . $x_value;
  echo "<br>";
}

$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
echo "Peter is " . $age['Peter'] . " years old.";


$array['name'] = 'Walter';
$array['age'] = 20;

//STATIC FUNCTION

class greeting {
  
  public static function welcome() 
  {
    echo "Hello Walter!";
  }
}

// Call static method
greeting::welcome();

/* Use static function as a counter */
  
class solution {
      
  static $count;
    
  public static function getCount() {
      return self::$count++;
  }
}

solution::$count = 1;

for($i = 0; $i < 5; ++$i) {
  echo 'The next value is: '. 
  solution::getCount() . "\n";
}



#This example shows how to encode an associative array into a JSON object:


$age = array("Peter"=>35, "Ben"=>37, "Joe"=>43);

echo json_encode($age);


#This example shows how to encode an indexed array into a JSON array:


$cars = array("Volvo", "BMW", "Toyota");

echo json_encode($cars);


# initialise normal functions in PHP

Function add($a, $b)
{
    return $a + $b;
}

function subtract($a, $b)
{
    return $a - $b;
}

require_once 'math.php';

echo add(4, 5).'<br>';
echo subtract(9, 4);


#Return a new DateTime object, and then format the date:

$date=date_create("2013-03-15");
echo date_format($date,"Y/m/d H:i:s");


// Print current date
echo date('Y-m-d H:i:s') . '<br>';

// Print yesterday
echo date('Y-m-d H:i:s', time() - 60 * 60 * 24) . '<br>';

// Different format: https://www.php.net/manual/en/function.date.php
echo date('F j Y, H:i:s') . '<br>';

// Print current timestamp
echo time() . '<br>';

// Parse date: https://www.php.net/manual/en/function.date-parse.php
$dateString = '2020-02-06 12:45:35';
$parsedDate = date_parse($dateString); 
echo '<pre>';
var_dump($parsedDate);
echo '</pre>';

// Parse date from format: https://www.php.net/manual/en/function.date-parse-from-format.php
$dateString = 'February 4 2020 12:45:35';

$parsedDate = date_parse_from_format('F j Y H:i:s', $dateString);
echo '<pre>';
var_dump($parsedDate);
echo '</pre>';




#loops

// while
while (true) { // Infinite loop: DON'T run this
  // Do something constantly
}

// Loop with $counter
$counter = 0; // When counter is 10??
while ($counter < 10) {
  echo $counter.'<br>';
  // if ($counter > 5) break;
  $counter++;
}

// do - while
$counter = 0; // When counter is 10?
do {
  // Do some code right here
  $counter++;
} while ($counter < 10);

// for
for ($i = 0; $i < 10; $i++) {
  echo $i."<br>";
}

// foreach
$fruits = ["Banana", "Apple", "Orange"];
foreach ($fruits as $i => $fruit) {
  echo $i . ' ' . $fruit . '<br>';
}

// Iterate Over associative array.
$person = [
  'name' => 'Brad',
  'surname' => 'Traversy',
  'age' => 30,
  'hobbies' => ['Tennis', 'Video Games'],
];
foreach ($person as $key => $value) {
  if ($key === 'hobbies') {
      break;
  }
  echo $key . ' ' . $value . '<br>';
}


//cookies

setcookie('name', 'Zura', time() + 60);

echo '<pre>';
var_dump($_COOKIE);
echo '</pre>';

// How to update cookie
setcookie('name', 'Bob', time() + 2 * 60);

// How to delete cookie

setcookie('name', 'Bob', time() - 1);

#sessions


session_start();
echo session_id();

$_SESSION['page_count'] = $_SESSION['page_count'] ?? 0;
$_SESSION['page_count']++;

if ($_SESSION['page_count'] > 10){
    echo "Thank you for visiting our website 10 times";
    session_unset();
    session_destroy();
}

?>

<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
<h1>My Awesome page visited: <?php echo $_SESSION['page_count'] ?? 0 ?></h1>
</body>
</html>


#file handling

$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
echo fread($myfile,filesize("webdictionary.txt"));
fclose($myfile);


$filename = "demo.txt";
$file = fopen( $filename, 'r' );
$size = filesize( $filename );
$filedata = fread( $file, $size );


$file = fopen("demo.txt", 'r');
//some code to be executed
fclose($file);





?>
                   



