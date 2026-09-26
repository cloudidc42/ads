# Part 085: TikTok Metrics และการอ่านผลลัพธ์

**Section:** I — TikTok Targeting, Optimization & Scaling
**Step ที่ครอบคลุม:** Step 841–850 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 8–11 ชั่วโมง (รวมการฝึกอ่าน Ads Manager จริงและทำ Workshop สร้างเทมเพลตเช็กเมตริกรายวัน)
**ระดับ:** กลาง (ต้องมีพื้นฐานจาก Part 083-084 เรื่อง Audience และ Retargeting Funnel มาก่อน และควรทบทวน Part 056-057 เรื่องการอ่านตัวเลข Ads Manager ของ Facebook เพื่อเทียบหลักการ)

Part นี้เน้นการฝึกอ่านตัวเลขจริงเป็นหลัก แนะนำให้เปิด TikTok Ads Manager ควบคู่ไปกับการอ่านเนื้อหาเพื่อฝึกหาตำแหน่ง Column และทดลองปรับแต่ง Report ไปพร้อมกันทีละ Step

---

Part 083-084 สอนให้สร้าง Audience Library และ Retargeting Funnel ที่ถูกต้องแล้ว แต่ระบบที่ดีที่สุดก็ไร้ประโยชน์ถ้าไม่มีความสามารถ "อ่านตัวเลข" ว่าระบบนั้นกำลังทำงานดีหรือแย่ ตรงไหนคือปัญหาจริง ตรงไหนคือความผันผวนปกติที่ไม่ต้องแก้ นักยิงแอดจำนวนมากเปิด TikTok Ads Manager ทุกวันแต่ดูแค่ 2-3 ตัวเลขผิวเผิน (Spend, CPA, ROAS) โดยไม่รู้ว่าตัวเลขอื่นที่ TikTok มีให้ — โดยเฉพาะ Metrics เฉพาะทางด้านวิดีโอที่ Facebook ไม่มีให้ละเอียดเท่า — สามารถบอกสาเหตุของปัญหาได้ชัดเจนกว่ามาก

Part นี้จะพาไปเจาะทุก Metrics ที่ TikTok Ads Manager มีให้ ตั้งแต่ Metrics พื้นฐานที่คุ้นเคยจาก Facebook ไปจนถึง Metrics เฉพาะทางวิดีโอที่เป็นเอกลักษณ์ของ TikTok การเทียบ Benchmark ระหว่างสองแพลตฟอร์ม การปรับแต่ง Column/Report ให้ทำงานเร็วขึ้น การอ่าน Delivery Status และปิดท้ายด้วยการสร้างเทมเพลตเช็กเมตริกรายวันที่ใช้งานได้จริงในหน้างาน

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 841** — TikTok Ads Manager Metrics Glossary: CPM, CPC, CTR, Conversion Rate, Cost per Conversion
2. **Step 842** — TikTok Video Metrics เฉพาะทาง: 2-Second/6-Second Video Views, Average Watch Time, Completion Rate, Play Rate, Engagement Rate
3. **Step 843** — สิ่งที่ Video Metrics บอกเราเกี่ยวกับคุณภาพ Creative: Hook Problem vs Offer Problem
4. **Step 844** — เทียบ Benchmark ตัวเลข TikTok กับ Facebook: อะไรคือ "ปกติ" อะไรคือ "ผิดปกติ"
5. **Step 845** — การปรับแต่ง Columns และ Custom Report ใน TikTok Ads Manager
6. **Step 846** — การอ่าน Delivery Status: Active, Not Delivering, Learning, Learning Limited, Rejected
7. **Step 847** — การวินิจฉัยแคมเปญที่ทำผลลัพธ์แย่ด้วยสัญญาณเฉพาะของ TikTok
8. **Step 848** — ข้อผิดพลาดคลาสสิกในการอ่านและตีความ Metrics ของ TikTok
9. **Step 849** — การทำ Breakdown Analysis เพื่อหา Insight ที่ซ่อนอยู่ในตัวเลขรวม
10. **Step 850** — Workshop: สร้างเทมเพลตเช็กเมตริกรายวันสำหรับบัญชี TikTok Ads

---

## Step 841: TikTok Ads Manager Metrics Glossary — CPM, CPC, CTR, Conversion Rate, Cost per Conversion

### ตำแหน่งที่ดู Metrics เหล่านี้

ไปที่ **Campaign → เลือก Campaign/Ad Group/Ad → ตารางด้านล่าง** จะเห็น Column พื้นฐานที่ระบบแสดงเป็นค่าเริ่มต้น (Default Columns) ซึ่งมักมีไม่ครบทุกตัวที่ต้องการ ต้องกด **Columns → Customize Columns** เพื่อเพิ่ม Metrics ที่ต้องการดู (รายละเอียดวิธีปรับแต่งจะเรียนใน Step 845)

### ตารางคำอธิบาย Metrics พื้นฐาน

| Metric | ความหมาย | สูตรคำนวณ | หมายเหตุ |
|---|---|---|---|
| **CPM (Cost per Mille)** | ต้นทุนต่อการแสดงผล 1,000 ครั้ง | Spend ÷ Impressions × 1000 | สะท้อนความแข่งขันในการประมูลและคุณภาพ Ad Score |
| **CPC (Cost per Click)** | ต้นทุนต่อการคลิก 1 ครั้ง | Spend ÷ Clicks | มี 2 แบบย่อย: CPC (Destination) วัดคลิกที่ไปหน้าเว็บ และ CPC (All) วัดคลิกทุกประเภทรวม Like/Comment/Share ด้วย |
| **CTR (Click-Through Rate)** | อัตราการคลิกต่อการแสดงผล | Clicks ÷ Impressions × 100 | เช่นเดียวกับ CPC มี CTR (Destination) และ CTR (All) แยกกัน |
| **Conversion Rate** | อัตราการเกิด Conversion ต่อ Click/Impression | Conversions ÷ Clicks × 100 | TikTok มักแสดงเป็น "Cost per Result" คู่กับ Result Rate มากกว่าเขียนเป็น % ตรง ๆ ในบางมุมมอง |
| **Cost per Conversion (CPA)** | ต้นทุนต่อ Conversion 1 ครั้ง | Spend ÷ Conversions | ชื่อ Column อาจแสดงเป็น "Cost per Result" ขึ้นกับ Optimization Goal ที่เลือก |

### จุดที่ต้องระวัง: CPC/CTR (All) vs (Destination)

TikTok แยก CPC และ CTR เป็น 2 แบบ ซึ่งเป็นจุดที่มือใหม่สับสนบ่อยที่สุด:

- **CTR (Destination)** — วัดเฉพาะคลิกที่นำไปสู่ปลายทางที่ตั้งไว้ (เว็บไซต์/แอป) เทียบเท่า Link Click ของ Facebook
- **CTR (All)** — วัดคลิกทุกประเภทรวมถึงการคลิกที่ตัว Video, Profile, Music, Hashtag ที่ไม่ได้ไปปลายทางเลย

การดู CTR (All) เพียงอย่างเดียวโดยไม่เทียบกับ CTR (Destination) อาจทำให้เข้าใจผิดว่าโฆษณา Perform ดีทั้งที่จริง ๆ คนคลิกเข้าไปดู Profile/เพลงเยอะแต่ไม่ได้คลิกไปเว็บไซต์เลย สำหรับแคมเปญ Conversion **ต้องดู CTR (Destination) เป็นหลักเสมอ**

### ตารางเปรียบเทียบชื่อ Metrics: TikTok vs Facebook

| ความหมาย | TikTok เรียกว่า | Facebook เรียกว่า |
|---|---|---|
| คลิกที่ไปหน้าเว็บ | Clicks (Destination) | Link Clicks |
| คลิกทุกประเภทรวม Engagement | Clicks (All) | Post Engagement / All Clicks |
| ต้นทุนต่อ Conversion | Cost per Conversion / Cost per Result | Cost per Result / CPA |
| อัตราการเกิด Conversion | Conversion Rate | ไม่มี Column ตรงชื่อนี้ มักต้องคำนวณเอง |

### ข้อผิดพลาดที่พบบ่อย

1. ดู CTR (All) แทน CTR (Destination) สำหรับแคมเปญ Conversion ทำให้ตีความ Performance ผิดพลาด
2. สับสนระหว่าง Cost per Conversion กับ Cost per Result เพราะชื่อ Column เปลี่ยนไปตาม Optimization Goal ที่เลือกไว้
3. ไม่รู้ว่า CPM สูงอาจมาจาก Ad Score ต่ำ (Creative ไม่ดี) ไม่ใช่แค่จากการแข่งขันในตลาดสูงเพียงอย่างเดียว
4. เปรียบเทียบ CPC ข้าม Campaign ที่ใช้ Objective ต่างกัน (เช่น Traffic vs Conversion) โดยไม่รู้ว่าฐานการคำนวณต่างกัน

---

## Step 842: TikTok Video Metrics เฉพาะทาง — Watch Time, Completion Rate, Play Rate

### ทำไม Video Metrics สำคัญกว่าที่คิดบน TikTok

ตามหลักการที่เรียนใน Part 083 (Step 823) TikTok เป็นระบบ Content-Behavior-Based ที่กลไก Delivery ผูกกับ Video Performance โดยตรง Video Metrics จึงไม่ใช่แค่ตัวเลข "น่ารู้" แต่เป็นสัญญาณเชิงสาเหตุที่อธิบายว่าทำไม CTR/CPA ถึงเป็นแบบนั้น

### ตารางคำอธิบาย Video Metrics ทั้งหมด

| Metric | ความหมาย | สิ่งที่บอกเรา |
|---|---|---|
| **2-Second Video Views** | จำนวนคนที่ดูวิดีโอต่อเนื่อง ≥ 2 วินาที | วัด Impression ที่ผ่านการ "หยุดสไลด์" อย่างน้อยแวบแรก ใกล้เคียง Impression ที่มีคุณภาพขั้นต่ำ |
| **6-Second Video Views** | จำนวนคนที่ดูวิดีโอต่อเนื่อง ≥ 6 วินาที | สัญญาณว่า Hook ทำงาน — ผ่าน 6 วินาทีแรกได้แปลว่าคนเริ่มสนใจจริง |
| **Average Watch Time** | เวลาเฉลี่ยที่คนดูวิดีโอต่อครั้ง (หน่วยวินาที) | บอกว่าคอนเทนต์โดยรวม "ดึงดูด" คนได้นานแค่ไหนเทียบกับความยาววิดีโอทั้งหมด |
| **Completion Rate** | % ของคนที่ดูวิดีโอจบ 100% เทียบกับจำนวนคนที่เริ่มดู | สัญญาณความสมบูรณ์ของ Storytelling — จบเรื่องได้ดีแค่ไหน |
| **Play Rate** | % ของคนที่กด Play/ดูวิดีโอ เทียบกับ Impression ทั้งหมด | มักใกล้เคียง 100% เพราะ TikTok Auto-play เป็นค่าเริ่มต้น แต่ใช้เช็คปัญหาทางเทคนิค (เช่น วิดีโอโหลดไม่ขึ้น) ได้ |
| **Engagement Rate** | (Like+Comment+Share+Follow) ÷ Impressions × 100 | สัญญาณว่าคอนเทนต์ "โดนใจ" มากพอให้คนอยากมีส่วนร่วมต่อ ไม่ใช่แค่ดูเฉย ๆ |

### วิธีอ่าน Watch Time เทียบกับความยาววิดีโอ

Average Watch Time ต้องอ่านคู่กับความยาวจริงของวิดีโอเสมอ ไม่ใช่ดูตัวเลขวินาทีเดี่ยว ๆ วิธีที่ถูกต้องคือคำนวณ **% Watch Time = Average Watch Time ÷ ความยาววิดีโอ × 100**

| % Watch Time | การตีความ |
|---|---|
| ต่ำกว่า 20% | Hook อ่อนมาก คนดูไม่ถึง 1/5 ของวิดีโอ ต้องแก้ 3 วินาทีแรกก่อนอื่นใด |
| 20-40% | Hook พอใช้ได้แต่เนื้อหากลางเรื่องยังไม่ดึงดูดพอให้ดูต่อ |
| 40-60% | ดีในระดับใช้งานได้ คนดูเกินครึ่งทางของเรื่อง |
| เกิน 60% | ดีมาก คอนเทนต์ดึงดูดได้ตลอดความยาว มีโอกาสสูงที่จะได้ Conversion ดี |

### ตัวอย่างการอ่านค่าจริง

วิดีโอโฆษณาความยาว 30 วินาที มี Average Watch Time 9 วินาที (% Watch Time = 30%) และ Completion Rate 8% เทียบกับวิดีโออีกตัวความยาว 15 วินาที มี Average Watch Time 11 วินาที (% Watch Time = 73%) และ Completion Rate 45% แม้ Average Watch Time ตัวเลขดิบของวิดีโอแรกจะดูใกล้เคียงตัวที่สอง (9 vs 11 วินาที) แต่เมื่อคิดเป็น % แล้ววิดีโอที่สองมีคุณภาพการดึงดูดที่ดีกว่ามาก และมักให้ CTR/CPA ที่ดีกว่าตามไปด้วย — นี่คือเหตุผลที่ไม่ควรเทียบ Average Watch Time แบบตัวเลขดิบข้าม Creative ที่ความยาวต่างกัน

### ข้อผิดพลาดที่พบบ่อย

1. เทียบ Average Watch Time แบบตัวเลขดิบระหว่างวิดีโอที่ความยาวต่างกันโดยไม่แปลงเป็น %
2. มองข้าม 6-Second Video Views ทั้งที่เป็นสัญญาณ Hook ที่ตรงไปตรงมาที่สุดของ TikTok
3. ไม่แยกวิเคราะห์ Engagement Rate ออกจาก CTR ทั้งที่สื่อความหมายคนละมุม (Engagement Rate บอกว่าคอนเทนต์โดนใจ ส่วน CTR บอกว่าคนอยากไปดูต่อที่ปลายทาง)
4. ใช้ Completion Rate เป็นตัวชี้วัดเดียวโดยไม่ดู Watch Time ควบคู่ ทำให้พลาดรายละเอียดว่าคนหลุดออกไปตอนไหนของวิดีโอกันแน่

---

## Step 843: สิ่งที่ Video Metrics บอกเราเกี่ยวกับคุณภาพ Creative — Hook Problem vs Offer Problem

### กรอบการวินิจฉัยด้วย Video Metrics

จุดแข็งที่สุดของ Video Metrics คือช่วยแยกแยะว่าปัญหาของแคมเปญอยู่ที่ **"คอนเทนต์ไม่ดึงดูด" (Hook/Content Problem)** หรือ **"คอนเทนต์ดึงดูดดีแต่ Offer/Landing Page ไม่โน้มน้าวพอ" (Offer/Funnel Problem)** ซึ่งเป็นสองปัญหาที่แก้ด้วยวิธีต่างกันโดยสิ้นเชิง

### Diagnostic Matrix: จับคู่ Video Metrics กับ CTR/CPA

| 6-Second View Rate | Completion Rate | CTR (Destination) | การวินิจฉัย | วิธีแก้ |
|---|---|---|---|---|
| ต่ำ | ต่ำ | ต่ำ | **Hook Problem รุนแรง** — คนไม่หยุดดูตั้งแต่ต้น | เขียน Hook ใหม่ทั้งหมด ทดสอบ 3 วินาทีแรกหลายแบบ |
| สูง | สูง | ต่ำ | **Offer/CTA Problem** — คนดูจนจบแต่ไม่คลิก | ปรับ CTA ให้ชัดเจนขึ้น ทบทวน Offer ว่าน่าสนใจพอหรือไม่ |
| สูง | ต่ำ | ปานกลาง | **Middle Content Problem** — Hook ดีแต่กลางเรื่องหลุดความสนใจ | ตัดกลางเรื่องให้กระชับขึ้น หรือใส่ Pattern Interrupt ตรงกลาง |
| สูง | สูง | สูง แต่ Conversion Rate ต่ำ | **Landing Page/Funnel Problem** — Creative ทำงานดีมากแล้ว ปัญหาอยู่หลังคลิก | ตรวจ Landing Page Speed, CRO (ตามหลักการ Part 054-055 ของ Facebook ที่ใช้ได้เหมือนกัน) |

### ตัวอย่างการวินิจฉัยจริง

แคมเปญขายคอร์สออนไลน์มี 6-Second View Rate 65% (สูง) Completion Rate 38% (ปานกลาง-สูง) แต่ CTR (Destination) เพียง 0.6% (ต่ำกว่าค่าเฉลี่ยอุตสาหกรรมมาก) ตามกรอบ Diagnostic Matrix นี่คือสัญญาณ Offer/CTA Problem ไม่ใช่ Hook Problem ทีมจึงไม่แก้ 3 วินาทีแรกของวิดีโอ (ซึ่งทำงานดีอยู่แล้ว) แต่ไปแก้ CTA ท้ายวิดีโอที่เดิมพูดกำกวมว่า "สนใจดูรายละเอียดเพิ่มเติม" เปลี่ยนเป็น "กดลิงก์ด้านล่างรับส่วนลด 30% วันนี้เท่านั้น" ผล CTR เพิ่มขึ้นเป็น 1.8% โดยไม่ต้องเปลี่ยนวิดีโอเลย ยืนยันว่าการวินิจฉัยที่ถูกจุดช่วยประหยัดเวลาผลิต Creative ใหม่ทั้งตัวโดยไม่จำเป็น

### ข้อผิดพลาดที่พบบ่อย

1. เห็น CTR ต่ำแล้วรีบตัดสินใจถ่ายวิดีโอใหม่ทั้งหมดทันที โดยไม่เช็ค Video Metrics ก่อนว่าปัญหาจริงอยู่ที่ Hook หรือ CTA
2. แก้ Hook ใหม่ทั้งที่ 6-Second View Rate สูงอยู่แล้ว (Hook ทำงานดี) ทำให้เสียเวลาแก้จุดที่ไม่ใช่ปัญหา
3. ไม่เชื่อมโยง Video Metrics กับ Conversion Rate หลังคลิก ทำให้พลาดสัญญาณว่าปัญหาอาจอยู่ที่ Landing Page ไม่ใช่ตัวโฆษณาเลย
4. วินิจฉัยจาก Sample Size เล็กเกินไป (Impression ต่ำกว่า 1,000) ที่ตัวเลข Video Metrics ยังไม่นิ่งพอให้เชื่อถือได้

---

## Step 844: เทียบ Benchmark ตัวเลข TikTok กับ Facebook — อะไรคือ "ปกติ" อะไรคือ "ผิดปกติ"

### คำเตือนก่อนใช้ Benchmark

Benchmark เป็นแค่ "จุดอ้างอิงกว้าง ๆ" ไม่ใช่เกณฑ์ตายตัวที่ใช้ได้กับทุกอุตสาหกรรม/ทุก Objective ตัวเลขจริงต้องดูเทียบกับ Performance History ของบัญชีตัวเองเป็นหลัก แต่ Benchmark ยังมีประโยชน์ในการเช็คว่าตัวเลขที่เห็นอยู่ "อยู่ในช่วงที่สมเหตุสมผล" หรือ "ผิดปกติจนต้องสงสัยว่ามีปัญหาทางเทคนิค"

### ตารางเปรียบเทียบ Benchmark กว้าง ๆ (อีคอมเมิร์ซ/สินค้าอุปโภคบริโภค ตลาดไทย)

| Metric | TikTok (ช่วงที่พบบ่อย) | Facebook (ช่วงที่พบบ่อย) |
|---|---|---|
| CTR (Destination) | 0.8% – 2.0% | 0.9% – 1.8% |
| CPM | 30 – 90 บาท | 60 – 150 บาท |
| Conversion Rate (จาก Click) | 2% – 6% | 3% – 8% |
| CPA (สินค้าราคา 500-1,500 บาท) | 100 – 300 บาท | 150 – 350 บาท |

*(ตัวเลขเหล่านี้เป็นช่วงกว้างสำหรับใช้อ้างอิงเบื้องต้นเท่านั้น ควรตรวจสอบ Benchmark ล่าสุดจาก TikTok/Meta หรือเทียบกับ Performance History ของบัญชีตัวเองเสมอ เพราะเปลี่ยนแปลงตามฤดูกาล อุตสาหกรรม และสภาวะตลาดที่ผันผวนอยู่เสมอ)*

### ตารางเสริม: Benchmark คร่าว ๆ แยกตามประเภทธุรกิจ (TikTok)

| ประเภทธุรกิจ | CTR (Destination) ที่พบบ่อย | Cost per Result ที่พบบ่อย |
|---|---|---|
| E-commerce (สินค้าราคาต่ำกว่า 1,000 บาท) | 1.0% – 2.5% | 80 – 200 บาทต่อ Purchase |
| Lead Generation (B2C ทั่วไป) | 1.5% – 3.5% | 50 – 150 บาทต่อ Lead |
| Lead Generation (B2B/Ticket Size สูง) | 0.5% – 1.5% | 300 – 1,000+ บาทต่อ Lead |
| App Install | 1.5% – 4.0% | 15 – 60 บาทต่อ Install |
| TikTok Shop (In-app Conversion) | 2.0% – 5.0% | ต่ำกว่า Website Conversion เพราะ Friction น้อยกว่า |

ตัวเลขเหล่านี้ยิ่งต้องระมัดระวังในการใช้อ้างอิงมากกว่าตารางก่อนหน้า เพราะความหลากหลายภายในแต่ละหมวดธุรกิจสูงมาก (เช่น B2B Ticket Size สูงมีช่วง Cost per Lead ที่กว้างมากตามมูลค่าสินค้า/บริการจริง) ควรใช้เป็นจุดเริ่มต้นตั้งเป้าหมายเบื้องต้นเท่านั้น แล้วปรับตาม Performance History ของบัญชีจริงภายใน 4-6 สัปดาห์แรก

### ทำไม TikTok CPM มักถูกกว่า Facebook

เหตุผลหลักคือ Inventory (พื้นที่โฆษณา) ของ TikTok ยังมีการแข่งขันน้อยกว่า Facebook ในหลายอุตสาหกรรม เพราะจำนวน Advertiser ที่ยิงบน TikTok ยังน้อยกว่า Facebook มาก แม้ผู้ใช้จะมีจำนวนมากก็ตาม ทำให้ต้นทุนการประมูลต่อการแสดงผลถูกกว่าตามธรรมชาติของ Auction ที่มีผู้แข่งขันน้อยกว่า อย่างไรก็ตาม CPM ที่ถูกกว่าไม่ได้แปลว่า CPA จะถูกกว่าเสมอ เพราะ Conversion Rate ของ TikTok ในบางอุตสาหกรรมยังต่ำกว่า Facebook (ผู้ใช้ TikTok มักอยู่ในโหมด Entertainment มากกว่า Purchase Intent เทียบกับ Facebook ในบางบริบท)

### สัญญาณที่บอกว่าตัวเลขผิดปกติ (ไม่ใช่แค่ต่างจาก Benchmark)

1. **CTR หรือ CVR เปลี่ยนแปลงฉับพลันเกิน 50% ในวันเดียวโดยไม่มีการเปลี่ยน Creative/Targeting** — มักเป็นสัญญาณปัญหาทางเทคนิค (Pixel หลุด, Landing Page ล่ม) มากกว่าปัญหา Creative
2. **CPM พุ่งสูงกว่าปกติ 3-4 เท่าในชั่วข้ามคืน** — ตรวจสอบว่ามี Ad Set/Ad Group อื่นในบัญชีที่ Targeting ทับซ้อนกันเพิ่งเริ่มรันหรือไม่ (Overlap ตามที่เรียนใน Part 083 Step 829)
3. **6-Second View Rate ต่ำกว่า 10%** — ต่ำผิดปกติเมื่อเทียบกับ TikTok ทั่วไปที่มักอยู่ระดับ 20-40%+ สำหรับ Creative ที่ทำงานได้ดี อาจเป็นสัญญาณว่า Creative แย่มากหรือ Targeting ผิดกลุ่มโดยสิ้นเชิง

### ข้อผิดพลาดที่พบบ่อย

1. เทียบ Benchmark ข้ามอุตสาหกรรมที่ไม่เกี่ยวข้องกัน (เช่น เทียบ CPA ของธุรกิจ B2B Ticket Size สูงกับ Benchmark อีคอมเมิร์ซ)
2. เชื่อว่า CPM ถูกกว่า = ธุรกิจจะได้ ROAS ดีกว่าเสมอ โดยไม่พิจารณา Conversion Rate ที่อาจต่ำกว่าชดเชยกัน
3. ตกใจกับตัวเลขที่ต่างจาก Benchmark กว้าง ๆ โดยไม่เทียบกับ Performance History ของบัญชีตัวเองก่อน
4. ไม่แยกแยะระหว่าง "ตัวเลขต่างจาก Benchmark" กับ "ตัวเลขผิดปกติที่บ่งบอกปัญหาทางเทคนิคจริง"
5. ใช้ Benchmark จากบทความ/คอร์สเก่าที่อาจล้าสมัยไปแล้วหลายปี โดยไม่ตรวจสอบว่าตัวเลขยังสมเหตุสมผลกับสภาวะตลาดปัจจุบันหรือไม่

---

## Step 845: การปรับแต่ง Columns และ Custom Report ใน TikTok Ads Manager

### วิธีปรับแต่ง Columns แบบ Step-by-Step

1. ที่หน้าตาราง Campaign/Ad Group/Ad คลิกปุ่ม **Columns** (มุมขวาบนของตาราง)
2. เลือก **Customize Columns**
3. เลือกหมวด Metrics ที่ต้องการ (Performance, Video Engagement, Engagement, Conversion) แล้วติ๊กเลือก Metrics ที่ต้องการแสดง
4. จัดเรียงลำดับ Column ตามความสำคัญที่ใช้งานบ่อย
5. บันทึกเป็น **Custom Column Preset** ตั้งชื่อให้จำง่าย (เช่น "Daily Check - Video Metrics", "Daily Check - Conversion")

### Preset ที่แนะนำสำหรับงานประจำวัน

**Preset 1 — Overview Check (เช็คภาพรวมทุกเช้า):** Spend, Impressions, CPM, CTR (Destination), Conversions, Cost per Conversion, ROAS

**Preset 2 — Video Quality Check (เช็คคุณภาพ Creative):** 6-Second Video Views, Average Watch Time, Completion Rate, Engagement Rate, CTR (Destination)

**Preset 3 — Delivery Health Check (เช็คสถานะการวิ่ง):** Delivery Status, Frequency, Impressions, Spend, Learning Phase Status

### การสร้าง Custom Report แบบ Export

สำหรับการรายงานลูกค้าหรือทีม ไปที่ **Reporting → Create Report** เลือก Dimension (Campaign/Ad Group/Ad/Day/Age/Gender/Placement) และ Metrics ที่ต้องการ ตั้งค่า Schedule ให้ส่งรายงานอัตโนมัติทาง Email เป็นรายวัน/รายสัปดาห์ได้ ลดงานที่ต้อง Manual Export ทุกครั้ง

### เปรียบเทียบความสามารถ Custom Report: TikTok vs Facebook

| ความสามารถ | TikTok Ads Manager | Facebook Ads Manager |
|---|---|---|
| บันทึก Column Preset | รองรับ | รองรับ (Report ที่บันทึกไว้) |
| Scheduled Email Report | รองรับ | รองรับ |
| Breakdown by Age/Gender/Placement | รองรับ | รองรับ (ละเอียดกว่าเล็กน้อย เช่น Breakdown by Device/Platform) |
| Export เป็น CSV/Excel | รองรับ | รองรับ |

### ข้อผิดพลาดที่พบบ่อย

1. ใช้ Default Columns ตลอดโดยไม่ปรับแต่งเลย ทำให้มองไม่เห็น Video Metrics ที่สำคัญที่ซ่อนอยู่ในหมวดอื่น
2. สร้าง Preset ที่มี Column มากเกินไปจนตารางกว้างเทอะทะ อ่านยากในหน้างานจริง ควรมี 6-10 Column ต่อ Preset ก็เพียงพอ
3. ไม่บันทึก Preset ทำให้ต้องเลือก Column ใหม่ทุกครั้งที่เปิดบัญชี เสียเวลาสะสมในระยะยาว
4. ไม่ตั้ง Scheduled Report สำหรับลูกค้า/ทีม ทำให้ต้อง Export มือทุกสัปดาห์ทั้งที่ระบบทำอัตโนมัติได้

---

## Step 846: การอ่าน Delivery Status — Active, Not Delivering, Learning, Learning Limited, Rejected

### ตำแหน่งที่ดู Delivery Status

อยู่ที่ Column แรกสุดของตาราง Campaign/Ad Group/Ad เป็น Column ที่ TikTok แสดงเป็นค่า Default เสมอ (ไม่ต้องเพิ่มเอง) ต่างจาก Facebook ที่บางครั้งต้องคลิกเข้าไปดูรายละเอียดใน Ad Set Diagnostics ถึงจะเห็นสถานะแบบเดียวกัน

### ตารางความหมายของแต่ละ Delivery Status

| Status | ความหมาย | สิ่งที่ต้องทำ |
|---|---|---|
| **Active** | กำลังวิ่งปกติ | ไม่ต้องทำอะไร ติดตามผลตามรอบปกติ |
| **Not Delivering** | ไม่ได้แสดงผลเลย | ตรวจสอบ Budget/Bid ว่าต่ำเกินไปหรือไม่, ตรวจ Targeting ว่าแคบเกินไปหรือไม่, ตรวจสถานะ Ad Review |
| **Learning** | อยู่ในช่วงเรียนรู้ ระบบยังหา Pattern การส่ง Ad ที่ดีที่สุด | ให้เวลาระบบเรียนรู้ ไม่ควรแก้ไข Ad Group บ่อยในช่วงนี้ |
| **Learning Limited** | ระบบเรียนรู้ได้จำกัดเพราะ Conversion Volume ไม่พอ | เพิ่ม Budget, ขยาย Targeting, หรือเปลี่ยน Optimization Goal ให้ Event ที่เกิดถี่ขึ้น (เช่นจาก Purchase เป็น AddToCart ชั่วคราว) |
| **Rejected** | โฆษณาถูกปฏิเสธจากการ Review | ตรวจ Policy ที่ละเมิด (เรียนใน Part 071) แก้ไข Creative/Copy แล้วส่งใหม่ |
| **Under Review** | อยู่ในระหว่างตรวจสอบก่อนอนุมัติ | รอผล มักใช้เวลาไม่กี่ชั่วโมงถึง 1 วัน |

### สถานะเพิ่มเติมที่อาจพบในบางบัญชี

นอกจาก 6 สถานะหลักข้างต้น บางบัญชีอาจเห็นสถานะย่อยเพิ่มเติมเช่น **Inactive** (Ad Group ถูกปิดโดยผู้ใช้เอง ไม่ได้เกิดจากปัญหาระบบ) และ **Campaign Budget Exceeded** (งบระดับ Campaign หมดแล้วในวันนั้น ทำให้ Ad Group ภายในหยุดแสดงผลชั่วคราวจนกว่าจะถึงวันถัดไปหรือมีการเพิ่มงบ) การแยกแยะสถานะเหล่านี้ออกจาก Not Delivering ช่วยประหยัดเวลาในการวินิจฉัยปัญหาที่ไม่มีอยู่จริง

### จุดแข็งของ TikTok ในการแสดง Learning Limited

ตามที่เคยกล่าวถึงใน Part 069 TikTok มักแสดงสถานะ Learning Limited ให้เห็นชัดเจนกว่า Facebook ในหน้าตารางหลักโดยตรง ไม่ต้องคลิกเข้าไปดูรายละเอียดเพิ่ม ทำให้ Troubleshoot ได้เร็วกว่าในหลายกรณี นักยิงแอดที่มาจากฝั่ง Facebook ที่ไม่คุ้นกับการเช็ค Diagnostics บ่อย ๆ ควรใช้ประโยชน์จากจุดแข็งนี้ของ TikTok โดยตรวจ Column Delivery Status เป็นกิจวัตรทุกวัน

### ตัวอย่างการวินิจฉัยจากสถานะ

Ad Group หนึ่งแสดง Learning Limited ต่อเนื่อง 10 วันโดยไม่เปลี่ยนสถานะ ทีมตรวจสอบพบว่า Optimization Goal ตั้งเป็น Purchase แต่ Conversion Volume เฉลี่ยเพียง 3-4 ครั้งต่อสัปดาห์ (ต่ำกว่าเกณฑ์ที่ระบบต้องการเพื่อเรียนรู้ได้ดี) แก้ไขโดยเปลี่ยน Optimization Goal เป็น InitiateCheckout ชั่วคราว (Event ที่เกิดถี่กว่า Purchase ประมาณ 3-4 เท่า) ทำให้ Ad Group ผ่านพ้น Learning Limited ภายใน 5 วัน แล้วค่อยพิจารณาเปลี่ยนกลับเป็น Purchase เมื่อ Volume สะสมมากพอในภายหลัง

### ข้อผิดพลาดที่พบบ่อย

1. ไม่เช็ค Delivery Status เป็นกิจวัตร มารู้ว่า Ad Group ไม่วิ่งมาหลายวันแล้วก็ตอนที่เสียโอกาสไปมากแล้ว
2. แก้ไข Ad Group บ่อยเกินไปในช่วง Learning ทำให้ Learning Phase Reset ซ้ำ ๆ ไม่จบสักที
3. เห็น Not Delivering แล้วรีบเพิ่ม Budget ทันทีโดยไม่ตรวจสาเหตุจริงก่อน (อาจเป็นเพราะ Ad ถูก Reject ไม่ใช่ Budget ต่ำ)
4. ไม่รู้ความต่างระหว่าง Learning กับ Learning Limited ทำให้ตอบสนองผิดวิธี (Learning ควรรอเฉย ๆ แต่ Learning Limited ต้องเข้าไปแก้ไขเชิงรุก)
5. สับสนสถานะ Inactive (ที่ตัวเองสั่งปิดไว้) กับ Not Delivering (ที่ระบบหยุดให้เอง) ทำให้เสียเวลาหาสาเหตุที่ไม่มีอยู่จริง

---

## Step 847: การวินิจฉัยแคมเปญที่ทำผลลัพธ์แย่ด้วยสัญญาณเฉพาะของ TikTok

### กรอบการวินิจฉัยแบบเป็นระบบ (Diagnostic Flowchart)

```
CPA สูงกว่าเป้า?
 ├─ ตรวจ Delivery Status ก่อน
 │    ├─ Learning Limited → เพิ่ม Budget/ขยาย Targeting/เปลี่ยน Optimization Goal ชั่วคราว
 │    └─ Active ปกติ → ไปขั้นต่อไป
 ├─ ตรวจ Video Metrics (6-Second View Rate, Completion Rate)
 │    ├─ ต่ำทั้งคู่ → Hook/Creative Problem → แก้ Creative
 │    └─ สูงทั้งคู่ → ไปขั้นต่อไป
 ├─ ตรวจ CTR (Destination)
 │    ├─ ต่ำ (แม้ Video Metrics ดี) → Offer/CTA Problem → แก้ CTA/Offer
 │    └─ สูง → ไปขั้นต่อไป
 ├─ ตรวจ Conversion Rate หลังคลิก
 │    ├─ ต่ำ → Landing Page/Funnel Problem → ตรวจ Page Speed/CRO
 │    └─ ปกติแต่ CPA ยังสูง → ตรวจ Targeting/Audience Overlap หรือ Frequency สูงเกิน
```

### สัญญาณเฉพาะของ TikTok ที่ควรเช็คเพิ่มจาก Facebook

1. **Music/Sound ที่ใช้ถูก Copyright Claim หรือถูกจำกัดการมองเห็น** — ปัญหานี้ไม่มีบน Facebook แต่เกิดได้บน TikTok ถ้าใช้เพลงที่ไม่มีสิทธิ์เชิงพาณิชย์ (ตามที่เรียนใน Part 081) ตรวจสอบผ่าน Creative Center ว่า Sound ที่ใช้ยังมีสถานะปกติหรือถูกจำกัดแล้ว
2. **Spark Ads ที่ Authorization Code หมดอายุกลางทาง** — ทำให้ Ad หยุดวิ่งโดยไม่มี Error ชัดเจนในบางกรณี ต้องเช็คสถานะ Authorization ควบคู่กับ Delivery Status
3. **Trend ที่ใช้ใน Creative หมดความนิยมเร็ว** — Video Metrics ที่เคยดีอาจตกลงเร็วกว่าที่คาดเพราะ Sound/Format หมดเทรนด์ ไม่ใช่เพราะ Ad Fatigue ในความหมายทั่วไป
4. **Comment เชิงลบสะสมจำนวนมาก** — TikTok ผู้ใช้มักแสดงความเห็นตรงไปตรงมามากกว่า Facebook Comment เชิงลบจำนวนมากอาจกระทบ CTR ของคนที่เข้ามาดู Comment ก่อนคลิก (พฤติกรรมที่พบบ่อยบน TikTok มากกว่า Facebook)

### ตัวอย่างการวินิจฉัยที่ใช้สัญญาณเฉพาะ TikTok

แคมเปญหนึ่งมี Video Metrics ดีต่อเนื่อง 2 สัปดาห์แล้วอยู่ ๆ 6-Second View Rate ตกลงจาก 35% เหลือ 12% ในวันเดียวโดยไม่ได้เปลี่ยน Creative ทีมตรวจสอบ Creative Center พบว่า Sound ที่ใช้ในวิดีโอถูกระบบ TikTok จำกัดการแสดงผลเนื่องจากมีการร้องเรียนเรื่อง Copyright แม้ Video ตัวเดิมจะยังรันได้ แต่ระบบลดการกระจายให้เพราะ Sound มีปัญหา หลังเปลี่ยนเป็น Sound ที่ปลอดภัยเชิงพาณิชย์ (Commercial Music Library ของ TikTok เอง) 6-Second View Rate กลับมาที่ 33% ภายใน 2 วัน

### ข้อผิดพลาดที่พบบ่อย

1. ใช้กรอบ Diagnostic แบบ Facebook ล้วน ๆ โดยไม่เพิ่มการเช็คสัญญาณเฉพาะของ TikTok (Music Copyright, Authorization Code, Trend Decay)
2. เจอปัญหา Video Metrics ตกแล้วรีบสรุปว่า Ad Fatigue โดยไม่ตรวจสอบสาเหตุอื่นที่เป็นไปได้ก่อน
3. ไม่อ่าน Comment ของ Ad จริง ทั้งที่เป็นแหล่งข้อมูลเชิงคุณภาพที่ช่วยเข้าใจว่าทำไมคนไม่คลิก (เช่น มีคนถามคำถามซ้ำ ๆ ที่ Creative ไม่ได้ตอบ)
4. วินิจฉัยจากวันเดียวโดยไม่ดู Trend ต่อเนื่อง 3-7 วัน ทำให้ตัดสินใจเปลี่ยนแปลงเร็วเกินไปจากความผันผวนปกติรายวัน

---

## Step 848: ข้อผิดพลาดคลาสสิกในการอ่านและตีความ Metrics ของ TikTok

### สรุปข้อผิดพลาดการตีความที่พบบ่อยที่สุด

1. **สับสน CTR (All) กับ CTR (Destination)** — ทำให้เข้าใจผิดว่า Performance ดีทั้งที่คนคลิกแค่ดู Profile/Sound
2. **เทียบ Average Watch Time แบบตัวเลขดิบข้าม Creative ที่ความยาวต่างกัน** — ต้องแปลงเป็น % Watch Time เสมอ
3. **ตกใจกับ CPM ที่สูงกว่า Facebook โดยไม่รู้ว่าเป็นเรื่องปกติในบางอุตสาหกรรม/บาง Placement**
4. **มองว่า Conversion Rate ต่ำ = Targeting ผิด ทั้งที่บางครั้งเป็น Landing Page Problem** — ต้องแยกวินิจฉัยตาม Diagnostic Matrix ใน Step 843
5. **ไม่แยกวิเคราะห์ Metrics ตามชั้น Funnel** — ใช้เกณฑ์ Benchmark เดียวกันเทียบ TOF กับ BOF ทั้งที่ธรรมชาติของตัวเลขต่างกันมาก (TOF ควรดู Video Metrics เป็นหลัก, BOF ควรดู CPA/ROAS เป็นหลัก)
6. **ตัดสินใจจาก Sample Size เล็กเกินไป** — เปลี่ยน Creative/Targeting ทั้งที่ Impression ยังไม่ถึงหลักพันครั้ง ตัวเลขยังไม่นิ่งพอเชื่อถือได้
7. **ไม่ตรวจ Delivery Status ก่อนตีความ Metrics อื่น** — วินิจฉัยปัญหา Creative ทั้งที่ตัวจริงคือ Ad ยังไม่ผ่าน Review หรือ Learning Limited อยู่
8. **มองข้าม Engagement Rate เพราะไม่ใช่ Metrics ที่ผูกกับ Conversion โดยตรง** — ทั้งที่เป็นสัญญาณ Leading Indicator ที่ช่วยทำนายว่า Creative จะทำงานดีในระยะยาวหรือไม่

### ตารางสรุปวิธีป้องกันแต่ละข้อผิดพลาด

| ข้อผิดพลาด | วิธีป้องกัน |
|---|---|
| สับสน CTR (All)/(Destination) | ตั้ง Preset ที่แสดง CTR (Destination) เป็นค่าหลักเสมอสำหรับแคมเปญ Conversion |
| เทียบ Watch Time ดิบ | คำนวณ % Watch Time ทุกครั้งก่อนเทียบข้าม Creative |
| ตกใจ CPM สูง | เทียบกับ Performance History ของบัญชีเอง ไม่ใช่แค่ Benchmark ภาพกว้าง |
| เข้าใจผิด CVR ต่ำ = Targeting ผิด | ใช้ Diagnostic Matrix จาก Step 843 ก่อนสรุป |
| ไม่แยก Metrics ตาม Funnel | ตั้ง Column Preset แยกสำหรับ TOF/MOF/BOF |
| Sample Size เล็ก | รอ Impression อย่างน้อย 1,000-2,000 ก่อนตัดสินใจเปลี่ยนแปลงใหญ่ |
| ไม่ตรวจ Delivery Status ก่อน | ทำ Delivery Status เป็นขั้นแรกของ Diagnostic Flowchart เสมอ |
| มองข้าม Engagement Rate | เพิ่ม Engagement Rate ใน Preset "Video Quality Check" |

---

## Step 849: การทำ Breakdown Analysis เพื่อหา Insight ที่ซ่อนอยู่ในตัวเลขรวม

### ทำไมตัวเลขรวมอาจซ่อน Insight สำคัญไว้

Ad Group ที่แสดง CPA เฉลี่ย "พอใช้ได้" ในภาพรวม อาจซ่อนความจริงว่ามี Segment หนึ่งที่ CPA ดีมาก และอีก Segment ที่ CPA แย่มาก มาถัวเฉลี่ยกันจนดูเหมือนปกติ การทำ Breakdown Analysis คือการแยกดูตัวเลขตามมิติต่าง ๆ เพื่อหา Segment ที่ซ่อนอยู่เหล่านี้

### มิติ Breakdown ที่ TikTok Ads Manager รองรับ

| มิติ | ประโยชน์ |
|---|---|
| **Age/Gender** | หา Segment ที่ CPA ดี/แย่ตามกลุ่มประชากร ปรับ Targeting ให้เน้นกลุ่มที่ดี |
| **Placement** | เทียบ Performance ระหว่าง In-Feed, TopView, Pangle (Audience Network ของ TikTok) |
| **Device** | เทียบ iOS vs Android ที่บางครั้งมี Conversion Rate ต่างกันมาก (เช่น จาก Checkout Flow ที่ไม่ Responsive ดีบนบางระบบ) |
| **Day/Hour** | หาช่วงเวลาที่ Performance ดีที่สุดสำหรับ Dayparting (หลักการเดียวกับ Ad Scheduling ของ Facebook Part 018) |
| **Creative (Ad Level)** | เทียบ Creative แต่ละตัวในกลุ่มเดียวกันเพื่อหาตัวที่ควร Scale เพิ่ม |

### ตัวอย่างการทำ Breakdown Analysis จริง

Ad Group หนึ่งแสดง CPA เฉลี่ย 220 บาท ซึ่งทีมมองว่า "พอรับได้" แต่หลังทำ Breakdown by Age พบว่า:

| Age Group | CPA | สัดส่วน Spend |
|---|---|---|
| 18-24 | 340 บาท | 25% |
| 25-34 | 165 บาท | 45% |
| 35-44 | 195 บาท | 20% |
| 45+ | 410 บาท | 10% |

ตัวเลขเผยว่ากลุ่ม 25-34 คือ Segment ที่ทำ CPA ดีที่สุดจริง ๆ ในขณะที่กลุ่ม 18-24 และ 45+ ฉุด CPA เฉลี่ยรวมให้สูงขึ้น ทีมปรับ Age Targeting ให้เน้น 25-34 และ 35-44 มากขึ้น (ลด/ตัดกลุ่ม 18-24 และ 45+ ออก) ผล CPA เฉลี่ยรวมของ Ad Group ลดลงเหลือ 175 บาทภายใน 1 สัปดาห์ โดยไม่ต้องเปลี่ยน Creative หรือ Offer เลย

### ข้อผิดพลาดที่พบบ่อย

1. ดูแค่ตัวเลขรวมโดยไม่เคยทำ Breakdown เลย ทำให้พลาด Insight ที่จะช่วยลด CPA ได้ทันที
2. ทำ Breakdown แล้วตัดสินใจจาก Sample Size เล็กเกินไปในแต่ละ Segment (เช่น Segment ที่มี Conversion แค่ 2-3 ครั้ง ยังไม่นิ่งพอสรุป)
3. ทำ Breakdown by Placement แล้วตัด Placement ที่ CPA สูงออกทันทีโดยไม่พิจารณาว่า Placement นั้นอาจทำหน้าที่ TOF (Awareness) มากกว่า Conversion โดยธรรมชาติ
4. ไม่ทำ Breakdown Analysis เป็นประจำ ทำครั้งเดียวตอนเริ่มแคมเปญแล้วไม่กลับมาเช็คซ้ำทั้งที่ Segment ที่ดีอาจเปลี่ยนไปตามเวลา
5. ไม่บันทึกผล Breakdown Analysis ไว้เป็นประวัติ ทำให้ไม่สามารถเทียบว่า Segment ที่ดีในเดือนนี้ยังคงดีเหมือนเดือนก่อนหรือไม่
6. ใช้ Breakdown by Device โดยไม่รู้ว่าความต่างระหว่าง iOS/Android อาจมาจาก Checkout Flow ของเว็บไซต์ ไม่ใช่จาก TikTok Ads เอง

---

## Step 850: Workshop — สร้างเทมเพลตเช็กเมตริกรายวันสำหรับบัญชี TikTok Ads

### เป้าหมายของ Workshop นี้

สร้างเทมเพลต (Google Sheet หรือ Checklist ที่ใช้งานได้จริง) สำหรับเช็ก TikTok Ads Manager ทุกเช้าอย่างเป็นระบบ ไม่ใช่เปิดดูแบบสุ่มไม่มีโครงสร้าง

### ขั้นตอนที่ 1 — สร้าง Column Preset ทั้ง 3 ชุดตาม Step 845

สร้าง Preset "Overview Check", "Video Quality Check", "Delivery Health Check" จริงในบัญชี TikTok Ads Manager ของตัวเองหรือบัญชี Sandbox

### ขั้นตอนที่ 2 — ออกแบบ Checklist ลำดับการเช็กทุกเช้า

เขียนลำดับขั้นตอนที่ต้องทำทุกเช้าเป็นข้อ ๆ เช่น:

1. เช็ค Delivery Status ของทุก Ad Group ก่อนอื่นใด — มี Not Delivering หรือ Learning Limited ตัวไหนไหม
2. เช็ค Spend เทียบ Budget ที่ตั้งไว้ — มี Ad Group ที่ Spend เกิน/ต่ำกว่าคาดผิดปกติไหม
3. เช็ค CPA/ROAS ของแต่ละ Ad Group เทียบเป้าหมาย
4. ถ้า CPA ผิดปกติ ใช้ Diagnostic Flowchart จาก Step 847 หาสาเหตุ
5. เช็ค Video Metrics (6-Second View Rate, Completion Rate) ของ Ad ใหม่ที่เพิ่งเปิดไม่เกิน 3 วัน
6. เช็ค Frequency ของ Ad Group Retargeting ทุกตัวว่าเกินเกณฑ์ที่ตั้งไว้หรือไม่ (ตาม Part 084 Step 835)
7. บันทึกตัวเลขสำคัญลง Log ประจำวันเพื่อเทียบ Trend ย้อนหลัง

### ขั้นตอนที่ 3 — สร้าง Log Sheet บันทึกตัวเลขรายวัน

ออกแบบตารางบันทึกที่มี Column: วันที่, Campaign/Ad Group, Spend, CPM, CTR (Destination), Conversion Rate, CPA, 6-Second View Rate, Completion Rate, Delivery Status, บันทึกข้อสังเกต

### ขั้นตอนที่ 4 — กำหนดเกณฑ์ Alert ที่ต้องรีบดำเนินการ

เขียนเกณฑ์ตัวเลขที่ถ้าถึงจุดนี้ต้องรีบเข้าไปแก้ไขทันที ไม่ต้องรอถึงรอบเช็กถัดไป เช่น "CPA สูงกว่าเป้า 50% ติดต่อกัน 2 วัน" หรือ "Frequency ของ Ad Group Retargeting เกิน 8 ภายในสัปดาห์เดียว"

### ขั้นตอนที่ 5 — ทำ Breakdown Analysis รายสัปดาห์

กำหนดวันคงที่ในสัปดาห์ (เช่น ทุกวันจันทร์) สำหรับทำ Breakdown by Age/Gender/Placement/Device ของทุก Ad Group ที่ใช้งบสูง เพื่อหา Insight ที่ตัวเลขรวมรายวันอาจซ่อนไว้

### Case Study อ้างอิงสำหรับ Workshop นี้

เอเจนซี่ขนาดเล็กที่ดูแลลูกค้า 6 บัญชี TikTok Ads พร้อมกัน เดิมทีทีมงานเปิดดูแต่ละบัญชีแบบสุ่มไม่มีโครงสร้าง ทำให้เคยพลาดสัญญาณ Learning Limited ของบัญชีลูกค้ารายหนึ่งไปนานถึง 6 วันโดยไม่รู้ตัว หลังสร้างเทมเพลตเช็กเมตริกรายวันตาม Workshop นี้และบังคับให้ทีมทำตามลำดับขั้นตอนทุกเช้า ปัญหา Delivery Status ผิดปกติถูกจับได้ภายในวันเดียวเสมอ และค่าเฉลี่ย CPA ของทั้ง 6 บัญชีลดลง 18% ภายใน 2 เดือน เพราะการตอบสนองต่อปัญหาเร็วขึ้นมากจากเดิม

---

## เทคนิคขั้นสูง: Attribution Window และผลกระทบต่อการอ่าน Conversion Metrics

### Attribution Window คืออะไร ทำไมกระทบตัวเลขที่เห็น

Attribution Window คือระยะเวลาที่ระบบยอมรับว่า Conversion หนึ่งครั้ง "เกิดจาก" การเห็น/คลิกโฆษณาตัวใดตัวหนึ่ง TikTok เปิดให้ตั้งค่าได้ทั้ง **Click-through Attribution** (นับ Conversion ที่เกิดหลังคลิก ภายในกรอบเวลาที่กำหนด) และ **View-through Attribution** (นับ Conversion ที่เกิดหลังเห็นโฆษณาแต่ไม่ได้คลิก ภายในกรอบเวลาที่กำหนด)

### ตารางตัวเลือก Attribution Window ที่ TikTok เปิดให้ใช้

| ประเภท | ตัวเลือก Window ที่พบบ่อย | ผลต่อตัวเลข Conversion ที่รายงาน |
|---|---|---|
| Click-through | 1 วัน, 7 วัน, 28 วัน | Window ยาวขึ้น = จับ Conversion ได้มากขึ้น (แต่ Conversion นั้นอาจมาจากปัจจัยอื่นด้วยไม่ใช่แค่โฆษณา) |
| View-through | 1 วัน | นับคนที่เห็นโฆษณาแล้วซื้อในเวลาไม่นานโดยไม่ได้คลิกเลย — ทำให้ตัวเลข Conversion สูงกว่าความเป็นจริงเชิงสาเหตุถ้าตั้งค่าไม่เหมาะสม |

### ผลกระทบต่อการเปรียบเทียบ Performance ข้าม Ad Group/Campaign

ถ้า Ad Group สองตัวตั้ง Attribution Window ต่างกัน (เช่นตัวหนึ่งใช้ Default 7-day Click/1-day View อีกตัวถูกปรับเป็น 1-day Click เท่านั้น) การเทียบ CPA ระหว่างสองตัวจะไม่ Fair เพราะฐานการนับ Conversion ต่างกัน ก่อนเทียบ Performance ข้าม Ad Group ควรตรวจสอบว่าทุกตัวใช้ Attribution Window เดียวกันเสมอ

### ความสัมพันธ์กับ View-through Conversion และการตีความ ROAS ที่สูงเกินจริง

Ad Group ที่มี Reach กว้างมาก (เช่น TOF Campaign) มักมี View-through Conversion ปนอยู่ในตัวเลขค่อนข้างมาก เพราะคนจำนวนมากเห็นโฆษณาผ่านตาแล้วบังเอิญไปซื้อสินค้าด้วยเหตุผลอื่นในเวลาใกล้เคียงกัน (ไม่ได้เกี่ยวกับโฆษณาจริง) การดู ROAS ของ TOF Campaign ที่รวม View-through Conversion เข้าไปด้วยอาจทำให้เข้าใจผิดว่า TOF สร้าง Conversion ได้ดีกว่าความเป็นจริง แนวทางที่แนะนำคือแยกดู Click-through Conversion อย่างเดียวเป็นตัวเลขหลักสำหรับประเมิน Performance เชิงสาเหตุ และดู View-through Conversion เป็นข้อมูลเสริมเท่านั้น

### ตัวอย่างการอ่านตัวเลขที่ระมัดระวังเรื่อง Attribution

Campaign TOF หนึ่งแสดง Conversion รวม 85 ครั้งในสัปดาห์หนึ่ง แยกได้เป็น Click-through 22 ครั้ง และ View-through 63 ครั้ง ถ้าดูตัวเลขรวม CPA จะดูดีมาก (ต่ำ) แต่ถ้าคำนวณ CPA จาก Click-through อย่างเดียว (ซึ่งเป็นตัวเลขที่เชื่อถือได้เชิงสาเหตุมากกว่า) CPA จะสูงกว่าตัวเลขรวมถึง 3-4 เท่า ทีมที่ไม่ระมัดระวังเรื่องนี้อาจตัดสินใจ Scale Campaign TOF นี้เร็วเกินไปโดยเข้าใจผิดว่า Performance ดีกว่าที่ควรจะเป็นจริง

### ข้อผิดพลาดที่พบบ่อยเรื่อง Attribution

1. ไม่รู้ว่า Ad Group ต่างกันอาจตั้ง Attribution Window ต่างกัน ทำให้เทียบ Performance ข้าม Ad Group แบบไม่ Fair
2. ดู Conversion รวม (Click+View) เป็นตัวเลขหลักตลอดโดยไม่แยกดู Click-through อย่างเดียวเพื่อประเมินเชิงสาเหตุ
3. Scale Campaign ที่มี View-through Conversion สูงเร็วเกินไปโดยเข้าใจผิดว่า Performance ดีกว่าความเป็นจริง
4. ไม่ตรวจสอบ Attribution Window Setting ก่อนเริ่มแคมเปญใหม่ ปล่อยใช้ค่า Default โดยไม่รู้ว่ามีทางเลือกอื่นที่อาจเหมาะกับธุรกิจมากกว่า
5. เปลี่ยน Attribution Window กลางทางของแคมเปญที่กำลังรันอยู่โดยไม่บันทึกวันที่เปลี่ยน ทำให้เทียบ Performance ก่อน-หลังผิดพลาดในภายหลัง
6. ไม่ระบุ Attribution Window ที่ใช้ไว้ในเอกสาร Test Log หรือ Report ทำให้ทีมอื่นที่มาดูข้อมูลย้อนหลังตีความผลผิดพลาดโดยไม่รู้ตัว

---

## Case Study สรุปท้าย Part: แบรนด์รองเท้าผ้าใบใช้ Video Metrics แก้ปัญหา CPA สูงที่เข้าใจผิดมาตลอด

แบรนด์รองเท้าผ้าใบสัญชาติไทยยิง TikTok Ads มา 4 เดือนด้วย CPA เฉลี่ย 340 บาทต่อออเดอร์ ซึ่งสูงกว่าเป้าที่ตั้งไว้ (250 บาท) ทีมงานเชื่อมาตลอดว่าปัญหาคือ Targeting ผิดกลุ่ม จึงทดสอบเปลี่ยน Interest/Behavior มาแล้วกว่า 15 ชุดโดยไม่ได้ผลดีขึ้นชัดเจน

หลังนำกรอบ Diagnostic Matrix จาก Step 843 มาใช้ ทีมพบว่า Video Metrics ของ Creative ที่ใช้อยู่มี 6-Second View Rate สูงถึง 42% และ Completion Rate 28% (ทั้งคู่ดีกว่า Benchmark ทั่วไป) แต่ CTR (Destination) ต่ำเพียง 0.5% ตามกรอบ Diagnostic Matrix นี่คือสัญญาณ Offer/CTA Problem ไม่ใช่ Creative หรือ Targeting Problem ทีมตรวจ CTA ในวิดีโอพบว่าพูดกำกวมว่า "ลองดูสิรับรองไม่ผิดหวัง" โดยไม่มี Offer ที่จับต้องได้เลย

หลังเปลี่ยน CTA เป็น "กดลิงก์รับส่วนลด 15% เฉพาะ 3 วันนี้" โดยไม่แก้ Creative ตัวอื่นเลย ผลลัพธ์:

| ตัวชี้วัด | ก่อนแก้ CTA | หลังแก้ CTA |
|---|---|---|
| 6-Second View Rate | 42% | 41% (ไม่เปลี่ยนแปลงมาก เพราะเป็นส่วนต้นวิดีโอ) |
| CTR (Destination) | 0.5% | 1.9% |
| CPA | 340 บาท | 178 บาท |

บทเรียนสำคัญคือทีมงานเสียเวลากว่า 4 เดือนไปกับการทดสอบ Targeting ที่ไม่ใช่ปัญหาจริง เพราะไม่เคยใช้ Video Metrics มาช่วยวินิจฉัยแยกแยะระหว่าง Hook Problem กับ Offer Problem หากใช้กรอบ Diagnostic Matrix ตั้งแต่เดือนแรก จะประหยัดเวลาและงบประมาณที่เสียไปกับการทดสอบผิดจุดได้มาก

ทีมงานยังสะท้อนในภายหลังว่าสิ่งที่ทำให้พลาดประเด็นนี้มานานคือความเคยชินจากการยิง Facebook ที่ไม่มี Video Metrics ละเอียดขนาดนี้ให้ดู ทำให้ไม่ได้สร้างวินัยในการเปิดดู Video Metrics เป็นกิจวัตร เมื่อย้ายมายิง TikTok จึงใช้กรอบการวินิจฉัยแบบเดิมที่เคยใช้กับ Facebook (เดาว่าปัญหาน่าจะมาจาก Targeting เพราะเป็นตัวแปรที่คุ้นเคยที่สุด) ทั้งที่ TikTok มีเครื่องมือวินิจฉัยที่ดีกว่าให้ใช้อยู่แล้วในมือตลอดเวลา

---

## FAQ ที่พบบ่อยเกี่ยวกับ TikTok Metrics และการอ่านผลลัพธ์

**Q0: ควรเริ่มเช็ค Metrics ตัวไหนก่อนเป็นอันดับแรกสุดถ้ามีเวลาจำกัดมากในตอนเช้า**

ถ้ามีเวลาน้อยมาก (ต่ำกว่า 5 นาที) ให้เช็ค Delivery Status ก่อนเสมอ เพราะเป็นสัญญาณที่บอกว่า "แคมเปญกำลังทำงานหรือไม่" ซึ่งสำคัญกว่าการรู้ว่า "ทำงานดีแค่ไหน" ถ้าแคมเปญหยุดวิ่งไปแล้ว 2-3 วันโดยไม่รู้ตัว ความเสียหายจะรุนแรงกว่าการไม่ได้ปรับปรุง Performance ที่ยังพอวิ่งอยู่

**Q1: ควรดู Metrics ที่ระดับ Campaign, Ad Group หรือ Ad เป็นหลัก**

ควรดูทั้ง 3 ระดับแต่เพื่อจุดประสงค์ต่างกัน ระดับ Campaign ใช้เช็คภาพรวมงบและ ROAS รวม ระดับ Ad Group ใช้เช็ค Targeting/Audience และ Delivery Status ระดับ Ad ใช้เช็ค Video Metrics และเปรียบเทียบ Creative แต่ละตัว การวินิจฉัยปัญหาที่แม่นยำต้องลงไปถึงระดับ Ad เสมอ เพราะ Ad Group ที่ดูปกติในภาพรวมอาจมี Creative บางตัวที่ฉุดค่าเฉลี่ยลงอยู่

**Q2: ตัวเลข Video Metrics ควรดูตอนไหนถึงจะ "นิ่ง" พอเชื่อถือได้**

แนะนำรอ Impression อย่างน้อย 1,000-2,000 ครั้งต่อ Ad ก่อนตัดสินใจอะไรจาก Video Metrics เพราะ Sample เล็กเกินไปทำให้ตัวเลข % ผันผวนสูง (เช่น Completion Rate จาก 10 คนดูจบ 2 คน จะแสดง 20% ซึ่งไม่มีความหมายทางสถิติเท่าไหร่)

**Q3: ทำไม Engagement Rate ของ Ad บางตัวสูงมากแต่ CPA ยังแย่**

Engagement Rate สูงบอกว่าคอนเทนต์ "โดนใจ" ในเชิง Entertainment แต่ไม่ได้แปลว่าคนที่กด Like/Comment/Share เหล่านั้นคือกลุ่มที่มี Purchase Intent เสมอ บางครั้งคอนเทนต์ Viral เพราะ Entertainment Value สูงแต่ดึงคนที่ไม่ใช่กลุ่มเป้าหมายจริงเข้ามาปนจำนวนมาก ควรดู Engagement Rate ควบคู่กับ CTR (Destination) และ Conversion Rate เสมอ ไม่ใช่มองแยกโดดๆ

**Q4: ควรตั้ง Custom Conversion หรือใช้ Standard Event ในการวัดผลหลัก**

ใช้ Standard Event เป็นหลักเสมอถ้าตรงกับ Action ของธุรกิจอยู่แล้ว (Purchase, Lead, CompleteRegistration) เพราะ TikTok Optimize ให้ Standard Event ได้แม่นยำกว่า Custom Event ที่นิยามขึ้นเอง ใช้ Custom Event เฉพาะเมื่อ Action ของธุรกิจไม่ตรงกับ Standard Event ใดเลยจริง ๆ ตามหลักการที่เรียนใน Part 066 Step 653

**Q5: Report ที่ส่งให้ลูกค้าควรมี Metrics อะไรบ้างเป็นอย่างน้อย**

อย่างน้อยควรมี Spend, Impressions, CTR (Destination), Conversions, Cost per Conversion, ROAS (ถ้าเป็นอีคอมเมิร์ซ) พร้อม Breakdown by Campaign/Ad Group ระดับ Video Metrics (6-Second View Rate, Completion Rate) ควรใส่เพิ่มถ้าลูกค้าสนใจด้าน Creative Performance ด้วย ไม่ใช่แค่ตัวเลข Conversion เพียงอย่างเดียว เพราะช่วยให้ลูกค้าเข้าใจว่าทำไม Creative ตัวไหนถึงถูกเลือก Scale ต่อหรือถูกปิด

**Q6: ควรใช้ Click-through Conversion หรือ Conversion รวม (Click+View) เป็นตัวเลขหลักในการรายงานผล**

สำหรับการวิเคราะห์เชิงกลยุทธ์ภายในทีม (ตัดสินใจว่าจะ Scale/ปิด Ad Group ไหน) ควรใช้ Click-through Conversion เป็นหลักเพราะเชื่อถือได้เชิงสาเหตุมากกว่าตามที่อธิบายในหัวข้อ Attribution Window แต่สำหรับการรายงานให้ลูกค้าเห็นภาพรวม อาจแสดงทั้งสองตัวเลขคู่กันพร้อมอธิบายความหมายที่ต่างกัน เพื่อไม่ให้ลูกค้าเข้าใจผิดว่า TOF Campaign สร้าง Conversion ได้เยอะกว่าความเป็นจริง

**Q7: ทำไมตัวเลข Conversion ใน TikTok Ads Manager กับตัวเลขใน GA4 ไม่ตรงกัน ควรเชื่อตัวไหน**

ความไม่ตรงกันเป็นเรื่องปกติและเกิดกับทุกแพลตฟอร์มโฆษณา (รวมถึง Facebook) เพราะแต่ละระบบใช้ Attribution Model และ Tracking Method ต่างกัน (TikTok อิง Pixel/Events API ของตัวเอง ส่วน GA4 อิง Session-based Tracking ของ Google) หลักการที่แนะนำคือใช้ตัวเลขของ TikTok Ads Manager เพื่อ**ตัดสินใจเชิง Optimization ภายในแพลตฟอร์ม** (เช่น เปรียบเทียบ Ad Group ไหนดีกว่ากัน) และใช้ GA4 เพื่อดู**ภาพรวมความจริงของธุรกิจข้ามทุกช่องทาง** (Facebook+TikTok+Organic+Direct) ไม่ควรพยายามบังคับให้ตัวเลขทั้งสองระบบตรงกัน 100% เพราะเป็นไปไม่ได้ในทางเทคนิค รายละเอียดเรื่องนี้จะเรียนลึกขึ้นใน Part 089 (UTM Tracking และ GA4 Integration)

## เทคนิคขั้นสูง: ปิดวงจร Metrics กลับไปสู่ทีม Creative (Data-to-Creative Feedback Loop)

### ทำไมทีม Media Buying และทีม Creative มักทำงานแยกกันจนเสียโอกาส

ปัญหาที่พบบ่อยในองค์กรขนาดกลาง-ใหญ่คือทีม Media Buying อ่าน Metrics ได้ดีแต่ไม่ได้ส่งต่อ Insight ให้ทีม Creative ที่ผลิตวิดีโอ ทำให้ทีม Creative ผลิตคอนเทนต์ต่อไปโดยไม่รู้ว่า Pattern แบบไหนที่ Video Metrics บอกว่าใช้ได้ผลจริง กลายเป็นการผลิตคอนเทนต์แบบเดาสุ่มซ้ำ ๆ ทั้งที่มีข้อมูลอยู่ในมือแล้ว

### โครงสร้าง Feedback Loop ที่ใช้ได้จริง

1. **สรุป Video Metrics เป็นภาษาที่ทีม Creative เข้าใจง่าย** — แปลงตัวเลขให้เป็นข้อสรุปเชิงปฏิบัติ เช่น ไม่พูดว่า "6-Second View Rate 38%" แต่พูดว่า "Hook แบบเปิดด้วยคำถามตรงกล้องทำงานดีกว่า Hook แบบเริ่มด้วยภาพสินค้าเฉย ๆ ถึง 2 เท่า"
2. **ทำ Creative Performance Ranking รายเดือน** — จัดอันดับ Creative ทั้งหมดที่ทดสอบในเดือนนั้นตาม Video Metrics และ CPA พร้อมสรุป Pattern ร่วมของ Creative ที่ติดอันดับต้น (Hook Style, ความยาว, ประเภทครีเอเตอร์, Sound ที่ใช้)
3. **ประชุม Creative Review ร่วมกันทุก 2 สัปดาห์** — ให้ทีม Media Buying นำ Insight มาคุยกับทีม Creative โดยตรง ไม่ใช่ส่งเป็นเอกสารอย่างเดียวที่อาจไม่มีใครอ่าน
4. **สร้าง "Creative Brief Checklist" ที่อัปเดตตาม Insight ล่าสุด** — เช่น ถ้าข้อมูลบอกว่า Hook แบบถามคำถามตรงกล้องได้ผลดีต่อเนื่อง 3 เดือน ให้เพิ่มเป็นข้อบังคับใน Brief ทุกครั้งที่สั่งงาน Creative ใหม่

### ตัวอย่างการปิดวงจรที่ได้ผลจริง

แบรนด์เครื่องใช้ไฟฟ้าขนาดเล็กสร้าง Creative Performance Ranking รายเดือนต่อเนื่อง 4 เดือน พบ Pattern ชัดเจนว่า Creative ที่ใช้ครีเอเตอร์พูดตรงกล้องแบบ "รีวิวจริงไม่มีสคริปต์" มี 6-Second View Rate เฉลี่ยสูงกว่า Creative ที่ถ่ายแบบมีการจัดแสง/ตัดต่อสวยงามถึง 60% ทั้งที่ทีม Creative เดิมเชื่อว่าคอนเทนต์ที่ Production Value สูงกว่าน่าจะได้ผลดีกว่า หลังปรับ Creative Brief ให้เน้นสไตล์ "รีวิวจริงไม่มีสคริปต์" เป็นหลักตามข้อมูล ค่าเฉลี่ย CPA ของบัญชีลดลง 25% ภายในไตรมาสถัดมา เพราะทีม Creative ผลิตคอนเทนต์ที่ตรงกับ Pattern ที่พิสูจน์แล้วว่าได้ผล แทนที่จะเดาจากสัญชาตญาณ Production อย่างเดียว

### ข้อผิดพลาดที่พบบ่อยเรื่อง Feedback Loop

1. ทีม Media Buying เก็บ Insight ไว้กับตัวเองโดยไม่ส่งต่อให้ทีม Creative อย่างเป็นระบบ
2. ส่ง Insight เป็นตัวเลขดิบที่ทีม Creative ไม่เข้าใจความหมายเชิงปฏิบัติ ทำให้ไม่ถูกนำไปใช้จริง
3. ทำ Creative Review ไม่สม่ำเสมอ (นาน ๆ ครั้งเมื่อมีเวลา) ทำให้ Insight ล่าช้าเกินกว่าจะทันใช้กับ Creative ที่กำลังผลิตอยู่
4. ไม่มี Creative Brief Checklist ที่เป็นเอกสารกลาง ทำให้ Insight ที่ดีสูญหายไปเมื่อคนในทีมเปลี่ยน หรือถูกลืมเมื่อเวลาผ่านไป

## Checklist ท้ายบท

- [ ] เข้าใจความต่างระหว่าง CTR/CPC (All) กับ (Destination) และใช้ (Destination) เป็นหลักสำหรับแคมเปญ Conversion
- [ ] รู้จัก Video Metrics ทั้ง 6 ตัว (2s/6s Views, Watch Time, Completion Rate, Play Rate, Engagement Rate) และความหมายของแต่ละตัว
- [ ] แปลง Average Watch Time เป็น % Watch Time ก่อนเทียบข้าม Creative ที่ความยาวต่างกัน
- [ ] ใช้ Diagnostic Matrix แยกแยะ Hook Problem กับ Offer Problem ก่อนตัดสินใจแก้ Creative หรือ CTA
- [ ] เทียบ Benchmark กับ Performance History ของบัญชีตัวเอง ไม่ใช่แค่ Benchmark ภาพกว้างของอุตสาหกรรม
- [ ] สร้าง Column Preset อย่างน้อย 3 ชุด (Overview, Video Quality, Delivery Health) ในบัญชี TikTok Ads Manager
- [ ] เช็ค Delivery Status เป็นขั้นแรกก่อนวินิจฉัยปัญหาอื่นเสมอ
- [ ] รู้จักสัญญาณเฉพาะของ TikTok (Music Copyright, Authorization Code, Trend Decay) ที่ Facebook ไม่มี
- [ ] ทำ Breakdown Analysis อย่างน้อยรายสัปดาห์เพื่อหา Insight ที่ซ่อนอยู่ในตัวเลขรวม
- [ ] มีเทมเพลตเช็กเมตริกรายวันที่ใช้งานได้จริง พร้อมเกณฑ์ Alert ที่ชัดเจน
- [ ] เข้าใจ Attribution Window (Click-through vs View-through) และใช้ Click-through Conversion เป็นหลักในการประเมิน Performance เชิงสาเหตุ
- [ ] มีระบบส่งต่อ Insight จาก Video Metrics ให้ทีม Creative อย่างสม่ำเสมอ ไม่เก็บไว้กับทีม Media Buying ฝ่ายเดียว
- [ ] แยกแยะสถานะ Inactive/Campaign Budget Exceeded ออกจาก Not Delivering ก่อนเริ่มวินิจฉัยปัญหา

## Workshop / แบบฝึกหัด

ทำตาม Step 850 อย่างละเอียดกับบัญชี TikTok Ads Manager ของตัวเองหรือของลูกค้า โดยส่งมอบผลงาน 4 ชิ้นตามนี้:

1. **Column Preset 3 ชุดจริงในบัญชี TikTok Ads Manager** (Overview Check, Video Quality Check, Delivery Health Check) พร้อม Screenshot
2. **เอกสาร Checklist ลำดับขั้นตอนเช็กเมตริกทุกเช้า** เป็นข้อ ๆ ที่ทีมงานใช้ตามได้จริง
3. **Log Sheet บันทึกตัวเลขรายวัน** ย้อนหลังอย่างน้อย 5-7 วัน พร้อมข้อสังเกตที่พบ
4. **รายงาน Breakdown Analysis 1 ชุด** ที่พบ Insight ซ่อนอยู่ในตัวเลขรวม พร้อมข้อเสนอปรับปรุงที่นำไปใช้จริงได้

**เกณฑ์ประเมินความพร้อมของเทมเพลต (Self-Scoring Rubric)** ให้คะแนน 0-2 ต่อหัวข้อ (รวมเต็ม 20):

| หัวข้อประเมิน | คะแนน |
|---|---|
| Column Preset ครบ 3 ชุดและมี Metrics ที่เหมาะสมกับจุดประสงค์ของแต่ละชุด | /2 |
| Checklist มีลำดับขั้นตอนชัดเจนที่ตรวจ Delivery Status เป็นอันดับแรก | /2 |
| Log Sheet มี Column ครบตามที่กำหนดและบันทึกต่อเนื่องได้จริง | /2 |
| มีเกณฑ์ Alert ที่ระบุตัวเลขชัดเจน ไม่ใช่แค่ "ถ้าแย่ผิดปกติ" | /2 |
| Breakdown Analysis ใช้มิติที่เหมาะสมกับคำถามที่ต้องการตอบ | /2 |
| พบ Insight จริงจาก Breakdown ที่ไม่เห็นในตัวเลขรวม | /2 |
| มีข้อเสนอปรับปรุงที่นำไปปฏิบัติได้จริงจาก Insight ที่พบ | /2 |
| เทมเพลตใช้งานได้จริงในเวลาไม่เกิน 15-20 นาทีต่อวัน ไม่ซับซ้อนเกินไปจนไม่มีใครทำตามต่อเนื่อง | /2 |
| มีแผนทบทวนและปรับปรุงเทมเพลตเป็นระยะ (เช่น ทุกไตรมาส) | /2 |
| เทมเพลตครอบคลุมทั้ง Metrics พื้นฐานและ Video Metrics เฉพาะทางของ TikTok | /2 |

หากคะแนนรวมต่ำกว่า 14/20 ควรกลับไปปรับปรุงเทมเพลตให้ใช้งานได้จริงและครบถ้วนกว่านี้ก่อนนำไปใช้ประจำวัน

โบนัส: ถ้าดูแลบัญชีที่มีทีม Creative แยกจากทีม Media Buying ให้ทดลองสร้าง Creative Performance Ranking รายเดือนตามหลักการใน "เทคนิคขั้นสูง: ปิดวงจร Metrics กลับไปสู่ทีม Creative" แล้วนำไปพูดคุยกับทีม Creative จริง บันทึกว่า Pattern อะไรที่ทีม Creative ยังไม่เคยรู้มาก่อน และปรับ Creative Brief Checklist ตามข้อมูลที่พบ

โบนัสขั้นสูง: เปิด Attribution Setting ของ Ad Group ที่ใช้งบสูงที่สุดในบัญชี ตรวจสอบว่าใช้ Window แบบไหนอยู่ (Click-through/View-through กี่วัน) แล้วคำนวณ CPA แยกเฉพาะ Click-through Conversion เทียบกับ CPA ที่รวม View-through เพื่อดูว่าตัวเลขต่างกันมากน้อยแค่ไหนสำหรับบัญชีของตัวเอง

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ปิดท้ายด้วยทักษะการอ่านและตีความ Metrics ของ TikTok Ads Manager อย่างครบทุกมิติ ตั้งแต่ Metrics พื้นฐานที่คุ้นเคยจาก Facebook ไปจนถึง Video Metrics เฉพาะทางที่เป็นเอกลักษณ์ของ TikTok การเทียบ Benchmark ระหว่างสองแพลตฟอร์มอย่างมีวิจารณญาณ การปรับแต่ง Column/Report ให้ทำงานเร็วขึ้น การอ่าน Delivery Status ที่ TikTok แสดงชัดเจนกว่า Facebook ในหลายกรณี กรอบ Diagnostic Matrix ที่แยกแยะ Hook Problem จาก Offer Problem ได้อย่างแม่นยำ และการทำ Breakdown Analysis เพื่อหา Insight ที่ตัวเลขรวมซ่อนไว้

ทักษะการอ่านตัวเลขที่เรียนใน Part นี้คือกุญแจสำคัญที่เชื่อมทุก Part ของ Section I เข้าด้วยกัน — Audience Library ที่สร้างใน Part 083, Retargeting Funnel ที่วางไว้ใน Part 084 จะถูกปรับปรุงและพัฒนาต่อได้ก็ด้วยความสามารถในการอ่านผลลัพธ์อย่างแม่นยำที่เรียนในที่นี้

ข้อคิดสำคัญที่ควรติดตัวไปคือ ตัวเลขใน Ads Manager ไม่ใช่แค่ "รายงานผล" แต่เป็น "เครื่องมือวินิจฉัย" ที่บอกทิศทางการแก้ไขได้ชัดเจน ถ้ารู้จักอ่านให้ถูกจุด นักยิงแอดที่ใช้เวลา 15-20 นาทีต่อวันเช็ค Metrics อย่างเป็นระบบตามเทมเพลตที่สร้างขึ้นใน Workshop นี้ จะประหยัดเวลาและงบประมาณที่เคยเสียไปกับการเดาสุ่มแก้ปัญหาผิดจุดได้มากกว่าที่คิด และที่สำคัญไม่น้อยกว่ากันคือการปิดวงจรข้อมูลกลับไปสู่ทีม Creative อย่างสม่ำเสมอ เพราะข้อมูลที่ดีที่สุดก็ไม่มีประโยชน์ถ้าไม่ถูกนำไปใช้ปรับปรุงงานจริงในรอบต่อไป

Part ถัดไป (Part 086) จะพาไปเจาะลึก **TikTok Scaling Strategy** ซึ่งนำทักษะการอ่าน Metrics ที่เรียนใน Part นี้ไปใช้ตัดสินใจว่าแคมเปญไหนพร้อม Scale แคมเปญไหนควรปรับปรุงก่อน และวิธี Scale งบประมาณอย่างปลอดภัยโดยไม่ทำลาย Performance ที่พิสูจน์แล้วว่าดี

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- TikTok for Business Help Center: หมวด "Metrics Glossary" และ "About Video Metrics"
- TikTok for Business: "Delivery Status Guide" (เอกสารอธิบายสถานะ Delivery ทั้งหมดของ TikTok)
- TikTok for Business Help Center: หมวด "Attribution Settings" และ "Click-through vs View-through Attribution"
- TikTok Marketing API Documentation: Reporting Endpoint (สำหรับทีมพัฒนาที่ต้องดึง Metrics ผ่าน API สำหรับ Custom Dashboard)
- Part 043-044 ของหลักสูตรนี้ — A/B Testing Creative และ Creative Testing Framework ของ Facebook (หลักการเดียวกันที่ใช้เชื่อมกับ Data-to-Creative Feedback Loop)
- Part 056-057 ของหลักสูตรนี้ — อ่านตัวเลข Ads Manager และ CPM/CPC/CTR/ROAS ของ Facebook (ใช้เทียบหลักการ)
- Part 069 ของหลักสูตรนี้ — TikTok Budget, Bidding, Optimization Goal (พื้นฐานเรื่อง Learning Limited ที่ขยายความใน Step 846)
- Part 081 ของหลักสูตรนี้ — TikTok Creative Center (สำหรับตรวจสอบสถานะ Sound/Copyright ที่เกี่ยวกับ Step 847)
- Part 083-084 ของหลักสูตรนี้ — TikTok Audience Targeting และ Retargeting Funnel (ระบบที่ Metrics ใน Part นี้ใช้วัดผล)
- Part 089 ของหลักสูตรนี้ (Section J) — UTM Tracking และ GA4 Integration (ขยายความเรื่องความไม่ตรงกันของตัวเลขข้ามแพลตฟอร์มจาก FAQ Q7)
- Part 086 ของหลักสูตรนี้ (Section I) — TikTok Scaling Strategy (นำทักษะการอ่าน Metrics ไปใช้ต่อ)
