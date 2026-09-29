# RM WMS — ระบบจัดการคลังสินค้าวัตถุดิบของ BIO-COSLAB

RM WMS เป็นระบบจัดการคลังสินค้าวัตถุดิบของ BIO-COSLAB สำหรับดูสต็อก ผังพื้นที่คลัง ค้นหา BOM รับเข้า จัดเก็บ และเบิกจ่าย ผ่าน static web app ที่เปิดได้โดยไม่ต้องล็อกอิน

**เว็บที่เผยแพร่:** [BCL WMS / RM](https://bcl-wms.vercel.app/rm-wms/) · [GitHub Pages](https://nk02388-cyber.github.io/RM-WMS/)

**ซอร์สโค้ด:** [nk02388-cyber/RM-WMS](https://github.com/nk02388-cyber/RM-WMS)

## เปิดใช้งานในเครื่อง

โปรเจกต์นี้ไม่มีขั้นตอน build สามารถเปิดผ่าน static web server ได้ทันที เช่น

```powershell
python -m http.server 8080
```

จากนั้นเปิด `http://localhost:8080/`

## Deploy

GitHub Pages เผยแพร่จากโฟลเดอร์รากของสาขา `main` โดยไม่ต้องใช้ build command เว็บ BCL WMS ส่งเส้นทาง `/rm-wms/` มายังหน้า GitHub Pages นี้ โปรเจกต์ยังมี `netlify.toml` สำหรับกรณี deploy บน Netlify

## ไฟล์หลัก

- `index.html` — หน้า dashboard และ logic ทั้งหมด
- `pk-template.css` — รูปแบบหน้าจอที่ปรับจาก PK Dashboard ให้ใช้กับข้อมูล RM
- `rm-incoming.js`, `rm-incoming-core.js`, `rm-incoming.css` — ขั้นตอน QR รับเข้า พิมพ์ป้ายพาเลต และจัดเก็บที่ดัดแปลงจาก PK WMS สำหรับ RM
- `netlify.toml` — การตั้งค่า deploy และ security headers

ดู [QR-CODE.md](QR-CODE.md) สำหรับวิธีรับเข้าและจัดเก็บด้วย QR

## หมายเหตุ

เวอร์ชันสาธารณะนี้แสดงข้อมูลที่ฝังในหน้าเว็บและข้อมูลที่บันทึกในเบราว์เซอร์เครื่องนั้น ไม่มีการอ่านหรือเขียนฐานข้อมูล Supabase และไม่ซิงก์ข้อมูลข้ามเครื่อง เพื่อไม่เปิดสิทธิ์แก้ไขสต็อกสาธารณะ หากต้องการซิงก์ข้ามเครื่องโดยไม่ล็อกอิน ต้องออกแบบ API และสิทธิ์ฝั่งเซิร์ฟเวอร์ใหม่ก่อน
