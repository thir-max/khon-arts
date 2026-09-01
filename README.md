# 🎭 KHON — THE LIVING MASK (3D Digital Exhibition V8)

**KHON (โขน)** คือนิทรรศการดิจิทัลเชิงโต้ตอบ (Interactive Online Art Exhibition) ที่ถ่ายทอดมรดกหัวโขนไทยตามจารีตกรมศิลปากร สู่ประสบการณ์สื่อรำแบบ **Dark Thai Contemporary** ผสมผสานโมเดลสามมิติเสมือนจริงแบบ 3D Canvas Interactive และระบบควบคุมไร้สัมผัสผ่านกล้องด้วย **MediaPipe Hand Tracking**

---

## ✨ คุณสมบัติสำคัญใน V8 (Real Reference 3D Edition)

* **👹 Real-Image Based 3D Khon Mask Model (หัวโขนยักษ์ตามภาพจริง):** ปรับปรุงโครงสร้าง Three.js 3D Model ใหม่ทั้งหมดโดยอ้างอิงจากรูปถ่ายจริงอย่างละเอียด:
  * **องค์ประกอบหน้ากากยักษ์:** ใบหน้ายักษ์สีเขียวแก่/ม่วงเข้มประดับเส้นลายกนก คิ้วทักษิณาวรรต เขี้ยวโค้งลง ตาโพลง และปากแสยะ
  * **ชฎาและมงกุฎย่อมุม (Tiered Crown):** มงกุฎทองคำประดับเพชร/กระจกเกลียบหลายชั้น ยอดแหลมทรงยอดชัย
  * **พวงมาลัยประดับ (Floral Garland):** พวงมาลัยมะลิและอุบะดอกไม้สีแดง/ขาว ห้อยประดับข้างจอนหูกนกทองคำแท้
  * **Realistic Lighting & Materials:** ใช้ระบบแสง Studio Lighting ร่วมกับ Shader วัสดุทองคำสะท้อนแสง (Metallic Reflection) และพื้นผิวลงรักปิดทอง
* **🖐️ Real-time Adaptive Hand Icon:** ปุ่มไอคอนมุมขวาล่างเปลี่ยนสัญลักษณ์ตามท่าทางมือที่ตรวจจับได้จากกล้องทันที:
  * 🖐️ **กางมือ:** ไอคอนเปลี่ยนเป็น 🖐️ (สั่งการ Zoom In)
  * ✊ **กำมือ:** ไอคอนเปลี่ยนเป็น ✊ (สั่งการ Zoom Out)
  * ✋ **สถานะปกติ:** ไอคอนเป็น ✋
* **🎮 Integrated Quiz Challenge:** ระบบเกมทายตัวละครจากอัตลักษณ์หัวโขนพร้อมเฉลยแบบ Real-time
* **🏛️ Fine Arts Department Archives:** คลังข้อมูลจารีตกรมศิลปากร (พระราม, นางสีดา, หนุมาน, ทศกัณฐ์, พิเภก) และภูมิปัญญาช่างสิบหมู่
* **📖 Glassmorphism Modal Detail:** อ่านเนื้อหาฉบับเต็มของแต่ละตัวละครผ่านป๊อปอัปกระจกฝ้า

---

## 🛠️ เทคโนโลยีที่ใช้ (Tech Stack)

* **Frontend:** HTML5, CSS3 (Glassmorphism & Thai Typography Hierarchy), JavaScript (ES6+)
* **3D Graphics Engine:** [Three.js](https://threejs.org/) (WebGL Rendering, Custom Complex Geometry, Metallic Shading)
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

1. คัดลอกโค้ดไฟล์ `index.html` ทั้งหมดไปวางในโปรเจกต์ของคุณ
2. บันทึกไฟล์และเปิดใช้งานผ่าน Web Browser (แนะนำ Google Chrome, Microsoft Edge หรือ Safari)
3. เชื่อมต่ออินเทอร์เน็ต เพื่อให้หน้าเว็บโหลดไลบรารี Three.js และ MediaPipe ผ่าน CDNs ได้อย่างสมบูรณ์

---

## 📜 แหล่งอ้างอิงข้อมูล (Credits & References)

* **รูปภาพอ้างอิงและจารีตโขน:** สำนักการสังคีต และสถาบันชาติตระการ กรมศิลปากร กระทรวงวัฒนธรรม
* **3D & Hand Tracking Engine:** Three.js Community & Google MediaPipe
