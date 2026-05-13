// Dynamic QR
IPromptPayBuilder builder = PPay.DynamicQR;
string qr = PPay.StaticQR.MobileNumber("0914185401").Amount(50).CreateCreditTransferQrCode();
