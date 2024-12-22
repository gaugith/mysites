<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Đang cập nhật</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #f0f0f0;
        }

        .container {
            text-align: center;
        }

        .spinner {
            width: 100px;
            height: 100px;
            border: 8px solid #ddd;
            border-top: 8px solid #007bff;
            border-radius: 50%;
            animation: spin 2s linear infinite;
            margin: 0 auto 20px;
        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        h1 {
            font-size: 24px;
            margin: 10px 0;
            color: #333;
        }

        p {
            font-size: 16px;
            margin: 10px 0 20px;
            color: #555;
        }

        .button {
            display: inline-block;
            padding: 10px 20px;
            font-size: 16px;
            text-decoration: none;
            color: #fff;
            background: #007bff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .button:hover {
            background: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="spinner"></div>
        <h1>Đang cập nhật</h1>
        <p>Vui lòng thử lại sau!</p>
        <a href="#" class="button">Cancel</a>
    </div>
</body>
</html>



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login with Google reCAPTCHA</title>
    <script src="https://www.google.com/recaptcha/api.js" async defer></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
        }

        .container {
            width: 400px;
            background: #ffffff;
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 20px;
            text-align: center;
        }

        .header {
            background-color: #4a4a4a;
            color: white;
            padding: 20px;
            font-size: 1.8em;
            font-weight: bold;
        }

        .content {
            padding: 25px;
        }

        .form {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .form input {
            padding: 12px;
            font-size: 1em;
            border: 1px solid #ddd;
            border-radius: 10px;
            background-color: #f9f9f9;
        }

        .form button {
            padding: 12px;
            font-size: 1em;
            color: white;
            background-color: #4a4a4a;
            border: none;
            border-radius: 10px;
            cursor: pointer;
        }

        .form button:hover {
            background-color: #3c3c3c;
        }

        .notification {
            margin-top: 20px;
            padding: 10px;
            font-weight: bold;
            color: #4caf50;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">Login</div>
        <div class="content">
            <form id="login-form" class="form" onsubmit="return validateForm(event)">
                <input type="text" id="username" placeholder="Username" required>
                <input type="password" id="password" placeholder="Password" required>
                <!-- Google reCAPTCHA -->
                <div class="g-recaptcha" data-sitekey="6LdbMaIqAAAAAKMc7h8NcB_nQKa3HA5w26RZD-pr"></div>
                <button type="submit">Login</button>
            </form>
            <div id="notification" class="notification"></div>
        </div>
    </div>

    <script>
        // Cập nhật khóa site reCAPTCHA của bạn
        const VALID_USERNAME = "testchatbot123";
        const VALID_PASSWORD = "12345";

        function validateForm(event) {
            event.preventDefault();  // Ngừng gửi form mặc định

            // Lấy giá trị từ form
            const username = document.getElementById("username").value;
            const password = document.getElementById("password").value;

            // Lấy response của Google reCAPTCHA
            const recaptchaResponse = grecaptcha.getResponse();

            if (recaptchaResponse.length == 0) {
                showNotification("Please verify that you are not a robot.", "error");
                return;
            }

            // Kiểm tra thông tin đăng nhập
            if (username === VALID_USERNAME && password === VALID_PASSWORD) {
                showNotification("Login successful!", "success");
            } else {
                showNotification("Incorrect username or password.", "error");
            }
        }

        function showNotification(message, type) {
            const notification = document.getElementById("notification");
            notification.style.display = "block";
            notification.textContent = message;

            if (type === "success") {
                notification.style.color = "#4caf50"; // Xanh lá
            } else if (type === "error") {
                notification.style.color = "#f44336"; // Đỏ
            }
        }
    </script>
</body>
</html>

