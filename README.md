# 🎭 KHON — THE LIVING MASK (3D Digital Exhibition V7)

**KHON (โขน)** คือนิทรรศการดิจิทัลเชิงโต้ตอบ (Interactive Online Art Exhibition) ที่ถ่ายทอดมรดกหัวโขนไทยตามจารีตกรมศิลปากร สู่ประสบการณ์สื่อรำแบบ **Dark Thai Contemporary** ผสมผสานโมเดลสามมิติเสมือนจริงแบบ 3D Canvas Interactive และระบบควบคุมไร้สัมผัสผ่านกล้องด้วย **MediaPipe Hand Tracking**

---

## ✨ คุณสมบัติสำคัญใน V7 (Realism & Adaptive Icon Edition)

* **🎭 Highly Detailed 3D Khon Mask Model:** ปรับปรุงโครงสร้าง Three.js 3D Model ขึ้นรูปองค์ประกอบหัวโขนพระรามตามแบบแผนจารีต (มงกุฎชัยย่อมุม, จอนหูกนก, คิ้ว/ตามงกุฎ) พร้อมสมมติการใช้วัสดุรัก-ทองคำแท้ (Metallic Gold & Deep Burgundy Lacquer) และการจัดแสง Studio Three-Point Lighting เสริมความสมจริง
* **🖐️ Real-time Adaptive Hand Icon:** ปุ่มเปิด-ปิดกล้องที่มุมขวาล่างจะเปลี่ยนสัญลักษณ์ไอคอนตามท่าทางมือที่ตรวจจับได้จากกล้องทันที:
  * 🖐️ **กางมือ:** ไอคอนเปลี่ยนเป็น 🖐️ (สั่งการ Zoom In)
  * ✊ **กำมือ:** ไอคอนเปลี่ยนเป็น ✊ (สั่งการ Zoom Out)
  * ✋ **สถานะปกติ:** ไอคอนเป็น ✋
* **🎮 Integrated Quiz Challenge:** นำระบบเกมทายตัวละครจากเอกลักษณ์หัวโขนกลับมาใช้งานได้แบบ Real-time พร้อมแสดงคำอธิบายเฉลยเชิงลึก
* **🏛️ Fine Arts Department Archives:** รวบรวมอัตลักษณ์สีกาย มงกุฎ ท่ารำของตัวละครสำคัญ (พระราม, นางสีดา, หนุมาน, ทศกัณฐ์, พิเภก) และกระบวนการทำหัวโขนของช่างสิบหมู่
* **📖 Glassmorphism Modal Detail:** อ่านเนื้อหาฉบับเต็มของแต่ละตัวละครผ่านหน้าต่างป๊อปอัปแบบกระจกฝ้าได้เรียบลื่น

---

## 🛠️ เทคโนโลยีที่ใช้ (Tech Stack)

* **Frontend:** HTML5, CSS3 (Glassmorphism & Thai Typography Hierarchy), JavaScript (ES6+)
* **3D Graphics Engine:** [Three.js](https://threejs.org/) (WebGL Rendering, Custom Mesh Geometry, Studio Lighting)
* **Computer Vision:** [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands.html) & Camera Utils
* **Fonts:** Google Fonts (`Prompt` สำหรับภาษาไทยโครงสร้างหลัก และ `Cinzel` สำหรับ Typography สไตล์ Display)

---

## ✋ การสั่งงานด้วยภาษามือ (Hand Gesture Controls)

| ท่าทางมือ (Hand Gesture) | ไอคอนบนปุ่ม (Dynamic Icon) | คำสั่งการทำงาน (Action) |
| :--- | :---: | :--- |
| 🖐️ **กางมือ 5 นิ้ว** | 🖐️ | ซูมขยายหน้าเว็บเข้า (Zoom In) |
| ✊ **กำมือ** | ✊ | ซูมย่อหน้าเว็บออก (Zoom Out) |
| ✋ **ไม่พบมือ / มือปกติ** | ✋ | สแตนด์บายพร้อมรับคำสั่ง |

> 💡 **วิธีเปิดใช้งานระบบ Hand Control:**
> 1. กดปุ่มไอคอน ✋ ที่มุมขวาล่างเพื่อเปิดแถบควบคุม Hand Control Dock
> 2. กดปุ่ม **"เริ่มเปิดกล้อง 📹"** และกดอนุญาต (Allow) ให้เบราว์เซอร์เข้าถึงกล้อง Webcam
> 3. ยกมือขึ้นมาหน้ากล้อง ปุ่มไอคอนขวาล่างจะเปลี่ยนรูปทรงและเริ่มปรับการซูมตามท่าทางมือทันที

---

## 🚀 วิธีการใช้งาน (Getting Started)

1. คัดลอกโค้ดไฟล์ `index.html` (V7) ทั้งหมดไปวางในโปรเจกต์ของคุณ
2. บันทึกไฟล์และเปิดใช้งานผ่าน Web Browser (แนะนำ Google Chrome, Microsoft Edge หรือ Safari)
3. ตรวจสอบการเชื่อมต่ออินเทอร์เน็ต เพื่อให้หน้าเว็บโหลดไลบรารี Three.js และ MediaPipe ผ่าน CDNs ได้อย่างสมบูรณ์

---

## 📜 แหล่งอ้างอิงข้อมูล (Credits & References)

* **ข้อมูลเนื้อหาและจารีตโขน:** สำนักการสังคีต และสถาบันชาติตระการ กรมศิลปากร กระทรวงวัฒนธรรม
* **3D & Hand Tracking Engine:** Three.js Community & Google MediaPipe
