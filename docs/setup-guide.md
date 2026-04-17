# 🛠️ คู่มือติดตั้งและตั้งค่าระบบ (Setup Guide)

คู่มือนี้จะช่วยให้คุณติดตั้งระบบ **Realtime Income/Expense Tracker** บน n8n ตั้งแต่เริ่มต้น

### 1. สิ่งที่ต้องเตรียม (Prerequisites)
* **n8n Account:** แนะนำเวอร์ชัน Desktop หรือ Cloud (ที่รองรับ Webhook)
* [cite_start]**Google Account:** สำหรับใช้งาน Google Sheets [cite: 9]
* [cite_start]**OpenRouter API Key:** สำหรับเชื่อมต่อ AI Model (Bytedance UI-Tars) [cite: 9]
* [cite_start]**LINE Developers Account:** สำหรับสร้าง LINE Messaging API [cite: 9]

### 2. การนำเข้า Workflow (Workflow Import)
1. ดาวน์โหลดไฟล์ `workflows/realtime-tracker.json` จาก Repository นี้
2. เปิดหน้า n8n ของคุณ -> คลิก **Import from File**
3. เลือกไฟล์ `.json` ที่ดาวน์โหลดไว้

### 3. การตั้งค่า Credentials (ความลับระบบ)
คุณต้องสร้าง Credentials ใน n8n ให้ครบ 3 ส่วนเพื่อให้ระบบทำงานได้:
* [cite_start]**lineMessagingApi:** ใส่ `Channel Access Token` จาก LINE Developers [cite: 9]
* [cite_start]**openRouterApi:** ใส่ `API Key` จาก OpenRouter [cite: 9]
* [cite_start]**googleSheetsOAuth2Api:** ทำการ Authentication กับบัญชี Google ที่เก็บไฟล์ `template.xlsx` [cite: 9]

### 4. การเตรียม Google Sheets
1. [cite_start]สร้างไฟล์ Google Sheets ใหม่ และตั้งชื่อแท็บว่า `Transactions` [cite: 32]
2. สร้างหัวตาราง (Header) ในแถวที่ 1 ดังนี้:
   [cite_start]`Date`, `Time`, `Type`, `Amount`, `Description`, `Category`, `UserID` [cite: 32]
3. คัดลอก **Spreadsheet ID** จาก URL ไปใส่ใน Node `Append Google Sheets` และ `Read Transactions` ใน n8n