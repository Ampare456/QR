// โอนเงินพร้อมเพย์ไปที่ เบอร์มือถือ 091-418-5401 จำนวน 50 บาท
string qr = PPay.StaticQR.MobileNumber("0914185401").Amount(50).CreateCreditTransferQrCode();
