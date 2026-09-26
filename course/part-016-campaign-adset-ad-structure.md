# Part 016: Campaign, Ad Set, Ad — โครงสร้าง 3 ชั้นของ Facebook Ads

**Section:** C — Facebook Ads Manager Deep Dive: Setup & Structure
**Step ที่ครอบคลุม:** Step 151–160 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 6–8 ชั่วโมง (รวมการสร้างโครงสร้างแคมเปญ Template จริง)

หลังจากปูพื้นระบบ Tracking ครบใน Part 013–015 มาถึงจุดที่ต้องเข้าใจ "โครงร่าง" ของทุกแคมเปญที่จะสร้างต่อจากนี้ไปตลอดทั้งหลักสูตร Facebook Ads ทุกแคมเปญมีโครงสร้าง 3 ชั้นเสมอ: **Campaign → Ad Set → Ad** ถ้าเข้าใจว่าแต่ละชั้นควบคุมอะไร และตั้งชื่อ/จัดระบบอย่างไรให้ scale ได้ Part นี้จะเป็นกระดูกสันหลังที่ใช้ซ้ำได้กับทุก Objective ในหลักสูตรต่อจากนี้

---

## Steps ที่ครอบคลุมใน Part นี้

1. **ภาพรวมโครงสร้าง Campaign > Ad Set > Ad** — หลักการพื้นฐานว่าทำไมต้องมี 3 ชั้น และแต่ละชั้นสัมพันธ์กันอย่างไร
2. **Campaign Level ตั้งค่าอะไรบ้าง** — Objective, Buying Type, Campaign Budget Optimization, A/B Test
3. **Ad Set Level: Audience, Placement, Budget, Schedule** — ศูนย์กลางของการกำหนดกลุ่มเป้าหมายและงบ
4. **Ad Level: Creative, Copy, Destination, Tracking** — จุดที่ลูกค้าเห็นจริงและเป็นตัวตัดสินผลลัพธ์สุดท้าย
5. **Naming Convention มาตรฐานสำหรับทุกระดับ** — ระบบตั้งชื่อที่ทำให้ทีมงาน/เอเจนซี่ทำงานร่วมกันได้อย่างมีระบบ
6. **จำนวน Ad Set/Ad ที่เหมาะสมต่อ Campaign** — หลักการ Consolidation เพื่อไม่ให้ Learning Phase กระจัดกระจาย
7. **Campaign Budget Optimization vs Ad Set Budget** — ความแตกต่างเชิงกลยุทธ์ที่มีผลต่อการกระจายงบ
8. **การ Duplicate Campaign/Ad Set อย่างมีระบบ** — เทคนิคการทำซ้ำโครงสร้างโดยไม่ทำลาย Learning Phase เดิม
9. **Draft และ Bulk Edit ผ่าน Ads Manager** — เครื่องมือเร่งความเร็วงานสำหรับมืออาชีพที่บริหารหลายแคมเปญ
10. **Workshop: สร้างโครงสร้างแคมเปญมาตรฐาน (Template)** — สร้าง Template ที่ใช้ซ้ำได้กับทุกลูกค้า/ทุกแคมเปญ

---

## Step 151: ภาพรวมโครงสร้าง Campaign > Ad Set > Ad

### ทำไมต้องมี 3 ชั้น ไม่ใช่ชั้นเดียว

Facebook ออกแบบโครงสร้างนี้เพื่อแยกการตัดสินใจออกเป็น 3 ระดับที่มีหน้าที่ต่างกันชัดเจน:

```
Campaign (แคมเปญ)
  └─ กำหนด "เป้าหมายภาพใหญ่" (Objective) และงบรวม (ถ้าใช้ CBO)
      │
      ├─ Ad Set 1 (ชุดโฆษณา)
      │     └─ กำหนด "ใครจะเห็น" (Audience), "เห็นที่ไหน" (Placement),
      │         "งบเท่าไหร่" (Budget), "เมื่อไหร่" (Schedule)
      │         │
      │         ├─ Ad 1 (โฆษณา) → กำหนด "เห็นอะไร" (Creative, Copy, Link)
      │         ├─ Ad 2 (โฆษณา)
      │         └─ Ad 3 (โฆษณา)
      │
      └─ Ad Set 2 (ชุดโฆษณา)
            ├─ Ad 1
            └─ Ad 2
```

### เปรียบเทียบกับโครงสร้างองค์กร (ช่วยจำง่าย)

ถ้านึกภาพไม่ออก ให้เทียบกับโครงสร้างบริษัท: **Campaign** เหมือน "แผนก" ที่มีเป้าหมายใหญ่ (เช่น แผนกขาย), **Ad Set** เหมือน "ทีมงาน" ภายในแผนกที่รับผิดชอบลูกค้ากลุ่มต่างกัน (ทีมลูกค้าใหม่ vs ทีมลูกค้าเก่า), และ **Ad** เหมือน "พนักงานขาย" แต่ละคนที่ใช้วิธีนำเสนอ (Script การขาย) ต่างกันไปในทีมเดียวกัน การเปรียบเทียบนี้ช่วยให้เข้าใจว่าทำไมการตัดสินใจแต่ละชั้นต้องแยกจากกันอย่างมีเหตุผล ไม่ใช่ผสมปนเปกัน

### หลักการง่าย ๆ ที่ต้องจำตลอดหลักสูตร

- **Campaign = ทำไม (Why)** — เราต้องการผลลัพธ์แบบไหน (ยอดขาย, Lead, Traffic)
- **Ad Set = ใคร/ที่ไหน/เท่าไหร่ (Who/Where/How Much)** — กลุ่มเป้าหมาย, ตำแหน่งแสดงผล, งบประมาณ
- **Ad = อะไร (What)** — สิ่งที่ลูกค้าเห็นจริงบนหน้าจอ

### ผลกระทบของโครงสร้างต่อ Machine Learning

จุดที่มือใหม่มักไม่รู้คือ **Learning Phase เกิดขึ้นที่ระดับ Ad Set** ไม่ใช่ระดับ Campaign หรือ Ad ซึ่งหมายความว่า:

- ถ้าสร้าง Ad Set ใหม่ทุกครั้งที่อยากทดสอบอะไร → Learning Phase ต้องเริ่มใหม่ตลอด ข้อมูลไม่สะสม
- ถ้ายัด Audience/Budget ทุกอย่างไว้ใน Ad Set เดียวที่ใหญ่พอ (มี Volume Event เพียงพอ) → Learning Phase มีโอกาสจบเร็วและมีเสถียรภาพมากกว่า

นี่คือเหตุผลที่ Step 156 (จำนวน Ad Set ที่เหมาะสม) และ Step 157 (CBO vs ABO) เป็นเรื่องสำคัญมาก ไม่ใช่แค่เรื่องความสวยงามของโครงสร้าง

### ข้อผิดพลาดที่มือใหม่ทำบ่อยที่สุดในระดับโครงสร้าง

- สร้าง Campaign ใหม่ทุกครั้งที่มีสินค้าใหม่ ทั้งที่ Objective เดียวกัน ทำให้ Business Manager รกไปด้วยแคมเปญเป็นร้อยที่จัดการไม่ได้
- ใส่ Audience ที่ทับซ้อนกันในหลาย Ad Set ของ Campaign เดียวกัน (Audience Overlap) ทำให้ Ad Set แข่งประมูลกันเอง เสียเงินโดยไม่จำเป็น
- ไม่แยกการทดสอบ Creative ออกจากการทดสอบ Audience ทำให้ไม่รู้ว่าผลลัพธ์ที่เปลี่ยนไปมาจากตัวแปรไหน

---

## Step 152: Campaign Level ตั้งค่าอะไรบ้าง

### รายการตั้งค่าทั้งหมดในระดับ Campaign

เมื่อกด **Create** ใน Ads Manager สิ่งที่ต้องตั้งค่าในหน้า Campaign มีดังนี้:

1. **Objective (เป้าหมาย)** — Awareness, Traffic, Engagement, Leads, App Promotion, Sales (รายละเอียดเจาะลึกทุกตัวอยู่ใน Part 017)
2. **Campaign Name** — ชื่อแคมเปญ (ตาม Naming Convention ใน Step 155)
3. **Buying Type** — เลือกระหว่าง **Auction** (แข่งประมูลปกติ ใช้ 99% ของกรณี) หรือ **Reach and Frequency** (ซื้อแบบล็อกราคา/เข้าถึงจำนวนคนที่รู้แน่นอน เหมาะกับ Branding งบใหญ่ที่วางแผนล่วงหน้านาน)
4. **Campaign Budget Optimization (CBO) Toggle** — เปิดหรือปิดการให้ Facebook กระจายงบข้าม Ad Set อัตโนมัติ (เจาะลึกใน Step 157)
5. **A/B Test Toggle** — เปิดใช้ถ้าต้องการทดสอบเปรียบเทียบ Ad Set/Audience/Creative แบบมีนัยสำคัญทางสถิติ (Facebook จะช่วยแบ่งกลุ่มไม่ให้ Audience ปนกัน)
6. **Advantage Campaign Budget** — ชื่อใหม่ของฟีเจอร์ CBO ใน UI เวอร์ชันปัจจุบันที่รวม Automation เพิ่มเติม
7. **Special Ad Category** — ต้องระบุถ้าธุรกิจอยู่ในหมวด Housing, Employment, Credit, หรือ Politics/Social Issues (เจาะลึกใน Part 020 Step 197) ถ้าเลือกผิดหรือไม่ระบุทั้งที่เข้าเงื่อนไข เสี่ยงถูก Reject หรือ Disable บัญชี

### สิ่งที่ Campaign Level "ไม่ได้" ควบคุม

เพื่อไม่ให้สับสน ต้องรู้ด้วยว่า Campaign Level **ไม่ได้กำหนด** เรื่องต่อไปนี้ (เพราะอยู่ชั้นถัดไป): Audience, Placement, Creative, Ad Copy, Destination URL — ทั้งหมดนี้กำหนดที่ Ad Set หรือ Ad Level

### ตัวอย่างการตั้งค่า Campaign จริงสำหรับธุรกิจ e-Commerce

```
Objective: Sales
Campaign Name: FB_Sales_AllProducts_Q3-2026_v1
Buying Type: Auction
Advantage Campaign Budget: เปิดใช้ (CBO)
Campaign Budget: 1,500 บาท/วัน
A/B Test: ปิด (จะทดสอบที่ระดับ Ad Set แทน)
Special Ad Category: ไม่มี (สินค้าทั่วไปไม่เข้าเงื่อนไข)
```

---

## Step 153: Ad Set Level: Audience, Placement, Budget, Schedule

### รายการตั้งค่าหลักในระดับ Ad Set

1. **Conversion Location** — เลือกว่าผลลัพธ์จะเกิดที่ไหน (Website, App, Instant Form, Messenger, Calls) มีผลต่อ Pixel/Event ที่ผูกด้วย
2. **Performance Goal / Optimization Goal** — เลือก Event ที่ต้องการให้ระบบ Optimize หา (เช่น Maximize Conversions, Maximize Value of Conversions)
3. **Pixel/Dataset Selection** — เลือก Pixel ที่จะใช้วัดผล (ต้องเคย Assign ให้ Ad Account ตามที่เรียนใน Part 013)
4. **Conversion Event** — เลือก Event เฉพาะที่จะ Optimize (Purchase, Lead, AddToCart ฯลฯ)
5. **Audience** — Core Audience (Demographics, Interest, Behavior), Custom Audience, Lookalike, หรือ Advantage+ Audience (รายละเอียดเต็มใน Section E)
6. **Placement** — Automatic Placements (แนะนำเริ่มต้น) หรือ Manual Placements (รายละเอียดใน Part 019)
7. **Budget & Schedule** — ถ้าไม่ได้เปิด CBO ที่ Campaign จะตั้งงบที่นี่ (Daily/Lifetime Budget), วันเริ่ม-สิ้นสุด, Ad Scheduling (Dayparting)
8. **Bid Strategy** — Lowest Cost (ค่าเริ่มต้น), Cost Cap, Bid Cap, ROAS Goal (เจาะลึกใน Part 018)

### ความสัมพันธ์ระหว่าง Ad Set กับ Pixel ที่ต้องระวัง

ทุก Ad Set ที่เลือก Conversion Location = Website **ต้องมี Pixel ที่ผูกกับ Domain ที่ Verify แล้ว** ไม่เช่นนั้นจะไม่สามารถเลือก Conversion Event ได้ครบ หรือระบบจะเตือนว่า Event ที่เลือกไม่อยู่ใน Priority Event List ของ Domain นั้น (เชื่อมโยงกับ Part 015 Step 145 โดยตรง)

### ตัวอย่าง Ad Set ที่ตั้งค่าสมบูรณ์

```
Ad Set Name: FB_Sales_Retarget_ATC-NoPurchase-7D_AllPlacement_v1
Conversion Location: Website
Performance Goal: Maximize number of conversions
Pixel: ABC-Cosmetics-MainPixel
Conversion Event: Purchase
Audience: Custom Audience - AddToCart 7 days (ยกเว้น Purchase 7 days)
Placement: Advantage+ Placements (Automatic)
Budget: 500 บาท/วัน (ถ้าไม่ได้เปิด CBO)
Schedule: Run continuously ตั้งแต่วันนี้
Bid Strategy: Highest volume (Lowest Cost)
```

---

## Step 154: Ad Level: Creative, Copy, Destination, Tracking

### รายการตั้งค่าหลักในระดับ Ad

1. **Identity** — เลือก Facebook Page และ Instagram Account ที่จะใช้แสดงเป็นผู้โพสต์โฆษณา
2. **Ad Format** — Single Image/Video, Carousel, Collection, Instant Experience (รายละเอียดเต็มใน Part 042)
3. **Creative Asset** — รูปภาพ/วิดีโอที่อัปโหลด หรือเลือกจาก Existing Post (Boost Post)
4. **Primary Text, Headline, Description** — ข้อความโฆษณาทั้ง 3 ส่วน (เจาะลึกการเขียนใน Part 037–038)
5. **Destination (Website URL / App Deep Link / Instant Form)** — ปลายทางที่คนจะไปหลังคลิก ต้องตรงกับที่ Pixel ติดตั้งไว้
6. **Call to Action (CTA) Button** — เช่น "Shop Now", "Learn More", "Sign Up"
7. **URL Parameters (UTM Tracking)** — ต่อท้าย URL ปลายทางเพื่อ track ผ่าน Google Analytics คู่กัน (เจาะลึกใน Part 089)
8. **Tracking Options เพิ่มเติม** — เปิด/ปิดการส่ง Event ไปที่ Facebook Pixel ยืนยันว่า Pixel ที่เลือกถูกต้องตรงกับ Ad Set

### ตัวอย่างการตั้งค่า URL Parameters ที่ควรทำเป็นมาตรฐาน

```
Website URL: https://mystore.com/product/serum-vitamin-c
URL Parameters: utm_source=facebook&utm_medium=paid&utm_campaign={{campaign.name}}&utm_content={{ad.name}}
```

การใช้ Dynamic Parameter อย่าง `{{campaign.name}}` และ `{{ad.name}}` ทำให้ Facebook ดึงชื่อ Campaign/Ad จริงมาแทนอัตโนมัติในทุกลิงก์ ไม่ต้องพิมพ์ UTM มือทีละ Ad ซึ่งเสี่ยงพิมพ์ผิดหรือลืมใส่

### จุดที่มือใหม่พลาดบ่อยระดับ Ad

- Destination URL ไม่ตรงกับ Domain ที่ Pixel ติดตั้งไว้ (เช่น ลิงก์ไปหน้า Landing Page ใหม่ที่ยังไม่ได้ฝัง Pixel) ทำให้เสีย Data ทั้งแคมเปญ
- ใช้ Creative เดียวกันซ้ำในหลาย Ad ของ Ad Set เดียวกันโดยไม่มีความแตกต่างจริง ทำให้ Facebook เอา Budget ไปแข่งกันเองระหว่าง Ad ที่คล้ายกันเกินไป (ควรมีความแตกต่างที่มีสมมติฐานชัดเจนในแต่ละ Ad)

---

## Step 155: Naming Convention มาตรฐานสำหรับทุกระดับ

### ทำไม Naming Convention สำคัญกว่าที่คิด

เมื่อบริหารมากกว่า 1 แคมเปญ (และแน่นอนว่าเอเจนซี่/นักยิงแอดมืออาชีพต้องบริหารหลายสิบ-หลายร้อยแคมเปญ) การตั้งชื่อที่เป็นระบบทำให้:

- กรองข้อมูลใน Ads Manager ด้วย Search/Filter ได้เร็ว
- ทำ Report ผ่าน Excel/Google Sheets/Looker Studio ได้ง่ายเพราะแยกมิติต่าง ๆ ได้จากชื่อโดยตรง (Breakdown by Naming Pattern)
- ทีมใหม่ที่เข้ามาดูแลต่อเข้าใจโครงสร้างได้ทันทีโดยไม่ต้องเปิดดูการตั้งค่าทีละอัน

### สูตร Naming Convention ที่แนะนำ

**Campaign:**
```
[Platform]_[Objective]_[กลุ่มสินค้า/บริการ]_[ช่วงเวลา]_[version]
```

**Ad Set:**
```
[Platform]_[Objective]_[Audience Type]_[Audience Detail]_[Placement]_[version]
```

**Ad:**
```
[Format]_[Creative Concept]_[Angle/Hook]_[version]
```

### ตารางตัวอย่างจริงที่ใช้งานได้ทันที

| ระดับ | ชื่อตัวอย่าง | อธิบาย |
|---|---|---|
| Campaign | `FB_Conv_Cosmetics_Q3-2026_v1` | Facebook, Conversion Objective, กลุ่มสินค้าเครื่องสำอาง, ไตรมาส 3 ปี 2026, เวอร์ชัน 1 |
| Ad Set | `FB_Conv_Retarget_ATC7D-NoPurchase_AllPlacement_v1` | Retargeting คนใส่ตะกร้า 7 วันที่ยังไม่ซื้อ, ใช้ทุก Placement |
| Ad Set | `FB_Conv_LAL1pct_Purchase180D_Auto_v1` | Lookalike 1% จากคนซื้อ 180 วัน, Auto Placement |
| Ad | `Carousel_BeforeAfter_SkinProblem_v1` | โฆษณาแบบ Carousel, Concept ก่อน-หลัง, Angle ปัญหาผิว |
| Ad | `Video_UGC_Testimonial_RealCustomer_v2` | วิดีโอ UGC, Testimonial จากลูกค้าจริง, เวอร์ชัน 2 |

ตัวอย่างตามที่โจทย์กำหนด: **`FB_Conv_Retarget_18-34_Carousel_v1`** อ่านได้ว่า Facebook, Conversion Objective, กลุ่ม Retargeting, อายุ 18-34 ปี, ใช้ Format Carousel, เวอร์ชันที่ 1 — เป็นชื่อที่กระชับแต่บอกข้อมูลสำคัญครบใน 1 บรรทัดโดยไม่ต้องเปิดดูการตั้งค่าเพิ่ม

### หลักการเรื่อง Version Number (v1, v2, ...)

ให้เพิ่มเลข version ทุกครั้งที่มีการเปลี่ยนแปลงสำคัญ (เปลี่ยน Audience, เปลี่ยน Bid Strategy, Restart Learning Phase) เพื่อให้ Report ย้อนหลังแยกช่วงเวลาที่ผลลัพธ์เปลี่ยนไปได้ชัดเจนว่าเกิดจาก version ไหน ไม่ต้องเดาจาก Timeline อย่างเดียว

---

## Step 156: จำนวน Ad Set/Ad ที่เหมาะสมต่อ Campaign

### หลักการ Consolidation (การรวมศูนย์)

Meta เองแนะนำแนวทาง **Consolidation** มาหลายปีแล้ว คือการ**ลดจำนวน Ad Set ที่ไม่จำเป็นลง** และให้แต่ละ Ad Set มี Volume Event เพียงพอ แทนที่จะแยกย่อยเป็น Ad Set เล็ก ๆ จำนวนมาก (เช่น แยกตามอายุทีละ 5 ปี, แยกตาม Interest ทีละตัว) ซึ่งเป็นวิธีคิดแบบเก่าก่อนยุค Machine Learning ที่ทรงพลัง

### กฎทั่วไปที่แนะนำ (ปรับตามงบจริงของธุรกิจ)

| ขนาดงบรายวัน | จำนวน Ad Set ต่อ Campaign ที่แนะนำ | จำนวน Ad ต่อ Ad Set ที่แนะนำ |
|---|---|---|
| ต่ำกว่า 500 บาท/วัน | 1 Ad Set | 2–3 Ad |
| 500–3,000 บาท/วัน | 1–3 Ad Set | 3–5 Ad |
| 3,000–15,000 บาท/วัน | 3–6 Ad Set | 4–6 Ad |
| สูงกว่า 15,000 บาท/วัน | 5–10+ Ad Set (แยกตามกลยุทธ์ชัดเจน) | 4–6 Ad |

### เหตุผลเชิงเทคนิคที่ต้องจำกัดจำนวน

1. **งบถูกแบ่งย่อยเกินไป** — ถ้ามี 10 Ad Set แต่งบรวมแค่ 500 บาท/วัน แต่ละ Ad Set จะได้งบเฉลี่ยแค่ 50 บาท/วัน ซึ่งน้อยเกินกว่าจะออกจาก Learning Phase ได้เลย (ยิ่งน้อยกว่าเกณฑ์ ~50 Optimization Event/สัปดาห์ที่ Meta แนะนำ)
2. **Audience Overlap ระหว่าง Ad Set** — Ad Set ที่มากเกินไปมักมี Audience ที่ทับซ้อนกันเอง ทำให้ระบบประมูลแข่งกันเองในบัญชีเดียวกัน (Internal Competition) เสียเงินไปกับการแข่งขันที่ไม่มีประโยชน์
3. **ข้อมูลกระจัดกระจาย ไม่สะสมเป็นก้อนใหญ่** — Machine Learning ทำงานดีขึ้นเมื่อมีข้อมูลมากในที่เดียว การแยกย่อยมากเกินไปทำให้แต่ละ Ad Set มีข้อมูลน้อยเกินกว่าจะเรียนรู้ได้แม่นยำ

### ตัวอย่างเปรียบเทียบ: โครงสร้างที่ผิดกับที่ถูกสำหรับงบ 1,000 บาท/วัน

**โครงสร้างที่มักเห็นจากมือใหม่ (ผิดหลักการ):**

```
Campaign: FB_Sales_Product
├─ Ad Set: Age 18-24 Female
├─ Ad Set: Age 25-34 Female
├─ Ad Set: Age 35-44 Female
├─ Ad Set: Interest - Beauty
├─ Ad Set: Interest - Skincare
├─ Ad Set: Interest - Makeup
└─ Ad Set: Lookalike 1%
```
(7 Ad Set แบ่งงบ 1,000 บาท เหลือ Ad Set ละ ~143 บาท/วัน — น้อยเกินกว่าจะออก Learning Phase ได้ดี และ Audience ทับซ้อนกันสูงมากเพราะ Interest ทั้ง 3 ตัวมักเป็นกลุ่มคนคล้ายกัน)

**โครงสร้างที่ถูกหลักการ Consolidation:**

```
Campaign: FB_Sales_Product (CBO เปิด งบ 1,000 บาท/วัน)
├─ Ad Set: Broad Interest (Beauty + Skincare + Makeup รวมกันเป็น Audience เดียวกว้าง ๆ)
└─ Ad Set: Lookalike 1% Purchase
```
(2 Ad Set แต่ละตัวมีโอกาสได้งบเฉลี่ย ~500 บาท/วัน เพียงพอต่อการเรียนรู้ และ Audience ไม่ทับซ้อนกันเองเพราะรวม Interest เป็นกลุ่มกว้างเดียว ปล่อยให้ Machine Learning หาคนที่เหมาะสมภายใน Audience กว้างนั้นเอง)

### เมื่อไหร่ที่ควรแยก Ad Set จริง ๆ (มีเหตุผลเชิงกลยุทธ์)

- แยกตาม **Funnel Stage** ที่ต่างกันชัดเจน (TOF vs Retargeting) เพราะพฤติกรรม Bid/Budget ที่เหมาะสมต่างกันมาก
- แยกตาม **Conversion Location** ที่ต่างกัน (Website vs Instant Form)
- แยกเพื่อทำ **A/B Test ที่มีสมมติฐานชัดเจน** (เช่น ทดสอบ Lookalike 1% vs Interest-based Audience) ไม่ใช่แยกเพราะ "อยากลองดู" แบบไม่มีโครงสร้าง

---

## Step 157: Campaign Budget Optimization vs Ad Set Budget

### นิยามทั้งสองแบบ

- **Campaign Budget Optimization (CBO)** หรือชื่อใหม่ **Advantage Campaign Budget** — ตั้งงบที่ระดับ Campaign เพียงจุดเดียว แล้วให้ Facebook **กระจายงบข้าม Ad Set โดยอัตโนมัติ** ไปยัง Ad Set ที่ทำผลลัพธ์ได้ดีกว่าแบบ Real-time
- **Ad Set Budget Optimization (ABO)** — ตั้งงบแยกทีละ Ad Set เอง ควบคุมเองว่า Ad Set ไหนได้งบเท่าไหร่แน่นอน ไม่ขึ้นกับ Facebook

### ตารางเปรียบเทียบเชิงกลยุทธ์

| มิติ | CBO (Advantage Campaign Budget) | ABO |
|---|---|---|
| ผู้ควบคุมการกระจายงบ | Facebook (อัตโนมัติ) | นักยิงแอด (Manual) |
| เหมาะกับ | Ad Set ที่มีลักษณะคล้ายกัน แข่งกันเพื่อหาตัวที่ดีที่สุด | Ad Set ที่มีความสำคัญต่างกันชัดเจน ต้องการันตีงบขั้นต่ำ |
| ความเสี่ยง | Ad Set ใหม่/เพิ่งเทสอาจไม่ได้งบเลยถ้าแข่งกับ Ad Set เดิมที่ผลดีอยู่แล้ว | ต้องบริหารเองทุก Ad Set อาจไม่ Optimize เท่าที่ Facebook ทำได้ |
| การทดสอบ Audience ใหม่ | ยากกว่า เพราะ Ad Set ใหม่แข่งกับของเดิมที่มีข้อมูลมากกว่า | ง่ายกว่า เพราะการันตีงบให้ Ad Set ทดสอบได้แน่นอน |
| ตัวอย่างการใช้งาน | Campaign ที่มี Ad Set หลายตัวลักษณะคล้ายกัน (Lookalike หลายเปอร์เซ็นต์) | Campaign ที่มี Ad Set สำคัญมาก (Retargeting) ที่ต้องการันตีงบไม่ให้ถูก Auto ตัดลดไปให้ Ad Set อื่น |

### แนวทางเลือกใช้ที่แนะนำในทางปฏิบัติ

- **ใช้ CBO เมื่อ:** Ad Set ทั้งหมดในแคมเปญมีบทบาทคล้ายกัน (เช่น ทดสอบ Interest หลายกลุ่มที่ Funnel Stage เดียวกัน) และต้องการให้ Facebook หาตัวที่ดีที่สุดให้อัตโนมัติ
- **ใช้ ABO เมื่อ:** มี Ad Set ที่มีความสำคัญทางธุรกิจต่างกันชัดเจน (เช่น Retargeting ต้องมีงบขั้นต่ำการันตีเสมอ ไม่ให้ถูกลดเพราะ Ad Set อื่นทำ CPA ดีกว่าในช่วงสั้น ๆ)
- **แนวทางผสม:** หลายเอเจนซี่มืออาชีพใช้ **CBO สำหรับ Prospecting Campaign** (หา Audience ใหม่) และ **ABO สำหรับ Retargeting Campaign** (คุมงบ Retargeting ให้แน่นอนเสมอเพราะมูลค่าต่อคนสูงกว่า)

---

## Step 158: การ Duplicate Campaign/Ad Set อย่างมีระบบ

### ทำไมต้อง Duplicate แทนการสร้างใหม่ทุกครั้ง

การ Duplicate (คลิกขวาที่ Campaign/Ad Set → Duplicate) ช่วยประหยัดเวลาอย่างมากเพราะติดตั้งการตั้งค่าที่ซับซ้อน (Custom Audience, Placement, Pixel) มาให้พร้อมแล้ว ไม่ต้องตั้งใหม่ทุกครั้ง แต่ต้องทำอย่างมีระบบเพื่อไม่ให้เกิดปัญหา

### ขั้นตอน Duplicate ที่ถูกต้อง

1. เลือก Campaign/Ad Set ต้นฉบับ → คลิก **Duplicate**
2. เลือกตำแหน่งปลายทาง: **Same Campaign** (ทำสำเนาไว้ในแคมเปญเดียวกัน) หรือ **New Campaign** (ย้ายไปแคมเปญใหม่)
3. เลือกจำนวนสำเนา (Facebook อนุญาตให้ Duplicate ได้หลายชุดพร้อมกันในครั้งเดียว)
4. **แก้ไขชื่อให้ตรงตาม Naming Convention ทันที** (เพิ่ม version หรือเปลี่ยนรายละเอียดที่ต่างจากต้นฉบับ)
5. ปรับส่วนที่ต้องการเปลี่ยน (เช่น Audience ใหม่, Budget ใหม่) — **ห้ามลืมแก้ไขจนกลายเป็นสำเนาที่ซ้ำกับต้นฉบับเป๊ะโดยไม่ได้ตั้งใจ** เพราะจะทำให้ 2 Ad Set แข่งประมูลกันเอง

### ผลกระทบต่อ Learning Phase เมื่อ Duplicate

Ad Set ที่ Duplicate ออกมาใหม่จะ**เริ่ม Learning Phase ใหม่หมด** ไม่ได้สืบทอดข้อมูลจากต้นฉบับ (แม้จะมีการตั้งค่าเหมือนกันทุกอย่าง) เพราะ Facebook มองเป็น Ad Set ID ใหม่ ดังนั้นการ Duplicate ควรทำเมื่อมีเหตุผลชัดเจน เช่น ต้องการทดสอบ Audience ใหม่ที่มีเหตุผลต่างจากเดิมจริง ๆ ไม่ใช่ Duplicate พร่ำเพรื่อโดยไม่มีจุดประสงค์

### เทคนิคมืออาชีพ: การใช้ Duplicate เพื่อทำ Horizontal Scaling

วิธีที่นักยิงแอดมืออาชีพใช้บ่อยเมื่อต้องการขยายงบ (Scale) โดยไม่รบกวน Ad Set เดิมที่ผลดีอยู่แล้ว (Vertical Scaling เสี่ยง Reset Learning Phase ถ้าปรับงบเปลี่ยนแปลงมากเกิน 20% ในครั้งเดียว) คือ **Duplicate Ad Set เดิมที่ผลดีออกมาเป็นตัวใหม่ แล้วค่อยขยาย Audience หรือเพิ่มงบในตัวใหม่นี้** ปล่อยให้ตัวเดิมวิ่งต่อตามปกติไม่ต้องแก้ไขอะไร วิธีนี้ป้องกันความเสี่ยงจากการรบกวน Ad Set ที่ทำงานดีอยู่แล้ว (รายละเอียดเจาะลึกเรื่อง Scaling เต็มรูปแบบอยู่ใน Part 058)

---

## Step 159: Draft และ Bulk Edit ผ่าน Ads Manager

### Draft Campaign คืออะไร

Ads Manager อนุญาตให้สร้างแคมเปญแบบ **Draft** (บันทึกไว้แต่ยังไม่ Publish จริง) เหมาะสำหรับ:
- เตรียมแคมเปญไว้ล่วงหน้าสำหรับ Campaign ที่มีกำหนดเวลาเปิดตัวชัดเจน (เช่น เปิดตัวสินค้าใหม่วันที่กำหนด)
- ให้ทีม/ลูกค้าตรวจสอบก่อน Approve การ Publish จริง (ลด error จากการรีบเปิดแคมเปญ)

วิธีใช้: ตอนสร้างแคมเปญใหม่ ถ้ายังไม่พร้อม Publish ให้กด **Save Draft** (มุมขวาบน) แทนการกด Publish ระบบจะบันทึกไว้ในแท็บ Drafts ให้กลับมาแก้ไขและ Publish ทีหลังได้

### Bulk Edit คืออะไร ทำงานอย่างไร

ฟีเจอร์ **Bulk Edit** (เลือกหลาย Ad Set/Ad พร้อมกัน → คลิก Edit) ช่วยแก้ไขค่าพร้อมกันหลายรายการโดยไม่ต้องเปิดทีละตัว เช่น:

1. เลือก Ad Set หลายตัวที่ต้องการปรับ Budget พร้อมกัน (ติ๊กเลือกใน checkbox)
2. คลิก **Edit** → เลือก **Budget** → ปรับเป็นค่าใหม่ หรือ **เพิ่ม/ลดเป็นเปอร์เซ็นต์** (เช่น เพิ่มงบทุก Ad Set ที่เลือก 20% พร้อมกันในคลิกเดียว)
3. ระบบจะ Preview การเปลี่ยนแปลงก่อน Apply จริงเสมอ ให้ตรวจสอบให้ดีก่อนกด Publish

### กรณีใช้งาน Bulk Edit ที่มืออาชีพใช้บ่อย

- ปรับ Budget ทุก Ad Set ในบัญชีพร้อมกันช่วง Sale/โปรโมชั่นพิเศษ (เพิ่ม 50% ทุกตัวในคลิกเดียว แทนเข้าไปแก้ทีละ Ad Set)
- Pause Ad Set ที่ CPA สูงเกินเกณฑ์ทั้งหมดพร้อมกันหลัง Filter ตามเงื่อนไข (ใช้คู่กับ Automated Rules ใน Part 063)
- เปลี่ยน Bid Strategy ของหลาย Ad Set พร้อมกันเมื่อมีการเปลี่ยนกลยุทธ์ทั้งบัญชี

### เครื่องมือเสริมที่มืออาชีพใช้คู่กับ Bulk Edit

- **Rules (Automated Rules):** ตั้งกฎอัตโนมัติ เช่น "ถ้า CPA > 300 บาท ให้ Pause Ad Set อัตโนมัติ" ทำงานควบคู่กับ Bulk Edit เพื่อลดงานที่ต้องทำซ้ำ ๆ ทุกวัน (เจาะลึกเต็มรูปแบบใน Part 063)
- **Ads Manager Columns Customization:** ปรับแต่งคอลัมน์ที่แสดง (Columns → Customize Columns) ให้เห็นตัวเลขที่ต้องใช้ตัดสินใจ Bulk Edit ได้ทันทีโดยไม่ต้องสลับหน้าไปมา เช่น จัดกลุ่มคอลัมน์ตาม Performance (CPA, ROAS, CTR) ไว้ติดกัน
- **Save Report Template:** บันทึกชุดคอลัมน์และ Filter ที่ใช้บ่อยไว้เป็น Template เพื่อเรียกกลับมาใช้ได้ทันทีในการรีวิวครั้งต่อไป ไม่ต้องตั้งค่าใหม่ทุกครั้ง

### ข้อควรระวังของ Bulk Edit

การแก้ไขพร้อมกันจำนวนมากเสี่ยงเกิด error ที่ไม่ได้ตั้งใจ (เช่น เผลอเลือก Ad Set ผิดตัวรวมอยู่ใน Bulk Selection) ควรตรวจสอบรายการที่เลือกให้ถูกต้องทุกครั้งก่อนกด Apply และควรมีระบบ Screenshot/Backup ค่าตั้งต้นก่อนทำ Bulk Edit ใหญ่ ๆ เพื่อย้อนกลับได้ถ้าพลาด

---

## Step 160: Workshop — สร้างโครงสร้างแคมเปญมาตรฐาน (Template)

### ภารกิจ: สร้าง Campaign Structure Template สำหรับธุรกิจ e-Commerce

ให้สร้างโครงสร้างสมบูรณ์ (ไม่ต้อง Publish จริงถ้ายังไม่พร้อม ใช้ Save Draft ได้) ตามแผนผังนี้:

```
Campaign: FB_Conv_MainProduct_[เดือน-ปี]_v1
(Objective: Sales, Advantage Campaign Budget: เปิด, งบรวม 1,000 บาท/วัน)

├─ Ad Set 1: FB_Conv_Prospect_LAL1pct-Purchase180D_Auto_v1
│    (Audience: Lookalike 1% จาก Purchase 180 วัน, Placement: Automatic)
│    ├─ Ad: Video_UGC_Testimonial_v1
│    ├─ Ad: Carousel_ProductBenefit_v1
│    └─ Ad: Image_Offer_Discount20_v1
│
├─ Ad Set 2: FB_Conv_Prospect_Interest-SkincareLovers_Auto_v1
│    (Audience: Interest-based กว้าง, Placement: Automatic)
│    ├─ Ad: Video_UGC_Testimonial_v1 (ใช้ครีเอทีฟเดิมทดสอบ Audience ต่าง)
│    └─ Ad: Image_Offer_Discount20_v1
│
└─ Ad Set 3: FB_Conv_Retarget_ATC7D-NoPurchase_Auto_v1
     (Audience: Custom Audience AddToCart 7 วัน ยกเว้น Purchase, Placement: Automatic)
     ├─ Ad: Image_Reminder_CartAbandon_v1
     └─ Ad: Carousel_BestSeller_v1
```

### ขั้นตอนปฏิบัติจริง

1. สร้าง Campaign ตาม Naming Convention ให้ครบทุกฟิลด์ที่เรียนใน Step 152
2. สร้าง Ad Set ทั้ง 3 ตัวตาม Step 153 พร้อมตรวจสอบว่า Pixel/Conversion Event ตั้งถูกต้อง
3. สร้าง Ad อย่างน้อย 2 ตัวต่อ Ad Set ตาม Step 154 (ใช้ Creative ตัวอย่าง/Mockup ได้ถ้ายังไม่มีของจริง)
4. ตรวจสอบ Naming ทุกระดับให้ตรงตาม Convention ที่วางไว้ 100%
5. บันทึกเป็น Draft และถ่าย Screenshot โครงสร้างทั้งหมดเก็บไว้เป็น Template สำหรับใช้ซ้ำกับสินค้าตัวต่อไป

### เกณฑ์ประเมินผลงาน Workshop

- [ ] จำนวน Ad Set ไม่เกิน 3–4 ตัวสำหรับงบระดับเริ่มต้น (ตามตารางใน Step 156)
- [ ] แต่ละ Ad Set มีบทบาทต่างกันชัดเจน ไม่ทับซ้อน Audience กันเอง
- [ ] Naming Convention อ่านแล้วเข้าใจทันทีโดยไม่ต้องเปิดดูการตั้งค่า
- [ ] Ad ในแต่ละ Ad Set มีความแตกต่างที่มีสมมติฐานชัดเจน ไม่ใช่ก็อปวางซ้ำ ๆ

---

## Case Study: เอเจนซี่ที่ลดความยุ่งเหยิงของบัญชีลูกค้าด้วย Naming Convention

เอเจนซี่ขนาดกลางที่ดูแลลูกค้า 8 แบรนด์พร้อมกัน เคยมีปัญหาใหญ่: ทีม Media Buyer 3 คนตั้งชื่อ Campaign/Ad Set ตามใจตัวเอง บางคนใช้ภาษาไทย บางคนใช้อังกฤษ บางคนไม่ใส่วันที่หรือเวอร์ชันเลย ผลคือเมื่อ Media Buyer คนหนึ่งลาออก คนใหม่ที่เข้ามารับงานต่อใช้เวลากว่า 2 สัปดาห์เพื่อทำความเข้าใจว่าแคมเปญไหนทำอะไร กี่สิบแคมเปญที่ยังวิ่งอยู่มีบางตัวที่ไม่มีใครรู้ว่าทำไมถึงเปิดทิ้งไว้

หลังจากนำระบบ Naming Convention ตามที่สอนใน Step 155 มาใช้บังคับทั้งทีม (พร้อมทำ Google Sheets Template สำหรับ Media Buyer กรอกก่อนสร้างแคมเปญทุกครั้ง เพื่อ Generate ชื่อที่ถูกต้องอัตโนมัติ) ผลลัพธ์ที่เห็นได้ชัดภายใน 1 เดือน:

1. เวลา Handover งานระหว่างทีมลดจาก 2 สัปดาห์เหลือ 2 วัน
2. การทำ Report รายเดือนเร็วขึ้นมาก เพราะ Filter/Group ข้อมูลจากชื่อได้ทันทีโดยไม่ต้องเปิดดูการตั้งค่าทีละแคมเปญ
3. พบแคมเปญ "ที่ไม่มีใครรู้ว่าทำไมยังเปิดอยู่" มากถึง 12 แคมเปญที่ไม่มี version/วันที่ระบุ ปิดไปแล้วประหยัดงบที่รั่วไหลได้กว่า 40,000 บาท/เดือน

บทเรียนสำคัญ: **Naming Convention ไม่ใช่เรื่องความสวยงาม แต่เป็นระบบบริหารความเสี่ยงและต้นทุนที่จับต้องได้จริง** โดยเฉพาะเมื่อทีมงานมีมากกว่า 1 คน หรือดูแลมากกว่า 1 บัญชี

---

## คำถามที่พบบ่อย (FAQ) ของ Part นี้

**Q: ถ้าเปิด CBO แล้ว Ad Set ใหม่ที่เพิ่งสร้างจะไม่ได้งบเลยจริงไหม?**
A: มีความเสี่ยงสูงในช่วงแรก เพราะระบบ CBO มักเทงบไปที่ Ad Set ที่มีข้อมูล/ผลลัพธ์ดีอยู่แล้ว ทางแก้คือใช้ **Minimum Budget** ที่ตั้งได้ในแต่ละ Ad Set ภายใน Campaign ที่เปิด CBO (คลิกที่ Ad Set → Edit → Ad Set Spending Limits) เพื่อการันตีว่า Ad Set ใหม่จะได้งบขั้นต่ำสำหรับเก็บข้อมูลก่อนถูกลดเหลือ 0

**Q: Special Ad Category กระทบ Ad Set Level ด้วยไหม หรือแค่ Campaign Level?**
A: กระทบทั้งคู่ — เมื่อเลือก Special Ad Category ที่ Campaign แล้ว ตัวเลือก Targeting บางอย่างที่ Ad Set Level จะถูกจำกัดอัตโนมัติ (เช่น ไม่สามารถ Targeting ตาม Age, Gender, Zip Code แบบละเอียดได้ในหมวด Housing/Employment/Credit) ต้องวางแผน Audience ล่วงหน้าให้สอดคล้องกับข้อจำกัดนี้ (รายละเอียดเต็มอยู่ใน Part 020 Step 197)

**Q: ทำไมบางครั้ง Ad Set ที่ Duplicate มาแล้วไม่มีการเปลี่ยนอะไรเลย กลับได้ผลลัพธ์ต่างจากตัวเดิม?**
A: เพราะ Ad Set ใหม่มี Ad Set ID ใหม่ ทำให้ Learning Phase เริ่มต้นใหม่ทั้งหมด แม้การตั้งค่าจะเหมือนเดิมทุกอย่าง ผลลัพธ์ในช่วง Learning Phase มักผันแปรมากกว่าปกติ ต้องรอให้ผ่าน Learning Phase ก่อนเปรียบเทียบผลลัพธ์อย่างเป็นธรรม

**Q: ควรใส่ Ad กี่ตัวต่อ Ad Set ถ้าใช้ Advantage+ Creative หรือ Dynamic Creative?**
A: ถ้าเปิดใช้ Dynamic Creative (ระบบผสมส่วนประกอบ Creative หลายชิ้นอัตโนมัติ) มักจะใส่แค่ 1 "Ad" ที่มีหลาย Asset ย่อยอยู่ในนั้น (เช่น รูป 5 แบบ, Headline 3 แบบ) แทนการสร้างหลาย Ad แยกกัน เพราะระบบจะทดสอบ Combination เองภายใน Ad เดียว วิธีนี้ต่างจาก Manual Ad Testing ที่สอนใน Step 156 ควรเลือกใช้อย่างใดอย่างหนึ่งให้ชัดเจน ไม่ปนกันจนวิเคราะห์ผลไม่ได้ว่าอะไรทำงานได้ดีจริง

**Q: การเปลี่ยน Bid Strategy ระหว่างที่ Ad Set กำลังวิ่งอยู่ มีผลกระทบอะไรบ้าง?**
A: การเปลี่ยน Bid Strategy (เช่น จาก Lowest Cost เป็น Cost Cap) ถือเป็นการเปลี่ยนแปลงที่ **Significant Edit** ซึ่งจะรีเซ็ต Learning Phase ของ Ad Set นั้นใหม่ทั้งหมด ควรวางแผนก่อนว่าจะใช้ Bid Strategy แบบไหนตั้งแต่ต้น ไม่ใช่เปลี่ยนไปมาบ่อย ๆ ระหว่างแคมเปญกำลังทำผลลัพธ์ดีอยู่

---

## ตารางสรุปการตั้งค่าทั้ง 3 ระดับแบบเทียบเคียง (Quick Reference)

| ระดับ | ตั้งค่าอะไร | ตัวอย่างค่าที่ตั้ง | ใครควบคุม Learning Phase |
|---|---|---|---|
| Campaign | Objective, Buying Type, CBO Toggle, Special Ad Category | Sales, Auction, CBO เปิด | ไม่เกี่ยวข้องตรง (แต่กระทบทางอ้อมผ่านงบที่กระจาย) |
| Ad Set | Audience, Placement, Budget, Pixel, Optimization Goal, Bid Strategy | LAL 1%, Auto Placement, 500 บาท/วัน | **ควบคุมโดยตรง** — Learning Phase เกิดที่นี่ |
| Ad | Creative, Copy, Destination, CTA, UTM | Video UGC, "Shop Now", ลิงก์ /product/serum | ไม่กระทบ Learning Phase โดยตรง แต่กระทบ CTR/Relevance ซึ่งมีผลต่อ Cost |

ตารางนี้ช่วยให้ตัดสินใจได้เร็วเวลาต้องแก้ไขแคมเปญที่กำลังวิ่งอยู่ — ถ้าต้องแก้ไขอะไรที่ระดับ Ad Set (โดยเฉพาะ Audience, Optimization Goal, Bid Strategy) ให้เตรียมใจว่า Learning Phase จะรีเซ็ตใหม่ ส่วนการแก้ไขที่ระดับ Ad (เช่น เปลี่ยนรูปภาพ) มีผลกระทบน้อยกว่ามากในเชิงเทคนิค แม้จะกระทบผลลัพธ์เชิงการตลาดได้เหมือนกัน

---

## Checklist ท้ายบท

- [ ] เข้าใจว่า Campaign, Ad Set, Ad ควบคุมอะไรแต่ละชั้น ไม่สับสนว่าอะไรอยู่ชั้นไหน
- [ ] ตั้งค่า Campaign Level ครบ (Objective, Buying Type, CBO/ABO, Special Ad Category)
- [ ] ตั้งค่า Ad Set Level ครบ (Conversion Location, Pixel, Audience, Placement, Budget)
- [ ] ตั้งค่า Ad Level ครบ (Creative, Copy, Destination URL ตรงกับ Pixel, UTM Parameters)
- [ ] มี Naming Convention ที่เป็นระบบและใช้บังคับกับทุกแคมเปญ ไม่ใช่แค่บางแคมเปญ
- [ ] จำนวน Ad Set ต่อ Campaign เหมาะสมกับขนาดงบ ไม่กระจัดกระจายเกินไป
- [ ] เข้าใจความแตกต่างระหว่าง CBO และ ABO และเลือกใช้ให้ตรงกับสถานการณ์
- [ ] รู้วิธี Duplicate อย่างปลอดภัยโดยไม่ทำให้ Ad Set แข่งประมูลกันเอง
- [ ] ใช้ Draft สำหรับแคมเปญที่ต้องรอ Approve ก่อน Publish
- [ ] รู้จักและเคยใช้ Bulk Edit สำหรับงานที่ต้องแก้ไขหลายรายการพร้อมกัน

---

## Workshop / แบบฝึกหัด

**แบบฝึกหัดที่ 1 — สร้าง Naming Convention ของตัวเอง**
ออกแบบสูตร Naming Convention สำหรับ Campaign/Ad Set/Ad ของธุรกิจ/ลูกค้าที่ดูแลอยู่ (หรือธุรกิจสมมติ) เขียนเป็นเอกสาร 1 หน้าพร้อมตัวอย่างชื่อจริงอย่างน้อย 5 รายการต่อระดับ

**แบบฝึกหัดที่ 2 — วิเคราะห์โครงสร้างที่มีปัญหา**
สมมติว่าได้รับ Ads Manager ของบัญชีที่มี 15 Ad Set ใน campaign เดียว งบรวม 800 บาท/วัน ให้วิเคราะห์ว่าโครงสร้างนี้มีปัญหาอะไร (อ้างอิงหลักการ Consolidation ใน Step 156) และเสนอวิธีจัดโครงสร้างใหม่ให้เหมาะสม

**แบบฝึกหัดที่ 3 — ทำ Template โครงสร้างแคมเปญ**
ทำตาม Workshop ใน Step 160 ให้ครบ พร้อมบันทึก Screenshot และเขียนสรุปว่าทำไมเลือกจำนวน Ad Set/Ad เท่านี้ ไม่มากไม่น้อยไปกว่านี้

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ทำให้เข้าใจ "กระดูกสันหลัง" ของทุกแคมเปญ Facebook Ads อย่างลึกซึ้ง ตั้งแต่หลักการ 3 ชั้น, การตั้งค่าแต่ละระดับอย่างละเอียด, ระบบ Naming Convention ที่ทำให้งานเป็นมืออาชีพ, หลักการ Consolidation ที่ป้องกันการกระจัดกระจายของงบและข้อมูล, ความแตกต่างระหว่าง CBO/ABO, ไปจนถึงเครื่องมือ Duplicate/Draft/Bulk Edit ที่ช่วยให้ทำงานเร็วขึ้นในระดับที่บริหารหลายแคมเปญพร้อมกัน

ทุกอย่างใน Part นี้เป็น "โครงร่างเปล่า" ที่ยังไม่ได้เลือก Objective ที่เหมาะสมกับธุรกิจจริง ๆ Part 017 จะพาไปเจาะลึก Campaign Objectives ทั้งหมดของ Facebook — ตั้งแต่ Awareness ไปจนถึง Sales — ว่าแต่ละตัวเหมาะกับสถานการณ์ไหน และมีความสัมพันธ์กับ Optimization Goal ที่เรียนไปแล้วใน Part นี้อย่างไร ก่อนที่ Section C จะพาไปสร้างแคมเปญจริงทีละ Objective ตั้งแต่ Part 021 เป็นต้นไป

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center: About Campaign Structure — https://www.facebook.com/business/help
- Meta Business Help Center: About Campaign Budget Optimization — https://www.facebook.com/business/help/campaign-budget-optimization
- Meta for Business: Ad Account Structure Best Practices
- Meta Business Help Center: Duplicate Campaigns, Ad Sets and Ads
- Meta Business Help Center: Use Bulk Edit in Ads Manager
