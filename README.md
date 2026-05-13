<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ชำระเงินพร้อมเพย์</title>
    <style>
        .qr-container {
            text-align: center;
            margin-top: 50px;
            font-family: sans-serif;
        }
        .qr-image {
            width: 250px; /* ปรับขนาดได้ */
            height: auto;
        }
    </style>
</head>
<body>
    <div class="qr-container">
        <h2>สแกนเพื่อชำระเงิน</h2>
        <!-- แทนที่ 'qr.png' ด้วย path จริงของภาพคุณ -->
        <img src="path/to/your/qr.png" alt="PromptPay QR Code" class="qr-image">
        <p>โอนเงินผ่าน PromptPay</p>
    </div>
</body>
</html>
