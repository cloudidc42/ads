# Part 013: Facebook Pixel และ Conversions API เบื้องต้น

**Section:** B — Facebook Ads Ecosystem Fundamentals
**Step ที่ครอบคลุม:** Step 121–130 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 5–7 ชั่วโมง (รวมการลงมือทำ Workshop จริงบนเว็บไซต์ของตัวเองหรือเว็บทดสอบ)

Part นี้คือจุดเปลี่ยนสำคัญของหลักสูตร เพราะทุกอย่างที่เรียนมาก่อนหน้านี้ (Business Manager, Ad Account, Page) เป็นแค่ "โครงสร้างบ้าน" แต่ Pixel และ Conversions API คือ "ระบบประสาท" ที่ทำให้ Facebook รู้ว่าใครทำอะไรบนเว็บไซต์ของเราบ้าง ถ้าไม่มีระบบนี้หรือมีแต่ตั้งค่าผิด ต่อให้ครีเอทีฟดีแค่ไหน งบเยอะแค่ไหน อัลกอริทึมของ Facebook ก็จะ "ตาบอด" และไม่สามารถหาคนที่มีโอกาสซื้อจริงให้เราได้ นักยิงแอดที่ไม่เข้าใจ Pixel/CAPI คือนักยิงแอดที่ทำงานแบบเดา ไม่ใช่แบบมีข้อมูล

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Facebook Pixel คืออะไร ทำงานอย่างไร** — หลักการพื้นฐานของ tracking pixel, cookie, และการส่งข้อมูล event กลับไปที่ Meta
2. **สร้าง Pixel และเชื่อมกับ Ad Account** — ขั้นตอนสร้าง Pixel ใน Events Manager และผูกกับ Business Manager/Ad Account
3. **Standard Events ทั้งหมดและความหมาย** — รายการ Standard Event ของ Meta ทุกตัว พร้อมความหมายและการใช้งานจริง
4. **Custom Conversions และการใช้งาน** — สร้างกฎวัดผลจาก URL/Event โดยไม่ต้องแก้โค้ด
5. **Conversions API (CAPI) คืออะไร ทำไมสำคัญขึ้นหลัง iOS14** — พื้นฐานการส่งข้อมูลฝั่ง Server และเหตุผลเชิงนโยบาย privacy
6. **ความแตกต่างระหว่าง Browser Pixel และ Server-Side CAPI** — จุดแข็ง จุดอ่อน และทำไมต้องใช้ทั้งสองคู่กัน
7. **Event Match Quality และการปรับปรุงคุณภาพข้อมูล** — วิธีอ่านคะแนน EMQ และแนวทางเพิ่มคะแนน
8. **Aggregated Event Measurement (AEM) เบื้องต้น** — ระบบวัดผลแบบรวมสำหรับ iOS14+ และการจัดลำดับความสำคัญ Event
9. **การ Debug Pixel ด้วย Meta Pixel Helper** — เครื่องมือตรวจสอบ Pixel แบบ real-time บน Chrome
10. **Workshop: ติดตั้งและตรวจสอบ Pixel แบบสมบูรณ์** — ลงมือติดตั้งและตรวจทุกจุดจนพร้อมใช้งานจริง

---

## Step 121: Facebook Pixel คืออะไร ทำงานอย่างไร

### นิยามที่ต้องเข้าใจให้แม่น

Facebook Pixel คือ **โค้ด JavaScript** ชิ้นเล็ก ๆ ที่เราวางไว้ในทุกหน้าของเว็บไซต์ (หรือแอป ผ่าน SDK) หน้าที่ของมันคือ "ส่งสัญญาณ" กลับไปที่เซิร์ฟเวอร์ของ Meta ทุกครั้งที่มีคนทำกิจกรรมบางอย่าง เช่น เข้าเว็บ, ดูสินค้า, กดใส่ตะกร้า, หรือกดซื้อสำเร็จ

พูดง่าย ๆ คือ Pixel ทำ 3 อย่างหลัก:

1. **ระบุตัวบุคคล (Matching):** เชื่อมโยง browser ของคนที่กำลังเข้าเว็บ กับบัญชี Facebook ของเขา ผ่านการจับคู่ cookie (`fbp`), ค่า click ID (`fbc`), และข้อมูลอื่น ๆ ที่ browser ส่งมา
2. **บันทึกพฤติกรรม (Event Tracking):** ส่งข้อมูลว่า "คนนี้ทำอะไร" เช่น `PageView`, `ViewContent`, `AddToCart`, `Purchase`
3. **ป้อนข้อมูลให้ Machine Learning:** ข้อมูล Event ที่ Pixel ส่งกลับมาคือ "อาหาร" ของอัลกอริทึม Facebook ที่ใช้หาคนกลุ่มใหม่ที่มีพฤติกรรมคล้ายคนที่ซื้อของเราแล้ว (Lookalike, Advantage+ Audience)

### กลไกทางเทคนิคแบบง่าย

เมื่อ browser โหลดหน้าเว็บที่มี Pixel ฝังอยู่ ลำดับการทำงานคร่าว ๆ คือ:

```
[User เปิดเว็บ] 
   → [Browser โหลด Pixel base code] 
   → [Pixel สร้าง/อ่าน cookie ชื่อ _fbp] 
   → [ถ้ามาจากคลิกโฆษณา จะมี query parameter fbclid → แปลงเป็น cookie _fbc]
   → [Pixel ยิง event PageView ไปที่ Facebook (ผ่าน request ไปยัง domain facebook.com/tr)]
   → [Facebook รับข้อมูล → จับคู่กับ Facebook User ID (ถ้าเป็นไปได้) → บันทึกเข้าระบบ]
```

สิ่งที่ส่งไปจริง ๆ คือ HTTP request ไปที่ endpoint ประมาณนี้ (ทำผ่าน JavaScript อัตโนมัติ ไม่ต้องยิงเอง):

```
https://www.facebook.com/tr/?id=PIXEL_ID&ev=PageView&dl=...&rl=...&if=false&ts=...&fbp=fb.1.169...&fbc=fb.1.169...
```

คุณสามารถเห็น request นี้ได้จริงในแท็บ Network ของ Chrome DevTools โดย filter คำว่า `tr?` หรือ `facebook.com/tr`

### จุดที่มือใหม่เข้าใจผิดบ่อย

- **เข้าใจผิดว่า Pixel คือ "ตัวติดตามคน"** — ที่จริง Pixel ติดตาม *เหตุการณ์* (event) บน *เบราว์เซอร์* ไม่ใช่ตัวบุคคลโดยตรง การจับคู่กับบุคคลทำผ่านกระบวนการ probabilistic/deterministic matching ของ Meta อีกที
- **เข้าใจผิดว่ามี Pixel แล้วแอดจะดีขึ้นทันที** — Pixel ต้องมี "ปริมาณ Event" ที่พอเพียง (Meta แนะนำอย่างน้อย ~50 Optimization Event ต่อสัปดาห์ต่อ Ad Set) จึงจะออกจาก Learning Phase ได้ดี
- **เข้าใจผิดว่า 1 เว็บไซต์ควรมีหลาย Pixel** — โดยทั่วไปควรมี **Pixel เดียวต่อธุรกิจ** เพื่อให้ข้อมูลสะสมอยู่ในที่เดียว ไม่กระจัดกระจาย (ยกเว้นกรณีเอเจนซี่บริหารหลายลูกค้าที่ต้องแยกจริง ๆ)
- **ลืมว่า Pixel ถูก Browser บล็อกได้** — Safari (ITP), Firefox (ETP), Ad Blocker และ iOS14+ ล้วนบล็อกหรือจำกัดการทำงานของ cookie-based tracking ซึ่งเป็นเหตุผลที่ Step 125 จะพูดถึง CAPI

### ทำไมต้องเรียน Step นี้ก่อนเรื่องอื่น

เพราะทุก Feature ขั้นสูงของ Facebook Ads ไม่ว่าจะเป็น Custom Audience จาก Website, Lookalike Audience, Advantage+ Shopping, Conversion Optimization, Value Optimization — **ทั้งหมดพึ่งพา Pixel เป็นฐาน** ถ้าฐานนี้ไม่แน่น ทุกอย่างข้างบนจะสร้างบนทรายทั้งหมด

---

## Step 122: สร้าง Pixel และเชื่อมกับ Ad Account

### ขั้นตอนสร้าง Pixel ผ่าน Events Manager (เมนูปัจจุบันปี 2026)

1. เข้า **Meta Business Suite** หรือ **Business Manager** → https://business.facebook.com
2. ไปที่เมนู **Events Manager** (ค้นหาผ่านช่องค้นหาบนสุด หรือ All Tools → Measure & Report → Events Manager)
3. คลิก **Connect Data Sources** (ปุ่มสีเขียว มุมบนซ้ายของหน้า Events Manager)
4. เลือก **Web** → คลิก **Get Started**
5. เลือกวิธีเชื่อมต่อ:
   - **Meta Pixel** (ใส่โค้ดเอง หรือผ่าน Partner Integration เช่น Shopify, WordPress)
   - **Conversions API** (ถ้าจะทำฝั่ง Server เลย)
   - แนะนำมือใหม่: เลือก **Meta Pixel** ก่อน แล้วค่อยเพิ่ม CAPI ทับในขั้นต่อไป (Step 125–126)
6. ตั้งชื่อ Pixel — **ควรตั้งชื่อตามธุรกิจ ไม่ใช่ชื่อสินค้าเดียว** เช่น `ABC-Cosmetics-MainPixel` เพราะ Pixel นี้จะใช้ยาวตลอดอายุธุรกิจ
7. ใส่ URL เว็บไซต์ (ถ้ามี) → ระบบจะพยายามสแกนอัตโนมัติว่าเว็บใช้ Partner Platform ไหน เช่น Shopify, WooCommerce, Wix เพื่อเสนอวิธีติดตั้งแบบ 1-Click
8. กด **Continue** → ระบบจะสร้าง **Pixel ID** (เลข 15–16 หลัก) ให้ทันที เช่น `1234567890123456`

### การผูก Pixel กับ Ad Account

Pixel ไม่ได้ "อยู่ใน" Ad Account แต่อยู่ใน **Business Manager** และถูก **แชร์ (Share)** ให้ Ad Account ใช้งานได้ ขั้นตอนตรวจสอบ/ผูกสิทธิ์:

1. Business Settings (business.facebook.com/settings) → **Data Sources** → **Pixels**
2. เลือก Pixel ที่สร้างไว้ → แท็บ **Assign Partners** หรือ **Assign Ad Accounts**
3. ติ๊กเลือก Ad Account ที่ต้องการให้ใช้ Pixel นี้ในการ Optimize แคมเปญ
4. กำหนดสิทธิ์ผู้ใช้งาน (Standard Access / Advanced Access / Manage) ให้พนักงานหรือทีมที่ดูแล Pixel

**ข้อควรระวังสำคัญ:** ถ้า Ad Account ไม่ได้ถูก Assign ให้เข้าถึง Pixel ตัวนี้ เวลาไปสร้างแคมเปญ Conversion จะไม่เห็น Pixel นี้ในรายการ dropdown เลือก Conversion Location — เป็นปัญหาที่มือใหม่งงบ่อยมาก

### เชื่อม Pixel เข้ากับ Domain ที่ Verify แล้ว

ตั้งแต่ iOS14 เป็นต้นมา Meta บังคับให้ธุรกิจทำ **Domain Verification** (เรียนละเอียดใน Part 011 Step 108) ก่อน เพราะ **Priority Access** ของ 8 Event สำคัญ (Step 145) จะขึ้นกับ Domain ที่ Verify แล้วเท่านั้น ไม่ใช่ Pixel เดี่ยว ๆ อีกต่อไป — นี่คือการเปลี่ยนแปลงสถาปัตยกรรมที่สำคัญมากหลัง iOS14 ที่ต้องจำให้ได้

### Case Study สั้น: ธุรกิจที่ Pixel "หาย" ตอน Scale

ร้านเสื้อผ้าออนไลน์ทีมหนึ่งใช้ Pixel เดียวมาตลอด แต่เมื่อเปลี่ยน Web Developer ทีมใหม่ไปติดตั้งเว็บใหม่และ **สร้าง Pixel ใหม่โดยไม่รู้ว่ามีของเดิมอยู่แล้ว** ผลคือข้อมูล Purchase Event ที่สะสมมา 2 ปีถูกทิ้งไปเปล่า ๆ เพราะแคมเปญใหม่ต้องเริ่ม Learning Phase จาก Pixel เปล่าใหม่ทั้งหมด บทเรียนคือ: **ก่อนสร้าง Pixel ใหม่ ให้เช็ค Events Manager ก่อนเสมอว่ามี Pixel เดิมของ Business Manager นี้อยู่หรือไม่**

---

## Step 123: Standard Events ทั้งหมดและความหมาย

Meta กำหนด **Standard Event** ไว้เป็นชุดคำสั่งมาตรฐานที่อัลกอริทึมเข้าใจได้ทันทีโดยไม่ต้องตั้งค่าเพิ่ม (ต่างจาก Custom Event ที่เราตั้งชื่อเองแล้วต้อง map เอง) รายการทั้งหมดที่ใช้บ่อยและควรรู้ความหมายให้แม่น:

| Event Name | โค้ดเรียก (fbq) | ใช้เมื่อไหร่ |
|---|---|---|
| PageView | `fbq('track', 'PageView')` | ทุกหน้าเว็บโหลดสำเร็จ (มักอยู่ใน Base Code) |
| ViewContent | `fbq('track', 'ViewContent')` | ลูกค้าดูหน้าสินค้า/บริการ |
| Search | `fbq('track', 'Search')` | ลูกค้าค้นหาสินค้าในเว็บ |
| AddToCart | `fbq('track', 'AddToCart')` | กดเพิ่มสินค้าลงตะกร้า |
| AddToWishlist | `fbq('track', 'AddToWishlist')` | กดบันทึก/ถูกใจสินค้า |
| InitiateCheckout | `fbq('track', 'InitiateCheckout')` | เริ่มกระบวนการชำระเงิน |
| AddPaymentInfo | `fbq('track', 'AddPaymentInfo')` | กรอกข้อมูลการชำระเงินสำเร็จ |
| Purchase | `fbq('track', 'Purchase', {value: 990, currency: 'THB'})` | ซื้อสำเร็จ (**ต้องมี value/currency เสมอ**) |
| Lead | `fbq('track', 'Lead')` | กรอกฟอร์มสนใจ/ขอข้อมูล |
| CompleteRegistration | `fbq('track', 'CompleteRegistration')` | ลงทะเบียนสมาชิก/สมัครเสร็จ |
| Contact | `fbq('track', 'Contact')` | ติดต่อธุรกิจ (โทร/แชท/อีเมล) |
| CustomizeProduct | `fbq('track', 'CustomizeProduct')` | ปรับแต่งสินค้าก่อนซื้อ |
| Donate | `fbq('track', 'Donate')` | บริจาคเงิน |
| FindLocation | `fbq('track', 'FindLocation')` | ค้นหาสาขา/หน้าร้าน |
| Schedule | `fbq('track', 'Schedule')` | จองนัด/จองเวลา |
| StartTrial | `fbq('track', 'StartTrial')` | เริ่มทดลองใช้ฟรี |
| SubmitApplication | `fbq('track', 'SubmitApplication')` | สมัครงาน/สมัครสมาชิกโครงการ |
| Subscribe | `fbq('track', 'Subscribe', {value: 299, currency: 'THB', predicted_ltv: 3600})` | สมัครสมาชิกแบบชำระเงินต่อเนื่อง |

### หลักการเลือกใช้ Event ให้ตรงกับ Funnel

- **TOF (Top of Funnel):** PageView, ViewContent, Search
- **MOF (Middle of Funnel):** AddToCart, InitiateCheckout, Lead
- **BOF (Bottom of Funnel):** Purchase, CompleteRegistration, Subscribe

ข้อผิดพลาดที่พบบ่อยที่สุดคือ **ใส่ Event ผิดตำแหน่ง** เช่น ยิง `Purchase` ตอนลูกค้ากดปุ่ม "สั่งซื้อ" (ที่ยังไม่ได้ชำระเงินจริง) แทนที่จะยิงตอนหน้า Thank You Page ที่ยืนยันว่าออเดอร์สำเร็จแล้วจริง ๆ — ทำให้ข้อมูล Purchase เพี้ยนและ ROAS ที่รายงานในระบบไม่ตรงกับยอดขายจริง

### พารามิเตอร์เสริมที่ควรใส่ทุกครั้งที่เป็นไปได้

Standard Event รับพารามิเตอร์เสริม (Custom Data Parameters) ที่ช่วยให้ Optimize ได้ดีขึ้นมาก เช่น:

```javascript
fbq('track', 'Purchase', {
  value: 1590.00,
  currency: 'THB',
  content_ids: ['SKU12345', 'SKU12399'],
  content_type: 'product',
  num_items: 2,
  contents: [
    {id: 'SKU12345', quantity: 1, item_price: 990.00},
    {id: 'SKU12399', quantity: 1, item_price: 600.00}
  ]
});
```

การใส่ `content_ids` และ `contents` แบบนี้ทำให้ระบบ Dynamic Ads / Catalog Sales (Part 027) ทำงานได้แม่นยำขึ้นมาก เพราะ Facebook รู้ว่าสินค้าตัวไหนขายดี แล้วนำไปทำ Retargeting แบบ Dynamic ได้ทันที

---

## Step 124: Custom Conversions และการใช้งาน

### Custom Conversion คืออะไร ต่างจาก Custom Event อย่างไร

หลายคนสับสนคำว่า "Custom Event" กับ "Custom Conversion" — สองอย่างนี้ไม่เหมือนกัน:

- **Custom Event:** คือ Event ที่เราตั้งชื่อเองในโค้ด เช่น `fbq('trackCustom', 'ReadBlogPost')` ต้องแก้โค้ดจริง
- **Custom Conversion:** คือการสร้าง "กฎ" (Rule) ขึ้นมาจาก URL หรือ Event ที่มีอยู่แล้ว **โดยไม่ต้องแก้โค้ดเว็บไซต์เลย** ทำผ่านหน้า Events Manager ล้วน ๆ

Custom Conversion เหมาะมากสำหรับสถานการณ์ที่ **Developer ไม่พร้อมแก้โค้ด** แต่เราต้องการวัดผลบางอย่างด่วน ๆ เช่น "คนที่เข้าหน้า `/thankyou-order` ถือว่าซื้อสำเร็จ"

### ขั้นตอนสร้าง Custom Conversion

1. Events Manager → เลือก Pixel/Dataset ที่ใช้งาน
2. แท็บ **Custom Conversions** → คลิก **Create Custom Conversion**
3. เลือก **Data Source** (Pixel ที่จะอ้างอิง)
4. เลือกกฎ (Rule) เช่น:
   - **URL contains** `/thankyou`
   - **URL equals** `https://mystore.com/order-success`
   - หรืออิงจาก Event ที่มีอยู่ เช่น `PageView` + URL condition
5. เลือก **Category** ให้ตรงกับความหมาย (Purchase, Lead, CompleteRegistration ฯลฯ) — Category นี้สำคัญเพราะมีผลต่อการเลือกใน Priority Event (Step 145)
6. ตั้งชื่อให้ชัดเจน เช่น `CC-Purchase-ThankYouPage`
7. (ถ้าต้องการ) ใส่ **Value** คงที่ เช่น มูลค่าเฉลี่ยต่อออเดอร์ กรณีเว็บไม่ส่ง dynamic value มาให้

### ข้อจำกัดที่ต้องรู้

- Custom Conversion จะเริ่มเก็บข้อมูล **ตั้งแต่วันที่สร้าง** เท่านั้น ไม่ดึงข้อมูลย้อนหลัง
- 1 Business Manager มี Custom Conversion ได้จำกัดจำนวน (โดยทั่วไปหลักร้อยต่อ Pixel) ควรตั้งอย่างมีระบบ ไม่สร้างมั่ว ๆ
- Custom Conversion **ไม่แม่นยำเท่า Standard Event ที่ฝังในโค้ดโดยตรง** เพราะอิงจาก URL/PageView เป็นหลัก ถ้า URL เปลี่ยนแปลงในอนาคต (เช่น Developer ปรับ URL structure) กฎเดิมจะพังทันทีโดยไม่มีการเตือนอัตโนมัติ

### เมื่อไหร่ควรใช้ Custom Conversion แทน Standard Event

| สถานการณ์ | แนะนำ |
|---|---|
| มี Developer พร้อมแก้โค้ดได้ | ใช้ Standard Event ฝังโค้ดตรง |
| ต้องการวัดผลด่วนวันนี้ ไม่มี Dev | ใช้ Custom Conversion จาก URL |
| ต้องการความแม่นยำสูงสุดสำหรับ Optimize งบใหญ่ | Standard Event + CAPI เท่านั้น |
| ทดสอบ Landing Page ใหม่ชั่วคราว | Custom Conversion เพียงพอ |

---

## Step 125: Conversions API (CAPI) คืออะไร ทำไมสำคัญขึ้นหลัง iOS14

### นิยาม

**Conversions API (CAPI)** คือวิธีส่งข้อมูล Event เดียวกับที่ Pixel ส่ง แต่ส่งจาก **เซิร์ฟเวอร์ของธุรกิจเราเอง** ตรงไปยัง Meta โดยไม่ผ่าน Browser ของลูกค้า พูดง่าย ๆ คือ Pixel ส่งจาก "ฝั่งลูกค้า" (Client-Side) ส่วน CAPI ส่งจาก "ฝั่งเรา" (Server-Side)

### เหตุผลเชิงเทคนิคที่ทำให้ CAPI สำคัญขึ้นมาก

1. **Apple ITP (Intelligent Tracking Prevention) บน Safari** — บล็อก third-party cookie เกือบทั้งหมด ทำให้ Pixel บน Safari แม่นยำต่ำมาก
2. **iOS 14.5+ App Tracking Transparency (ATT)** — ผู้ใช้ iOS ส่วนใหญ่กด "Ask App Not to Track" ทำให้แอปต่าง ๆ (รวม Facebook App) ไม่สามารถส่งข้อมูลระบุตัวบุคคลได้เต็มที่เหมือนเดิม แม้ Step นี้เกี่ยวกับ Pixel เว็บโดยตรงมากกว่า แต่ผลกระทบภาพรวมของ "การเห็นข้อมูลน้อยลง" ก็ทำให้ธุรกิจต้องหาทางเสริมความแม่นยำทุกทาง
3. **Ad Blocker และ Browser Extension** — บล็อก request ที่ยิงไปยัง `facebook.com/tr` โดยตรง แต่ **ไม่สามารถบล็อก request ที่ยิงจาก Server ไป Server ได้** เพราะไม่มีการรันโค้ดบน browser ของผู้ใช้เลย
4. **Ad Blocker ระดับเน็ตเวิร์ก (Pi-hole, DNS-based)** — บล็อกโดเมนของ Facebook ที่อุปกรณ์ แต่ก็ยังไม่กระทบ Server-to-Server

ผลคือ: ธุรกิจที่ใช้ **Pixel เพียงอย่างเดียว** อาจสูญเสียข้อมูล Event จริงไป 20–40% (ตัวเลขแตกต่างตามอุตสาหกรรมและกลุ่มลูกค้า) ซึ่งหมายความว่า Facebook มองเห็นแค่ 60–80% ของยอดขายจริง แล้วเอาข้อมูลที่ไม่ครบนี้ไปเรียนรู้ (Learning) — ผลลัพธ์คือ Optimize ได้ไม่เต็มประสิทธิภาพ

### CAPI ทำงานอย่างไรในภาพรวม (ไม่ต้องเขียนโค้ดเองเสมอไป)

มี 3 วิธีหลักในการติดตั้ง CAPI:

1. **Partner Integration** (ง่ายที่สุด) — เช่น Shopify, WooCommerce ผ่าน Plugin ที่เชื่อม CAPI ให้อัตโนมัติแบบ 1-Click ผ่านหน้า Events Manager → Partner Integration
2. **Conversions API Gateway** — เครื่องมือของ Meta ที่ช่วยตั้งค่า Server-Side โดยไม่ต้องเขียนโค้ดเยอะ เหมาะกับธุรกิจ SME ที่มี Developer พื้นฐาน
3. **Direct Integration ด้วย API เอง** — เขียนโค้ดเรียก Meta Conversions API endpoint ตรง เหมาะกับทีมที่มี Developer เต็มรูปแบบ

ตัวอย่างโครงสร้างข้อมูล (JSON) ที่ระบบ Server ของเราจะยิงไปที่ Meta Conversions API:

```json
{
  "data": [
    {
      "event_name": "Purchase",
      "event_time": 1758870000,
      "action_source": "website",
      "event_source_url": "https://mystore.com/checkout/success",
      "user_data": {
        "em": ["a1b2c3d4e5f6...hashed_email"],
        "ph": ["f1e2d3c4b5a6...hashed_phone"],
        "client_ip_address": "203.0.113.42",
        "client_user_agent": "Mozilla/5.0 (iPhone; CPU iPhone OS 17_0 like Mac OS X)...",
        "fbc": "fb.1.1758869000123.AbCdEfGhIj",
        "fbp": "fb.1.1758860000456.987654321"
      },
      "custom_data": {
        "currency": "THB",
        "value": 1590.00,
        "content_ids": ["SKU12345", "SKU12399"],
        "content_type": "product"
      }
    }
  ],
  "access_token": "EAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```

จุดสำคัญที่ต้องสังเกต:
- `em` และ `ph` (email, phone) ต้องถูก **hash ด้วย SHA-256** เสมอ ห้ามส่งข้อมูล plaintext ไปตรง ๆ (เรื่อง privacy/compliance)
- `fbc` และ `fbp` คือค่าเดียวกันกับที่ Pixel สร้างไว้ใน cookie ของ browser — นี่คือจุดเชื่อมสำคัญที่ทำให้ Meta รู้ว่า Server Event นี้กับ Browser Event เป็นคนเดียวกัน (เกี่ยวกับ Deduplication ใน Step 147)
- `access_token` ต้องขอจากหน้า Events Manager → Settings → Conversions API → Generate Access Token และเก็บเป็นความลับสุดขีด (ห้ามฝังใน front-end code)

### สิ่งที่ต้องจำ

CAPI **ไม่ได้มาแทน Pixel** แต่ทำงาน **คู่กัน** เสริมความสมบูรณ์ของข้อมูล — รายละเอียดเปรียบเทียบเจาะลึกอยู่ใน Step 126

---

## Step 126: ความแตกต่างระหว่าง Browser Pixel และ Server-Side CAPI

### ตารางเปรียบเทียบ

| มิติ | Browser Pixel | Server-Side CAPI |
|---|---|---|
| ตำแหน่งที่ส่งข้อมูล | จาก Browser ของลูกค้า | จาก Server ของธุรกิจเรา |
| ความเสี่ยงถูกบล็อก | สูง (Ad Blocker, ITP, Safari) | ต่ำมาก (Server-to-Server) |
| ความเร็วในการติดตั้ง | เร็ว วางโค้ดบรรทัดเดียวก็ใช้ได้ | ช้ากว่า ต้องมี Developer หรือ Partner Integration |
| ข้อมูลที่ได้ | Client-side signal (device, browser, cookie) | ข้อมูลจากระบบหลังบ้านจริง (order database) |
| ความแม่นยำของ Value/Currency | ขึ้นกับ front-end ส่งถูกไหม | แม่นยำสูงเพราะมาจากฐานข้อมูลออเดอร์จริง |
| เหมาะกับ | เว็บไซต์ทั่วไป, Landing Page เร็ว ๆ | E-commerce ที่มี Order Management System |
| ปัญหาเรื่อง Data Duplication | ไม่มีถ้าใช้ตัวเดียว | ต้องทำ Deduplication กับ Pixel (Step 147) |

### ทำไม Meta แนะนำให้ใช้ "คู่กัน" ไม่ใช่เลือกอย่างใดอย่างหนึ่ง

Meta เรียกแนวทางนี้ว่า **"Redundancy"** — คือถ้า Pixel จับ Event ไม่ได้ (เพราะถูกบล็อก) CAPI ก็ยังจับได้อยู่ และในทางกลับกัน ถ้า Server มีปัญหาชั่วคราว Pixel ก็ยังทำงานสำรองอยู่ Meta ยืนยันในเอกสารทางการว่าธุรกิจที่ใช้ทั้งสองคู่กันมักเห็น **Event Match Quality สูงขึ้น และ Cost per Result ลดลง** เมื่อเทียบกับใช้ Pixel เดี่ยว ๆ

### กรณีที่ CAPI สำคัญเป็นพิเศษ

- ธุรกิจที่ลูกค้าส่วนใหญ่ใช้ **iPhone/Safari** (กลุ่มลูกค้าไทยที่ใช้ iPhone มีสัดส่วนสูงมากในกลุ่มกำลังซื้อสูง)
- ธุรกิจที่มี Sales Cycle ยาว หรือปิดการขายผ่าน **Line/โทรศัพท์** (Offline Conversion) ซึ่ง Pixel จับไม่ได้เลยเพราะไม่มีการกระทำบนเว็บ ต้องส่งย้อนกลับผ่าน CAPI หรือ Offline Conversions API
- ธุรกิจที่มีระบบ CRM/e-Commerce Backend ที่รู้ยอดขายจริงแม่นยำกว่า front-end (เช่น กรณีลูกค้าคืนสินค้า ระบบยอด Purchase ที่ front-end ส่งไปแล้วจะไม่ถูก "หัก" ออกอัตโนมัติ แต่ CAPI จากระบบหลังบ้านสามารถส่ง event เพิ่มเพื่อ mapping ข้อมูลให้แม่นยำกว่าได้)

---

## Step 127: Event Match Quality และการปรับปรุงคุณภาพข้อมูล

### EMQ คืออะไร

**Event Match Quality (EMQ)** คือคะแนน 0–10 ที่ Meta ให้กับ Event แต่ละตัวที่เรายิงเข้าไป (ดูได้ใน Events Manager → เลือก Event → คอลัมน์ Event Match Quality หรือคลิกเข้าไปดูรายละเอียด) คะแนนนี้สะท้อนว่า **ข้อมูลที่ส่งมาเพียงพอต่อการจับคู่กับผู้ใช้ Facebook จริงแค่ไหน**

### พารามิเตอร์ที่มีผลต่อ EMQ (เรียงตามน้ำหนักที่มีผลมาก)

1. **Email (em)** — น้ำหนักสูงสุด ถ้ามีและ hash ถูกต้อง
2. **Phone (ph)** — น้ำหนักสูงมากเช่นกัน โดยเฉพาะในไทยที่คนกรอกเบอร์มากกว่าอีเมล
3. **External ID** — รหัสลูกค้าภายในระบบเรา (เช่น customer_id ใน database) ถ้าธุรกิจมี Login/Membership
4. **fbp / fbc** — cookie ที่ Pixel สร้างไว้ ช่วยยืนยันว่า Browser Event กับ Server Event เป็นคนเดียวกัน
5. **Client IP Address + User Agent** — ข้อมูลพื้นฐานที่ต้องมีเสมอในทุก CAPI Event
6. **First Name / Last Name / City / Zip / Country** — เสริมความแม่นยำแต่น้ำหนักรองลงมา

### วิธีปรับปรุง EMQ ให้สูงขึ้นจริง

- **ฝั่ง Pixel:** เปิดใช้ **Advanced Matching** (Automatic Advanced Matching) ใน Events Manager → Settings → เปิด toggle "Automatic Advanced Matching" เพื่อให้ Pixel ดึงข้อมูลจากฟอร์มบนเว็บ (เช่นช่อง email/phone ที่ลูกค้ากรอก) มาช่วย hash และส่งเสริมอัตโนมัติ โดยไม่ต้องเขียนโค้ดเพิ่ม
- **ฝั่ง CAPI:** ต้องเขียนโค้ด Server ให้ดึงข้อมูล user_data ให้ครบที่สุดเท่าที่มี ในทุก Event ที่ส่ง ไม่ใช่แค่ field บังคับ
- **Hash ให้ถูกวิธี:** อีเมลต้อง lowercase และ trim space ก่อน hash เสมอ (`sha256(trim(lowercase(email)))`) เพราะถ้า hash ผิดรูปแบบ Meta จะจับคู่ไม่ได้แม้จะส่งอีเมลจริงมาก็ตาม
- **ส่ง fbp/fbc ให้ครบใน CAPI เสมอ** — ดึงจาก cookie ของ browser ตอนลูกค้า checkout แล้วส่งต่อไปให้ backend ใช้ยิง CAPI (ผ่าน hidden input ใน form หรือ session)

### เกณฑ์คะแนนที่ควรตั้งเป้า

| คะแนน EMQ | ระดับ | คำแนะนำ |
|---|---|---|
| 0–3 | แย่มาก | ต้องแก้ด่วน มักขาด email/phone/fbc |
| 4–6 | พอใช้ | ควรเพิ่ม External ID และ Advanced Matching |
| 7–8 | ดี | อยู่ในเกณฑ์ที่ธุรกิจ SME ส่วนใหญ่ควรได้ |
| 9–10 | ดีเยี่ยม | ระดับ Enterprise ที่มีข้อมูลลูกค้าสมบูรณ์มาก |

---

## Step 128: Aggregated Event Measurement (AEM) เบื้องต้น

### AEM คืออะไร

**Aggregated Event Measurement (AEM)** คือระบบที่ Meta สร้างขึ้นมาเพื่อรองรับข้อจำกัดจาก iOS14+ App Tracking Transparency โดยจะวัดผล Event จากอุปกรณ์ iOS ที่ผู้ใช้ปฏิเสธการติดตาม (Opt-out) ในรูปแบบ **ข้อมูลรวม (Aggregated)** แทนที่จะเป็นข้อมูลรายบุคคล (Individual-level)

พูดง่าย ๆ AEM คือ "โปรโตคอลกลาง" ที่ทำให้ Meta ยังพอวัดผล Conversion ได้ในระดับที่ยอมรับได้ แม้จะไม่รู้ว่า "ใครคนไหน" ทำ Event นั้นแบบเจาะจงเหมือนเดิม

### กฎสำคัญของ AEM ที่ต้องรู้

1. **จำกัดที่ 8 Event ต่อโดเมน** — ธุรกิจสามารถเลือก Priority Event ได้สูงสุด **8 Event ต่อ 1 Domain ที่ Verify แล้ว** (รายละเอียดการตั้งค่าอยู่ใน Step 145)
2. **ลำดับความสำคัญมีผล** — ถ้าผู้ใช้คนหนึ่งทำหลาย Event ในวันเดียว (เช่น ViewContent → AddToCart → Purchase) ระบบจะรายงานเฉพาะ **Event ที่มีลำดับความสำคัญสูงสุด** เท่านั้นสำหรับผู้ใช้ iOS ที่ Opt-out (ดังนั้น Purchase ควรถูกจัดให้มีความสำคัญสูงสุดในกรณีทั่วไป)
3. **มีความหน่วงของข้อมูล (Reporting Delay)** — ข้อมูล AEM อาจรายงานช้ากว่าปกติ 24–72 ชั่วโมง ทำให้การอ่านผลลัพธ์แบบ Real-time ในบัญชีที่มีลูกค้า iOS จำนวนมากไม่แม่นยำเท่าเดิม ต้องรอดูข้อมูลย้อนหลัง
4. **ต้องผ่าน Domain Verification ก่อน** — ถ้า Domain ไม่ผ่านการ Verify การจัดลำดับ Priority Event จะทำไม่ได้เลย

### ผลกระทบเชิงปฏิบัติต่อนักยิงแอด

- ตัวเลข Conversion ที่เห็นใน Ads Manager สำหรับผู้ใช้ iOS อาจ **ไม่ตรง 100%** กับความเป็นจริง ต้องดูแนวโน้ม (Trend) มากกว่าตัวเลขเป๊ะ ๆ รายวัน
- Attribution Window ถูกจำกัดเหลือ **7-day click** เป็นค่าสูงสุดสำหรับ Event ที่มาจาก AEM (ไม่มี view-through หรือ 28-day แบบเดิมอีกแล้วสำหรับ iOS opt-out traffic)
- ธุรกิจควรใช้ **เครื่องมือวัดผลเสริม** เช่น UTM + Google Analytics 4, Coupon Code เฉพาะแคมเปญ, หรือถามลูกค้าตรง ๆ ("รู้จักเราจากไหน") เพื่อ Cross-check กับตัวเลขจาก Ads Manager

---

## Step 129: การ Debug Pixel ด้วย Meta Pixel Helper

### Meta Pixel Helper คืออะไร

เป็น Chrome Extension ทางการของ Meta (ค้นหาใน Chrome Web Store คำว่า "Meta Pixel Helper") ที่ติดตั้งแล้วจะแสดงไอคอนบนแถบ URL ของ Chrome เมื่อคลิกเข้าไปจะบอกทันทีว่า:

- เว็บไซต์นี้มี Pixel ติดตั้งอยู่กี่ตัว, Pixel ID อะไรบ้าง
- Event ไหนถูกยิงบ้างในหน้านั้น (PageView, ViewContent ฯลฯ)
- พารามิเตอร์ที่ส่งไปพร้อม Event นั้น (value, currency, content_ids)
- **คำเตือน (Warning)** สีเหลือง/แดง เช่น "Event ยิงซ้ำ 2 ครั้ง", "ไม่พบ currency/value ใน Purchase Event", "Pixel เวอร์ชันเก่าเกินไป"

### วิธีใช้งานตรวจสอบแบบ Step-by-step

1. ติดตั้ง Extension → เปิดเว็บไซต์ที่ต้องการตรวจ
2. คลิกไอคอน Pixel Helper (รูปสี่เหลี่ยม) → ดูว่าวงกลมสถานะเป็นสีเขียว (ทำงานถูกต้อง), เหลือง (มีคำเตือน), หรือแดง (มีปัญหา)
3. ทำ User Journey จริงทีละขั้น: เปิดหน้าแรก → ดูสินค้า → ใส่ตะกร้า → checkout → หน้า thank you
4. ตรวจทุกขั้นว่า Event ที่ควรยิง ยิงจริงหรือไม่ และพารามิเตอร์ครบไหม
5. เปิด **Chrome DevTools → Network tab** ควบคู่ไปด้วย filter คำว่า `tr?` เพื่อดู raw request จริงที่ยิงออกไป — บาง Warning ของ Pixel Helper ไม่ครอบคลุมทุกกรณี การดู Network โดยตรงช่วยยืนยันซ้ำอีกชั้น

### ปัญหาที่ Pixel Helper ช่วยจับได้บ่อยที่สุด

| อาการที่เจอ | สาเหตุที่เป็นไปได้ |
|---|---|
| ไม่มีไอคอน Pixel Helper ขึ้นเลย | ไม่มี Pixel ติดตั้งในหน้านี้ หรือโค้ดถูกบล็อกโดย Ad Blocker/Consent tool |
| Event ยิง 2 ครั้งซ้ำกัน | โค้ด Pixel ถูกวางซ้ำ 2 ที่ (เช่น ทั้งใน theme.liquid และใน GTM พร้อมกัน) |
| Purchase ไม่มี value/currency | Developer ลืมส่งพารามิเตอร์ หรือ variable ดึงค่าผิด |
| PageView ยิงแต่ Custom Event ไม่ยิงเลย | โค้ด Event ถูกวางผิดตำแหน่ง (เช่น วางก่อนปุ่มโหลดเสร็จ หรือ event listener ไม่ทำงาน) |
| Pixel Helper บอก "Pixel not found" ทั้งที่วางโค้ดแล้ว | โค้ดอยู่ใน section ที่ไม่ได้ render จริง (เช่น cache เก่าของเว็บยังไม่ล้าง) |

### เครื่องมือเสริมอื่น ๆ ที่ควรใช้คู่กัน

- **Events Manager → Test Events** (รายละเอียดลึกใน Part 014 Step 137) — ดู Event แบบ real-time ฝั่ง Server ของ Meta เอง แม่นยำกว่า Extension ในบาง edge case
- **Google Chrome DevTools Console** — เช็ค JavaScript error ที่อาจทำให้ `fbq()` ไม่ทำงานเลยเพราะโค้ดพัง

---

## Step 130: Workshop — ติดตั้งและตรวจสอบ Pixel แบบสมบูรณ์

Workshop นี้คือการรวมทุก Step ใน Part นี้เข้าด้วยกัน ให้ทำตามลำดับจริงกับเว็บไซต์ของตัวเองหรือเว็บทดสอบ (Sandbox site ก็ได้ถ้ายังไม่มีเว็บจริง)

### ภารกิจที่ 1: สร้าง Pixel

- สร้าง Pixel ใหม่ใน Events Manager (หรือใช้ของเดิมถ้ามีอยู่แล้ว — **เช็คให้แน่ใจก่อนสร้างใหม่**)
- ตั้งชื่อ Pixel ตามชื่อธุรกิจ ไม่ใช่ชื่อแคมเปญ
- Assign Pixel ให้ Ad Account ที่จะใช้งาน

### ภารกิจที่ 2: วาง Base Code

วาง Pixel Base Code ในส่วน `<head>` ของทุกหน้าเว็บไซต์ (ตัวอย่างโค้ดจริงที่ Meta ให้มาตอนสร้าง Pixel):

```html
<!-- Meta Pixel Code -->
<script>
!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window, document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
fbq('init', '1234567890123456'); // แทนด้วย Pixel ID จริงของธุรกิจคุณ
fbq('track', 'PageView');
</script>
<noscript><img height="1" width="1" style="display:none"
src="https://www.facebook.com/tr?id=1234567890123456&ev=PageView&noscript=1"
/></noscript>
<!-- End Meta Pixel Code -->
```

### ภารกิจที่ 3: ยิง Standard Event ที่จำเป็นครบ 4 ตัวขั้นต่ำ

ใส่โค้ด Event ให้ตรงตำแหน่งจริงในหน้าเว็บ:

```javascript
// หน้าสินค้า
fbq('track', 'ViewContent', {
  content_ids: ['SKU12345'],
  content_type: 'product',
  value: 990.00,
  currency: 'THB'
});

// ปุ่มใส่ตะกร้า (ผูกกับ event listener ของปุ่ม)
document.querySelector('#add-to-cart-btn').addEventListener('click', function() {
  fbq('track', 'AddToCart', {
    content_ids: ['SKU12345'],
    content_type: 'product',
    value: 990.00,
    currency: 'THB'
  });
});

// หน้า checkout
fbq('track', 'InitiateCheckout', {value: 990.00, currency: 'THB'});

// หน้า thank you (หลังชำระเงินสำเร็จจริงเท่านั้น)
fbq('track', 'Purchase', {
  value: 990.00,
  currency: 'THB',
  content_ids: ['SKU12345'],
  content_type: 'product'
});
```

### ภารกิจที่ 4: ตรวจสอบด้วย Pixel Helper

เดินตาม User Journey เต็มรูปแบบ (หน้าแรก → ดูสินค้า → ใส่ตะกร้า → checkout → thank you) พร้อมเปิด Pixel Helper และ Network tab คู่กัน บันทึกผลว่า Event ไหนยิงถูก ไหนยิงผิด/ไม่ยิงเลย

### ภารกิจที่ 5: เช็คคะแนน Event Match Quality

เข้า Events Manager → เลือก Purchase Event → ดูคะแนน EMQ ปัจจุบัน ถ้าต่ำกว่า 5 ให้เปิด Advanced Matching และวางแผนทำ CAPI ต่อใน Part ถัดไป

---

## Case Study: ร้านขายอาหารเสริมออนไลน์ที่แก้ปัญหา "แอดดูดี แต่ไม่มียอดขายจริง"

ธุรกิจอาหารเสริมรายหนึ่งยิงแอด Conversion Objective มา 3 เดือน ตัวเลขใน Ads Manager บอกว่ามี Purchase 40 ครั้ง/สัปดาห์ ROAS 3.2 แต่เจ้าของธุรกิจยืนยันว่ายอดขายจริงในระบบหลังบ้านมีแค่ประมาณ 15 ออเดอร์/สัปดาห์ — ต่างกันเกือบ 3 เท่า

เมื่อตรวจสอบด้วย Meta Pixel Helper พบว่า:

1. โค้ด Purchase Event ถูกวางไว้ **ในหน้า Checkout** (ตอนกดปุ่ม "ยืนยันคำสั่งซื้อ") ไม่ใช่หน้า Thank You ที่ยืนยันว่าชำระเงินสำเร็จแล้ว
2. ลูกค้าจำนวนมากกดยืนยันคำสั่งซื้อแล้ว **ไม่ได้ชำระเงินจริง** (เลือกโอนเงินแล้วไม่โอน หรือ COD แล้วปฏิเสธรับสินค้า) แต่ Event Purchase ก็ถูกนับไปแล้วตั้งแต่ตอนกดปุ่ม

การแก้ไข:
- ย้าย Purchase Event ไปอยู่หน้า Thank You ที่เข้าถึงได้เฉพาะกรณีระบบยืนยันคำสั่งซื้อสำเร็จเท่านั้น
- เพิ่ม CAPI จากระบบ Order Management ฝั่ง Server เพื่อยิง Purchase เฉพาะออเดอร์ที่สถานะ "ชำระเงินแล้ว" จริง ๆ (ไม่ใช่แค่ "สร้างออเดอร์")
- ผลลัพธ์หลัง 2 สัปดาห์: ตัวเลข Purchase ใน Ads Manager ลดลงมาใกล้เคียงยอดขายจริง (18 ออเดอร์/สัปดาห์) แต่ **คุณภาพการ Optimize ดีขึ้นมาก** เพราะอัลกอริทึมเรียนรู้จากคนที่ "ซื้อจริง" ไม่ใช่คนที่ "แค่กดปุ่ม" — CPA ที่แท้จริงลดลง 35% ภายใน 1 เดือน แม้ตัวเลข ROAS ที่โชว์ในระบบจะดูแย่ลงในตอนแรก (เพราะฐานข้อมูลถูกต้องมากขึ้น)

บทเรียนสำคัญ: **ตัวเลขที่ "ดูดี" ในระบบไม่ได้แปลว่าถูกต้อง** ต้องตรวจสอบ (Reconcile) กับยอดขายจริงเสมอ อย่างน้อยเดือนละครั้ง

---

## Checklist ท้ายบท

- [ ] มี Pixel เดียวสำหรับธุรกิจนี้ใน Business Manager (ไม่มี Pixel ซ้ำซ้อนที่สร้างโดยไม่ตั้งใจ)
- [ ] Pixel ถูก Assign ให้ Ad Account ที่จะใช้งานแคมเปญแล้ว
- [ ] Base Code ของ Pixel ถูกวางในทุกหน้าของเว็บไซต์ (ไม่ใช่แค่หน้าแรก)
- [ ] ยิง Standard Event ครบตาม Funnel: ViewContent, AddToCart, InitiateCheckout, Purchase (หรือ Lead ถ้าเป็นธุรกิจ Lead Gen)
- [ ] Purchase Event มี `value` และ `currency` ครบทุกครั้ง ไม่มีค่าใดเป็น 0 หรือ undefined
- [ ] Purchase Event ถูกวางไว้ที่ "จุดที่ยืนยันการซื้อสำเร็จจริง" เท่านั้น ไม่ใช่จุดกดปุ่มสั่งซื้อ
- [ ] ตรวจสอบด้วย Meta Pixel Helper แล้วไม่มี Warning สีแดง
- [ ] เช็คคะแนน Event Match Quality ของ Purchase Event อย่างน้อยเดือนละครั้ง
- [ ] เข้าใจความแตกต่างระหว่าง Pixel (Browser) และ CAPI (Server) และรู้ว่าธุรกิจนี้ควรมี CAPI หรือยัง
- [ ] รู้ว่า Domain ของเว็บไซต์ผ่านการ Verify แล้ว (จำเป็นสำหรับ AEM และ Priority Event)

---

## Workshop / แบบฝึกหัด

**แบบฝึกหัดที่ 1 — ตรวจสอบ Pixel ของธุรกิจตัวเอง**
ใช้ Meta Pixel Helper ตรวจเว็บไซต์ของธุรกิจตัวเอง (หรือธุรกิจลูกค้าถ้าเป็นฟรีแลนซ์/เอเจนซี่) เดิน User Journey ครบ 5 ขั้น (หน้าแรก → สินค้า → ตะกร้า → checkout → thank you) แล้วบันทึกผลเป็นตารางว่า Event ไหนยิงถูก ไหนมีปัญหา

**แบบฝึกหัดที่ 2 — เปรียบเทียบตัวเลข**
ดึงยอดขายจริงจากระบบหลังบ้าน (หรือสมุดบันทึกออเดอร์) เทียบกับตัวเลข Purchase ใน Events Manager ของสัปดาห์ที่ผ่านมา คำนวณเปอร์เซ็นต์ความคลาดเคลื่อน ถ้าต่างกันเกิน 20% ให้วิเคราะห์ว่าเกิดจากอะไร (Event วางผิดจุด, ไม่มี CAPI, Ad Blocker ฯลฯ)

**แบบฝึกหัดที่ 3 — เขียน Custom Conversion จำลอง**
สมมติว่าเว็บไซต์มีหน้า `/promotion/summer-sale/thankyou` ที่ยังไม่มี Pixel Event ฝังอยู่ ให้ลองสร้าง Custom Conversion จาก URL rule ผ่าน Events Manager (ทำในบัญชีทดสอบก็ได้ถ้ายังไม่มีเว็บจริง) แล้วอธิบายว่าทำไมวิธีนี้เหมาะกับสถานการณ์นี้มากกว่าการรอ Developer แก้โค้ด

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ปูพื้นฐานที่สำคัญที่สุดของการวัดผลโฆษณา Facebook ทั้งหมด: Pixel คือ "ตา" ที่มองเห็นพฤติกรรมลูกค้า, Standard Event คือ "ภาษา" ที่บอกอัลกอริทึมว่าเกิดอะไรขึ้น, Custom Conversion คือทางลัดเวลาไม่มี Developer, CAPI คือ "ตาสำรอง" ฝั่ง Server ที่จำเป็นมากขึ้นทุกวันหลัง iOS14, และ Event Match Quality กับ AEM คือตัวชี้วัดว่าระบบเราแข็งแรงแค่ไหน

แต่ความรู้ทั้งหมดนี้จะไม่มีประโยชน์เลยถ้ายังไม่รู้วิธี **ติดตั้งจริง** บนแพลตฟอร์มต่าง ๆ ที่ธุรกิจไทยใช้กันจริง เช่น WordPress, Shopify, Shopee/Lazada, LINE OA — ซึ่งแต่ละแพลตฟอร์มมีวิธีติดตั้งที่แตกต่างกันโดยสิ้นเชิง Part 014 จะพาไปติดตั้งแบบ step-by-step ทุกช่องทาง พร้อมสอนตั้งค่า Server-Side Tagging ผ่าน GTM และวิธีแก้ปัญหา Pixel ยิงซ้ำ/ไม่ยิง ที่เป็นปัญหาที่พบบ่อยที่สุดในหน้างานจริง

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center: Meta Pixel Overview — https://www.facebook.com/business/help
- Meta for Developers: Conversions API Documentation — https://developers.facebook.com/docs/marketing-api/conversions-api
- Meta for Developers: Standard Events Reference — https://developers.facebook.com/docs/meta-pixel/reference
- Meta Business Help Center: Aggregated Event Measurement — https://www.facebook.com/business/help/aggregated-event-measurement
- Chrome Web Store: Meta Pixel Helper Extension
- Events Manager: https://business.facebook.com/events_manager2
