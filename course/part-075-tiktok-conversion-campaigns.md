# Part 075: สร้างแคมเปญ Conversion และ Web/App Events

**Section:** H — TikTok Ads Manager Deep Dive & Creative
**Step ที่ครอบคลุม:** 741–750 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 6–8 ชั่วโมง (รวมเวลาตั้งค่าแคมเปญจริงและวิเคราะห์ข้อมูล Pixel ประกอบ)

Part 073 และ 074 พาคุณผ่านสองระดับแรกของ Funnel มาแล้ว (สร้างการรับรู้/พา Action และเก็บข้อมูลติดต่อ) มาถึง Part นี้เราเข้าสู่ปลายสุดของ Funnel — **Conversion** คือ Objective ที่ยากที่สุดในการตั้งค่าให้ได้ผลลัพธ์ดี เพราะต้องพึ่งพา Machine Learning ของ TikTok ในการหาคนที่มีโอกาส "ทำ Action มูลค่าสูงที่สุด" (ซื้อสินค้า, สมัครสมาชิก, จองบริการ) ซึ่งต้องการข้อมูล Pixel/Events ที่มีคุณภาพและปริมาณเพียงพอมากกว่า Objective อื่นๆ ทั้งหมดที่เรียนมา

ถ้าคุณเคยเรียน Part 026 ของ Facebook (สร้างแคมเปญ Conversions) มาแล้ว หลักการ 50-Event Rule และแนวคิด Value-based Optimization จะคุ้นเคย เพราะ TikTok นำแนวคิดเดียวกันมาปรับใช้ เพียงแต่รายละเอียดปลีกย่อยของ UI, ชื่อ Field, และเกณฑ์บางอย่างต่างกัน — Part นี้จะเจาะลึกทุกจุดต่างที่ต้องรู้ก่อนใช้งบจริงกับ Conversion Campaign บน TikTok

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 741** — Website Conversion Objective บน TikTok และการเลือก Event ตั้งต้น
2. **Step 742** — หลัก "50 Events Rule" ฉบับ TikTok และการเลือก Event ตามปริมาณข้อมูลที่มี
3. **Step 743** — Value-based Optimization (VBO) บน TikTok คืออะไร เมื่อไหร่ควรใช้
4. **Step 744** — ปริมาณ Event ขั้นต่ำสำหรับการส่งมอบที่มั่นคง (Stable Delivery)
5. **Step 745** — สร้าง Ad Group และ Ad สำหรับแคมเปญ Conversion แบบ Step-by-Step
6. **Step 746** — แนวทางกำหนดงบประมาณสำหรับแคมเปญ Conversion บนตลาดไทย
7. **Step 747** — ข้อผิดพลาดที่พบบ่อย: Optimize Event ผิดจังหวะเร็วเกินไป
8. **Step 748** — การอ่าน Metric ของแคมเปญ Conversion อย่างมืออาชีพ
9. **Step 749** — App Conversion Campaigns เบื้องต้นและความต่างจาก Website Conversion
10. **Step 750** — Workshop: สร้างแคมเปญ Purchase Conversion เต็มรูปแบบบน TikTok

---

## Step 741: Website Conversion Objective บน TikTok และการเลือก Event ตั้งต้น

### ภาพรวม Website Conversion

**Website Conversion** อยู่ในกลุ่ม **Conversion** ของ TikTok Objective (เทียบเท่า Sales/Conversions Objective ของ Facebook ที่เรียนใน Part 026) มีเป้าหมายให้ระบบ Optimize เพื่อหาคนที่มีโอกาส "ทำ Event ที่กำหนด" มากที่สุดบนเว็บไซต์ของคุณ เช่น การซื้อสินค้า (Complete Payment), การสมัครสมาชิก (Complete Registration), หรือ Event Custom ที่ธุรกิจกำหนดขึ้นเอง

### ข้อกำหนดก่อนเริ่มใช้ Objective นี้

ก่อนสร้างแคมเปญ Website Conversion ต้องมีสิ่งต่อไปนี้พร้อมแล้ว (ตามที่เรียนใน Part 066):

1. **TikTok Pixel ติดตั้งบนเว็บไซต์** และ Verify Domain แล้ว
2. **Event ที่ต้องการ Optimize ยิงทำงานถูกต้อง** ทดสอบผ่าน TikTok Pixel Helper (Chrome Extension) หรือ Events Manager > Test Events
3. **ควรติดตั้ง TikTok Events API (Server-Side)** ควบคู่กับ Browser Pixel เพื่อเพิ่ม Event Match Quality โดยเฉพาะในยุคที่ Browser บล็อก Third-party Cookie มากขึ้น

### รายการ Standard Events หลักที่ใช้กับ Website Conversion

| Event | ความหมาย | ใช้ตอนไหน |
|---|---|---|
| **ViewContent** | ดูหน้ารายละเอียดสินค้า | Event บนสุดของ Funnel Conversion |
| **AddToCart** | เพิ่มสินค้าลงตะกร้า | กลาง Funnel |
| **InitiateCheckout** | เริ่มขั้นตอนชำระเงิน | ใกล้ปลาย Funnel |
| **AddPaymentInfo** | กรอกข้อมูลการชำระเงิน | ใกล้ปลาย Funnel มากขึ้น |
| **CompletePayment** | ชำระเงินสำเร็จ (Purchase) | ปลาย Funnel — Event หลักที่ธุรกิจ e-Commerce ส่วนใหญ่ต้องการ Optimize |
| **CompleteRegistration** | ลงทะเบียน/สมัครสมาชิกสำเร็จ | ธุรกิจ Lead-based/Subscription |
| **Subscribe** | สมัครสมาชิกแบบต่อเนื่อง (Recurring) | ธุรกิจ SaaS/สมาชิกรายเดือน |

### การเลือก Event ตั้งต้นสำหรับธุรกิจใหม่ที่ยังไม่มีข้อมูล

ถ้าเป็นบัญชีใหม่ที่ยังไม่มี Pixel Data สะสมเลย **ไม่ควรเริ่มที่ CompletePayment ทันที** เพราะระบบไม่มีข้อมูลพอจะเรียนรู้ว่าใครมีโอกาสซื้อ แนะนำเริ่มไล่ระดับจาก Event ที่มี Volume มากกว่าก่อน (เช่น ViewContent หรือ AddToCart) เก็บข้อมูลสะสมสัก 1-2 สัปดาห์ แล้วค่อยขยับไป InitiateCheckout และ CompletePayment ตามลำดับเมื่อมี Volume Event เพียงพอในแต่ละขั้น — หลักการนี้จะเจาะลึกเต็มรูปแบบใน Step 742

### ข้อผิดพลาดที่พบบ่อยตอนเลือก Objective

- เลือก Traffic Objective แล้วหวังผลเหมือน Conversion เพราะคิดว่า "ได้ Click มากก็ต้องขายได้เยอะ" ทั้งที่ Traffic ไม่ได้ Optimize เพื่อ Conversion เลย (ย้อนไปดู Step 723)
- ตั้ง Optimization Event เป็น CompletePayment ตั้งแต่วันแรกทั้งที่บัญชียังไม่มี Pixel Data สะสมแม้แต่ Event เดียว ทำให้ระบบหาคนไม่ได้ Delivery ไม่ออก

### เจาะลึกเพิ่ม: Custom Conversion บน TikTok

นอกจาก Standard Event ตามตารางข้างต้น TikTok ยังรองรับ **Custom Conversion** สำหรับธุรกิจที่ต้องการวัด Event เฉพาะที่ไม่ตรงกับ Standard Event ใดๆ เลย เช่น "ดูวิดีโอสาธิตสินค้าจบ" หรือ "กดปุ่มขอใบเสนอราคา" วิธีสร้างคือเข้าไปที่ **Assets > Events > Custom Conversions** แล้วกำหนดเงื่อนไข URL หรือ Event Parameter ที่จะนับเป็น Conversion (เช่น URL ที่มีคำว่า `/thank-you-quote/`) หลักการเดียวกับ Custom Conversions ของ Facebook ที่เรียนใน Part 013 Step 124

Custom Conversion มีข้อจำกัดสำคัญคือมักมี Volume Event น้อยกว่า Standard Event มาก (เพราะเป็น Action เฉพาะทาง) จึงต้องพิจารณาเรื่อง 50 Events Rule อย่างเข้มงวดกว่าปกติ ตามที่จะเรียนละเอียดใน Step 742

### เจาะลึกเพิ่ม: ความสัมพันธ์ระหว่าง Optimization Event และ Ad Group ที่ตั้งไว้ก่อนหน้า

ถ้าธุรกิจเคยสร้าง Traffic Campaign หรือ Reach Campaign มาก่อน (ตามที่เรียนใน Part 073) ข้อมูล Pixel ที่เก็บสะสมจากแคมเปญเหล่านั้น (ViewContent ที่เกิดขึ้นเองจากคนที่คลิกเข้าเว็บ) จะเป็นประโยชน์ต่อ Conversion Campaign ที่สร้างตามมาทีหลัง เพราะระบบมี Signal สะสมอยู่บ้างแล้วไม่ต้องเริ่มจากศูนย์เต็มรูปแบบ นี่คือเหตุผลหนึ่งที่แนะนำให้ทุกธุรกิจติด Pixel ไว้ตั้งแต่แคมเปญแรกแม้ Objective นั้นจะไม่บังคับต้องมี Pixel ก็ตาม (ตามที่แนะนำไว้ใน Part 073 Step 721)

---

## Step 742: หลัก "50 Events Rule" ฉบับ TikTok และการเลือก Event ตามปริมาณข้อมูลที่มี

### แนวคิดพื้นฐานที่เหมือนกับ Facebook

TikTok ใช้แนวคิดเดียวกับที่ Meta เรียก "50 Optimization Events per week" (ที่เรียนใน Part 067 Step 661 และ Part 026) คือ **Ad Group ควรได้รับ Optimization Event อย่างน้อยประมาณ 50 ครั้งต่อสัปดาห์** เพื่อให้ Machine Learning มีข้อมูลพอเรียนรู้ Pattern ของคนที่มีโอกาสทำ Event นั้นได้อย่างมีเสถียรภาพ ถ้าต่ำกว่านี้มาก ระบบจะเข้าสถานะ **"Learning Limited"** ซึ่งหมายความว่าการ Optimize จะสุ่มมากกว่าใช้ Pattern ที่เรียนรู้มา ผลลัพธ์จะไม่แน่นอนและมักแพงกว่าที่ควรจะเป็น

### สูตรคำนวณเบื้องต้น

```
Event ต่อสัปดาห์ที่คาดว่าจะได้ = (Budget ต่อวัน × 7) ÷ Cost per Event โดยประมาณ

ตัวอย่าง: Budget 1,000 บาท/วัน, Cost per Purchase โดยประมาณ 200 บาท
Event ต่อสัปดาห์ = (1,000 × 7) ÷ 200 = 35 Event/สัปดาห์ (ต่ำกว่าเกณฑ์ 50)
```

ถ้าคำนวณแล้วต่ำกว่า 50 มีทางเลือก 3 ทาง: (1) เพิ่ม Budget ให้ได้ Event มากขึ้น (2) เปลี่ยนไป Optimize Event ที่อยู่สูงขึ้นใน Funnel ที่มี Volume มากกว่า หรือ (3) รวม Ad Group หลายตัวเข้าด้วยกันเพื่อสะสม Event ในที่เดียว

### ตารางไล่ระดับ Event ตามปริมาณ Traffic/Data ที่มี (ปรับจากแนวคิด Facebook มาใช้กับ TikTok)

| ระดับ Traffic เว็บไซต์ต่อเดือน | Event ที่แนะนำให้ Optimize | เหตุผล |
|---|---|---|
| ต่ำกว่า 5,000 Session/เดือน | ViewContent หรือ AddToCart | Purchase Event มีปริมาณน้อยเกินกว่าจะ Optimize ตรงได้ |
| 5,000–20,000 Session/เดือน | AddToCart หรือ InitiateCheckout | เริ่มมี Signal พอสำหรับ Event กลาง Funnel |
| 20,000–50,000 Session/เดือน | InitiateCheckout หรือ CompletePayment (ถ้า Conversion Rate สูง) | เริ่มมี Purchase Event สะสมพอสมควร |
| มากกว่า 50,000 Session/เดือน | CompletePayment ตรง | มี Volume เพียงพอให้ Optimize ที่ปลาย Funnel ได้อย่างมั่นคง |

ตัวเลขเหล่านี้เป็น**แนวทางเริ่มต้น** ปัจจัยจริงขึ้นกับ Conversion Rate ของเว็บไซต์และ Margin ของสินค้าด้วย ธุรกิจที่มี Conversion Rate สูงมาก (เช่น 5%+) อาจ Optimize ตรงที่ CompletePayment ได้แม้ Traffic ไม่สูงมาก

### วิธีเช็กว่า Ad Group ของคุณมี Event เพียงพอหรือไม่

เข้าไปดูคอลัมน์ **Delivery Status** ที่ระดับ Ad Group ถ้าแสดง **"Learning"** แบบไม่มี "Limited" ต่อท้าย แสดงว่ากำลังเรียนรู้ปกติ ถ้าแสดง **"Learning Limited"** ให้เช็กจำนวน Event สะสมของสัปดาห์ที่ผ่านมาเทียบกับเกณฑ์ 50 ครั้ง แล้วปรับตามทางเลือก 3 ทางที่กล่าวไปข้างต้น

### ข้อผิดพลาดที่พบบ่อย

- ตั้ง Optimize ที่ CompletePayment ทันทีในบัญชีใหม่ที่ยัง Traffic ต่ำ เพราะเข้าใจผิดว่า "ยิ่ง Optimize ลึกยิ่งดีเสมอ" ทั้งที่ต้องดูปริมาณ Data ที่มีประกอบด้วย
- ไม่รู้จักวิธีคำนวณ Event ต่อสัปดาห์ ปล่อยให้แคมเปญวิ่งแบบ Learning Limited นานหลายสัปดาห์โดยไม่แก้ไข ทำให้เสียงบไปกับ Performance ที่ไม่แน่นอน

---

## Step 743: Value-based Optimization (VBO) บน TikTok คืออะไร เมื่อไหร่ควรใช้

### Value-based Optimization คืออะไร

**Value-based Optimization (VBO)** คือการให้ระบบ Optimize เพื่อ **มูลค่ารวม (Total Value)** ของ Conversion มากที่สุด ไม่ใช่แค่ **จำนวนครั้ง (Count)** ของ Conversion — เทียบเท่า **Value Optimization** ของ Facebook ที่เรียนใน Part 015 Step 146

ตัวอย่างความต่าง: Optimization Goal ปกติ (Complete Payment แบบนับจำนวน) จะพยายามหาคนที่มีโอกาส "ซื้อ" มากที่สุด โดยไม่สนใจว่าซื้อสินค้าราคาถูกหรือแพง ในขณะที่ VBO จะพยายามหาคนที่มีโอกาส "ซื้อของมูลค่าสูง" มากที่สุด แม้จะได้จำนวนออเดอร์น้อยกว่า แต่ยอดขายรวม (Revenue) อาจสูงกว่า

### ข้อกำหนดก่อนใช้ VBO

1. Pixel ต้องส่ง **Value Parameter** พร้อม Event CompletePayment ทุกครั้ง (เช่น `value: 1290, currency: THB`) ไม่ใช่แค่ยิง Event เปล่าๆ
2. ต้องมี Volume Purchase Event สะสมมากพอสมควร (มากกว่าเกณฑ์ปกติของ Complete Payment ธรรมดา เพราะ VBO ต้องเรียนรู้ทั้ง "ใครซื้อ" และ "ซื้อเท่าไหร่" ซึ่งซับซ้อนกว่า)
3. สินค้าต้องมีความหลากหลายของราคาในระดับที่มีนัยสำคัญ (ถ้าสินค้าราคาเดียวหมดทุกตัว VBO จะให้ผลไม่ต่างจาก Optimize แบบนับจำนวนธรรมดา)

### วิธีเปิดใช้ VBO ในหน้า Ad Group

ในส่วน **Optimization Goal** ของ Ad Group ที่ Promotion Type = Website และเลือก Event = CompletePayment แล้ว จะมี Toggle เพิ่มเติม **"Value Optimization"** หรือชื่อคล้ายกันปรากฏขึ้น (ตำแหน่งอาจขยับตาม UI Version) เปิด Toggle นี้เพื่อสลับจาก Optimize แบบนับจำนวนไปเป็น Optimize แบบมูลค่ารวม

### เมื่อไหร่ควรใช้ VBO เมื่อไหร่ไม่ควร

**ควรใช้ VBO เมื่อ:**
- ธุรกิจมี Product Range หลากหลายราคาชัดเจน (เช่น สินค้าราคา 300–5,000 บาทในร้านเดียว)
- ต้องการเพิ่ม Average Order Value (AOV) ไม่ใช่แค่จำนวนออเดอร์
- มี Purchase Event สะสมมากพอ (แนะนำมากกว่า 100+ Purchase/สัปดาห์ทั้งบัญชีเป็นแนวทางเริ่มต้น)

**ไม่ควรใช้ VBO เมื่อ:**
- สินค้าราคาเดียวหรือใกล้เคียงกันทั้งหมด (VBO ไม่มีประโยชน์เพิ่ม)
- บัญชียังใหม่ Purchase Event สะสมน้อย (VBO ต้องการ Data มากกว่า Optimize แบบนับจำนวนธรรมดา ถ้า Data ไม่พอผลลัพธ์จะแย่กว่า)
- ธุรกิจที่เป้าหมายหลักคือ Volume/จำนวนลูกค้าใหม่ ไม่ใช่ยอดขายรวมสูงสุด (เช่น ธุรกิจที่เน้นสร้างฐานลูกค้าเพื่อ Upsell ทีหลัง)

### ข้อผิดพลาดที่พบบ่อย

- เปิด VBO ทันทีในบัญชีที่ Purchase Event ยังน้อยมาก ทำให้ Learning Phase ไม่จบเลยเพราะ Data ไม่พอสำหรับความซับซ้อนที่เพิ่มขึ้น
- ลืมยิง Value Parameter คู่กับ Event ทำให้ VBO ทำงานผิดพลาด (ระบบเห็น Value เป็น 0 หรือค่าเดียวกันหมดทุก Order)
- ใช้ VBO กับสินค้าราคาเดียวแล้วหวังผลต่างจากการ Optimize ปกติ ทั้งที่ไม่มีความหลากหลายของมูลค่าให้ระบบเรียนรู้อยู่แล้ว

### เจาะลึกเพิ่ม: ตัวอย่างการเปรียบเทียบผลลัพธ์ VBO กับ Optimize แบบนับจำนวน

สมมติร้านค้าออนไลน์ขายสินค้าตั้งแต่ 200-3,000 บาท ทดสอบสองแบบพร้อมกันด้วยงบเท่ากัน 1,000 บาท/วัน เป็นเวลา 2 สัปดาห์:

```
Ad Group A (Optimize แบบนับจำนวน CompletePayment):
  จำนวน Order: 45 Order/สัปดาห์
  AOV เฉลี่ย: 380 บาท
  Revenue รวม: 17,100 บาท/สัปดาห์

Ad Group B (Value-based Optimization):
  จำนวน Order: 32 Order/สัปดาห์ (น้อยกว่า)
  AOV เฉลี่ย: 720 บาท (สูงกว่าเกือบ 2 เท่า)
  Revenue รวม: 23,040 บาท/สัปดาห์ (สูงกว่า แม้จำนวน Order น้อยกว่า)
```

ตัวอย่างนี้แสดงให้เห็นแก่นของ VBO ชัดเจน: จำนวน Order ที่น้อยกว่าไม่ได้แปลว่าแย่กว่าเสมอไป ถ้า Order ที่ได้มามีมูลค่าเฉลี่ยสูงกว่าอย่างมีนัยสำคัญ ธุรกิจที่มี Margin คงที่เป็นเปอร์เซ็นต์ (เช่น 30% ของยอดขาย) จะได้กำไรรวมสูงกว่าจาก Ad Group B แม้ CPA ต่อ Order อาจดูสูงกว่าเมื่อดูตัวเลขผิวเผิน

### เจาะลึกเพิ่ม: ผลกระทบของ VBO ต่อ Learning Phase

เพราะ VBO ต้องเรียนรู้สองมิติพร้อมกัน (ใครมีโอกาสซื้อ + ซื้อเท่าไหร่) ระยะเวลา Learning Phase ของ Ad Group ที่เปิด VBO มักยาวกว่า Ad Group ที่ Optimize แบบนับจำนวนธรรมดาเล็กน้อย (โดยเฉลี่ยอาจนานกว่า 20-40%) ธุรกิจที่เพิ่งเริ่มเปิด VBO ควรเผื่อเวลาประเมินผลอย่างน้อย 2 สัปดาห์เต็มก่อนตัดสินใจว่าใช้ได้ผลหรือไม่ ไม่ควรตัดสินใจจากข้อมูลสัปดาห์แรกเพียงอย่างเดียว

---

## Step 744: ปริมาณ Event ขั้นต่ำสำหรับการส่งมอบที่มั่นคง (Stable Delivery)

### ทำไม "ขั้นต่ำ" ไม่เท่ากับ "เพียงพอสำหรับผลลัพธ์ที่ดี"

เกณฑ์ 50 Event/สัปดาห์คือ**ขั้นต่ำที่ระบบต้องการเพื่อออกจาก Learning Limited** แต่ไม่ได้แปลว่าที่ 50 Event พอดี Performance จะดีที่สุดแล้ว ในทางปฏิบัติ Ad Group ที่มี Event สะสม **100–200+ ต่อสัปดาห์** มักให้ CPA ที่เสถียรกว่าและ Machine Learning เรียนรู้ Pattern ได้แม่นยำกว่า Ad Group ที่มีเพียง 50–60 Event ที่ยังถือว่าอยู่ในระดับ "ผ่านเกณฑ์ต่ำสุด" เท่านั้น

### ปัจจัยที่กระทบปริมาณ Event ที่ต้องการ

1. **ความหลากหลายของ Audience** — Ad Group ที่ Targeting กว้างต้องการ Event มากกว่า Ad Group ที่ Targeting แคบและเจาะจงชัดเจน เพื่อให้ระบบเรียนรู้ Pattern ได้ครอบคลุม
2. **ความผันแปรของ Value** — ถ้าใช้ VBO และสินค้ามีช่วงราคากว้างมาก ต้องการ Event มากกว่าปกติเพื่อให้ระบบเรียนรู้ทั้งมิติ "ใครซื้อ" และ "ซื้อเท่าไหร่"
3. **ฤดูกาล/ช่วงเวลา** — ช่วงเทศกาลที่มีการแข่งขันสูง (เช่น 11.11, 12.12) การแข่งประมูลรุนแรงขึ้นทำให้ต้องการ Event สะสมมากกว่าปกติเพื่อรักษาความเสถียรของ Delivery

### สัญญาณที่บอกว่า Ad Group มี Event ไม่พอ

- Delivery Status ค้างที่ "Learning" นานเกิน 7 วันไม่ยอมเปลี่ยนเป็น "Active"/Exit Learning
- CPA ผันผวนขึ้นลงรุนแรงวันต่อวัน (บางวันถูกมาก บางวันแพงมาก) ไม่มี Pattern ที่สม่ำเสมอ
- Spend ไม่เป็นไปตาม Budget ที่ตั้งไว้ (Under-delivery) ต่อเนื่องหลายวัน

### แนวทางแก้ไขเมื่อ Event ไม่พอ

1. **รวม Ad Group** — ถ้ามีหลาย Ad Group ที่ Targeting ใกล้เคียงกันและแต่ละตัว Event ไม่พอ ให้รวมเป็น Ad Group เดียวที่ Budget สูงขึ้น (ตามหลัก Consolidation ที่เรียนใน Part 067 Step 668)
2. **ขยาย Targeting** — เปิด Automatic Targeting หรือลด Interest ที่แคบเกินไปออก เพื่อให้ระบบหา Audience ได้กว้างขึ้น
3. **ลดระดับ Event ที่ Optimize ลง** — ถ้า CompletePayment ยังไม่พอ ให้ถอยไป InitiateCheckout หรือ AddToCart ก่อนตามที่เรียนใน Step 742
4. **เพิ่ม Budget** — ถ้างบยังมีพื้นที่เพิ่มได้ การเพิ่ม Budget มักช่วยให้ Event สะสมเร็วขึ้นตรงที่สุด

### ข้อผิดพลาดที่พบบ่อย

- แก้ปัญหา Event ไม่พอด้วยการสร้าง Ad Group ใหม่ซ้ำๆ (แทนที่จะแก้ Ad Group เดิม) ทำให้ Learning Phase เริ่มใหม่ทุกครั้งไม่มีวันสะสมข้อมูลได้
- ไม่รู้ว่าตัวเองอยู่ในสถานะ Learning Limited เพราะไม่เคยเช็กคอลัมน์ Delivery Status เลย ปล่อยแคมเปญวิ่งแบบ Performance ไม่แน่นอนนานหลายสัปดาห์

### เจาะลึกเพิ่ม: ตารางเทียบเกณฑ์ Event ระหว่าง Facebook และ TikTok

| ประเด็น | Facebook | TikTok |
|---|---|---|
| เกณฑ์ Event ขั้นต่ำ | ~50 Event/สัปดาห์/Ad Set | ~50 Event/สัปดาห์/Ad Group |
| สถานะ Learning ที่ต่ำกว่าเกณฑ์ | "Learning Limited" | "Learning Limited" |
| ผลกระทบเมื่อต่ำกว่าเกณฑ์ | CPA ผันผวน, Delivery ไม่สม่ำเสมอ | CPA ผันผวน, Delivery ไม่สม่ำเสมอ (ผลกระทบใกล้เคียงกันมาก) |
| การไล่ระดับ Event เมื่อ Data ไม่พอ | แนวคิดเดียวกัน (Micro-conversion ก่อน) | แนวคิดเดียวกัน (Micro-conversion ก่อน) |
| ความอ่อนไหวต่อการเปลี่ยน Budget กะทันหัน | รีเซ็ต Learning บางส่วนถ้าเกิน ±20% | รีเซ็ต Learning บางส่วนในลักษณะคล้ายกัน |

ตารางนี้ยืนยันว่าหลักการพื้นฐานของ Machine Learning ทั้งสองแพลตฟอร์มคล้ายกันมาก ต่างกันที่รายละเอียดของ UI และ Field เท่านั้น การเข้าใจหลักการนี้อย่างลึกซึ้งจากแพลตฟอร์มหนึ่งช่วยให้เรียนรู้แพลตฟอร์มอื่นได้เร็วขึ้นมาก

### เจาะลึกเพิ่ม: การใช้ Lookalike/Custom Audience ช่วยเร่งการสะสม Event

วิธีหนึ่งที่ช่วยให้ Ad Group ผ่านเกณฑ์ Event เร็วขึ้นโดยไม่ต้องรอ Automatic Targeting อย่างเดียว คือการใช้ **Custom Audience จาก Pixel Data ที่สะสมไว้แล้ว** (เช่น Website Visitor 30 วัน, AddToCart 7 วัน) มาเป็น Targeting เสริมใน Ad Group ที่ Optimize CompletePayment เพราะกลุ่มนี้มี Signal ความสนใจสูงกว่า Cold Audience ทั่วไป ทำให้ Conversion Rate สูงกว่าและได้ Event สะสมเร็วกว่า (รายละเอียดเต็มรูปแบบเรื่อง Custom Audience/Lookalike บน TikTok จะเรียนใน Part 083)

---

## Step 745: สร้าง Ad Group และ Ad สำหรับแคมเปญ Conversion แบบ Step-by-Step

### สร้าง Campaign

กด Create ใน Custom Mode เลือกกลุ่ม **Conversion** แล้วคลิก **"Website Conversion"** ตั้งชื่อตาม Naming Convention (`TT_Conv_[สินค้า]_[YYMMDD]_v1`) เลือก Advertising Type = Regular กด Next

### Ad Group: Promotion Type และ Pixel

หน้า Ad Group จะให้เลือก:

1. **Promotion Type** = Website (ถูกกำหนดอัตโนมัติตาม Objective)
2. **Pixel** — เลือก Pixel ที่ติดตั้งบนเว็บไซต์ (ต้องเลือกให้ตรง ถ้ามีหลาย Pixel ในบัญชี)
3. **Optimization Event** — เลือก Event ตามหลักการที่เรียนใน Step 741–742 (เริ่มจาก Event ที่มี Volume พอตามข้อมูลจริงของธุรกิจ)
4. **Value Optimization Toggle** — เปิดถ้าตัดสินใจใช้ VBO ตามเงื่อนไขใน Step 743

### Targeting, Placement

หลักการเดียวกับที่เรียนใน Part 073 Step 725 ทุกประการ (Location, Age, Gender, Interest & Behavior, Automatic Targeting, Placement) เพียงแต่สำหรับ Conversion Campaign แนะนำให้เปิด **Automatic Targeting** มากกว่า Objective อื่นๆ เพราะ Conversion Event มี Signal ที่ชัดเจนกว่ามาก (ระบบรู้แน่ชัดว่าใคร "ซื้อจริง") การให้ AI ขยาย Audience กว้างขึ้นเองมักได้ผลดีกว่าจำกัด Targeting แคบด้วยมือ เมื่อมี Pixel Data สะสมเพียงพอแล้ว

### Budget & Bid Strategy

ตั้งค่าตามที่จะเรียนละเอียดใน Step 746 — สรุปสั้นคือ Conversion Campaign ต้องการ Budget สูงกว่า Traffic/Reach/Lead อย่างมีนัยสำคัญ เพราะ Event ที่ Optimize อยู่ปลายสุดของ Funnel มีอัตราเกิดต่ำที่สุด

### Ad Level: Creative และ Destination

หลักการเหมือน Part 073 Step 727 ทุกประการ (Identity, Ad Format, อัปโหลดวิดีโอ 9:16, Ad Text, CTA) จุดต่างสำคัญคือ:

1. **Destination URL ต้องเป็นหน้า Product Detail Page หรือหน้าที่ตรงกับ Event ที่ Optimize** — ถ้า Optimize ที่ CompletePayment แต่พาไปหน้า Home Page ทั่วไป จะทำให้ Conversion Rate ต่ำเพราะคนต้องคลิกซ้ำหลายจังหวะกว่าจะไปถึงหน้าสั่งซื้อ
2. **CTA ควรเป็น "Shop Now" หรือ "Order Now"** ที่สื่อความชัดเจนว่าเป็นการซื้อ ไม่ใช่ "Learn More" ที่คลุมเครือ
3. **Creative ต้องแสดงสินค้า/ราคา/โปรโมชั่นชัดเจน** เพราะคนที่จะ Convert จริงต้องเห็นข้อมูลตัดสินใจสำคัญ (ราคา, จุดขาย) ตั้งแต่ในวิดีโอโฆษณา ไม่ใช่แค่ Hook ความสนใจแบบ Awareness Campaign

### ตัวอย่าง Ad Group ที่ตั้งค่าสมบูรณ์

```
Ad Group: TT_Conv_Broad-Beauty_18-45All_AutoTargeting_v1
Promotion Type: Website
Pixel: ABC-Cosmetics-TikTokPixel
Optimization Event: Complete Payment
Value Optimization: ปิด (สินค้าราคาใกล้เคียงกันทั้งหมด)
Targeting: Location Thailand, Gender All, Age 18-44
Automatic Targeting: เปิด
Placement: Automatic Placement
Budget: Daily 1,500 บาท/วัน
Bid Strategy: Lowest Cost
```

### ข้อผิดพลาดที่พบบ่อย

- ตั้ง Destination URL เป็นหน้า Home Page ทั่วไปแทนหน้าสินค้าที่ตรงกับโฆษณา ทำให้เสีย Conversion ไปกับความสับสนของผู้ใช้
- เลือก Pixel ผิดตัว (มีหลาย Pixel ในบัญชีจากการทดสอบเก่า) ทำให้ Event ไม่ตรงกับ Traffic จริง

### เจาะลึกเพิ่ม: Attribution Window ที่ระดับ Ad Group

ในหน้า Ad Group ของ Website Conversion จะมีส่วน **"Attribution Settings"** ให้เลือก Click-through Window (1, 7, หรือ 28 วัน) และ Engaged-view/View-through Window (1 วัน เป็นค่ามาตรฐาน) ค่า Default ของ TikTok มักเป็น Click-through 7 วัน + View-through 1 วัน ซึ่งเหมาะกับสินค้าทั่วไปที่ตัดสินใจซื้อไม่นานหลังเห็นโฆษณา

สำหรับสินค้าที่ Customer Journey ยาวกว่าปกติ (เช่น สินค้ามูลค่าสูงที่คนต้องเปรียบเทียบหลายวัน) อาจพิจารณาขยายเป็น Click-through 28 วัน แต่ต้องเข้าใจว่า Window ที่ยาวขึ้นจะทำให้ ROAS ที่แสดงดูดีขึ้นเพราะนับ Conversion ที่เกิดห่างจากการคลิกนานขึ้นด้วย ไม่ใช่เพราะแคมเปญมีประสิทธิภาพดีขึ้นจริง ต้องระวังไม่ให้ตีความผิดเมื่อเปรียบเทียบ Performance ข้ามช่วงเวลาที่ตั้ง Attribution Window ต่างกัน

### เจาะลึกเพิ่ม: การทดสอบ Automatic Targeting เทียบกับ Manual Targeting สำหรับ Conversion

แนะนำให้ทดสอบสองแบบคู่ขนานเมื่อมี Budget เพียงพอ: Ad Group หนึ่งเปิด Automatic Targeting เต็มรูปแบบ อีกตัวใช้ Manual Targeting ที่กำหนด Interest ตาม Custom Audience ที่มีอยู่ รันพร้อมกัน 2 สัปดาห์ด้วย Budget เท่ากัน แล้วเทียบ CPA/ROAS โดยทั่วไปธุรกิจที่มี Pixel Data สะสมมากแล้วมักพบว่า Automatic Targeting ให้ผลลัพธ์ดีกว่าหรือใกล้เคียงกับ Manual Targeting เพราะ AI เข้าถึง Signal ได้กว้างกว่า แต่ธุรกิจที่มีเงื่อนไข Targeting เฉพาะทาง (เช่น ต้องจำกัดอายุตามกฎหมาย) ยังจำเป็นต้องใช้ Manual Targeting ควบคู่ไปด้วยเสมอ

---

## Step 746: แนวทางกำหนดงบประมาณสำหรับแคมเปญ Conversion บนตลาดไทย

### ทำไม Conversion Campaign ต้องการ Budget สูงกว่า Objective อื่น

Event ที่ Optimize อยู่ปลาย Funnel (เช่น Purchase) มีอัตราเกิดต่ำกว่า Event ต้น Funnel มาก (เช่น Click, View) ตามธรรมชาติของ Funnel เอง (ตามที่เรียนใน Part 005 Step 41) ดังนั้นเพื่อให้ได้ Event สะสมครบ 50+ ต่อสัปดาห์ตามเกณฑ์ Learning Phase Budget ที่ต้องใช้จึงสูงกว่า Traffic/Reach/Lead อย่างมีนัยสำคัญ

### ตาราง Budget ขั้นต่ำที่แนะนำตาม Conversion Rate ของเว็บไซต์

| Website Conversion Rate | Cost per Purchase โดยประมาณ | Daily Budget ขั้นต่ำที่แนะนำ (เพื่อให้ได้ 50+ Purchase/สัปดาห์) |
|---|---|---|
| ต่ำ (<1%) | สูง (300+ บาท) | 2,500–3,500 บาท/วัน |
| กลาง (1–3%) | กลาง (150–300 บาท) | 1,200–2,200 บาท/วัน |
| สูง (3%+) | ต่ำ (<150 บาท) | 700–1,200 บาท/วัน |

ตัวเลขเหล่านี้เป็นแนวทางเริ่มต้นที่ต้องปรับตาม Margin สินค้าจริงและ Break-even ROAS ของธุรกิจ (ตามที่คำนวณไว้ใน Part 004 Step 34) ห้ามตั้ง Budget สูงเกินกว่าที่ธุรกิจรับความเสี่ยงได้แม้จะรู้ว่าต้องใช้ Budget สูงเพื่อผ่าน Learning Phase

### กลยุทธ์สำหรับธุรกิจที่งบไม่พอสำหรับ CompletePayment โดยตรง

ถ้าคำนวณแล้ว Budget ที่ต้องใช้เกินกว่าที่ธุรกิจรับได้ ให้กลับไปใช้หลักการไล่ระดับ Event จาก Step 742: เริ่ม Optimize ที่ Event สูงกว่าใน Funnel ก่อน (เช่น InitiateCheckout) สะสม Performance และข้อมูล Custom Audience สัก 2–4 สัปดาห์ แล้วค่อยขยับ Budget และ Event ลึกลงไปเมื่อธุรกิจมีรายได้จากแคมเปญกลับมาหมุนต่อได้

### การปรับ Budget เมื่อ Performance ดีแล้ว (Scaling)

หลักการเดียวกับที่เรียนใน Part 073 Step 726 และ Part 021 Step 205: ปรับ Budget ทีละ 15–20% ทุก 2–3 วัน ไม่กระโดดข้ามทีเดียว โดยเฉพาะ Conversion Campaign ที่ Learning Phase อ่อนไหวต่อการเปลี่ยนแปลง Budget มากกว่า Objective อื่น (รายละเอียดเต็มรูปแบบเรื่อง Scaling Strategy จะเรียนใน Part 086)

### ข้อผิดพลาดที่พบบ่อย

- ตั้ง Budget ตามที่ "อยากได้ยอดขาย" โดยไม่คำนวณจาก Conversion Rate จริงของเว็บไซต์ก่อน ทำให้ Budget ต่ำเกินกว่าจะผ่าน Learning Phase ได้เลย
- Scale Budget ก้าวกระโดดทันทีที่เห็น ROAS ดีในวันแรกๆ (ซึ่งอาจเป็นความผันผวนปกติของ Learning Phase ไม่ใช่ Performance ที่เสถียรจริง) ทำให้ Performance ร่วงลงทันทีหลัง Scale

---

## Step 747: ข้อผิดพลาดที่พบบ่อย — Optimize Event ผิดจังหวะเร็วเกินไป

### รูปแบบความผิดพลาดที่พบบ่อยที่สุดของ Conversion Campaign บน TikTok

ความผิดพลาดที่ร้ายแรงที่สุดและพบบ่อยที่สุดคือการ **Optimize Event ที่ลึกเกินไปเทียบกับข้อมูลที่มี** ซึ่งมีรูปแบบย่อยดังนี้:

1. **บัญชีใหม่เริ่ม Optimize ที่ CompletePayment ทันที** ไม่มี Pixel Data สะสมมาก่อนเลย — ระบบไม่มี Signal พอเรียนรู้ ผลคือ Delivery ไม่ออกหรือ CPA สูงลอยจนไม่คุ้มค่า
2. **เปลี่ยน Event ที่ Optimize กลางทางบ่อยเกินไป** เห็นว่า Purchase Event มาช้าเลยสลับไป AddToCart แล้วพอ AddToCart มาเยอะก็สลับกลับไป Purchase อีก ทำให้ Learning Phase รีเซ็ตซ้ำๆ ไม่มีวันได้ข้อมูลที่เสถียร
3. **เปิด VBO ก่อนมี Purchase Event สะสมพอ** ตามที่เรียนใน Step 743 ทำให้ความซับซ้อนเกินกว่า Data ที่มีจะรองรับได้

### วิธีวินิจฉัยว่ากำลัง Optimize ผิดจังหวะหรือไม่

เช็กคำถามเหล่านี้:

- Ad Group นี้อยู่ในสถานะ "Learning Limited" นานเกิน 7 วันหรือไม่?
- Cost per Result สูงกว่า Benchmark ของธุรกิจตัวเองมากกว่า 2-3 เท่าอย่างต่อเนื่องหรือไม่?
- เคยเปลี่ยน Optimization Event ของ Ad Group นี้มากกว่า 1 ครั้งในช่วง 2 สัปดาห์ที่ผ่านมาหรือไม่?

ถ้าตอบ "ใช่" ข้อใดข้อหนึ่ง ให้พิจารณากลับไปใช้ Event ที่อยู่สูงขึ้นใน Funnel ก่อน แล้วค่อยไล่ระดับกลับลงมาอย่างมีระบบตามที่เรียนใน Step 742 ไม่ใช่สลับไปมาแบบไม่มีแผน

### กรอบเวลาที่แนะนำสำหรับการไล่ระดับ Event อย่างมีระบบ

```
สัปดาห์ที่ 1-2: Optimize ที่ ViewContent หรือ AddToCart (ตาม Volume ที่มี)
  → เก็บข้อมูล Custom Audience และ Pattern ผู้เข้าชม
สัปดาห์ที่ 3-4: ประเมิน Volume Purchase Event ที่เกิดขึ้นเองจากแคมเปญ
  → ถ้า Purchase สะสม ≥50/สัปดาห์แล้ว ค่อยสร้าง Ad Group ใหม่ (หรือ Duplicate)
     ที่ Optimize ตรงที่ InitiateCheckout หรือ CompletePayment
สัปดาห์ที่ 5 เป็นต้นไป: ถ้า Ad Group ใหม่ผ่าน Learning Phase ได้ดี
  → ค่อยปิด Ad Group เดิมที่ Optimize Event ต้น Funnel ทีละน้อย ย้าย Budget มาที่ตัวใหม่
```

### ข้อผิดพลาดที่พบบ่อย

- ใจร้อนอยากเห็นยอดขายทันที ข้าม Step การไล่ระดับทั้งหมดไปเริ่มที่ CompletePayment เลยตั้งแต่วันแรก
- ปิด Ad Group เดิมทันทีที่สร้าง Ad Group ใหม่ที่ Optimize Event ลึกกว่า ทำให้ขาดข้อมูล Buffer ระหว่างการเปลี่ยนผ่าน

---

## Step 748: การอ่าน Metric ของแคมเปญ Conversion อย่างมืออาชีพ

### Metric หลักที่ต้องดูสำหรับ Conversion Campaign

| Metric | ความหมาย | สิ่งที่บอก |
|---|---|---|
| **Cost per Result (CPA)** | ต้นทุนต่อ Conversion Event ที่เลือก Optimize | ต้นทุนจริงต่อลูกค้าหนึ่งราย เทียบกับ Break-even ที่ยอมรับได้ |
| **ROAS (Return on Ad Spend)** | รายได้หารด้วย Ad Spend | ตัวชี้วัดหลักว่าแคมเปญคุ้มค่าหรือไม่ (ต้องมี Value Parameter ยิงมาถูกต้อง) |
| **Conversion Rate (Click to Purchase)** | สัดส่วนคนที่คลิกแล้วซื้อจริง | สะท้อนคุณภาพ Landing Page ควบคู่กับคุณภาพ Traffic |
| **Complete Payment Rate** | สัดส่วน InitiateCheckout ที่จบเป็น CompletePayment | บอกปัญหาที่ขั้นตอนชำระเงิน ถ้าต่ำมากอาจมีปัญหา UX/ระบบชำระเงิน |
| **Frequency** | จำนวนครั้งเฉลี่ยที่คนเห็นโฆษณา | ถ้าสูงเกินไปอาจเกิด Ad Fatigue กระทบ Conversion Rate |
| **Delivery Status** | สถานะ Learning ของ Ad Group | บอกว่าระบบยังเรียนรู้อยู่หรือนิ่งแล้ว |

### การอ่าน ROAS ให้ถูกต้อง

ROAS ที่ TikTok Ads Manager แสดงคำนวณจาก Value ที่ Pixel/Events API ส่งมา **เฉพาะ Event ที่ Attribution Window ครอบคลุม** (ตั้งค่า Attribution Window ได้ที่ระดับ Ad Group เช่น Click-through 7 วัน, View-through 1 วัน) ถ้า Attribution Window ตั้งสั้นเกินไปเทียบกับ Customer Journey จริงของธุรกิจ ROAS ที่แสดงจะดูต่ำกว่าความเป็นจริง ควรเทียบ ROAS จาก TikTok กับ ROAS จริงที่คำนวณจาก Google Analytics/ระบบขายจริงเป็นระยะ เพื่อเช็ก Discrepancy (ความคลาดเคลื่อน) ระหว่างสองระบบ

### Breakdown ที่ควรใช้ประกอบการวิเคราะห์

- **Breakdown by Age/Gender** — หา Segment ที่ ROAS ดีที่สุดเพื่อปรับ Targeting ในรอบถัดไป
- **Breakdown by Placement** — เช็กว่า TikTok App กับ Pangle ให้ ROAS ต่างกันแค่ไหน (ถ้าเลือก Automatic Placement)
- **Breakdown by Ad** — หา Creative ที่ Convert ดีที่สุดเพื่อทำ Creative Testing ต่อ (เจาะลึกเต็มรูปแบบใน Section I)

### ข้อผิดพลาดที่พบบ่อยในการอ่าน Metric

- ดูแค่ CPA/ROAS วันเดียวแล้วตัดสินใจทันที ไม่ดู Trend สะสมอย่างน้อย 3-7 วัน ทำให้ตัดสินใจผิดจากความผันผวนปกติของ Learning Phase
- ไม่เทียบ ROAS จาก TikTok กับข้อมูลขายจริง ทำให้เข้าใจผิดว่าแคมเปญขาดทุน/ได้กำไรทั้งที่ตัวเลขจริงต่างจากที่ Ads Manager แสดง เพราะปัญหา Attribution Window หรือ Pixel Match Quality

### เจาะลึกเพิ่ม: Frequency และ Ad Fatigue ในแคมเปญ Conversion ระยะยาว

แคมเปญ Conversion ที่รันต่อเนื่องนานหลายสัปดาห์มีความเสี่ยงเรื่อง **Ad Fatigue** เหมือนกับ Facebook (ตามที่เรียนใน Part 060) คือ Frequency สูงขึ้นเรื่อยๆ จนคนกลุ่มเดิมเห็นโฆษณาซ้ำมากเกินไป ทำให้ CTR และ Conversion Rate ลดลง แม้ Targeting/Budget จะเหมือนเดิมทุกอย่าง สัญญาณที่ควรจับตาคือ Frequency ที่เกิน 3-4 ครั้ง/สัปดาห์/คนในกลุ่ม Prospecting (ไม่ใช่ Retargeting ที่ยอมรับ Frequency สูงกว่าได้) เมื่อเห็นสัญญาณนี้ ควรพิจารณาผลิต Creative ใหม่มาสลับ หรือขยาย Targeting ให้กว้างขึ้นเพื่อลด Frequency ต่อคน

### เจาะลึกเพิ่ม: ตารางสรุปการวินิจฉัยปัญหา Conversion Campaign เบื้องต้น

| อาการที่เจอ | สาเหตุที่เป็นไปได้มากที่สุด | วิธีแก้ |
|---|---|---|
| CPA สูงกว่า Break-even มาก ตั้งแต่วันแรก | Optimize Event ลึกเกินไปเทียบกับ Data ที่มี | ถอยไป Optimize Event ที่สูงขึ้นใน Funnel |
| Delivery Status ค้างที่ Learning Limited | Event ต่อสัปดาห์ไม่ถึง 50 | เพิ่ม Budget, ขยาย Targeting, หรือรวม Ad Group |
| ROAS ผันผวนรุนแรงวันต่อวัน | Purchase Event สะสมยังน้อย, VBO เปิดเร็วเกินไป | รอให้ Data สะสมมากขึ้น, ปิด VBO ชั่วคราว |
| Conversion Rate (Click to Purchase) ต่ำผิดปกติ | Landing Page ไม่ตรงกับโฆษณา, หน้าเว็บโหลดช้า | เช็ก Page Speed, เช็ก Message Match ระหว่างโฆษณาและหน้าเว็บ |
| ROAS จาก TikTok สูงกว่ายอดขายจริงมาก | Attribution Window ยาวเกินไป, Over-count จาก View-through | ปรับ Attribution Window ให้สอดคล้องกับ Customer Journey จริง |
| Complete Payment Rate ต่ำ (คนเข้า Checkout แต่ไม่จ่าย) | ระบบชำระเงินมีปัญหา, ค่าส่งสูงเกินคาด | ทดสอบขั้นตอนชำระเงินด้วยตัวเอง, เช็ก UX หน้า Checkout |

---

## Step 749: App Conversion Campaigns เบื้องต้นและความต่างจาก Website Conversion

### ภาพรวม App Conversion

**App Conversion** เป็น Objective สำหรับธุรกิจที่มี Mobile App และต้องการ Optimize เพื่อ In-app Event (เช่น การสมัครสมาชิกในแอป, การซื้อ In-app Purchase, การจองผ่านแอป) แทนที่จะเป็น Event บนเว็บไซต์

### ข้อกำหนดพิเศษที่ต่างจาก Website Conversion

1. **ต้องเชื่อมต่อกับ Mobile Measurement Partner (MMP)** เช่น AppsFlyer, Adjust, Kochava เพื่อ Track In-app Event แทนการใช้ Pixel บนเว็บ (TikKok ไม่สามารถอ่าน Event ในแอปได้ตรงๆ ต้องผ่าน MMP เป็นตัวกลางส่งข้อมูล)
2. **ต้องลงทะเบียน App ใน TikTok Ads Manager** ก่อน (เมนู Assets > App) เชื่อมกับ App Store/Play Store Listing ให้ถูกต้อง
3. **In-app Event ที่เลือก Optimize ได้** เช่น App Install, Registration, Purchase, Achieve Level (สำหรับเกม), Subscribe

### ตารางเทียบ Website Conversion vs App Conversion

| ประเด็น | Website Conversion | App Conversion |
|---|---|---|
| ระบบ Track | TikTok Pixel + Events API | MMP (AppsFlyer, Adjust ฯลฯ) |
| Destination | Website URL | App Store/Play Store Listing หรือ Deep Link เข้าแอปตรง |
| Event หลัก | ViewContent, AddToCart, CompletePayment | Install, Registration, Purchase, In-app Event Custom |
| ความซับซ้อนการติดตั้ง | ปานกลาง (Pixel + Tag Manager) | สูงกว่า (ต้องผ่าน SDK ของ MMP ในตัวแอป) |

### เมื่อไหร่ธุรกิจควรพิจารณา App Conversion

ธุรกิจที่มี App เป็นช่องทางหลักในการขาย/ให้บริการ (เช่น App สั่งอาหาร, App จองที่พัก, Game Mobile) ควรใช้ App Conversion โดยตรงแทนการพา Traffic ไปเว็บไซต์แล้วค่อยให้ดาวน์โหลดแอปทีหลัง เพราะ Deep Link และการ Track ที่ตรงกว่าจะให้ผลลัพธ์ดีกว่ามาก

### ข้อผิดพลาดที่พบบ่อย (ระดับเบื้องต้นที่ควรรู้ก่อนเริ่ม)

- ไม่เชื่อมต่อ MMP ให้ครบก่อนเริ่มแคมเปญ ทำให้ไม่มี Event ให้ Optimize เลยตั้งแต่ต้น
- สร้างแคมเปญ App Conversion แต่ใส่ Destination เป็น Website URL ทั่วไปแทน App Store Link ทำให้ผู้ใช้สับสนไม่รู้จะดาวน์โหลดอย่างไร

### เจาะลึกเพิ่ม: Deep Linking สำหรับผู้ใช้ที่มีแอปติดตั้งอยู่แล้ว

สำหรับผู้ใช้ที่มี App ติดตั้งอยู่ในมือถือแล้ว (ไม่ต้องดาวน์โหลดใหม่) TikTok รองรับ **Deep Link** ที่พาผู้ใช้เข้าไปยังหน้าเฉพาะภายในแอปได้ตรง (เช่น หน้าสินค้าเฉพาะตัวในแอป ไม่ใช่หน้า Home ของแอป) ต้องตั้งค่า Deep Link URL Scheme ร่วมกับทีม Developer ก่อน และทดสอบให้แน่ใจว่า Deep Link ทำงานได้ทั้งกรณีมีแอปอยู่แล้ว (เปิดตรงเข้าแอป) และกรณียังไม่มีแอป (Fallback ไปหน้า Store ให้ดาวน์โหลดก่อน) การตั้งค่า Deep Link ที่ถูกต้องช่วยเพิ่ม Conversion Rate ได้มากสำหรับผู้ใช้กลุ่มที่เคยติดตั้งแอปแล้วแต่ยังไม่ได้ใช้งานต่อ (Re-engagement)

### เจาะลึกเพิ่ม: Attribution Window สำหรับ App Conversion

App Conversion Campaign มี Attribution Window ที่ตั้งค่าได้แยกจาก Website Conversion เช่น **Click-through 7 วัน + View-through 1 วัน** เป็นค่ามาตรฐานที่ MMP ส่วนใหญ่รองรับ ธุรกิจที่มี Customer Journey ยาวกว่าปกติ (เช่น เกมที่คนดูโฆษณาหลายรอบก่อนตัดสินใจโหลด) อาจพิจารณาขยาย Window ให้ยาวขึ้น แต่ต้องระวังว่า Window ที่ยาวเกินไปจะทำให้ตัวเลข Conversion ดูดีเกินจริงเมื่อเทียบกับพฤติกรรมจริงของผู้ใช้

> รายละเอียดเชิงลึกเรื่อง App Promotion Campaign เต็มรูปแบบ (การตั้งค่า MMP แบบ Step-by-Step, Deep Linking, App Event Optimization ระดับสูง) จะไม่ได้เจาะลึกทั้งหมดใน Part นี้ เพราะ Part นี้โฟกัสที่ Website Conversion เป็นหลัก แต่ประเด็นพื้นฐานที่ควรรู้ไว้ก่อนคือความต่างของระบบ Track และ Destination ตามตารางข้างต้น

---

## Case Study: ร้านเครื่องสำอางออนไลน์ไล่ระดับ Event จนถึง Purchase Conversion สำเร็จ

ร้านเครื่องสำอางออนไลน์ขนาดกลาง มีเว็บไซต์ที่ทำ Conversion Rate เฉลี่ย 1.8% (อยู่ในระดับกลาง) เพิ่งเริ่มยิง TikTok Ads เป็นครั้งแรกโดยไม่มี Pixel Data สะสมเลย ต้องการยอดขายจาก TikTok ให้ได้ ROAS ที่คุ้มค่าภายใน 2 เดือน

**สัปดาห์ที่ 1-2: Optimize ที่ AddToCart**

```
Campaign: TT_Conv_เซรั่มวิตซี_260801_v1
Ad Group: TT_Conv_Broad-Beauty_18-44All_AutoTargeting_v1
Optimization Event: Add to Cart
Budget: 800 บาท/วัน
```

ผลลัพธ์: AddToCart สะสมเฉลี่ย 95 ครั้ง/สัปดาห์ (ผ่านเกณฑ์ 50 อย่างสบาย) แต่ Purchase ที่เกิดขึ้นเองมีเพียง 12-15 ครั้ง/สัปดาห์ (ยังไม่ถึง 50 สำหรับ Optimize ตรงที่ CompletePayment)

**สัปดาห์ที่ 3-4: สร้าง Ad Group ใหม่ Optimize ที่ InitiateCheckout ควบคู่กับตัวเดิม**

ทีมไม่ปิด Ad Group เดิมทันที แต่สร้าง Ad Group ใหม่แยกทดสอบ Optimize ที่ InitiateCheckout เพิ่ม Budget เป็น 1,200 บาท/วันสำหรับ Ad Group ใหม่ ผลลัพธ์: InitiateCheckout สะสมได้ 58 ครั้ง/สัปดาห์ (ผ่านเกณฑ์) และ Purchase เพิ่มขึ้นมาเป็น 22-25 ครั้ง/สัปดาห์ (ยังไม่ผ่านเกณฑ์ 50 สำหรับ Purchase ตรง แต่แนวโน้มดีขึ้นชัดเจน)

**สัปดาห์ที่ 5-6: เพิ่ม Budget รวมเป็น 2,000 บาท/วัน และ Optimize ตรงที่ CompletePayment**

เมื่อเห็นแนวโน้ม Purchase เพิ่มขึ้นต่อเนื่อง ทีมตัดสินใจเพิ่ม Budget ของ Ad Group InitiateCheckout เป็น 2,000 บาท/วัน (เพิ่มทีละ 15-20% ทุก 3 วันตามหลักการ Step 746 ไม่กระโดดทีเดียว) และเมื่อ Purchase สะสมแตะ 48-52 ครั้ง/สัปดาห์ต่อเนื่อง 2 สัปดาห์ จึงสร้าง Ad Group ใหม่อีกตัว Optimize ตรงที่ CompletePayment โดยคง Ad Group เดิมไว้ควบคู่กันระยะหนึ่ง

**ผลลัพธ์เดือนที่ 2:** Ad Group ที่ Optimize CompletePayment ตรงเข้าสู่สถานะ Learning สำเร็จ (ไม่ Limited) ภายใน 5 วัน (เร็วกว่าที่คาด เพราะมี Custom Audience และ Pixel Data สะสมจากเดือนแรกรองรับอยู่แล้ว) ROAS เฉลี่ยอยู่ที่ 3.2 เท่า สูงกว่า Break-even ROAS ที่ธุรกิจตั้งไว้ (2.1 เท่า) อย่างมีนัยสำคัญ

**บทเรียนสำคัญ:** การไล่ระดับ Event อย่างมีระบบ (AddToCart → InitiateCheckout → CompletePayment) โดยไม่รีบข้ามขั้น และไม่ปิด Ad Group เดิมทันทีตอนสร้างตัวใหม่ ช่วยให้ธุรกิจที่เริ่มจาก Pixel Data เป็นศูนย์ ไปถึงจุดที่ Optimize CompletePayment ได้อย่างมั่นคงภายในเวลาที่เหมาะสม แทนที่จะพยายาม Optimize CompletePayment ตั้งแต่วันแรกซึ่งมีความเป็นไปได้สูงว่าจะล้มเหลวเพราะ Data ไม่พอ

**สาเหตุที่แผนไล่ระดับได้ผลในรอบที่สอง:** ปัจจัยหลักคือทีมให้เวลาแต่ละขั้นสะสมข้อมูลอย่างเพียงพอก่อนขยับต่อ ไม่รีบร้อน และคงข้อมูล Custom Audience/Pixel ที่สะสมมาจากขั้นก่อนหน้าไว้ใช้ประโยชน์ในขั้นถัดไปเสมอ แทนที่จะรีเซ็ตทุกอย่างใหม่ทุกครั้งที่เปลี่ยน Event

**สิ่งที่ทำผิดในเดือนแรกที่ควรบันทึกไว้เป็นบทเรียน:** ก่อนจะมาถึงแผนไล่ระดับที่ได้ผล ทีมนี้เคยลองสร้าง Ad Group Optimize ที่ CompletePayment ตรงตั้งแต่สัปดาห์แรกมาก่อนแล้ว (โดยไม่รู้หลักการไล่ระดับ) ผลคือ Ad Group นั้นใช้งบไปแล้ว 3,500 บาทตลอด 4 วันแต่ได้ Purchase เพียง 2 ครั้ง (CPA เกือบ 1,750 บาท ในขณะที่ Break-even ROAS ต้องการ CPA ไม่เกิน 400 บาท) และ Delivery Status ค้างที่ Learning Limited ตลอดเวลา ทีมจึงตัดสินใจปิด Ad Group นั้นและเริ่มใหม่ด้วยแผนไล่ระดับตามที่อธิบายไว้ข้างต้น ความแตกต่างของผลลัพธ์ระหว่างสองแนวทางนี้เป็นตัวอย่างที่ชัดเจนที่สุดว่าทำไม Step 747 (Optimize Event ผิดจังหวะ) ถึงเป็นข้อผิดพลาดที่ "แพง" ที่สุดในบรรดาข้อผิดพลาดทั้งหมดของ Conversion Campaign บน TikTok

---

## เจาะลึกเพิ่ม: ตารางสรุปเส้นทางไล่ระดับ Event แบบครบวงจร

สรุปภาพรวมทั้ง Part นี้ในตารางเดียว เพื่อใช้เป็น Quick Reference เมื่อต้องตัดสินใจว่าธุรกิจของตัวเองอยู่ในขั้นไหนและควรทำอะไรต่อ:

| ขั้น | Event ที่ Optimize | เงื่อนไขที่จะขยับไปขั้นถัดไป | ความเสี่ยงถ้าข้ามขั้นนี้ไปเร็วเกินไป |
|---|---|---|---|
| 1 | ViewContent | Event สะสม ≥50/สัปดาห์ต่อเนื่อง 1-2 สัปดาห์ | Data ไม่พอทุกขั้นถัดไป |
| 2 | AddToCart | Event สะสม ≥50/สัปดาห์ และเห็น Purchase เริ่มเกิดขึ้นเองบ้าง | Learning Limited ต่อเนื่อง, CPA ผันผวนสูง |
| 3 | InitiateCheckout | Event สะสม ≥50/สัปดาห์ และ Purchase เพิ่มขึ้นตามสัดส่วนที่คาด | เสียงบไปกับ Ad Group ที่ไม่นิ่ง |
| 4 | CompletePayment (นับจำนวน) | Purchase สะสม ≥50/สัปดาห์ต่อเนื่อง 2 สัปดาห์ | Delivery ไม่ออก, Under-delivery รุนแรง |
| 5 | CompletePayment (VBO) | Purchase สะสม ≥100/สัปดาห์ทั้งบัญชี และสินค้ามีช่วงราคากว้าง | Learning Phase ยาวเกินจำเป็น, ผลลัพธ์แย่กว่า Optimize แบบนับจำนวน |

### หลักการสำคัญที่ต้องย้ำอีกครั้ง

การไล่ระดับนี้ไม่ใช่กฎที่ต้องทำตามทุกขั้นแบบตายตัวเสมอไป ธุรกิจที่มี Traffic สูงอยู่แล้ว (เช่น มีฐานลูกค้าเดิมจำนวนมาก หรือมี Organic Traffic สูงจาก SEO/Social) อาจเริ่มที่ขั้น 3 หรือ 4 ได้ทันทีโดยไม่ต้องผ่านขั้น 1-2 เพราะมี Pixel Data สะสมมากพอในทันทีที่ติดตั้ง Pixel

สิ่งที่สำคัญที่สุดคือการ **ตรวจสอบ Volume ข้อมูลจริงก่อนตัดสินใจ** ไม่ใช่การท่องจำว่าต้องผ่านทุกขั้นตามลำดับเสมอ ตารางนี้เป็นกรอบความคิด (Framework) ให้ใช้ประกอบการตัดสินใจ ไม่ใช่สูตรตายตัวที่ใช้ได้กับทุกธุรกิจแบบเดียวกันหมด

---

## Checklist ท้ายบท

- [ ] เช็กว่า Pixel/Events API ติดตั้งและยิง Event ถูกต้องก่อนสร้างแคมเปญ Conversion
- [ ] เลือก Optimization Event ตามปริมาณ Traffic/Data จริงของเว็บไซต์ ไม่ใช่ตามที่ "อยากได้"
- [ ] คำนวณ Event ต่อสัปดาห์ที่คาดว่าจะได้ เทียบกับเกณฑ์ 50 Event/สัปดาห์ก่อนตั้ง Budget
- [ ] ตัดสินใจใช้ Value-based Optimization เฉพาะเมื่อสินค้ามีความหลากหลายราคาและมี Purchase Event สะสมพอ
- [ ] ตั้ง Destination URL ตรงกับหน้าที่สอดคล้องกับ Event ที่ Optimize
- [ ] ตั้ง Budget ตามระดับ Conversion Rate จริงของเว็บไซต์ ไม่ใช่ตัวเลขที่หวังไว้ลอยๆ
- [ ] ไล่ระดับ Event อย่างมีระบบถ้าบัญชียังใหม่ ไม่ข้ามไป CompletePayment ทันที
- [ ] ไม่สลับ Optimization Event ไปมาบ่อยเกินไปในช่วงเวลาสั้นๆ
- [ ] อ่าน ROAS เทียบกับข้อมูลขายจริงเป็นระยะ ไม่เชื่อตัวเลขจาก Ads Manager อย่างเดียว
- [ ] เช็ก Delivery Status สม่ำเสมอเพื่อวินิจฉัย Learning Limited แต่เนิ่นๆ
- [ ] สำหรับธุรกิจ App ให้เชื่อมต่อ MMP ให้ครบก่อนเริ่ม App Conversion Campaign
- [ ] ตั้งค่า Attribution Window ให้เหมาะกับ Customer Journey จริงของธุรกิจ ไม่ใช้ค่า Default โดยไม่พิจารณา
- [ ] เก็บข้อมูล Custom Audience จาก Pixel ตั้งแต่แคมเปญแรกแม้ Objective นั้นไม่บังคับต้องมี Pixel
- [ ] ทดสอบ Automatic Targeting คู่กับ Manual Targeting เมื่อ Budget เพียงพอ
- [ ] พิจารณาใช้ Custom Conversion เมื่อ Standard Event ไม่ตรงกับ Action ที่ธุรกิจต้องการวัดจริง
- [ ] เช็ก Frequency ของกลุ่ม Prospecting เป็นระยะ เพื่อป้องกัน Ad Fatigue ในแคมเปญที่รันต่อเนื่องนาน
- [ ] บันทึกทุกการเปลี่ยนแปลงสำคัญ (Event, Budget, Targeting) พร้อมวันที่ไว้เป็นประวัติ เพื่อวิเคราะห์ย้อนหลังได้ง่าย
- [ ] ทบทวน Checklist นี้ทุกครั้งก่อนสร้างแคมเปญ Conversion ใหม่ ไม่ใช่อ่านครั้งเดียวแล้วลืม

---

## Workshop / แบบฝึกหัด

### เตรียมตัวก่อนเริ่ม Workshop

ก่อนลงมือทำภารกิจต่อไปนี้ ให้เตรียมสิ่งเหล่านี้ให้พร้อม:

- สิทธิ์ Admin เข้าถึง TikTok Ads Manager และ Events Manager ของ Ad Account ที่จะใช้ทำ Workshop
- ข้อมูล Conversion Rate และ Traffic เฉลี่ยต่อเดือนของเว็บไซต์ (จาก Google Analytics)
- ข้อมูล Break-even ROAS/CAC ของธุรกิจที่คำนวณไว้แล้วจาก Part 004
- Google Sheet เปล่าสำหรับบันทึกข้อมูลระหว่างทำ Workshop ทุกภารกิจ

### ภารกิจที่ 1: ประเมินความพร้อมของ Pixel Data

ตรวจสอบ Events Manager ของ TikTok Pixel ธุรกิจตัวเอง/ลูกค้า นับจำนวน Event แต่ละประเภท (ViewContent, AddToCart, InitiateCheckout, CompletePayment) ในช่วง 30 วันที่ผ่านมา แล้วคำนวณเฉลี่ยต่อสัปดาห์ เทียบกับเกณฑ์ 50 Event/สัปดาห์ เพื่อตัดสินใจว่าควร Optimize ที่ Event ไหนเป็นจุดเริ่มต้น

### ภารกิจที่ 2: สร้างแผนไล่ระดับ Event เป็นลายลักษณ์อักษร

เขียนแผน 4-6 สัปดาห์ตามกรอบเวลาใน Step 747 ระบุว่าสัปดาห์ไหนจะ Optimize Event อะไร, Budget เท่าไหร่, และเงื่อนไขที่จะขยับไป Event ถัดไป (เช่น "ขยับเมื่อ Event สะสม ≥50/สัปดาห์ต่อเนื่อง 2 สัปดาห์")

### ภารกิจที่ 3: สร้างแคมเปญ Conversion จริงตามแผน

สร้างแคมเปญ Website Conversion ใน Custom Mode ตาม Step 745 ครบทุก Field ตั้ง Optimization Event ตามที่วิเคราะห์ไว้ในภารกิจที่ 1 พร้อม Creative Native 9:16 อย่างน้อย 3 ตัว

โครงสร้างที่ต้องทำให้ครบ:

```
Campaign: TT_Conv_[สินค้าหลัก]_[YYMMDD]_v1
  Ad Group: TT_Conv_Broad-[Interest]_[Age]_AutoTargeting_v1
    Ad: Video_โปรโมชั่น_v1
    Ad: Video_UGCรีวิว_v1
    Ad: Video_Testimonial_v1
```

### ภารกิจที่ 4: ทำ Dashboard ติดตาม Metric รายสัปดาห์

สร้าง Google Sheet บันทึก Spend, Event ที่เกิดขึ้นจริงแต่ละประเภท, CPA, ROAS, Delivery Status ของแคมเปญทุกสัปดาห์ต่อเนื่อง 4-6 สัปดาห์ เพื่อเห็นแนวโน้มการไล่ระดับ Event ตามแผนที่วางไว้ในภารกิจที่ 2

### ภารกิจที่ 5: วิเคราะห์ ROAS จาก TikTok เทียบกับข้อมูลขายจริง

หลังแคมเปญรันครบ 2 สัปดาห์ ดึงยอดขายจริงจากระบบหลังบ้าน (เว็บไซต์/CRM) มาเทียบกับ ROAS ที่ TikTok Ads Manager แสดง คำนวณ Discrepancy (%) และวิเคราะห์ว่าอาจเกิดจากปัจจัยอะไร (Attribution Window, Pixel Match Quality, การซื้อผ่านช่องทางอื่นที่ไม่ผ่าน Pixel)

### ภารกิจที่ 6: ทดสอบ Value-based Optimization (สำหรับธุรกิจที่มีสินค้าหลากหลายราคา)

ถ้าธุรกิจมี Product Range หลากหลายและมี Purchase Event สะสมมากพอ (100+ ต่อสัปดาห์ทั้งบัญชี) สร้าง Ad Group คู่ขนานสองตัวด้วย Budget เท่ากัน ตัวหนึ่งเปิด VBO อีกตัวปิด รันพร้อมกันอย่างน้อย 2 สัปดาห์ แล้วเปรียบเทียบ Revenue รวมและ AOV ตามตัวอย่างในหัวข้อเจาะลึกของ Step 743

### ภารกิจที่ 7: เขียนรายงานสรุปสำหรับลูกค้า/ทีมงาน

รวบรวมข้อมูลจากภารกิจที่ 1-6 เขียนรายงานสรุป 1-2 หน้ากระดาษ อธิบายว่าแคมเปญ Conversion ของธุรกิจอยู่ในขั้นไหนของการไล่ระดับ Event, ตัวเลข CPA/ROAS ปัจจุบันเทียบกับ Break-even, และแผนขั้นต่อไปที่จะทำใน 4 สัปดาห์ข้างหน้า

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้พาคุณเข้าสู่ปลายสุดของ Funnel ด้วยแคมเปญ Website Conversion บน TikTok ครอบคลุมตั้งแต่การเลือก Optimization Event ให้เหมาะกับปริมาณข้อมูลที่มี, หลัก 50 Events Rule ฉบับ TikTok, Value-based Optimization, ปริมาณ Event ที่จำเป็นสำหรับ Stable Delivery, การตั้งค่า Ad Group/Ad แบบละเอียด, แนวทางกำหนดงบประมาณ, ไปจนถึงการอ่าน Metric อย่างมืออาชีพและความรู้พื้นฐานเรื่อง App Conversion

บทเรียนสำคัญที่สุดของ Part นี้คือ **Conversion Campaign ไม่ใช่ Objective ที่ "ตั้งแล้วได้ผลทันที"** แต่ต้องอาศัยการไล่ระดับ Event อย่างมีระบบ โดยเฉพาะสำหรับบัญชีที่ยังไม่มี Pixel Data สะสม — หลักการนี้ต่อเนื่องมาจาก Section G ทั้งหมด (โดยเฉพาะ Part 066 เรื่อง Pixel/Events API) และเป็นฐานสำคัญสำหรับ Part ถัดไป

Part ถัดไป **Part 076: TikTok Shop Ads แบบเจาะลึก (GMV Max, Product Ads)** จะพาคุณเข้าสู่รูปแบบการขายที่เป็นเอกลักษณ์ของ TikTok มากที่สุด คือการขายผ่าน TikTok Shop โดยตรงในแพลตฟอร์ม ซึ่งมีระบบ Optimization และ Ad Format ที่แตกต่างจาก Website Conversion ที่เรียนใน Part นี้อย่างชัดเจน โดยเฉพาะฟีเจอร์ GMV Max ที่เป็น AI-Driven Campaign เฉพาะสำหรับ E-commerce บน TikTok Shop

ก่อนไป Part ถัดไป ควรให้แน่ใจว่าเข้าใจหลักการไล่ระดับ Event และ 50 Events Rule ให้แน่นก่อน เพราะแม้ TikTok Shop Ads จะมีระบบ Optimization ที่ดูเหมือนต่างออกไป (ผูกกับ Catalog และ GMV โดยตรง) แต่แนวคิดพื้นฐานเรื่องปริมาณข้อมูลที่ระบบต้องการเพื่อเรียนรู้ยังคงเป็นหลักการเดียวกันกับที่เรียนมาทั้ง Part นี้

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- TikTok for Business — Website Conversion Objective Documentation (ads.tiktok.com/help)
- TikTok Marketing API — Events/Pixel Documentation (business-api.tiktok.com/portal)
- TikTok for Business — Value-based Optimization Guide
- เอกสารภายในหลักสูตร: Part 026 (Facebook Conversions Campaign), Part 015 Step 146 (Value Optimization บน Facebook), Part 066 (TikTok Pixel/Events API), Part 004 Step 34 (Break-even ROAS), Part 067 Step 661 (50 Events Rule แนวคิดพื้นฐาน)
- Mobile Measurement Partner Documentation — AppsFlyer, Adjust (สำหรับ App Conversion Campaigns)
- บันทึก Benchmark CPA/ROAS ของบัญชีตัวเอง — สำคัญกว่าตัวเลข Benchmark ทั่วไปเพราะแต่ละธุรกิจมี Margin/Funnel ต่างกันมาก
- TikTok for Business — Custom Conversions Setup Guide
- เอกสารภายในหลักสูตร (ต่อ): Part 083 (Custom Audience/Lookalike TikTok), Part 086 (Scaling Strategy TikTok), Part 054–055 (Landing Page/CRO สำหรับปรับปรุง Complete Payment Rate)

### สิ่งที่ควรทำต่อทันทีหลังอ่าน Part นี้จบ

เปิด Events Manager ของบัญชีตัวเองตอนนี้เลย แล้วเช็กตัวเลข Event สะสม 30 วันที่ผ่านมาตามภารกิจที่ 1 ของ Workshop ก่อนไปอ่าน Part ถัดไป เพราะข้อมูลจริงจากบัญชีของตัวเองมีค่ามากกว่าตัวอย่างทั้งหมดใน Part นี้รวมกัน

การลงมือเช็กข้อมูลจริงทันทีจะช่วยให้เนื้อหา Part 076 ที่กำลังจะเรียนต่อไปเข้าใจง่ายขึ้นมาก เพราะจะมีภาพความพร้อมของ Pixel Data ของธุรกิจตัวเองอยู่ในหัวแล้วเป็นฐานเทียบกับสิ่งที่จะเรียนเรื่อง TikTok Shop Ads ต่อไป

ขอให้โชคดีกับการไล่ระดับ Event ของธุรกิจตัวเอง — นี่คือทักษะที่แยกนักยิงแอด TikTok มือใหม่ออกจากมือโปรได้ชัดเจนที่สุดใน Section H ทั้งหมด

พบกันใหม่ใน Part 076
