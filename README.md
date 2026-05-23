# ⚔️ Combat Car — Extreme External | 2026

> ระบบควบคุมรถ Combat แบบ Real-time ผ่าน Xbox Controller (Bluetooth) พร้อม Brushless Motor + Soft Start System

---

<!-- ใส่รูป Cover ตอนแข่งที่นี่ -->
![Combat Car in Action](images/cover.jpg)

---

## 📌 About This Project

Combat Car สร้างเพื่อเข้าร่วมการแข่งขัน **[ชื่อการแข่งขัน]** จัดที่ **[สถานที่]** ปี **[ปี]**

เป้าหมาย: [เป้าหมายของการแข่งขัน เช่น ทำลายหรือผลักรถคู่แข่งออกจาก Arena]

| รายละเอียด | ข้อมูล |
|---|---|
| ทีม | Extreme External |
| สมาชิก | 6 คน |
| สถาบัน | มหาวิทยาลัยรังสิต |
| วันแข่ง | 12/05/2023 |

---

## ⚙️ Tech Stack & Components

### Microcontroller
| Component | รายละเอียด |
|---|---|
| MCU | ESP32 (via Arduino Framework) |
| Framework | Arduino + PlatformIO |
| Bluetooth | Bluepad32 Library |

### Drive System (ล้อรถ)
| Component | รายละเอียด |
|---|---|
| Motor | [ระบุ Motor รุ่นที่ใช้] × 2 |
| Motor Driver | [ระบุ Driver รุ่น เช่น L298N / BTS7960] |
| ENA Pin | GPIO 13 |
| ENB Pin | GPIO 25 |
| IN1/IN2 | GPIO 12, 14 |
| IN3/IN4 | GPIO 27, 26 |

### Weapon System (ใบพัด / อาวุธ)
| Component | รายละเอียด |
|---|---|
| Motor | Brushless Motor |
| ESC | [ระบุ ESC รุ่น เช่น 30A Hobbywing] |
| ESC Pin | GPIO 18 |
| PWM Range | 1000–2000 µs |
| Control Mode | Soft Start → RB Button (Hold) |

### Power
| Component | รายละเอียด |
|---|---|
| Battery | [เช่น LiPo 3S 11.1V 2200mAh] |
| ระบบไฟ | [แยก Drive / Weapon หรือรวม] |

### Controller
| Component | รายละเอียด |
|---|---|
| จอย | Xbox Controller |
| โปรโตคอล | Bluetooth (Bluepad32) |

---

## 🕹️ Control Mapping

| ปุ่ม | ฟังก์ชัน |
|---|---|
| **Joystick ซ้าย (Y)** | เดินหน้า / ถอยหลัง |
| **Joystick ซ้าย (X)** | เลี้ยวซ้าย / เลี้ยวขวา |
| **ปุ่ม A** | Soft Start ใบพัด (กดครั้งแรกก่อนใช้งาน) |
| **ปุ่ม B** | หยุดฉุกเฉิน (Emergency Stop) |
| **RB (R1)** | เปิดใบพัด / อาวุธ (กดค้าง) |

---

## 🔧 Key Features

### Soft Start System
ก่อนใช้ใบพัดได้ ต้องกด **ปุ่ม A** เพื่อ Soft Start ก่อนเสมอ
ระบบจะค่อยๆ เพิ่มความเร็วจาก 0% → 30% ทีละ 1% ทุก 50ms
ป้องกันแรงกระชากที่ทำให้ ESC หรือ Motor เสียหายได้

### Speed Ramp
ความเร็ว ESC ไม่เปลี่ยนทันทีทันใด แต่ Ramp Rate = 2% ต่อ Loop (20ms)
ทำให้การหยุด-ออกตัวนุ่มนวลกว่า

### Emergency Stop
กด **ปุ่ม B** หรือ จอยหลุด Bluetooth → หยุดทุกระบบทันที
ต้อง Soft Start ใหม่ทุกครั้งหลัง Emergency Stop

### Deadzone
Joystick มี Deadzone ±15 ป้องกันรถขยับเองเวลาปล่อยมือ

---

## 🔌 Circuit Diagram

<!-- ใส่รูป Diagram วงจรที่นี่ -->
![Circuit Diagram](images/circuit_diagram.png)

---

## 📸 Competition Photos

<!-- เพิ่มรูปตอนแข่งได้เลย ใส่ได้หลายรูป -->
| | |
|---|---|
| ![Race 1](images/race1.jpg) | ![Race 2](images/race2.jpg) |
| ![Race 3](images/race3.jpg) | ![Race 4](images/race4.jpg) |

---

## 🏆 Results

> 🥇 อันดับที่ **[X]** จากทั้งหมด **[Y]** ทีม — [ชื่อการแข่งขัน] [ปี]

---

## 📁 Repository Structure

```
combat-car/
├── src/
│   └── main.cpp          ← Source code หลัก (ESP32 + Bluepad32)
├── images/
│   ├── cover.jpg         ← รูป Cover ตอนแข่ง
│   ├── circuit_diagram.png
│   ├── race1.jpg
│   └── race2.jpg
├── docs/
│   ├── BOM.md            ← Bill of Materials (รายการอุปกรณ์+ราคา)
│   └── wiring_notes.md   ← โน้ตการต่อวงจร
├── platformio.ini        ← PlatformIO config
└── README.md
```

---

## 🚀 Setup & Upload

### Prerequisites
- PlatformIO IDE หรือ VS Code + PlatformIO Extension
- ESP32 Board Package
- Library: `ESP32Servo`, `Bluepad32`

### platformio.ini (ตัวอย่าง)
```ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = arduino
lib_deps =
    madhephaestus/ESP32Servo
    ricardoquesada/Bluepad32
```

### ขั้นตอน
```bash
# 1. Clone repo
git clone https://github.com/[username]/combat-car.git

# 2. เปิดด้วย PlatformIO แล้วกด Upload

# 3. เปิด Serial Monitor (115200 baud) เพื่อดู log
```

### วิธีใช้งาน
1. เปิดไฟรถ — รอ ESC Calibrate และ Arm เสร็จ
2. เปิดจอย Xbox → กดปุ่ม Pair จนเชื่อมต่อ Bluetooth
3. ขับรถด้วย Joystick ซ้าย
4. กด **A** เพื่อ Soft Start ใบพัดก่อนแข่ง
5. กด **RB (R1)** ค้างไว้เพื่อหมุนใบพัด

---

## 📦 Dependencies

| Library | Version | ลิงก์ |
|---|---|---|
| ESP32Servo | latest | [GitHub](https://github.com/madhephaestus/ESP32Servo) |
| Bluepad32 | latest | [GitHub](https://github.com/ricardoquesada/bluepad32) |

---

*สร้างด้วยความมุ่งมั่น ❤️ "
