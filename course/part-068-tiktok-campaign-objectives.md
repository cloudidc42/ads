# Part 068: TikTok Campaign Objectives ทั้งหมด

**Section:** G — TikTok Ads Fundamentals
**Step ที่ครอบคลุม:** Step 671–680 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 7–9 ชั่วโมง (รวมการเปิดหน้า Create Campaign จริงเพื่อดูตัวเลือก Objective ทั้งหมดและทดลองสร้าง Draft หลายแบบ)

Part 067 สอนโครงสร้าง 3 ชั้นของ TikTok Ads (Campaign > Ad Group > Ad) ไปแล้ว และบอกไว้ว่า "Campaign = ทำไม (Why)" — สิ่งที่กำหนดคำว่า "ทำไม" ตรงนั้นคือ **Campaign Objective** ซึ่งเป็นตัวเลือกแรกสุดที่ต้องกดตั้งแต่เปิดหน้า Create Campaign และเป็นตัวเลือกที่ส่งผลกระทบมากที่สุดต่อทั้งแคมเปญ เพราะ Objective ที่เลือกจะกำหนดว่า TikTok จะไปหาใครให้เห็นโฆษณา, จะ Optimize เพื่อผลลัพธ์แบบไหน, และ Ad Group ชั้นถัดไปจะมีตัวเลือก Optimization Goal ให้เลือกอะไรได้บ้าง

คนที่ยิง Facebook Ads มาก่อนมักเข้าใจว่า "TikTok ก็มี Objective คล้าย ๆ กัน เลือกตามชื่อที่คุ้นก็พอ" ซึ่งเป็นความเข้าใจที่ถูกครึ่งเดียว เพราะแม้แนวคิดพื้นฐานจะเหมือนกันมาก (แบ่งตาม Funnel: บนสุด-กลาง-ล่าง) แต่ TikTok มีการจัดกลุ่ม Objective ที่ไม่ตรงกับ Facebook เป๊ะทุกตัว มี Objective บางตัวที่ Facebook ไม่มี (เช่น Community Interaction, Product Sales แบบผูกกับ TikTok Shop โดยตรง) และมี Objective ที่ Facebook มีแต่ TikTok ไม่มีให้เลือกตรง ๆ (เช่น Facebook แยก Engagement เป็น Objective เดี่ยว ส่วน TikTok รวมเรื่องนี้ไว้ใต้ Consideration)

Part นี้จะไล่ทุก Objective ของ TikTok ทีละตัวอย่างละเอียด พร้อมเทียบกับ Facebook Objective ที่ใกล้เคียงที่สุดตลอดทั้งบท เพื่อให้คนที่มีพื้นฐาน Facebook (จาก Part 017 ของหลักสูตรนี้) นำความเข้าใจเดิมมาต่อยอดได้เร็วที่สุด โดยไม่หลงเชื่อว่าทุกอย่างเหมือนกันหมด

---

## Steps ที่ครอบคลุมใน Part นี้

1. **ภาพรวม 3 กลุ่ม Objective ของ TikTok และการเทียบระดับ Funnel กับ Facebook** — Awareness, Consideration, Conversion คืออะไร ต่างจาก Facebook Funnel Mapping อย่างไร
2. **Awareness: Reach Objective เจาะลึก** — เมื่อไหร่ควรใช้ วัดผลอย่างไร เทียบกับ Facebook Awareness/Reach
3. **Consideration: Traffic Objective เจาะลึก** — การตั้งค่า ข้อจำกัด และการเทียบกับ Facebook Traffic
4. **Consideration: App Install Objective เจาะลึก** — การตั้งค่าเบื้องต้นสำหรับธุรกิจแอป เทียบกับ Facebook App Promotion
5. **Consideration: Lead Generation Objective เจาะลึก** — Instant Form บน TikTok เทียบกับ Facebook Instant Form
6. **Consideration: Community Interaction และ Video Views Objective** — สอง Objective ที่ Facebook ไม่มีตรง ๆ ต้องเข้าใจแยกจากกันให้ชัด
7. **Conversion: Website Conversion Objective เจาะลึก** — หัวใจของแคมเปญขายผ่านเว็บไซต์ เทียบกับ Facebook Sales/Conversion
8. **Conversion: App Conversion และ Product Sales Objective** — สอง Objective ระดับ Conversion ที่ต้องแยกให้ถูกตามลักษณะธุรกิจ
9. **TikTok Shop-Specific Objectives และ GMV Max** — เมื่อธุรกิจขายผ่าน TikTok Shop โดยตรง ต้องเลือก Objective แบบไหน
10. **Workshop: Objective Selection Framework — Mapping Business Goal สู่ TikTok Objective** — กรอบการตัดสินใจพร้อมตารางเทียบ Facebook ↔ TikTok แบบสมบูรณ์

---

## Step 671: ภาพรวม 3 กลุ่ม Objective ของ TikTok และการเทียบระดับ Funnel กับ Facebook

### โครงสร้าง Objective ของ TikTok แบ่งเป็น 3 กลุ่มใหญ่

TikTok Ads Manager (ในโหมด Custom Mode ตามที่แนะนำใน Part 067) จะแสดง Objective เป็น 3 กลุ่มตามลำดับ Funnel เมื่อกด Create Campaign:

```
1) Awareness (การรับรู้)
   └─ Reach

2) Consideration (การพิจารณา)
   ├─ Traffic
   ├─ App Install (Promote App)
   ├─ Lead Generation (Instant Form)
   ├─ Community Interaction (Engagement)
   └─ Video Views

3) Conversion (การเปลี่ยนเป็นลูกค้า)
   ├─ Website Conversion
   ├─ App Conversion (App Events)
   └─ Product Sales (TikTok Shop / Catalog)
```

โครงสร้างนี้ตรงกับหลัก Marketing Funnel ที่เรียนไปแล้วใน Part 005 (Awareness → Consideration → Conversion) เป๊ะ ทำให้เข้าใจง่ายกว่าที่คิด เพียงแต่รายชื่อ Objective ย่อยในแต่ละกลุ่มไม่ตรงกับ Facebook 100%

### ตารางเทียบ Funnel Stage: TikTok ↔ Facebook

| Funnel Stage | TikTok Objective Group | Facebook Objective Group (Part 017) |
|---|---|---|
| Top of Funnel (TOF) | Awareness | Awareness |
| Middle of Funnel (MOF) | Consideration | Traffic, Engagement, Leads, App Promotion (Facebook ไม่แยกกลุ่มรวมชัดเจนเท่า TikTok) |
| Bottom of Funnel (BOF) | Conversion | Sales |

ข้อสังเกตสำคัญ: **Facebook ไม่ได้จัดกลุ่ม Objective เป็น 3 ชั้นแบบเห็นภาพชัดในหน้าจอเหมือน TikTok** — Facebook แสดง Objective เป็นรายการเดียว (Awareness, Traffic, Engagement, Leads, App Promotion, Sales) ให้เลือกโดยไม่แบ่งกลุ่มภาพใหญ่ให้เห็นตรง ๆ ในหน้าจอ (แม้แนวคิดเบื้องหลังจะจัดกลุ่มตาม Funnel เหมือนกัน) ส่วน TikTok ออกแบบ UI ให้เห็น 3 กลุ่มชัดเจนกว่า ซึ่งจริง ๆ ช่วยให้ตัดสินใจง่ายขึ้นถ้าเข้าใจ Funnel ของธุรกิจตัวเองดีอยู่แล้ว

### ทำไม Objective ถึงสำคัญกว่าที่คิด (หลักการเดียวกับ Facebook)

Objective ที่เลือกในระดับ Campaign จะกำหนด:

1. **Ad Group จะมี Optimization Goal ให้เลือกอะไรได้บ้าง** — เช่น เลือก Reach Objective จะไม่มีตัวเลือก Optimize เพื่อ Conversion ให้เลือกในชั้น Ad Group เลย
2. **Bid Strategy ที่ระบบเปิดให้ใช้** — Objective บางตัวเปิดให้ใช้ Cost Cap/Bid Cap ได้ Objective บางตัวจำกัดแค่ Lowest Cost
3. **Machine Learning จะไปโฟกัสหา Audience แบบไหน** — TikTok จะพยายามหาคนที่ "มีโอกาสทำ Action ที่ Objective ต้องการ" ไม่ใช่แค่คนที่ตรง Targeting เท่านั้น
4. **ตัวเลือก Ad Format บางอย่างจะเปิด/ปิดตาม Objective** — เช่น TikTok Shop Product Ads จะปรากฏเฉพาะเมื่อเลือก Objective ที่รองรับ

### ตารางสรุปเต็ม: Objective ทั้งหมด × Optimization Goal ที่รองรับ × Bid Strategy ที่เปิดให้ใช้

ก่อนลงรายละเอียดแต่ละ Objective ในสเต็ปถัดไป ให้ดูภาพรวมทั้งหมดเป็นตารางเดียวก่อน เพื่อเห็นว่าแต่ละ Objective "เปิดประตู" ให้ใช้ตัวเลือกอะไรได้บ้างในชั้น Ad Group (รายละเอียดเชิงลึกของ Optimization Goal และ Bid Strategy แต่ละตัวจะอยู่ใน Part 069 แต่ควรเห็นภาพเชื่อมโยงตั้งแต่ตอนนี้):

| Objective | กลุ่ม Funnel | Optimization Goal ที่เลือกได้ | Bid Strategy ที่เปิดให้ใช้ |
|---|---|---|---|
| Reach | Awareness | Reach | Lowest Cost, Reach & Frequency |
| Traffic | Consideration | Click, Landing Page View | Lowest Cost, Cost Cap |
| App Install | Consideration | Install, Click | Lowest Cost, Cost Cap |
| Lead Generation | Consideration | Lead (Form Submission) | Lowest Cost, Cost Cap |
| Community Interaction | Consideration | Follow, Comment, Profile Visit | Lowest Cost |
| Video Views | Consideration | 6-Second View, Video View (2s) | Lowest Cost |
| Website Conversion | Conversion | Conversion, Value | Lowest Cost, Cost Cap, Bid Cap |
| App Conversion | Conversion | In-App Event, Value | Lowest Cost, Cost Cap, Bid Cap |
| Product Sales | Conversion | Conversion, Value (ROAS) | Lowest Cost, Cost Cap, Bid Cap |
| GMV Max (TikTok Shop) | Conversion (Automated) | GMV (อัตโนมัติ ไม่ต้องเลือกเอง) | อัตโนมัติเต็มรูปแบบ ไม่มี Bid Strategy ให้เลือกมือ |

ข้อสังเกตที่สำคัญจากตารางนี้: **ยิ่ง Objective อยู่ลึกลง Funnel เท่าไหร่ ตัวเลือก Bid Strategy จะยิ่งเปิดกว้างขึ้น** เพราะ Objective ระดับ Conversion ต้องพึ่ง Machine Learning ที่ซับซ้อนกว่าในการควบคุมต้นทุนต่อผลลัพธ์ ขณะที่ Objective ระดับ Awareness/Consideration บางตัว (Community Interaction, Video Views) มีแค่ Lowest Cost ให้ใช้เพราะเป้าหมายเป็นเรื่อง Volume ไม่ใช่เรื่องต้นทุนต่อ Action ที่มีมูลค่าทางธุรกิจสูง

### กฎทองข้อแรก: เลือก Objective ตาม "ผลลัพธ์ทางธุรกิจที่วัดได้จริง" ไม่ใช่ตาม "ชื่อที่ฟังดูดี"

หลักการนี้เหมือนกับที่เรียนใน Facebook (Part 017 Step 167) เป๊ะ: ความผิดพลาดที่พบบ่อยที่สุดคือเลือก Objective ที่ฟังดูตรงกับสิ่งที่อยากได้ (เช่น เลือก "Traffic" เพราะอยากให้คนเข้าเว็บ) แต่จริง ๆ ธุรกิจต้องการ "การซื้อ" ไม่ใช่แค่ "การคลิก" ซึ่งควรเลือก Website Conversion แทน เพราะ Traffic Objective จะ Optimize หาคนที่ "มีโอกาสคลิกสูงที่สุด" ไม่ใช่คนที่ "มีโอกาสซื้อสูงที่สุด" แม้ผลลัพธ์ปลายทางที่ธุรกิจต้องการคือยอดขาย

### ข้อผิดพลาดเชิงภาพรวมที่พบบ่อยที่สุด

- เลือก Traffic เพราะคิดว่า "ปลอดภัยกว่า" ทั้งที่มี Pixel/Event พร้อมสำหรับ Conversion แล้ว
- เลือก Reach เพื่อ "ประหยัดงบ" ทั้งที่ธุรกิจต้องการยอดขายจริง ไม่ใช่แค่การมองเห็น
- ไม่รู้ว่า TikTok Shop มี Objective เฉพาะของตัวเอง (Product Sales) จึงไปสร้างแคมเปญ Website Conversion แทนทั้งที่ขายผ่าน TikTok Shop โดยตรง ทำให้พลาดฟีเจอร์สำคัญอย่าง GMV Max และ Live Shopping Ads
- คิดว่า Objective เปลี่ยนได้หลังสร้างแคมเปญ — **ความจริงคือเปลี่ยนไม่ได้** เหมือน Facebook ต้องสร้าง Campaign ใหม่เท่านั้นถ้าอยากเปลี่ยน Objective

---

## Step 672: Awareness: Reach Objective เจาะลึก

### Reach คืออะไร

**Reach** เป็น Objective เดียวในกลุ่ม Awareness ของ TikTok มีเป้าหมายให้โฆษณาเข้าถึงคนให้ได้มากที่สุดภายในงบที่กำหนด โดย TikTok จะ Optimize เพื่อ **Reach สูงสุดในราคาต่อ 1,000 Impression (CPM) ที่ต่ำที่สุด** ไม่สนใจว่าคนที่เห็นจะคลิกหรือทำ Action อะไรต่อหรือไม่

### เทียบกับ Facebook

| มิติ | TikTok Reach | Facebook Awareness (Reach) |
|---|---|---|
| เป้าหมายหลัก | เข้าถึงคนมากที่สุดในงบที่กำหนด | เข้าถึงคนมากที่สุดในงบที่กำหนด |
| Optimization Goal ที่ใช้ | Reach | Reach |
| Bid Strategy ที่รองรับ | Lowest Cost, Reach & Frequency (งบใหญ่/Booking ล่วงหน้า) | Lowest Cost, Reach & Frequency |
| เหมาะกับ | Brand Awareness, การเปิดตัวสินค้าใหม่, การสร้าง Top of Funnel Pool ก่อนทำ Retargeting | เหมือนกันทุกประการ |

โดยหลักการแล้ว Reach Objective ของ TikTok กับ Facebook **เหมือนกันมากที่สุดในบรรดา Objective ทั้งหมด** เพราะเป็น Objective พื้นฐานที่สุดที่ไม่ต้องพึ่ง Machine Learning ขั้นสูงในการหา "คนที่มีโอกาสทำ Action" — แค่กระจาย Impression ให้กว้างและถูกราคา

### เมื่อไหร่ควรใช้ Reach บน TikTok

1. **เปิดตัวสินค้า/แคมเปญใหม่ที่ต้องการสร้างการรับรู้ก่อน** โดยยังไม่เน้นยอดขายทันที
2. **สร้าง Retargeting Pool** — ยิง Reach ราคาถูกไปที่กลุ่มเป้าหมายกว้าง เพื่อสร้างฐาน "คนที่ดูวิดีโอ" (Video Viewers) ไว้ทำ Custom Audience Retargeting ต่อใน Funnel ขั้นถัดไป (เทคนิคนี้ใช้ได้ผลดีมากบน TikTok เพราะ Engagement Rate สูง)
3. **แคมเปญที่มีงบ Branding แยกจากงบ Performance ชัดเจน** เช่น แบรนด์ใหญ่ที่มีทั้งทีม Brand และทีม Performance
4. **Reach & Frequency Buying** สำหรับ Event/Launch ที่ต้องการ Guarantee การเข้าถึงในช่วงเวลาที่กำหนดแน่นอน (ต้องมีงบขั้นต่ำสูงกว่าปกติมาก)

### เมื่อไหร่ไม่ควรใช้ Reach

- ธุรกิจ SME/e-Commerce งบจำกัดที่ต้องการยอดขายเป็นหลัก — ควรข้ามไปที่ Conversion Objective ตรง ๆ เพราะ Reach ไม่ Optimize เพื่อยอดขายเลย
- ธุรกิจที่มี Pixel/Event พร้อมสมบูรณ์แล้ว การใช้ Reach เป็นการเสียโอกาสให้ Machine Learning ช่วยหาคนที่มีโอกาสซื้อสูง

### วิธีวัดผล Reach Campaign อย่างถูกต้อง

Metric หลักที่ต้องดู: **Reach, Frequency, CPM** ไม่ใช่ CTR หรือ CPA เพราะ Reach Campaign ไม่ได้ถูก Optimize เพื่อการคลิกหรือซื้อ ถ้าเอา CPA มาวัดผล Reach Campaign จะสรุปผิดว่าแคมเปญ "แย่" ทั้งที่มันทำงานตามเป้าหมายของมันถูกต้องแล้ว (Reach สูง CPM ต่ำ) — ข้อผิดพลาดเชิง Metric แบบนี้เหมือนกับที่เกิดกับ Facebook Awareness Campaign เป๊ะ

### ตัวอย่างการตั้งค่า Reach Campaign จริง

```
Campaign Objective: Reach
Campaign Name: TT_Reach_NewProductLaunch_Q3-2026_v1
Ad Group Optimization Goal: Reach
Bid Strategy: Lowest Cost
Budget: 2,000 บาท/วัน x 7 วัน (จำกัดเวลาให้ชัดเจนสำหรับ Branding Campaign)
Targeting: Core Audience กว้าง อายุ 18-45 ทั่วประเทศ (ไม่ Narrow เพราะต้องการ Reach สูงสุด)
Frequency Cap: ไม่เกิน 2 ครั้ง/คน/7 วัน (กันไม่ให้คนเดิมเห็นซ้ำเกินจำเป็น)
```

---

## Step 673: Consideration: Traffic Objective เจาะลึก

### Traffic คืออะไร

**Traffic** อยู่ในกลุ่ม Consideration มีเป้าหมายให้คนคลิกจากโฆษณาไปยัง Destination ที่กำหนด (เว็บไซต์ภายนอก, TikTok Profile, หรือ Instant Page) โดย TikTok จะ Optimize เพื่อหาคนที่ **มีโอกาสคลิกสูงที่สุด** ในราคาต่อคลิก (CPC) ที่ต่ำที่สุด

### เทียบกับ Facebook

| มิติ | TikTok Traffic | Facebook Traffic |
|---|---|---|
| Optimization Goal | Click, Landing Page View | Link Clicks, Landing Page Views |
| Bid Strategy | Lowest Cost, Cost Cap | Lowest Cost, Cost Cap, Bid Cap |
| Destination ที่รองรับ | Website, TikTok Instant Page | Website, Instant Experience |
| จุดต่างสำคัญ | ไม่มีตัวเลือก "Messenger/App" ปนอยู่แบบ Facebook Traffic บางเวอร์ชันเก่า | Facebook Traffic เคยรวม Destination หลากหลายมากกว่า |

หลักการ Optimization เหมือนกันมาก แต่ TikTok มีตัวเลือก **Landing Page View** ที่ละเอียดกว่า Click ธรรมดา คือนับเฉพาะคนที่หน้าเว็บโหลดสำเร็จจริง (ไม่ใช่แค่กดคลิก) ซึ่งช่วยกรอง Traffic ปลอมจาก Bot หรือคนที่กดแล้วปิดทันทีก่อนหน้าโหลดเสร็จได้ดีกว่า Click เฉย ๆ — ควรเลือก **Landing Page View เป็น Optimization Goal เสมอเมื่อใช้ Traffic Objective** ถ้าเว็บไซต์มี Pixel ติดตั้งสมบูรณ์แล้ว

### เมื่อไหร่ควรใช้ Traffic บน TikTok

1. **เว็บไซต์ยังไม่มี Pixel Event ที่มี Volume พอสำหรับ Conversion Optimization** (ธุรกิจใหม่ยังไม่มี Purchase Data สะสม)
2. **Content Site/บทความ/บล็อกที่วัดผลด้วย Pageview เป็นหลัก** ไม่ใช่การซื้อขาย
3. **ต้องการทดสอบ Landing Page หรือ Creative เบื้องต้นก่อนลงทุนกับ Conversion Campaign** ที่ต้องใช้เวลา Learning นานกว่า
4. **Traffic ไปยัง TikTok Profile หรือ Instant Page** เพื่อสร้าง Follower/Engagement ต่อเนื่อง

### เมื่อไหร่ไม่ควรใช้ Traffic

ถ้าธุรกิจมี Pixel ที่ยิง Purchase/Lead Event สม่ำเสมออยู่แล้ว (มากกว่า ~50 Event/สัปดาห์) **ควรข้ามไปใช้ Website Conversion Objective ตรง ๆ ทันที** เพราะ Traffic Objective หาคนที่ "ชอบคลิก" ซึ่งไม่ใช่กลุ่มเดียวกันกับคนที่ "มีโอกาสซื้อ" เสมอไป การเสียเวลากับ Traffic Objective เมื่อพร้อมทำ Conversion แล้วคือการเสียโอกาสให้ Machine Learning ทำงานเต็มประสิทธิภาพ

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Traffic Objective ตลอดไปเพราะ "CPC ถูกกว่า" โดยไม่เคยลองเทียบ CPA จริงกับ Conversion Objective — CPC ถูกไม่ได้แปลว่า CPA จะถูกตามเสมอ เพราะคนที่คลิกถูกอาจไม่ใช่คนที่ซื้อ
- ตั้ง Optimization Goal เป็น Click ธรรมดาทั้งที่มี Pixel ติดตั้งสมบูรณ์แล้ว ทำให้เสียโอกาสใช้ Landing Page View ที่มีคุณภาพ Traffic ดีกว่า
- ใช้ Traffic Objective แล้วคาดหวัง ROAS เหมือน Conversion Campaign

---

## Step 674: Consideration: App Install Objective เจาะลึก

### App Install (Promote App) คืออะไร

Objective นี้ (บางเวอร์ชัน UI เรียก **Promote App** หรือ **App Install**) มีเป้าหมายให้คนติดตั้งแอปมือถือ โดยเชื่อมกับ App Store/Google Play ผ่าน App Event API หรือ Mobile Measurement Partner (MMP) เช่น AppsFlyer, Adjust, Kochava ที่รองรับ TikTok

### เทียบกับ Facebook

| มิติ | TikTok App Install | Facebook App Promotion |
|---|---|---|
| ระบบเชื่อมข้อมูล | TikTok App Events API หรือ MMP (AppsFlyer/Adjust) | Facebook SDK, MMP (AppsFlyer/Adjust) เหมือนกัน |
| Optimization Goal พื้นฐาน | Install, In-App Event (เช่น Purchase, Registration ในแอป) | App Installs, App Events |
| Deep Link Support | รองรับ Deep Link ไปหน้าเฉพาะในแอปหลังติดตั้ง | รองรับเหมือนกัน |
| ผลกระทบจาก iOS 14+/ATT | ได้รับผลกระทบเรื่อง Attribution เหมือนกัน ต้องพึ่ง SKAdNetwork (SKAN) บน iOS | ได้รับผลกระทบเหมือนกัน (เรียนไปแล้วใน Part 013 เรื่อง CAPI ซึ่งเป็นแนวคิดคู่กับ SKAN) |

จุดที่ต้องเข้าใจเพิ่มจาก Facebook: TikTok เพิ่งขยาย Support ด้าน App Ads ในช่วงหลังให้ครบเครื่องขึ้นมาก แต่ระบบ Attribution ฝั่ง iOS ยังพึ่ง Apple's SKAdNetwork เหมือนกับทุกแพลตฟอร์มอื่น (Facebook รวมถึง Google) หมายความว่าข้อจำกัดเรื่อง Data Delay และ Conversion Modeling ที่เรียนไปแล้วในบท Facebook ก็ใช้ได้กับ TikTok เช่นกัน ไม่ใช่ปัญหาเฉพาะ Facebook อย่างที่บางคนเข้าใจผิด

### เมื่อไหร่ควรใช้

- ธุรกิจที่มีแอปมือถือและต้องการยอด Install หรือ In-app Action (เช่น Registration, First Purchase ในแอป)
- ธุรกิจ Gaming, Fintech App, e-Commerce App ที่มี MMP เชื่อมพร้อมแล้ว

### ข้อควรระวังก่อนเริ่ม

ต้องเชื่อม MMP หรือ TikTok App Events API **ให้เรียบร้อยก่อน** สร้างแคมเปญ ไม่เช่นนั้น Optimization Goal ระดับ In-App Event จะไม่มีให้เลือก เหลือแค่ Install เป็น Event ต่ำสุดที่วัดได้ ซึ่งเหมือนกับปัญหา Pixel ไม่พร้อมของ Website Objective ทุกประการ

---

## Step 675: Consideration: Lead Generation Objective เจาะลึก

### Lead Generation คืออะไร

Objective นี้เปิดให้สร้าง **Instant Form** ที่กรอกข้อมูลได้ทันทีในแอป TikTok โดยไม่ต้องออกไปเว็บไซต์ภายนอก — แนวคิดเดียวกันกับ **Instant Form ของ Facebook Leads Objective** (เรียนไปแล้วใน Part 017 Step 164) เป๊ะ

### เทียบกับ Facebook

| มิติ | TikTok Lead Generation | Facebook Leads (Instant Form) |
|---|---|---|
| ฟอร์มอยู่ที่ไหน | ในแอป TikTok โดยตรง | ในแอป Facebook/Instagram โดยตรง |
| ความเร็วในการกรอก | เร็วมาก (Auto-fill ข้อมูลบางส่วนจากโปรไฟล์ TikTok) | เร็วมากเช่นกัน (Auto-fill จากโปรไฟล์ Facebook) |
| การดึงข้อมูล Lead | ดาวน์โหลด CSV จาก TikTok Ads Manager หรือเชื่อม CRM ผ่าน Webhook/API | ดาวน์โหลด CSV หรือเชื่อม CRM ผ่าน Meta Leads API/Zapier |
| คุณภาพ Lead โดยทั่วไป | มักมี Lead ปลอม/สุ่มกรอกสูงกว่า Facebook เล็กน้อย เพราะพฤติกรรมผู้ใช้ TikTok เน้นเสพ Content เร็ว กด Skip/กรอกไม่ตั้งใจได้ง่าย | Lead ปลอมมีเช่นกันแต่ระบบ Auto-fill จาก Facebook Profile ที่ผู้ใช้ผูกกับกิจกรรมจริงในชีวิตมากกว่ามักให้คุณภาพสูงกว่าเล็กน้อย |

### สิ่งที่ต้องทำเพิ่มเพื่อกรองคุณภาพ Lead บน TikTok (สำคัญมาก)

เพราะพฤติกรรมผู้ใช้ TikTok ต่างจาก Facebook (เสพ Content แบบ Passive มากกว่า Active Searching) การตั้งฟอร์มควรเพิ่มคำถามคัดกรอง (Qualifying Question) อย่างน้อย 1-2 ข้อเสมอ เช่น "งบประมาณที่สนใจ" หรือ "พร้อมตัดสินใจภายในกี่วัน" เพื่อลด Lead ที่กรอกมั่ว การไม่เพิ่มคำถามคัดกรองแล้วปล่อยฟอร์มสั้นเกินไปเป็นสาเหตุอันดับหนึ่งที่ทำให้ทีมขายบ่นว่า "Lead จาก TikTok คุณภาพแย่กว่า Facebook"

### เมื่อไหร่ควรใช้ Lead Generation บน TikTok

- ธุรกิจ B2C ที่มี Sales Cycle สั้น-กลาง (ประกัน, คอร์สเรียน, อสังหาริมทรัพย์ระดับเริ่มต้น, ความงาม/คลินิก)
- ธุรกิจที่มีทีม Telesales ที่ตอบ Lead ได้เร็ว (ภายใน 5-15 นาที) เพราะความสนใจของผู้ใช้ TikTok เย็นเร็วกว่า Facebook ถ้าปล่อย Lead ค้างไว้นาน

### ข้อจำกัดที่ TikTok มีต่างจาก Facebook

TikTok Instant Form ในบางตลาด/บางช่วงเวลามีตัวเลือก Field ให้ปรับแต่งน้อยกว่า Facebook Lead Form ที่พัฒนามานานกว่าและมี Feature เสริม เช่น Conditional Logic หรือ Context Card ที่ละเอียดกว่า ควรตรวจสอบ Field ที่รองรับปัจจุบันในหน้า Ads Manager จริงก่อนออกแบบฟอร์มที่ซับซ้อนเกินขอบเขตที่ TikTok รองรับ

---

## Step 676: Consideration: Community Interaction และ Video Views Objective

### สอง Objective ที่ Facebook ไม่มีตรง ๆ

นี่คือจุดที่ TikTok ต่างจาก Facebook ชัดเจนที่สุดในกลุ่ม Consideration เพราะมี Objective เฉพาะสำหรับแพลตฟอร์ม Content แบบ TikTok โดยตรง

### Community Interaction คืออะไร

**Community Interaction** มีเป้าหมายเพิ่ม Engagement บนโปรไฟล์ TikTok ของแบรนด์ เช่น Follower เพิ่ม, Comment, Profile Visit — ใกล้เคียงกับแนวคิด **Facebook Engagement Objective (Page Likes/Post Engagement)** ที่เรียนไปแล้ว แต่ TikTok เจาะจงกว่าตรงที่โฟกัสที่ "การมีปฏิสัมพันธ์กับ Community/โปรไฟล์" มากกว่าแค่ยอด Like ของโพสต์เดียว

| มิติ | TikTok Community Interaction | Facebook Engagement |
|---|---|---|
| Optimize เพื่อ | Follow, Comment, Profile Visit | Post Engagement, Page Likes |
| เหมาะกับ | แบรนด์ที่ต้องการสร้างฐาน Follower ระยะยาวบน TikTok เพื่อทำ Organic Content ต่อ | แบรนด์ที่ต้องการสร้าง Social Proof บน Page |
| ผลต่อยอดขาย | ทางอ้อม สร้างฐานผู้ติดตามที่รับ Content ในอนาคตได้ | ทางอ้อมเช่นกัน |

### Video Views คืออะไร

**Video Views** Optimize เพื่อให้คนดูวิดีโอนานที่สุด/ครบมากที่สุด วัดผลด้วย **6-Second View, Video Watched (25%/50%/75%/100%)** — ไม่มี Objective คู่ตรงเป๊ะใน Facebook (Facebook มี ThruPlay/Video Views Optimization Goal อยู่ใต้ Objective อื่นแทน ไม่ได้แยกเป็น Objective หลักเดี่ยว ๆ เหมือน TikTok)

| มิติ | TikTok Video Views | Facebook (ใกล้เคียงที่สุด) |
|---|---|---|
| ตำแหน่งใน UI | Objective หลักแยกเดี่ยว | Optimization Goal ย่อยใต้ Awareness/Engagement (ThruPlay) |
| Metric วัดผล | 6-Sec View, Watch Time, Completion Rate | ThruPlay, Video Average Watch Time |
| ประโยชน์ | สร้าง Custom Audience "Video Viewers" ราคาถูกมาก เพื่อ Retarget ต่อ | สร้าง Custom Audience "Video Viewers" เหมือนกัน |

### ทำไม Video Views สำคัญมากบน TikTok (มากกว่าที่คิดเมื่อเทียบ Facebook)

เพราะ TikTok เป็น Content-first Platform ที่ Custom Audience จาก "คนดูวิดีโอ X%" มีคุณภาพสูงมากในการทำ Retargeting ต่อ (คนที่ดูวิดีโอโฆษณาจบ 75% ขึ้นไปมักมีความสนใจสูงใกล้เคียงคนที่ Engage บนโพสต์ Facebook) กลยุทธ์ที่ใช้ได้ผลบ่อยคือ ยิง Video Views Objective ราคาถูกเพื่อสร้าง Pool คนดูจบก่อน แล้วค่อยทำ Conversion Campaign แบบ Retargeting เฉพาะกลุ่มนี้ในขั้นต่อไป (รายละเอียดโครงสร้าง Funnel เต็มรูปแบบอยู่ใน Part 084)

### ข้อผิดพลาดที่พบบ่อยกับสองตัวนี้

- ใช้ Community Interaction คาดหวังยอดขายทันที ทั้งที่ Objective นี้ Optimize เพื่อ Follow/Comment เท่านั้น
- ไม่รู้ว่า Video Views สร้าง Custom Audience ได้ จึงไม่เคยเอาไปต่อ Funnel เลย เสียโอกาสสร้าง Retargeting Pool ราคาถูก
- สับสนระหว่าง Video Views (Objective) กับ "Video Views" ที่เป็นแค่ Metric แสดงในทุกแคมเปญไม่ว่า Objective ใด — ตัวเลข Video View ที่เห็นในรายงานของ Reach หรือ Traffic Campaign ก็มี แต่นั่นไม่ได้แปลว่าแคมเปญนั้นถูก Optimize เพื่อ Video View จริง

---

## Step 677: Conversion: Website Conversion Objective เจาะลึก

### Website Conversion คืออะไร

**Website Conversion** คือ Objective หลักของกลุ่ม Conversion สำหรับธุรกิจที่ขายผ่านเว็บไซต์ภายนอก (ไม่ใช่ TikTok Shop) โดย TikTok จะ Optimize เพื่อหาคนที่ **มีโอกาสทำ Conversion Event ที่กำหนด** (Purchase, Lead, Complete Registration ฯลฯ) สูงสุดในราคาที่ต่ำที่สุด — เทียบเท่า **Facebook Sales Objective (Conversion)** ที่เรียนไปแล้วในบท Facebook (Part 017 Step 166, Part 026)

### เทียบกับ Facebook

| มิติ | TikTok Website Conversion | Facebook Sales (Conversion) |
|---|---|---|
| ต้องมีอะไรก่อนใช้งาน | TikTok Pixel + Events API (Part 066) | Facebook Pixel + CAPI (Part 013) |
| Optimization Goal | Conversion, Value (ROAS-based) | Conversions, Value, ROAS Goal |
| ระดับ Event ที่เลือกได้ | Standard Event หรือ Custom Event ที่ตั้งไว้ใน Events Manager ของ TikTok | Standard Event หรือ Custom Conversion ใน Events Manager ของ Facebook |
| ผลกระทบจาก Privacy Changes (iOS 14+) | ได้รับผลกระทบเช่นกัน ต้องพึ่ง Events API (Server-Side) ชดเชย Data Loss จาก Browser Pixel | เรียนไปแล้วทั้ง Part ว่าต้องพึ่ง CAPI ชดเชย |
| Learning Phase ขั้นต่ำที่แนะนำ | ~50 Optimization Event/สัปดาห์/Ad Group | ~50 Optimization Event/สัปดาห์/Ad Set |

หลักการ Optimization ของ Website Conversion เหมือนกับ Facebook Conversion Objective แทบทุกประการ เพราะทั้งสองแพลตฟอร์มใช้แนวคิด Machine Learning แบบเดียวกันคือหา "Lookalike Signal" จากคนที่เคย Convert จริงในอดีต แล้วขยายหาคนที่มี Pattern คล้ายกันในกลุ่มเป้าหมายกว้าง

### การเลือก Conversion Event ที่เหมาะสม (สำคัญมาก)

เหมือนหลักการ Facebook: ควร Optimize เพื่อ Event ที่ "อยู่ปลายสุดของ Funnel ที่มี Volume เพียงพอ" ไม่ใช่ Event ที่อยากได้ที่สุดเสมอไป

| สถานการณ์ Volume | Event ที่ควร Optimize |
|---|---|
| Purchase > 50 ครั้ง/สัปดาห์ | Optimize เพื่อ Purchase ตรง ๆ (ดีที่สุด) |
| Purchase < 50 ครั้ง/สัปดาห์ แต่ AddToCart/InitiateCheckout มาก | Optimize เพื่อ InitiateCheckout ก่อน แล้วขยับขึ้น Purchase เมื่อ Volume พอ |
| ธุรกิจใหม่ยังไม่มี Purchase สะสมเลย | เริ่มที่ Complete Payment แบบ Value-based ไม่ได้ ต้องสะสม Standard Event พื้นฐานก่อน (เช่น ViewContent, AddToCart) ตามลำดับ Funnel |

### Value Optimization (Optimize เพื่อ ROAS) บน TikTok

TikTok รองรับการ Optimize เพื่อ **Value** (ส่งค่า Order Value ไปพร้อม Purchase Event) คล้ายกับ Facebook Value Optimization/ROAS Goal ที่เรียนไปแล้ว โดยต้องส่ง Parameter `value` และ `currency` ไปพร้อม Purchase Event ทุกครั้งผ่าน Pixel/Events API ถ้าค่าที่ส่งไม่ครบหรือผิด TikTok จะ Optimize ผิดทิศทาง (เช่น หาคนที่ซื้อบ่อยแต่ Order เล็ก แทนที่จะหาคนที่ Order ใหญ่)

### ข้อผิดพลาดที่พบบ่อย

- Optimize เพื่อ Purchase ทั้งที่มี Volume ต่ำกว่า 10 ครั้ง/สัปดาห์ ทำให้ไม่ผ่าน Learning Phase เลย งบไหลไม่หยุดโดยไม่มีผลลัพธ์ที่เสถียร
- ไม่ส่ง Value/Currency ไปกับ Purchase Event ทำให้พลาดโอกาสใช้ Value Optimization ทั้งที่มีข้อมูลพร้อม
- ใช้ Domain ที่ไม่ Verify กับ TikTok Business Center ทำให้ Optimization Event บางตัวไม่ปรากฏให้เลือก (ปัญหาเดียวกับ Facebook Domain Verification ที่เรียนใน Part 011 Step 108)

### ตัวอย่างคำนวณ Breakeven CPA ก่อนตั้ง Website Conversion Campaign

ก่อนเริ่มแคมเปญ Website Conversion ทุกครั้ง ควรคำนวณ Breakeven CPA (อ้างอิงหลักการจาก Part 004 Step 34) เพื่อรู้ว่า TikTok ทำ CPA ได้ในระดับที่ธุรกิจยังพอมีกำไรหรือไม่ ตัวอย่าง:

```
ราคาขายสินค้าเฉลี่ยต่อออเดอร์ (AOV): 890 บาท
ต้นทุนสินค้า + ค่าจัดส่ง (COGS): 420 บาท
กำไรขั้นต้นก่อนค่าโฆษณา: 470 บาท

Breakeven CPA = 470 บาท
(ถ้า CPA ต่ำกว่า 470 บาท = มีกำไรหลังหักค่าโฆษณา)
(ถ้า CPA สูงกว่า 470 บาท = ขาดทุนทุกออเดอร์)

เป้าหมาย CPA ที่ตั้งไว้จริง (เผื่อ Margin ปลอดภัย 30%): 470 x 0.7 = 329 บาท
```

การคำนวณนี้ต้องทำก่อนดู Metric ในหน้า TikTok Ads Manager เสมอ เพราะถ้าไม่มีเลขอ้างอิง จะตัดสินใจได้ยากว่า CPA ที่เห็นจริง (เช่น 510 บาท) "ดี" หรือ "แย่" สำหรับธุรกิจนี้โดยเฉพาะ

---

## Step 678: Conversion: App Conversion และ Product Sales Objective

### App Conversion คืออะไร

**App Conversion** (บางที่เรียก App Events Objective ในกลุ่ม Conversion) ต่างจาก App Install ของกลุ่ม Consideration (Step 674) ตรงที่ App Conversion Optimize เพื่อ **In-App Event ที่มีค่าทางธุรกิจสูง** (เช่น Purchase ในแอป, Subscribe, Complete Tutorial) ไม่ใช่แค่ยอด Install

| มิติ | TikTok App Install (Consideration) | TikTok App Conversion (Conversion) |
|---|---|---|
| Optimize เพื่อ | การติดตั้งแอป | Event หลังติดตั้ง เช่น Purchase, Subscribe |
| เหมาะกับ | แอปเปิดตัวใหม่ ต้องการยอด Download ก่อน | แอปที่มี User Base แล้ว ต้องการเพิ่ม Value จาก User |
| เทียบเท่า Facebook | App Promotion (Optimize: Install) | App Promotion (Optimize: App Event เช่น Purchase) |

จุดนี้เหมือนกับ Facebook มาก: Facebook App Promotion Objective เดียวกันก็มีให้เลือก Optimize ได้ทั้ง Install และ App Event ต่างกันแค่ TikTok แยกเป็นชื่อ Objective คนละกลุ่ม Funnel ให้เห็นชัดเจนกว่า

### Product Sales คืออะไร

**Product Sales** คือ Objective ที่ผูกกับ **Product Catalog** โดยตรง (ไม่ว่าจะเป็น Catalog ที่เชื่อมจาก Website ผ่าน Feed หรือ Catalog ของ TikTok Shop) ใช้สำหรับแคมเปญที่ต้องการโปรโมทสินค้าเป็นชิ้น ๆ จาก Catalog แบบ Dynamic — เทียบเท่า **Facebook Catalog Sales / Dynamic Ads** (เรียนไปแล้วใน Part 027)

| มิติ | TikTok Product Sales | Facebook Catalog Sales / Dynamic Ads |
|---|---|---|
| ต้องมีอะไรก่อน | Product Catalog เชื่อมกับ TikTok Business Center | Product Catalog เชื่อมกับ Business Manager (Commerce Manager) |
| รูปแบบ Ad | Video/Image ที่ดึงข้อมูลสินค้าอัตโนมัติจาก Feed | Dynamic Ads ดึงข้อมูลจาก Catalog อัตโนมัติเช่นกัน |
| Retargeting อัตโนมัติ | รองรับ Dynamic Retargeting (คนดูสินค้า A เห็นโฆษณาสินค้า A ที่เคยดู) | รองรับ Dynamic Retargeting เหมือนกัน (DPA — Dynamic Product Ads) |
| ผูกกับ TikTok Shop ได้ | ได้ ถ้า Catalog มาจาก TikTok Shop โดยตรง (รายละเอียดเต็มใน Step 679) | ไม่มีแนวคิด "TikTok Shop" แต่ Facebook มี Shop/Marketplace แยกอีกระบบ |

### ความแตกต่างสำคัญที่ต้องเข้าใจ: Product Sales ไม่ใช่แค่ "Website Conversion ที่มีรูปสินค้า"

ข้อผิดพลาดที่พบบ่อยคือคิดว่า Product Sales เป็นแค่ Website Conversion Objective ที่ใส่ Catalog เข้าไปเฉย ๆ แต่จริง ๆ Product Sales Objective เปิดให้ระบบทำ **Dynamic Creative จาก Catalog อัตโนมัติเต็มรูปแบบ** (ดึงรูป ราคา ชื่อสินค้า สร้างเป็นวิดีโอ/Ad Format อัตโนมัติ) ซึ่ง Website Conversion Objective ธรรมดาไม่มีความสามารถนี้ ถ้าธุรกิจมี Catalog สินค้าจำนวนมาก (มากกว่า 20-30 SKU) ควรพิจารณา Product Sales Objective แทน Website Conversion ธรรมดาเสมอ เพื่อใช้ประโยชน์จาก Dynamic Creative และ Dynamic Retargeting

---

## Step 679: TikTok Shop-Specific Objectives และ GMV Max

### ทำไม TikTok Shop ต้องมี Objective แยกจากธุรกิจ Website ทั่วไป

TikTok Shop คือระบบ e-Commerce ในตัวแอป TikTok เอง (คนซื้อขายจบในแอปโดยไม่ต้องออกไปเว็บไซต์ภายนอก) ซึ่ง **Facebook ไม่มีระบบที่เทียบเท่ากันโดยตรง** (Facebook Shop/Marketplace มีแนวคิดคล้ายกันบางส่วนแต่ไม่ได้ผูกกับ Ads Objective ในระดับเดียวกับ TikTok Shop) ทำให้ Objective กลุ่มนี้เป็นสิ่งที่คนมาจาก Facebook ต้องเรียนรู้ใหม่ทั้งหมด

### Objective/โหมดที่เกี่ยวกับ TikTok Shop โดยตรง

| ชื่อ | ลักษณะ | เหมาะกับ |
|---|---|---|
| **Product Sales (Promotion Type = TikTok Shop)** | เลือก Objective Product Sales แล้วกำหนด Promotion Type เป็น TikTok Shop ตอนสร้าง Ad Group แทน Website | ธุรกิจที่ตั้ง Shop ใน TikTok Shop แล้วต้องการโปรโมทสินค้าเฉพาะตัว/กลุ่มสินค้า |
| **GMV Max** | โหมด Automation เต็มรูปแบบที่ให้ AI จัดการ Budget, Bid, Targeting, และเลือกสินค้าที่จะโปรโมทจาก Shop เพื่อ Maximize **GMV (Gross Merchandise Value)** โดยอัตโนมัติ | ธุรกิจที่มี Shop พร้อม Catalog สินค้าจำนวนมากและมี Sales History สะสมแล้ว ต้องการ Scale แบบไม่ต้องจัดการโครงสร้างมือทั้งหมด |
| **Live Shopping Ads** | โปรโมท LIVE Session ของแบรนด์บน TikTok Shop โดยตรง ดึงคนเข้าชม LIVE ที่กำลังขายสินค้าอยู่ | ธุรกิจที่ทำ LIVE Commerce เป็นประจำ |
| **Video Shopping Ads (VSA)** | โปรโมทวิดีโอ Organic ที่ Tag สินค้า TikTok Shop ไว้ (คล้าย Spark Ads แต่เจาะจงกับ Shop) | ธุรกิจที่มี UGC/Creator Content ที่ Tag สินค้าอยู่แล้ว |

### GMV Max เจาะลึกเบื้องต้น (รายละเอียดเต็มอยู่ใน Part 076)

GMV Max ทำงานคล้าย Smart+ Campaigns (Part 067 Step 667) แต่เจาะจงกับ TikTok Shop โดยเฉพาะ ต่างจาก Smart+ Catalog Ads ตรงที่ GMV Max **รวม LIVE Content, Video Content และ Product Card เข้าด้วยกันในแคมเปญเดียว** และ Optimize เพื่อ GMV (มูลค่าการขายรวม) ไม่ใช่แค่จำนวน Conversion หรือ ROAS — ธุรกิจที่ใช้ GMV Max มักไม่ต้องสร้างโครงสร้าง Campaign > Ad Group > Ad แบบดั้งเดิมเลย เพราะระบบจัดการเกือบทุกอย่างอัตโนมัติ

### ตารางเทียบ TikTok Shop Objective กับสิ่งที่ใกล้เคียงที่สุดใน Facebook

| TikTok Shop Feature | สิ่งที่ใกล้เคียงที่สุดใน Facebook | ระดับความเทียบเท่า |
|---|---|---|
| Product Sales (Promotion Type: TikTok Shop) | Advantage+ Catalog Ads ที่ผูกกับ Facebook Shop | เทียบเท่าบางส่วน (Facebook Shop ไม่ได้แพร่หลายเท่า TikTok Shop ในตลาดไทย) |
| GMV Max | Advantage+ Shopping Campaigns (ASC) | ใกล้เคียงในแนวคิด Automation แต่ TikTok ผูกกับ LIVE ด้วย ซึ่ง Facebook ไม่มี |
| Live Shopping Ads | ไม่มีเทียบเท่าตรง ๆ | Facebook Live ไม่มีระบบโฆษณาผูก Live Commerce แบบ TikTok |
| Video Shopping Ads | ใกล้เคียง Boosted Post ที่ Tag สินค้าจาก Facebook Shop | ใกล้เคียงบางส่วน |

### ข้อควรระวังก่อนใช้ TikTok Shop Objectives

- ต้องเปิด **TikTok Shop Seller Account** และผ่านการอนุมัติก่อน ไม่ใช่แค่มี TikTok Business Account ธรรมดา
- Catalog ต้องซิงค์สินค้า สต็อก และราคาให้ตรงกับความเป็นจริงตลอดเวลา เพราะ TikTok Shop เป็นระบบซื้อขายจริงในแอป ถ้าสต็อกไม่ตรงจะกระทบ Order จริงทันที ไม่ใช่แค่กระทบ Traffic เหมือน Website Objective
- ค่าธรรมเนียม TikTok Shop (Commission) เป็นค่าใช้จ่ายเพิ่มเติมจากค่าโฆษณา ต้องคำนวณ Unit Economics ทั้งสองส่วนรวมกัน (เชื่อมโยงกับ Part 003 Step 24 เรื่อง Unit Economics)

---

## Step 680: Workshop — Objective Selection Framework: Mapping Business Goal สู่ TikTok Objective

### กรอบการตัดสินใจ 4 คำถามก่อนเลือก Objective

ก่อนเลือก Objective ทุกครั้ง ให้ตอบ 4 คำถามนี้ตามลำดับ:

1. **ธุรกิจอยู่ Funnel Stage ไหน** — ยังไม่มีคนรู้จักเลย (Awareness) / มีคนรู้จักแล้วแต่ยังไม่ตัดสินใจ (Consideration) / พร้อมปิดการขายแล้ว (Conversion)?
2. **มี Pixel/Event/Catalog พร้อมหรือยัง** — ถ้ายังไม่มี Volume Event เพียงพอ อาจต้องเริ่มที่ Objective ระดับ Consideration ก่อนสะสม Data
3. **ขายผ่านช่องทางไหน** — Website ภายนอก, App, หรือ TikTok Shop? (แต่ละช่องทางมี Objective ที่ถูกออกแบบมาเฉพาะ)
4. **ผลลัพธ์ปลายทางที่วัดความสำเร็จจริงคืออะไร** — ยอดขาย, Lead, Install, หรือแค่การรับรู้?

### ตาราง Mapping ธุรกิจเป้าหมาย → TikTok Objective → Facebook Objective เทียบเคียง

| เป้าหมายธุรกิจ | TikTok Objective ที่แนะนำ | Facebook Objective เทียบเคียง | หมายเหตุ |
|---|---|---|---|
| เปิดตัวแบรนด์/สินค้าใหม่ ให้คนรู้จักก่อน | Reach | Awareness (Reach) | ใช้งบจำกัดช่วงเวลา ไม่ใช่งบต่อเนื่องระยะยาว |
| สร้าง Traffic เข้าเว็บที่ยังไม่มี Pixel Data สะสม | Traffic | Traffic | ชั่วคราวเท่านั้น ควรเปลี่ยนเมื่อมี Data พอ |
| ต้องการยอด Follower/Engagement บนโปรไฟล์ | Community Interaction | Engagement | ผลทางอ้อมต่อยอดขาย |
| สร้าง Pool คนดูวิดีโอราคาถูกเพื่อ Retarget ต่อ | Video Views | (ThruPlay ใต้ Objective อื่น) | TikTok แยกเป็น Objective หลัก ต่างจาก Facebook |
| ธุรกิจแอปมือถือ ต้องการยอด Install | App Install | App Promotion (Install) | ต้องเชื่อม MMP ก่อน |
| ธุรกิจแอป ต้องการ In-app Purchase/Subscribe | App Conversion | App Promotion (App Event) | ต้องมี In-App Event Volume พอ |
| ธุรกิจต้องการ Lead (ประกัน, คอร์ส, อสังหาฯ) | Lead Generation | Leads (Instant Form) | เพิ่ม Qualifying Question เสมอ |
| ธุรกิจขายผ่านเว็บไซต์ มี Pixel พร้อม | Website Conversion | Sales (Conversion) | หัวใจของแคมเปญ Performance ส่วนใหญ่ |
| ธุรกิจมี Catalog สินค้าจำนวนมาก | Product Sales | Catalog Sales / Dynamic Ads | ใช้ Dynamic Creative จาก Catalog |
| ธุรกิจขายผ่าน TikTok Shop โดยตรง มี Data สะสมแล้ว | GMV Max | Advantage+ Shopping (ใกล้เคียงบางส่วน) | Automation เต็มรูปแบบ ผูก LIVE ด้วย |
| ธุรกิจทำ LIVE Commerce เป็นประจำ | Live Shopping Ads | ไม่มีเทียบเท่าตรง | เฉพาะ TikTok Shop เท่านั้น |

### Framework แบบ Flowchart ที่ใช้งานได้ทันที

```
START
  │
  ▼
มี Pixel/Catalog/Shop พร้อมหรือยัง?
  │
  ├─ ยังไม่มี Data สะสมเลย ──► ต้องการอะไรตอนนี้?
  │                              ├─ แค่ให้คนรู้จัก ──► Reach
  │                              ├─ อยากได้ Follower/Engagement ──► Community Interaction
  │                              └─ อยากได้ Traffic เข้าเว็บ ──► Traffic (ชั่วคราว)
  │
  └─ มี Data สะสมพอแล้ว ──► ขายช่องทางไหน?
                              ├─ Website ภายนอก ──► มี Catalog สินค้ามากไหม?
                              │                        ├─ ใช่ ──► Product Sales
                              │                        └─ ไม่ ──► Website Conversion
                              ├─ App ──► App Conversion
                              ├─ Lead-based Business ──► Lead Generation
                              └─ TikTok Shop ──► มี Sales History สะสมพอไหม?
                                                   ├─ ใช่ ──► GMV Max
                                                   └─ ไม่ ──► Product Sales (Promotion Type: TikTok Shop) ก่อน
```

---

## Case Study: ร้านเครื่องสำอาง SME ย้ายจาก Facebook Sales มายิง TikTok แล้วเลือก Objective ผิดในเดือนแรก

### สถานการณ์

"ร้าน B" เป็นแบรนด์เครื่องสำอางที่ยิง Facebook Conversion Objective มาแล้ว 8 เดือน มี Pixel และ Catalog พร้อมสมบูรณ์ ทำ ROAS เฉลี่ย 4.2 บน Facebook เจ้าของแบรนด์ตัดสินใจขยายมายิง TikTok เพราะเห็นคู่แข่งในกลุ่มเดียวกันเริ่มยิง TikTok แล้วได้ผลดี

### ข้อมูลเบื้องหลังธุรกิจก่อนย้ายมา TikTok

ร้าน B ขายเครื่องสำอางกลุ่ม Skincare ราคาเฉลี่ยต่อออเดอร์ 890 บาท มี Margin ขั้นต้นประมาณ 53% (COGS รวมค่าจัดส่งอยู่ที่ราว 420 บาท) ทำให้ Breakeven CPA อยู่ที่ประมาณ 470 บาท เจ้าของแบรนด์ตั้งงบทดสอบ TikTok เดือนแรกไว้ที่ 45,000 บาท โดยแบ่งเป็น 3 สัปดาห์ทดลอง Objective ต่างกัน แต่เพราะความไม่มั่นใจของทีมงาน ทำให้ตัดสินใจใช้ Objective เดียว (Traffic) ตลอดทั้งเดือนแรกโดยไม่ได้วางแผนทดสอบเทียบ Objective คู่กันตั้งแต่ต้น ซึ่งเป็นจุดที่ควรทำตาม Framework ใน Step 680 แต่ทีมงานยังไม่เคยเรียนรู้มาก่อนตอนนั้น

### สิ่งที่ทำผิดในเดือนแรก

ทีมงานที่ดูแลแคมเปญ (ซึ่งมีพื้นฐาน Facebook แน่นมาก) เข้าไปสร้างแคมเปญ TikTok แคมเปญแรกโดยเลือก **Traffic Objective** เพราะให้เหตุผลว่า "ยังไม่มั่นใจว่า TikTok Pixel จะทำงานได้ดีเท่า Facebook เลยอยากเริ่มแบบปลอดภัยก่อน ดูคนคลิกเข้าเว็บก่อน" ทั้งที่จริง ๆ TikTok Pixel ติดตั้งและ Verify Domain สมบูรณ์แล้วตั้งแต่ Part 066 (สมมติว่าผ่านมาแล้ว) และมี Standard Event Purchase พร้อมยิงได้ทันที

ผลลัพธ์เดือนแรก: CPC ถูกมาก (2.8 บาท/คลิก) CTR สูง (3.1%) แต่ Purchase ที่เกิดขึ้นจริงมีเพียง 6 ครั้งจากงบ 45,000 บาท (CPA เท่ากับ 7,500 บาท ทั้งที่สินค้าเฉลี่ยราคาแค่ 890 บาท) — ขาดทุนหนักมาก ทีมงานเริ่มสรุปผิดว่า "TikTok Ads ไม่เหมาะกับธุรกิจนี้"

### การวินิจฉัยปัญหา

เมื่อวิเคราะห์ Traffic ที่เข้ามาพบว่า Traffic ส่วนใหญ่เป็นคนที่คลิกเพราะ Creative น่าสนใจ (Curiosity Click) แต่ไม่ใช่กลุ่มที่มีความตั้งใจซื้อจริง เพราะ Traffic Objective ถูก Optimize เพื่อหา "คนที่มีโอกาสคลิกสูงสุด" ไม่ใช่ "คนที่มีโอกาสซื้อสูงสุด" — Machine Learning ของ TikTok ทำงานตามที่ Objective สั่งถูกต้องทุกประการ ปัญหาไม่ได้อยู่ที่ TikTok Ads แต่อยู่ที่ Objective ที่เลือกไม่ตรงกับความพร้อมของ Data ที่มี

### การแก้ไข

เดือนที่ 2 ทีมงานเปลี่ยนมาสร้างแคมเปญใหม่ด้วย **Website Conversion Objective** Optimize เพื่อ Complete Payment ตรง ๆ (เพราะ Volume Purchase สะสมจาก Facebook Pixel เดิมและ TikTok Pixel ที่เริ่มยิง Event มาแล้ว 1 เดือนรวมกันเพียงพอสำหรับ Learning Phase) ใช้ Ad Group แบบ Broad Targeting ไม่แบ่งย่อยตามหลัก Consolidation (Part 067 Step 668) และใช้ Creative แบบ UGC Native ที่ผลิตใหม่เฉพาะสำหรับ TikTok (ไม่ใช่ Creative ที่ตัดมาจาก Facebook)

### ผลลัพธ์เดือนที่ 2-3

CPA ลดลงมาอยู่ที่ 620 บาท (ยังสูงกว่า Facebook เล็กน้อยที่ 480 บาท แต่ยังทำกำไรได้เพราะ Margin สินค้าเพียงพอ) และเมื่อเข้าเดือนที่ 3 หลัง Ad Group ผ่าน Learning Phase อย่างมั่นคง CPA ลดลงมาอยู่ที่ 510 บาท ใกล้เคียง Facebook มากขึ้น ทีมงานสรุปบทเรียนว่า "TikTok ไม่ได้แย่กว่า Facebook แต่ต้องเลือก Objective ให้ตรงกับความพร้อมของ Data เหมือนที่เคยเรียนรู้มาแล้วตอนเริ่ม Facebook Conversion Campaign ครั้งแรกเมื่อ 8 เดือนก่อน"

### บทเรียนสำคัญจาก Case นี้

ความเข้าใจผิดว่า "Objective ระดับล่างของ Funnel ปลอดภัยกว่าเสมอ" เป็นกับดักที่พบบ่อยที่สุดในคนย้ายจาก Facebook มา TikTok เพราะกลัวว่า TikTok Machine Learning จะยังไม่ดีพอ ทั้งที่ในความจริง TikTok Machine Learning ทำงานตามหลักการเดียวกับ Facebook และควรได้รับโอกาสทำงานเต็มที่ตั้งแต่ Objective ที่ตรงกับความพร้อมของ Data จริง ไม่ใช่ Objective ที่ "รู้สึกปลอดภัย" กว่า

---

## Case Study เสริม: แอปฟินเทคเลือก App Install ทั้งที่ควรใช้ App Conversion ตั้งแต่ต้น

### สถานการณ์

สตาร์ทอัพฟินเทค "แอป C" ปล่อยแอปกู้เงินรายย่อยมาแล้ว 4 เดือน มี MMP (AppsFlyer) เชื่อมกับ TikTok เรียบร้อย และมี In-App Event "Loan Application Submitted" กับ "Loan Approved" ที่ยิงเข้า TikKok ผ่าน App Events API มาสม่ำเสมอ (เฉลี่ย 300 Loan Application/สัปดาห์) ทีม Marketing ตั้งแคมเปญด้วย **App Install Objective** ต่อเนื่องมา 4 เดือนเพราะ "ต้องการยอด Install เพิ่มก่อน แล้วค่อยดูว่าใครสมัครกู้บ้าง"

### ปัญหาที่เกิดขึ้น

ยอด Install เพิ่มขึ้นเรื่อย ๆ ในราคาต่อ Install ที่ถูกมาก (18 บาท/Install) ทำให้ทีมงานพอใจกับตัวเลขนี้มาตลอด แต่เมื่อเจ้าของธุรกิจถามหา "จำนวนคนที่สมัครกู้จริงจากงบโฆษณา" พบว่า Conversion Rate จาก Install ไปสู่ Loan Application ต่ำมากเพียง 4% เท่านั้น (ต่ำกว่าค่าเฉลี่ยอุตสาหกรรมที่ควรอยู่ราว 12-15%) เมื่อคำนวณ CPA ต่อ Loan Application จริงพบว่าสูงถึง 450 บาท/Application ทั้งที่ธุรกิจตั้งเป้า Breakeven ไว้ที่ 180 บาท/Application เท่านั้น

### การวินิจฉัย

สาเหตุคือ App Install Objective Optimize เพื่อหา "คนที่มีโอกาส Install สูงสุด" ซึ่งเป็นคนละกลุ่มกับ "คนที่มีโอกาสสมัครกู้เงินจริง" — คนที่ Install ง่ายมักเป็นกลุ่มที่ Install แอปหลากหลายบ่อย ๆ (Serial Installer) ไม่ใช่กลุ่มที่มีความต้องการทางการเงินจริงจัง ทั้งที่ธุรกิจมี In-App Event ที่มีค่าทางธุรกิจสูงกว่าพร้อมใช้งานมาตลอด 4 เดือน แต่ไม่เคยสั่งให้ระบบ Optimize เพื่อ Event นั้นเลย

### การแก้ไขและผลลัพธ์

เปลี่ยนมาใช้ **App Conversion Objective** Optimize เพื่อ "Loan Application Submitted" ตรง ๆ โดยใช้ Ad Group เดิมที่มี Audience กว้างพอ ผลลัพธ์ในเดือนถัดมา: ราคาต่อ Install เพิ่มขึ้นเป็น 34 บาท (แพงขึ้นเกือบ 2 เท่า) แต่ Conversion Rate จาก Install ไปสู่ Loan Application เพิ่มเป็น 19% และ CPA ต่อ Loan Application จริงลดลงมาอยู่ที่ 165 บาท ต่ำกว่าเป้า Breakeven ที่ตั้งไว้ — บทเรียนคือ **ราคาต่อ Action ระดับบนของ Funnel ที่ถูกกว่า ไม่ได้แปลว่าธุรกิจจะได้ผลลัพธ์ที่ดีกว่าเสมอ ถ้า Action นั้นไม่ใช่ Action ที่มีมูลค่าทางธุรกิจจริง**

---

## Checklist ท้ายบท

ก่อนสร้างแคมเปญ TikTok ทุกครั้ง ให้ตรวจสอบตามลำดับนี้:

- [ ] รู้ชัดเจนว่าธุรกิจอยู่ Funnel Stage ไหน (Awareness/Consideration/Conversion) ก่อนเปิดหน้า Create Campaign
- [ ] ตรวจสอบว่า Pixel/App Events API/Catalog พร้อมและมี Volume Event เพียงพอสำหรับ Objective ระดับ Conversion หรือไม่
- [ ] ถ้าธุรกิจขายผ่าน TikTok Shop ตรวจสอบว่า Seller Account ผ่านการอนุมัติและ Catalog Sync เรียบร้อยก่อนเลือก Objective กลุ่ม Shop
- [ ] ไม่เลือก Objective ที่ "รู้สึกปลอดภัยกว่า" (เช่น Traffic) ทั้งที่มี Data พร้อมสำหรับ Conversion Objective แล้ว
- [ ] ตรวจสอบว่า Optimization Event ที่จะเลือกใน Ad Group มี Volume มากกว่า ~50 Event/สัปดาห์ ก่อนเลือก Optimize เพื่อ Event นั้น
- [ ] ถ้าเลือก Website Conversion และมี Order Value ให้ส่ง Value/Currency ไปกับ Purchase Event เพื่อเปิดใช้ Value Optimization
- [ ] ถ้าเลือก Lead Generation เพิ่มคำถามคัดกรอง (Qualifying Question) อย่างน้อย 1-2 ข้อในฟอร์มเสมอ
- [ ] จดบันทึกไว้ว่า Objective ที่เลือกในแคมเปญนี้คืออะไร เพราะเปลี่ยนไม่ได้หลังสร้างแคมเปญแล้ว
- [ ] ถ้าธุรกิจมี Catalog สินค้าจำนวนมาก พิจารณา Product Sales Objective แทน Website Conversion ธรรมดาเพื่อใช้ Dynamic Creative
- [ ] เทียบ Objective ที่เลือกกับตาราง Mapping ใน Step 680 อีกครั้งก่อนกด Publish จริง

---

## Workshop / แบบฝึกหัด

### ส่วนที่ 1: วิเคราะห์ธุรกิจ 5 แบบ แล้วเลือก Objective ให้ถูก

สมมติสถานการณ์ 5 ธุรกิจต่อไปนี้ ให้เขียนคำตอบว่าควรเลือก TikTok Objective อะไร พร้อมให้เหตุผลอ้างอิงจาก Framework ใน Step 680:

1. แอปเรียนภาษาที่เพิ่งเปิดตัว ยังไม่มี User เลย ต้องการยอด Install เดือนแรก 5,000 ครั้ง
2. คลินิกความงามที่มี Pixel ยิง Lead Form มา 3 เดือนแล้ว มี Lead สะสม 400 รายการ ต้องการเพิ่ม Lead ต่อเดือน
3. แบรนด์เสื้อผ้าที่เพิ่งเปิด TikTok Shop มี Catalog 150 SKU แต่ยังไม่มี Order เลยแม้แต่ 1 รายการ
4. ร้านขายอุปกรณ์ครัวที่มี Pixel Purchase Event มา 6 เดือน เฉลี่ย 80 Purchase/สัปดาห์ ROAS บน Facebook อยู่ที่ 3.5
5. YouTuber/Creator ที่ต้องการเพิ่ม Follower บน TikTok เพื่อขยายฐานผู้ชมก่อนเริ่มขายคอร์สออนไลน์ในอีก 3 เดือนข้างหน้า

### ส่วนที่ 2: สร้าง Draft Campaign จริงใน TikTok Ads Manager

เลือกธุรกิจของตัวเอง/ลูกค้า 1 ราย แล้วทำตามขั้นตอน:

1. เปิด TikTok Ads Manager ในโหมด Custom Mode
2. เข้าหน้า Create Campaign แล้ว Screenshot หน้าจอ Objective ทั้ง 3 กลุ่มที่ปรากฏจริงในปี 2026 (เผื่อ TikTok ปรับ UI/ชื่อ Objective เพิ่มเติม)
3. เลือก Objective ที่เหมาะกับธุรกิจตาม Framework ที่เรียนไป บันทึกเป็น Draft (ไม่ต้อง Publish จริง)
4. เขียนสรุป 3-5 บรรทัดว่าทำไมเลือก Objective นี้ อ้างอิงจาก 4 คำถามใน Step 680

### ส่วนที่ 3: ทำตาราง Objective Comparison ของตัวเอง

สร้างตาราง (ใน Google Sheets หรือกระดาษ) เทียบ Objective ที่ธุรกิจ/ลูกค้าของตัวเองใช้อยู่บน Facebook กับ Objective ที่ควรใช้บน TikTok สำหรับสินค้า/บริการเดียวกัน อย่างน้อย 3 แคมเปญ โดยระบุเหตุผลของแต่ละแถวตามความพร้อมของ Data จริง

### ส่วนที่ 4: คำนวณ Breakeven CPA ของธุรกิจตัวเองก่อนเลือก Objective ระดับ Conversion

ใช้สูตรจาก Step 677 คำนวณ Breakeven CPA ของสินค้า/บริการหลักที่จะโปรโมทบน TikTok:

```
AOV (ราคาขายเฉลี่ยต่อออเดอร์) = ______ บาท
COGS (ต้นทุนสินค้า + ค่าจัดส่ง + ค่าคอมมิชชัน TikTok Shop ถ้ามี) = ______ บาท
กำไรขั้นต้นก่อนค่าโฆษณา = AOV - COGS = ______ บาท
Breakeven CPA = ______ บาท
เป้าหมาย CPA จริง (เผื่อ Margin ปลอดภัย 30%) = Breakeven CPA x 0.7 = ______ บาท
```

บันทึกตัวเลขนี้ไว้เป็นเกณฑ์อ้างอิงก่อนเริ่มแคมเปญจริง แล้วนำไปเทียบกับ CPA ที่เกิดขึ้นจริงในสัปดาห์ที่ 2 หลัง Ad Group ผ่าน Learning Phase

### ส่วนที่ 5: เขียน Objective Decision Log

ทุกครั้งที่สร้างแคมเปญใหม่ ให้บันทึกลง Decision Log (Google Sheets 1 แถวต่อแคมเปญ) ประกอบด้วยคอลัมน์: วันที่สร้าง, ชื่อแคมเปญ, Objective ที่เลือก, เหตุผลที่เลือก (อ้างอิง 4 คำถามจาก Step 680), Volume Event ที่มีตอนสร้าง, และ CPA/ผลลัพธ์จริงหลัง 2 สัปดาห์ — Log นี้จะกลายเป็นข้อมูลอ้างอิงสำคัญเมื่อต้องตัดสินใจเลือก Objective สำหรับแคมเปญถัดไป หรือเมื่อต้องอธิบายผลลัพธ์ให้เจ้าของธุรกิจ/ลูกค้าฟัง

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ไล่ทุก Objective ของ TikTok ครบทั้ง 3 กลุ่ม (Awareness, Consideration, Conversion) พร้อมเทียบกับ Facebook Objective ที่ใกล้เคียงที่สุดตลอดทั้งบท ประเด็นสำคัญที่สุดที่ต้องจำคือ **Objective ต้องเลือกตามความพร้อมของ Data และผลลัพธ์ทางธุรกิจจริง ไม่ใช่ตามชื่อที่ฟังดูปลอดภัยหรือคุ้นเคย** และ TikTok มี Objective เฉพาะที่ Facebook ไม่มี (Community Interaction, Video Views, TikTok Shop Objectives รวม GMV Max) ที่ต้องเรียนรู้ใหม่แยกจากพื้นฐาน Facebook

Objective ที่เลือกในระดับ Campaign เป็นเพียงจุดเริ่มต้น — ขั้นต่อไปที่ต้องเข้าใจให้แม่นคือการตั้งค่า **Budget, Bid Strategy, และ Optimization Goal** ที่ระดับ Ad Group ซึ่งเป็นตัวกำหนดว่าเงินที่จ่ายไปจะถูกใช้อย่างมีประสิทธิภาพแค่ไหน แม้จะเลือก Objective ถูกต้องแล้ว แต่ถ้าตั้ง Budget/Bid ผิด ก็ยังทำให้แคมเปญไม่ได้ผลลัพธ์ที่ควรจะเป็น — เนื้อหาเรื่องนี้ทั้งหมดจะอยู่ใน **Part 069: TikTok Budget, Bidding, Optimization Goal** ซึ่งเป็น Part ต่อไปทันที

---

## หมายเหตุปิดท้าย: Objective ไม่ใช่สิ่งที่ตั้งครั้งเดียวแล้วจบ

ข้อควรจำสุดท้ายก่อนปิด Part นี้คือ การเลือก Objective ที่ถูกต้องในวันแรกไม่ได้แปลว่าธุรกิจจะใช้ Objective เดียวนั้นตลอดไป เมื่อธุรกิจสะสม Data มากขึ้น (เช่น จาก Website Conversion ไปสู่การมี Catalog มากพอสำหรับ Product Sales หรือจาก Product Sales ไปสู่ GMV Max เมื่อมี TikTok Shop Sales History สะสมพอ) ควรกลับมาทบทวน Framework ใน Step 680 ทุกไตรมาสว่า Objective ที่ใช้อยู่ยังตรงกับความพร้อมของ Data และเป้าหมายธุรกิจปัจจุบันหรือไม่ — หลักการ "ทบทวนเป็นระยะ" นี้เหมือนกับที่เรียนไปแล้วในฝั่ง Facebook เรื่อง Scaling Strategy (Part 058) ที่ต้องประเมินโครงสร้างแคมเปญใหม่เมื่อธุรกิจโตขึ้น ไม่ใช่ยึดติดกับโครงสร้างเดิมตลอดไป

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- TikTok for Business — Campaign Objectives (เอกสารทางการ TikTok Ads Manager, ตรวจสอบ UI ปัจจุบันเสมอเพราะมีการปรับชื่อ/จัดกลุ่ม Objective เป็นระยะ)
- TikTok Shop Seller Center — เอกสารเกี่ยวกับ GMV Max, Live Shopping Ads, Video Shopping Ads
- TikTok Marketing API Documentation — สำหรับทีมที่ต้องการเชื่อม App Events API/MMP ระดับลึก
- Meta Business Help Center — Campaign Objectives (สำหรับเทียบเคียงกับ Part 017 ของหลักสูตรนี้)
- Part 013–015 ของหลักสูตรนี้ — พื้นฐาน Pixel/CAPI/Events Manager ฝั่ง Facebook ที่ใช้อ้างอิงเทียบเคียงตลอด Part นี้
- Part 066 ของหลักสูตรนี้ — TikTok Pixel และ Events API ที่ต้องพร้อมก่อนเลือก Objective ระดับ Conversion
- Part 076 ของหลักสูตรนี้ — TikTok Shop Ads แบบเจาะลึกรวม GMV Max (สำหรับผู้ที่ต้องการรายละเอียดเพิ่มจาก Step 679)
