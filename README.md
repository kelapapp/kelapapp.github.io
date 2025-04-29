<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pertanyaan Penting!</title>
    <style>
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            background-color: #ffebee;
            text-align: center;
            margin: 0;
            padding: 0;
            overflow: hidden;
            user-select: none;
            touch-action: none;
        }
        #escape-blocker {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 24px;
        }
        .container {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            position: relative;
        }
        h1 {
            color: #e91e63;
            text-shadow: 1px 1px 3px pink;
        }
        .emoji {
            font-size: 60px;
            margin: 20px;
            animation: pulse 1.5s infinite;
        }
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }
        button {
            background-color: #e91e63;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            border-radius: 50px;
            cursor: pointer;
            margin: 15px;
            transition: all 0.3s;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        button:hover {
            background-color: #c2185b;
            transform: scale(1.1);
        }
        #no-btn {
            background-color: #9e9e9e;
        }
        #no-btn:hover {
            background-color: #757575;
        }
        .hidden {
            display: none;
        }
        #message {
            font-size: 20px;
            line-height: 1.6;
            margin: 20px 0;
            color: #555;
        }
        .cursor-trail {
            position: fixed;
            width: 20px;
            height: 20px;
            background-color: pink;
            border-radius: 50%;
            pointer-events: none;
            z-index: -1;
        }
        #floating-hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        .floating-heart {
            position: absolute;
            font-size: 24px;
            animation: float-up 4s linear forwards;
        }
        @keyframes float-up {
            to {
                top: -50px;
                opacity: 0;
                transform: rotate(360deg);
            }
        }
        #fake-close {
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 24px;
            cursor: not-allowed;
            color: #ccc;
        }
    </style>
</head>
<body>
    <div id="escape-blocker" class="hidden">
        <div>Jangan kabur dong... jawab dulu pertanyaannya 😊</div>
    </div>
    
    <div id="floating-hearts"></div>
    
    <div class="container">
        <div id="fake-close">✕</div>
        <div class="emoji">💌</div>
        <h1>Hai Sayang!</h1>
        
        <div id="initial-content">
            <p>Aku punya pertanyaan penting nih...</p>
            <button id="show-message">Buka Pesan</button>
        </div>
        
        <div id="main-content" class="hidden">
            <div id="message">
                <p>Setiap hari bersamamu itu spesial buat aku ❤️</p>
                <p>Aku ingin kamu menjadi bagian dari hidupku selamanya...</p>
                <p>Maukah kamu menjadi pacarku?</p>
            </div>
            
            <div>
                <button id="yes-btn">YA! Aku Mau 💖</button>
                <button id="no-btn">Nggak Dulu...</button>
            </div>
        </div>
        
        <div id="response-yes" class="hidden">
            <div class="emoji">🥳</div>
            <h2>ALHAMDULILLAH! ❤️</h2>
            <p>Aku janji akan membuatmu bahagia selalu!</p>
            <p>Mari kita mulai petualangan indah kita~</p>
        </div>
        
        <div id="response-no" class="hidden">
            <div class="emoji">😢</div>
            <h2>Oke aku terima...</h2>
            <p>Tapi aku nggak akan menyerah deh!</p>
            <p>Boleh aku tetap mencoba meluluhkan hatimu?</p>
            <button id="try-again-btn">Coba Lagi</button>
        </div>
    </div>

    <script>
        // Blok semua cara untuk keluar
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape' || e.key === 'F12' || 
                (e.ctrlKey && e.key === 'w') || 
                (e.ctrlKey && e.key === 'n')) {
                e.preventDefault();
                showEscapeBlocker();
            }
        });
        
        document.addEventListener('contextmenu', function(e) {
            e.preventDefault();
            showEscapeBlocker();
        });
        
        document.getElementById('fake-close').addEventListener('click', function() {
            showEscapeBlocker();
        });
        
        function showEscapeBlocker() {
            const blocker = document.getElementById('escape-blocker');
            blocker.classList.remove('hidden');
            setTimeout(() => blocker.classList.add('hidden'), 2000);
        }
        
        // Efek cursor trail
        document.addEventListener('mousemove', function(e) {
            const trail = document.createElement('div');
            trail.className = 'cursor-trail';
            trail.style.left = e.pageX - 10 + 'px';
            trail.style.top = e.pageY - 10 + 'px';
            document.body.appendChild(trail);
            
            setTimeout(() => {
                trail.style.opacity = '0';
                trail.style.transform = 'scale(2)';
                setTimeout(() => trail.remove(), 300);
            }, 100);
        });
        
        // Animasi hati mengambang
        function createFloatingHearts() {
            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'floating-heart';
                heart.innerHTML = ['❤️', '🧡', '💛', '💚', '💙', '💜', '🤎', '🖤', '💖'][Math.floor(Math.random() * 9)];
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.top = '100vh';
                heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
                heart.style.animationDuration = (Math.random() * 3 + 3) + 's';
                document.getElementById('floating-hearts').appendChild(heart);
                
                setTimeout(() => heart.remove(), 4000);
            }, 300);
        }
        
        // Logika utama
        document.getElementById('show-message').addEventListener('click', function() {
            document.getElementById('initial-content').classList.add('hidden');
            document.getElementById('main-content').classList.remove('hidden');
            createFloatingHearts();
        });
        
        document.getElementById('yes-btn').addEventListener('click', function() {
            document.getElementById('main-content').classList.add('hidden');
            document.getElementById('response-yes').classList.remove('hidden');
            createFloatingHearts();
        });
        
        document.getElementById('no-btn').addEventListener('click', function() {
            document.getElementById('main-content').classList.add('hidden');
            document.getElementById('response-no').classList.remove('hidden');
        });
        
        document.getElementById('try-again-btn').addEventListener('click', function() {
            document.getElementById('response-no').classList.add('hidden');
            document.getElementById('main-content').classList.remove('hidden');
        });
    </script>
</body>
</html>
