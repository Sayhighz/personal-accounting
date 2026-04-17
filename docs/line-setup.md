# 💬 วิธีสร้าง LINE Bot และตั้งค่า Webhook

ขั้นตอนการเชื่อมต่อ LINE เข้ากับ n8n Workflow

### 1. สร้าง Channel ใน LINE Developers
1. เข้าไปที่ [LINE Developers Console](https://developers.line.biz/)
2. สร้าง **Provider** และสร้าง **Messaging API Channel**
3. ในแท็บ **Messaging API**:
   * คัดลอก `Channel Access Token` (กด Issue ใหม่)
   * คัดลอก `Channel Secret` (จากแท็บ Basic Settings)

### 2. ตั้งค่า Webhook URL
1. ไปที่ n8n ของคุณ เปิด Node `Line Messaging Trigger`
2. คัดลอก **Webhook URL** (แนะนำให้ใช้ Production URL)
3. กลับมาที่หน้า LINE Developers แท็บ **Messaging API**
4. วาง URL ในช่อง **Webhook URL** และกด **Verify**
5. **สำคัญ:** ตรวจสอบว่าเปิดใช้งาน **Use Webhook** เป็น On เรียบร้อยแล้ว

### 3. ปรับแต่ง Auto-response
* ไปที่ส่วน **LINE Official Account Manager**
* ปิด **Auto-response messages** ของ LINE (เพื่อให้บอท n8n ของเราตอบแทนเพียงอย่างเดียว)