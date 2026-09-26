# Part 046: Core Audience — Demographics, Interests, Behaviors

**Section:** E — Facebook Targeting, Audiences & Funnels
**Step ที่ครอบคลุม:** 451–460 (จากทั้งหมด 1000 Steps)
**เวลาศึกษาโดยประมาณ:** 6–8 ชั่วโมง (รวมอ่านเนื้อหา + ลงมือสร้าง Audience จริงใน Ads Manager)
**ระดับ:** เริ่มต้น–กลาง (ต้องมีพื้นฐาน Campaign/Ad Set/Ad Structure จาก Part 016 และเข้าใจ Advantage+ Audience จาก Part 030 มาก่อน จะได้ไม่สับสนว่าทำไม Part นี้ยังต้องพูดถึง "Core Audience" แบบเดิม)

---

หลาย Part ที่ผ่านมาใน Section C เราเรียนเรื่อง Advantage+ Audience กันไปแล้วว่า AI ของ Meta เข้ามาทำหน้าที่ "หาคน" แทนมนุษย์มากขึ้นเรื่อย ๆ คำถามที่ตามมาคือ แล้วทำไม Section E ซึ่งเป็น Section ใหม่เรื่อง Targeting & Audiences โดยเฉพาะ ยังต้องเปิดด้วย Part ที่พูดถึง Core Audience แบบ Demographics, Interests, Behaviors ซึ่งฟังดูเป็นเรื่อง "เก่า" อีก

คำตอบคือ Core Audience ไม่ได้ตายไปจากระบบ Meta Ads เพียงแต่บทบาทของมันเปลี่ยนไป จากที่เคยเป็น "อาวุธหลัก" ในการเจาะกลุ่มเป้าหมาย กลายเป็น "วัตถุดิบ" ที่ AI ใช้ประกอบการตัดสินใจ และในหลายสถานการณ์ — บัญชีใหม่ที่ยังไม่มี Pixel Data, ธุรกิจ B2B เฉพาะทาง, สินค้าที่มีข้อจำกัดทางกฎหมาย, หรือช่วงที่ต้องทำ Market Research หา Persona ใหม่ — Core Audience ยังเป็นเครื่องมือที่จำเป็นและทรงพลังอยู่ดี นักยิงแอดมืออาชีพต้องเข้าใจกลไกเบื้องหลังอย่างละเอียด ไม่ใช่แค่รู้ว่า "มีปุ่มให้กด" เพราะความเข้าใจนี้จะเป็นฐานให้ตัดสินใจถูกว่าเมื่อไหร่ควรใช้ Core Audience เมื่อไหร่ควรปล่อยให้ AI ทำงาน และที่สำคัญที่สุดคือเข้าใจว่าทำไมข้อมูล Interest ที่ Facebook เก็บไว้ในปี 2026 นี้ไม่เหมือนกับข้อมูลที่เก็บไว้เมื่อ 8-10 ปีก่อนอีกต่อไป

Part นี้จะพาไปเจาะทุกส่วนของ Core Audience ตั้งแต่ Building Block พื้นฐานอย่าง Location/Age/Gender/Language ไปจนถึง Detailed Targeting แบบ Interest/Behavior/Demographics การผสม Logic แบบ AND/OR การ Exclude การประเมิน Audience Size ที่เหมาะสม และปิดท้ายด้วย Workshop สร้าง Audience จริง 3 แบบสำหรับสินค้าจริงหนึ่งตัว

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 451** — Core Audience Building Blocks: Location, Age, Gender, Language ตั้งค่าอย่างไรให้ถูกต้องและแม่นยำ
2. **Step 452** — Detailed Targeting: Interests คืออะไร ข้อมูลมาจากไหน และทำงานต่างจากเมื่อ 5 ปีก่อนอย่างไรหลัง iOS14/Signal Loss
3. **Step 453** — Detailed Targeting: Behaviors และ Demographics แยกประเภท พร้อมตัวอย่างการใช้งานจริงแต่ละหมวด
4. **Step 454** — Interest Stacking: Logic แบบ AND/OR การใช้ "Narrow Audience" และ "Broaden Audience" อย่างถูกวิธี
5. **Step 455** — Exclusion Targeting: Exclude Interest, Behavior, และ Custom Audience อย่างมีชั้นเชิง
6. **Step 456** — Audience Size Guidance: อ่าน Potential Reach และ Estimated Results เป็น แคบไปเป็นแบบไหน กว้างไปเป็นแบบไหน
7. **Step 457** — Saved Audiences: Workflow การสร้าง บันทึก ตั้งชื่อ และดูแลรักษาในระยะยาว
8. **Step 458** — เมื่อไหร่ Core Audience Targeting ยังสำคัญ เมื่อไหร่ควรให้ Advantage+ Audience ครองสนาม
9. **Step 459** — ข้อผิดพลาดคลาสสิก: Audience Overlap ระหว่าง Ad Set และวิธีตรวจสอบด้วย Audience Overlap Tool
10. **Step 460** — Workshop: สร้าง 3 Core Audience สำหรับสินค้าจริง 1 ตัว และประเมิน Reach เปรียบเทียบ

---

## Step 451: Core Audience Building Blocks — Location, Age, Gender, Language

### Core Audience คืออะไรกันแน่

Core Audience คือกลุ่มเป้าหมายที่สร้างจากเงื่อนไขที่ Meta เก็บไว้เกี่ยวกับผู้ใช้ทุกคนบนแพลตฟอร์ม แบ่งเป็น 2 ชั้นหลัก คือ

1. **Location, Age, Gender, Language** — เงื่อนไขพื้นฐานที่บังคับต้องตั้งเสมอ (Location เป็น Required Field, ส่วน Age/Gender/Language มีค่า Default เป็น "ทั้งหมด")
2. **Detailed Targeting** — Interests, Behaviors, Demographics ที่เป็นตัวเลือกเสริม ไม่บังคับต้องใส่

ตำแหน่งตั้งค่าอยู่ที่ Ads Manager → เลือก Campaign → เลือก Ad Set → เลื่อนลงมาที่ส่วน **Audience Controls** (ในบัญชีที่ยังเปิดให้เลือก Manual/Original Audience ได้ จะเห็นตัวเลือกให้สลับจาก Advantage+ Audience กลับมาเป็น Original Audience ก่อน จึงจะเห็นฟิลด์ Core Audience แบบเต็มรูปแบบทั้งหมด)

### Location: เจาะลึกฟิลด์ที่มักถูกมองข้าม

ฟิลด์ Location ไม่ใช่แค่กล่องให้พิมพ์ชื่อจังหวัด แต่มีตัวเลือกย่อยที่กระทบผลลัพธ์อย่างมาก:

- **Everyone in this location** — ยิงให้ทุกคนที่ Location History ชี้ว่าอยู่ในพื้นที่นั้น รวมคนที่กำลังเดินทางผ่าน (ค่า Default และเหมาะกับธุรกิจส่วนใหญ่)
- **People who live in this location** — จำกัดเฉพาะคนที่ Meta ประเมินว่า "อยู่อาศัยจริง" ในพื้นที่นั้น (ใช้ Location History ระยะยาวกว่า) เหมาะกับธุรกิจที่ต้องการลูกค้าประจำท้องถิ่นจริง ๆ เช่น คลินิก ร้านอาหาร ที่ไม่อยากเสียงบให้นักท่องเที่ยว
- **People recently in this location** — เจาะกลุ่มคนที่เพิ่งอยู่ในพื้นที่ช่วงเวลาสั้น ๆ ที่ผ่านมา เหมาะกับธุรกิจที่เกี่ยวกับ Event หรือสถานที่ท่องเที่ยว
- **People traveling in this location** — เฉพาะคนที่กำลังเดินทาง ไม่ได้อยู่อาศัยประจำ เหมาะกับธุรกิจสนามบิน โรงแรม ของฝาก

การตั้งค่า Radius Targeting ทำได้โดยพิมพ์ชื่อสถานที่ (Pin Location) แล้วปรับรัศมีได้ตั้งแต่ 1 กม. ถึง 80 กม. เหมาะกับร้านค้าหน้าร้าน (Brick & Mortar) ที่ต้องการยิงเฉพาะคนในระยะที่มาซื้อของได้จริง เช่น ร้านอาหาร Delivery ที่ส่งได้ในรัศมี 5 กม. ควรตั้ง Radius 5 กม. รอบที่ตั้งร้าน ไม่ใช่ตั้งทั้งจังหวัด

**ข้อผิดพลาดที่พบบ่อยเรื่อง Location:**

1. ตั้ง Location กว้างเกินความสามารถในการให้บริการจริง เช่น ร้าน Delivery ตั้งยิงทั้งกรุงเทพฯ ทั้งที่ส่งได้แค่ 5 กม. ทำให้เสียงบไปกับคนที่สนใจแต่สั่งไม่ได้
2. ใช้ "Everyone in this location" กับธุรกิจที่ต้องการลูกค้าประจำจริง ๆ ทำให้ปนกับนักท่องเที่ยวที่ไม่กลับมาซื้อซ้ำ
3. ลืมว่า Location เป็น Hard Constraint แม้ใน Advantage+ Audience — ตั้งผิดพื้นที่แล้วจะไม่มีทางแก้ด้วย Suggestion อื่นเลย ต้องแก้ที่ Location ตรง ๆ เท่านั้น
4. ไม่ใช้ Location Exclusion เมื่อธุรกิจมีพื้นที่ที่รู้แน่ชัดว่าไม่คุ้มยิง (เช่น พื้นที่ที่เคยยิงแล้ว Conversion Rate ต่ำมากต่อเนื่องหลายเดือน)

### Age: ช่วงอายุและข้อจำกัด

Age ตั้งได้ตั้งแต่ 13-65+ (ขั้นต่ำ 13 ปีตามนโยบาย Meta ทั่วโลก) ค่า Default คือ 18-65+ สำหรับ Campaign Objective ส่วนใหญ่ แต่บางหมวดสินค้า (แอลกอฮอล์, การเงิน, สินค้าสำหรับผู้ใหญ่) ระบบจะบังคับขั้นต่ำที่สูงกว่า และไม่สามารถปรับลดได้แม้เราต้องการ

ข้อควรระวังคือการตั้งช่วงอายุแคบเกินไปโดยไม่มีข้อมูลรองรับ เช่น ตั้ง 25-34 เพราะ "คิดว่า" กลุ่มนี้คือลูกค้าหลัก โดยไม่เคยเปิด Breakdown by Age ดูข้อมูลจริงจากแคมเปญก่อนหน้าเลย วิธีที่ถูกต้องคือเริ่มด้วยช่วงกว้าง (เช่น 18-65+) ในช่วง Testing แรก แล้วค่อยใช้ Breakdown by Age (Ads Manager → Ad Set/Ad → Breakdown → By Delivery → Age) มาสร้าง Persona ที่มีข้อมูลรองรับจริง

### Gender: ตัวเลือกและข้อจำกัดนโยบาย

Gender มี 3 ตัวเลือก คือ All, Men, Women ธุรกิจที่มีสินค้าเฉพาะเพศชัดเจน (เสื้อผ้าใน, เครื่องสำอางเฉพาะทาง) ใช้ตัวเลือกนี้ได้ตรงไปตรงมา แต่ต้องระวังหมวด **Special Ad Category** (ที่เรียนใน Part 020) เช่น สินค้าหมวด Employment/Credit/Housing จะถูกบังคับให้ตั้ง Gender เป็น All เท่านั้น ไม่สามารถเจาะเพศได้ตามกฎหมายป้องกันการเลือกปฏิบัติ

### Language: เมื่อไหร่ต้องใช้

Language เป็นฟิลด์ที่มักถูกมองข้ามเพราะ Location ก็บอกพื้นที่อยู่แล้ว แต่ Language มีประโยชน์มากในสถานการณ์เฉพาะ เช่น ธุรกิจในกรุงเทพฯ ที่ต้องการเจาะกลุ่มคนต่างชาติที่พำนักอยู่ (Expat) โดยตั้ง Location เป็นกรุงเทพฯ แต่ Language เป็น English (UK)/English (US) เพื่อกรองเฉพาะคนที่ใช้ Facebook ภาษาอังกฤษ ซึ่งมักเป็นกลุ่ม Expat หรือคนไทยที่ใช้ภาษาอังกฤษเป็นหลักในชีวิตดิจิทัล เหมาะกับธุรกิจ International School, คลินิกเฉพาะทาง, Co-working Space ที่มีลูกค้าต่างชาติ

### ตารางสรุป: เลือก Location Option ให้ตรงกับประเภทธุรกิจ

| ประเภทธุรกิจ | Location Option ที่แนะนำ | เหตุผล |
|---|---|---|
| ร้านอาหาร/ร้านกาแฟหน้าร้าน | Everyone in this location (Radius 3-8 กม.) | ต้องการทั้งคนอยู่อาศัยและคนผ่านไปมาที่อาจแวะ |
| คลินิกความงาม/ทันตกรรม | People who live in this location | ต้องการลูกค้าประจำที่กลับมารักษาต่อเนื่อง ไม่ใช่นักท่องเที่ยว |
| ธุรกิจ Delivery อาหาร | Everyone in this location (Radius ตามพื้นที่ส่งจริง) | คนที่ "อยู่ในพื้นที่ขณะนั้น" คือกลุ่มที่สั่งได้จริง ไม่จำเป็นต้องอยู่อาศัยประจำ |
| โรงแรม/ที่พักตากอากาศ | People traveling in this location (ยิงในเมืองต้นทางของนักท่องเที่ยว ไม่ใช่ปลายทาง) | ต้องเจาะกลุ่มที่กำลังวางแผนเดินทาง ไม่ใช่คนที่อยู่ในพื้นที่ปลายทางอยู่แล้ว |
| ร้านขายของฝาก/สนามบิน | People recently in this location + Traveling | จับกลุ่มที่เพิ่งอยู่ในพื้นที่ท่องเที่ยวช่วงสั้น ๆ ก่อนเดินทางกลับ |
| E-commerce ส่งทั่วประเทศ | Everyone in this location (ทั้งประเทศ ไม่ต้อง Radius) | ไม่มีข้อจำกัดพื้นที่บริการ ควรปล่อยกว้างระดับประเทศ |
| ธุรกิจ B2B ขายทั่วประเทศแต่มี Sales Team ประจำภาค | แยก Ad Set ตามภาคที่ Sales Team ดูแล | ต้องการให้ Lead แต่ละภาคไปตกกับ Sales ที่ดูแลพื้นที่นั้นถูกคน |

### ตัวอย่างจริงจากหน้างาน

ธุรกิจ International Kindergarten แห่งหนึ่งในกรุงเทพฯ ยิงแอดเจาะกลุ่มผู้ปกครองไทยทั่วไปมานาน 6 เดือน CPA อยู่ที่ 450 บาทต่อ Lead แต่ Lead ส่วนใหญ่ไม่ได้คุณภาพเพราะราคาเทอมสูงเกินกำลังของกลุ่มที่ยิงถึง หลังปรับ Location เป็นเขตที่มีคอนโดหรูและหมู่บ้านราคาสูงเฉพาะ (Sukhumvit, Thonglor, Ekkamai) และเพิ่ม Language เป็น English ควบคู่กับ Thai จับกลุ่ม Expat และคนไทยที่พูดอังกฤษ ผล CPA ลดลงเหลือ 280 บาท และ Close Rate จาก Lead เพิ่มขึ้น 3 เท่า เพราะกลุ่มที่ได้ตรงกับกำลังซื้อจริงมากขึ้น

### ข้อผิดพลาดที่พบบ่อยโดยรวมของ Step นี้

1. มองว่า Building Block พื้นฐานเหล่านี้ "ไม่สำคัญเท่า Interest" ทั้งที่จริง Location/Age/Gender มักกระทบผลลัพธ์มากกว่า Interest เสียอีก เพราะเป็น Hard Constraint
2. ไม่เคยทดสอบตัวเลือก Location แบบต่าง ๆ (Everyone/Live/Recently/Traveling) ทั้งที่แต่ละแบบให้กลุ่มคนที่ต่างกันมาก
3. ตั้ง Age แคบตามสมมติฐานที่ไม่มีข้อมูลรองรับ
4. ลืมตรวจว่าธุรกิจตัวเองอยู่ใน Special Ad Category หรือไม่ ทำให้ตั้งค่า Gender/Age ที่จะถูกระบบ Reject ในภายหลัง

---

## Step 452: Detailed Targeting — Interests ทำงานอย่างไรในปี 2026

### ที่มาของข้อมูล Interest

Interest ที่ Meta ใช้ในการ Targeting มาจากการรวบรวมสัญญาณหลายชั้น:

1. **Explicit Signal** — สิ่งที่ผู้ใช้กด Like, Follow Page, เข้าร่วม Group, หรือใส่ไว้ใน Profile (เช่น งานอดิเรก, สถานที่ทำงาน)
2. **Behavioral Signal** — สิ่งที่ผู้ใช้ Engage ด้วยบน Facebook/Instagram เช่น หยุดดูวิดีโอประเภทไหนนาน, กด Save โพสต์แบบไหน, คลิกโฆษณาประเภทไหนบ่อย
3. **Off-platform Signal (ลดลงมากหลัง iOS14)** — ข้อมูลจาก Pixel ของเว็บไซต์อื่นที่ติดตั้ง Facebook Pixel ซึ่งเคยเป็นแหล่งข้อมูล Interest ที่แข็งแรงมากในอดีต แต่ตั้งแต่ Apple บังคับ App Tracking Transparency (ATT) ปี 2021 เป็นต้นมา สัดส่วนนี้ลดลงเรื่อย ๆ เพราะผู้ใช้ iOS จำนวนมากปฏิเสธการ Track

### ทำไม Interest ในปี 2026 "อ่อนแรง" กว่าเมื่อก่อน

ผลจาก ATT ทำให้ Meta เก็บ Off-platform Signal ได้น้อยลงมาก Interest ที่เคยแม่นยำสูง (เพราะอิงพฤติกรรมการซื้อของจริงจากเว็บนอก) ตอนนี้ต้องพึ่งพา On-platform Signal เป็นหลัก ซึ่งมีข้อจำกัดคือ:

- คนกด Like Page แบรนด์หนึ่งเมื่อ 5 ปีก่อน แล้วไม่ได้ Engage อะไรกับแบรนด์นั้นอีกเลย Interest นั้นอาจยังติดอยู่ใน Profile แต่ไม่สะท้อนพฤติกรรมปัจจุบัน
- Interest บางตัวกว้างเกินไปเพราะรวมคนที่ "เคยดูวิดีโอเกี่ยวกับเรื่องนั้นผ่าน ๆ" เข้ามาด้วย ไม่ได้กรองว่าเป็นความสนใจจริงจังหรือดูผ่านตาเฉย ๆ
- Interest ประเภท Lifestyle กว้าง (เช่น "Shopping", "Online Shopping") มักมีขนาดหลักสิบล้านคนในไทย ซึ่งกว้างเกินกว่าจะใช้เป็นตัวกรองที่มีความหมายจริง

### วิธีค้นหาและตรวจสอบ Interest ใน Ads Manager

ไปที่ Ads Manager → Ad Set → Audience Controls → Detailed Targeting → พิมพ์คำในกล่องค้นหา ระบบจะแสดง:

- **ชื่อ Interest/Behavior/Demographic**
- **หมวดหมู่** (Interest, Behavior, Demographic, หรือ Employer/Job Title สำหรับบาง Interest)
- **Audience Size** — จำนวนคนโดยประมาณที่มี Interest นี้ (ตัวเลขนี้เป็น Potential Reach ไม่ใช่ตัวเลขที่จะได้ Impression จริงเท่านี้)

เทคนิคที่มืออาชีพใช้คือคลิกที่ Interest ที่สนใจแล้วดู "Suggestions" ที่ระบบแนะนำ Interest ที่เกี่ยวข้อง (คนที่มี Interest A มักมี Interest B ด้วย) เป็นวิธีค้นหา Interest ใหม่ที่ไม่เคยคิดถึง

### หมวดของ Interest ที่ควรรู้จัก

| หมวด | ตัวอย่าง | ลักษณะเด่น |
|---|---|---|
| Business & Industry | Small Business, Digital Marketing, Entrepreneurship | เหมาะกับ B2B, คอร์สธุรกิจ |
| Entertainment | Movies, Music, TV Shows, Games | กว้างมาก มักใช้ประกอบ ไม่ใช้เดี่ยว |
| Family & Relationships | Parenting, Weddings, Dating | เหมาะกับสินค้าเด็ก/แม่และเด็ก, ธุรกิจงานแต่ง |
| Fitness & Wellness | Physical Fitness, Yoga, Bodybuilding | เหมาะกับฟิตเนส, อาหารเสริม, เสื้อผ้ากีฬา |
| Food & Drink | Cooking, Restaurants, Wine | เหมาะกับร้านอาหาร, สินค้าอาหาร |
| Hobbies & Activities | Photography, Gardening, Pets | เจาะกลุ่มเฉพาะได้ดี |
| Shopping & Fashion | Fashion, Luxury Goods, Online Shopping | กว้าง ควรจับคู่กับ Interest แคบอื่น |
| Sports & Outdoors | Running, Golf, Camping | เหมาะกับสินค้ากีฬาเฉพาะประเภท |
| Technology | Smartphones, Consumer Electronics | เหมาะกับ Gadget, App |

### กรณีศึกษาการเลือก Interest ที่แม่นยำ

แบรนด์อาหารเสริมสำหรับนักวิ่งมาราธอนต้องการเจาะกลุ่มนักวิ่งจริงจัง (ไม่ใช่คนที่แค่สนใจ Fitness ทั่วไป) ทีมทดสอบ 3 แนวทาง:

1. Interest กว้าง: "Physical Fitness" (ขนาด ~15 ล้านคนในไทย) → CTR 0.8%, CPA 380 บาท
2. Interest เฉพาะ: "Marathon" + "Running" (ขนาด ~1.2 ล้านคนในไทย) → CTR 1.9%, CPA 210 บาท
3. Interest เฉพาะ + Behavior: "Marathon" + "Running" + Behavior "Engaged Shoppers" → CTR 2.3%, CPA 175 บาท

บทเรียนคือ Interest ที่แคบและเฉพาะเจาะจงตรงกับ Persona จริง (นักวิ่งมาราธอน ไม่ใช่แค่คนสนใจออกกำลังกายทั่วไป) ให้ผลลัพธ์ที่ดีกว่า Interest กว้างมาก และการผสม Behavior เข้าไปช่วยกรองคุณภาพเพิ่มอีกขั้น

### ข้อผิดพลาดที่พบบ่อย

1. เลือก Interest กว้างเกินไป (Shopping, Beauty, Fashion) โดยคิดว่ายิ่งกว้างยิ่งได้ Reach มาก แต่ไม่ได้ตรงกับ Persona จริง
2. ไม่ตรวจสอบ Audience Size ของ Interest ก่อนใช้ ทำให้ไม่รู้ว่า Interest นั้นแคบหรือกว้างแค่ไหนเทียบกับประชากรทั้งหมด
3. เชื่อว่า Interest สะท้อนพฤติกรรมปัจจุบัน 100% ทั้งที่จริงอาจเป็นข้อมูลเก่าหลายปี
4. ไม่เคยใช้ฟีเจอร์ Suggestions เพื่อหา Interest ใหม่ที่อาจตรงกับ Persona มากกว่า Interest ที่คิดขึ้นเองจากหัว
5. ใช้ Interest เดียวเดี่ยว ๆ โดยไม่ทดสอบผสมกับ Behavior หรือ Demographic เพื่อเพิ่มความแม่นยำ

---

## Step 453: Detailed Targeting — Behaviors และ Demographics แยกประเภท

### Behaviors คืออะไร ต่างจาก Interest อย่างไร

Interest สะท้อน "สิ่งที่คนสนใจ" ส่วน Behavior สะท้อน "สิ่งที่คนทำ" บนแพลตฟอร์มและอุปกรณ์ ตัวอย่างหมวด Behavior ที่ Meta เปิดให้ใช้:

| หมวด Behavior | ตัวอย่าง | ใช้เมื่อไหร่ |
|---|---|---|
| Purchase Behavior | Engaged Shoppers, Premium Brand Affinity | เจาะกลุ่มที่มีพฤติกรรมซื้อของออนไลน์บ่อย |
| Digital Activities | Facebook Page Admin, Small Business Owners | เหมาะกับ B2B ที่ขายเครื่องมือให้ธุรกิจ |
| Mobile Device User | iOS Devices, Android Devices, Device Price | เจาะกลุ่มตามงบซื้อมือถือ (สัมพันธ์กับกำลังซื้อ) |
| Travel | Frequent Travelers, Returned from Trip 1 Week Ago | เหมาะกับธุรกิจท่องเที่ยว, ประกันเดินทาง |
| Anniversary | Upcoming Birthday, Anniversary within 30 Days | เหมาะกับธุรกิจของขวัญ |

**Engaged Shoppers** เป็น Behavior ที่ใช้บ่อยที่สุดในกลุ่ม E-commerce เพราะจับกลุ่มคนที่กดคลิก Shop Now หรือซื้อของผ่านโฆษณา Facebook ในช่วง 7 วันที่ผ่านมา เป็นสัญญาณว่าเป็นคนที่ "พร้อมซื้อออนไลน์" จริง ไม่ใช่แค่สนใจดูเฉย ๆ

**Mobile Device User** แบบแยกตามราคาเครื่อง (High-end Mobile Devices) เป็นเทคนิคที่ใช้ประเมินกำลังซื้อทางอ้อม เหมาะกับสินค้า Premium/Luxury ที่ต้องการกรองกลุ่มที่มีกำลังซื้อสูงในเบื้องต้น แต่ต้องระวังว่าไม่ใช่ตัวชี้วัดที่แม่นยำ 100% เพราะบางคนใช้เครื่องรุ่นเก่าทั้งที่มีกำลังซื้อสูง

### Demographics คืออะไร

Demographic ในบริบทของ Detailed Targeting (แยกจาก Age/Gender ที่เป็น Core Field) หมายถึงข้อมูลเชิงสถานะชีวิตที่ละเอียดกว่า เช่น:

| หมวด Demographic | ตัวอย่าง |
|---|---|
| Education | Education Level, Field of Study, Undergrad/Grad School |
| Financial | Income Level (บางตลาด เช่น สหรัฐฯ), Business Owner |
| Life Events | Newly Engaged, Newly Married, New Job, Recently Moved, New Parent |
| Parents | Parents (All), Parents of Toddlers, Parents of Pre-teens |
| Relationship | Single, In a Relationship, Married, Engaged |
| Work | Employer, Job Title, Industry |

**Life Events** เป็นหมวดที่ทรงพลังมากเพราะจับ "ช่วงเวลาเปลี่ยนผ่านของชีวิต" ซึ่งมักมาพร้อมพฤติกรรมการใช้จ่ายที่เปลี่ยนไปทันที เช่น "New Parent" เหมาะกับสินค้าเด็ก/แม่และเด็ก, "Recently Moved" เหมาะกับสินค้าเฟอร์นิเจอร์/ของแต่งบ้าน, "Newly Engaged" เหมาะกับธุรกิจงานแต่ง/ตัดสูท/ช่างภาพ

**Job Title/Employer** เหมาะกับ B2B โดยเฉพาะ เช่น ธุรกิจขาย Software HR สามารถ Targeting Job Title "HR Manager", "Human Resources Director" ได้ตรงจุด แต่ข้อจำกัดคือขนาด Audience มักเล็กมากในตลาดไทย (บางครั้งต่ำกว่า 50,000 คน) ต้องระวังเรื่อง Audience Size ขั้นต่ำ (ดู Step 456)

### ตัวอย่างการผสม Behavior + Demographic ที่ได้ผลจริง

ธุรกิจขายคอร์สเรียนออนไลน์สำหรับผู้บริหารระดับกลาง ผสม Demographic "Job Title: Manager, Director" + Behavior "Small Business Owners" + Interest "Leadership" ได้ Audience ขนาด ~180,000 คน แคบกว่าการยิงกว้างมาก แต่ CPA ต่ำกว่าถึง 40% เพราะกลุ่มที่ได้ตรงกับ Buyer Persona (ผู้บริหารที่มีอำนาจตัดสินใจซื้อคอร์สด้วยตัวเอง) มากกว่าการยิงกว้างที่ปนคนทั่วไปที่ไม่มีอำนาจซื้อ

### ข้อผิดพลาดที่พบบ่อย

1. ใช้ Interest อย่างเดียวโดยไม่รู้จัก Behavior/Demographic ทั้งที่บางครั้ง Behavior ให้สัญญาณพฤติกรรมจริงที่แม่นยำกว่า Interest มาก
2. ใช้ Job Title Targeting กับตลาดไทยโดยไม่ตรวจสอบ Audience Size ก่อน ทำให้ Ad Set เล็กเกินจนติด Learning Phase นาน
3. เชื่อว่า Device Price สะท้อนกำลังซื้อได้แม่นยำ 100% โดยไม่ทดสอบเปรียบเทียบกับกลุ่มอื่น
4. มองข้าม Life Events ทั้งที่เป็นหมวดที่ทรงพลังมากสำหรับสินค้าที่เกี่ยวกับช่วงเปลี่ยนผ่านชีวิต
5. ไม่อัปเดตรายการ Behavior/Demographic ที่มีอยู่ — Meta เพิ่ม/ลด Option เหล่านี้เป็นระยะ ควรเข้าไปสำรวจกล่องค้นหาใหม่ทุก 2-3 เดือน

---

### เครื่องมือที่เคยใช้คู่กับ Interest แต่ปิดตัวไปแล้ว: Audience Insights

นักยิงแอดที่เรียนมาจากคอร์สหรือบทความเก่าอาจเคยเห็นชื่อเครื่องมือ **Audience Insights** ซึ่งเคยเป็นเครื่องมือสำคัญมากสำหรับการสำรวจว่า Interest หนึ่งมีลักษณะ Demographic อย่างไร (อายุ เพศ Page ที่ Like บ่อย ตำแหน่งที่อยู่) แต่ Meta ได้ปิดการใช้งาน Audience Insights แบบเดิมไปแล้วตั้งแต่ปี 2023 เป็นต้นมา เหตุผลหลักคือข้อมูลที่ Audience Insights แสดงมีความละเอียดสูงเกินไปในมุมความเป็นส่วนตัว และซ้ำซ้อนกับทิศทางที่ Meta ต้องการผลักดันไปสู่ AI-Powered Targeting อยู่แล้ว

สิ่งที่ใช้ทดแทนได้ในทางปฏิบัติปี 2026:

1. **Breakdown by Age/Gender/Region ในระดับ Ad Set/Ad จริง** — ข้อมูลจากแคมเปญที่รันจริงแม่นยำกว่าข้อมูลเชิงสถิติทั่วไปของ Audience Insights เสียอีก เพราะสะท้อนพฤติกรรมจริงที่เกิดกับธุรกิจเรา ไม่ใช่ค่าเฉลี่ยของคนทั้งหมดที่มี Interest นั้น
2. **Meta Business Suite Insights (สำหรับ Page)** — ดูข้อมูล Demographic ของคนที่ติดตาม Engage กับ Page อยู่แล้ว ช่วยยืนยันว่า Persona ที่ตั้งไว้ตรงกับผู้ติดตามจริงหรือไม่
3. **การพิมพ์คำค้นหาใน Detailed Targeting แล้วดู Suggestions ที่เกี่ยวข้อง** — เป็นวิธีสำรวจ Interest ที่ใกล้เคียงกันแบบง่าย ๆ แทนการดูภาพรวมเชิงสถิติแบบเดิม
4. **Meta Ad Library** (เรียนใน Part 003) — ดูว่าคู่แข่งในอุตสาหกรรมเดียวกันเน้นสื่อสารกับกลุ่มไหน เป็นการอนุมาน Persone ทางอ้อมจากพฤติกรรมตลาด

### ข้อผิดพลาดที่พบบ่อยเรื่องเครื่องมือที่เลิกใช้แล้ว

1. ค้นหาวิธีเปิด Audience Insights ตามบทความเก่าแล้วเสียเวลาเพราะเครื่องมือไม่มีอยู่แล้วในปี 2026
2. อ้างอิงตัวเลข Demographic จาก Audience Insights เวอร์ชันเก่าที่จำมาจากประสบการณ์เดิม ทั้งที่ข้อมูล Interest ปัจจุบันเปลี่ยนไปมากแล้ว
3. ไม่รู้จักวิธีทดแทนจึงข้ามการทำ Research ก่อนตั้ง Audience ไปเลย ทำให้ตั้ง Persona แบบเดาสุ่มไม่มีข้อมูลรองรับ

---

## Step 454: Interest Stacking — Logic AND/OR, Narrow Audience และ Broaden Audience

### หลักการ Logic พื้นฐานของ Detailed Targeting

เมื่อเพิ่ม Interest/Behavior/Demographic หลายตัวลงในกล่อง Detailed Targeting กล่องเดียวกัน ระบบจะใช้ Logic แบบ **OR** ระหว่างรายการทั้งหมดในกล่องนั้น หมายความว่าคนที่มี Interest A **หรือ** Interest B **หรือ** Interest C ก็จะถูกรวมเข้ามาทั้งหมด (Audience Size จะรวมกันแบบ Union ไม่ใช่ตัดกัน)

ตัวอย่าง: ใส่ "Yoga" + "Pilates" + "Running" ในกล่องเดียวกัน = คนที่สนใจ Yoga **หรือ** Pilates **หรือ** Running คนใดคนหนึ่งก็เข้าเงื่อนไขแล้ว

### การทำ AND Logic ด้วย "Narrow Audience"

ถ้าต้องการให้เป็น Logic แบบ **AND** (ต้องมีทั้ง A และ B) ต้องคลิก **"Narrow Further"** หรือ **"Narrow Audience"** (ปุ่มที่อยู่ใต้กล่อง Detailed Targeting กล่องแรก) เพื่อเปิดกล่องที่สอง แล้วใส่เงื่อนไขที่ต้องการให้ต้องเป็นจริง**ร่วมกับ**กล่องแรก

ตัวอย่าง: กล่องแรกใส่ "Yoga" OR "Pilates" กล่องที่สอง (หลังกด Narrow Further) ใส่ "Engaged Shoppers" = คนที่ (สนใจ Yoga หรือ Pilates) **และ** เป็น Engaged Shoppers ด้วย

สามารถกด Narrow Further ซ้ำได้หลายชั้น เพื่อสร้าง Logic ที่ซับซ้อนขึ้น เช่น (Yoga OR Pilates) AND (Engaged Shoppers) AND (Age สูงกว่าที่ตั้งไว้ใน Core ก็ยังเป็น AND กับทั้งหมดอยู่แล้วโดยธรรมชาติ)

### ตารางสรุป Logic ที่ต้องจำ

| การกระทำ | Logic ที่ได้ | ผลต่อ Audience Size |
|---|---|---|
| ใส่หลาย Interest ในกล่องเดียวกัน | OR (รวมกัน) | ขนาดใหญ่ขึ้น (Union) |
| กด Narrow Further แล้วใส่เงื่อนไขใหม่ | AND (ตัดกัน) | ขนาดเล็กลง (Intersection) |
| กด Exclude แล้วใส่เงื่อนไข | NOT | ขนาดเล็กลง (ตัดคนกลุ่มนั้นออก) |

### Broaden Audience: ตัวเลือกที่ตรงข้ามกับ Narrow

เมื่อ Detailed Targeting แคบเกินไป Meta มักแสดง Suggestion ให้ **"Broaden your audience for more reach"** ซึ่งจะเสนอให้ลบเงื่อนไขบางตัวออก หรือเสนอ Interest ที่เกี่ยวข้องเพิ่มเข้ามาแบบ OR เพื่อขยาย Pool ให้กว้างขึ้น ควรใช้ Suggestion นี้อย่างมีวิจารณญาณ ไม่ใช่กดตามทุกครั้งที่ระบบเสนอ เพราะบางครั้งความแคบคือสิ่งที่ตั้งใจออกแบบไว้แล้ว (เช่น กรณี B2B เฉพาะทาง)

### กรณีศึกษาการใช้ Narrow Audience อย่างมีชั้นเชิง

ธุรกิจขายคอร์สลงทุนหุ้นสำหรับมือใหม่ ต้องการเจาะกลุ่มที่ (1) สนใจการลงทุน **และ** (2) มีพฤติกรรมใช้จ่ายออนไลน์ **และ** (3) อยู่ในช่วงอายุทำงานที่มีเงินเก็บ

การตั้งค่า:
- กล่องที่ 1 (OR ภายในกล่อง): "Stock Market" OR "Investment" OR "Mutual Funds"
- Narrow Further กล่องที่ 2: "Engaged Shoppers" (Behavior)
- Core Audience: Age 28-50

ผลคือ Audience จาก Potential Reach เดิม 8.5 ล้านคน (ถ้าใส่แค่กล่องแรกอย่างเดียว) ลดลงเหลือ 640,000 คน หลัง Narrow ด้วย Behavior แต่ CPA ลดลงจาก 620 บาท เหลือ 340 บาทต่อ Lead เพราะกลุ่มที่ได้ตรงกับ Persona ที่มีทั้งความสนใจและกำลังซื้อจริง

### ข้อผิดพลาดที่พบบ่อย

1. ใส่ Interest จำนวนมากในกล่องเดียวกันโดยไม่รู้ว่าเป็น OR Logic ทำให้ Audience กว้างเกินคาด และไม่ตรงกับที่ตั้งใจ
2. ใช้ Narrow Further มากเกินไป (3-4 ชั้น) จนทำให้ Audience เล็กจนต่ำกว่าเกณฑ์ที่ระบบเรียนรู้ได้ดี
3. กด Broaden Audience ตามที่ระบบเสนอทุกครั้งโดยไม่พิจารณาว่าความแคบนั้นตั้งใจหรือไม่
4. ไม่ตรวจสอบ Potential Reach ก่อนและหลัง Narrow ทุกครั้ง ทำให้ไม่รู้ว่าการ Narrow แต่ละชั้นกระทบขนาดแค่ไหน
5. สลับสับสนระหว่าง Narrow Further (อยู่ในกล่อง Detailed Targeting) กับ Exclude (อยู่คนละกล่อง) ทำให้ตั้งค่าผิด Logic ไปเลย

---

## Step 455: Exclusion Targeting — Exclude Interest, Behavior, และ Custom Audience

### ทำไม Exclusion สำคัญไม่แพ้ Inclusion

การ Exclude ที่ถูกต้องช่วยสองเรื่องหลัก คือ (1) ป้องกันไม่ให้งบไปเสียกับคนที่ไม่ใช่กลุ่มเป้าหมายจริง และ (2) ป้องกัน Audience Overlap ระหว่าง Ad Set หลายตัวในบัญชีเดียวกัน (รายละเอียดเรื่อง Overlap อยู่ใน Step 459)

### ตำแหน่งตั้งค่า Exclusion

ไปที่ Ads Manager → Ad Set → Audience Controls → Detailed Targeting → คลิก **"Exclude"** (อยู่คู่กับปุ่ม Include ในกล่องเดียวกัน หรือในบางเวอร์ชัน UI จะอยู่เป็นแถบแยกด้านล่าง "Exclude People") จากนั้นพิมพ์ Interest, Behavior, Demographic, หรือ Custom Audience ที่ต้องการ Exclude

### ประเภทของการ Exclude ที่ใช้บ่อยที่สุด

1. **Exclude Interest ที่ไม่เกี่ยวข้องหรือให้สัญญาณผิด** เช่น ธุรกิจขายสินค้า Premium อาจ Exclude Interest "Coupons", "Discount Shopping" เพื่อกันกลุ่มที่ล่าแต่ของลดราคาไม่ซื้อราคาปกติ
2. **Exclude Behavior ที่ขัดกับ Persona** เช่น ธุรกิจ B2B Exclude "Small Business Owners" ถ้าสินค้าออกแบบมาสำหรับองค์กรขนาดใหญ่เท่านั้น
3. **Exclude Custom Audience ของลูกค้าเดิม** — Exclude รายชื่อคนที่ซื้อไปแล้วออกจากแคมเปญ Prospecting เพื่อไม่ให้งบไปเลี้ยงคนที่ Convert แล้วซ้ำ ๆ (ต้องมี Custom Audience นี้อยู่ก่อน ซึ่งจะเรียนละเอียดใน Part 047)
4. **Exclude Employee/Internal List** — ป้องกันพนักงานหรือทีมงานเห็นโฆษณาและกดจนปนข้อมูล Conversion เทียม

### ตารางโครงสร้าง Exclusion มาตรฐานที่แนะนำ

| ประเภทแคมเปญ | Include | Exclude ที่ควรมี |
|---|---|---|
| Prospecting ใหม่ | Interest/Behavior ตาม Persona | Custom Audience: Purchasers 180 วัน, Existing Customer List, Employee List |
| Prospecting (ทดสอบ Interest ต่างกันหลาย Ad Set) | Interest แตกต่างกันแต่ละ Ad Set | เหมือนข้อบน + Exclude Ad Set อื่นในแคมเปญเดียวกัน (ผ่าน Custom Audience ของ Engager กลุ่มนั้น ถ้าจำเป็นต้องกันชนกันจริง ๆ) |
| Warm Retargeting | Custom Audience: Website Visitors/Add to Cart | Exclude Purchasers (Event ที่เพิ่งเกิดในช่วงเวลาที่กำหนด) |

### ข้อผิดพลาดที่พบบ่อย

1. ไม่ Exclude ลูกค้าเดิมออกจากแคมเปญ Prospecting เลย ทำให้เกิดการยิงซ้ำใส่คนที่ซื้อแล้วโดยไม่จำเป็น สิ้นเปลืองงบ
2. Exclude Interest ที่กว้างเกินไปจนกระทบ Reach โดยไม่ได้ประโยชน์ชัดเจน
3. ลืมอัปเดต Exclusion List เป็นระยะ (เช่น Custom Audience "Purchasers_30d" ที่ควร Refresh Window ให้ตรงกับ Purchase Cycle ของสินค้า)
4. Exclude ผิดฝั่ง — บางคนเผลอกด Exclude ในกล่อง Include ทำให้ Logic สลับกันโดยไม่รู้ตัว ต้องตรวจสอบหน้า Review ก่อน Publish เสมอ
5. ไม่รู้ว่า Exclude Interest ในยุค Advantage+ Audience มีน้ำหนักน้อยกว่า Exclude Custom Audience มาก ควรให้ความสำคัญกับ Custom Audience Exclusion เป็นอันดับแรก

---

## Step 456: Audience Size Guidance — อ่าน Potential Reach และ Estimated Results

### Potential Reach คืออะไร ไม่ใช่อะไร

Potential Reach คือตัวเลขประมาณจำนวนคนที่ตรงกับเงื่อนไข Targeting ทั้งหมดที่ตั้งไว้ **ไม่ใช่**จำนวนคนที่จะเห็นโฆษณาจริง และไม่ใช่ตัวชี้วัดคุณภาพของ Audience โดยตรง เป็นเพียงตัวเลขบอกขนาด Pool เท่านั้น

ตำแหน่งดูอยู่ทางขวาของหน้า Ad Set ในกล่อง **Audience Definition** จะแสดงแถบวัด "Specific" ถึง "Broad" พร้อมตัวเลข Potential Reach ประมาณ

### แนวทางประเมินขนาดที่เหมาะสม (ตาม Objective และงบประมาณ)

ไม่มีตัวเลขตายตัวที่ใช้ได้ทุกกรณี แต่มีแนวทางที่ใช้ได้จริงดังนี้:

| ระดับ Potential Reach (ประเทศไทย) | ลักษณะ | ความเสี่ยง |
|---|---|---|
| ต่ำกว่า 100,000 คน | แคบมาก | เสี่ยง Learning Phase ไม่จบ, CPM พุ่งเร็วเพราะ Pool หมด, Frequency สูงเร็ว |
| 100,000 – 500,000 คน | แคบ เหมาะกับ B2B/Niche | ต้องมีงบสอดคล้อง ไม่ใหญ่เกินความจำเป็น |
| 500,000 – 3,000,000 คน | กลาง เหมาะกับสินค้าทั่วไปที่มี Persona ชัด | จุดที่สมดุลสำหรับ SME ส่วนใหญ่ |
| 3,000,000 – 10,000,000 คน | กว้าง เหมาะกับ Mass Market | ต้องมี Creative/Data Signal ที่ดีพอให้ AI คัดกรอง |
| เกิน 10,000,000 คน | กว้างมาก มักใกล้เคียงประชากรทั้งประเทศ | เหมาะกับ Awareness Campaign หรือปล่อยให้ Advantage+ Audience ทำงานเต็มที่ |

### สัญญาณที่บอกว่า "แคบเกินไป"

- Ad Set ค้างอยู่ใน Learning Phase นานเกิน 7 วันโดยไม่ผ่าน (ได้ Conversion ไม่ถึง 50 ครั้งต่อสัปดาห์)
- Frequency พุ่งเกิน 3-4 ภายในสัปดาห์แรก ทั้งที่งบยังไม่มาก
- CPM เพิ่มขึ้นต่อเนื่องแบบไม่มีเหตุผลด้านการแข่งขันจากภายนอก
- Ads Manager แสดง Warning "Audience size may limit ad set delivery"

### สัญญาณที่บอกว่า "กว้างเกินไปโดยไม่มีคุณภาพรองรับ"

- CTR ต่ำกว่าค่าเฉลี่ยอุตสาหกรรมอย่างมีนัยสำคัญ ทั้งที่ Creative ทดสอบแล้วว่าดีในบริบทอื่น
- CPA สูงแบบไม่สม่ำเสมอ วันดีวันร้ายสวิงมาก แสดงว่าระบบยังหา Pattern ที่ชัดเจนไม่ได้เพราะกลุ่มปนกันเกินไป
- Breakdown by Age/Gender/Region แสดงว่า Conversion กระจายเบาบางไปทั่วโดยไม่มี Segment ไหนเด่นชัด

### วิธีตัดสินใจแบบเป็นระบบ

```
เริ่มต้น: ตั้ง Persona สมมติฐาน + ประมาณ Potential Reach
 ├─ Reach < 100,000 → พิจารณา Broaden Interest หรือรวมหลาย Interest แบบ OR
 ├─ Reach 100,000-3,000,000 → เหมาะกับ Testing เริ่มต้น ตั้งงบ 3-5x เป้า CPA/วัน
 └─ Reach > 5,000,000 → พิจารณาว่าจำเป็นต้องแคบลงหรือไม่ 
           ถ้า Data Signal ดีอยู่แล้ว ปล่อยกว้างและให้ Advantage+ Audience ช่วยคัดกรอง
```

### ข้อผิดพลาดที่พบบ่อย

1. ตั้งเป้าให้ Potential Reach ตัวเลขหนึ่งตายตัว (เช่น "ต้อง 1 ล้านคนพอดี") โดยไม่พิจารณางบประมาณและ Objective ประกอบ
2. เข้าใจผิดว่า Potential Reach สูง = ผลลัพธ์ดี ทั้งที่เป็นแค่ขนาด Pool ไม่ใช่คุณภาพ
3. ไม่เชื่อม Potential Reach กับงบประมาณที่มี ทำให้ตั้ง Audience กว้างเกินกว่างบจะ Explore ได้ทัน หรือแคบเกินกว่าที่งบจะได้ Conversion พอในเวลาที่กำหนด
4. ตกใจกับ Warning "Audience size limit" ทันทีโดยไม่พิจารณาบริบท บางครั้ง Audience แคบเป็นสิ่งที่ตั้งใจไว้ (B2B เฉพาะทาง) และยอมรับ Learning Phase ที่ช้าลงได้

---

## Step 457: Saved Audiences — Workflow การสร้าง บันทึก และดูแลรักษา

### ทำไมต้อง Save Audience

Saved Audience ช่วยประหยัดเวลาเมื่อต้องสร้าง Ad Set หลายตัวที่ใช้ Targeting เดียวกัน ไม่ต้องพิมพ์ Interest/Location/Age ซ้ำทุกครั้ง และช่วยให้ทีมงานหลายคนใช้มาตรฐาน Audience เดียวกันได้ ลดความคลาดเคลื่อนจากการพิมพ์ผิดหรือเข้าใจ Persona ต่างกัน

### วิธีสร้าง Saved Audience แบบ Step-by-Step

1. ไปที่ **Meta Ads Manager → เมนูซ้าย/บนขวา (รูปแฮมเบอร์เกอร์) → All Tools → Audiences** (หรือเข้าจาก Ad Set โดยตรงตอนตั้งค่า Targeting)
2. คลิก **Create Audience → Saved Audience**
3. ตั้งชื่อ Audience ให้เป็นระบบ (ดู Naming Convention ด้านล่าง)
4. ใส่เงื่อนไข Location, Age, Gender, Language, Detailed Targeting, Connections (เช่น Exclude คนที่ Like Page ไปแล้ว), Custom Audience ตามต้องการ
5. คลิก **Create Audience**

### Naming Convention ที่แนะนำสำหรับ Saved Audience

รูปแบบที่ใช้งานได้จริงในทีม: `[ประเภท]_[Persona]_[Location]_[AgeRange]_[วันที่สร้าง]`

ตัวอย่าง: `CORE_FitnessWomen_BKK_25-40_20260315` หรือ `CORE_B2B-HRManager_Nationwide_ALL_20260315`

การตั้งชื่อแบบนี้ช่วยให้เมื่อเปิดรายการ Audience ยาว ๆ ในบัญชีที่มีหลายสิบ Audience ยังหาและเข้าใจได้เร็วว่าแต่ละตัวคืออะไร ไม่ต้องเปิดดูรายละเอียดทีละตัว

### การนำ Saved Audience ไปใช้ในการสร้าง Ad Set ใหม่

ตอนตั้งค่า Ad Set → Audience Controls → ถ้าอยู่ในโหมด Original Audience จะมีตัวเลือก **"Use Saved Audience"** ที่ดรอปดาวน์ด้านบนของส่วน Audience ให้เลือก Saved Audience ที่สร้างไว้ ระบบจะดึงเงื่อนไขทั้งหมดมาใส่อัตโนมัติ (สามารถแก้ไขเพิ่มเติมได้หลังเลือก โดยไม่กระทบ Saved Audience ต้นฉบับ เว้นแต่จะกด Save การเปลี่ยนแปลงกลับไปทับ)

### การดูแลรักษา Saved Audience ในระยะยาว

Saved Audience ไม่ได้ Refresh ข้อมูล Interest/Demographic เอง — มันคือ "Query" ที่บันทึกไว้ ทุกครั้งที่นำไปใช้ ระบบจะ Query ข้อมูลปัจจุบันใหม่เสมอ ดังนั้นสิ่งที่ต้องดูแลคือ:

1. **ลบ Saved Audience ที่ไม่ได้ใช้แล้ว** เป็นระยะ (ทุก 3-6 เดือน) เพื่อไม่ให้รายการรกและสร้างความสับสนให้ทีมใหม่
2. **ตรวจสอบว่า Interest ที่ใช้ยังมีอยู่ในระบบหรือไม่** — Meta อาจยกเลิก Interest บางตัวเป็นระยะ ถ้า Saved Audience อ้างอิง Interest ที่ถูกยกเลิก ควรอัปเดตใหม่
3. **แยก Saved Audience ตามวัตถุประสงค์ชัดเจน** ไม่ปนกันระหว่าง Audience สำหรับ Testing กับ Audience ที่พิสูจน์แล้วว่าใช้ Scale ได้จริง

### ข้อผิดพลาดที่พบบ่อย

1. สร้าง Saved Audience ไม่ตั้งชื่อให้เป็นระบบ ทำให้ทีมสับสนเมื่อบัญชีมี Audience สะสมหลายสิบตัว
2. คิดว่า Saved Audience คือ "รายชื่อคนที่บันทึกไว้ตายตัว" (สับสนกับ Custom Audience) ทั้งที่จริงมันคือเงื่อนไข Query ที่ประมวลผลใหม่ทุกครั้ง
3. ไม่ลบ Saved Audience เก่าที่ไม่ได้ใช้แล้ว ทำให้รายการรกจนหาของที่ต้องการยาก
4. แก้ไข Saved Audience ต้นฉบับโดยไม่รู้ตัวว่ากระทบ Ad Set อื่นที่อาจใช้ชื่อเดียวกันอยู่ (ในบางกรณี) จริง ๆ แล้ว Saved Audience ที่ถูกดึงไปใช้ในหลาย Ad Set แล้วจะไม่เชื่อมกันอัตโนมัติ แต่ควรระมัดระวังไม่ให้สับสนระหว่างตัวต้นฉบับกับตัวที่ถูกแก้ไขในแต่ละ Ad Set

---

## Step 458: เมื่อไหร่ Core Audience Targeting ยังสำคัญ เมื่อไหร่ควรให้ Advantage+ Audience ครองสนาม

### ทบทวนสั้น ๆ จาก Part 030

ใน Part 030 เราเรียนแล้วว่า Advantage+ Audience คือทิศทางหลักที่ Meta ผลักดันให้ใช้ เพราะ AI มักหาคนที่ Convert ได้ดีกว่าการเดา Interest ของมนุษย์ แต่นั่นไม่ได้แปลว่า Core Audience หมดความสำคัญไปเลย มีสถานการณ์เฉพาะที่ Core Audience (หรือการใส่ Suggestion ที่อ้างอิง Core Audience หนัก ๆ) ยังจำเป็น

### สถานการณ์ที่ Core Audience Targeting ยังสำคัญ

1. **บัญชีใหม่ที่ยังไม่มี Pixel Data สะสม** — AI ยังไม่มีสัญญาณ Conversion พอที่จะเรียนรู้ การใส่ Interest/Demographic ที่ตรงกับ Persona ช่วยให้มีจุดตั้งต้นที่ดีกว่าปล่อยกว้างแบบไม่มีอะไรช่วยเลย
2. **ธุรกิจ B2B ที่มีกลุ่มเป้าหมายแคบชัดเจนมาก** — เช่น ขาย Software ให้ตำแหน่งงานเฉพาะ Job Title/Industry Targeting ยังช่วยให้ระบบ Converge เร็วขึ้นเมื่อ Conversion Volume ต่ำ (Sales Cycle ยาว, Ticket Size สูง)
3. **สินค้าที่มีข้อจำกัดทางกฎหมายหรืออายุ** — ต้องตั้ง Age/Location ที่ Compliance บังคับ ไม่ใช่เพื่อ Performance
4. **ช่วง Market Research หา Persona ใหม่ที่ยังไม่มีข้อมูล** — การตั้ง Core Audience หลายชุดแบบ A/B เพื่อทดสอบว่ากลุ่มไหนตอบสนองดีที่สุด เป็นวิธี "ถามตลาด" ก่อนปล่อยให้ AI ทำงานแบบกว้างในภายหลัง
5. **ธุรกิจที่มีสินค้าหลากหลายกลุ่มลูกค้าในเพจเดียวกัน** — ต้องแยก Ad Set ตาม Persona ชัดเจนเพื่อให้ Creative ที่ตรงกลุ่มไปเจอกลุ่มที่ตรงจริง ไม่ปนกัน

### สถานการณ์ที่ควรให้ Advantage+ Audience ครองสนาม

1. Data Signal แข็งแรงแล้ว (EMQ 7+, Conversion สม่ำเสมอต่อเนื่อง)
2. สินค้า/บริการมีฐานลูกค้ากว้าง ไม่เฉพาะกลุ่มมาก
3. งบประมาณสูงพอให้ AI Explore ได้จริง
4. ต้องการหา Segment ใหม่ที่ยังไม่รู้จัก (ให้ AI ช่วยทำ Market Research แทน)

### แนวทางแบบ Hybrid ที่ใช้ได้จริงในทีมมืออาชีพ

หลายทีมไม่ได้เลือกสุดทางไปด้านใดด้านหนึ่ง แต่ใช้โครงสร้างผสม เช่น สร้าง Ad Set 2-3 ตัวในแคมเปญเดียวกันแบบ ABO (Ad Set Budget Optimization ที่จะเรียนใน Part 059):

- Ad Set 1: Advantage+ Audience ปล่อยกว้างเต็มที่ (งบ 50% ของแคมเปญ)
- Ad Set 2: Core Audience แบบ Interest เฉพาะที่พิสูจน์แล้วว่าดี ใส่เป็น Suggestion ใน Advantage+ Audience (งบ 30%)
- Ad Set 3: Core Audience แบบทดสอบ Persona ใหม่ที่ยังไม่เคยลอง (งบ 20% สำหรับ Explore)

โครงสร้างนี้ทำให้ได้ทั้งความมั่นคงจาก Ad Set ที่พิสูจน์แล้ว และโอกาสค้นพบ Segment ใหม่ไปพร้อมกัน โดยไม่เสี่ยงทั้งหมดไปกับทางเดียว

### ข้อผิดพลาดที่พบบ่อย

1. เลือกสุดทางไปทางใดทางหนึ่ง (Core อย่างเดียว หรือ Advantage+ อย่างเดียว) โดยไม่พิจารณาบริบทธุรกิจตัวเอง
2. ใช้ Core Audience ต่อไปเพราะความเคยชิน ทั้งที่ Data Signal พร้อมมากพอที่จะปล่อยกว้างแล้ว
3. รีบปล่อยกว้างทั้งที่บัญชียังใหม่และ Data Signal ยังอ่อนมาก ทำให้ผลลัพธ์แรกแย่จนเสียความมั่นใจ
4. ไม่มีการทดสอบเปรียบเทียบ (Parallel Test แบบที่เรียนใน Part 030 Step 296) เพื่อหาสัดส่วนที่เหมาะกับบัญชีตัวเองจริง ๆ

---

## Step 459: ข้อผิดพลาดคลาสสิก — Audience Overlap ระหว่าง Ad Set

### Audience Overlap คืออะไร ทำไมเป็นปัญหา

เมื่อสร้างหลาย Ad Set ในแคมเปญเดียวกันหรือหลายแคมเปญพร้อมกัน โดยตั้ง Targeting ที่คล้ายกันหรือทับซ้อนกันมาก (เช่น Ad Set A ใช้ Interest "Yoga" และ Ad Set B ใช้ Interest "Fitness" ซึ่งมีคนที่สนใจทั้งสองอย่างจำนวนมาก) ทั้งสอง Ad Set จะเข้าประมูล (Auction) แข่งกับ**ตัวเอง**ในกลุ่มคนที่ทับซ้อนกัน ผลคือ:

- CPM สูงขึ้นโดยไม่จำเป็น เพราะ Advertiser คนเดียวกันแย่งประมูลกับตัวเอง
- ระบบ Machine Learning สับสนเพราะสัญญาณ Conversion จากกลุ่มคนเดียวกันไปกระจายอยู่ในหลาย Ad Set ทำให้แต่ละ Ad Set เรียนรู้ได้ช้าลง
- วัดผลเปรียบเทียบ Ad Set ผิดพลาด เพราะไม่รู้ว่าผลลัพธ์ที่ต่างกันมาจาก Targeting ที่ต่างกันจริง หรือมาจากการแข่งกันเองในกลุ่มที่ทับซ้อน

### วิธีตรวจสอบด้วย Audience Overlap Tool

ตำแหน่ง: Ads Manager → All Tools → Audiences → เลือก Audience 2 ตัวขึ้นไปที่ต้องการเทียบ (ต้องเป็น Saved Audience หรือ Custom Audience ที่บันทึกไว้ ไม่สามารถเทียบ Detailed Targeting แบบที่ยังไม่ Save ได้โดยตรง) → คลิกปุ่ม **"..."** (More Options) → **Show Audience Overlap**

ระบบจะแสดงเปอร์เซ็นต์การทับซ้อนระหว่าง Audience ที่เลือก เช่น "Audience B has 34% overlap with Audience A" หมายความว่า 34% ของคนใน Audience B ก็อยู่ใน Audience A ด้วย

### เกณฑ์การตัดสินใจเมื่อพบ Overlap

| % Overlap | การตัดสินใจ |
|---|---|
| ต่ำกว่า 20% | ยอมรับได้ ไม่ต้องแก้ไข |
| 20-40% | เฝ้าระวัง พิจารณา Exclude หนึ่ง Ad Set ออกจากอีกตัว หากทั้งสองมีงบสูง |
| สูงกว่า 40% | ควรแก้ไข โดย Exclude Ad Set หนึ่งออกจากอีกตัว หรือรวม Ad Set เป็นตัวเดียวแล้วปล่อยให้ CBO/ABO จัดการงบเอง |

### วิธีแก้ Overlap ที่ใช้ได้จริง

1. **รวม Ad Set ที่ Overlap สูงเป็นตัวเดียว** — ถ้า Persona จริง ๆ ใกล้เคียงกันมาก ไม่มีเหตุผลต้องแยก ให้รวมเป็น Ad Set เดียวแล้วปล่อยให้ระบบ Optimize เอง
2. **Exclude Custom Audience ของ Ad Set หนึ่งออกจากอีกตัว** — สร้าง Custom Audience จาก Engager ของ Ad Set A แล้ว Exclude ออกจาก Ad Set B (ใช้เมื่อมีเหตุผลจำเป็นต้องแยก Ad Set จริง ๆ เช่น ทดสอบ Creative ต่างกันกับ Persona เดียวกัน)
3. **ปรับ Targeting ให้แยกจากกันชัดเจนขึ้น** — เช่น แยกตาม Age Range ที่ไม่ทับซ้อนกัน หรือแยกตาม Location ที่ต่างกันจริง

### ตัวอย่าง Overlap Matrix เต็มรูปแบบจากบัญชีจริง

เพื่อให้เห็นภาพว่าการตรวจ Overlap แบบเป็นระบบทำอย่างไรเมื่อมี Ad Set มากกว่า 2 ตัว ลองดูตัวอย่างบัญชีร้านเครื่องสำอางที่มี 5 Saved Audience ที่ทดสอบ Interest ต่างกัน:

| | AudA: Makeup | AudB: SkinCare | AudC: K-Beauty | AudD: Luxury Cosmetics | AudE: Engaged Shoppers |
|---|---|---|---|---|---|
| **AudA: Makeup** | — | 52% | 38% | 29% | 44% |
| **AudB: SkinCare** | 52% | — | 41% | 22% | 39% |
| **AudC: K-Beauty** | 38% | 41% | — | 18% | 33% |
| **AudD: Luxury Cosmetics** | 29% | 22% | 18% | — | 26% |
| **AudE: Engaged Shoppers** | 44% | 39% | 33% | 26% | — |

จากตารางนี้ คู่ที่ต้องแก้ไขก่อนคือ AudA-AudB (52% Overlap สูงสุด) และ AudA-AudE (44%) ทีมตัดสินใจ:

1. รวม AudA (Makeup) กับ AudB (SkinCare) เป็น Audience เดียวแบบ OR Logic เพราะ Overlap สูงมากและ Persona ก็คล้ายกันอยู่แล้ว (คนสนใจ Makeup ส่วนใหญ่สนใจ SkinCare ด้วย)
2. คง AudC (K-Beauty) และ AudD (Luxury Cosmetics) แยกกัน เพราะ Overlap กับตัวอื่นต่ำกว่า 40% ทั้งหมด และเป็น Persona ที่มีเหตุผลเฉพาะตัวชัดเจน (K-Beauty = กลุ่มตามเทรนด์เกาหลี, Luxury = กลุ่มกำลังซื้อสูง)
3. ไม่ใช้ AudE (Engaged Shoppers) เป็น Ad Set แยก แต่เปลี่ยนไปใส่เป็น Behavior เสริมแบบ Narrow Further ในทั้ง 3 Ad Set ที่เหลือแทน เพราะ Overlap กับทุกตัวสูงพอสมควรอยู่แล้ว การแยกเป็น Ad Set เดี่ยวจะยิ่งซ้ำซ้อน

ผลลัพธ์หลังปรับโครงสร้างจาก 5 Ad Set เหลือ 3 Ad Set ที่มี Overlap ต่ำกว่า 40% ทุกคู่: CPM รวมของแคมเปญลดลง 15% และงบที่เคยกระจายไปแข่งกันเองถูกนำไปใช้ Explore กลุ่มใหม่ได้มากขึ้น ทำให้ภายใน 1 เดือนพบ Segment ใหม่ที่ไม่เคยรู้จักมาก่อนคือกลุ่ม "ผู้ชายที่ซื้อ Skincare ให้แฟน/ภรรยา" ซึ่งมี CPA ต่ำกว่าค่าเฉลี่ย 20%

### กรณีศึกษา Overlap ที่พบจริง

เอเจนซี่ดูแลลูกค้าร้านเสื้อผ้าแฟชั่นสร้าง 5 Ad Set ในแคมเปญเดียวกัน แต่ละตัวใช้ Interest ต่างกันเล็กน้อย (Fashion, Online Shopping, Women's Clothing, Shoes, Accessories) หลังตรวจ Audience Overlap พบว่าทุกคู่มี Overlap เกิน 45% เพราะ Interest เหล่านี้ล้วนอยู่ในกลุ่มคนที่สนใจแฟชั่นเป็นหลักอยู่แล้ว ทีมตัดสินใจรวมทั้ง 5 Ad Set เป็น 1 Ad Set เดียวที่ใช้ Interest ทั้งหมดแบบ OR ในกล่องเดียวกัน ผลคือ CPM ลดลง 22% และ CPA ลดลง 18% ภายใน 2 สัปดาห์ เพราะไม่มีการแข่งประมูลกับตัวเองอีกต่อไป

### ข้อผิดพลาดที่พบบ่อย

1. สร้าง Ad Set จำนวนมากเพื่อ "ทดสอบ Interest" โดยไม่ตรวจ Overlap เลย ทำให้เผลอแข่งกับตัวเองมาตั้งแต่ต้น
2. ไม่รู้ว่า Audience Overlap Tool มีอยู่ในระบบ หรือรู้แต่ไม่เคยใช้ตรวจสอบเป็นประจำ
3. เข้าใจผิดว่า Advantage+ Audience ไม่มีปัญหา Overlap เพราะ AI จัดการเอง — ความจริงคือถ้า Suggestion ของหลาย Ad Set คล้ายกันมาก ก็ยังเสี่ยง Overlap ได้เช่นกัน แม้ AI จะช่วยลดปัญหานี้ลงกว่าเดิม
4. แก้ Overlap โดยรวม Ad Set โดยไม่พิจารณาว่าจริง ๆ ต้องการแยกเพื่อเปรียบเทียบ Creative หรือ Bid Strategy ที่ต่างกัน (ในกรณีนี้ Overlap ไม่ใช่ปัญหา แต่เป็นการทดสอบที่ตั้งใจ ต้องแยกให้ชัดว่าเป้าหมายคืออะไร)
5. ไม่ตรวจ Overlap ข้ามแคมเปญ (Cross-Campaign) — ปัญหา Overlap ไม่ได้เกิดแค่ในแคมเปญเดียวกัน แต่เกิดข้ามแคมเปญที่รันพร้อมกันได้เช่นกัน ต้องตรวจทั้งบัญชี ไม่ใช่แค่ภายในแคมเปญเดียว

---

## Step 460: Workshop — สร้าง 3 Core Audience สำหรับสินค้าจริง 1 ตัว และประเมิน Reach

Step นี้คือ Workshop หลักของ Part นี้ ให้ลงมือทำจริงในบัญชีโฆษณาของตัวเองหรือบัญชี Sandbox

### สินค้าตัวอย่างที่ใช้ในการฝึก

สมมติเลือกสินค้า: **เครื่องกรองน้ำติดตั้งในบ้าน ราคา 8,900 บาท** (เลือกสินค้านี้เพราะมีกลุ่มเป้าหมายที่ตีความได้หลายมุม เหมาะกับการฝึกสร้าง Persona ต่างกัน 3 แบบ)

### ขั้นตอนที่ 1 — กำหนด Persona 3 แบบก่อนเปิด Ads Manager

ก่อนเปิดหน้าตั้งค่า Audience ให้เขียน Persona สมมติฐาน 3 แบบลงในกระดาษหรือ Sheet ก่อน:

| Persona | ลักษณะ | เหตุผลที่น่าสนใจ |
|---|---|---|
| A: คุณแม่บ้านห่วงสุขภาพครอบครัว | หญิง 30-50, สนใจ Health/Family, มีลูก | กังวลคุณภาพน้ำที่ลูกดื่ม เป็นผู้ตัดสินใจซื้อของใช้ในบ้าน |
| B: คนซื้อบ้าน/คอนโดใหม่ | ทุกเพศ 28-45, Life Event "Recently Moved/New Home" | ต้องจัดของใช้ในบ้านใหม่ทั้งหมด เครื่องกรองน้ำเป็นของที่ต้องซื้อพอดี |
| C: คนรักสุขภาพที่ใส่ใจ Lifestyle | ทุกเพศ 25-45, สนใจ Fitness/Organic/Clean Eating | มองว่าน้ำสะอาดเป็นส่วนหนึ่งของ Lifestyle สุขภาพดี |

### ขั้นตอนที่ 2 — สร้าง Saved Audience ทั้ง 3 แบบใน Ads Manager

สำหรับแต่ละ Persona ให้เปิด Ads Manager → All Tools → Audiences → Create Audience → Saved Audience แล้วตั้งค่าตามนี้:

**Audience A — `CORE_HealthMom_Nationwide_30-50`**
- Location: ประเทศไทย (หรือจังหวัดที่ธุรกิจส่งของถึง)
- Age: 30-50
- Gender: Women
- Detailed Targeting: "Parenting" OR "Health" OR "Family" → Narrow Further → "Water Filter" (ถ้ามีในระบบ) หรือ Behavior "Engaged Shoppers"

**Audience B — `CORE_NewHomeOwner_Nationwide_ALL`**
- Location: ประเทศไทย
- Age: 28-45
- Gender: All
- Detailed Targeting: Life Event "Recently Moved" OR "New Home Owner" (ถ้ามีในระบบ) OR Interest "Home Improvement", "Interior Design"

**Audience C — `CORE_HealthLifestyle_Nationwide_25-45`**
- Location: ประเทศไทย
- Age: 25-45
- Gender: All
- Detailed Targeting: "Physical Fitness" OR "Organic Food" OR "Clean Eating" → Narrow Further → Behavior "Engaged Shoppers"

### ขั้นตอนที่ 3 — บันทึก Potential Reach ของทั้ง 3 Audience

จดตัวเลข Potential Reach ที่ระบบแสดงในกล่อง Audience Definition ของแต่ละ Audience ลงในตารางเปรียบเทียบ:

| Audience | Potential Reach (ประมาณ) | ระดับความแคบ/กว้าง |
|---|---|---|
| A: HealthMom | (บันทึกตัวเลขจริงที่เห็น) | |
| B: NewHomeOwner | (บันทึกตัวเลขจริงที่เห็น) | |
| C: HealthLifestyle | (บันทึกตัวเลขจริงที่เห็น) | |

### ขั้นตอนที่ 4 — ตรวจ Audience Overlap ระหว่างทั้ง 3 ตัว

ใช้ Audience Overlap Tool (Step 459) เทียบทั้ง 3 คู่ (A-B, A-C, B-C) บันทึกเปอร์เซ็นต์ Overlap และประเมินว่าคู่ไหนมีปัญหาต้องแก้ก่อนนำไปใช้จริงในแคมเปญเดียวกัน

### ขั้นตอนที่ 5 — เขียนสรุปเชิงกลยุทธ์

ตอบคำถามเหล่านี้เป็นลายลักษณ์อักษร (ใช้เป็น Test Log สำหรับทีมหรือลูกค้า):

1. Audience ไหนมี Potential Reach ที่เหมาะกับงบประมาณที่มีจริง?
2. มี Overlap ระหว่าง Audience คู่ใดที่ต้องระวังหากนำไปใช้ในแคมเปญเดียวกัน?
3. ถ้าต้องเลือกทดสอบก่อนแค่ 1 Audience เพราะงบจำกัด จะเลือกตัวไหน และเพราะอะไร?
4. Audience ไหนที่ควรเก็บไว้เป็น Suggestion สำหรับ Advantage+ Audience ในอนาคต แทนที่จะใช้เป็น Manual Targeting ตรง ๆ?

### Case Study อ้างอิงสำหรับ Workshop นี้

ธุรกิจเครื่องกรองน้ำรายหนึ่ง (ชื่อสมมติ "AquaPure") ทำ Workshop แบบเดียวกันนี้จริงในบัญชีของตัวเอง พบว่า Audience B (NewHomeOwner) มี Potential Reach เล็กที่สุด (ประมาณ 420,000 คนทั่วประเทศ) แต่หลังทดสอบยิงจริง 2 สัปดาห์ด้วยงบเท่ากันทั้ง 3 Audience กลับให้ CPA ต่ำที่สุด (310 บาทต่อ Lead เทียบกับ Audience A ที่ 480 บาท และ Audience C ที่ 590 บาท) เพราะคนที่ย้ายบ้านใหม่มี "Timing" ที่ตรงกับความต้องการซื้อเครื่องกรองน้ำมากที่สุด แม้ Reach จะเล็กกว่า Audience อื่น บทเรียนคือ Potential Reach ไม่ใช่ตัวชี้วัดความสำเร็จ Timing และความตรง Persona สำคัญกว่าขนาด

---

## Case Study สรุปท้าย Part: ร้านกาแฟ Specialty ปรับ Core Audience จนเจอ Persona ที่ใช่

ร้านกาแฟ Specialty แห่งหนึ่งในเชียงใหม่เปิดสาขาใหม่และต้องการโปรโมทผ่าน Facebook Ads เดิมทีทีมงานตั้ง Core Audience แบบกว้าง ๆ คือ Location รัศมี 10 กม. รอบร้าน, Age 20-45, Interest "Coffee" เพียงตัวเดียว ผลลัพธ์คือ CTR 0.6% และ CPA ต่อการเดินเข้าร้าน (วัดผ่าน Store Traffic Objective) สูงถึง 85 บาทต่อคน

ทีมงานกลับไปทำ Workshop แบบเดียวกับ Step 460 โดยตั้ง Persona 3 แบบ คือ (1) คนทำงาน Remote/Freelance ที่มองหาที่นั่งทำงาน (2) นักท่องเที่ยวที่มาเชียงใหม่ระยะสั้น (3) คนรักกาแฟ Specialty ที่ตามร้านใหม่ ๆ

หลังสร้าง Saved Audience ทั้ง 3 แบบและตรวจ Overlap พบว่า Persona (1) และ (3) มี Overlap ต่ำ (18%) ส่วน Persona (2) ที่ใช้ Location "Traveling in this location" มี Reach ใหญ่ที่สุดแต่ไม่ Overlap กับสองกลุ่มแรกเลย ทีมจึงตัดสินใจรัน 3 Ad Set แยกกันในแคมเปญเดียว (ABO) ด้วยงบเท่ากัน ผลลัพธ์หลัง 2 สัปดาห์:

| Persona | CTR | CPA ต่อการเดินเข้าร้าน |
|---|---|---|
| (1) Remote Worker | 2.1% | 32 บาท |
| (2) นักท่องเที่ยว | 1.4% | 58 บาท |
| (3) Coffee Lover | 1.8% | 41 บาท |

ทีมจึงย้ายงบส่วนใหญ่ไปที่ Persona (1) และ (3) และปรับ Creative ให้เจาะจงมากขึ้น (Persona 1 ใช้ภาพที่นั่งทำงานมี Wi-Fi/ปลั๊ก, Persona 3 ใช้ภาพขั้นตอนการคั่ว/ชง) ผล CPA เฉลี่ยรวมของร้านลดลงจาก 85 บาท เหลือ 36 บาทภายในเดือนแรก บทเรียนสำคัญคือ Interest เดียวกว้าง ๆ อย่าง "Coffee" ไม่พอ ต้องแยก Persona ตาม Intent การมาร้านที่ต่างกันจริง แม้จะเป็นสินค้า/บริการเดียวกัน

---

## FAQ ที่พบบ่อยเกี่ยวกับ Core Audience

**Q1: ถ้าไม่แน่ใจว่า Interest ที่เลือกตรงกับ Persona จริงหรือไม่ ควรเช็คจากที่ไหนก่อนใช้จริง**

ก่อนใช้ Interest ใหม่ที่ไม่มีข้อมูลในอดีตรองรับ ให้ตรวจ 3 จุด คือ (1) Audience Size ของ Interest นั้นสมเหตุสมผลกับตลาดไทยหรือไม่ (Interest บางตัวแปลมาจากตลาดต่างประเทศ อาจมีขนาดเล็กผิดปกติในไทย) (2) ลองดู Suggestions ที่ระบบแนะนำเพิ่มว่าเกี่ยวข้องกับ Persona ที่คิดไว้หรือไม่ ถ้า Suggestions ที่ออกมาดูไม่เกี่ยวข้องเลย อาจแปลว่า Interest ที่เลือกไม่ตรงกลุ่มจริง (3) ตั้งงบทดสอบเล็ก ๆ (Test Budget) ก่อนทุ่มงบเต็ม แล้วดู Breakdown by Age/Gender ว่าตรงกับสมมติฐานหรือไม่

**Q2: Core Audience กับ Custom Audience ต่างกันยังไง ทำไมต้องเรียนแยก Part**

Core Audience สร้างจาก "เงื่อนไขที่ Meta เก็บไว้เกี่ยวกับผู้ใช้ทุกคน" (Demographic, Interest, Behavior) โดยเราไม่รู้จักตัวบุคคลเลย เป็นการเดาจากลักษณะ ส่วน Custom Audience (Part 047) สร้างจาก "ข้อมูลจริงที่ธุรกิจมีอยู่แล้ว" เช่น คนที่เคยเข้าเว็บไซต์ คนที่อยู่ในฐานลูกค้า CSV ของเราเอง ซึ่งแม่นยำกว่ามากเพราะอิงพฤติกรรมจริงกับธุรกิจเรา ไม่ใช่การเดาจากลักษณะทั่วไป

**Q3: ตั้ง Interest ไว้ 1 ตัวแคบมาก แต่ Ad Set ไม่ยอมวิ่ง (Not Delivering) ควรทำอย่างไร**

ตรวจ Potential Reach ก่อน ถ้าต่ำกว่า 50,000 คนในประเทศไทยและงบต่อวันสูงกว่าที่ Pool จะรับได้ ระบบมักจะ Delivery ช้าหรือไม่วิ่งเลย วิธีแก้คือ (1) เพิ่ม Interest อื่นที่เกี่ยวข้องแบบ OR เพื่อขยาย Pool (2) ลด Age Range ให้กว้างขึ้นถ้าตั้งแคบเกินไป (3) ลดงบต่อวันให้สมเหตุสมผลกับขนาด Pool หรือ (4) ยอมรับว่า Interest นี้แคบเกินสำหรับ Manual Targeting และย้ายไปใช้เป็น Suggestion ใน Advantage+ Audience แทน

**Q4: ควรใส่ Interest กี่ตัวต่อ Ad Set ถึงจะเหมาะสม**

ไม่มีตัวเลขตายตัว แต่แนวทางที่ใช้ได้จริงคือ 2-5 Interest ที่เกี่ยวข้องกันชัดเจนในกล่องแรก (OR Logic) และถ้าต้องการ Narrow เพิ่มความแม่นยำ ใช้ Narrow Further อีก 1 ชั้นก็เพียงพอสำหรับธุรกิจส่วนใหญ่ การใส่ Interest 10-15 ตัวแบบ "เผื่อไว้ทุกทาง" มักทำให้สัญญาณเจือจางและตีความยาก เหมือนที่เคยพูดถึงใน Part 030 เรื่อง Suggestion สำหรับ Advantage+ Audience

**Q5: ทำไมบัญชีของเพื่อนเห็นตัวเลือก Manual/Original Audience เต็มรูปแบบ แต่บัญชีของเรามีแค่ Advantage+ Audience**

Meta ทยอย Roll out การเปลี่ยนแปลง UI ไม่พร้อมกันทุกบัญชี บัญชีใหม่หรือบัญชีที่ Meta จัดอยู่ในกลุ่มทดสอบฟีเจอร์ใหม่มักถูกบังคับให้ใช้ Advantage+ Audience เป็นค่าเริ่มต้นโดยไม่มีตัวเลือกปิด ในขณะที่บัญชีเก่าบางบัญชียังเห็นตัวเลือกสลับได้ ไม่ใช่บั๊ก แต่เป็นการทดสอบและ Roll out แบบเป็นขั้นตอนของ Meta เอง

**Q6: Location Radius Targeting กับ Location แบบเลือกเขต/จังหวัด อันไหนแม่นยำกว่า**

Radius Targeting (ปักหมุด + กำหนดรัศมี) แม่นยำกว่าสำหรับธุรกิจหน้าร้านที่มีพื้นที่บริการจำกัดชัดเจน เพราะคำนวณจากระยะทางจริงรอบจุดที่ปัก ในขณะที่การเลือกเขต/จังหวัดจะยิงทั่วทั้งเขตนั้นแม้พื้นที่ชายขอบจะไกลจากร้านมาก ธุรกิจ Delivery ควรใช้ Radius เสมอ ส่วนธุรกิจที่ลูกค้าเดินทางมาหาได้ไกล (เช่น คลินิกเฉพาะทาง, โรงเรียนนานาชาติ) อาจใช้เขต/จังหวัดได้เพราะลูกค้ายอมเดินทางไกลอยู่แล้ว

## Checklist ท้ายบท

- [ ] เข้าใจความแตกต่างระหว่าง Core Field (Location/Age/Gender/Language) ที่เป็น Hard Constraint กับ Detailed Targeting ที่เป็น Suggestion ในบริบท Advantage+ Audience
- [ ] ตั้งค่า Location ถูกตัวเลือก (Everyone/Live/Recently/Traveling) ตรงกับลักษณะธุรกิจ ไม่ใช่ปล่อย Default เสมอ
- [ ] เข้าใจที่มาของ Interest ว่ามาจาก Explicit + Behavioral + Off-platform Signal และรู้ว่า Off-platform อ่อนลงมากหลัง iOS14/ATT
- [ ] รู้จักหมวด Behavior และ Demographic อย่างน้อย 5 หมวดที่เกี่ยวกับธุรกิจตัวเอง ไม่ใช่รู้จักแค่ Interest
- [ ] เข้าใจ Logic OR (ในกล่องเดียวกัน) vs AND (Narrow Further) vs NOT (Exclude) และใช้ถูกต้องตามที่ตั้งใจ
- [ ] มี Exclusion Strategy พื้นฐานอย่างน้อย Exclude Purchasers และ Employee List ในทุกแคมเปญ Prospecting
- [ ] รู้วิธีอ่าน Potential Reach และรู้สัญญาณของ Audience ที่แคบเกินไป/กว้างเกินไป
- [ ] มี Saved Audience ที่ตั้งชื่อเป็นระบบอย่างน้อย 3 ตัวสำหรับธุรกิจ/ลูกค้าที่ดูแล
- [ ] มีกรอบตัดสินใจชัดเจนว่าเมื่อไหร่ใช้ Core Audience เมื่อไหร่ปล่อย Advantage+ Audience ครองสนาม
- [ ] ตรวจ Audience Overlap ระหว่าง Ad Set ทุกครั้งที่สร้างหลาย Ad Set ในแคมเปญ/บัญชีเดียวกัน

## Workshop / แบบฝึกหัด

ทำตาม Step 460 อย่างละเอียดกับสินค้า/บริการของตัวเองหรือของลูกค้า โดยส่งมอบผลงาน 3 ชิ้นตามนี้:

1. **เอกสาร Persona 3 แบบ** พร้อมเหตุผลว่าทำไมเลือก Persona เหล่านี้ (อ้างอิงข้อมูลลูกค้าเดิมถ้ามี หรือสมมติฐานที่มีเหตุผลรองรับถ้าเป็นธุรกิจใหม่)
2. **Saved Audience 3 ตัวจริงในบัญชี Ads Manager** ตั้งชื่อตาม Naming Convention ที่แนะนำ พร้อม Screenshot ตัวเลข Potential Reach ของแต่ละตัว
3. **ตาราง Audience Overlap** เทียบทั้ง 3 คู่ พร้อมสรุปว่าจะจัดการ Overlap อย่างไรถ้าจะนำไปยิงจริงพร้อมกัน

โบนัส: ถ้ามีบัญชีที่มี Pixel Data สะสมอยู่แล้ว ให้ลองรันจริง 3 Ad Set นี้แบบ ABO งบเท่ากันเป็นเวลา 1 สัปดาห์ แล้วกลับมาเปรียบเทียบ CTR/CPA จริงกับสมมติฐานที่ตั้งไว้ตอนแรก

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ปูพื้นให้เข้าใจ Core Audience อย่างละเอียดครบทุกมิติ ตั้งแต่ Building Block พื้นฐาน ไปจนถึง Logic การผสม Interest, Exclusion, การอ่านขนาด Audience, และการจัดการ Overlap ซึ่งทั้งหมดนี้ยังเป็นทักษะจำเป็นแม้ในยุคที่ AI-Powered Targeting ครองสนามมากขึ้นเรื่อย ๆ เพราะ Core Audience คือ "วัตถุดิบ" ที่ AI ใช้ตั้งต้นเรียนรู้ และเป็นเครื่องมือสำรองที่จำเป็นในสถานการณ์เฉพาะ

Part ถัดไป (Part 047) จะพาไปเจาะลึก **Custom Audience จากทุกแหล่งข้อมูล** ซึ่งเป็นก้าวต่อจาก Core Audience ไปอีกขั้น — จาก "การเดากลุ่มเป้าหมายจากข้อมูลประชากร" ไปสู่ "การใช้ข้อมูลพฤติกรรมจริงของคนที่เคย Interact กับธุรกิจเราแล้ว" ซึ่งเป็นรากฐานสำคัญของ Retargeting และ Lookalike Audience ที่จะเรียนต่อใน Part 048

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- Meta Business Help Center: หมวด "About Detailed Targeting" และ "About Audience Overlap"
- Meta for Business: Advertising Policies ส่วน Special Ad Category (เชื่อมกับ Part 020)
- Meta Business Help Center: "About Saved Audiences"
- เอกสารภายในทีม: Test Log Template จาก Part 030 Step 296 (นำมาปรับใช้บันทึกผลการทดสอบ Core Audience ได้เช่นกัน)
- ทบทวน Part 005 (Buyer Persona) และ Part 030 (Advantage+ Audience) เพื่อเชื่อมความเข้าใจให้ครบวงจร
