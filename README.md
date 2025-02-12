<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ödeme Sayfası - Standart Paket (800 TL)</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .payment-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0,0,0,0.1);
            width: 350px;
        }

        h2 {
            text-align: center;
        }

        form {
            display: flex;
            flex-direction: column;
        }

        label {
            margin-top: 10px;
            font-weight: bold;
        }

        input, select {
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .error {
            color: red;
            font-size: 14px;
            display: none;
        }

        .alert {
            display: none;
            color: white;
            background: red;
            padding: 10px;
            text-align: center;
            margin-bottom: 10px;
            border-radius: 5px;
        }

        button {
            margin-top: 15px;
            padding: 12px;
            background-color: #FF9800;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
        }

        button:hover {
            background-color: #E68900;
        }

        .success {
            color: green;
            text-align: center;
            font-weight: bold;
            display: none;
        }
    </style>
</head>
<body>
    <div class="payment-container">
        <div class="alert" id="alertBox">Lütfen geçerli bilgiler girin!</div>
        <h2>Standart Paket (800 TL) Ödeme Bilgilerini Girin</h2>
        <form onsubmit="return validateForm()">
            <!-- Paket İsim ve Fiyat -->
            <h3>Standart Paket - 800 TL</h3>

            <!-- E-Posta -->
            <label for="email">E-Posta</label>
            <input type="email" id="email" placeholder="example@mail.com" required>
            <span class="error" id="emailError">Geçerli bir e-posta girin.</span>

            <!-- Telefon Numarası -->
            <label for="phone">Telefon Numarası</label>
            <input type="tel" id="phone" placeholder="05XX XXX XX XX" required>
            <span class="error" id="phoneError">Geçerli bir telefon numarası girin.</span>

            <!-- Kart Numarası -->
            <label for="card">Kart Numarası</label>
            <input type="text" id="card" placeholder="1234 5678 9101 1121" maxlength="16" required>
            <span class="error" id="cardError">Geçerli bir 16 haneli kart numarası girin.</span>

            <!-- Son Kullanma Tarihi -->
            <label for="expiry">Son Kullanma Tarihi</label>
            <input type="text" id="expiry" placeholder="MM/YY" maxlength="5" required>
            <span class="error" id="expiryError">Geçerli bir son kullanma tarihi girin.</span>

            <!-- CVV -->
            <label for="cvv">CVV</label>
            <input type="password" id="cvv" placeholder="123" maxlength="3" required>
            <span class="error" id="cvvError">Geçerli bir 3 haneli CVV girin.</span>

            <!-- Ad Soyad -->
            <label for="name">Ad Soyad</label>
            <input type="text" id="name" placeholder="Kart Üzerindeki Ad Soyad" required>

            <!-- Ödeme Butonu -->
            <button type="submit">Ödemeyi Tamamla</button>
            <div class="success" id="successMessage">Ödeme Başarılı! ✔️</div>
        </form>
    </div>

    <script>
        function validateForm() {
            let isValid = true;
            
            const email = document.getElementById("email").value;
            const phone = document.getElementById("phone").value;
            const card = document.getElementById("card").value;
            const expiry = document.getElementById("expiry").value;
            const cvv = document.getElementById("cvv").value;
            
            const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            const phonePattern = /^05\d{9}$/;
            const cardPattern = /^\d{16}$/;
            const expiryPattern = /^(0[1-9]|1[0-2])\/(\d{2})$/;
            const cvvPattern = /^\d{3}$/;

            document.getElementById("emailError").style.display = emailPattern.test(email) ? "none" : "block";
            document.getElementById("phoneError").style.display = phonePattern.test(phone) ? "none" : "block";
            document.getElementById("cardError").style.display = cardPattern.test(card) ? "none" : "block";
            document.getElementById("expiryError").style.display = expiryPattern.test(expiry) ? "none" : "block";
            document.getElementById("cvvError").style.display = cvvPattern.test(cvv) ? "none" : "block";
            
            if (!emailPattern.test(email) || !phonePattern.test(phone) || !cardPattern.test(card) || !expiryPattern.test(expiry) || !cvvPattern.test(cvv)) {
                document.getElementById("alertBox").style.display = "block";
                isValid = false;
            } else {
                document.getElementById("alertBox").style.display = "none";
                document.getElementById("successMessage").style.display = "block"; // Success message shown
            }
            
            return isValid;
        }
    </script>
</body>
</html>
