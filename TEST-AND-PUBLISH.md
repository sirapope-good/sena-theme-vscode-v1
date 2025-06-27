# 🧪 คู่มือการ Test และ Publish Sena Theme V1

## 📋 ขั้นตอนการ Test Theme

### 1. 🏠 Local Testing

**Test ในเครื่องของคุณเอง:**

```bash
# 1. Package theme
vsce package

# 2. Install locally
code --install-extension sena-theme-vscode-v1-1.0.0.vsix

# 3. Test ใน VS Code
# - เปิด VS Code ใหม่
# - เปลี่ยน theme: Ctrl+K Ctrl+T
# - เลือก "Sena Theme V1"
```

### 2. 🔍 ตรวจสอบรายละเอียด

**สิ่งที่ต้องตรวจสอบ:**

✅ **สีพื้นหลัง:**
- Editor background สีเข้ม
- Sidebar สีที่ต่างจาก editor
- Status bar สีโดดเด่น

✅ **Syntax Highlighting:**
- Keywords (if, else, function) - สีม่วงอ่อน
- Strings - สีเขียวอ่อน  
- Numbers - สีเหลือง
- Comments - สีเทาเขียว
- Functions - สีฟ้าอ่อน

✅ **UI Elements:**
- Tabs ที่ active/inactive
- Sidebar icons และ text
- Terminal colors
- Search highlight
- Selection colors

### 3. 📝 Test กับไฟล์ต่างๆ

**สร้างไฟล์ test เหล่านี้:**

**test.js:**
```javascript
// Test JavaScript syntax
function greetUser(name) {
    const message = `Hello, ${name}!`;
    console.log(message);
    return message;
}

const user = "Sena";
const result = greetUser(user);
```

**test.py:**
```python
# Test Python syntax
def calculate_sum(a, b):
    """Calculate sum of two numbers"""
    result = a + b
    print(f"Sum of {a} and {b} is {result}")
    return result

numbers = [1, 2, 3, 4, 5]
total = sum(numbers)
```

**test.html:**
```html
<!-- Test HTML/CSS -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Sena Theme Test</title>
    <style>
        .container {
            background-color: #f0f0f0;
            padding: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Testing Sena Theme</h1>
        <p>This is a test paragraph.</p>
    </div>
</body>
</html>
```

### 4. 📱 Cross-platform Testing

**Test บนระบบปฏิบัติการต่างๆ:**
- Windows 10/11
- macOS
- Linux (Ubuntu)

## 🚀 ขั้นตอนการ Publish

### 1. 📝 เตรียมการ Pre-publish

**1.1 สร้าง Visual Studio Marketplace Account:**
- ไปที่ [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage)
- สร้าง account ด้วย Microsoft account
- สร้าง Publisher profile

**1.2 สร้าง Personal Access Token:**
- ไปที่ [Azure DevOps](https://dev.azure.com/)
- User Settings → Personal Access Tokens
- สร้าง token ใหม่:
  - Name: `vsce-publishing`
  - Organization: All accessible organizations
  - Scopes: Marketplace (manage)

**1.3 ตรวจสอบไฟล์ที่จำเป็น:**
```
sena-theme-vscode-v1/
├── package.json          ✅ มี
├── LICENSE               ✅ มี
├── README.md             ✅ มี
├── icon.png              ⚠️ ต้องเป็นไฟล์จริง (128x128px)
├── themes/
│   └── Sena Theme V1-color-theme.json  ✅ มี
└── assets/               ❓ ลบออกได้ (ไม่ใช้แล้ว)
```

### 2. 🔧 ตั้งค่า VSCE

```bash
# 1. Install vsce globally
npm install -g vsce

# 2. Login with Personal Access Token
vsce login <your-publisher-name>
# Enter your Personal Access Token when prompted

# 3. Verify login
vsce ls-publishers
```

### 3. 📦 Package และ Publish

**3.1 Final Package:**
```bash
# ลบ files ที่ไม่ต้องการ
rm -rf assets/  # หากมี
rm -rf styles/  # หากมี
rm -rf src/     # หากมี

# Package final version
vsce package
```

**3.2 Test Package อีกครั้ง:**
```bash
# Uninstall version เก่า
code --uninstall-extension sena-dev.sena-theme-vscode-v1

# Install version ใหม่
code --install-extension sena-theme-vscode-v1-1.0.0.vsix

# Test ทุกอย่างอีกครั้ง
```

**3.3 Publish to Marketplace:**
```bash
# Publish theme
vsce publish

# หรือ publish จาก .vsix file
vsce publish sena-theme-vscode-v1-1.0.0.vsix
```

### 4. 📈 Post-publish

**4.1 ตรวจสอบใน Marketplace:**
- ไปที่ [VS Code Marketplace](https://marketplace.visualstudio.com/vscode)
- ค้นหา "Sena Theme V1"
- ตรวจสอบว่าข้อมูลถูกต้อง

**4.2 Test การติดตั้งจาก Marketplace:**
```bash
# Uninstall local version
code --uninstall-extension sena-dev.sena-theme-vscode-v1

# Install from marketplace
code --install-extension sena-dev.sena-theme-vscode-v1
```

## 🔄 การอัปเดต Theme

**เมื่อต้องการอัปเดต:**

```bash
# 1. แก้ไขไฟล์ theme
# 2. เพิ่ม version ใน package.json
{
  "version": "1.0.1"  // เพิ่มจาก 1.0.0
}

# 3. อัปเดต CHANGELOG.md
# 4. Package และ publish ใหม่
vsce package
vsce publish
```

## 🎯 Best Practices

**1. การตั้งชื่อ:**
- ใช้ชื่อที่ไม่ซ้ำกับ theme อื่น
- ใช้คำที่ค้นหาง่าย

**2. คุณภาพ:**
- Test บนไฟล์หลายภาษา
- ตรวจสอบความคมชัดของสี
- ให้เพื่อนทดสอบใช้

**3. Marketing:**
- สร้าง screenshot สวยๆ
- เขียน description ที่ดึงดูด
- ใช้ tags ที่เกี่ยวข้อง

## 📊 การติดตาม Analytics

**ใน Marketplace Management:**
- ดูจำนวน downloads
- อ่าน reviews และ ratings
- ตอบ comments ของ users

---

**🎉 Congratulations! Theme ของคุณพร้อม publish แล้ว!** 