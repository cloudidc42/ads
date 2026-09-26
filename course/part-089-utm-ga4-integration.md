# Part 089: UTM Tracking และ Google Analytics 4 Integration

**Section:** J — Cross-Platform Analytics, Tracking & Automation (Part 089–093, Step 881–930) — **Part เปิด Section J**
**Step ที่ครอบคลุม:** 881–890 (จาก 1000 Steps ทั้งหมด)
**เวลาเรียนโดยประมาณ:** 12–14 ชั่วโมง (อ่าน+ทำความเข้าใจ 5 ชม. / ตั้งค่า GA4 และทดสอบ UTM จริง 7–9 ชม.)

---

## ทำไม Part นี้สำคัญ

ตั้งแต่ Section B ถึง Section I คุณเรียน Facebook Ads และ TikTok Ads แยกกันเป็นสองระบบ — สองแพลตฟอร์ม สอง Ads Manager สอง Pixel สอง Dashboard เมื่อทำงานจริงกับธุรกิจที่ยิงทั้งสองแพลตฟอร์มพร้อมกัน (ซึ่งเป็นเรื่องปกติมากขึ้นทุกปี) คำถามที่เจ้าของธุรกิจถามคุณทุกครั้งคือ **"แพลตฟอร์มไหนคุ้มกว่ากัน"** และ **"งบที่เพิ่มจาก TikTok ไปกระทบยอดขายรวมแค่ไหน"** — คำถามแบบนี้ตอบไม่ได้ถ้าข้อมูลอยู่คนละที่ วัดคนละแบบ ชื่อแคมเปญไม่มีมาตรฐาน

Section J คือจุดที่หลักสูตรนี้ "รวม" สองแพลตฟอร์มเข้าด้วยกันในมุมของการวัดผล ไม่ใช่รวมกลยุทธ์การยิงแอด (ซึ่งยังคงต่างกันตามที่เรียนมา) แต่รวม**ระบบ Tracking** ให้ข้อมูลจาก Facebook และ TikTok ไหลเข้าสู่จุดกลางเดียวกัน — Google Analytics 4 — ด้วยโครงสร้างที่เทียบเคียงกันได้ (Comparable) นี่คือทักษะที่แยกนักยิงแอดระดับกลางออกจากนักยิงแอดระดับโลก เพราะคนที่ตอบคำถาม Cross-Platform ได้อย่างมีข้อมูลรองรับ คือคนที่ลูกค้าไว้ใจให้ดูแลงบก้อนใหญ่ขึ้นเรื่อยๆ

Part นี้เริ่มจากพื้นฐานที่สุด — UTM Parameters — แล้วไต่ระดับไปถึงการสร้าง Taxonomy ที่ใช้งานได้จริงในทีม และการตั้งค่า GA4 ให้รับข้อมูลจากทั้งสองแพลตฟอร์มอย่างถูกต้อง ทุก Step มีตัวอย่าง Syntax UTM และการ Mapping Event จริงที่คุณคัดลอกไปใช้ได้ทันที

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 881 — UTM Parameters พื้นฐาน: โครงสร้าง 5 พารามิเตอร์** ความหมายของ source, medium, campaign, content, term และกฎการเขียนที่ถูกต้อง
2. **Step 882 — Naming Convention มาตรฐานสำหรับ UTM ข้าม Facebook และ TikTok** โครงสร้างชื่อที่ทำให้สองแพลตฟอร์มเทียบกันได้ใน 1 ตาราง
3. **Step 883 — Meta Dynamic UTM Parameters** ใช้ {{campaign.name}}, {{adset.name}}, {{ad.name}} ให้ Facebook เติม UTM อัตโนมัติแบบไม่พลาด
4. **Step 884 — TikTok URL Parameters เทียบเท่า Dynamic UTM** __CID__, __AID__, __CAMPAIGN_NAME__ และการตั้งค่า Tracking URL บน TikTok
5. **Step 885 — ตั้งค่า GA4 Property และ Data Streams ให้พร้อมรับทั้งสองแพลตฟอร์ม** โครงสร้าง Property, Stream, การตั้งค่าเบื้องต้นที่มักลืม
6. **Step 886 — GA4 Events vs Facebook/TikTok Pixel Events: ตาราง Mapping ฉบับสมบูรณ์** แปลง Standard Event ให้กลายเป็นภาษาเดียวกันใน GA4
7. **Step 887 — สร้าง Unified UTM Taxonomy ให้เทียบเคียงกันได้ข้าม Platform ใน GA4** วิธีให้ GA4 มองเห็น Facebook และ TikTok เป็นแถวเดียวกันในตารางเดียว
8. **Step 888 — GA4 Explorations สำหรับเปรียบเทียบ Cross-Channel** Funnel Exploration, Free-form Exploration ที่ตอบคำถาม "แพลตฟอร์มไหนคุ้มกว่า"
9. **Step 889 — ข้อผิดพลาด UTM ที่พบบ่อยและวิธีป้องกัน** ตัวพิมพ์เล็กใหญ่ไม่ตรงกัน, พารามิเตอร์หาย, Encoding ผิด
10. **Step 890 — Workshop: สร้างเอกสาร UTM Naming Convention ฉบับสมบูรณ์และทดสอบข้ามสองแพลตฟอร์มจริง**

---

## Step 881: UTM Parameters พื้นฐาน — โครงสร้าง 5 พารามิเตอร์

### UTM คืออะไรและทำไมยังสำคัญในปี 2026

UTM (Urchin Tracking Module) คือชุดพารามิเตอร์ที่ต่อท้าย URL เพื่อบอก Analytics Platform ว่า Traffic ที่เข้ามาชิ้นนี้มาจากไหน ผ่านช่องทางอะไร แคมเปญอะไร แม้ในยุคที่ Pixel และ Conversions API ทำงานเบื้องหลังได้ดีขึ้นมาก UTM ยังจำเป็นเพราะ **Pixel บอกได้ว่า "มีคน Convert" แต่ UTM บอกได้ว่า "คนนั้นมาจาก Traffic เส้นทางไหนกันแน่"** — สองอย่างนี้ตอบคำถามคนละแบบ และ GA4 ใช้ UTM เป็นแกนหลักในการจัดกลุ่ม Traffic (Session Source/Medium) ซึ่งเป็นสิ่งที่ Pixel ของแต่ละแพลตฟอร์มไม่ได้ให้มาตรงๆ

### 5 พารามิเตอร์หลักและความหมาย

| พารามิเตอร์ | ชื่อเต็ม | ความหมาย | ตัวอย่างค่า |
|---|---|---|---|
| `utm_source` | Campaign Source | แหล่งที่มาของ Traffic (แพลตฟอร์ม) | `facebook`, `tiktok` |
| `utm_medium` | Campaign Medium | ประเภทช่องทาง/รูปแบบการเข้าถึง | `paid_social`, `cpc` |
| `utm_campaign` | Campaign Name | ชื่อแคมเปญ | `sale-9924-newcust` |
| `utm_content` | Campaign Content | แยกความแตกต่างของ Creative/Ad ภายในแคมเปญเดียวกัน | `carousel-v1`, `ugc-review-03` |
| `utm_term` | Campaign Term | ใช้แยก Audience/Keyword (สำหรับ Search มากกว่า แต่ปรับใช้กับ Social ได้) | `lookalike-1pct`, `interest-fitness` |

### กฎการเขียนที่ต้องยึดเป็นมาตรฐาน

1. **ตัวพิมพ์เล็กทั้งหมด (lowercase) เสมอ** — GA4 มองค่า `Facebook` และ `facebook` เป็นคนละค่ากัน ทำให้ Report แตกเป็นสองแถว
2. **ใช้ Hyphen (-) แทน Space** — ห้ามเว้นวรรคใน URL เพราะจะถูก Encode เป็น `%20` ทำให้อ่านยากใน Report
3. **ห้ามใช้ Underscore ปนกับ Hyphen แบบสุ่ม** — เลือกอย่างใดอย่างหนึ่งเป็นมาตรฐานทีมแล้วใช้ตลอด (แนะนำ Hyphen เพราะ Google เองใช้ Hyphen ใน Best Practice)
4. **ห้ามใช้ตัวอักษรไทยใน UTM** — เพราะเมื่อ Encode แล้วจะยาวและอ่านไม่ออกใน Report ให้ใช้ทับศัพท์อังกฤษ (Transliteration) แทน
5. **ทุก Link โฆษณาต้องมีอย่างน้อย source, medium, campaign** — content และ term เป็น Optional แต่แนะนำให้ใส่เสมอเพื่อ Creative-level Analysis

### ตัวอย่าง URL ที่ประกอบ UTM ครบ

```
https://www.mybrand.com/landing/sale-sept?utm_source=facebook&utm_medium=paid_social&utm_campaign=sale-9924-newcust&utm_content=carousel-v1&utm_term=lookalike-1pct
```

### ข้อผิดพลาดที่พบบ่อยใน Step นี้

- ใส่ UTM เฉพาะ `utm_source` และ `utm_campaign` โดยลืม `utm_medium` — ทำให้ GA4 จัดกลุ่ม Traffic เป็น "(not set)" หรือจัดผิดกลุ่มเป็น Organic
- Copy URL จากแคมเปญเก่ามาใช้ซ้ำโดยไม่แก้ `utm_campaign` — ทำให้ข้อมูลแคมเปญใหม่ไปปนกับแคมเปญเก่าใน Report
- ใส่ UTM ซ้ำสองชุดในลิงก์เดียว (มักเกิดจาก Copy-paste ผิด) ทำให้ URL พังและ Redirect ไม่ทำงาน

### ตาราง "ผิด vs ถูก" ที่ใช้สอนทีมใหม่ได้ทันที

| กรณี | ตัวอย่างที่ผิด | ตัวอย่างที่ถูก | สาเหตุที่ต้องแก้ |
|---|---|---|---|
| ตัวพิมพ์ | `utm_source=Facebook` | `utm_source=facebook` | GA4 case-sensitive แยกเป็นสองแถว |
| เว้นวรรค | `utm_campaign=sale sept` | `utm_campaign=sale-sept` | เว้นวรรคถูก Encode เป็น `%20` อ่านยาก |
| ภาษาไทย | `utm_content=โพสต์รีวิว` | `utm_content=ugc-review-03` | Encode ยาว วิเคราะห์ยาก คัดลอกผิดง่าย |
| Parameter ซ้ำ | `?utm_source=fb&utm_source=facebook` | `?utm_source=facebook` | ระบบอาจอ่านค่าตัวแรกหรือตัวหลังไม่ตรงกันในแต่ละเบราว์เซอร์ |
| ลืม medium | `?utm_source=tiktok&utm_campaign=promo` | `?utm_source=tiktok&utm_medium=paid_social&utm_campaign=promo` | ไม่มี medium ทำให้ Channel Group จัดผิดหมวด |

### ทำความเข้าใจ URL Encoding ให้ลึกขึ้นอีกนิด

เมื่อ Browser ส่ง URL ที่มีอักขระพิเศษ (เว้นวรรค, ภาษาไทย, เครื่องหมาย `&` `?` `#` ที่ไม่ได้ตั้งใจใช้เป็น Parameter Separator) ระบบจะแปลงเป็นรหัส Percent-Encoding โดยอัตโนมัติ เช่น เว้นวรรคกลายเป็น `%20` และภาษาไทยกลายเป็นชุดรหัส `%E0%B8...` ที่ยาวมาก ปัญหาคือ URL ที่ยาวและอ่านไม่ออกแบบนี้เมื่อไปโผล่ใน Report ของ GA4 จะทำให้ทีม Marketing อ่านและจดจำไม่ได้ว่าแคมเปญไหนคือแคมเปญไหน จึงต้องยึดกฎ "ใช้ตัวอักษรอังกฤษ ตัวเลข และ Hyphen เท่านั้น" อย่างเคร่งครัดใน UTM ทุกตัว

---

## Step 882: Naming Convention มาตรฐานสำหรับ UTM ข้าม Facebook และ TikTok

### ปัญหาที่ Naming Convention แก้

ถ้าทีม Facebook ตั้งชื่อแคมเปญว่า `FB_Sale_Sept24` และทีม TikTok ตั้งว่า `tiktok-promotion-sep` — พอทั้งสองชื่อนี้กลายเป็นค่าใน `utm_campaign` มันจะเป็นคนละแถวใน GA4 ทันที เทียบกันไม่ได้เลยแม้จะเป็นแคมเปญโปรโมชั่นเดียวกัน การแก้คือสร้าง **Naming Convention ระดับ Taxonomy** ที่บังคับให้ทุกแพลตฟอร์มเขียนชื่อในโครงสร้างเดียวกัน

### โครงสร้าง Taxonomy ที่แนะนำ

```
utm_campaign = {platform}-{objective}-{promo-code}-{audience-type}-{yymm}
```

ตัวอย่าง:

| แพลตฟอร์ม | ค่า utm_campaign |
|---|---|
| Facebook | `fb-conv-sale0924-newcust-2409` |
| TikTok | `tt-conv-sale0924-newcust-2409` |

สังเกตว่าโครงสร้างเหมือนกันทุกส่วน ต่างเพียง Prefix แพลตฟอร์ม (`fb` / `tt`) ทำให้ตอนวิเคราะห์ใน GA4 สามารถ Filter หรือ Group ด้วย Regex เพื่อดึงแคมเปญ `sale0924-newcust` จากทั้งสองแพลตฟอร์มมาเทียบกันได้ทันที

### ตาราง Field Dictionary ที่ต้องทำเป็นเอกสารทีม

| Field | ค่าที่อนุญาต | ตัวอย่าง |
|---|---|---|
| platform | `fb`, `tt` | — |
| objective | `conv` (conversion), `lead`, `traffic`, `aware`, `eng` (engagement) | — |
| promo-code | รหัสโปรโมชั่นภายใน ตกลงกับทีม Content/Sales | `sale0924`, `bday5yr` |
| audience-type | `newcust` (new customer), `retgt` (retargeting), `lal` (lookalike), `bday` (broad) | — |
| yymm | ปี-เดือนแบบ 4 หลัก | `2409` = กันยายน 2024 |

### utm_medium มาตรฐานสำหรับ Paid Social

ใช้ค่าเดียวกันสำหรับทั้งสองแพลตฟอร์มเสมอ: `utm_medium=paid_social` — ห้ามใช้ `cpc` เพราะ `cpc` ใน GA4 จะถูกดึงไปจัดกลุ่ม Channel เป็น "Paid Search" โดยอัตโนมัติ ทำให้ Traffic จาก Social ไปปนกับ Google Ads ผิดหมวด

### utm_content สำหรับแยกระดับ Creative

```
utm_content = {ad-format}-{creative-id}-{version}
```

ตัวอย่าง: `carousel-ugc03-v2`, `spark-video01-v1`

### ตารางสรุป Taxonomy แบบเต็มพร้อมตัวอย่างใช้งานจริง

| ระดับ | Facebook | TikTok |
|---|---|---|
| utm_source | `facebook` | `tiktok` |
| utm_medium | `paid_social` | `paid_social` |
| utm_campaign | `fb-conv-sale0924-newcust-2409` | `tt-conv-sale0924-newcust-2409` |
| utm_content | `carousel-ugc03-v2` | `spark-video01-v1` |
| utm_term | `lal-1pct` | `interest-beauty` |

### ข้อผิดพลาดที่พบบ่อย

- ปล่อยให้แต่ละคนในทีมตั้งชื่อ UTM ตามความสะดวกของตัวเองโดยไม่มีเอกสารกลาง ทำให้ภายใน 2-3 เดือนข้อมูลกระจัดกระจายจนวิเคราะห์ไม่ได้
- ใส่ข้อมูลที่เปลี่ยนบ่อยเกินไปใน utm_campaign (เช่น วันที่แบบละเอียดวันต่อวัน) ทำให้ Report แตกเป็นแคมเปญละเอียดจนไม่มีประโยชน์
- ไม่มี Prefix แพลตฟอร์มที่ Consistent ทำให้ Filter/Regex ทำไม่ได้ในระยะยาว

### Governance: ใครควรเป็นเจ้าภาพดูแล Taxonomy

Naming Convention ที่ดีจะพังภายในไม่กี่เดือนถ้าไม่มีเจ้าภาพชัดเจน แนะนำให้กำหนดบทบาทดังนี้:

| บทบาท | หน้าที่ |
|---|---|
| **Tracking Owner** (มักเป็น Media Buyer อาวุโสหรือ Analytics Lead) | ดูแลเอกสาร Master Convention, อนุมัติ Field ใหม่ที่ขอเพิ่ม, ตรวจสอบ Compliance รายเดือน |
| **Media Buyer ทุกคน** | ตั้งชื่อ Campaign/Ad Set/Ad ตาม Convention ทุกครั้งก่อน Publish |
| **Freelance/Agency ภายนอก** | ต้องได้รับเอกสาร Convention ก่อนเริ่มงานวันแรก และถูกตรวจ QA อย่างน้อยสัปดาห์แรกที่เริ่มทำงาน |

### เวอร์ชันของเอกสาร Convention

เมื่อ Business เติบโต Field ใน Taxonomy อาจต้องเพิ่ม (เช่น เพิ่ม Field ประเทศสำหรับธุรกิจที่ขยายไปหลายตลาด) ควรทำ Version Control ของเอกสารนี้แบบง่ายๆ เช่น ใส่ "Version 2.1 — Updated 2026-03" ที่หัวเอกสาร และเก็บ Version เก่าไว้อ้างอิงเสมอ เพื่อให้ทีมที่วิเคราะห์ข้อมูลย้อนหลังเข้าใจว่าทำไมแคมเปญเก่ากับใหม่มีจำนวน Field ต่างกัน

---

## Step 883: Meta Dynamic UTM Parameters

### ทำไมต้องใช้ Dynamic Parameters แทนการพิมพ์มือ

การพิมพ์ UTM ด้วยมือทุกครั้งที่สร้างโฆษณามีความเสี่ยงสูงที่จะพิมพ์ผิด สลับตัวอักษร หรือลืมอัปเดตตามชื่อแคมเปญจริง Meta จึงมี Dynamic UTM Parameters ที่ให้ระบบดึงชื่อ Campaign/Ad Set/Ad จริงมาเติมใน URL อัตโนมัติ ลดความผิดพลาดของมนุษย์ลงเกือบทั้งหมด

### ตำแหน่งตั้งค่าใน Ads Manager

ตั้งค่าที่ **Ad Level > Destination > Build a URL parameter** หรือกรอกตรงในช่อง Website URL parameters ท้าย URL หลัก

### ตาราง Dynamic Parameters ที่ใช้บ่อยที่สุด

| Placeholder | ดึงค่าจาก | ตัวอย่างผลลัพธ์ |
|---|---|---|
| `{{campaign.name}}` | ชื่อ Campaign | `fb-conv-sale0924-newcust-2409` |
| `{{campaign.id}}` | Campaign ID (ตัวเลข) | `120211xxxxxxxxx` |
| `{{adset.name}}` | ชื่อ Ad Set | `lal-1pct-25-45` |
| `{{adset.id}}` | Ad Set ID | `120211xxxxxxxxx` |
| `{{ad.name}}` | ชื่อ Ad | `carousel-ugc03-v2` |
| `{{ad.id}}` | Ad ID | `120211xxxxxxxxx` |
| `{{placement}}` | ตำแหน่งที่แสดง (feed, reels, stories) | `an_classic` |
| `{{site_source_name}}` | แพลตฟอร์มย่อย | `fb`, `ig`, `msg` |

### ตัวอย่างการตั้งค่าใน Ads Manager

```
utm_source=facebook&utm_medium=paid_social&utm_campaign={{campaign.name}}&utm_content={{ad.name}}&utm_term={{adset.name}}
```

ข้อดีสำคัญของวิธีนี้คือ **ถ้าตั้งชื่อ Campaign/Ad Set/Ad ตาม Naming Convention ใน Step 882 อย่างเคร่งครัด UTM จะถูกต้องอัตโนมัติทุกครั้งโดยไม่ต้องพิมพ์ซ้ำ** — นี่คือเหตุผลที่ Step 882 ต้องทำก่อน Step นี้เสมอ ชื่อแคมเปญที่ตั้งใน Ads Manager และ UTM คือสิ่งเดียวกัน

### การตั้งค่าระดับ Default ที่ Ad Account เพื่อไม่ต้องพิมพ์ทุกครั้ง

Meta อนุญาตให้ตั้ง URL Parameters เป็น Template ระดับ Ad Account ผ่าน **Ads Manager > Settings > Tracking Domains and URL Parameters** เมื่อสร้างแคมเปญใหม่ทุกครั้ง Parameter Template นี้จะถูกดึงมาใส่อัตโนมัติ ลดงานซ้ำสำหรับทีมที่สร้างแคมเปญจำนวนมาก

### ข้อผิดพลาดที่พบบ่อย

- ใส่ Placeholder ผิด Syntax (เช่น ลืมวงเล็บปีกกาคู่ `{{ }}`) ทำให้ระบบไม่แทนค่าและ UTM กลายเป็นข้อความ Literal `{{campaign.name}}` ตรงๆใน Report
- ใช้ `{{campaign.name}}` แต่ชื่อ Campaign มีตัวอักษรพิเศษหรือภาษาไทยปน ทำให้ URL Encode ยาวและอ่านยากใน GA4
- ลืมทดสอบ URL จริงก่อนเปิดใช้งาน (ควรกด "Preview" ใน Ads Manager เพื่อดู URL ที่ Render จริงก่อน Publish เสมอ)

### Troubleshooting: เมื่อ Dynamic Parameter ไม่ทำงานตามที่ควร

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---|---|---|
| UTM ใน Report โชว์เป็น `{{campaign.name}}` ตรงๆ | พิมพ์ Syntax ผิด หรือ Meta ยังไม่ Support Macro นั้นใน Placement ที่ใช้ | ตรวจสอบรายชื่อ Macro ที่รองรับล่าสุดใน Meta Business Help Center และทดสอบ Preview |
| utm_campaign มีค่าแต่เป็น ID ตัวเลขไม่ใช่ชื่อ | ใช้ `{{campaign.id}}` ผิดที่ควรใช้ `{{campaign.name}}` | สลับ Macro ให้ตรงกับที่ต้องการ |
| Auto-tagging ของ Meta (ถ้าเปิดใช้) ไปทับ UTM ที่ตั้งเอง | Meta บางบัญชีมีการเติม Parameter อัตโนมัติเพิ่มเติมนอกจากที่ตั้งไว้ | ตรวจสอบ URL ที่ Render จริงเทียบกับที่ตั้งไว้ ปิด Auto-tagging ถ้าไม่ต้องการให้ระบบเติมเพิ่ม |
| UTM หายไปหลัง Redirect ผ่าน Bit.ly หรือ Shortlink อื่น | บริการ Shortlink บางตัวไม่ Pass Query String ต่อ | เลือกบริการ Shortlink ที่ยืนยันว่า Pass Parameter ได้ หรือ Encode URL ปลายทางทั้งหมดเป็นค่าเดียวก่อนย่อ |

---

## Step 884: TikTok URL Parameters เทียบเท่า Dynamic UTM

### TikTok ใช้ระบบ Macro/Placeholder คนละชุดกับ Meta

TikTok Ads Manager ไม่ได้ใช้ Syntax `{{ }}` แบบ Meta แต่ใช้ Macro รูปแบบ `__PLACEHOLDER__` (ขีดเส้นใต้สองข้าง) แทน ตั้งค่าที่ **Ad Level > Tracking > URL Parameters (Optional)** ในหน้าสร้าง/แก้ไข Ad

### ตาราง TikTok Macro ที่ใช้บ่อยที่สุด

| Macro | ดึงค่าจาก | เทียบเท่า Meta |
|---|---|---|
| `__CAMPAIGN_ID__` | Campaign ID | `{{campaign.id}}` |
| `__CAMPAIGN_NAME__` | ชื่อ Campaign | `{{campaign.name}}` |
| `__CID__` | Ad Group ID (ตัวย่อ) | `{{adset.id}}` |
| `__AID__` | Ad ID | `{{ad.id}}` |
| `__PLACEMENT__` | ตำแหน่งแสดงผล | `{{placement}}` |
| `__AD_UNIT_ID__` | ID ของหน่วยโฆษณา | — |
| `__REGION__` | ภูมิภาคที่แสดงผล | — |

### ตัวอย่างการตั้งค่า TikTok URL Parameters

```
utm_source=tiktok&utm_medium=paid_social&utm_campaign=__CAMPAIGN_NAME__&utm_content=__AID__&utm_term=__CID__
```

### ความต่างสำคัญที่ต้องรู้: TikTok ไม่รองรับ Ad Group Name เป็น Macro ตรงๆในบางเวอร์ชัน

ณ ช่วงที่เขียนหลักสูตรนี้ TikTok มี Macro สำหรับ **ID** ของ Campaign/Ad Group/Ad ครบ แต่ Macro สำหรับ **Name** ของ Ad Group (เทียบเท่า `{{adset.name}}` ของ Meta) ยังไม่รองรับในทุก Ad Type — วิธีแก้ทางปฏิบัติคือใช้ `__CID__` (ID) แทน แล้วทำตาราง Mapping ID → Name เก็บไว้แยก หรือใส่ชื่อ Ad Group ในส่วน `utm_content`/`utm_term` แบบ Static (พิมพ์มือ) ตาม Naming Convention เพื่อให้อ่านง่ายใน Report โดยไม่พึ่ง Macro

### เทคนิคผสม Static + Dynamic สำหรับ TikTok

```
utm_campaign=tt-conv-sale0924-newcust-2409&utm_content=spark-video01-v1-__AID__
```

วิธีนี้ทำให้ `utm_content` อ่านง่าย (มนุษย์เข้าใจ) และยังมี AID ต่อท้ายเพื่อ Join กับข้อมูลใน TikTok Ads Manager ได้แบบ Unique เมื่อจำเป็นต้องเจาะลึกถึงระดับ Ad

### ตรวจสอบ Macro ให้ทำงานถูกต้องก่อนเปิดใช้จริง

TikTok Ads Manager มีปุ่ม **Preview URL** ในหน้าตั้งค่า Tracking ให้กดตรวจทุกครั้งก่อน Publish เพื่อดูว่า Macro ถูกแทนค่าเป็นตัวเลข/ข้อความจริงถูกต้อง ไม่ใช่ค่า Literal ของ Macro เอง

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Syntax `{{ }}` แบบ Meta ผิดแพลตฟอร์มมาใส่ใน TikTok (ทั้งสองระบบไม่ใช้ Syntax เดียวกัน) ทำให้ Macro ไม่ทำงานเลย
- ลืมว่า TikTok Macro บางตัวคืนค่าเป็น ID ตัวเลขไม่ใช่ชื่อ ทำให้ Report อ่านยากถ้าไม่มีตาราง Mapping
- ตั้งค่า Parameter ที่ Campaign Level แล้วคิดว่าจะ Apply ไปทุก Ad Group/Ad อัตโนมัติ — ในบางกรณีต้องตั้งซ้ำที่ Ad Level ด้วย ควรตรวจทุกชั้นเสมอ

### TikTok Smart+ และแคมเปญ Automated ที่ลดการควบคุม Manual UTM

แคมเปญประเภท Smart+ หรือแคมเปญที่เปิด Automated Creative Optimization เต็มรูปแบบ อาจไม่เปิดให้ตั้งค่า URL Parameters ในระดับ Ad ได้ละเอียดเท่าแคมเปญ Manual ทั่วไป สำหรับกรณีนี้ให้ตั้งค่า Parameter ที่ระดับสูงสุดที่ระบบอนุญาต (มักเป็น Campaign หรือ Ad Group Level) และยอมรับว่า `utm_content` ระดับ Creative รายตัวอาจไม่ละเอียดเท่าที่ต้องการ — ใช้ TikTok Ads Manager เองในการดู Performance ระดับ Creative แทน แล้วใช้ GA4 เพื่อดูภาพรวมระดับ Campaign เป็นหลัก

### สร้างตาราง Mapping ID ↔ Name เก็บไว้ใช้งานจริง

เนื่องจาก TikTok มักคืนค่าเป็น ID มากกว่าชื่อใน Macro บางตัว แนะนำให้สร้างตารางอ้างอิงแบบนี้เก็บไว้ใน Google Sheet ของทีม อัปเดตทุกครั้งที่สร้าง Ad Group ใหม่:

| Ad Group ID (CID) | ชื่อ Ad Group จริง | Audience Type | วันที่สร้าง |
|---|---|---|---|
| 1769xxxxxxxx01 | lal-1pct-25-45 | Lookalike | 2026-02-01 |
| 1769xxxxxxxx02 | interest-beauty-18-34 | Interest | 2026-02-03 |

ตารางนี้ทำให้เมื่อเปิด GA4 Report แล้วเห็นเลข CID ใน `utm_term` สามารถ Join กลับมาดูชื่อที่มนุษย์อ่านเข้าใจได้ทันทีโดยไม่ต้องสลับหน้าไปเปิด TikTok Ads Manager

---

## Step 885: ตั้งค่า GA4 Property และ Data Streams ให้พร้อมรับทั้งสองแพลตฟอร์ม

### โครงสร้าง GA4 ที่ต้องเข้าใจก่อนตั้งค่า

```
Google Analytics Account
   └── Property (1 ธุรกิจ = 1 Property ปกติ)
         └── Data Stream (Web / iOS App / Android App)
               └── Events (เก็บ Interaction ทุกประเภท)
```

สำหรับธุรกิจที่ยิงทั้ง Facebook และ TikTok ไปที่เว็บไซต์เดียวกัน **ใช้ Property เดียวและ Data Stream (Web) เดียว** — ไม่ต้องแยก Property ตามแพลตฟอร์มโฆษณา เพราะเป้าหมายคือให้ GA4 เห็น Traffic ทั้งหมดในที่เดียวแล้วแยกด้วย Session Source/Medium ที่มาจาก UTM แทน

### ขั้นตอนตั้งค่า Property ใหม่

1. เข้า **Google Analytics > Admin > Create Property**
2. ตั้งชื่อ Property ตามชื่อธุรกิจ เลือก Timezone และ Currency ให้ตรงกับประเทศที่ขายจริง (สำคัญมากสำหรับการคำนวณ Revenue ให้ตรงกับ Ads Manager)
3. กรอกข้อมูล Business ตามที่ระบบถาม (Industry, Business Size)
4. สร้าง **Data Stream > Web** กรอก URL เว็บไซต์หลัก
5. ระบบจะให้ **Measurement ID** (รูปแบบ `G-XXXXXXXXXX`) และ Global Site Tag (gtag.js) ให้นำไปติดตั้งผ่าน GTM (ทวน Part 014 เรื่องการติดตั้งผ่าน Google Tag Manager)

### การตั้งค่าที่มักถูกลืมแต่สำคัญมาก

| การตั้งค่า | ทำไมสำคัญ |
|---|---|
| **Enhanced Measurement** | เปิดให้ GA4 เก็บ Scroll, Outbound Click, Site Search อัตโนมัติโดยไม่ต้องเขียนโค้ดเอง |
| **Google Signals** | เปิดเพื่อได้ข้อมูล Demographics/Interest และ Cross-device Reporting (ต้องสอดคล้องกับ Consent/PDPA) |
| **Data Retention** | ตั้งเป็น 14 เดือน (ค่าสูงสุดที่ GA4 อนุญาตในระดับ Standard) ไม่ใช่ค่า Default 2 เดือน |
| **Internal Traffic Filter** | Filter IP ของทีมงาน/Office ออก ไม่ให้ปนกับข้อมูลลูกค้าจริง |
| **Cross-domain Measurement** | ถ้า Checkout อยู่คนละ Domain (เช่น Landing Page กับ Shopify Checkout) ต้องตั้งค่านี้ไม่ให้ Session ขาดตอน |

### ตั้งค่า Conversion Events ใน GA4

หลังติดตั้ง Data Stream แล้ว ต้องไปที่ **Admin > Events** เพื่อ Mark Event สำคัญเป็น **Key Event** (ชื่อเดิมคือ Conversion) เช่น `purchase`, `generate_lead`, `sign_up` — Key Event เท่านั้นที่จะถูกดึงไปคำนวณใน Report สรุประดับสูงและ Attribution Model

### ข้อผิดพลาดที่พบบ่อย

- สร้าง Property ใหม่หลายอันสำหรับแต่ละแคมเปญ/แพลตฟอร์ม ทำให้ข้อมูลกระจายและ Cross-Platform Analysis ทำไม่ได้เลย
- ไม่ตั้ง Currency ให้ตรงกับสกุลเงินที่ขายจริง ทำให้ Revenue ใน GA4 คลาดเคลื่อนจาก Ads Manager
- ปล่อย Data Retention ไว้ที่ค่า Default 2 เดือน ทำให้ Explorations แบบ Cohort/Lifetime Value ย้อนดูได้ไม่ไกลพอ

### โครงสร้าง Property สำหรับธุรกิจที่มีหลายเว็บไซต์/แอป

ถ้าธุรกิจมีทั้งเว็บไซต์หลักและแอปมือถือ ให้ใช้ Property เดียวแต่เพิ่ม Data Stream สองอัน (Web + App) ภายใต้ Property เดิม เพราะ GA4 ถูกออกแบบมาให้รวม Web และ App เข้าด้วยกันได้ในโครงสร้างเดียว (ต่างจาก Universal Analytics รุ่นเก่าที่ต้องแยก) วิธีนี้ทำให้เห็น Customer Journey ที่ข้ามจาก Facebook Ad → เปิดเว็บ → โหลดแอป → ซื้อในแอป ได้ในรายงานเดียวกันผ่าน User-ID หรือ Google Signals

### การเชื่อม GA4 กับ Google Ads, Search Console และ BigQuery

แม้ Part นี้โฟกัสที่ Facebook และ TikTok แต่การเชื่อม GA4 กับเครื่องมืออื่นตั้งแต่ต้นจะเป็นประโยชน์มากเมื่อธุรกิจโตขึ้น:

| การเชื่อมต่อ | ประโยชน์ |
|---|---|
| **BigQuery Export** | Export Raw Event Data ทุกตัวไป BigQuery แบบไม่มีการ Sampling ใช้ทำ Custom Analysis ที่ Explorations ทำไม่ได้ (ต่อเนื่องกับ Part 090-091) |
| **Google Ads Link** | ถ้ามียิง Google Ads ด้วย จะเห็นครบทั้ง 3 แพลตฟอร์มโฆษณาในที่เดียว |
| **Search Console Link** | เทียบ Organic Search กับ Paid Social เพื่อดู Baseline ที่ไม่ต้องจ่ายเงิน |

การเปิด BigQuery Export ควรทำตั้งแต่วันที่สร้าง Property เพราะ Export จะเก็บข้อมูลย้อนหลังไม่ได้ (เก็บได้ตั้งแต่วันที่เปิดใช้งานเป็นต้นไปเท่านั้น) — ธุรกิจที่วางแผนทำ Dashboard ระดับสูงใน Part 091 ควรเปิดฟีเจอร์นี้ไว้ล่วงหน้าแม้จะยังไม่ได้ใช้ทันที

---

## Step 886: GA4 Events vs Facebook/TikTok Pixel Events — ตาราง Mapping ฉบับสมบูรณ์

### ทำไมชื่อ Event ต้องตรงกันข้ามระบบ

Facebook Pixel เรียก Event มาตรฐานด้วยชื่อของตัวเอง (เช่น `Purchase`) TikTok Pixel เรียกอีกแบบ (เช่น `CompletePayment`) และ GA4 มีชื่อ Recommended Event ของตัวเอง (เช่น `purchase`) — ถ้าไม่ทำ Mapping ให้ชัดเจน ทีมจะสับสนว่า Event ไหนคือ Event ไหนเมื่อเทียบ Report ข้ามระบบ และที่สำคัญกว่านั้น **การส่ง Event เดียวกันไปหลายปลายทางด้วยชื่อคนละชื่อ ทำให้ Debug ยากขึ้นมากเมื่อเกิดปัญหา**

### ตาราง Mapping สมบูรณ์: Facebook × TikTok × GA4

| ความหมาย Event | Facebook Pixel (Standard Event) | TikTok Pixel (Standard Event) | GA4 (Recommended Event) |
|---|---|---|---|
| ดูหน้าสินค้า | `ViewContent` | `ViewContent` | `view_item` |
| เพิ่มลงตะกร้า | `AddToCart` | `AddToCart` | `add_to_cart` |
| เริ่ม Checkout | `InitiateCheckout` | `InitiateCheckout` | `begin_checkout` |
| เพิ่มข้อมูลการจ่ายเงิน | `AddPaymentInfo` | `AddPaymentInfo` | `add_payment_info` |
| ซื้อสำเร็จ | `Purchase` | `CompletePayment` | `purchase` |
| ลงทะเบียน/สมัครสมาชิก | `CompleteRegistration` | `CompleteRegistration` | `sign_up` |
| ส่งฟอร์ม Lead | `Lead` | `SubmitForm` | `generate_lead` |
| ค้นหาในเว็บ | `Search` | `Search` | `search` |
| เริ่มทดลองใช้ | `StartTrial` | `Subscribe` (ใกล้เคียง) | `begin_trial` (Custom) |
| แชร์เนื้อหา | `Share` (Custom ส่วนใหญ่) | `Share` (Custom) | `share` |

### หลักการตั้งชื่อ Custom Event ให้ Consistent

เมื่อ Event ไม่มีในรายการ Standard ของทั้งสามระบบ ให้ตั้งชื่อ Custom Event ด้วยหลักการเดียวกันทั้งหมด: **ใช้ snake_case (ตัวพิมพ์เล็ก คั่นด้วย Underscore) และใช้คำกริยา + คำนาม** เช่น `download_catalog`, `book_consultation`, `chat_started` — ยึดชื่อ GA4-style เป็นมาตรฐานกลาง แล้ว Map Facebook Custom Conversion และ TikTok Custom Event ให้ชี้กลับมาที่ชื่อเดียวกันในเชิงความหมาย

### ตัวอย่าง Data Layer Push ที่ส่ง Event เดียวกันไปทั้ง 3 ปลายทางพร้อมกัน (ผ่าน GTM)

```javascript
// Data Layer Event มาตรฐานเดียว — ยิงครั้งเดียวตอน Purchase สำเร็จ
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  event: 'purchase',
  ecommerce: {
    transaction_id: 'TXN-20409',
    value: 1590.00,
    currency: 'THB',
    items: [{
      item_id: 'SKU-0012',
      item_name: 'เซรั่มบำรุงผิว 30ml',
      price: 1590.00,
      quantity: 1
    }]
  }
});
```

จาก Data Layer เดียวกันนี้ GTM สามารถกระจาย (Fan-out) ไปยัง 3 Tag พร้อมกัน: GA4 Event Tag (`purchase`), Facebook Pixel Tag (`Purchase`), TikTok Pixel Tag (`CompletePayment`) — นี่คือหลักการที่ Part 090 (Server-Side Tracking) จะขยายเพิ่ม

### ข้อผิดพลาดที่พบบ่อย

- ตั้งชื่อ Custom Event คนละชื่อในแต่ละระบบสำหรับความหมายเดียวกัน (เช่น `LeadForm` ใน Facebook, `lead_submit` ใน GA4, `Contact` ใน TikTok) ทำให้ทีมสับสนเวลาต้อง Debug ข้ามระบบ
- คิดว่า Event ชื่อเหมือนกันจะ "รวมค่า" กันอัตโนมัติข้ามแพลตฟอร์ม — ความจริงแต่ละระบบเก็บ Event ของตัวเองแยกกัน การ Mapping มีไว้เพื่อให้อ่าน**เข้าใจตรงกัน** ไม่ใช่รวมข้อมูลอัตโนมัติ
- ลืม Mark Event ใน GA4 เป็น Key Event หลัง Map เสร็จ ทำให้ Report สรุปไม่นับ Event นั้นเป็น Conversion

### ตัวอย่างการตั้ง GTM Tag สำหรับ GA4 Event Configuration Tag

```
Tag Type: Google Analytics: GA4 Event
Configuration Tag: GA4 Configuration (Measurement ID: G-XXXXXXXXXX)
Event Name: {{DLV - event}}       // ดึงชื่อ Event จาก Data Layer
Event Parameters:
  - transaction_id : {{DLV - ecommerce.transaction_id}}
  - value          : {{DLV - ecommerce.value}}
  - currency       : {{DLV - ecommerce.currency}}
  - items          : {{DLV - ecommerce.items}}
Trigger: Custom Event = purchase
```

### ตัวอย่างการตั้ง GTM Tag สำหรับ Facebook Pixel คู่กัน (จาก Data Layer เดียวกัน)

```
Tag Type: Custom HTML (หรือ Facebook Pixel Template จาก Community Gallery)
HTML:
<script>
  fbq('track', 'Purchase', {
    value: {{DLV - ecommerce.value}},
    currency: {{DLV - ecommerce.currency}},
    content_ids: {{DLV - ecommerce.items.item_id}},
    content_type: 'product'
  });
</script>
Trigger: Custom Event = purchase
```

สังเกตว่าทั้งสอง Tag ใช้ Trigger เดียวกัน (`Custom Event = purchase`) และดึงค่าจาก Data Layer Variable เดียวกัน แต่แปลงชื่อ Event และรูปแบบ Parameter ให้ตรงกับที่แต่ละระบบต้องการ — นี่คือแก่นของการทำ Cross-Platform Tracking ที่ดี: **ยิง Data Layer ครั้งเดียว กระจาย Tag หลายปลายทาง** แทนการเขียนโค้ดแยกยิงแต่ละระบบเองซึ่งเสี่ยง Data ไม่ตรงกันสูงกว่ามาก

### เทคนิคตรวจสอบว่า Mapping ถูกต้องหรือไม่

ใช้ **GA4 DebugView** คู่กับ **Meta Pixel Helper** และ **TikTok Pixel Helper** เปิดพร้อมกันตอนทดสอบ Transaction จำลอง 1 ครั้ง แล้วเทียบว่า Event, Value, Currency ที่แต่ละเครื่องมือรายงานตรงกันหรือไม่ ถ้า Value ไม่ตรงกัน (เช่น GA4 ได้ 1590 แต่ Facebook ได้ 0) แสดงว่า Data Layer Variable Mapping ผิดที่ Tag ใด Tag หนึ่ง ต้องเข้าไปแก้ที่ GTM ก่อนปล่อยใช้งานจริง

---

## Step 887: สร้าง Unified UTM Taxonomy ให้เทียบเคียงกันได้ข้าม Platform ใน GA4

### จาก Naming Convention สู่ Taxonomy ที่ใช้งานได้ใน GA4 Report

Step 882 สร้างกฎการตั้งชื่อไว้แล้ว ขั้นนี้คือการทำให้ GA4 **อ่านและจัดกลุ่ม** ชื่อเหล่านั้นได้อย่างมีประโยชน์ เครื่องมือหลักคือ **Custom Dimension** และ **Regex Table** ใน Exploration

### สร้าง Custom Dimension จาก UTM เพื่อดึงข้อมูลย่อยออกมา

ค่า `utm_campaign` แบบ `fb-conv-sale0924-newcust-2409` มีข้อมูลซ่อนอยู่ 5 ส่วน แต่ GA4 มองเห็นเป็น String เดียว ถ้าต้องการแยกวิเคราะห์แต่ละส่วน (เช่น เทียบ Objective `conv` vs `lead` ข้ามแพลตฟอร์ม) มีสองวิธี:

**วิธีที่ 1 — แยกด้วย UTM เพิ่มเติม (แนะนำสำหรับ Setup ใหม่):** เพิ่ม Custom Parameter นอก UTM มาตรฐาน เช่น `cs_objective=conv&cs_audience=newcust` ต่อท้าย URL แล้วสร้าง Custom Dimension ใน GA4 ที่ Scope "Event" ดึงค่าจาก Parameter เหล่านี้ตรงๆ วิธีนี้แม่นยำที่สุดเพราะไม่ต้องแยก String ด้วย Regex

**วิธีที่ 2 — แยก String ด้วย Regex ใน BigQuery/Looker Studio:** สำหรับ Setup ที่มีอยู่แล้วและไม่อยากแก้ URL ทั้งหมด ใช้ Regex แยกส่วนจาก `utm_campaign` ตอนทำ Report เช่น:

```
REGEXP_EXTRACT(utm_campaign, r'^(fb|tt)-') AS platform
REGEXP_EXTRACT(utm_campaign, r'-([a-z]+)-[a-z0-9]+-') AS objective
```

### ทำให้ Session Source/Medium ของสองแพลตฟอร์ม "จัดกลุ่มเดียวกัน" ใน Default Channel Group

GA4 มี Default Channel Group ที่จัดกลุ่ม Traffic อัตโนมัติ ถ้า `utm_medium=paid_social` ถูกใช้ Consistent ทั้ง Facebook และ TikTok ทั้งคู่จะถูกจัดเข้ากลุ่ม **"Paid Social"** เดียวกันโดยอัตโนมัติ ทำให้ Report ระดับสูง (เช่น Acquisition Overview) แสดงผลรวม Paid Social ได้ทันทีโดยไม่ต้องทำอะไรเพิ่ม — นี่คือเหตุผลสำคัญที่สุดที่ทำไม `utm_medium` ต้อง Standardize ให้เหมือนกันทุกแพลตฟอร์มตั้งแต่ Step 882

### สร้าง Custom Channel Group แยกระเอียดกว่า Default

ถ้าต้องการแยก Facebook และ TikTok เป็นแถวย่อยภายใต้ Paid Social (ไม่ใช่รวมเป็นก้อนเดียว) ให้สร้าง **Custom Channel Group** ที่ Admin > Data Display > Channel Groups โดยตั้งเงื่อนไข:

| Channel Name | เงื่อนไข |
|---|---|
| Facebook Paid Social | `Session source` = `facebook` AND `Session medium` = `paid_social` |
| TikTok Paid Social | `Session source` = `tiktok` AND `Session medium` = `paid_social` |

วิธีนี้ทำให้ Report แสดงทั้งภาพรวม (Default Channel Group) และภาพแยกราย Platform (Custom Channel Group) พร้อมกันในเครื่องมือเดียว

### ตารางสรุป Taxonomy Layer ที่ควรมีครบ

| Layer | เก็บที่ไหน | ใช้ตอบคำถาม |
|---|---|---|
| Source/Medium | UTM มาตรฐาน | "Traffic มาจากแพลตฟอร์มไหน ผ่านช่องทางแบบไหน" |
| Campaign Taxonomy | utm_campaign (structured string) | "แคมเปญนี้ Objective/Audience/รอบไหน" |
| Content/Term | utm_content, utm_term | "Creative ตัวไหน Audience กลุ่มไหนที่เวิร์ก" |
| Custom Dimension | Parameter เพิ่มเติม หรือ Regex แยก | "เทียบ Objective เดียวกันข้าม Platform" |
| Channel Group | GA4 Admin Settings | "ภาพรวม Paid Social ทั้งหมดเทียบ Channel อื่น" |

### ข้อผิดพลาดที่พบบ่อย

- พยายามแยกข้อมูลละเอียดทั้งหมดด้วย Regex หลังเก็บข้อมูลไปแล้วหลายเดือน โดยไม่มีการวางแผน Taxonomy ตั้งแต่ต้น ทำให้ Regex ซับซ้อนและเสี่ยง Error สูง
- สร้าง Custom Channel Group ซ้อนกันหลายชุดจนทีมสับสนว่าดู Report ตัวไหนกันแน่
- ลืมว่า Default Channel Group เปลี่ยนพฤติกรรมตาม `utm_medium` โดยตรง — ถ้าตั้ง `utm_medium` ไม่ตรงกัน (เช่น Facebook ใช้ `social`, TikTok ใช้ `paid_social`) ทั้งสองจะถูกจัดเข้าคนละกลุ่มโดยไม่รู้ตัว

### สร้าง Audience/Segment จาก UTM สำหรับ Remarketing ข้าม Platform

ประโยชน์อีกอย่างของ Taxonomy ที่สร้างไว้คือการนำไปสร้าง **GA4 Audience** เพื่อ Export กลับไปยิง Remarketing ได้ เช่น สร้าง Audience "เคยเห็นโฆษณา TikTok แต่ไม่ซื้อภายใน 14 วัน" โดยกำหนดเงื่อนไข:

```
Condition 1: Session source = tiktok
Condition 2: Session medium = paid_social
Condition 3: Did not trigger event "purchase" within 14 days of first matching session
```

Audience นี้ Export ไปยัง Google Ads ได้ตรง หรือใช้เป็น Insight เพื่อสร้าง Custom Audience บน Facebook แบบ Manual (Upload Customer List ที่กรองจาก GA4/CRM) เป็นสะพานเชื่อมระหว่าง Data ที่ TikTok เก็บกับ Retargeting ที่ทำบน Facebook — เทคนิคนี้มีประโยชน์มากสำหรับธุรกิจที่พบว่า TikTok สร้าง Awareness ได้ดีแต่ Facebook Retargeting ปิดการขายได้ดีกว่า

### ตาราง Comparison: Facebook Ads Manager Report vs GA4 Report — เมื่อไหร่ควรเชื่อตัวไหน

| แง่มุม | Facebook Ads Manager | GA4 |
|---|---|---|
| Attribution Window | Default 7-day click, 1-day view (ปรับได้) นับ Conversion ที่ Facebook "เชื่อว่า" มาจากโฆษณาตัวเอง | Session-based ตาม Last Non-direct Click หรือ Data-driven Attribution ข้าม Channel ทั้งหมด |
| มองเห็น Traffic จากแพลตฟอร์มอื่นไหม | ไม่เห็น เห็นแต่ผลของตัวเอง | เห็นทุกแพลตฟอร์มที่มี UTM ถูกต้อง |
| Conversion ที่ไม่ผ่าน Browser (เช่น Offline, Call) | นับได้ถ้าตั้ง Offline Conversion/CAPI เพิ่ม | ไม่เห็นถ้าไม่ Integrate เพิ่ม |
| เหมาะกับการตัดสินใจแบบไหน | ปรับ Budget/Bid ระดับ Ad Set/Ad รายวัน | เข้าใจ Customer Journey ข้าม Channel ระดับกลยุทธ์ |

หลักปฏิบัติที่แนะนำคือ **ใช้ Ads Manager ของแต่ละแพลตฟอร์มสำหรับการตัดสินใจปรับแคมเปญรายวัน (Optimization) และใช้ GA4 สำหรับการตัดสินใจระดับกลยุทธ์ข้ามแพลตฟอร์ม (Budget Allocation ระดับเดือน/ไตรมาส)** ตัวเลขทั้งสองจะไม่เท่ากัน 100% เสมอ (เพราะ Attribution Model ต่างกัน) และนั่นเป็นเรื่องปกติ ไม่ใช่ความผิดพลาด — สิ่งที่สำคัญคือเข้าใจว่าทำไมต่างกันและใช้แต่ละตัวให้ตรงกับคำถามที่ถูกต้อง

---

## Step 888: GA4 Explorations สำหรับเปรียบเทียบ Cross-Channel

### ทำไม Standard Report ไม่พอสำหรับคำถาม Cross-Platform

Report มาตรฐานของ GA4 (Acquisition, Engagement) ออกแบบมาให้ดูภาพกว้าง แต่คำถามจริงจากธุรกิจมักเจาะจงกว่านั้น เช่น "Lookalike Audience ของ Facebook กับ Interest Targeting ของ TikTok ใครสร้าง Retention 30 วันได้ดีกว่า" — คำถามแบบนี้ต้องใช้ **Explorations** ซึ่งเป็นเครื่องมือ Custom Report ที่ GA4 ให้มา

### Exploration Type ที่ใช้บ่อยที่สุดสำหรับงาน Cross-Platform

| Exploration Type | ใช้ตอบคำถาม |
|---|---|
| **Free-form** | เทียบ Metric หลายตัวข้าม Dimension ที่เลือกเอง เช่น เทียบ Conversion Rate ระหว่าง Session Source ต่างๆ |
| **Funnel Exploration** | ดู Drop-off ในแต่ละขั้นของ Funnel แยกตาม Source เช่น view_item → add_to_cart → purchase ของ Facebook เทียบ TikTok |
| **Cohort Exploration** | เทียบ Retention ของผู้ใช้ที่มาจาก Facebook vs TikTok ในแต่ละสัปดาห์หลังเข้าเว็บครั้งแรก |
| **Path Exploration** | ดูเส้นทางพฤติกรรมจริงของ User หลังคลิกจาก Facebook เทียบ TikTok |

### ตัวอย่างการสร้าง Free-form Exploration เทียบ Facebook vs TikTok

**Dimensions ที่เลือก:** Session source, Session campaign name
**Metrics ที่เลือก:** Sessions, Add to carts, Purchases, Purchase revenue, Session conversion rate
**Filter:** Session medium = paid_social

ผลลัพธ์ที่ได้จะเป็นตารางเทียบ Row ต่อ Row ระหว่างแคมเปญ Facebook และ TikTok ทั้งหมดในหน้าเดียว เพราะทั้งคู่ใช้ `utm_medium=paid_social` เดียวกันตาม Taxonomy ที่วางไว้

### ตัวอย่างการสร้าง Funnel Exploration เทียบ Drop-off

```
Step 1: view_item      (filter: session_source in [facebook, tiktok])
Step 2: add_to_cart
Step 3: begin_checkout
Step 4: purchase
Breakdown dimension: Session source
```

Funnel นี้จะแสดง % ที่หลุดออกในแต่ละขั้นแยกสีตามแพลตฟอร์ม ทำให้เห็นชัดว่าถ้า TikTok ดึง Traffic เข้ามาได้มากกว่าแต่ Drop-off ที่ `add_to_cart` สูงกว่า Facveook มาก ปัญหาอาจอยู่ที่ความเข้ากันของ Landing Page กับพฤติกรรมผู้ชม TikTok ไม่ใช่ปัญหาที่ตัวโฆษณา

### ตัวอย่างการสร้าง Cohort Exploration เทียบ Retention

```
Cohort inclusion: first_visit (filtered by session_source)
Cohort earning: any event within 30 days
Granularity: Weekly
```

เทียบ Retention Curve ของ Cohort "มาจาก Facebook" กับ "มาจาก TikTok" — มักพบว่า Audience จาก TikTok มี Retention ต่ำกว่าในสัปดาห์แรกๆแต่ค่อยๆใกล้เคียงกันในสัปดาห์ที่ 3-4 ซึ่งเป็น Insight ที่ Ads Manager ของแต่ละแพลตฟอร์มให้ไม่ได้เลย เพราะมองไม่เห็นพฤติกรรมหลังคลิกในระยะยาวข้าม Session

### ข้อผิดพลาดที่พบบ่อย

- สร้าง Exploration แล้วลืม Save เป็น Template ทำให้ต้องสร้างใหม่ทุกครั้งที่ต้องดูซ้ำ ควร Save และแชร์ให้ทีม
- ใช้ Dimension "Source/Medium" (Default Session Level) ปนกับ "First user source/medium" (Attribution ตอนมาครั้งแรก) โดยไม่รู้ความต่าง ทำให้ตีความ Attribution ผิด
- ตั้ง Date Range สั้นเกินไป (7 วัน) สำหรับ Cohort Exploration ที่ต้องการเห็น Pattern ระยะยาว ทำให้ข้อมูลไม่มีนัยสำคัญทางสถิติ

### Segment Overlap: ดูว่าผู้ใช้เจอทั้ง Facebook และ TikTok หรือไม่

หนึ่งใน Insight ที่มีค่ามากที่สุดของ Cross-Platform Analysis คือการดูว่ามีผู้ใช้กลุ่มไหนที่เจอโฆษณาทั้งสองแพลตฟอร์มก่อนซื้อ ("Multi-touch") ใน GA4 ทำได้ผ่าน **Segment Overlap Exploration**:

```
Segment A: Users who had a session with source = facebook
Segment B: Users who had a session with source = tiktok
Exploration Type: Segment Overlap
```

ผลลัพธ์จะแสดง Venn Diagram บอกจำนวน User ที่เจอ Facebook เท่านั้น, TikTok เท่านั้น, และเจอทั้งคู่ — ถ้าพบว่ากลุ่มที่เจอทั้งคู่มี Conversion Rate สูงกว่ากลุ่มที่เจอแพลตฟอร์มเดียวอย่างมีนัยสำคัญ นั่นเป็นหลักฐานสนับสนุนกลยุทธ์ **Omnichannel** ที่ยิงทั้งสองแพลตฟอร์มพร้อมกันในกลุ่มเป้าหมายเดียวกัน แทนการเลือกใช้แพลตฟอร์มเดียว (ประเด็นนี้จะขยายต่อใน Part 099 เรื่อง Omnichannel Strategy)

### สร้าง Exploration Template มาตรฐานสำหรับใช้ทุกสัปดาห์

เพื่อไม่ต้องสร้าง Exploration ใหม่ทุกครั้ง แนะนำให้ทำ Template 3 ชุดเก็บไว้ใน Property แล้ว Duplicate ปรับ Date Range ทุกสัปดาห์:

| Template | เนื้อหา | ใช้ตอบคำถาม |
|---|---|---|
| Weekly Platform Comparison | Free-form: Session source × Sessions, Purchases, Revenue, Conv. Rate | "สัปดาห์นี้แพลตฟอร์มไหนทำผลงานดีกว่า" |
| Funnel Health Check | Funnel: view_item → add_to_cart → begin_checkout → purchase แยกตาม Source | "Drop-off เกิดขั้นไหน ต่างกันระหว่างแพลตฟอร์มอย่างไร" |
| New Customer Retention | Cohort: first_visit by Source, retained by any event 30 วัน | "ลูกค้าใหม่จากแพลตฟอร์มไหน Stick กับแบรนด์นานกว่า" |

---

## Step 889: ข้อผิดพลาด UTM ที่พบบ่อยและวิธีป้องกัน

### ตารางสรุปข้อผิดพลาดที่พบบ่อยที่สุดพร้อมผลกระทบและวิธีป้องกัน

| ข้อผิดพลาด | ผลกระทบต่อ Report | วิธีป้องกัน |
|---|---|---|
| ตัวพิมพ์เล็ก-ใหญ่ไม่ตรงกัน (`Facebook` vs `facebook`) | GA4 แยกเป็นสองแถว ข้อมูลกระจาย วิเคราะห์ยาก | บังคับ Lowercase ทุกครั้งด้วย Checklist หรือ Script ตรวจสอบก่อน Publish |
| ลืม `utm_medium` | Traffic ถูกจัดเป็น "(not set)" หรือปนกับ Organic | ใช้ Dynamic Parameter Template ที่ตั้งไว้ล่วงหน้าเสมอ ไม่พิมพ์มือทุกครั้ง |
| เว้นวรรคใน UTM | ถูก Encode เป็น `%20` อ่านไม่ออกใน Report | ใช้ Hyphen แทน Space ตาม Naming Convention |
| ใช้ UTM ซ้ำสองชุดในลิงก์เดียว | URL พัง Redirect ผิด หรือ Parameter ตัวหลังทับตัวแรก | ตรวจสอบด้วย URL Builder หรือปุ่ม Preview ก่อน Publish ทุกครั้ง |
| Copy URL แคมเปญเก่ามาใช้ซ้ำ | ข้อมูลแคมเปญใหม่ปนกับแคมเปญเก่า | ใช้ Dynamic UTM (Step 883, 884) แทนการพิมพ์มือเสมอที่ทำได้ |
| ใส่ตัวอักษรไทยหรือสัญลักษณ์พิเศษ | Encode เป็น String ยาวอ่านไม่ออก | ใช้ทับศัพท์อังกฤษหรือรหัสตัวย่อ (Code) แทนคำไทยเต็ม |
| Landing Page มี Redirect หลายชั้น (Shortlink → Redirect → Final URL) | UTM หลุดหายระหว่างการ Redirect ถ้า Redirect ไม่ Pass Parameter ต่อ | ทดสอบทุก Redirect Chain ด้วยการเปิด Link จริงและเช็ค URL ปลายทางว่า UTM ยังอยู่ครบ |
| Consent Mode/PDPA บล็อก Cookie ก่อน UTM ถูกบันทึก | Session แรกไม่มี UTM ติดมา ทำให้ Attribution เพี้ยนไปเป็น Direct/Organic | ตรวจสอบ Consent Banner ให้ยิง Analytics ได้ทันทีสำหรับ Cookie ประเภท Analytics (ไม่ต้องรอ Consent เต็มรูปแบบตามนโยบายที่ธุรกิจเลือกใช้) |

### เทคนิคตรวจสอบ UTM ก่อน Publish จริง (QA Checklist)

1. คัดลอก URL ที่มี UTM ไปเปิดใน Browser จริง (Incognito) แล้วเช็คว่า URL ปลายทางที่ Landing Page ยัง Keep Parameter ครบ
2. เปิด GA4 DebugView (ผ่าน GA Debugger Extension หรือ Tag Assistant) แล้วคลิก Ad จริงแบบ Test เพื่อดูว่า Session Source/Medium ขึ้นถูกต้องแบบ Real-time
3. เช็คด้วย Google's Campaign URL Builder หรือเครื่องมือภายในทีมเพื่อยืนยัน Syntax UTM ถูกต้องตาม Naming Convention ก่อนใส่ลง Ads Manager

### ข้อผิดพลาดระดับองค์กรที่มักมองข้าม

- ไม่มีเจ้าภาพ (Owner) รับผิดชอบ UTM Convention ทำให้เมื่อมีคนใหม่เข้าทีมไม่มีใครสอนและ Convention ค่อยๆพังไปเรื่อยๆ
- ไม่มี Central Sheet/Doc เก็บ Naming Convention ทำให้แต่ละแคมเปญต้องถามกันไปมาว่าจะตั้งชื่ออย่างไร เสียเวลาและเสี่ยงผิดพลาด

---

## Case Study: ร้านเครื่องสำอาง "GlowLab" รวมข้อมูล Facebook + TikTok หลังยิงแยกกัน 8 เดือน

### สถานการณ์ก่อนแก้ไข

GlowLab เป็นแบรนด์เครื่องสำอางที่ยิง Facebook Ads มา 8 เดือนและเริ่มยิง TikTok Ads เพิ่มอีก 3 เดือนหลัง ทีม Facebook ตั้งชื่อแคมเปญแบบ `Sale_Sept_NewCust_v3` ทีม TikTok (Freelance แยกคนละคน) ตั้งชื่อแบบ `tt_promo_september` — เมื่อเจ้าของแบรนด์ถามว่า "เดือนนี้ควรเพิ่มงบ Facebook หรือ TikTok" ทีม Marketing ต้องเปิด Ads Manager สองอันแยกกัน จด Excel มือ เทียบ ROAS ที่คำนวณคนละสูตร (Facebook คิดจาก Purchase Value ที่ Attribution 7-day click, TikTok คิดจาก Attribution 7-day click เหมือนกันแต่ Currency คนละแบบเพราะ Ad Account ตั้ง USD ไว้ผิดตอนแรก) — ทำให้ตัวเลขเทียบกันไม่ได้เลยและใช้เวลาทำ Report นี้เกือบครึ่งวันทุกสัปดาห์

### การแก้ไขตาม Framework ใน Part นี้

1. เขียนเอกสาร UTM Naming Convention ตาม Step 882 ร่วมกันทั้งสองทีม กำหนด Taxonomy `{platform}-{objective}-{promo}-{audience}-{yymm}`
2. ตั้ง Dynamic UTM ผ่าน `{{campaign.name}}` บน Facebook และ `__CAMPAIGN_NAME__` บน TikTok ให้ทั้งสองทีมเปลี่ยนชื่อ Campaign ในระบบให้ตรง Convention ก่อน แล้ว UTM จะถูกต้องอัตโนมัติ
3. สร้าง GA4 Property เดียว ตั้ง Currency เป็น THB ให้ตรงกับ Ad Account ทั้งสองแพลตฟอร์ม แก้ปัญหา Currency Mismatch ที่เป็นต้นเหตุ ROAS เพี้ยน
4. Mark `purchase` เป็น Key Event ใน GA4 และตั้ง Custom Channel Group แยก Facebook Paid Social / TikTok Paid Social
5. สร้าง Free-form Exploration เทียบ Session, Add to Cart, Purchase, Revenue ของทั้งสองแพลตฟอร์มในตารางเดียว รันทุกสัปดาห์

### ผลลัพธ์หลังใช้ระบบใหม่ 6 สัปดาห์

| ตัวชี้วัด | ก่อนแก้ | หลังแก้ |
|---|---|---|
| เวลาทำ Weekly Report | ~4 ชั่วโมง | ~30 นาที |
| ความมั่นใจในตัวเลข ROAS เทียบข้าม Platform | ต่ำ (คนละสูตร Currency) | สูง (Currency/Attribution สอดคล้องกัน) |
| การตัดสินใจจัดงบ | ตามความรู้สึก/ประสบการณ์ | อ้างอิงข้อมูล GA4 Exploration ที่เทียบ Apples-to-Apples |
| พบ Insight ใหม่ | ไม่มี | พบว่า TikTok ดึง Traffic ราคาถูกกว่าแต่ Add-to-Cart Rate ต่ำกว่า Facebook 40% นำไปสู่การแก้ Landing Page ให้เหมาะ Mobile-first มากขึ้น |

บทเรียนสำคัญจาก Case นี้คือ **ปัญหาไม่ได้อยู่ที่แพลตฟอร์มไหนดีกว่ากัน แต่อยู่ที่ระบบวัดผลที่ไม่ Comparable ตั้งแต่แรก** — เมื่อระบบ Tracking ถูกต้อง คำถาม "ใครดีกว่า" กลายเป็นคำถามที่ตอบได้ด้วยข้อมูล ไม่ใช่ความเห็น

## Case Study เพิ่มเติม: ธุรกิจคอร์สออนไลน์ "SkillUp Academy" ใช้ UTM แก้ปัญหา Lead ปลอม

### สถานการณ์

SkillUp Academy ขายคอร์สออนไลน์ผ่าน Lead Form ทั้งบน Facebook (Instant Form) และ TikTok (Instant Form เทียบเท่า) ทีม Sales บ่นว่า Lead จาก TikTok "คุณภาพแย่กว่า" Facebook มาก ปิดการขายได้น้อย แต่เมื่อถามว่า "แย่กว่ายังไง วัดจากอะไร" ไม่มีใครตอบได้ชัดเจน มีเพียงความรู้สึกจากทีม Sales ที่โทรตาม Lead ทุกวัน

### การแก้ไข

ทีมนำ Framework Part นี้มาใช้:

1. ตั้ง Taxonomy `{platform}-lead-{course-code}-{audience}-{yymm}` ให้ทั้งสองแพลตฟอร์ม
2. เนื่องจาก Lead Form เป็นแบบ Native (กรอกในแพลตฟอร์มโดยไม่เข้าเว็บ) UTM มาตรฐานใช้ไม่ได้ตรงๆ ทีมจึงส่ง Lead ทุกตัวเข้า CRM พร้อม Field "lead_source_campaign" ที่ดึงมาจาก Lead Ads Webhook (Facebook) และ Leads Center Export (TikTok) โดย Mapping ชื่อ Campaign ตาม Taxonomy เดียวกัน
3. เชื่อม CRM กับ GA4 ผ่าน Measurement Protocol เพื่อส่ง Event `generate_lead` และต่อมาส่ง Event Custom `sales_qualified_lead` และ `deal_closed` เมื่อ Sales อัปเดตสถานะใน CRM — ทำให้ GA4 เห็น Funnel เต็มตั้งแต่คลิกโฆษณาจนถึงปิดการขายจริง ไม่ใช่แค่ถึงขั้น Lead
4. สร้าง Exploration เทียบ "Lead-to-Close Rate" แยกตาม Session Source

### ผลลัพธ์

ตัวเลขจริงที่พบคือ TikTok สร้าง Lead ในราคาต่อหัวถูกกว่า Facebook ประมาณ 35% แต่ Lead-to-Close Rate ต่ำกว่าจริง (8% เทียบกับ 19% ของ Facebook) — ยืนยันความรู้สึกของทีม Sales ด้วยข้อมูลจริงเป็นครั้งแรก แต่สิ่งที่ Insight เพิ่มเติมเผยคือ **สาเหตุไม่ใช่ตัวแพลตฟอร์ม แต่เป็นคำถามในฟอร์มที่ TikTok สั้นกว่า Facebook ทำให้ได้ข้อมูล Lead น้อยกว่าและกรองคนที่ไม่พร้อมซื้อออกไม่ได้** ทีมแก้โดยเพิ่มคำถามคัดกรองในฟอร์ม TikTok ให้เทียบเท่า Facebook และ Lead-to-Close Rate ขยับขึ้นเป็น 13% ภายใน 2 เดือน — เป็นตัวอย่างที่ดีว่า Cross-Platform Tracking ไม่ใช่แค่บอกว่า "ใครดีกว่า" แต่ช่วยหาสาเหตุที่แท้จริงเพื่อแก้ปัญหาตรงจุด

---

## Checklist ท้ายบท

- [ ] มีเอกสาร UTM Naming Convention กลางที่ทั้งทีม Facebook และ TikTok ใช้ร่วมกัน
- [ ] utm_source, utm_medium มาตรฐานทุกแคมเปญ (`facebook`/`tiktok`, `paid_social` เหมือนกันทั้งคู่)
- [ ] utm_campaign เขียนตาม Taxonomy `{platform}-{objective}-{promo}-{audience}-{yymm}`
- [ ] ตั้ง Dynamic UTM Parameter บน Facebook ผ่าน `{{campaign.name}}` ฯลฯ
- [ ] ตั้ง URL Parameters บน TikTok ผ่าน `__CAMPAIGN_NAME__` ฯลฯ และมีตาราง Mapping ID ↔ Name สำหรับ Ad Group
- [ ] GA4 Property ตั้ง Currency/Timezone ตรงกับ Ad Account จริง
- [ ] Mark Key Event ครบตามตาราง Mapping (purchase, generate_lead, sign_up ฯลฯ)
- [ ] มี Custom Channel Group แยก Facebook Paid Social / TikTok Paid Social
- [ ] ทดสอบ URL จริงผ่าน Incognito + GA4 DebugView ก่อน Publish ทุกแคมเปญ
- [ ] สร้าง Exploration Template (Free-form, Funnel, Cohort) ไว้ใช้ซ้ำทุกสัปดาห์

---

## Step 890: Workshop — สร้างเอกสาร UTM Naming Convention ฉบับสมบูรณ์และทดสอบข้ามสองแพลตฟอร์มจริง

## Workshop / แบบฝึกหัด

### เป้าหมาย
สร้างเอกสาร UTM Naming Convention ฉบับสมบูรณ์ 1 ชุด และทดสอบใช้งานจริงข้าม Facebook และ TikTok อย่างน้อย 1 แคมเปญต่อแพลตฟอร์ม

### ขั้นตอน

1. **ร่าง Taxonomy** — เขียนโครงสร้าง `utm_campaign` ของธุรกิจ/ลูกค้าที่คุณดูแลตามแบบ `{platform}-{objective}-{promo}-{audience}-{yymm}` พร้อม Field Dictionary กำหนดค่าที่อนุญาตในแต่ละ Field (อ้างอิงตารางใน Step 882)
2. **ตั้งค่า Dynamic UTM จริง** — เข้า Ads Manager ของทั้งสองแพลตฟอร์ม ตั้ง URL Parameters ด้วย Dynamic Placeholder ตาม Step 883/884 บนแคมเปญทดสอบ (ใช้ Budget ต่ำสุดหรือ Campaign แบบ Draft ก็ได้)
3. **ตรวจสอบ URL จริง** — กด Preview ทั้งสองระบบ คัดลอก URL ที่ Render ออกมาจริง เปิดใน Incognito ตรวจว่า UTM ถูกต้องครบ 5 พารามิเตอร์
4. **ตั้งค่า GA4** — สร้างหรือใช้ Property ที่มีอยู่ ตรวจสอบ Currency/Timezone ให้ตรงกับ Ad Account Mark Key Event ตามตาราง Mapping ใน Step 886
5. **สร้าง Custom Channel Group** — ตั้ง Facebook Paid Social และ TikTok Paid Social ตามเงื่อนไขใน Step 887
6. **สร้าง Exploration แรก** — ทำ Free-form Exploration เทียบ Sessions, Purchases, Revenue ระหว่าง Session Source สองแพลตฟอร์ม
7. **เขียนสรุป 5 บรรทัด** — สรุปว่าพบ Insight อะไรจากการเทียบครั้งแรกนี้ (แม้ข้อมูลยังน้อยก็ให้ฝึกอ่านตารางเป็น)

### เกณฑ์ความสำเร็จ
เอกสาร Taxonomy ที่ทำสามารถส่งให้เพื่อนร่วมทีมอ่านแล้วตั้งชื่อแคมเปญได้ถูกต้องโดยไม่ต้องถามคุณเพิ่ม และ GA4 Exploration แสดงข้อมูลทั้งสองแพลตฟอร์มในตารางเดียวกันได้จริง

### แบบฟอร์มเอกสาร UTM Naming Convention (คัดลอกไปใช้ได้ทันที)

```
=== UTM Naming Convention — [ชื่อธุรกิจ] ===
Version: 1.0        Owner: [ชื่อ Tracking Owner]      Last Updated: [วันที่]

1. utm_source (ค่าคงที่ตามแพลตฟอร์ม)
   - facebook
   - tiktok

2. utm_medium (ค่าคงที่ — ห้ามเปลี่ยน)
   - paid_social

3. utm_campaign โครงสร้าง:
   {platform}-{objective}-{promo}-{audience}-{yymm}
   - platform: fb / tt
   - objective: conv / lead / traffic / aware / eng
   - promo: [รหัสโปรโมชั่นภายใน ดูรายการ Promo Code Master Sheet]
   - audience: newcust / retgt / lal / broad
   - yymm: ปี-เดือน 4 หลัก

4. utm_content โครงสร้าง:
   {ad-format}-{creative-id}-{version}
   ตัวอย่าง: carousel-ugc03-v2, spark-video01-v1

5. utm_term โครงสร้าง:
   {audience-detail}
   ตัวอย่าง: lal-1pct, interest-beauty, cid-1769xxxxxxxx01

=== ตัวอย่างสมบูรณ์ ===
Facebook: ?utm_source=facebook&utm_medium=paid_social&utm_campaign=fb-conv-sale0924-newcust-2409&utm_content=carousel-ugc03-v2&utm_term=lal-1pct
TikTok:   ?utm_source=tiktok&utm_medium=paid_social&utm_campaign=tt-conv-sale0924-newcust-2409&utm_content=spark-video01-v1&utm_term=cid-1769xxxxxxxx01
```

### คำถามที่พบบ่อยระหว่างทำ Workshop

**ถ้าธุรกิจใช้ Landing Page Builder ที่ไม่รองรับ Query Parameter ยาวๆ ทำอย่างไร?**
ให้ทดสอบก่อนว่า Builder นั้น Pass Parameter ผ่านไปยัง GA4 ได้จริงหรือไม่ (บาง Builder แบบ No-code ตัดพารามิเตอร์ที่ยาวเกินไปทิ้ง) ถ้าตัดทิ้งจริง ให้ลดความยาวของ `utm_campaign` โดยใช้รหัสย่อมากขึ้น หรือใช้ URL Shortener ที่ยืนยันว่า Pass Parameter ได้ครบ

**ถ้าทีมมีคนไม่เข้าใจภาษาอังกฤษดี ควรใช้รหัสแทนคำเต็มไหม?**
ใช้รหัสสั้นพร้อมเอกสารอธิบายแยกจะปลอดภัยกว่าการใช้คำเต็มที่อาจพิมพ์ผิด แต่ต้องมี Master Sheet ที่แปลรหัสกลับเป็นความหมายเสมอ ไม่เช่นนั้นทีมจะจดจำรหัสไม่ได้ในระยะยาว

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้วางรากฐานสำคัญของ Section J — ทำให้ UTM และ GA4 กลายเป็น "ภาษากลาง" ที่ Facebook และ TikTok สื่อสารกันได้ในมุมของการวัดผล คุณได้เรียนตั้งแต่โครงสร้าง UTM พื้นฐาน ไปจนถึง Dynamic Parameters ของทั้งสองแพลตฟอร์ม การตั้งค่า GA4 ให้ถูกต้อง การ Map Event ให้เข้าใจตรงกัน และการใช้ Exploration ตอบคำถาม Cross-Platform จริง

แต่ระบบที่สร้างไว้ใน Part นี้ยังมีข้อจำกัดสำคัญหนึ่งอย่าง: **มันยังพึ่งพา Browser-side Tracking เป็นหลัก** (Pixel ที่ยิงจาก Browser ผู้ใช้) ซึ่งถูกกระทบหนักจาก Ad Blocker, iOS App Tracking Transparency, และการทยอยเลิกใช้ Third-party Cookie ของ Browser Vendor ต่างๆ Part 090 จะพาคุณไปอีกขั้น — สร้างระบบ Tracking แบบ Server-Side ผ่าน Conversions API, TikTok Events API และ Server-Side Google Tag Manager ที่ทำให้ข้อมูลแม่นยำขึ้นและทนทานต่อการบล็อกมากกว่าที่ Browser-side เพียงอย่างเดียวจะทำได้

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Google Analytics 4 Help Center — หมวด "Campaign URL Builder" และ "Recommended events"
- Meta Business Help Center — หมวด "About URL parameters" และ "Dynamic creative and dynamic parameters"
- TikTok Ads Help Center — หมวด "Tracking URL and macros for TikTok Ads"
- Google Tag Manager Help Center — หมวด "Data Layer" และ "GA4 Configuration Tag"
- เอกสารภายในทีม: แนะนำให้ทำ Google Sheet ชื่อ "UTM Naming Convention Master" แชร์ให้ทุกคนที่สร้างแคมเปญเข้าถึงได้ตลอดเวลา
