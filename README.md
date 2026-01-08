# Index.html
<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Telegram Botga Ma'lumot Yuborish</title>
    <style>
        body { font-family: sans-serif; display: flex; justify-content: center; padding-top: 50px; }
        .form-container { width: 300px; border: 1px solid #ccc; padding: 20px; border-radius: 10px; }
        input { width: 100%; margin-bottom: 10px; padding: 8px; box-sizing: border-box; }
        button { width: 100%; padding: 10px; background-color: #0088cc; color: white; border: none; border-radius: 5px; cursor: pointer; }
        button:hover { background-color: #006699; }
    </style>
</head>
<body>

<div class="form-container">
    <h3>Ma'lumot yuborish</h3>
    <form id="tgForm">
        <label for="name">Name:</label>
        <input type="text" id="name" placeholder="Ismingizni kiriting" required>
        
        <label for="username">Username:</label>
        <input type="text" id="username" placeholder="Familiyangizni kiriting" required>
        
        <button type="submit">Telegramga yuborish</button>
    </form>
</div>

<script>
    const token = "8221545338:AAGnfNTqCBqY7KLBFCMMiluvT3zYOwgM5SY";
    const chat_id = "8485643079";

    const form = document.getElementById('tgForm');

    form.addEventListener('submit', (e) => {
        e.preventDefault();

        const name = document.getElementById('name').value;
        const username = document.getElementById('username').value;
        
        const message = `Yangi xabar!\n\nIsm: ${name}\nFamiliya (Username): ${username}`;

        const url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chat_id}&text=${encodeURIComponent(message)}`;

        fetch(url)
            .then(response => {
                if (response.ok) {
                    alert("Ma'lumot muvaffaqiyatli yuborildi!");
                    form.reset();
                } else {
                    alert("Xatolik yuz berdi. Token va Chat IDni tekshiring.");
                }
            })
            .catch(error => {
                console.error('Xato:', error);
                alert("Tarmoq xatosi!");
            });
    });
</script>

</body>
</html>

