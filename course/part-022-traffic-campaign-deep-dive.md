# Part 022: สร้างแคมเปญ Traffic แบบละเอียด

**Section:** C — Facebook Ads Manager Deep Dive: Setup & Structure
**Step ที่ครอบคลุม:** 211–220 (จาก 1000 Steps ทั้งหมด)
**เวลาเรียนโดยประมาณ:** 5–6 ชั่วโมง (รวมเวลาลงมือทำ Workshop จริงใน Ads Manager)

Part 021 เราสร้างแคมเปญ Awareness แรกไปแล้ว รู้จักหน้าจอ Ads Manager และ Flow การสร้างแคมเปญครบทั้ง 3 ระดับ มาถึง Part นี้เราจะเจาะลึก Objective ที่นักยิงแอดใช้บ่อยที่สุดเป็นอันดับต้นๆ คือ **Traffic** — Objective ที่ออกแบบมาเพื่อ "ส่งคนไปที่ปลายทางที่คุณกำหนด" ไม่ว่าจะเป็นเว็บไซต์, แอป, Messenger หรือหมายเลขโทรศัพท์

Traffic Campaign มีจุดที่ซับซ้อนกว่า Awareness พอสมควร เพราะมี Optimization Goal ให้เลือกหลายแบบ มี Destination หลายประเภท และมีปัญหาเฉพาะตัวที่มือใหม่ (และมือเก่าที่ประมาท) มักเจอบ่อย เช่น Bot Click และ CPC ที่ดูถูกแต่ไม่ได้ Traffic คุณภาพจริง

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 211** — Traffic Objective คืออะไร และ Use Case ที่เหมาะสมในโลกจริง
2. **Step 212** — Optimization Goal: Link Clicks vs Landing Page Views vs Conversions เจาะลึกความแตกต่าง
3. **Step 213** — เลือก Destination Type: Website, App, Messenger/WhatsApp/Instagram, Calls
4. **Step 214** — ตั้งค่า UTM Parameters สำหรับ Traffic Campaign แบบละเอียดทุก Field
5. **Step 215** — Budget และ Bid Strategy สำหรับ Traffic — จุดที่ต่างจาก Awareness
6. **Step 216** — Creative Considerations สำหรับ Traffic Ads ที่ต้องต่างจาก Awareness
7. **Step 217** — ปัญหาที่พบบ่อยของ Traffic Campaign: Bot Click, CPC สูง, Junk Traffic
8. **Step 218** — อ่าน Metrics ของ Traffic Campaign อย่างมืออาชีพ (CTR, CPC, Landing Page View Rate)
9. **Step 219** — เมื่อไหร่ Traffic Campaign คือตัวเลือกที่ผิด และควรใช้ Objective อื่นแทน
10. **Step 220** — Workshop: สร้าง Traffic Campaign เต็มรูปแบบพร้อม UTM Tracking

---

## Step 211: Traffic Objective คืออะไร และ Use Case ที่เหมาะสมในโลกจริง

### นิยามที่ต้องเข้าใจให้ถูก

Traffic Objective คือ Objective ที่ Meta ออกแบบมาเพื่อ **"เพิ่มจำนวนคนที่ไปยังปลายทางที่คุณกำหนด"** ไม่ว่าปลายทางนั้นจะเป็นเว็บไซต์ภายนอก, หน้า Landing Page, แอปมือถือ, กล่องแชท Messenger/WhatsApp/Instagram Direct หรือแม้แต่การกดโทรออก

จุดที่มือใหม่เข้าใจผิดบ่อยที่สุดคือคิดว่า Traffic = "แคมเปญขายของ" ทั้งที่จริงแล้ว Traffic Objective **ไม่ได้ Optimize เพื่อการซื้อ** โดยตรง มันแค่พยายามส่งคน "ไปให้ถึง" ปลายทางให้ได้มากที่สุดในงบที่กำหนด ส่วนคนที่ไปถึงแล้วจะซื้อหรือไม่ ไม่ใช่สิ่งที่ Machine Learning ของ Traffic Campaign ใช้เป็นสัญญาณหลักในการหา Audience (ต่างจาก Sales/Conversion Objective ที่จะเรียนใน Part 026 ซึ่ง Optimize เพื่อ Purchase Event ตรงๆ)

### Use Case ที่เหมาะสมกับ Traffic Objective

1. **ธุรกิจที่มี Content/บทความอยากให้คนอ่าน** — เว็บข่าว, บล็อก, สื่อที่มีรายได้จาก Ad Impression บนเว็บตัวเอง (ยิ่งมีคนเข้าเว็บมาก ยิ่งมีรายได้จากโฆษณาบนเว็บ)
2. **ธุรกิจที่ต้องการทดสอบ Landing Page ก่อนไปทำ Conversion Campaign จริงจัง** — ยิงงบน้อยๆ ดู Bounce Rate, Time on Page ก่อนเทงบหนักเข้า Conversion
3. **ธุรกิจที่ Pixel ยังไม่มีข้อมูล Conversion เพียงพอ** — Sales Objective ต้องการ Purchase Event สะสมอย่างน้อยประมาณ 20–50 ครั้ง/สัปดาห์ถึงจะ Optimize ได้ดี ถ้ายังไม่มีข้อมูลระดับนั้น การเริ่มด้วย Traffic เพื่อ "อุ่น" เว็บไซต์และเก็บ Pixel Data ไปพลางๆ เป็นทางเลือกที่สมเหตุสมผล
4. **แคมเปญที่ต้องการ Drive คนไปยัง Messenger/WhatsApp เพื่อเริ่มบทสนทนาขาย** — สำหรับธุรกิจที่ปิดการขายผ่านแชท ไม่ใช่ผ่านเว็บ
5. **ธุรกิจที่ต้องการวัด "ความสนใจเบื้องต้น"** — เช่น เปิดตัวสินค้าใหม่ อยากรู้ว่ามีคนสนใจกดเข้าไปดูรายละเอียดกี่คน ก่อนตัดสินใจลงทุนด้าน Creative/Content เพิ่ม

### เมื่อไหร่ที่ไม่ควรใช้ Traffic (สรุปสั้นๆ ก่อนเจาะลึกใน Step 219)

ถ้าเป้าหมายสุดท้ายคือ "ยอดขาย" และ Pixel มีข้อมูล Purchase สะสมมากพอ ควรข้ามไปใช้ Sales/Conversion Objective ตรงเลย เพราะ Traffic Campaign ไม่ได้ถูกออกแบบมาให้ Machine Learning มองหาคนที่ "มีโอกาสซื้อ" แต่มองหาคนที่ "มีโอกาสคลิก" ซึ่งเป็นคนละกลุ่มกัน (คนที่ชอบคลิกลิงก์เยอะๆ ไม่ได้แปลว่าเป็นคนที่จะควักเงินซื้อ)

### ตารางเปรียบเทียบ Traffic vs Objective อื่นที่ใกล้เคียง

| ประเด็น | Traffic | Engagement | Sales (Conversion) |
|---|---|---|---|
| Optimize เพื่อ | คลิก/เข้าเว็บ | ปฏิสัมพันธ์กับโพสต์ | การซื้อ/Event เป้าหมาย |
| ต้องมี Pixel ข้อมูลมากไหม | ไม่จำเป็นมาก | ไม่จำเป็น | จำเป็นมาก (ยิ่งมากยิ่งดี) |
| เหมาะกับช่วง Funnel | Top-Mid Funnel | Top Funnel | Bottom Funnel |
| วัดผลด้วย ROAS ได้ตรงไหม | ไม่ตรง ต้องดู Pixel แยก | ไม่ตรง | ตรงที่สุด |

### ข้อผิดพลาดที่พบบ่อย

- เข้าใจว่า Traffic = แคมเปญขายของ แล้วคาดหวัง ROAS สูงเหมือน Conversion Campaign
- ใช้ Traffic กับธุรกิจที่มี Pixel ข้อมูลสมบูรณ์แล้ว ทั้งที่ควรข้ามไป Conversion Objective ตรงเพื่อประสิทธิภาพที่ดีกว่า
- ไม่รู้ว่า Traffic Campaign มี Optimization Goal ย่อยหลายแบบ (จะเรียนใน Step 212) แล้วปล่อยให้ระบบเลือก Default ให้โดยไม่พิจารณา

### เจาะลึกเพิ่ม: Traffic Objective ในมุมมอง Funnel Stage

ถ้ามองผ่านกรอบ Marketing Funnel (Awareness → Consideration → Conversion → Loyalty ที่เรียนใน Part 005 Step 41) Traffic Objective มักอยู่ตรงกลางระหว่าง Awareness กับ Consideration — มันไม่ใช่แค่ "ให้คนรู้จัก" (นั่นคือ Awareness) แต่ก็ยังไม่ถึงขั้น "ให้คนซื้อ" (นั่นคือ Conversion) มันคือขั้นตอนที่คนเริ่มมีความสนใจในระดับที่ยอมสละเวลากดคลิกเพื่อไปดูข้อมูลเพิ่ม ซึ่งเป็นสัญญาณของ Intent ที่แรงกว่าการแค่ดูโฆษณาเฉยๆ

การเข้าใจตำแหน่งนี้สำคัญเพราะมันบอกเราว่า **Traffic Campaign ไม่ควรถูกใช้เป็น Objective เดียวตลอด Funnel** — ควรใช้ร่วมกับ Retargeting Campaign (ที่จะเรียนเจาะลึกใน Part 049) เพื่อดึงคนที่คลิกเข้าเว็บแล้วแต่ยังไม่ซื้อ กลับมาอีกครั้งด้วย Offer ที่แรงขึ้น

### เจาะลึกเพิ่ม: ต้นทุนเปรียบเทียบระหว่าง Traffic และ Conversion Campaign ในธุรกิจเดียวกัน

สมมติธุรกิจหนึ่งใช้งบ 1,000 บาทเท่ากันในสองแคมเปญคู่ขนาน (Split Test):

| | Traffic Campaign | Conversion Campaign |
|---|---|---|
| Link Clicks ที่ได้ | 280 | 190 |
| CPC | 3.57 บาท | 5.26 บาท |
| Purchase ที่เกิดขึ้นจริง | 3 | 9 |
| Cost per Purchase | 333 บาท | 111 บาท |

ตัวเลขนี้แสดงให้เห็นชัดว่า Traffic Campaign ได้คลิกมากกว่าและ CPC ถูกกว่า แต่ **คุณภาพของคนที่คลิกมีโอกาสซื้อต่ำกว่ามาก** เพราะระบบไม่ได้ Optimize เพื่อการซื้อ ทำให้ต้นทุนต่อการขาย 1 ครั้ง (Cost per Purchase) ของ Traffic สูงกว่า Conversion ถึง 3 เท่าในตัวอย่างนี้ — นี่คือเหตุผลเชิงตัวเลขที่สนับสนุนหลักการใน Step 219 ว่าเมื่อพร้อมแล้วต้องย้ายไป Conversion Objective

---

## Step 212: Optimization Goal — Link Clicks vs Landing Page Views vs Conversions เจาะลึกความแตกต่าง

หลังเลือก Objective = Traffic และไปถึงระดับ Ad Set ส่วน **"Conversion location"** จะให้เลือกก่อนว่าปลายทางคือที่ไหน (Website, App, Messenger ฯลฯ — จะเจาะลึกใน Step 213) จากนั้นถ้าเลือก Website จะมีส่วน **"Performance goal"** ให้เลือก Optimization Goal ย่อย ซึ่งเป็นจุดตัดสินใจที่สำคัญที่สุดของ Traffic Campaign

### ตัวเลือกที่ 1: Link Clicks

ระบบจะ Optimize เพื่อหาคนที่ **"มีโอกาสคลิกลิงก์"** มากที่สุด โดยไม่สนใจว่าหลังคลิกแล้วหน้าเว็บจะโหลดสำเร็จหรือไม่

**ข้อดี:** ได้จำนวนคลิกเยอะในงบเท่ากัน, CPC ต่ำที่สุดในบรรดา 3 ตัวเลือกนี้ (เพราะระบบไม่ต้องการสัญญาณเพิ่มเติมอะไรมาก แค่หา "คนชอบคลิก")

**ข้อเสีย:** เสี่ยงได้ Traffic คุณภาพต่ำมากที่สุด เพราะ "คนชอบคลิก" ไม่ได้แปลว่า "คนที่หน้าเว็บโหลดสำเร็จแล้วอ่านต่อ" จำนวนมากอาจเป็นคนที่กดพลาด, กดเพราะ Curiosity ชั่วครู่แล้วปิดทันทีที่หน้าเว็บกำลังโหลด หรือแม้แต่ Traffic จาก Connection ที่ช้า/ไม่แน่นอน (มือถือสัญญาณอ่อน) ซึ่งนับเป็น "Click" แต่ไม่ถึงหน้าเว็บจริง

### ตัวเลือกที่ 2: Landing Page Views

ระบบจะ Optimize เพื่อหาคนที่ **"มีโอกาสคลิกลิงก์ และหน้าเว็บโหลดสำเร็จจริง"** (ต้องมี Pixel ติดตั้งอยู่บนเว็บไซต์เพื่อให้ระบบรู้ว่าหน้าเว็บโหลดสำเร็จ)

**ข้อดี:** คุณภาพ Traffic ดีกว่า Link Clicks อย่างชัดเจน เพราะกรองคนที่กดแล้วหน้าเว็บไม่โหลด (Connection แย่, กดผิดแล้วปิดทันที) ออกไปจากการนับผลลัพธ์

**ข้อเสีย:** CPC จะสูงกว่า Link Clicks เล็กน้อยถึงปานกลาง เพราะระบบต้องการสัญญาณที่แม่นยำกว่า (ต้องรอ Pixel ยืนยัน Page Load)

**คำแนะนำ:** สำหรับเว็บไซต์ที่ติดตั้ง Pixel แล้ว **แนะนำเลือก Landing Page Views เป็นค่า Default เสมอ** ยกเว้นกรณีที่ยังไม่ติดตั้ง Pixel เลย (ซึ่งไม่ควรเกิดขึ้นถ้าคุณเรียนตาม Part 013–015 มาแล้ว)

### ตัวเลือกที่ 3: Conversions (ภายใต้ Traffic Objective)

บางเวอร์ชัน UI จะให้เลือก Optimization Goal ลึกไปถึง **Conversions** ได้แม้อยู่ใน Traffic Objective (เลือก Conversion Event เช่น ViewContent, AddToCart) ระบบจะพยายามหาคนที่มีโอกาสทำ Event นั้นมากที่สุด แม้ Objective หลักยังเป็น Traffic

**ข้อควรระวัง:** ตัวเลือกนี้ต้องการ Event สะสมเพียงพอ (Meta แนะนำ Custom Conversion หรือ Standard Event ที่เกิดขึ้นบ่อยพอ) ถ้า Event เกิดน้อยเกินไป ระบบจะ Optimize ได้ไม่ดีและอาจเจอ Learning Limited (ที่เรียนใน Part 009 Step 86)

### ตารางสรุปเปรียบเทียบ 3 ตัวเลือก

| Optimization Goal | ต้องมี Pixel | คุณภาพ Traffic | CPC | เหมาะกับ |
|---|---|---|---|---|
| Link Clicks | ไม่จำเป็น | ต่ำที่สุด | ต่ำที่สุด | เว็บที่ยังไม่มี Pixel, ต้องการ Volume คลิกเยอะราคาถูก |
| Landing Page Views | จำเป็น | ปานกลาง-ดี | ปานกลาง | ค่า Default ที่แนะนำสำหรับเว็บที่มี Pixel |
| Conversions (ภายใน Traffic) | จำเป็นมาก + Event สะสมพอ | ดีที่สุด (ในกลุ่ม Traffic) | สูงที่สุด | เว็บที่มี Pixel Data ปานกลาง อยากได้คุณภาพสูงขึ้นแต่ยังไม่พร้อมสำหรับ Sales Objective เต็มรูปแบบ |

### ข้อผิดพลาดที่พบบ่อย

- ปล่อยให้ระบบเลือก Default เป็น Link Clicks ทั้งที่เว็บมี Pixel ติดตั้งสมบูรณ์แล้ว ทำให้เสียโอกาสได้ Traffic คุณภาพดีกว่าในราคาที่ต่างกันไม่มาก
- เลือก Conversions Optimization Goal ทั้งที่ Event สะสมยังน้อยเกินไป ทำให้ระบบหา Audience ไม่เจอ CPC พุ่งสูงผิดปกติ
- ไม่เข้าใจว่า Optimization Goal คือสิ่งที่กำหนดว่า "ระบบไปหาคนแบบไหน" ไม่ใช่แค่ Metric ที่โชว์ผลลัพธ์

### เจาะลึกเพิ่ม: ตำแหน่งที่แท้จริงของ Field เหล่านี้ใน UI (สำหรับผู้ที่หา Field ไม่เจอ)

ลำดับที่แนะนำให้ไล่หาในหน้า Ad Set (จากบนลงล่าง) คือ:

1. **Conversion location** (มักอยู่บนสุดของหน้า Ad Set หลัง Audience) — เลือก Website/App/Messenger/Calls ก่อนอันดับแรก
2. **Performance goal** — ปรากฏต่อจาก Conversion location ทันที เป็น Dropdown ให้เลือก Link Clicks/Landing Page Views/Conversions/Impressions (ตัวเลือกจะเปลี่ยนไปตาม Conversion Location ที่เลือกไว้ก่อนหน้า)
3. ถ้าเลือก Performance Goal = Conversions จะมี Field เพิ่มขึ้นมาคือ **"Conversion event"** ให้เลือก Event เฉพาะ (เช่น ViewContent, AddToCart) จาก Pixel ที่เชื่อมกับ Ad Account นี้

**ข้อสังเกตสำคัญ:** ถ้าคุณยังไม่ได้เลือก Pixel ให้กับ Ad Account หรือยังไม่เชื่อม Pixel ตัวเลือก "Conversions" และ "Landing Page Views" อาจไม่ปรากฏให้เลือกเลย จะเห็นแค่ "Link Clicks" เพียงอย่างเดียว — นี่เป็นสัญญาณเตือนว่าต้องกลับไปตรวจสอบการเชื่อม Pixel ใน Events Manager (Part 013–015) ก่อนสร้างแคมเปญต่อ

### เจาะลึกเพิ่ม: Impressions เป็น Optimization Goal ได้ไหม

บางครั้งในหน้า Performance Goal จะมีตัวเลือก **"Impressions"** ปรากฏขึ้นมาด้วย (ให้ระบบแสดงโฆษณาให้มากที่สุดโดยไม่สนใจว่าจะมีคนคลิกหรือไม่) ตัวเลือกนี้ **ไม่แนะนำสำหรับ Traffic Campaign เกือบทุกกรณี** เพราะขัดกับเจตนาของ Objective นี้โดยตรง (ถ้าต้องการ Optimize เพื่อการแสดงผลอย่างเดียว ควรกลับไปใช้ Awareness Objective ที่ Part 021 แทน) ตัวเลือกนี้มักปรากฏเป็น Fallback ทางเทคนิคเท่านั้น ไม่ใช่ตัวเลือกที่ควรใช้งานจริง

---

## Step 213: เลือก Destination Type — Website, App, Messenger/WhatsApp/Instagram, Calls

ก่อนไปถึง Performance Goal ตามที่เรียนใน Step 212 จะต้องเลือก **"Conversion location"** ก่อนเสมอ ซึ่งเป็นตัวกำหนดปลายทางที่คนจะถูกส่งไป

### Website

ตัวเลือกที่ใช้บ่อยที่สุด — คนคลิกโฆษณาแล้วเปิดเบราว์เซอร์ไปที่ URL ที่กำหนดไว้ในช่อง Destination URL ของแต่ละ Ad ต้องมี Pixel ติดตั้งบนเว็บนั้นเพื่อให้เลือก Landing Page Views หรือ Conversions Goal ได้

### App

สำหรับธุรกิจที่มีแอปมือถือ คนคลิกโฆษณาแล้วจะถูกพาไปที่ App Store/Play Store เพื่อดาวน์โหลด หรือถ้ามีแอปอยู่แล้วในเครื่อง จะเปิดแอปตรงไปยังหน้าที่กำหนด (Deep Link) ต้องเชื่อม App Events SDK ไว้ล่วงหน้า (จะเรียนเจาะลึกใน Part 028 App Promotion)

### Messenger, WhatsApp, Instagram Direct

คนคลิกโฆษณาแล้วจะเปิดกล่องแชทของแพลตฟอร์มที่เลือกโดยตรง พร้อมข้อความเริ่มต้น (Prefilled Message) ที่คุณตั้งไว้ล่วงหน้าได้ เหมาะกับธุรกิจที่ปิดการขายผ่านแชท (จะเรียนเจาะลึกเต็ม Part ใน Part 025 — Messages Objective) แต่สามารถเลือกเป็น Destination ของ Traffic Campaign ได้เช่นกันถ้าต้องการเพียงแค่ "ดึงคนเข้าแชท" โดยไม่จำเป็นต้องวัด Lead แบบเป็นระบบ

### Calls (การโทร)

คนคลิกโฆษณาบนมือถือแล้วเครื่องจะเปิดหน้าโทรออกไปยังหมายเลขที่กำหนดไว้ทันที เหมาะกับธุรกิจที่ปิดการขายทางโทรศัพท์เป็นหลัก เช่น ธุรกิจบริการซ่อมด่วน, คลินิกที่นัดผ่านโทรศัพท์ Destination นี้ใช้ได้เฉพาะบนอุปกรณ์มือถือเท่านั้น (บน Desktop จะไม่แสดงตัวเลือกนี้ในการคลิก)

### วิธีเลือก Destination ให้ตรงกับ Business Model

ให้ถามตัวเองว่า "ลูกค้าปิดการขายที่ไหน" — ถ้าปิดผ่านเว็บ (มี Cart, Checkout) เลือก Website ถ้าปิดผ่านแชท เลือก Messenger/WhatsApp/IG ถ้าปิดผ่านโทรศัพท์ เลือก Calls การเลือก Destination ผิดจาก Business Model จริงจะทำให้ Traffic ที่ได้ไปแล้วไม่มีทางปิดการขายได้ (เช่น ส่งคนไปเว็บ แต่เว็บไม่มี Checkout ต้องทักแชทเพื่อสั่งซื้อ — ทำให้เสีย Step ที่ไม่จำเป็นออกไปโดยเปล่าประโยชน์)

### ข้อผิดพลาดที่พบบ่อย

- เลือก Website Destination ทั้งที่ธุรกิจปิดการขายผ่านแชทเป็นหลัก ทำให้คนต้องกดออกจากเว็บไปเปิดแชทอีกที เสีย Conversion Rate ไปมากในขั้นตอนที่ไม่จำเป็น
- ไม่ตั้ง Prefilled Message สำหรับ Destination Messenger ทำให้ลูกค้าไม่รู้จะเริ่มพิมพ์อะไรก่อน
- ตั้ง Calls Destination แต่ไม่ได้เตรียมทีมรับสายให้พร้อมในช่วงที่แคมเปญวิ่ง ทำให้พลาดสายที่มีคุณภาพ

### เจาะลึกเพิ่ม: การตั้งค่า Prefilled Message สำหรับ Messenger/WhatsApp Destination

เมื่อเลือก Destination เป็น Messenger, WhatsApp หรือ Instagram Direct ในหน้า Ad Level จะมีส่วน **"Message template"** ให้เลือก:

- **Custom** — เขียนข้อความเริ่มต้นเองที่ลูกค้าจะเห็นเมื่อเปิดแชทมา (แนะนำให้ใส่คำถามที่ Guide ลูกค้าไปสู่การซื้อ เช่น "สวัสดีค่ะ สนใจดัมเบลรุ่นไหนคะ" ให้ลูกค้ากดตอบต่อได้ทันทีโดยไม่ต้องคิดว่าจะเริ่มพิมพ์อะไร)
- **Generic** — ใช้ Template มาตรฐานของ Meta ที่ออกแบบมาให้เข้ากับบริบททั่วไป

นอกจากนี้ยังตั้งค่า **Quick Replies** ได้ (ปุ่มคำตอบสำเร็จรูปให้ลูกค้ากดเลือกแทนการพิมพ์) เช่น "ดูราคา", "สอบถามการจัดส่ง", "ดูสินค้าอื่น" ช่วยลด Friction ในการเริ่มบทสนทนาได้มาก (จะเรียนเจาะลึกเต็มรูปแบบใน Part 025)

### เจาะลึกเพิ่ม: Destination แบบ "Website" ที่แท้จริงมีตัวเลือกย่อยซ้อนอยู่

แม้เลือก Destination = Website แล้ว ยังมีรายละเอียดย่อยที่ต้องตั้งในระดับ Ad คือช่อง **"Website URL"** ต้องใส่ URL แบบเต็ม (รวม `https://`) ไม่ใช่แค่ชื่อโดเมน และควรใส่ URL ของหน้าที่เกี่ยวข้องตรงกับ Creative จริง (เช่น ถ้าโฆษณาสินค้า A ต้องพาไปหน้าสินค้า A โดยตรง ไม่ใช่หน้าแรกของเว็บที่ต้องให้ลูกค้าไปหาสินค้า A เอง) การพาไปหน้าแรกเว็บทั่วไปเป็นสาเหตุอันดับหนึ่งที่ทำให้ Landing Page View สูงแต่ AddToCart ต่ำ เพราะลูกค้าไม่รู้จะกดต่อไปทางไหน

---

## Step 214: ตั้งค่า UTM Parameters สำหรับ Traffic Campaign แบบละเอียดทุก Field

### ทำไม Traffic Campaign ต้องพึ่ง UTM มากกว่า Objective อื่น

Traffic Campaign เน้นส่งคนไปเว็บไซต์ ดังนั้นการรู้ว่า "คลิกที่มาจากเว็บ" นั้นมาจากแคมเปญ/Ad Set/Ad ไหนกันแน่ คือข้อมูลสำคัญที่สุดในการวิเคราะห์ผลลัพธ์ต่อใน Google Analytics 4 หรือเครื่องมือ Tracking อื่นที่ Ads Manager เองไม่ได้แสดงละเอียดพอ (Ads Manager จะรู้แค่ระดับ Facebook แต่ไม่รู้ว่าคนที่มาจากเว็บนั้นไปทำอะไรต่อในเว็บ ถ้าไม่เชื่อม Analytics)

### 5 Parameter หลักของ UTM

1. **utm_source** — แหล่งที่มา ระบุว่ามาจากไหน เช่น `facebook`
2. **utm_medium** — ประเภทสื่อ เช่น `paid_social` หรือ `cpc`
3. **utm_campaign** — ชื่อแคมเปญ ควรตรงกับชื่อ Campaign ใน Ads Manager (หรือย่อให้จำง่าย)
4. **utm_content** — ระบุ Ad/Creative ตัวไหน เหมาะกับตอนทำ A/B Test หลาย Creative
5. **utm_term** — (ใช้น้อยกับ Facebook เพราะไม่มี Keyword แบบ Search Ads) มักเว้นว่างหรือใช้ระบุ Audience/Ad Set แทน

### ตัวอย่าง URL ที่ต่อ UTM ครบ

```
https://www.beanandbrew.co.th/?utm_source=facebook&utm_medium=paid_social&utm_campaign=250926_TRF_เปิดสาขาลาดพร้าว&utm_content=Video_Hook3วิ_V1
```

**ข้อควรระวัง:** ห้ามใส่ภาษาไทยหรือช่องว่างในค่า UTM ตรงๆ (ต้อง URL-Encode) แนะนำใช้ค่าภาษาอังกฤษ/อักขระที่ปลอดภัยเสมอ เช่น เปลี่ยนเป็น `campaign_awareness_lat_phrao_v1` แทนการใส่ภาษาไทยลงไปตรงๆ ในค่า Parameter เพื่อป้องกันปัญหา Encoding ผิดพลาดเมื่อนำไปวิเคราะห์ต่อใน GA4

### วิธีตั้งค่าใน Ads Manager — ช่อง URL Parameters

ในหน้า Ad Level เลื่อนไปที่ **"Ad setup"** > กด **"Show more options"** เพื่อขยายเมนู Advanced จะเจอช่อง **"URL Parameters"** — วิธีที่แนะนำที่สุดคือใช้ **Dynamic Parameters ของ Meta** ที่แปลงค่าอัตโนมัติตามข้อมูลจริงของแคมเปญ:

```
utm_source=facebook&utm_medium=paid_social&utm_campaign={{campaign.name}}&utm_content={{ad.name}}&utm_term={{adset.name}}
```

`{{campaign.name}}`, `{{ad.name}}`, `{{adset.name}}` เป็น **Dynamic Parameter ที่ Meta จะแทนค่าด้วยชื่อจริงของ Campaign/Ad/Ad Set นั้นอัตโนมัติทุกครั้งที่คนคลิก** — นี่คือเหตุผลสำคัญอีกข้อว่าทำไม **Naming Convention (Step 203 ของ Part 021) ต้องทำให้ดีตั้งแต่ต้น** เพราะชื่อที่ตั้งไว้จะไปโชว์เป็นค่า UTM ใน GA4 โดยตรง ถ้าตั้งชื่อสับสนไว้ ข้อมูลใน GA4 ก็จะสับสนตามไปด้วย

### วิธีตรวจสอบว่า UTM ทำงานถูกต้อง

1. คลิกลิงก์โฆษณาตัวอย่าง (หรือใช้ Ad Preview แล้วกด Link)
2. ดู URL ที่เปิดขึ้นมาจริงในเบราว์เซอร์ ว่ามีค่า UTM ต่อท้ายครบและถูกแทนค่าจาก Dynamic Parameter แล้ว (ไม่ใช่ยังเป็น `{{campaign.name}}` ดิบๆ)
3. เข้า Google Analytics 4 > Reports > Acquisition > Traffic acquisition ดูว่ามี Session ที่มี Source/Medium = `facebook / paid_social` เข้ามาจริงหรือไม่ (อาจต้องรอ 24–48 ชั่วโมงกว่าข้อมูลจะประมวลผลเต็มใน GA4)

### ระวัง: UTM ซ้ำซ้อนกับ Facebook Click ID (fbclid)

Facebook จะแนบ Parameter `fbclid=...` ต่อท้าย URL อัตโนมัติเสมอ (ใช้สำหรับ Attribution ภายในของ Meta เอง) ไม่ต้องไปยุ่งหรือลบออก ปล่อยให้อยู่คู่กับ UTM ของคุณได้ตามปกติ ไม่ชนกัน

### ข้อผิดพลาดที่พบบ่อย

- ใส่ UTM ผิดที่ (ใส่ในช่อง Website URL หลักแทนช่อง URL Parameters) ทำให้ลิงก์ปลายทางพังเพราะมี `?` ซ้ำกัน 2 ตัว
- ใช้ค่า UTM ที่มีภาษาไทยหรือช่องว่างไม่ Encode ทำให้ GA4 อ่านค่าผิดเพี้ยน
- ไม่ใช้ Dynamic Parameter แต่พิมพ์ชื่อ Campaign/Ad ตายตัวเอง ทำให้เมื่อสร้าง Ad ใหม่ในอนาคตแล้วลืมอัปเดต UTM ค่าจะไม่ตรงกับชื่อจริง
- ลืมเช็คว่า UTM ทำงานจริงก่อน Publish จนงบวิ่งไปหลายวันแล้วเพิ่งมาพบว่า GA4 ไม่มีข้อมูลเข้ามาเลย

### เจาะลึกเพิ่ม: Dynamic Parameter ทั้งหมดที่ Meta รองรับ

นอกจาก `{{campaign.name}}`, `{{adset.name}}`, `{{ad.name}}` ที่ใช้บ่อยที่สุด Meta ยังรองรับ Dynamic Parameter อื่นที่มีประโยชน์:

| Dynamic Parameter | ค่าที่ได้ |
|---|---|
| `{{campaign.id}}` | Campaign ID ตัวเลข (เสถียรกว่าชื่อ เพราะไม่เปลี่ยนแม้เปลี่ยนชื่อแคมเปญทีหลัง) |
| `{{adset.id}}` | Ad Set ID ตัวเลข |
| `{{ad.id}}` | Ad ID ตัวเลข |
| `{{placement}}` | ตำแหน่งที่แสดงโฆษณา (เช่น Facebook_Feed, Instagram_Stories) |
| `{{site_source_name}}` | แพลตฟอร์มที่มา (fb, ig, msg, an) |

สำหรับทีมที่ต้องการวิเคราะห์ละเอียดถึงระดับ Placement ว่า Traffic จาก Feed กับ Reels ต่างกันอย่างไรใน GA4 โดยไม่ต้องเปิด Ads Manager สลับดู ให้เพิ่ม `&placement={{placement}}` ต่อท้าย URL Parameters ด้วย

**ข้อแนะนำเชิงปฏิบัติ:** สำหรับทีมเล็กที่ต้องอ่านชื่อได้ทันทีโดยไม่ต้องเปิด Ads Manager ควบคู่ ให้ใช้ `{{campaign.name}}` (อ่านง่าย) แต่สำหรับทีม/เอเจนซี่ที่มีระบบ Dashboard เชื่อมต่อ API และแปลง ID กลับเป็นชื่อได้อัตโนมัติ การใช้ `{{campaign.id}}` จะปลอดภัยกว่าเพราะไม่กระทบแม้มีคนไปแก้ชื่อแคมเปญทีหลัง

### เจาะลึกเพิ่ม: การตรวจสอบ UTM แบบ End-to-End ด้วย Chrome DevTools

สำหรับคนที่ต้องการความมั่นใจสูงสุดก่อน Publish งบจริง ให้เปิด Chrome DevTools (กด F12) แท็บ **Network** ก่อนคลิกลิงก์ Preview จากนั้นดู Request แรกที่ยิงไปที่โดเมนเว็บไซต์ ตรวจสอบ Query String ในแถบ Headers ว่ามีค่า UTM ครบและถูกต้องตามที่ตั้งใจ วิธีนี้แม่นยำกว่าการดูจาก Address Bar เฉยๆ เพราะบางเว็บไซต์มี JavaScript Redirect ที่อาจตัดพารามิเตอร์บางตัวออกโดยไม่รู้ตัว

---

## Step 215: Budget และ Bid Strategy สำหรับ Traffic — จุดที่ต่างจาก Awareness

### Budget ขั้นต่ำที่แนะนำ

Traffic Campaign ต้องการ Volume การคลิกที่มากพอสมควรต่อวันเพื่อให้ระบบ Optimize ได้ดี แนะนำ Daily Budget เริ่มต้นที่ **150–300 บาท/วัน** สำหรับตลาดไทย (สูงกว่า Awareness เล็กน้อยเพราะต้นทุนต่อคลิกที่มีคุณภาพสูงกว่าต้นทุนต่อ Reach)

### Bid Strategy — Lowest Cost คือค่า Default ที่ปลอดภัยที่สุด

ในส่วน Ad Set จะมี **"Bid strategy"** (บางเวอร์ชัน UI ซ่อนอยู่ใต้ "Show more options" ของ Budget & Schedule) ตัวเลือกหลักที่เกี่ยวกับ Traffic:

- **Lowest cost (Highest volume)** — ค่า Default ให้ระบบหาผลลัพธ์มากที่สุดในงบที่มี โดยไม่จำกัดว่าต้นทุนต่อผลลัพธ์จะสูงแค่ไหน (แต่ระบบจะพยายามควบคุมให้ต่ำที่สุดเท่าที่ทำได้) เหมาะกับมือใหม่และ Traffic Campaign ทั่วไป
- **Cost cap** — กำหนดเพดานต้นทุนต่อผลลัพธ์ที่ยอมรับได้ ระบบจะพยายามไม่ให้เกินเพดานนี้ (แต่ถ้าตั้งต่ำเกินจริง อาจได้ผลลัพธ์น้อยลงหรือใช้งบไม่หมด) เหมาะกับมือที่มีข้อมูล Benchmark ต้นทุนที่ชัดเจนแล้ว
- **Bid cap** — กำหนดราคาสูงสุดที่ยอมประมูลต่อ Auction หนึ่งครั้ง ควบคุมละเอียดที่สุดแต่ต้องเข้าใจกลไก Auction ดีพอ (เหมาะกับมือโปรระดับ Advanced เท่านั้น)

สำหรับแคมเปญ Traffic แรกๆ **แนะนำ Lowest Cost เสมอ** เพราะยังไม่มีข้อมูล Benchmark ต้นทุนของธุรกิจตัวเองมากพอที่จะตั้ง Cost Cap ได้อย่างแม่นยำ

### ความแตกต่างของ Bid Strategy ระหว่าง Awareness และ Traffic

Awareness Campaign มักไม่ต้องสนใจเรื่อง Bid Strategy มากเพราะ Metric ที่วัด (Reach, Recall) ไม่ผันผวนจาก Bid มากเท่า Traffic ที่วัดด้วย CPC ซึ่งอ่อนไหวต่อการแข่งขันในตลาดสูงกว่ามาก — นี่คือเหตุผลที่ Traffic Campaign ต้องให้ความสำคัญกับการติดตาม Bid/CPC มากกว่า

### Pacing สำหรับ Traffic Campaign

Pacing (การกระจายงบตลอดวัน) ของ Traffic Campaign มักเร็วกว่า Awareness ในช่วงชั่วโมงที่มีการแข่งขันสูง (เช่น 19:00–22:00 ที่คนไทยใช้มือถือมากที่สุด) เพราะ Auction ในช่วงเวลานั้นมี Advertiser แข่งกันดึง Traffic เยอะ ทำให้ CPC พุ่งสูงชั่วคราว ถ้าสังเกตว่า Budget หมดเร็วเกินไปตอนหัวค่ำ อาจพิจารณาใช้ Ad Scheduling (Dayparting) จำกัดชั่วโมงที่ยิงถ้าต้องการควบคุม Pacing ให้กระจายทั่วทั้งวันมากขึ้น

### ข้อผิดพลาดที่พบบ่อย

- ตั้ง Cost Cap ต่ำเกินจริงตั้งแต่แคมเปญแรกโดยไม่มี Benchmark อ้างอิง ทำให้ระบบใช้งบไม่หมดและได้ผลลัพธ์น้อยกว่าที่ควร
- ตกใจเมื่อเห็น CPC พุ่งสูงในบางชั่วโมงแล้วรีบปิดแคมเปญ ทั้งที่เป็นแค่ความผันผวนตาม Pacing ปกติของช่วงเวลานั้น
- ใช้ Bid Cap โดยไม่เข้าใจกลไก Auction ทำให้แคมเปญไม่ Deliver เลยเพราะ Bid ต่ำเกินไปจนแข่งไม่ได้

---

## Step 216: Creative Considerations สำหรับ Traffic Ads ที่ต้องต่างจาก Awareness

### เป้าหมายของ Creative เปลี่ยนไป

Awareness Creative เน้น "จดจำ" ส่วน Traffic Creative ต้องเน้น **"กระตุ้นให้คลิกไปดูรายละเอียดต่อ"** — โครงสร้าง Copy จึงต้องเปลี่ยนจากการเล่าเรื่องเปิดกว้าง มาเป็นการสร้าง **Curiosity Gap** หรือ **Value Proposition ที่ชัดเจน** ว่าคลิกแล้วจะได้อะไร

### องค์ประกอบ Creative ที่ควรมีใน Traffic Ads

1. **Headline ที่บอก Value ชัดเจน** — เช่น "ดูราคาพิเศษเดือนนี้" มากกว่า Headline แบบเปิดกว้างของ Awareness
2. **CTA ที่ตรงกับ Destination** — ถ้า Destination เป็น Website ใช้ CTA "Learn More" หรือ "Shop Now", ถ้าเป็น Messenger ใช้ "Send Message"
3. **ภาพ/วิดีโอที่โชว์สิ่งที่รออยู่หลังคลิก** — เช่น Screenshot หน้าเว็บ, ภาพสินค้าที่ชัดเจน ให้คนรู้สึกว่า "รู้อยู่แล้วว่าจะได้เจออะไร" ลดความลังเลก่อนคลิก
4. **ไม่ต้อง Overclaim เพื่อเรียกคลิก** — การใช้ Copy โอเว่อร์เกินจริงเพื่อ "หลอกให้คลิก" (Clickbait) จะได้ CTR สูงจริง แต่ Landing Page View Rate และ Time on Page จะต่ำ เพราะคนคลิกด้วยความคาดหวังที่ผิด แล้วปิดทันทีที่เห็นว่าไม่ตรงกับที่โฆษณาบอก

### ความยาว Copy ที่เหมาะกับ Traffic

Primary Text สำหรับ Traffic ควรสั้นกระชับกว่า Awareness เล็กน้อย เพราะเป้าหมายคือ "กระตุ้นการกระทำ" ไม่ใช่ "เล่าเรื่องยาว" — แนะนำ 2–4 บรรทัดสั้นๆ จบด้วย CTA ที่ชัดเจนว่าอยากให้คนทำอะไรต่อ

### ทดสอบ Creative หลายแบบพร้อมกันได้ไหม

ได้ และแนะนำให้ทำ — สร้าง Ad หลายตัวภายใน Ad Set เดียวกัน (Audience/Budget เดียวกัน) แต่ Creative ต่างกัน (เปลี่ยน Hook, เปลี่ยนภาพ) เพื่อดูว่า Creative ไหนได้ CTR/Landing Page View Rate ดีที่สุด — หลักการนี้จะเจาะลึกเต็มรูปแบบในการทำ A/B Testing ที่ Part 043

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Creative ตัวเดียวกันกับ Awareness Campaign โดยไม่ปรับ CTA/Copy ให้เข้ากับเป้าหมายของ Traffic
- ใช้ Clickbait เพื่อดัน CTR ให้สูง แต่ Landing Page View Rate ต่ำมาก (สัญญาณว่า Creative หลอกลวงเกินจริง)
- ไม่ทดสอบหลาย Creative พร้อมกัน ทำให้ไม่รู้ว่า Creative ไหนใช้ได้ผลจริง

---

## Step 217: ปัญหาที่พบบ่อยของ Traffic Campaign — Bot Click, CPC สูง, Junk Traffic

### ปัญหา Bot Click และ Junk Traffic

แม้ Meta จะมีระบบกรอง Invalid Traffic ในระดับหนึ่ง แต่ Traffic Campaign (โดยเฉพาะที่ Optimize ด้วย Link Clicks) มีความเสี่ยงสูงที่จะได้ Traffic คุณภาพต่ำ:

- **Accidental Click** — คนกดโดยไม่ตั้งใจ (นิ้วโป้งขนาดใหญ่ ปุ่มเล็กบนมือถือ) แล้วรีบกดปิดทันที
- **Low-intent Click** — คนที่กด "เพราะอยากรู้" แต่ไม่ได้สนใจซื้อจริง เกิดบ่อยกับ Creative ที่เน้น Curiosity มากเกินไปโดยไม่มี Value ชัดเจน
- **Click Farm/Bot** — พบได้น้อยมากบน Facebook Ads ของแท้เพราะระบบกรองในระดับ Auction แล้วในระดับหนึ่ง แต่ยังพบได้ในบาง Placement เช่น Audience Network บางแอปที่คุณภาพผู้ใช้ต่ำ

### วิธีตรวจสอบว่าเจอ Junk Traffic หรือไม่

1. เข้า Google Analytics 4 ดู **Bounce Rate / Engagement Rate** และ **Average Engagement Time** ของ Session ที่มาจาก `utm_source=facebook` — ถ้า Bounce Rate สูงผิดปกติ (เช่น เกิน 80–90%) และ Engagement Time เฉลี่ยต่ำกว่า 5–10 วินาที เป็นสัญญาณว่า Traffic คุณภาพต่ำ
2. เทียบ **CTR** กับ **Landing Page View Rate** — ถ้า CTR สูงมากแต่ Landing Page Views ต่ำกว่ามากเกินคาด (ต่างกันเกิน 30–40%) แสดงว่ามีคนคลิกแล้วหน้าเว็บไม่โหลดสำเร็จจำนวนมาก (อาจเป็นปัญหาเว็บช้า หรือ Junk Click)
3. เช็ค **Breakdown by Placement** — ถ้า Audience Network ให้ Traffic จำนวนมากแต่ Conversion Rate ต่ำผิดปกติเทียบกับ Feed/Reels ให้พิจารณาตัด Placement นั้นออกด้วย Manual Placement

### วิธีป้องกันและแก้ไข

1. **เปลี่ยน Optimization Goal เป็น Landing Page Views หรือ Conversions** แทน Link Clicks (ตามที่เรียนใน Step 212) เพื่อให้ระบบกรองคุณภาพให้ในระดับ Machine Learning เอง
2. **ปรับ Creative ให้ตรงไปตรงมา** ลด Clickbait ที่สร้าง Expectation ผิด
3. **ตรวจ Placement Breakdown สม่ำเสมอ** ตัด Placement ที่ Performance แย่ออก
4. **เพิ่ม Custom Conversion หรือ Micro-conversion** (เช่น Scroll Depth, Time on Page) เป็นสัญญาณเพิ่มเติมให้ Pixel เรียนรู้คุณภาพ Traffic ได้ดีขึ้น
5. **ปิด Ad Set ที่มี Bounce Rate สูงผิดปกติต่อเนื่องหลายวัน** และวิเคราะห์ว่าปัญหาเกิดจาก Audience หรือ Creative

### ข้อผิดพลาดที่พบบ่อย

- เห็น CPC ต่ำแล้วดีใจ โดยไม่เช็คว่า Traffic ที่ได้มีคุณภาพหรือไม่ (CPC ต่ำ + Bounce Rate สูง = เสียเงินฟรี)
- ไม่เชื่อม GA4 เข้ากับเว็บไซต์ ทำให้ไม่มีทางรู้ได้เลยว่า Traffic ที่มาจริงมีคุณภาพแค่ไหน (มองเห็นแค่ตัวเลขจาก Ads Manager ซึ่งไม่บอกพฤติกรรมหลังคลิก)
- โทษว่า "แคมเปญพัง" ทั้งที่ปัญหาจริงคือเว็บไซต์โหลดช้าเกินไป ทำให้คนปิดหน้าก่อนโหลดเสร็จ

---

## Step 218: อ่าน Metrics ของ Traffic Campaign อย่างมืออาชีพ

### Metric หลักที่ต้องดูเป็นชุด ไม่ใช่ดูตัวเดียว

| Metric | นิยาม | ค่าที่น่าสนใจ (Reference กว้างๆ ตลาดไทย) |
|---|---|---|
| **CTR (All)** | % ของคนที่เห็นโฆษณาแล้วคลิกอะไรก็ตาม (รวม Like/Comment) | 1–3% ถือว่าปกติ |
| **CTR (Link Click-through Rate)** | % ของคนที่เห็นแล้วคลิกลิงก์โดยเฉพาะ | 0.8–2% ถือว่าปกติ |
| **CPC (Cost per Link Click)** | ต้นทุนต่อคลิกลิงก์ 1 ครั้ง | ผันผวนตามอุตสาหกรรมมาก อยู่ที่ประมาณ 2–15 บาท |
| **Landing Page View Rate** | % ของคนที่คลิกแล้วหน้าเว็บโหลดสำเร็จจริง | ควรอยู่ที่ 70%+ ของ Link Clicks ถ้าต่ำกว่านี้มาก ให้เช็คความเร็วเว็บ |
| **Cost per Landing Page View** | ต้นทุนต่อคนที่เข้าเว็บสำเร็จจริง 1 คน | Metric ที่แม่นยำกว่า CPC เพราะกรอง Junk ออกไปแล้วระดับหนึ่ง |

**หมายเหตุสำคัญ:** ตัวเลข Benchmark ข้างบนเป็นเพียง**แนวทางอ้างอิงกว้างๆ** ผันผวนมากตามอุตสาหกรรม ฤดูกาล และการแข่งขัน ณ ขณะนั้น ไม่ควรยึดเป็นมาตรฐานตายตัว ควรสร้าง Benchmark ของตัวเองจากข้อมูลในอดีตของบัญชีนั้นๆ (ตามที่จะเรียนเจาะลึกวิธีอ่าน Metric ทั้งระบบใน Part 056–057)

### วิธีดู Metric เหล่านี้ใน Ads Manager

เปิดปุ่ม **"Columns"** มุมบนขวาของตาราง เลือก **"Customize columns"** จะเปิด Modal ให้ติ๊กเลือก Metric ที่ต้องการแสดง ค้นหาคำว่า "Landing Page Views", "Cost per Landing Page View", "CTR (Link Click-Through Rate)", "CPC (Cost per Link Click)" แล้วกด Apply เพื่อบันทึกเป็น Preset ที่ใช้ประจำ (ตั้งชื่อ Preset เช่น "Traffic Report" เพื่อสลับดูได้เร็วในอนาคต)

### การอ่านผลแบบ Funnel Mini ภายใน Traffic Campaign

ให้มองเป็น Funnel เล็กๆ ภายในแคมเปญเดียว:

```
Impressions → Clicks (All) → Link Clicks → Landing Page Views → (ถ้ามี) Add to Cart/Lead
```

ถ้าตัวเลขหล่นฮวบระหว่างขั้นไหนมากผิดปกติ นั่นคือจุดที่ต้องไปแก้ไข เช่น
- Impressions สูง แต่ Clicks (All) ต่ำ → ปัญหาที่ Creative ไม่ดึงดูด
- Link Clicks สูง แต่ Landing Page Views ต่ำ → ปัญหาที่ความเร็วเว็บหรือ Junk Click
- Landing Page Views สูง แต่ Add to Cart ต่ำ → ปัญหาที่ตัว Landing Page เอง (CRO ที่จะเรียนใน Part 055)

### ข้อผิดพลาดที่พบบ่อย

- ดูแค่ CPC ตัวเดียวโดยไม่ดู Landing Page View Rate ประกอบ ทำให้พลาดสัญญาณ Junk Traffic
- ไม่ Customize Columns ทำให้มองไม่เห็น Metric สำคัญที่ซ่อนอยู่ (ค่า Default ของ Ads Manager ไม่โชว์ Landing Page Views ให้เห็นทันที)
- เปรียบเทียบ Benchmark ของธุรกิจตัวเองกับตัวเลขที่เห็นจากอินเทอร์เน็ต/เพื่อนในอุตสาหกรรมคนละแบบ โดยไม่ปรับตามบริบท (Audience, ราคาสินค้า, ฤดูกาล) ที่ต่างกัน

---

## Step 219: เมื่อไหร่ Traffic Campaign คือตัวเลือกที่ผิด และควรใช้ Objective อื่นแทน

### สัญญาณที่บอกว่าคุณควรเลิกใช้ Traffic Objective

1. **Pixel มีข้อมูล Purchase สะสมมากพอแล้ว** (ประมาณ 20–50 Event/สัปดาห์ขึ้นไป) — ควรย้ายไปใช้ Sales/Conversion Objective ที่ Part 026 เพราะ Machine Learning จะ Optimize เพื่อการซื้อโดยตรง แม่นยำกว่า Traffic มาก
2. **เป้าหมายจริงคือ Lead ไม่ใช่การเข้าเว็บ** — ควรย้ายไปใช้ Leads Objective (Part 024) ที่มี Instant Form ในตัว ลด Friction กว่าการส่งไปเว็บแล้วให้กรอกฟอร์มเอง
3. **เป้าหมายจริงคือปิดการขายผ่านแชท** — ควรย้ายไปใช้ Messages Objective (Part 025) ที่มี Feature เฉพาะสำหรับวัดผลการสนทนา ไม่ใช่แค่การคลิก
4. **ธุรกิจขายผ่าน Catalog จำนวนมาก (E-commerce)** — ควรย้ายไปใช้ Catalog Sales/Dynamic Ads (Part 027) ที่ทำ Retargeting สินค้ารายชิ้นได้ ซึ่ง Traffic Objective ทำไม่ได้
5. **CPC ต่ำแต่ ROAS จากข้อมูล Pixel ไม่ขยับเลยหลายสัปดาห์** — เป็นสัญญาณว่า Traffic ที่ได้มาไม่ใช่กลุ่มที่มีโอกาสซื้อจริง ต้องเปลี่ยนกลยุทธ์ ไม่ใช่แค่ปรับ Budget

### กรณีที่ Traffic Campaign ยังเหมาะสมต่อไป

- ธุรกิจ Content/สื่อที่วัดผลด้วย Pageview ไม่ใช่ Purchase
- ช่วงทดสอบ Landing Page ใหม่ก่อนเทงบหนัก
- ธุรกิจใหม่ที่ Pixel ยังไม่มีข้อมูล Purchase เลยแม้แต่ 1 ครั้ง (ต้องใช้ Traffic หรือ Engagement สร้าง Traffic พื้นฐานก่อน)

### กรอบการตัดสินใจแบบง่าย (Decision Framework)

```
ถามคำถาม: "เป้าหมายสุดท้ายที่วัดความสำเร็จของแคมเปญนี้คืออะไร"

→ ถ้าคำตอบคือ "ยอดขาย/Purchase" และมี Pixel Data พอ → ใช้ Sales Objective
→ ถ้าคำตอบคือ "เก็บเบอร์/อีเมลลูกค้า" → ใช้ Leads Objective
→ ถ้าคำตอบคือ "เปิดบทสนทนาขาย" → ใช้ Messages Objective
→ ถ้าคำตอบคือ "แค่อยากให้คนเข้าเว็บ/อ่าน Content/ทดสอบ Landing Page" → ใช้ Traffic Objective
```

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Traffic Campaign ต่อไปเรื่อยๆ นานหลายเดือนทั้งที่มี Pixel Data พร้อมสำหรับ Conversion Objective แล้ว เพราะความเคยชิน ไม่กล้าเปลี่ยน
- เปลี่ยนไป Sales Objective ทั้งที่ Pixel Data ยังน้อยเกินไป (แทนที่จะได้ผลดีกว่า กลับได้ Learning Limited และ Performance แย่กว่าเดิม)
- ไม่ตั้งเกณฑ์ล่วงหน้าว่า "เมื่อไหร่จะเปลี่ยน Objective" ทำให้ตัดสินใจแบบสุ่มไปเรื่อยๆ

---

## Case Study: ร้านขายอุปกรณ์ออกกำลังกายออนไลน์ "FitGear TH"

**สถานการณ์:** ร้านขายอุปกรณ์ Fitness ออนไลน์ เพิ่งเปิดเว็บไซต์ใหม่ 2 สัปดาห์ ติดตั้ง Pixel แล้วแต่ยังไม่มี Purchase Event เกิดขึ้นเลยสักครั้ง (เพราะยังไม่มีคนเข้าเว็บมากพอ) ต้องการเริ่มสร้าง Traffic เข้าเว็บก่อนเพื่อเก็บข้อมูล Pixel และทดสอบว่า Landing Page ใช้งานได้ดีหรือไม่

**การตั้งค่าที่ทำ:**
- Objective: Traffic, Conversion Location: Website
- Performance Goal: Landing Page Views (เพราะมี Pixel ติดตั้งแล้ว)
- Ad Set: Location = ทั่วประเทศไทย, Age 22–40, Detailed Targeting = "Gym", "Fitness and wellness", "Home gym equipment"
- Budget: 250 บาท/วัน
- UTM: ใช้ Dynamic Parameter ครบ (`utm_campaign={{campaign.name}}&utm_content={{ad.name}}`)
- Creative: ภาพสินค้าจริงพร้อมราคาชัดเจนในภาพ, Primary Text บอก Value ตรงๆ "ดัมเบลปรับน้ำหนักได้ ส่งฟรีทั่วไทย ราคาพิเศษเดือนนี้เท่านั้น"

**ผลลัพธ์หลัง 7 วัน:**
- Link Clicks: 480 ครั้ง, CPC เฉลี่ย 3.6 บาท
- Landing Page Views: 410 ครั้ง (Landing Page View Rate ~85% ของ Link Clicks — ถือว่าดี เว็บโหลดเร็ว)
- ใน GA4 พบว่า Bounce Rate อยู่ที่ 55% (ไม่สูงผิดปกติ), Average Engagement Time 38 วินาที
- AddToCart Event เริ่มเกิดขึ้น 22 ครั้งในสัปดาห์แรก (ยังไม่มี Purchase แต่เริ่มมีสัญญาณความสนใจจริง)

**การปรับตัวในสัปดาห์ที่ 2:** เจ้าของร้านสังเกตเห็นจาก Breakdown by Placement ว่า Traffic จาก Audience Network มี Bounce Rate สูงกว่า Feed/Reels อย่างชัดเจน (Bounce Rate 78% เทียบกับ 45% ของ Feed) จึงสวิตช์จาก Automatic Placement มาเป็น Manual Placement ตัด Audience Network ออก ทำให้ CPC ขยับขึ้นเล็กน้อย (จาก 3.6 เป็น 4.2 บาท) แต่ Landing Page View Rate ดีขึ้นเป็น 91% และ AddToCart เพิ่มเป็น 35 ครั้งในสัปดาห์ที่สองด้วยงบเท่ากัน

**สิ่งที่เรียนรู้:** การตัดสินใจจาก CPC ตัวเดียวจะนำไปสู่ข้อสรุปผิด (CPC ที่สูงขึ้นดูเหมือนแย่ลง) แต่เมื่อดู Metric ชุดเต็ม (Landing Page View Rate, AddToCart) จะเห็นว่าคุณภาพ Traffic ดีขึ้นจริง นี่คือเหตุผลที่ Part นี้ย้ำเรื่องการอ่าน Metric เป็นชุดใน Step 218

---

## Checklist ท้ายบท

- [ ] เข้าใจว่า Traffic Objective Optimize เพื่อ "คลิก/เข้าเว็บ" ไม่ใช่ "การซื้อ" โดยตรง
- [ ] เลือก Optimization Goal (Link Clicks/Landing Page Views/Conversions) ให้เหมาะกับสถานะ Pixel ของธุรกิจ
- [ ] เลือก Destination Type ให้ตรงกับ Business Model จริง (ปิดการขายที่ไหน)
- [ ] ตั้งค่า UTM Parameters ครบทั้ง 5 Field โดยใช้ Dynamic Parameter ของ Meta
- [ ] ทดสอบคลิกลิงก์จริงเพื่อยืนยันว่า UTM ทำงานถูกต้องก่อน Publish
- [ ] ตั้ง Budget อย่างน้อย 150–300 บาท/วัน และเลือก Bid Strategy = Lowest Cost สำหรับแคมเปญแรก
- [ ] ปรับ Creative ให้เหมาะกับเป้าหมาย "กระตุ้นคลิก" ไม่ใช่ "จดจำ" และไม่ใช้ Clickbait เกินจริง
- [ ] ติดตาม CTR, CPC, Landing Page View Rate เป็นชุดเดียวกัน ไม่ดูตัวใดตัวหนึ่งเดี่ยวๆ
- [ ] เช็ค Breakdown by Placement เพื่อหา Placement ที่ให้ Traffic คุณภาพต่ำ
- [ ] มีเกณฑ์ชัดเจนว่าเมื่อไหร่จะเปลี่ยนจาก Traffic ไปใช้ Objective อื่น (Sales/Leads/Messages)

---

## Workshop / แบบฝึกหัด

**เป้าหมาย:** สร้างแคมเปญ Traffic เต็มรูปแบบ 1 แคมเปญ พร้อม UTM Tracking ที่ตรวจสอบได้จริง

**ขั้นตอน:**

1. เลือกเว็บไซต์จริง 1 เว็บ (ของตัวเอง/ลูกค้า) ที่ติดตั้ง Pixel และ GA4 แล้ว
2. สร้าง Campaign ใหม่ Objective = Traffic, Conversion Location = Website
3. เลือก Performance Goal = Landing Page Views
4. ตั้งชื่อ Campaign ตามสูตร `[วันที่]_TRF_[ชื่อสินค้า/หน้าที่จะส่ง]_V1`
5. ตั้ง Ad Set: Audience ตาม Persona ธุรกิจ, Budget 150–250 บาท/วัน, Bid Strategy = Lowest Cost
6. ที่ระดับ Ad: ใส่ Destination URL ของหน้า Landing Page จริง แล้วตั้งค่า URL Parameters ด้วย Dynamic Parameter ครบ 5 Field
7. เขียน Primary Text ที่บอก Value ชัดเจน ไม่ Clickbait พร้อม CTA ที่ตรงกับ Destination
8. ก่อน Publish ให้เปิด Ad Preview คลิกลิงก์ทดสอบ (ผ่านฟีเจอร์ Preview Link) แล้วเช็คว่า URL ที่เปิดมีค่า UTM ถูกแทนค่าแล้วจริง
9. Publish แล้วรอ 3–4 วัน จากนั้นเข้า Ads Manager เปิด Column แสดง CTR, CPC, Landing Page Views, Cost per Landing Page View
10. เข้า GA4 เช็คว่ามี Session จาก `facebook / paid_social` เข้ามาจริง และดู Bounce Rate/Engagement Time เทียบกับ Metric ใน Ads Manager แล้วสรุปว่า Traffic ที่ได้มีคุณภาพหรือไม่

**คำถามให้ตอบหลังทำ Workshop:**
- Landing Page View Rate (Landing Page Views ÷ Link Clicks x 100) ของคุณอยู่ที่กี่เปอร์เซ็นต์ ถ้าต่ำกว่า 70% ควรตรวจสอบอะไรก่อน
- UTM ที่ตั้งไว้ปรากฏใน GA4 ถูกต้องหรือไม่ ถ้าไม่ถูกต้อง ปัญหาอยู่ที่ขั้นตอนไหน
- จาก Metric ที่ได้ คุณคิดว่าธุรกิจนี้พร้อมจะย้ายไปใช้ Sales Objective แล้วหรือยัง เพราะอะไร

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Traffic Campaign คือ Objective ที่ดูเหมือนง่ายที่สุดในสายตามือใหม่ แต่มีรายละเอียดซ่อนอยู่มากที่สุดในเรื่อง Optimization Goal, Destination, UTM Tracking และการอ่าน Metric อย่างถูกต้อง — สิ่งสำคัญที่สุดที่ต้องจำจาก Part นี้คือ Traffic Objective ไม่ได้ Optimize เพื่อยอดขาย มันแค่ส่งคนไปให้ถึงปลายทาง ส่วนคุณภาพของคนที่ไปถึงนั้นต้องอาศัยการตั้งค่า Optimization Goal ที่ถูกต้องและการติดตาม Metric ที่ครบชุด

Part ถัดไป (**Part 023: สร้างแคมเปญ Engagement และ Video Views**) เราจะเรียนรู้ Objective ที่เน้นสร้างการมีส่วนร่วมและการดูวิดีโอ ซึ่งมีบทบาทสำคัญในช่วงต้นของ Funnel (Top of Funnel) และเป็นฐานสำคัญสำหรับการทำ Retargeting ในอนาคต พร้อมเรียนรู้กับดัก "Vanity Metrics" ที่นักยิงแอดมือใหม่หลายคนหลงเชื่อว่าตัวเลข Engagement สูงคือความสำเร็จ ทั้งที่ธุรกิจอาจไม่ได้อะไรจากมันเลยถ้าไม่วางแผนต่อให้ถูกทาง

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center — "About the Traffic objective"
- Meta Business Help Center — "About optimization for ad delivery"
- Google Analytics 4 Help — "UTM parameters" และ "Traffic acquisition report"
- Meta Business Help Center — "About URL parameters for ads"
- เอกสารภายในหลักสูตร: Part 013–015 (Pixel/Events Manager), Part 018 (Budget/Bid Strategy), Part 055 (CRO), Part 056–057 (การอ่าน Metrics เจาะลึก)
