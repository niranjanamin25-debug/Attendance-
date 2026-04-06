<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gothic Attendance Vault</title>
    <style>
        body {
            background-color: #0a0a0a;
            color: #d4af37;
            font-family: 'Georgia', serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .vault {
            background: #1a1a1a;
            padding: 30px;
            border: 2px solid #8b0000;
            box-shadow: 0 0 20px #8b0000;
            width: 350px;
            text-align: center;
        }
        h2 { border-bottom: 1px solid #8b0000; padding-bottom: 10px; }
        input {
            width: 100%;
            margin: 10px 0;
            padding: 10px;
            background: #000;
            color: #fff;
            border: 1px solid #444;
        }
        #fate {
            margin-top: 20px;
            font-weight: bold;
            color: #8b0000;
        }
    </style>
</head>
<body>
    <div class="vault">
        <h2>The Vault</h2>
        <input type="number" id="total" placeholder="Total Lectures Held" oninput="checkFate()">
        <input type="number" id="attended" placeholder="Lectures Attended" oninput="checkFate()">
        <div id="fate">Your fate awaits...</div>
    </div>

    <script>
        function checkFate() {
            let T = parseInt(document.getElementById('total').value);
            let A = parseInt(document.getElementById('attended').value);
            let display = document.getElementById('fate');
            
            if(T > 0 && A >= 0) {
                let current = (A / T) * 100;
                if(current < 75) {
                    let need = (3 * T) - (4 * A);
                    display.innerHTML = `Peril! Attend the next ${need} classes.`;
                } else {
                    let skip = Math.floor((A - 0.75 * T) / 0.75);
                    display.innerHTML = `Safe. You can skip ${skip} classes.`;
                }
            }
        }
    </script>
</body>
</html>
