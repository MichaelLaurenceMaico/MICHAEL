<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Triangle Area Calculator</title>
</head>
<body>
    <h1>Triangle Area Calculator</h1>
    <form method="post">
        <label for="side1">Side 1:</label>
        <input type="number" id="side1" name="side1" step="any" required><br><br>
        <label for="side2">Side 2:</label>
        <input type="number" id="side2" name="side2" step="any" required><br><br>
        <label for="side3">Side 3:</label>
        <input type="number" id="side3" name="side3" step="any" required><br><br>
        <input type="submit" value="Calculate Area">
    </form>


    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        // Get the side lengths from the form
        $side1 = $_POST['side1'];
        $side2 = $_POST['side2'];
        $side3 = $_POST['side3'];
        
        $s = ($side1 + $side2 + $side3) / 2;

    
        $areaSquared = $s * ($s - $side1) * ($s - $side2) * ($s - $side3);

    
        function sqrtApprox($number) {
            if ($number <= 0) return 0;
            $approx = $number;
            $betterApprox = ($approx + $number / $approx) / 2;
            while (abs($approx - $betterApprox) > 0.00001) {
                $approx = $betterApprox;
                $betterApprox = ($approx + $number / $approx) / 2;
            }
            return $approx;
        }

        $area = sqrtApprox($areaSquared);

      
        echo "<h2>Area of the Triangle:</h2>";
        echo "<p>The area of the triangle is " . number_format($area, 2) . "</p>";
    }
    ?>
</body>
</html>
