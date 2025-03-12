# gerador-de-senhas
<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gerador de Senhas</title>
    <style>
        body {
          
            font-family:'Merriweather', serif;
            font-size: 25px;
            text-align: center;
            margin:50px;
            background-color: #f191c1;
             }
             
        .container {
            background: rgb(202, 59, 138);
            padding: 100px;
            border-radius: 25px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
        }
        input[type='number'] {
            width: 50px;
        }
        button {
            padding: 15px 20px;
            background:#f191c1;
           color: rgb(43, 1, 25);
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
        }
        button:hover {
            background: #92798c;
        }
        .password-container {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 10px;
        }
        #password {
            font-size: 18px;
            font-weight: bold;
            background: #e9ecef;
            padding: 20px;
            border-radius: 5px;
            margin-right: 10px;
            min-width: 200px;
            text-align: center;
        }
        .copy-btn {
            background: #f191c1;
            padding:10px 10px;
        }
        .copy-btn:hover {
            background: #92798c;

        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Gerador de Senhas Fortes</h2>
        <label for="length">Comprimento:</label>
        <input type="number" id="length" value="12" min="4" max="20"><br><br>
        <input type="checkbox" id="uppercase" checked> Incluir Maiúsculas<br>
        <input type="checkbox" id="numbers" checked> Incluir Números<br>
        <input type="checkbox" id="symbols" checked> Incluir Símbolos<br><br>
        <button onclick="generatePassword()">Gerar Senha</button>
        <div class="password-container">
            <span id="password"></span>
            <button class="copy-btn" onclick="copyPassword()">Copiar</button>
        </div>
    </div>

    <script>
        function generatePassword() {
            const length = document.getElementById('length').value;
            const includeUppercase = document.getElementById('uppercase').checked;
            const includeNumbers = document.getElementById('numbers').checked;
            const includeSymbols = document.getElementById('symbols').checked;
            
            const lowercase = 'abcdefghijklmnopqrstuvwxyz';
            const uppercase = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
            const numbers = '0123456789';
            const symbols = '!@#$%^&*()_+[]{}<>?';
            
            let characters = lowercase;
            if (includeUppercase) characters += uppercase;
            if (includeNumbers) characters += numbers;
            if (includeSymbols) characters += symbols;
            
            let password = '';
            for (let i = 0; i < length; i++) {
                const randomIndex = Math.floor(Math.random() * characters.length);
                password += characters[randomIndex];
            }
            
            document.getElementById('password').innerText = password;
        }

        function copyPassword() {
            const passwordText = document.getElementById('password').innerText;
            if (passwordText) {
                navigator.clipboard.writeText(passwordText);
                alert('Senha copiada para a área de transferência!');
            }
        }
    </script>
</body>
</html>
