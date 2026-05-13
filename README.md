<!DOCTYPE html>
<html>
<head>
    <title>PromptPay QR Generator</title>
    <!-- ใช้ QR Code JS Library -->
    <script src="https://jsdelivr.net"></script>
</head>
<body>
    <h2>สแกนเพื่อโอนเงิน</h2>
    <div id="qrcode"></div>

    <script type="text/javascript">
        // เบอร์โทรศัพท์ หรือเลขบัตรประชาชน
        const ppID = '081xxxxxxx'; 
        const amount = '100.00'; // จำนวนเงิน (ว่างไว้ได้)
        
        // ฟังก์ชันสร้างข้อความมาตรฐานพร้อมเพย์ (ตัวอย่างนี้ย่อ)
        // ต้องแปลงข้อมูลตามรูปแบบ EMVCo QR Code
        const payload = `00020101021130420016A0000001030001015802TH5910Name Surname6010City Name6304XXXX`; 

        new QRCode(document.getElementById("qrcode"), payload);
    </script>
</body>
</html>
# QR
