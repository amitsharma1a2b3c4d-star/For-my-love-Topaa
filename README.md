<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Message For You ❤️</title>
    <style>
        body {
            background-color: #fff0f3;
            margin: 0;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        #question-page, #success-page {
            text-align: center;
            transition: 0.5s;
        }

        #success-page { display: none; }

        h1 { color: #ff4d6d; font-size: 2rem; padding: 20px; }

        .btn-group {
            position: relative;
            height: 100px;
            width: 300px;
            margin: 0 auto;
        }

        button {
            padding: 15px 30px;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        #yesBtn { background-color: #ff4d6d; color: white; position: absolute; left: 0; }
        
        #noBtn { background-color: #808080; color: white; position: absolute; right: 0; transition: 0.1s; }

        .main-heart {
            font-size: 80px;
            animation: beat 0.8s infinite alternate;
            margin-bottom: 20px;
        }

        @keyframes beat { to { transform: scale(1.2); } }

        .falling-heart {
            position: absolute;
            top: -20px;
            animation: fall linear forwards;
        }

        @keyframes fall { to { transform: translateY(110vh) rotate(360deg); } }
    </style>
</head>
<body>

    <div id="question-page">
        <h1>Will you be mine forever? ❤️</h1>
        <div class="btn-group">
            <button id="yesBtn" onclick="showLove()">YES</button>
            <button id="noBtn" onmouseover="moveNo()" onclick="moveNo()">NO</button>
        </div>
    </div>

    <div id="success-page">
        <div class="main-heart">❤️</div>
        <h1 id="typewriter"></h1>
    </div>

    <script>
        function moveNo() {
            const noBtn = document.getElementById('noBtn');
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            noBtn.style.position = "fixed";
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        }

        function showLove() {
            document.getElementById('question-page').style.display = 'none';
            document.getElementById('success-page').style.display = 'block';
            
            // Start typewriter
            const text = "I knew you couldn't say no! I love you so much! 😍✨";
            let i = 0;
            function type() {
                if (i < text.length) {
                    document.getElementById("typewriter").innerHTML += text.charAt(i);
                    i++;
                    setTimeout(type, 100);
                }
            }
            type();

            // Start heart rain
            setInterval(createHeart, 300);
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('falling-heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.fontSize = Math.random() * 20 + 20 + 'px';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }
    </script>
</body>
</html>
