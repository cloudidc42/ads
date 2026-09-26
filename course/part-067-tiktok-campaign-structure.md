# Part 067: โครงสร้างแคมเปญ TikTok (Campaign, Ad Group, Ad)

**Section:** G — TikTok Ads Fundamentals
**Step ที่ครอบคลุม:** Step 661–670 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 6–8 ชั่วโมง (รวมการสร้างโครงสร้างแคมเปญ Template จริงใน TikTok Ads Manager)

เมื่อผ่าน Part 064–066 มาแล้ว (ระบบนิเวศ TikTok Ads, การสร้าง TikTok Ads Manager/Business Center, และ TikTok Pixel/Events API) ขั้นต่อไปที่ต้องเข้าใจให้แม่นก่อนสร้างแคมเปญจริงคือ "โครงร่าง" ของทุกแคมเปญบน TikTok เพราะแม้หน้าตาของ TikTok Ads Manager จะดูคล้าย Facebook Ads Manager มาก แต่มีจุดต่างเชิงโครงสร้างและพฤติกรรมที่ถ้าไม่รู้ จะทำให้คนที่ยิงแอด Facebook เก่งอยู่แล้วพลาดซ้ำ ๆ เมื่อย้ายมายิง TikTok เพราะ "เดา" ว่าเหมือนกันทั้งหมด

Part นี้เขียนขึ้นสำหรับคนที่มีพื้นฐาน Facebook Ads มาก่อน (ตาม Part 016 ของหลักสูตรนี้) จึงจะเทียบเคียงกับ Facebook ตลอดทั้งบทเพื่อให้จำง่ายและเห็นจุดต่างที่ต้องระวังชัดเจน

---

## Steps ที่ครอบคลุมใน Part นี้

1. **ภาพรวมโครงสร้าง 3 ชั้นของ TikTok และการเทียบกับ Facebook** — Campaign > Ad Group > Ad เทียบกับ Campaign > Ad Set > Ad
2. **Campaign Level ตั้งค่าอะไรบ้าง** — Objective, Campaign Type, Budget Mode ที่ระดับแคมเปญ, Campaign Budget เทียบเท่า CBO
3. **Ad Group Level: Targeting, Placement, Budget, Schedule, Bidding** — หัวใจของการกำหนดกลุ่มเป้าหมายและงบ (เทียบเท่า Ad Set ของ Facebook)
4. **Ad Level: Creative, Copy, Destination** — จุดที่ผู้ใช้ TikTok เห็นจริงและตัดสินผลลัพธ์
5. **Naming Convention มาตรฐานสำหรับ TikTok** — ระบบตั้งชื่อที่ปรับจาก Facebook มาใช้กับ TikTok ได้
6. **Simplified Mode vs Custom Mode ใน TikTok Ads Manager** — สองโหมดการสร้างแคมเปญที่ต้องเลือกให้ถูกตั้งแต่ต้น
7. **Smart+ Campaigns — TikTok's Advantage+ เทียบเท่า** — แคมเปญ AI-Driven แบบครบวงจรของ TikTok
8. **จำนวน Ad Group/Ad ที่เหมาะสมต่อ Campaign** — หลัก Consolidation ฉบับ TikTok
9. **ข้อผิดพลาดที่พบบ่อยในการจัดโครงสร้างแคมเปญ TikTok** — โดยเฉพาะจากคนที่ย้ายมาจาก Facebook
10. **Workshop: สร้างโครงสร้างแคมเปญ TikTok มาตรฐาน (Template)** — สร้าง Template ที่ใช้ซ้ำได้กับทุกลูกค้า/สินค้า

---

## Step 661: ภาพรวมโครงสร้าง 3 ชั้นของ TikTok และการเทียบกับ Facebook

### โครงสร้าง 3 ชั้นของ TikTok Ads Manager

TikTok ใช้โครงสร้าง 3 ชั้นเหมือน Facebook แต่เปลี่ยนชื่อชั้นกลางจาก "Ad Set" เป็น **"Ad Group"**:

```
Campaign (แคมเปญ)
  └─ กำหนด "เป้าหมายภาพใหญ่" (Objective), Campaign Type, งบระดับแคมเปญ (ถ้าเลือกตั้งที่นี่)
      │
      ├─ Ad Group 1 (กลุ่มโฆษณา)
      │     └─ กำหนด "ใครจะเห็น" (Targeting), "เห็นที่ไหน" (Placement),
      │         "งบเท่าไหร่" (Budget), "เมื่อไหร่" (Schedule), "ประมูลอย่างไร" (Bid Strategy)
      │         │
      │         ├─ Ad 1 (โฆษณา) → กำหนด "เห็นอะไร" (Creative, Copy, Destination)
      │         ├─ Ad 2 (โฆษณา)
      │         └─ Ad 3 (โฆษณา)
      │
      └─ Ad Group 2 (กลุ่มโฆษณา)
            ├─ Ad 1
            └─ Ad 2
```

### ตารางเทียบศัพท์ TikTok ↔ Facebook แบบละเอียด

| แนวคิด | Facebook | TikTok | หมายเหตุความต่าง |
|---|---|---|---|
| ชั้นบนสุด | Campaign | Campaign | ชื่อเหมือนกัน หน้าที่คล้ายกัน |
| ชั้นกลาง | Ad Set | **Ad Group** | ชื่อต่างกัน แต่หน้าที่ (Targeting/Budget/Schedule/Bid) เหมือนกันเป็นส่วนใหญ่ |
| ชั้นล่างสุด | Ad | Ad | ชื่อเหมือนกัน |
| CBO | Campaign Budget Optimization / Advantage Campaign Budget | **Campaign Budget** (ติ๊ก "Enable Campaign Budget Optimization" หรือใน UI ใหม่คือเลือก Budget ที่ระดับ Campaign) | หลักการเดียวกัน แต่ TikTok เรียกสั้นกว่าและอยู่ตำแหน่งต่างในหน้าจอ |
| Learning Phase | เกิดที่ Ad Set | เกิดที่ **Ad Group** | เข้าใจผิดบ่อยว่า TikTok ไม่มี Learning Phase — มีเหมือนกัน แต่เกณฑ์ Event ต่อสัปดาห์ต่างกัน |
| Auto Optimization ระดับ Creative | Advantage+ Creative / Dynamic Creative | **Smart Creative** / Automated Creative Optimization (ACO) | แนวคิดคล้ายกันมาก คือให้ระบบผสม Asset อัตโนมัติ |
| แคมเปญ AI ครบวงจร | Advantage+ Shopping / Advantage+ Audience | **Smart+ Campaigns** | เทียบเท่ากันโดยตรง อธิบายเจาะลึกใน Step 667 |
| Reach & Frequency Buying | Reach and Frequency | Reach & Frequency (มีใน TikTok เช่นกัน แต่เงื่อนไขงบขั้นต่ำสูงกว่า) | เหมาะกับ Branding งบใหญ่เหมือนกัน |

### หลักการง่าย ๆ ที่ต้องจำ (เหมือน Facebook แต่เปลี่ยนชื่อชั้นกลาง)

- **Campaign = ทำไม (Why)** — Objective ที่ต้องการ (Reach, Traffic, Conversion ฯลฯ)
- **Ad Group = ใคร/ที่ไหน/เท่าไหร่/เมื่อไหร่/ประมูลยังไง (Who/Where/How Much/When/How)** — นี่คือจุดที่ TikTok รวมเรื่อง Targeting + Budget + Schedule + Bid ไว้ในชั้นเดียวเหมือน Facebook Ad Set แทบทุกอย่าง
- **Ad = อะไร (What)** — สิ่งที่ผู้ใช้ TikTok เห็นจริงบนหน้าฟีด (For You Page)

### ทำไมชื่อ "Ad Group" (ไม่ใช่ "Ad Set") ถึงสำคัญที่ต้องรู้

ความต่างของชื่อดูเหมือนเรื่องเล็ก แต่ในทางปฏิบัติทำให้คนที่คุ้นกับ Facebook สับสนเวลาอ่าน Documentation ของ TikTok หรือคุยกับทีม Media Buyer ที่ชินกับศัพท์ TikTok อยู่แล้ว ควรฝึกใช้คำว่า "Ad Group" ให้เป็นธรรมชาติตั้งแต่ต้น ไม่แปลเป็น "Ad Set" ในใจตลอดเวลา เพราะจะสับสนตอนอ่าน Error Message หรือ API Documentation ของ TikTok Marketing API ที่ใช้คำว่า `adgroup_id` ตรง ๆ

### ผลกระทบของโครงสร้างต่อ Machine Learning (TikTok)

เหมือนกับ Facebook, **Learning Phase ของ TikTok เกิดขึ้นที่ระดับ Ad Group** ไม่ใช่ Campaign หรือ Ad ซึ่งหมายความว่า:

- สร้าง Ad Group ใหม่ทุกครั้งที่อยากทดสอบอะไร → Learning Phase เริ่มใหม่ทุกครั้ง ข้อมูลไม่สะสม
- รวม Targeting ที่กว้างพอไว้ใน Ad Group เดียวที่มี Volume Event เพียงพอ → มีโอกาสผ่าน Learning Phase (TikTok เรียกสถานะนี้ว่า **"Learning"** ที่แสดงในคอลัมน์ Delivery Status เหมือนกัน) ได้เร็วและมีเสถียรภาพกว่า

TikTok แนะนำ Event ขั้นต่ำประมาณ **50 Optimization Event ต่อสัปดาห์ต่อ Ad Group** เพื่อให้ระบบเรียนรู้ได้ดี ซึ่งเป็นเกณฑ์เดียวกันในเชิงแนวคิดกับที่ Facebook ใช้ (Facebook ก็แนะนำ ~50 Event/สัปดาห์/Ad Set เช่นกัน) — นี่คือจุดหนึ่งที่สองแพลตฟอร์มคล้ายกันมาก ต่างจากที่หลายคนเข้าใจผิดว่า TikTok "ไม่ต้องมี Data มากก็ Optimize ได้ดี"

### ตำแหน่งของ Business Center ในภาพรวมทั้งหมด

ก่อนเข้าโครงสร้าง 3 ชั้น ต้องเข้าใจว่า TikTok มีชั้นบนสุดที่ครอบทุกอย่างอยู่อีกชั้นคือ **Business Center** (เทียบเท่า Business Manager ของ Facebook ตามที่เรียนใน Part 011) ซึ่งภายใน Business Center หนึ่งบัญชีสามารถมี **Ad Account** ได้หลายบัญชี และในแต่ละ Ad Account จึงมีโครงสร้าง Campaign > Ad Group > Ad ซ้อนอยู่ข้างในอีกที เช่นเดียวกับที่ Business Manager ของ Facebook ครอบ Ad Account ไว้หลายบัญชี ลำดับชั้นแบบเต็มจึงเป็น:

```
Business Center
  └─ Ad Account 1
        └─ Campaign
              └─ Ad Group
                    └─ Ad
  └─ Ad Account 2
        └─ Campaign
              └─ ...
```

การเข้าใจลำดับนี้สำคัญเวลาต้อง Troubleshoot ปัญหา เพราะบางครั้งปัญหาที่ดูเหมือนเป็นเรื่องโครงสร้างแคมเปญ จริง ๆ แล้วเป็นปัญหาที่ระดับ Ad Account หรือ Business Center (เช่น Pixel ที่ Assign ผิด Ad Account, สิทธิ์การเข้าถึงที่ไม่ครบ) ซึ่งรายละเอียดเต็มรูปแบบอยู่ใน Part 065

### ข้อผิดพลาดที่มือใหม่ (และคนย้ายจาก Facebook) ทำบ่อยที่สุด

- คิดว่า Ad Group เท่ากับ Ad Set ทุกกระเบียดนิ้ว แล้ว Copy พฤติกรรมการสร้างโครงสร้างจาก Facebook มาตรง ๆ โดยไม่เช็คตัวเลือกที่ TikTok มีต่างออกไป (เช่น Placement, Bid Strategy ที่ชื่อไม่เหมือนกัน)
- สร้าง Campaign ใหม่ทุกครั้งที่มีสินค้าใหม่ ทั้งที่ Objective เดียวกัน ทำให้ Business Center รกเหมือนปัญหาที่เคยเกิดกับ Business Manager ของ Facebook
- ไม่รู้ว่า TikTok มี Smart+ Campaigns เป็นโหมดพิเศษที่ "ข้าม" โครงสร้าง 3 ชั้นแบบเดิมบางส่วน (อธิบายใน Step 667) ทำให้เลือกโหมดผิดตั้งแต่ต้น

---

## Step 662: Campaign Level ตั้งค่าอะไรบ้าง

### รายการตั้งค่าทั้งหมดในระดับ Campaign

เมื่อกด **Create** ใน TikTok Ads Manager สิ่งที่ต้องตั้งค่าในหน้า Campaign มีดังนี้:

1. **Campaign Objective (เป้าหมาย)** — Awareness (Reach), Consideration (Traffic, App Install, Lead Generation, Community Interaction, Video Views), Conversion (Website Conversion, App Conversion, Product Sales) — รายละเอียดเจาะลึกทุกตัวอยู่ใน Part 068
2. **Campaign Name** — ชื่อแคมเปญ (ตาม Naming Convention ใน Step 665)
3. **Campaign Type** — เลือกระหว่าง **Regular** (สร้างเองทีละชั้นแบบดั้งเดิม) หรือ **Smart+ Campaign** (ให้ AI จัดการ Targeting/Bid/Creative อัตโนมัติเกือบทั้งหมด — เจาะลึกใน Step 667)
4. **Campaign Budget Toggle** — เปิดหรือปิดการตั้งงบที่ระดับ Campaign (เทียบเท่า CBO ของ Facebook) โดยถ้าเปิด TikTok จะกระจายงบข้าม Ad Group อัตโนมัติไปยัง Ad Group ที่ทำผลลัพธ์ได้ดีกว่า
5. **Budget Mode ที่ระดับ Campaign** — ถ้าเปิด Campaign Budget จะเลือกได้ระหว่าง **Daily Budget** และ **Total Budget** (เทียบเท่า Lifetime Budget ของ Facebook) — รายละเอียดเจาะลึกอยู่ใน Part 069
6. **Split Test** — ฟีเจอร์ A/B Test ของ TikTok เทียบเท่า Facebook A/B Test Tool ใช้เปรียบเทียบ Targeting/Bid Strategy/Creative แบบมีนัยสำคัญทางสถิติ
7. **Industry/Category Certification** — สำหรับสินค้าบางหมวด (การเงิน, สุขภาพ, การเมือง) TikTok อาจขอให้ระบุ/ยืนยันหมวดธุรกิจตั้งแต่ระดับ Campaign เพื่อคัดกรอง Policy ที่เกี่ยวข้อง

### เมนูที่ต้องหาให้เจอในหน้าจอจริง (ปี 2026)

ใน UI ปัจจุบันของ TikTok Ads Manager หน้า Create Campaign จะให้เลือก Campaign Objective เป็นการ์ดก่อน (คล้าย Facebook) จากนั้นจะมีตัวเลือก **"Advertising Type"** ให้เลือกระหว่าง Regular หรือ Smart+ อยู่ใต้ Objective ทันที ควรตรวจสอบให้แน่ใจว่าเลือก **Regular** ถ้าต้องการควบคุมโครงสร้างแบบละเอียดตามที่เรียนใน Part นี้ ไม่เผลอไปเลือก Smart+ โดยไม่ตั้งใจ เพราะ Smart+ จะซ่อนตัวเลือก Ad Group และ Targeting แบบละเอียดไปเกือบทั้งหมด

### สิ่งที่ Campaign Level "ไม่ได้" ควบคุม

Campaign Level **ไม่ได้กำหนด**: Targeting/Audience, Placement, Creative, Ad Copy, Destination URL — ทั้งหมดนี้กำหนดที่ Ad Group หรือ Ad Level เหมือนหลักการเดียวกับ Facebook

### ตัวอย่างการตั้งค่า Campaign จริงสำหรับธุรกิจ e-Commerce บน TikTok

```
Campaign Objective: Product Sales (Conversion)
Campaign Name: TT_Conv_AllProducts_Q3-2026_v1
Advertising Type: Regular
Campaign Budget: เปิดใช้ (เทียบเท่า CBO)
Budget Mode: Daily Budget 1,500 บาท/วัน
Split Test: ปิด (จะทดสอบที่ระดับ Ad Group แทน)
```

### จุดต่างสำคัญจาก Facebook ที่ต้องระวังตรง Campaign Level

TikTok ไม่มีแนวคิด "Special Ad Category" แบบ Facebook (Housing/Employment/Credit/Politics) ในรูปแบบเดียวกันเป๊ะ แต่มีนโยบายเฉพาะหมวดที่เข้มงวดมาก (เช่น การเงิน, สุขภาพ, ความงาม, การเมือง/สังคม) ที่ต้องทำ Certification หรือขออนุญาตล่วงหน้าก่อนยิงแอด ซึ่งรายละเอียดเต็มรูปแบบจะอยู่ใน Part 071 (TikTok Ad Policies) — ณ ขั้นตอนสร้าง Campaign ควรรู้ล่วงหน้าว่าธุรกิจตัวเองเข้าเงื่อนไขหมวดพิเศษหรือไม่ ก่อนเสียเวลาตั้งค่าทั้งโครงสร้างแล้วมาติดปัญหา Policy ทีหลัง

---

## Step 663: Ad Group Level — Targeting, Placement, Budget, Schedule, Bidding

### รายการตั้งค่าหลักในระดับ Ad Group

Ad Group คือชั้นที่ "อัดแน่น" ที่สุดของ TikTok เพราะรวมเรื่อง Targeting, Placement, Budget, Schedule และ Bid Strategy ไว้ในหน้าเดียวกันทั้งหมด (คล้าย Ad Set ของ Facebook มาก):

1. **Promotion Type** — เลือกว่าจะโปรโมทอะไร (Website, App, TikTok Shop, Lead Generation Form) มีผลต่อ Pixel/Event ที่ผูกด้วย เทียบเท่า Conversion Location ของ Facebook
2. **Placement** — เลือกระหว่าง **Automatic Placement** (TikTok เลือกให้เอง กระจายไปทั้ง TikTok, Pangle Audience Network) หรือ **Select Placement** (เลือกเอง เช่น TikTok only) — รายละเอียดเต็มอยู่ใน Part 070
3. **Targeting** — Demographics (Age, Gender, Location, Language), Interest & Behavior, Custom Audience, Lookalike Audience — รายละเอียดเต็มใน Section I (Part 083)
4. **Budget & Schedule** — ถ้าไม่ได้เปิด Campaign Budget จะตั้งงบที่นี่ (Daily/Total Budget), วันเริ่ม-สิ้นสุด, Dayparting (Ad Scheduling) — เจาะลึกใน Part 069
5. **Optimization Goal** — เลือก Event ที่ต้องการให้ระบบ Optimize หา (Click, Conversion, Value, Reach) — เจาะลึกใน Part 069
6. **Bid Strategy** — Lowest Cost (ค่าเริ่มต้น), Cost Cap, Bid Cap — เจาะลึกใน Part 069
7. **Pixel/App Events Selection** — เลือก Pixel หรือ App Events API ที่จะใช้วัดผล (ต้อง Assign ไว้แล้วตามที่เรียนใน Part 066)
8. **Frequency Cap** — ตั้งจำนวนครั้งสูงสุดที่คนหนึ่งจะเห็นโฆษณาในช่วงเวลาที่กำหนด (TikTok เปิดให้ตั้งค่านี้ตรงในหน้า Ad Group ชัดเจนกว่า Facebook ที่ซ่อนอยู่ลึกกว่า)

### ความสัมพันธ์ระหว่าง Ad Group กับ Pixel ที่ต้องระวัง

ทุก Ad Group ที่เลือก Promotion Type = Website **ต้องมี Pixel ที่ Verify Domain แล้ว** ไม่เช่นนั้นจะเลือก Optimization Event ได้ไม่ครบ หรือระบบเตือนว่า Event ที่เลือกยังไม่มีข้อมูลเพียงพอ (เชื่อมโยงกับ Part 066 โดยตรง)

### ความสัมพันธ์ระหว่าง Optimization Goal และ Bid Strategy ที่มักสับสน (เหมือน Facebook)

เหมือนที่เคยเรียนใน Part 016/018 ของ Facebook: "Optimization Goal" บอกว่าต้องการให้ระบบ Optimize เพื่อผลลัพธ์อะไร ส่วน "Bid Strategy" บอกว่าจะประมูลอย่างไรเพื่อให้ได้ผลลัพธ์นั้น ตัวอย่าง: Optimization Goal = "Conversion" บอกว่าต้องการ Conversion ให้มากที่สุด ส่วน Bid Strategy = "Cost Cap" บอกว่ายอมจ่ายได้ไม่เกินราคาเท่าไหร่ต่อ Conversion หนึ่งครั้ง ถ้าตั้ง Cost Cap ต่ำเกินไปเทียบกับตลาดจริง ระบบอาจใช้งบไม่หมดเพราะหาคนในราคานั้นไม่ได้เพียงพอ

### ตัวอย่าง Ad Group ที่ตั้งค่าสมบูรณ์

```
Ad Group Name: TT_Conv_Retarget_ATC7D-NoPurchase_AutoPlacement_v1
Promotion Type: Website
Placement: Automatic Placement
Pixel: ABC-Cosmetics-TikTokPixel
Optimization Goal: Conversion (Complete Payment)
Targeting: Custom Audience - AddToCart 7 days (ยกเว้น Purchase 7 days)
Budget: 500 บาท/วัน (ถ้าไม่ได้เปิด Campaign Budget)
Schedule: Run continuously ตั้งแต่วันนี้
Bid Strategy: Lowest Cost (No Cap)
Frequency Cap: ไม่เกิน 3 ครั้ง/คน/7 วัน
```

### จุดต่างที่สำคัญจาก Facebook Ad Set

- TikTok มีตัวเลือก **"Comment"**, **"Video Download"**, **"Share"** ที่ระดับ Ad Group ให้เปิด/ปิดได้ตรง ๆ (ควบคุมว่าคนดูจะ Comment/ดาวน์โหลด/แชร์วิดีโอโฆษณาได้หรือไม่) ซึ่ง Facebook ไม่มีตัวเลือกลักษณะนี้ในระดับเดียวกัน
- TikTok มี **Pixel Category "Delivery Type"** ที่ให้เลือก Standard หรือ Accelerated Delivery ตรงในหน้า Ad Group (เจาะลึกใน Part 069 Step 687) ซึ่งเป็นแนวคิดที่ Facebook ซ่อนอยู่ในเมนู Bid Strategy แทน

### Ad Group สำหรับ TikTok Shop โดยเฉพาะ

ถ้า Promotion Type ที่เลือกเป็น **TikTok Shop** (ไม่ใช่ Website ทั่วไป) หน้า Ad Group จะเปลี่ยนตัวเลือกบางส่วนไปโดยอัตโนมัติ:

- ตัวเลือก Pixel จะถูกแทนที่ด้วยการเชื่อม **TikTok Shop Catalog** โดยตรง ไม่ต้องพึ่ง Pixel Event แบบ Website
- Optimization Goal จะเปลี่ยนมาเป็นตัวเลือกเฉพาะ เช่น **Complete Payment (in TikTok Shop)** หรือ **GMV (Gross Merchandise Value)**
- มีตัวเลือก **Product Selection** เพิ่มเข้ามาในระดับ Ad Group เพื่อเลือกว่าจะโปรโมทสินค้าตัวไหนหรือทั้ง Catalog

รายละเอียดเชิงลึกของ TikTok Shop Ads ทั้งหมด (รวม GMV Max) จะอยู่ใน Part 072 และ Part 076 — ใน Part นี้ให้จำไว้ก่อนว่าโครงสร้าง Ad Group จะปรับเปลี่ยนหน้าตาตาม Promotion Type ที่เลือกไว้ตั้งแต่ต้น

---

## Step 664: Ad Level — Creative, Copy, Destination

### รายการตั้งค่าหลักในระดับ Ad

1. **Identity** — เลือก TikTok Account/Business Account ที่จะใช้แสดงเป็นผู้โพสต์โฆษณา (เทียบเท่า Facebook Page/IG Account selection)
2. **Ad Format** — Single Video, Single Image (บาง Placement), Carousel, Spark Ads (Boost วิดีโอ Organic ของ Creator/แบรนด์) — รายละเอียดเต็มใน Part 070 และ Part 077
3. **Creative Asset** — วิดีโอ/ภาพที่อัปโหลด หรือเลือกจาก TikTok Creative Center Library
4. **Ad Text (Copy)** — ข้อความโฆษณาสั้น ๆ ที่แสดงเหนือ CTA Button (สั้นกว่า Primary Text ของ Facebook มาก — จำกัดประมาณ 100 ตัวอักษร)
5. **Destination (Website URL / App Deep Link / TikTok Shop Product Page / Instant Form)** — ปลายทางที่คนจะไปหลังคลิก ต้องตรงกับที่ Pixel ติดตั้งไว้
6. **Call to Action (CTA) Button** — เช่น "Shop Now", "Learn More", "Download Now", "Sign Up"
7. **URL Parameters (UTM Tracking)** — ต่อท้าย URL ปลายทางเพื่อ track ผ่าน Google Analytics คู่กัน (เจาะลึกใน Part 089)
8. **Sound On/Off Default & Caption** — TikTok เปิดให้ควบคุมว่าวิดีโอจะเริ่มมีเสียงหรือปิดเสียงเป็นค่าเริ่มต้น และเพิ่ม Caption อัตโนมัติได้ตรงจากหน้า Ad Level เลย

### ตัวอย่างการตั้งค่า URL Parameters ที่ควรทำเป็นมาตรฐาน

```
Website URL: https://mystore.com/product/serum-vitamin-c
URL Parameters: utm_source=tiktok&utm_medium=paid&utm_campaign=__CAMPAIGN_NAME__&utm_content=__AID__
```

TikTok มีระบบ Dynamic Parameter ของตัวเองที่ใช้ Syntax ต่างจาก Facebook (Facebook ใช้ `{{campaign.name}}` ส่วน TikTok ใช้ตัวแปรเฉพาะ เช่น `__CAMPAIGN_ID__`, `__AID__`, `__CID__` — ต้องเช็ค Documentation ปัจจุบันของ TikTok เสมอเพราะชื่อ Parameter อาจเปลี่ยนตาม Version ของ UI) การใช้ Dynamic Parameter ทำให้ไม่ต้องพิมพ์ UTM มือทีละ Ad ซึ่งเสี่ยงพิมพ์ผิด

### ความต่างสำคัญของ Ad Level: TikTok เน้น "1 Ad = 1 Video" มากกว่า Facebook

Facebook เปิดให้ 1 Ad มีหลาย Asset ผสมกันได้ผ่าน Dynamic Creative แต่ TikTok โดยธรรมชาติของ Native Content เน้นให้แต่ละ Ad ผูกกับวิดีโอ 1 ตัวที่สมบูรณ์ในตัวเอง (แม้จะมี Automated Creative Optimization ที่ผสม Text/CTA ได้บ้าง) ทำให้จำนวน Ad ต่อ Ad Group ของ TikTok มักน้อยกว่าจำนวน Creative Concept ที่ต้องทดสอบจริง เพราะแต่ละ Concept ต้องทำเป็นวิดีโอเต็มรูปแบบ ไม่ใช่แค่สลับรูปภาพเหมือน Facebook Carousel

### จุดที่มือใหม่พลาดบ่อยระดับ Ad

- Destination URL ไม่ตรงกับ Domain ที่ Pixel ติดตั้งไว้ ทำให้เสีย Data ทั้งแคมเปญ (ปัญหาเดียวกับ Facebook)
- อัปโหลดวิดีโอที่ตัดมาจาก Facebook Ads โดยตรง (สัดส่วนภาพ 1:1 หรือ 16:9, มี Watermark ของแพลตฟอร์มอื่น, จังหวะตัดต่อแบบโฆษณาทีวี) โดยไม่ปรับให้เป็น Native TikTok Content (แนวตั้ง 9:16, จังหวะเร็ว, ไม่มี Watermark แพลตฟอร์มอื่น) ทำให้ผลลัพธ์แย่กว่าที่ควรจะเป็นมาก แม้ Targeting/Budget จะตั้งถูกทุกอย่าง

---

## Step 665: Naming Convention มาตรฐานสำหรับ TikTok

### ทำไม Naming Convention สำคัญกว่าที่คิด (เช่นเดียวกับ Facebook)

หลักการเหมือนที่เรียนใน Part 016 ทุกประการ: ช่วยกรองข้อมูลเร็ว, ทำ Report ง่าย, Handover งานได้ไว — เพียงแต่ TikTok มีข้อจำกัดความยาวชื่อและอักขระบางตัวที่ต่างจาก Facebook เล็กน้อย ต้องปรับสูตรให้เหมาะสม

### สูตร Naming Convention ที่แนะนำสำหรับ TikTok

**Campaign:**
```
[Platform]_[Objective]_[กลุ่มสินค้า/บริการ]_[ช่วงเวลา]_[version]
```

**Ad Group:**
```
[Platform]_[Objective]_[Targeting Type]_[Targeting Detail]_[Placement]_[version]
```

**Ad:**
```
[Format]_[Creative Concept]_[Angle/Hook]_[version]
```

(โครงสร้างสูตรเหมือน Facebook เพื่อให้ทีมที่ทำงานทั้งสองแพลตฟอร์มจำได้ง่าย เปลี่ยนแค่ Prefix Platform จาก `FB_` เป็น `TT_`)

### ตารางตัวอย่างจริงที่ใช้งานได้ทันที

| ระดับ | ชื่อตัวอย่าง | อธิบาย |
|---|---|---|
| Campaign | `TT_Conv_Cosmetics_Q3-2026_v1` | TikTok, Conversion Objective, กลุ่มสินค้าเครื่องสำอาง, ไตรมาส 3 ปี 2026, เวอร์ชัน 1 |
| Ad Group | `TT_Conv_Retarget_ATC7D-NoPurchase_AutoPlacement_v1` | Retargeting คนใส่ตะกร้า 7 วันที่ยังไม่ซื้อ, ใช้ Automatic Placement |
| Ad Group | `TT_Conv_LAL1pct_Purchase180D_TikTokOnly_v1` | Lookalike 1% จากคนซื้อ 180 วัน, จำกัด Placement เฉพาะ TikTok |
| Ad | `Video_UGC_UnboxingReview_v1` | วิดีโอ UGC, Concept Unboxing/Review |
| Ad | `Video_TrendSound_BeforeAfter_v2` | วิดีโอใช้เสียงเทรนด์, Concept ก่อน-หลัง, เวอร์ชัน 2 |

### หลักการเสริมเฉพาะ TikTok: ระบุ "แหล่ง Creative" ในชื่อ Ad ด้วย

เพราะ TikTok มี Ad มาจากหลายแหล่งต่างกันมาก (ถ่ายเอง, ซื้อจาก Creator Marketplace, Boost จาก Spark Ads) การเพิ่ม Tag แหล่งที่มาในชื่อ Ad ช่วยให้ Report แยกได้ว่า Creator/Content แบบไหนทำผลลัพธ์ดีที่สุด เช่น `Spark_CreatorXYZ_UnboxingReview_v1` บอกทันทีว่าเป็น Spark Ad จาก Creator ชื่อ XYZ

### หลักการเรื่อง Version Number (v1, v2, ...)

เหมือน Facebook: เพิ่มเลข version ทุกครั้งที่มีการเปลี่ยนแปลงสำคัญ (เปลี่ยน Targeting, เปลี่ยน Bid Strategy, Restart Learning) เพื่อให้ Report ย้อนหลังแยกช่วงเวลาที่ผลลัพธ์เปลี่ยนไปได้ชัดเจน

### ข้อจำกัดความยาวชื่อและอักขระที่ควรรู้

TikTok Ads Manager จำกัดความยาวชื่อ Campaign/Ad Group/Ad ไว้ที่ประมาณ 512 ตัวอักษร (มากกว่า Facebook มาก) แต่ในทางปฏิบัติไม่ควรตั้งชื่อยาวเกินความจำเป็นเพราะจะอ่านยากในหน้า Ads Manager ที่แสดงผลแบบตาราง ควรจำกัดตัวเองไว้ที่ไม่เกิน 60–70 ตัวอักษรต่อชื่อเหมือนที่แนะนำสำหรับ Facebook เช่นเดียวกัน และหลีกเลี่ยงอักขระพิเศษ เช่น `emoji`, `#`, `%` ที่บางระบบ Export ไปยัง Excel/Google Sheets หรือส่งผ่าน TikTok Marketing API อาจตีความผิดพลาดได้

---

## Step 666: Simplified Mode vs Custom Mode ใน TikTok Ads Manager

### สองโหมดหลักของการสร้างแคมเปญบน TikTok

TikTok Ads Manager มีสองโหมดหลักที่ต้องเลือกตอนเริ่มสร้างแคมเปญใหม่ ซึ่ง **Facebook ไม่มีแนวคิดนี้แบบตรง ๆ** จึงเป็นจุดที่คนย้ายจาก Facebook มักไม่รู้ว่ามีตัวเลือกนี้อยู่:

| โหมด | ลักษณะ | เหมาะกับ |
|---|---|---|
| **Simplified Mode** | ระบบรวมขั้นตอน Campaign + Ad Group + Ad เข้าด้วยกันในหน้าเดียว ลดตัวเลือก Targeting/Bid แบบละเอียดลง ให้ AI ช่วยตัดสินใจมากขึ้น | มือใหม่ที่เพิ่งเริ่มยิง TikTok, ธุรกิจขนาดเล็กที่ต้องการความเร็ว, การทดสอบเบื้องต้นแบบไม่ซับซ้อน |
| **Custom Mode** | แยกทุกขั้นตอนชัดเจนตามโครงสร้าง 3 ชั้นเต็มรูปแบบ (Campaign → Ad Group → Ad) ควบคุม Targeting/Bid/Placement ได้ละเอียดทุกจุด | นักยิงแอดมืออาชีพ, เอเจนซี่, ธุรกิจที่ต้องการควบคุมโครงสร้างและทำ Naming Convention/Consolidation ตามที่เรียนใน Part นี้ |

### ทำไม Part นี้ (และหลักสูตรทั้งหมด) แนะนำให้ใช้ Custom Mode

Simplified Mode สะดวกแต่ซ่อนตัวเลือกสำคัญหลายอย่างไว้ (เช่น การเลือก Placement เอง, การตั้ง Frequency Cap, การเลือก Optimization Goal แบบละเอียด) และที่สำคัญคือ **ทำให้ Naming Convention และการ Consolidation ตามหลักการที่เรียนไปไม่สามารถควบคุมได้เต็มที่** เพราะระบบอาจสร้าง Ad Group ให้อัตโนมัติในแบบที่ไม่ตรงกับ Template ที่วางไว้ ธุรกิจที่ต้องการ Scale และทำ Report อย่างเป็นระบบ (ตามที่หลักสูตรนี้สอนทั้งฝั่ง Facebook และ TikTok) ควรใช้ **Custom Mode เป็นหลักเสมอ** ยกเว้นกรณีทดสอบเร็ว ๆ งบน้อยมากเป็นครั้งคราว

### วิธีสลับโหมดในหน้าจอจริง

ที่หน้า Campaign Creation จะมีปุ่ม Toggle "Simplified Mode" / "Custom Mode" อยู่มุมขวาบนของหน้าจอเสมอ (ตำแหน่งอาจขยับเล็กน้อยตาม UI Update แต่หลักการ Toggle นี้คงที่มาหลายปี) ควรตรวจสอบว่าอยู่ใน Custom Mode ก่อนเริ่มตั้งค่าทุกครั้ง เพราะ TikTok มักตั้ง Default เป็น Simplified Mode ให้บัญชีใหม่

### ข้อควรระวัง: การสลับโหมดระหว่างที่มีแคมเปญ Draft อยู่

การสลับจาก Simplified ไป Custom Mode (หรือกลับกัน) ขณะกำลังตั้งค่า Campaign อยู่ อาจทำให้ค่าที่กรอกไว้บางส่วนรีเซ็ต ควรตัดสินใจเลือกโหมดให้แน่ใจก่อนเริ่มกรอกรายละเอียด ไม่สลับโหมดกลางทาง

---

## Step 667: Smart+ Campaigns — TikTok's Advantage+ เทียบเท่า

### Smart+ Campaigns คืออะไร

**Smart+ Campaigns** คือแคมเปญที่ให้ AI ของ TikTok จัดการ Targeting, Bid, Budget Allocation และ Creative Optimization แบบอัตโนมัติเกือบทั้งหมด โดยนักยิงแอดใส่แค่ Creative, Budget รวม และ Destination เข้าไป ระบบจะหา Audience ที่เหมาะสมเองแบบไม่ต้องกำหนด Targeting ละเอียดเหมือน Custom Mode — แนวคิดนี้**เทียบเท่าโดยตรงกับ Advantage+ Shopping Campaigns (ASC) และ Advantage+ Audience ของ Facebook** ที่เรียนไปแล้วใน Part 029–030

### ประเภทของ Smart+ Campaigns

| ประเภท | เหมาะกับ | เทียบเท่า Facebook |
|---|---|---|
| **Smart+ Catalog Ads** | ธุรกิจ e-Commerce ที่มี Product Catalog เชื่อมกับ TikTok Shop หรือ Website | Advantage+ Shopping Campaigns (ASC) |
| **Smart+ App Campaigns** | ธุรกิจ App ที่ต้องการ Install/In-app Event แบบ Automation เต็มรูปแบบ | Advantage+ App Campaigns |
| **Smart+ Lead Generation** | ธุรกิจที่ต้องการ Lead จำนวนมากโดยให้ AI หา Audience เอง | Advantage+ Leads (บางส่วน) |

### ข้อดีของ Smart+ Campaigns

- ประหยัดเวลาตั้งค่า Targeting ละเอียด เหมาะกับธุรกิจที่มี Data/Catalog พร้อมอยู่แล้วและต้องการ Scale เร็ว
- มักได้ CPA ที่ดีกว่าในระยะยาวเมื่อ Data Feed มีคุณภาพสูง เพราะ AI เข้าถึง Signal ได้กว้างกว่าที่มนุษย์กำหนด Targeting เอง
- ลดความเสี่ยงเรื่อง Audience Overlap ที่เกิดจากการแยก Ad Group มากเกินไป (ปัญหาที่เรียนใน Step 668)

### ข้อจำกัดและเมื่อไหร่ไม่ควรใช้ Smart+

- ควบคุม Targeting แบบละเอียดไม่ได้ ถ้าธุรกิจมีเงื่อนไขกฎหมาย/Policy ที่ต้องจำกัดกลุ่มเป้าหมายเฉพาะ (เช่น อายุขั้นต่ำตามกฎหมาย) ควรใช้ Custom Mode แทน
- ต้องมี Pixel/Catalog Data คุณภาพดีและมี Volume Event เพียงพอ ถ้าเป็นธุรกิจใหม่ที่ยังไม่มี Pixel Data สะสม Smart+ อาจทำงานได้ไม่ดีเท่า Custom Mode ที่มนุษย์ช่วยกำหนดทิศทางเบื้องต้น
- การทำ A/B Test เปรียบเทียบ Creative แบบละเอียดทำได้ยากกว่า เพราะ Smart+ มักผสม Creative เข้ากับ Automation ทั้งระบบ แยกผลลัพธ์รายตัวได้ไม่ชัดเท่า Custom Mode

### แนวทางแนะนำในทางปฏิบัติ

ธุรกิจที่มี Data สะสมเพียงพอแล้ว (ผ่าน Custom Mode มาสักระยะ เห็น Pattern ของ Audience ที่ Convert ดีชัดเจน) ควรทดลองแบ่งงบส่วนหนึ่ง (เช่น 20–30% ของงบรวม) มาทดสอบ Smart+ ควบคู่กับ Custom Mode เดิม แล้วเปรียบเทียบ CPA/ROAS ในช่วงเวลาเดียวกัน ไม่ควรย้ายงบทั้งหมดไป Smart+ ทันทีโดยไม่มีข้อมูลเปรียบเทียบ

---

## Step 668: จำนวน Ad Group/Ad ที่เหมาะสมต่อ Campaign

### หลักการ Consolidation ฉบับ TikTok

เช่นเดียวกับ Facebook, TikTok แนะนำให้ **ลดจำนวน Ad Group ที่ไม่จำเป็นลง** และให้แต่ละ Ad Group มี Volume Event เพียงพอ แทนที่จะแยกย่อยเป็น Ad Group เล็ก ๆ จำนวนมาก

### กฎทั่วไปที่แนะนำ (ปรับตามงบจริงของธุรกิจ)

| ขนาดงบรายวัน | จำนวน Ad Group ต่อ Campaign ที่แนะนำ | จำนวน Ad ต่อ Ad Group ที่แนะนำ |
|---|---|---|
| ต่ำกว่า 600 บาท/วัน | 1 Ad Group | 2–3 Ad (วิดีโอ) |
| 600–3,000 บาท/วัน | 1–2 Ad Group | 3–4 Ad |
| 3,000–15,000 บาท/วัน | 2–5 Ad Group | 4–5 Ad |
| สูงกว่า 15,000 บาท/วัน | 4–8+ Ad Group (แยกตามกลยุทธ์ชัดเจน) | 4–6 Ad |

หมายเหตุ: ตัวเลข Ad ต่อ Ad Group ของ TikTok มักน้อยกว่า Facebook เล็กน้อยเมื่อเทียบที่งบระดับเดียวกัน เพราะการผลิตวิดีโอ Native แต่ละตัวใช้ทรัพยากรมากกว่ารูปภาพ/Carousel ของ Facebook (ตามที่อธิบายใน Step 664)

### เหตุผลเชิงเทคนิคที่ต้องจำกัดจำนวน (เหมือนหลักการ Facebook)

1. **งบถูกแบ่งย่อยเกินไป** — Ad Group ที่มากเกินไปเทียบกับงบรวม ทำให้แต่ละตัวได้งบเฉลี่ยน้อยเกินกว่าจะออกจาก Learning Phase ได้เลย
2. **Targeting Overlap ระหว่าง Ad Group** — Ad Group ที่ทับซ้อนกันเองทำให้ระบบประมูลแข่งกันเองในบัญชีเดียวกัน
3. **ข้อมูลกระจัดกระจาย** — Machine Learning ทำงานดีขึ้นเมื่อมีข้อมูลมากในที่เดียว

### ตัวอย่างเปรียบเทียบ: โครงสร้างที่ผิดกับที่ถูกสำหรับงบ 1,200 บาท/วัน

**โครงสร้างที่มักเห็นจากมือใหม่ (ผิดหลักการ):**

```
Campaign: TT_Sales_Product
├─ Ad Group: Age 18-24
├─ Ad Group: Age 25-34
├─ Ad Group: Interest - Beauty
├─ Ad Group: Interest - Skincare
├─ Ad Group: Custom Audience - Website Visitors
└─ Ad Group: Lookalike 5%
```
(6 Ad Group แบ่งงบ 1,200 บาท เหลือ Ad Group ละ 200 บาท/วัน — น้อยเกินกว่าจะออก Learning Phase ได้ดี)

**โครงสร้างที่ถูกหลักการ Consolidation:**

```
Campaign: TT_Sales_Product (Campaign Budget เปิด งบ 1,200 บาท/วัน)
├─ Ad Group: Broad Targeting (Beauty + Skincare รวมกันเป็น Interest กว้าง ๆ + อายุ 18-45)
└─ Ad Group: Custom Audience - Website Visitors 30 วัน (Retargeting)
```
(2 Ad Group แต่ละตัวมีโอกาสได้งบเฉลี่ยเพียงพอ และ Targeting ไม่ทับซ้อนกันเอง)

### เมื่อไหร่ที่ควรแยก Ad Group จริง ๆ

- แยกตาม **Funnel Stage** ที่ต่างกันชัดเจน (Prospecting vs Retargeting)
- แยกตาม **Placement** ที่ต้องการควบคุมต่างกัน (TikTok Only vs Automatic Placement รวม Pangle)
- แยกเพื่อทำ **Split Test ที่มีสมมติฐานชัดเจน** ผ่านฟีเจอร์ Split Test ของ TikTok เอง (ไม่ใช่แยกมือแบบไม่มีระบบ)

---

## Step 669: ข้อผิดพลาดที่พบบ่อยในการจัดโครงสร้างแคมเปญ TikTok

### ข้อผิดพลาดของคนที่ย้ายมาจาก Facebook โดยตรง

1. **คิดว่า Ad Group = Ad Set 100% แล้วก็อปโครงสร้างมาตรงๆ** — ทำให้พลาดฟีเจอร์เฉพาะ TikTok เช่น Comment/Share/Download Control, Frequency Cap ที่ตั้งตรงในหน้า Ad Group
2. **ใช้ Creative ที่ตัดมาจาก Facebook Ads ไม่ปรับเป็น Native** — เป็นสาเหตุอันดับหนึ่งของ CTR ต่ำในโฆษณา TikTok ที่โครงสร้างตั้งถูกทุกอย่างแต่ผลลัพธ์แย่
3. **ไม่รู้จัก Smart+ Campaigns จึงพลาดโอกาส Scale** หรือในทางกลับกัน **เลือก Smart+ ตั้งแต่วันแรกโดยไม่มี Data สะสม** ทำให้ผลลัพธ์ไม่ดีเพราะ AI ยังไม่มี Signal พอ

### ข้อผิดพลาดทั่วไปที่เกิดกับทุกคนไม่ว่าพื้นฐานจากไหน

4. **แยก Ad Group มากเกินไปโดยไม่มีเหตุผลเชิงกลยุทธ์** (เหมือนปัญหา Facebook Ad Set)
5. **ไม่ตั้ง Naming Convention ตั้งแต่แคมเปญแรก** ทำให้ Business Center รกเมื่อบัญชีโตขึ้น
6. **สลับระหว่าง Simplified Mode และ Custom Mode ไปมาโดยไม่รู้ตัว** ทำให้โครงสร้างไม่สอดคล้องกันระหว่างแคมเปญต่าง ๆ ในบัญชีเดียวกัน
7. **ลืมตรวจสอบว่า Ad Group ตั้ง Placement เป็น Automatic แต่ต้องการควบคุมเฉพาะ TikTok** ทำให้งบไหลไป Pangle Audience Network (เครือข่ายพันธมิตรนอก TikTok App) โดยไม่ได้ตั้งใจ ซึ่งบางครั้งคุณภาพ Traffic ต่างจาก In-App TikTok ชัดเจน (รายละเอียดเจาะลึกใน Part 070)
8. **แก้ Targeting/Bid Strategy ของ Ad Group ที่กำลังทำผลลัพธ์ดีอยู่บ่อยเกินไป** ทำให้ Learning Phase รีเซ็ตซ้ำ ๆ ไม่มีวันได้ข้อมูลที่เสถียรพอจะตัดสินใจ Scale

### ตารางสรุปข้อผิดพลาดและวิธีแก้

| ข้อผิดพลาด | ผลกระทบ | วิธีแก้ |
|---|---|---|
| ใช้ Creative จาก Facebook ตรง ๆ | CTR ต่ำ, CPM สูงกว่าที่ควร | ผลิต Creative ใหม่แบบ Native 9:16 สำหรับ TikTok โดยเฉพาะ |
| แยก Ad Group มากเกินไป | Learning Phase ไม่จบ, งบกระจัดกระจาย | รวม Targeting ที่คล้ายกันเข้า Ad Group เดียว ตามตารางใน Step 668 |
| ไม่รู้จัก Smart+ | พลาดโอกาส Scale ด้วย AI | ทดสอบ Smart+ คู่กับ Custom Mode เมื่อมี Data สะสมพอ |
| Placement เป็น Automatic โดยไม่ตรวจสอบ | งบไหลไป Pangle โดยไม่ตั้งใจ | ตรวจสอบ Breakdown by Placement ทุกสัปดาห์ |
| แก้ไข Ad Group บ่อยเกินไป | Learning Phase รีเซ็ตซ้ำ ๆ | วางแผนการเปลี่ยนแปลงล่วงหน้า จำกัดความถี่การแก้ไข |

---

## Step 670: Workshop — สร้างโครงสร้างแคมเปญ TikTok มาตรฐาน (Template)

### ภารกิจ: สร้าง Campaign Structure Template สำหรับธุรกิจ e-Commerce บน TikTok

ให้สร้างโครงสร้างสมบูรณ์ใน Custom Mode (ไม่ต้อง Publish จริงถ้ายังไม่พร้อม บันทึกเป็น Draft ได้) ตามแผนผังนี้:

```
Campaign: TT_Conv_MainProduct_[เดือน-ปี]_v1
(Objective: Product Sales, Campaign Budget: เปิด, งบรวม 1,200 บาท/วัน, Advertising Type: Regular)

├─ Ad Group 1: TT_Conv_Prospect_Broad-Interest-Beauty_AutoPlacement_v1
│    (Targeting: Interest กว้าง Beauty+Skincare, อายุ 18–45, Placement: Automatic)
│    ├─ Ad: Video_UGC_UnboxingReview_v1
│    ├─ Ad: Video_TrendSound_ProductDemo_v1
│    └─ Ad: Video_Testimonial_RealCustomer_v1
│
├─ Ad Group 2: TT_Conv_Prospect_LAL1pct-Purchase180D_AutoPlacement_v1
│    (Targeting: Lookalike 1% จาก Purchase 180 วัน, Placement: Automatic)
│    ├─ Ad: Video_UGC_UnboxingReview_v1 (ใช้ครีเอทีฟเดิมทดสอบ Targeting ต่าง)
│    └─ Ad: Video_TrendSound_ProductDemo_v1
│
└─ Ad Group 3: TT_Conv_Retarget_WebsiteVisitor30D_AutoPlacement_v1
     (Targeting: Custom Audience Website Visitor 30 วัน ยกเว้น Purchase, Placement: Automatic)
     ├─ Ad: Video_Reminder_LimitedOffer_v1
     └─ Ad: Video_BestSeller_SocialProof_v1
```

### ขั้นตอนปฏิบัติจริง

1. ตรวจสอบว่าอยู่ใน **Custom Mode** ก่อนเริ่มสร้าง (Step 666)
2. สร้าง Campaign ตาม Naming Convention ให้ครบทุกฟิลด์ที่เรียนใน Step 662
3. สร้าง Ad Group ทั้ง 3 ตัวตาม Step 663 พร้อมตรวจสอบว่า Pixel/Optimization Goal ตั้งถูกต้อง
4. สร้าง Ad อย่างน้อย 2 ตัวต่อ Ad Group ตาม Step 664 (ใช้วิดีโอตัวอย่าง/Mockup ได้ถ้ายังไม่มีของจริง แต่ต้องเป็นสัดส่วน 9:16)
5. ตรวจสอบ Naming ทุกระดับให้ตรงตาม Convention ที่วางไว้ 100%
6. บันทึกเป็น Draft และถ่าย Screenshot โครงสร้างทั้งหมดเก็บไว้เป็น Template สำหรับใช้ซ้ำกับสินค้าตัวต่อไป

### เกณฑ์ประเมินผลงาน Workshop

- [ ] จำนวน Ad Group ไม่เกิน 3 ตัวสำหรับงบระดับเริ่มต้น (ตามตารางใน Step 668)
- [ ] แต่ละ Ad Group มีบทบาทต่างกันชัดเจน ไม่ทับซ้อน Targeting กันเอง
- [ ] Naming Convention อ่านแล้วเข้าใจทันทีโดยไม่ต้องเปิดดูการตั้งค่า
- [ ] Ad ในแต่ละ Ad Group เป็นวิดีโอ Native สัดส่วน 9:16 ไม่ใช่ Creative ที่ตัดมาจาก Facebook ตรง ๆ
- [ ] มี Ad Group อย่างน้อย 1 ตัวสำหรับ Retargeting แยกจาก Prospecting ชัดเจน

---

## Case Study: แบรนด์เครื่องสำอางที่ลดความยุ่งเหยิงตอนย้ายจาก Facebook มา TikTok

แบรนด์เครื่องสำอางไทยขนาดกลางที่ทำ Facebook Ads มา 2 ปีจนมีระบบ Naming Convention และ Consolidation ที่แน่นแล้ว ตัดสินใจขยายมายิง TikTok Ads เป็นครั้งแรก ทีม Media Buyer เดิมเข้าใจผิดว่า "TikTok ก็เหมือน Facebook แค่เปลี่ยนแพลตฟอร์ม" จึงก็อปโครงสร้าง Facebook มาตรงๆ: สร้าง 8 Ad Group แยกตาม Interest ทีละตัวในงบเริ่มต้นแค่ 1,000 บาท/วัน (เหมือนที่เคยทำตอนเริ่ม Facebook หลายปีก่อน) พร้อมใช้วิดีโอโฆษณา Facebook เดิมที่เป็นสัดส่วน 1:1 มาอัปโหลดตรง ๆ

ผลลัพธ์ใน 2 สัปดาห์แรก: CPM สูงผิดปกติ, CTR ต่ำกว่า 0.5% (ปกติ TikTok ควรอยู่ 1–3% สำหรับ Creative ที่ดี), แทบไม่มี Ad Group ไหนออกจาก Learning Phase เพราะงบกระจายเกินไป (เฉลี่ย Ad Group ละ 125 บาท/วัน)

หลังปรับตามหลักการใน Part นี้:
1. รวม Ad Group จาก 8 ตัวเหลือ 2 ตัว (Broad Interest + Lookalike) ตามหลัก Consolidation ใน Step 668
2. ผลิตวิดีโอ Native ใหม่ 9:16 ถ่ายด้วยมือถือ ให้ความรู้สึกเหมือน Content ปกติของ TikTok ไม่เหมือนโฆษณา
3. ปรับ Placement เป็น Automatic แต่ตรวจ Breakdown ทุกสัปดาห์เพื่อดูสัดส่วน Pangle vs TikTok In-App

ภายใน 3 สัปดาห์ CTR ขึ้นมาอยู่ที่ 1.8% และ Ad Group ทั้ง 2 ตัวออกจาก Learning Phase ได้สำเร็จ CPA ลดลง 42% เทียบกับช่วงเริ่มต้น บทเรียนสำคัญ: **โครงสร้าง 3 ชั้นอาจคล้ายกัน แต่พฤติกรรมของ Creative และ Consolidation ต้องปรับเฉพาะแพลตฟอร์ม ไม่ใช่ก็อปข้ามมาตรง ๆ**

---

## คำถามที่พบบ่อย (FAQ) ของ Part นี้

**Q: ถ้าเปิด Campaign Budget แล้ว Ad Group ใหม่ที่เพิ่งสร้างจะไม่ได้งบเลยจริงไหม?**
A: มีความเสี่ยงเหมือนกับ CBO ของ Facebook เพราะระบบมักเทงบไปที่ Ad Group ที่มีข้อมูล/ผลลัพธ์ดีอยู่แล้ว ทางแก้คือตรวจสอบว่า TikTok Ads Manager เวอร์ชันที่ใช้มีตัวเลือก Minimum Budget ระดับ Ad Group หรือไม่ (ฟีเจอร์นี้ทยอยเปิดให้ในบางตลาด) ถ้าไม่มี ให้พิจารณาใช้ Ad Group Budget (ปิด Campaign Budget) แทนในช่วงทดสอบ Ad Group ใหม่

**Q: Ad Group เท่ากับ Ad Set ของ Facebook 100% หรือมีอะไรที่ Facebook ไม่มี?**
A: หน้าที่หลักเหมือนกันมาก (Targeting/Budget/Schedule/Bid) แต่ TikTok เพิ่มตัวเลือกเฉพาะตัว เช่น การเปิด/ปิด Comment/Share/Download ของวิดีโอ และ Frequency Cap ที่ตั้งตรงในหน้าเดียวกัน ซึ่ง Facebook ไม่มีในรูปแบบเดียวกัน

**Q: ควรใช้ Smart+ Campaign ตั้งแต่แคมเปญแรกเลยไหม สำหรับธุรกิจที่ไม่มี Data มาก่อน?**
A: ไม่แนะนำ ควรเริ่มจาก Custom Mode ก่อนเพื่อสร้าง Data สะสมและเข้าใจ Pattern ของ Audience ที่ Convert ดี แล้วค่อยทดสอบ Smart+ เมื่อมี Pixel Data เพียงพอ (ตามที่อธิบายใน Step 667)

**Q: ทำไม Ad ของ TikTok มักมีจำนวนน้อยกว่า Ad ของ Facebook ในงบระดับเดียวกัน?**
A: เพราะการผลิตวิดีโอ Native แต่ละตัวใช้ทรัพยากรมากกว่ารูปภาพ/Carousel ของ Facebook ทำให้จำนวน Creative Concept ที่ทดสอบได้จริงต่อรอบมักน้อยกว่า ควรวางแผนการผลิต Content ล่วงหน้าให้เพียงพอต่อ Ad Group ที่ต้องการทดสอบ

**Q: Placement เป็น Automatic ปลอดภัยไหม หรือควรจำกัดเฉพาะ TikTok เสมอ?**
A: ขึ้นกับ Objective และ Budget — Automatic Placement (รวม Pangle) มักช่วยลด CPM ในภาพรวมและเพิ่ม Volume ได้ดีสำหรับ Prospecting Campaign งบไม่สูง แต่ถ้าธุรกิจต้องการควบคุมคุณภาพ Traffic อย่างเข้มงวด (เช่น High-ticket Product) ควรทดสอบจำกัดเฉพาะ TikTok In-App แล้วเปรียบเทียบ CPA กับ Automatic Placement ก่อนตัดสินใจระยะยาว (รายละเอียดเต็มใน Part 070)

---

## ตารางสรุปการตั้งค่าทั้ง 3 ระดับแบบเทียบเคียง (Quick Reference)

| ระดับ | ตั้งค่าอะไร | ตัวอย่างค่าที่ตั้ง | ใครควบคุม Learning Phase |
|---|---|---|---|
| Campaign | Objective, Advertising Type (Regular/Smart+), Campaign Budget Toggle | Product Sales, Regular, Campaign Budget เปิด | ไม่เกี่ยวข้องตรง (กระทบทางอ้อมผ่านงบที่กระจาย) |
| Ad Group | Targeting, Placement, Budget, Optimization Goal, Bid Strategy, Frequency Cap | Broad Interest, Automatic Placement, 500 บาท/วัน | **ควบคุมโดยตรง** — Learning Phase เกิดที่นี่ |
| Ad | Creative, Ad Text, Destination, CTA, UTM | Video Native 9:16, "Shop Now", ลิงก์ /product/serum | ไม่กระทบ Learning Phase โดยตรง แต่กระทบ CTR/Relevance ซึ่งมีผลต่อ Cost |

---

## Checklist ท้ายบท

- [ ] เข้าใจว่า Campaign, Ad Group, Ad ควบคุมอะไรแต่ละชั้น และเทียบกับ Campaign/Ad Set/Ad ของ Facebook ได้ถูกต้อง
- [ ] ตั้งค่า Campaign Level ครบ (Objective, Advertising Type, Campaign Budget)
- [ ] ตั้งค่า Ad Group Level ครบ (Targeting, Placement, Budget, Optimization Goal, Bid Strategy, Frequency Cap)
- [ ] ตั้งค่า Ad Level ครบ (Creative แบบ Native 9:16, Ad Text, Destination URL ตรงกับ Pixel, UTM Parameters)
- [ ] มี Naming Convention ที่เป็นระบบ ปรับสูตรจาก Facebook มาใช้กับ TikTok ได้
- [ ] เข้าใจความแตกต่างระหว่าง Simplified Mode และ Custom Mode และเลือกใช้ Custom Mode เป็นหลัก
- [ ] เข้าใจว่า Smart+ Campaigns คืออะไร เทียบเท่า Advantage+ ของ Facebook ตัวไหน และเมื่อไหร่ควร/ไม่ควรใช้
- [ ] จำนวน Ad Group ต่อ Campaign เหมาะสมกับขนาดงบ ไม่กระจัดกระจายเกินไป
- [ ] รู้จักข้อผิดพลาดที่พบบ่อยของคนย้ายจาก Facebook มา TikTok และวิธีป้องกัน
- [ ] สร้างโครงสร้างแคมเปญ Template สำเร็จตาม Workshop

---

## Workshop / แบบฝึกหัด

**แบบฝึกหัดที่ 1 — เปรียบเทียบโครงสร้าง Facebook vs TikTok ของธุรกิจตัวเอง**
นำโครงสร้างแคมเปญ Facebook ที่มีอยู่แล้ว (หรือจาก Part 016) มาเขียนเทียบเป็นโครงสร้าง TikKok ที่เทียบเท่า ระบุว่าอะไรเหมือนกัน อะไรต้องปรับเพราะข้อจำกัด/จุดต่างของ TikTok

**แบบฝึกหัดที่ 2 — วิเคราะห์โครงสร้างที่มีปัญหา**
สมมติว่าได้รับ TikTok Ads Manager ของบัญชีที่มี 10 Ad Group ใน Campaign เดียว งบรวม 900 บาท/วัน ให้วิเคราะห์ว่าโครงสร้างนี้มีปัญหาอะไร (อ้างอิงหลักการ Consolidation ใน Step 668) และเสนอวิธีจัดโครงสร้างใหม่ให้เหมาะสม

**แบบฝึกหัดที่ 3 — ทำ Template โครงสร้างแคมเปญ TikTok**
ทำตาม Workshop ใน Step 670 ให้ครบ พร้อมบันทึก Screenshot และเขียนสรุปว่าทำไมเลือกจำนวน Ad Group/Ad เท่านี้ ไม่มากไม่น้อยไปกว่านี้ และอธิบายว่าเลือก Regular หรือ Smart+ ด้วยเหตุผลอะไร

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ทำให้เข้าใจ "กระดูกสันหลัง" ของทุกแคมเปญ TikTok Ads อย่างลึกซึ้ง ตั้งแต่หลักการ 3 ชั้น (Campaign > Ad Group > Ad) ที่เทียบเคียงกับ Facebook ได้ชัดเจน, การตั้งค่าแต่ละระดับอย่างละเอียด, ระบบ Naming Convention ที่ปรับใช้ข้ามแพลตฟอร์มได้, ความต่างระหว่าง Simplified Mode และ Custom Mode, แนวคิด Smart+ Campaigns ที่เทียบเท่า Advantage+ ของ Facebook, หลักการ Consolidation ฉบับ TikTok ไปจนถึงข้อผิดพลาดที่พบบ่อยโดยเฉพาะในกลุ่มคนที่ย้ายมาจาก Facebook

ทุกอย่างใน Part นี้เป็น "โครงร่างเปล่า" ที่ยังไม่ได้เลือก Objective ที่เหมาะสมกับธุรกิจจริง ๆ Part 068 จะพาไปเจาะลึก TikTok Campaign Objectives ทั้งหมด — ตั้งแต่ Awareness (Reach) ไปจนถึง Conversion (Website/App/Product Sales/TikTok Shop) — พร้อมตารางเทียบกับ Objective ของ Facebook ที่เรียนไปแล้วใน Part 017 ก่อนที่ Section H จะพาไปสร้างแคมเปญจริงทีละ Objective ตั้งแต่ Part 073 เป็นต้นไป

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- TikTok for Business Help Center: Campaign Structure Overview — https://ads.tiktok.com/help
- TikTok for Business Help Center: About Smart+ Campaigns
- TikTok for Business Help Center: Campaign Budget Optimization
- TikTok Marketing API Documentation: Ad Group Object Reference
- TikTok for Business Help Center: Simplified Mode vs Custom Mode
