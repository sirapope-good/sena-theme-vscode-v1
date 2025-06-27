# 📋 คู่มือติดตั้ง Sena Theme พร้อม Background Animation

## 🎯 ขั้นตอนการติดตั้งแบบละเอียด

### ขั้นตอนที่ 1: ติดตั้ง Custom CSS and JS Loader Extension

**ทำผ่าน VS Code:**
1. เปิด VS Code
2. กด `Ctrl+Shift+X` (Windows/Linux) หรือ `Cmd+Shift+X` (Mac)
3. ค้นหา **"Custom CSS and JS Loader"**
4. เลือก extension โดย **be5invis** (หรือ **iocave** ถ้าไม่เจอ)
5. กด **Install**

**หรือทำผ่าน Command Line:**
```bash
# ลองสองตัวนี้
code --install-extension be5invis.vscode-custom-css
# หรือ
code --install-extension iocave.monkey-patch
```

### ขั้นตอนที่ 2: เตรียมไฟล์ CSS

**ตัวอย่าง path ที่ต้องแก้ไขในไฟล์ `styles/sena-background.css`:**

```css
/* แก้ไข path เหล่านี้ให้ตรงกับเครื่องของคุณ */
background-image: url('file:///C:/Users/softt/Documents/sena-theme-vscode-v1/assets/sena-normal.png') !important;
background-image: url('file:///C:/Users/softt/Documents/sena-theme-vscode-v1/assets/sena-sit.png') !important;
background-image: url('file:///C:/Users/softt/Documents/sena-theme-vscode-v1/assets/sena-close.png') !important;
```

**🔧 วิธีหา path ที่ถูกต้อง:**
1. เปิด File Explorer ไปยัง `assets` folder
2. คลิกขวาที่ `sena-normal.png` → Properties
3. Copy path แล้วแปลงเป็นรูปแบบ `file:///` 

**ตัวอย่างการแปลง path:**
- จาก: `C:\Users\softt\Documents\sena-theme-vscode-v1\assets\sena-normal.png`
- เป็น: `file:///C:/Users/softt/Documents/sena-theme-vscode-v1/assets/sena-normal.png`

### ขั้นตอนที่ 3: กำหนดค่า VS Code Settings

**เปิด Settings JSON:**
1. กด `Ctrl+Shift+P` → พิมพ์ "Preferences: Open Settings (JSON)"
2. เพิ่มการตั้งค่าเหล่านี้:

```json
{
  "vscode_custom_css.imports": [
    "file:///C:/Users/softt/Documents/sena-theme-vscode-v1/styles/sena-background.css"
  ],
  "vscode_custom_css.policy": true
}
```

**⚠️ สำคัญ:** แก้ไข path ให้ตรงกับเครื่องของคุณ!

### ขั้นตอนที่ 4: เปิดใช้งาน CSS

1. กด `Ctrl+Shift+P`
2. พิมพ์ **"Enable Custom CSS and JS"**
3. เลือกคำสั่งนี้
4. VS Code จะขออนุญาต → กด **"Allow"**
5. **Restart VS Code**

### ขั้นตอนที่ 5: เลือก Sena Theme

1. กด `Ctrl+K` แล้วกด `Ctrl+T`
2. หรือ `File > Preferences > Color Theme`
3. เลือก **"Sena Theme V1"**

## 🔧 การแก้ไขปัญหา

### ปัญหา: ภาพไม่แสดง
```
❌ ไม่แสดง → ตรวจสอบ path ในไฟล์ CSS
❌ เห็นแค่กรอบ → ตรวจสอบว่าไฟล์ภาพอยู่ใน assets/
❌ ขนาดผิด → ปรับ --sena-size ในไฟล์ CSS
```

### ปัญหา: CSS ไม่ทำงาน
```
❌ ไม่มีการเปลี่ยนแปลง → ตรวจสอบว่า Enable Custom CSS แล้ว
❌ VS Code แจ้งเตือน → กด Allow และ restart
❌ Path ผิด → ตรวจสอบ path ในไฟล์ settings.json
```

### ปัญหา: Animation ไม่ทำงาน
```
❌ ภาพไม่เปลี่ยน → ตรวจสอบไฟล์ภาพทั้ง 3 ไฟล์
❌ เปลี่ยนเร็วเกินไป → แก้ไข animation-duration ใน CSS
❌ ติดภาพเดียว → ตรวจสอบ @keyframes
```

## ⚙️ การปรับแต่ง

### เปลี่ยน Opacity:
```css
:root {
  --sena-opacity: 0.2;  /* ใสมาก */
  --sena-opacity: 0.5;  /* เข้มขึ้น */
}
```

### เปลี่ยนขนาด:
```css
:root {
  --sena-size: 200px;  /* เล็กลง */
  --sena-size: 350px;  /* ใหญ่ขึ้น */
}
```

### เปลี่ยนความเร็ว Animation:
```css
.monaco-workbench .part.editor > .content::before {
  animation-duration: 10s !important;  /* เร็วขึ้น */
  animation-duration: 25s !important;  /* ช้าลง */
}
```

### เปลี่ยนตำแหน่ง:
```css
.monaco-workbench .part.editor > .content::before {
  bottom: 50px !important;   /* ห่างจากล่าง */
  right: 50px !important;    /* ห่างจากขวา */
  left: 20px !important;     /* ย้ายไปซ้าย */
}
```

## 📁 โครงสร้างไฟล์สำคัญ

```
sena-theme-vscode-v1/
├── assets/                    👈 ไฟล์รูปภาพ
│   ├── sena-normal.png
│   ├── sena-sit.png
│   └── sena-close.png
├── styles/                    👈 ไฟล์ CSS
│   └── sena-background.css
└── themes/                    👈 ไฟล์ theme
    └── Sena Theme V1-color-theme.json
```

## 🎨 คำสั่งเสริม

### ปิด Background ชั่วคราว:
```css
/* เพิ่มใน CSS */
.sena-hidden .monaco-workbench .part.editor > .content::before {
  display: none !important;
}
```

### เปลี่ยน Opacity แบบ realtime:
กด `F12` ใน VS Code → Console → พิมพ์:
```javascript
document.documentElement.style.setProperty('--sena-opacity', '0.1');
```

---

**✅ เสร็จแล้ว! ตอนนี้คุณจะได้ Sena theme พร้อม background animation แล้ว! 🎉** 