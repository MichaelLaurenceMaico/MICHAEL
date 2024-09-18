<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $side1 = $_POST['side1'];
    $side2 = $_POST['side2'];
    $side3 = $_POST['side3'];

    // Calculate the semi-perimeter
    $s = ($side1 + $side2 + $side3) / 2;

    // Calculate the area using Heron's formula without sqrt function
    $area = $s * ($s - $side1) * ($s - $side2) * ($s - $side3);
    $area = pow($area, 0.5); // Equivalent to sqrt

    // Format the result to two decimal places
    $formatted_area = number_format($area, 2);

    // Display the result
    echo "The area of the triangle is: " . $formatted_area . " square units.";
}
?>
