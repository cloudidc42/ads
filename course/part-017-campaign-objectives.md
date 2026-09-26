# Part 017: Campaign Objectives ทั้งหมดและการเลือกใช้

**Section:** B — Facebook Ads Ecosystem Fundamentals (Part 009–020, Step 81–200)
**Step ที่ครอบคลุม:** 161–170 (จาก 1000 Steps ทั้งหมด)
**เวลาเรียนโดยประมาณ:** 4–5 ชั่วโมง (อ่าน+ทำความเข้าใจ 2.5 ชม. / ลงมือฝึกใน Ads Manager 1.5–2 ชม.)

Part นี้คือหัวใจของการตั้งแคมเปญ Facebook Ads ทุกครั้ง เพราะ **Objective ที่เลือกผิด = แคมเปญทั้งลูกพังตั้งแต่ยังไม่ยิงจริง** ไม่ว่าครีเอทีฟจะสวยแค่ไหน ทาร์เก็ตจะแม่นแค่ไหน ถ้า Objective ไม่ตรงกับสิ่งที่ธุรกิจต้องการ ระบบ Machine Learning ของ Meta จะไปหาคนที่ "ทำพฤติกรรมตาม Objective นั้น" ให้คุณ ซึ่งอาจไม่ใช่คนที่จะซื้อสินค้าคุณเลย

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 161 — Awareness Objective: เมื่อไหร่ควรใช้** เข้าใจว่า Awareness เหมาะกับการสร้างการรู้จักแบรนด์ ไม่ใช่ขายตรง และควรใช้ในสถานการณ์ไหน
2. **Step 162 — Traffic Objective: เจาะลึกการตั้งค่า** ทำความเข้าใจ Optimization Goal ย่อยของ Traffic และข้อจำกัดสำคัญที่มือใหม่มักเข้าใจผิด
3. **Step 163 — Engagement Objective: Page, Post, Video Views** วิธีใช้ Engagement สร้าง Social Proof และสร้าง Audience สำหรับ Retargeting
4. **Step 164 — Leads Objective: Instant Form vs Website Leads** เปรียบเทียบสองวิธีเก็บลีดและเลือกให้เหมาะกับสินค้า
5. **Step 165 — App Promotion Objective เบื้องต้น** ภาพรวมการโปรโมทแอปและสิ่งที่ต้องเตรียมก่อนใช้
6. **Step 166 — Sales Objective: Conversion, Catalog, Store Traffic** สามรูปแบบย่อยของการขายและเมื่อไหร่ควรใช้แต่ละแบบ
7. **Step 167 — การเลือก Objective ให้ตรงกับ Funnel Stage** เชื่อม Objective เข้ากับ TOF-MOF-BOF อย่างเป็นระบบ
8. **Step 168 — ความสัมพันธ์ระหว่าง Objective และ Optimization Goal** เข้าใจว่าทำไม Objective เดียวกันแต่ตั้ง Optimization Goal ต่างกัน ผลลัพธ์ต่างกันสิ้นเชิง
9. **Step 169 — ข้อผิดพลาดที่พบบ่อยในการเลือก Objective** รวมเคสผิดพลาดจริงที่พบบ่อยที่สุดในบัญชีลูกค้า
10. **Step 170 — Workshop: Objective Selection Framework** ฝึกเลือก Objective จากสถานการณ์ธุรกิจจริง 5 เคส

---

## Step 161: Awareness Objective — เมื่อไหร่ควรใช้

### Awareness คืออะไรกันแน่

ในโครงสร้าง Campaign ปัจจุบันของ Meta Ads Manager (ODAX — Outcome-Driven Ad Experiences) Objective ถูกจัดกลุ่มใหม่เหลือ 6 ตัวหลัก คือ **Awareness, Traffic, Engagement, Leads, App Promotion, Sales** โดย Awareness คือกลุ่มที่รวม "Brand Awareness" และ "Reach" แบบเดิมเข้าไว้ด้วยกัน เป้าหมายของ Objective นี้คือ **ทำให้คนจำนวนมากที่สุดได้เห็นโฆษณา และ/หรือจดจำแบรนด์ได้** ไม่ใช่การกดคลิกหรือซื้อ

Optimization Goal ที่เลือกได้ภายใต้ Awareness มีหลักๆ คือ:
- **Ad Recall Lift (จำนวนคนที่คาดว่าจะจำโฆษณาได้)** — ระบบจะเลือกฉายให้กับคนที่มีโอกาส "จดจำ" แบรนด์สูงสุด มักใช้กับงบที่มากพอสมควรและ Reach ฐานใหญ่ (แนะนำอย่างน้อย Reach หลักหมื่นขึ้นไปเพื่อให้ Ad Recall Lift มีความหมายทางสถิติ)
- **Reach (จำนวนคนที่เห็นโฆษณามากที่สุด)** — เหมาะกับงบจำกัดกว่า ต้องการกระจายให้เห็นกว้างที่สุดโดยไม่ซ้ำคนเดิม
- **Impressions** — เน้นจำนวนครั้งที่แสดงผล ไม่สนใจว่าซ้ำคนหรือไม่ ใช้น้อยมากในทางปฏิบัติ

### เมื่อไหร่ควรใช้ Awareness จริงๆ

1. **แบรนด์ใหม่เข้าตลาด ไม่มีใครรู้จักเลย** — ก่อนจะรีทาร์เก็ตขายของ ต้องมี "คนที่รู้จักแบรนด์" ในระบบก่อน Awareness คือจุดเริ่มต้นของ Funnel
2. **เปิดสาขาใหม่ในพื้นที่ที่ยังไม่มีฐานลูกค้า** — เช่น ร้านกาแฟเปิดสาขาที่ 2 ในอีกจังหวัด ต้องให้คนในรัศมีรู้จักก่อน
3. **มีอีเวนต์/แคมเปญใหญ่ที่ต้องการ Reach สูงในเวลาสั้น** เช่น เปิดตัวสินค้าใหม่ Product Launch
4. **ธุรกิจที่ Sales Cycle ยาว** (อสังหาริมทรัพย์, การศึกษาระดับปริญญา, ประกันภัยระดับพรีเมียม) ที่ต้องสร้างการจดจำก่อนคนจะกล้าติดต่อ
5. **ต้องการสร้าง Video Audience หรือ Engager Audience ปริมาณมากในราคาถูก** เพื่อนำไปทำ Custom Audience รีทาร์เก็ตขั้นต่อไป

### เมื่อไหร่ "ไม่ควร" ใช้

- ธุรกิจ SME งบน้อย (ต่ำกว่า 300 บาท/วัน) ที่ต้องการยอดขายเร็ว — Awareness จะเผางบไปกับการสร้างการรู้จักที่ยังแปลงเป็นเงินไม่ได้ในระยะสั้น
- ธุรกิจที่มี Conversion Event พร้อมอยู่แล้ว (Pixel ยิง Purchase ได้ปกติ) และมีสินค้าราคาต่ำ-กลางที่ตัดสินใจซื้อเร็ว ควรข้ามไปที่ Sales Objective ตรงๆ เลย

### ตัวอย่างจริง

แบรนด์สกินแคร์หน้าใหม่ในไทย งบเริ่มต้น 30,000 บาท/เดือน วางแผนดังนี้:
- เดือนที่ 1: ใช้งบ 40% (12,000 บาท) กับ Awareness Objective (Optimization Goal = Reach) ยิง Video สั้น 15 วินาทีเล่าเรื่องแบรนด์ ไปยัง Interest กว้างๆ ที่เกี่ยวกับสกินแคร์ อายุ 20-40 ปี ทั่วประเทศ
- ผลลัพธ์ที่คาดหวังไม่ใช่ยอดขาย แต่คือ Reach 200,000+ คน และสร้างกลุ่ม "คนที่ดูวิดีโอ 50%+" ไว้เป็น Custom Audience
- เดือนที่ 2: นำ Custom Audience นั้นมารีทาร์เก็ตด้วย Traffic แล้วค่อยขึ้น Sales Objective ในเดือนที่ 3

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Awareness แล้วคาดหวังยอดขายทันที แล้วสรุปว่า "แอดไม่เวิร์ก" — ทั้งที่ Objective นี้ไม่ได้ถูกออกแบบมาเพื่อขาย
- เลือก Ad Recall Lift ทั้งที่งบน้อยเกินไป (ต่ำกว่า 5,000 บาท/วัน) ทำให้ระบบไม่มีข้อมูลพอจะคำนวณ Lift ได้แม่นยำ ควรใช้ Reach แทนถ้างบจำกัด
- ใช้ Awareness แทน Traffic เพื่อ "ประหยัดงบ" เพราะ CPM ดูถูกกว่า แต่ไม่ได้ Traffic ไปหน้าเว็บเลยเพราะ Optimization Goal ไม่ได้เน้นคลิก
- ตั้ง Frequency Cap ไม่เหมาะสม ปล่อยให้คนกลุ่มเดิมเห็นโฆษณาเดียวกันเกิน 5-6 ครั้งต่อสัปดาห์ ทำให้เกิด Ad Fatigue เร็วเกินจำเป็นก่อนจะได้ Reach กว้างพอ
- ไม่ตั้งเวลาแคมเปญให้เหมาะสม (Awareness ควรรันต่อเนื่องอย่างน้อย 5-7 วันให้ระบบมีเวลากระจาย Reach อย่างมีประสิทธิภาพ ไม่ใช่รันแค่ 1-2 วันแล้วปิด)

### เกณฑ์เปรียบเทียบเชิงตัวเลข (Benchmark) สำหรับตลาดไทย

ตัวเลขด้านล่างเป็นค่าเฉลี่ยที่พบได้บ่อยในตลาดไทยปี 2025-2026 (ผันแปรตามอุตสาหกรรมและช่วงเวลา ใช้เป็นแนวทางเทียบผลลัพธ์ ไม่ใช่ตัวเลขตายตัว):

| Objective | CPM เฉลี่ย (บาท) | CTR เฉลี่ย | หมายเหตุ |
|---|---|---|---|
| Awareness (Reach) | 30-60 | 0.5-1.2% | CPM ต่ำสุดในกลุ่ม Objective เพราะแข่งประมูลน้อยกว่า |
| Awareness (Ad Recall Lift) | 45-90 | 0.8-1.5% | สูงกว่า Reach เพราะระบบเลือกฉายกลุ่มที่มีโอกาสจดจำสูง |
| Traffic (Landing Page Views) | 60-110 | 1.0-2.0% | CPM สูงขึ้นตามคุณภาพ Landing Page Views |

### เทคนิคระดับ Professional

นักยิงแอดมืออาชีพจะไม่ใช้ Awareness แบบลอยๆ แต่จะออกแบบ "Awareness ที่มีจุดหมายปลายทางชัดเจน" เสมอ เทคนิคที่ใช้บ่อยคือ:

1. **Sequential Video Storytelling** — ทำวิดีโอ 3 ตอนต่อกัน (ตอนที่ 1 เล่าปัญหา ตอนที่ 2 เล่าทางออก ตอนที่ 3 CTA) แล้วใช้ Awareness ยิงตอนที่ 1 ก่อน จากนั้นดึงคนที่ดูตอนที่ 1 จบมารีทาร์เก็ตด้วยตอนที่ 2 และ 3 ต่อเนื่อง วิธีนี้ทำให้ Awareness ไม่ใช่แค่ "สร้างการรู้จัก" แต่เป็นจุดเริ่มต้นของ Sequential Funnel ที่มีเป้าหมายวัดผลได้
2. **ใช้ Awareness คู่กับ Brand Lift Study** — สำหรับบัญชีที่มีงบสูงพอ (มักหลักแสนบาทขึ้นไปต่อเดือน) สามารถขอ Meta ทำ Brand Lift Study เพื่อวัดผลกระทบต่อ Brand Recall/Purchase Intent อย่างเป็นทางการ
3. **จับเวลาให้ตรงกับ Seasonality** — เช่น เริ่ม Awareness ก่อนช่วง 11.11 หรือ 12.12 ล่วงหน้า 2-3 สัปดาห์ เพื่อให้ Retargeting Pool พร้อมก่อนวันโปรโมชั่นจริง

---

## Step 162: Traffic Objective — เจาะลึกการตั้งค่า

### Traffic คืออะไร

Traffic Objective ออกแบบมาเพื่อ "พาคนไปที่ปลายทาง" ไม่ว่าจะเป็นเว็บไซต์ แอป Messenger หรือเบอร์โทร โดย Optimization Goal ที่เลือกได้หลักๆ คือ:

| Optimization Goal | ระบบเลือกฉายให้ใคร | เหมาะกับ |
|---|---|---|
| **Landing Page Views** | คนที่มีโอกาสสูงว่าจะคลิกและ "โหลดหน้าเว็บสำเร็จจริง" (รอ signal Landing Page View ไม่ใช่แค่คลิก) | เว็บไซต์ที่ต้องการคนที่ตั้งใจเข้าเว็บจริง ไม่ใช่คลิกมั่ว |
| **Link Clicks** | คนที่มีโอกาสคลิกลิงก์สูงที่สุด (นับตอนคลิก ไม่รอโหลดหน้าเว็บ) | ใช้เมื่อเว็บโหลดช้าหรือยังไม่ติด Pixel สมบูรณ์ |
| **Impressions/Daily Unique Reach** | เน้นแสดงผลกว้าง | ใช้น้อย เหมาะกับแจ้งข่าวสั้นๆ |

**ข้อควรรู้สำคัญ:** Landing Page Views ดีกว่า Link Clicks เสมอถ้าเว็บไซต์โหลดได้ปกติและติด Pixel ถูกต้อง เพราะ Link Clicks นับรวมคนที่คลิกแล้วเว็บโหลดไม่ทัน/ปิดหนี ทำให้ได้ Traffic "ปลอม" เข้ามาปนในรีทาร์เก็ตออดิเอนซ์

### การตั้งค่าใน Ads Manager แบบละเอียด

1. เลือก Objective = Traffic ที่ Campaign Level
2. ที่ Ad Set Level → Conversion Location เลือก "Website" (หรือ App, Messenger, Calls ตามปลายทางจริง)
3. Performance Goal เลือก "Maximize number of landing page views" (แนะนำ) แทน Link Clicks
4. หากต้องการวัดผลลึกกว่านั้น สามารถเลือก "Conversion Events" ย่อยใน Traffic ได้ในบางบัญชี (เช่นเลือก ViewContent เป็นเป้า) แต่โดยพื้นฐาน Traffic ไม่ได้ออปติไมซ์เพื่อ Purchase
5. ตรวจสอบว่า Pixel ติดตั้งถูกต้องก่อนเลือก Landing Page Views ไม่เช่นนั้นระบบจะไม่มีข้อมูลพอเรียนรู้ และ Fallback ไปใช้ Link Clicks โดยอัตโนมัติ

### เมื่อไหร่ควรใช้ Traffic

- ธุรกิจ Content/บทความ/บล็อกที่รายได้มาจาก Ad Revenue หรือ Affiliate ต้องการคนเข้าเว็บมากๆ
- พาคนไปดู Quiz, Landing Page ข้อมูลก่อนตัดสินใจซื้อ (Middle of Funnel)
- สร้าง Retargeting Pool จากคนที่เข้าเว็บ (Website Visitors) เพื่อนำไปยิง Sales Objective ต่อ
- ทดสอบ Landing Page ใหม่ว่าคนคลิกเข้าไปแล้ว Bounce Rate เป็นอย่างไร ก่อนลงทุนกับ Sales Objective เต็มรูปแบบ

### ข้อผิดพลาดที่พบบ่อยที่สุด (ร้ายแรง)

**การใช้ Traffic Objective เพื่อหวังยอดขาย** คือความผิดพลาดอันดับ 1 ที่เจอในบัญชี SME ไทย เหตุผลคือ Traffic ดู CPC ถูกกว่า Sales Objective มาก (เช่น CPC 2-3 บาท เทียบกับ Cost per Purchase หลักร้อย) ทำให้เจ้าของธุรกิจรู้สึกว่า "คุ้มกว่า" แต่ความจริงคือ:
- Machine Learning จะไปหา "คนที่ชอบคลิกลิงก์" ซึ่งเป็นกลุ่มคนละกลุ่มกับ "คนที่ชอบซื้อของ"
- ได้ Traffic เข้าเว็บจำนวนมากแต่ Conversion Rate ต่ำมาก (มักต่ำกว่า 0.5% เทียบกับ Sales Objective ที่ 1-3%)
- สุดท้ายต้นทุนต่อการขายจริง (Cost per Purchase) แพงกว่าการใช้ Sales Objective ตรงๆ ตั้งแต่แรก

### ตัวอย่างตัวเลขเปรียบเทียบให้เห็นภาพ

สมมติร้านค้าออนไลน์งบ 10,000 บาท ทดลองยิง 2 Objective คู่กัน 7 วัน:

| ตัวชี้วัด | Traffic Objective | Sales Objective |
|---|---|---|
| งบที่ใช้ | 10,000 บาท | 10,000 บาท |
| จำนวนคลิก | 5,000 คลิก (CPC 2 บาท) | 1,800 คลิก (CPC 5.5 บาท) |
| Conversion Rate | 0.4% | 2.8% |
| จำนวน Purchase | 20 ครั้ง | 50 ครั้ง |
| Cost per Purchase | 500 บาท | 200 บาท |

จะเห็นว่า Traffic ได้คลิกมากกว่าเกือบ 3 เท่า แต่ Purchase ได้น้อยกว่า และ Cost per Purchase แพงกว่า Sales Objective ถึง 2.5 เท่า นี่คือหลักฐานเชิงตัวเลขว่าทำไม "CPC ถูก" ไม่ได้แปลว่า "คุ้มกว่า" เสมอไป

### เมื่อไหร่ Traffic ยังจำเป็นอยู่แม้ธุรกิจต้องการขาย

มีข้อยกเว้นที่ Traffic ยังจำเป็น คือช่วง **เริ่มต้นธุรกิจที่ยังไม่มี Purchase Event สะสมเลย** (Pixel เพิ่งติดตั้ง ยังไม่มีข้อมูล) การยิง Sales Objective ตรงจะทำให้ Learning Phase ไม่จบเพราะไม่มี Signal ให้เรียนรู้ ในกรณีนี้ควรใช้ Traffic (Landing Page Views) วิ่งสัก 1-2 สัปดาห์แรกเพื่อสร้าง Pixel Data พื้นฐาน (ViewContent, AddToCart) ก่อน แล้วค่อยขยับไป Sales Objective เมื่อมีข้อมูลมากพอ

---

## Step 163: Engagement Objective — Page, Post, Video Views

### โครงสร้างของ Engagement Objective

Engagement ในระบบ ODAX ปัจจุบันรวม 3 อย่างเดิมเข้าด้วยกัน คือ Post Engagement, Page Likes, และ Event Responses (บางตลาดยังรวม Messages เข้าไปด้วย) โดย Optimization Goal หลักที่เจอบ่อยคือ:

- **Post Engagement (Reactions, Comments, Shares, Clicks รวมกัน)** — ใช้สร้าง Social Proof ให้โพสต์ดูน่าเชื่อถือ คนเห็นคนอื่นคอมเมนต์แล้วอยากคอมเมนต์ตาม (Social Proof Effect)
- **Video Views** — แบ่งเป็น 2 แบบย่อยคือ **ThruPlay** (ดูจนจบหรือดูอย่างน้อย 15 วินาที) และ **2-Second Continuous Video Views** ระบบจะไปหาคนที่มีโอกาสดูวิดีโอนานสูงสุด
- **Page Likes** — ปัจจุบันใช้น้อยลงมากเพราะ Meta ลดความสำคัญของ Page Likes ในการวัดผลธุรกิจ (Vanity Metric)

### ทำไม Engagement สำคัญกว่าที่คิด

หลายคนมองว่า Engagement คือ "แอดกดไลก์" ที่ไม่มีประโยชน์ทางธุรกิจ แต่ในมือของนักยิงแอดมืออาชีพ Engagement คือเครื่องมือสร้าง **Retargeting Audience ต้นทุนต่ำ** ที่สำคัญมาก:

- คนที่ดูวิดีโอ 75% ขึ้นไป = สัญญาณความสนใจสูง สามารถนำมาทำ Custom Audience "Video Viewers 75%" แล้วรีทาร์เก็ตด้วย Sales Objective ในราคาที่ถูกกว่ายิง Cold Audience มาก
- โพสต์ที่มี Engagement สูง (คอมเมนต์เยอะ แชร์เยอะ) เมื่อนำไป Boost ต่อด้วย Sales Objective จะได้ Relevance Score/Quality Ranking ที่ดีกว่าโพสต์เปล่าที่ไม่มีคนโต้ตอบเลย เพราะ Social Proof ช่วยลด Friction ในการตัดสินใจของคนที่เห็นครั้งแรก

### การตั้งค่าที่แนะนำ

1. เลือก Objective = Engagement
2. เลือก "Video Views" ถ้าครีเอทีฟหลักเป็นวิดีโอ และเลือก Optimization = ThruPlay (แนะนำมากกว่า 2-second เพราะ ThruPlay ให้สัญญาณคุณภาพคนดูที่ดีกว่า)
3. ถ้าเป้าหมายคือสร้าง Social Proof ให้โพสต์ขาย เลือก "Messages" หรือ "Post Engagement" ตามความเหมาะสม
4. ตั้งงบให้เพียงพอสร้าง Engager Pool ที่มีขนาดใหญ่พอ (แนะนำอย่างน้อย 3,000-5,000 บาท ต่อการรันแคมเปญ Engagement 5-7 วัน เพื่อให้ได้ Pool ขนาดพอสมควรสำหรับรีทาร์เก็ต)

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Engagement เป็น Objective หลักตลอดทั้งเดือนโดยไม่มีแผนต่อยอดไปสู่ Sales — เท่ากับเสียงบไปกับ Vanity Metric ล้วนๆ
- วัดความสำเร็จแคมเปญด้วย "จำนวนไลก์" แทนที่จะวัดด้วย Cost per Result ที่เชื่อมกับ Business Goal
- เลือก 2-Second Video View แทน ThruPlay เพราะ CPV ถูกกว่า แต่ได้คนดูแค่ 2 วินาทีซึ่งสัญญาณความสนใจต่ำมาก ทำให้ Retargeting Audience ที่ได้มาคุณภาพต่ำ

### การสร้าง Custom Audience จาก Video Engagement (ต่อยอดการใช้งานจริง)

หลังยิง Engagement (Video Views) ไปแล้ว ให้เข้าไปที่ Audiences ใน Ads Manager และสร้าง Custom Audience แบบ "Engagement" เลือกประเภท Video โดยแบ่งระดับความสนใจได้ 5 ระดับ:

| ระดับ Video View | ความหมาย | การนำไปใช้ |
|---|---|---|
| ThruPlay | ดูจนจบหรือ 15 วิ+ | Retargeting Pool ที่มีคุณภาพสูงสุด ใช้ยิง Sales ต่อได้เลย |
| 75% | ดูเกือบทั้งคลิป | Pool คุณภาพสูง เหมาะกับ Sales/Leads |
| 50% | ดูครึ่งคลิป | Pool ขนาดกลาง เหมาะทำ Traffic/Leads ต่อ |
| 25% | ดูช่วงต้น | Pool ขนาดใหญ่ เหมาะทำ Engagement/Traffic รอบสอง |
| 3 วินาที | เห็นแค่ผ่านตา | Pool กว้างสุด มักใช้ทำ Lookalike Source เท่านั้น ไม่ควรยิงขายตรง |

ยิ่งระดับความสนใจสูง (ThruPlay, 75%) ขนาด Pool จะเล็กลงแต่คุณภาพสูงขึ้น เหมาะกับการยิง Sales Objective ต่อทันที ส่วนระดับต่ำ (25%, 3 วินาที) เหมาะใช้เป็นฐานสร้าง Lookalike Audience มากกว่าจะยิงขายตรง

---

## Step 164: Leads Objective — Instant Form vs Website Leads

### สองเส้นทางเก็บลีดที่ต้องเข้าใจให้ชัด

Leads Objective มี Conversion Location ให้เลือก 2 แบบหลักที่ต้องแยกให้ออก:

**1. Instant Forms (On-Facebook)**
ฟอร์มเปิดขึ้นมาทันทีในแอป Facebook/Instagram โดยไม่ต้องออกจากแพลตฟอร์ม ข้อมูลชื่อ-เบอร์-อีเมลจะถูก Pre-fill จากข้อมูลโปรไฟล์ผู้ใช้อัตโนมัติ

ข้อดี:
- อัตราการกรอกฟอร์มสำเร็จสูงมาก (Conversion Rate มักอยู่ที่ 15-30%+ ของคนที่คลิก) เพราะ Friction ต่ำสุด
- โหลดเร็ว ไม่มีปัญหาเรื่องเว็บไซต์ล่มหรือช้า
- เหมาะกับตลาดที่คนใช้เน็ตมือถือความเร็วไม่แน่นอน

ข้อเสีย:
- คุณภาพลีดมักต่ำกว่า เพราะ Pre-fill ทำให้คนกรอกแบบไม่ได้ตั้งใจจริง (บางคนกดฟอร์มเล่นๆ)
- ต้องมีทีม Follow-up เร็วมาก (ภายใน 5-15 นาที) ไม่เช่นนั้นลีดเย็นและไม่รับสาย
- CPL (Cost per Lead) ต่ำกว่า Website Leads แต่ Lead-to-Sale Rate ก็ต่ำกว่าด้วย

**2. Website Leads (Conversion Leads นำไปหน้าเว็บ/Landing Page)**
คนคลิกแล้วออกจาก Facebook ไปกรอกฟอร์มบนเว็บไซต์ของธุรกิจเอง ต้องมี Pixel/CAPI ยิง Event "Lead" หรือ "CompleteRegistration" กลับมา

ข้อดี:
- คุณภาพลีดสูงกว่า เพราะคนต้องตั้งใจออกจาก Facebook ไปกรอกเอง (Friction สูงกว่า = กรองคนไม่สนใจออกไปตามธรรมชาติ)
- สามารถออกแบบฟอร์มได้อิสระเต็มที่ ใส่คำถามคัดกรอง (Qualifying Questions) ได้ละเอียดกว่า
- เชื่อมกับ CRM/ระบบหลังบ้านได้ลื่นไหลกว่า

ข้อเสีย:
- CPL สูงกว่า Instant Form เพราะ Friction สูงกว่า คนดรอปออกกลางทางมากกว่า
- ต้องพึ่งพาความเร็วเว็บไซต์และการติดตั้ง Pixel/CAPI ที่แม่นยำ

### วิธีเลือกให้เหมาะกับธุรกิจ

| ประเภทธุรกิจ | แนะนำ | เหตุผล |
|---|---|---|
| คอร์สออนไลน์ ราคาต่ำ-กลาง ต้องการโวลุ่มมาก | Instant Form | เน้นปริมาณ ทีม Telesales ตามงานหนัก คัดกรองทีหลังได้ |
| อสังหาริมทรัพย์ ราคาสูง (คอนโด/บ้าน) | Website Leads หรือ Instant Form + คำถามคัดกรองละเอียด | ต้องการคุณภาพลีดสูง ไม่อยากเสียเวลาเซลส์กับลีดปลอม |
| ประกันชีวิต/ประกันสุขภาพ | Website Leads | ต้องมีคำถามคัดกรองสุขภาพ/อายุ/งบประมาณที่ Instant Form ทำได้ไม่ละเอียดพอ |
| ธุรกิจ B2B ที่ Sales Cycle ยาว | Website Leads เชื่อม CRM | ต้องการข้อมูล Lead Scoring ที่ลึกกว่า |
| ร้านเสริมความงาม/คลินิกทั่วไป | Instant Form | ต้องการโวลุ่มลีดเข้าไลน์/แชทเร็ว ตามด้วยแอดมินปิดสด |

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Instant Form กับสินค้าราคาสูง (บ้าน คอนโด) โดยไม่มีคำถามคัดกรองเลย ได้ลีดจำนวนมากแต่ไม่มีเงินซื้อจริงแม้แต่คนเดียว
- ตั้ง Instant Form แล้วไม่มีระบบ Follow-up อัตโนมัติเชื่อมต่อ CRM ทำให้ลีดตกหล่นหรือ Follow-up ช้าเกินไป
- ใช้ Website Leads แต่เว็บโหลดช้าหรือฟอร์มยาวเกินไป (มากกว่า 5-6 ช่อง) ทำให้ Drop-off สูงมาก

### การออกแบบคำถามใน Instant Form ให้กรองคุณภาพลีด

แม้ Instant Form จะเน้นความง่ายในการกรอก แต่ก็สามารถแทรกคำถามคัดกรอง (Custom Questions) ได้ 2-3 ข้อโดยไม่ทำให้ Drop-off สูงเกินไป ตัวอย่างคำถามที่ใช้ได้ผลจริงในธุรกิจอสังหาริมทรัพย์:

1. "งบประมาณที่สนใจ" (แบบ Multiple Choice ให้เลือกช่วงราคา ไม่ใช่ให้กรอกตัวเลขเอง)
2. "ต้องการที่อยู่อาศัยภายในกี่เดือน" (ตัวเลือก: ภายใน 1 เดือน / 1-3 เดือน / มากกว่า 3 เดือน / ยังไม่แน่ใจ)
3. "วิธีการชำระเงินที่วางแผนไว้" (เงินสด/ผ่อนธนาคาร/ยังไม่แน่ใจ)

คำถามเหล่านี้ทำหน้าที่เป็น "Lead Scoring" อัตโนมัติ ทีมเซลส์สามารถจัดลำดับความสำคัญโทรตามลีดที่ตอบ "ภายใน 1 เดือน" ก่อนลีดที่ตอบ "ยังไม่แน่ใจ" ได้ทันที

### Response Time คือตัวแปรที่กระทบยอดปิดขายมากที่สุด

งานวิจัยหลายชิ้น (รวมถึงข้อมูลจาก Meta เอง) ชี้ว่าลีดที่ได้รับการ Follow-up ภายใน 5 นาทีแรก มีโอกาสปิดการขายสูงกว่าลีดที่ Follow-up หลัง 30 นาทีถึง 4-5 เท่า ดังนั้นก่อนยิง Leads Objective ทุกครั้ง ต้องเตรียม:
- ระบบแจ้งเตือนอัตโนมัติ (LINE Notify, Zapier, Make.com) ที่ส่งลีดใหม่เข้าไลน์แอดมินทันทีที่มีคนกรอกฟอร์ม
- Script การโทร/แชทมาตรฐานที่ทีมงานพร้อมใช้ทันที ไม่ต้องมาคิดสดหน้างาน

---

## Step 165: App Promotion Objective เบื้องต้น

### ภาพรวมสำหรับผู้ที่ยังไม่ทำแอป

App Promotion เป็น Objective เฉพาะสำหรับธุรกิจที่มีแอปพลิเคชันบน App Store/Google Play และต้องการให้คนดาวน์โหลดหรือทำกิจกรรมในแอป (App Events) แม้ Part นี้จะไม่ได้เจาะลึกเพราะเป็นเนื้อหาเฉพาะทางที่ Section ถัดไปจะพูดถึง แต่นักยิงแอดทุกคนต้องรู้พื้นฐาน 3 เรื่องนี้ไว้ก่อน:

1. **MMP (Mobile Measurement Partner) จำเป็นเสมอ** — เช่น AppsFlyer, Adjust, Branch ต้องเชื่อมกับแอปก่อนจะยิงแอด Meta จะไม่รับข้อมูล Conversion จากแอปตรงๆ โดยไม่มี MMP เป็นตัวกลาง (ยกเว้นบางกรณีใช้ Meta SDK ตรง)
2. **Optimization Goal มี 2 ระดับ** คือ **App Installs** (เน้นยอดดาวน์โหลดอย่างเดียว) และ **App Events** (เน้นพฤติกรรมในแอปเช่น Registration, Purchase in-app — ให้ผลลัพธ์ที่มีคุณภาพกว่ามากเพราะกรองคนที่โหลดแล้วไม่ใช้ออกไป)
3. **iOS กับ SKAdNetwork (SKAN)** — หลัง iOS 14+ การวัดผลแอปบน iPhone มีข้อจำกัดเรื่อง Privacy สูงมาก ข้อมูลจะดีเลย์และไม่ Real-time เหมือน Android ต้องตั้งความคาดหวังเรื่องความแม่นยำของรายงานให้ถูกต้อง

### เมื่อไหร่จะได้ใช้จริง

ถ้าธุรกิจของคุณยังไม่มีแอป ให้ข้าม Step นี้ไปพลางๆ ได้ แต่ถ้าลูกค้าเป็นธุรกิจ Fintech, e-Commerce ที่มีแอป, หรือ Game ให้จำหลักการ "App Events ดีกว่า App Installs เสมอถ้าแอปมีข้อมูลพอ" ไว้ใช้งานจริงในอนาคต (รายละเอียดเจาะลึกเรื่อง App Promotion แบบเต็มรูปแบบจะอยู่ใน Section C ช่วง Part 028)

### ข้อผิดพลาดที่พบบ่อย

- ยิง App Installs อย่างเดียวโดยไม่ดู Retention หลังติดตั้ง ได้ยอดโหลดสูงแต่คนลบแอปทิ้งภายในวันเดียวเกินครึ่ง
- ไม่ตั้งค่า Deep Linking ทำให้คนคลิกแอดแล้วเปิดแอปไปหน้าแรกทั่วไป ไม่ตรงกับสินค้าที่โฆษณา เสีย Conversion Rate ไปมาก
- ไม่แยก Ad Set ตามระบบปฏิบัติการ (iOS vs Android) ทั้งที่พฤติกรรมและต้นทุนการได้ผู้ใช้ (Cost per Install) ต่างกันมากระหว่างสองแพลตฟอร์ม โดยทั่วไป iOS มักมี Cost per Install สูงกว่า Android เพราะกำลังซื้อเฉลี่ยสูงกว่าและข้อจำกัดเรื่อง SKAN ทำให้การออปติไมซ์ทำได้ยากกว่า
- คาดหวังผลลัพธ์ Real-time บน iOS เหมือน Android ทั้งที่ SKAN มีการหน่วงเวลารายงาน (Delay) และปัดเศษข้อมูลเพื่อรักษา Privacy ทำให้ตัวเลขที่เห็นในช่วง 24-48 ชั่วโมงแรกไม่สมบูรณ์

---

## Step 166: Sales Objective — Conversion, Catalog, Store Traffic

### สามรูปแบบย่อยของการขาย

Sales คือ Objective ที่ทรงพลังที่สุดสำหรับธุรกิจที่มี Conversion Event พร้อมใช้งาน มี Conversion Location ให้เลือก 3 แบบหลัก:

**1. Website Conversions**
ออปติไมซ์เพื่อ Event บนเว็บไซต์ เช่น Purchase, Add to Cart, Initiate Checkout ต้องมี Pixel + CAPI ที่ยิง Event ถูกต้องครบถ้วน (ตามที่เรียนใน Part 013-015) ระบบจะไปหาคนที่มีโอกาสทำ Event นั้นสูงที่สุด

**2. Catalog Sales (Advantage+ Catalog Ads)**
ใช้ร่วมกับ Product Catalog ที่อัปโหลดสินค้าไว้ (ผ่าน Commerce Manager) เหมาะมากสำหรับ:
- Dynamic Retargeting — โชว์สินค้าที่ลูกค้าเคยดู/เคยใส่ตะกร้าแบบอัตโนมัติ ไม่ต้องทำครีเอทีฟรายสินค้าเอง
- Dynamic Prospecting — หาลูกค้าใหม่จาก Catalog โดยระบบเลือกสินค้าที่น่าจะขายได้ดีที่สุดให้คนที่ยังไม่รู้จักแบรนด์
เหมาะกับร้านที่มีสินค้าจำนวนมาก (หลักสิบ-หลักพัน SKU) เช่น แฟชั่น, ของแต่งบ้าน, อุปกรณ์อิเล็กทรอนิกส์

**3. Store Traffic**
ออปติไมซ์เพื่อพาคนไปที่ร้านสาขาจริง (Physical Store) ใช้ Location Targeting แบบรัศมีรอบสาขา เหมาะกับธุรกิจที่มีหลายสาขาเช่น ร้านอาหารเชนใหญ่ ร้านสะดวกซื้อ ธุรกิจค้าปลีกที่วัดผลจาก Foot Traffic ไม่ใช่ Online Purchase

### การตั้งค่าที่ต้องเตรียมก่อนใช้ Sales Objective

- Website Conversions ต้องมี Pixel/CAPI ยิง Standard Event ที่เลือกเป็นเป้าได้อย่างน้อย 15-25 ครั้ง/สัปดาห์ต่อ Ad Set (ตามเกณฑ์ Learning Phase ที่จะเรียนใน Part ถัดๆไป) ไม่เช่นนั้นระบบจะไม่มีข้อมูลพอเรียนรู้
- Catalog Sales ต้องอัปโหลด Product Feed ให้ครบ ถูกต้อง และอัปเดตสต็อก/ราคาสม่ำเสมอ (Feed ที่ Error หรือสินค้าหมดสต็อกจะทำให้แอดโดนตีคุณภาพ)
- Store Traffic ต้องผูก Location ของทุกสาขาไว้ใน Business Manager ล่วงหน้า

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Website Conversions ออปติไมซ์ Purchase ทั้งที่ยอด Purchase ต่อสัปดาห์ต่ำเกินไป (ต่ำกว่า 10 ครั้ง) ทำให้ Learning Phase ไม่จบ ควรลดระดับไปออปติไมซ์ Add to Cart หรือ Initiate Checkout ก่อนชั่วคราว
- ใช้ Catalog Sales แต่ไม่เคยเช็ก Feed Health ใน Commerce Manager เลย ทำให้สินค้าครึ่งหนึ่งใน Feed ผิด Error และไม่ถูกนำไปแสดงโฆษณา
- ใช้ Store Traffic โดยตั้งรัศมีกว้างเกินจริง (เช่น 50 กม.) ทำให้คนที่เห็นโฆษณาไม่สะดวกเดินทางไปร้านจริง ควรตั้งรัศมีตามพฤติกรรมการเดินทางจริงของกลุ่มเป้าหมาย (ปกติ 3-10 กม.สำหรับเมืองใหญ่)
- ไม่ใช้ Value Optimization ทั้งที่ธุรกิจมี Order Value หลากหลายมาก (สินค้าราคา 200-20,000 บาทในร้านเดียวกัน) ทำให้ระบบไปเน้นหาคนที่ซื้อสินค้าราคาถูกจำนวนมาก (Purchase Count สูง) แทนที่จะหาคนที่สร้างรายได้สูงสุด (Value สูง) ซึ่งอาจทำให้ ROAS โดยรวมต่ำกว่าที่ควรจะเป็น

### รายละเอียดเพิ่มเติม: Advantage+ Shopping Campaigns (ASC)

ปัจจุบัน Meta ผลักดัน **Advantage+ Shopping Campaigns** ให้เป็นค่าเริ่มต้นสำหรับธุรกิจ E-commerce มากขึ้น โดย ASC คือรูปแบบหนึ่งของ Sales Objective ที่ให้ระบบ AI ควบคุมเกือบทุกอย่างอัตโนมัติ (Audience, Placement, Budget Allocation ระหว่าง Ad Set) นักยิงแอดยังต้องเข้าใจ Sales Objective แบบ Manual ในระดับ Advanced ก่อน เพราะ ASC ทำงานได้ดีที่สุดเมื่อมี Pixel/Catalog ที่สมบูรณ์อยู่แล้ว (Part 029 จะเจาะลึกเรื่องนี้เต็มรูปแบบ)

---

## Step 167: การเลือก Objective ให้ตรงกับ Funnel Stage

### แผนที่ Objective ตาม Funnel

หลักการสำคัญที่สุดของ Part นี้คือ **Objective ต้องเดินตาม Funnel Stage ของลูกค้า ไม่ใช่เลือกตามความชอบส่วนตัว**

| Funnel Stage | เป้าหมายทางธุรกิจ | Objective ที่แนะนำ | กลุ่มเป้าหมาย |
|---|---|---|---|
| **TOF (Top of Funnel)** — คนไม่รู้จักแบรนด์เลย | สร้างการรู้จัก / เก็บ Engager Pool | Awareness, Engagement (Video Views) | Cold Audience กว้าง (Interest, Lookalike, Advantage+ Audience) |
| **MOF (Middle of Funnel)** — รู้จักแล้ว สนใจแต่ยังไม่ตัดสินใจ | พาไปดูข้อมูลเพิ่ม / เก็บลีด | Traffic, Leads, Engagement (Messages) | Website Visitors, Video Viewers 25-75%, Engager 30-180 วัน |
| **BOF (Bottom of Funnel)** — พร้อมซื้อ/ตัดสินใจแล้ว | ปิดการขาย | Sales (Conversion/Catalog) | Add to Cart, Initiate Checkout ที่ยังไม่ Purchase, Retargeting 1-30 วัน |
| **Retention (หลังซื้อ)** — ซื้อไปแล้ว | ซื้อซ้ำ/Upsell | Sales (Catalog Dynamic Retargeting) | Past Purchasers, Custom Audience จาก CRM/Customer List |

### ตัวอย่างการวางแผนแบบ Full-Funnel จริง

ร้านขายเครื่องใช้ไฟฟ้าออนไลน์ งบรวม 100,000 บาท/เดือน แบ่งดังนี้:
- 15% (15,000 บาท) → Awareness/Engagement ยิง Video Views เจาะกลุ่ม Interest เครื่องใช้ไฟฟ้า/ของแต่งบ้าน สร้าง Video Viewer Pool
- 20% (20,000 บาท) → Traffic พาคนไปดูหน้า Landing Page โปรโมชั่นรายเดือน สร้าง Website Visitor Pool
- 55% (55,000 บาท) → Sales (Website Conversions) ยิงตรงกลุ่ม Lookalike จากลูกค้าเก่า + รีทาร์เก็ต Add to Cart/Initiate Checkout
- 10% (10,000 บาท) → Sales (Catalog Dynamic Retargeting) เฉพาะกลุ่มที่เคยดูสินค้าแต่ไม่ซื้อใน 14 วัน

การแบ่งงบแบบนี้ทำให้ Funnel เดินครบวงจร ไม่ใช่ยิงแต่ BOF ตลอด (ซึ่งจะทำให้ Retargeting Pool หมดและ Cost per Purchase ค่อยๆ แพงขึ้นทุกเดือนเพราะไม่มีคนใหม่เข้าระบบ)

---

## Step 168: ความสัมพันธ์ระหว่าง Objective และ Optimization Goal

### Objective คือกรอบใหญ่ Optimization Goal คือกลไกจริงที่ทำงาน

จุดที่มือใหม่สับสนมากที่สุดคือคิดว่า "เลือก Objective ถูกแล้วจบ" แต่จริงๆ แล้ว **Objective แค่กำหนดว่า Optimization Goal ตัวไหนจะปรากฏให้เลือกได้** ส่วน Optimization Goal ที่เลือกจริงใน Ad Set Level คือสิ่งที่กำหนดว่า Machine Learning จะไป "ตามหาใคร" ให้คุณ

ตัวอย่างที่ชี้ให้เห็นชัด: Objective = Sales สามารถเลือก Optimization Goal ได้หลายแบบ เช่น
- **Conversions** (ออปติไมซ์เพื่อ Purchase Event โดยตรง) — ดีที่สุดถ้ามีข้อมูล Purchase พอ
- **Value** (ออปติไมซ์เพื่อมูลค่าการซื้อสูงสุด ไม่ใช่จำนวนครั้ง) — เหมาะกับธุรกิจที่มี Order Value หลากหลายและต้องการ ROAS สูงสุด ไม่ใช่แค่จำนวนออเดอร์
- **Landing Page Views** (ในบางกรณี Ad Set ระดับ Sales ยังตั้งเป็น Landing Page Views ได้ถ้าข้อมูล Purchase ยังน้อยเกินไป)

ถ้าเลือก Objective = Sales แต่ไปตั้ง Optimization Goal เป็น Landing Page Views โดยไม่รู้ตัว (เพราะ Purchase Event ยังน้อยระบบเลือก Fallback ให้) แคมเปญจะทำงานคล้าย Traffic Objective มากกว่า Sales จริงๆ ทั้งที่ Objective บอกว่าเป็น Sales — นี่คือเหตุผลที่ต้อง **เช็ก Optimization Goal ที่ Ad Set Level ทุกครั้ง ไม่ใช่ดูแค่ชื่อ Objective ที่ Campaign Level**

### ตารางความสัมพันธ์แบบสรุป

| Objective | Optimization Goal ที่มักเจอ | สิ่งที่ควรเช็กก่อนเลือก |
|---|---|---|
| Awareness | Ad Recall Lift, Reach | งบพอสำหรับ Reach ฐานใหญ่หรือไม่ |
| Traffic | Landing Page Views, Link Clicks | Pixel ติดตั้งสมบูรณ์หรือยัง (ถ้ายัง ใช้ Link Clicks ชั่วคราว) |
| Engagement | Post Engagement, ThruPlay, 2-Sec Video View | ต้องการ Social Proof หรือ Retargeting Pool |
| Leads | Instant Form Submissions, On-Facebook Leads, Conversion Leads | ต้องการปริมาณหรือคุณภาพ |
| Sales | Conversions, Value, Landing Page Views (Fallback) | จำนวน Purchase Event/สัปดาห์เพียงพอหรือไม่ |

---

## Step 169: ข้อผิดพลาดที่พบบ่อยในการเลือก Objective

รวบรวมจากเคสจริงที่พบบ่อยที่สุดในบัญชีโฆษณา SME และเอเจนซี่ไทย:

1. **ใช้ Traffic ทดแทน Sales เพราะ CPC ถูกกว่า** — อธิบายไว้แล้วใน Step 162 เป็นความผิดพลาดที่พบบ่อยที่สุดอันดับ 1
2. **สลับ Objective ไปมาบ่อยเกินไปในแคมเปญเดียวกัน** — การเปลี่ยน Objective ทำให้ Ad Set รีเซ็ต Learning Phase ใหม่ทุกครั้ง เสียทั้งเงินและเวลาไปกับการเรียนรู้ซ้ำ ควรตัดสินใจให้ชัดก่อนสร้างแคมเปญ ไม่ใช่ลองผิดลองถูกกลางแคมเปญที่ใช้เงินจริงไปแล้ว
3. **ใช้ Instant Form (Leads) กับสินค้าราคาสูงโดยไม่มีคำถามคัดกรอง** — ได้ลีดจำนวนมากแต่ปิดขายไม่ได้เลย เสียเวลาทีมเซลส์
4. **เลือก App Promotion โดยยังไม่มี MMP เชื่อมต่อ** — ยิงไปแล้ววัดผลไม่ได้เลย เพราะ Meta ไม่รับข้อมูล Conversion จากแอปตรงๆ
5. **ไม่เข้าใจว่า Objective ต้องเดินตาม Funnel** — ยิง Sales Objective ตรงกับ Cold Audience 100% ตั้งแต่วันแรกโดยไม่มี TOF/MOF เลย ทำให้ CPA สูงเวอร์เพราะไม่มี Warm Audience ให้ระบบเลือกก่อน
6. **มองข้าม Optimization Goal ที่ Ad Set Level** — เข้าใจว่าเลือก Objective ถูกแล้วจบ โดยไม่เช็กว่า Ad Set กำลังออปติไมซ์อะไรจริงๆ (ตามที่อธิบายใน Step 168)
7. **ใช้ Awareness/Engagement เป็น Objective หลักตลอดไปโดยไม่มี Sales ตามมาเลย** — เสียงบไปกับ Vanity Metric แบบไม่มีจุดจบ
8. **ไม่ปรับ Objective ตามข้อมูล Purchase ที่มีจริง** — ธุรกิจใหม่ที่ยังไม่มี Purchase Event เลยแต่เลือกออปติไมซ์ Conversions ทันที ทำให้ Learning Phase ไม่จบไปเรื่อยๆ ควรเริ่มจาก Traffic/Engagement ก่อนสร้างข้อมูลพื้นฐาน แล้วขยับไป Sales เมื่อมี Signal พอ

---

## การวัดผลข้าม Objective (Cross-Objective Attribution)

ปัญหาหนึ่งที่นักยิงแอดมือใหม่มักเจอคือการ "ตัดสินความสำเร็จของแคมเปญ TOF/MOF จากยอดขายโดยตรง" ซึ่งไม่ถูกต้อง เพราะ Awareness/Engagement/Traffic ไม่ได้ถูกออปติไมซ์เพื่อขาย การตัดสินความสำเร็จของแต่ละ Objective จึงต้องใช้ตัวชี้วัดที่ต่างกัน:

| Objective | ตัวชี้วัดความสำเร็จหลัก | ตัวชี้วัดรอง |
|---|---|---|
| Awareness | Reach, Frequency, Ad Recall Lift (ถ้ามี) | CPM |
| Traffic | Landing Page Views, Cost per LPV, Bounce Rate หลังคลิก | CTR |
| Engagement | Cost per Engagement, Video Watch Time, Pool Size ที่สร้างได้ | Comment/Share Rate |
| Leads | Cost per Lead, Lead Quality Score (ผลจากทีมเซลส์) | Form Completion Rate |
| Sales | Cost per Purchase, ROAS, AOV (Average Order Value) | Add to Cart Rate |

เมื่อประเมินผลรวมทั้ง Funnel ให้มองเป็น **"ต้นทุนรวมต่อการปิดขาย 1 ครั้ง" (Blended CPA)** โดยรวมงบทั้งหมดที่ใช้ในทุก Objective หารด้วยจำนวนยอดขายทั้งหมดที่เกิดขึ้นในช่วงเวลาเดียวกัน แทนที่จะดู Cost per Purchase ของแคมเปญ Sales อย่างเดียวโดยไม่นับงบที่ใช้ไปกับ Awareness/Engagement/Traffic ที่ช่วยปูทางมา

---

## Case Study: ร้านกาแฟ Specialty เปิดสาขาใหม่ในเชียงใหม่

**สถานการณ์:** ร้านกาแฟ Specialty แบรนด์หนึ่งในกรุงเทพฯ เปิดสาขาที่ 2 ที่เชียงใหม่ ไม่มีฐานลูกค้าในพื้นที่เลย งบโฆษณาเริ่มต้น 25,000 บาท สำหรับ 60 วันแรก

**แผนที่ใช้จริง:**
- **สัปดาห์ 1-2 (งบ 8,000 บาท):** Objective = Awareness (Optimization = Reach) เจาะรัศมี 5 กม. รอบร้าน อายุ 20-45 ปี สนใจกาแฟ/คาเฟ่/ไลฟ์สไตล์ ครีเอทีฟเป็นวิดีโอเปิดร้าน บรรยากาศภายใน
- **สัปดาห์ 3-4 (งบ 7,000 บาท):** Objective = Engagement (ThruPlay) ยิงต่อกับกลุ่มเดิมพร้อมโปรโมชั่นเปิดร้าน "ซื้อ 1 แถม 1" เก็บ Video Viewer Pool และ Page Engager ไว้
- **สัปดาห์ 5-6 (งบ 5,000 บาท):** Objective = Traffic พาคนไปดูเมนูเต็มบนเว็บไซต์/LINE OA สร้าง Website Visitor Pool
- **สัปดาห์ 7-8 (งบ 5,000 บาท):** Objective = Sales (Website Conversions ออปติไมซ์ Event "จองโต๊ะ/สั่งล่วงหน้า") รีทาร์เก็ตทุก Pool ที่สร้างไว้ก่อนหน้า

**ผลลัพธ์:** Reach สะสม 45,000 คนในรัศมี 5 กม. (ครอบคลุมประชากรเป้าหมายในพื้นที่เกือบทั้งหมด) มีคนเข้าร้านที่แจ้งว่า "เห็นจากโฆษณา" มากกว่า 300 คนในช่วง 60 วัน และ Cost per Reservation ในสัปดาห์ 7-8 อยู่ที่ 45 บาท/การจอง ซึ่งต่ำกว่าที่คาดการณ์ไว้ (ตั้งเป้าไว้ 80 บาท) เพราะกลุ่มที่รีทาร์เก็ตเป็นกลุ่มที่ผ่านการ "อุ่น" มาจาก Awareness → Engagement → Traffic มาแล้ว ไม่ใช่ Cold Audience

**บทเรียน:** ถ้าร้านเลือกใช้ Sales Objective ยิงตรงกับ Cold Audience ตั้งแต่วันแรก (แบบที่หลายร้านทำ) จะได้ CPA ที่แพงกว่านี้มาก เพราะไม่มีใครในเชียงใหม่รู้จักแบรนด์เลย ระบบไม่มีข้อมูลพอจะหาคนที่ "น่าจะจอง" ได้แม่นยำ

---

## ตารางตัดสินใจ: Business Goal → Objective → Optimization Goal (Decision Framework)

| Business Goal (สิ่งที่ธุรกิจต้องการ) | Objective ที่แนะนำ | Optimization Goal | เงื่อนไข/ข้อควรระวัง |
|---|---|---|---|
| แบรนด์ใหม่ ไม่มีใครรู้จัก ต้องการสร้างการจดจำ | Awareness | Reach (งบน้อย) / Ad Recall Lift (งบมาก) | Reach หลักหมื่นขึ้นไปก่อนใช้ Ad Recall Lift |
| ต้องการคนเข้าอ่านบทความ/บล็อก/ดูข้อมูลก่อนซื้อ | Traffic | Landing Page Views | ต้องติด Pixel สมบูรณ์ก่อน ไม่งั้น Fallback เป็น Link Clicks |
| ต้องการสร้าง Social Proof ให้โพสต์ก่อน Boost ขาย | Engagement | Post Engagement | ใช้ระยะสั้น 3-5 วันก่อนเปลี่ยนไป Sales |
| ต้องการสร้าง Retargeting Pool จากคนดูวิดีโอ | Engagement | ThruPlay | เลือก ThruPlay ไม่ใช่ 2-Second เพื่อคุณภาพ Pool ที่ดีกว่า |
| ต้องการลีดปริมาณมาก สินค้าราคาต่ำ-กลาง | Leads | Instant Form Submissions | ต้องมีทีม Follow-up เร็วภายใน 15 นาที |
| ต้องการลีดคุณภาพสูง สินค้าราคาสูง/B2B | Leads | Conversion Leads (Website) | ต้องมี Pixel/CAPI ยิง Lead Event ถูกต้อง |
| มีแอปต้องการยอดโหลด + คนใช้งานจริง | App Promotion | App Events | ต้องเชื่อม MMP ก่อนเริ่มยิง |
| มี Pixel พร้อม ต้องการยอดขายบนเว็บ | Sales | Conversions (หรือ Value ถ้าต้องการ ROAS สูงสุด) | ต้องมี Purchase Event ≥ 15-25 ครั้ง/สัปดาห์/Ad Set |
| มีสินค้าหลาย SKU ต้องการรีทาร์เก็ตอัตโนมัติ | Sales (Catalog) | Catalog Sales | ต้องมี Product Feed ที่อัปเดตสม่ำเสมอ |
| ธุรกิจหลายสาขา ต้องการ Foot Traffic เข้าร้าน | Sales (Store Traffic) | Store Visits | ต้องผูก Location ทุกสาขาใน Business Manager |
| ลูกค้าเก่าที่ซื้อไปแล้ว ต้องการให้ซื้อซ้ำ | Sales (Catalog Dynamic Retargeting) | Catalog Sales (Custom Audience: Purchasers) | Exclude คนที่ซื้อสินค้าตัวเดิมไปแล้วถ้าไม่ใช่สินค้าซื้อซ้ำได้ |

---

## คำถามที่พบบ่อย (FAQ)

**ถาม: ถ้าไม่แน่ใจว่าจะเลือก Objective อะไร ควรทำอย่างไร?**
ตอบ: กลับไปตอบคำถามพื้นฐาน 2 ข้อก่อนเสมอ — (1) ธุรกิจนี้อยู่ใน Funnel Stage ไหน (คนรู้จักแบรนด์แล้วหรือยัง มี Pixel Data พอหรือไม่) และ (2) ผลลัพธ์ทางธุรกิจที่วัดผลได้จริงคืออะไร (ยอดขาย ลีด หรือการรู้จักแบรนด์) ตอบสองคำถามนี้ให้ชัดก่อน แล้วใช้ตารางตัดสินใจด้านบนเทียบ

**ถาม: สามารถรันหลาย Objective พร้อมกันในบัญชีเดียวได้หรือไม่?**
ตอบ: ได้แน่นอน และควรทำด้วยซ้ำ เพราะธุรกิจส่วนใหญ่ต้องมี Full-Funnel ที่มีทั้ง TOF (Awareness/Engagement) MOF (Traffic/Leads) และ BOF (Sales) วิ่งพร้อมกันตลอดเวลา เพียงแต่แต่ละ Objective ต้องแยก Campaign กันชัดเจน ไม่ปนกันใน Campaign เดียว

**ถาม: เปลี่ยน Objective กลางแคมเปญได้หรือไม่ ถ้าทำแล้วจะเกิดอะไรขึ้น?**
ตอบ: ในทางเทคนิค Meta ไม่อนุญาตให้เปลี่ยน Objective ของ Campaign ที่สร้างไปแล้ว (Objective ถูกล็อกตั้งแต่สร้าง Campaign) ถ้าต้องการเปลี่ยนต้องสร้าง Campaign ใหม่ทั้งลูก ซึ่งหมายความว่า Learning Phase จะเริ่มนับใหม่ทั้งหมด ดังนั้นการตัดสินใจเลือก Objective ตั้งแต่แรกจึงสำคัญมาก

**ถาม: Objective ใดที่เหมาะกับธุรกิจงบน้อยที่สุด (ต่ำกว่า 300 บาท/วัน)?**
ตอบ: โดยทั่วไปแนะนำเริ่มที่ Traffic หรือ Engagement ก่อนเพื่อสร้างข้อมูลพื้นฐานในราคาที่ประหยัด แล้วค่อยขยับไป Sales เมื่องบเพิ่มขึ้นหรือมี Pixel Data สะสมพอ การยิง Sales Objective ตรงด้วยงบต่ำมากอาจทำให้ Learning Phase ไม่จบเพราะได้ Purchase ต่อสัปดาห์ไม่พอ

**ถาม: ทำไมบางครั้งเลือก Objective เดียวกัน แต่ผลลัพธ์ในบัญชีต่างกันมาก?**
ตอบ: เพราะปัจจัยอื่นที่ไม่ใช่ Objective ก็มีผลมหาศาล เช่น คุณภาพครีเอทีฟ ขนาด Audience ความแข่งขันในตลาด (Auction Competition) และที่สำคัญคือ Optimization Goal ย่อยที่เลือกไว้ใน Ad Set ตามที่อธิบายใน Step 168 — Objective เหมือนกันแต่ Optimization Goal ต่างกัน ผลลัพธ์ต่างกันได้มาก

---

## Checklist ท้ายบท

- [ ] เข้าใจความแตกต่างของ 6 Objective หลักใน ODAX: Awareness, Traffic, Engagement, Leads, App Promotion, Sales
- [ ] รู้ว่า Objective แต่ละตัวมี Optimization Goal ย่อยอะไรบ้าง และเลือกใช้ตัวที่เหมาะสม ไม่ใช่ปล่อย Default
- [ ] เข้าใจความแตกต่างของ Landing Page Views vs Link Clicks และรู้ว่าเมื่อไหร่ต้องใช้ตัวไหน
- [ ] เข้าใจความแตกต่างของ ThruPlay vs 2-Second Video View
- [ ] เข้าใจความแตกต่างของ Instant Form vs Website Leads และเลือกให้เหมาะกับราคาสินค้า/Sales Cycle
- [ ] รู้ว่า App Promotion ต้องมี MMP ก่อนเริ่มยิงเสมอ
- [ ] เข้าใจ 3 รูปแบบของ Sales Objective: Website Conversions, Catalog Sales, Store Traffic
- [ ] สามารถแมป Objective เข้ากับ Funnel Stage (TOF/MOF/BOF/Retention) ได้
- [ ] ตรวจสอบ Optimization Goal ที่ Ad Set Level ทุกครั้ง ไม่ดูแค่ชื่อ Objective ที่ Campaign Level
- [ ] ไม่สลับ Objective กลางแคมเปญที่กำลังรันอยู่โดยไม่จำเป็น เพราะจะรีเซ็ต Learning Phase

---

## Workshop / แบบฝึกหัด

**โจทย์:** ให้เลือก Objective + Optimization Goal ที่เหมาะสมที่สุดสำหรับ 5 สถานการณ์ธุรกิจต่อไปนี้ พร้อมอธิบายเหตุผล 2-3 ข้อสำหรับแต่ละเคส

1. **เคส A:** แบรนด์เครื่องสำอางออนไลน์ใหม่ ยังไม่มี Pixel ติดตั้งเลย งบ 500 บาท/วัน ต้องการเริ่มสร้างฐานลูกค้า
2. **เคส B:** ร้านขายรองเท้าออนไลน์ มี Pixel สมบูรณ์ Purchase Event เฉลี่ย 40 ครั้ง/สัปดาห์ ต้องการเพิ่มยอดขายช่วง Double Day
3. **เคส C:** คลินิกทำฟันเปิดใหม่ ต้องการลีดคนสนใจจัดฟัน งบ 800 บาท/วัน ราคาคอร์สจัดฟันเริ่ม 35,000 บาท
4. **เคส D:** เพจขายของมือสองที่มี Engagement ต่ำมาก อยากให้โพสต์ขายดูน่าเชื่อถือขึ้นก่อนยิงจริง
5. **เคส E:** ร้านสะดวกซื้อเชนมี 15 สาขาในกรุงเทพฯ ต้องการให้คนแวะเข้าร้านช่วงโปรโมชั่นสิ้นเดือน

**วิธีส่งงาน:** เขียนคำตอบแต่ละเคสในรูปแบบ "Objective → Optimization Goal → เหตุผล" ลงในสมุดบันทึกของคุณ แล้วเทียบกับเฉลยแนวทางด้านล่าง

**เฉลยแนวทางแบบละเอียด:**

**เคส A — เครื่องสำอางออนไลน์ใหม่ ไม่มี Pixel งบ 500 บาท/วัน**
- Objective: Traffic (Optimization = Link Clicks เพราะยังไม่มี Pixel ที่จะยิง Landing Page Views ได้แม่นยำ) ควบคู่กับ Engagement (ThruPlay) สลับสัปดาห์
- เหตุผล: (1) ไม่มี Pixel แปลว่ายังไม่มีข้อมูล Conversion ให้ Sales Objective เรียนรู้เลย (2) งบ 500 บาท/วันเล็กเกินไปสำหรับ Ad Recall Lift (3) ต้องรีบติดตั้ง Pixel ทันทีคู่ขนานไปกับการยิง Traffic เพื่อให้มีข้อมูลพร้อมขยับไป Sales ใน 2-3 สัปดาห์ถัดไป

**เคส B — ร้านรองเท้าออนไลน์ Pixel สมบูรณ์ Purchase 40 ครั้ง/สัปดาห์ ต้องการเพิ่มยอดขาย Double Day**
- Objective: Sales (Optimization = Conversions เป็นหลัก หรือ Value ถ้าสินค้ามีช่วงราคาหลากหลายและอยากได้ ROAS สูงสุด)
- เหตุผล: (1) มีข้อมูล Purchase มากพอ (เกิน 25 ครั้ง/สัปดาห์ตามเกณฑ์ Learning Phase) (2) ช่วง Double Day ควรเพิ่มงบล่วงหน้า 3-5 วันก่อนวันจริงเพื่อให้ Learning Phase เสถียรก่อนวันเดโพรโมชั่นสูงสุด (3) ควรมี Ad Set แยกสำหรับ Retargeting ผู้ที่เคย Add to Cart แต่ไม่ Purchase โดยเฉพาะ เพราะช่วง Double Day คนมักรอเปรียบเทียบราคา

**เคส C — คลินิกทำฟันเปิดใหม่ ราคาคอร์ส 35,000 บาท งบ 800 บาท/วัน**
- Objective: Leads (Optimization = Conversion Leads ผ่านเว็บไซต์/LINE OA พร้อมคำถามคัดกรองงบประมาณและช่วงเวลาที่สนใจ)
- เหตุผล: (1) ราคาสูงมาก ต้องการคุณภาพลีดเหนือปริมาณ (2) Instant Form อย่างเดียวจะได้ลีดจำนวนมากที่ไม่มีกำลังซื้อจริงปนมาก (3) ควรตั้งคำถามคัดกรอง เช่น "งบประมาณที่วางแผนไว้สำหรับการจัดฟัน" เพื่อกรองลีดตั้งแต่ต้นทาง

**เคส D — เพจขายของมือสอง Engagement ต่ำ**
- Objective: Engagement (Optimization = Post Engagement) ระยะสั้น 3-5 วันก่อน จากนั้นขยับไป Sales หรือ Traffic ตามความพร้อมของ Pixel
- เหตุผล: (1) ต้องสร้าง Social Proof (คอมเมนต์ ไลก์ แชร์) ให้โพสต์ดูน่าเชื่อถือก่อน เพราะ Engagement ต่ำมากทำให้คนที่เห็นโพสต์ครั้งแรกไม่มั่นใจจะซื้อ (2) ใช้ระยะสั้นเท่านั้น ไม่ควรยืดยาวเพราะ Engagement ไม่ใช่เป้าหมายสุดท้ายของธุรกิจ

**เคส E — ร้านสะดวกซื้อเชน 15 สาขา ต้องการ Foot Traffic ช่วงโปรโมชั่นสิ้นเดือน**
- Objective: Sales (Optimization = Store Visits/Store Traffic) เจาะ Location รัศมี 3-5 กม. รอบแต่ละสาขา
- เหตุผล: (1) ธุรกิจมีหลายสาขาจริง ต้องการวัดผลที่ Foot Traffic ไม่ใช่ Online Purchase (2) ควรผูก Location ทุกสาขาไว้ใน Business Manager ล่วงหน้าและตั้งครีเอทีฟที่ระบุโปรโมชั่นชัดเจนพร้อมวันที่มีผล (3) ควรเริ่มยิงล่วงหน้า 3-4 วันก่อนสิ้นเดือนเพื่อให้คนวางแผนมาได้ทัน

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ปูพื้นฐานสำคัญที่สุดอย่างหนึ่งของการยิงแอด Facebook คือ **การเลือก Objective ที่ตรงกับ Funnel Stage และเป้าหมายทางธุรกิจจริง** ไม่ใช่เลือกตามราคาที่ดูถูกที่สุด เราได้เรียนรู้ทั้ง 6 Objective หลัก ความสัมพันธ์กับ Optimization Goal และกรอบการตัดสินใจที่ใช้ได้จริงในสนาม

แต่การเลือก Objective ถูกต้องเพียงอย่างเดียวยังไม่พอ — ต้องมี **งบประมาณที่เพียงพอและ Bid Strategy ที่เหมาะสม** เพื่อให้ Machine Learning มีโอกาสทำงานได้เต็มที่ ใน **Part 018: งบประมาณ (Budget) แบบต่างๆ และ Bid Strategy เบื้องต้น** เราจะเจาะลึกเรื่อง Daily Budget vs Lifetime Budget, CBO vs ABO, และ Bid Strategy ทั้ง 4 แบบ (Lowest Cost, Cost Cap, Bid Cap, ROAS Goal) พร้อม Workshop วางแผนงบประมาณแคมเปญ 30 วันแบบมีตัวเลขจริงให้ฝึกคำนวณ

---

## ตารางสรุปเปรียบเทียบทั้ง 6 Objective (Quick Reference)

ตารางนี้ออกแบบให้ปริ้นแขวนไว้ข้างจอสำหรับใช้อ้างอิงเร็วๆ เวลาสร้างแคมเปญจริง:

| Objective | เหมาะกับ Funnel Stage | ตัวอย่างธุรกิจที่เหมาะ | สิ่งที่ต้องมีก่อนใช้ | ความเสี่ยงถ้าใช้ผิด |
|---|---|---|---|---|
| Awareness | TOF | แบรนด์ใหม่, เปิดสาขาใหม่, Sales Cycle ยาว | งบพอสำหรับ Reach ฐานใหญ่ | เสียงบไปกับคนที่ไม่มีวันซื้อ |
| Traffic | TOF-MOF | Content Site, Landing Page ข้อมูล, สร้าง Pixel Data เริ่มต้น | Pixel ติดตั้งสมบูรณ์ (ถ้าจะใช้ LPV) | ได้ทราฟฟิกไม่มีคุณภาพถ้าใช้แทน Sales |
| Engagement | TOF-MOF | เพจใหม่ที่ Engagement ต่ำ, สร้าง Video Pool | ครีเอทีฟที่กระตุ้นการมีส่วนร่วมได้จริง | ติดกับ Vanity Metric ไม่มีจุดจบ |
| Leads | MOF-BOF | อสังหาฯ, ประกัน, การศึกษา, B2B, คลินิก | คำถามคัดกรอง + ทีม Follow-up เร็ว | ได้ลีดไม่มีคุณภาพ เสียเวลาเซลส์ |
| App Promotion | TOF-BOF (เฉพาะแอป) | Fintech App, e-Commerce App, Game | MMP เชื่อมต่อแล้ว, Deep Linking พร้อม | วัดผลไม่ได้เลยถ้าไม่มี MMP |
| Sales | BOF-Retention | E-commerce, ร้านค้าปลีกหลายสาขา, ธุรกิจที่มี Pixel พร้อม | Purchase Event ≥ 15-25 ครั้ง/สัปดาห์/Ad Set | Learning Phase ไม่จบถ้าข้อมูลน้อยเกินไป |

## กรอบคิดสุดท้ายก่อนสร้างแคมเปญทุกครั้ง

ก่อนกดสร้าง Campaign ใหม่ทุกครั้ง ให้ถามตัวเอง 4 คำถามนี้ตามลำดับ:

1. **ธุรกิจนี้อยู่ตรงไหนของ Funnel ในตอนนี้?** (ยังไม่มีใครรู้จัก / มีคนสนใจแล้วแต่ยังไม่ซื้อ / มี Retargeting Pool พร้อมปิดขาย)
2. **มีข้อมูล Pixel/Conversion เพียงพอให้ Machine Learning เรียนรู้ Objective ที่อยากใช้หรือยัง?** (ถ้ายังไม่พอ ให้ลดระดับ Objective ลงมาก่อนชั่วคราว)
3. **ผลลัพธ์ที่วัดความสำเร็จของ Objective นี้คืออะไร ไม่ใช่แค่ยอดขายอย่างเดียว?** (ตามตาราง Cross-Objective Attribution ด้านบน)
4. **Objective นี้จะเชื่อมต่อไปสู่ Objective ขั้นต่อไปอย่างไร?** (ทุก Objective ควรมีแผนต่อยอด ไม่ใช่จบแค่ตัวเดียวลอยๆ)

ตอบ 4 คำถามนี้ได้ครบ = พร้อมสร้างแคมเปญที่มีทิศทางชัดเจน ไม่ใช่แคมเปญที่ยิงไปแบบเดา

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center: "About campaign objectives" — เอกสารทางการอัปเดตล่าสุดเรื่อง ODAX (Outcome-Driven Ad Experiences)
- Meta Business Help Center: "About the Value optimization goal"
- Meta Business Help Center: "About Advantage+ catalog ads"
- Meta Business Help Center: "About Store Traffic objective"
- Meta for Developers: SKAdNetwork Overview (สำหรับ App Promotion บน iOS)
- Meta Business Help Center: "About Instant Forms for lead ads" และ "Best practices for lead ads"
- Meta Business Help Center: "About video ad optimization goals: ThruPlay and 2-second continuous video views"
- สังเกตการเปลี่ยนแปลง Objective ใหม่ๆ ผ่าน Meta Ads Manager Release Notes ที่อัปเดตทุก 1-2 เดือน เนื่องจาก Meta ปรับโครงสร้าง ODAX อยู่เรื่อยๆ
- ติดตามกลุ่ม Facebook Ads Practitioner ในไทย (เช่น กลุ่ม Facebook Ads Thailand) เพื่อดูเคสจริงที่คนอื่นเจอเมื่อ Meta อัปเดต Objective
