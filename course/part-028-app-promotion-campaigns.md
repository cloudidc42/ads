# Part 028: สร้างแคมเปญ App Promotion

**Section:** C — Facebook Ads Manager Deep Dive: Setup & Structure
**Step ที่ครอบคลุม:** Step 271–280 (จาก 1000 Steps ทั้งหลักสูตร)
**เวลาที่ใช้เรียนโดยประมาณ:** 5–6 ชั่วโมง (รวมเวลาทำความเข้าใจการเชื่อม SDK/MMP ซึ่งต้องมีความรู้ Technical ร่วมด้วย)

Part นี้เปลี่ยนบริบทจากอีคอมเมิร์ซใน Part 027 มาสู่โลกของ **App Promotion** — การโปรโมทแอปพลิเคชันมือถือให้คนดาวน์โหลดและใช้งาน ถ้าคุณรับงานจากธุรกิจที่มีแอปของตัวเอง (แอปสั่งอาหาร แอปธนาคาร แอปเกม แอปฟิตเนส แอป Delivery) เนื้อหานี้คือทักษะเฉพาะทางที่ต่างจากการยิงแอด Traffic/Conversion ทั่วไปพอสมควร เพราะมีชั้นของ Technical Integration (SDK, MMP, SKAdNetwork) เข้ามาเกี่ยวข้องซึ่งนักยิงแอดต้องเข้าใจแม้จะไม่ได้เป็นคนเขียนโค้ดเอง

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 271:** App Promotion Objective คืออะไร ต่างจาก Objective อื่นในโครงสร้างอย่างไร
2. **Step 272:** เชื่อมแอปกับ Facebook ผ่าน App Events — Facebook SDK, การลงทะเบียนแอปใน Meta for Developers
3. **Step 273:** MMP (Mobile Measurement Partner) คืออะไร — AppsFlyer, Adjust, Branch, Singular และวิธีเชื่อมกับ Meta
4. **Step 274:** เลือก Optimization Event ที่เหมาะสม — Install, In-app Event, Value Optimization
5. **Step 275:** โครงสร้างแคมเปญ App Ads แบบ Step-by-Step ใน Ads Manager
6. **Step 276:** Creative Specs สำหรับ App Ads — Playable Ads, Video, App Preview, End Card
7. **Step 277:** Advantage+ App Campaigns เบื้องต้น
8. **Step 278:** iOS14+ และ SKAdNetwork — ผลกระทบและการปรับตัวสำหรับแคมเปญแอป
9. **Step 279:** งบประมาณ, CPI/CPA Benchmark, และการอ่านผลลัพธ์แคมเปญแอปให้ถูกต้อง
10. **Step 280:** ข้อผิดพลาดที่พบบ่อยในการยิงแอด App Install พร้อม Workshop วางแผนแคมเปญ App Install จริง

---

## Step 271: App Promotion Objective คืออะไร ต่างจาก Objective อื่นอย่างไร

### นิยามและตำแหน่งใน Ads Manager

**App Promotion** เป็นหนึ่งใน 6 Objective หลักของ Meta Ads (Awareness, Traffic, Engagement, Leads, App Promotion, Sales — ทบทวนจาก Part 017) ที่ออกแบบมาเฉพาะสำหรับธุรกิจที่ต้องการให้คนทำ 2 อย่างหลัก:

1. **ติดตั้งแอป (App Install)** — เป้าหมายคือให้คนที่ยังไม่มีแอปกดดาวน์โหลดจาก App Store/Google Play
2. **ทำกิจกรรมภายในแอป (In-app Event/Engagement)** — เป้าหมายคือให้คนที่มีแอปอยู่แล้วกลับมาเปิดใช้ ทำ Action บางอย่าง เช่น สมัครสมาชิก, เติมเงิน, สั่งซื้อในแอป

### ความแตกต่างสำคัญจาก Traffic/Conversion Objective

| ประเด็น | Traffic/Sales Objective (เว็บไซต์) | App Promotion Objective |
|---|---|---|
| ปลายทางที่คนคลิกไปถึง | หน้าเว็บไซต์ | หน้า App Store / Google Play หรือเปิดแอปที่มีอยู่ตรง |
| เครื่องมือ Track ผลลัพธ์ | Pixel/Conversions API บนเว็บ | SDK ในแอป + MMP หรือ Meta App Events API |
| ตัวระบุผู้ใช้หลัง iOS14 | Cookie/Browser Signal | SKAdNetwork (iOS) / Google Play Install Referrer (Android) |
| หน่วยที่ Optimize | Purchase, Lead, PageView | Install, Registration, Purchase in-app, Level Achieved ฯลฯ |
| Creative ที่ใช้บ่อย | Image, Carousel, Video โชว์สินค้า/บริการ | Video Gameplay, Playable Ads, App Preview |

### เมื่อไหร่ควรเลือก App Promotion แทน Objective อื่น

- เมื่อธุรกิจมีแอปของตัวเองบน App Store/Google Play และต้องการเพิ่มยอดดาวน์โหลด → เลือก App Promotion แน่นอน อย่าใช้ Traffic Objective ยิงลิงก์ App Store เพราะจะขาดการเชื่อม SDK และ Meta จะ Optimize แบบ Traffic ทั่วไปที่ไม่รู้จัก Install Event เลย ทำให้ได้แต่คนคลิกลิงก์แต่ไม่ได้แปลงเป็น Install จริงในสัดส่วนที่ควรจะได้
- เมื่อธุรกิจมีทั้งเว็บไซต์และแอป และต้องการให้คนที่มีแอปอยู่แล้วกลับมาใช้งาน (Re-engagement) → ยังใช้ App Promotion Objective ได้ โดยเลือก Optimization Event เป็น In-app Event แทน Install (จะอธิบายใน Step 274)
- ถ้าธุรกิจมีแอปแต่ต้องการโปรโมทเนื้อหา/บทความในแอปแบบ Traffic ทั่วไปที่ไม่ใช่การกระตุ้น Install → บางกรณีใช้ Traffic Objective ร่วมกับ Deep Link ก็ได้ แต่ส่วนใหญ่แนะนำให้ใช้ App Promotion เพื่อให้ได้ประโยชน์จาก Machine Learning ที่เข้าใจ App Ecosystem โดยตรง

### ข้อผิดพลาดที่พบบ่อยตั้งแต่จุดเริ่มต้น

- เลือก Traffic Objective แล้วใส่ลิงก์ App Store ตรงๆ เพราะคิดว่าง่ายกว่า ทำให้เสียโอกาสในการ Optimize เพื่อ Install จริง และไม่มีข้อมูล Post-install Event ย้อนกลับมาปรับปรุงแคมเปญ
- ไม่รู้ว่าต้องเชื่อม SDK/MMP ก่อนสร้างแคมเปญ พอไปถึงหน้าสร้างแคมเปญแล้วหา App ไม่เจอในระบบ ต้องกลับไปทำ Technical Setup ก่อน (Step 272-273)
- คิดว่า App Promotion ใช้ได้แค่กับแอปเกม ทั้งที่จริงใช้ได้กับแอปทุกประเภท ธนาคาร อีคอมเมิร์ซ Delivery ฟิตเนส Dating ฯลฯ

### App Install กับ Web-to-App Funnel — กลยุทธ์ผสม

ธุรกิจจำนวนมากในปัจจุบันไม่ได้มีแค่แอปอย่างเดียว แต่มีทั้งเว็บไซต์และแอปทำงานร่วมกัน (เช่น ร้านค้าออนไลน์ที่มีทั้งเว็บและแอป Loyalty) กลยุทธ์ที่ใช้บ่อยคือ **Web-to-App Funnel**:

1. ใช้ Traffic/Sales Objective ดึงคนเข้าเว็บไซต์ก่อน (Prospecting ผ่านเว็บที่ต้นทุนต่ำกว่า)
2. หลังจากคนมีปฏิสัมพันธ์กับเว็บไซต์แล้ว (เช่น ดูสินค้า, สมัครสมาชิกบนเว็บ) ใช้ App Promotion Objective ยิง Retargeting ไปยัง Custom Audience ที่มาจาก Pixel เว็บไซต์ โดยข้อความโฆษณาเน้น "โหลดแอปวันนี้ รับส่วนลดเพิ่ม 100 บาท" เพื่อจูงใจให้ย้ายไปใช้แอปซึ่งปกติมี Retention และ LTV สูงกว่าเว็บไซต์
3. ใช้ Branch หรือ MMP ที่รองรับ Deferred Deep Linking (Step 273) เพื่อให้คนที่คลิกโฆษณาจากเว็บแล้วไป Install แอป เปิดแอปมาแล้วเจอหน้าสินค้าเดิมที่เคยดูบนเว็บทันที ไม่ต้องเริ่มค้นหาใหม่

วิธีนี้ช่วยลด CPI โดยรวมของธุรกิจ เพราะใช้เว็บไซต์เป็น "ตัวคัดกรอง" คนที่มี Intent จริงก่อน แล้วค่อยลงทุนงบ App Install กับกลุ่มที่มีโอกาส Convert สูงกว่าค่าเฉลี่ยตลาด

---

## Step 272: เชื่อมแอปกับ Facebook ผ่าน App Events — Facebook SDK

### ลงทะเบียนแอปใน Meta for Developers

ก่อนสร้างแคมเปญ App Promotion ได้ ต้องมี "App" ที่ลงทะเบียนไว้ใน Meta for Developers ก่อน ขั้นตอน:

1. ไปที่ **developers.facebook.com** > My Apps > **Create App**
2. เลือกประเภท Use Case: **"Other"** หรือ **"Consumer"** (ขึ้นอยู่กับประเภทแอป ถ้าไม่แน่ใจเลือก Consumer)
3. กรอกชื่อแอป (App Display Name) — ควรตรงกับชื่อแอปจริงบน Store เพื่อไม่ให้สับสน
4. เลือก Business Manager ที่จะผูกแอปนี้ (สำคัญ: ต้องเป็น Business Manager เดียวกับ Ad Account ที่จะใช้ยิงแคมเปญ)
5. ระบบจะสร้าง **App ID** และ **App Secret** ให้ — ค่าเหล่านี้ต้องส่งให้ทีม Developer นำไปฝัง SDK

### เชื่อม Ad Account เข้ากับ App

ไปที่ App Dashboard > Settings > Advanced > เชื่อม **Ad Account** ที่จะใช้ยิงแคมเปญโปรโมทแอปนี้ หรือทำผ่าน Business Manager > Business Settings > Data Sources > Apps > Add เพื่อผูก App เข้ากับ Business Manager โดยตรง

### Facebook SDK คืออะไร ทำหน้าที่อะไร

Facebook SDK for iOS/Android คือชุดโค้ดที่ทีม Developer นำไปติดตั้งในแอป ทำหน้าที่คล้าย Pixel บนเว็บไซต์ คือส่งข้อมูล Event ที่เกิดขึ้นในแอปกลับมาที่ Meta เช่น:

- `fb_mobile_activate_app` — แอปถูกเปิดครั้งแรก (เทียบเท่า Install)
- `fb_mobile_complete_registration` — ผู้ใช้สมัครสมาชิกสำเร็จ
- `fb_mobile_add_to_cart` — เพิ่มสินค้าลงตะกร้าในแอป
- `fb_mobile_purchase` — ซื้อสินค้า/บริการในแอปสำเร็จ พร้อม Value
- `fb_mobile_level_achieved`, `fb_mobile_tutorial_completion` — สำหรับแอปเกม/แอปที่มีขั้นตอนการเรียนรู้

### ขั้นตอนความร่วมมือกับทีม Developer (สิ่งที่นักยิงแอดต้องสื่อสารให้ถูก)

แม้นักยิงแอดไม่ต้องเขียนโค้ดเอง แต่ต้องเข้าใจและสื่อสารกับทีม Dev ได้ว่า:

1. ต้องติดตั้ง Facebook SDK เวอร์ชันล่าสุดตาม Official Documentation ของ Meta for Developers
2. ต้องยิง Event มาตรฐาน (Standard Events) ให้ครบตามที่ธุรกิจต้องการ Optimize (เช่น ถ้าเป็นแอป E-commerce ต้องมี AddToCart, Purchase พร้อม Value/Currency)
3. บน iOS ต้องตั้งค่า **App Tracking Transparency (ATT)** prompt ให้ถูกต้องตามนโยบาย Apple (ผู้ใช้ต้องกด Allow ก่อนถึงจะ Track แบบเต็มรูปแบบได้ — เกี่ยวเนื่องกับ Step 278)
4. ควรมีการ Test Event ผ่าน Meta Events Manager (เมนู "Test Events" เหมือนที่ใช้กับ Pixel เว็บไซต์ใน Part 015) ก่อนปล่อยแอปเวอร์ชันจริง เพื่อยืนยันว่า Event ถูกส่งมาจริงและมี Parameter ครบ

### ข้อผิดพลาดที่พบบ่อย

- ทีม Dev ติดตั้ง SDK แต่ไม่ยิง Purchase Event พร้อม Value ทำให้ Optimize ได้แค่ระดับ Install ไม่สามารถทำ Value Optimization ได้ (เสียโอกาสสำคัญ)
- ลงทะเบียน App ผิด Business Manager ทำให้ Ad Account ที่ต้องการใช้มองไม่เห็น App ตอนสร้างแคมเปญ
- ไม่ Test Event ก่อนขึ้นแอปเวอร์ชันจริง พบว่า Event ไม่ยิงหลังจากรันแคมเปญไปแล้วหลายวัน เสียงบไปกับ Learning Phase ที่ไม่มีข้อมูลป้อนกลับ

---

## Step 273: MMP (Mobile Measurement Partner) — AppsFlyer, Adjust, Branch, Singular

### ทำไมต้องมี MMP ทั้งที่มี Facebook SDK อยู่แล้ว

Facebook SDK ส่งข้อมูล Event เข้า Meta ได้ตัวเดียว แต่ธุรกิจส่วนใหญ่ยิงแอดหลายแพลตฟอร์มพร้อมกัน (Facebook, TikTok, Google Ads, Apple Search Ads) การมี SDK แยกของแต่ละแพลตฟอร์มฝังในแอปทั้งหมดจะซับซ้อนและซ้ำซ้อนมาก **MMP (Mobile Measurement Partner)** คือตัวกลางที่ทำหน้าที่:

1. รับ Event จากแอป (ติดตั้ง SDK ของ MMP ตัวเดียวในแอป)
2. **Attribution** — ตัดสินว่า Install หรือ Event นั้นมาจากแพลตฟอร์มโฆษณาไหน (Facebook, TikTok, Google, Organic) โดยใช้เทคนิค Fingerprinting/Click Attribution/SKAdNetwork
3. ส่งข้อมูลกลับไปยังทุกแพลตฟอร์มโฆษณาที่เชื่อมไว้พร้อมกัน (Postback) — ทำให้ Meta, TikTok, Google ต่างได้ข้อมูล Conversion ของตัวเองโดยไม่ต้องฝัง SDK แยก

### MMP ที่นิยมใช้และจุดเด่น

| MMP | จุดเด่น | เหมาะกับ |
|---|---|---|
| **AppsFlyer** | Market Share สูงสุดในตลาด, Ecosystem Integration กว้าง, Dashboard ละเอียด | ธุรกิจทุกขนาด โดยเฉพาะที่ยิงหลายแพลตฟอร์ม |
| **Adjust** | UI ใช้งานง่าย, แข็งแรงด้าน Fraud Prevention | ธุรกิจ Gaming และ Performance Marketing |
| **Branch** | เด่นด้าน Deep Linking ข้าม Platform (Web-to-App) | ธุรกิจที่มี Web และ App ทำงานร่วมกันแน่น (เช่น E-commerce ที่มีทั้งเว็บและแอป) |
| **Singular** | เด่นด้าน Marketing Analytics และ ROI Reporting ข้ามแพลตฟอร์ม | ทีม Data/Marketing ที่ต้องการ Dashboard รวมทุกช่องทางในที่เดียว |

### ขั้นตอนเชื่อม MMP กับ Meta (ภาพรวมที่นักยิงแอดต้องเข้าใจ)

1. ทีม Dev/Marketing Ops ตั้งค่า MMP Dashboard (เช่น AppsFlyer) ผูกกับแอปที่ลงทะเบียนไว้
2. ใน MMP Dashboard ไปที่ส่วน **"Integrated Partners"** หรือ **"Ad Networks"** ค้นหา "Facebook" แล้วกด Activate
3. ใส่ **App ID** ของ Meta ที่ได้จาก Step 272 ลงในช่องที่ MMP กำหนด เพื่อให้ MMP รู้ว่าต้องส่ง Postback ไปที่ Meta App ตัวไหน
4. เปิด **Postback Configuration** — เลือก Event ที่จะส่งกลับไปให้ Meta (เช่น Install, Registration, Purchase) พร้อมกำหนด Mapping ชื่อ Event ให้ตรงกับ Standard Event ของ Meta
5. ทดสอบด้วย **Test Device** ที่ MMP มีให้ ติดตั้งแอปเวอร์ชัน Debug แล้วดูว่า Event ส่งเข้า Meta Events Manager จริงหรือไม่

### Attribution Window ที่ต้องตกลงกันให้ชัด

MMP จะให้ตั้งค่า **Attribution Window** ว่าจะนับ Install/Event ว่ามาจากโฆษณาตัวไหนภายในกี่วันหลังคนคลิก/เห็นโฆษณา ค่ามาตรฐานที่ Meta ใช้คือ:
- **Click-through Attribution**: 7 วัน (คนคลิกโฆษณาแล้ว Install ภายใน 7 วัน นับเป็นผลจากโฆษณานั้น)
- **View-through Attribution**: 1 วัน (คนเห็นโฆษณาแล้ว Install ภายใน 1 วันโดยไม่ได้คลิก ก็นับได้ในบางกรณี)

ต้องตั้งค่า Attribution Window ใน MMP ให้สอดคล้องกับค่าที่ Meta ใช้ ไม่งั้นตัวเลข Install ที่ MMP รายงานกับที่ Meta Ads Manager รายงานจะไม่ตรงกัน ทำให้ทีมงาน/ลูกค้าสับสนว่าตัวเลขไหนถูก

### ข้อผิดพลาดที่พบบ่อย

- ตั้งค่า Postback Event Mapping ผิด (เช่น Map "Registration" ไปเป็น "Purchase" ใน Meta) ทำให้ Meta Optimize ผิดเป้าหมายโดยไม่รู้ตัว
- ไม่ตกลง Attribution Window ให้ตรงกันระหว่างทุกแพลตฟอร์มที่ยิงแอดพร้อมกัน ทำให้เปรียบเทียบ Performance ข้าม Platform ไม่ได้อย่างเป็นธรรม
- ลืมอัปเดต Postback Setting เมื่อเปลี่ยน App ID หรือสร้างแอปเวอร์ชันใหม่ (เช่น แยก iOS/Android เป็น App ID คนละตัว)

### ปัญหา Multi-touch Attribution และ Duplicate Conversion

เมื่อธุรกิจยิงหลายแพลตฟอร์มพร้อมกัน (Facebook + TikTok + Google Ads) ปัญหาคลาสสิกคือแต่ละแพลตฟอร์ม "อ้าง" ว่า Install/Purchase หนึ่งรายการเป็นผลจากตัวเอง (Over-reporting) เพราะแต่ละ Ad Network มีวิธี Attribution ของตัวเองที่ Generous กับตัวเองเสมอ

MMP แก้ปัญหานี้ด้วยหลัก **Attribution Waterfall** — เมื่อมี Event เกิดขึ้น 1 ครั้ง MMP จะเช็คตามลำดับความสำคัญ (เช่น Click-through ก่อน View-through, แพลตฟอร์มที่คลิกล่าสุดก่อน) แล้ว "มอบ" Credit ให้แพลตฟอร์มเดียวเท่านั้นตาม Rule ที่ตั้งไว้ ไม่ใช่ให้ Credit ซ้ำกับทุกแพลตฟอร์ม นักยิงแอดควรเข้าไปดู Dashboard ของ MMP เป็นแหล่งข้อมูล "True Attribution" หลัก แล้วใช้ตัวเลขจาก Ads Manager ของแต่ละแพลตฟอร์มเป็นข้อมูลเสริมเพื่อ Optimize ภายในแพลตฟอร์มนั้นเท่านั้น ไม่ใช่นำตัวเลขจาก 3 แพลตฟอร์มมาบวกกันแล้วสรุปว่าได้ Install รวมเท่านั้นเท่านี้ เพราะจะสูงกว่าความจริงมาก

---

## Step 274: เลือก Optimization Event ที่เหมาะสม

### ลำดับขั้นของ Optimization Event ในแคมเปญแอป

การเลือก Optimization Event ผิดคือสาเหตุอันดับ 1 ที่ทำให้แคมเปญ App Promotion ได้ผลลัพธ์ไม่คุ้มงบ หลักการเลือกที่ถูกต้องคือดูจาก **Volume ของ Event นั้นในช่วง 7 วันที่ผ่านมา** เป็นหลัก ไม่ใช่ดูจาก "อยากได้ผลลัพธ์อะไร" อย่างเดียว

**ลำดับ Event จากบนลงล่าง (ตื้นไปลึก):**

1. **App Install** — Optimize เพื่อให้คนดาวน์โหลดแอปมากที่สุดในราคาถูกที่สุด เหมาะกับแอปใหม่ที่ยังไม่มี Volume ข้อมูล In-app Event มากพอ หรือธุรกิจที่เป้าหมายหลักคือ Volume ผู้ใช้ก่อน Monetize ทีหลัง
2. **In-app Event ระดับต้น** เช่น Registration, Tutorial Completion — Optimize เพื่อให้คนที่ Install แล้วผ่านขั้นตอนเริ่มต้นจริง ไม่ใช่ Install แล้วลบทิ้ง เหมาะกับแอปที่มี Onboarding Funnel ชัดเจน
3. **In-app Event ระดับกลาง** เช่น Add to Cart, Add Payment Info — Optimize เพื่อคนที่มี Intent จะซื้อ/สมัคร เหมาะกับแอป E-commerce/Fintech ที่มี Volume Purchase ยังไม่มากพอจะ Optimize ตรงไปที่ Purchase ได้
4. **In-app Event ระดับลึก (Purchase/Subscribe)** — Optimize ตรงไปที่ Purchase ในแอป เหมาะกับแอปที่มี Purchase Event มากกว่า 50-100 ครั้ง/สัปดาห์แล้ว (เกณฑ์ Volume ขั้นต่ำที่ Machine Learning ต้องการเพื่อออกจาก Learning Phase ได้อย่างมีเสถียรภาพ — หลักการเดียวกับที่เรียนใน Part 018 เรื่อง Learning Phase)
5. **Value Optimization** — ระดับสูงสุด ให้ Meta Optimize เพื่อหาคนที่จะทำ Purchase มูลค่าสูงสุด ไม่ใช่แค่ Purchase ที่ราคาไหนก็ได้ ต้องมี Purchase Value ส่งมาพร้อม Event และต้องมี Volume Purchase สูงมากพอ (แนะนำมากกว่า 100-200 Purchase/สัปดาห์เป็นต้นไป)

### กฎการเลือกที่ใช้ได้จริง

**อย่า Optimize สำหรับ Event ที่มี Volume ต่ำกว่า 25-50 ครั้ง/สัปดาห์** เพราะ Machine Learning จะไม่มีข้อมูลพอเรียนรู้ Pattern ของคนที่ทำ Event นั้น ผลคือ Cost per Event จะสูงลิบและแคมเปญจะไม่ Stable วิธีแก้คือเริ่ม Optimize จาก Event ที่ตื้นกว่าก่อน (เช่น Install หรือ Registration) สร้าง Volume ให้มากพอ แล้วค่อยขยับ Optimize ไปที่ Event ที่ลึกขึ้นเมื่อ Volume พร้อม

### ตัวอย่างการวางแผน Roadmap การเลือก Optimization Event

| ช่วงเวลา | Optimization Event | เหตุผล |
|---|---|---|
| สัปดาห์ที่ 1-2 (แอปใหม่) | App Install | ยังไม่มีข้อมูล In-app Event เพียงพอ ต้องสร้าง Volume ผู้ใช้ก่อน |
| สัปดาห์ที่ 3-4 | Registration/Complete Onboarding | เริ่มมี Volume Install พอ ขยับไป Optimize คนที่ผ่าน Onboarding จริง |
| เดือนที่ 2 | Add to Cart หรือ Key Action ระดับกลาง | Volume Registration เพิ่มขึ้น เริ่มมี Purchase บางส่วน |
| เดือนที่ 3 เป็นต้นไป (ถ้า Purchase Volume ≥ 50-100/สัปดาห์) | Purchase | ข้อมูลเพียงพอให้ Optimize ตรงเป้าหมายทางธุรกิจที่สุด |
| เมื่อ Purchase Volume สูงมาก (≥ 100-200/สัปดาห์) | Value Optimization | เพิ่มประสิทธิภาพสูงสุด หาคนที่จ่ายมูลค่าสูง |

### ข้อผิดพลาดที่พบบ่อย

- รีบ Optimize ไปที่ Purchase ตั้งแต่วันแรกที่แอปยังไม่มีใครโหลดเลย ทำให้แคมเปญไม่ Spend งบเลยหรือ Spend ช้ามาก (Under-delivery)
- เปลี่ยน Optimization Event บ่อยเกินไป (สัปดาห์ละครั้ง) ทำให้ Learning Phase Reset ตลอดเวลา ไม่มีช่วงที่ระบบเรียนรู้เสร็จสมบูรณ์
- ใช้ Optimization Event เดียวกันตลอดไปโดยไม่ขยับขึ้นเมื่อ Volume พร้อมแล้ว ทำให้พลาดโอกาสได้ผู้ใช้ที่มีคุณภาพสูงกว่า (Purchase-ready) ในราคาที่คุ้มกว่า

---

## Step 275: โครงสร้างแคมเปญ App Ads แบบ Step-by-Step

### ขั้นตอนสร้างแคมเปญใน Ads Manager

1. Ads Manager > **+ Create**
2. เลือก Objective: **App Promotion**
3. ตั้งชื่อแคมเปญตาม Naming Convention เช่น `APP-Install-Prospecting-Android-Sep2026`
4. เลือก **App Store**: iOS (App Store) หรือ Android (Google Play) — **ต้องแยกแคมเปญตาม OS เสมอ** เพราะพฤติกรรมผู้ใช้ ราคา CPI และข้อจำกัดด้าน Tracking (SKAdNetwork) ต่างกันมาก ไม่ควรรวม iOS/Android ไว้ Ad Set เดียวกัน
5. เลือก **App** ที่ลงทะเบียนไว้จาก Step 272 (ถ้าหาไม่เจอ แสดงว่ายังไม่เชื่อม App เข้า Business Manager/Ad Account ให้ถูกต้อง)
6. เลือก Budget Level: CBO หรือ ABO (หลักการเหมือน Part 018)

### Ad Set Level

1. **Optimization Event** — เลือกตาม Step 274
2. **Audience** — Core Audience (Demographics, Interests, Behaviors ที่เกี่ยวกับแอปประเภทนั้น เช่น คนสนใจแอปคล้ายกัน) หรือ Lookalike จาก Customer ที่ Purchase ในแอปแล้ว (ถ้ามี MMP ส่งข้อมูลกลับมาสร้าง Custom Audience จาก Mobile App Activity ได้)
3. **Placements** — แนะนำ Advantage+ Placements เป็นค่าเริ่มต้น โดยเฉพาะ Audience Network ซึ่งมีบทบาทสำคัญมากสำหรับ App Ads (Audience Network คือเครือข่ายแอปพันธมิตรของ Meta ที่โชว์โฆษณา คนที่อยู่ใน Audience Network มักมีแนวโน้ม Install แอปอื่นสูงกว่าคนที่อยู่บน Feed ปกติ)
4. **Budget & Schedule** — ตั้งตาม Guideline ใน Step 279

### Ad Level

1. เลือก Format: Single Video (แนะนำที่สุดสำหรับ App Ads), Carousel (โชว์หลาย Feature ของแอป), หรือ Playable Ad (Step 276)
2. ระบบจะดึงข้อมูล **App Name, Icon, Rating, ปุ่ม Install** มาจาก App Store/Google Play อัตโนมัติ (ผ่าน App ID ที่ผูกไว้) ไม่ต้องกรอกมือ
3. ใส่ Primary Text ที่บอก Value Proposition ของแอปชัดเจน เช่น "สั่งอาหารได้ภายใน 3 คลิก ส่งเร็วสุดใน 20 นาที ดาวน์โหลดฟรีวันนี้"
4. Call-to-Action: **"Install Now"**, **"Use App"**, **"Play Game"**, **"Shop Now"** (เลือกให้ตรงกับประเภทแอปและ Objective ที่ตั้ง)
5. Destination จะเป็น App Store/Google Play โดยอัตโนมัติสำหรับ Install Campaign หรือเป็น **Deep Link** เข้าไปหน้าเฉพาะในแอปเลยสำหรับ Re-engagement Campaign (คนที่มีแอปอยู่แล้วในเครื่อง)

### Deep Linking สำหรับ Re-engagement Campaign

ถ้าเป้าหมายคือดึงคนที่มีแอปอยู่แล้วกลับมาใช้ (เช่น คนที่ Install แอป Delivery ไว้แต่ไม่ได้เปิดมา 30 วัน) ต้องตั้งค่า **App Links / Deep Link** ให้คลิกโฆษณาแล้วเปิดตรงไปยังหน้าโปรโมชั่นในแอปเลย ไม่ใช่เปิดหน้า App Store ซ้ำ ตั้งค่าได้ที่ Ad Level > Destination > เลือก "Application" แทน "App Store" แล้วใส่ Deep Link URL ที่ทีม Dev เตรียมไว้ (เช่น `myapp://promo/september2026`)

### ข้อผิดพลาดที่พบบ่อย

- รวม iOS และ Android ไว้แคมเปญ/Ad Set เดียวกัน ทำให้ Machine Learning สับสนและวัดผลแยกไม่ได้ว่า OS ไหนให้ผลตอบแทนดีกว่า
- ใช้ Destination เป็น App Store ทั้งที่เป้าหมายคือ Re-engagement ทำให้คนที่มีแอปอยู่แล้วต้องเปิด App Store ก่อนซึ่งเพิ่ม Friction โดยไม่จำเป็น
- ไม่ตรวจสอบว่า App Icon/Rating ที่ดึงมาจาก Store อัตโนมัติแสดงถูกต้อง (บางครั้งแอปมีหลายเวอร์ชัน/หลาย Listing ทำให้ดึงข้อมูลแอปผิดตัว)

### Naming Convention เฉพาะทางสำหรับแคมเปญแอป

เพิ่มเติมจากหลัก Naming Convention ทั่วไปใน Part 016 แคมเปญแอปควรมีข้อมูลเฉพาะทางอยู่ในชื่อเสมอเพื่อให้ทีมงานแยกแยะได้ทันทีโดยไม่ต้องเปิดดูรายละเอียด:

```
[Objective]-[OS]-[Optimization Event]-[Audience Type]-[เดือน/ปี]
ตัวอย่าง: APP-iOS-Registration-LAL1%-Sep2026
ตัวอย่าง: APP-Android-Install-Broad-Sep2026
ตัวอย่าง: APP-iOS-Purchase-Retarget7d-Oct2026
```

รูปแบบนี้ทำให้เวลาดึงรายงานหลายแคมเปญมารวมกันใน Excel/Looker Studio (ทบทวน Part 091) สามารถใช้ฟังก์ชัน Text-to-Column แยกข้อมูลจากชื่อแคมเปญออกมาเป็นแต่ละมิติได้ทันทีโดยไม่ต้องเปิดเข้าไปเช็คทีละแคมเปญ ประหยัดเวลาทำรายงานได้มากเมื่อบริหารแคมเปญแอปจำนวนมาก

### Ad Account Structure สำหรับเอเจนซี่ที่ดูแลหลายแอป

ถ้าเอเจนซี่รับงานลูกค้าหลายรายที่มีแอปคนละตัว แนะนำโครงสร้างดังนี้:
- 1 Business Manager ต่อ 1 ลูกค้า (ไม่ปนกัน)
- ภายใน Business Manager นั้น แยก Ad Account ตาม OS ถ้าลูกค้ามีงบสูงพอ (Ad Account หนึ่งสำหรับ iOS อีกหนึ่งสำหรับ Android) เพื่อให้ Billing/Spending Limit และ Performance History แยกชัดเจน ถ้างบไม่สูงมากรวม Ad Account เดียวได้ แต่ต้องคุมผ่าน Campaign Naming ให้เข้มงวด
- ตั้ง App ID แยกชัดสำหรับแต่ละ OS ตั้งแต่ตอนลงทะเบียนใน Meta for Developers (Step 272) เพราะบางธุรกิจใช้ App ID เดียวข้าม OS ทำให้ Report ปนกันแก้ไขยาก

---

## Step 276: Creative Specs สำหรับ App Ads

### รูปแบบครีเอทีฟที่ Convert ดีที่สุดสำหรับ App Ads

**1. Gameplay/Screen Recording Video (สำหรับแอปเกม)**
วิดีโอที่โชว์การเล่นเกมจริง 15-30 วินาที เน้น Moment ที่ตื่นเต้นหรือท้าทายที่สุดในช่วง 3 วินาทีแรก ไม่ใช่ Cutscene หรือ Trailer แบบภาพยนตร์ เพราะผู้ใช้ตัดสินใจโหลดเกมจากการเห็น Gameplay จริงมากกว่าดู Story

**2. UI Walkthrough Video (สำหรับแอป Utility/E-commerce/Fintech)**
วิดีโอที่โชว์หน้าจอแอปจริงพร้อม Cursor/นิ้วชี้ทำ Action ทีละขั้น เช่น เปิดแอป > เลือกสินค้า > กดจ่ายเงิน > ได้รับการยืนยัน ควรมี Text Overlay อธิบายแต่ละขั้นสั้นๆ เพื่อให้เข้าใจได้แม้ปิดเสียง

**3. Playable Ads**
รูปแบบโฆษณาแบบ Interactive ที่ให้ผู้ใช้ "ลองเล่น" Mini-version ของแอป/เกมได้จริงก่อนโหลด เช่น เกมปริศนาสั้นๆ 15-20 วินาทีที่ให้ลากตัวละครเล่นในโฆษณาได้เลย จบด้วยปุ่ม Install ขนาดไฟล์ Playable ต้องเล็ก (แนะนำไม่เกิน 2MB) เพื่อโหลดเร็วในทุกความเร็วเน็ต Playable Ads มักให้ Install Rate สูงกว่า Video ทั่วไปเพราะผู้ใช้ได้สัมผัสสินค้าจริงก่อนตัดสินใจ (Try-before-you-buy) แต่ต้องใช้ทีม Dev ทำ HTML5 Interactive File ซึ่งมีต้นทุนการผลิตสูงกว่า Video ปกติ

**4. App Preview / End Card**
ภาพหรือวิดีโอสั้นๆ ที่แสดงตอนจบของ Video Ad โชว์ App Icon, Rating (ดาว), จำนวนดาวน์โหลด, และปุ่ม Install ชัดเจน ช่วยเพิ่มความน่าเชื่อถือ (Social Proof) — ถ้าแอปมี Rating สูง (4.5+ ดาว) ควรใส่ตัวเลขนี้เด่นในครีเอทีฟเสมอ

### ขนาดและ Spec ที่แนะนำ

| Format | Aspect Ratio แนะนำ | ความยาว | หมายเหตุ |
|---|---|---|---|
| Feed Video | 1:1 หรือ 4:5 | 15-30 วินาที | ต้อง Hook ใน 3 วินาทีแรก |
| Stories/Reels Video | 9:16 | 9-15 วินาที | เต็มจอ ไม่มีขอบดำ |
| Carousel | 1:1 ต่อการ์ด | 3-5 การ์ด | แต่ละการ์ดโชว์ Feature ต่างกันของแอป |
| Playable Ad | ตามที่ Platform รองรับ | Interactive 15-20 วินาที | ไฟล์ HTML5 ขนาดเล็ก |

### การ Localize ครีเอทีฟสำหรับตลาดไทย

แอปต่างชาติที่เข้ามาทำตลาดในไทยมักพลาดจุดนี้บ่อยที่สุด — ใช้ครีเอทีฟที่แปลจากภาษาอังกฤษตรงๆ โดยไม่ปรับให้เข้ากับบริบทไทย ข้อควรระวัง:

- ใช้ Font ภาษาไทยที่อ่านง่ายบนมือถือ ไม่ใช่ Font แบบ Display ที่สวยแต่อ่านยากเมื่อ Text Overlay มีขนาดเล็ก
- ตัวเลขราคา/โปรโมชั่นต้องเป็นสกุลเงินบาทและใช้รูปแบบที่คนไทยคุ้นเคย (เช่น "ลด 100 บาทแรก" มากกว่า "Get $3 off")
- Rating/Review ที่โชว์ในครีเอทีฟควรดึงจาก Google Play/App Store เวอร์ชันไทยถ้าจำนวน Rating มากพอ ถ้า Rating ไทยยังน้อยเกินไปให้ใช้ Rating รวมทั่วโลกแทนแต่ระบุให้ชัดว่าเป็น Global Rating
- เสียง Voice-over ควรใช้สำเนียงไทยธรรมชาติ ไม่ใช่ AI Voice ที่ฟังดูแปลกหรือ Google Translate เสียงแข็ง เพราะกระทบความน่าเชื่อถือของแอปตั้งแต่ 3 วินาทีแรก
- Subtitle/Text Overlay ภาษาไทยควรเว้นระยะห่างตัวอักษรให้อ่านง่ายบนจอมือถือขนาดเล็ก และหลีกเลี่ยงคำทับศัพท์ที่คนไทยทั่วไปไม่คุ้นเคยโดยไม่มีคำอธิบายเพิ่ม

### หลัก Hook สำหรับ App Ads โดยเฉพาะ

ทบทวนหลัก Hook จาก Part 036 แต่ปรับใช้กับ App Ads:
- เปิดด้วยปัญหาที่แอปแก้ได้ทันที เช่น "เบื่อรอสั่งอาหารนาน 40 นาทีไหม?"
- โชว์ผลลัพธ์ก่อนอธิบายวิธี (Result-first Hook) เช่น โชว์ยอดเงินที่ประหยัดได้จากแอป ก่อนอธิบายว่าแอปทำงานอย่างไร
- ใช้ตัวเลขที่จับตาได้ทันที เช่น "ดาวน์โหลดแล้วกว่า 2 ล้านครั้ง" หรือ "Rating 4.8 จาก 50,000 รีวิว"

### ข้อผิดพลาดที่พบบ่อย

- ใช้วิดีโอโปรโมทแบบ Branding (มีแต่โลโก้และ Concept สวยๆ) แทน Gameplay/UI จริง ทำให้คนไม่เข้าใจว่าแอปทำอะไรได้บ้างก่อนโหลด
- Playable Ads ที่โหลดช้าเกินไปเพราะไฟล์ใหญ่ ทำให้คนเบื่อรอและปิดโฆษณาก่อนได้ลองเล่น
- ไม่ปรับ Aspect Ratio ให้เหมาะกับ Placement แต่ละที่ ใช้วิดีโอ 16:9 ตัวเดียวยิงทุก Placement ทำให้ใน Stories/Reels มีขอบดำเต็มจอ ลด Immersive Experience

### เทคนิคการทำ Creative Testing สำหรับ App Ads โดยเฉพาะ

การทดสอบครีเอทีฟ App Ads มีจุดที่ต่างจาก E-commerce Creative Testing (Part 043) เล็กน้อย เพราะตัวชี้วัดที่ควรดูมี 2 ชั้น:

1. **ชั้นบน (Top of Funnel Metric)** — Hook Rate, CTR, Cost per Install ใช้บอกว่าครีเอทีฟ "ดึงความสนใจ" ได้ดีแค่ไหน
2. **ชั้นล่าง (Post-install Quality Metric)** — Retention Day 1, Cost per Registration ใช้บอกว่าคนที่โฆษณาดึงมา Install นั้น "ใช่กลุ่มเป้าหมายจริง" หรือไม่

ครีเอทีฟบางชุดอาจได้ CTR สูงและ CPI ต่ำมาก (เพราะทำให้ดูน่าตื่นเต้นเกินจริง เช่น โชว์ Gameplay ที่ไม่มีอยู่จริงในเกม) แต่ Retention Day 1 ต่ำมากเพราะคนรู้สึกว่าถูกหลอก กรณีนี้เป็นสัญญาณเตือนว่าครีเอทีฟนั้น "ได้ Volume แต่เสีย Quality" ต้องตัดออกแม้ตัวเลข CPI จะดูดีในหน้า Ads Manager ก็ตาม หลักการนี้สำคัญมากในอุตสาหกรรมเกมที่การทำ Creative แบบ "False Advertising" (โชว์ Gameplay ปลอมที่ไม่มีในเกมจริง) เป็นปัญหาเรื้อรังที่ทำให้ได้ Install จำนวนมากแต่ผู้เล่นถอนแอปภายในไม่กี่นาที ควรยึดหลัก Ethics จาก Part 007 อย่างเคร่งครัดในจุดนี้ — ครีเอทีฟต้องสะท้อนสิ่งที่แอปทำได้จริงเท่านั้น

---

## Step 277: Advantage+ App Campaigns เบื้องต้น

### คืออะไร

**Advantage+ App Campaigns** คือเวอร์ชัน Automated เต็มรูปแบบของแคมเปญ App Promotion คล้ายกับ Advantage+ Shopping Campaigns (ASC) ที่จะเรียนใน Part 029 แต่ออกแบบมาสำหรับ App Install/Re-engagement โดยเฉพาะ หลักการคือให้ Meta AI จัดการ:

- **Audience** — ไม่ต้องเลือก Interest/Behavior เอง ระบบหา Audience ที่มีโอกาส Install/ทำ Event สูงสุดจากทั้งฐานผู้ใช้ Facebook ทั้งหมด
- **Creative Combination** — ถ้าอัปโหลดครีเอทีฟหลายชุด (Video, Carousel, Image) ระบบจะทดสอบและเลือก Combination ที่ให้ผลดีที่สุดในแต่ละ Placement อัตโนมัติ
- **Budget Allocation** — กระจายงบไปยัง Ad ที่ Perform ดีที่สุดโดยอัตโนมัติภายในแคมเปญเดียว

### วิธีเปิดใช้

ตอนสร้างแคมเปญ App Promotion ที่ Campaign Level จะมีตัวเลือก **"Advantage+ app campaign"** เป็น Toggle — เมื่อเปิดใช้ โครงสร้างจะลดจาก 3 ชั้น (Campaign > Ad Set > Ad) เหลือใกล้เคียง 2 ชั้น (Campaign > Ad) เพราะ Ad Set ถูกจัดการโดย AI ทั้งหมด คุณจะป้อนแค่ Budget, Creative หลายชุด, และ Optimization Event เท่านั้น

### เมื่อไหร่ควรใช้ Advantage+ App Campaign เมื่อไหร่ควรใช้ Manual

| สถานการณ์ | แนะนำ |
|---|---|
| แอปใหม่ ยังไม่มีข้อมูล Baseline | เริ่มด้วย Manual ก่อน 2-3 สัปดาห์เพื่อเข้าใจ Benchmark ราคาคร่าวๆ ของตลาด |
| มี Creative หลากหลายชุดพร้อมทดสอบ (5+ Video/Carousel) | Advantage+ เพราะ AI จะทดสอบ Combination ได้เร็วกว่า Manual A/B Test เอง |
| ต้องการควบคุม Audience เฉพาะกลุ่มสูง (เช่น เจาะเฉพาะพื้นที่ที่ให้บริการ Delivery ได้) | Manual — ตั้ง Location Targeting ให้ชัดเจน เพราะ Advantage+ อาจกระจาย Budget ไปยังพื้นที่ที่ไม่มีบริการ |
| Purchase/Event Volume สูงสม่ำเสมอแล้ว ต้องการ Scale | Advantage+ ช่วย Scale ได้ลื่นกว่าเพราะ AI ปรับ Allocation เร็วกว่ามือ |

### ข้อผิดพลาดที่พบบ่อย

- เปิด Advantage+ App Campaign แต่ใส่ Creative แค่ 1 ชุด ทำให้ไม่ได้ประโยชน์จาก Creative Combination Testing เลย (ควรมีอย่างน้อย 3-5 Asset ที่หลากหลาย)
- ใช้กับแอปที่มีพื้นที่บริการจำกัด (เช่น Delivery เฉพาะกรุงเทพฯ) โดยไม่ล็อก Location ทำให้เสียงบกับคนในพื้นที่ที่ใช้บริการไม่ได้

---

## Step 278: iOS14+ และ SKAdNetwork — ผลกระทบและการปรับตัว

### ทบทวนบริบท iOS14 (เชื่อมกับที่เรียนใน Part 013)

Apple เปิดตัว **App Tracking Transparency (ATT)** ตั้งแต่ iOS14.5 เป็นต้นมา บังคับให้แอปทุกตัวต้องขออนุญาตผู้ใช้ก่อน Track ข้อมูลข้าม App/Website (ผ่าน IDFA — Identifier for Advertisers) ผู้ใช้ส่วนใหญ่ (มากกว่า 60-70% ในหลายตลาด) เลือก **"Ask App Not to Track"** ทำให้ผู้ลงโฆษณาไม่สามารถระบุตัวผู้ใช้แต่ละคนได้แบบละเอียดเหมือนก่อน

### SKAdNetwork คืออะไร

**SKAdNetwork (SKAN)** คือ Framework ของ Apple ที่ใช้แทน IDFA สำหรับวัดผล App Install Campaign บน iOS โดยไม่ต้องระบุตัวผู้ใช้รายบุคคล หลักการทำงาน:

1. เมื่อคน Install แอปจากการคลิก/เห็นโฆษณา Apple จะส่ง **Postback** แบบ Aggregated (รวมกลุ่ม ไม่ระบุตัวบุคคล) กลับไปยัง Ad Network (Meta) หลังจากผ่านช่วงเวลาหน่วง (Delay) เพื่อป้องกันการระบุตัวบุคคลย้อนกลับ
2. Postback มีข้อมูลจำกัดมาก เช่น Campaign ID (แต่เป็นตัวเลข 0-99 เท่านั้น ไม่ใช่ชื่อแคมเปญจริง), Conversion Value (ค่า 0-63 ที่ใช้แทน In-app Event บางอย่างแบบเข้ารหัส), Source App ID
3. Meta ต้องแปล/Map ข้อมูลเข้ารหัสนี้กลับมาเป็นรายงานที่อ่านเข้าใจได้ใน Ads Manager ผ่านระบบ **Aggregated Event Measurement for App** (คล้ายหลักการ AEM ของเว็บไซต์ที่เรียนใน Part 013 Step 128)

### ผลกระทบที่นักยิงแอดต้องรู้และปรับตัว

1. **จำนวนแคมเปญ iOS ที่ Optimize ได้พร้อมกันมีจำกัด** — Meta จะ Optimize เฉพาะแคมเปญที่ Active มากที่สุดในช่วงเวลานั้น (ระบบมีเพดานจำนวนแคมเปญที่ได้รับ Priority สำหรับ SKAN) ดังนั้นควร **รวมงบไว้ในแคมเปญ iOS จำนวนน้อยแต่คุณภาพสูง** ดีกว่าแยกเป็นแคมเปญเล็กๆ จำนวนมาก
2. **ข้อมูลมาช้า (Delay)** — Postback จาก SKAN อาจใช้เวลา 24-48 ชั่วโมงกว่าจะรายงานผลครบ ทำให้การอ่านผลลัพธ์รายวันของแคมเปญ iOS ไม่ Real-time เหมือนก่อน ต้องรอดูข้อมูล 3-5 วันก่อนตัดสินใจปรับ/ปิดแคมเปญ
3. **Conversion Value Mapping ต้องตั้งเอง** — ใน Meta Events Manager ต้องกำหนด **Conversion Value Rules** ว่า In-app Event ระดับไหนแทนค่าตัวเลขอะไร (เช่น Registration = ค่า 5, Purchase ต่ำกว่า 500 บาท = ค่า 20, Purchase มากกว่า 500 บาท = ค่า 40) ถ้าไม่ตั้งค่านี้ Meta จะไม่รู้ว่า Postback ที่ได้มาคือ Event ระดับไหน
4. **Geo-targeting และ Age-targeting มีข้อจำกัดมากขึ้นบน iOS Campaign** เพราะ SKAN มีเพดานเรื่อง Privacy Threshold (ต้องมีจำนวนคนมากพอในกลุ่มจึงจะรายงานผลได้ ไม่งั้นข้อมูลจะถูกระงับเพื่อป้องกันการระบุตัวบุคคล)

### แนวทางปรับตัวที่มืออาชีพใช้จริง

- แยกงบระหว่าง iOS และ Android ให้ชัดเจน และยอมรับว่าตัวเลข iOS จะ "ดูแม่นน้อยกว่า" Android โดยธรรมชาติ ไม่ใช่เพราะแคมเปญห่วย
- ตั้งค่า Conversion Value Rules ให้ครอบคลุม Event สำคัญที่สุด 3-5 ระดับ ไม่ต้องซับซ้อนเกินไป
- ใช้ข้อมูลจาก MMP (Step 273) ควบคู่กับ Ads Manager เพื่อ Cross-check เพราะ MMP มักมีวิธี Modeling ข้อมูลที่ขาดหายไปจาก SKAN ให้เห็นภาพที่สมบูรณ์ขึ้น
- ให้เวลา Learning Phase นานขึ้นกว่าปกติสำหรับแคมเปญ iOS (อาจต้องรอ 2 สัปดาห์ขึ้นไปกว่าจะเห็นภาพที่ Stable เพราะข้อมูล Delay)

### ข้อผิดพลาดที่พบบ่อย

- ไม่ตั้ง Conversion Value Rules เลย ทำให้แคมเปญ iOS Optimize ได้แค่ระดับ Install อย่างเดียวตลอดไป ไม่สามารถขยับไปที่ Purchase ได้แม้จะมี Purchase เกิดขึ้นจริงในแอป
- ตัดสินใจปิดแคมเปญ iOS เร็วเกินไป (ภายใน 1-2 วัน) เพราะเห็นตัวเลขน้อย ทั้งที่ข้อมูลยังไม่มาครบเพราะ SKAN Delay
- สร้างแคมเปญ iOS จำนวนมากเกินไปพร้อมกัน ทำให้งบกระจายและไม่มีแคมเปญไหนได้ Priority Signal เพียงพอสำหรับ SKAN Optimization

### ตัวอย่างการตั้ง Conversion Value Rules แบบละเอียด

สมมติแอป Fintech ต้องการตั้ง Conversion Value Rules ใน Meta Events Manager > เมนู "Conversion Values" (ต้องเปิดใช้งานผ่าน SKAdNetwork Configuration) ตัวอย่างการวาง Rule แบบ Priority (ระบบจะเช็คจากบนลงล่าง แล้วใช้ค่าแรกที่ตรงเงื่อนไข):

| ลำดับ Priority | เงื่อนไข | Conversion Value ที่ Map |
|---|---|---|
| 1 | ทำ Purchase มูลค่ารวม ≥ 5,000 บาท ภายใน 24 ชม. แรก | 63 (ค่าสูงสุด) |
| 2 | ทำ Purchase มูลค่า 1,000-4,999 บาท | 45 |
| 3 | ทำ Purchase มูลค่า < 1,000 บาท | 30 |
| 4 | ยืนยันตัวตน (KYC) สำเร็จ แต่ยังไม่ Purchase | 15 |
| 5 | สมัครสมาชิก (Registration) แต่ยังไม่ยืนยันตัวตน | 5 |
| 6 | เปิดแอปแต่ไม่ทำ Action ใดๆ (Activate Only) | 1 |

ค่า Conversion Value เป็นตัวเลข 0-63 ที่ Apple อนุญาตให้ Encode ได้ (6-bit) เมื่อ Meta ได้รับ Postback พร้อมค่านี้ ระบบจะแปลกลับมาบอกได้ว่า "แคมเปญนี้ได้ผู้ใช้ที่ทำ Action ระดับไหนบ้าง" แล้วใช้ Optimize ให้เจอคนที่มีโอกาสทำ Action ระดับสูงมากขึ้นเรื่อยๆ ยิ่ง Volume Purchase มากพอ ระบบจะเรียนรู้ Pattern ได้แม่นยำขึ้น

### กรอบเวลา Conversion Value Window

Apple กำหนดกรอบเวลาที่ยอมให้แอปอัปเดต Conversion Value ได้ (มักเป็น 2-3 รอบ Timer ภายใน 35-60 วันแรกหลัง Install ขึ้นอยู่กับเวอร์ชัน SKAdNetwork) หลังจากหมดกรอบเวลานี้ ค่าที่ Encode ไว้ล่าสุดจะถูกส่งเป็น Postback สุดท้าย ดังนั้นถ้าธุรกิจมี Purchase Cycle ยาว (เช่น สมัคร Trial 30 วันก่อนตัดสินใจซื้อ Subscription) ต้องออกแบบ Conversion Value ให้ครอบคลุม Milestone สำคัญภายในกรอบเวลานี้ ไม่ใช่รอ Event ที่อาจเกิดหลัง 60 วันไปแล้ว เพราะจะไม่ถูกนับใน Postback เลย

---

## Step 279: งบประมาณ, CPI/CPA Benchmark, และการอ่านผลลัพธ์

### ตัวชี้วัดหลักของแคมเปญแอป

- **CPI (Cost Per Install)** — ต้นทุนต่อการติดตั้ง 1 ครั้ง
- **CPA (Cost Per Action)** — ต้นทุนต่อ In-app Event ที่กำหนด (Registration, Purchase)
- **ROAS (Return on Ad Spend)** — สำหรับแอปที่มี In-app Purchase
- **Retention Rate D1/D7/D30** — สัดส่วนคนที่ยัง Active หลัง Install ไปแล้ว 1/7/30 วัน (ตัวเลขนี้สำคัญมากเพราะ CPI ถูกแต่ Retention แย่ = เสียเงินเปล่า ต้องดูควบคู่กันเสมอ ไม่ใช่ดู CPI อย่างเดียว)

### CPI Benchmark คร่าวๆ ในตลาดไทย (ใช้เป็นจุดอ้างอิง ไม่ใช่ตัวเลขตายตัว เพราะเปลี่ยนตามช่วงเวลาและการแข่งขัน)

| ประเภทแอป | CPI โดยประมาณ (Android) | CPI โดยประมาณ (iOS) |
|---|---|---|
| แอป Utility/Productivity ทั่วไป | 10-25 บาท | 25-50 บาท |
| แอป E-commerce/Delivery | 20-40 บาท | 40-80 บาท |
| แอปเกม Casual | 8-20 บาท | 20-40 บาท |
| แอปเกม Mid-core/Hard-core | 30-70 บาท | 60-120 บาท |
| แอป Fintech/Banking | 40-100 บาท | 80-180 บาท |

(ตัวเลขเหล่านี้ผันแปรตามช่วงเวลา คู่แข่งในตลาด และคุณภาพครีเอทีฟ ใช้เป็น Sanity Check เบื้องต้นเท่านั้น ไม่ควรยึดเป็นมาตรฐานตายตัว)

### วิธีอ่านผลลัพธ์ให้ถูกต้อง (ไม่ดู CPI อย่างเดียว)

1. ดู CPI ควบคู่กับ **Post-install Event Rate** — ถ้า CPI ถูกมากแต่คนที่ Install แล้วไม่ทำ Registration/Purchase เลย แสดงว่าได้ผู้ใช้คุณภาพต่ำ (มักเกิดจาก Audience Network ที่มี Incentivized Traffic หรือ Bot บางส่วน)
2. ดู **Cost per Registration/Purchase** แทน CPI เป็นตัวชี้วัดหลักเมื่อธุรกิจมี Funnel หลัง Install ชัดเจน
3. เทียบ **LTV (Lifetime Value) ต่อผู้ใช้** กับ CPI+CPA รวมกัน ถ้า LTV สูงกว่าต้นทุนรวมในกรอบเวลาที่ยอมรับได้ (เช่น 90 วัน) ถือว่าแคมเปญคุ้มค่า แม้ CPI ตอนแรกจะดูสูงก็ตาม
4. ใช้ **Breakdown by Placement** เช็คว่า Audience Network ให้ Volume สูงแต่ Retention ต่ำหรือไม่ ถ้าใช่ ให้พิจารณาลด Placement นี้ออกหรือจำกัดเฉพาะ Video Placement ภายใน Audience Network

### การตั้งงบเริ่มต้น

แนะนำงบเริ่มต้นขั้นต่ำต่อ Ad Set สำหรับแคมเปญ App Install อยู่ที่ประมาณ **50-100 เท่าของ CPI ที่คาดการณ์ต่อวัน** เพื่อให้ระบบมี Volume Event พอเรียนรู้ภายใน Learning Phase (สอดคล้องกับหลักการทั่วไปที่เรียนใน Part 018 ว่าต้องมี Conversion อย่างน้อย 50 ครั้ง/สัปดาห์ต่อ Ad Set)

### ข้อผิดพลาดที่พบบ่อย

- ตัดสินแคมเปญจาก CPI เพียงอย่างเดียวโดยไม่ดู Retention/Post-install Quality
- ตั้งงบต่ำเกินไปจนแคมเปญไม่มี Volume Install พอออกจาก Learning Phase (Under-funded Campaign)
- ไม่แยกดู Performance ตาม Placement ทำให้ไม่รู้ว่า Budget ส่วนใหญ่ไปอยู่กับ Traffic คุณภาพต่ำจาก Audience Network บางส่วน

### การคำนวณ Payback Period สำหรับแคมเปญแอป

นอกจาก CPI/CPA แล้ว มืออาชีพระดับสูงจะคำนวณ **Payback Period** — จำนวนวันที่ต้องใช้กว่า LTV สะสมของผู้ใช้ 1 คนจะเท่ากับต้นทุนที่จ่ายไปเพื่อได้ผู้ใช้คนนั้นมา (CPI + CPA เฉลี่ย) สูตรคร่าวๆ:

```
Payback Period (วัน) = (CPI + Cost per Registration เฉลี่ย) ÷ (LTV เฉลี่ยต่อวันต่อผู้ใช้)
```

ตัวอย่าง: แอป Fintech มี CPI+CPA รวม 120 บาทต่อผู้ใช้ และผู้ใช้แต่ละคนสร้างรายได้เฉลี่ย 4 บาทต่อวัน (จากค่าธรรมเนียมธุรกรรม) Payback Period จะอยู่ที่ 120 ÷ 4 = 30 วัน ถ้าธุรกิจตั้งเป้า Payback Period ไม่เกิน 45 วัน แคมเปญนี้ถือว่าผ่านเกณฑ์ ควร Scale งบเพิ่ม แต่ถ้า Payback Period ยาวกว่า 90 วัน ต้องพิจารณาปรับ Optimization Event หรือ Audience ใหม่ก่อน Scale

ตัวชี้วัดนี้สำคัญมากสำหรับการสื่อสารกับเจ้าของธุรกิจ/นักลงทุน เพราะเป็นภาษาที่ฝั่ง Finance เข้าใจง่ายกว่า CPI ตรงๆ และช่วยตัดสินใจเรื่อง Cashflow ได้ชัดเจนกว่า (ธุรกิจต้องมีเงินทุนสำรองพอสำหรับ Payback Period ที่ยาวก่อนจะเห็นกำไรกลับมา)

### Scaling Budget สำหรับแคมเปญแอปที่ Performance ดีแล้ว

เมื่อแคมเปญผ่านเกณฑ์ CPI/Retention/Payback Period ที่ตั้งไว้แล้ว การเพิ่มงบควรทำแบบ **Vertical Scaling ทีละ 20-30% ทุก 3-4 วัน** (หลักการเดียวกับ Part 058 เรื่อง Scaling Strategy) ไม่ควรเพิ่มงบทีเดียวเกิน 50% เพราะจะรีเซ็ต Learning Phase และทำให้ CPI พุ่งขึ้นชั่วคราว สำหรับแคมเปญ iOS ควรระมัดระวังเป็นพิเศษเพราะการเพิ่มงบกระทันหันอาจทำให้แคมเปญหลุดจากกลุ่มที่ได้รับ SKAN Priority Signal ไปเลย

---

## Step 280: ข้อผิดพลาดที่พบบ่อยในการยิงแอด App Install และ Workshop

### สรุปข้อผิดพลาดที่พบบ่อยที่สุดในสนามจริง (เรียบเรียงจากทุก Step ก่อนหน้า)

1. **ไม่เตรียม Technical Setup ให้พร้อมก่อนเริ่มยิง** — SDK/MMP ยังไม่เชื่อมสมบูรณ์ แต่รีบสร้างแคมเปญ ทำให้ไม่มีข้อมูล Event ป้อนกลับตั้งแต่วันแรก
2. **เลือก Optimization Event ที่ Volume ต่ำเกินไปเร็วเกินไป** — อยาก Optimize Purchase ทั้งที่ยังไม่มี Volume Install พอ
3. **รวม iOS/Android ไว้ด้วยกัน** — ทำให้วัดผลและ Optimize สับสน
4. **ไม่ตั้ง Conversion Value Rules สำหรับ iOS** — ทำให้ SKAN Optimize ได้แค่ระดับ Install ตลอดไป
5. **ใช้ Creative แบบ Branding ล้วนไม่โชว์ Gameplay/UI จริง** — Install Rate ต่ำเพราะคนไม่เห็นภาพว่าแอปทำอะไรได้
6. **ตัดสินใจเร็วเกินไปจากข้อมูล iOS ที่ยังมาไม่ครบ** — ปิดแคมเปญที่จริงๆ ยังรอ SKAN Postback อยู่
7. **ดู CPI อย่างเดียวไม่ดู Retention/LTV** — ได้ Volume Install ถูกแต่คุณภาพต่ำ ขาดทุนในระยะยาว

### Case Study: แอป Delivery อาหารระดับภูมิภาค "QuickBite"

QuickBite เป็นแอปสั่งอาหาร Delivery ที่ให้บริการในกรุงเทพฯและปริมณฑล เปิดตัวแคมเปญ App Install ครั้งแรกโดยทำผิดพลาดตามสูตรคลาสสิก: สร้างแคมเปญเดียวรวม iOS+Android, Optimize ไปที่ Purchase in-app ตั้งแต่วันแรกทั้งที่ยังไม่มีใครโหลดแอปเลย และไม่ได้ล็อก Location เฉพาะพื้นที่บริการ ผลคือแคมเปญ Spend งบช้ามาก (Under-delivery) และ CPI ที่ได้สูงกว่าตลาดเกือบ 3 เท่า

ทีมมีเดียไบเยอร์เข้ามาปรับใหม่ทั้งระบบ:

1. แยกแคมเปญเป็น 2 ชุด: `APP-Install-Android-Bangkok` และ `APP-Install-iOS-Bangkok` โดยล็อก Location เฉพาะกรุงเทพฯและปริมณฑลที่ให้บริการจริง
2. เปลี่ยน Optimization Event เป็น **App Install** ก่อนในช่วง 2 สัปดาห์แรกเพื่อสร้าง Volume ผู้ใช้
3. ตั้งค่า Conversion Value Rules บน iOS: Registration = 10, First Order = 30, Order มูลค่ามากกว่า 300 บาท = 50
4. เปลี่ยนครีเอทีฟจาก Branding Video เป็น UI Walkthrough ที่โชว์ขั้นตอนสั่งอาหารจริง 3 ขั้นตอนภายใน 15 วินาที พร้อม Overlay ตัวเลข "ส่งเร็วสุด 20 นาที"
5. เชื่อม AppsFlyer เป็น MMP กลาง ส่ง Postback ให้ทั้ง Meta และ Google Ads พร้อมกัน เพื่อเปรียบเทียบ Performance ข้าม Platform ได้อย่างเป็นธรรม

หลังรัน 6 สัปดาห์: CPI ของ Android ลดลงจาก 65 บาทเหลือ 28 บาท (ต่ำกว่า Benchmark ตลาด) ส่วน iOS ลดลงจาก 140 บาทเหลือ 75 บาท และเมื่อ Volume Registration เพิ่มขึ้นเพียงพอ (มากกว่า 100 ครั้ง/สัปดาห์) ทีมขยับ Optimization Event ไปที่ First Order ได้สำเร็จ ทำให้ต้นทุนต่อผู้ใช้ที่สั่งอาหารจริงครั้งแรก (Cost per First Order) ลดลง 45% เทียบกับช่วงเริ่มต้น

จุดที่เกือบพลาดอีกครั้ง: ทีมเกือบปิดแคมเปญ iOS ในวันที่ 3 เพราะเห็นตัวเลข Purchase เป็น 0 ทั้งที่จริงมี Order เกิดขึ้นแล้วในระบบหลังบ้าน แต่ SKAN Postback ยังไม่ส่งกลับมา (Delay ปกติ 24-48 ชั่วโมง) โชคดีที่ตรวจสอบกับข้อมูลจาก AppsFlyer ก่อนตัดสินใจปิด ทำให้รอดูข้อมูลต่ออีก 2 วันจนเห็นตัวเลขที่ถูกต้อง

ผลลัพธ์ระยะยาวเมื่อครบไตรมาสแรก: QuickBite สามารถ Scale งบรายเดือนขึ้นจาก 150,000 บาทเป็น 480,000 บาท โดยยังคง Payback Period อยู่ที่ประมาณ 35 วัน (อยู่ในเกณฑ์ที่ทีม Finance ของธุรกิจยอมรับได้) และสัดส่วนงบระหว่าง Android:iOS ที่ปรับจนเหมาะสมที่สุดอยู่ที่ประมาณ 65:35 เพราะ Android ให้ Volume ผู้ใช้ที่คุ้มค่ากว่าในตลาดที่ให้บริการ ขณะที่ iOS ยังคงรักษาไว้เพราะกลุ่มผู้ใช้ iOS มี Average Order Value สูงกว่า Android ราว 20% ซึ่งชดเชยต้นทุน CPI ที่สูงกว่าได้ในระยะยาว บทเรียนสำคัญจากเคสนี้คือการตัดสินใจเรื่องสัดส่วนงบ OS ไม่ควรดูแค่ CPI แต่ต้องดู Value ของผู้ใช้ที่ได้มาในภาพรวมด้วย

---

## คำถามที่พบบ่อย (FAQ)

**Q: ธุรกิจที่มีทั้งเว็บไซต์และแอป ควรยิงทั้งสองแบบพร้อมกันไหม หรือเลือกอย่างใดอย่างหนึ่ง?**
A: ควรยิงคู่กันแบบมีกลยุทธ์ ไม่ใช่แข่งกันเอง ใช้เว็บไซต์เป็นช่องทาง Prospecting ต้นทุนต่ำ และใช้ App Promotion เป็นช่องทาง Retargeting/Conversion หลังบ้านที่มี LTV สูงกว่า ตามหลัก Web-to-App Funnel ที่อธิบายใน Step 271

**Q: จำเป็นต้องใช้ MMP ไหม ถ้าธุรกิจยิงโฆษณาแค่ Facebook แพลตฟอร์มเดียว?**
A: ถ้ายิงแพลตฟอร์มเดียวจริงๆ และไม่มีแผนขยายไปแพลตฟอร์มอื่น สามารถใช้ Facebook SDK ส่ง Event ตรงเข้า Meta โดยไม่ต้องผ่าน MMP ได้ แต่ในทางปฏิบัติธุรกิจส่วนใหญ่มักขยายไปยิง TikTok/Google Ads ในอนาคต การมี MMP ตั้งแต่แรกจะประหยัดเวลาทำ Integration ซ้ำในระยะยาว

**Q: Advantage+ App Campaign เหมาะกับแอปที่มีงบน้อยไหม?**
A: เหมาะกับแอปที่มี Volume ข้อมูล Event สม่ำเสมอมากกว่างบมาก/น้อย ถ้าแอปยังไม่มี Purchase Event เลยและงบน้อย ควรเริ่มด้วย Manual Campaign เพื่อควบคุม Learning Phase ให้แม่นยำก่อน

**Q: ทำไม Cost per Install บน Audience Network ถูกกว่า Feed มาก แต่ Retention แย่?**
A: Audience Network เป็นเครือข่ายแอปพันธมิตรจำนวนมาก คุณภาพผู้ใช้หลากหลายกว่า Feed หลัก บางส่วนอาจเป็น Traffic จากแอปที่ผู้ใช้ Install แบบไม่ตั้งใจ (เช่น กด Install ผิดจากโฆษณาเกมที่ฝังอยู่ในแอปอื่น) แนะนำเช็ค Breakdown by Placement เสมอ และถ้า Retention ต่ำมากให้พิจารณาตัด Audience Network Placement บางส่วนออก แม้ CPI จะดูดีในภาพรวมก็ตาม

**Q: SKAdNetwork ใช้กับ Android ด้วยหรือไม่?**
A: ไม่ใช้ SKAdNetwork เป็นระบบของ Apple เท่านั้น สำหรับ Android ยังใช้ Google Play Install Referrer และ GAID (Google Advertising ID) ซึ่งยังให้ข้อมูลละเอียดกว่า iOS มากในปัจจุบัน ทำให้แคมเปญ Android มักวัดผลได้แม่นยำและเร็วกว่า iOS อย่างชัดเจน

**Q: ถ้างบมีจำกัดมาก ควรเลือกยิงแค่ Android อย่างเดียวได้ไหม?**
A: ได้ และเป็นทางเลือกที่สมเหตุสมผลสำหรับธุรกิจงบน้อยในตลาดไทย เพราะ Android มีสัดส่วนผู้ใช้มากกว่าในหลายกลุ่มประชากร วัดผลได้แม่นยำกว่าเพราะไม่ติดข้อจำกัด SKAdNetwork และ CPI มักต่ำกว่า iOS อย่างมีนัยสำคัญ ควรพิจารณาเพิ่ม iOS เมื่อธุรกิจเติบโตและมีงบเพียงพอที่จะรับความคลาดเคลื่อนของข้อมูลที่มาช้ากว่า

---

### บทเรียนสำคัญที่สรุปได้จากเคส QuickBite

- การล็อก Location Targeting ให้ตรงกับพื้นที่บริการจริงคือจุดแรกที่ต้องตรวจสอบก่อนเริ่มยิงแอด Delivery ทุกครั้ง
- การไล่ระดับ Optimization Event ตาม Volume ข้อมูลจริง (ไม่รีบ Optimize Purchase ตั้งแต่วันแรก) คือปัจจัยที่ทำให้ CPI ลดลงได้เร็วที่สุด
- ครีเอทีฟที่โชว์ขั้นตอนใช้งานจริงพร้อมตัวเลขที่จับต้องได้ (เช่น "20 นาที") ให้ผลดีกว่า Branding Video ล้วนอย่างชัดเจน
- การมี MMP กลางที่ให้ข้อมูล Cross-check ช่วยป้องกันการตัดสินใจผิดพลาดจาก SKAN Delay ได้จริง
- สัดส่วนงบระหว่าง OS ควรตัดสินจาก Value รวมของผู้ใช้ ไม่ใช่ดูจาก CPI เพียงอย่างเดียว

---

## Checklist ท้ายบท

- [ ] ลงทะเบียนแอปใน Meta for Developers และผูกกับ Business Manager/Ad Account ที่ถูกต้อง
- [ ] ทีม Dev ติดตั้ง Facebook SDK และยิง Standard Event ครบตามที่ธุรกิจต้องการ Optimize
- [ ] Test Event ผ่าน Meta Events Manager ก่อนขึ้นแอปเวอร์ชันจริง
- [ ] เลือกและตั้งค่า MMP (AppsFlyer/Adjust/Branch/Singular) เชื่อม Postback กับ Meta เรียบร้อย
- [ ] ตกลง Attribution Window ให้ตรงกันทุกแพลตฟอร์มที่ยิงแอดพร้อมกัน
- [ ] แยกแคมเปญ iOS และ Android ออกจากกันเสมอ
- [ ] เลือก Optimization Event ตาม Volume ข้อมูลจริง ไม่ใช่ตามที่อยากได้
- [ ] เตรียม Creative แบบ Gameplay/UI Walkthrough จริง ไม่ใช่ Branding Video ล้วน
- [ ] ตั้งค่า Conversion Value Rules สำหรับแคมเปญ iOS
- [ ] ล็อก Location Targeting ให้ตรงกับพื้นที่ที่แอปให้บริการได้จริง (ถ้ามีข้อจำกัดด้านพื้นที่)
- [ ] ดู Retention Rate และ LTV ควบคู่กับ CPI/CPA เสมอ ไม่ตัดสินจาก CPI อย่างเดียว
- [ ] รอข้อมูล SKAN Postback ครบ 3-5 วันก่อนตัดสินใจปิด/ปรับแคมเปญ iOS
- [ ] คำนวณ Payback Period และเทียบกับเกณฑ์ที่ธุรกิจยอมรับได้ก่อนตัดสินใจ Scale งบ
- [ ] Localize ครีเอทีฟให้เหมาะกับตลาดไทยจริง ไม่ใช่แปลตรงจากภาษาอังกฤษ
- [ ] ตั้ง Naming Convention ที่มีข้อมูล OS, Optimization Event, Audience Type ครบในชื่อแคมเปญทุกตัว
- [ ] ตรวจสอบว่าครีเอทีฟไม่ใช้ False Advertising (Gameplay/Feature ที่ไม่มีจริงในแอป) ตามหลัก Ethics
- [ ] วางแผน Web-to-App Funnel ถ้าธุรกิจมีทั้งเว็บไซต์และแอปทำงานคู่กัน
- [ ] แยกโครงสร้าง Business Manager/Ad Account ให้ชัดเจนถ้าดูแลหลายแอปพร้อมกันในฐานะเอเจนซี่

---

## Workshop / แบบฝึกหัด

**เป้าหมาย:** วางแผนแคมเปญ App Install แบบสมบูรณ์สำหรับแอปสมมติหรือแอปจริงที่คุณดูแล

**ขั้นตอนที่ต้องทำ:**

1. เลือกแอป (จริงหรือสมมติ) 1 ตัว ระบุประเภทธุรกิจให้ชัด (Delivery, Fintech, E-commerce, Game ฯลฯ)
2. เขียนรายการ Standard Event ที่แอปนี้ควรยิงอย่างน้อย 5 Event เรียงจากตื้นไปลึก (เช่น Install → Registration → AddToCart → InitiateCheckout → Purchase)
3. เลือก MMP ที่เหมาะกับธุรกิจนี้ 1 ตัว พร้อมให้เหตุผลว่าทำไมเลือกตัวนี้จากตารางเปรียบเทียบใน Step 273
4. วางแผน Roadmap การเลือก Optimization Event เป็นตาราง 4 ช่วงเวลา (เดือนที่ 1, 2, 3, 4) ว่าจะ Optimize Event อะไรในแต่ละช่วง โดยอ้างอิงเกณฑ์ Volume ที่เรียนใน Step 274
5. ร่างโครงสร้างแคมเปญ: แยกกี่แคมเปญ (iOS/Android), แต่ละแคมเปญมีกี่ Ad Set, ตั้ง Location Targeting อย่างไร
6. เขียน Concept ครีเอทีฟ 2 ชุด: 1 ชุดสำหรับ Prospecting (คนยังไม่รู้จักแอป) และ 1 ชุดสำหรับ Re-engagement (คนมีแอปแล้วแต่ไม่ได้เปิด)
7. กำหนด Conversion Value Rules สมมติสำหรับ iOS อย่างน้อย 3 ระดับ
8. ตั้งงบประมาณเริ่มต้นต่อวันสำหรับ Ad Set แรก พร้อมคำนวณว่าใช้เวลากี่วันถึงจะมี Volume Event พอออกจาก Learning Phase (อ้างอิง CPI Benchmark ในตารางที่ Step 279)
9. เขียนแผนตรวจสอบผลลัพธ์: จะดู Metric อะไรในสัปดาห์ที่ 1, 2, 4 ตามลำดับ และเงื่อนไขที่จะทำให้ตัดสินใจปิด/ขยับ Ad Set
10. คำนวณ Payback Period สมมติจากตัวเลข CPI/CPA และ LTV ต่อวันที่คุณประมาณเอง แล้วสรุปว่าธุรกิจนี้ควร Scale งบหรือควรปรับกลยุทธ์ก่อน
11. เขียน Naming Convention มาตรฐานสำหรับทุกแคมเปญ/Ad Set/Ad ของโปรเจกต์นี้ ตามรูปแบบใน Step 275 แล้วลองตั้งชื่อแคมเปญสมมติ 4 ชื่อให้ครบทุก Dimension

### ตารางสรุปสำหรับส่งงาน (Deliverable Template)

ใช้ตารางนี้สรุปผลลัพธ์การทำ Workshop เป็น 1 หน้าเดียว เพื่อฝึกการนำเสนอแผนแบบที่ใช้คุยกับเจ้าของธุรกิจ/ลูกค้าได้จริง:

| หัวข้อ | รายละเอียดที่ต้องกรอก |
|---|---|
| ชื่อแอปและประเภทธุรกิจ | |
| Standard Events ที่ต้องยิง (เรียงตื้นไปลึก) | |
| MMP ที่เลือกและเหตุผล | |
| จำนวนแคมเปญ (แยก OS) และ Optimization Event ต่อช่วงเวลา | |
| Conversion Value Rules (iOS) | |
| Concept ครีเอทีฟ Prospecting / Re-engagement | |
| งบเริ่มต้นต่อวันและระยะเวลาประเมิน Learning Phase | |
| Payback Period ที่ยอมรับได้ และเกณฑ์ Scale งบ | |

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้พาคุณเจาะลึกโลกของ App Promotion ตั้งแต่การเชื่อม Technical Infrastructure (SDK, MMP) ที่ต่างจากงานยิงแอดเว็บไซต์ทั่วไป ไปจนถึงการเลือก Optimization Event ที่เหมาะกับ Volume ข้อมูลจริง การจัดการผลกระทบจาก iOS14/SKAdNetwork และการอ่านผลลัพธ์อย่างรอบด้าน ไม่ใช่ดูแค่ CPI

ทักษะเรื่อง Automation ที่เริ่มเห็นเค้าลางใน Advantage+ App Campaigns (Step 277) จะถูกขยายความแบบเต็มรูปแบบใน **Part 029: Advantage+ Shopping Campaigns (ASC) เจาะลึก** ซึ่งจะพากลับไปที่โลก E-commerce อีกครั้ง แต่คราวนี้จะเห็นว่า Meta ให้ AI ควบคุมเกือบทุกจุดตัดสินใจของแคมเปญได้อย่างไร และนักยิงแอดมืออาชีพจะวาง Test ที่เป็นธรรมระหว่าง Manual Campaign กับ ASC ได้อย่างไรเพื่อพิสูจน์ว่าอันไหนเหมาะกับธุรกิจมากกว่า

หลักการที่คุณเรียนไปแล้วในทั้งสอง Part นี้ — การให้เวลา Machine Learning เรียนรู้อย่างพอเพียงก่อนตัดสินใจ, การไม่รีบ Optimize Event ที่ Volume ยังไม่พร้อม, และการอ่านผลลัพธ์แบบรอบด้านไม่ใช่ดูตัวเลขเดียว — จะเป็นแกนความคิดที่ใช้ซ้ำได้กับ ASC เช่นกัน เพียงแต่ระดับ Automation จะยิ่งสูงขึ้นไปอีกขั้น

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta for Developers: Facebook SDK for iOS/Android Documentation
- Meta Business Help Center: App Ads Overview และ App Events
- Meta Business Help Center: SKAdNetwork และ Aggregated Event Measurement for Apps
- Apple Developer Documentation: SKAdNetwork Framework
- AppsFlyer, Adjust, Branch, Singular — Official Integration Guides สำหรับ Facebook/Meta Ads
- Meta Business Help Center: Advantage+ App Campaigns
- Google Play Console Documentation: Install Referrer API
- Meta Business Help Center: Value Optimization for App Events
- เอกสารภายในทีม: SOP การประสานงานกับ Developer สำหรับติดตั้ง SDK/MMP ก่อนเริ่มแคมเปญทุกครั้ง
- Meta Business Help Center: Deep Linking และ App Links Best Practices
- Meta Business Help Center: Audience Network Placement Guidelines สำหรับ App Ads
- Meta Business Help Center: Creative Best Practices for Gaming and Utility Apps
- Meta for Developers: Conversion Value Rules Configuration Guide สำหรับ SKAdNetwork
- Google Play Console: Best Practices for Store Listing และผลต่อ Install Conversion Rate
- Apple App Store Connect: App Analytics และการอ่านข้อมูล Retention เทียบกับ Meta Ads Manager
