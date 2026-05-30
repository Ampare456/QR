const promptpay = require("promptpay");
const QRCode = require("qrcode");

// เบอร์พร้อมเพย์ หรือเลขบัตรประชาชน
const mobileNumber = "0812345678";

// จำนวนเงิน
const amount = 199;

// สร้าง payload พร้อมเพย์
const payload = promptpay(mobileNumber, { amount });

// Generate QR Code
QRCode.toFile(
  "promptpay.png",
  payload,
  {
    color: {
      dark: "#000000",
      light: "#FFFFFF",
    },
  },
  function (err) {
    if (err) throw err;
    console.log("สร้าง QR Code สำเร็จ");
  }
);
