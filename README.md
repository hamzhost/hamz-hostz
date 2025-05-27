<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>𝗛𝗮𝗺𝘇 𝗛𝗼𝘀𝘁t Gateway</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #9c59ff;
            --secondary: #6d3dbb;
            --dark: #2a1b3d;
            --light: #f4f4f9;
            --accent: #ff7e5f;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: var(--dark);
            color: var(--light);
            background-image: url('https://i.pinimg.com/originals/3b/2c/02/3b2c0225a5f9c7a2e5c5e5e5e5e5e5e5.jpg');
            background-size: cover;
            background-attachment: fixed;
            background-position: center;
            min-height: 100vh;
            position: relative;
        }

        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(42, 27, 61, 0.85);
            z-index: -1;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        header {
            text-align: center;
            margin-bottom: 2rem;
            position: relative;
        }

        .logo {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid var(--primary);
            box-shadow: 0 0 20px var(--primary);
            margin-bottom: 1rem;
            transition: transform 0.3s;
        }

        .logo:hover {
            transform: scale(1.05) rotate(5deg);
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            color: var(--primary);
            text-shadow: 0 0 10px rgba(156, 89, 255, 0.5);
        }

        .subtitle {
            font-size: 1.2rem;
            color: var(--light);
            opacity: 0.8;
            margin-bottom: 2rem;
        }

        .payment-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .payment-method {
            background: linear-gradient(135deg, rgba(109, 61, 187, 0.3), rgba(42, 27, 61, 0.7));
            border-radius: 15px;
            padding: 2rem;
            border: 1px solid var(--primary);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s, box-shadow 0.3s;
            backdrop-filter: blur(10px);
            position: relative;
            overflow: hidden;
        }

        .payment-method:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(156, 89, 255, 0.3);
        }

        .payment-method::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                to bottom right,
                transparent,
                transparent,
                transparent,
                var(--primary)
            );
            transform: rotate(30deg);
            opacity: 0.1;
            pointer-events: none;
        }

        .payment-header {
            display: flex;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .payment-icon {
            width: 50px;
            height: 50px;
            margin-right: 1rem;
            object-fit: contain;
        }

        .payment-title {
            font-size: 1.5rem;
            color: var(--light);
        }

        .payment-details {
            margin-bottom: 1.5rem;
        }

        .payment-number {
            font-size: 1.2rem;
            background-color: rgba(255, 255, 255, 0.1);
            padding: 0.8rem 1rem;
            border-radius: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .copy-btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 0.3rem 0.6rem;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
            display: flex;
            align-items: center;
            gap: 0.3rem;
        }

        .copy-btn:hover {
            background-color: var(--secondary);
        }

        .payment-instruction {
            font-size: 0.9rem;
            opacity: 0.8;
            line-height: 1.6;
            margin-bottom: 1rem;
        }

        .qris-image {
            width: 100%;
            border-radius: 10px;
            margin-top: 1rem;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.3s;
        }

        .qris-image:hover {
            transform: scale(1.03);
        }

        .elaina-character {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 200px;
            transition: transform 0.3s;
            z-index: -1;
            opacity: 0.7;
        }

        .elaina-character:hover {
            transform: scale(1.05) rotate(-5deg);
            opacity: 1;
        }

        footer {
            text-align: center;
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 0.9rem;
            opacity: 0.7;
        }

        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background-color: var(--primary);
            color: white;
            padding: 1rem 2rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            transform: translateX(150%);
            transition: transform 0.3s;
            z-index: 1000;
        }

        .notification.show {
            transform: translateX(0);
        }

        @media (max-width: 768px) {
            .payment-container {
                grid-template-columns: 1fr;
            }
            
            .elaina-character {
                width: 150px;
                opacity: 0.5;
            }
        }

        /* Animations */
        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }

        .floating {
            animation: float 3s ease-in-out infinite;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <img src="https://i.pinimg.com/originals/3b/2c/02/3b2c0225a5f9c7a2e5c5e5e5e5e5e5e5.jpg" alt="𝗛𝗮𝗺𝘇" class="logo floating">
            <h1>𝗛𝗔𝗠𝗭 𝗢𝗙𝗙𝗜𝗖𝗜𝗔𝗟</h1>
            <p class="subtitle">Choose your preferred payment method</p>
        </header>

        <div class="payment-container">
            <!-- Dana -->
            <div class="payment-method">
                <div class="payment-header">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/7/72/Logo_DANA.svg" alt="DANA" class="payment-icon">
                    <h2 class="payment-title">DANA</h2>
                </div>
                <div class="payment-details">
                    <div class="payment-number">
                        <span id="dana-number">0881012676067</span>
                        <button class="copy-btn" onclick="copyToClipboard('dana-number')">
                            <i class="fas fa-copy"></i> Copy
                        </button>
                    </div>
                    <p class="payment-instruction">
                        1. Open DANA app<br>
                        2. Go to Send Money<br>
                        3. Paste the number above<br>
                        4. Enter the amount and confirm
                    </p>
                </div>
            </div>

            <!-- OVO -->
            <div class="payment-method">
                <div class="payment-header">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/e/eb/Logo_ovo_purple.svg" alt="OVO" class="payment-icon">
                    <h2 class="payment-title">OVO</h2>
                </div>
                <div class="payment-details">
                    <div class="payment-number">
                        <span id="ovo-number">087824683192</span>
                        <button class="copy-btn" onclick="copyToClipboard('ovo-number')">
                            <i class="fas fa-copy"></i> Copy
                        </button>
                    </div>
                    <p class="payment-instruction">
                        1. Open OVO app<br>
                        2. Go to Transfer<br>
                        3. Paste the number above<br>
                        4. Enter the amount and confirm
                    </p>
                </div>
            </div>

            <!-- GoPay -->
            <div class="payment-method">
                <div class="payment-header">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/8/8b/GoPay_logo.svg" alt="GoPay" class="payment-icon">
                    <h2 class="payment-title">GoPay</h2>
                </div>
                <div class="payment-details">
                    <div class="payment-number">
                        <span id="gopay-number">083871485062</span>
                        <button class="copy-btn" onclick="copyToClipboard('gopay-number')">
                            <i class="fas fa-copy"></i> Copy
                        </button>
                    </div>
                    <p class="payment-instruction">
                        1. Open Gojek app<br>
                        2. Go to Pay<br>
                        3. Select GoPay<br>
                        4. Paste the number above and confirm
                    </p>
                </div>
            </div>

            <!-- QRIS -->
            <div class="payment-method">
                <div class="payment-header">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/d/d0/QRIS_logo.svg" alt="QRIS" class="payment-icon">
                    <h2 class="payment-title">QRIS</h2>
                </div>
                <div class="payment-details">
                    <p class="payment-instruction">
                        1. Open your mobile banking/e-wallet app<br>
                        2. Select QRIS payment<br>
                        3. Scan the QR code below<br>
                        4. Enter the amount and confirm
                    </p>
                    <img src="https://files.catbox.moe/ej9t2h.jpg" alt="QR Code" class="qris-image">
                </div>
            </div>
        </div>
           
           <div class="note">
                <p><strong>Penting:</strong> Setelah melakukan pembayaran, harap konfirmasi dengan mengirimkan bukti transfer ke WhatsApp <strong>0838-7148-5062</strong> atau  <strong>087824683192</strong>. Jangan lupa mencantumkan kode pesanan Anda untuk mempercepat proses verifikasi.</p>
            </div>
        </div>
    </div>
       
         <footer>
            <p>© 2025 HAMZ OFFICIAL Gateway. All rights reserved.</p>
            <p>Contact support: support@elainapay.com</p>
        </footer>
    </div>

    <img src="https://i.pinimg.com/originals/3b/2c/02/3b2c0225a5f9c7a2e5c5e5e5e5e5e5e5.jp" alt="Elaina" class="elaina-character floating">

    <div class="notification" id="notification">
        Number copied to clipboard!
    </div>

    <script>
        function copyToClipboard(elementId) {
            const element = document.getElementById(elementId);
            const text = element.innerText;
            
            navigator.clipboard.writeText(text).then(() => {
                showNotification();
            }).catch(err => {
                console.error('Failed to copy text: ', err);
            });
        }

        function showNotification() {
            const notification = document.getElementById('notification');
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Add floating animation to payment methods
        document.querySelectorAll('.payment-method').forEach((card, index) => {
            card.style.animationDelay = `${index * 0.1}s`;
        });
    </script>
</body>
</html>
