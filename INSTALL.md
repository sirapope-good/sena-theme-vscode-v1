# การติดตั้ง Sena Theme V1 พร้อม Background Animation 🎨

## วิธีที่ 1: ใช้ Extension (แนะนำ) ⭐

### ขั้นตอนการติดตั้ง:

1. **Clone หรือ Download โปรเจค**
   ```bash
   git clone [your-repo-url]
   cd sena-theme-vscode-v1
   ```

2. **ติดตั้ง Dependencies**
   ```bash
   npm install
   ```

3. **Compile TypeScript**
   ```bash
   npm run compile
   ```

4. **Package Extension**
   ```bash
   npx vsce package
   ```

5. **ติดตั้งใน VS Code**
   - เปิด VS Code
   - กด `Ctrl+Shift+P` (Windows/Linux) หรือ `Cmd+Shift+P` (Mac)
   - พิมพ์ "Extensions: Install from VSIX"
   - เลือกไฟล์ `.vsix` ที่สร้างขึ้น

## วิธีที่ 2: ใช้ Custom CSS Extension 🎯

หากคุณไม่ต้องการสร้าง extension เอง สามารถใช้ extension "Custom CSS and JS Loader" แทน:

### ขั้นตอน:

1. **ติดตั้ง Custom CSS and JS Loader**
   - เปิด Extensions (`Ctrl+Shift+X`)
   - ค้นหา "Custom CSS and JS Loader"
   - ติดตั้ง extension

2. **Copy CSS File**
   - Copy ไฟล์ `styles/background.css` ไปยังโฟลเดอร์ที่เข้าถึงได้
   - แก้ไข path ของรูปภาพในไฟล์ CSS ให้ชี้ไปยัง `assets/` folder

3. **กำหนดค่า VS Code Settings**
   ```json
   {
     "vscode_custom_css.imports": [
       "file:///path/to/your/sena-theme/styles/background.css"
     ],
     "vscode_custom_css.policy": true
   }
   ```

4. **Enable CSS**
   - กด `Ctrl+Shift+P`
   - พิมพ์ "Enable Custom CSS and JS"
   - Restart VS Code

## การใช้งาน 🚀

### การเลือก Theme:
1. `File > Preferences > Color Theme`
2. เลือก "Sena Theme V1"

### การตั้งค่า Background:
```json
{
  "senaTheme.enableBackground": true,
  "senaTheme.backgroundOpacity": 0.3,
  "senaTheme.animationSpeed": 5000
}
```

### Commands:
- `Ctrl+Shift+P` → "Toggle Sena Background"

## การ Customize 🎛️

### เปลี่ยน Opacity:
```json
{
  "senaTheme.backgroundOpacity": 0.1  // ใสมาก
  "senaTheme.backgroundOpacity": 0.5  // เข้มขึ้น
}
```

### เปลี่ยนความเร็วการแสดงภาพ:
```json
{
  "senaTheme.animationSpeed": 3000   // เร็วขึ้น (3 วินาที)
  "senaTheme.animationSpeed": 10000  // ช้าลง (10 วินาที)
}
```

### ปิด Background ชั่วคราว:
```json
{
  "senaTheme.enableBackground": false
}
```

## การแก้ไขปัญหา 🔧

### ถ้าภาพไม่แสดง:
1. ตรวจสอบ path ของไฟล์รูปภาพ
2. ลอง restart VS Code
3. ตรวจสอบ console ใน Developer Tools (`Help > Toggle Developer Tools`)

### ถ้า CSS ไม่ทำงาน:
1. ตรวจสอบว่าติดตั้ง Custom CSS extension แล้ว
2. ตรวจสอบ path ในการตั้งค่า
3. Enable Custom CSS และ restart

### ถ้าภาพเปลี่ยนไม่เป็นตามเวลา:
1. ตรวจสอบการตั้งค่า `animationSpeed`
2. ตรวจสอบว่าไฟล์ภาพทั้ง 3 ไฟล์อยู่ในโฟลเดอร์ `assets/`

## ไฟล์ที่สำคัญ 📁

```
sena-theme-vscode-v1/
├── assets/
│   ├── sena-normal.png   # ภาพปกติ
│   ├── sena-sit.png      # ภาพนั่ง
│   └── sena-close.png    # ภาพหลับตา
├── themes/
│   └── Sena Theme V1-color-theme.json
├── styles/
│   └── background.css    # CSS สำหรับ background
├── src/
│   └── extension.ts      # Extension code
└── package.json
```

## การพัฒนาต่อ 🛠️

หากต้องการแก้ไขหรือเพิ่มฟีเจอร์:

1. แก้ไข `src/extension.ts` สำหรับ logic
2. แก้ไข `styles/background.css` สำหรับ styling
3. แก้ไข `themes/Sena Theme V1-color-theme.json` สำหรับสี
4. Run `npm run compile` เพื่อ build ใหม่

---

**สนุกกับการ coding ไปกับ Sena! 💝** 