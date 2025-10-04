<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Password Generator</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>Password Generator 🔐</h1>
    
    <label for="length">Password Length:</label>
    <input type="number" id="length" min="4" max="20" value="12">

    <div>
      <label><input type="checkbox" id="uppercase" checked> Include Uppercase</label><br>
      <label><input type="checkbox" id="numbers" checked> Include Numbers</label><br>
      <label><input type="checkbox" id="symbols" checked> Include Symbols</label>
    </div>

    <button onclick="generatePassword()">Generate Password</button>

    <input type="text" id="password" readonly>
    <button onclick="copyPassword()">Copy</button>
  </div>

  
  <script src="script.js"></script>
</body>
</html>   

body {
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(135deg, #667eea, #764ba2);
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
}

.container {
  background: #fff;
  padding: 25px;
  border-radius: 15px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
  width: 350px;
  text-align: center;
}

button {
  background: #667eea;
  color: white;
  border: none;
  padding: 10px;
  border-radius: 8px;
  margin-top: 10px;
  cursor: pointer;
}

function generatePassword() {
  const length = document.getElementById("length").value;
  let chars = "abcdefghijklmnopqrstuvwxyz";
  if (document.getElementById("uppercase").checked) chars += "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  if (document.getElementById("numbers").checked) chars += "0123456789";
  if (document.getElementById("symbols").checked) chars += "!@#$%^&*()_+[]{}|;:,.<>?";

  let password = "";
  for (let i = 0; i < length; i++) {
    password += chars.charAt(Math.floor(Math.random() * chars.length));
  }

  document.getElementById("password").value = password;
}

function copyPassword() {
  const passwordField = document.getElementById("password");
  passwordField.select();
  passwordField.setSelectionRange(0, 99999); // For mobile
  navigator.clipboard.writeText(passwordField.value);
  alert("Password copied to clipboard!");
}
