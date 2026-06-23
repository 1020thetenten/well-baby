# Well Baby Clinic — Checklist ตามอายุ

แอพ checklist ตรวจสุขภาพเด็กดี (Well Baby Clinic) แยกตามช่วงอายุ **1 เดือน → 6 ปี**
อ้างอิงแบบบันทึกสุขภาพเด็ก Ramathibodi Child Health Record (RPD-031)

ครอบคลุม: ประวัติ/ซักผู้เลี้ยงดู · พัฒนาการ 4 ด้าน · การเจริญเติบโต · ตรวจร่างกาย ·
special consideration เฉพาะวัย · คัดกรอง · วัคซีน · สุขภาพช่องปาก (NaF) · คำแนะนำล่วงหน้า
พร้อมปุ่ม **สรุป** คัดลอก/แชร์ไปลง note ได้

เป็น **PWA** — กด *Add to Home Screen* บนมือถือ/ไอแพดแล้วใช้ **ออฟไลน์** ข้างเตียงได้

---

## ขึ้น GitHub Pages (5 นาที)

1. สร้าง repo ใหม่ใน GitHub เช่น `wellbaby`
2. อัปโหลดไฟล์ทั้งหมดนี้ไว้ที่ root ของ repo:
   ```
   index.html
   manifest.json
   sw.js
   icon-192.png
   icon-512.png
   icon-maskable.png
   apple-touch-icon.png
   ```
3. ไปที่ **Settings → Pages**
4. หัวข้อ *Build and deployment* → Source = **Deploy from a branch**
5. เลือก Branch = `main`, Folder = `/ (root)` → **Save**
6. รอ ~1 นาที จะได้ลิงก์: `https://<username>.github.io/wellbaby/`

> ทุก path ในแอพเป็นแบบ relative (`./`) จึงทำงานได้ทั้งใต้ subpath (`/wellbaby/`)
> และที่ root domain — ไม่ต้องแก้อะไร

### ติดตั้งลงเครื่อง (ใช้ออฟไลน์)
- **iOS (Safari):** เปิดลิงก์ → ปุ่มแชร์ → *Add to Home Screen*
- **Android (Chrome):** เปิดลิงก์ → เมนู ⋮ → *Install app / เพิ่มลงหน้าจอหลัก*

---

## หมายเหตุ

- **ตารางวัคซีนอิงแบบฟอร์มปี พ.ศ. 2556** (เช่น MMR2 ที่ 4 ปี) ซึ่งต่างจาก EPI ปัจจุบัน
  โปรดเทียบกับสมุดสุขภาพแม่และเด็ก / ตาราง EPI ฉบับล่าสุดก่อนสั่งจริง
  แก้ได้ในตัวแปร `STAGES` ภายใน `index.html`
- ข้อมูลที่กรอก **เก็บในหน่วยความจำของหน้าเท่านั้น ไม่ถูกบันทึก/ส่งออกที่ใด**
  (รีเฟรช = ล้าง) เพื่อความปลอดภัยของข้อมูลผู้ป่วย
- เป็นเครื่องมือช่วยบันทึก ไม่ใช่เวชระเบียน

## แก้ไขเนื้อหา
ข้อมูลทุกช่วงอายุอยู่ในตัวแปร `STAGES` ใกล้ต้นของ `<script>` ใน `index.html`
แต่ละช่วงมี: `history`, `dev` (g/f/l/s), `special`, `screening`, `oral`, `vacc`, `guide`, `next`
แก้เสร็จอย่าลืมเปลี่ยนเลขเวอร์ชันใน `sw.js` (`wellbaby-v1` → `v2`) เพื่อให้ cache อัปเดต
