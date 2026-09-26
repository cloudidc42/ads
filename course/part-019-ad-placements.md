# Part 019: Ad Placements และ Automatic vs Manual Placements

**Section:** B — Facebook Ads Ecosystem Fundamentals (Part 009–020, Step 81–200)
**Step ที่ครอบคลุม:** 181–190 (จาก 1000 Steps ทั้งหมด)
**เวลาเรียนโดยประมาณ:** 4–5 ชั่วโมง (อ่าน+ทำความเข้าใจ 2.5 ชม. / ฝึกตั้งค่าและอ่าน Breakdown จริงใน Ads Manager 1.5–2.5 ชม.)

หลายคนตั้ง Objective ถูก ตั้งงบถูก แต่ยังได้ผลลัพธ์แย่ เพราะละเลยตัวแปรสำคัญอีกตัวคือ **Placement** — ตำแหน่งที่โฆษณาไปแสดงผลจริง Facebook และ Instagram ไม่ได้มีแค่ "Feed" อย่างที่คนทั่วไปนึกถึง แต่มีมากกว่า 15 ตำแหน่งย่อยกระจายอยู่ในระบบ Meta Family of Apps ทั้งหมด แต่ละตำแหน่งมีพฤติกรรมผู้ใช้ต่างกัน มี Aspect Ratio ที่ต้องการต่างกัน และมี CPM/CTR เฉลี่ยต่างกันมาก

ความเข้าใจผิดที่พบบ่อยที่สุดคือ "เปิด Automatic Placements แล้วปล่อยให้ระบบจัดการทุกอย่างได้เสมอ" — ในหลายกรณีนี่คือทางเลือกที่ดีที่สุดจริง แต่ในบางสถานการณ์การเลือก Manual Placement อย่างมีเหตุผลกลับให้ผลลัพธ์ที่ดีกว่ามาก Part นี้จะสอนให้คุณแยกแยะได้ว่าเมื่อไหร่ควรปล่อยให้ AI ทำงาน และเมื่อไหร่ต้องลงมือควบคุมเอง

---

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 181 — Placement ทั้งหมดของ Facebook/Instagram** สำรวจทุกตำแหน่งที่โฆษณาสามารถไปแสดงผลได้ในระบบ Meta
2. **Step 182 — Automatic Placements ทำงานอย่างไรและควรใช้เมื่อไหร่** เข้าใจกลไก Advantage+ Placements และข้อดีของการปล่อยให้ AI จัดการ
3. **Step 183 — Manual Placements และเมื่อไหร่ควรเลือกเอง** สถานการณ์ที่การควบคุมเองให้ผลลัพธ์ดีกว่า
4. **Step 184 — Feed vs Stories vs Reels: ความแตกต่างด้าน Creative** ทำความเข้าใจพฤติกรรมผู้ใช้และข้อกำหนดครีเอทีฟของแต่ละรูปแบบ
5. **Step 185 — Audience Network และ In-stream Video** Placement ที่อยู่นอก Facebook/Instagram แต่ยังอยู่ในเครือข่าย Meta
6. **Step 186 — Messenger Placements** การใช้ Messenger เป็นตำแหน่งแสดงผลโฆษณา
7. **Step 187 — Placement Asset Customization สำหรับแต่ละตำแหน่ง** เทคนิคใส่ครีเอทีฟต่างกันในแต่ละ Placement จากโฆษณาตัวเดียว
8. **Step 188 — Breakdown by Placement ในการอ่านผลลัพธ์** วิธีวิเคราะห์ว่า Placement ไหนทำงานดี/แย่จากรายงานจริง
9. **Step 189 — Placement ที่เหมาะกับแต่ละ Objective** จับคู่ Placement กับ Objective ให้ตรงจุด
10. **Step 190 — Workshop: ทดสอบ Placement Performance** ฝึกออกแบบการทดสอบ Placement แบบวัดผลได้จริง

---

## Step 181: Placement ทั้งหมดของ Facebook/Instagram

### ภาพรวม Placement ในระบบ Meta

Placement คือ "ตำแหน่งที่โฆษณาปรากฏ" ซึ่งกระจายอยู่ใน 4 แพลตฟอร์มหลักภายใต้ Meta Family of Apps คือ Facebook, Instagram, Messenger และ Audience Network โดยแต่ละแพลตฟอร์มมี Placement ย่อยดังนี้:

**Facebook:**
- Feed (หน้าฟีดหลัก มือถือและเดสก์ท็อป)
- Stories (แนวตั้ง หายไปใน 24 ชม.)
- Reels (วิดีโอสั้นแนวตั้ง)
- In-stream Videos (โฆษณาคั่นระหว่างวิดีโอที่มีคนอื่นทำ)
- Right Column (แถบด้านขวาบนเดสก์ท็อปเท่านั้น)
- Video Feeds
- Marketplace
- Search Results
- Business Explore / Facebook Reels Ads (บางตลาดทดสอบเพิ่ม)

**Instagram:**
- Feed
- Stories
- Reels
- Explore
- Explore Home
- Profile Feed

**Messenger:**
- Inbox (หน้ารายการแชท)
- Stories
- Sponsored Messages (ส่งข้อความตรงถึงคนที่เคยแชทกับเพจ)

**Audience Network:**
- Native, Banner, and Interstitial (โฆษณาในแอปอื่นๆนอกเครือ Meta)
- Rewarded Video (โฆษณาที่ผู้ใช้ดูเพื่อรับของในแอป/เกม)
- In-stream Video

### ทำไมต้องรู้ครบทุกตำแหน่ง แม้จะไม่ได้ใช้ทั้งหมด

หลายคนไม่รู้ด้วยซ้ำว่าโฆษณาของตัวเองไปแสดงที่ Marketplace หรือ Right Column เพราะเลือก Automatic Placements แล้วไม่เคยเช็ก Breakdown ผลที่ตามมาคือใช้ครีเอทีฟตัวเดียวที่ออกแบบมาสำหรับ Feed ไปแสดงในทุกตำแหน่ง ทำให้บาง Placement ที่มีสัดส่วนภาพไม่ตรงกัน (เช่น Right Column ที่เป็นภาพสี่เหลี่ยมเล็กบนเดสก์ท็อป) แสดงผลได้แย่มากเพราะภาพถูกครอบตัดผิดจุด

### ตารางสรุป Placement ทั้งหมดพร้อมลักษณะเด่น

| Placement | แพลตฟอร์ม | ลักษณะพฤติกรรมผู้ใช้ | ความเหมาะสมทั่วไป |
|---|---|---|---|
| Feed | FB, IG | เลื่อนดูเรื่อยๆ (Scroll) เจตนาเสพคอนเทนต์นาน | เหมาะกับทุก Objective โดยเฉพาะที่ต้องการอ่านข้อความ/ดูภาพนิ่ง |
| Stories | FB, IG, Messenger | ดูเร็ว แนวตั้งเต็มจอ กดข้ามง่ายถ้าไม่น่าสนใจใน 1-2 วิ | ต้องการ Hook แรงมากในวินาทีแรก |
| Reels | FB, IG | เสพ Entertainment สั้น คาดหวังความ Native ไม่เหมือนโฆษณา | เหมาะกับ UGC/วิดีโอที่ดูเป็นธรรมชาติ ไม่เหมือนแอดทั่วไป |
| In-stream Video | FB, Audience Network | ถูกบังคับดูคั่นวิดีโอ (Skippable หลัง 5 วิ) | เหมาะกับ Awareness/Video Views มากกว่า Direct Response |
| Right Column | FB (Desktop) | เห็นแบบ Passive ไม่ได้ตั้งใจมอง | CPM ถูกที่สุด แต่ CTR ต่ำมาก เหมาะกับ Awareness งบจำกัด |
| Marketplace | FB | กำลังหาซื้อของมือสอง/สินค้าเฉพาะ | เหมาะกับธุรกิจขายสินค้าที่แข่งกับตลาดมือสองได้ |
| Search Results | FB | กำลังค้นหาเชิงรุก (Active Intent) | เหมาะกับ Traffic/Sales ที่มี Keyword ตรงกับสิ่งที่ค้นหา |
| Explore/Explore Home | IG | เสพ Content ที่ระบบแนะนำ ไม่ใช่คนที่ Follow อยู่แล้ว | เหมาะกับ Cold Prospecting หา Audience ใหม่ |
| Audience Network | นอกเครือ Meta | อยู่ในแอป/เกมอื่น ความตั้งใจดูโฆษณาต่ำสุด | CPM ถูกมาก แต่คุณภาพ Traffic ควรตรวจสอบเป็นพิเศษ |
| Messenger Inbox | Messenger | กำลังเช็คแชท มีสมาธิสูงกว่า Feed | เหมาะกับ Local Business/Message Objective |

### ข้อผิดพลาดที่พบบ่อย

- ไม่รู้เลยว่าโฆษณาไปแสดงที่ Audience Network เพราะไม่เคยเปิด Breakdown by Placement มาดู ทำให้เสียงบไปกับ Placement ที่คุณภาพ Traffic ต่ำโดยไม่รู้ตัว
- ใช้ภาพสัดส่วน 1:1 เดียวกันหมดทุก Placement รวมถึง Stories/Reels ที่ต้องการภาพแนวตั้ง ทำให้ภาพถูกครอบตัดหรือมีขอบดำเสียพื้นที่จอไปมาก
- คิดว่า Placement ทุกตัวมีพฤติกรรมผู้ใช้เหมือนกัน ทำครีเอทีฟตัวเดียวใช้ทุกที่โดยไม่ปรับ Message/Hook ให้เหมาะกับความตั้งใจในการเสพคอนเทนต์ของแต่ละที่

---

## Step 182: Automatic Placements ทำงานอย่างไรและควรใช้เมื่อไหร่

### กลไกการทำงานของ Automatic Placements (Advantage+ Placements)

เมื่อเลือก Automatic Placements ระบบจะกระจายงบไปยังทุก Placement ที่มีสิทธิ์แสดงผลตามที่ Objective/Optimization Goal อนุญาต โดยพยายามหาสัดส่วนที่ให้ผลลัพธ์คุ้มค่าที่สุดในราคาที่ดีที่สุดแบบ Real-time เหมือนกับหลักการของ CBO แต่ทำงานที่ระดับ Placement แทนที่จะเป็นระดับ Ad Set

จุดสำคัญคือระบบจะ **เรียนรู้และปรับสัดส่วนเรื่อยๆ** ไม่ได้ตัดสินใจครั้งเดียวแล้วหยุด ถ้า Placement หนึ่งเริ่มมี CPM แพงขึ้นเพราะ Auction แข่งขันสูง ระบบจะลดสัดส่วนงบที่ไปยัง Placement นั้นและโยกไปที่อื่นโดยอัตโนมัติ

### ข้อดีของ Automatic Placements

1. **CPM ถูกลงเฉลี่ยรวม** — เพราะระบบมีตัวเลือกมากขึ้น ไม่ต้องแข่ง Auction เฉพาะใน Feed ที่มีคนแข่งประมูลหนาแน่นที่สุด
2. **Reach กว้างขึ้น** — เข้าถึงกลุ่มคนที่ไม่ได้เสพ Feed เป็นหลักแต่เสพ Stories/Reels/Messenger
3. **ป้องกัน Ad Fatigue เร็วขึ้น** — เพราะกลุ่มเป้าหมายเห็นโฆษณากระจายในหลายตำแหน่ง ไม่ได้เจอซ้ำๆที่เดียว
4. **ระบบเรียนรู้เร็วกว่า Manual** — เพราะมีข้อมูล Auction จากหลาย Placement ให้เรียนรู้พร้อมกัน มักช่วยให้ Learning Phase จบเร็วขึ้นด้วยงบเท่ากัน

### เมื่อไหร่ควรใช้ Automatic Placements

- เริ่มต้นแคมเปญใหม่ที่ยังไม่มีข้อมูลว่า Placement ไหนเหมาะกับ Audience/สินค้านี้
- งบจำกัด ต้องการ Reach/ผลลัพธ์คุ้มค่าที่สุดโดยไม่ต้องเสียเวลาบริหารจัดการหลาย Placement
- ครีเอทีฟที่มีในมือครอบคลุมหลาย Aspect Ratio อยู่แล้ว (มีทั้งภาพสี่เหลี่ยมและแนวตั้ง) ทำให้ Automatic Placements แสดงผลได้เต็มประสิทธิภาพในทุกตำแหน่ง
- Meta เองแนะนำ Automatic Placements เป็นค่า Default สำหรับบัญชีส่วนใหญ่ เพราะข้อมูลในวงกว้างแสดงว่าโดยเฉลี่ยได้ผลลัพธ์ดีกว่า Manual Placement สำหรับคนที่ไม่มีข้อมูลเชิงลึกมาก่อน

### ข้อผิดพลาดที่พบบ่อย

- เปิด Automatic Placements แต่มีครีเอทีฟแค่ภาพสี่เหลี่ยมตัวเดียว ทำให้ Placement แนวตั้ง (Stories, Reels) แสดงผลได้ไม่เต็มที่เพราะภาพไม่เข้ากับพื้นที่จอ
- คิดว่า Automatic Placements คือ "ปุ่มขี้เกียจ" ที่ไม่ต้องดูอะไรเลยหลังตั้งค่า ทั้งที่ยังต้องเข้าไปเช็ก Breakdown by Placement เป็นระยะเพื่อดูว่าสัดส่วนงบไปที่ไหนบ้าง
- ปิด Automatic Placements ทันทีเมื่อเห็น Placement บางตัวมี CTR ต่ำ โดยไม่พิจารณาว่า Placement นั้นอาจให้ Conversion ที่ดีในต้นทุนต่ำ แม้ CTR จะดูไม่สวย (CTR ต่ำไม่ได้แปลว่าแย่เสมอไปถ้า Cost per Result ยังดี)

---

## Step 183: Manual Placements และเมื่อไหร่ควรเลือกเอง

### วิธีเลือก Manual Placements ใน Ads Manager

ที่ Ad Set Level → Placements → เลือก "Manual Placements" แทน "Advantage+ Placements" จากนั้นจะเห็นรายการ Platform (Facebook, Instagram, Messenger, Audience Network) และ Placement ย่อยให้ติ๊กเลือก/ปลดออกได้ตามต้องการ รวมถึงสามารถเลือกอุปกรณ์ (Mobile only, Desktop only) และระบบปฏิบัติการได้ด้วย

### เมื่อไหร่ Manual Placements ให้ผลลัพธ์ดีกว่า

1. **มีข้อมูล Breakdown by Placement ในอดีตชัดเจนแล้ว** — เช่น รันแคมเปญคล้ายกันมาก่อนและพบว่า Audience Network ให้ Traffic คุณภาพต่ำมากสำหรับธุรกิจนี้โดยเฉพาะ (Bounce Rate สูงผิดปกติ, Conversion Rate ต่ำกว่า Placement อื่นมาก) การตัด Audience Network ออกไปเลยจะช่วยประหยัดงบและเพิ่มคุณภาพ Traffic โดยรวม
2. **มีครีเอทีฟที่ออกแบบมาเฉพาะสำหรับ Placement เดียว** — เช่น ทำ Reels Content ที่เป็น Native Video สั้นมากๆ ซึ่งจะดูไม่เข้ากับ Feed แบบภาพนิ่งเลย ในกรณีนี้อาจแยกเป็น Ad Set เฉพาะ Reels เพื่อควบคุมการวัดผลให้ชัดเจน
3. **สินค้า/บริการที่ Sensitive กับ Context การแสดงผล** — เช่น โฆษณาบริการทางการเงินที่ไม่ต้องการไปแสดงใน Audience Network ที่อยู่ในแอปเกมเด็ก เพราะกระทบภาพลักษณ์แบรนด์
4. **ต้องการควบคุม Frequency แยกตาม Placement** — เช่น ต้องการให้ Stories/Reels ได้ความถี่สูงกว่า Feed เพราะเนื้อหาสั้นและดูซ้ำได้ง่ายกว่าโดยไม่รู้สึกล้า
5. **ทดสอบเปรียบเทียบ Placement อย่างเป็นระบบ (A/B Test)** — ต้องการรู้ชัดๆว่า Feed vs Reels ให้ ROAS ต่างกันแค่ไหนสำหรับสินค้านี้ ต้องแยก Ad Set ตาม Placement แล้วเทียบผลแบบ Manual

### ตัวอย่างตัวเลขจริงที่สนับสนุนการเลือก Manual Placement

ร้านขายเครื่องประดับพรีเมียม พบว่าหลังรัน Automatic Placements 2 สัปดาห์ Breakdown แสดงผลดังนี้:

| Placement | สัดส่วนงบที่ใช้ | CTR | Conversion Rate | Cost per Purchase |
|---|---|---|---|---|
| Facebook Feed | 35% | 1.8% | 2.1% | 280 บาท |
| Instagram Feed | 30% | 2.4% | 2.8% | 210 บาท |
| Instagram Stories | 15% | 0.9% | 0.6% | 620 บาท |
| Audience Network | 12% | 0.3% | 0.1% | 1,450 บาท |
| Instagram Reels | 8% | 1.5% | 0.9% | 480 บาท |

จากตารางนี้ Audience Network และ Instagram Stories ให้ผลลัพธ์แย่มากสำหรับสินค้าพรีเมียมชิ้นนี้ (สินค้าราคาสูงที่ต้องการความน่าเชื่อถือ ไม่เหมาะกับ Placement ที่คนดูแบบเผลอๆหรือไม่ได้ตั้งใจ) การเปลี่ยนมาใช้ Manual Placements ตัด Audience Network ออกและลดสัดส่วน Stories ลง จะช่วยให้งบไหลไปที่ Facebook/Instagram Feed ที่ให้ Cost per Purchase ดีกว่ามาก

### ข้อผิดพลาดที่พบบ่อย

- ตัด Placement ออกเร็วเกินไปโดยดูข้อมูลจากงบที่ใช้น้อยเกินไป (เช่น Audience Network ใช้งบไปแค่ 200 บาท แล้วสรุปว่าแย่ทั้งที่ Sample Size เล็กเกินจะสรุปได้แม่นยำ)
- เลือก Manual Placements แต่ติ๊กเหลือ Placement เดียว (เช่น Feed อย่างเดียว) ทำให้ Auction แข่งขันสูงขึ้นมาก เพราะไม่มีตัวเลือกอื่นให้ระบบไปหาโอกาสที่ถูกกว่า
- ไม่ทบทวน Manual Placements ที่ตั้งไว้เป็นระยะ ทั้งที่พฤติกรรมผู้ใช้และ Auction Dynamics เปลี่ยนไปเรื่อยๆ (Placement ที่แย่เมื่อ 6 เดือนก่อนอาจดีขึ้นแล้วในตอนนี้)

---

## Step 184: Feed vs Stories vs Reels — ความแตกต่างด้าน Creative

### พฤติกรรมผู้ใช้ที่แตกต่างกันโดยพื้นฐาน

**Feed:** ผู้ใช้เลื่อนดูแบบ Passive เจตนาเสพเนื้อหาหลากหลายผสมกัน (โพสต์เพื่อน ข่าว โฆษณา) มีเวลาหยุดอ่านนานกว่า สามารถใส่ข้อความยาวได้ ภาพนิ่งทำงานได้ดีพอกับวิดีโอ

**Stories:** ผู้ใช้ปัดผ่านเร็วมาก (เฉลี่ยไม่ถึง 2-3 วินาทีต่อ Story ก่อนปัดต่อ) ต้องการ Hook ที่ชัดในครึ่งวินาทีแรก ข้อความบนภาพต้องสั้นกระชับ พื้นที่จอเต็มแนวตั้ง

**Reels:** ผู้ใช้คาดหวัง Entertainment/ความ Native สูงมาก โฆษณาที่ดูเหมือนโฆษณาชัดเจนเกินไปจะถูกปัดข้ามทันที เนื้อหาที่ดูเป็น UGC หรือ Trend-based มักได้ผลดีกว่าโฆษณาที่ Production สูงแต่ดูเป็นทางการ

### ตาราง Aspect Ratio และข้อกำหนดครีเอทีฟตาม Placement (อ้างอิงสำหรับใช้งานจริง)

| Placement | Aspect Ratio แนะนำ | ความยาววิดีโอแนะนำ | ตำแหน่งข้อความ/CTA | ข้อควรระวัง |
|---|---|---|---|---|
| Facebook/Instagram Feed | 1:1 (สี่เหลี่ยมจัตุรัส) หรือ 4:5 (แนวตั้งเล็กน้อย) | 15-60 วินาที | ตรงกลาง/ล่างภาพได้ ไม่มีข้อจำกัดพื้นที่ปิดบัง | เลี่ยงข้อความเกิน 20% ของพื้นที่ภาพเพื่อประสิทธิภาพการแสดงผลที่ดีกว่า |
| Stories (FB/IG/Messenger) | 9:16 (แนวตั้งเต็มจอ) | 5-15 วินาที (สั้นเพราะปัดเร็ว) | เว้นขอบบน-ล่างประมาณ 14-20% ไม่ให้ข้อความโดน UI ปิดบัง (ปุ่ม Reply, Progress Bar) | ห้ามใส่ Safe Zone ผิด เพราะข้อความ/CTA จะโดน UI ของแพลตฟอร์มบัง |
| Reels (FB/IG) | 9:16 (แนวตั้งเต็มจอ) | 15-30 วินาที | เว้นขอบล่างมากกว่า Stories เพราะมีแถบ Caption/ปุ่มไลก์-แชร์บังพื้นที่มากกว่า | เนื้อหาต้อง Native ไม่เหมือนแอด ใช้เพลง/Trend ปัจจุบันช่วยเพิ่ม Retention |
| In-stream Video | 16:9 (แนวนอน) หรือ 1:1 | 5-15 วินาที (ต้องดึงดูดก่อนกด Skip ได้ที่ 5 วิ) | Hook ต้องอยู่ใน 3 วินาทีแรกเสมอ | ผู้ดูไม่ได้เลือกจะดู ถูกคั่นมา ต้อง Hook แรงกว่า Placement อื่น |
| Right Column | 1:1 (สี่เหลี่ยมเล็ก) | ภาพนิ่งเท่านั้น ไม่รองรับวิดีโอ | ข้อความสั้นมาก อ่านในพื้นที่จำกัด | เลี่ยงภาพที่มีรายละเอียดซับซ้อน เพราะขนาดแสดงผลเล็กมาก |
| Audience Network | 1:1, 4:5, 9:16 (ขึ้นกับแอปปลายทาง) | 5-30 วินาที | หลากหลายตามรูปแบบแอปที่ไปแสดง | ควรใช้ Automatic Placements เพื่อให้ระบบเลือกขนาดที่เหมาะกับแต่ละแอปเอง |
| Marketplace | 1:1, 4:5 | ภาพนิ่งหรือวิดีโอสั้น | เหมือน Feed แต่บริบทคือกำลังหาซื้อของ | เน้นภาพสินค้าชัดเจน ราคาระบุตรงไปตรงมาแบบสินค้ามือสอง |

### หลักการออกแบบครีเอทีฟข้าม Placement ที่ใช้ได้จริง

แทนที่จะพยายามทำครีเอทีฟตัวเดียวให้ "ใช้ได้กับทุก Placement" (ซึ่งมักลงเอยด้วยการประนีประนอมจนไม่ดีพอสำหรับที่ไหนเลย) มืออาชีพจะทำครีเอทีฟอย่างน้อย **2 สัดส่วนหลัก** เสมอ:

1. **สี่เหลี่ยม/แนวนอนเล็กน้อย (1:1 หรือ 4:5)** สำหรับ Feed
2. **แนวตั้งเต็มจอ (9:16)** สำหรับ Stories/Reels

การมีครีเอทีฟทั้งสองสัดส่วนพร้อมใช้ Placement Asset Customization (อธิบายละเอียดใน Step 187) จะทำให้ Automatic Placements แสดงผลได้เต็มประสิทธิภาพในทุกตำแหน่ง ไม่ต้องเสียเวลาไปกับการเลือก Manual Placement เพียงเพราะครีเอทีฟไม่พร้อม

### ข้อผิดพลาดที่พบบ่อย

- ถ่ายวิดีโอแนวนอน (16:9) แล้วนำไปใส่ Stories/Reels โดยไม่ครอบตัดใหม่ ทำให้เกิดขอบดำด้านบน-ล่างจำนวนมาก เสียพื้นที่จอและดูไม่เป็นมืออาชีพ
- ใส่ข้อความ/CTA ชิดขอบภาพเกินไปใน Stories ทำให้โดนปุ่ม UI ของแพลตฟอร์ม (เช่น ปุ่ม Reply, ไอคอนโปรไฟล์) บังจนอ่านไม่ออก
- ทำ Reels ที่มี Production สูงเกินไป (เหมือนโฆษณาทีวี) ทำให้คนรู้สึกว่า "นี่คือแอด" ทันทีและปัดข้ามเร็วกว่าคอนเทนต์ที่ดู Native
- ใช้ความยาววิดีโอเดียวกันทุก Placement (เช่น 60 วินาทีทุกที่) ทั้งที่ Stories/Reels ต้องการความยาวสั้นกว่ามากเพื่อให้จบเรื่องก่อนคนจะปัดออก

---

## Step 185: Audience Network และ In-stream Video

### Audience Network คืออะไร

Audience Network คือเครือข่ายแอปพลิเคชันและเว็บไซต์ของบุคคลที่สาม (Third-party) ที่ร่วมมือกับ Meta ให้แสดงโฆษณาจาก Meta Ads Manager ได้ พูดง่ายๆคือโฆษณาของคุณอาจไปโชว์ในแอปเกม แอปข่าว หรือเว็บไซต์อื่นที่ไม่ใช่ Facebook/Instagram เลย แต่ยังจ่ายเงินและวัดผลผ่านระบบ Meta Ads Manager เดียวกัน

### ข้อดีของ Audience Network

- CPM ถูกที่สุดในบรรดา Placement ทั้งหมด เพราะการแข่งขัน Auction ต่ำกว่า Feed มาก
- ช่วยเพิ่ม Reach ได้มากในงบเท่าเดิม เหมาะกับ Awareness Objective ที่เน้นปริมาณคนเห็น

### ข้อเสียและความเสี่ยงของ Audience Network

- คุณภาพ Traffic มักต่ำกว่า Placement อื่นอย่างมีนัยสำคัญ เพราะผู้ใช้ไม่ได้ตั้งใจดูโฆษณา (บางครั้งคลิกโดยไม่ได้ตั้งใจ เช่น กดปุ่มปิดโฆษณาผิดตำแหน่งในเกม)
- เสี่ยงกระทบภาพลักษณ์แบรนด์ถ้าไปแสดงในแอป/เว็บไซต์ที่มีเนื้อหาไม่เหมาะสม แม้ Meta จะมีระบบกรองคุณภาพ Publisher แต่ก็ไม่สมบูรณ์แบบ 100%
- Conversion Rate ที่ได้จาก Audience Network มักต่ำกว่า Feed/Stories หลายเท่าตัวสำหรับธุรกิจที่ต้องการ Conversion คุณภาพสูง

### In-stream Video คืออะไร

In-stream Video คือโฆษณาที่คั่นแสดงระหว่างวิดีโอของ Creator อื่นบน Facebook (คล้าย YouTube Ads) ผู้ดูมักกดข้ามได้หลัง 5 วินาที (Skippable) จึงต้องออกแบบ Hook ที่แรงมากในช่วงต้นวิดีโอ

### เมื่อไหร่ควรใช้ / ไม่ควรใช้ Audience Network และ In-stream Video

| สถานการณ์ | แนะนำ | เหตุผล |
|---|---|---|
| Awareness Objective งบจำกัด ต้องการ Reach กว้างที่สุด | ใช้ Audience Network ได้ | CPM ถูกช่วยขยาย Reach ในงบเท่าเดิม |
| Sales Objective ที่ต้องการ Conversion คุณภาพสูง (สินค้าราคาสูง/B2B) | ควรตัด Audience Network ออกด้วย Manual Placements | คุณภาพ Traffic ต่ำ ไม่คุ้มกับสินค้าที่ต้องการความน่าเชื่อถือ |
| ธุรกิจที่ Sensitive เรื่องภาพลักษณ์แบรนด์ (การเงิน, เด็ก, สุขภาพ) | ควรตัด Audience Network ออกเป็นค่าเริ่มต้น | ควบคุม Context การแสดงผลไม่ได้เต็มที่ |
| ต้องการ Video Views ปริมาณมากในราคาถูก เพื่อสร้าง Retargeting Pool | ใช้ In-stream Video ร่วมกับ Feed ได้ | CPV ถูกกว่า ช่วยขยาย Pool ในงบจำกัด |

### ข้อผิดพลาดที่พบบ่อย

- ปล่อย Audience Network ไว้ในทุกแคมเปญโดยไม่เคยเช็ก Breakdown แยกดูคุณภาพ Traffic เฉพาะ Placement นี้
- ใช้ In-stream Video กับครีเอทีฟที่ Hook ช้า (เนื้อเรื่องค่อยๆเข้า) ทำให้คนกด Skip ก่อนถึงจุดสำคัญ
- ตัด Audience Network ออกทั้งหมดโดยอัตโนมัติทุกครั้งโดยไม่เคยทดสอบเปรียบเทียบก่อน ทั้งที่บางธุรกิจ (เช่น สินค้าที่ขายผ่านแอปเกม/ความบันเทิง) อาจได้ผลดีจาก Audience Network มากกว่าปกติ

---

## Step 186: Messenger Placements

### Messenger ในฐานะ Placement โฆษณา

Messenger มี 3 รูปแบบ Placement หลักที่ใช้แสดงโฆษณาได้:

1. **Messenger Inbox** — โฆษณาปรากฏอยู่ในรายการแชทเหมือนข้อความปกติ มีจุดเด่นคือผู้ใช้มักมีสมาธิสูงกว่าตอนเลื่อน Feed เพราะกำลังตั้งใจเช็คข้อความ
2. **Messenger Stories** — เหมือน Facebook/Instagram Stories แต่แสดงในแอป Messenger
3. **Sponsored Messages** — ส่งข้อความโฆษณาตรงถึงกล่องแชทของคนที่ **เคยคุยกับเพจมาก่อนแล้ว** เท่านั้น (ไม่สามารถส่งหาคนที่ไม่เคยแชทมาก่อนได้ เพราะผิดนโยบาย Spam) เหมาะมากสำหรับการ Follow-up ลูกค้าเก่าหรือแจ้งโปรโมชั่นให้คนที่เคยติดต่อ

### เมื่อไหร่ควรใช้ Messenger Placements

- ธุรกิจ Local ที่ปิดการขายผ่านแชท (ร้านอาหาร, ร้านเสื้อผ้า, ธุรกิจบริการ) ที่มี Objective = Leads หรือ Sales แบบ Click-to-Messenger
- ธุรกิจที่มี Chatbot พร้อมตอบอัตโนมัติ 24 ชั่วโมง ทำให้ Conversion Rate จาก Messenger สูงกว่าปกติเพราะตอบได้ทันที
- Sponsored Messages เหมาะกับการ Reactivate ลูกค้าเก่าที่แชทไว้นานแล้วแต่ยังไม่ปิดการขาย หรือแจ้งโปรโมชั่นใหม่ให้ลูกค้าเก่าเฉพาะกลุ่ม

### ข้อผิดพลาดที่พบบ่อย

- เปิด Messenger Placement ไว้แต่ไม่มีทีมตอบแชทหรือ Chatbot รองรับ ทำให้ลีดที่เข้ามาไม่ได้รับการตอบสนอง เสียโอกาสปิดการขาย
- ใช้ Sponsored Messages บ่อยเกินไปกับกลุ่มคนเดิม ทำให้ผู้ใช้รู้สึกถูกสแปมและบล็อกเพจ/รีพอร์ต ซึ่งกระทบ Page Quality โดยตรง
- ไม่แยก Ad Set สำหรับ Messenger ออกจาก Feed/Stories ทำให้วัดผลความสำเร็จของ Messenger แยกจากตำแหน่งอื่นไม่ได้ชัดเจน

---

## Step 187: Placement Asset Customization สำหรับแต่ละตำแหน่ง

### Placement Asset Customization คืออะไร

ฟีเจอร์นี้ช่วยให้คุณอัปโหลดครีเอทีฟหลายเวอร์ชัน (ต่างสัดส่วน ต่างข้อความ) ไว้ใน Ad ตัวเดียว แล้วให้ระบบเลือกใช้ครีเอทีฟที่เหมาะกับแต่ละ Placement โดยอัตโนมัติ เช่น เมื่อโฆษณาไปแสดงที่ Stories ระบบจะใช้เวอร์ชันแนวตั้ง 9:16 ที่คุณเตรียมไว้ แต่พอไปแสดงที่ Feed จะสลับไปใช้เวอร์ชัน 1:1 หรือ 4:5 แทน — ทั้งหมดนี้เกิดขึ้นภายใน Ad เดียว ไม่ต้องสร้างหลาย Ad แยกกัน

### วิธีตั้งค่าใน Ads Manager

1. ที่ Ad Level → เมื่ออัปโหลดรูป/วิดีโอ ให้เลือก "Customize placements" หรือ "Show more options" (ตำแหน่งอาจเปลี่ยนตาม UI)
2. อัปโหลดครีเอทีฟหลายสัดส่วนไว้ในช่องเดียวกัน (แนะนำอย่างน้อย 1:1 หรือ 4:5 สำหรับ Feed และ 9:16 สำหรับ Stories/Reels)
3. สามารถปรับข้อความ (Primary Text, Headline) ให้ต่างกันในแต่ละ Placement ได้ด้วย เช่น Feed ใช้ข้อความยาวอธิบายละเอียด ส่วน Stories ใช้ข้อความสั้นกระชับ
4. ระบบจะ Preview ให้เห็นว่าแต่ละ Placement จะแสดงผลเป็นอย่างไรก่อน Publish จริง ควรเช็กทุกตำแหน่งในหน้า Preview ก่อนกดยืนยัน

### ทำไม Placement Asset Customization สำคัญกว่าที่คิด

การไม่ใช้ฟีเจอร์นี้แล้วปล่อยให้ระบบ "Crop" ภาพสี่เหลี่ยมให้เป็นแนวตั้งเองอัตโนมัติ มักทำให้เกิดปัญหา:
- จุดสำคัญของภาพ (โลโก้ หน้าคน ข้อความ CTA) ถูกครอบตัดออกไปเพราะระบบ Crop แบบอัตโนมัติไม่รู้ว่าจุดไหนสำคัญ
- เกิดขอบดำ/เบลอด้านบน-ล่างที่ดูไม่เป็นมืออาชีพ ทำให้ CTR ต่ำกว่าที่ควรจะเป็น

### ตัวอย่างการวางแผนครีเอทีฟให้พร้อม Customization

| Placement | ไฟล์ที่ควรเตรียม | ข้อความที่ควรปรับ |
|---|---|---|
| Feed | ภาพ/วิดีโอ 1:1 หรือ 4:5 | Primary Text ยาวอธิบายรายละเอียดสินค้า/โปรโมชั่นครบถ้วน |
| Stories | วิดีโอ/ภาพ 9:16 ความยาว 5-15 วิ | ข้อความสั้นมาก 1 บรรทัด + CTA ชัดเจน |
| Reels | วิดีโอ 9:16 Native Style 15-30 วิ | Caption สั้น ใช้ Hashtag/Sound Trend ถ้ามี |
| Right Column | ภาพ 1:1 เรียบง่าย ไม่มีรายละเอียดซับซ้อน | ข้อความสั้นที่สุด อ่านง่ายในขนาดเล็ก |

### ข้อผิดพลาดที่พบบ่อย

- อัปโหลดแค่สัดส่วนเดียวแล้วเข้าใจว่า Placement Asset Customization "ทำงานได้เอง" โดยไม่ต้องเตรียมไฟล์เพิ่ม (ความจริงคือต้องอัปโหลดหลายสัดส่วนเองก่อน ระบบแค่เลือกใช้ให้ถูกที่)
- ลืมเช็ก Preview ในทุก Placement ก่อน Publish ทำให้พบปัญหาการ Crop ผิดจุดหลังโฆษณาวิ่งไปแล้วหลายวัน
- ใช้ข้อความเดียวกันทุก Placement ทั้งที่ Stories/Reels ต้องการความกระชับกว่า Feed มาก ทำให้ข้อความยาวเกินไปจนอ่านไม่ทันในหน้าจอที่ปัดเร็ว

---

## Step 188: Breakdown by Placement ในการอ่านผลลัพธ์

### วิธีเปิด Breakdown by Placement

ใน Ads Manager ที่ระดับ Campaign/Ad Set/Ad → คลิก "Breakdown" → เลือก "By Delivery" → "Placement" ระบบจะแสดงผลลัพธ์แยกตามแต่ละ Placement ให้เห็นทันทีว่า Feed, Stories, Reels, Audience Network ฯลฯ แต่ละตัวทำผลลัพธ์อย่างไรบ้าง

### ตัวชี้วัดที่ต้องดูคู่กันเสมอ

อย่าดู Placement Breakdown จากตัวชี้วัดเดียว ให้ดูอย่างน้อย 4 ค่าประกอบกัน:

| ตัวชี้วัด | ความหมายที่ต้องระวัง |
|---|---|
| Amount Spent | Placement ที่ใช้งบน้อยเกินไป (ต่ำกว่า 10-15% ของงบรวม) ยังไม่มี Sample Size พอสรุปผลได้แม่นยำ |
| CTR | บอกความน่าสนใจของครีเอทีฟในบริบทนั้น แต่ไม่ได้บอกคุณภาพ Traffic โดยตรง |
| Cost per Result / CPA | ตัวชี้วัดหลักที่ควรใช้ตัดสินใจ เพราะเชื่อมกับต้นทุนธุรกิจจริง |
| Conversion Rate หลังคลิก | ช่วยแยกว่า Placement ที่ CTR สูงแต่ Conversion แย่ อาจได้ Traffic ที่ไม่ตรงกลุ่ม |

### ตัวอย่างการวิเคราะห์ Breakdown จริง

| Placement | Amount Spent (บาท) | CTR | Cost per Purchase (บาท) | การตัดสินใจที่แนะนำ |
|---|---|---|---|---|
| Facebook Feed | 4,500 (30%) | 1.9% | 195 | คงไว้ เป็น Placement หลักที่ทำงานดี |
| Instagram Feed | 5,200 (35%) | 2.6% | 165 | คงไว้ และอาจเพิ่มน้ำหนักครีเอทีฟให้ Placement นี้ |
| Instagram Reels | 3,000 (20%) | 3.1% | 310 | CTR สูงแต่ Conversion แย่ ต้องเช็คว่า Landing Page เหมาะกับ Traffic จาก Reels หรือไม่ |
| Audience Network | 900 (6%) | 0.4% | 780 | พิจารณาตัดออกด้วย Manual Placements ถ้าเทรนด์นี้ต่อเนื่องหลายสัปดาห์ |
| Messenger | 1,400 (9%) | 2.2% | 140 | ผลดีมาก ควรพิจารณาเพิ่มงบเฉพาะ Placement นี้ในรอบถัดไป |

จากตารางนี้ Instagram Reels เป็นตัวอย่างชัดของ "CTR สูงแต่ Conversion แย่" ซึ่งอาจไม่ใช่ปัญหาของ Placement เอง แต่อาจเป็นเพราะกลุ่มคนที่คลิกจาก Reels เป็นกลุ่มที่ยังไม่พร้อมซื้อ (คลิกด้วยความอยากรู้มากกว่าตั้งใจซื้อจริง) การแก้ปัญหาอาจไม่ใช่การตัด Reels ออก แต่คือการปรับ Landing Page หรือ Offer ให้เหมาะกับพฤติกรรมกลุ่มนี้มากขึ้น

### ข้อผิดพลาดที่พบบ่อย

- ตัด Placement ออกจาก Breakdown เพียง 2-3 วันแรกที่ Sample Size ยังน้อยเกินไป ทำให้ตัดสินใจผิดพลาดจากข้อมูลที่ไม่นิ่งพอ
- ดูแค่ CTR อย่างเดียวแล้วสรุปว่า Placement ไหน "ดีที่สุด" โดยไม่เช็ก Cost per Result ที่เชื่อมกับธุรกิจจริง
- ไม่เคยเปิด Breakdown by Placement เลยตลอดที่รันแคมเปญ ทำให้ไม่รู้เลยว่างบไปกระจุกอยู่ที่ไหนและ Placement ไหนคุ้มค่าที่สุด

---

## Step 189: Placement ที่เหมาะกับแต่ละ Objective

### ตารางจับคู่ Placement กับ Objective

| Objective | Placement ที่มักทำงานดี | Placement ที่ควรพิจารณาตัดออก (ถ้าจำเป็น) |
|---|---|---|
| Awareness (Reach) | Automatic Placements ทั้งหมด (ยิ่งกว้างยิ่งดีสำหรับ Reach) | ไม่ควรตัดอะไรออก เพราะเป้าหมายคือ Reach สูงสุด |
| Traffic | Feed, Search Results, Marketplace (ถ้าสินค้าเหมาะ) | Right Column (CTR ต่ำเกินไปสำหรับเป้าหมายที่ต้องการคลิก) |
| Engagement (Video Views) | Reels, Stories, In-stream Video | Right Column (ไม่รองรับวิดีโอ) |
| Leads (Instant Form) | Feed, Stories | Audience Network (คุณภาพลีดมักต่ำ) |
| Leads (Messenger/Click-to-Chat) | Messenger Inbox, Stories | Audience Network |
| Sales (Website Conversions) | Feed, Instagram Feed, Messenger (ถ้าปิดขายผ่านแชท) | Audience Network ถ้าคุณภาพ Traffic ต่ำจาก Breakdown |
| Sales (Catalog/Dynamic Retargeting) | Feed, Instagram Feed, Audience Network (Native/Banner เหมาะกับ Retargeting) | Right Column (พื้นที่เล็กเกินไปสำหรับ Dynamic Product Card) |
| App Promotion | Audience Network, Reels, In-stream Video | Right Column (ไม่เหมาะกับการโปรโมทแอปที่ต้องการ Engagement สูง) |

### หลักการเลือกที่ใช้ได้จริง

แทนที่จะจำตารางนี้แบบตายตัว ให้ใช้หลักคิด 3 ข้อนี้ประกอบกันเสมอ:

1. **Objective ต้องการพฤติกรรมแบบไหน** — ถ้าต้องการ "ความตั้งใจสูง" (Sales, Leads คุณภาพสูง) ให้เลือก Placement ที่ผู้ใช้มีสมาธิสูง (Feed, Messenger) ถ้าต้องการ "ปริมาณ" (Awareness, Reach) ให้เปิดกว้างที่สุด
2. **ครีเอทีฟที่มีพร้อมหรือไม่** — ถ้ามีแค่ภาพสี่เหลี่ยม อย่าฝืนใช้ Stories/Reels เป็นหลัก เพราะจะแสดงผลได้ไม่ดี
3. **มีข้อมูล Breakdown ในอดีตหรือไม่** — ถ้ามี ให้ใช้ข้อมูลจริงตัดสินใจมากกว่าตารางทั่วไป เพราะแต่ละธุรกิจมีพฤติกรรม Audience ที่ต่างกัน

### ข้อผิดพลาดที่พบบ่อย

- ใช้ Placement เดียวกันสำหรับทุก Objective โดยไม่ปรับตามลักษณะพฤติกรรมที่ Objective นั้นต้องการ
- เชื่อตารางแนะนำทั่วไป 100% โดยไม่เคยทดสอบเทียบกับข้อมูลจริงของธุรกิจตัวเอง (บางธุรกิจ Audience Network อาจทำงานดีผิดคาด ถ้าไม่ทดสอบก็จะไม่รู้)
- ตัด Placement ที่ "ดูไม่ตรงกับ Objective ตามทฤษฎี" ออกทันทีโดยไม่เคยให้โอกาสทดสอบเลยแม้แต่ครั้งเดียว

---

## Case Study: แบรนด์รองเท้าวิ่งทดสอบ Placement เพื่อลด Cost per Purchase

**สถานการณ์:** แบรนด์รองเท้าวิ่งออนไลน์ใช้ Automatic Placements มาตลอด 4 เดือน Cost per Purchase เฉลี่ยอยู่ที่ 420 บาท ซึ่งสูงกว่า Break-even ที่ตั้งไว้ (350 บาท) เจ้าของแบรนด์ต้องการหาสาเหตุว่าเงินรั่วไหลไปที่ไหน

**การตรวจสอบ:** เปิด Breakdown by Placement ของ 30 วันล่าสุด พบว่า:

| Placement | สัดส่วนงบ | Cost per Purchase |
|---|---|---|
| Instagram Feed | 28% | 240 บาท |
| Facebook Feed | 22% | 310 บาท |
| Instagram Reels | 18% | 290 บาท |
| Facebook Reels | 10% | 350 บาท |
| Audience Network | 15% | 890 บาท |
| Messenger | 7% | 260 บาท |

Audience Network ใช้งบไปถึง 15% ของงบรวม แต่ Cost per Purchase สูงกว่าค่าเฉลี่ยของ Placement อื่นถึง 2-3 เท่า เมื่อคำนวณ Blended Cost per Purchase ทั้งหมดพบว่า Audience Network ตัวเดียวดึงค่าเฉลี่ยรวมขึ้นไปมาก

**การแก้ไข:** เปลี่ยนจาก Automatic Placements เป็น Manual Placements โดยตัด Audience Network ออก คงเหลือ Facebook/Instagram Feed, Reels, และ Messenger จากนั้นนำงบ 15% ที่เคยไปทาง Audience Network มาเพิ่มให้ Instagram Feed และ Messenger ที่ทำผลงานดีที่สุด

**ผลลัพธ์หลัง 3 สัปดาห์:** Blended Cost per Purchase ลดลงจาก 420 บาท เหลือ 285 บาท ต่ำกว่า Break-even ที่ตั้งไว้แล้ว โดยไม่ได้เพิ่มงบรวมเลย เพียงจัดสรร Placement ใหม่ให้ตรงกับข้อมูลจริง

**บทเรียน:** Automatic Placements ไม่ได้แปลว่า "ดีที่สุดเสมอ" — มันคือค่า Default ที่ดีสำหรับการเริ่มต้นเมื่อยังไม่มีข้อมูล แต่เมื่อมีข้อมูล Breakdown เพียงพอแล้ว การเปลี่ยนไป Manual Placements อย่างมีเหตุผลสามารถปรับปรุงผลลัพธ์ได้อย่างมีนัยสำคัญ กุญแจสำคัญคือ **ต้องมีข้อมูลก่อนตัดสินใจ ไม่ใช่ตัดสินใจจากความรู้สึก**

---

## Checklist ท้ายบท

- [ ] รู้จัก Placement ทั้งหมดในระบบ Meta Family of Apps อย่างน้อย 10 ตำแหน่งหลัก
- [ ] เข้าใจกลไกการทำงานของ Automatic Placements และรู้ว่าเหมาะกับสถานการณ์ไหน
- [ ] เข้าใจเมื่อไหร่ Manual Placements ให้ผลลัพธ์ดีกว่า และรู้วิธีตั้งค่าใน Ads Manager
- [ ] จำ Aspect Ratio ที่ถูกต้องของ Feed (1:1, 4:5), Stories/Reels (9:16), In-stream (16:9) ได้
- [ ] เข้าใจความเสี่ยงและข้อดีของ Audience Network และ In-stream Video
- [ ] รู้จัก 3 รูปแบบของ Messenger Placement และเงื่อนไขการใช้ Sponsored Messages
- [ ] เข้าใจและสามารถตั้งค่า Placement Asset Customization เพื่อให้ครีเอทีฟแสดงผลถูก Placement
- [ ] สามารถเปิดและวิเคราะห์ Breakdown by Placement พร้อมดูตัวชี้วัดอย่างน้อย 4 ค่าประกอบกัน
- [ ] จับคู่ Placement ที่เหมาะสมกับแต่ละ Objective ได้อย่างมีเหตุผล ไม่ใช่จำตารางแบบตายตัว
- [ ] มีแผนทดสอบ Placement Performance ของธุรกิจตัวเองอย่างเป็นระบบ

---

## Workshop / แบบฝึกหัด: ทดสอบ Placement Performance

### โจทย์

ธุรกิจ: ร้านขายกระเป๋าแฟชั่นออนไลน์ กำลังใช้ Automatic Placements มา 3 สัปดาห์ ต้องการทดสอบว่าควรเปลี่ยนไป Manual Placements หรือไม่ ให้ออกแบบการทดสอบตามขั้นตอนต่อไปนี้

### ขั้นตอนที่ต้องทำ

**ขั้นที่ 1 — เก็บ Baseline Data**
เปิด Breakdown by Placement ของแคมเปญที่รันด้วย Automatic Placements มาอย่างน้อย 14 วัน บันทึกตัวเลข Amount Spent, CTR, Cost per Purchase ของทุก Placement ลงในตาราง

**ขั้นที่ 2 — ตั้งเกณฑ์การตัดสินใจล่วงหน้า (ก่อนดูผล เพื่อลด Bias)**
เขียนเกณฑ์ไว้ก่อนว่า "Placement ที่จะพิจารณาตัดออก ต้องมี Amount Spent อย่างน้อย 10% ของงบรวม และ Cost per Purchase สูงกว่าค่าเฉลี่ยรวมอย่างน้อย 50%"

**ขั้นที่ 3 — สร้างการทดสอบแบบ Split**
สร้าง Ad Set คู่ (Duplicate) จาก Ad Set เดิม โดย:
- Ad Set A: คง Automatic Placements ไว้เหมือนเดิม งบครึ่งหนึ่ง
- Ad Set B: เปลี่ยนเป็น Manual Placements ตัด Placement ที่เข้าเกณฑ์ Step 2 ออก งบอีกครึ่งหนึ่ง
- ใช้ Audience และ Creative เดียวกันทั้งสอง Ad Set เพื่อให้เปรียบเทียบได้ยุติธรรม (ควรใช้ Meta's A/B Test Tool อย่างเป็นทางการถ้าบัญชีรองรับ เพื่อป้องกัน Audience Overlap)

**ขั้นที่ 4 — รันทดสอบอย่างน้อย 7-10 วัน**
รอให้ทั้งสอง Ad Set ผ่าน Learning Phase ก่อนสรุปผล อย่าตัดสินใจจากข้อมูล 2-3 วันแรก

**ขั้นที่ 5 — เปรียบเทียบและตัดสินใจ**
เทียบ Cost per Purchase, Amount Spent, และ ROAS ของทั้งสอง Ad Set แล้วเลือกแนวทางที่ให้ผลลัพธ์ดีกว่าไปใช้กับแคมเปญหลัก

### ตารางบันทึกผลสำหรับ Workshop (ให้กรอกด้วยข้อมูลจริงหรือสมมติ)

| Placement | Amount Spent (Ad Set A) | Cost per Purchase (Ad Set A) | Amount Spent (Ad Set B) | Cost per Purchase (Ad Set B) |
|---|---|---|---|---|
| Facebook Feed | _____ | _____ | _____ | _____ |
| Instagram Feed | _____ | _____ | _____ | _____ |
| Stories | _____ | _____ | _____ | _____ |
| Reels | _____ | _____ | _____ | _____ |
| Audience Network | _____ | _____ | (ตัดออก) | (ตัดออก) |
| Messenger | _____ | _____ | _____ | _____ |
| **สรุป Cost per Purchase เฉลี่ยรวม** | | _____ | | _____ |

### คำถามให้ฝึกคิดต่อ

1. ถ้า Ad Set B (Manual) ได้ Cost per Purchase ดีกว่า แต่ Amount Spent ใช้ไม่เต็มงบ (Underspend) ควรตีความผลลัพธ์นี้อย่างไร?
2. ถ้าผลลัพธ์ของทั้งสอง Ad Set ใกล้เคียงกันมาก (ต่างกันไม่ถึง 10%) ควรเลือกแบบไหนและเพราะอะไร?
3. หลังตัดสินใจใช้ Manual Placements แล้ว ควรกลับมาทดสอบ Automatic Placements อีกครั้งเมื่อไหร่ (เพราะ Auction Dynamics เปลี่ยนแปลงตลอดเวลา)?

**วิธีส่งงาน:** บันทึกผลการทดสอบจริง (หรือออกแบบสมมติฐานที่เป็นไปได้ถ้ายังไม่มีบัญชีจริง) พร้อมข้อสรุปว่าจะใช้ Automatic หรือ Manual Placements ต่อไป และเหตุผลสนับสนุนจากข้อมูล

---

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้เติมเต็มความเข้าใจเรื่อง "โฆษณาไปแสดงที่ไหน" ซึ่งเป็นตัวแปรที่หลายคนมองข้าม เราได้เรียนรู้ Placement ทั้งหมดของ Meta Family of Apps, กลไกและข้อดีของ Automatic Placements, สถานการณ์ที่ Manual Placements ให้ผลลัพธ์ดีกว่า, ความแตกต่างด้าน Creative ระหว่าง Feed/Stories/Reels พร้อมตาราง Aspect Ratio ที่ใช้งานจริงได้ทันที, ความเสี่ยงของ Audience Network, การใช้ Messenger เป็น Placement, เทคนิค Placement Asset Customization, วิธีอ่าน Breakdown by Placement อย่างมีหลักการ และการจับคู่ Placement กับ Objective

ตอนนี้คุณมีองค์ประกอบสำคัญครบแล้วสามอย่าง — Objective ที่ถูกต้อง (Part 017), Budget/Bid Strategy ที่เหมาะสม (Part 018), และ Placement ที่ตรงจุด (Part 019) — แต่ก่อนจะเริ่มลงมือสร้างแคมเปญจริงในทางปฏิบัติ ยังมีเรื่องสำคัญที่ต้องรู้ก่อนเสมอ คือ **นโยบายโฆษณาของ Facebook และการป้องกันไม่ให้บัญชีถูกระงับ** ใน **Part 020: นโยบายโฆษณา Facebook และการหลีกเลี่ยงแอดโดนระงับ** เราจะเจาะลึกหมวดหมู่ที่เข้มงวดที่สุด สาเหตุที่บัญชีถูก Disable และวิธีป้องกันความเสี่ยงเหล่านี้อย่างเป็นระบบ ก่อนที่คุณจะเริ่มลงมือสร้างแคมเปญจริงทีละ Step ใน Section C

---

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center: "About placements for ads"
- Meta Business Help Center: "About Advantage+ placements"
- Meta Business Help Center: "Ad creative specs for Facebook and Instagram" (อัปเดตขนาด/สัดส่วนล่าสุดเสมอ เพราะ Meta ปรับข้อกำหนดเป็นระยะ)
- Meta Business Help Center: "About Audience Network"
- Meta Business Help Center: "About sponsored messages"
- Meta for Business: "Placement Asset Customization overview"
- Meta Business Help Center: "About breakdowns in Ads Manager reporting"
- ตรวจสอบ Ad Specs ล่าสุดที่ facebook.com/business/ads-guide ก่อนสร้างครีเอทีฟทุกครั้ง เพราะขนาดไฟล์/สัดส่วนที่แนะนำอาจเปลี่ยนแปลงตามการอัปเดต Feature ของแพลตฟอร์ม
