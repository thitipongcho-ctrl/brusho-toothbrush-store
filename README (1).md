# BRUSHO — ร้านค้าแปรงสีฟัน

เว็บไซต์ตัวอย่างภาษาไทย มีสินค้า 2 SKUs, ฟอร์มสั่งซื้อ, Google Sheets order capture และหน้ารายการหยิบ/แพ็คสินค้า

## โครงสร้าง
- `index.html` — Landing page และหน้าจัดการคำสั่งซื้อ
- `apps-script/Code.gs` — Google Apps Script สำหรับบันทึก/อ่าน Google Sheets
- `assets/products/` — โฟลเดอร์แยกรูปสินค้า
- `vercel.json` — ตั้งค่า static deployment

## ตั้งค่า Google Sheets
1. สร้าง Google Sheet ใหม่ แล้วไปที่ Extensions → Apps Script
2. วางโค้ดจาก `apps-script/Code.gs`
3. เปลี่ยน `ADMIN_KEY` เป็นรหัสลับที่คาดเดายาก
4. Deploy → New deployment → Web app; Execute as: Me; Who has access: Anyone (จำเป็นสำหรับฟอร์มสาธารณะ โปรดพิจารณานโยบายข้อมูลส่วนบุคคลก่อนใช้ข้อมูลลูกค้าจริง)
5. คัดลอก Web app URL ไปใส่ในตัวแปร `SCRIPT_URL` ของ `index.html`
6. Deploy เวอร์ชันใหม่ และทดสอบส่งคำสั่งซื้อ 1 รายการ ตรวจสอบว่าแถวใหม่ปรากฏในแท็บ Orders

## หยิบและแพ็ค
เปิดส่วน Fulfillment Desk ใส่ ADMIN_KEY แล้วกดโหลดคำสั่งซื้อ จากนั้นพิมพ์หน้าเว็บเพื่อใช้เป็นใบหยิบ/แพ็ค ตรวจ SKU จำนวน ชื่อผู้รับ เบอร์โทร และที่อยู่ก่อนปิดกล่องและจัดส่ง

## สินค้า
- BR-01 — BRUSHO Soft Daily — ฿89
- BR-02 — BRUSHO Charcoal Care — ฿129

## Deploy ผ่าน GitHub + Vercel
1. สร้าง GitHub repository แล้วอัปโหลดไฟล์/โฟลเดอร์ทั้งหมด
2. Vercel → Add New → Project → Import Git Repository
3. Framework Preset: Other; Build Command: เว้นว่าง; Output Directory: เว้นว่าง/ค่าเริ่มต้น
4. กด Deploy
5. ทุกครั้งที่ push ไปยัง production branch Vercel จะ deploy อัตโนมัติ

หมายเหตุ: การ deploy โดยตรงจาก Vercel ไม่ได้สร้าง GitHub repository ให้โดยอัตโนมัติ ต้องอัปโหลด source ไป GitHub แยกต่างหาก
