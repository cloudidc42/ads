# Part 015: Events Manager และการตั้งค่า Standard Events

**Section:** B — Facebook Ads Ecosystem Fundamentals
**Step ที่ครอบคลุม:** Step 141–150 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 6–8 ชั่วโมง (รวมการตรวจสอบและปรับปรุง Health Check จริง)

Part 013 และ 014 สอนให้ Pixel/CAPI "ทำงาน" ได้แล้ว Part นี้คือการทำให้มัน "ทำงานได้ดีที่สุด" ผ่านศูนย์บัญชาการเดียวที่ชื่อว่า **Events Manager** — หน้าจอนี้คือที่ที่นักยิงแอดมืออาชีพต้องเข้าไปดูสม่ำเสมอไม่น้อยกว่า Ads Manager เอง เพราะถ้าข้อมูลตรงนี้ผิดหรือไม่สมบูรณ์ ไม่ว่าแคมเปญจะออกแบบดีแค่ไหน อัลกอริทึมก็จะ Optimize ผิดทางอยู่ดี

---

## Steps ที่ครอบคลุมใน Part นี้

1. **ภาพรวม Events Manager และการอ่านข้อมูล** — โครงสร้างหน้าจอ เมนู และตัวเลขสำคัญที่ต้องรู้จัก
2. **ตั้งค่า Purchase Event พร้อม Value และ Currency** — จุดที่มีผลต่อ ROAS มากที่สุดในทั้งระบบ
3. **ตั้งค่า Lead และ CompleteRegistration Event** — สำหรับธุรกิจ Lead Generation และ Membership
4. **ตั้งค่า AddToCart, InitiateCheckout, ViewContent** — Event กลาง Funnel ที่ช่วยให้ Optimize ได้แม่นยำขึ้น
5. **Priority Events สำหรับ iOS14+ (8 Events)** — การจัดลำดับความสำคัญที่มีผลกับ AEM โดยตรง
6. **Value Optimization และการส่ง Dynamic Value** — ทำให้ Facebook หาคนที่จะใช้เงินมากกว่าให้เราได้
7. **Deduplication ระหว่าง Pixel และ CAPI** — เทคนิค event_id ที่ป้องกันข้อมูลนับซ้ำ
8. **Data Processing Options และ Privacy Settings** — การปฏิบัติตามข้อกฎหมายและนโยบายความเป็นส่วนตัว
9. **การตรวจสุขภาพ Event ด้วย Diagnostics** — อ่านคำเตือนของ Meta และแก้ไขอย่างเป็นระบบ
10. **Workshop: Events Manager Health Check ฉบับเต็ม** — ตรวจทุกจุดจนมั่นใจว่าพร้อมสเกลงบ

---

## Step 141: ภาพรวม Events Manager และการอ่านข้อมูล

### โครงสร้างหน้าจอ Events Manager

เข้าผ่าน business.facebook.com/events_manager2 หรือจากเมนู All Tools → Measure & Report → Events Manager โครงสร้างหลักมี 4 ส่วนสำคัญ:

1. **Data Sources (ซ้ายมือ):** รายการ Pixel/Dataset ทั้งหมดที่ธุรกิจมี — ถ้าดูแลหลายลูกค้าจะเห็นหลายรายการในนี้ ต้องเลือกให้ถูกตัวก่อนดูข้อมูลทุกครั้ง
2. **Overview Tab:** สรุปภาพรวม Event ทั้งหมดที่ยิงเข้ามาในช่วงเวลาที่เลือก แยกตาม Browser/Server, จำนวนครั้ง, และ Trend กราฟ
3. **Test Events Tab:** เครื่องมือ Debug แบบ Real-time (อธิบายแล้วใน Part 014 Step 137)
4. **Diagnostics Tab:** คำเตือนและปัญหาที่ Meta ตรวจพบอัตโนมัติ (ใช้เจาะลึกใน Step 149)
5. **Settings Tab:** ตั้งค่า Advanced Matching, Conversions API Access Token, Data Processing Options, Aggregated Event Measurement Configuration

### การเลือกช่วงเวลา (Date Range) และการเปรียบเทียบ

มุมบนขวาของ Events Manager มีตัวเลือกช่วงเวลาเสมอ (7 วัน, 28 วัน, Custom Range) หลักการที่ควรใช้:
- **ตรวจสุขภาพประจำวัน:** ดูช่วง 3–7 วันล่าสุด เทียบกับ 7 วันก่อนหน้า เพื่อจับความเปลี่ยนแปลงกะทันหัน
- **วิเคราะห์ EMQ ระยะยาว:** ดูช่วง 28 วัน เพราะ EMQ ผันแปรได้ตามปริมาณ Traffic รายวัน ดูช่วงสั้นเกินไปอาจสรุปผิด
- **ก่อน/หลังแก้ไขเว็บไซต์:** เทียบช่วงก่อนแก้ไขกับหลังแก้ไขแบบ Manual เพื่อยืนยันว่าการแก้ไขได้ผลจริง ไม่ใช่แค่ความผันแปรตามปกติของระบบ

### ตัวเลขสำคัญที่ต้องอ่านให้เป็นทุกครั้งที่เปิดหน้านี้

- **Received Events:** จำนวน Event ที่ได้รับทั้งหมดในช่วงเวลา แยกตามชื่อ Event
- **Event Match Quality (EMQ):** คะแนนคุณภาพการจับคู่ (อธิบายละเอียดใน Part 013 Step 127)
- **Deduplication Rate/Deduplicated Events:** จำนวน Event ที่ระบบตรวจพบว่าซ้ำกันจาก Browser+Server แล้วรวมเป็นรายการเดียว
- **Coverage:** สัดส่วนของ Event ที่มี User Data ครบ (email, phone, fbc ฯลฯ) เทียบกับ Event ทั้งหมด

### การอ่านกราฟ Trend เพื่อจับความผิดปกติ

ควรเปิดดู Events Manager **ทุกวันในช่วงที่แคมเปญกำลังวิ่งงบสูง** เพื่อจับสัญญาณ เช่น:
- กราฟ Purchase หล่นลงกะทันหันในวันที่ไม่มีเหตุผลทางธุรกิจ (ไม่ใช่วันหยุด ไม่มีปัญหาสต็อก) → มักเป็นสัญญาณว่า Pixel/CAPI พังบางส่วน ต้องรีบตรวจสอบก่อนเสียงบไปกับ Event ที่ Optimize ผิดทาง
- กราฟ EMQ ตกฮวบ → บ่งบอกว่ามีการเปลี่ยนแปลงบางอย่างที่ทำให้ user_data ที่ส่งไปไม่ครบเหมือนเดิม (เช่น Developer แก้โค้ด checkout แล้วลืมส่ง email/phone)

### ข้อผิดพลาดที่มือใหม่ทำบ่อย

- ดู Events Manager แค่ตอนตั้งค่าครั้งแรกแล้วไม่กลับมาดูอีก ทั้งที่ปัญหา Pixel เกิดขึ้นได้ตลอดเวลา (เช่น Developer อัปเดตเว็บแล้วโค้ด Pixel หลุด)
- สับสนตัวเลขใน Events Manager กับตัวเลข Conversion ใน Ads Manager — สองที่นี้อาจไม่เท่ากันเป๊ะเสมอเพราะ Attribution Window และวิธีคำนวณต่างกัน (Events Manager แสดง Raw Event ทั้งหมด ส่วน Ads Manager แสดงเฉพาะที่ Attributed กับโฆษณา)

---

## Step 142: ตั้งค่า Purchase Event พร้อม Value และ Currency

### ทำไม Purchase ต้องมี Value/Currency เสมอ ไม่มีข้อยกเว้น

Purchase คือ Event ที่ตัดสินความสำเร็จของธุรกิจส่วนใหญ่ ถ้าไม่มี value/currency ระบบจะยัง Optimize หาคน "ที่มีโอกาสซื้อ" ได้อยู่ (Conversion Optimization) แต่จะ **ไม่สามารถทำ Value Optimization** ได้เลย (หาคนที่มีโอกาสซื้อ "แพง" กว่า) และ ROAS ที่รายงานในระบบจะผิดทั้งหมดเพราะไม่มีมูลค่าอ้างอิง

### วิธีตั้งค่าให้ถูกต้องสำหรับสินค้าหลายรายการในตะกร้าเดียว

```javascript
fbq('track', 'Purchase', {
  value: 2380.00,          // ผลรวมมูลค่าออเดอร์ทั้งหมด (ไม่ใช่ราคาต่อชิ้น)
  currency: 'THB',
  content_ids: ['SKU001', 'SKU045', 'SKU045'], // ใส่ id ซ้ำได้ถ้าซื้อชิ้นเดียวกัน 2 อัน
  content_type: 'product',
  num_items: 3,
  contents: [
    {id: 'SKU001', quantity: 1, item_price: 990.00},
    {id: 'SKU045', quantity: 2, item_price: 695.00}
  ]
});
```

**ข้อผิดพลาดคลาสสิก:** Developer มือใหม่มักส่ง `value` เป็นราคาสินค้าตัวแรกตัวเดียว ไม่ใช่ผลรวมทั้งออเดอร์ ทำให้ ROAS ในระบบต่ำกว่าความจริงเมื่อลูกค้าซื้อหลายชิ้น ต้องตรวจสอบ Logic การคำนวณ value ให้ตรงกับยอดที่เก็บเงินจริงเสมอ (รวม Shipping หรือไม่ก็ต้องตัดสินใจให้สอดคล้องกันทุกครั้ง ไม่ใช่บางออเดอร์รวม บางออเดอร์ไม่รวม)

### สกุลเงินต้องตรงกับที่เก็บเงินจริง

ถ้าธุรกิจเก็บเงินเป็นบาทไทยแต่ใส่ `currency: 'USD'` โดยไม่ได้แปลงตัวเลข ระบบจะตีความ value เป็นดอลลาร์ทันที ทำให้ ROAS ผิดพลาดมหาศาล (เช่น ใส่ 990 แต่บอกว่าเป็น USD จะเท่ากับเกือบ 35,000 บาทในสายตาของระบบ) ควรใช้ ISO Currency Code ที่ถูกต้องเสมอ (`THB` สำหรับไทย)

### การตั้งค่า Purchase ผ่าน Custom Conversion เมื่อไม่มี Dynamic Value

ถ้าธุรกิจยังไม่มีระบบส่ง dynamic value จริง (เช่น เว็บ Landing Page ง่าย ๆ ที่ราคาสินค้าคงที่) สามารถตั้งค่าคงที่ผ่าน Custom Conversion ได้ (Events Manager → Custom Conversions → เลือก Purchase Event เป็นฐาน → ใส่ Default Value) แต่วิธีนี้เป็นทางเลือกรองเท่านั้น ควรผลักดันให้มี dynamic value จริงโดยเร็วที่สุดเมื่อธุรกิจเติบโตขึ้น

---

## Step 143: ตั้งค่า Lead และ CompleteRegistration Event

### ความแตกต่างระหว่าง Lead และ CompleteRegistration

- **Lead:** ใช้เมื่อลูกค้าแสดงความสนใจแต่ยังไม่ใช่สมาชิก/ลูกค้าเต็มตัว เช่น กรอกฟอร์มขอใบเสนอราคา, กดสนใจดูรายละเอียดคอร์ส
- **CompleteRegistration:** ใช้เมื่อลูกค้าสมัครสมาชิก/ลงทะเบียนสำเร็จจริง เช่น สร้างบัญชีผู้ใช้ใหม่ในระบบ, สมัครเรียนคอร์สและได้รับ Login แล้ว

### ตัวอย่างโค้ดสำหรับฟอร์ม Lead Gen

```javascript
document.querySelector('#lead-form').addEventListener('submit', function(e) {
  fbq('track', 'Lead', {
    content_name: 'ฟอร์มขอใบเสนอราคา - แพ็กเกจ Premium',
    currency: 'THB',
    value: 0 // หรือประเมินมูลค่าเฉลี่ยของ Lead แต่ละราย เช่น 150 บาท
  });
});
```

**เทคนิคสำคัญ:** สำหรับธุรกิจ Lead Gen ที่มูลค่า Lead แต่ละคนไม่เท่ากัน (เช่น สายบางเบอร์ปิดง่ายกว่า) สามารถส่ง `value` เป็น **มูลค่าเฉลี่ยที่คาดหวัง (Predicted Value)** จากข้อมูลในอดีต เพื่อให้ระบบ Value Optimization ทำงานได้ แม้จะเป็นค่าประมาณก็ยังดีกว่าไม่มีเลย

ตัวอย่างการคำนวณ Predicted Value แบบง่าย: ถ้าจากข้อมูลย้อนหลัง 3 เดือนพบว่า Lead 100 คนปิดการขายได้ 12 คน มูลค่าเฉลี่ยต่อออเดอร์ 8,000 บาท ให้คำนวณ `predicted_value = (12/100) * 8000 = 960` บาทต่อ Lead แล้วนำค่านี้ไปใส่เป็น `value` เริ่มต้นของทุก Lead Event จนกว่าจะมีข้อมูลแยกตามคุณภาพ Lead ที่ละเอียดกว่านี้ (เช่น แยกตาม Source หรือ Landing Page ที่มา)

### สำหรับ Instant Form (Lead Ads บน Facebook เอง)

ถ้าใช้ Instant Form (ฟอร์มที่เปิดในแอป Facebook เอง ไม่ต้องออกไปเว็บไซต์) **ไม่ต้องยิง Pixel Event เอง** เพราะ Facebook รู้ผลลัพธ์อยู่แล้วในระบบ (Objective = Leads) แต่ถ้าต้องการส่งข้อมูล Lead กลับไปที่ CRM ของธุรกิจ ต้องใช้ **Meta Leads Integration** หรือเชื่อมผ่าน Zapier/Make/CRM Connector ซึ่งเป็นคนละกระบวนการจาก Pixel/CAPI (จะเรียนลึกใน Part 024)

### CompleteRegistration สำหรับธุรกิจ Membership/คอร์สออนไลน์

```javascript
// หลัง Backend ยืนยันว่าสร้างบัญชีสำเร็จและมี user_id แล้ว
fbq('track', 'CompleteRegistration', {
  content_name: 'สมัครสมาชิก Free Trial',
  currency: 'THB',
  value: 0,
  status: true // บอกว่าลงทะเบียนสำเร็จ (ไม่ใช่แค่กดปุ่ม)
});
```

ควรวาง Event นี้ **หลังจาก Backend ยืนยันการสร้างบัญชีสำเร็จแล้วเท่านั้น** ไม่ใช่ตอนกดปุ่ม Submit เพราะถ้า Backend ปฏิเสธ (เช่น อีเมลซ้ำ) แต่ Event ถูกยิงไปแล้ว จะทำให้ข้อมูลเพี้ยนเหมือนกรณี Purchase ที่อธิบายใน Case Study ของ Part 013

---

## Step 144: ตั้งค่า AddToCart, InitiateCheckout, ViewContent

### ทำไม Event กลาง Funnel เหล่านี้สำคัญ แม้ไม่ใช่ Event สุดท้าย

Event เหล่านี้มีบทบาท 2 อย่าง:

1. **เป็นสัญญาณเสริมให้ Machine Learning** — แม้ธุรกิจจะ Optimize ที่ Purchase เป็นหลัก แต่ข้อมูล ViewContent/AddToCart ช่วยให้อัลกอริทึมเข้าใจ "ลักษณะของคนที่มีโอกาสซื้อ" ได้ละเอียดขึ้น โดยเฉพาะช่วงที่ Purchase Event ยังมีปริมาณน้อย (ธุรกิจใหม่)
2. **เป็นฐานสร้าง Custom Audience สำหรับ Retargeting** — คนที่ดูสินค้าแต่ไม่ซื้อ (ViewContent ไม่มี Purchase), คนที่ใส่ตะกร้าแต่ไม่ checkout (AddToCart ไม่มี InitiateCheckout) คือกลุ่มเป้าหมาย Retargeting ที่มีค่าที่สุด (รายละเอียดเต็มอยู่ใน Part 047–049)

### ตัวอย่างโค้ดที่ครบสมบูรณ์ทั้ง 3 Event

```javascript
// ViewContent - วางในหน้าสินค้า
fbq('track', 'ViewContent', {
  content_ids: ['SKU12345'],
  content_type: 'product',
  content_name: 'เซรั่มวิตามินซี 30ml',
  content_category: 'Skincare',
  value: 990.00,
  currency: 'THB'
});

// AddToCart - ผูกกับปุ่มใส่ตะกร้า
document.querySelector('.add-to-cart-btn').addEventListener('click', function() {
  fbq('track', 'AddToCart', {
    content_ids: ['SKU12345'],
    content_type: 'product',
    value: 990.00,
    currency: 'THB'
  });
});

// InitiateCheckout - วางในหน้า checkout ก่อนกรอกข้อมูลชำระเงิน
fbq('track', 'InitiateCheckout', {
  content_ids: ['SKU12345', 'SKU00098'],
  num_items: 2,
  value: 1780.00,
  currency: 'THB'
});
```

### ข้อผิดพลาดที่พบบ่อยในระดับ Content Parameters

- ใส่ `content_ids` ไม่ตรงกับ Catalog ID ที่ใช้ในระบบ Catalog Sales/Dynamic Ads (Part 027) ทำให้ Dynamic Retargeting แสดงสินค้าผิดหรือไม่แสดงเลย ต้อง**ตรวจสอบให้ content_id ตรงกับ item id ใน Catalog Feed เป๊ะ ๆ**
- ลืมยิง ViewContent ในหน้า Category/Listing ที่ไม่ใช่หน้าสินค้าเดี่ยว — ทำให้พลาดสัญญาณจากคนที่กำลังเปรียบเทียบสินค้าอยู่ (ถ้าต้องการวัดผลจริงจัง ควรใช้ Custom Event แยก เช่น `ViewCategory` เพิ่มเติมนอกเหนือ Standard Event)

---

## Step 145: Priority Events สำหรับ iOS14+ (8 Events)

### ทำไมต้องเลือกแค่ 8 Event

ตามที่อธิบายหลักการไว้ใน Part 013 Step 128 (AEM) — Meta อนุญาตให้ธุรกิจกำหนด **Priority Event ได้สูงสุด 8 Event ต่อ 1 Domain ที่ Verify แล้ว** เพื่อให้ระบบ Aggregated Event Measurement รู้ว่าจะรายงานผลจากผู้ใช้ iOS ที่ Opt-out โดยยึด Event ไหนเป็นหลักเมื่อผู้ใช้คนเดียวทำหลาย Event ในวันเดียว

### วิธีตั้งค่า Priority Event

1. Events Manager → เลือก Pixel → แท็บ **Aggregated Event Measurement** (หรือเข้าทาง Settings → Web Events Configuration)
2. เลือก Domain ที่ต้องการตั้งค่า (ต้อง Verify แล้วเท่านั้น)
3. ระบบจะแสดงรายการ Event ทั้งหมดที่เคยยิงเข้ามาจาก Domain นี้ ให้ **ลากเรียงลำดับ (Drag to Reorder)** ตามความสำคัญจากบนลงล่าง (บนสุด = สำคัญที่สุด)
4. เลือกเฉพาะ 8 อันดับแรกที่จะใช้เป็น Priority (ระบบจะเก็บได้สูงสุด 8 ช่อง)
5. กด Save

### ลำดับความสำคัญที่แนะนำสำหรับธุรกิจ e-Commerce ทั่วไป

1. Purchase
2. InitiateCheckout
3. AddPaymentInfo
4. AddToCart
5. Lead
6. CompleteRegistration
7. ViewContent
8. Search

### ลำดับความสำคัญที่แนะนำสำหรับธุรกิจ Lead Generation

1. CompleteRegistration (ถ้ามี)
2. Lead
3. Schedule (ถ้ามีระบบจองนัด)
4. Contact
5. InitiateCheckout (ถ้ามีขั้นตอนกรอกข้อมูลเพิ่มเติม)
6. ViewContent
7. Search
8. PageView (ใส่ไว้ล่างสุดเพราะสำคัญน้อยที่สุดเสมอ)

### หลักการจัดลำดับที่ต้องเข้าใจ

ให้จัดจาก **Event ที่อยู่ปลาย Funnel และมีมูลค่าทางธุรกิจสูงสุดไว้บนสุดเสมอ** เพราะถ้าผู้ใช้ iOS คนหนึ่งทำ ViewContent → AddToCart → Purchase ในวันเดียวกัน ระบบจะรายงานเฉพาะ Purchase (อันดับสูงสุดที่ทำสำเร็จ) เท่านั้นสำหรับ Conversion ที่มาจาก AEM ถ้าจัดผิดโดยเอา ViewContent ไว้บนสุด ธุรกิจจะเห็นแค่ ViewContent ทั้งที่จริงมี Purchase เกิดขึ้น — ผิดพลาดร้ายแรงที่ทำให้มองข้ามยอดขายจริงไปเลย

---

## Step 146: Value Optimization และการส่ง Dynamic Value

### Value Optimization คืออะไร

เป็นระดับการ Optimize ที่สูงกว่า Conversion Optimization ทั่วไป โดยระบบจะไม่ใช่แค่หา "คนที่มีโอกาสซื้อ" แต่หา **"คนที่มีโอกาสซื้อในมูลค่าสูง"** สำหรับใช้ Value Optimization ได้อย่างมีประสิทธิภาพ ต้องมี:

1. Purchase Event ที่ส่ง `value` แบบ **Dynamic ตามยอดจริงของแต่ละออเดอร์** (ไม่ใช่ค่าคงที่)
2. ปริมาณ Purchase Event ที่มากพอ (Meta แนะนำอย่างน้อย ~50 Purchase/สัปดาห์ต่อ Ad Set เป็นเกณฑ์ทั่วไปสำหรับออกจาก Learning Phase ได้ดี)
3. Bid Strategy/Objective ที่รองรับ (เลือก Conversion Location = Website, Performance Goal = "Maximize Value of Conversions" ในขั้นตอนสร้างแคมเปญ Sales Objective)

### ตัวอย่างสถานการณ์ที่ Value Optimization ต่างจาก Conversion Optimization อย่างชัดเจน

ธุรกิจขายทั้งสินค้าราคา 200 บาท และแพ็กเกจ VIP ราคา 15,000 บาท ถ้าใช้ Conversion Optimization ธรรมดา ระบบจะพยายามหา "จำนวนคนซื้อให้มากที่สุด" ซึ่งมักได้คนซื้อสินค้า 200 บาทเยอะ (ปิดง่ายกว่า) แต่ถ้าเปลี่ยนเป็น Value Optimization ระบบจะเริ่มเอนเอียงไปหาคนที่มีพฤติกรรมคล้ายคนที่ซื้อแพ็กเกจ 15,000 บาท เพราะ "มูลค่ารวม" สำคัญกว่า "จำนวนครั้ง"

### Predicted LTV กับ Subscribe Event

สำหรับธุรกิจ Subscription สามารถส่งค่า `predicted_ltv` เสริมได้:

```javascript
fbq('track', 'Subscribe', {
  value: 299.00,
  currency: 'THB',
  predicted_ltv: 3588.00 // ประมาณการรายได้ตลอดอายุสมาชิก 12 เดือน
});
```

ค่านี้ช่วยให้ระบบมองเห็น "มูลค่าที่แท้จริง" ของลูกค้าคนนั้นในระยะยาว ไม่ใช่แค่ค่าสมาชิกเดือนแรก ซึ่งสำคัญมากสำหรับธุรกิจที่กำไรจริงมาจาก Retention ไม่ใช่แค่การขายครั้งแรก

---

## Step 147: Deduplication ระหว่าง Pixel และ CAPI

### ปัญหาที่ต้องแก้: นับ Event ซ้ำเมื่อมีทั้ง Browser และ Server

เมื่อธุรกิจติดตั้งทั้ง Pixel (Browser) และ CAPI (Server) สำหรับ Event เดียวกัน (เช่น Purchase เดียวกันถูกยิงทั้งจาก JavaScript หน้าเว็บ และจาก Backend ตอนยืนยันออเดอร์) ถ้าไม่มีระบบแยกแยะ Meta จะเห็นเป็น **2 Event คนละอันไปเลย** ทำให้ตัวเลข Purchase สูงเกินจริง 2 เท่า

### กลไก Deduplication ของ Meta

Meta ใช้ **`event_id`** เป็นตัวจับคู่: ถ้า Event จาก Browser และ Server มี `event_id` เดียวกัน + `event_name` เดียวกัน + เกิดในช่วงเวลาใกล้เคียงกัน (ภายใน 48 ชั่วโมง) ระบบจะรวมเป็น Event เดียวโดยอัตโนมัติ (นับแค่ 1 ครั้งในการ Optimize แต่ยังคงเก็บ log ของทั้งสองแหล่งไว้ดูใน Diagnostics)

### วิธี Implement ให้ถูกต้อง

**ฝั่ง Browser (JavaScript):**

```javascript
const orderId = 'ORDER98765'; // ดึงจาก Backend ตอนสร้างออเดอร์สำเร็จ
const eventId = 'purchase_' + orderId;

fbq('track', 'Purchase', {
  value: 1590.00,
  currency: 'THB'
}, {eventID: eventId});
```

**ฝั่ง Server (CAPI JSON Payload):**

```json
{
  "data": [
    {
      "event_name": "Purchase",
      "event_id": "purchase_ORDER98765",
      "event_time": 1758870000,
      "action_source": "website",
      "user_data": {
        "em": ["hashed_email_value"],
        "client_ip_address": "203.0.113.42",
        "client_user_agent": "Mozilla/5.0..."
      },
      "custom_data": {
        "value": 1590.00,
        "currency": "THB"
      }
    }
  ]
}
```

**กฎสำคัญ:** `event_id` ต้อง **เหมือนกันเป๊ะ** ทั้งสองฝั่ง (ตัวพิมพ์เล็ก-ใหญ่มีผล) และต้อง **ไม่ซ้ำกับออเดอร์อื่น** (ใช้ order_id เป็นฐานเสมอเพื่อความ unique) ถ้าใช้ timestamp อย่างเดียวเป็น event_id เสี่ยงชนกันได้ถ้ามีออเดอร์เข้ามาพร้อมกันหลายรายการในวินาทีเดียวกัน

สำหรับ Event ที่ไม่มี order_id ชัดเจน (เช่น ViewContent, PageView) สามารถใช้ combination ของ `session_id + timestamp + product_id` เป็นฐานสร้าง event_id แทนได้ ตราบใดที่ค่านี้ถูกสร้างขึ้นครั้งเดียวแล้วส่งให้ทั้ง Browser และ Server ใช้ค่าเดียวกันเสมอ ไม่ใช่คำนวณแยกกันคนละที่จนได้ค่าไม่ตรงกัน

### เมื่อไหร่ที่ไม่ต้องทำ Deduplication

ถ้าธุรกิจใช้ **แค่ Pixel อย่างเดียวโดยไม่มี CAPI เลย** ก็ไม่ต้องกังวลเรื่อง Deduplication เพราะไม่มีแหล่งข้อมูลที่สอง แต่ในทางกลับกัน ถ้าตัดสินใจเพิ่ม CAPI เข้ามาทีหลัง ต้อง**วางแผน event_id ให้พร้อมตั้งแต่ก่อน Launch จริง** ไม่ใช่ค่อยแก้ทีหลัง เพราะช่วงเปลี่ยนผ่านที่ event_id ยังไม่สมบูรณ์ จะทำให้ตัวเลขเพี้ยนไปช่วงหนึ่งซึ่งกระทบการอ่านผลลัพธ์แคมเปญที่กำลังวิ่งอยู่

### วิธีตรวจสอบว่า Deduplication ทำงานถูกต้อง

Events Manager → Overview → เลือก Purchase Event → ดูคอลัมน์ **"Deduplicated Events"** หรือ diagram ที่แสดง Venn Diagram ระหว่าง Browser/Server/Deduplicated ถ้าตัวเลข Deduplicated สูงใกล้เคียงกับผลรวม Browser+Server แสดงว่าระบบจับคู่ได้ดี แต่ถ้า Deduplicated ต่ำมาก (แทบไม่มีการรวม) แสดงว่า event_id ตั้งค่าไม่ตรงกัน ต้องกลับไปตรวจโค้ดทั้งสองฝั่ง

---

## Step 148: Data Processing Options และ Privacy Settings

### Data Processing Options (DPO) คืออะไร

เป็นระบบที่ Meta สร้างขึ้นเพื่อรองรับกฎหมาย California Consumer Privacy Act (CCPA) แต่แนวคิดเดียวกันนี้เกี่ยวข้องกับการปฏิบัติตามกฎหมายความเป็นส่วนตัวอื่น ๆ ทั่วโลก รวมถึง **PDPA ของไทย** (เรียนละเอียดใน Part 007 Step 64) ที่ควบคุมว่าข้อมูลลูกค้าจะถูกใช้ประมวลผลอย่างไร

ตั้งค่าได้ที่ Events Manager → Settings → Data Processing Options โดยสามารถกำหนดให้ Event บางประเภทหรือจาก Location บางแห่งถูกจำกัดการใช้งาน (Limited Data Use — LDU) เมื่อจำเป็นตามกฎหมายท้องถิ่น

### สิ่งที่นักยิงแอดไทยต้องรู้เกี่ยวกับ PDPA และ Pixel/CAPI

1. **ต้องมี Cookie Consent Banner ที่ชัดเจน** — แจ้งผู้ใช้ว่าเว็บไซต์ใช้ Pixel เก็บข้อมูลพฤติกรรมเพื่อการโฆษณา และให้สิทธิ์ปฏิเสธได้ (Opt-out)
2. **การ Hash ข้อมูลก่อนส่งผ่าน CAPI (SHA-256) ถือเป็นแนวปฏิบัติที่ดี** แต่ไม่ได้แปลว่าไม่ต้องขอความยินยอมเก็บข้อมูลตั้งแต่ต้น — PDPA กำหนดให้ต้องมี **วัตถุประสงค์ที่ชัดเจนและความยินยอม** ก่อนเก็บข้อมูลส่วนบุคคลเสมอ ไม่ใช่แค่ hash แล้วจบ
3. **ควรมี Privacy Policy ที่ระบุการใช้ Pixel/Cookie ของบุคคลที่สาม (Meta)** อย่างชัดเจนบนเว็บไซต์ทุกหน้าที่มีการเก็บข้อมูล
4. **สิทธิ์ในการขอลบข้อมูล (Right to be Forgotten)** — ถ้าลูกค้าขอให้ลบข้อมูล ธุรกิจต้องมีกระบวนการแจ้ง Meta ผ่าน Events Manager → Data Deletion Request (บางกรณีทำผ่าน Data Deletion API สำหรับแอปที่เชื่อมต่อ)

### แนวทางปฏิบัติที่แนะนำสำหรับธุรกิจไทย

- ติดตั้ง Consent Management Platform (CMP) เช่น Cookiebot, OneTrust หรือระบบ Custom ที่ทำเอง ให้ผู้ใช้เลือกได้ว่าจะยอมรับ Cookie เพื่อการตลาดหรือไม่ ก่อนที่ Pixel จะเริ่มยิง Event ใด ๆ
- ตั้งค่าให้ Pixel รอ Consent ก่อนเริ่มทำงาน (Consent Mode) แทนการยิงทันทีที่โหลดหน้าเว็บ เพื่อป้องกันความเสี่ยงทางกฎหมาย
- เก็บบันทึก (Log) ว่าผู้ใช้แต่ละคน Consent เมื่อไหร่ ไว้เป็นหลักฐานหากถูกตรวจสอบ

---

## Step 149: การตรวจสุขภาพ Event ด้วย Diagnostics

### Diagnostics Tab คืออะไร

Events Manager → แท็บ **Diagnostics** คือระบบที่ Meta สแกนข้อมูล Event ของเราโดยอัตโนมัติ แล้วแจ้งเตือนปัญหาที่พบเป็น 3 ระดับ:

- 🔴 **Severe (แดง):** ปัญหาร้ายแรงที่กระทบการ Optimize ทันที เช่น Event หยุดยิงกะทันหัน, Access Token ของ CAPI หมดอายุ
- 🟡 **Warning (เหลือง):** ปัญหาที่ควรแก้แต่ยังไม่กระทบรุนแรง เช่น EMQ ต่ำกว่าเกณฑ์, ขาดพารามิเตอร์บางตัว
- 🔵 **Info (น้ำเงิน):** ข้อเสนอแนะเพื่อปรับปรุงให้ดีขึ้น เช่น แนะนำให้เพิ่ม Advanced Matching

### ปัญหาที่ Diagnostics มักแจ้งบ่อยที่สุดและวิธีแก้

| ข้อความที่ Meta แจ้ง | ความหมาย | วิธีแก้ |
|---|---|---|
| "Purchase event has low match quality" | ขาด email/phone/fbc ในหลาย Event | เปิด Advanced Matching, ตรวจโค้ด CAPI ให้ส่ง user_data ครบ |
| "No activity detected in the last 24 hours" | Pixel หยุดยิงกะทันหัน | เช็คเว็บไซต์ว่าล่มหรือไม่, เช็คว่ามีการแก้โค้ดล่าสุดหรือไม่ |
| "Access token will expire soon" | Token ของ CAPI ใกล้หมดอายุ | Generate Token ใหม่ผ่าน Settings → Conversions API |
| "Value parameter missing" | Purchase Event บางส่วนไม่มี value | ตรวจ Logic การส่ง value ในโค้ด ให้ครอบคลุมทุกเคส (รวม edge case เช่น ส่วนลด 100%) |
| "Duplicate event IDs detected across different events" | event_id ถูกใช้ซ้ำผิดที่ผิดทาง | ตรวจสอบว่า event_id สร้างจาก order_id ที่ unique จริง ไม่ใช่ timestamp ซ้ำได้ |

### วินัยการตรวจ Diagnostics ที่แนะนำ

ควรเข้าไปดู Diagnostics **สัปดาห์ละครั้งเป็นอย่างน้อย** สำหรับบัญชีที่ใช้งบสูง หรือ **ทุกครั้งที่มีการแก้ไขเว็บไซต์/เปลี่ยน Developer/ย้าย Hosting** เพราะการเปลี่ยนแปลงฝั่งเว็บไซต์คือสาเหตุอันดับหนึ่งที่ทำให้ Pixel/CAPI พังโดยไม่มีใครรู้ตัวจนกว่าจะเห็นยอดขายตกโดยไม่มีสาเหตุ

### การตั้ง Automated Alert เพื่อไม่ต้องเข้าไปเช็คเอง

นอกจาก Manual Check แล้ว ยังตั้งค่าให้ Meta ส่งอีเมลแจ้งเตือนอัตโนมัติได้ที่ Events Manager → Settings → Alerts → เปิด Toggle "Email me about Pixel issues" วิธีนี้ช่วยให้รู้ปัญหาเร็วขึ้นโดยไม่ต้องรอเข้าไปดูเองทุกวัน แต่ไม่ควรใช้แทนการตรวจสอบด้วยตนเองทั้งหมด เพราะ Alert อัตโนมัติมักจับได้เฉพาะปัญหาระดับ Severe เท่านั้น ปัญหาระดับ Warning ที่ค่อย ๆ กัดกร่อนคุณภาพข้อมูล (เช่น EMQ ลดลงทีละน้อย) มักไม่ถูกส่งเป็น Alert และต้องอาศัยการเข้าไปดูด้วยตาเป็นระยะ

---

## Step 150: Workshop — Events Manager Health Check ฉบับเต็ม

ทำตามลำดับนี้กับ Pixel ของธุรกิจจริง (หรือ Pixel ทดสอบถ้ายังไม่มีธุรกิจจริง):

### ภารกิจที่ 1: ตรวจภาพรวม
เปิด Events Manager → Overview → บันทึกจำนวน Event แต่ละตัวใน 7 วันที่ผ่านมา (PageView, ViewContent, AddToCart, InitiateCheckout, Purchase) เขียนเป็นตาราง Funnel Drop-off คร่าว ๆ

### ภารกิจที่ 2: ตรวจ Purchase Event ให้ครบ
- ยืนยันว่ามี value/currency ครบทุก Event
- ยืนยันว่า value เป็นผลรวมออเดอร์จริง ไม่ใช่ราคาสินค้าชิ้นแรก
- เทียบตัวเลขกับยอดขายจริงจากระบบหลังบ้าน คำนวณ % ความคลาดเคลื่อน

### ภารกิจที่ 3: ตั้ง Priority Event
เข้า Aggregated Event Measurement Settings → จัดลำดับ 8 Priority Event ให้ตรงกับลักษณะธุรกิจ (อ้างอิงจาก Step 145) บันทึกภาพก่อน-หลัง

### ภารกิจที่ 4: ตรวจ Deduplication
ถ้ามีทั้ง Pixel และ CAPI ให้เช็คคอลัมน์ Deduplicated Events ว่าทำงานถูกต้อง ถ้ายังไม่มี CAPI ให้บันทึกแผนว่าจะ Implement event_id อย่างไรตอนเริ่มทำ CAPI

### ภารกิจที่ 5: ไล่ Diagnostics ทุกข้อความ
เปิดแท็บ Diagnostics แก้ไขทุกข้อความสีแดงก่อน จากนั้นไล่แก้สีเหลืองทีละข้อ บันทึกผลก่อน-หลังเป็นตาราง

### ภารกิจที่ 6: สรุปคะแนนสุขภาพ Pixel
ให้คะแนนตัวเองแบบ 1–10 ในแต่ละมิติ: EMQ, Deduplication, Diagnostics (ไม่มี Severe), Priority Event ครบ 8 ตัว, Privacy Compliance แล้วเขียน Action Plan สำหรับข้อที่ยังไม่ถึง 8 คะแนน

---

## คำถามที่พบบ่อย (FAQ) ของ Part นี้

**Q: ทำไมตัวเลข Purchase ใน Events Manager กับ Ads Manager ไม่เท่ากัน?**
A: Events Manager แสดง **Raw Event ทั้งหมด** ที่ยิงเข้ามาไม่ว่าจะมาจากโฆษณาหรือไม่ก็ตาม (เช่น Traffic จาก SEO, Direct, Email ก็นับด้วย) ส่วน Ads Manager แสดงเฉพาะ Conversion ที่ **Attributed** กับโฆษณาตาม Attribution Window ที่ตั้งไว้ (เช่น 7-day click, 1-day view) ตัวเลขทั้งสองจึงไม่จำเป็นต้องเท่ากัน และควรใช้ Events Manager เป็นตัวเช็คสุขภาพระบบ ใช้ Ads Manager เป็นตัวประเมินผลโฆษณา

**Q: ควรตั้ง Priority Event ใหม่บ่อยแค่ไหน?**
A: ไม่ควรเปลี่ยนบ่อยเกินไปเพราะกระทบ Learning Phase และการรายงานผลย้อนหลัง แนะนำให้ตั้งครั้งแรกให้รอบคอบตามลักษณะธุรกิจ แล้วรีวิวใหม่เฉพาะเมื่อธุรกิจเปลี่ยนโมเดลรายได้อย่างมีนัยสำคัญ (เช่น จากขายสินค้าเดี่ยวเปลี่ยนเป็น Subscription)

**Q: Advanced Matching ปลอดภัยกับข้อมูลลูกค้าไหม เพราะดึง email/phone จากฟอร์มไปเลย?**
A: Advanced Matching จะ hash ข้อมูล (SHA-256) ที่ฝั่ง Browser ก่อนส่งออกไปเสมอ ไม่ส่ง Plain Text ออกจากเครื่องผู้ใช้ อย่างไรก็ตามธุรกิจยังมีหน้าที่แจ้งผู้ใช้ในนโยบายความเป็นส่วนตัวว่ามีการส่งข้อมูลไปประมวลผลกับบุคคลที่สาม (Meta) ตามที่อธิบายใน Step 148

**Q: ถ้าเพิ่งเริ่มธุรกิจใหม่ ยังไม่มี Purchase Event เลย ควร Optimize ด้วย Event ไหน?**
A: ควร Optimize ด้วย Event ที่ปริมาณมากพอในช่วงแรก เช่น AddToCart หรือ InitiateCheckout เพื่อให้ระบบพอมีข้อมูลเรียนรู้ (Learning Phase ต้องการ Volume) แล้วค่อยขยับไป Optimize ที่ Purchase เมื่อมีข้อมูลสะสมมากพอ (แนวทางนี้เรียกว่า Funnel-based Optimization Ladder)

**Q: EMQ กับ Quality Ranking (Ad Relevance Diagnostics) ใน Part 009 เกี่ยวข้องกันไหม?**
A: เป็นคะแนนคนละชุด — EMQ วัดคุณภาพการจับคู่ข้อมูล Event กับผู้ใช้ Facebook ส่วน Ad Relevance Diagnostics (Quality/Engagement/Conversion Ranking) วัดคุณภาพของตัวโฆษณาเอง (ครีเอทีฟ, Landing Page) เทียบกับคู่แข่งที่แข่งประมูลกลุ่มเป้าหมายเดียวกัน ทั้งสองค่ามีผลต่อผลลัพธ์แคมเปญ แต่แก้ไขด้วยวิธีที่แตกต่างกันโดยสิ้นเชิง

---

## Case Study: ธุรกิจคอร์สออนไลน์ที่เพิ่ม ROAS โดยไม่เพิ่มงบ ด้วยการทำ Health Check

สถาบันสอนภาษาออนไลน์รายหนึ่งยิงแอด Lead Generation มา 6 เดือน CPA ต่อ Lead อยู่ที่ประมาณ 180 บาท ซึ่งสูงกว่าที่ตั้งเป้าไว้ (120 บาท) ทีมงานพยายามแก้ด้วยการเปลี่ยนครีเอทีฟและ Audience หลายรอบแต่ไม่ดีขึ้น

เมื่อเข้าไปทำ Events Manager Health Check ตามขั้นตอนใน Workshop พบปัญหาที่ไม่มีใครสังเกตมาก่อน:

1. **EMQ ของ Lead Event อยู่ที่ 3.2 เท่านั้น** — ต่ำมาก เพราะฟอร์มสมัครไม่ได้ส่ง email/phone ไปกับ Pixel Event เลย (ส่งแค่ Event เปล่า ๆ ไม่มี user_data เสริม)
2. **Diagnostics แจ้งเตือนสีเหลือง "Lead event has low match quality" มาตลอด 4 เดือน** แต่ไม่มีใครในทีมเคยเปิดดูแท็บนี้เลย
3. **ไม่มี CAPI ติดตั้งอยู่เลย** ทั้งที่กลุ่มลูกค้าเป้าหมาย (นักเรียน/นักศึกษาที่ใช้ iPhone) มีสัดส่วนสูงถึง 55% ของ Traffic

การแก้ไข:
- เปิดใช้ **Automatic Advanced Matching** ทันที ทำให้ Pixel ดึง email/phone จากฟอร์มมาช่วย hash และส่งอัตโนมัติโดยไม่ต้องแก้โค้ด
- ติดตั้ง CAPI ผ่าน Server-Side GTM (ตามวิธีใน Part 014 Step 136) เพื่อส่ง Lead Event จาก Backend อีกชั้น พร้อมทำ Deduplication ด้วย event_id
- จัด Priority Event ใหม่ให้ Lead อยู่อันดับ 1 (เดิมไม่ได้ตั้งค่าอะไรเลย ปล่อยให้ระบบเลือกอัตโนมัติซึ่งไม่ตรงกับความสำคัญทางธุรกิจ)

ผลลัพธ์หลัง 3 สัปดาห์: EMQ ขึ้นจาก 3.2 เป็น 7.8, CPA ต่อ Lead ลดลงจาก 180 บาท เป็น 128 บาท โดย **ไม่ได้เปลี่ยนครีเอทีฟหรือ Audience เลยแม้แต่ตัวเดียว** — พิสูจน์ให้เห็นว่าปัญหาพื้นฐานเรื่อง Tracking บางครั้งสำคัญกว่าการปรับแคมเปญผิวเผินมาก

---

## ตารางสรุปพารามิเตอร์ Custom Data ที่ใช้บ่อยที่สุด

| พารามิเตอร์ | ประเภทข้อมูล | ใช้กับ Event | ตัวอย่างค่า |
|---|---|---|---|
| `value` | number | ทุก Conversion Event | `990.00` |
| `currency` | string (ISO Code) | ทุก Conversion Event | `"THB"` |
| `content_ids` | array of string | ViewContent, AddToCart, Purchase | `["SKU123"]` |
| `content_type` | string | ViewContent, AddToCart, Purchase | `"product"` |
| `content_name` | string | ViewContent, Lead | `"เซรั่มวิตามินซี"` |
| `content_category` | string | ViewContent | `"Skincare"` |
| `num_items` | integer | InitiateCheckout, Purchase | `3` |
| `predicted_ltv` | number | Subscribe | `3588.00` |
| `status` | boolean | CompleteRegistration | `true` |
| `search_string` | string | Search | `"ครีมกันแดด SPF50"` |

การจดจำตารางนี้ให้แม่นช่วยให้เขียนโค้ด Event ได้ถูกต้องโดยไม่ต้องเปิดเอกสารทุกครั้ง และช่วยตรวจสอบโค้ดของ Developer ได้เร็วขึ้นเมื่อมีปัญหา

---

## Checklist ท้ายบท

- [ ] เข้าใจโครงสร้างหน้าจอ Events Manager และรู้ว่าดูตัวเลขอะไรตรงไหน
- [ ] Purchase Event ทุกครั้งมี value/currency ที่ถูกต้องและเป็นผลรวมออเดอร์จริง
- [ ] Lead/CompleteRegistration ถูกวางในตำแหน่งที่ถูกต้อง (หลัง Backend ยืนยันสำเร็จ)
- [ ] AddToCart, InitiateCheckout, ViewContent ยิงครบและมี content_ids ตรงกับ Catalog
- [ ] ตั้ง Priority Event 8 ตัวเรียงลำดับตามความสำคัญทางธุรกิจแล้ว
- [ ] เข้าใจและ (ถ้าเป็นไปได้) ใช้งาน Value Optimization สำหรับธุรกิจที่มีสินค้าหลายราคา
- [ ] ทำ Deduplication ด้วย event_id ระหว่าง Pixel และ CAPI แล้ว (ถ้ามีทั้งสองระบบ)
- [ ] มี Cookie Consent และ Privacy Policy ที่สอดคล้องกับ PDPA
- [ ] ไม่มี Diagnostics สีแดงเหลืออยู่ และไล่แก้สีเหลืองแล้วเป็นระบบ
- [ ] ทำ Health Check เป็นประจำ (แนะนำสัปดาห์ละครั้ง) ไม่ใช่แค่ตอนตั้งค่าครั้งแรก

---

## Workshop / แบบฝึกหัด

**แบบฝึกหัดที่ 1 — Health Check เต็มรูปแบบ**
ทำตามภารกิจทั้ง 6 ข้อใน Step 150 กับ Pixel จริงของธุรกิจ บันทึกผลเป็นรายงาน 1 หน้าพร้อมคะแนนสุขภาพและ Action Plan

**แบบฝึกหัดที่ 2 — จัดลำดับ Priority Event**
สมมติธุรกิจ 3 แบบ (e-Commerce, Lead Gen, Subscription SaaS) ให้จัดลำดับ Priority Event 8 ตัวสำหรับแต่ละแบบ พร้อมอธิบายเหตุผลการจัดลำดับทุกอันดับ

**แบบฝึกหัดที่ 3 — เขียนโค้ด Deduplication**
เขียน pseudo-code (หรือโค้ดจริงถ้าถนัด) แสดงการสร้าง event_id ที่ใช้ร่วมกันระหว่าง Browser Pixel และ Server CAPI สำหรับ Event `CompleteRegistration` ของระบบสมาชิกที่มี user_id เป็นตัวเลข

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ทำให้ Events Manager ไม่ใช่แค่หน้าจอที่เปิดดูผ่าน ๆ อีกต่อไป แต่เป็นเครื่องมือวินิจฉัยสุขภาพระบบวัดผลที่ต้องเข้าไปดูสม่ำเสมอ ตั้งแต่การตั้งค่า Purchase ให้มี Value ที่แม่นยำ, จัดลำดับ Priority Event ให้ตรงกับธุรกิจ, ทำ Deduplication ให้สมบูรณ์, ไปจนถึงการปฏิบัติตามกฎหมายความเป็นส่วนตัว และการไล่แก้ Diagnostics อย่างเป็นระบบ

เมื่อระบบวัดผล (Foundation) แน่นแล้ว ขั้นต่อไปคือการนำ Foundation นี้ไปใช้สร้างแคมเปญจริง Part 016 จะพาไปเจาะลึกโครงสร้าง 3 ชั้นของ Facebook Ads — Campaign, Ad Set, Ad — ว่าแต่ละชั้นควบคุมอะไร ตั้งค่าอย่างไรให้เป็นระบบ และวางโครงสร้างมาตรฐานที่จะใช้ซ้ำได้กับทุกแคมเปญในอนาคต

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center: Events Manager Overview — https://www.facebook.com/business/help
- Meta for Developers: Value Optimization Documentation — https://developers.facebook.com/docs/marketing-api/optimization
- Meta Business Help Center: Aggregated Event Measurement Priority Setup
- Meta for Developers: Deduplicate Meta Pixel and Conversions API Events — https://developers.facebook.com/docs/marketing-api/conversions-api/deduplicate-pixel-and-server-events
- สำนักงานคณะกรรมการคุ้มครองข้อมูลส่วนบุคคล (PDPC): https://www.pdpc.or.th
- Meta Business Help Center: Data Processing Options
