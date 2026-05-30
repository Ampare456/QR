<!DOCTYPE html>
<html>
<head>
  <title>PromptPay QR</title>
</head>
<body>

<input type="text" id="phone" placeholder="เบอร์พร้อมเพย์">
<input type="number" id="amount" placeholder="จำนวนเงิน">
<button onclick="generateQR()">Generate QR</button>

<br><br>

<img id="qr" />

<script src="https://cdn.jsdelivr.net/npm/promptpay-qr/index.js"></script>
<script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script>

<script>
async function generateQR() {
    const phone = document.getElementById("phone").value;
    const amount = document.getElementById("amount").value;

    const payload = generatePayload(phone, { amount });

    const qr = await QRCode.toDataURL(payload);

    document.getElementById("qr").src = qr;
}
</script>

</body>
</html>
