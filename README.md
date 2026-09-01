# 🎭 KHON — THE LIVING MASK (3D Digital Exhibition)

**KHON (โขน)** คือโปรเจกต์นิทรรศการดิจิทัลเชิงโต้ตอบ (Interactive Online Art Exhibition) ที่นำเสนอศิลปะการแสดงโขนไทยตามจารีตกรมศิลปากร ผ่านมุมมอง **Dark Thai Contemporary** ผสมผสานเทคโนโลยี **3D Canvas Interactive** และระบบควบคุมอินเทอร์เฟซด้วยภาษามือไร้สัมผัส (**MediaPipe Hand Tracking**)

---

## ✨ มีอะไรใหม่ในเวอร์ชันนี้ (V5 Fine Arts Edition)

* **🎨 Dark Thai Contemporary Aesthetics:** ดีไซน์หน้าเว็บใหม่สไตล์พิพิธภัณฑ์ศิลปะร่วมสมัย โทนสี ดำหมึก (Ink Black), แดงเลือดหมู (Deep Burgundy) และทองโบราณ (Antique Gold)
* **🏛️ คลังข้อมูลตามจารีตกรมศิลปากร:** รวบรวมอัตลักษณ์หัวโขน สีกาย มงกุฎ และนาฏยศัพท์ของตัวละครสำคัญ (พระราม, นางสีดา, หนุมาน, ทศกัณฐ์, พิเภก) ตามคัมภีร์นาฏศิลป์ไทย
* **🧊 3D Interactive Character:** แสดงผลชฎาและหน้ากากโขนแบบ 3D Canvas ขยับหมุนตามทิศทางเมาส์และลอยตัวแบบ Real-time ด้วย Three.js
* **📖 Editorial Layout & Detail Modal:** จัดวางเลย์เอาต์สไตล์นิตยสารศิลปะ สรุปเนื้อหาสำคัญ และมีปุ่ม Glassmorphism กดเพื่อเปิด Modal อ่านรายละเอียดเชิงลึก
* **✋ Minimal Hand Control Dock:** กล้องตรวจจับท่าทางมินิมอลที่มุมจอ สามารถสั่งการซูมเข้า-ออก และเลื่อนหน้าเว็บได้อย่างเสถียร

---

## 🛠️ เทคโนโลยีที่ใช้ (Tech Stack)

* **Frontend:** HTML5, CSS3 (Glassmorphism & Thai Typography Layout), JavaScript (ES6+)
* **3D Graphics:** [Three.js](https://threejs.org/) (WebGL Rendering)
* **AI & Computer Vision:** [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands.html)
* **Fonts:** Google Fonts (`Prompt` สำหรับภาษาไทยโมเดิร์น และ `Cinzel` สำหรับ Typography สไตล์ Display)

---

## ✋ การสั่งงานด้วยท่าทางมือ (Gesture Controls)

| ท่าทางมือ (Hand Gesture) | คำสั่งการทำงาน (Action) |
| :--- | :--- |
| 🖐️ **กางมือ 5 นิ้ว** | ซูมขยายหน้าเว็บเข้า (Zoom In) |
| ✊ **กำมือ** | ซูมย่อหน้าเว็บออก (Zoom Out) |
| ✌️ **ชู 2 นิ้ว (ชี้-กลาง)** | เลื่อนหน้าเว็บลง (Scroll Down) |
| 🤞 **งอนิ้วซูมลง** | เลื่อนหน้าเว็บขึ้น (Scroll Up) |
| 👌 **ทำมือ OK** | หยุดการเลื่อนหน้าเว็บ (Pause Scroll) |

> 💡 **Tip:** สามารถเปิด/ปิด หรือพับเก็บหน้าต่างกล้องที่มุมขวาล่างได้โดยการกดปุ่ม ✋

---

## 🚀 วิธีการเปิดใช้งาน (Getting Started)

1. Clone หรือ Download Repository นี้ลงเครื่องของคุณ
2. เปิดไฟล์ `index.html` ผ่านเว็บเบราว์เซอร์ (แนะนำให้ใช้ Google Chrome หรือ Edge)
3. อนุญาตให้หน้าเว็บเข้าถึงกล้อง (Webcam) เพื่อใช้งานระบบ Hand Control

---

## 📜 แหล่งอ้างอิงข้อมูล (Credits & References)

* **ข้อมูลเนื้อหาและจารีตโขน:** สำนักการสังคีต และสถาบันชาติตระการ กรมศิลปากร กระทรวงวัฒนธรรม
* **3D & Hand Tracking Engine:** Three.js Community & Google MediaPipe
