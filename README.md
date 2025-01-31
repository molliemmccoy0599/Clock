# Clock
Dachshund clock, based on the popular Kit-Cat Clock 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dachshund Clock</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background-color: white;
            font-family: Arial, sans-serif;
        }

        .clock-container {
            width: 300px;
            height: 600px;
            position: relative;
        }

        #dachshund-clock {
            width: 100%;
            height: 100%;
        }

        .clock-face {
            fill: white;
            stroke: black;
            stroke-width: 2;
        }

        .dachshund-body {
            fill: #B22222;
            stroke: black;
            stroke-width: 2;
        }

        .hand {
            transform-origin: 100px 250px; /* Match the center of the clock face */
            transition: transform 0.1s cubic-bezier(0.4, 2.08, 0.55, 0.44);
        }

        .tail {
            animation: wag 1s infinite alternate ease-in-out;
        }

        @keyframes wag {
            0% { transform: rotate(-5deg); }
            100% { transform: rotate(5deg); }
        }

        .clock-number {
            font-size: 16px;
            text-anchor: middle;
            dominant-baseline: middle;
        }
    </style>
</head>
<body>
    <div class="clock-container">
        <svg id="dachshund-clock" viewBox="0 0 200 600">
            <!-- Long vertical body - clock face -->
            <path class="dachshund-body" 
                  d="M60 100 Q60 80 80 80 L120 80 Q140 80 140 100 L140 400 Q140 420 120 420 L80 420 Q60 420 60 400 Z" />
            
            <!-- Head - front facing -->
            <path class="dachshund-body" 
                  d="M70 40 Q100 35 130 40 Q140 50 140 70 Q140 85 100 90 Q60 85 60 70 Q60 50 70 40" />
            
            <!-- Ears -->
            <path class="dachshund-body" d="M60 50 Q55 60 65 70" />
            <path class="dachshund-body" d="M140 50 Q145 60 135 70" />
            
            <!-- Snout -->
            <ellipse cx="100" cy="65" rx="25" ry="15" class="dachshund-body" />
            
            <!-- Eyes -->
            <ellipse cx="80" cy="50" rx="3" ry="4" fill="black" />
            <ellipse cx="120" cy="50" rx="3" ry="4" fill="black" />
            
            <!-- Nose -->
            <circle cx="100" cy="60" r="5" fill="black" />
            
            <!-- Mouth -->
            <path d="M90 70 Q100 75 110 70" fill="none" stroke="black" stroke-width="1.5" />
            
            <!-- Collar -->
            <path d="M70 80 L130 80 Q135 85 130 90 L70 90 Q65 85 70 80" 
                  fill="#4169E1" stroke="#00008B" stroke-width="2" />
            
            <!-- Collar Tag -->
            <circle cx="100" cy="85" r="5" fill="#FFD700" stroke="#DAA520" stroke-width="1" />
            
            <!-- Clock face -->
            <circle class="clock-face" cx="100" cy="250" r="70" />
            
            <!-- Clock hands -->
            <g id="hour-hand" class="hand">
                <line x1="100" y1="250" x2="100" y2="220" 
                      stroke="black" stroke-width="4" stroke-linecap="round" />
            </g>
            <g id="minute-hand" class="hand">
                <line x1="100" y1="250" x2="100" y2="190" 
                      stroke="black" stroke-width="3" stroke-linecap="round" />
            </g>
            <g id="second-hand" class="hand">
                <line x1="100" y1="250" x2="100" y2="185" 
                      stroke="red" stroke-width="1" stroke-linecap="round" />
            </g>
            
            <!-- Center dot -->
            <circle cx="100" cy="250" r="3" fill="black" />
            
            <!-- Clock numbers -->
            <g id="numbers"></g>
            
            <!-- Legs -->
            <line x1="70" y1="420" x2="70" y2="440" stroke="black" stroke-width="2" />
            <line x1="130" y1="420" x2="130" y2="440" stroke="black" stroke-width="2" />
            
            <!-- Tail -->
            <path class="tail dachshund-body" d="M100 420 Q100 440 100 460" />
        </svg>
    </div>

    <script>
        // Add clock numbers
        const numbers = document.getElementById('numbers');
        for (let i = 1; i <= 12; i++) {
            const angle = (i * 30 - 90) * (Math.PI / 180);
            const x = 100 + 55 * Math.cos(angle);
            const y = 250 + 55 * Math.sin(angle);
            
            const text = document.createElementNS("http://www.w3.org/2000/svg", "text");
            text.setAttribute("x", x);
            text.setAttribute("y", y);
            text.setAttribute("class", "clock-number");
            text.textContent = i;
            numbers.appendChild(text);
        }

        // Update clock hands
        function updateClock() {
            const now = new Date();
            const hours = now.getHours() % 12;
            const minutes = now.getMinutes();
            const seconds = now.getSeconds();
            
            const hourDegrees = (hours + minutes / 60) * 30;
            const minuteDegrees = minutes * 6;
            const secondDegrees = seconds * 6;
            
            document.getElementById('hour-hand').style.transform = `rotate(${hourDegrees}deg)`;
            document.getElementById('minute-hand').style.transform = `rotate(${minuteDegrees}deg)`;
            document.getElementById('second-hand').style.transform = `rotate(${secondDegrees}deg)`;
        }

        // Update every second
        setInterval(updateClock, 1000);
        updateClock(); // Initial update
    </script>
</body>
</html>



https://github.com/user-attachments/assets/1a287248-c4bd-4eab-9bf9-f3d6be2c67f2

## Overview
I had alot of fun yet challenge with this project. I came at it initially with an incredibly basic idea; a 90s vintage clock. I then decided I wanted to make it a little more fun and thought of my Kit-Cat clock which is the iconic cat clocks from the 1930's. I then wanted to add my own twist to it of making it into my dog instead of the classic cat.

## Users 
Dachshund owners such as myself would be the users in this case with it being a cute decorative piece to go in ones home, or in digital form on someones desktop if converted into such a form.

## Learning 
I learned that Claude.ai definitley struggles with time and the concept of clocks to a degree, I had to ask it several times to make adjusts. I also learned that the most basic design isnt always it, I have been reflecting on the idea of "this is supposed to be fun" and trying to allow myself to do so. 


