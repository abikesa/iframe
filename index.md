
<!DOCTYPE html>
<html>
<head>
    <title>Flight Tracker</title>
    <style>
        #flightInfo {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
    </style>
</head>
<body>
    <div id="flightInfo">
        <h1>Flight BEL455</h1>
        <pre id="data"></pre>
    </div>

    <script>
        async function fetchFlightData() {
            const username = 'your_flightaware_username';
            const apiKey = 'your_flightaware_api_key';
            const response = await fetch('https://flightxml.flightaware.com/json/FlightXML2/InFlightInfo', {
                headers: {
                    'Authorization': 'Basic ' + btoa(username + ':' + apiKey)
                }
            });
            const data = await response.json();
            document.getElementById('data').innerText = JSON.stringify(data, null, 2);
        }

        fetchFlightData();
    </script>
</body>
</html>
