<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bilgi Formu</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            display: flex;
            flex-direction: column; /* İçeriğin dikey sıralanması için */
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 500px;
        }
        h2 {
            text-align: center;
            color: #333;
            margin-bottom: 25px;
        }
        .form-group {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            color: #555;
            font-weight: bold;
        }
        input[type="text"],
        input[type="email"],
        input[type="tel"],
        textarea,
        input[type="password"] { /* Şifre input'u da eklendi */
            width: calc(100% - 20px);
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
            box-sizing: border-box; 
        }
        textarea {
            resize: vertical; 
            min-height: 80px;
        }
        button {
            background-color: #007bff;
            color: white;
            padding: 12px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
            width: 100%;
            transition: background-color 0.3s ease;
            margin-top: 10px; /* Giriş butonu için boşluk */
        }
        button:hover {
            background-color: #0056b3;
        }

        /* YENİ STİL: Giriş kutusu ve Formu varsayılan olarak gizleme */
        #formKapsayici {
            display: none; /* Formu başlangıçta gizler */
        }
        .giris-kutusu {
            text-align: center;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            background: #fff;
        }
    </style>
</head>
<body>

    <div class="container giris-kutusu" id="girisKutusu">
        <h2>Erişim İçin Şifre Girin</h2>
        <input type="password" id="sifreInput" placeholder="Şifrenizi Girin">
        <button onclick="sifreKontrol()">Giriş Yap</button>
        <p id="hataMesaji" style="color: red;"></p>
    </div>

    <div class="container" id="formKapsayici">
        <h2>Kişisel Bilgi Formu</h2>
        <form action="https://script.google.com/macros/s/AKfycbw7qBXpunqWY8zNA7LCyrRKFOFSYW5XvSgMjIy_SmdW-vVyPuhncxFYFJF9M4WHVGRiRA/exec" method="POST"> 
            
            <div class="form-group">
                <label for="adSoyad">Adınız Soyadınız:</label>
                <input type="text" id="adSoyad" name="Ad Soyad" required>
            </div>
            
            <div class="form-group">
                <label for="email">E-posta Adresiniz:</label>
                <input type="email" id="email" name="E-posta" required>
            </div>
            
            <div class="form-group">
                <label for="telefon">Telefon Numaranız:</label>
                <input type="tel" id="telefon" name="Telefon">
            </div>
            
            <div class="form-group">
                <label for="mesaj">Mesajınız / Ek Bilgi:</label>
                <textarea id="mesaj" name="Mesaj"></textarea>
            </div>
            
            <button type="submit">Gönder</button>
        </form>
    </div>

    <script>
        // *** DİKKAT: Şifreyi burada kendi istediğiniz ile değiştirin ***
        const DOGRU_SIFRE = ","; 
        
        function sifreKontrol() {
            const girilenSifre = document.getElementById('sifreInput').value;
            const formDiv = document.getElementById('formKapsayici');
            const girisDiv = document.getElementById('girisKutusu');
            const hataMesaji = document.getElementById('hataMesaji');

            if (girilenSifre === DOGRU_SIFRE) {
                // Şifre doğruysa: giriş ekranını gizle, formu göster
                girisDiv.style.display = 'none';
                formDiv.style.display = 'block'; 
                hataMesaji.textContent = '';
            } else {
                // Şifre yanlışsa: hata mesajı göster
                hataMesaji.textContent = 'Yanlış şifre. Lütfen tekrar deneyin.';
            }
        }
        
        // Kullanıcının Enter tuşuna basarak da giriş yapmasını sağlama
        document.getElementById('sifreInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                sifreKontrol();
            }
        });
    </script>

</body>
</html>
