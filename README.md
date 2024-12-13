<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Query Parameter Pop-Up</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        .popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: white;
            padding: 20px;
            border: 2px solid #ccc;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            z-index: 1000;
        }

        .popup-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 999;
        }

        .popup .close-btn {
            background-color: #ff4c4c;
            color: white;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
            font-size: 16px;
        }

        .popup .close-btn:hover {
            background-color: #ff0000;
        }
    </style>
</head>
<body>
    <h1>Welcome to the Information Page</h1>

    <div class="popup-overlay" id="popup-overlay"></div>
    <div class="popup" id="popup">
        <h2>Summary Information</h2>
        <p id="info-summary">Loading...</p>
        <button class="close-btn" id="close-btn">Close</button>
    </div>

    <script>
        // Function to get query parameter by name
        function getQueryParam(name) {
            const urlParams = new URLSearchParams(window.location.search);
            return urlParams.get(name);
        }

        // Show the popup with the information
        function showPopup(info) {
            document.getElementById('popup').style.display = 'block';
            document.getElementById('popup-overlay').style.display = 'block';
            document.getElementById('info-summary').innerText = `The year you selected is ${info.year}. More details: ${info.details}`;
        }

        // Close the popup
        document.getElementById('close-btn').addEventListener('click', function () {
            document.getElementById('popup').style.display = 'none';
            document.getElementById('popup-overlay').style.display = 'none';
        });

        // Main logic to extract query parameter and show popup
        window.onload = function() {
            const year = getQueryParam('year'); // Get the 'year' query parameter
            const claims = getQueryParam('ptotalclaims');
            const premiums = getQueryParam('ptotalprem');
            if (true) {
                const info = {
                    year: year,
                    details: `This is the summary for the year ${year}. Here we can provide more information or data based on the year. Total Claims is ${claims} Total Premiums is ${premiums} yay`,
                };
                showPopup(info); // Show the popup with the information
            } else {
                console.log('No year parameter found.');
            }
        };
    </script>
</body>
</html>
