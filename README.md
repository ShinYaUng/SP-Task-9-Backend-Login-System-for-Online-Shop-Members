
---

# 📝 README

## 📌 Project Overview

ระบบนี้เป็น **Web Application สำหรับการจัดการผู้ใช้ (User Management System)**
รองรับ 2 บทบาทหลัก:

* **Admin** → จัดการข้อมูลลูกค้า (เพิ่ม, แก้ไข, ลบ, ดูรายการ)
* **Customer** → จัดการโปรไฟล์ส่วนตัวของตนเอง

พัฒนาโดยใช้:

* **Frontend:** HTML, PHP (พื้นฐาน)
* **Backend:** PHP + MySQL (MariaDB)
* **Database Tool:** phpMyAdmin

---

## 📂 Project Structure

```bash
.
├── index.html               # หน้า Login
├── regis.html               # หน้า Register (สมัครสมาชิก)
├── login.php                # ตรวจสอบการเข้าสู่ระบบ
├── logout.php               # ออกจากระบบ
├── register.php             # ลงทะเบียนผู้ใช้ใหม่
├── dbconnect.php            # เชื่อมต่อฐานข้อมูล
├── showdata.php             # แสดงข้อมูลผู้ใช้ทั้งหมด
│
├── customer_dashboard.php   # แดชบอร์ดลูกค้า
├── customer_edit_profile.php # แก้ไขโปรไฟล์ลูกค้า
│
├── admin_dashboard.php      # แดชบอร์ดแอดมิน
├── admin_add_customer.php   # เพิ่มลูกค้าใหม่ (โดยแอดมิน)
└── admin_edit_customer.php  # แก้ไขข้อมูลลูกค้า (โดยแอดมิน)
```

---

## 🗄️ Database

ชื่อฐานข้อมูล: **`dbhw9`**

### ตาราง `users`

| Field     | Type                      | Description             |
| --------- | ------------------------- | ----------------------- |
| id        | int (AUTO\_INCREMENT, PK) | รหัสผู้ใช้              |
| username  | varchar(50), UNIQUE       | ชื่อผู้ใช้ (ล็อกอิน)    |
| password  | varchar(255)              | รหัสผ่าน (เข้ารหัส MD5) |
| firstname | varchar(50)               | ชื่อจริง                |
| lastname  | varchar(50)               | นามสกุล                 |
| gender    | enum('Male','Female')     | เพศ                     |
| age       | int                       | อายุ                    |
| province  | varchar(50)               | จังหวัด                 |
| email     | varchar(100), UNIQUE      | อีเมล                   |
| role      | enum('Admin','Customer')  | บทบาทผู้ใช้             |

🔑 **บัญชีตัวอย่าง**

* Admin → `admin / 1234`
* Customer → `Kittamate / 2222`

---

## 🚀 Features

### 👤 Customer

* Login / Logout
* ดูโปรไฟล์
* แก้ไขข้อมูลส่วนตัว

### 🛠️ Admin

* Login / Logout
* ดูข้อมูลลูกค้าทั้งหมด
* เพิ่มลูกค้าใหม่
* แก้ไขข้อมูลลูกค้า
* ลบลูกค้า

---

## ⚙️ Installation & Setup

1. Clone หรือดาวน์โหลดโปรเจกต์นี้
2. นำไฟล์ทั้งหมดไปวางในโฟลเดอร์ **htdocs** (XAMPP) หรือ **www** (WAMP)
3. Import ไฟล์ฐานข้อมูล `dbhw9.sql` เข้าสู่ phpMyAdmin
4. แก้ไขการเชื่อมต่อฐานข้อมูลใน `dbconnect.php` ถ้าจำเป็น

   ```php
   $conn = new mysqli("localhost", "root", "", "dbhw9");
   ```
5. เปิดเบราว์เซอร์และเข้าใช้งานผ่าน:

   ```
   http://localhost/index.html
   ```

---

## 🔒 Security Notes

* ปัจจุบันใช้ **MD5** ในการเก็บรหัสผ่าน → แนะนำให้เปลี่ยนเป็น **password\_hash() / password\_verify()**
* ยังไม่มีการป้องกัน SQL Injection (เช่น mysqli\_real\_escape\_string, prepared statements)
* Session ควรตั้งค่า `session_regenerate_id()` หลัง login เพื่อเพิ่มความปลอดภัย

---

## ✨ Future Improvements

* เปลี่ยนระบบ Login ให้ใช้ `password_hash()`
* เพิ่ม Role-Based Access Control (RBAC) ที่เข้มงวดขึ้น
* ปรับ UI ด้วย CSS/Bootstrap ให้สวยงาม
* เพิ่มระบบแจ้งเตือน (Flash message) เวลาลงทะเบียน/แก้ไข/ลบสำเร็จ

---
