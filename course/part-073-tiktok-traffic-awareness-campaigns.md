# Part 073: สร้างแคมเปญ Traffic/Awareness บน TikTok

**Section:** H — TikTok Ads Manager Deep Dive & Creative
**Step ที่ครอบคลุม:** 721–730 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 5–7 ชั่วโมง (รวมเวลาลงมือสร้างแคมเปญจริงใน TikTok Ads Manager และรอดูผล 24–48 ชั่วโมงแรก)

ผ่าน Section G มาแล้ว (Part 064–072) คุณควรเข้าใจระบบนิเวศ TikTok Ads, การสร้าง Business Center, Pixel/Events API, โครงสร้าง Campaign > Ad Group > Ad, Objective ทั้งหมด, Budget/Bidding และ Placement ในเชิงทฤษฎีครบแล้ว มาถึง Section H เราจะเริ่ม "ลงมือกดจริง" ทีละคลิกใน TikTok Ads Manager เหมือนที่ Section C ทำกับ Facebook — โดย Part แรกของ Section นี้จะจับคู่สอง Objective ที่ปลอดภัยที่สุดสำหรับมือใหม่ TikTok คือ **Reach (Awareness)** และ **Traffic** เพื่อให้คุณคุ้นมือกับหน้าจอ ปุ่ม เมนู และ Field ต่างๆ ก่อนไปสร้างแคมเปญที่ซับซ้อนขึ้น (Lead Generation ใน Part 074 และ Conversion ใน Part 075)

> หมายเหตุสำคัญ: TikTok อัปเดต UI ของ Ads Manager บ่อยกว่า Facebook มาก (บางไตรมาสเปลี่ยนตำแหน่งเมนูเลย) แต่ **ตรรกะของโครงสร้าง 3 ชั้น** (Campaign > Ad Group > Ad) และชื่อ Field หลักที่สอนใน Part นี้ยังคงเดิมมาหลายปี ให้โฟกัสที่ตรรกะ ไม่ใช่ตำแหน่งพิกเซลของปุ่ม — ถ้าเปิดมาแล้วหน้าตาไม่เหมือนในเอกสารเป๊ะๆ ให้มองหาชื่อ Field ที่ตรงกันแทน

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 721** — เปิด TikTok Ads Manager, เลือก Custom Mode, และทำความรู้จักหน้าจอหลักก่อนสร้างแคมเปญ
2. **Step 722** — สร้างแคมเปญ Reach (Awareness) แบบ Step-by-Step ตั้งแต่ Campaign จนถึง Ad Group
3. **Step 723** — สร้างแคมเปญ Traffic แบบ Step-by-Step และความต่างจาก Reach ที่ต้องรู้
4. **Step 724** — Naming Convention มาตรฐานสำหรับแคมเปญ TikTok ทั้งสอง Objective นี้
5. **Step 725** — Ad Group: Targeting พื้นฐานสำหรับ Traffic/Awareness (Location, Age, Gender, Interest, Placement)
6. **Step 726** — Ad Group: Budget, Schedule, Bid Strategy สำหรับแคมเปญแรก
7. **Step 727** — Ad Level: อัปโหลดวิดีโอ, เขียน Ad Text, ตั้ง CTA และ Destination
8. **Step 728** — หน้า Review ก่อน Publish และสิ่งที่ต้องเช็กก่อนกดปุ่ม Submit
9. **Step 729** — หลัง Publish: สิ่งที่ต้องเช็กใน 24–48 ชั่วโมงแรก และข้อผิดพลาดที่พบบ่อยของมือใหม่ TikTok
10. **Step 730** — Workshop: สร้างแคมเปญ Traffic จริงแบบ Step-by-Step ด้วยตัวเอง

---

## Step 721: เปิด TikTok Ads Manager, เลือก Custom Mode, และทำความรู้จักหน้าจอหลักก่อนสร้างแคมเปญ

### เข้า TikTok Ads Manager ได้ทางไหน

เข้าตรงผ่าน URL `ads.tiktok.com` แล้ว Login ด้วยบัญชีที่ผูกกับ TikTok Business Center (ตามที่เรียนใน Part 065) ระบบจะพาไปหน้า Dashboard ของ Ad Account ล่าสุดที่คุณใช้งานโดยอัตโนมัติ

ถ้าดูแลหลาย Ad Account ผ่าน Business Center เดียว ให้เช็กที่มุมบนซ้ายของหน้าจอ จะมี Dropdown แสดงชื่อ Ad Account ปัจจุบัน — **นี่คือจุดพลาดอันดับหนึ่งของมือใหม่ TikTok เช่นเดียวกับ Facebook**: สร้างแคมเปญผิด Ad Account เพราะไม่เช็กก่อนกด Create ตั้งเป็นสูตรนิสัยว่าทุกครั้งก่อนกด Create ให้มองชื่อ Ad Account มุมบนซ้ายก่อน 1 วินาทีเสมอ เหมือนที่เรียนใน Part 021 Step 201

### ส่วนประกอบหลักของหน้าจอ TikTok Ads Manager

แถบเมนูด้านซ้ายมีหมวดหลักคือ:

- **Campaign** — เข้าดูตาราง Campaign / Ad Group / Ad ทั้งหมด (มี Tab สลับ 3 ระดับอยู่บนตาราง)
- **Assets** — คลัง Creative, Audience, Pixel/Events, Catalog, Comment Management
- **Reporting** — สร้าง Report แบบ Custom เปรียบเทียบ Metric ข้ามช่วงเวลา
- **Tools** — Automated Rules, Split Test, Creative Center (บางเมนูอาจย้ายไปอยู่ใต้ Assets ขึ้นกับ Version UI)

แถบด้านบนของตาราง Campaign มีปุ่ม **"Create"** สีน้ำเงิน (สีต่างจาก Facebook ที่เป็นเขียว — จุดเล็กๆ ที่ช่วยแยกความรู้สึกตอนสลับหน้าจอสองแพลตฟอร์ม) ถัดจากปุ่ม Create จะมี Toggle **"Custom Mode" / "Simplified Mode"** อยู่มุมขวาบนเสมอ ซึ่งเป็นจุดที่ต้องเช็กก่อนกด Create ทุกครั้ง (รายละเอียดเจาะลึกอยู่ใน Part 067 Step 666 — สรุปสั้นคือ Custom Mode ให้ควบคุมทุกชั้นละเอียด ส่วน Simplified Mode ให้ AI ช่วยตัดสินใจมากกว่าและซ่อนตัวเลือกหลายอย่าง)

### สำหรับ Part นี้: ใช้ Custom Mode เสมอ

เพราะเราต้องการเห็นทุก Field ของ Campaign > Ad Group > Ad ครบถ้วนเพื่อฝึกความเข้าใจพื้นฐาน จึงต้องสลับ Toggle ให้เป็น **Custom Mode** ก่อนกด Create ทุกครั้งใน Part นี้ (TikTok มักตั้ง Default เป็น Simplified Mode ให้บัญชีใหม่ ต้องเปลี่ยนเอง)

### Pre-flight Check ก่อนสร้างแคมเปญทุกครั้ง

1. Ad Account ถูกต้อง (เช็กตามที่บอกไปข้างบน)
2. Payment Method Active ไม่มี Error สีแดงเตือนเรื่องบัตร/วงเงิน (เช็กที่ Billing ใต้ Business Center Settings)
3. TikTok Pixel ติดตั้งและ Active แล้ว (เช็กที่ Assets > Events ตามที่เรียนใน Part 066) — สำหรับ Traffic Campaign ไม่บังคับต้องมี Pixel แต่ควรติดไว้เสมอเพื่อเก็บข้อมูลสร้าง Custom Audience ในอนาคต
4. TikTok Business Account/Profile ที่จะใช้เป็น Identity ของโฆษณาตั้งค่าเรียบร้อยแล้ว (โลโก้, ชื่อ, Bio) ไม่ใช่โปรไฟล์เปล่า
5. Creative (วิดีโอ) เตรียมพร้อมแล้วอย่างน้อย 2–3 ตัว ในสัดส่วน 9:16 ก่อนเริ่มสร้างแคมเปญ (ห้ามเข้าไปสร้างแคมเปญก่อนแล้วค่อยไปหาวิดีโอทีหลัง เพราะจะทำให้ Draft ค้างและเสียเวลา)

### ข้อผิดพลาดที่พบบ่อยตอนเปิด Ads Manager ครั้งแรก

- ไม่เช็ก Toggle Custom/Simplified Mode แล้วงงว่าทำไมหน้าจอไม่มี Field ที่คาดหวัง
- เปิดหลาย Tab พร้อมกันแล้วแก้ไขแคมเปญคนละ Tab พร้อมกัน (ปัญหาเดียวกับ Facebook Ads Manager) ทำให้ Save ไม่ติดหรือข้อมูล Conflict
- ใช้เบราว์เซอร์ที่มี Ad Blocker Extension บล็อกบางส่วนของหน้า TikTok Ads Manager (โดยเฉพาะ Preview Player ของวิดีโอโฆษณา) ทำให้มองไม่เห็น Preview ก่อน Publish จริง

### มุมมองตารางและการค้นหา

TikTok Ads Manager มี Tab สลับ **Campaign / Ad Group / Ad** อยู่เหนือตารางเสมอ ต่างจาก Facebook ที่ใช้แถบเมนูซ้าย — คลิก Tab ไหนจะเห็นตารางของชั้นนั้นทั้งหมดในบัญชี พร้อม Filter ตาม Status, Objective, วันที่สร้าง และช่อง Search ที่ Filter ตามชื่อได้ (จุดที่ Naming Convention ใน Step 724 จะมีประโยชน์มาก)

---

## Step 722: สร้างแคมเปญ Reach (Awareness) แบบ Step-by-Step

### กดปุ่ม Create

คลิกปุ่ม **"Create"** จะเปิดหน้า Campaign Objective ให้เลือกทันที (TikTok ไม่มีขั้นตอนเลือก Buying Type แบบ Auction/Reservation แยกเหมือน Facebook ในหน้าแรก — Reach & Frequency Buying ของ TikTok จะซ่อนอยู่เป็นตัวเลือกภายใน Objective บางตัวแทน ไม่ใช่หน้าคัดกรองแรกสุด)

### เลือก Objective

TikTok แบ่ง Objective เป็น 3 กลุ่มใหญ่ตาม Funnel Stage (ตามที่เรียนใน Part 068):

1. **Awareness** — Reach
2. **Consideration** — Traffic, App Promotion, Lead Generation, Community Interaction, Video Views
3. **Conversion** — Website Conversion, App Conversion, Product Sales

คลิกเลือกกลุ่ม **Awareness** จะเห็นตัวเลือกเดียวคือ **"Reach"** (TikTok ไม่มี Brand Awareness แยกจาก Reach แบบ Facebook — Reach คือ Awareness Objective เดียวของ TikTok ในปัจจุบัน) คลิกเลือก **Reach** แล้วกด **Next**

### ตั้งชื่อ Campaign และ Advertising Type

หน้าถัดไปจะให้:

1. **Campaign Name** — ช่องกรอกชื่อ (สูตรตั้งชื่ออยู่ใน Step 724)
2. **Advertising Type** — เลือกระหว่าง **Regular** และ **Smart+ Campaign** — สำหรับ Reach ให้เลือก **Regular** เสมอ เพราะ Smart+ ของ TikTok ปัจจุบันออกแบบมาสำหรับ Conversion/Catalog เป็นหลัก ไม่รองรับ Reach Objective
3. **Campaign Budget Toggle** — เปิดหรือปิดการตั้งงบที่ระดับ Campaign (เทียบเท่า CBO) — สำหรับแคมเปญแรกที่มี Ad Group เดียว แนะนำ **ปิด Toggle นี้ไว้ก่อน** แล้วไปตั้ง Budget ที่ระดับ Ad Group แทน เพื่อให้เห็นภาพว่า Budget ผูกกับอะไรชัดเจน

กด **Next** เพื่อเข้าสู่หน้า Ad Group

### Performance Goal ของ Reach

ในหน้า Ad Group จะมีส่วน **"Optimization Goal"** ที่ผูกกับ Objective Reach จะมีตัวเลือกหลักคือ **Reach** (ให้ระบบพยายามแสดงโฆษณาให้คนไม่ซ้ำกันมากที่สุด) และในบางตลาด/บาง Placement จะมีตัวเลือกเสริม **Frequency (Reach & Frequency Buying)** ที่ต้องใช้งบขั้นต่ำสูงกว่ามากและจองล่วงหน้า (เทียบเท่า Reservation ของ Facebook) — สำหรับมือใหม่และงบไม่สูง ให้เลือก **Reach** แบบ Auction ปกติ ไม่ต้องเข้า Reach & Frequency Buying

### Frequency Cap

TikTok เปิดให้ตั้ง Frequency Cap ตรงในหน้า Ad Group สำหรับ Reach Objective ชัดเจน เช่น **"Show ads no more than 2 times per 7 days"** — ควบคุมไม่ให้คนเดิมเห็นถี่เกินไป เป็น Field ที่ TikTok เอามาไว้ในหน้าเดียวเลย ไม่ต้องเจาะเข้าเมนูย่อยเหมือน Facebook

### ทำไมแนะนำ Reach เป็นแคมเปญแรกในการฝึกมือ

- Metric อ่านง่าย (Reach, Frequency, CPM) ไม่ต้องพึ่ง Model การทำนายซับซ้อน
- ควบคุม Frequency Cap ได้ตรงๆ เห็นผลกระทบชัด
- ไม่ต้องพึ่ง Pixel Event หรือข้อมูล Conversion ใดๆ เหมาะกับบัญชีที่ยังไม่มี Pixel Data สะสม

### ข้อผิดพลาดที่พบบ่อย

- เลือก Objective "Video Views" เพราะคิดว่าคล้าย Reach ทั้งที่ Optimization Goal ต่างกัน (Video Views เน้น Optimize ให้คนดูวิดีโอนานที่สุด ไม่ใช่เข้าถึงคนมากที่สุด)
- เปิด Campaign Budget ทั้งที่มี Ad Group เดียว ทำให้งงว่า Budget หายไปไหนตอนไปดูที่ระดับ Ad Group
- เลือก Smart+ Campaign สำหรับ Reach Objective ทั้งที่ระบบไม่รองรับ ทำให้ตัวเลือกบางอย่างหายไปแบบไม่รู้ตัว

### เจาะลึกเพิ่ม: Objective ผิดแก้ไม่ได้หลัง Publish

เช่นเดียวกับ Facebook, **Campaign Objective ของ TikTok แก้ไขไม่ได้หลัง Publish** ต้องสร้างแคมเปญใหม่เท่านั้นถ้าเลือกผิด จึงต้องมั่นใจตั้งแต่ตอนเลือก Objective — วิธีป้องกันคือกลับไปดู Goal Sheet ของแคมเปญนี้ (จาก Part 004) ก่อนกดปุ่ม Create ทุกครั้งว่าเป้าหมายจริงคืออะไร

---

## Step 723: สร้างแคมเปญ Traffic แบบ Step-by-Step และความต่างจาก Reach ที่ต้องรู้

### เลือก Objective Traffic

กด Create ใหม่ เลือกกลุ่ม **Consideration** แล้วคลิก **"Traffic"** — Traffic Objective ของ TikTok มุ่งพา Traffic ไปยังปลายทางที่กำหนด (Website, App Store Listing, TikTok Shop) โดย Optimize เพื่อให้ได้จำนวนคลิกมากที่สุดในงบที่กำหนด เทียบเท่า Traffic Objective ของ Facebook ที่เรียนใน Part 022

### ตั้งชื่อ Campaign และ Advertising Type

เหมือน Step 722 ทุกประการ: ตั้งชื่อ, เลือก Advertising Type = Regular, ตัดสินใจเปิด/ปิด Campaign Budget

### Ad Group: Destination

จุดต่างสำคัญของ Traffic เทียบกับ Reach คือหน้า Ad Group จะมีส่วน **"Promotion Type"** / **"Destination"** ให้เลือกชัดเจนว่าจะพา Traffic ไปที่ไหน:

- **Website** — ไปหน้าเว็บที่ระบุ URL (ต้องมี Pixel ติดตั้งถ้าต้องการ Track Event ต่อ)
- **App** — ไปหน้า App Store/Play Store พร้อมเปิด Deep Link ได้ถ้าตั้งค่าไว้
- **TikTok Instant Page** — หน้า Landing Page แบบ Native ที่สร้างในระบบ TikTok เอง โหลดเร็วกว่าเว็บภายนอกมาก เหมาะกับตลาดที่ Internet ช้าหรือกลุ่มเป้าหมายที่ใช้มือถือเน็ตจำกัด

สำหรับแคมเปญแรก แนะนำเลือก **Website** เพื่อให้เชื่อมกับ Pixel ที่ติดตั้งไว้แล้วและเก็บข้อมูลสร้าง Custom Audience ต่อได้

### Optimization Goal ของ Traffic

จะมีตัวเลือกหลักคือ:

- **Click (Traffic)** — Optimize เพื่อให้ได้จำนวนคลิกไปยัง Landing Page มากที่สุดในงบที่กำหนด ไม่สนใจว่าคลิกแล้วคนจะทำอะไรต่อ
- **Landing Page View (LPV)** — Optimize เพื่อให้ได้คนที่คลิกแล้วหน้าเว็บโหลดสำเร็จจริงๆ (กรองคนที่คลิกแล้วปิดก่อนหน้าโหลดออกไป) ต้องมี Pixel ยิง Event พื้นฐานได้ก่อน

แนะนำเลือก **Landing Page View** เมื่อมี Pixel พร้อมแล้ว เพราะกรอง Traffic คุณภาพต่ำ (Bot Click, คนกดผิด) ออกได้ดีกว่า Click ธรรมดา ถ้ายังไม่มี Pixel ให้เลือก Click ไปก่อนแล้วค่อยย้ายมา LPV ในแคมเปญถัดไป

### ตารางเทียบ Reach vs Traffic แบบสรุป

| ประเด็น | Reach | Traffic |
|---|---|---|
| Optimize เพื่อ | คนไม่ซ้ำมากที่สุด | คลิก/LPV ไปยังปลายทางมากที่สุด |
| ต้องมี Pixel หรือไม่ | ไม่จำเป็น | ไม่บังคับ (Click) แต่แนะนำมี (LPV) |
| Metric หลักที่ดู | Reach, Frequency, CPM | Clicks, CTR, CPC, LPV, CPLPV |
| Destination ที่เลือกได้ | ไม่มี (ไม่พาไปไหน) | Website, App, Instant Page |
| เหมาะกับ | สร้างการรับรู้ ไม่มี Action ที่ต้องการทันที | ต้องการพาคนไปทำ Action ต่อ (ดูสินค้า, อ่าน Blog) |

### ข้อผิดพลาดที่พบบ่อย

- เลือก Optimization Goal = Click ทั้งที่มี Pixel พร้อมแล้ว ทำให้ได้ Traffic ปริมาณมากแต่คุณภาพต่ำ (Bounce Rate สูง)
- ตั้ง Destination เป็น Website แต่ไม่เช็กว่า Domain ตรงกับ Pixel ที่ Verify ไว้หรือไม่ ทำให้ Track ไม่ได้เต็มรูปแบบ
- ใช้ Traffic Objective เพื่อหวังให้เกิดการซื้อโดยตรง ทั้งที่ Traffic ไม่ได้ Optimize เพื่อ Conversion เลย — ถ้าต้องการยอดขายต้องใช้ Website Conversion Objective ตามที่จะเรียนใน Part 075

### เจาะลึกเพิ่ม: TikTok Instant Page คืออะไร และควรใช้เมื่อไหร่

TikTok Instant Page (บางเวอร์ชัน UI เรียก "Instant Experience" ก็มี) คือ Landing Page แบบ Native ที่สร้างขึ้นในระบบ TikTok เอง ไม่ได้ Host อยู่บนเว็บไซต์ของคุณ ข้อดีคือโหลดเร็วกว่าเว็บภายนอกมาก (เพราะ Cache ไว้ในแอป TikTok เลย) เหมาะกับ:

- กลุ่มเป้าหมายที่ใช้อินเทอร์เน็ตมือถือความเร็วจำกัด (พบมากในตลาดต่างจังหวัดของไทย)
- แคมเปญที่ต้องการหน้า Landing Page เรียบง่าย ไม่ต้องมี Feature ซับซ้อน (เช่นหน้าโปรโมชั่นสั้นๆ พร้อมปุ่มกดสั่งซื้อทาง LINE)
- ธุรกิจที่ยังไม่มีเว็บไซต์ของตัวเอง หรือเว็บไซต์หลักโหลดช้าเกินไป (ปัญหา Page Speed ตามที่เรียนใน Part 008)

ข้อจำกัดคือ Customize ได้จำกัดกว่าเว็บไซต์จริง ไม่รองรับ Tracking Script ของบุคคลที่สามบางตัว และ Pixel Event ที่ยิงได้จะจำกัดเฉพาะ Event ที่ระบบ Instant Page รองรับเท่านั้น สำหรับธุรกิจที่มีเว็บไซต์ที่โหลดเร็วอยู่แล้วและต้องการ Track Event ละเอียด แนะนำใช้ Website ปกติต่อไปดีกว่า

---

## Step 724: Naming Convention มาตรฐานสำหรับแคมเปญ TikTok ทั้งสอง Objective นี้

หลักการเหมือนที่เรียนใน Part 021 Step 203 และ Part 067 Step 665 ทุกประการ เพียงปรับสูตรให้เจาะจงกับ Traffic/Awareness Objective ของ TikTok

### สูตร Naming ระดับ Campaign

```
TT_[Objective]_[กลุ่มสินค้า/แคมเปญ]_[วันที่ YYMMDD]_[version]
```

ตัวอย่างจริง:
```
TT_Reach_เปิดสาขาลาดพร้าว_260926_v1
TT_Traffic_บล็อกรีวิวสกินแคร์_260926_v1
```

### สูตร Naming ระดับ Ad Group

```
TT_[Objective]_[Targeting Type]_[Detail]_[Placement]_[version]
```

ตัวอย่าง:
```
TT_Reach_Interest-กาแฟ_18-45All_AutoPlacement_v1
TT_Traffic_Broad-Skincare_18-45F_TikTokOnly_v1
```

### สูตร Naming ระดับ Ad

```
Video_[Concept/Hook]_[version]
```

ตัวอย่าง:
```
Video_Hookปัญหาสิว3วิ_v1
Video_UGCรีวิวลูกค้า_v2
```

### ตัวอย่างเต็มระบบ 3 ชั้น

```
Campaign:  TT_Traffic_บล็อกรีวิวสกินแคร์_260926_v1
  Ad Group: TT_Traffic_Broad-Skincare_18-45F_TikTokOnly_v1
    Ad:     Video_Hookปัญหาสิว3วิ_v1
    Ad:     Video_UGCรีวิวลูกค้า_v1
```

### ตารางตัวย่อ Objective มาตรฐานสำหรับ TikTok (ใช้ควบคู่กับตัวย่อ Facebook จาก Part 021)

| Objective TikTok | ตัวย่อ |
|---|---|
| Reach | Reach |
| Traffic | Traffic |
| App Promotion | App |
| Lead Generation | Lead |
| Community Interaction | Comm |
| Video Views | VV |
| Website Conversion | Conv |
| App Conversion | AppConv |
| Product Sales | Sales |

### หลักการเสริมเฉพาะ TikTok

เพราะ TikTok มี Placement เฉพาะ (TikTok Only vs Automatic รวม Pangle) และ Bid Strategy หลายแบบ ควรระบุ Placement ในชื่อ Ad Group เสมอ เช่น `_TikTokOnly_` หรือ `_AutoPlacement_` เพื่อให้ Filter ได้ทันทีว่า Ad Group ไหนวิ่งแค่ในแอป TikTok และตัวไหนกระจายไป Pangle Network ด้วย (ปัญหาที่เรียนใน Part 067 Step 669 ข้อ 7)

### ข้อผิดพลาดที่พบบ่อย

- ปล่อยให้ระบบตั้งชื่อ Default (เช่น "Campaign 1") ทำให้พอมีแคมเปญที่ 5 แยกไม่ออก
- ใช้ Prefix `FB_` ผิดแพลตฟอร์มเพราะเคยตั้งชื่อ Facebook มาก่อนจนติดเป็นนิสัย ต้องเช็กก่อนกด Save ทุกครั้งว่าใช้ `TT_` สำหรับแคมเปญ TikTok
- ตั้งชื่อยาวเกินไปจนตารางแสดงผลไม่ครบ ต้อง Hover อ่านทุกครั้ง

---

## Step 725: Ad Group — Targeting พื้นฐานสำหรับ Traffic/Awareness

หลังตั้งชื่อ Campaign เสร็จ กด Next จะเข้าสู่หน้า Ad Group ส่วนแรกที่ต้องตั้งคือ Targeting

### Location

Field แรก **"Location"** พิมพ์ประเทศ/จังหวัด/เมืองที่ต้องการยิง สำหรับตลาดไทยส่วนใหญ่เลือก "Thailand" ทั้งประเทศไปก่อนในแคมเปญแรก เว้นแต่ธุรกิจมีหน้าร้านเฉพาะพื้นที่ (TikTok ยังไม่มีฟีเจอร์ Drop Pin กำหนดรัศมีรอบจุดแบบ Facebook ในทุกตลาด ต้องเลือกระดับ City/District ที่มีอยู่ในระบบแทน)

### Gender, Age, Languages

- **Gender** — All, Male, Female เลือก All เป็นค่าเริ่มต้นถ้าไม่แน่ใจ
- **Age** — เลือกช่วงอายุ (13–17, 18–24, 25–34, 35–44, 45–54, 55+) เป็น Checkbox ติ๊กได้หลายช่วง ต่างจาก Facebook ที่เป็น Slider ต่อเนื่อง — TikTok แบ่งเป็น Bucket ตายตัว ต้องเลือกติ๊กช่วงที่ต้องการ ไม่สามารถกำหนดตัวเลขอายุแบบละเอียด (เช่น 27–38) ได้
- **Languages** — ปล่อยว่างไว้ (หมายถึงทุกภาษา) ยกเว้นต้องการยิงเฉพาะกลุ่มภาษาเฉพาะ

### Interest & Behavior

ช่อง **"Interest & Behavior"** ให้พิมพ์คำค้นหา ระบบจะ Suggest Category ที่เกี่ยวข้อง แบ่งเป็น 2 กลุ่มย่อยคือ:

- **Interest Category** — ความสนใจระยะยาวที่วิเคราะห์จากพฤติกรรม Engagement สะสม (เช่น Beauty & Personal Care, Food & Beverage)
- **Video Interaction Behavior / Creator Interaction Behavior** — พฤติกรรมที่วิเคราะห์จาก Interaction ล่าสุด (เช่น Like/Comment/Share วิดีโอในหมวดไหนบ่อยในช่วง 7/15/30 วันที่ผ่านมา, Follow Creator ในหมวดไหน)

ความแตกต่างสำคัญจาก Facebook Detailed Targeting คือ TikTok เพิ่ม "มิติพฤติกรรมล่าสุด" (Recent Behavior) เข้ามาชัดเจนกว่า เพราะ Machine Learning ของ TikTok ให้น้ำหนักกับ Signal สดใหม่ (Fresh Signal) มากกว่า Facebook ที่พึ่ง Historical Interest เป็นหลัก

### Automatic Targeting

TikTok มี Checkbox **"Automatic Targeting"** ให้ระบบ AI ขยาย Audience กว้างขึ้นเองนอกเหนือจากที่กำหนดไว้ (คล้าย Advantage+ Audience ของ Facebook) — สำหรับแคมเปญแรกที่ต้องการเรียนรู้กลไกพื้นฐาน แนะนำ **ปิด** Checkbox นี้ก่อน แล้วค่อยเปิดทดลองในแคมเปญถัดไปเมื่อคุ้นมือแล้ว

### Placement

เลือกระหว่าง:

- **Automatic Placement** — กระจายไปทั้ง TikTok App และ Pangle Audience Network (เครือข่ายพันธมิตรนอกแอป TikTok)
- **Select Placement** — เลือกเอง เช่น TikTok Only

สำหรับแคมเปญแรก แนะนำเลือก **TikTok Only** (Select Placement แล้วติ๊กเฉพาะ TikTok) เพื่อให้แน่ใจว่า Creative และผลลัพธ์ที่วัดได้มาจาก Native TikTok Experience จริงๆ ไม่ปนกับ Pangle ที่คุณภาพ Traffic อาจต่างกันมาก (รายละเอียดเจาะลึกเรื่อง Placement เต็มรูปแบบอยู่ใน Part 070)

### ตัวอย่าง Targeting ที่ตั้งค่าสมบูรณ์สำหรับ Traffic Campaign

```
Location: Thailand
Gender: All
Age: 18-24, 25-34, 35-44
Languages: (ว่าง = ทุกภาษา)
Interest: Beauty & Personal Care, Skincare
Behavior: Engaged with Beauty content in last 7 days
Automatic Targeting: ปิด
Placement: Select Placement > TikTok Only
```

### ข้อผิดพลาดที่พบบ่อย

- ติ๊ก Age Bucket เดียว (เช่น เฉพาะ 18–24) ทั้งที่กลุ่มเป้าหมายจริงกว้างกว่านั้นมาก ทำให้ Audience แคบเกินจำเป็นตั้งแต่แคมเปญแรก
- เลือก Automatic Targeting พร้อม Interest แคบมากในเวลาเดียวกัน ทำให้ระบบสับสนว่าจะเน้นทางไหน
- ไม่รู้ว่า Placement Automatic รวม Pangle ด้วย ทำให้งบไหลไปนอกแอป TikTok โดยไม่ตั้งใจ แล้วมาสงสัยทีหลังว่าทำไมผลลัพธ์ไม่เหมือนที่คาด

---

## Step 726: Ad Group — Budget, Schedule, Bid Strategy สำหรับแคมเปญแรก

### Budget

ถ้าปิด Campaign Budget ไว้ที่ระดับ Campaign (ตามที่แนะนำใน Step 722/723) การตั้งงบจะมาอยู่ที่ระดับ Ad Group นี้ มีสองแบบ:

- **Daily Budget** — งบต่อวัน ระบบพยายามใช้ให้ใกล้เคียงจำนวนนี้ทุกวัน
- **Total Budget** — งบรวมทั้ง Ad Group ตลอดช่วงเวลาที่กำหนด (เทียบเท่า Lifetime Budget ของ Facebook) ต้องระบุ Start/End Date คู่กัน

สำหรับมือใหม่ แนะนำ **Daily Budget** เพราะปรับ/หยุดง่ายกว่า

### Budget ขั้นต่ำที่แนะนำสำหรับตลาดไทย

| Objective | Daily Budget ขั้นต่ำที่แนะนำ | เหตุผล |
|---|---|---|
| Reach (Awareness) | 300–500 บาท | TikTok มี Minimum Daily Budget ต่อ Ad Group ที่สูงกว่า Facebook พอสมควร (มักอยู่ที่ประมาณ 300+ บาทขึ้นไปตาม Currency/ตลาด) |
| Traffic | 400–600 บาท | ต้องได้ Click/LPV มากพอต่อวันเพื่อให้ระบบเก็บข้อมูล Optimize ได้ |

หมายเหตุ: TikTok กำหนด **Minimum Budget ต่อ Ad Group** ไว้ชัดเจนกว่า Facebook (มักแสดง Error ทันทีถ้าตั้งต่ำกว่าเกณฑ์ เช่น "Budget must be at least ฿XXX") ตัวเลขจริงอาจเปลี่ยนตาม Currency ของ Ad Account และนโยบายล่าสุด ให้เช็กที่ข้อความ Error/Suggestion ที่ระบบแสดงในหน้าจอจริงเสมอ เพราะปรับเปลี่ยนได้บ่อย

### Schedule

- **Start Date** — วันเริ่มต้น (Default มักเป็นวันนี้ทันทีที่ Publish)
- **End Date** — ถ้าเลือก Total Budget ต้องระบุ ถ้าเลือก Daily Budget สามารถเลือก "No End Date" (รันต่อเนื่องไม่มีกำหนด) หรือระบุ End Date ก็ได้
- **Dayparting** — ตัวเลือก "Run ads all day" หรือ "Select time and days to run ads" ให้กำหนดช่วงเวลาของวัน/วันในสัปดาห์ที่ต้องการให้โฆษณาวิ่ง เหมาะกับธุรกิจที่รู้ชัดว่าลูกค้า Active ช่วงไหน (เช่น ร้านอาหารเปิดเฉพาะช่วงเย็น)

### Bid Strategy

สำหรับ Reach และ Traffic Objective ตัวเลือก Bid Strategy หลักคือ:

- **Lowest Cost** (ค่า Default) — ให้ระบบหาผลลัพธ์ให้มากที่สุดในงบที่กำหนด โดยไม่จำกัดราคาต่อผลลัพธ์
- **Cost Cap** — กำหนดเพดานราคาเฉลี่ยต่อผลลัพธ์ที่ยอมจ่าย ระบบจะพยายามควบคุมให้ไม่เกินตัวเลขนี้โดยเฉลี่ย (มีใน Objective บางตัวเท่านั้น มักไม่แสดงสำหรับ Reach เพราะ Reach ไม่มี "ราคาต่อผลลัพธ์" ที่ชัดเจนแบบ Click/Conversion)

สำหรับแคมเปญแรก แนะนำใช้ **Lowest Cost** ไปก่อนเพื่อให้ระบบเก็บข้อมูลได้เร็วที่สุด ยังไม่ต้องตั้ง Cost Cap จนกว่าจะมีข้อมูล Benchmark ราคาจริงของธุรกิจตัวเองแล้ว

### Delivery Type

TikTok มีตัวเลือก **Delivery Type**: **Standard** (กระจายงบสม่ำเสมอตลอดวัน) หรือ **Accelerated** (เร่งใช้งบให้เร็วที่สุด เหมาะกับ Promotion ระยะสั้นที่ต้องการผลเร็ว) — แนะนำ Standard สำหรับแคมเปญแรก

### ตัวอย่าง Ad Group Budget/Bid ที่ตั้งค่าสมบูรณ์

```
Budget: Daily Budget 500 บาท/วัน
Schedule: Start ทันที, No End Date, Run ads all day
Bid Strategy: Lowest Cost
Delivery Type: Standard
Frequency Cap: ไม่เกิน 2 ครั้ง/7 วัน (เฉพาะ Reach)
```

### ข้อผิดพลาดที่พบบ่อย

- ตั้ง Daily Budget ต่ำกว่า Minimum ที่ระบบกำหนด ทำให้ Publish ไม่ผ่าน แล้วงงว่าทำไม Error
- เลือก Total Budget แต่ลืมตั้ง End Date ทำให้ระบบไม่ยอมให้ Publish
- ตั้ง Cost Cap ทั้งที่ยังไม่มีข้อมูล Benchmark ราคาจริง ทำให้ตั้งเพดานต่ำเกินตลาดจนระบบใช้งบไม่หมด (Under-delivery)

### เจาะลึกเพิ่ม: ทำไมการปรับ Budget ทีละมากๆ กระทบ Learning เหมือน Facebook

หลักการเดียวกับที่เรียนใน Part 021 Step 205: การปรับ Budget แบบก้าวกระโดด (เช่น จาก 500 บาท เป็น 3,000 บาททันที) ทำให้ Ad Group เข้าสู่สถานะ Learning ใหม่บางส่วน กระทบ Pacing และ Performance ชั่วคราว 1–2 วัน แนะนำปรับทีละ 15–20% ทุก 2–3 วันเมื่อต้องการ Scale (รายละเอียดเต็มอยู่ใน Part 086)

---

## Step 727: Ad Level — อัปโหลดวิดีโอ, เขียน Ad Text, ตั้ง CTA และ Destination

### Identity

ส่วนแรกของหน้า Ad คือ **Identity** — เลือก TikTok Account/Business Account ที่จะใช้แสดงเป็นผู้โพสต์โฆษณา ชื่อ, รูปโปรไฟล์, Link Bio ที่คนเห็นจะมาจาก Identity นี้ ถ้า Business Center มีหลาย Identity ต้องเลือกให้ตรงกับแบรนด์/ลูกค้าที่ถูกต้องเสมอ

### Ad Format

TikTok สำหรับ Objective Traffic/Reach ส่วนใหญ่รองรับ:

- **Single Video** — วิดีโอเดียว รูปแบบหลักและแนะนำที่สุดสำหรับแคมเปญแรก
- **Single Image** — บาง Placement รองรับภาพนิ่ง (ผลลัพธ์มักด้อยกว่าวิดีโอมากในบริบท TikTok เพราะผู้ใช้คุ้นกับ Content แบบวิดีโอเคลื่อนไหว)
- **Spark Ads** — Boost วิดีโอ Organic ที่มีอยู่แล้วบนโปรไฟล์ TikTok จริง (เจาะลึกเต็มรูปแบบใน Part 077)

สำหรับแคมเปญแรก แนะนำ **Single Video** อัปโหลดใหม่โดยตรง

### อัปโหลดวิดีโอ

กดปุ่ม **"Upload"** เลือกไฟล์จากคอมพิวเตอร์ หรือเลือกจาก **"TikTok Creative Center"** (คลัง Template/Trend) หรือใช้เครื่องมือ **"Smart Video"** ที่ช่วยตัดต่ออัตโนมัติจากภาพนิ่ง/วิดีโอดิบที่มีอยู่

Spec ที่แนะนำสำหรับวิดีโอ TikTok:

- **สัดส่วนภาพ**: 9:16 (แนวตั้งเต็มจอ) เป็นหลัก — รองรับ 1:1 และ 16:9 แต่ผลลัพธ์มักด้อยกว่า 9:16 อย่างชัดเจนในฟีด For You Page
- **ความยาว**: 9–15 วินาทีสำหรับ Traffic/Awareness ทั่วไป (ยาวได้ถึง 60 วินาที แต่ Hook ต้องจับใน 3 วินาทีแรกเสมอ)
- **ขนาดไฟล์**: ไม่เกิน 500MB
- **ความละเอียด**: อย่างน้อย 720x1280 พิกเซล แนะนำ 1080x1920

### Ad Text (Copy)

ช่อง **"Ad Text"** จำกัดความยาวประมาณ 100 ตัวอักษร (สั้นกว่า Primary Text ของ Facebook มาก) แสดงอยู่เหนือปุ่ม CTA ในหน้าฟีด — ต้องเขียนให้กระชับ ตรงประเด็น ไม่ใช่เล่าเรื่องยาว เพราะพื้นที่จำกัดและผู้ใช้ TikTok สไลด์ผ่านเร็ว

ตัวอย่างที่ใช้ได้จริง:
```
เซรั่มวิตซี ลดสิวใน 7 วัน กดอ่านรีวิวจริงที่นี่ 👇
```

### Destination

ถ้าเลือก Promotion Type = Website จะมีช่อง **"Website URL"** ให้กรอก URL ปลายทาง ต้องตรงกับ Domain ที่ Pixel Verify ไว้แล้ว (ตามที่เรียนใน Part 066)

### Call to Action (CTA)

Dropdown เลือก CTA เช่น "Shop Now", "Learn More", "Sign Up", "Download Now", "Contact Us" — เลือกให้ตรงกับ Action ที่ต้องการจริง เช่น Traffic ไปหน้า Blog รีวิว ใช้ "Learn More" เหมาะกว่า "Shop Now"

### URL Parameters (UTM Tracking)

ต่อท้าย Website URL ด้วย UTM Parameter เพื่อ Track ผ่าน Google Analytics คู่กัน:

```
Website URL: https://mystore.com/blog/best-skincare-routine
URL Parameters: utm_source=tiktok&utm_medium=paid&utm_campaign=__CAMPAIGN_NAME__&utm_content=__AID__
```

TikTok มีตัวแปร Dynamic Parameter เฉพาะตัว เช่น `__CAMPAIGN_ID__`, `__AID__`, `__CID__` — ต้องเช็ค Documentation ล่าสุดของ TikTok เสมอเพราะชื่อ Parameter อาจเปลี่ยนตาม UI Version (รายละเอียดเต็มเรื่อง UTM/GA4 อยู่ใน Part 089)

### Caption และ Sound Setting

TikTok เปิดให้เพิ่ม **Auto Caption** (คำบรรยายอัตโนมัติจากเสียงพูดในวิดีโอ) ตรงจากหน้า Ad Level — แนะนำเปิดใช้เสมอ เพราะช่วยคนที่เปิดเสียงปิด (Sound Off) ยังเข้าใจเนื้อหาได้ และ TikTok มักให้ Reach ดีขึ้นเล็กน้อยกับวิดีโอที่มี Caption ครบ

### ข้อผิดพลาดที่พบบ่อยระดับ Ad

- อัปโหลดวิดีโอที่ตัดมาจาก Facebook Ads ตรงๆ (สัดส่วน 1:1 หรือ 16:9, มี Watermark แพลตฟอร์มอื่น, จังหวะตัดต่อแบบโฆษณาทีวี) ไม่ปรับให้เป็น Native TikTok — ทำให้ผลลัพธ์แย่กว่าที่ควรมาก แม้ Targeting/Budget ถูกทุกอย่าง
- Destination URL ไม่ตรงกับ Domain ที่ Pixel Verify ไว้ ทำให้เสีย Data ทั้งแคมเปญ
- เลือก CTA ไม่สอดคล้องกับปลายทางจริง (เช่นเลือก "Shop Now" แต่พาไปหน้า Blog ที่ไม่มีปุ่มซื้อ) ทำให้ผู้ใช้สับสนและ Bounce สูง

---

## Step 728: หน้า Review ก่อน Publish และสิ่งที่ต้องเช็กก่อนกดปุ่ม Submit

### Checklist ก่อนกด Submit

หน้า Review ของ TikTok จะสรุปทุกชั้น (Campaign/Ad Group/Ad) ให้เห็นในหน้าเดียว ก่อนกดปุ่ม **"Submit"** (สีน้ำเงิน มุมขวาล่าง) ให้ไล่เช็กตามลำดับนี้:

1. **Objective ถูกต้องตามที่ตั้งใจ** (Reach หรือ Traffic ตามที่ต้องการจริง — แก้ไม่ได้หลัง Publish)
2. **ชื่อ Campaign/Ad Group/Ad ตรงตาม Naming Convention** ที่วางไว้ (Step 724)
3. **Location, Age, Gender, Interest ตรงกับกลุ่มเป้าหมายจริง** ไม่ใช่ Default ที่ระบบตั้งมาให้
4. **Budget และ Schedule ถูกต้อง** ไม่เผลอตั้ง Total Budget ผิดจำนวนศูนย์ (พลาดจุดทศนิยม/ศูนย์เกินคือความผิดพลาดที่แพงที่สุดที่พบได้จริง)
5. **Placement ตรงตามที่ตัดสินใจ** (Automatic หรือ TikTok Only)
6. **Destination URL ถูกต้อง ไม่มีตัวอักษรพิมพ์ผิด** ทดสอบคลิกลิงก์จาก Preview จริงก่อน Submit เสมอ
7. **Preview วิดีโอเล่นได้ปกติ ไม่มีเสียง/ภาพขาดหาย** ใช้ Preview Panel ด้านขวาของหน้า Ad ที่จำลองหน้าจอมือถือจริง
8. **Pixel/Event ที่เลือกถูกต้อง** (สำหรับ Traffic ที่ใช้ LPV Optimization Goal)
9. **Payment Method พร้อมรับการเก็บเงิน**

### Preview Panel

ด้านขวาของหน้า Ad จะมี Preview Panel จำลองหน้าจอมือถือแบบ Real-time ให้ดูว่าโฆษณาจะแสดงผลอย่างไรจริงบน For You Page พร้อมปุ่มสลับดู Preview บน Placement ต่างๆ (TikTok, Pangle) — ควรดูให้ครบทุก Placement ที่เลือกไว้ก่อน Submit เสมอ ไม่ใช่ดูแค่อันแรกที่โชว์

### สถานะหลัง Submit

หลังกด Submit แคมเปญจะเข้าสถานะ **"Under Review"** ก่อนเสมอ (ระบบตรวจสอบ Policy อัตโนมัติและอาจมีทีมคนตรวจเพิ่มในบางกรณี) ใช้เวลาปกติประมาณ **ไม่กี่นาทีถึง 24 ชั่วโมง** ขึ้นกับความซับซ้อนของ Content และหมวดธุรกิจ (สินค้าหมวด Sensitive เช่น การเงิน/สุขภาพ อาจใช้เวลานานกว่า) ระหว่างนี้แคมเปญจะยังไม่วิ่งจริง ต้องรอสถานะเปลี่ยนเป็น **"Active"** ก่อน

### ข้อผิดพลาดที่พบบ่อยตอน Review

- ไม่เช็ก Preview บนทุก Placement ก่อน Submit ทำให้พลาดเรื่อง Caption ล้นเฟรมหรือข้อความถูกปุ่ม CTA บังในบาง Placement
- Submit แคมเปญที่ยังเป็น Draft ไม่สมบูรณ์เพราะรีบ ทำให้ระบบ Reject กลับมาแก้ไขหลายรอบ เสียเวลามากกว่าเช็กให้ครบตั้งแต่ต้น
- ไม่รู้ว่าแคมเปญเข้าสถานะ Under Review แล้วรีบปิด Ads Manager ไปเลย ไม่ได้กลับมาเช็กว่าผ่านหรือถูก Reject

---

## Step 729: หลัง Publish — สิ่งที่ต้องเช็กใน 24–48 ชั่วโมงแรก และข้อผิดพลาดที่พบบ่อยของมือใหม่ TikTok

### ชั่วโมงที่ 0–6: เช็กสถานะการ Approve

เปิด Ads Manager กลับมาเช็กว่าแคมเปญเปลี่ยนจาก "Under Review" เป็น **"Active"** แล้วหรือยัง ถ้าขึ้นสถานะ **"Rejected"** ให้เข้าไปดูเหตุผลที่ระบบแจ้งไว้ (มักอยู่ที่ระดับ Ad) ปกติเป็นเรื่อง Policy เนื้อหา (เช่น มีข้อความ Overclaim, ใช้ Font ที่ระบบตรวจไม่ผ่าน Text Overlay Ratio) แก้ไข Creative/Copy แล้ว Resubmit ใหม่ได้โดยไม่ต้องสร้างแคมเปญใหม่ทั้งหมด (แก้แค่ระดับ Ad ที่มีปัญหา)

### ชั่วโมงที่ 6–24: เช็ก Delivery และ Spend Pacing

- แคมเปญเริ่มมี **Impressions/Reach** ขึ้นหรือยัง ถ้าผ่านไป 6+ ชั่วโมงแล้ว Impressions ยังเป็น 0 ให้เช็ก: Budget ตั้งถูกหรือไม่, Targeting แคบเกินไปหรือไม่, Bid Strategy ตั้ง Cost Cap ต่ำเกินตลาดหรือไม่
- **Spend เทียบกับ Budget ที่ตั้งไว้** — ถ้า Spend ต่ำกว่า Budget มากในวันแรก (Under-delivery) มักเกิดจาก Targeting แคบหรือ Bid ต่ำเกินไป
- **CPM** เทียบกับ Benchmark อุตสาหกรรม (สำหรับตลาดไทย CPM TikTok มักอยู่ในช่วง 30–80 บาทต่อ 1,000 Impressions ขึ้นกับหมวดธุรกิจและช่วงเวลา — ตัวเลขนี้ผันผวนตามฤดูกาลและการแข่งขัน ใช้เป็นแนวทางประกอบ ไม่ใช่มาตรฐานตายตัว)

### ชั่วโมงที่ 24–48: เช็ก Learning Status และ Metric ตาม Objective

เข้าไปดูคอลัมน์ **"Delivery Status"** ที่ระดับ Ad Group จะแสดงสถานะ **"Learning"** หรือ **"Learning Limited"** (ถ้าจำนวน Optimization Event ต่อสัปดาห์ไม่พอ ตามเกณฑ์ ~50 Event/สัปดาห์ที่เรียนใน Part 067 Step 661)

สำหรับ **Reach Campaign** ดู: Reach ทั้งหมด, Frequency เฉลี่ย, CPM — ถ้า Frequency เกิน Cap ที่ตั้งไว้แสดงว่า Frequency Cap อาจไม่ทำงานตามที่คาด ต้องเช็กการตั้งค่าซ้ำ

สำหรับ **Traffic Campaign** ดู: Clicks, CTR, CPC, Landing Page View Rate (LPV/Click) — ถ้า CTR ต่ำกว่า 1% อย่างต่อเนื่องในตลาดไทย ควรพิจารณาเปลี่ยน Creative ก่อนอย่างอื่น เพราะปัญหามักอยู่ที่ Hook ไม่น่าสนใจมากกว่า Targeting

### เจาะลึกเพิ่ม: ตาราง Delivery Status ทั้งหมดที่ควรรู้จัก

คอลัมน์ Delivery Status ที่ระดับ Ad Group ของ TikTok มีสถานะหลักที่พบบ่อยดังนี้ ควรจำความหมายให้ครบเพื่อวินิจฉัยปัญหาได้เร็ว:

| สถานะ | ความหมาย | สิ่งที่ควรทำ |
|---|---|---|
| **Active** | กำลังวิ่งปกติ | Monitor ตามรอบปกติ |
| **Learning** | อยู่ในช่วงเรียนรู้ Auction ยังไม่นิ่ง | ปล่อยให้วิ่งต่อ ไม่แก้ไข อย่างน้อย 3–7 วัน หรือจน Event สะสมครบเกณฑ์ |
| **Learning Limited** | Event ต่อสัปดาห์ไม่พอ ระบบเรียนรู้ได้จำกัด | เพิ่ม Budget, ขยาย Targeting ให้กว้างขึ้น หรือรวม Ad Group เข้าด้วยกัน |
| **Not Delivering** | ไม่มีการแสดงผลเลย | เช็ก Budget, Bid, Targeting แคบเกินไปหรือ Ad ถูก Reject |
| **Pending Review / Under Review** | รอตรวจสอบ Policy | รอ ไม่ต้องแก้ไขอะไรถ้าไม่มี Error แจ้ง |
| **Rejected** | ไม่ผ่าน Policy | เข้าไปดูเหตุผลที่ระดับ Ad แล้วแก้ไข Resubmit |
| **Inactive/Paused** | ถูกปิดโดยผู้ใช้หรือหมดงบ/หมดกำหนดเวลา | เช็กว่าปิดโดยตั้งใจหรือไม่ ถ้าหมดงบให้เพิ่ม Budget/Schedule |

### เจาะลึกเพิ่ม: การ Monitor ผ่านมือถือในช่วง 48 ชั่วโมงแรก

TikTok มี App แยกชื่อ **"TikTok Ads Manager"** สำหรับมือถือ ใช้เช็คสถานะด่วนระหว่างวันได้ (เปิด/ปิด Ad Group, ดู Spend, ดู Delivery Status) เหมาะกับช่วง 48 ชั่วโมงแรกที่ต้องเช็คบ่อยแต่ไม่ได้อยู่หน้าคอมพิวเตอร์ตลอดเวลา แต่เช่นเดียวกับ Facebook (ตามที่เรียนใน Part 021 Step 201) **ไม่แนะนำให้สร้างหรือแก้ไขโครงสร้างแคมเปญจากมือถือ** เพราะ Field หลายอย่าง (Detailed Targeting, Bid Strategy แบบละเอียด) จะถูกย่อ/ซ่อนไปเมื่อเทียบกับเวอร์ชันเว็บ ให้ใช้มือถือเป็นเครื่องมือ Monitor เท่านั้น

### ข้อผิดพลาดที่พบบ่อยในช่วง 24–48 ชั่วโมงแรก

1. **ปิด/แก้ไขแคมเปญเร็วเกินไป** — เห็นตัวเลขยังไม่ดีใน 2–3 ชั่วโมงแรกแล้วรีบปิด ทั้งที่ระบบยังอยู่ใน Learning Phase ปกติ ต้องให้เวลาอย่างน้อย 24–48 ชั่วโมงก่อนตัดสินใจใดๆ
2. **แก้ Targeting/Budget ซ้ำๆ ในวันเดียว** — ทุกครั้งที่แก้ไขสำคัญจะรีเซ็ต Learning Phase บางส่วน ทำให้ไม่มีวันได้ข้อมูลที่เสถียรพอ
3. **ไม่เช็ก Breakdown by Placement** — ไม่รู้ว่างบไหลไป Pangle มากกว่าที่คิด (ถ้าเลือก Automatic Placement) ทำให้ตัวเลขรวมดูเพี้ยนจากที่คาด
4. **เข้าใจผิดว่า TikTok ไม่มี Learning Phase** เพราะเคยได้ยินว่า TikTok "Optimize เร็วกว่า Facebook" — ความจริงมี Learning Phase เหมือนกัน เพียงแต่บาง Ad Group ที่ Budget สูงและ Targeting กว้างอาจผ่านไวกว่าที่คุ้นเคยจาก Facebook เท่านั้น ไม่ใช่ไม่มีเลย
5. **ไม่ตรวจสอบว่า Comment ใต้โฆษณาเป็นลบหรือมีคนถามคำถามที่ต้องตอบ** — TikTok เป็นแพลตฟอร์มที่คนคอมเมนต์ใต้โฆษณาโดยตรงมากกว่า Facebook มาก ถ้าไม่มีแอดมินตอบคอมเมนต์ อาจเสียโอกาสปิดการขายหรือปล่อยให้คอมเมนต์ลบสะสมกระทบความน่าเชื่อถือ

---

## Case Study: ร้านสกินแคร์ออนไลน์ทดสอบ Traffic Campaign ครั้งแรกบน TikTok

ร้านสกินแคร์ขนาดเล็กในกรุงเทพฯ เคยยิง Facebook Ads มา 8 เดือน ต้องการขยายมา TikTok เป็นครั้งแรก โดยมีเป้าหมายพา Traffic ไปยังหน้า Blog รีวิว "5 ขั้นตอนดูแลผิวหน้าสิว" บนเว็บไซต์ตัวเอง (เป็น Content ที่ทำ SEO ไว้อยู่แล้ว ไม่ใช่หน้าขายตรง) เพื่อ Warm Up ก่อนทำ Retargeting ต่อในอนาคต

**การตั้งค่า:**
```
Campaign: TT_Traffic_บล็อกรีวิวสิว_260901_v1
Objective: Traffic, Advertising Type: Regular, Campaign Budget: ปิด
Ad Group: TT_Traffic_Broad-Skincare_18-34F_TikTokOnly_v1
Targeting: Location Thailand, Gender Female, Age 18-24+25-34,
           Interest: Skincare, Beauty & Personal Care
           Automatic Targeting: ปิด, Placement: TikTok Only
Optimization Goal: Landing Page View
Budget: Daily 500 บาท/วัน, Bid Strategy: Lowest Cost
Ad: 3 วิดีโอ UGC ความยาว 12-15 วินาที สัดส่วน 9:16
```

**ผลลัพธ์ 7 วันแรก:**

สัปดาห์แรกทีมทำผิดพลาดสำคัญคือใช้วิดีโอ 2 จาก 3 ตัวที่เคยตัดมาจาก Facebook Ads เดิม (สัดส่วน 1:1 มี Logo ร้านมุมขวาบนแบบ Static เหมือนโฆษณาทีวี) ผลคือ CTR เฉลี่ยอยู่ที่ 0.6% เท่านั้น (ต่ำกว่า Benchmark ตลาดไทยที่ควรอยู่ 1–2%+ สำหรับ Traffic Objective) ส่วนวิดีโอตัวที่ 3 ซึ่งเป็น UGC ถ่ายแนวตั้งโดยลูกค้าจริงพูดถึงปัญหาสิวของตัวเองแบบเรียล ๆ ทำ CTR ได้ 2.3% — ต่างกันเกือบ 4 เท่าโดยที่ Targeting/Budget เหมือนกันทุกอย่าง

**การปรับแก้:** วันที่ 5 ทีมปิดวิดีโอ 2 ตัวที่ CTR ต่ำ เหลือแต่วิดีโอ UGC ตัวเดียว และผลิตวิดีโอ UGC เพิ่มอีก 2 คอนเซปต์ในสไตล์เดียวกัน (ถ่ายแนวตั้งด้วยมือถือ ไม่มี Logo Static) อัปโหลดเป็น Ad ใหม่ในระหว่างที่ Ad Group เดิมยังวิ่งต่อเนื่อง (ไม่ได้สร้าง Ad Group ใหม่ เพื่อไม่ให้ Learning Phase รีเซ็ต)

**ผลลัพธ์สัปดาห์ที่ 2:** CTR เฉลี่ยรวมขยับมาที่ 1.9%, CPC ลดลงจาก 8.20 บาท เป็น 4.10 บาท, Landing Page View Rate อยู่ที่ 78% ของ Click ทั้งหมด (แปลว่าหน้าเว็บโหลดเร็วพอสมควร ไม่มีปัญหา Page Speed ที่เรียนใน Part 008)

**บทเรียนสำคัญ:** ปัญหาที่ดูเหมือนเป็นเรื่อง Targeting หรือ Budget แท้จริงมักเป็นเรื่อง Creative Native vs Non-Native เป็นอันดับหนึ่งบน TikTok — ยืนยันหลักการที่เรียนใน Part 067 Step 669 ว่า "ใช้ Creative จาก Facebook ตรงๆ" คือสาเหตุอันดับหนึ่งของ CTR ต่ำในโฆษณา TikTok

---

## ตารางสรุปการวินิจฉัยปัญหาเบื้องต้น (Quick Diagnosis Table)

ก่อนไปถึง Checklist สรุปตารางนี้ไว้เป็นเครื่องมือวินิจฉัยด่วนเมื่อแคมเปญ Traffic/Reach แรกของคุณมีอาการผิดปกติ:

| อาการที่เจอ | สาเหตุที่เป็นไปได้มากที่สุด | วิธีเช็ก | วิธีแก้ |
|---|---|---|---|
| Impressions = 0 หลัง Active 6+ ชม. | Bid/Cost Cap ต่ำเกินตลาด, Targeting แคบเกินไป, Budget ต่ำกว่า Minimum จริง | เช็ก Delivery Status, เช็ก Audience Size | เพิ่ม Budget, ขยาย Targeting, เปลี่ยนเป็น Lowest Cost |
| Spend ต่ำกว่า Budget มาก (Under-delivery) | เหตุผลเดียวกับข้างบน หรือ Ad ถูก Limited Delivery จาก Policy | เช็ก Ad Status ระดับ Ad | Resubmit Creative ที่แก้ปัญหา Policy แล้ว |
| CTR ต่ำกว่า 1% ต่อเนื่อง | Creative ไม่ Native, Hook ไม่น่าสนใจใน 3 วิแรก | เทียบ CTR รายตัว Ad | เปลี่ยน Hook, ถ่ายใหม่แบบ UGC/Native 9:16 |
| CPM สูงกว่า Benchmark มาก | Targeting แคบ, แข่งประมูลสูงในช่วงเทศกาล, หมวดธุรกิจ Sensitive | เทียบช่วงเวลา/หมวดธุรกิจ | ขยาย Targeting, เลี่ยงช่วงเทศกาลถ้าเป็นไปได้ |
| Frequency พุ่งสูงเกิน Cap ที่ตั้ง | Audience เล็กเกินไปเทียบกับ Budget | เช็ก Reach vs Audience Size | ขยาย Audience หรือลด Budget ต่อ Ad Group |
| LPV Rate ต่ำกว่า 50% ของ Click | หน้าเว็บโหลดช้า, Domain ไม่ตรง Pixel | ทดสอบเปิดลิงก์จากมือถือจริง | แก้ Page Speed ตาม Part 008, เช็ก Domain Verification |

---

## Checklist ท้ายบท

- [ ] เข้า TikTok Ads Manager และเช็ก Ad Account ถูกต้องก่อนกด Create ทุกครั้ง
- [ ] สลับ Toggle เป็น Custom Mode ก่อนสร้างแคมเปญ
- [ ] เลือก Objective ตรงกับเป้าหมายจริง (Reach สำหรับสร้างการรับรู้, Traffic สำหรับพา Action ไปทำต่อ)
- [ ] เลือก Advertising Type = Regular (ไม่ใช่ Smart+) สำหรับแคมเปญฝึกมือ
- [ ] ตั้งชื่อ Campaign/Ad Group/Ad ตาม Naming Convention (Prefix `TT_`)
- [ ] ตั้ง Targeting ไม่แคบเกินไป (Interest 3–6 คำ ไม่ Narrow ซ้อนหลายชั้น)
- [ ] ตัดสินใจ Placement ชัดเจน (TikTok Only หรือ Automatic) และรู้ผลกระทบของแต่ละแบบ
- [ ] ตั้ง Budget ไม่ต่ำกว่า Minimum ที่ระบบกำหนด
- [ ] เลือก Optimization Goal ให้ตรงกับ Pixel ที่มี (LPV ถ้ามี Pixel พร้อม, Click ถ้ายังไม่มี)
- [ ] วิดีโอทุกตัวเป็น Native 9:16 ไม่ใช่ Creative ตัดมาจาก Facebook
- [ ] ตั้ง Destination URL ตรงกับ Domain ที่ Pixel Verify แล้ว พร้อม UTM Parameter
- [ ] เช็ก Preview ทุก Placement ก่อน Submit
- [ ] รอ 24–48 ชั่วโมงก่อนตัดสินใจปรับแก้ใดๆ หลัง Publish
- [ ] เช็ก Breakdown by Placement ทุกสัปดาห์เพื่อดูว่างบไหลไป Pangle เท่าไหร่

---

## Workshop / แบบฝึกหัด

### ภารกิจที่ 1: สร้างแคมเปญ Reach จริง (Draft)

เปิด TikTok Ads Manager ของธุรกิจตัวเอง/ลูกค้า สร้างแคมเปญ Reach ตาม Custom Mode ครบทุกขั้นตอนที่เรียนใน Step 722, 724, 725, 726 (บันทึกเป็น Draft ได้ถ้ายังไม่พร้อม Publish จริง) ใช้ Naming Convention ให้ครบทั้ง 3 ชั้น

### ภารกิจที่ 2: สร้างแคมเปญ Traffic เต็มรูปแบบและ Publish จริง

ต่อจากภารกิจที่ 1 สร้างแคมเปญ Traffic ที่มีเป้าหมายพา Traffic ไปยัง Content ที่ไม่ใช่หน้าขายตรง (เช่น Blog, บทความรีวิว, หน้า Landing Page แนะนำสินค้า) พร้อมอัปโหลดวิดีโอ Native 9:16 อย่างน้อย 3 ตัวที่แนวคิด (Hook) ต่างกัน แล้ว Submit จริงด้วยงบทดสอบ 400–600 บาท/วัน

โครงสร้างที่ต้องทำให้ครบ:

```
Campaign: TT_Traffic_[ชื่อสินค้า/Content]_[YYMMDD]_v1
  Ad Group: TT_Traffic_Broad-[Interest หลัก]_[Age]_TikTokOnly_v1
    Ad: Video_Hook1_v1
    Ad: Video_Hook2_v1
    Ad: Video_Hook3_v1
```

### ภารกิจที่ 3: บันทึกผล 48 ชั่วโมงแรก

ทำตาราง Tracking แบบง่ายบันทึกทุก 6–12 ชั่วโมง: Impressions, Clicks, CTR, CPC, LPV Rate, Spend, Delivery Status ของ Ad Group แล้ววิเคราะห์ว่า Ad ตัวไหนทำ CTR ได้ดีที่สุด และลองเชื่อมโยงว่าเพราะ Hook แบบไหน

### ภารกิจที่ 4: เขียนสรุปเปรียบเทียบ Reach vs Traffic

หลังรันทั้งสองแคมเปญอย่างน้อย 3 วัน เขียนสรุป 1 หน้ากระดาษเปรียบเทียบว่า Objective ไหนเหมาะกับเป้าหมายธุรกิจปัจจุบันมากกว่า และเพราะอะไร (อ้างอิงตัวเลขจริงจากแคมเปญที่ทำ ไม่ใช่ความรู้สึก)

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้พาคุณสร้างแคมเปญ TikTok สองแบบแรกด้วยตัวเองแบบ Step-by-Step ทั้ง Reach (Awareness) และ Traffic ครอบคลุมตั้งแต่เปิด Ads Manager, เลือก Custom Mode, ตั้งค่า Campaign/Ad Group/Ad ครบทุก Field, Naming Convention, ไปจนถึงการ Monitor ผลลัพธ์ในช่วง 24–48 ชั่วโมงแรกและข้อผิดพลาดที่พบบ่อยที่สุดของมือใหม่ TikTok — โดยเฉพาะเรื่อง Creative ที่ต้องเป็น Native 9:16 อย่างแท้จริง ไม่ใช่ของที่เหลือจาก Facebook

ทักษะการสร้างแคมเปญพื้นฐานนี้จะเป็นฐานสำคัญสำหรับ Part ถัดไป **Part 074: สร้างแคมเปญ Lead Generation บน TikTok** ซึ่งจะซับซ้อนขึ้นอีกขั้น เพราะต้องเรียนรู้ TikTok Instant Form Builder ทั้งหน้า Intro, คำถาม, Privacy Policy และหน้า Ending รวมถึงการออกแบบคำถามให้เหมาะกับพฤติกรรมผู้ใช้ TikTok ที่สไลด์เร็วและมีแนวโน้มกดฟอร์มแบบหุนหันพลันแล่นมากกว่า Facebook — เป็นความท้าทายใหม่ที่ต้องเข้าใจก่อนลงมือสร้างจริง

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- TikTok Ads Manager Help Center — Campaign Creation Guide (business-api.tiktok.com/portal และ ads.tiktok.com/help)
- TikTok For Business — Objective & Optimization Goal Documentation
- TikTok Creative Center — Trend/Template Library (ads.tiktok.com/business/creativecenter)
- เอกสารภายในหลักสูตร: Part 021 (แคมเปญแรก Facebook), Part 067 (โครงสร้างแคมเปญ TikTok), Part 068 (Objective TikTok ทั้งหมด), Part 069 (Budget/Bidding TikTok), Part 070 (Placement TikTok)
- บันทึก Benchmark CPM/CTR ของบัญชีตัวเอง — สร้างเป็น Google Sheet ส่วนตัวเก็บข้อมูลทุกแคมเปญเพื่อใช้เทียบในอนาคต (ตัวเลข Benchmark ในตลาดเปลี่ยนเร็ว การมีข้อมูลของตัวเองสำคัญกว่าตัวเลขทั่วไปในบทความออนไลน์)
