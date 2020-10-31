<?php
$servername = "localhost";
$username = "root";
$password = "234@#$";
$dbname = "myDB";

$conn = new mysqli($servername, $username, $password,$dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
else
echo "connection has been established-------\n";


$sql = "CREATE DATABASE ABC";
if ($conn->query($sql) === TRUE) {
    echo "Database created successfully--------\n";
} else {
    echo "Error creating database: " . $conn->error;
}
$sql = "CREATE TABLE DEMO(
id INT(6) PRIMARY KEY, 
firstname VARCHAR(30) NOT NULL,
lastname VARCHAR(30) NOT NULL,
email VARCHAR(50)
)";

if ($conn->query($sql) === TRUE) {
    echo "Table DEMO created successfully----------\n";
} else {
    echo "Error creating table: " . $conn->error;
}
$sql = "INSERT INTO DEMO(id,firstname, lastname, email)
VALUES (21,'SARFARAZ', 'KHAN', 'sarkhan086@gmail.com')";

if ($conn->query($sql) === TRUE) {
    echo "Values inserted successfully----------";
} else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}
$sql = "SELECT * FROM DEMO
$result = $conn->query($sql);
if ($result->num_rows > 0) {
    while($row = $result->fetch_assoc()) {
        echo "id : " . $row["id"]. " - Name: " . $row["firstname"]. " " . $row["lastname"]." Email: ". $row["email"]. "<br>";
    }
} else {
    echo "0 results";
}

$conn->close();
?>

