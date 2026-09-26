# Part 047: Custom Audience จากทุกแหล่งข้อมูล

**Section:** E — Facebook Targeting, Audiences & Funnels
**Step ที่ครอบคลุม:** 461–470 (จากทั้งหมด 1000 Steps)
**เวลาศึกษาโดยประมาณ:** 7–9 ชั่วโมง (รวมอ่านเนื้อหา + ลงมือสร้าง Custom Audience จริงจากทุกแหล่งข้อมูลที่มี)
**ระดับ:** กลาง (ต้องมี Pixel/CAPI ติดตั้งแล้วจาก Part 013–015 และเข้าใจ Core Audience จาก Part 046 มาก่อน)

---

ถ้า Core Audience ใน Part 046 คือการ "เดากลุ่มเป้าหมายจากลักษณะประชากร" Custom Audience ใน Part นี้คือการก้าวข้ามการเดาไปสู่ "การใช้ข้อมูลจริงของคนที่เคย Interact กับธุรกิจเราแล้ว" ซึ่งเป็นข้อมูลชั้นหนึ่ง (First-party Data) ที่มีค่ามากที่สุดในยุคที่ Third-party Data อ่อนแรงลงเรื่อย ๆ

Custom Audience คือหัวใจของทุกกลยุทธ์ Retargeting (ที่จะเรียนเจาะลึกใน Part 049) และเป็นวัตถุดิบสำคัญที่สุดสำหรับสร้าง Lookalike Audience (Part 048) พูดได้ว่าถ้า Custom Audience ของบัญชีไม่แข็งแรง ทั้ง Retargeting และ Lookalike ก็จะอ่อนแรงตามไปด้วย ไม่ว่า Creative หรือ Copy จะเก่งแค่ไหนก็ตาม

นักยิงแอดมือใหม่จำนวนมากรู้จัก Custom Audience แค่แบบเดียวคือ "คนที่เคยเข้าเว็บไซต์" ทั้งที่ Meta เปิดให้สร้าง Custom Audience ได้จากแหล่งข้อมูลมากถึง 6-7 ประเภท แต่ละประเภทมีจุดแข็งและการใช้งานที่ต่างกัน Part นี้จะพาไปสร้างครบทุกแหล่ง ตั้งแต่ Pixel-based, Customer List, Engagement, App Activity, ไปจนถึง Offline Activity และปิดท้ายด้วย Workshop สร้าง Custom Audience Library เต็มรูปแบบ 10 กว่าตัวสำหรับธุรกิจจริง

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 461** — ภาพรวม Custom Audience ทั้งหมด: ประเภท ตำแหน่ง UI และหลักการเลือกใช้
2. **Step 462** — Website Custom Audience: สร้างจาก Pixel ตาม URL, Event, และ Time Window
3. **Step 463** — Customer List Custom Audience: อัปโหลด CSV, การ Hash ข้อมูล, และการเพิ่ม Match Rate
4. **Step 464** — Engagement Custom Audience: Video Views %, Page/IG Engagers, Lead Form Openers, Instant Experience
5. **Step 465** — App Activity Custom Audience: สร้างจากพฤติกรรมในแอปมือถือ
6. **Step 466** — Offline Activity Custom Audience: เชื่อมข้อมูลการซื้อขายหน้าร้าน/Call Center
7. **Step 467** — การรวมและ Exclude Custom Audience หลายตัว (Combination Logic)
8. **Step 468** — กลยุทธ์ Refresh Audience และการตั้ง Exclusion Window ให้เหมาะกับ Purchase Cycle
9. **Step 469** — ขนาดขั้นต่ำ 100 คนตามกฎ Meta และขนาดขั้นต่ำที่ใช้งานได้จริงเพื่อความเสถียร
10. **Step 470** — Workshop: สร้าง Custom Audience Library ครบชุด 10+ ตัวสำหรับธุรกิจจริง

---

## Step 461: ภาพรวม Custom Audience ทั้งหมด — ประเภท ตำแหน่ง UI และหลักการเลือกใช้

### ตำแหน่งเริ่มต้นสร้าง Custom Audience

ไปที่ Ads Manager → คลิกไอคอนเมนู (Hamburger) มุมซ้ายบน → **All Tools** → หมวด **Assets** → **Audiences** → คลิกปุ่ม **Create Audience** (สีน้ำเงิน มุมขวาบน) → เลือก **Custom Audience** จากดรอปดาวน์ (แยกจาก Saved Audience และ Lookalike Audience ที่อยู่ในดรอปดาวน์เดียวกัน)

ระบบจะแสดงตัวเลือกแหล่งข้อมูล 7 ประเภทหลัก (UI อาจจัดกลุ่มเป็น 2 หมวดใหญ่ คือ "Your Sources" และ "Meta Sources"):

| แหล่งข้อมูล | หมวด | อยู่ใน Step ไหนของ Part นี้ |
|---|---|---|
| Website | Your Sources | Step 462 |
| Customer List | Your Sources | Step 463 |
| App Activity | Your Sources | Step 465 |
| Offline Activity | Your Sources | Step 466 |
| Video | Meta Sources | Step 464 |
| Instagram Account | Meta Sources | Step 464 |
| Facebook Page | Meta Sources | Step 464 |
| Lead Form | Meta Sources | Step 464 |
| Instant Experience | Meta Sources | Step 464 |
| Events | Meta Sources | Step 464 (สำหรับธุรกิจที่ใช้ Facebook Events Feature) |

### หลักการเลือกใช้แหล่งข้อมูลให้ตรงกับเป้าหมาย

ก่อนสร้าง Custom Audience ทุกครั้ง ควรตอบคำถาม 3 ข้อนี้ก่อน:

1. **เรามีข้อมูลอะไรอยู่แล้วบ้าง** — Pixel ติดตั้งแล้วหรือยัง, มีฐานลูกค้าเก่าเป็น CSV หรือไม่, เพจมีคน Engage มากพอหรือไม่
2. **ต้องการใช้ Custom Audience นี้ทำอะไร** — Retargeting (ต้องการคนที่ Interest สูงล่าสุด), เป็น Seed สำหรับ Lookalike (ต้องการคุณภาพสูงมากกว่าปริมาณ), หรือเป็น Exclusion (ต้องการรายชื่อคนที่ไม่ต้องการยิงซ้ำ)
3. **ความสดของข้อมูลสำคัญแค่ไหน** — Website Custom Audience Refresh อัตโนมัติทุกวัน แต่ Customer List ต้องอัปโหลดใหม่มือทุกครั้งที่ต้องการอัปเดต

### Custom Audience Dashboard และการอ่านสถานะ

หลังสร้างแล้ว หน้า Audiences จะแสดงคอลัมน์สำคัญที่ต้องเข้าใจ:

- **Availability** — สถานะ Active/Unavailable (Unavailable มักเกิดจาก Audience มีขนาดต่ำกว่า 100 คน หรือ Pixel/Source ถูกลบ/ถอดสิทธิ์ไปแล้ว)
- **Type** — บอกประเภทแหล่งข้อมูล
- **Size** — ขนาดปัจจุบัน อัปเดตทุก 24-48 ชั่วโมงสำหรับ Audience ที่อิง Pixel/Engagement
- **Audience combinations** — บอกว่า Custom Audience นี้ถูกใช้เป็นส่วนหนึ่งของ Lookalike หรือ Combination Audience อื่นหรือไม่

### ข้อผิดพลาดที่พบบ่อย

1. สร้าง Custom Audience จากแหล่งข้อมูลที่ไม่เหมาะกับเป้าหมาย เช่น ใช้ Customer List (ข้อมูลเก่าหลายเดือน) เป็น Retargeting หลักทั้งที่ Website Custom Audience ที่ Real-time กว่าจะเหมาะกว่ามาก
2. ไม่ตรวจสถานะ Availability เป็นระยะ ทำให้ Ad Set อ้างอิง Custom Audience ที่ Unavailable ไปแล้วโดยไม่รู้ตัว กระทบ Delivery
3. สร้าง Custom Audience ซ้ำหลายตัวที่มีเงื่อนไขเกือบเหมือนกันโดยไม่มีระบบตั้งชื่อ ทำให้จัดการยากเมื่อบัญชีโตขึ้น
4. ไม่เข้าใจว่า Custom Audience แต่ละประเภทมี "ความสด" ต่างกัน ทำให้ใช้ข้อมูลเก่าไปยิง Retargeting ที่ควรใช้ข้อมูล Real-time

---

## Step 462: Website Custom Audience — สร้างจาก Pixel ตาม URL, Event, และ Time Window

### วิธีสร้างแบบ Step-by-Step

1. Create Audience → Custom Audience → **Website**
2. เลือก Pixel ที่ต้องการ (ถ้ามีหลาย Pixel ในบัญชี ต้องเลือกให้ถูกตัว)
3. ตั้งเงื่อนไข ซึ่งมี 4 รูปแบบหลักให้เลือกจากดรอปดาวน์แรก:
   - **All website visitors** — ทุกคนที่เข้าเว็บไซต์ในช่วงเวลาที่กำหนด
   - **People who visited specific web pages** — กรองตาม URL (Contains, Equals, Starts with, ฯลฯ)
   - **Website visitors by time spent** — กรองตามเปอร์เซ็นต์เวลาที่ใช้บนเว็บ (Top 25%, Top 10%, Top 5% ของผู้เข้าชมทั้งหมด) เหมาะกับการหากลุ่ม "คนที่สนใจจริง" จากพฤติกรรมการอ่าน
   - **Custom Combination** — ผสมหลายเงื่อนไข Event/URL เข้าด้วยกันในตัวเดียว
4. ตั้ง **Retention (Time Window)** ตั้งแต่ 1-180 วัน (ค่าสูงสุดที่ Meta อนุญาต)
5. ตั้งชื่อ Audience ตาม Naming Convention แล้วคลิก **Create Audience**

### การกรองตาม Event (Standard Events/Custom Conversions)

จุดที่ทรงพลังที่สุดของ Website Custom Audience คือการกรองตาม **Event** ไม่ใช่แค่ URL เช่น เลือก "People who triggered specific events" แล้วเลือก Event ที่ Pixel เก็บไว้ (ViewContent, AddToCart, InitiateCheckout, Purchase ที่เรียนไว้ใน Part 015) วิธีนี้แม่นยำกว่าการกรองตาม URL มาก เพราะ URL อาจเปลี่ยนแปลงบ่อย (เช่น Product Page ที่มี URL ต่างกันเป็นพัน SKU) แต่ Event เดียวกันเก็บสัญญาณพฤติกรรมได้สม่ำเสมอ

### ตัวอย่าง Time Window ตามระดับ Funnel

| ระดับ Funnel | Event/เงื่อนไข | Time Window ที่แนะนำ | เหตุผล |
|---|---|---|---|
| Top of Funnel (เย็น) | All Website Visitors | 30-90 วัน | คนที่เคยผ่านมาแต่ยังไม่แสดงความสนใจสินค้าเจาะจง |
| Middle of Funnel (อุ่น) | ViewContent | 14-30 วัน | สนใจดูสินค้าแล้ว แต่ยังไม่ตัดสินใจ |
| Middle of Funnel (อุ่นกว่า) | AddToCart, InitiateCheckout | 7-14 วัน | ใกล้ตัดสินใจซื้อมาก ต้อง Retarget เร็วก่อนลืม |
| Bottom of Funnel (ร้อน) | Purchase | 180 วัน (สำหรับ Exclusion) / 30-60 วัน (สำหรับ Upsell) | ใช้ Exclude จาก Prospecting หรือใช้ยิง Upsell/Cross-sell |

### เทคนิค Custom Combination ที่ใช้บ่อย

ตัวอย่าง Combination ที่มืออาชีพใช้จริง: "คนที่ AddToCart ใน 14 วันที่ผ่านมา **และ** ไม่ได้ Purchase ใน 14 วันที่ผ่านมา" — สร้างโดยเลือก Custom Combination → Include Event "AddToCart" (14 วัน) → Exclude Event "Purchase" (14 วัน) ภายในตัวสร้าง Audience เดียวกัน วิธีนี้ได้ Audience ที่แม่นยำมากสำหรับ Retargeting "คนที่ทิ้งตะกร้า" โดยไม่ปนคนที่ซื้อไปแล้ว ซึ่งดีกว่าการสร้าง 2 Audience แยกแล้วมา Exclude ทีหลังในขั้น Ad Set เพราะทำงานเสร็จในขั้นตอนเดียว

### ข้อผิดพลาดที่พบบ่อย

1. ตั้ง Time Window ยาวเกินไปสำหรับ Event ที่ควร Retarget เร็ว เช่น ตั้ง AddToCart Retention 90 วัน ทำให้ยิงซ้ำใส่คนที่ทิ้งตะกร้าไปนานแล้วจนลืมความสนใจไปแล้ว
2. กรองตาม URL อย่างเดียวโดยไม่ใช้ Event ทำให้พลาดคนที่เข้าผ่าน URL รูปแบบอื่น (เช่น UTM Parameter ต่างกัน) ที่จริง ๆ คือหน้าเดียวกัน
3. ไม่ตรวจว่า Pixel ยิง Event ถูกต้องหรือไม่ก่อนสร้าง Audience (ควรตรวจผ่าน Events Manager ตามที่เรียนใน Part 015 ก่อนเสมอ) ถ้า Event ยิงผิดพลาด Audience ที่ได้ก็ผิดเพี้ยนตามไปด้วย
4. สร้าง Website Custom Audience ซ้ำหลายตัวที่เงื่อนไขเกือบเหมือนกันแค่ Time Window ต่างกันเล็กน้อย ทำให้จัดการยากและสิ้นเปลืองเวลา ควรวางแผน Time Window ให้ครอบคลุมตาม Funnel ตั้งแต่ต้น

---

## Step 463: Customer List Custom Audience — CSV Upload, Hashing, Match Rate

### วิธีเตรียมไฟล์ CSV ให้ถูกต้อง

Meta กำหนดรูปแบบคอลัมน์ที่รองรับไว้ชัดเจน คอลัมน์ที่แนะนำให้ใส่มากที่สุดเท่าที่มีข้อมูลจริง (ยิ่งมีหลายคอลัมน์ Match Rate ยิ่งสูง):

| คอลัมน์ | ชื่อ Header ที่ Meta รู้จัก | หมายเหตุ |
|---|---|---|
| Email | email | สำคัญที่สุด ควรมีเสมอ |
| Phone | phone | ต้องใส่ Country Code (เช่น +66) |
| First Name | fn | |
| Last Name | ln | |
| City | ct | |
| State/Province | st | สำหรับไทยมักใส่ชื่อจังหวัด |
| Zip Code | zip | รหัสไปรษณีย์ |
| Country | country | รหัส 2 ตัวอักษร เช่น TH |
| Date of Birth | dobm/dobd/doby | ถ้ามี ช่วยเพิ่ม Match Rate มาก |
| Gender | gen | m/f |
| Mobile Advertiser ID | madid | สำหรับแอป |

### กระบวนการ Hashing

Meta ไม่รับข้อมูลดิบ (Plain Text) เพื่อป้องกันความเป็นส่วนตัว ระบบจะทำการ **Hash ข้อมูลด้วย SHA-256 อัตโนมัติที่ฝั่ง Browser ก่อนส่งขึ้น Server** เมื่อเราอัปโหลดผ่าน UI ปกติ (ไม่ต้อง Hash เองด้วยมือถ้าอัปโหลดผ่านหน้า Ads Manager โดยตรง) แต่ถ้าส่งผ่าน API (Marketing API/Conversions API สำหรับ Customer List) ทีม Developer ต้อง Hash ข้อมูลเองก่อนส่ง โดยต้องทำตามมาตรฐานที่ Meta กำหนดเป๊ะ ๆ เช่น:

- Email: แปลงเป็นตัวพิมพ์เล็กทั้งหมด ตัดช่องว่างหน้า-หลัง ก่อน Hash
- Phone: ต้องมี Country Code นำหน้า ตัดเครื่องหมาย (-, (), space) ออกให้เหลือแต่ตัวเลข ก่อน Hash

### วิธีอัปโหลดผ่าน UI

1. Create Audience → Custom Audience → **Customer List**
2. เลือกประเภทข้อมูล (Customers, Website Visitors อื่น ๆ ตาม Dropdown — ปกติเลือก "Customer List" ธรรมดา)
3. อัปโหลดไฟล์ CSV หรือ TXT (หรือ Copy-paste ข้อมูลตรงในกล่องก็ได้สำหรับรายชื่อไม่มาก)
4. Map คอลัมน์ในไฟล์กับ Field ของ Meta ให้ถูกต้อง (ระบบมักเดาให้อัตโนมัติ แต่ควรตรวจสอบทุกครั้ง)
5. ตั้งชื่อ Audience → คลิก **Upload & Create**
6. รอผลลัพธ์ Match Rate ที่ระบบแสดง (ปกติใช้เวลาไม่กี่นาทีถึง 1 ชั่วโมงสำหรับไฟล์ขนาดใหญ่)

### Match Rate คืออะไร และวิธีปรับปรุง

Match Rate คือเปอร์เซ็นต์ของรายชื่อในไฟล์ที่ Meta สามารถจับคู่กับ Facebook User Profile ได้สำเร็จ โดยเฉลี่ยอยู่ที่ 40-70% ขึ้นอยู่กับคุณภาพข้อมูล วิธีเพิ่ม Match Rate:

1. **ใส่หลายคอลัมน์ให้มากที่สุด** — Email เดี่ยว ๆ อาจ Match ได้ 40-50% แต่ถ้าเพิ่ม Phone + ชื่อ-นามสกุล + เมือง Match Rate อาจขึ้นไปถึง 60-70%
2. **ทำความสะอาดข้อมูลก่อนอัปโหลด** — ลบแถวที่ Email ผิดรูปแบบ (ไม่มี @), Phone ที่ไม่ครบเลข, ข้อมูลซ้ำ
3. **ใช้ Email ที่ลูกค้าใช้สมัคร Facebook จริง** — บางธุรกิจเก็บ Email สำหรับใบเสร็จที่ต่างจาก Email ส่วนตัวที่ใช้ Facebook ทำให้ Match Rate ต่ำกว่าที่ควรเป็น
4. **อัปเดต Country Code ของเบอร์โทรให้ถูกต้องเสมอ** — เบอร์ไทยที่ไม่มี +66 นำหน้าอาจ Match ไม่ได้เลยในบางกรณี

### เทคนิคขั้นสูง: ทำ RFM Segmentation ก่อนอัปโหลด Customer List

ก่อนอัปโหลด Customer List ทั้งหมดเป็นก้อนเดียว มืออาชีพมักแบ่งฐานลูกค้าด้วยหลัก **RFM (Recency, Frequency, Monetary)** ก่อนเสมอ เพราะลูกค้าทุกคนไม่มีค่าเท่ากัน และ Custom Audience ที่แบ่งตาม RFM จะเป็น Seed ที่มีคุณภาพต่างกันมากเมื่อนำไปสร้าง Lookalike ใน Part 048

- **Recency** — ซื้อล่าสุดเมื่อไหร่ (ยิ่งเร็ว ยิ่งมีโอกาสตอบสนองต่อ Retargeting/Win-back สูง)
- **Frequency** — ซื้อบ่อยแค่ไหน (ลูกค้าที่ซื้อซ้ำหลายครั้งมักมีความภักดีสูงกว่า)
- **Monetary** — ใช้จ่ายสะสมเท่าไหร่ (บอกกำลังซื้อและมูลค่าที่ธุรกิจได้จากลูกค้าคนนั้น)

วิธีปฏิบัติจริงคือ Export ข้อมูลจาก CRM/ระบบ Order เป็น Excel/Sheets แล้วคำนวณ 3 คะแนนนี้ให้แต่ละลูกค้า จากนั้นแบ่งกลุ่มอย่างน้อย 3 ระดับ เช่น:

| กลุ่ม | เกณฑ์ตัวอย่าง | การใช้งาน |
|---|---|---|
| VIP/Champions | Recency < 30 วัน, Frequency 3+ ครั้ง, Monetary Top 20% | Seed คุณภาพสูงสุดสำหรับ Value-Based Lookalike |
| Loyal ทั่วไป | Recency < 90 วัน, Frequency 2+ ครั้ง | Seed สำหรับ Lookalike ทั่วไป, Upsell Campaign |
| At-risk/Lapsed | Recency > 90 วัน, เคย Frequency สูงแต่หายไป | Win-back Campaign เฉพาะกลุ่ม |
| One-time Buyer | Frequency 1 ครั้ง | Nurture ให้กลายเป็น Repeat Customer |

การอัปโหลดแยกไฟล์ตามกลุ่ม RFM แทนการอัปโหลดฐานลูกค้าทั้งหมดเป็นก้อนเดียว ช่วยให้สามารถสร้าง Custom Audience และต่อยอดเป็น Lookalike ที่มีคุณภาพแตกต่างกันตามวัตถุประสงค์ ซึ่งจะเห็นผลชัดเจนมากเมื่อไปถึง Value-Based Lookalike ใน Part 048 Step 474

### ข้อผิดพลาดที่พบบ่อย

1. อัปโหลดไฟล์ที่มีเบอร์โทรไม่มี Country Code ทำให้ Match Rate ต่ำผิดปกติ
2. ใส่แค่คอลัมน์ Email อย่างเดียวทั้งที่มีข้อมูลอื่นอยู่แล้วในระบบ CRM แต่ไม่ได้ Export มาด้วย
3. ไม่ลบข้อมูลลูกค้าที่ Unsubscribe หรือขอให้ลบข้อมูล (ตาม PDPA ที่เรียนใน Part 007) ออกจากไฟล์ก่อนอัปโหลด ซึ่งเป็นความเสี่ยงทั้งด้านกฎหมายและความสัมพันธ์กับลูกค้า
4. อัปโหลดไฟล์ครั้งเดียวแล้วไม่อัปเดตอีกเลยเป็นปี ทำให้ Audience ล้าสมัยไม่สะท้อนฐานลูกค้าปัจจุบัน
5. สับสนระหว่าง "Customer List" (สำหรับสร้าง Custom Audience) กับการอัปโหลด CSV ในบริบทอื่นของ Ads Manager เช่น Catalog Feed (Part 027) ซึ่งเป็นคนละฟังก์ชันกันโดยสิ้นเชิง

---

## Step 464: Engagement Custom Audience — Video Views, Page/IG Engagers, Lead Form, Instant Experience

### Video Views Custom Audience

สร้างจาก Create Audience → Custom Audience → **Video** เลือกวิดีโอ (หรือ Post ที่มีวิดีโอ) ที่ต้องการ แล้วเลือกระดับเปอร์เซ็นต์การดูจาก 5 ระดับ:

| ระดับ | ความหมาย | การใช้งาน |
|---|---|---|
| 3-second video views | ดูอย่างน้อย 3 วินาที | Audience กว้างที่สุด ใช้เป็น Awareness Retargeting เบา ๆ |
| ThruPlay / 15-second | ดูจนจบหรืออย่างน้อย 15 วินาที | สัญญาณความสนใจระดับต้น |
| 25% ของวิดีโอ | ดูได้ 1/4 ของความยาว | เริ่มกรองคนที่สนใจจริง |
| 50% ของวิดีโอ | ดูได้ครึ่งหนึ่ง | กรองแน่นขึ้น เหมาะกับวิดีโอ 30-60 วินาที |
| 75% ของวิดีโอ | ดูเกือบจบ | สัญญาณความสนใจสูง เหมาะเป็น Seed สำหรับ Lookalike |
| 95% ของวิดีโอ | ดูจบแทบทั้งหมด | แคบที่สุด แต่คุณภาพสูงสุด เหมาะกับวิดีโอ Storytelling ยาว |

**หลักการเลือกเปอร์เซ็นต์:** สำหรับวิดีโอสั้น (15-30 วินาที) ควรใช้ 50%/75%/95% เพราะดูจบเร็วสัญญาณจะแม่นยำ ส่วนวิดีโอยาว (มากกว่า 2 นาที) การดู 25% ก็ถือว่าเป็นสัญญาณความสนใจที่มีน้ำหนักพอแล้ว เพราะคนที่ไม่สนใจมักปัดผ่านภายใน 3-5 วินาทีแรก

### Page/Instagram Engagement Custom Audience

Create Audience → Custom Audience → **Facebook Page** (หรือ **Instagram Account**) เลือกเพจ/บัญชี IG แล้วเลือกประเภท Engagement:

- Everyone who engaged with your Page/Account
- People who visited your Page/Profile
- People who engaged with any post or ad
- People who sent a message to your Page/Account
- People who saved your Page/Profile or any post

Time Window เลือกได้สูงสุด 365 วันสำหรับ Page/IG Engagement (ยาวกว่า Website Custom Audience ที่จำกัดแค่ 180 วัน) เหมาะกับธุรกิจที่ Content Organic แข็งแรงและต้องการเก็บกลุ่ม Engager ระยะยาวไว้ Retarget

### Lead Form Custom Audience

สำหรับธุรกิจที่ใช้ Instant Form (Lead Ads จาก Part 024) สามารถสร้าง Custom Audience จาก **Lead Form** โดยเลือกได้ 3 ระดับ:

1. **People who opened the form** — เปิดฟอร์มแต่ยังไม่กรอก (สัญญาณความสนใจแต่ยังไม่ตัดสินใจ)
2. **People who opened but didn't submit** — เปิดแล้วแต่ไม่ส่ง (กลุ่มที่น่าสนใจมากสำหรับ Retarget เพราะแสดงความตั้งใจแต่มีบางอย่างขัดขวาง)
3. **People who submitted the form** — กรอกและส่งสำเร็จแล้ว (ใช้เป็น Exclusion จากแคมเปญ Lead Gen ใหม่ หรือใช้ยิง Nurture Content ต่อ)

Audience กลุ่ม "เปิดแต่ไม่ส่ง" เป็นหนึ่งใน Audience ที่ถูกมองข้ามบ่อยที่สุด ทั้งที่มีศักยภาพสูงมาก เพราะคนกลุ่มนี้สนใจมากพอจะเปิดฟอร์ม แต่มีอุปสรรคบางอย่าง (ฟอร์มยาวเกินไป, ลังเลตอนสุดท้าย, สัญญาณอินเทอร์เน็ตขาด) การยิง Retargeting กลุ่มนี้ด้วย Message ที่ช่วยลดความลังเล (เช่น รีวิว, การันตี) มักได้ CPA ต่ำกว่า Prospecting ใหม่มาก

### Instant Experience Custom Audience

สำหรับแคมเปญที่ใช้ Instant Experience (Canvas เดิม) สามารถสร้าง Custom Audience จากคนที่เปิดดู Instant Experience นั้น รวมถึงกรองตามการกระทำภายใน เช่น คนที่คลิกลิงก์ภายใน Instant Experience หรือเปิดดูจนถึงส่วนใดส่วนหนึ่ง เหมาะกับธุรกิจที่ใช้ Instant Experience เป็น Mini Landing Page ภายใน Facebook

### ข้อผิดพลาดที่พบบ่อย

1. ใช้ Video Views 3-second Audience ไปยิง Retargeting แบบ Hard Sell ทันที ทั้งที่สัญญาณนี้อ่อนเกินไป ควรใช้ Content ที่ให้ข้อมูลเพิ่มก่อน ไม่ใช่ขายตรงทันที
2. ไม่เคยสร้าง "เปิดฟอร์มแต่ไม่ส่ง" Audience ทั้งที่เป็นกลุ่มคุณภาพสูงที่รอ Retarget อยู่
3. ตั้ง Time Window ของ Page Engagement ยาวเกินไป (365 วัน) สำหรับธุรกิจที่มีสินค้าเปลี่ยนเทรนด์เร็ว ทำให้ Engager เก่ามากไม่มีความหมายกับสินค้าปัจจุบันแล้ว
4. ไม่แยก Custom Audience ตามระดับ Engagement (3s vs 75%) ทำให้ยิง Message เดียวกันหมดกับทุกระดับความสนใจ ทั้งที่ควรมี Message ต่างกันตามความอุ่นของแต่ละกลุ่ม

---

## Step 465: App Activity Custom Audience

### เมื่อไหร่ต้องใช้ App Activity Custom Audience

สำหรับธุรกิจที่มีแอปมือถือของตัวเอง (เรียนพื้นฐานใน Part 028 เรื่อง App Promotion) และติดตั้ง Facebook SDK สำหรับแอป (Meta SDK for Android/iOS) แล้ว สามารถสร้าง Custom Audience จากพฤติกรรมภายในแอปได้ เช่น เปิดแอป, ทำ In-App Event (Add to Cart ในแอป, Purchase ในแอป, Level Achieved สำหรับเกม, Tutorial Completed)

### วิธีสร้าง

Create Audience → Custom Audience → **App Activity** → เลือกแอปที่เชื่อมกับ Business Manager แล้ว → เลือก Event ที่ต้องการ (ดึงมาจาก App Events ที่ตั้งค่าไว้ใน Events Manager เหมือนกับ Pixel Events) → ตั้ง Time Window → ตั้งชื่อ → Create

### กรณีใช้งานที่พบบ่อย

1. **Retarget คนที่ติดตั้งแอปแต่ไม่เคย Open App อีกเลย** — เพื่อดึงกลับมาใช้งาน (Re-engagement Campaign)
2. **Retarget คนที่ Add to Cart ในแอปแต่ไม่ Purchase** — เหมือนกับ Website แต่เกิดในบริบทแอป
3. **สร้าง Lookalike จากคนที่ทำ Level สูง/ใช้เงินในเกม (High LTV Players)** — สำหรับธุรกิจเกม
4. **Exclude คนที่ Uninstall แอปไปแล้ว** — ป้องกันงบเสียไปกับการโปรโมทให้คนที่ลบแอปไปแล้ว (ต้องเก็บ Event Uninstall ผ่าน SDK ที่รองรับ)

### ข้อผิดพลาดที่พบบ่อย

1. ไม่ได้ติดตั้ง SDK ให้ครบทุก Event ที่จำเป็น ทำให้สร้าง Custom Audience ได้จำกัดแค่ Event พื้นฐาน (Install, Open) ไม่สามารถแยกระดับความสนใจได้ละเอียด
2. สับสนระหว่าง App Events ที่ตั้งค่าผ่าน SDK โดยตรง กับ Deep Link Event ที่มาจาก Facebook Ads Manager เอง ทำให้ตีความ Custom Audience ผิดพลาด
3. ไม่ Refresh ข้อมูล App Activity Audience เป็นระยะ ทั้งที่พฤติกรรมผู้ใช้แอปเปลี่ยนเร็วกว่าเว็บไซต์ในหลายกรณี

---

## Step 466: Offline Activity Custom Audience

### Offline Activity คืออะไร

สำหรับธุรกิจที่มีการขายหรือติดต่อลูกค้านอกช่องทางดิจิทัล เช่น การขายหน้าร้าน (POS), การจองผ่าน Call Center, การซื้อผ่าน Sales ที่ไม่ได้เกิดบนเว็บไซต์เลย Meta เปิดให้อัปโหลดข้อมูลเหล่านี้เข้าระบบผ่าน **Offline Event Set** เพื่อนำมาสร้าง Custom Audience และยังใช้วัด Conversion แบบ Offline Conversion ได้ด้วย (เชื่อมกับการวัดผล ROAS จากช่องทางที่ไม่ใช่ออนไลน์)

### วิธีตั้งค่า

1. ไปที่ Events Manager → คลิก **Connect Data Sources** → เลือก **Offline** → **Create Offline Event Set**
2. ตั้งชื่อ Event Set แล้วเลือกวิธีอัปโหลดข้อมูล — อัปโหลดไฟล์ CSV ด้วยมือ, เชื่อมผ่าน Partner Integration (เช่น ระบบ POS ที่รองรับ Meta Offline Conversions API), หรือส่งผ่าน API โดยทีม Developer
3. ไฟล์ CSV ต้องมีคอลัมน์อย่างน้อย Event Name (เช่น Purchase), Event Time, และข้อมูลลูกค้าอย่างน้อย 1 อย่าง (Email/Phone/ชื่อ) เพื่อให้ Match กับ Facebook User ได้
4. หลังอัปโหลดและ Match สำเร็จ ไปที่ Create Audience → Custom Audience → **Offline Activity** → เลือก Event Set → เลือก Event/Time Window → Create

### กรณีใช้งานที่พบบ่อย

1. ร้านค้าปลีกที่มีระบบ POS เชื่อม Offline Events เพื่อสร้าง Custom Audience "ลูกค้าที่ซื้อหน้าร้านใน 30 วัน" แล้วนำไปยิง Cross-sell สินค้าอื่นทางออนไลน์
2. ธุรกิจ B2B ที่ปิดการขายผ่าน Sales Call อัปโหลดรายชื่อลูกค้าที่ปิดดีลสำเร็จ เพื่อ Exclude จากแคมเปญ Lead Gen ใหม่ (ไม่ต้องเสียงบยิงหาคนที่ซื้อไปแล้ว)
3. คลินิก/ธุรกิจบริการที่นัดผ่านโทรศัพท์ อัปโหลดข้อมูลการนัดสำเร็จ เพื่อวัด True ROAS จากแอด Facebook ที่แปลงมาเป็นการนัดจริง ไม่ใช่แค่ Lead ดิบ

### ตัวอย่างตัวเลขจริงจากธุรกิจที่เชื่อม Offline Activity สำเร็จ

ร้านเฟอร์นิเจอร์แห่งหนึ่งมีทั้งหน้าร้าน 3 สาขาและเว็บไซต์ ก่อนเชื่อม Offline Activity ทีมวัด ROAS จาก Facebook Ads ได้แค่ 1.8x (นับเฉพาะ Purchase ที่เกิดบนเว็บไซต์) แต่ในความจริงมีลูกค้าจำนวนมากที่เห็นโฆษณาแล้วเดินทางไปซื้อที่หน้าร้านแทน ซึ่ง Pixel มองไม่เห็นเลย หลังตั้ง Offline Event Set และฝึกพนักงานหน้าร้านให้เก็บเบอร์โทรลูกค้าทุกครั้งที่ขาย (ผ่านระบบสมาชิกง่าย ๆ) แล้วอัปโหลดข้อมูลการขายหน้าร้านเข้า Offline Event Set ทุกสัปดาห์ ผลคือ Meta สามารถ Match ธุรกรรมหน้าร้านกับคนที่เคยเห็นโฆษณาได้ประมาณ 35% ของยอดขายหน้าร้านทั้งหมด ทำให้ ROAS ที่วัดได้จริงขยับขึ้นเป็น 3.1x ซึ่งเป็นตัวเลขที่ใกล้เคียงความจริงมากกว่าเดิม และยังนำ Custom Audience จาก Offline Purchasers ไปใช้ Exclude จากแคมเปญ Prospecting ได้อีกด้วย ลด CPA รวมของบัญชีลงเพิ่มอีก 12%

### ข้อผิดพลาดที่พบบ่อย

1. ไม่มีระบบเก็บข้อมูล Offline ที่มี Email/Phone ของลูกค้าเลย ทำให้ไม่มีอะไรจะอัปโหลด (ควรวางระบบเก็บข้อมูลลูกค้าหน้าร้านตั้งแต่ต้น เช่น สมาชิก/ใบเสร็จที่ขอเบอร์โทร)
2. อัปโหลดข้อมูล Offline ล่าช้าเกินไป (เดือนละครั้ง) ทำให้ Custom Audience ไม่ทันเวลาสำหรับ Retargeting ที่ควรทำเร็ว
3. ไม่ตรวจ Data Privacy/PDPA ก่อนอัปโหลดข้อมูลลูกค้า Offline เข้าระบบ Meta ต้องแน่ใจว่าลูกค้ายินยอมให้ใช้ข้อมูลเพื่อการตลาดแล้ว (ดู Part 007)

---

## Step 467: การรวมและ Exclude Custom Audience หลายตัว (Combination Logic)

### Audience Combination คืออะไร

Meta เปิดให้สร้าง **Custom Combination Audience** ที่ผสม Custom Audience หลายตัวเข้าด้วยกันด้วย Logic AND/OR/NOT ในตัวสร้าง Audience เดียว โดยไม่ต้องไปตั้งค่าที่ระดับ Ad Set ทุกครั้ง วิธีนี้ช่วยประหยัดเวลาและลดความผิดพลาดเมื่อต้องใช้ Combination เดียวกันในหลาย Ad Set/แคมเปญ

### วิธีสร้าง

Create Audience → Custom Audience → **Custom Combination** (หรือในบางบัญชีอยู่ในหน้าเดียวกับตอนสร้าง Website Custom Audience แบบ Custom Combination) → เลือก Audience ที่มีอยู่แล้วมาผสม เช่น:

- Include: `Website_AllVisitors_180d`
- AND (Narrow): `Website_ViewContent_30d`
- AND NOT (Exclude): `Website_Purchase_30d`

ผลคือ Audience ใหม่ = คนที่เข้าเว็บ 180 วัน และดูสินค้าใน 30 วัน แต่ยังไม่ซื้อใน 30 วัน — เหมาะเป็น Retargeting กลุ่ม "สนใจแต่ยังไม่ซื้อ" อย่างแม่นยำ

### ตัวอย่าง Combination ที่ใช้บ่อยในธุรกิจจริง

| ชื่อ Combination | Logic | ใช้เพื่อ |
|---|---|---|
| Warm_NotPurchased | (Website Visitors 30d) AND NOT (Purchasers 30d) | Retargeting กลุ่มอุ่นที่ยังไม่ซื้อ |
| HighIntent_Excl_Lead | (AddToCart 14d OR InitiateCheckout 14d) AND NOT (Purchasers 14d) | เจาะกลุ่มใกล้ซื้อที่สุด |
| Loyal_Repeat | (Purchasers 365d) AND NOT (Purchasers 30d) | ลูกค้าเก่าที่ห่างหายไปพักหนึ่ง เหมาะกับ Win-back Campaign |
| EngagedButColdEmail | (Page Engagers 90d) AND NOT (Website Visitors 90d) | คน Engage บนโซเชียลแต่ไม่เคยเข้าเว็บ ต้องดึงเข้าเว็บก่อน |

### ตัวอย่างการไล่ Logic แบบเห็นภาพ (Worked Example)

สมมติธุรกิจขายรองเท้ากีฬาต้องการ Audience "คนที่สนใจรองเท้าวิ่งจริงจัง แต่ยังไม่เคยซื้ออะไรจากร้านเลย" การไล่ Logic ทำได้ดังนี้:

```
Step 1: สร้าง WEB_ViewContent_Running_60d
        (Website Custom Audience: Event=ViewContent, URL contains "/running-shoes/", 60 วัน)

Step 2: สร้าง WEB_Purchase_AllTime
        (Website Custom Audience: Event=Purchase, 180 วัน — ครอบคลุมสูงสุดที่ Pixel ทำได้)

Step 3: สร้าง LIST_AllCustomers_Lifetime
        (Customer List: อัปโหลดฐานลูกค้าทั้งหมดจาก CRM ไม่จำกัด Time Window)

Step 4: สร้าง Custom Combination ใหม่
        Include: WEB_ViewContent_Running_60d
        AND NOT: WEB_Purchase_AllTime
        AND NOT: LIST_AllCustomers_Lifetime
```

ผลลัพธ์คือ Audience ที่กรอง 2 ชั้น — ทั้งคนที่ Purchase Event เคยยิงในเว็บ (180 วันหลังสุด) และคนที่อยู่ในฐานลูกค้าทั้งหมดของ CRM (ซึ่งอาจรวมคนที่ซื้อเกิน 180 วันมาแล้วด้วย) ถูกตัดออกทั้งคู่ เหลือแต่คนที่สนใจรองเท้าวิ่งจริง ๆ แต่ยังไม่เคยเป็นลูกค้าเลยไม่ว่าจะซื้อเมื่อไหร่ก็ตาม นี่คือเหตุผลที่ควรใช้ Customer List ควบคู่กับ Website Custom Audience ในการ Exclude เสมอ เพราะ Pixel-based เพียงอย่างเดียวมีเพดาน 180 วันที่มองไม่เห็นลูกค้าเก่าที่ซื้อมานานแล้ว

### ข้อผิดพลาดที่พบบ่อย

1. ตั้ง Combination ซับซ้อนเกินไปจนขนาด Audience เล็กกว่า 100 คนและใช้งานไม่ได้ (ดู Step 469 เรื่องขนาดขั้นต่ำ)
2. สร้าง Combination แล้วไม่ตั้งชื่อให้สื่อ Logic ที่ใช้ ทำให้ทีมอื่นเข้าใจผิดว่า Audience นี้คืออะไรกันแน่
3. ลืมว่า Combination Audience ที่สร้างไว้ล่วงหน้าไม่ Auto-update Logic ถ้าไปแก้ Custom Audience ต้นทางที่เอามาผสมทีหลัง (ต้องตรวจสอบว่ายังอ้างอิงถูกต้องอยู่)
4. ใช้ NOT Logic ผิดทาง (Exclude สิ่งที่ควร Include) ทำให้ได้ Audience ตรงข้ามกับที่ตั้งใจโดยไม่รู้ตัว ควรตรวจสอบ Estimated Size ก่อนเทียบกับสมมติฐานเสมอ

---

## Step 468: กลยุทธ์ Refresh Audience และ Exclusion Window

### ทำไมต้องคิดเรื่อง Refresh และ Exclusion Window อย่างเป็นระบบ

Custom Audience ที่อิง Pixel/Engagement จะ Refresh ตัวเองอัตโนมัติทุก 24-48 ชั่วโมงอยู่แล้ว (คนใหม่เข้ามา คนเก่าที่เกิน Time Window หลุดออกไปเอง) แต่ปัญหาคือ **Time Window ที่เลือกไว้ต้องสัมพันธ์กับ Purchase Cycle ของสินค้าจริง** ไม่ใช่ตั้งตามความเคยชินหรือค่า Default

### ตัวอย่างการคำนวณ Time Window ตาม Purchase Cycle

| ประเภทสินค้า | Purchase Cycle เฉลี่ย | Time Window ที่แนะนำสำหรับ Retargeting | Exclusion Window สำหรับ Prospecting |
|---|---|---|---|
| อาหาร/เครื่องดื่ม (ซื้อซ้ำเร็ว) | 3-7 วัน | Retarget 3-5 วัน | Exclude Purchasers 3-5 วัน (ซื้อซ้ำได้เร็ว) |
| เครื่องสำอาง/สกินแคร์ | 30-45 วัน | Retarget 14-21 วัน | Exclude Purchasers 30-45 วัน |
| เสื้อผ้าแฟชั่น | 30-60 วัน | Retarget 14-30 วัน | Exclude Purchasers 30 วัน |
| อาหารเสริม (ใช้ต่อเนื่อง) | 20-30 วัน (ตามรอบสินค้าหมด) | Retarget 15-25 วัน (ก่อนของหมดพอดี) | Exclude Purchasers 15 วัน (เพื่อยิง Reorder ตอนใกล้หมด) |
| เฟอร์นิเจอร์/เครื่องใช้ไฟฟ้า | 180-365+ วัน | Retarget 30-60 วัน | Exclude Purchasers 180-365 วัน |
| คอร์สออนไลน์/ดิจิทัลโปรดักต์ | ซื้อครั้งเดียว/ไม่ซื้อซ้ำ | Retarget 7-14 วัน (ก่อนหมดความสนใจ) | Exclude Purchasers ตลอดไป (Lifetime ถ้าเป็นไปได้ หรือ 180 วันสูงสุดที่ระบบรองรับ) |

### ข้อจำกัดสำคัญ: Time Window สูงสุดของ Meta

Website Custom Audience จำกัด Retention สูงสุดที่ **180 วัน** เท่านั้น (ไม่สามารถตั้ง Lifetime ได้) หมายความว่าสำหรับสินค้าที่ Purchase Cycle ยาวกว่า 180 วัน (เช่น เฟอร์นิเจอร์ที่ซื้อซ้ำทุก 2-3 ปี) การ Exclude Purchasers แบบ Lifetime จริง ๆ ต้องใช้วิธีอื่นเสริม เช่น อัปโหลด Customer List ของ Purchasers ทั้งหมดที่มีในระบบ CRM แทน เพราะ Customer List ไม่มีข้อจำกัด Time Window แบบ Pixel-based Audience

### การตั้งปฏิทิน Refresh สำหรับ Customer List

Customer List ไม่ Refresh อัตโนมัติเหมือน Pixel-based ต้องอัปโหลดใหม่ด้วยมือ (หรือผ่าน API แบบอัตโนมัติ) แนะนำให้ตั้งปฏิทินตายตัว เช่น:

- ธุรกิจ E-commerce ที่มีลูกค้าใหม่ทุกวัน: Export/อัปโหลด Customer List ใหม่ **ทุกสัปดาห์**
- ธุรกิจ B2B ที่มี Sales Cycle ยาว: อัปโหลดใหม่**ทุกเดือน**
- ธุรกิจที่ใช้ CRM ที่รองรับ API เชื่อมตรง (เช่นผ่าน Zapier/Make หรือ Direct Integration): ตั้งให้ Sync อัตโนมัติแบบ Real-time หรือรายวัน ไม่ต้องอัปโหลดมือเลย

### ข้อผิดพลาดที่พบบ่อย

1. ใช้ Time Window เดียวกันหมดทุกสินค้าโดยไม่คำนึงถึง Purchase Cycle ที่ต่างกัน
2. คิดว่า Website Custom Audience Refresh เอง = ไม่ต้องดูแลอะไรเลย ทั้งที่ Time Window ที่ตั้งผิดจากต้นจะให้ผลลัพธ์ผิดตลอดไปจนกว่าจะแก้
3. ลืมอัปเดต Customer List เป็นเวลานาน ทำให้ Exclusion ไม่ครอบคลุมลูกค้าใหม่ที่เพิ่งซื้อไปหลังจากอัปโหลดครั้งล่าสุด
4. ไม่มีเจ้าภาพ (Owner) ที่รับผิดชอบ Refresh Audience ในทีม ทำให้งานนี้ตกหล่นเมื่อธุรกิจโตและมีคนดูแลหลายคน

---

## Step 469: ขนาดขั้นต่ำ 100 คน และขนาดที่ใช้งานได้จริงเพื่อความเสถียร

### กฎขั้นต่ำ 100 คนของ Meta

Meta กำหนดว่า Custom Audience ต้องมีขนาดอย่างน้อย **100 คน** ถึงจะสามารถใช้ยิงโฆษณาได้ (ต่ำกว่านี้ระบบจะแสดงสถานะ "Audience size too small" และ Ad Set จะไม่ Deliver) นี่คือเกณฑ์ขั้นต่ำสุดทางเทคนิค แต่ **ไม่ใช่**เกณฑ์ที่แนะนำสำหรับการใช้งานจริงที่ต้องการผลลัพธ์ดี

### ขนาดที่ใช้งานได้จริงเพื่อความเสถียร (Practical Minimums)

| วัตถุประสงค์การใช้งาน | ขนาดขั้นต่ำที่แนะนำจริง | เหตุผล |
|---|---|---|
| Retargeting ทั่วไป (Traffic/Engagement Objective) | 1,000+ คน | ต่ำกว่านี้ Frequency จะพุ่งเร็วมากภายในไม่กี่วัน |
| Retargeting เพื่อ Conversion (Purchase/Lead) | 1,000-3,000 คน | ต้องมี Pool พอให้ระบบหมุนคนได้ ไม่ Fatigue เร็วเกินไป |
| Seed สำหรับสร้าง Lookalike Audience | 500-1,000+ คน (ยิ่งมาก ยิ่งดี ถ้าคุณภาพสูง) | Seed เล็กเกินไป Lookalike จะไม่มี Pattern ให้เรียนรู้พอ (เจาะลึกใน Part 048) |
| Exclusion Audience | ไม่มีขั้นต่ำที่ต้องกังวล (แม้ 100 คนก็ใช้ Exclude ได้) | Exclusion ไม่ต้องพึ่งขนาดใหญ่เพื่อความเสถียรเหมือน Include |
| Custom Combination ที่ Narrow หลายชั้น | ตรวจสอบว่าไม่ต่ำกว่า 1,000 คนหลัง Combine ทั้งหมด | Combination ที่แคบเกินมักเจอปัญหาขนาดเล็กโดยไม่รู้ตัวจนกว่าจะสร้างเสร็จ |

### สัญญาณเตือนเมื่อ Audience เล็กเกินไปสำหรับใช้งานจริง

- Frequency ทะลุ 5-6 ภายในสัปดาห์แรกของการยิง Retargeting
- CPM พุ่งสูงขึ้นเรื่อย ๆ ทุกวันแบบไม่มีเหตุผลจากภายนอก
- Ads Manager แสดงคำเตือน "Your audience may be too small to reach many people" แม้จะผ่านเกณฑ์ 100 คนแล้วก็ตาม

### วิธีแก้เมื่อ Custom Audience เล็กเกินไป

1. **ขยาย Time Window** ถ้ายังไม่ถึงเพดาน 180 วัน (สำหรับ Website Custom Audience)
2. **รวมหลาย Event เข้าด้วยกันแบบ OR** เช่น รวม ViewContent + AddToCart เป็น Audience เดียว แทนแยกกัน 2 ตัวเล็ก ๆ
3. **ลด Narrow Further ที่ไม่จำเป็นออก** ถ้า Combination แคบเกินไปจนเล็ก
4. **ใช้ร่วมกับ Lookalike** — ถ้า Seed เล็กเกินกว่าจะยิง Retargeting ตรงได้ผลดี อาจใช้ Seed นั้นสร้าง Lookalike แทนเพื่อขยาย Pool (เจาะลึกวิธีเลือก % ที่เหมาะสมใน Part 048)

### ข้อผิดพลาดที่พบบ่อย

1. สร้าง Custom Combination แคบมากเพื่อความแม่นยำสูงสุด แต่ได้ Audience 150 คนที่ผ่านเกณฑ์ขั้นต่ำ 100 คนพอดี ทำให้ใช้งานได้ทางเทคนิคแต่ผลลัพธ์แย่มากในทางปฏิบัติเพราะ Pool เล็กเกินจะมี Performance ที่เสถียร
2. เข้าใจผิดว่าเกณฑ์ 100 คนของ Meta คือ "ขนาดที่ดีพอ" ทั้งที่เป็นแค่เกณฑ์ขั้นต่ำทางเทคนิคเท่านั้น
3. ไม่ตรวจ Frequency ของ Ad Set ที่ยิง Custom Audience ขนาดเล็กเป็นประจำ ทำให้ Ad Fatigue เกิดขึ้นโดยไม่รู้ตัว (เชื่อมกับ Part 060 เรื่อง Ad Fatigue)
4. พยายามยิง Conversion Objective กับ Custom Audience ที่เล็กเกินไปจนไม่มีทางได้ Conversion เพียงพอต่อสัปดาห์เพื่อออกจาก Learning Phase

---

## Step 470: Workshop — สร้าง Custom Audience Library ครบชุด 10+ ตัวสำหรับธุรกิจจริง

### เป้าหมายของ Workshop

สร้าง "Library" ของ Custom Audience ที่ครอบคลุมทุกระดับ Funnel และทุกแหล่งข้อมูลที่ธุรกิจมีอยู่จริง เพื่อให้พร้อมใช้งานในทุกแคมเปญ ไม่ต้องมาสร้างใหม่ทุกครั้งที่ต้องการ Retarget

### สินค้าตัวอย่างที่ใช้ในการฝึก

สมมติเลือกธุรกิจ: **ร้านค้าออนไลน์ขายเครื่องใช้ไฟฟ้าในบ้านขนาดเล็ก** (มีเว็บไซต์ + Pixel ติดตั้งแล้ว, มี Facebook Page ที่มี Engager, มีฐานลูกค้าเก่าเป็น CSV จากระบบ Order, ไม่มีแอปมือถือ)

### รายการ Custom Audience ที่ต้องสร้างให้ครบ (Checklist การสร้าง)

**กลุ่ม Website-based (5 ตัว)**

1. `WEB_AllVisitors_180d` — ทุกคนที่เข้าเว็บ 180 วัน
2. `WEB_ViewContent_30d` — ดูหน้าสินค้าใน 30 วัน
3. `WEB_AddToCart_NotPurchase_14d` — Combination: AddToCart 14 วัน AND NOT Purchase 14 วัน
4. `WEB_InitiateCheckout_NotPurchase_7d` — Combination: InitiateCheckout 7 วัน AND NOT Purchase 7 วัน
5. `WEB_Purchase_180d` — ผู้ซื้อทั้งหมดใน 180 วัน (ใช้เป็น Exclusion หลักและ Seed สำหรับ Lookalike)

**กลุ่ม Engagement-based (3 ตัว)**

6. `ENG_PageEngagers_90d` — คน Engage กับ Page ใน 90 วัน
7. `ENG_VideoViews75_30d` — คนดูวิดีโอโฆษณา 75%+ ใน 30 วัน
8. `ENG_IGEngagers_90d` — คน Engage กับ Instagram Account ใน 90 วัน

**กลุ่ม Customer List-based (2 ตัว)**

9. `LIST_AllCustomers_Lifetime` — อัปโหลดฐานลูกค้าทั้งหมดจากระบบ Order (ไม่มีข้อจำกัด Time Window แบบ Pixel)
10. `LIST_HighValueCustomers_Top20pct` — อัปโหลดเฉพาะลูกค้าที่มียอดซื้อสะสมสูงสุด Top 20% (Export จาก CRM ตาม Order Value)

**กลุ่ม Combination พิเศษ (2 ตัวเพิ่มเติม)**

11. `COMBO_Warm_NotPurchased_30d` — (WEB_AllVisitors_180d) AND NOT (WEB_Purchase_30d)
12. `COMBO_Loyal_Lapsed_180d` — (LIST_AllCustomers_Lifetime) AND NOT (WEB_Purchase_60d) — ลูกค้าเก่าที่ห่างหายเกิน 60 วัน เหมาะกับ Win-back Campaign

### ขั้นตอนปฏิบัติจริง

1. เปิด Ads Manager → All Tools → Audiences
2. สร้างตามรายการทั้ง 12 ตัวข้างต้นตามลำดับ โดยอ้างอิงวิธีสร้างจาก Step 462-467
3. หลังสร้างครบ ให้เปิดตาราง Audiences ทั้งหมด บันทึกขนาด (Size) ของแต่ละตัวลงในสมุด/ชีทติดตาม
4. ตรวจสอบว่าตัวไหนมีขนาดต่ำกว่า 1,000 คน (เกณฑ์ Practical Minimum จาก Step 469) แล้ววางแผนว่าจะขยาย Time Window หรือรวม Event เพิ่มอย่างไร
5. จัดกลุ่ม Audience ทั้ง 12 ตัวลงในตาราง Funnel Mapping ดังนี้

| ระดับ Funnel | Custom Audience ที่ใช้ | วัตถุประสงค์หลัก |
|---|---|---|
| Cold/Prospecting | (ไม่ใช้ Custom Audience ตรง ใช้ Core/Lookalike แทน แต่ Exclude ด้วย #5, #9) | หาลูกค้าใหม่ ไม่ปนคนซื้อแล้ว |
| Warm (สนใจแล้วยังไม่ซื้อ) | #2, #6, #7, #8, #11 | Nurture ให้ตัดสินใจซื้อ |
| Hot (ใกล้ซื้อมาก) | #3, #4 | ดันให้ปิดการขายด้วย Urgency/Offer |
| Post-purchase (ลูกค้าเดิม) | #5, #9, #10, #12 | Upsell/Cross-sell/Win-back |

### ผลที่ควรได้จาก Workshop นี้

เมื่อทำครบแล้ว ธุรกิจจะมี Custom Audience Library ที่ครอบคลุมทุกจุดของ Funnel พร้อมใช้สร้าง Retargeting Campaign ได้ทันทีใน Part 049 และมี Seed คุณภาพสูง (#5, #10) พร้อมสร้าง Lookalike Audience ใน Part 048

---

## Case Study: ร้านขายอุปกรณ์ตกแต่งบ้านออนไลน์สร้าง Custom Audience Library แล้วลด CPA ลง 45%

ร้าน "HomeDecoTH" (ชื่อสมมติ) ขายของแต่งบ้านออนไลน์ ก่อนหน้านี้ยิงแอดแบบ Prospecting อย่างเดียวมาตลอด 8 เดือน ไม่มี Custom Audience เลยแม้จะติด Pixel ไว้แล้ว CPA เฉลี่ยอยู่ที่ 620 บาทต่อ Purchase (AOV เฉลี่ย 890 บาท ทำให้ Margin บางมาก)

ทีมทำ Workshop แบบ Step 470 สร้าง Custom Audience 10 ตัวครบทุกระดับ Funnel และเริ่มรัน Retargeting Campaign แยกจาก Prospecting โดยแบ่งงบ 70% Prospecting / 30% Retargeting ผลลัพธ์หลัง 4 สัปดาห์:

| กลุ่มแคมเปญ | CPA เฉลี่ย | สัดส่วนยอดขายรวม |
|---|---|---|
| Prospecting (Cold) | 580 บาท | 55% |
| Retargeting Warm (#2, #6, #11) | 290 บาท | 25% |
| Retargeting Hot (#3, #4) | 175 บาท | 20% |

CPA เฉลี่ยรวมทั้งบัญชีลดลงจาก 620 บาท เหลือ 341 บาท (ลดลง 45%) เพราะงบส่วนหนึ่งที่เคยกระจายไปหาลูกค้าใหม่ทั้งหมด ถูกจัดสรรใหม่ไปดึงกลุ่มที่ใกล้ซื้ออยู่แล้วกลับมาปิดการขาย ซึ่งใช้งบน้อยกว่ามากในการได้ Conversion 1 ครั้ง บทเรียนสำคัญคือ การมี Pixel ติดตั้งไว้เฉย ๆ โดยไม่สร้าง Custom Audience ไปใช้จริง เท่ากับเสียโอกาสมหาศาลที่มีอยู่แล้วในมือ

---

## FAQ ที่พบบ่อยเกี่ยวกับ Custom Audience

**Q1: Custom Audience ที่สร้างจาก Pixel กับที่สร้างจาก Customer List อันไหนแม่นยำกว่ากัน**

ทั้งสองแม่นยำในมุมต่างกัน Pixel-based แม่นยำเรื่อง "ความสด" เพราะจับพฤติกรรม Real-time และ Refresh อัตโนมัติ แต่ไม่รู้ว่าใครคือใครจริง ๆ (แค่รู้ Browser/Device ID) ส่วน Customer List แม่นยำเรื่อง "ตัวบุคคล" เพราะมาจากข้อมูลที่ธุรกิจเก็บเองแน่ชัด (Email/Phone ที่ผูกกับ Order จริง) แต่ไม่ Real-time ต้องอัปเดตมือ ธุรกิจที่แข็งแรงควรใช้ทั้งสองแบบผสมกันตามจุดประสงค์ ไม่ใช่เลือกอย่างเดียว

**Q2: ทำไม Custom Audience ที่สร้างไว้ขนาดใหญ่ (เช่น 50,000 คน) ตอนสร้าง แต่พอผ่านไป 2 สัปดาห์ขนาดหดลงเยอะ**

Website Custom Audience เป็น "Rolling Window" คือคนที่เกิน Time Window ที่ตั้งไว้จะหลุดออกจาก Audience โดยอัตโนมัติทุกวัน ถ้าจำนวนคนใหม่ที่เข้ามาต่อวันน้อยกว่าจำนวนคนที่หลุดออกในแต่ละวัน (เช่น เว็บไซต์มี Traffic ลดลงช่วงนั้น) ขนาด Audience โดยรวมจะหดลงเรื่อย ๆ เป็นพฤติกรรมปกติ ไม่ใช่ข้อผิดพลาด แต่ควรตรวจ Traffic ต้นทางว่าลดลงเพราะเหตุใดด้วย

**Q3: สามารถสร้าง Custom Audience จากคนที่ Comment ใต้โพสต์ได้หรือไม่**

ได้ ผ่าน Facebook Page Custom Audience โดยเลือกตัวเลือก "People who engaged with any post or ad" ซึ่งรวมการ Comment, Like, Share, และ Reaction ไว้ในนิยาม Engagement เดียวกัน หากต้องการแยกเฉพาะ Comment ล้วน ๆ ปัจจุบัน Meta ไม่มีตัวกรองละเอียดถึงระดับนั้นในหน้า UI ปกติ ต้องใช้ผ่าน Marketing API ที่ทีม Developer เขียนสคริปต์ดึงเฉพาะ Comment มา Custom Upload เป็น Customer List แทนหากต้องการความละเอียดระดับนั้นจริง ๆ

**Q4: Custom Audience ใช้ได้กับทุก Campaign Objective หรือไม่**

ใช้ได้กับ Objective ส่วนใหญ่ (Traffic, Engagement, Leads, Sales) แต่บาง Objective ที่เน้น Awareness ล้วน ๆ ในบางบัญชีอาจไม่แสดงตัวเลือก Custom Audience ให้ใส่โดยตรงถ้าเลือกใช้ Advantage+ Audience เต็มรูปแบบ ต้องสลับไปที่ Original Audience หรือใส่ Custom Audience เป็น Suggestion แทนตามที่เรียนใน Part 030

**Q5: ถ้าลบ Pixel เดิมแล้วสร้าง Pixel ใหม่ Custom Audience ที่สร้างจาก Pixel เดิมจะยังใช้ได้ไหม**

ไม่ได้ Custom Audience ที่อิง Pixel จะผูกกับ Pixel ID นั้นตลอด ถ้า Pixel ถูกลบหรือไม่มีสิทธิ์เข้าถึงแล้ว Audience จะกลายเป็น Unavailable ทันที และไม่มีทางย้ายไปผูกกับ Pixel ใหม่ได้ ต้องสร้าง Custom Audience ใหม่จาก Pixel ใหม่เท่านั้น นี่คือเหตุผลสำคัญที่ไม่ควรลบ/สร้าง Pixel ใหม่โดยไม่จำเป็น (ทบทวน Part 013)

**Q6: Engagement Custom Audience จาก Instagram ต้องเชื่อม Instagram Business Account ก่อนหรือไม่**

ต้องเชื่อม IG Business/Creator Account เข้ากับ Business Manager ก่อน (ตามที่เรียนใน Part 011) ถ้ายังไม่เชื่อม ตัวเลือก "Instagram Account" จะไม่ปรากฏในหน้าสร้าง Custom Audience หรือปรากฏแต่ไม่มีข้อมูลให้เลือก

## เจาะลึกเพิ่มเติม: ตารางเปรียบเทียบ "ความสด" ของแต่ละแหล่งข้อมูล

การเลือกใช้ Custom Audience ประเภทไหนควรพิจารณาความสดของข้อมูล (Data Freshness) ควบคู่กับความแม่นยำเชิงตัวบุคคล (Identity Certainty) เสมอ ตารางนี้สรุปทั้งสองมิติไว้ให้เทียบง่าย:

| แหล่งข้อมูล | ความสด (Refresh) | ความแม่นยำเชิงตัวบุคคล | เหมาะกับ |
|---|---|---|---|
| Website (Pixel) | สูงมาก (Real-time, Rolling 24-48 ชม.) | ปานกลาง (อิง Browser/Device ID) | Retargeting ระดับ Warm/Hot ที่ต้องเร็ว |
| Engagement (Video/Page/IG) | สูง (Real-time) | ปานกลาง-สูง (ผูกกับ Facebook/IG Account จริง) | Nurture กลุ่มที่ Engage แต่ยังไม่เข้าเว็บ |
| Lead Form | สูง (Real-time) | สูง (มีข้อมูล Contact จริงจากฟอร์ม) | Retarget คนที่เกือบสมัคร/เกือบซื้อ |
| App Activity | สูง (Real-time ถ้า SDK ติดตั้งสมบูรณ์) | ปานกลาง (อิง Device/Advertiser ID) | Re-engagement สำหรับแอป |
| Customer List | ต่ำ (อัปเดตตามรอบที่อัปโหลดมือ/Sync) | สูงมาก (Email/Phone จริงจาก CRM) | Seed คุณภาพสูงสำหรับ Lookalike, Exclusion ระยะยาว |
| Offline Activity | ต่ำ-ปานกลาง (ตามรอบ Sync ของระบบ POS) | สูงมาก (ผูกกับ Transaction จริง) | วัด True ROAS, Exclude ลูกค้าที่ปิดดีลแล้ว |

หลักการที่ควรจำคือ **ยิ่งต้องการ Retarget เร็ว ให้ใช้แหล่งที่ Refresh เร็ว (Website/Engagement) ยิ่งต้องการ Seed คุณภาพสูงสำหรับ Lookalike หรือ Exclusion ระยะยาว ให้ใช้แหล่งที่แม่นยำเชิงตัวบุคคลสูง (Customer List/Offline)** สองมิตินี้ไม่จำเป็นต้องมาคู่กันเสมอ นักยิงแอดที่เข้าใจตารางนี้จะเลือกแหล่งข้อมูลได้ตรงจุดประสงค์มากกว่าใช้แหล่งเดียวกันหมดทุกกรณี

## Checklist ท้ายบท

- [ ] เข้าใจแหล่งข้อมูล Custom Audience ทั้ง 7 ประเภทและรู้ว่าธุรกิจตัวเองมีข้อมูลจากแหล่งไหนบ้าง
- [ ] สร้าง Website Custom Audience อย่างน้อยครอบคลุม 3 ระดับ Funnel (Cold/Warm/Hot) โดยอิง Event ไม่ใช่แค่ URL
- [ ] มีไฟล์ Customer List ที่สะอาด ครบคอลัมน์ (Email, Phone มี Country Code, ชื่อ) และรู้ Match Rate ปัจจุบัน
- [ ] สร้าง Engagement Custom Audience ครอบคลุม Video Views, Page/IG Engagers, และ Lead Form Openers (ถ้ามี)
- [ ] ตรวจสอบว่าธุรกิจมี App Activity หรือ Offline Activity ที่ควรเชื่อมเข้าระบบหรือไม่
- [ ] มี Custom Combination Audience อย่างน้อย 1-2 ตัวที่ใช้ Logic AND/NOT เพื่อความแม่นยำสูงขึ้น
- [ ] ตั้ง Time Window/Exclusion Window ตาม Purchase Cycle จริงของสินค้า ไม่ใช่ค่า Default
- [ ] ตรวจว่า Custom Audience ทุกตัวมีขนาดเกิน Practical Minimum (1,000+ คนสำหรับ Retargeting ทั่วไป)
- [ ] มีปฏิทิน Refresh Customer List ที่ชัดเจน (รายสัปดาห์/รายเดือนตามความเหมาะสม)
- [ ] มี Custom Audience Library ที่ตั้งชื่อเป็นระบบ ครอบคลุมทุกระดับ Funnel พร้อมใช้งานทันที

## Workshop / แบบฝึกหัด

ทำตาม Step 470 กับธุรกิจของตัวเองหรือของลูกค้าจริง โดยส่งมอบผลงาน:

1. **Custom Audience Library เต็มรูปแบบ 10-12 ตัว** สร้างจริงในบัญชี Ads Manager ตาม Naming Convention ที่แนะนำ
2. **ตาราง Funnel Mapping** ที่จัดกลุ่ม Audience ตามระดับ Cold/Warm/Hot/Post-purchase
3. **ตารางบันทึกขนาด (Size) ของทุก Audience** พร้อมระบุว่าตัวไหนต่ำกว่า Practical Minimum และแผนแก้ไข
4. **ปฏิทิน Refresh** สำหรับ Customer List ที่ระบุความถี่และผู้รับผิดชอบชัดเจน

โบนัส: ถ้ามีข้อมูล Offline หรือ App Activity ให้ลองเชื่อมเข้าระบบและสร้าง Custom Audience จากแหล่งเหล่านั้นเพิ่มเติมด้วย

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ปูพื้น Custom Audience ครบทุกแหล่งข้อมูลที่ Meta เปิดให้ใช้ ตั้งแต่ Website, Customer List, Engagement, App Activity, ไปจนถึง Offline Activity พร้อมเทคนิคการรวม Exclude และดูแลรักษาให้สดใหม่อยู่เสมอ Custom Audience ที่สร้างไว้ใน Part นี้จะเป็นวัตถุดิบหลักสำหรับสอง Part ถัดไป — **Part 048 (Lookalike Audience)** ที่จะใช้ Seed คุณภาพสูงอย่าง Purchasers และ High-Value Customers ที่สร้างไว้ ไปขยายเป็น Audience ใหม่ที่มีลักษณะคล้ายกัน และ **Part 049 (Retargeting Funnel)** ที่จะนำ Custom Audience Library ทั้งหมดไปออกแบบเป็นระบบ Retargeting แบบมืออาชีพที่ทำงานอัตโนมัติตลอด Customer Journey

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center: "About Custom Audiences" และ "About Customer List Custom Audiences"
- Meta Business Help Center: "Create an Offline Event Set" สำหรับธุรกิจที่มีข้อมูลหน้าร้าน
- Meta for Developers: เอกสาร Hashing Requirements สำหรับ Customer List API (สำหรับทีม Developer ที่ส่งข้อมูลผ่าน API)
- ทบทวน Part 013-015 (Pixel/CAPI/Events Manager) เพื่อให้แน่ใจว่า Event ที่ใช้สร้าง Custom Audience ถูกต้องแม่นยำ
- ทบทวน Part 007 (PDPA) ก่อนอัปโหลดข้อมูลลูกค้าทุกครั้ง เพื่อความถูกต้องตามกฎหมาย
