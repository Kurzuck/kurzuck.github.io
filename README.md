<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch with Date and Time</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }
        .container {
            text-align: center;
        }
        .ads {
            position: absolute;
            top: 0;
            bottom: 0;
            width: 100px;
        }
        .ads-left {
            left: 0;
        }
        .ads-right {
            right: 0;
        }
    </style>
</head>
<body>
    <div class="ads ads-left">Ad Space</div>
    <div class="container">
        <div id="date"></div>
        <div id="stopwatch">00:00:00</div>
        <div id="time"></div>
    </div>
    <div class="ads ads-right">Ad Space</div>
    <script>
        function updateDateTime() {
            const now = new Date();
            document.getElementById('date').innerText = now.toDateString();
            document.getElementById('time').innerText = now.toLocaleTimeString();
        }

        let stopwatchInterval;
        let startTime;

        function startStopwatch() {
            startTime = Date.now();
            stopwatchInterval = setInterval(() => {
                const elapsedTime = Date.now() - startTime;
                const hours = Math.floor(elapsedTime / 3600000);
                const minutes = Math.floor((elapsedTime % 3600000) / 60000);
                const seconds = Math.floor((elapsedTime % 60000) / 1000);
                document.getElementById('stopwatch').innerText = 
                    `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            }, 1000);
        }

        document.addEventListener('DOMContentLoaded', () => {
            updateDateTime();
            setInterval(updateDateTime, 1000);
            startStopwatch();
        });
    </script>
</body>
</html>
