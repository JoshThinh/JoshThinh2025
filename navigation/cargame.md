---
layout: cargame
title: carGame
permalink: /cargame/
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Racing Game</title>
    <style>
        body { margin: 0; }
        canvas { background: #eee; display: block; margin: auto; }
    </style>
</head>
<body>
    <canvas id="raceCanvas" width="800" height="600"></canvas>
    <script>
        const canvas = document.getElementById('raceCanvas');
        const ctx = canvas.getContext('2d');
        
        const car1 = { x: 100, y: 250, size: 40, emoji: '🚗', dx: 0, dy: 0, flip: 1 };
        const car2 = { x: 660, y: 250, size: 40, emoji: '🚙', dx: 0, dy: 0, flip: 1 };
        
        const track = {
            x: 400,
            y: 300,
            outerRadiusX: 250,  // Horizontal radius of the outer oval
            outerRadiusY: 125,  // Vertical radius of the outer oval
            innerRadiusX: 150,  // Horizontal radius of inner oval (smaller)
            innerRadiusY: 75    // Vertical radius of inner oval (smaller)
        };
        
        function drawTrack() {
            // Draw the grey filled inner oval (smaller)
            ctx.fillStyle = 'grey';
            ctx.beginPath();
            ctx.ellipse(track.x, track.y, track.innerRadiusX, track.innerRadiusY, 0, 0, 2 * Math.PI);
            ctx.fill();
            
            // Draw the outer oval border (invisible)
            ctx.fillStyle = 'white'; // Same as background to make it look like just the grey oval is present
            ctx.beginPath();
            ctx.ellipse(track.x, track.y, track.outerRadiusX, track.outerRadiusY, 0, 0, 2 * Math.PI);
            ctx.fill();
        }
        
        function drawCar(car) {
            ctx.save(); // Save the current state
            ctx.font = `${car.size}px Arial`;
            ctx.textAlign = 'center';
            ctx.textBaseline = 'middle';
            ctx.translate(car.x + car.size / 2, car.y + car.size / 2);
            ctx.scale(car.flip, 1); // Flip horizontally if car.flip is -1
            ctx.fillText(car.emoji, 0, 0);
            ctx.restore(); // Restore the state
        }
        
        function isValidPosition(x, y) {
            const dx = x - track.x;
            const dy = y - track.y;
            // Check only against the inner boundary (collision with the center oval)
            const insideInnerBoundary = (Math.pow(dx / track.innerRadiusX, 2) + Math.pow(dy / track.innerRadiusY, 2)) >= 1;
            return insideInnerBoundary;
        }
        
        function update() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            drawTrack();
            drawCar(car1);
            drawCar(car2);
            
            // Calculate new positions
            const newCar1X = car1.x + car1.dx;
            const newCar1Y = car1.y + car1.dy;
            const newCar2X = car2.x + car2.dx;
            const newCar2Y = car2.y + car2.dy;
            
            // Update positions only if they are valid
            if (isValidPosition(newCar1X, newCar1Y)) {
                car1.x = newCar1X;
                car1.y = newCar1Y;
            }
            if (isValidPosition(newCar2X, newCar2Y)) {
                car2.x = newCar2X;
                car2.y = newCar2Y;
            }
            
            requestAnimationFrame(update);
        }
        
        document.addEventListener('keydown', (event) => {
            switch(event.code) {
                case 'KeyW': car1.dy = -2; break;
                case 'KeyS': car1.dy = 2; break;
                case 'KeyA': car1.dx = -2; car1.flip = 1; break; // Flip right
                case 'KeyD': car1.dx = 2; car1.flip = -1; break; // Flip left
                case 'KeyI': car2.dy = -2; break;
                case 'KeyK': car2.dy = 2; break;
                case 'KeyJ': car2.dx = -2; car2.flip = 1; break; // Flip right
                case 'KeyL': car2.dx = 2; car2.flip = -1; break; // Flip left
            }
        });
        
        document.addEventListener('keyup', (event) => {
            switch(event.code) {
                case 'KeyW':
                case 'KeyS': car1.dy = 0; break;
                case 'KeyA':
                case 'KeyD': car1.dx = 0; break;
                case 'KeyI':
                case 'KeyK': car2.dy = 0; break;
                case 'KeyJ':
                case 'KeyL': car2.dx = 0; break;
            }
        });
        
        update();
    </script>
</body>
</html>






