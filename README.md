<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Standart Paket - 800 TL</title>
    <style>
        /* Styles from previous response */
    </style>
</head>
<body>
    <div class="payment-container">
        <h2>Standart Paket - 800 TL</h2>
        <form onsubmit="return validateForm()">
            <label for="package">Paket Seçimi</label>
            <input type="text" id="package" name="package" value="Standart Paket - 800 TL" disabled>

            <label for="expiry">Son Kullanma Tarihi (MM/YY)</label>
            <input type="text" id="expiry" name="expiry" placeholder="MM/YY">

            <div id="expiryError" class="error"></div>
            <div id="successAlert" class="alert">Ödeme Başarılı! Onaylandı ✅</div>

            <button type="submit">Ödemeyi Tamamla</button>
        </form>
    </div>

    <script>
        // JavaScript kodu burada
    </script>
</body>
</html>
