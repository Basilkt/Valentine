# Valentine
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #fce4ec; /* Soft pink background */
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            text-align: center;
        }

        .container {
            background: white;
            padding: 2.5rem;
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(255, 64, 129, 0.2);
            z-index: 10;
            max-width: 400px;
            width: 90%;
        }

        h1 { color: #c2185b; font-size: 1.8rem; margin-bottom: 1.5rem; }

        .image-container {
            width: 100%;
            margin-bottom: 1.5rem;
            position: relative;
        }

        /* Styles for your uploaded photo */
        #mainPhoto {
            width: 100%;
            height: auto;
            border-radius: 20px;
            border: 5px solid #f8bbd0;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }

        button {
            padding: 12px 28px;
            font-size: 1.1rem;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        #yesBtn { background-color: #ff4081; color: white; }
        #yesBtn:hover { transform: scale(1.1); background-color: #e91e63; }

        #noBtn {
            background-color: #f48fb1;
            color: white;
            position: relative;
        }

        .heart {
            position: absolute;
            color: #ff4081;
            font-size: 20px;
            animation: float 4s linear infinite;
            pointer-events: none;
        }

        @keyframes float {
            0% { transform: translateY(110vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="container">
        <h1 id="question">Will you be my Valentine? ❤️</h1>
        
        <div class="image-container">
            <img id="mainPhoto" src="valentine-photo.jpg" alt="Our Photo">
        </div>

        <div class="buttons">
            <button id="yesBtn" onclick="celebrate()">Yes!</button>
            <button id="noBtn" onmouseover="moveButton()">No</button>
        </div>
    </div>

    <script>
        function moveButton() {
            const noBtn = document.getElementById('noBtn');
            // Calculate random position within the viewport
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        }

        function celebrate() {
            document.getElementById('question').innerText = "Yay! Best Valentine's ever! 🥰";
            document.querySelector('.buttons').style.display = 'none';
            
            // Change the border color of the photo on "Yes"
            document.getElementById('mainPhoto').style.borderColor = "#ff4081";
            
            // Start the heart shower
            setInterval(createHeart, 200);
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 2 + 2) + 's';
            heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
            document.body.appendChild(heart);
            
            setTimeout(() => heart.remove(), 4000);
        }
    </script>
</body>
</html>
