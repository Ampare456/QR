// Presented by BrilliantPy ✓ v.1.1.0
/*######################### Editable1 Start #########################*/
const PROMPTPAY_ID = '0812345678'; // ใส่เบอร์พร้อมเพย์ที่นี่
const ACCOUNT_NAME = 'Mr.BrilliantPy BLP'; // ใส่ชื่อบัญชีที่นี่
const LOGO_URL = 'https://brilliantpy.com/wp-content/uploads/2021/07/cropped-logo_circle_v2_whitebg.jpg';
/*#########################  Editable1 End  #########################*/

function doGet() {
  return HtmlService.createHtmlOutput(htmlTemplate())
    .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}

function htmlTemplate() {
  return `
    <!DOCTYPE html>
    <html>
      <head>
        <title>PromptPay QR Generator</title>
        <style>
          body {
            font-family: 'Segoe UI', sans-serif;
            background: linear-gradient(to bottom right, #f7f7f7, #e0e0e0);
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
          }

          .container {
            background: #ffffff;
            border-radius: 16px;
            box-shadow: 0 8px 30px rgba(0,0,0,0.1);
            padding: 40px 30px;
            width: 100%;
            max-width: 400px;
            text-align: center;
          }

          .logo {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            margin-bottom: 20px;
          }

          h1 {
            margin-bottom: 16px;
            font-size: 24px;
            color: #333333;
          }

          input[type="number"] {
            width: 100%;
            padding: 14px;
            font-size: 18px;
            border: 1px solid #ccc;
            border-radius: 10px;
            box-sizing: border-box;
            margin-bottom: 20px;
            transition: border-color 0.3s;
          }

          input[type="number"]:focus {
            border-color: #007aff;
            outline: none;
          }

          button {
            background: #007aff;
            color: white;
            padding: 12px 24px;
            font-size: 18px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: background 0.3s;
            width: 100%;
          }

          button:hover {
            background: #005fcc;
          }

          #qrcode {
            margin-top: 30px;
          }

          #qrcode img {
            width: 100%;
            max-width: 300px;
            border-radius: 12px;
            border: 1px solid #eee;
          }

          .info {
            margin-top: 15px;
            font-size: 16px;
            color: #555;
            line-height: 1.6;
          }

          .amount-highlight {
            font-weight: bold;
            font-size: 18px;
            color: #000;
          }
        </style>
      </head>
      <body>
        <div class="container">
          <img class="logo" src=${LOGO_URL} />
          <h1>สร้าง QR พร้อมเพย์</h1>
          <input type="number" id="amount" placeholder="กรอกจำนวนเงิน (บาท)" min="1" />
          <button onclick="generateQR()">สร้าง QR</button>
          <div id="qrcode"></div>
        </div>

        <script>
          function generateQR() {
            const amount = document.getElementById("amount").value;
            if (!amount || parseFloat(amount) <= 0) {
              alert("กรุณากรอกจำนวนเงินที่ถูกต้อง");
              return;
            }

            const formattedAmount = parseFloat(amount).toLocaleString('th-TH', {
              minimumFractionDigits: 2,
              maximumFractionDigits: 2
            });

            const qrDiv = document.getElementById("qrcode");
            const img = document.createElement("img");
            img.src = "https://promptpay.io/${PROMPTPAY_ID}/" + amount;

            const info = document.createElement("div");
            info.className = "info";
            info.innerHTML = \`
              ชื่อบัญชี:<br><strong>${ACCOUNT_NAME}</strong><br>
              ยอดโอน: <span class="amount-highlight">\${formattedAmount} บาท</span>
            \`;

            qrDiv.innerHTML = "";
            qrDiv.appendChild(img);
            qrDiv.appendChild(info);
          }
        </script>
      </body>
    </html>
  `;
}
