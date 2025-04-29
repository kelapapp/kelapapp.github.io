<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untuk Kamu yang Spesial</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #ffebee;
            text-align: center;
            padding: 20px;
            transition: background-color 0.5s;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            background-color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        h1 {
            color: #e91e63;
        }
        p {
            font-size: 18px;
            line-height: 1.6;
            color: #333;
        }
        .btn {
            background-color: #e91e63;
            color: white;
            border: none;
            padding: 12px 25px;
            font-size: 16px;
            border-radius: 25px;
            cursor: pointer;
            margin: 10px;
            transition: transform 0.3s;
        }
        .btn:hover {
            transform: scale(1.05);
        }
        .hidden {
            display: none;
        }
        .heart {
            font-size: 60px;
            color: #e91e63;
            animation: pulse 1.5s infinite;
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.3); }
            100% { transform: scale(1); }
        }
        .photo-frame {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            border: 5px solid #e91e63;
            margin: 20px auto;
            overflow: hidden;
            background-size: cover;
            background-position: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="photo-frame" id="photo"></div>
        <h1>Hai [Baby]!</h1>
        
        <div id="page1">
            <p>Aku punya sesuatu yang ingin aku sampaikan...</p>
            <p>Selama ini, setiap kali bertemu denganmu, hatiku selalu berbunga-bunga.</p>
            <button class="btn" onclick="nextPage()">Lanjut</button>
        </div>
        
        <div id="page2" class="hidden">
            <p>Aku sadar bahwa perasaanku padamu bukan sekadar teman biasa.</p>
            <p>Kamu membuat hariku lebih cerah hanya dengan hadirmu.</p>
            <button class="btn" onclick="nextPage()">Lanjut</button>
        </div>
        
        <div id="page3" class="hidden">
            <p>Maukah kamu...</p>
            <p>Menjadi pacarku?</p>
            
            <div class="heart">❤️</div>
            
            <button class="btn" onclick="showResponse(true)">Iya</button>
            <button class="btn" onclick="showResponse(false)">Tidak</button>
        </div>
        
        <div id="response-yes" class="hidden">
            <h1>Yeayyy! ❤️</h1>
            <p>Aku sangat senang kamu menerima perasaanku!</p>
            <p>Ayo kita jalan bareng minggu ini!</p>
            <div class="heart">🥰</div>
        </div>
        
        <div id="response-no" class="hidden">
            <h1>😢</h1>
            <p>Aku menghargai kejujuranmu.</p>
            <p>Semoga kita tetap bisa berteman baik.</p>
        </div>
    </div>

    <script>
        let currentPage = 1;
        const totalPages = 3;
        
        // Ganti dengan URL foto dia (opsional)
        document.getElementById('photo').style.backgroundImage = "url('https://i.ibb.co.com/LXykPFML/IMG-20230617-WA0010.jpg')";
        
        function nextPage() {
            document.getElementById('page' + currentPage).classList.add('hidden');
            currentPage++;
            document.getElementById('page' + currentPage).classList.remove('hidden');
        }
        
        function showResponse(isYes) {
            document.getElementById('page3').classList.add('hidden');
            if(isYes) {
                document.getElementById('response-yes').classList.remove('hidden');
                document.body.style.backgroundColor = "#fce4ec";
            } else {
                document.getElementById('response-no').classList.remove('hidden');
                document.body.style.backgroundColor = "#e0e0e0";
            }
        }
        
        // Ganti [Nama Dia] dengan nama aslinya
        document.querySelector('h1').innerText = "Hai Baby!";
    </script>
</body>
</html>
