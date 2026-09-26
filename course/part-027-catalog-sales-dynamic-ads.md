# Part 027: สร้างแคมเปญ Catalog Sales และ Dynamic Ads

**Section:** C — Facebook Ads Manager Deep Dive: Setup & Structure
**Step ที่ครอบคลุม:** Step 261–270 (จาก 1000 Steps ทั้งหลักสูตร)
**เวลาที่ใช้เรียนโดยประมาณ:** 5–6 ชั่วโมง (รวมเวลาลงมือทำ Workshop จริงกับ Catalog และ Feed ของธุรกิจตัวเอง)

Part นี้ต่อเนื่องจาก Part 026 ที่คุณเรียนรู้การสร้างแคมเปญ Conversions (Purchase, Add to Cart) แบบ Manual ไปแล้ว ทีนี้เราจะยกระดับขึ้นไปอีกขั้น เข้าสู่โลกของ **Catalog Sales** และ **Dynamic Ads** ซึ่งเป็นเครื่องมือที่ร้านค้าออนไลน์ที่มีสินค้าตั้งแต่ 10 SKU ขึ้นไป "ต้องมี" ในกระเป๋าเครื่องมือ เพราะมันคือความต่างระหว่างการทำแอดที่ต้องนั่งไล่สร้างทีละภาพทีละสินค้า กับการให้ระบบดึงสินค้าที่ "ใช่" มาโชว์ให้คนที่ "ใช่" โดยอัตโนมัติ เป็นพันเป็นหมื่นชิ้น พร้อมกัน

ถ้าคุณเป็นนักยิงแอดที่รับงานร้านค้าออนไลน์ ร้านเสื้อผ้า ร้านเครื่องสำอาง ร้านอุปกรณ์ IT หรือเว็บอีคอมเมิร์ซทุกประเภท เนื้อหาใน Part นี้คือทักษะที่แยกมือใหม่กับมือโปรออกจากกันอย่างชัดเจน

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 261:** Catalog และ Dynamic Ads คืออะไร ต่างจากโฆษณาทั่วไปอย่างไร และทำไมถึงสำคัญกับธุรกิจที่มีสินค้าหลายตัว
2. **Step 262:** สร้าง Catalog ใน Commerce Manager แบบ Step-by-Step ตั้งแต่เลือกประเภทธุรกิจจนถึงเชื่อม Pixel
3. **Step 263:** รูปแบบ Feed ทั้งหมด (CSV/TSV, XML/RSS, Google Sheets, API) และ Field ที่จำเป็นต้องมีในทุกแถวสินค้า
4. **Step 264:** การอัปโหลดและอัปเดต Feed แบบอัตโนมัติผ่าน Scheduled Fetch, API, และ Partner Platform (Shopify/WooCommerce)
5. **Step 265:** เชื่อม Pixel/Conversions API กับ Catalog เพื่อให้ Dynamic Ads จับคู่สินค้าได้แม่นยำ (content_id matching)
6. **Step 266:** สร้างแคมเปญ Dynamic Ads (Catalog Sales) แบบ Step-by-Step ใน Ads Manager
7. **Step 267:** Advantage+ Catalog Ads คืออะไร ใช้แทน Manual Dynamic Ads ได้เมื่อไหร่
8. **Step 268:** Product Sets — แบ่งกลุ่มสินค้าเพื่อทำ Cross-sell, Upsell, และ Retargeting แบบเจาะจง
9. **Step 269:** Dynamic Ads Retargeting Funnel (Viewed → Add to Cart → Purchased) และ Dynamic Ads แบบ Broad Audience สำหรับ Prospecting
10. **Step 270:** Creative Template สำหรับ Catalog Ads, Feed Error ที่พบบ่อยที่สุดและวิธีแก้ไข, พร้อม Workshop สร้าง Catalog และแคมเปญ Dynamic Retargeting จริง 1 ตัว

---

## Step 261: Catalog และ Dynamic Ads คืออะไร ต่างจากโฆษณาทั่วไปอย่างไร

### นิยามที่ต้องเข้าใจให้แม่นก่อน

**Catalog** คือ "คลังข้อมูลสินค้า" ของคุณที่ Meta เก็บไว้ในระบบของตัวเอง ประกอบด้วยข้อมูลสินค้าทุกตัวที่คุณขาย เช่น ชื่อ ราคา รูปภาพ ลิงก์ไปหน้าสินค้า สต็อกคงเหลือ ฯลฯ โดยข้อมูลนี้จะถูกส่งเข้ามาผ่านไฟล์ที่เรียกว่า **Feed** (จะอธิบายละเอียดใน Step 263)

**Dynamic Ads** คือรูปแบบโฆษณาที่ "ดึง" ข้อมูลจาก Catalog มาสร้างโฆษณาแบบอัตโนมัติ โดยระบบจะเลือกสินค้าที่เหมาะสมกับผู้ใช้แต่ละคนมาแสดง — คนละสินค้า คนละราคา คนละภาพ ขึ้นอยู่กับพฤติกรรมของคนคนนั้นบนเว็บไซต์หรือแอปของคุณ

พูดง่ายๆ คือ: โฆษณาทั่วไป (Static Ads) คุณสร้าง 1 ครีเอทีฟ ทุกคนเห็นเหมือนกัน ส่วน Dynamic Ads คุณสร้าง "แม่แบบ" (Template) 1 ชุด แล้วระบบ auto-generate โฆษณาที่ต่างกันเป็นพันเป็นหมื่นชิ้น ตามสินค้าใน Catalog และตามคนที่เห็น

### ตัวอย่างที่เห็นภาพชัด

ลูกค้าชื่อ "แนน" เข้าเว็บไซต์ร้านรองเท้าของคุณ ดูรองเท้าผ้าใบสีขาวรุ่น A แล้วออกจากเว็บโดยไม่ซื้อ วันต่อมาแนนเลื่อน Facebook Feed แล้วเห็นโฆษณาที่มีภาพรองเท้าผ้าใบสีขาวรุ่น A ตัวเดียวกันที่เพิ่งดู พร้อมราคาและปุ่ม "ซื้อเลย" — นี่คือ Dynamic Ads ที่ทำงานแบบ Retargeting

ขณะเดียวกัน ลูกค้าอีกคนชื่อ "ต้น" ที่ไม่เคยเข้าเว็บไซต์เลย แต่มีพฤติกรรมคล้ายคนที่เคยซื้อรองเท้าวิ่งไปแล้ว อาจเห็นโฆษณาที่มีรองเท้าวิ่งรุ่นขายดีของร้านคุณโชว์อยู่ — นี่คือ Dynamic Ads แบบ Prospecting/Broad Audience

ทั้งสองกรณีนี้ Ads Manager สร้างจาก **แคมเปญเดียว** และ **ครีเอทีฟเทมเพลตเดียว** แต่แสดงผลต่างกันหมด เพราะระบบดึงข้อมูลจาก Catalog มาประกอบเอง

### ทำไมต้องใช้ Catalog + Dynamic Ads แทนโฆษณาทั่วไป

1. **ประหยัดเวลาสร้างครีเอทีฟมหาศาล** — ร้านที่มี 500 SKU ไม่ต้องนั่งทำกราฟิก 500 ภาพ ทำ Feed ครั้งเดียว ระบบดึงภาพจากลิงก์ในไฟล์ Feed มาใช้ทั้งหมด
2. **Personalization ระดับรายบุคคล** — โฆษณาที่ตรงกับสิ่งที่คนสนใจจริงๆ ย่อม Convert ดีกว่าโฆษณากว้างๆ เสมอ งานวิจัยภายในของ Meta และ case study จากหลายธุรกิจพบว่า Dynamic Retargeting มี ROAS สูงกว่า Static Retargeting โดยเฉลี่ย 2-3 เท่า
3. **สเกลง่าย** — เมื่อสินค้าใหม่เข้ามาใน Feed โฆษณาจะครอบคลุมสินค้านั้นทันทีโดยไม่ต้องสร้างแอดใหม่
4. **ใช้ได้ทั้ง Retargeting และ Prospecting** — ไม่ได้จำกัดแค่คนที่เคยเข้าเว็บ (จะอธิบายใน Step 269)
5. **รองรับ Cross-sell/Upsell อัตโนมัติ** — เช่น คนซื้อกล้องไปแล้ว ระบบโชว์เลนส์หรือกระเป๋ากล้องตาม (ผ่าน Product Sets ใน Step 268)

### ธุรกิจแบบไหนที่ควรใช้ Catalog + Dynamic Ads

- ร้านค้าออนไลน์ที่มีสินค้าตั้งแต่ 10 SKU ขึ้นไป (ยิ่งมากยิ่งเห็นผลชัด)
- ธุรกิจ E-commerce ที่มีเว็บไซต์ของตัวเอง (Shopify, WooCommerce, Magento, Custom)
- ธุรกิจท่องเที่ยว/โรงแรม (Catalog แบบ Travel — ไม่ได้ครอบคลุมลึกใน Part นี้แต่หลักการ Feed เหมือนกัน)
- ธุรกิจอสังหาริมทรัพย์ (Catalog แบบ Real Estate)
- ธุรกิจรถยนต์มือสอง (Catalog แบบ Auto)

ธุรกิจที่ **ไม่จำเป็น** ต้องใช้ Catalog: ธุรกิจบริการที่ขายแพ็กเกจเดียว (เช่น คลินิกที่ขายคอร์สโบท็อกซ์ 1 แพ็กเกจ), คอร์สออนไลน์ 1-2 คอร์ส, ธุรกิจที่ปิดการขายผ่านแชทเป็นหลัก — กรณีนี้ Manual Conversion Campaign จาก Part 026 เพียงพอแล้ว

### ข้อผิดพลาดที่พบบ่อยตั้งแต่จุดเริ่มต้น

- เข้าใจผิดว่า Catalog ใช้ได้เฉพาะร้านที่ขายของจริง (สินค้าจับได้) เท่านั้น — ที่จริงใช้ได้กับดิจิทัลโปรดักต์ที่มีหลายรายการเช่นกัน (เช่น คอร์สออนไลน์ 30 คอร์ส)
- คิดว่า Dynamic Ads ใช้แทน Static Creative ได้ 100% — ความจริงคือควรใช้ "คู่กัน" Dynamic Ads เก่งเรื่อง Retargeting/Personalization แต่ Static/Video Ads ยังจำเป็นสำหรับสร้าง Awareness และ Storytelling
- ไม่เตรียมรูปสินค้าให้มีคุณภาพก่อนทำ Feed — ภาพเบลอ ภาพมีโลโก้บังสินค้า พื้นหลังรก จะทำให้ Dynamic Ads ดูไม่น่าเชื่อถือ

### ความสัมพันธ์ระหว่าง Catalog กับ Objective อื่นๆ ที่เรียนมาแล้ว

หลายคนสงสัยว่า Catalog Sales เป็น Objective แยกจาก Sales Objective ที่เรียนใน Part 026 หรือไม่ — คำตอบคือ **ไม่ใช่ Objective แยก** แต่เป็น "โหมด" ที่ซ้อนอยู่ภายใต้ Sales Objective ตัวเดียวกัน ตอนสร้างแคมเปญคุณจะยังเลือก Objective เป็น Sales เหมือนเดิม เพียงแต่ที่ Campaign Level จะมีตัวเลือกเพิ่มขึ้นมาว่าจะทำแบบ "Manual/Standard" (ไม่ใช้ Catalog) หรือทำแบบ "Catalog" (ผูกกับ Catalog ที่สร้างไว้) ความเข้าใจผิดจุดนี้ทำให้มือใหม่หลายคนไปหา Objective ชื่อ "Catalog Sales" แบบเดี่ยวๆ ใน Ads Manager ไม่เจอ แล้วคิดว่า Meta เอาฟีเจอร์นี้ออกไปแล้ว ทั้งที่จริงมันซ่อนอยู่ในขั้นตอนถัดไปของ Sales Objective นั่นเอง

### Dynamic Ads ทำงานร่วมกับ Placement ไหนได้บ้าง

Dynamic Ads ไม่ได้จำกัดอยู่แค่ Feed เท่านั้น ปัจจุบันรองรับ:
- Facebook Feed, Instagram Feed
- Facebook และ Instagram Stories
- Instagram Reels และ Facebook Reels
- Marketplace
- Audience Network (สำหรับบางประเทศ/บางบัญชี)

ข้อจำกัดที่ต้องรู้คือ Placement แนวตั้ง (Stories/Reels) ต้องการภาพสินค้าที่ Crop ได้สัดส่วน 9:16 สวยงาม ถ้า Feed ของคุณมีแต่ภาพสินค้าสัดส่วน 1:1 บนพื้นหลังสีขาว ระบบจะ Auto-crop ให้ แต่บางครั้งจะเหลือพื้นที่ว่างด้านบน-ล่างมาก ทำให้ดูไม่เต็มจอ วิธีแก้คือเตรียม `additional_image_link` เป็นภาพสัดส่วนแนวตั้งแยกไว้ในหมวด Lifestyle Photography (สินค้าอยู่ในบริบทการใช้งานจริง) เพื่อให้ระบบเลือกใช้ในโฆษณา Placement แนวตั้งได้สวยกว่า

---

## Step 262: สร้าง Catalog ใน Commerce Manager แบบ Step-by-Step

### เข้าสู่ Commerce Manager

Catalog ไม่ได้ถูกสร้างใน Ads Manager แต่สร้างใน **Commerce Manager** ซึ่งเป็นเครื่องมือแยกที่เชื่อมกับ Business Manager ของคุณ

ขั้นตอน:
1. ไปที่ **business.facebook.com/commerce_manager** หรือเข้าจาก Business Settings > เมนูซ้าย "Data Sources" > "Catalogs"
2. คลิก **"Add Catalog"** (หรือ "สร้าง Catalog")
3. เลือกประเภทธุรกิจ (Catalog Type) — ตัวเลือกที่มี:
   - **E-commerce** — สำหรับร้านค้าออนไลน์ทั่วไป (ตัวเลือกที่ใช้บ่อยที่สุด และเป็นตัวเลือกหลักของ Part นี้)
   - **Hotels** — สำหรับโรงแรม
   - **Flights** — สำหรับสายการบิน
   - **Destinations** — สำหรับสถานที่ท่องเที่ยว
   - **Home Listings** — สำหรับอสังหาริมทรัพย์
   - **Vehicles** — สำหรับรถยนต์
4. ตั้งชื่อ Catalog — แนะนำให้ใช้ Naming Convention ที่สื่อความหมาย เช่น `[ชื่อธุรกิจ]-EC-Catalog-TH` เพื่อให้แยกง่ายเวลามีหลาย Business/หลายประเทศ
5. เลือก Business Manager ที่จะเป็นเจ้าของ Catalog นี้ (ถ้าคุณดูแลหลาย Business ต้องเลือกให้ถูก)
6. คลิก **Create**

### เชื่อม Catalog กับ Business Manager และ Ad Account

หลังสร้าง Catalog เสร็จ ต้องทำ 2 อย่างต่อ:

1. **Assign Ad Account** — ไปที่ Catalog Settings > "Ad Account Associations" > เลือก Ad Account ที่จะใช้ Catalog นี้ยิงแอด (Ad Account ต้องอยู่ใน Business Manager เดียวกัน หรือได้รับสิทธิ์ Partner Access)
2. **Assign Pixel/Dataset** — ไปที่ Catalog Settings > "Dataset" (บางเวอร์ชันเรียก "Domains" หรือ "Data Sources") > เชื่อม Pixel ที่ติดตั้งอยู่บนเว็บไซต์ของคุณ (Pixel ตัวนี้ต้องเป็นตัวเดียวกับที่ใช้ยิง Conversion Campaign เพื่อให้ Dynamic Ads แม่นยำ)

### ตั้งค่า Domain สำหรับ Catalog (สำคัญมาก)

ไปที่ Catalog > Settings > "Sales Channels" หรือ "Website" > ใส่โดเมนเว็บไซต์ของคุณ (เช่น `www.yourshop.com`) ต้องเป็นโดเมนเดียวกับที่ผ่าน **Domain Verification** แล้วใน Business Manager (ย้อนกลับไปดู Part 011 Step 108) เพราะ Dynamic Ads จะไม่ทำงานถ้าโดเมนไม่ยืนยัน

### สิทธิ์การเข้าถึง Catalog (Roles)

ไปที่ Catalog Settings > "Catalog Access" (People and assets ในบางเวอร์ชัน) เพื่อกำหนดว่าใครในทีมมีสิทธิ์:
- **Advertise** — ใช้ Catalog ในการยิงแอดได้ แต่แก้ไข Feed ไม่ได้
- **Manage Catalog** — แก้ไข Feed, Product Sets, Settings ได้เต็มรูปแบบ
- **Full Control** — ควบคุมทุกอย่างรวมถึงลบ Catalog

สำหรับเอเจนซี่ที่รับงานลูกค้าหลายราย แนะนำให้ตั้ง Catalog แยกต่อลูกค้า 1 Catalog และให้สิทธิ์ทีมงานเฉพาะ Catalog ของลูกค้านั้น ไม่ควรรวม Catalog ของลูกค้าหลายคนไว้ที่เดียวเพื่อป้องกันความสับสนและความเสี่ยงข้อมูลรั่ว

### ข้อผิดพลาดที่พบบ่อย

- สร้าง Catalog ผิดประเภท (เลือก Hotels ทั้งที่ขายสินค้าทั่วไป) ทำให้ Field ที่ต้องกรอกไม่ตรงกับสินค้าจริง
- ลืม Assign Pixel เข้า Catalog ทำให้ Dynamic Ads ยิงได้แต่ไม่ Optimize ตาม Signal ของผู้ใช้จริง
- ใช้ Ad Account คนละ Business Manager กับ Catalog โดยไม่ทำ Partner Access ทำให้เลือก Catalog ไม่เจอตอนสร้างแคมเปญ

---

## Step 263: รูปแบบ Feed ทั้งหมดและ Field ที่จำเป็นต้องมี

### Feed คืออะไร

Feed คือไฟล์ที่บรรจุข้อมูลสินค้าทั้งหมดของคุณ แต่ละแถว (Row) คือสินค้า 1 SKU แต่ละคอลัมน์ (Column) คือ Attribute หนึ่งตัว เช่น ชื่อ ราคา ลิงก์ Feed นี้คือ "หัวใจ" ของ Catalog — ถ้า Feed มีคุณภาพ Dynamic Ads จะทำงานดี ถ้า Feed มีข้อมูลผิดหรือขาด Dynamic Ads จะโชว์ผิดหรือไม่โชว์เลย

### รูปแบบไฟล์ที่ Meta รองรับ

| รูปแบบ | ใช้เมื่อไหร่ | ข้อดี | ข้อจำกัด |
|---|---|---|---|
| **CSV / TSV** | ร้านขนาดเล็ก-กลาง, ทำ Feed มือ หรือ export จากระบบหลังบ้าน | เปิดแก้ไขง่ายด้วย Excel/Google Sheets | ต้อง Upload/Fetch ใหม่ทุกครั้งที่มีการเปลี่ยนแปลง ถ้าไม่ตั้ง Auto-fetch |
| **XML / RSS** | ระบบ E-commerce ขนาดใหญ่, Feed ที่ export จาก CMS อัตโนมัติ | โครงสร้างชัดเจน รองรับ Nested Data | อ่านยากด้วยตาเปล่าเมื่อเทียบกับ CSV |
| **Google Sheets** | ร้านเล็ก-กลางที่อยากแก้ไขง่ายและเห็นการเปลี่ยนแปลง Real-time | แก้ไขร่วมกันได้, เชื่อมกับ Google Apps Script ได้ | ต้องตั้งค่า Sharing เป็น "Anyone with the link can view" ไม่งั้น Meta ดึงข้อมูลไม่ได้ |
| **API (Product Feed API / Commerce Platform API)** | ร้านที่มี Developer ทีมหรือใช้ Partner Platform | อัปเดต Real-time, แม่นยำสูงสุด | ต้องมีความรู้ Technical |
| **Partner Integration** (Shopify, WooCommerce, Magento) | ร้านที่ใช้ Platform เหล่านี้อยู่แล้ว | เชื่อมผ่าน App/Plugin ไม่ต้องทำ Feed เอง | ต้องพึ่งพา App บุคคลที่สาม อาจมี Field บางตัวที่ Sync ไม่ครบ |

### Field ที่จำเป็นต้องมี (Required Fields) — ท่องให้ขึ้นใจ

Meta กำหนด Field บังคับที่ทุกแถวใน Feed ต้องมี ไม่งั้นสินค้านั้นจะถูก "Reject" หรือไม่ถูกอนุมัติ:

1. **id** — รหัสสินค้าที่ไม่ซ้ำกัน (Unique) ควรตรงกับ `content_id` ที่ Pixel ยิงออกมาตอนคนดูสินค้า (เพื่อ Matching — สำคัญมากสำหรับ Step 265)
2. **title** — ชื่อสินค้า แนะนำไม่เกิน 150 ตัวอักษร ควรมี Brand + ชื่อสินค้า + คุณสมบัติเด่น เช่น "Nike Air Max 270 - สีขาว/ดำ Size 42"
3. **description** — คำอธิบายสินค้า (ไม่เกิน 5000 ตัวอักษร แต่ที่แสดงจริงในโฆษณาสั้นกว่านั้นมาก แนะนำเขียนให้กระชับ 1-2 บรรทัดแรกสำคัญที่สุด)
4. **availability** — สถานะสต็อก มีค่าที่ใช้ได้คือ `in stock`, `out of stock`, `preorder`, `available for order` (ถ้าสินค้า out of stock ระบบจะไม่โชว์ในโฆษณาโดยอัตโนมัติ — ฟีเจอร์นี้ป้องกันไม่ให้คุณโฆษณาสินค้าที่ขายหมดแล้ว)
5. **condition** — สภาพสินค้า: `new`, `refurbished`, `used`
6. **price** — ราคา ต้องมีสกุลเงินต่อท้าย เช่น `1290.00 THB` (รูปแบบต้องตรงตาม ISO currency code)
7. **link** — URL ไปยังหน้าสินค้าโดยตรง (Landing Page ของสินค้านั้นๆ ไม่ใช่หน้าแรกของเว็บ)
8. **image_link** — URL ของรูปภาพสินค้า ต้องเป็นรูปที่เข้าถึงได้แบบ Public ไม่ต้อง Login ขนาดแนะนำอย่างน้อย 500x500 px และเป็นภาพพื้นหลังโล่งไม่มีตัวอักษรทับมากเกินไป
9. **brand** — ชื่อแบรนด์สินค้า

### Field ที่แนะนำอย่างยิ่ง (Recommended Fields) เพื่อเพิ่มประสิทธิภาพ

- **google_product_category** — หมวดหมู่สินค้าตามมาตรฐาน Google Taxonomy ช่วยให้ Meta เข้าใจสินค้าและจับคู่ Audience แม่นยำขึ้น
- **fb_product_category** — หมวดหมู่ตามมาตรฐาน Meta
- **sale_price** / **sale_price_effective_date** — ราคาโปรโมชั่นและช่วงเวลาลดราคา (ทำให้โฆษณาโชว์ราคาขีดฆ่า + ราคาลดอัตโนมัติ)
- **additional_image_link** — ลิงก์ภาพเพิ่มเติม (สูงสุด 10 ภาพ) สำหรับ Carousel/Collection format
- **item_group_id** — ใช้จับกลุ่มสินค้าที่เป็น Variant กัน (เช่น เสื้อตัวเดียวกันแต่ต่างสี/ไซซ์) ให้ Meta รวมเป็นสินค้าเดียวในโฆษณาแล้วให้ลูกค้าเลือก Variant เอง
- **color, size, pattern, material** — สำหรับสินค้าแฟชั่นที่มี Variant ใช้คู่กับ item_group_id
- **shipping** / **shipping_weight** — ข้อมูลค่าส่งถ้าต้องการโชว์ในบางฟอร์แมต
- **custom_label_0** ถึง **custom_label_4** — Field อิสระที่คุณกำหนดเองได้ ใช้สำหรับสร้าง Product Sets แบบละเอียด (เช่น custom_label_0 = "Best Seller", custom_label_1 = "Margin สูง")

### ตัวอย่างแถว Feed แบบ CSV (Header + 1 แถวตัวอย่าง)

```
id,title,description,availability,condition,price,link,image_link,brand,google_product_category,item_group_id
SKU-00123,Nike Air Max 270 สีขาว/ดำ Size 42,รองเท้าผ้าใบ Nike Air Max 270 เบาสบาย ระบายอากาศดี,in stock,new,3290.00 THB,https://yourshop.com/products/nike-airmax-270-white-42,https://yourshop.com/images/airmax270-white-42.jpg,Nike,Apparel & Accessories > Shoes,GROUP-AIRMAX270-WHITE
```

### ข้อผิดพลาดที่พบบ่อยเรื่อง Field

- ใส่ราคาไม่มีสกุลเงิน หรือใส่ผิดรูปแบบ (เช่น `3,290 บาท` ที่ระบบอ่านไม่ได้) — ต้องเป็น `3290.00 THB`
- ลิงก์ `link` พาไปหน้าแรกเว็บไซต์แทนหน้าสินค้าจริง ทำให้คนคลิกแอดแล้วหาสินค้าที่เห็นในโฆษณาไม่เจอ (Bounce Rate สูง)
- `image_link` เป็นลิงก์ที่ต้อง Login ก่อนดู หรือเป็นภาพที่ขนาดเล็กเกินไป (ต่ำกว่า 500x500 px) ทำให้ภาพถูกปฏิเสธหรือดูไม่ชัดในโฆษณา
- id เปลี่ยนไปเปลี่ยนมาทุกครั้งที่ Sync Feed ใหม่ (เช่น ใช้ Timestamp เป็นส่วนหนึ่งของ id) ทำให้ระบบมองว่าเป็นสินค้าใหม่ตลอด สูญเสีย Performance History ของสินค้านั้น

### กรณีธุรกิจขายหลายสกุลเงิน/หลายประเทศ

ถ้าธุรกิจของคุณขายทั้งในไทยและต่างประเทศ (เช่น ขายผ่าน Shopee ในไทยและมี Order จากลูกค้าสิงคโปร์ผ่านเว็บไซต์ตัวเอง) มีวิธีจัดการ Feed 2 แบบ:

1. **Multi-currency Feed** — ใน Feed เดียวสามารถใส่ Field เพิ่มชื่อ `sale_price` ตามแต่ละตลาด หรือใช้ Field `price [XX]` ที่ระบุสกุลเงินเฉพาะประเทศได้ในบางกรณี แต่วิธีนี้ซับซ้อนและ Meta แนะนำให้ใช้วิธีที่ 2 มากกว่าสำหรับธุรกิจส่วนใหญ่
2. **Catalog แยกต่อประเทศ/สกุลเงิน** — สร้าง Catalog แยก 1 อันต่อ 1 สกุลเงิน/ตลาด แล้วเชื่อม Ad Account ที่มีสกุลเงินตรงกันเข้ากับ Catalog แต่ละอัน วิธีนี้จัดการง่ายกว่าและลดความเสี่ยง Price Mismatch แนะนำสำหรับธุรกิจ SME ส่วนใหญ่ที่ขายไม่เกิน 2-3 ประเทศ

### การจัดการ Variant สินค้า (Item Group) แบบละเอียด

เมื่อสินค้า 1 ตัวมีหลาย Variant (สี, ไซซ์) มี 2 แนวทางออกแบบ Feed:

- **แนวทาง A: แยกทุก Variant เป็น 1 แถว** — เสื้อสีแดง Size S, สีแดง Size M, สีน้ำเงิน Size S ฯลฯ แต่ละอันมี `id` ของตัวเอง และผูกด้วย `item_group_id` เดียวกัน (เช่น `GROUP-TSHIRT-001`) วิธีนี้ทำให้ Meta รวมเป็นการ์ดสินค้าเดียวในโฆษณาที่ให้ลูกค้าเลือก Variant เองได้ (คล้ายเลือก Option บนเว็บอีคอมเมิร์ซ) เป็นวิธีที่แนะนำสำหรับสินค้าแฟชั่น
- **แนวทาง B: 1 สินค้า 1 แถว ไม่แยก Variant** — เหมาะกับสินค้าที่ไม่มี Option ซับซ้อน หรือธุรกิจที่ยังไม่พร้อมจัดการ Feed ละเอียด แต่จะเสียโอกาส Personalization ระดับ Variant ไป (เช่น คนดูสีแดงแต่โฆษณาโชว์สีน้ำเงินให้)

### Feed สำหรับดิจิทัลโปรดักต์และคอร์สออนไลน์

สำหรับธุรกิจที่ขายคอร์สออนไลน์หลายคอร์ส (เช่น แพลตฟอร์มขายคอร์ส 40 คอร์ส) การทำ Catalog ก็ใช้หลักการเดียวกันทุกประการ เพียงแต่:
- `availability` มักตั้งเป็น `in stock` ตลอด (ไม่มีสต็อกหมด ยกเว้นกรณีเปิดรับจำนวนจำกัด)
- `condition` ตั้งเป็น `new` เสมอ
- `google_product_category` เลือกหมวดที่ใกล้เคียงที่สุด เช่น "Media > Education"
- `image_link` ใช้ภาพ Thumbnail/Cover ของคอร์ส
เคสนี้เหมาะมากกับการทำ Retargeting Dynamic Ads ให้คนที่ดูหน้าคอร์สแต่ไม่ได้ลงทะเบียน เพราะแต่ละคนสนใจคอร์สคนละตัว การยิงโฆษณาที่ตรงกับคอร์สที่เขาดูจริงจะ Convert ดีกว่ายิงภาพรวมคอร์สทั้งหมด

---

## Step 264: การอัปโหลดและอัปเดต Feed แบบอัตโนมัติ

### วิธี Upload Feed เข้า Catalog มี 3 แบบหลัก

**แบบที่ 1: Upload ไฟล์ครั้งเดียว (One-time Upload)**
ไปที่ Catalog > Data Sources > "Add Items" > "Use Data Feed" > เลือก "Upload Once" > เลือกไฟล์ CSV/XML จากคอมพิวเตอร์ — เหมาะกับการทดสอบครั้งแรก หรือ Catalog ที่มีสินค้าไม่เปลี่ยนบ่อย แต่ **ไม่แนะนำ** สำหรับร้านที่สต็อก/ราคาเปลี่ยนบ่อย เพราะต้อง Upload มือทุกครั้ง

**แบบที่ 2: Scheduled Fetch (ดึงไฟล์อัตโนมัติตามรอบเวลา)**
วิธีที่ใช้บ่อยที่สุดสำหรับร้านทั่วไป:
1. Catalog > Data Sources > "Add Items" > "Use Data Feed" > "Set a Schedule"
2. ใส่ **URL ของไฟล์ Feed** ที่ Host อยู่บนเซิร์ฟเวอร์ของคุณ (ต้องเป็น URL แบบ Public เข้าถึงได้ตลอดเวลา)
3. เลือกความถี่ในการดึงไฟล์: ทุก **1 ชั่วโมง / 12 ชั่วโมง / รายวัน / รายสัปดาห์** — สำหรับร้านที่สต็อก/ราคาเปลี่ยนบ่อย แนะนำตั้งเป็นทุก 1-3 ชั่วโมง
4. ตั้งเวลาที่ต้องการให้ระบบดึงไฟล์ (เช่น ทุกวันตี 3 เพื่อไม่ชนช่วง Traffic สูง)
5. ระบบจะแจ้งเตือนทาง Email หากดึงไฟล์ไม่สำเร็จ (เช่น URL เสีย, format ผิด)

**แบบที่ 3: Google Sheets**
1. สร้าง Google Sheet ที่มี Column ตรงตาม Required/Recommended Fields
2. ไปที่ File > Share > เปลี่ยนสิทธิ์เป็น "Anyone with the link" + "Viewer"
3. Copy ลิงก์ Google Sheet มาใส่ในช่อง Feed URL ตอนสร้าง Data Source
4. ตั้ง Schedule เหมือนแบบที่ 2 — Meta จะอ่านค่าจาก Sheet ตามรอบเวลาที่ตั้ง

**แบบที่ 4: Partner Platform Integration (แนะนำที่สุดถ้าใช้ Shopify/WooCommerce)**
- **Shopify**: ติดตั้ง App "Facebook & Instagram" จาก Shopify App Store > เชื่อมกับ Business Manager > เลือก Catalog ปลายทาง > ระบบจะ Sync สินค้า สต็อก ราคาแบบ Real-time อัตโนมัติ ไม่ต้องทำ Feed มือเลย
- **WooCommerce**: ติดตั้ง Plugin "Facebook for WooCommerce" > ตั้งค่าเชื่อม Pixel และ Catalog ในหน้า Plugin Settings > Sync อัตโนมัติเมื่อมีการเปลี่ยนแปลงสินค้า

### API (สำหรับทีมที่มี Developer)

ใช้ **Meta Marketing API > Product Catalog Endpoint** ส่งข้อมูลสินค้าเข้า Catalog แบบ Batch ผ่าน HTTP Request วิธีนี้เหมาะกับระบบที่มีการเปลี่ยนแปลงสต็อกทุกวินาที เช่น Flash Sale หรือ Marketplace ขนาดใหญ่ ข้อดีคือ Real-time สูงสุด อัปเดตได้ทันทีที่มีการเปลี่ยนแปลงโดยไม่ต้องรอรอบ Fetch

### การตรวจสอบสถานะ Feed หลัง Upload

หลัง Feed ถูกดึงเข้า Catalog ให้ไปที่ Catalog > Data Sources > เลือก Feed นั้น > ดูแท็บ **"Overview"** จะเห็น:
- จำนวนสินค้าทั้งหมด (Total Items)
- จำนวนสินค้าที่ Active (พร้อมใช้ยิงแอด)
- จำนวนสินค้าที่มี **Error** หรือ **Warning** — คลิกดูรายละเอียดได้ว่า Field ไหนผิด แถวไหนมีปัญหา

### ข้อผิดพลาดที่พบบ่อย

- ตั้ง Schedule ดึงไฟล์ถี่เกินไปโดยไม่จำเป็น (เช่น ทุก 15 นาที) ทำให้เซิร์ฟเวอร์ที่ Host ไฟล์ Feed โหลดหนักเกินไปจนล่ม
- ไม่มีระบบแจ้งเตือนเมื่อ Feed ดึงไม่สำเร็จ ทำให้สินค้าใน Catalog "ค้าง" ข้อมูลเก่าเป็นสัปดาห์โดยไม่รู้ตัว (ราคาผิด สต็อกผิด) — ควรเช็ค Feed Health ทุกสัปดาห์เป็นอย่างน้อย
- ใช้ App Sync จาก Shopify/WooCommerce ควบคู่กับการ Upload Feed มือ ทำให้ข้อมูลชนกันและ Overwrite กันเอง ต้องเลือกวิธีเดียวเป็นหลัก

---

## Step 265: เชื่อม Pixel/Conversions API กับ Catalog เพื่อความแม่นยำ

### ทำไม Pixel ต้องเชื่อมกับ Catalog

Dynamic Ads ทำงานโดยอาศัย **Signal จาก Pixel/CAPI** เพื่อรู้ว่าใครดูสินค้าตัวไหน ใครเพิ่มสินค้าตัวไหนลงตะกร้า ใครซื้อสินค้าตัวไหนไปแล้ว — ข้อมูลนี้จะถูกจับคู่กับ `id` ของสินค้าใน Catalog ผ่าน Parameter ที่เรียกว่า **content_id**

### Event ที่ต้องยิงพร้อม content_id (ทบทวนจาก Part 013-015 แต่สำคัญมากในบริบทนี้)

- **ViewContent** — ต้องยิงพร้อม `content_ids: ['SKU-00123']` ทุกครั้งที่คนเปิดหน้าสินค้า
- **AddToCart** — ต้องยิงพร้อม `content_ids` และ `value`/`currency` ของสินค้าที่ถูกเพิ่ม
- **InitiateCheckout** — ยิงพร้อม `content_ids` ของสินค้าทั้งหมดในตะกร้าตอนกด Checkout
- **Purchase** — ยิงพร้อม `content_ids` ของสินค้าที่ซื้อจริง พร้อม `value` ยอดรวม

**กฎเหล็ก:** ค่า `content_ids` ที่ Pixel ยิงออกมา **ต้องตรงกับค่า `id` ใน Feed เป๊ะๆ** ทุกตัวอักษร (Case-sensitive) ถ้า Pixel ยิง `content_ids: ['sku-00123']` (ตัวพิมพ์เล็ก) แต่ Feed ใส่ `id: SKU-00123` (ตัวพิมพ์ใหญ่) ระบบจะจับคู่ไม่ได้ Dynamic Ads จะไม่โชว์สินค้านั้นให้คนที่เคยดู

### วิธีตรวจสอบว่า content_id ตรงกันหรือไม่

1. เปิดหน้าสินค้าจริงบนเว็บไซต์ ใช้ Extension **Meta Pixel Helper** เช็คว่า Event `ViewContent` ยิงออกมาพร้อมค่า `content_ids` เป็นอะไร
2. เปิด Catalog > Data Sources > ค้นหาสินค้าตัวเดียวกันด้วยชื่อ ดูค่า `id` ในแถวนั้น
3. เทียบค่าทั้งสองตัวว่าตรงกันทุกตัวอักษรหรือไม่

### เชื่อม Dataset เข้า Catalog

ไปที่ Commerce Manager > เลือก Catalog > Settings > **"Dataset"** (บางบัญชีเรียก "Tracking") > เลือก Pixel/Dataset ที่ต้องการเชื่อม โดยปกติควรเป็น Pixel เดียวกับที่ Ad Account ใช้ยิงแคมเปญ Conversion ทั้งหมด เพื่อให้ Machine Learning ใช้ข้อมูล Signal ร่วมกันแทนที่จะแยกกันคนละ Pixel ซึ่งจะทำให้ Learning Phase ช้าลง

### Event Match Quality กับ Dynamic Ads

ทบทวนจาก Part 013 — คุณภาพของ Event Match (ชื่อ อีเมล เบอร์โทรที่ Pixel/CAPI ส่งมา) มีผลต่อความแม่นยำของ Dynamic Ads ด้วย เพราะยิ่ง Match Quality สูง ระบบยิ่งระบุตัวผู้ใช้ได้แม่นยำ ทำให้ Dynamic Retargeting เจาะกลับไปหาคนที่เคยดูสินค้าได้ตรงตัวมากขึ้น แนะนำให้ตั้งค่า Conversions API ควบคู่กับ Browser Pixel เสมอ (โดยเฉพาะหลัง iOS14) ไม่ใช้ Pixel อย่างเดียว

### ข้อผิดพลาดที่พบบ่อย

- ลืมส่ง `content_type` (ต้องเป็น `product` สำหรับ Catalog ทั่วไป) ทำให้ Meta ตีความ Event ผิดประเภท
- เชื่อม Pixel ผิดตัวเข้า Catalog (เช่น Business มี Pixel 3 ตัวจากการทดลองในอดีต เชื่อมตัวที่ไม่ได้ใช้งานจริง)
- ทำ Feed และ Pixel จากทีมคนละทีม (ทีม Dev ทำ Pixel, ทีม Marketing ทำ Feed) โดยไม่คุยกันเรื่อง Naming Convention ของ id ทำให้ content_id ไม่ตรงกันตั้งแต่แรก

---

## Step 266: สร้างแคมเปญ Dynamic Ads (Catalog Sales) แบบ Step-by-Step

เมื่อ Catalog พร้อม, Feed พร้อม, Pixel เชื่อมเรียบร้อยแล้ว ถึงเวลาสร้างแคมเปญจริงใน Ads Manager

### ขั้นตอนสร้างแคมเปญ

1. Ads Manager > **+ Create**
2. เลือก Objective: **Sales** (จะเป็น Sales objective เหมือน Part 026 แต่มี Setting เพิ่มเรื่อง Catalog)
3. ตั้งชื่อแคมเปญตาม Naming Convention เช่น `SALES-DynamicRT-Catalog-ViewedNotPurchased-Sep2026`
4. ที่ Campaign Level เลือก **"Catalog"** — ตรงนี้สำคัญมาก ต้องเลือก Catalog ที่สร้างไว้ใน Step 262 ก่อนไปขั้นตอนถัดไป (ถ้าไม่เลือกตรงนี้ ระบบจะไม่ให้เข้าโหมด Dynamic Ads)
5. เลือก **Campaign Budget Optimization (CBO)** หรือปล่อยงบไว้ที่ Ad Set ตามกลยุทธ์ (ทบทวน Part 018)

### Ad Set Level — จุดที่ Dynamic Ads ต่างจากแคมเปญทั่วไป

1. **Catalog** — ระบบจะดึง Catalog ที่เลือกจาก Campaign มาอัตโนมัติ
2. **Product Set** — เลือกกลุ่มสินค้าที่จะใช้ในแคมเปญนี้ (ถ้ายังไม่แบ่ง Product Set จะมีค่า Default เป็น "All Products" — แนะนำให้แบ่ง Product Set ก่อนเสมอ ดู Step 268)
3. **Audience** — ตรงนี้คือหัวใจของ Dynamic Ads เลือกได้ 2 แนวทางหลัก:
   - **Retargeting: "People who interacted with your products"** — เลือก Event ได้ว่าจะเจาะ Viewed, Added to Cart, หรือ Purchased ในกรอบเวลาเท่าไหร่ (1, 7, 14, 30 วัน) — ใช้สำหรับ Dynamic Retargeting (Step 269)
   - **Advantage+ Audience / Broad Audience** — ให้ระบบหา Audience ใหม่เองจาก Signal ของ Catalog ทั้งหมด — ใช้สำหรับ Dynamic Prospecting (Step 269)
4. **Exclude** — ตั้ง Exclude คนที่ซื้อไปแล้วออกจาก Audience ถ้าเป้าหมายคือ Retarget คนที่ยังไม่ซื้อ (สำคัญมาก ไม่งั้นจะยิงซ้ำใส่คนที่ซื้อไปแล้ว)
5. **Placements** — แนะนำเริ่มที่ Advantage+ Placements (Automatic) ก่อน เพราะ Dynamic Ads ทำงานได้ดีในทุก Placement รวมถึง Feed, Reels, Stories, Marketplace
6. **Optimization & Delivery** — เลือก Conversion Event เป็น **Purchase** (สำหรับ Bottom of Funnel) หรือ **AddToCart** (ถ้างบน้อย/Purchase Volume ยังต่ำ ต้องการให้ระบบเรียนรู้เร็วขึ้น)

### Ad Level — ตั้งครีเอทีฟ Dynamic

1. เลือก Format: **Carousel** (แนะนำ เพราะโชว์ได้หลายสินค้าในโฆษณาเดียว) หรือ **Single Image/Video Dynamic** (โชว์สินค้าเดียวต่อคน)
2. อัปโหลด **Template** — ระบบให้แนบ Primary Text, Headline, Description แบบ Dynamic ที่ดึงชื่อสินค้า/ราคาสินค้ามาแทรกอัตโนมัติผ่าน **Macro** เช่น `{{product.name}}`, `{{product.price}}`, `{{product.sale_price}}`
3. ตัวอย่าง Headline แบบ Dynamic: `{{product.name}} ลดเหลือ {{product.sale_price}}` — ระบบจะแทนที่ Macro นี้ด้วยชื่อและราคาจริงของสินค้าที่แสดงให้แต่ละคน
4. เพิ่ม Overlay เช่น Badge "ลดราคา" หรือ "สินค้าที่คุณเพิ่งดู" (Dynamic Ads บางฟอร์แมตรองรับ Text Overlay อัตโนมัติบนภาพสินค้า)
5. ตั้ง Call-to-Action button: "Shop Now", "Buy Now", "Learn More"
6. Destination: ลิงก์จะดึงจาก Field `link` ในสินค้านั้นๆ อัตโนมัติ ไม่ต้องกรอกมือ

### Preview ก่อนเผยแพร่

ใช้ปุ่ม **"Preview"** ที่ Ads Manager จะโชว์ตัวอย่างว่าถ้าดึงสินค้า 3-5 ตัวจาก Catalog มาใส่ในเทมเพลตนี้จะหน้าตาเป็นอย่างไร ให้เช็คว่าชื่อสินค้ายาวเกินจนตัดคำ, ราคาแสดงถูกสกุลเงินหรือไม่, ภาพสินค้าคมชัดหรือไม่

### ข้อผิดพลาดที่พบบ่อย

- เลือก Catalog แต่ลืมเลือก Product Set เจาะจง ปล่อยเป็น "All Products" ทำให้สินค้าที่ Margin ต่ำหรือ Out of Stock บ่อยถูกโฆษณาด้วย
- ไม่ตั้ง Exclude คนที่ซื้อแล้ว ทำให้เสียงบยิงซ้ำใส่ลูกค้าเก่าที่ไม่มีโอกาสซื้อซ้ำในกรอบเวลาสั้น
- ใส่ Primary Text ที่เป็น Static ทั้งหมดโดยไม่ใช้ Macro เลย ทำให้เสียจุดเด่นของ Personalization ไปครึ่งหนึ่ง

### อ่านผลลัพธ์ Dynamic Ads แบบแยกตามสินค้า (Breakdown)

หลังแคมเปญรันไปสักระยะ สิ่งที่มือใหม่มักมองข้ามคือการดู Performance แยกตามสินค้ารายตัว ไม่ใช่ดูแค่ตัวเลขรวมของ Ad Set วิธีดู:

1. เปิด Ads Manager > เลือกแคมเปญ Dynamic Ads > ที่ตาราง Performance คลิก **"Breakdown"** > เลือก **"By Delivery" > "Product ID"** (หรือในบางเวอร์ชันไปที่ Catalog > Reporting โดยตรง)
2. จะเห็นตารางแยกว่าสินค้าตัวไหนถูกแสดงบ่อย มี CTR เท่าไหร่ มี Purchase กี่ครั้ง ROAS เท่าไหร่
3. ใช้ข้อมูลนี้ปรับ Product Set — สินค้าที่ CTR สูงแต่ Purchase ต่ำอาจมีปัญหาที่หน้า Landing Page ไม่ใช่ปัญหาที่โฆษณา ส่วนสินค้าที่แสดงน้อยมากอาจติด Error ใน Feed หรือราคาสูงเกินกลุ่มเป้าหมาย
4. สินค้าที่ Performance แย่ต่อเนื่องเกิน 2 สัปดาห์ ควรย้ายออกจาก Product Set หลักไปไว้ Product Set แยกเพื่อไม่ให้ดึง Performance เฉลี่ยของทั้งกลุ่มลง

---

## Step 267: Advantage+ Catalog Ads เบื้องต้น

### คืออะไร

**Advantage+ Catalog Ads** (บางเอกสารเรียกรวมอยู่ใน Advantage+ Shopping/Sales umbrella) คือเวอร์ชันที่ Meta ใช้ AI จัดการ Automation ให้มากขึ้นในขั้นตอนสร้าง Dynamic Ads เมื่อเทียบกับ Manual Dynamic Ads ใน Step 266 — ระบบจะช่วยแนะนำ:

- **Audience Expansion อัตโนมัติ** — ไม่ต้องเลือก Retargeting Window เองทั้งหมด ระบบจะขยาย/หด Audience ตาม Signal ที่ดีที่สุด
- **Format และ Placement อัตโนมัติ** — ทดสอบและเลือก Format ที่ Convert ดีที่สุดให้อัตโนมัติในทุก Placement
- **Creative Enhancement อัตโนมัติ** — ปรับ Crop ภาพ, เพิ่ม Overlay, ปรับ Text ให้เหมาะกับแต่ละ Placement โดยไม่ต้องสร้างเวอร์ชันเองทุกขนาด

### ความสัมพันธ์กับ ASC (Part 029)

Advantage+ Catalog Ads กับ Advantage+ Shopping Campaigns (ASC) เกี่ยวข้องกันเพราะทั้งคู่ใช้ Catalog เป็นฐาน แต่ ASC คือ "แคมเปญทั้งแคมเปญ" ที่ออกแบบมาสำหรับ E-commerce โดยเฉพาะและให้ AI ควบคุมเกือบทุกอย่าง (จะเจาะลึกเต็ม Part ใน Part 029) ส่วน Advantage+ Catalog Ads ที่พูดถึงใน Step นี้คือ Feature/Setting ระดับ Ad Set ที่คุณเปิดใช้ได้ภายในแคมเปญ Dynamic Ads ปกติที่สร้างใน Step 266 ด้วย

### วิธีเปิดใช้

ตอนสร้าง Ad Set ในแคมเปญ Catalog Sales จะมีตัวเลือก **"Advantage+ creative"** และ **"Advantage+ audience"** ที่เปิด/ปิดเป็น Toggle:
- เปิด Advantage+ Creative → ให้ระบบปรับแต่งครีเอทีฟอัตโนมัติในแต่ละ Placement
- เปิด Advantage+ Audience → ให้ระบบขยาย Audience นอกเหนือจากที่คุณกำหนดเมื่อระบบเห็นสัญญาณว่าจะได้ผลลัพธ์ดีขึ้น (คล้ายกับ Advantage Detailed Targeting ที่เรียนใน Part 017)

### เมื่อไหร่ควรใช้ Manual เมื่อไหร่ควรใช้ Advantage+

| สถานการณ์ | แนะนำ |
|---|---|
| เพิ่งเริ่มทำ Dynamic Ads ครั้งแรก ยังไม่มีข้อมูล | เริ่มด้วย Manual Setting ควบคุมทุกอย่างเพื่อเข้าใจพฤติกรรมระบบก่อน |
| มีข้อมูล Conversion สม่ำเสมอแล้ว (Pixel มี Purchase Event มากกว่า 50 ครั้ง/สัปดาห์) | เปิด Advantage+ Audience เพื่อให้ระบบหา Incremental Reach เพิ่ม |
| มี Creative หลากหลาย Format พร้อมอยู่แล้ว (Square, Vertical, Landscape) | เปิด Advantage+ Creative เพื่อลดงาน Manual Crop |
| ต้องการควบคุม Brand Safety สูง (ธุรกิจที่มีข้อจำกัดด้าน Content) | ปิด Advantage+ Audience ไว้ก่อน ควบคุม Audience มือ |

### ข้อผิดพลาดที่พบบ่อย

- เปิด Advantage+ ทุกตัวทันทีตั้งแต่วันแรกโดยไม่มี Baseline การเปรียบเทียบ ทำให้ไม่รู้ว่า Performance ที่เปลี่ยนไปมาจาก Automation หรือจากปัจจัยอื่น
- เข้าใจผิดว่า Advantage+ Catalog Ads คือแคมเปญแยก ทั้งที่จริงเป็นแค่ Setting ในแคมเปญ Dynamic Ads ปกติ

---

## Step 268: Product Sets — แบ่งกลุ่มสินค้าสำหรับ Cross-sell/Upsell/Retargeting

### Product Set คืออะไร

Product Set คือการแบ่งสินค้าใน Catalog ออกเป็นกลุ่มย่อยตามเงื่อนไขที่คุณกำหนด เพื่อให้ Dynamic Ads แต่ละแคมเปญโฆษณาเฉพาะกลุ่มสินค้าที่ตรงเป้าหมาย ไม่ใช่โฆษณาสินค้าทั้งหมดปนกันไปหมด

### วิธีสร้าง Product Set

1. Commerce Manager > Catalog > เมนู **"Product Sets"** > **"Create Set"**
2. เลือกตั้งเงื่อนไข (Rules) โดยใช้ Field ต่างๆ ใน Feed เป็นตัวกรอง เช่น:
   - `price` less than 1000
   - `brand` equals "Nike"
   - `google_product_category` contains "Shoes"
   - `custom_label_0` equals "Best Seller"
   - `availability` equals "in stock"
3. ตั้งชื่อ Product Set ให้สื่อความหมาย เช่น `Best-Seller-Under-1000` หรือ `Cross-sell-Accessories`
4. บันทึก — ระบบจะแสดงจำนวนสินค้าที่เข้าเงื่อนไข ให้ตรวจสอบว่าตรงกับที่คาดไว้

### รูปแบบการใช้ Product Set ที่ใช้บ่อยที่สุด

1. **Retargeting Set** — เช่น Product Set = สินค้าทั้งหมด แต่ Audience กำหนดเป็น "คนที่ดูสินค้านี้แล้วไม่ซื้อ" → ระบบจะโชว์สินค้าตัวเดียวกันที่คนนั้นดู
2. **Cross-sell Set** — เช่น คนที่ซื้อ "กล้อง" ไปแล้ว ให้ Product Set โชว์ "เลนส์ กระเป๋ากล้อง ขาตั้งกล้อง" (ใช้ Field `custom_label` กำหนดว่าสินค้าตัวไหนคือ Accessory ของหมวดกล้อง) — ตั้ง Audience เป็น "Purchased Camera Category" แล้วให้ Ad Set นี้โชว์ Product Set = Camera Accessories
3. **Upsell Set** — เช่น คนที่ดูสินค้าราคาถูกในหมวดหนึ่ง ให้โชว์สินค้ารุ่นสูงกว่าในหมวดเดียวกัน (Bundle/Premium Version) กรองด้วย `price` range และ `google_product_category` เดียวกัน
4. **Best Seller Set สำหรับ Prospecting** — ใช้ custom_label_0 = "Best Seller" ทำ Product Set เฉพาะสินค้าขายดี 20-30 ตัว เพื่อยิง Dynamic Prospecting ให้คนที่ยังไม่รู้จักร้านเห็นแต่สินค้าที่มี Conversion Rate สูงสุด ไม่ปนกับสินค้าที่ยังไม่มีข้อมูลพิสูจน์ตัว
5. **Margin สูง Set** — ใช้ custom_label_1 = "High Margin" เพื่อเน้นยิงสินค้าที่ได้กำไรต่อชิ้นสูง แทนที่จะให้ระบบเลือกสินค้าที่ Convert ง่ายแต่ Margin บาง

### เทคนิคการตั้ง Custom Label ให้ใช้งานได้จริง

แนะนำให้วางแผน Custom Label ตั้งแต่ตอนทำ Feed ไม่ใช่มาไล่แก้ตอนหลัง เช่น:
- `custom_label_0`: สถานะยอดขาย (Best Seller / Regular / Slow Moving)
- `custom_label_1`: ระดับ Margin (High / Medium / Low)
- `custom_label_2`: ฤดูกาล/แคมเปญ (Summer / New Arrival / Clearance)
- `custom_label_3`: กลุ่มเป้าหมาย (Men / Women / Unisex / Kids)
- `custom_label_4`: สำรองไว้สำหรับ Test/Campaign เฉพาะกิจ

### ข้อผิดพลาดที่พบบ่อย

- สร้าง Product Set แบบ Static (เลือกสินค้าทีละตัวด้วยมือ) แทนการตั้งเป็น Rule-based ทำให้เมื่อ Feed อัปเดต สินค้าใหม่ที่เข้าเงื่อนไขไม่ถูกเพิ่มเข้า Set อัตโนมัติ
- ตั้งเงื่อนไข Product Set แคบเกินไปจนเหลือสินค้าไม่กี่ตัว (ต่ำกว่า 10 SKU) ทำให้ Dynamic Ads ไม่มีตัวเลือกพอที่จะ Optimize
- ไม่อัปเดต Custom Label เมื่อสถานะสินค้าเปลี่ยน (เช่น สินค้าเลิกเป็น Best Seller แล้วแต่ยัง Label ค้างอยู่) ทำให้ Product Set ผิดเป้าหมายในระยะยาว

### การทดสอบ Product Set แบบ A/B

เทคนิคที่มืออาชีพใช้บ่อยคือสร้าง Ad Set สองตัวที่ Audience เหมือนกันทุกอย่าง แต่สลับ Product Set กัน เช่น Ad Set A ใช้ Product Set "Best Seller เท่านั้น" ส่วน Ad Set B ใช้ Product Set "All Products" แล้วเทียบ CPA/ROAS หลังรัน 7-10 วัน วิธีนี้จะบอกได้ชัดว่าการโฟกัสสินค้าขายดีช่วยประหยัดงบจริงหรือไม่ หรือบางธุรกิจอาจพบว่าเปิดกว้างทุกสินค้ากลับได้ผลดีกว่าเพราะ Long-tail สินค้าเฉพาะกลุ่มมี Conversion Rate สูงในกลุ่มคนที่สนใจเฉพาะเจาะจงมากกว่าที่คาดไว้

### Seasonal Product Set

สำหรับธุรกิจที่มีสินค้าตามฤดูกาลหรือแคมเปญพิเศษ เช่น 11.11, 12.12, สงกรานต์ แนะนำสร้าง Product Set ชั่วคราวไว้ล่วงหน้า เช่น `Songkran-Promo-2027` ที่กรองด้วย `custom_label_2 = "Songkran"` แล้วตั้งเวลาผ่าน Automated Rules (ทบทวน Part 063) ให้ปิด Ad Set ที่ใช้ Product Set นี้อัตโนมัติเมื่อแคมเปญจบ ป้องกันการยิงโปรที่หมดอายุไปแล้วต่อเนื่องโดยไม่มีใครสังเกต

---

## Step 269: Dynamic Ads Retargeting Funnel และ Dynamic Prospecting

### Funnel มาตรฐานของ Dynamic Ads

Dynamic Ads ทำงานได้ดีที่สุดเมื่อวางเป็น Funnel ต่อเนื่อง 3 ชั้น ไม่ใช่ยิงมั่วรวมกันเป็นแคมเปญเดียว:

**ชั้นที่ 1 — Viewed but Not Added to Cart (Window 1-3 วัน)**
- Audience: คนที่ยิง ViewContent แต่ไม่มี AddToCart ในกรอบ 1-3 วันหลังสุด
- Exclude: คนที่ Purchase แล้วในกรอบ 180 วัน
- เป้าหมาย: ดึงกลับมาให้สนใจสินค้าอีกครั้งเร็วที่สุด เพราะ Intent ยังสูงอยู่ ควรยิงด้วย Budget ที่เข้มข้นและ Frequency ที่พอเหมาะ (ไม่ต้อง Cap ต่ำเกินไปในช่วงนี้)
- Message: เน้นเตือนความจำ ("ยังอยู่ในใจเราไหม?") ไม่ต้องลดราคาแรง

**ชั้นที่ 2 — Added to Cart but Not Purchased (Window 3-7 วัน)**
- Audience: คนที่ยิง AddToCart แต่ไม่มี Purchase ในกรอบ 3-7 วัน
- Exclude: Purchased 180 วัน
- เป้าหมาย: กลุ่มนี้มี Intent สูงสุด (เกือบซื้อแล้ว) ควรใส่ Message ที่กระตุ้นการตัดสินใจ เช่น "สินค้าใกล้หมด", Free Shipping, Coupon Code เฉพาะกลุ่มนี้
- แนะนำแยก Ad Set นี้ออกจากชั้นที่ 1 เพื่อคุม Budget/Bid ต่างกันได้ (Bid สูงกว่าได้เพราะ Value ต่อ Conversion สูงกว่า)

**ชั้นที่ 3 — Purchased (Cross-sell/Upsell, Window 7-30 วัน)**
- Audience: คนที่ Purchase แล้วในกรอบ 7-30 วันที่ผ่านมา
- Product Set: ใช้ Cross-sell Set (สินค้าเสริมของสิ่งที่ซื้อไปแล้ว) ไม่ใช่สินค้าตัวเดียวกันที่ซื้อแล้ว
- เป้าหมาย: เพิ่ม Customer Lifetime Value ผ่านการซื้อซ้ำ/ซื้อเสริม

### Dynamic Prospecting (Broad Audience Dynamic Ads)

นอกจาก Retargeting แล้ว Dynamic Ads ยังใช้หา Customer ใหม่ได้ (Prospecting) โดยไม่ต้องมีคนเคยเข้าเว็บมาก่อน:

- ตั้ง Audience เป็น **"New Customers" / "Advantage+ Audience"** แทนการเลือก Custom Audience
- ระบบจะใช้ Signal จาก Pixel ของคนที่ Purchase ไปแล้วทั้งหมด (Seed Audience) มาหาคนที่มีพฤติกรรมคล้ายกัน แล้วเลือกสินค้าที่น่าจะโดนใจคนนั้นจาก Catalog มาโชว์ — คล้าย Lookalike แต่ Dynamic ในระดับสินค้าด้วย
- ควรใช้ Product Set แบบ **Best Seller** สำหรับ Prospecting เพราะสินค้าที่พิสูจน์แล้วว่าขายดีมีโอกาส Convert กับคนใหม่มากกว่าสินค้าที่ยังไม่มีข้อมูล

### ตารางสรุป Budget Allocation แนะนำสำหรับ Dynamic Ads Funnel (ธุรกิจ E-commerce ทั่วไป)

| ชั้น Funnel | สัดส่วนงบแนะนำ | เป้าหมาย KPI |
|---|---|---|
| Prospecting (Broad Dynamic) | 40-50% | CPA ระดับ Awareness→Consideration, ดู Add to Cart Rate |
| Viewed not Added to Cart | 15-20% | CTR, Cost per Add to Cart |
| Added to Cart not Purchased | 20-25% | ROAS, Cost per Purchase |
| Purchased (Cross-sell) | 10-15% | Repeat Purchase Rate, AOV เพิ่มขึ้น |

(สัดส่วนนี้เป็นจุดเริ่มต้น ต้องปรับตาม Data จริงหลังรันแคมเปญ 2-3 สัปดาห์)

### ข้อผิดพลาดที่พบบ่อย

- รวม 3 ชั้น Funnel ไว้ Ad Set เดียวกัน (Audience กว้างเกินไป) ทำให้ Machine Learning Optimize ไปทางกลุ่มที่ Convert ง่ายที่สุด (มักเป็นกลุ่ม Added to Cart) จนกลุ่ม Prospecting ได้งบน้อยเกินไป ธุรกิจขาดลูกค้าใหม่ในระยะยาว
- ตั้ง Window การ Retarget นานเกินไป (เช่น 30 วันสำหรับสินค้าที่ Impulse Buy) ทำให้ยิงถูกคนที่หมด Intent ไปแล้ว เสียงบเปล่า
- ไม่ Exclude คนที่ Purchase แล้วออกจากทุกชั้น Retargeting ทำให้ยิงซ้ำใส่ลูกค้าเก่าเรื่อยๆ

---

## Step 270: Creative Template, Feed Error ที่พบบ่อย และ Workshop

### Creative Template ที่ใช้ได้ผลจริงกับ Catalog Ads

**Template 1: Carousel มาตรฐาน**
- ภาพสินค้า Crop 1:1 พื้นหลังโล่ง
- Overlay ราคาที่มุมล่างขวา (ถ้า sale_price มี ให้โชว์ราคาขีดฆ่า + ราคาลด)
- Headline ใช้ Macro: `{{product.name}}`
- Primary Text แบบ Static ที่ใช้ได้กับสินค้าทุกตัว เช่น "ยังไม่หมดโปร! คลิกดูสินค้าที่คุณสนใจ 🛒 ส่งฟรีทั่วประเทศ"

**Template 2: Single Dynamic Image พร้อม CTA เร่งด่วน**
- ใช้สำหรับชั้น "Added to Cart not Purchased"
- ใส่ Sticker/Badge "ใกล้หมด" หรือ "ราคานี้วันนี้เท่านั้น" ทับมุมภาพ (ถ้าเป็นความจริง — ห้ามใส่ Fake Urgency ตามหลัก Ethics ใน Part 007)
- Primary Text: "ตะกร้าคุณยังรอคุณอยู่ กดสั่งซื้อตอนนี้รับส่วนลดพิเศษ [CODE]"

**Template 3: Collection Ad (สำหรับ Prospecting)**
- ใช้ Cover Video/Image ที่โชว์ Brand Story สั้นๆ ด้านบน + Grid สินค้า 4 ตัวจาก Best Seller Set ด้านล่าง
- เหมาะกับ Placement Feed/Instant Experience บนมือถือ

### Feed Error ที่พบบ่อยที่สุดและวิธีแก้ (จากประสบการณ์จริงหน้างาน)

| Error ที่เห็นใน Diagnostics | สาเหตุ | วิธีแก้ |
|---|---|---|
| "Image not crawlable" | image_link เข้าถึงไม่ได้ (ต้อง Login, บล็อก Bot, หรือ URL เสีย) | เช็คว่า Server ไม่บล็อก User-agent ของ Facebook Bot (`facebookexternalhit`), ทดสอบเปิดลิงก์ใน Browser แบบ Incognito |
| "Missing required field" | ขาด Field บังคับ เช่น availability หรือ price | เพิ่ม Column ที่ขาดใน Feed แล้ว Re-fetch |
| "Price mismatch" | ราคาใน Feed กับราคาในหน้า Landing Page ไม่ตรงกัน | ต้องแก้ให้ราคาตรงกัน 100% เพราะ Meta ตรวจสอบ Cross-check อัตโนมัติ ถ้าไม่ตรงจะถูก Disapprove |
| "Item out of stock but ads still delivering" | Feed อัปเดต availability ช้ากว่าสต็อกจริง | ลด Fetch Interval ให้ถี่ขึ้น หรือใช้ API แทน Scheduled Fetch |
| "Duplicate ID" | มี id ซ้ำกันในไฟล์ Feed (มักเกิดจาก Merge ไฟล์จากหลายแหล่ง) | ตรวจสอบ Unique Key ก่อน Export ไฟล์ทุกครั้ง |
| "Currency not supported/mismatch" | ตั้งสกุลเงินใน Feed ไม่ตรงกับสกุลเงินของ Ad Account | แก้ Field price ให้ตรงสกุลเงินบัญชี หรือแก้ Currency ของ Ad Account ให้ตรง (ทำได้ยากถ้าบัญชีใช้งานแล้ว ควรแก้ Feed) |
| "Landing page not matching" | link ในสินค้าไม่ได้พาไปหน้าสินค้านั้นโดยตรง (Redirect ไปหน้าอื่น) | ตรวจสอบ URL ทุกตัวว่า Redirect ตรงจุดหรือไม่ โดยเฉพาะหลัง Migrate เว็บไซต์ |

### Case Study: ร้านเสื้อผ้าออนไลน์ "Closet & Co."

ร้าน Closet & Co. ขายเสื้อผ้าแฟชั่นผู้หญิงออนไลน์ มี SKU ทั้งหมด 340 ตัว (รวม Variant สี/ไซซ์) ก่อนใช้ Dynamic Ads ร้านนี้ยิงแอดแบบ Static โดยเลือกสินค้ามาทำครีเอทีฟเองสัปดาห์ละ 15-20 ภาพ ROAS เฉลี่ยอยู่ที่ 1.8

ทีมมีเดียไบเยอร์เข้ามาปรับระบบดังนี้:
1. ทำ Feed ผ่าน Google Sheets เชื่อมกับระบบสต็อกหลังบ้านให้ Sync อัตโนมัติทุก 2 ชั่วโมง ครบ Required Fields ทั้งหมด และเพิ่ม custom_label_0 แบ่ง Best Seller/Regular
2. สร้าง Product Set 4 กลุ่ม: Best Seller, New Arrival, Clearance (ราคาต่ำกว่า 500 บาท), Cross-sell Accessories
3. ตั้ง Dynamic Ads Retargeting Funnel 3 ชั้นตามที่อธิบายใน Step 269 พร้อม Exclude Purchased 180 วันในทุกชั้น
4. ตั้ง Dynamic Prospecting ด้วย Product Set = Best Seller เจาะ Advantage+ Audience

ผลลัพธ์หลังรัน 45 วัน: ROAS เฉลี่ยรวมทั้งพอร์ตขึ้นเป็น 3.4, Cost per Purchase ลดลง 38%, และเวลาที่ทีมกราฟิกต้องใช้ทำครีเอทีฟรายสัปดาห์ลดลงกว่า 70% เพราะไม่ต้องทำภาพสินค้าใหม่ทุกตัวด้วยมือ — ทีมกราฟิกเปลี่ยนไปโฟกัสที่ Static/Video Ads สำหรับ Awareness Campaign แทน ซึ่งทำงานคู่กับ Dynamic Ads ได้ดีขึ้นกว่าเดิม

จุดที่เกือบพลาด: ช่วงสัปดาห์แรก ทีมลืมตั้ง Exclude Purchased ในชั้น Retargeting ทำให้มีลูกค้าเก่าบางคนบ่นว่าโดนยิงแอดสินค้าที่ซื้อไปแล้วซ้ำๆ ต้องแก้ไข Ad Set หลังจากสังเกตเห็น Comment ร้องเรียนใต้โฆษณา

---

## คำถามที่พบบ่อย (FAQ)

**Q: Catalog หนึ่งอันใช้กับ Ad Account ได้กี่บัญชี?**
A: ใช้ได้กับหลาย Ad Account พร้อมกัน ตราบใดที่ Ad Account เหล่านั้นอยู่ใน Business Manager เดียวกันหรือได้รับ Partner Access เข้าถึง Catalog นั้น เหมาะกับเอเจนซี่ที่บริหารหลายบัญชีให้ลูกค้ารายเดียวกัน

**Q: ถ้าสินค้าหมดสต็อกกลางแคมเปญ ต้องปิดแคมเปญเองไหม?**
A: ไม่ต้อง ถ้า Feed อัปเดต `availability` เป็น `out of stock` ถูกต้องและทันเวลา ระบบจะหยุดแสดงสินค้าตัวนั้นในโฆษณาโดยอัตโนมัติ แคมเปญโดยรวมยังรันต่อด้วยสินค้าตัวอื่นที่ยังมีสต็อก

**Q: Dynamic Ads ใช้กับ Instant Experience (เดิมชื่อ Canvas) ได้ไหม?**
A: ได้ สามารถสร้าง Instant Experience ที่ดึงสินค้าจาก Catalog มาแสดงเป็น Grid ภายในหน้า Instant Experience เหมาะกับ Prospecting ที่ต้องการให้คนเลื่อนดูสินค้าหลายตัวแบบ Immersive บนมือถือ

**Q: ทำไม Preview บางครั้งไม่โชว์สินค้าจริง แสดงแต่ Placeholder?**
A: มักเกิดเมื่อ Product Set ที่เลือกมีสินค้าไม่พอ หรือ Feed ยังอยู่ในสถานะ Processing ยังไม่เสร็จ ให้รอ 10-15 นาทีแล้วลองใหม่ หรือตรวจสอบว่า Product Set มีสินค้า Active มากกว่า 1 ตัวจริงหรือไม่

**Q: จำเป็นต้องมี Conversions API ก่อนทำ Dynamic Ads หรือไม่?**
A: ไม่บังคับ แต่แนะนำอย่างยิ่ง เพราะหลัง iOS14+ ข้อมูลจาก Browser Pixel เพียงอย่างเดียวขาดหายไปมากจากการที่ผู้ใช้ปฏิเสธ Tracking บน Safari/iOS การมี CAPI ควบคู่จะทำให้ Signal ที่ใช้จับคู่ content_id สมบูรณ์ขึ้นมาก และ Dynamic Retargeting จะแม่นยำขึ้นตามไปด้วย

---

## Checklist ท้ายบท

- [ ] สร้าง Catalog ใน Commerce Manager และเลือกประเภทธุรกิจถูกต้อง (E-commerce สำหรับสินค้าทั่วไป)
- [ ] Assign Ad Account และ Pixel/Dataset เข้า Catalog เรียบร้อย
- [ ] Domain ที่ใช้ใน Catalog ผ่าน Domain Verification แล้ว
- [ ] Feed มี Required Fields ครบทุกตัว (id, title, description, availability, condition, price, link, image_link, brand)
- [ ] price ใส่หน่วยสกุลเงินถูกต้องและตรงกับ Ad Account Currency
- [ ] image_link เข้าถึงได้แบบ Public และมีความละเอียดอย่างน้อย 500x500 px
- [ ] ตั้ง Schedule Fetch หรือ Partner Integration (Shopify/WooCommerce) ให้ Feed อัปเดตอัตโนมัติสม่ำเสมอ
- [ ] content_id ที่ Pixel ยิงออกมาตรงกับ id ใน Feed ทุกตัวอักษร (เช็คด้วย Meta Pixel Helper)
- [ ] สร้าง Product Set อย่างน้อย 3-4 กลุ่ม (Best Seller, Cross-sell, Clearance, ฯลฯ) แบบ Rule-based ไม่ใช่เลือกมือ
- [ ] สร้าง Dynamic Ads Retargeting Funnel ครบ 3 ชั้น พร้อม Exclude คนที่ Purchase แล้วในทุกชั้น Retargeting
- [ ] ทดสอบ Dynamic Prospecting ด้วย Best Seller Product Set
- [ ] เช็ค Feed Diagnostics ทุกสัปดาห์เพื่อจับ Error ก่อนกระทบ Performance
- [ ] Preview โฆษณาก่อนเผยแพร่เพื่อเช็คว่า Macro แสดงชื่อ/ราคาสินค้าถูกต้อง

---

## Workshop / แบบฝึกหัด

**เป้าหมาย:** สร้าง Catalog และแคมเปญ Dynamic Retargeting 1 ตัวที่ใช้งานได้จริงกับธุรกิจของคุณหรือธุรกิจสมมติ

**ขั้นตอนที่ต้องทำ:**

1. เลือกธุรกิจที่มีสินค้าอย่างน้อย 15-20 SKU (ใช้ธุรกิจจริงของคุณ หรือถ้ายังไม่มีให้สมมติร้านค้าออนไลน์ 1 ร้านพร้อมสินค้า 20 รายการ)
2. เขียน Feed เป็นไฟล์ CSV หรือ Google Sheets ที่มี Required Fields ครบทั้ง 9 ตัว บวก item_group_id และ custom_label_0 อย่างน้อย
3. สร้าง Catalog ใน Commerce Manager ประเภท E-commerce แล้ว Upload/เชื่อม Feed ที่เขียนไว้
4. ตรวจสอบ Diagnostics ว่ามี Error กี่รายการ แก้ไขจนเหลือ 0 Error
5. สร้าง Product Set อย่างน้อย 2 กลุ่ม (เช่น Best Seller และ Under 500 บาท) แบบ Rule-based
6. สร้างแคมเปญ Dynamic Ads โดยตั้ง Audience เป็น "Viewed but not Purchased in 7 days" พร้อม Exclude Purchased 180 วัน
7. เขียน Primary Text และ Headline ที่ใช้ Macro (`{{product.name}}`, `{{product.price}}`) อย่างน้อย 1 ชุด
8. ใช้ปุ่ม Preview เช็คว่าโฆษณาแสดงผลถูกต้องกับสินค้าตัวอย่างอย่างน้อย 3 ตัว
9. บันทึกสิ่งที่คุณเจอ (Error, จุดที่ติดปัญหา, วิธีแก้) เป็นบันทึกส่วนตัว 1 หน้า เพื่อใช้อ้างอิงตอนทำงานจริงกับลูกค้า

---

## สรุปและเชื่อมไปยัง Part ถัดไป

ใน Part นี้คุณได้เรียนรู้ตั้งแต่พื้นฐานของ Catalog และ Dynamic Ads ไปจนถึงการสร้าง Feed ที่ใช้งานได้จริง เชื่อม Pixel ให้แม่นยำ สร้างแคมเปญ Dynamic Ads แบบ Manual และ Advantage+ แบ่ง Product Set สำหรับ Cross-sell/Upsell และวาง Retargeting Funnel 3 ชั้นแบบมืออาชีพ พร้อมรู้จัก Error ที่พบบ่อยและวิธีแก้ไข

ทักษะนี้คือรากฐานสำคัญที่จะพาไปสู่ **Part 029: Advantage+ Shopping Campaigns (ASC) เจาะลึก** ซึ่งจะขยายแนวคิดเรื่อง Catalog ให้กลายเป็นแคมเปญที่ AI ควบคุมแบบเต็มรูปแบบ แต่ก่อนจะไปถึงจุดนั้น **Part 028: สร้างแคมเปญ App Promotion** จะพาคุณออกนอกเส้นทาง E-commerce ชั่วคราวไปเรียนรู้การโปรโมทแอปมือถือ ซึ่งมีตรรกะ Objective และการวัดผลที่ต่างออกไปพอสมควร แต่ก็ยังใช้หลักการพื้นฐานของ Machine Learning และ Optimization Event ที่คุณคุ้นเคยมาแล้ว

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center: Commerce Manager และ Catalog Setup
- Meta Business Help Center: Product Feed Specification (Required and Supported Fields)
- Meta for Developers: Product Catalog API Reference
- Meta Business Help Center: Dynamic Ads Best Practices
- Meta Business Help Center: Advantage+ Catalog Ads Overview
- เอกสารประกอบ Plugin: "Facebook for WooCommerce" และ Shopify App "Facebook & Instagram"
