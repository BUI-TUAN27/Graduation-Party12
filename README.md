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
        .prize-box {
            display: none;
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            max-width: 500px;
            margin: auto;
            text-align: center;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 24px;
            font-weight: bold;
            color: #ff4081;
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
        }
        .btn:hover {
            background: #d63384;
            transform: scale(1.1);
        }
        .facebook-icon {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 50px;
            height: 50px;
        }
    </style>
    <script>
        function getNameFromURL() {
            const urlParams = new URLSearchParams(window.location.search);
            return urlParams.get('name') || "Khách mời";  // Nếu không có tham số name trong URL, hiển thị "Khách mời"
        }

        window.onload = function() {
            const guestName = getNameFromURL();
            document.getElementById('guest-name').innerText = guestName; // Cập nhật tên khách mời
        };

        function openInvitation() {
            let letter = document.getElementById('letter');
            let card = document.getElementById('invitation-card');
            let openButton = document.getElementById('open-button');
            let audio = document.getElementById('bg-music');
            
            letter.classList.add('open');
            openButton.style.display = 'none';
            setTimeout(() => {
                letter.style.display = 'none';
                card.style.display = 'block';
                audio.play();
            }, 500);
        }

        function openPrizeBox() {
            document.getElementById('prize-box').style.display = 'block';
            setTimeout(() => {
                const prizes = ["hông có ròi", "kẹo mút"];;
                const randomPrize = prizes[Math.floor(Math.random() * prizes.length)];
                document.getElementById('prize-result').innerText = `Bạn nhận được: ${randomPrize}`;
                
                // Nếu phần thưởng là "Anh Tuấn", yêu cầu xác nhận
                if (randomPrize === "mmmmmmm") {
                    document.getElementById('confirm-box').style.display = 'block';
                }
            }, 2000);
        }

        function confirmPrize() {
            const facebookLink = "";
            window.location.href = facebookLink;
        }
        
        function closePrizeBox() {
            document.getElementById('prize-box').style.display = 'none';
        }
    </script>
</head>
<body>
    <div class="letter-container">
        <img id="letter" class="letter" alt="Thư mời tốt nghiệp">
        <br>
        <button id="open-button" class="btn" onclick="openInvitation()">📩 Mở Thư</button>
    </div>
    
    <audio id="bg-music" loop>
        <source src="https://raw.githubusercontent.com/BUI-TUAN27/kiyeu/main/nhac/Wxrdie%20-%20M%E1%BB%9AI%20EM%20(ft.%20Mcee%20Blue)%20%5Bprod.%20by%20Machiot%2C%20Marlykid%5D.mp3" type="audio/mpeg">
    </audio>
    
    <div id="invitation-card" class="card">
        <h1>🎓 Graduation Party Invitation 🎓</h1>
        <h2>Nguyễn Sỹ Sáng</h2>
        <p class="date">📅 Thời gian: 09:00 - Ngày 06/04/2025</p>
        <p class="date">📍 Địa điểm: Trường THPT Đô Lương 2</p>
        <p><em>📜 TO: <span id="guest-name">Khách mời</span></em></p>
        <p><em>Mong bức ảnh thanh xuân của mình có sự góp mặt của bạn!</em></p>
        <button class="btn" onclick="openPrizeBox()">✅ Xác nhận tham gia</button>
    </div>
    
    <div id="prize-box" class="prize-box">
        <h2>🎁 Phần thưởng của bạn 🎁</h2>
        <p id="prize-result">Đang quay...</p>
        <button class="btn" onclick="closePrizeBox()">Đóng</button>
    </div>
    
    <!-- Confirmation box for Anh Tuấn -->
    <div id="confirm-box" style="display:none; background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);">
        <h3>🎉 Bạn nhận phần thưởng "Kẹo mút chứ "! 🎉</h3>
        <p>Bạn có muốn nhận phần thưởng không?</p>
        <button class="btn" onclick="confirmPrize()">✅ Xác nhận</button>
        <button class="btn" onclick="closePrizeBox()">❌ Hủy</button>
    </div>

    <a href="">
        <img class="facebook-icon" src="https://upload.wikimedia.org/wikipedia/commons/5/51/Facebook_f_logo_%282019%29.svg" alt="Facebook">
    </a>
</body>
</html>
