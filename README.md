
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Graduation Party Invitation</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
            text-align: center;
            padding: 50px;
            animation: fadeInBackground 2s ease-in-out;
        }
        @keyframes fadeInBackground {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .letter-container {
            position: relative;
            display: inline-block;
            cursor: pointer;
            animation: float 2s infinite ease-in-out;
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        .letter {
            width: 600px;
            transition: transform 0.5s ease-in-out;
            opacity: 1;
        }
        .letter.open {
            transform: scale(1.2);
            opacity: 0;
        }
        .card {
            display: none;
            background: white;
            padding: 60px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            max-width: 1000px;
            margin: auto;
            animation: fadeIn 1s ease-in-out;
            position: relative;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .btn {
            display: inline-block;
            margin-top: 30px;
            padding: 20px 40px;
            background: #ff4081;
            color: white;
            text-decoration: none;
            border-radius: 40px;
            font-weight: bold;
            font-size: 22px;
            transition: 0.3s;
            animation: glow 1.5s infinite alternate;
        }
        .btn:hover {
            background: #d63384;
            transform: scale(1.1);
        }
        @keyframes glow {
            from { box-shadow: 0 0 10px #ff4081; }
            to { box-shadow: 0 0 20px #ff4081; }
        }
        .countdown {
            font-size: 30px;
            margin-top: 20px;
            font-weight: bold;
            color: #ff4081;
        }
    </style>
    <script>
        function getGuestName() {
            const urlParams = new URLSearchParams(window.location.search);
            return urlParams.get('name') || 'Khách mời';
        }

        function openInvitation() {
            let letter = document.getElementById('letter');
            let card = document.getElementById('invitation-card');
            let openButton = document.getElementById('open-button');
            let guestNameElement = document.getElementById('guest-name');
            let audio = document.getElementById('bg-music');
            
            guestNameElement.innerText = getGuestName();
            letter.classList.add('open');
            openButton.style.display = 'none';
            setTimeout(() => {
                letter.style.display = 'none';
                card.style.display = 'block';
                audio.play();
            }, 500);

            startCountdown();
        }

        function startCountdown() {
            const countdownElement = document.getElementById('countdown');
            const eventDate = new Date("April 6, 2025 10:00:00").getTime();
            const interval = setInterval(() => {
                const now = new Date().getTime();
                const timeRemaining = eventDate - now;
                if (timeRemaining <= 0) {
                    clearInterval(interval);
                    countdownElement.innerHTML = "🎉 Thời gian sự kiện đã đến!";
                } else {
                    const days = Math.floor(timeRemaining / (1000 * 60 * 60 * 24));
                    const hours = Math.floor((timeRemaining % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                    const minutes = Math.floor((timeRemaining % (1000 * 60 * 60)) / (1000 * 60));
                    const seconds = Math.floor((timeRemaining % (1000 * 60)) / 1000);
                    countdownElement.innerHTML = `Thời gian còn lại: ${days}d ${hours}h ${minutes}m ${seconds}s`;
                }
            }, 1000);
        }
    </script>
</head>
<body>
    <div class="letter-container">
        <img id="letter" class="letter" src="https://i.imgur.com/Q9vSDru.jpeg" alt="Thư mời tốt nghiệp">
        <br>
        <button id="open-button" class="btn" onclick="openInvitation()">📩 Mở Thư</button>
    </div>
    
    <audio id="bg-music" loop>
        <source src="https://raw.githubusercontent.com/BUI-TUAN27/kiyeu/main/nhac/Wxrdie%20-%20M%E1%BB%9CI%20EM%20(ft.%20Mcee%20Blue)%20%5Bprod.%20by%20Machiot%2C%20Marlykid%5D.mp3" type="audio/mpeg">
    </audio>
    
    <div id="invitation-card" class="card">
        <h1>🎓 Graduation Party Invitation 🎓</h1>
        <h2>Bùi Trọng Tuấn</h2>
        <p><strong>TO:</strong> <span id="guest-name"></span></p>
        <p class="date">📅 Thời gian: 09:00 - Ngày 06/04/2025</p>
        <p class="date">📍 Địa điểm: Trường THPT Đô Lương 2</p>
        <p><em>Mong bức ảnh thanh xuân của mình có sự góp mặt của bạn!</em></p>
        <div id="countdown" class="countdown"></div>
        <a href="https://www.facebook.com/tuan1207hh" class="btn">✅ Xác nhận tham gia</a>
    </div>
</body>
</html>
