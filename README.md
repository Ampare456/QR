<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Next Level Fitness | ระบบจัดการสมาชิกฟิตเนสอัจฉริยะ</title>
  
  <!-- Main Stylesheet -->
  <link rel="stylesheet" href="css/styles.css">
  
  <!-- CDN Links: QRious for client-side QR Code rendering -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/qurious/4.0.2/qurious.min.js" integrity="sha512-Y455kyWmaEcrQdaE50yW7Q3UN1A51Vsh1G5TshdK7KuzszX+c6L+I2fT1cW8k17sY28p4S2lYg4Uq5l0d1y7oA==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
</head>
<body>

  <div class="app-container">
    <!-- --- NAVIGATION HEADER --- -->
    <header class="main-header">
      <div class="logo-section" onclick="App.navigateTo('home')">
        <!-- SVG Fitness Logo -->
        <svg viewBox="0 0 24 24">
          <path d="M20.57 14.86L22 13.43l-1.43-1.43 1.43-1.43L19.14 7.71l-1.43 1.43-1.43-1.43-1.43 1.43-1.43-1.43L10.57 9.14 9.14 7.71 7.71 9.14l1.43 1.43L2 17.71 6.29 22l7.14-7.14 1.43 1.43 1.43-1.43 1.43 1.43 1.43-1.43 1.43 1.43zM6.29 20.59L3.41 17.71l6.16-6.16 2.88 2.88-6.16 6.16z"/>
        </svg>
        <span>NEXT LEVEL</span>
      </div>

      <!-- Hamburger Menu for mobile -->
      <div class="menu-hamburger" id="mobile-hamburger" onclick="App.toggleMobileMenu()">
        <span></span>
        <span></span>
        <span></span>
      </div>

      <!-- Navbar Links Mount -->
      <nav>
        <ul class="nav-menu" id="nav-menu-mount">
          <!-- Dynamic links injected here -->
        </ul>
      </nav>

      <!-- Auth Action buttons & Gate scan trigger -->
      <div class="auth-btn-group">
        <button class="btn btn-accent" style="font-size:0.85rem; padding: 0.45rem 1rem;" onclick="App.openGymScannerSimulator()">
          🚪 เครื่องสแกนประตู
        </button>
        <div id="nav-badge-mount" style="display: flex; align-items: center; gap: 1rem;">
          <!-- Injected user profile badge or signup buttons -->
        </div>
      </div>
    </header>

    <!-- --- MAIN VIEW ROUTER MOUNT --- -->
    <main id="app-router-mount" class="main-content">
      <!-- Dynamic pages rendered here -->
    </main>

    <!-- --- FOOTER --- -->
    <footer class="main-footer">
      <div class="footer-content">
        <div class="footer-col">
          <h4>NEXT LEVEL FITNESS</h4>
          <p style="font-size: 0.85rem; line-height: 1.6;">ยิมออกกำลังกายและศูนย์ฟื้นฟูสุขภาพระดับพรีเมียม ตอบโจทย์ไลฟ์สไตล์คนรักสุขภาพ ครบวงจรด้วยเทรนเนอร์มืออาชีพและแผนสุขภาพส่วนบุคคล</p>
        </div>
        <div class="footer-col">
          <h4>ลิงก์ที่มีประโยชน์</h4>
          <ul>
            <li><a href="#home" onclick="App.navigateTo('home')">หน้าแรก</a></li>
            <li><a href="#pricing" onclick="App.navigateTo('pricing')">ตารางแพ็กเกจ</a></li>
            <li><a href="#contact" onclick="App.navigateTo('contact')">ติดต่อสอบถาม</a></li>
          </ul>
        </div>
        <div class="footer-col">
          <h4>คอร์สยอดนิยม</h4>
          <ul>
            <li>ฟิตเนสรายเดือน 3 เดือนสุดคุ้ม</li>
            <li>ฟิตเนสรายปีแถมชุดลิมิเต็ด</li>
            <li>แพ็กเกจเทรนส่วนตัว PT 10 ครั้ง</li>
          </ul>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2026 Next Level Fitness Center. สงวนลิขสิทธิ์ทั้งหมด ภาษาไทยเต็มระบบ</p>
        <p style="font-size: 0.8rem; color: var(--text-muted);">พัฒนาเพื่อความรวดเร็วด้วยสถาปัตยกรรม Client-Side SPA</p>
      </div>
    </footer>
  </div>

  <!-- --- TOAST NOTIFICATIONS CONTAINER --- -->
  <div id="toast-container-mount" class="toast-container"></div>

  <!-- ==================== MODALS & DIALOGS SECTION ==================== -->

  <!-- 1. LOGIN MODAL -->
  <div class="modal-overlay" id="login-modal">
    <div class="modal-box">
      <div class="modal-header">
        <h3 class="modal-title">🔑 เข้าสู่ระบบฟิตเนส</h3>
        <svg class="modal-close" viewBox="0 0 24 24"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
      </div>
      <form onsubmit="App.handleLogin(event)">
        <div class="modal-body">
          <div class="form-group">
            <label class="form-label">อีเมลผู้ใช้งาน (Email)</label>
            <input type="email" class="form-control" required placeholder="name@example.com">
            <span style="font-size:0.7rem; color:var(--text-muted); margin-top:0.25rem;">แอดมิน: admin@fitness.com | เทรนเนอร์: trainer@fitness.com | สมาชิก: member@fitness.com</span>
          </div>
          <div class="form-group">
            <label class="form-label">รหัสผ่าน (Password)</label>
            <input type="password" class="form-control" required placeholder="ป้อนรหัสผ่าน">
            <span style="font-size:0.7rem; color:var(--text-muted); margin-top:0.25rem;">รหัสผ่านทดสอบเริ่มต้นคือ: <strong>member1234</strong> (หรือ admin1234 / trainer1234)</span>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" onclick="App.showRegisterModal()">สมัครสมาชิกใหม่</button>
          <button type="submit" class="btn btn-primary">ยืนยันลงชื่อเข้าใช้</button>
        </div>
      </form>
    </div>
  </div>

  <!-- 2. REGISTER MODAL -->
  <div class="modal-overlay" id="register-modal">
    <div class="modal-box">
      <div class="modal-header">
        <h3 class="modal-title">📝 สมัครสมาชิกออนไลน์</h3>
        <svg class="modal-close" viewBox="0 0 24 24"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
      </div>
      <form onsubmit="App.handleRegister(event)">
        <div class="modal-body">
          <div class="form-group">
            <label class="form-label">ชื่อ-นามสกุลผู้สมัคร *</label>
            <input type="text" class="form-control" required placeholder="เช่น นายวิทยา ร่างกายดี">
          </div>
          <div class="form-group">
            <label class="form-label">เบอร์โทรศัพท์มือถือ *</label>
            <input type="tel" class="form-control" required placeholder="เช่น 0812345678" pattern="[0-9]{10}">
          </div>
          <div class="form-group">
            <label class="form-label">อีเมลผู้ใช้งาน *</label>
            <input type="email" class="form-control" required placeholder="example@mail.com">
          </div>
          <div class="form-group">
            <label class="form-label">ตั้งรหัสผ่าน (อย่างน้อย 6 หลัก) *</label>
            <input type="password" class="form-control" required minlength="6" placeholder="รหัสผ่านเข้าใช้งาน">
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" onclick="App.showLoginModal()">มีบัญชีอยู่แล้ว? เข้าสู่ระบบ</button>
          <button type="submit" class="btn btn-primary">ลงทะเบียนสมาชิก</button>
        </div>
      </form>
    </div>
  </div>

  <!-- 3. CHECKOUT & PAYMENT MODAL -->
  <div class="modal-overlay" id="checkout-modal">
    <div class="modal-box" style="max-width: 550px;">
      <div class="modal-header">
        <h3 class="modal-title">💳 ชำระเงินผ่าน QR PromptPay</h3>
        <svg class="modal-close" viewBox="0 0 24 24"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
      </div>
      <form onsubmit="App.handleCheckoutSubmit(event)">
        <div class="modal-body" style="text-align: center;">
          <h4 id="checkout-package-title" style="font-family: var(--font-display); font-size: 1.15rem; color: var(--accent-purple); margin-bottom: 0.25rem;">รายเดือนฟิตเนส</h4>
          <h3 id="checkout-package-price" style="font-family: var(--font-display); font-size: 1.5rem; margin-bottom: 1.5rem;">ยอดโอนสุทธิ: ฿1,500.00</h3>
          
          <!-- PromptPay Canvas Render -->
          <div style="background: white; padding: 1.25rem; border-radius: var(--border-radius-lg); max-width: 230px; margin: 0 auto 1.5rem auto; box-shadow: var(--shadow-premium);">
            <!-- PromptPay header logos inside QR wrapper -->
            <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom: 8px;">
              <img src="https://media.discordapp.net/attachments/936495574519939103/1169657476836904990/PromptPay-Logo.png" alt="PromptPay" style="height: 24px; pointer-events: none; opacity:0; display:none;" onerror="this.style.display='none'">
              <span style="font-family:'Outfit'; font-weight:800; font-size:14px; color:#0e1726;">PROMPTPAY QR</span>
            </div>
            <canvas id="checkout-promptpay-qr" style="display: block; margin: 0 auto;"></canvas>
            <div style="font-size: 0.65rem; color:#64748b; margin-top:8px; font-weight:700;">สแกนโอนเงินผ่านแอปพลิเคชันธนาคาร</div>
          </div>

          <!-- Slip Upload Zone -->
          <div class="form-group" style="text-align: left;">
            <label class="form-label">อัปโหลดภาพหลักฐานการโอนเงิน (สลิป) *</label>
            <div class="slip-upload-zone" id="slip-upload-drag-zone">
              <svg style="width: 32px; height: 32px; fill: var(--text-muted);" viewBox="0 0 24 24"><path d="M19.35 10.04C18.67 6.59 15.64 4 12 4 9.11 4 6.6 5.64 5.35 8.04 2.34 8.36 0 10.91 0 14c0 3.31 2.69 6 6 6h13c2.76 0 5-2.24 5-5 0-2.64-2.05-4.78-4.65-4.96zM14 13v4h-4v-4H7l5-5 5 5h-3z"/></svg>
              <span style="font-size:0.85rem; font-weight:600;">คลิกเพื่อเลือกไฟล์รูปภาพสลิป</span>
              <span style="font-size:0.75rem; color:var(--text-muted);">รองรับไฟล์ JPG, PNG</span>
            </div>
            <input type="file" id="checkout-slip-upload" accept="image/*" style="display: none;" required>
          </div>

          <!-- Uploaded Slip Preview -->
          <div class="slip-preview-container" id="slip-preview-container">
            <span style="font-size:0.8rem; color:var(--text-muted); display:block; text-align:left; margin-bottom:0.25rem;">ตัวอย่างไฟล์ที่เลือก:</span>
            <img src="" class="slip-preview" id="checkout-slip-preview-img" alt="Slip Uploaded">
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" onclick="document.getElementById('checkout-modal').classList.remove('active')">ยกเลิก</button>
          <button type="submit" class="btn btn-primary">ส่งหลักฐานการชำระเงิน</button>
        </div>
      </form>
    </div>
  </div>

  <!-- 4. ADMIN: SLIP VERIFICATION MODAL -->
  <div class="modal-overlay" id="slip-verification-modal">
    <div class="modal-box" style="max-width: 400px;">
      <div class="modal-header">
        <h3 class="modal-title">🔍 ตรวจสอบภาพสลิปเงินโอน</h3>
        <svg class="modal-close" viewBox="0 0 24 24"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
      </div>
      <div class="modal-body" style="text-align: center;">
        <p id="modal-slip-amount-text" style="font-weight: 700; color: var(--accent-cyan); font-size:1.1rem; margin-bottom: 1rem;">ยอดโอนสุทธิ: ฿0.00</p>
        
        <!-- Large Slip Render -->
        <div style="border-radius: var(--border-radius-md); border:1px solid var(--border-color); overflow:hidden; background:white; padding:10px; margin-bottom:1.5rem;">
          <img src="" id="modal-slip-preview-img" style="width:100%; height:auto; display:block;" alt="E-Slip checking">
        </div>
      </div>
      <div class="modal-footer" style="justify-content: space-between;">
        <button type="button" class="btn btn-danger" id="modal-slip-btn-reject" style="flex:1;">❌ ปฏิเสธสลิป</button>
        <button type="button" class="btn btn-success" id="modal-slip-btn-approve" style="flex:1.2; background:var(--success); color:white;">✔️ อนุมัติและเปิดสมาชิก</button>
      </div>
    </div>
  </div>

  <!-- 5. ADMIN: ADD PACKAGE MODAL -->
  <div class="modal-overlay" id="add-package-modal">
    <div class="modal-box">
      <div class="modal-header">
        <h3 class="modal-title">➕ เพิ่มคอร์ส/แพ็กเกจใหม่</h3>
        <svg class="modal-close" viewBox="0 0 24 24"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
      </div>
      <form id="add-package-form">
        <div class="modal-body">
          <div class="form-group">
            <label class="form-label">ชื่อคอร์ส/แพ็กเกจ *</label>
            <input type="text" class="form-control" required placeholder="เช่น รายเดือน 6 เดือนสุดคุ้ม">
          </div>
          <div class="form-group">
            <label class="form-label">ระยะเวลาสิทธิ์ (จำนวนวันใช้งาน) *</label>
            <input type="number" class="form-control" required placeholder="เช่น 180">
          </div>
          <div class="form-group">
            <label class="form-label">ราคาขายขาย (บาท) *</label>
            <input type="number" class="form-control" required placeholder="เช่น 7500">
          </div>
          <div class="form-group">
            <label class="form-label">รายละเอียด / สิทธิพิเศษเพิ่มเติม</label>
            <textarea class="form-control" rows="3" placeholder="ระบุสิ่งที่ผู้สมัครจะได้รับ..." required style="resize:none;"></textarea>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" onclick="document.getElementById('add-package-modal').classList.remove('active')">ยกเลิก</button>
          <button type="submit" class="btn btn-primary">สร้างแพ็กเกจ</button>
        </div>
      </form>
    </div>
  </div>

  <!-- 6. GYM GATE SCANNER SIMULATOR MODAL -->
  <div class="modal-overlay" id="gym-gate-scanner-modal">
    <div class="modal-box" style="max-width: 450px;">
      <div class="modal-header">
        <h3 class="modal-title">🚪 เครื่องสแกนประตูหน้ายิมจำลอง</h3>
        <svg class="modal-close" viewBox="0 0 24 24"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
      </div>
      <form onsubmit="App.handleScanSimulationSubmit(event)">
        <div class="modal-body" style="text-align: left;">
          <p style="color:var(--text-muted); font-size:0.85rem; margin-bottom: 1.25rem;">จำลองเครื่องสแกนบาร์โค้ดหน้าประตูฟิตเนสเพื่อเช็คอินสมาชิกเข้ายิม (รองรับระบบกันแคปหน้าจอ: รหัสจะใช้ได้แค่ 15 วินาทีหลังจากถูกสร้าง)</p>
          
          <div class="form-group">
            <label class="form-label">ดึงรหัส QR อัตโนมัติจากสมาชิกที่มีอยู่:</label>
            <select class="form-control" id="scanner-member-select">
              <!-- Dynamically populated options of member users -->
            </select>
          </div>

          <div style="text-align: center; margin: 0.5rem 0; font-weight: bold; color: var(--accent-purple);">หรือ</div>

          <div class="form-group">
            <label class="form-label">ป้อนรหัสสแกน QR Payload (fit-checkin:userId:timestamp):</label>
            <input type="text" class="form-control" id="scanner-qr-payload-input" placeholder="ป้อนค่ารหัสเช็คอิน เช่น fit-checkin:usr-member-1:1688534820">
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" onclick="document.getElementById('gym-gate-scanner-modal').classList.remove('active')">ยกเลิก</button>
          <button type="submit" class="btn btn-accent">Simulate Scan (สแกนบัตร)</button>
        </div>
      </form>
    </div>
  </div>

  <!-- ==================== SCRIPT FILES ==================== -->
  <script src="js/db.js"></script>
  <script src="js/components/promptpay.js"></script>
  <script src="js/components/charts.js"></script>
  <script src="js/views/public.js"></script>
  <script src="js/views/member.js"></script>
  <script src="js/views/trainer.js"></script>
  <script src="js/views/admin.js"></script>
  <script src="js/app.js"></script>

</body>
</html>
