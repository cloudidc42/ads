# Part 091: Dashboard และ Reporting (Google Sheets, Looker Studio)

**Section:** J — Cross-Platform Analytics, Tracking & Automation (Part 089–093, Step 881–930)
**Step ที่ครอบคลุม:** 901–910 (จาก 1000 Steps ทั้งหมด)
**เวลาเรียนโดยประมาณ:** 13–15 ชั่วโมง (อ่าน+ทำความเข้าใจ 5 ชม. / สร้าง Template Google Sheets และ Looker Studio จริง 8–10 ชม.)

---

## ทำไม Part นี้สำคัญ

Part 089 ทำให้ Facebook และ TikTok พูดภาษาเดียวกันใน GA4 ผ่าน UTM และ Event Mapping ส่วน Part 090 ทำให้ข้อมูลนั้นแม่นยำขึ้นด้วย Server-Side Tracking — แต่ข้อมูลที่ดีและแม่นยำจะไม่มีประโยชน์อะไรเลยถ้ามันถูกฝังอยู่ใน Ads Manager สองอันแยกกันที่ไม่มีใครอยากเปิดดูพร้อมกัน

ความจริงที่นักยิงแอดมืออาชีพทุกคนเจอคือ **เจ้าของธุรกิจ ผู้บริหาร หรือลูกค้าไม่มีเวลาและไม่มีความอยากเปิด Ads Manager ของ Facebook แล้วสลับไปเปิด TikTok Ads Manager เพื่อจดตัวเลขมาเทียบเองทุกสัปดาห์** พวกเขาต้องการเห็นภาพเดียวที่ตอบคำถามสำคัญได้ทันที: "เดือนนี้ผลงานเป็นอย่างไร" "งบที่ใช้คุ้มไหม" "ควรปรับอะไรต่อ" — และนักยิงแอดที่ตอบคำถามนี้ได้เร็วและชัดเจนที่สุดคือคนที่ลูกค้าไว้ใจให้ดูแลงบก้อนใหญ่ขึ้นเรื่อยๆ

Part นี้จะพาคุณสร้างระบบ Dashboard และ Reporting แบบ Cross-Platform ตั้งแต่ Google Sheets Template ที่ใช้งานได้ทันทีแม้ไม่มีเครื่องมือแพง ไปจนถึง Looker Studio Dashboard ระดับมืออาชีพที่ Blend ข้อมูล Facebook Ads, TikTok Ads และ GA4 เข้าด้วยกัน พร้อมหลักการเลือก View ที่เหมาะกับผู้ฟังแต่ละกลุ่ม และการหลีกเลี่ยงกับดัก Vanity Metrics ที่ทำให้ Report ดูสวยแต่ไม่มีประโยชน์ในการตัดสินใจจริง

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 901 — ทำไมต้องมี Dashboard รวม ไม่ใช่เปิด 2 Ads Manager แยกกัน** ปัญหาที่เกิดจากการรายงานแบบกระจัดกระจายและผลกระทบต่อความน่าเชื่อถือของนักยิงแอด
2. **Step 902 — สร้าง Google Sheets Reporting Template ดึงข้อมูล Facebook + TikTok** วิธี Export มือ, Connector อัตโนมัติ, และโครงสร้าง Sheet ที่ใช้งานได้จริง
3. **Step 903 — ใช้ API ดึงข้อมูลอัตโนมัติเข้า Google Sheets (แนวคิด)** Facebook Marketing API และ TikTok Business API ผ่าน Apps Script/Connector
4. **Step 904 — ออกแบบ Looker Studio Dashboard: Data Source และ Blending** เชื่อม Facebook Ads, TikTok Ads, GA4 เข้าด้วยกันใน Data Source เดียว
5. **Step 905 — สร้าง Looker Studio Dashboard: Executive Summary View** หน้าสรุปสำหรับผู้บริหาร/ลูกค้าที่ไม่มีเวลาดูรายละเอียด
6. **Step 906 — สร้าง Looker Studio Dashboard: Campaign-Level และ Creative-Level View** หน้าเจาะลึกสำหรับ Media Buyer ใช้ปรับแคมเปญจริง
7. **Step 907 — Automating Recurring Reports** ตั้งค่า Schedule Email, PDF Export, และ Alert อัตโนมัติ
8. **Step 908 — การนำเสนอข้อมูลให้ Stakeholder ที่ไม่ใช่สาย Technical** เทคนิคเล่าเรื่องด้วยข้อมูล (Data Storytelling) สำหรับลูกค้า/เจ้าของธุรกิจ
9. **Step 909 — ข้อผิดพลาดที่พบบ่อยในการทำ Dashboard** Vanity Metrics, ไม่มี Benchmark/Context, Dashboard ที่สวยแต่ตอบคำถามไม่ได้
10. **Step 910 — Workshop: สร้าง Weekly Cross-Platform Report Template ฉบับสมบูรณ์**

---

## Step 901: ทำไมต้องมี Dashboard รวม ไม่ใช่เปิด 2 Ads Manager แยกกัน

### ต้นทุนที่มองไม่เห็นของการรายงานแบบกระจัดกระจาย

เมื่อทีมต้องเปิด Facebook Ads Manager คัดลอกตัวเลขไปวางใน Excel แล้วสลับไปเปิด TikTok Ads Manager คัดลอกอีกชุดมาต่อกัน ทุกขั้นตอนนี้มีความเสี่ยงผิดพลาดสะสม: คัดลอกผิดคอลัมน์ วางผิดแถว ลืมอัปเดตบางแพลตฟอร์ม เทียบ Attribution Window ไม่ตรงกัน (Facebook อาจตั้ง 7-day click ส่วน TikTok ตั้ง Default ต่างออกไป) — และที่สำคัญที่สุดคือ **เวลาที่เสียไปกับงานคัดลอกข้อมูลคือเวลาที่ไม่ได้ใช้คิดวิเคราะห์หรือปรับแคมเปญ**

### ผลกระทบต่อความน่าเชื่อถือในสายตาลูกค้า/ผู้บริหาร

ลูกค้าหรือผู้บริหารที่ต้องรอ Report เพราะทีมยัง "กำลังรวมตัวเลข" จะเริ่มตั้งคำถามถึงความเป็นมืออาชีพของทีม ในทางกลับกัน นักยิงแอดที่ส่ง Dashboard ที่อัปเดตข้อมูลสด (หรือใกล้สด) ให้ลูกค้าดูได้ทุกเมื่อโดยไม่ต้องรอ จะถูกมองว่ามีระบบการทำงานที่น่าเชื่อถือกว่ามาก แม้ผลงานแคมเปญจะเท่ากันก็ตาม

### ตารางเปรียบเทียบวิธีการรายงานสามระดับ

| ระดับ | วิธีการ | ข้อดี | ข้อเสีย |
|---|---|---|---|
| ระดับ 1: Manual Copy-paste | เปิด Ads Manager ทั้งสอง คัดลอกตัวเลขมือลง Excel/Sheets | ไม่ต้องมีเครื่องมือเพิ่ม เริ่มได้ทันที | เสียเวลามาก เสี่ยงผิดพลาด ไม่ Real-time |
| ระดับ 2: Semi-automated (Sheets + Connector/API) | ใช้ Google Sheets ร่วมกับ Apps Script หรือ Connector ดึงข้อมูลอัตโนมัติบางส่วน | ลดงานคัดลอกมือ อัปเดตได้บ่อยขึ้น | ต้อง Setup เริ่มต้น ต้องมีความรู้ทางเทคนิคระดับหนึ่ง |
| ระดับ 3: Full Dashboard (Looker Studio + Blended Data Source) | เชื่อมต่อ Data Source โดยตรง Visualize อัตโนมัติ อัปเดตตาม Schedule | มืออาชีพที่สุด อัปเดตอัตโนมัติ แบ่ง View ตามผู้ฟังได้ | ต้องเข้าใจการ Blend Data และ Data Source Configuration |

ธุรกิจส่วนใหญ่ควรเริ่มจากระดับ 2 (Google Sheets ที่ทำ Automation บางส่วน) แล้วขยับไประดับ 3 เมื่อมีจำนวนแคมเปญ/แพลตฟอร์มมากขึ้นจนตารางเดียวไม่พอ

### ข้อผิดพลาดที่พบบ่อย

- คิดว่าต้องมี Dashboard ระดับ 3 ตั้งแต่วันแรกทั้งที่ธุรกิจยังมีแคมเปญไม่กี่ตัว ทำให้เสียเวลา Setup เกินความจำเป็นเมื่อเทียบกับประโยชน์ที่ได้ในช่วงเริ่มต้น
- ทำ Dashboard สวยงามแต่ไม่มีใครในทีมเข้าใจวิธีอัปเดต/แก้ไข ทำให้ Dashboard ค้างข้อมูลเก่าโดยไม่มีใครรู้ตัว
- ไม่มี Fallback Plan เมื่อ API/Connector มีปัญหา ทำให้ Report สัปดาห์นั้นหายไปเลยโดยไม่มีข้อมูลสำรอง

### หลักการเลือกระดับที่เหมาะกับขนาดธุรกิจ

| ขนาดธุรกิจ/จำนวนแคมเปญ | ระดับที่แนะนำ | เหตุผล |
|---|---|---|
| SME ยิงแคมเปญ 1-5 ตัว งบต่ำกว่า 50,000 บาท/เดือน | ระดับ 1-2 | ปริมาณข้อมูลน้อย Manual/Semi-automated ยังจัดการได้ ไม่คุ้มกับความซับซ้อนของระดับ 3 |
| ธุรกิจกลาง ยิงหลายแคมเปญ งบ 50,000-500,000 บาท/เดือน | ระดับ 2-3 | ปริมาณข้อมูลเริ่มมากพอที่ Automation จะคืนทุนเวลาชัดเจน |
| เอเจนซี่ที่ดูแลลูกค้าหลายราย หรือธุรกิจงบสูงกว่า 500,000 บาท/เดือน | ระดับ 3 เต็มรูปแบบ | ต้องการ Template ที่ Scale ได้กับหลายบัญชี/หลายลูกค้าพร้อมกัน |

### บทบาทของ Dashboard ในการสร้างความไว้วางใจระยะยาว

นอกจากประหยัดเวลา Dashboard ที่โปร่งใสยังเป็นเครื่องมือป้องกันความเข้าใจผิดระหว่างนักยิงแอดกับลูกค้า เมื่อลูกค้าเห็นข้อมูลได้ตลอดเวลาโดยไม่ต้องขอ ความสงสัยเรื่อง "เงินไปไหน ผลลัพธ์เป็นอย่างไร" จะลดลงมาก และเมื่อผลงานไม่ดีในบางช่วง การมี Dashboard ที่แสดงข้อมูลตรงไปตรงมาอยู่แล้วจะทำให้บทสนทนาเรื่องแก้ปัญหาเกิดขึ้นเร็วกว่าการที่ลูกค้าต้องมาทวงถามก่อน

---

## Step 902: สร้าง Google Sheets Reporting Template ดึงข้อมูล Facebook + TikTok

### โครงสร้าง Sheet ที่แนะนำ

```
Google Sheets File: "Cross-Platform Ads Report — [ชื่อธุรกิจ]"
├── Tab 1: Raw_Facebook      (ข้อมูล Export ดิบจาก Facebook Ads Manager)
├── Tab 2: Raw_TikTok        (ข้อมูล Export ดิบจาก TikTok Ads Manager)
├── Tab 3: Raw_GA4           (ข้อมูล Export จาก GA4 Exploration หรือ API)
├── Tab 4: Unified_Data      (รวมข้อมูลจาก 3 Tab ข้างบนด้วยสูตร มาตรฐานคอลัมน์เดียวกัน)
├── Tab 5: Summary_Dashboard (สรุปตัวเลขหลักพร้อมกราฟ อ้างอิงจาก Unified_Data)
└── Tab 6: Notes_Context     (บันทึกเหตุการณ์สำคัญ เช่น เปลี่ยน Creative, โปรโมชั่นพิเศษ)
```

### คอลัมน์มาตรฐานที่ควรมีใน Unified_Data (ใช้ Taxonomy จาก Part 089)

| คอลัมน์ | คำอธิบาย |
|---|---|
| `date` | วันที่ของข้อมูล |
| `platform` | `facebook` / `tiktok` |
| `campaign_name` | ชื่อแคมเปญตาม Naming Convention |
| `objective` | ดึงจาก Taxonomy (conv, lead, traffic, aware, eng) |
| `spend` | งบที่ใช้ |
| `impressions` | จำนวนการแสดงผล |
| `clicks` | จำนวนคลิก |
| `results` | จำนวน Conversion/Result ตาม Objective |
| `revenue` | รายได้ (ถ้าเป็น Objective เชิง Conversion) |
| `currency` | สกุลเงิน (ควร Standardize เป็นสกุลเดียวเสมอ) |

### สูตรตัวอย่างสำหรับรวมข้อมูลจากสองแพลตฟอร์มให้อยู่ในโครงสร้างเดียว

```
=QUERY({Raw_Facebook!A:H; Raw_TikTok!A:H}, "SELECT * WHERE Col1 IS NOT NULL", 1)
```

สูตรนี้ใช้ได้เมื่อทั้งสอง Tab มีจำนวนคอลัมน์และลำดับตรงกัน — ซึ่งเป็นเหตุผลที่ต้อง Standardize ชื่อคอลัมน์ Export จากทั้งสองแพลตฟอร์มให้ตรงกันก่อนเสมอ (เปลี่ยนชื่อ Column Header ตอน Export ให้ตรง Format มาตรฐานของทีม)

### สูตรคำนวณ ROAS และ CPA มาตรฐานที่ใช้ในทุกแถว

```
ROAS  = revenue / spend
CPA   = spend / results
CTR   = clicks / impressions
CPM   = (spend / impressions) * 1000
```

ใส่สูตรเหล่านี้เป็นคอลัมน์เพิ่มใน Unified_Data เพื่อให้ Summary_Dashboard ดึงไปใช้ต่อได้ทันทีโดยไม่ต้องคำนวณซ้ำในหลายที่ (ลดความเสี่ยง Error จากสูตรไม่ตรงกัน)

### ข้อผิดพลาดที่พบบ่อย

- Export ข้อมูลจากสองแพลตฟอร์มโดยเลือก Column ไม่ตรงกัน (เช่น Facebook Export "Amount Spent (THB)" แต่ TikTok Export "Cost") ทำให้ QUERY หรือสูตรรวมข้อมูลพัง
- ใส่สูตรคำนวณ ROAS/CPA ซ้ำหลายจุดในไฟล์ (บาง Tab คำนวณเอง บาง Tab อ้างจาก Tab อื่น) ทำให้ตัวเลขไม่ตรงกันเมื่อมีคนแก้สูตรจุดหนึ่งแต่ลืมแก้อีกจุด
- ไม่ล็อก (Protect) Tab ข้อมูลดิบ ทำให้มีคนแก้ไขข้อมูล Raw โดยไม่ตั้งใจและ Report เพี้ยนไปโดยไม่รู้สาเหตุ

### ขั้นตอน Export มือแบบละเอียดสำหรับทีมที่ยังไม่พร้อมทำ Automation

**จาก Facebook Ads Manager:** เข้า Ads Manager > เลือก Campaign ที่ต้องการ > ปุ่ม Columns > Customize Columns > เลือก Field ให้ตรงกับคอลัมน์มาตรฐานที่กำหนดไว้ > กด Export > Export table data (.csv) > เปิดไฟล์แล้ว Copy วางลง Tab Raw_Facebook

**จาก TikTok Ads Manager:** เข้า Campaign > เลือก Metrics ที่ต้องการแสดงผ่านปุ่ม Customize Metrics > กด Export ที่มุมขวาบน > เลือก Data Range และ Level (Campaign/Ad Group/Ad) ให้ตรงกับที่ Facebook Export มา > วางลง Tab Raw_TikTok

**ข้อควรระวังตอน Export มือทุกครั้ง:** ตรวจสอบ Timezone ที่ Ads Manager ใช้แสดงผลให้ตรงกับ Timezone ที่ GA4 Property ใช้ (Step 885) มิฉะนั้นข้อมูลวันที่จะเหลื่อมกัน 1 วันเมื่อนำมา Join กัน

---

## Step 903: ใช้ API ดึงข้อมูลอัตโนมัติเข้า Google Sheets

### แนวคิดของการดึงข้อมูลอัตโนมัติ

การ Export มือทุกสัปดาห์ทำได้ในระยะสั้น แต่ไม่ Scale เมื่อมีหลายแคมเปญ/หลายบัญชี ทางเลือกคือใช้ **Google Apps Script** เขียน Script เรียก Facebook Marketing API และ TikTok Business API ดึงข้อมูลเข้า Sheets โดยตรงตาม Schedule ที่ตั้งไว้ (เช่น ทุกเช้าวันจันทร์)

### โครงสร้างแนวคิดของ Apps Script ที่เรียก Facebook Marketing API

```javascript
function fetchFacebookData() {
  var accessToken = 'YOUR_LONG_LIVED_ACCESS_TOKEN';
  var adAccountId = 'act_XXXXXXXXXX';
  var url = 'https://graph.facebook.com/v19.0/' + adAccountId + '/insights' +
            '?fields=campaign_name,spend,impressions,clicks,actions' +
            '&level=campaign&date_preset=last_7d' +
            '&access_token=' + accessToken;

  var response = UrlFetchApp.fetch(url);
  var data = JSON.parse(response.getContentText());

  var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Raw_Facebook');
  data.data.forEach(function(row) {
    sheet.appendRow([
      new Date(), row.campaign_name, row.spend, row.impressions, row.clicks
    ]);
  });
}
```

### โครงสร้างแนวคิดสำหรับ TikTok Business API

```javascript
function fetchTikTokData() {
  var accessToken = 'YOUR_TIKTOK_ACCESS_TOKEN';
  var advertiserId = 'YOUR_ADVERTISER_ID';
  var url = 'https://business-api.tiktok.com/open_api/v1.3/report/integrated/get/' +
            '?advertiser_id=' + advertiserId +
            '&report_type=BASIC&dimensions=["campaign_id"]' +
            '&metrics=["spend","impressions","clicks","conversion"]' +
            '&data_level=AUCTION_CAMPAIGN';

  var options = {
    method: 'get',
    headers: { 'Access-Token': accessToken }
  };
  var response = UrlFetchApp.fetch(url, options);
  var data = JSON.parse(response.getContentText());
  // ประมวลผลและเขียนเข้า Sheet เช่นเดียวกับตัวอย่าง Facebook ข้างบน
}
```

### ตั้ง Trigger ให้ Script รันอัตโนมัติตาม Schedule

```
Apps Script Editor > Triggers > Add Trigger
Function: fetchFacebookData / fetchTikTokData
Event source: Time-driven
Type: Week timer
Day and time: ทุกวันจันทร์ 07:00
```

### ทางเลือกสำหรับทีมที่ไม่มี Developer: Connector สำเร็จรูป

สำหรับทีมที่ไม่มีความรู้เขียน Apps Script มีบริการ Connector สำเร็จรูป (ประเภท Supermetrics, Windsor.ai และเครื่องมือคล้ายกัน) ที่ติดตั้งเป็น Add-on บน Google Sheets แล้วเลือกดึงข้อมูลจาก Facebook/TikTok ผ่านหน้า UI โดยไม่ต้องเขียนโค้ดเลย ข้อดีคือ Setup เร็วกว่ามาก ข้อเสียคือมีค่าบริการรายเดือนตามปริมาณข้อมูล/บัญชีที่เชื่อมต่อ ซึ่งธุรกิจต้องประเมินความคุ้มค่าเทียบกับการจ้าง/ฝึก Developer ทำ Apps Script เอง

### ข้อผิดพลาดที่พบบ่อย

- เก็บ Access Token ไว้ในโค้ด Script ตรงๆแบบ Plain Text ในไฟล์ที่แชร์กับหลายคน เสี่ยง Token รั่วไหล ควรใช้ Script Properties (`PropertiesService`) เก็บ Token แยกจากโค้ดที่มองเห็นได้
- ไม่ตรวจสอบว่า Access Token มีวันหมดอายุ (Facebook User Token แบบสั้นหมดอายุเร็ว ควรใช้ Long-lived Token หรือ System User Token)
- ตั้ง Trigger ดึงข้อมูลถี่เกินไป (เช่น ทุก 5 นาที) ทำให้ชน Rate Limit ของ API และถูกบล็อกชั่วคราว ควรตั้งความถี่ให้เหมาะกับความจำเป็นจริง (รายวันหรือหลายครั้งต่อวันก็เพียงพอสำหรับ Report ส่วนใหญ่)

### เก็บ Access Token อย่างปลอดภัยด้วย Script Properties

```javascript
// ตั้งค่าครั้งเดียว (รันเองครั้งหนึ่งแล้วลบโค้ดนี้ทิ้ง ไม่ต้องเก็บ Token ไว้ในไฟล์)
function setupProperties() {
  PropertiesService.getScriptProperties().setProperties({
    'FB_ACCESS_TOKEN': 'YOUR_TOKEN_HERE',
    'TIKTOK_ACCESS_TOKEN': 'YOUR_TOKEN_HERE'
  });
}

// ดึงมาใช้ในฟังก์ชันอื่นโดยไม่ต้องเห็น Token ตรงๆในโค้ด
function fetchFacebookData() {
  var accessToken = PropertiesService.getScriptProperties().getProperty('FB_ACCESS_TOKEN');
  // ... ใช้ accessToken ต่อตามเดิม
}
```

### ตาราง Field ที่ควร Map ให้ตรงกันระหว่าง Facebook Insights API และ TikTok Reporting API

| ความหมาย | Field ชื่อใน Facebook Marketing API | Field ชื่อใน TikTok Business API |
|---|---|---|
| งบที่ใช้ | `spend` | `spend` |
| การแสดงผล | `impressions` | `impressions` |
| คลิก | `clicks` | `clicks` |
| Conversion | `actions` (ต้องกรองประเภท Action ที่ต้องการจาก Array) | `conversion` |
| ต้นทุนต่อคลิก | `cpc` | `cpc` |

การรู้ Field Mapping เหล่านี้ล่วงหน้าช่วยให้เขียน Apps Script ที่แปลงข้อมูลทั้งสองแหล่งให้อยู่ในโครงสร้างเดียวกันได้ตรงจุด ไม่ต้องเสียเวลา Debug ตอนพบว่าชื่อ Field ไม่ตรงกันหลัง Deploy ไปแล้ว

---

## Step 904: ออกแบบ Looker Studio Dashboard — Data Source และ Blending

### ทำไม Looker Studio เหมาะกับงาน Cross-Platform Dashboard

Looker Studio (เดิมชื่อ Google Data Studio) เป็นเครื่องมือ Visualization ฟรีของ Google ที่เชื่อมต่อกับ Data Source หลากหลายได้ในตัว รวมถึง Google Sheets, GA4 โดยตรง และผ่าน Connector ของ Third-party สำหรับ Facebook/TikTok Ads จุดแข็งที่สำคัญคือฟีเจอร์ **Blend Data** ที่รวมหลาย Data Source เข้าเป็นตารางเดียวโดยไม่ต้องเขียนโค้ด

### โครงสร้าง Data Source ที่แนะนำ

| Data Source | เชื่อมต่อผ่าน | เก็บข้อมูล |
|---|---|---|
| Facebook Ads | Connector สำเร็จรูป (บาง Connector มีให้ฟรีจำกัด Field หรือใช้ Google Sheets ที่ดึงมาจาก Step 903 เป็นตัวกลาง) | Spend, Impressions, Clicks, Results, Campaign Name |
| TikTok Ads | เช่นเดียวกับ Facebook ผ่าน Connector หรือ Google Sheets ตัวกลาง | Spend, Impressions, Clicks, Conversion, Campaign Name |
| GA4 | Looker Studio's Native GA4 Connector (เชื่อมตรงไม่ต้องผ่านตัวกลาง) | Sessions, Users, Key Events, Revenue, Session Source/Medium |

### การ Blend Data ให้ Facebook, TikTok, GA4 อยู่ในตารางเดียว

```
Resource > Manage blended data > Add a data source

Join Keys:
- date (จาก Facebook) = date (จาก TikTok) = date (จาก GA4)
- ใช้ LEFT OUTER JOIN เพื่อไม่ให้วันที่ที่ไม่มีข้อมูลบางแพลตฟอร์มถูกตัดออกทั้งแถว

Metrics ที่ดึงมารวม:
- spend (Facebook) + spend (TikTok) = Total Ad Spend
- results (Facebook) + conversion (TikTok) = Total Conversions
- purchase_revenue (GA4) = ใช้เป็น Revenue กลางที่เชื่อถือได้มากกว่าเพราะไม่ผ่าน Attribution Model ของแต่ละแพลตฟอร์มที่นับซ้อนกันได้
```

### หลักการสำคัญ: Join Key ต้อง Consistent

Blend Data จะทำงานถูกต้องก็ต่อเมื่อ Field ที่ใช้ Join (มักเป็น `date` หรือ `campaign_name`) มีรูปแบบตรงกันทุก Data Source เช่น Date Format ต้องเป็น YYYYMMDD เหมือนกันทั้งสามแหล่ง ถ้า Facebook Export เป็น DD/MM/YYYY แต่ GA4 เป็น YYYYMMDD การ Join จะไม่ตรงกันและ Dashboard จะแสดงข้อมูลว่างหรือผิดเพี้ยน

### ข้อผิดพลาดที่พบบ่อย

- Blend Data ด้วย INNER JOIN ทำให้วันที่ที่มีข้อมูลแค่แพลตฟอร์มเดียว (เช่น TikTok ไม่ได้ยิงในวันนั้น) หายไปทั้งแถว ควรใช้ LEFT OUTER JOIN จาก Data Source หลักเสมอ
- ใช้ Revenue จาก Facebook และ TikTok Ads Manager มารวมกันตรงๆ โดยไม่ระวังเรื่อง Double Counting (ถ้าลูกค้าเห็นโฆษณาทั้งสองแพลตฟอร์มก่อนซื้อ ทั้งสองระบบอาจนับ Revenue เดียวกันเป็นของตัวเอง) แนะนำให้ใช้ Revenue จาก GA4 หรือระบบ Order Management เป็นตัวเลขกลางที่น่าเชื่อถือกว่าสำหรับภาพรวม แล้วใช้ Revenue จาก Ads Manager เฉพาะตอนดู Performance ระดับแพลตฟอร์มเดี่ยว
- ไม่ตั้งชื่อ Field ให้สื่อความหมายก่อน Publish Dashboard ทำให้คนอ่าน Dashboard สับสนกับชื่อ Field แบบ Technical (เช่น `metric_1`, `blend_field_a`)

---

## Step 905: สร้าง Looker Studio Dashboard — Executive Summary View

### หลักการออกแบบหน้าสำหรับผู้บริหาร/ลูกค้า

Executive Summary View ต้องตอบคำถาม **"เดือนนี้เป็นอย่างไรเทียบกับที่ผ่านมา"** ได้ภายใน 10 วินาทีแรกที่เปิดดู ไม่ใช่หน้าที่มีตารางตัวเลขละเอียดยิบ หลักการคือ **น้อยแต่มาก (Less is More)** — เลือกเฉพาะ Metric ที่สำคัญที่สุด 4-6 ตัว แสดงเป็น Scorecard ขนาดใหญ่พร้อม Trend Indicator (ลูกศรขึ้น/ลง เทียบกับช่วงก่อนหน้า)

### Layout ที่แนะนำสำหรับ Executive Summary

```
[แถวบนสุด: Date Range Selector + Platform Filter]

[แถว Scorecard หลัก 4 ช่อง]
  Total Spend    | Total Revenue  | Overall ROAS  | Total Conversions
  (เทียบ % เปลี่ยนแปลงจากช่วงก่อนหน้าใต้ตัวเลขหลักทุกช่อง)

[กราฟเส้น: Spend vs Revenue รายวัน แยกสีตาม Platform]

[กราฟแท่งแนวนอน: สัดส่วน Spend และ Revenue ระหว่าง Facebook vs TikTok]

[ตารางสรุปสั้น: Top 3 Campaign ที่ทำผลงานดีที่สุดของเดือนนี้]
```

### ตัวอย่าง Calculated Field สำหรับ Trend Indicator

```
% Change vs Previous Period =
  (SUM(revenue) - SUM(revenue_previous_period)) / SUM(revenue_previous_period)
```

Looker Studio รองรับการเทียบ Date Range กับ Comparison Period ในตัว (ตั้งค่าที่ Date Range Control > Comparison Date Range) ทำให้ Scorecard แสดง % เปลี่ยนแปลงอัตโนมัติโดยไม่ต้องสร้าง Calculated Field ซับซ้อนเองในหลายกรณี

### สีและการออกแบบที่เหมาะกับผู้ฟังกลุ่มนี้

ใช้สีแยก Platform ให้ Consistent ทุกหน้า (เช่น สีน้ำเงินสำหรับ Facebook, สีดำ/ชมพูสำหรับ TikTok ตาม Brand Color ของแต่ละแพลตฟอร์ม) เพื่อให้ผู้อ่านจดจำได้เร็วโดยไม่ต้องอ่าน Label ทุกครั้ง และหลีกเลี่ยงการใช้สีมากกว่า 4-5 สีในหน้าเดียวเพราะทำให้ดูรกและสื่อสารได้แย่ลง

### ข้อผิดพลาดที่พบบ่อย

- ใส่ตารางข้อมูลละเอียดทุก Field ในหน้า Executive Summary ทำให้ผู้บริหารต้องเสียเวลาหาตัวเลขที่สำคัญท่ามกลางข้อมูลที่ไม่จำเป็น
- ไม่ใส่ Context การเปลี่ยนแปลง (% เทียบช่วงก่อน) ทำให้ตัวเลขลอยๆไม่มีความหมาย เช่น "ROAS 3.2x" ฟังดูดีแต่ถ้าเดือนก่อนได้ 4.1x นั่นคือสัญญาณเตือนที่ผู้บริหารควรรู้
- ใช้ Chart Type ที่ซับซ้อนเกินจำเป็น (เช่น Scatter Plot, Heatmap) สำหรับผู้ฟังที่ไม่ใช่สาย Data ทำให้ต้องอธิบายเพิ่มก่อนจะเข้าใจ Chart แทนที่จะเข้าใจ Insight

---

## Step 906: สร้าง Looker Studio Dashboard — Campaign-Level และ Creative-Level View

### หลักการออกแบบหน้าสำหรับ Media Buyer

ต่างจาก Executive Summary หน้านี้ต้อง **ละเอียดพอที่จะใช้ตัดสินใจปรับแคมเปญได้จริง** โดยไม่ต้องสลับไปเปิด Ads Manager แยก แต่ยังต้อง Filter/Sort ได้สะดวกเพื่อไม่ให้ข้อมูลจำนวนมากล้นจนหาสิ่งที่ต้องการไม่เจอ

### Layout ที่แนะนำสำหรับ Campaign-Level View

```
[Filter Control: Platform, Objective, Date Range]

[ตารางหลัก: Campaign Name | Platform | Spend | Impressions | CTR | CPA | ROAS | Conversions]
  - เรียงตาม Spend มากไปน้อยโดยอัตโนมัติ
  - ใส่ Conditional Formatting: สีเขียวถ้า ROAS > Target, สีแดงถ้าต่ำกว่า Break-even

[กราฟ: CPA Trend รายวันของ Top 5 Campaign]

[กราฟเปรียบเทียบ: Objective เดียวกันข้าม Platform (เช่น Conversion Campaign ของ FB vs TikTok)]
```

### Layout ที่แนะนำสำหรับ Creative-Level View

```
[Filter Control: Campaign, Ad Format]

[ตาราง: Ad/Creative Name (จาก utm_content) | Platform | Spend | CTR | Thumbstop Rate* | CPA | Frequency]
  *Thumbstop Rate ดึงจาก Video Metrics ของ Ads Manager แต่ละแพลตฟอร์ม ไม่มีใน GA4 ตรงๆ
   ต้องดึงมาจาก Sheet ตัวกลาง (Step 902-903)

[ภาพตัวอย่าง Thumbnail ของ Creative แต่ละตัว ถ้า Connector รองรับการดึงภาพ]

[กราฟ Scatter: CTR (แกน X) vs CPA (แกน Y) เพื่อหา Creative ที่ทั้งดึงคลิกดีและ CPA ต่ำ]
```

### การใช้ Conditional Formatting เพื่อให้อ่านเร็วขึ้น

```
Style > Conditional formatting
Rule 1: ROAS >= 3.0  → Background สีเขียวอ่อน
Rule 2: ROAS 1.5-2.9 → Background สีเหลืองอ่อน
Rule 3: ROAS < 1.5   → Background สีแดงอ่อน
```

การตั้ง Threshold ต้องอ้างอิงจาก Break-even ROAS ที่คำนวณจริงของธุรกิจ (ทวน Part 004 เรื่อง Break-even ROAS) ไม่ใช่ตัวเลขมาตรฐานทั่วไปที่อาจไม่ตรงกับ Margin ของธุรกิจนั้น

### ข้อผิดพลาดที่พบบ่อย

- ใส่ Filter มากเกินไปจนผู้ใช้ต้องคลิกหลายครั้งก่อนเห็นข้อมูลที่ต้องการ ควรตั้งค่า Default Filter ที่เข้าใจง่ายที่สุดไว้ก่อน (เช่น Date Range = Last 30 days)
- ใช้ Threshold ของ Conditional Formatting แบบเดียวกันทุกแคมเปญ ทั้งที่ Objective ต่างกันมี Benchmark ต่างกัน (Conversion Campaign กับ Traffic Campaign ไม่ควรใช้ ROAS Threshold เดียวกัน)
- ไม่แยก View ระหว่าง Media Buyer และ Executive ทำให้ต้องยัดทุกอย่างในหน้าเดียวจนทั้งสองกลุ่มไม่พอใจ (ผู้บริหารบอกว่ารกเกินไป Media Buyer บอกว่าไม่ละเอียดพอ)

---

## Step 907: Automating Recurring Reports

### ทำไมต้อง Automate การส่ง Report

แม้ Dashboard จะอัปเดตอัตโนมัติ แต่ถ้าต้อง "เข้าไปเปิดดูเอง" ทุกครั้ง Stakeholder ที่ไม่มีเวลาจะไม่เปิดดูจริง การส่ง Report แบบ Push (Email/PDF) ตาม Schedule ช่วยให้ข้อมูลไปถึงมือ Stakeholder โดยไม่ต้องรอให้เขานึกขึ้นได้ว่าต้องเปิด Dashboard ดู

### ตั้งค่า Schedule Email จาก Looker Studio

```
Looker Studio Dashboard > File > Schedule email delivery

Recipients: [อีเมลลูกค้า/ผู้บริหาร]
Frequency: Weekly, ทุกวันจันทร์ 08:00
Format: PDF attachment ของหน้า Dashboard ปัจจุบัน
Message: เขียนสรุป Insight สั้นๆ 2-3 บรรทัดแทนอีเมลเปล่า
```

### ตั้งค่า Automated Email จาก Google Sheets ผ่าน Apps Script

```javascript
function sendWeeklyReport() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Summary_Dashboard');
  var reportUrl = SpreadsheetApp.getActiveSpreadsheet().getUrl();

  MailApp.sendEmail({
    to: 'client@email.com',
    subject: 'Weekly Cross-Platform Ads Report — ' + new Date().toLocaleDateString(),
    body: 'สวัสดีครับ/ค่ะ นี่คือ Report ประจำสัปดาห์ ดูรายละเอียดได้ที่: ' + reportUrl +
          '\n\nสรุปสั้นๆ: [เขียนสรุป Insight สัปดาห์นี้ที่นี่]'
  });
}
```

ตั้ง Trigger แบบเดียวกับ Step 903 ให้รันทุกวันจันทร์เช้าอัตโนมัติ

### การตั้ง Alert เมื่อตัวเลขผิดปกติ (Threshold Alert)

```javascript
function checkCPAAlert() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Summary_Dashboard');
  var currentCPA = sheet.getRange('B5').getValue();  // สมมติ CPA อยู่ที่ Cell B5
  var targetCPA = 150; // บาท ตาม Break-even ที่ตั้งไว้

  if (currentCPA > targetCPA * 1.3) {  // สูงกว่า Target 30%
    MailApp.sendEmail({
      to: 'team@agency.com',
      subject: '⚠️ CPA สูงเกิน Threshold — ต้องตรวจสอบด่วน',
      body: 'CPA ปัจจุบัน: ' + currentCPA + ' บาท (Target: ' + targetCPA + ' บาท)'
    });
  }
}
```

Alert แบบนี้ทำให้ทีมรู้ปัญหาเร็วกว่าการรอถึงวัน Report ประจำสัปดาห์ ควรตั้ง Trigger ให้รันทุกวัน (Daily) แทน Weekly สำหรับ Alert ประเภทนี้

### ข้อผิดพลาดที่พบบ่อย

- ตั้ง Automated Email แล้วไม่มีใครตรวจสอบว่า Script ยังทำงานอยู่หรือไม่ ถ้า API หมดอายุหรือ Error, Report จะไม่ถูกส่งโดยไม่มีใครรู้จนกว่าลูกค้าจะทวงถาม
- ส่ง Report อัตโนมัติแบบไม่มีคำอธิบาย Insight ประกอบ ทำให้ลูกค้าได้แต่ตัวเลขที่ต้องตีความเอง ลดคุณค่าของ Report ลงมาก (ควรมีคนตรวจและเขียนสรุปสั้นๆแนบเสมอ ไม่ใช่ปล่อยให้ระบบส่งอัตโนมัติ 100% โดยไม่มี Human Touch)
- ตั้ง Threshold Alert หลวมเกินไปหรือแน่นเกินไป ทำให้ Alert แจ้งเตือนบ่อยจนทีมเมินเฉย (Alert Fatigue) หรือไม่แจ้งเตือนเมื่อควรจะแจ้ง

---

## Step 908: การนำเสนอข้อมูลให้ Stakeholder ที่ไม่ใช่สาย Technical

### หลักการ Data Storytelling สำหรับสาย Marketing

Dashboard ที่ดีที่สุดจะไร้ประโยชน์ถ้าคนนำเสนอไม่สามารถเล่าเรื่องจากตัวเลขได้ หลักการสำคัญคือ **เริ่มจากคำถามทางธุรกิจ ไม่ใช่เริ่มจากตัวเลข** — แทนที่จะพูดว่า "ROAS สัปดาห์นี้ 2.8x เทียบกับ 3.1x สัปดาห์ก่อน" ให้พูดว่า "สัปดาห์นี้เราใช้เงินคุ้มค่าน้อยลงเล็กน้อยเมื่อเทียบกับสัปดาห์ก่อน สาเหตุหลักคือต้นทุนคลิกที่สูงขึ้นจากการแข่งขันในตลาดที่ดุเดือดขึ้นช่วงก่อนเทศกาล เราได้ปรับ Bid Strategy แล้วและคาดว่าจะเห็นผลดีขึ้นในสัปดาห์หน้า"

### โครงสร้างการนำเสนอที่ใช้ได้ผลจริง (SCR Framework)

| ขั้น | เนื้อหา |
|---|---|
| **Situation** | สรุปภาพรวมสถานการณ์ปัจจุบันสั้นๆ (ใช้งบเท่าไหร่ ได้ผลอย่างไร) |
| **Complication** | มีอะไรเปลี่ยนแปลงหรือท้าทายที่เกิดขึ้น (ตัวเลขขึ้น/ลง สาเหตุที่วิเคราะห์ได้) |
| **Resolution** | สิ่งที่ทีมได้ทำไปแล้วหรือจะทำต่อเพื่อแก้ปัญหา/ต่อยอดโอกาส |

### เทคนิคเลือก Metric ให้ตรงกับสิ่งที่ Stakeholder สนใจจริง

| กลุ่ม Stakeholder | สนใจ Metric แบบไหนมากที่สุด |
|---|---|
| เจ้าของธุรกิจ/CEO | Revenue, ROAS, กำไรสุทธิหลังหักค่าโฆษณา, การเติบโตเทียบเดือนก่อน |
| CFO/ฝ่ายการเงิน | CPA, Total Spend เทียบ Budget ที่อนุมัติ, Cash Flow Impact |
| CMO/ผู้จัดการ Marketing | Funnel Performance, Creative Performance, Market Share เทียบคู่แข่ง |
| ทีม Sales | จำนวน Lead ที่ได้ คุณภาพ Lead (Lead-to-Close Rate) |

การเตรียม Slide/Dashboard View ที่ต่างกันสำหรับแต่ละกลุ่มแม้จะดึงจากข้อมูลชุดเดียวกัน ทำให้การประชุมมีประสิทธิภาพมากขึ้นเพราะทุกคนเห็นสิ่งที่ตรงกับความสนใจของตัวเองก่อน

### ข้อผิดพลาดที่พบบ่อย

- นำเสนอด้วย Jargon ทางเทคนิคมากเกินไป (เช่น "Event Match Quality Score", "Attribution Window") กับผู้ฟังที่ไม่ใช่สาย Technical ทำให้เกิดความสับสนมากกว่าความเข้าใจ
- นำเสนอตัวเลขโดยไม่มีคำแนะนำ Action ต่อไป ทำให้ Stakeholder ฟังจบแล้วไม่รู้ว่าต้องทำอะไรต่อ
- ปกปิดหรือลดความสำคัญของตัวเลขที่ไม่ดี พยายามเน้นแต่ตัวเลขที่ดี ทำให้เสียความน่าเชื่อถือเมื่อลูกค้ารู้ความจริงทีหลัง ควรนำเสนอทั้งดีและไม่ดีอย่างตรงไปตรงมาพร้อม Action Plan

---

## Step 909: ข้อผิดพลาดที่พบบ่อยในการทำ Dashboard

### Vanity Metrics: ตัวเลขที่ดูดีแต่ไม่มีประโยชน์ในการตัดสินใจ

| Vanity Metric | ทำไมหลอกตา | Metric ที่ควรใช้แทน |
|---|---|---|
| Impressions/Reach สูง | บอกได้แค่ว่าคนเห็นมาก ไม่บอกว่าเห็นแล้วทำอะไรต่อ | CTR, Engagement Rate ที่บอกคุณภาพของ Reach |
| Total Likes/Comments บนโพสต์โฆษณา | ไม่สัมพันธ์กับ Conversion โดยตรงในหลายกรณี | Conversion Rate, CPA |
| จำนวน Click ทั้งหมด | คลิกไม่เท่ากับซื้อ อาจเป็น Click จาก Bot หรือคนที่ไม่ตั้งใจคลิก | Landing Page Conversion Rate, Cost per Add-to-Cart |
| Follower ที่เพิ่มขึ้นจากโฆษณา | ไม่บอกว่า Follower เหล่านั้นจะซื้อของหรือไม่ | Retention Rate ของ Follower กลุ่มนี้ในระยะยาว |

### ปัญหาการไม่มี Benchmark/Context

Dashboard ที่แสดงตัวเลขลอยๆโดยไม่มีอะไรให้เทียบ (Benchmark อุตสาหกรรม, ผลงานเดือนก่อน, Target ที่ตั้งไว้) ทำให้ผู้อ่านไม่รู้ว่าตัวเลขนั้น "ดีหรือแย่" หลักการแก้คือทุก Metric สำคัญบน Dashboard ต้องมีอย่างน้อยหนึ่งใน 3 สิ่งนี้ประกบอยู่เสมอ: **(1) เทียบช่วงก่อนหน้า (2) เทียบ Target ที่ตกลงกันไว้ (3) เทียบ Benchmark อุตสาหกรรม**

### ตารางสรุปข้อผิดพลาดของ Dashboard ที่พบบ่อยที่สุด

| ข้อผิดพลาด | ผลกระทบ | วิธีป้องกัน |
|---|---|---|
| เน้น Vanity Metrics เป็นตัวเลขหลัก | ตัดสินใจผิดพลาดเพราะตัวเลขไม่สัมพันธ์กับผลลัพธ์ทางธุรกิจจริง | เลือก Metric ที่เชื่อมกับ Revenue/Profit โดยตรงเป็นหลัก |
| ไม่มี Context/Benchmark | อ่านแล้วไม่รู้ว่าดีหรือแย่ | ใส่ % เปลี่ยนแปลงและ Target เทียบเสมอ |
| ใส่ข้อมูลมากเกินไปในหน้าเดียว | คนอ่านหาสิ่งที่สำคัญไม่เจอ | แยก View ตามผู้ฟัง (Step 905-906) |
| Data ไม่ Real-time/อัปเดตล่าช้า | Stakeholder ตัดสินใจจากข้อมูลเก่า | ตั้ง Automation ที่ดึงข้อมูลสม่ำเสมอ (Step 903, 907) |
| ไม่มีคนรับผิดชอบดูแล Dashboard ต่อเนื่อง | Dashboard พังหรือข้อมูลผิดโดยไม่มีใครแก้ | กำหนด Dashboard Owner ชัดเจนเช่นเดียวกับ Tracking Owner ใน Part 089 |
| Revenue นับซ้ำจากหลาย Attribution Model | ตัวเลขรวมเกินจริงเมื่อ Blend Facebook + TikTok Revenue ตรงๆ | ใช้ Revenue จาก GA4/Order Management เป็นตัวเลขกลางสำหรับภาพรวม |

### ข้อผิดพลาดเพิ่มเติม

- Design Dashboard ให้สวยเกินความจำเป็นจนใช้เวลา Setup นานเกินคุ้ม ทั้งที่ธุรกิจต้องการแค่คำตอบที่ชัดเจน ไม่ใช่ความสวยงามระดับ Award-winning
- ไม่ทดสอบ Dashboard บนอุปกรณ์ที่ Stakeholder จะใช้ดูจริง (เช่น เปิดบนมือถือแล้ว Layout พังเพราะออกแบบมาสำหรับจอใหญ่เท่านั้น)

### เช็คลิสต์ตรวจสุขภาพ Dashboard แบบรวดเร็วก่อนส่งให้ลูกค้าทุกครั้ง

1. เปิด Dashboard บนมือถือจริง 1 ครั้งเสมอ ไม่ใช่แค่ตรวจบน Desktop
2. เทียบตัวเลข Spend รวมบน Dashboard กับตัวเลขจริงใน Ads Manager ทั้งสองแพลตฟอร์ม ต้องตรงกันหรืออธิบายความต่างได้ (เช่น Attribution Window ต่างกัน)
3. ตรวจว่า Date Range ที่ตั้งเป็น Default ไม่ใช่ช่วงที่ล้าสมัย (เช่น ยังตั้งเป็นเดือนที่แล้วเพราะลืมอัปเดต)
4. ตรวจว่า Comparison Period แสดงถูกต้องและไม่ทับซ้อนกับ Date Range หลัก
5. ให้คนที่ไม่เคยเห็น Dashboard นี้มาก่อนลองอ่าน 1 นาทีแล้วถามว่าเข้าใจอะไรบ้าง เป็นวิธีทดสอบ Clarity ที่ตรงไปตรงมาที่สุด

---

## Case Study: เอเจนซี่ "AdBridge" เปลี่ยนภาพลักษณ์ด้วย Cross-Platform Dashboard

### สถานการณ์ก่อนแก้ไข

AdBridge เป็นเอเจนซี่ขนาดเล็กที่ดูแลลูกค้า 8 ราย แต่ละรายยิงทั้ง Facebook และ TikTok ทีมส่ง Report ให้ลูกค้าทุกวันศุกร์ผ่าน Excel ที่ต้องนั่งคัดลอกข้อมูลจากทั้งสอง Ads Manager ใช้เวลาเฉลี่ยรายละ 1.5 ชั่วโมง (รวม 12 ชั่วโมงต่อสัปดาห์สำหรับ 8 ราย) ลูกค้าหลายรายบ่นว่า Report มาช้าและตัวเลขบางครั้งดูไม่ตรงกับที่เห็นใน Ads Manager ของตัวเอง (เพราะ Attribution Window ตั้งไม่ตรงกัน) ทำให้ความน่าเชื่อถือของทีมลดลง มีลูกค้า 1 รายขู่จะเปลี่ยนเอเจนซี่

### การแก้ไขตาม Framework ใน Part นี้

1. สร้าง Google Sheets Template มาตรฐานตาม Step 902 ใช้กับลูกค้าทุกราย ลดเวลา Setup ต่อรายจากการเริ่มใหม่ทุกครั้ง
2. ตั้ง Apps Script ดึงข้อมูลจาก Facebook Marketing API และ TikTok Business API อัตโนมัติทุกเช้าวันจันทร์ (Step 903) ลดงาน Manual Copy-paste เกือบทั้งหมด
3. สร้าง Looker Studio Dashboard Template ที่มี Executive Summary View และ Campaign-Level View แยกกัน (Step 905-906) ใช้ Blended Data Source เดียวที่ Clone ไปใช้กับลูกค้าแต่ละรายได้เร็ว
4. ตั้ง Schedule Email ส่ง Dashboard PDF ให้ลูกค้าทุกวันจันทร์เช้าอัตโนมัติ พร้อมสรุป Insight สั้นๆที่ Media Buyer เขียนเพิ่มเอง (Step 907-908)
5. อบรมทีม Media Buyer ทุกคนให้ใช้ SCR Framework ตอนประชุมรายเดือนกับลูกค้า

### ผลลัพธ์หลังใช้ระบบใหม่ 2 เดือน

| ตัวชี้วัด | ก่อนแก้ | หลังแก้ |
|---|---|---|
| เวลาทำ Report ต่อลูกค้าต่อสัปดาห์ | ~1.5 ชั่วโมง | ~15 นาที (ตรวจสอบ + เขียนสรุป) |
| เวลาส่ง Report ถึงลูกค้า | วันศุกร์ (บางครั้งเลื่อนเป็นวันจันทร์) | ทุกวันจันทร์เช้าอัตโนมัติ ตรงเวลาเสมอ |
| ข้อร้องเรียนเรื่องตัวเลขไม่ตรงกัน | 3-4 ครั้ง/เดือน | 0 ครั้ง (หลังอธิบาย Attribution Window ต่างกันชัดเจนใน Dashboard) |
| ลูกค้าที่ขู่จะเปลี่ยนเอเจนซี่ | 1 ราย | ยกเลิกความคิด หลังเห็นความเปลี่ยนแปลงและต่อสัญญาเพิ่ม 6 เดือน |
| ความสามารถรับลูกค้าใหม่ของทีม | จำกัดเพราะเวลาส่วนใหญ่ใช้ทำ Report | รับลูกค้าเพิ่มได้ 2 รายโดยไม่ต้องเพิ่มคน |

บทเรียนสำคัญจาก Case นี้คือ **ระบบ Dashboard ที่ดีไม่ใช่แค่เรื่องความสวยงาม แต่เป็นการคืนเวลาให้ทีมได้ทำงานที่สร้างมูลค่าจริง (วิเคราะห์และปรับแคมเปญ) แทนงานคัดลอกข้อมูลซ้ำๆ และยังเป็นเครื่องมือสร้างความน่าเชื่อถือที่ส่งผลตรงต่อการรักษาลูกค้าไว้ในระยะยาว**

---

## Checklist ท้ายบท

- [ ] มี Google Sheets Template ที่รวมข้อมูล Facebook + TikTok ในโครงสร้างคอลัมน์เดียวกัน
- [ ] ตั้งค่าดึงข้อมูลอัตโนมัติ (Apps Script หรือ Connector) แทนการ Copy-paste มือทั้งหมด
- [ ] มี Looker Studio Dashboard ที่ Blend Facebook Ads + TikTok Ads + GA4 ผ่าน Join Key ที่ Consistent
- [ ] แยก View ชัดเจนระหว่าง Executive Summary และ Campaign/Creative-Level
- [ ] ทุก Metric สำคัญมี Context ประกบ (% เปลี่ยนแปลง, Target, หรือ Benchmark)
- [ ] ตั้ง Automated Email/Schedule Report ที่ส่งตรงเวลาสม่ำเสมอ
- [ ] มี Threshold Alert สำหรับตัวเลขผิดปกติที่ต้องรู้เร็วกว่า Report ประจำสัปดาห์
- [ ] ทีมใช้ SCR Framework หรือแนวทาง Data Storytelling ที่ชัดเจนตอนนำเสนอ
- [ ] ไม่มี Vanity Metrics เป็นตัวเลขหลักของ Dashboard
- [ ] มี Dashboard Owner รับผิดชอบดูแล Data Source และแก้ปัญหาต่อเนื่อง

---

## Step 910: Workshop — สร้าง Weekly Cross-Platform Report Template ฉบับสมบูรณ์

## Workshop / แบบฝึกหัด

### เป้าหมาย
สร้าง Weekly Cross-Platform Report Template ฉบับสมบูรณ์ 1 ชุด ที่ใช้ได้จริงกับธุรกิจ/ลูกค้าที่คุณดูแล

### ขั้นตอน

1. **สร้าง Google Sheets ตามโครงสร้าง Step 902** — สร้าง Tab Raw_Facebook, Raw_TikTok, Raw_GA4, Unified_Data, Summary_Dashboard ตามตัวอย่าง
2. **Export ข้อมูลจริง 7-14 วันล่าสุด** จากทั้งสองแพลตฟอร์ม วางลง Raw Tab ตามโครงสร้างคอลัมน์มาตรฐาน
3. **เขียนสูตรรวมข้อมูลและคำนวณ ROAS/CPA/CTR/CPM** ใน Unified_Data ตามตัวอย่างใน Step 902
4. **สร้าง Looker Studio Dashboard เชื่อมกับ Google Sheets นี้** เป็น Data Source ทำ Executive Summary View 1 หน้าตามโครงสร้างใน Step 905
5. **เพิ่ม Conditional Formatting และ Trend Indicator** ตาม Threshold ที่เหมาะกับธุรกิจ
6. **เขียนสรุป Insight แบบ SCR Framework** ยาว 5-8 บรรทัดจากข้อมูลจริงที่ได้ ฝึกเล่าเรื่องจากตัวเลขไม่ใช่แค่รายงานตัวเลข
7. **(ถ้าเป็นไปได้) ตั้ง Schedule Email** ส่ง Dashboard นี้ให้ตัวเองหรือทีมทุกสัปดาห์เพื่อทดสอบ Automation จริง

### เกณฑ์ความสำเร็จ
Dashboard และ Sheet ที่สร้างสามารถส่งให้เจ้าของธุรกิจ/ลูกค้าดูได้จริงโดยไม่ต้องอธิบายเพิ่มว่าตัวเลขไหนดูตรงไหน และมีการสรุป Insight ที่ชัดเจนพร้อม Action ต่อไป ไม่ใช่แค่ตัวเลขลอยๆ

### ตัวอย่างสรุป Insight แบบ SCR ที่ใช้เป็นต้นแบบได้

```
Situation: สัปดาห์นี้ใช้งบรวม 45,000 บาท (Facebook 28,000 / TikTok 17,000)
ได้ Conversion รวม 62 รายการ ROAS เฉลี่ย 3.1x

Complication: ROAS ลดลงจาก 3.6x สัปดาห์ก่อน สาเหตุหลักมาจาก CPM ที่สูงขึ้น
15% บน Facebook ช่วงก่อนเทศกาล ทำให้ต้นทุนต่อ Conversion สูงขึ้นตามไปด้วย
TikTok ยังทรงตัวได้ดีกว่าเพราะการแข่งขันในกลุ่มนี้ยังไม่หนาแน่นเท่า

Resolution: ทีมได้ปรับ Budget Allocation ชั่วคราวโดยเพิ่มสัดส่วนงบให้ TikTok
มากขึ้น 20% ในสัปดาห์หน้า และจะเริ่มทดสอบ Creative ใหม่บน Facebook เพื่อ
สู้กับ CPM ที่สูงขึ้น คาดว่า ROAS จะกลับมาใกล้เคียงเดิมภายใน 2 สัปดาห์
```

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ปิดวงจรสำคัญของ Section J ในส่วนของการ "แสดงผล" ข้อมูลที่ Part 089 ทำให้ Comparable และ Part 090 ทำให้แม่นยำ — ตอนนี้คุณมีทั้ง Google Sheets Template สำหรับธุรกิจที่เริ่มต้น และ Looker Studio Dashboard ระดับมืออาชีพสำหรับธุรกิจที่ต้องการภาพที่สมบูรณ์กว่า พร้อมหลักการนำเสนอที่ทำให้ตัวเลขกลายเป็นการตัดสินใจได้จริง ไม่ใช่แค่ตัวเลขสวยๆบนหน้าจอ

คำถามที่ยังไม่ได้ตอบเต็มที่ในสามพาร์ทที่ผ่านมาคือ **"เมื่อรู้ผลงานของทั้งสองแพลตฟอร์มแล้ว ควรจัดสรรงบประมาณอย่างไรให้ได้ผลตอบแทนสูงสุด"** — Part 092 จะพาคุณไปสู่ **Cross-Platform Budget Allocation** ใช้ข้อมูลและ Dashboard ที่สร้างไว้ในนี้เป็นพื้นฐานสำคัญของการตัดสินใจจัดงบระหว่าง Facebook และ TikTok อย่างมีหลักการ ไม่ใช่ความรู้สึก

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Looker Studio Help Center — หมวด "Blend data" และ "Schedule email delivery"
- Google Apps Script Documentation — หมวด "UrlFetchApp" และ "Triggers"
- Meta for Developers — หมวด "Marketing API: Insights"
- TikTok for Business Developers — หมวด "Reporting API"
- Google Sheets Help Center — หมวด "QUERY function" และ "Data validation"
- หนังสือ "Storytelling with Data" โดย Cole Nussbaumer Knaflic — อ้างอิงหลักการ Data Storytelling ที่ใช้ในวงการ Business Intelligence อย่างกว้างขวาง
