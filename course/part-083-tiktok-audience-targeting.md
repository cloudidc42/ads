# Part 083: TikTok Audience Targeting (Core, Custom, Lookalike)

**Section:** I — TikTok Targeting, Optimization & Scaling
**Step ที่ครอบคลุม:** Step 821–830 (จาก 1000 Steps ทั้งหมด)
**เวลาที่ใช้เรียนโดยประมาณ:** 9–12 ชั่วโมง (รวมการลงมือสร้าง Audience จริงใน TikTok Ads Manager และทำ Workshop สร้าง Audience Library)
**ระดับ:** กลาง (ต้องมีพื้นฐานจาก Section G-H มาก่อน โดยเฉพาะ Part 064 เรื่องระบบนิเวศ TikTok เทียบกับ Facebook, Part 066 เรื่อง TikTok Pixel/Events API, และ Part 067 เรื่องโครงสร้างแคมเปญ Campaign > Ad Group > Ad)

---

Section H ที่ผ่านมาสอนให้ผลิตคอนเทนต์ TikTok ที่ดีได้แล้ว ตั้งแต่การเขียนสคริปต์ (Part 079) การผลิตด้วยงบต่ำ (Part 080) การหาเทรนด์จาก Creative Center (Part 081) ไปจนถึงการทำงานกับครีเอเตอร์ (Part 082) แต่คอนเทนต์ที่ดีที่สุดในโลกจะไม่สร้างผลลัพธ์อะไรเลยถ้าไปแสดงผลกับคนที่ไม่ใช่กลุ่มเป้าหมาย Section I เปิดฉากด้วย Part นี้เพราะ Targeting คือจุดที่ตัดสินว่าครีเอทีฟที่ทำมาอย่างดีจะไปเจอคนที่ "ใช่" หรือไม่

นักยิงแอดที่มาจากฝั่ง Facebook มักเข้าใจผิดจุดสำคัญเมื่อเริ่มยิง TikTok คือคิดว่า Targeting ของ TikTok ทำงานเหมือน Facebook เพียงแค่เปลี่ยนหน้าตา UI เท่านั้น ความจริงคือกลไกเบื้องหลังต่างกันมากพอที่จะทำให้ยุทธศาสตร์ที่ใช้ได้ผลบน Facebook ใช้ไม่ได้ผลแบบเดียวกันบน TikTok ถ้าไม่เข้าใจความต่างนี้ก่อน Part นี้จะพาไปเจาะทุกชั้นของ TikTok Audience ตั้งแต่ Core/Demographic Targeting, ความต่างของสัญญาณ Targeting ระหว่างสองแพลตฟอร์ม, Custom Audience จากทุกแหล่งข้อมูล, Lookalike Audience, ไปจนถึง Automated Targeting ที่เป็นทิศทางหลักของ TikTok ในปี 2026

## Steps ที่ครอบคลุมใน Part นี้

1. **Step 821** — TikTok Core/Demographic Targeting: Location, Age, Gender, Language ตั้งค่าอย่างไรและต่างจาก Facebook ที่ไหน
2. **Step 822** — TikTok Interest & Behavior Targeting เจาะลึก: Interest Category, Video Interaction, Creator Interaction, Hashtag Interaction
3. **Step 823** — ความแตกต่างเชิงกลไก: สัญญาณ Targeting ของ TikTok เป็น Content-Behavior-Based มากกว่า Social-Graph-Based ของ Facebook
4. **Step 824** — TikTok Custom Audience จาก Pixel/Events API: Website Traffic และ App Activity Audience
5. **Step 825** — TikTok Custom Audience จาก Customer File Upload: โครงสร้างไฟล์ การ Hash ข้อมูล และ Match Rate
6. **Step 826** — TikTok Engagement Audience: Video Views, Profile Visits, Business Account Engagement, Lead Gen Form Engagement
7. **Step 827** — TikTok Lookalike Audience: สร้างอย่างไร Source Audience ต้องเป็นแบบไหน และตั้งขนาดยังไง
8. **Step 828** — Automated Targeting vs Custom Targeting: TikTok's Advantage+ Audience Equivalent และเมื่อไหร่ควรใช้แบบไหน
9. **Step 829** — Audience Size Guidance, Exclusion Targeting, และข้อผิดพลาดคลาสสิกในการ Targeting บน TikTok
10. **Step 830** — Workshop: สร้าง TikTok Audience Library ฉบับสมบูรณ์สำหรับธุรกิจจริง 1 ราย

---

## Step 821: TikTok Core/Demographic Targeting — Location, Age, Gender, Language

### ตำแหน่งตั้งค่าใน TikTok Ads Manager

ไปที่ **Campaign → Ad Group → Targeting** จะเจอส่วน **Demographics** ซึ่งประกอบด้วย Location, Gender, Age, Languages เป็นชุดฟิลด์แรกที่ต้องตั้งเสมอ ต่างจาก Facebook เล็กน้อยตรงที่ TikTok รวม Core Field ทั้งหมดไว้ในหน้าเดียวไม่มีการซ่อนไว้หลัง Toggle แบบ Advantage+ Audience ของ Facebook (แม้ TikTok จะมี Toggle "Automated Targeting" อยู่ข้าง ๆ ก็ตาม ซึ่งจะเรียนละเอียดใน Step 828)

### Location: หน่วยที่เลือกได้และข้อจำกัด

TikTok ให้เลือก Location ได้ในระดับ **ประเทศ, ภูมิภาค (Region/State), เมือง (City)** แต่ **ไม่มี Radius Targeting แบบปักหมุด** เหมือน Facebook ที่ตั้งรัศมีเป็นกิโลเมตรรอบจุดใดจุดหนึ่งได้ นี่คือข้อจำกัดสำคัญที่ธุรกิจหน้าร้าน (Brick & Mortar) ต้องรู้ก่อนตั้งความคาดหวัง เพราะจะทำได้แค่เลือกระดับเมือง/เขตที่ใกล้เคียงที่สุด ไม่สามารถระบุ "รัศมี 5 กม. รอบร้าน" ได้ตรง ๆ แบบ Facebook

| ระดับ Location | TikTok Ads Manager | Facebook Ads Manager |
|---|---|---|
| ประเทศ | รองรับ | รองรับ |
| ภาค/จังหวัด (Region) | รองรับ | รองรับ |
| เมือง/เขต | รองรับ (บางตลาดเท่านั้น ขึ้นกับความละเอียดของ TikTok ในประเทศนั้น) | รองรับ |
| Radius รอบจุดปักหมุด | **ไม่รองรับ** | รองรับ (1-80 กม.) |
| Exclude Location | รองรับ | รองรับ |

**วิธีแก้สำหรับธุรกิจหน้าร้าน:** เลือก Location ระดับเขต/อำเภอที่ใกล้เคียงพื้นที่บริการที่สุด แล้วใช้ Creative ที่ระบุพื้นที่ชัดเจนในคอนเทนต์ (เช่น พูดชื่อทำเลในวิดีโอ) เพื่อกรองคนที่ไม่ได้อยู่ในพื้นที่ให้ Self-select ออกไปเอง หรือถ้าธุรกิจมีสาขาเดียวในเมืองเล็ก อาจตั้ง Location เป็นระดับเมืองไปตรง ๆ ได้เลยเพราะไม่มีเขตให้เลือกละเอียดกว่านั้น

### Age: ช่วงอายุที่ TikTok เปิดให้ใช้

TikTok เปิด Age Targeting ตั้งแต่ 13 ปีขึ้นไป (ต่ำสุดตามนโยบายเดียวกับ Facebook) แบ่งเป็นช่วง 13-17, 18-24, 25-34, 35-44, 45-54, 55+ เลือกได้หลายช่วงพร้อมกัน จุดต่างจาก Facebook คือ Facebook ให้พิมพ์อายุแบบต่อเนื่อง (เช่น 27-52) ส่วน TikTok บังคับเลือกเป็นช่วง Bucket ตายตัว ทำให้ยืดหยุ่นน้อยกว่าเล็กน้อย แต่ก็ทำให้อ่าน Breakdown ผลลัพธ์ตาม Age Group ได้ตรงไปตรงมากว่า

ข้อสังเกตสำคัญ: ฐานผู้ใช้ TikTok ในไทยกระจุกตัวที่ช่วง 18-34 หนาแน่นกว่า Facebook มาก ธุรกิจที่เคย Success บน Facebook ด้วยกลุ่ม 35-54 ต้องตระหนักว่าการยิง TikTok เจาะกลุ่มเดียวกันอาจได้ Reach น้อยกว่าที่คาด ไม่ใช่เพราะ Targeting ผิด แต่เพราะ Pool ของกลุ่มอายุนั้นบน TikTok เล็กกว่า Facebook จริง ๆ

### Gender และ Language

Gender มี All, Male, Female เหมือน Facebook ส่วน Language เลือกได้จากภาษาที่ผู้ใช้ตั้งไว้ในแอป TikTok เอง ประโยชน์คล้ายกับ Facebook คือใช้เจาะกลุ่ม Expat หรือกลุ่มที่ใช้ภาษาอังกฤษเป็นหลักในกรุงเทพฯ ได้ แต่ TikTok มีข้อจำกัดคือผู้ใช้จำนวนมากในไทยตั้งภาษาแอปเป็นไทยแม้จะเป็นคนต่างชาติที่อาศัยอยู่ในไทย (เพราะ UI ภาษาไทยของ TikTok ใช้งานง่ายและเนื้อหาส่วนใหญ่ก็เป็นไทยอยู่แล้ว) ทำให้ Language Targeting บน TikTok แม่นยำน้อยกว่าบน Facebook ในการกรอง Expat

### ตารางสรุปเปรียบเทียบ Core Targeting TikTok vs Facebook

| ฟิลด์ | TikTok | Facebook | ผลกระทบเชิงกลยุทธ์ |
|---|---|---|---|
| Location | ประเทศ/ภาค/เมือง เท่านั้น ไม่มี Radius | ประเทศ/ภาค/เมือง/Radius แบบปักหมุด | ธุรกิจหน้าร้านต้องปรับกลยุทธ์ Creative ชดเชยข้อจำกัดนี้บน TikTok |
| Age | เลือกจาก Bucket ตายตัว 6 ช่วง | พิมพ์ช่วงต่อเนื่องได้เอง | TikTok วิเคราะห์ Breakdown ง่ายกว่าแต่ปรับละเอียดได้น้อยกว่า |
| Gender | All/Male/Female | All/Men/Women | เหมือนกัน |
| Language | ตามภาษาที่ตั้งในแอป | ตามภาษาที่ตั้งใน Facebook | TikTok แม่นยำน้อยกว่าสำหรับกรอง Expat ในตลาดไทย |
| ฐานผู้ใช้ตามอายุ | กระจุก 18-34 หนาแน่น | กระจายกว้างกว่า รวม 35-54+ มาก | กลุ่มอายุมากบน TikTok มี Pool เล็กกว่า ต้องตั้งความคาดหวัง Reach ให้สมจริง |

### ข้อผิดพลาดที่พบบ่อย

1. คาดหวัง Radius Targeting แบบ Facebook แล้วผิดหวังเมื่อไม่เจอตัวเลือกนี้ใน TikTok Ads Manager
2. ตั้ง Age Range แคบเกินไปโดยลืมว่า TikTok เป็น Bucket ทำให้บางครั้งเผลอตัดกลุ่มที่ต้องการออกไปเพราะ Bucket ไม่ตรงกับขอบอายุที่ต้องการเป๊ะ ๆ
3. ยิงกลุ่มอายุ 45+ ด้วยงบเท่ากับที่เคยใช้บน Facebook แล้วผิดหวังกับ Reach ที่ได้ต่ำกว่ามาก โดยไม่รู้ว่า Pool ของกลุ่มนี้บน TikTok เล็กกว่าจริง
4. ใช้ Language Targeting เพื่อกรอง Expat บน TikTok เหมือนที่ทำบน Facebook แล้วได้ผลไม่ตรงเป้าเพราะพฤติกรรมตั้งภาษาแอปต่างกัน

---

## Step 822: TikTok Interest & Behavior Targeting เจาะลึก

### โครงสร้าง Interest & Behavior Targeting ของ TikTok

TikTok แบ่ง Detailed Targeting (อยู่ในส่วน **Interest & Behavior** ใต้ Demographics) เป็น 2 กลุ่มหลัก:

1. **Interest Category** — หมวดความสนใจที่ TikTok จัดกลุ่มไว้ล่วงหน้า (คล้าย Interest ของ Facebook) เช่น Beauty & Personal Care, Food & Beverage, Gaming, Fashion, Education
2. **Behavior** — แบ่งเป็น 3 กลุ่มย่อยที่เป็นเอกลักษณ์ของ TikTok และไม่มีบน Facebook แบบเดียวกันเป๊ะ ๆ:
   - **Video Interaction** — คนที่ Like, Comment, Share, ดูจบ Video ในหมวดหมู่ที่กำหนดในช่วง 7-15 วันที่ผ่านมา
   - **Creator Interaction** — คนที่ Follow, ดู Profile, หรือ Engage กับครีเอเตอร์ในหมวดหมู่ที่กำหนด
   - **Hashtag Interaction** — คนที่ Engage กับคอนเทนต์ที่ใช้ Hashtag ในหมวดหมู่ที่กำหนด (เปิดใช้งานเฉพาะบางตลาด/บาง Objective)

### ทำไม Video Interaction Behavior ถึงทรงพลังกว่าที่คิด

จุดที่ต่างจาก Facebook อย่างชัดเจนคือ TikTok ให้ Targeting คนที่ **"ดูจบวิดีโอ"** ในหมวดหมู่หนึ่งได้โดยตรง ไม่ใช่แค่ "สนใจหัวข้อนั้น" แบบ Interest ทั่วไป การดูจบวิดีโอเป็นสัญญาณพฤติกรรมที่หนักแน่นกว่าการกด Like หรือ Follow มาก เพราะสะท้อนว่าคนนั้นให้เวลาความสนใจจริงกับคอนเทนต์ประเภทนั้นในช่วงเวลาสั้น ๆ ที่ผ่านมา ไม่ใช่ความสนใจเก่าที่อาจไม่ตรงกับปัจจุบันแล้ว

### ตารางหมวด Interest Category ที่ใช้บ่อยและธุรกิจที่เหมาะ

| หมวด | ตัวอย่าง Sub-category | ธุรกิจที่เหมาะ |
|---|---|---|
| Beauty & Personal Care | Skincare, Makeup, Haircare | เครื่องสำอาง, คลินิกความงาม |
| Food & Beverage | Cooking, Restaurants, Healthy Eating | ร้านอาหาร, สินค้าอาหาร |
| Fashion & Accessories | Streetwear, Sneakers, Jewelry | เสื้อผ้า, เครื่องประดับ |
| Gaming | Mobile Games, PC Games, Esports | เกม, อุปกรณ์เกมมิ่ง |
| Education | Online Courses, Language Learning | คอร์สออนไลน์, สถาบันภาษา |
| Parenting & Family | Baby Products, Parenting Tips | สินค้าเด็ก, แม่และเด็ก |
| Fitness | Home Workout, Gym, Sports | ฟิตเนส, อาหารเสริม |
| Travel | Domestic Travel, Hotels | ท่องเที่ยว, โรงแรม |

### ตัวอย่างการผสม Interest + Behavior ที่ได้ผลจริง

แบรนด์อาหารเสริมลดน้ำหนักทดสอบ 2 แนวทางบน TikTok:

1. Interest Category "Fitness" เดี่ยว ๆ (Reach กว้าง ~4 ล้านคน) → CTR 1.1%, CPA 290 บาท
2. Interest "Fitness" + Behavior "Video Interaction: ดูจบวิดีโอหมวด Weight Loss/Diet ใน 7 วันที่ผ่านมา" (Reach แคบลงเหลือ ~650,000 คน) → CTR 2.4%, CPA 165 บาท

บทเรียนเช่นเดียวกับที่เคยเห็นบน Facebook คือการผสม Interest กับ Behavior ที่จับพฤติกรรมล่าสุดจริง ๆ ให้ผลลัพธ์ที่แม่นยำกว่า Interest กว้างเดี่ยว ๆ มาก แต่บน TikTok สัญญาณ Behavior "ดูจบวิดีโอ" นี้สดใหม่กว่า Interest ของ Facebook ที่มักอิงข้อมูลสะสมระยะยาว

### ข้อผิดพลาดที่พบบ่อย

1. ใช้ Interest Category เดี่ยว ๆ กว้างเกินไปโดยไม่จับคู่กับ Behavior เพื่อเพิ่มความแม่นยำ
2. ไม่รู้จัก Video/Creator/Hashtag Interaction Behavior เพราะคุ้นเคยกับ Interest แบบ Facebook มาก่อน จึงมองข้ามเครื่องมือที่ TikTok มีให้แต่ Facebook ไม่มี
3. เลือก Behavior ที่ Time Window สั้นเกินไป (เช่น 7 วัน) สำหรับสินค้าที่ Purchase Cycle ยาว ทำให้ Pool เล็กเกินความจำเป็น
4. ไม่ทดสอบเปรียบเทียบ Interest เดี่ยวกับ Interest+Behavior แบบมีระบบ ทำให้ไม่รู้ว่าจริง ๆ Behavior ช่วยหรือไม่ช่วยสำหรับธุรกิจตัวเอง

---

## Step 823: ความแตกต่างเชิงกลไก — TikTok เป็น Content-Behavior-Based มากกว่า Social-Graph-Based

### รากฐานที่ต่างกันของสองแพลตฟอร์ม

Facebook เกิดจาก Social Graph — เครือข่ายความสัมพันธ์ระหว่างคน (เพื่อน, Page ที่ Like, Group ที่เข้าร่วม) ระบบ Feed และ Ad Targeting ของ Facebook จึงพึ่งพาข้อมูล "ใครเชื่อมกับใคร" และ "ใคร Interact กับ Page/Content ประเภทไหน" เป็นรากฐานสำคัญมาตั้งแต่ต้น แม้ในปี 2026 ที่ Social Graph มีน้ำหนักลดลงเพราะ Feed เน้น Interest-based Content มากขึ้น แต่ระบบ Ad Targeting ก็ยังมีเงาของ Social Graph หลงเหลืออยู่ (เช่น Interest ที่มาจาก Page ที่ Like, Custom Audience ที่อิง Contact List ของเพื่อน)

TikTok เกิดในยุคที่ Recommendation Algorithm (For You Page) เป็นแกนหลักตั้งแต่วันแรก ไม่มี "เพื่อน" เป็นศูนย์กลางของประสบการณ์ผู้ใช้เหมือน Facebook For You Page แสดงคอนเทนต์จากคนที่ไม่รู้จักกันเลยได้ถ้าคอนเทนต์นั้นตรงกับ **พฤติกรรมการเสพคอนเทนต์** ของผู้ใช้คนนั้น ไม่ใช่ตรงกับความสัมพันธ์ทางสังคม ผลคือ Ad Targeting ของ TikTok จึงถูกออกแบบให้อิงพฤติกรรมการดู/Engage กับคอนเทนต์เป็นหลัก มากกว่าอิงเครือข่ายความสัมพันธ์

### ตารางเปรียบเทียบรากฐานสัญญาณ Targeting

| มิติ | Facebook | TikTok |
|---|---|---|
| รากฐานระบบ | Social Graph (เครือข่ายคน) | Recommendation Engine (พฤติกรรมเสพคอนเทนต์) |
| สัญญาณหลักของ Interest | Page Like, Group, Profile Info, พฤติกรรม Off-platform (ลดลงหลัง iOS14) | พฤติกรรมการดู/Engage วิดีโอแบบ Real-time เป็นหลัก |
| อายุของสัญญาณ | สะสมยาวนาน อาจมีข้อมูลเก่าหลายปีติดอยู่ | สดใหม่กว่า อัปเดตไวตามพฤติกรรมล่าสุด (วัน/สัปดาห์) |
| ผลของ "เพื่อน" ต่อ Targeting | มีอิทธิพลทางอ้อมผ่าน Social Signal | แทบไม่มีผลเลย |
| ความไวต่อ Content Performance | Creative ส่งผลต่อ Ad Score ผ่าน Relevance/Quality Ranking | Creative ส่งผลโดยตรงและเร็วมากต่อ Delivery เพราะระบบเดียวกับ Organic Feed |

### ผลกระทบเชิงยุทธศาสตร์ที่นักยิงแอดต้องปรับ

1. **Creative สำคัญกว่า Targeting มากกว่าที่เคยคิดตามสัดส่วนบน Facebook** — เพราะระบบ Delivery ของ TikTok ตัดสินใจส่งโฆษณาโดยดูจากว่าคอนเทนต์นั้นมีคน Engage เร็วแค่ไหนในกลุ่มตัวอย่างเล็ก ๆ ก่อน (คล้ายกลไก Organic Feed) มากกว่าการยึด Targeting ที่ตั้งไว้อย่างตายตัว ถ้า Creative ไม่ดีพอที่จะทำให้คนหยุดดู ต่อให้ Targeting แม่นแค่ไหนก็ไม่ช่วยมาก
2. **Interest/Behavior ของ TikTok เปลี่ยนเร็วกว่า ต้องอัปเดต Audience บ่อยกว่า** — Interest บน Facebook อาจใช้ได้ผลต่อเนื่องเป็นปี แต่ Behavior แบบ Video/Creator Interaction บน TikTok อาจให้ผลต่างกันในระยะเวลาไม่กี่เดือนเพราะเทรนด์เปลี่ยนเร็ว
3. **Custom Audience จาก Social Signal ทำได้จำกัดกว่า** — Facebook มี Engagement Audience ที่อิงคนที่เคย Comment/Share/React กับ Page คล้ายกับ TikTok แต่ Facebook ยังมี Custom Audience จาก Contact List ที่แข็งแรงกว่าเพราะฐาน Social Graph ที่ลึกกว่า
4. **Lookalike ของ TikTok ทำงานต่างไป** — เพราะไม่มี Social Graph ให้อ้างอิง TikTok Lookalike จึงต้องพึ่งพา Content-Behavior Pattern ในการหาคนคล้ายเป็นหลัก (รายละเอียดใน Step 827)

### ตัวอย่างจริงที่แสดงความต่างนี้อย่างชัดเจน

แบรนด์เสื้อผ้าสตรีทแวร์รายหนึ่งย้ายงบจาก Facebook มาทดสอบ TikTok โดยใช้ Creative และ Targeting Persona แบบเดียวกันทุกอย่าง (Interest: Streetwear, Fashion) ผลที่ได้บน Facebook ค่อนข้างสม่ำเสมอไม่ว่าจะเปลี่ยน Creative กี่ตัว แต่บน TikTok ผลลัพธ์แตกต่างกันมาก — วิดีโอที่ Hook 3 วินาทีแรกแรงพอได้ CPA ต่ำกว่าเฉลี่ย 60% ในขณะที่วิดีโอที่ Hook อ่อนได้ CPA สูงกว่าเฉลี่ยถึง 3 เท่า ทั้งที่ Targeting เหมือนกันทุกอย่าง สรุปคือ TikTok "ให้อภัย" Creative ที่อ่อนน้อยกว่า Facebook มาก เพราะกลไก Delivery ผูกกับ Content Performance โดยตรงกว่า

### ข้อผิดพลาดที่พบบ่อย

1. ยกยุทธศาสตร์ Targeting จาก Facebook มาใช้บน TikTok ตรง ๆ โดยไม่ปรับสัดส่วนความสำคัญของ Creative ให้สูงขึ้น
2. คาดหวังว่า Interest บน TikTok จะให้ผลคงที่ยาวนานเหมือน Facebook ทั้งที่ต้องหมั่นทดสอบ Refresh บ่อยกว่า
3. ไม่เข้าใจว่าทำไม Ad Set/Ad Group ที่ Targeting เหมือนกันแต่ Creative ต่างกันบน TikTok ให้ผลต่างกันมากกว่าที่เคยเห็นบน Facebook — มองว่าเป็นความผันผวนของระบบ ทั้งที่จริงคือกลไกการทำงานที่ต่างกันโดยธรรมชาติ
4. มองข้ามความสำคัญของการทำ Creative Testing (Part 043-044 ของ Facebook, และหลักการเดียวกันที่ต้องใช้กับ TikTok) เพราะเชื่อว่า Targeting ที่ดีพอจะเอาชนะ Creative ที่อ่อนได้เหมือนที่เคยทำได้บน Facebook

---

## Step 824: TikTok Custom Audience จาก Pixel/Events API — Website Traffic และ App Activity Audience

### ภาพรวม Custom Audience บน TikTok

TikTok แบ่งแหล่งข้อมูลสำหรับสร้าง Custom Audience ออกเป็นหลักๆ 4 แหล่ง: Customer File (Step 825), Website Traffic/App Activity ผ่าน Pixel/Events API (Step นี้), Engagement (Step 826), และ Lookalike ที่สร้างจาก Custom Audience เหล่านี้อีกชั้น (Step 827) ตำแหน่งตั้งค่าอยู่ที่ **Assets → Audiences → Create Audience → Custom Audience**

### Website Traffic Audience: สร้างจาก Pixel Events

เมื่อติดตั้ง TikTok Pixel และตั้งค่า Standard Events ตามที่เรียนใน Part 066 แล้ว สามารถสร้าง Custom Audience จากพฤติกรรมบนเว็บไซต์ได้โดยเลือกเงื่อนไข:

- **Event ที่ต้องการ** — เช่น ViewContent, AddToCart, InitiateCheckout, CompletePayment
- **Retention Window** — ระยะเวลาย้อนหลังที่ต้องการรวมคนเข้า Audience ตั้งได้ 1-180 วัน (เทียบเท่า Facebook Custom Audience ที่ตั้งได้ 1-365 วัน — TikTok มีเพดานสั้นกว่า Facebook)
- **URL Contains/Equals** — กรองเฉพาะคนที่เข้าหน้าที่มี URL ตรงกับเงื่อนไข (เช่น เฉพาะหน้าสินค้าหมวดหนึ่ง)
- **Frequency** — จำนวนครั้งขั้นต่ำที่ต้องเกิด Event นั้น (ใช้กรองคนที่ Engage หนักกว่าคนที่ผ่านมาแค่ครั้งเดียว)

### App Activity Audience

สำหรับธุรกิจที่มีแอปมือถือและติดตั้ง TikTok SDK/Events API เชื่อมกับ App Event สามารถสร้าง Custom Audience จากพฤติกรรมในแอปได้เช่นเดียวกัน เช่น คนที่เปิดแอปแต่ไม่ทำ Purchase ภายใน 7 วัน หรือคนที่ทำ Registration แล้วแต่ไม่กลับมาใช้งานต่อ

### ตารางเปรียบเทียบ Retention Window TikTok vs Facebook

| แพลตฟอร์ม | Retention Window สูงสุด | ค่าที่ใช้บ่อยสำหรับ Retargeting |
|---|---|---|
| TikTok Custom Audience | 180 วัน | 7, 14, 30, 60, 90, 180 วัน |
| Facebook Custom Audience | 365 วัน | 14, 30, 60, 90, 180 วัน |

ความหมายเชิงกลยุทธ์: ธุรกิจที่มี Purchase Cycle ยาวเกิน 180 วัน (เช่น อสังหาริมทรัพย์, รถยนต์, การศึกษาต่างประเทศ) จะไม่สามารถสร้าง Custom Audience ระยะยาวสุดขั้วแบบที่ทำได้บน Facebook (เช่น Website Visitors 365 วัน) ต้องวางแผนเก็บ Lead เข้า CRM หรือ Customer File แทนเพื่อ Retarget ระยะยาวกว่า 180 วัน

### Minimum Audience Size สำหรับใช้งานจริง

TikTok กำหนดขนาดขั้นต่ำของ Custom Audience ที่จะนำไปใช้ Targeting ได้จริงไว้ที่ประมาณ 1,000 คน (ตรวจสอบตัวเลขจริงในหน้า Ads Manager เสมอเพราะอาจปรับเปลี่ยน) ถ้า Audience มีขนาดเล็กกว่านี้ระบบจะแสดงสถานะ "ยังไม่พร้อมใช้งาน" จนกว่าจะมีคนเข้าเงื่อนไขมากพอ

### ตัวอย่างการใช้งานจริง

ร้านค้าออนไลน์เครื่องใช้ไฟฟ้าสร้าง Custom Audience 3 ระดับตามความลึกของ Funnel:

| ชื่อ Audience | Event | Window | วัตถุประสงค์ |
|---|---|---|---|
| WEB_ViewContent_180d | ViewContent | 180 วัน | Retargeting กว้าง สำหรับ Ad Group Awareness ต่อเนื่อง |
| WEB_AddToCart_30d | AddToCart | 30 วัน | Retargeting กลาง เตือนกลับมาดูสินค้าที่ค้างในตะกร้า |
| WEB_InitiateCheckout_NoPurchase_7d | InitiateCheckout minus CompletePayment | 7 วัน | Retargeting ร้อนแรงสุด เพื่อดันปิดการขายที่ทิ้งไว้กลางทาง |

### ข้อผิดพลาดที่พบบ่อย

1. ตั้ง Retention Window ยาวเกินความจำเป็นสำหรับสินค้า Impulse Buy ที่ Purchase Cycle สั้น ทำให้ Audience ปนคนที่หมดความสนใจไปแล้ว
2. ไม่รู้ว่า TikTok มีเพดาน Retention Window ที่ 180 วัน แล้ววางแผน Retargeting ระยะยาวแบบเดียวกับ Facebook 365 วันไม่ได้จนงงว่าทำไมตั้งค่าไม่ได้ตามที่ต้องการ
3. สร้าง Custom Audience จาก Event ที่ไม่ได้ Deduplicate กับ Purchase (เช่น InitiateCheckout ที่ไม่ได้ลบคนที่ซื้อไปแล้วออก) ทำให้ยิงซ้ำใส่คนที่ปิดการขายไปแล้ว
4. ไม่ตรวจสอบ EMQ/Match Rate ของ Pixel ก่อนสร้าง Custom Audience — ถ้า Pixel ยิง Event ไม่สมบูรณ์ Custom Audience ที่ได้จะเล็กและไม่แม่นยำกว่าที่ควรเป็น

---

## Step 825: TikTok Custom Audience จาก Customer File Upload

### หลักการพื้นฐาน

Customer File Audience สร้างจากข้อมูลลูกค้าที่ธุรกิจมีอยู่แล้ว (เบอร์โทร, อีเมล, TikTok User ID ถ้ามี) อัปโหลดเป็นไฟล์ CSV/TXT เพื่อให้ TikTok จับคู่กับบัญชีผู้ใช้บนแพลตฟอร์ม หลักการเดียวกับ Facebook Custom Audience จาก Customer List ที่เรียนใน Part 047 ทุกประการในเชิงแนวคิด

### โครงสร้างไฟล์ที่ TikTok รองรับ

| ประเภทข้อมูล | รูปแบบที่ต้องเตรียม | หมายเหตุ |
|---|---|---|
| หมายเลขโทรศัพท์ (Phone) | รูปแบบ E.164 (เช่น +66812345678) | ต้อง Hash ด้วย SHA-256 ก่อนอัปโหลด (หรือให้ระบบ Hash ให้อัตโนมัติถ้าอัปโหลดแบบ Plain Text ผ่านหน้าเว็บที่มีการเข้ารหัสระหว่างทาง) |
| อีเมล (Email) | ตัวพิมพ์เล็กทั้งหมด ไม่มีเว้นวรรค | Hash ด้วย SHA-256 เช่นเดียวกัน |
| TikTok User ID / Advertising ID (IDFA/GAID) | ตามที่ระบบ TikTok กำหนด | ใช้เมื่อมีข้อมูลจาก SDK/CRM ที่เก็บ ID เหล่านี้ไว้อยู่แล้ว |

### ขั้นตอนอัปโหลดแบบ Step-by-Step

1. เตรียมไฟล์ CSV ที่มี Column เดียวหรือหลาย Column (Phone, Email) ตามที่มี ไม่จำเป็นต้องมีครบทุกประเภท
2. ไปที่ **Assets → Audiences → Create Audience → Customer File**
3. เลือกประเภทข้อมูลที่จะอัปโหลด (Phone/Email/ID)
4. อัปโหลดไฟล์ ระบบจะ Hash และประมวลผลจับคู่โดยอัตโนมัติ (ใช้เวลาประมาณ 1-24 ชั่วโมงกว่า Audience จะพร้อมใช้)
5. ตั้งชื่อ Audience ตาม Naming Convention ที่เป็นระบบ

### Match Rate: ตัวเลขที่ต้องเข้าใจ

Match Rate คือสัดส่วนของรายชื่อในไฟล์ที่ TikTok หาบัญชีผู้ใช้ที่ตรงกันได้จริง โดยทั่วไป Match Rate ของ TikTok ในตลาดไทยอยู่ที่ประมาณ 30-55% ซึ่ง**ต่ำกว่า Facebook ที่มัก Match ได้ 60-80%** เหตุผลหลักคือฐานผู้ใช้ TikTok มีขนาดเล็กกว่า Facebook ในภาพรวม และผู้ใช้จำนวนมากลงทะเบียน TikTok ด้วยเบอร์/อีเมลที่ต่างจากที่ใช้ลงทะเบียนกับธุรกิจ (เช่น ใช้เบอร์รองสำหรับ Social Media)

| แพลตฟอร์ม | Match Rate เฉลี่ยในตลาดไทย |
|---|---|
| Facebook Custom Audience | 60-80% |
| TikTok Custom Audience (Customer File) | 30-55% |

**วิธีเพิ่ม Match Rate:** อัปโหลดทั้งเบอร์โทรและอีเมลพร้อมกันในไฟล์เดียว (ไม่ใช่แค่อย่างเดียว) เพราะระบบจะพยายามจับคู่จากทุก Field ที่มี ยิ่งมี Field มากยิ่งมีโอกาส Match สูงขึ้น และควรใช้ข้อมูลที่เป็นปัจจุบันที่สุด (ลูกค้าที่ Active ในช่วง 6-12 เดือนหลัง มักมี Match Rate สูงกว่าฐานลูกค้าเก่าหลายปี)

### ตัวอย่างการใช้งานจริง

ธุรกิจ SaaS B2B มีฐานข้อมูล Lead ที่ยังไม่ปิดการขายในระบบ CRM 25,000 รายชื่อ (มีทั้งเบอร์และอีเมล) อัปโหลดเป็น Customer File บน TikTok ได้ Match Rate 42% (ประมาณ 10,500 คน) นำไปสร้างเป็น Custom Audience สำหรับยิง Retargeting คู่กับ Creative ที่นำเสนอ Case Study ลูกค้าที่ใช้แล้วได้ผล ผล CPA ของ Lead ที่ Convert เป็น Demo Call ต่ำกว่าการยิง Prospecting ทั่วไปถึง 3 เท่า เพราะเป็นกลุ่มที่เคยแสดงความสนใจมาก่อนแล้ว

### ข้อผิดพลาดที่พบบ่อย

1. อัปโหลดเฉพาะอีเมลอย่างเดียวทั้งที่มีเบอร์โทรอยู่ในระบบด้วย ทำให้ Match Rate ต่ำกว่าที่ควรจะได้
2. ไม่ Hash ข้อมูลก่อนอัปโหลดในกรณีที่ใช้วิธีอัปโหลดผ่าน API โดยตรง (ต่างจากการอัปโหลดผ่านหน้าเว็บที่ระบบช่วย Hash ให้) ทำให้ระบบ Reject ไฟล์
3. ใช้ฐานข้อมูลลูกค้าเก่ามากเกินไป (เกิน 2-3 ปี) ที่ข้อมูลติดต่ออาจเปลี่ยนไปแล้ว ทำให้ Match Rate ต่ำผิดปกติ
4. คาดหวัง Match Rate เท่า Facebook แล้วมองว่า TikTok "มีบั๊ก" ทั้งที่ความจริงคือข้อจำกัดตามธรรมชาติของฐานผู้ใช้ที่เล็กกว่า

---

## Step 826: TikTok Engagement Audience — Video Views, Profile Visits, Business Account Engagement

### ภาพรวม Engagement Audience บน TikTok

Engagement Audience คือ Custom Audience ที่สร้างจากการ Interact กับคอนเทนต์/บัญชีของธุรกิจโดยตรงบนแพลตฟอร์ม TikTok เอง (ไม่ต้องพึ่งพา Pixel หรือไฟล์ภายนอก) เป็นแหล่งข้อมูลที่มีเอกลักษณ์เฉพาะของ TikTok เพราะอิงพฤติกรรมการเสพวิดีโอโดยตรง ตำแหน่งตั้งค่าอยู่ที่ **Assets → Audiences → Create Audience → Engagement**

### ประเภทของ Engagement Audience ที่สร้างได้

| ประเภท | เงื่อนไขที่เลือกได้ | Retention Window |
|---|---|---|
| **Video Views** | คนที่ดู Video Ad ของธุรกิจ ≥ % ที่กำหนด (25%, 50%, 75%, 95-100%) | 7-180 วัน |
| **Profile Visits (Business Account)** | คนที่เข้าดู Business Profile ของแบรนด์บน TikTok | 7-180 วัน |
| **Lead Generation Form Engagement** | คนที่เปิด/ส่ง/ไม่ส่ง TikTok Instant Form | 7-180 วัน |
| **Shopping Ads Engagement** | คนที่ Interact กับ Shopping Ads/TikTok Shop (View Product, Add to Cart, Purchase ผ่าน Shop) | 7-180 วัน |

### Video Views Audience: เครื่องมือที่ไม่มีบน Facebook แบบเดียวกัน

Facebook มี Video Engagement Custom Audience เช่นกัน (คนที่ดูวิดีโอ ≥ 25%/50%/75%/95%) แต่ TikTok ให้ความสำคัญกับ Audience ประเภทนี้มากกว่ามาก เพราะสอดคล้องกับธรรมชาติของแพลตฟอร์มที่วัดผลด้วย Watch Time เป็นหลัก (ตามที่จะเรียนละเอียดใน Part 085) การสร้าง Custom Audience จากคนที่ดูวิดีโอโฆษณาจบเกิน 75% แต่ไม่ได้คลิกลิงก์ เป็นกลุ่มที่มีค่ามากเพราะแสดงความสนใจสูงในคอนเทนต์แต่ยังไม่ได้ Action — เหมาะเป็นเป้าหมาย Retargeting ที่ใช้ CTA ที่แรงขึ้นในรอบถัดไป

### ตัวอย่างการแบ่งกลุ่มตาม Watch Percentage

| กลุ่ม | ความหมาย | กลยุทธ์ Retargeting ที่แนะนำ |
|---|---|---|
| ดู 25%+ | เห็นแค่ Hook เบื้องต้น ความสนใจต่ำสุด | ใช้ Creative คนละแบบ อาจ Hook ผิดกลุ่ม ไม่ควร Retarget หนัก |
| ดู 50%+ | ผ่าน Hook แล้วสนใจดูเนื้อหาต่อ | Retarget ด้วย Creative ที่ขยายรายละเอียด/Benefit เพิ่ม |
| ดู 75%+ | สนใจมาก ใกล้ดูจบ | Retarget ด้วย Offer/CTA ที่ชัดเจนขึ้น |
| ดู 95-100% | ดูจบเกือบทั้งหมด สัญญาณความสนใจสูงสุด | Retarget ด้วย Direct Offer/Promotion แบบเร่งให้ Action ทันที |

### กรณีศึกษาการใช้ Video Views Audience

แบรนด์คอร์สออนไลน์สอนทำอาหารสร้าง Ad Group Retargeting เฉพาะกลุ่มคนที่ดูวิดีโอโฆษณาความยาว 45 วินาทีจบเกิน 75% ในช่วง 14 วันที่ผ่านมา (ประมาณ 85,000 คน) แล้วยิง Creative รอบสองที่เป็น Testimonial ลูกค้าจริงพร้อมโปรโมชันจำกัดเวลา ผล Conversion Rate ของกลุ่มนี้สูงกว่ากลุ่ม Prospecting ทั่วไปถึง 5 เท่า และ CPA ต่ำกว่า 70% เพราะเป็นกลุ่มที่พิสูจน์แล้วว่าดูคอนเทนต์เต็มเวลาและสนใจหัวข้อจริง

### ข้อผิดพลาดที่พบบ่อย

1. ใช้แค่ Website Custom Audience (Pixel) โดยไม่รู้จัก Video Views Engagement Audience ทั้งที่เป็นแหล่งข้อมูลที่มีคุณค่ามากสำหรับธุรกิจที่ยังไม่มี Pixel Data สะสมมากพอ
2. Retarget กลุ่มดู 25%+ ด้วยความคาดหวังสูงเท่ากลุ่มดู 95%+ ทำให้ผลลัพธ์ไม่เป็นไปตามที่คาด
3. ไม่แยก Business Account Profile Visits ออกจาก Video Views ทั้งที่เป็นสัญญาณความสนใจคนละระดับ (คนที่เข้าไปดู Profile มักมีความสนใจสูงกว่าคนที่แค่ดูวิดีโอผ่านหน้า Feed)
4. ตั้ง Retention Window ของ Engagement Audience ยาวเกินไปจนปนคนที่ความสนใจเย็นลงไปแล้วเข้ามาในกลุ่ม Retargeting ที่ควรจะร้อน

---

## Step 827: TikTok Lookalike Audience — สร้างอย่างไร Source Audience ต้องเป็นแบบไหน

### หลักการพื้นฐานของ TikTok Lookalike

Lookalike Audience บน TikTok (บางบัญชีจะเห็นชื่อเมนูเป็น "Lookalike Audience" ตรงไปตรงมา) ทำงานตามหลักการเดียวกับ Facebook Lookalike ที่เรียนใน Part 048 คือใช้ Machine Learning หาคนที่มี "ลักษณะ/พฤติกรรมคล้ายกัน" กับกลุ่ม Source Audience ที่ระบุไว้ แต่เพราะ TikTok ไม่มี Social Graph ให้อ้างอิงแบบ Facebook (ตามที่อธิบายใน Step 823) การหาความคล้ายของ TikTok Lookalike จึงอิง **Pattern พฤติกรรมการเสพคอนเทนต์และการทำ Action บนแพลตฟอร์ม** เป็นหลัก มากกว่าอิงลักษณะ Demographic/Interest แบบตรงไปตรงมา

### Source Audience ที่ใช้สร้าง Lookalike ได้

| ประเภท Source | คุณภาพ Lookalike ที่ได้ | ขนาดขั้นต่ำที่แนะนำ |
|---|---|---|
| Customer File (ลูกค้าที่ซื้อแล้วจริง) | สูงสุด — Pattern การซื้อจริงชัดเจน | 1,000+ คน (แนะนำ 5,000+ เพื่อคุณภาพดีกว่า) |
| Website Custom Audience: Purchase Event | สูง — พฤติกรรมซื้อจริงบนเว็บ | 1,000+ คน |
| Website Custom Audience: ViewContent/AddToCart | กลาง — สนใจแต่ยังไม่ซื้อ | 1,000+ คน |
| Engagement Audience: Video Views 75%+ | กลาง — สนใจคอนเทนต์สูง แต่ไม่ได้ยืนยันว่าเป็นลูกค้า | 1,000+ คน |
| Engagement Audience: Video Views 25%+ | ต่ำ — สัญญาณอ่อน ไม่แนะนำเป็น Source หลัก | ใช้ได้แต่ควรมี Source อื่นควบคู่ |

หลักการเดียวกับ Facebook คือ **Source Audience ที่มีคุณภาพสูง (ใกล้เคียงลูกค้าจริงที่สุด) จะให้ Lookalike ที่มีคุณภาพสูงตามไปด้วย** — Garbage In, Garbage Out ใช้ได้กับทั้งสองแพลตฟอร์ม

### การตั้งขนาด Lookalike (Similarity/Reach Level)

TikTok ให้ตั้งระดับความคล้ายของ Lookalike เป็น Slider หรือ % แบบเดียวกับ Facebook 1%-10% แต่บางเวอร์ชัน UI ของ TikTok ใช้คำว่า "Balance" (Similar/Broad) แทนเปอร์เซ็นต์ตรง ๆ

| ระดับความคล้าย | ลักษณะ | เหมาะกับ |
|---|---|---|
| แคบ/คล้ายมากที่สุด (~1-2%) | คล้าย Source มากที่สุด แต่ Reach เล็ก | ธุรกิจที่ต้องการความแม่นยำสูงกว่า Reach เช่น Ticket Size สูง |
| กลาง (~3-5%) | สมดุลระหว่างความแม่นยำและ Reach | ธุรกิจทั่วไปที่ต้องการ Scale ต่อจาก Prospecting เดิม |
| กว้าง (~6-10%) | Reach ใหญ่แต่ความคล้ายลดลง | ธุรกิจที่ต้องการ Scale ปริมาณมากและมี Creative ที่ดีพอให้ AI ช่วยกรอง |

### ข้อจำกัดสำคัญที่ต่างจาก Facebook

Facebook Lookalike อ้างอิง Population ของประเทศเป้าหมายเป็นฐาน 100% แล้วเลือกเปอร์เซ็นต์ที่ใกล้เคียง Source มากที่สุด TikTok ใช้หลักการคล้ายกันแต่ฐานผู้ใช้ TikTok ในบางตลาด (รวมถึงไทย) มีขนาดเล็กกว่า Facebook มาก ทำให้ Lookalike ระดับกว้าง (6-10%) บน TikTok อาจให้ Audience Size ที่ดู "แคบ" กว่าที่คาดถ้าเทียบเปอร์เซ็นต์เดียวกันบน Facebook — ต้องดู Potential Reach จริงในหน้า Ads Manager เสมอ ไม่ใช่ยึดตัวเลข % อย่างเดียว

### ตัวอย่างการใช้งานจริง

ร้านค้าออนไลน์เครื่องสำอางมี Customer File ลูกค้าที่ซื้อซ้ำ (Repeat Purchase) 8,500 คน สร้าง Lookalike ระดับแคบ (2%) ได้ Audience ~180,000 คน และระดับกว้าง (7%) ได้ Audience ~620,000 คน ทดสอบยิงพร้อมกันด้วยงบเท่ากัน 2 สัปดาห์:

| Lookalike Level | Reach | CPA |
|---|---|---|
| แคบ (2%) | 180,000 | 145 บาท |
| กว้าง (7%) | 620,000 | 210 บาท |

บทเรียนคือ Lookalike แคบให้ CPA ต่ำกว่าเพราะใกล้เคียง Source (ลูกค้าซื้อซ้ำ) มากกว่า แต่ก็ Scale ได้จำกัดกว่าเพราะ Pool เล็ก ทีมจึงใช้กลยุทธ์ผสม คือใช้ Lookalike แคบเป็น Ad Group หลักที่ CPA ดี และใช้ Lookalike กว้างเป็น Ad Group สำรองสำหรับ Scale เพิ่มเมื่องบประมาณเพิ่มขึ้นและ Lookalike แคบเริ่มอิ่มตัว (Frequency สูงเกินจุดที่รับได้)

### ข้อผิดพลาดที่พบบ่อย

1. สร้าง Lookalike จาก Source Audience ที่คุณภาพต่ำ (เช่น Video Views 25%+) เพราะเป็น Audience ที่มีขนาดใหญ่พอสร้างได้ง่าย โดยไม่พิจารณาคุณภาพของ Pattern ที่จะได้
2. ใช้ Source Audience ขนาดเล็กเกินไป (ต่ำกว่า 1,000 คน) ทำให้ Lookalike ที่ได้ไม่แข็งแรงเพราะ Pattern ยังไม่ชัดเจนพอ
3. ตั้งความคาดหวัง Reach ของ % Lookalike เดียวกันให้เท่ากับที่เคยเห็นบน Facebook โดยไม่ตรวจสอบ Potential Reach จริงในตลาดไทยบน TikTok ก่อน
4. ไม่ Refresh Lookalike เป็นระยะ — เพราะ Behavior Pattern บน TikTok เปลี่ยนเร็ว Lookalike ที่สร้างจาก Source เมื่อ 6-12 เดือนก่อนอาจไม่สะท้อน Pattern ปัจจุบันแล้ว ควรสร้าง Lookalike ใหม่ทุก 2-3 เดือนโดยใช้ Source Audience ที่อัปเดตล่าสุด

---

## Step 828: Automated Targeting vs Custom Targeting — TikTok's Advantage+ Audience Equivalent

### TikTok Automated Targeting คืออะไร

**Automated Targeting** เป็น Toggle ที่อยู่คู่กับส่วน Targeting ใน Ad Group เมื่อเปิดใช้งาน ระบบ TikTok จะขยาย Targeting ออกไปเกินกว่าเงื่อนไข Demographics/Interest & Behavior ที่ตั้งไว้ โดยให้ Machine Learning ค้นหาคนที่มีโอกาส Convert สูงเพิ่มเติมนอกกลุ่มที่ระบุ หลักการเดียวกับ Advantage+ Audience ของ Facebook ที่เรียนใน Part 030 เป๊ะ ๆ ในเชิงแนวคิด — ต่างกันแค่ชื่อเรียกและรายละเอียดปลีกย่อยของ UI

### ตารางเปรียบเทียบ Automated Targeting (TikTok) vs Advantage+ Audience (Facebook)

| มิติ | TikTok Automated Targeting | Facebook Advantage+ Audience |
|---|---|---|
| ตำแหน่งตั้งค่า | Toggle ใน Ad Group → Targeting | Toggle ใน Ad Set → Audience Controls |
| เมื่อเปิดใช้ | ขยายเกิน Interest & Behavior ที่ตั้งไว้ แต่ยังคง Demographics (Location/Age/Gender) เป็น Hard Constraint | ขยายเกิน Detailed Targeting ที่ตั้งไว้ แต่ยังคง Location เป็น Hard Constraint เช่นกัน |
| การใส่ Suggestion | ใส่ Interest & Behavior เป็น "แนวทาง" ให้ AI อ้างอิง | ใส่ Detailed Targeting เป็น "Suggestion" ให้ AI อ้างอิง |
| ปิดใช้งานได้หรือไม่ | ปิดได้ในบัญชีส่วนใหญ่ (สลับเป็น Custom Targeting) | บางบัญชีถูกบังคับเปิดโดยไม่มีตัวเลือกปิด (Roll out แบบไม่พร้อมกันทุกบัญชี) |
| ระดับ Automation เมื่อรวมกับ Smart+ Campaign | Smart+ Campaign (จะเรียนใน Part 087) ผลักดัน Automation ไปอีกขั้น รวม Targeting+Creative+Bid | Advantage+ Shopping Campaign (ASC, Part 029) ทำหน้าที่คล้ายกัน |

### เมื่อไหร่ควรใช้ Custom Targeting (ปิด Automated Targeting)

1. **บัญชีใหม่ที่ยังไม่มี Pixel Data สะสม** — เหตุผลเดียวกับ Facebook คือ AI ยังไม่มีสัญญาณ Conversion พอเรียนรู้ การกำหนด Interest & Behavior ที่ตรง Persona ช่วยตั้งจุดเริ่มต้นที่ดีกว่า
2. **ธุรกิจที่มีข้อจำกัดทางกฎหมาย/อายุ** ต้องคุม Demographics อย่างเคร่งครัด (แม้ Automated Targeting จะไม่แตะ Demographics ก็ตาม แต่ธุรกิจกลุ่มนี้มักต้องการควบคุม Interest & Behavior ด้วยเพื่อความปลอดภัยด้าน Compliance)
3. **ช่วง Market Research หา Persona ใหม่** — ทดสอบ Interest & Behavior หลายชุดแบบ A/B เพื่อ "ถามตลาด" ก่อนปล่อยกว้าง
4. **ธุรกิจ Niche ที่มี Persona แคบชัดเจนมาก** เช่น อุปกรณ์กีฬาเฉพาะทาง ที่ Automated Targeting อาจขยายกว้างเกินจนปนกลุ่มที่ไม่มีกำลังซื้อหรือความสนใจจริง

### เมื่อไหร่ควรปล่อยให้ Automated Targeting ทำงานเต็มที่

1. Data Signal แข็งแรงแล้ว (Conversion สม่ำเสมอ, Pixel/Events API ทำงานดี)
2. สินค้า/บริการมีฐานลูกค้ากว้าง ไม่เฉพาะกลุ่มมาก
3. งบประมาณสูงพอให้ AI Explore ได้จริง (TikTok เองก็แนะนำงบขั้นต่ำที่สูงขึ้นเมื่อเปิด Automated Targeting เพื่อให้ระบบมีข้อมูลพอ Optimize)
4. ต้องการให้ระบบช่วยหา Segment ใหม่ที่ยังไม่เคยรู้จัก

### แนวทาง Hybrid ที่ใช้ได้จริง

เหมือนหลักการ Hybrid ที่เรียนใน Part 046 (Step 458) สำหรับ Facebook ทีมมืออาชีพส่วนใหญ่ไม่เลือกสุดทาง แต่สร้างโครงสร้าง Ad Group หลายตัวในแคมเปญเดียวกัน:

- Ad Group 1: Automated Targeting เปิดเต็มที่ ใส่ Interest & Behavior กว้าง ๆ เป็น Suggestion (งบ 40-50%)
- Ad Group 2: Custom Targeting แบบแคบที่พิสูจน์แล้วว่าดี (งบ 30%)
- Ad Group 3: Custom Targeting แบบทดสอบ Persona ใหม่ (งบ 20-30% สำหรับ Explore)

### ข้อผิดพลาดที่พบบ่อย

1. เปิด Automated Targeting ทันทีในบัญชีใหม่ที่ยังไม่มี Pixel Data โดยคาดหวังผลลัพธ์เท่าบัญชีที่มีข้อมูลสะสมแล้ว
2. ปิด Automated Targeting ตลอดไปเพราะความเคยชินกับ Manual Targeting แบบเดิม ทั้งที่ Data Signal พร้อมมากพอที่จะปล่อยกว้างแล้ว
3. ไม่ทดสอบเปรียบเทียบ Custom Targeting กับ Automated Targeting แบบมีระบบ (Parallel Test) ทำให้ไม่รู้สัดส่วนที่เหมาะกับบัญชีตัวเองจริง ๆ
4. สับสนระหว่าง Automated Targeting (ระดับ Ad Group) กับ Smart+ Campaign (ระดับ Campaign ที่ Automate มากกว่านี้อีกขั้น) — สองอย่างนี้ต่างระดับกัน จะเรียนแยกละเอียดใน Part 087

---

## Step 829: Audience Size Guidance, Exclusion Targeting, และข้อผิดพลาดคลาสสิก

### แนวทางประเมินขนาด Audience ที่เหมาะสมบน TikTok

หลักการใกล้เคียงกับที่เรียนใน Part 046 (Step 456) สำหรับ Facebook แต่ตัวเลขอ้างอิงต่างกันเพราะฐานผู้ใช้เล็กกว่า

| ระดับ Potential Reach (ประเทศไทย) | ลักษณะ | ความเสี่ยง |
|---|---|---|
| ต่ำกว่า 50,000 คน | แคบมาก | Learning ไม่จบ, CPM พุ่งเร็ว, Frequency สูงเร็วกว่าที่คาด |
| 50,000 – 300,000 คน | แคบ เหมาะกับ Niche/B2B | ต้องมีงบสอดคล้อง ไม่ใหญ่เกินความจำเป็น |
| 300,000 – 1,500,000 คน | กลาง เหมาะกับสินค้าทั่วไป | จุดสมดุลสำหรับ SME ส่วนใหญ่บน TikTok |
| 1,500,000 – 5,000,000 คน | กว้าง เหมาะกับ Mass Market | ต้องมี Creative ที่ดีพอให้ AI คัดกรอง |
| เกิน 5,000,000 คน | กว้างมาก | เหมาะกับ Awareness Campaign หรือปล่อยให้ Automated Targeting ทำงานเต็มที่ |

สังเกตว่าตัวเลขทุกระดับของ TikTok ต่ำกว่า Facebook ประมาณครึ่งหนึ่งถึงหนึ่งในสาม สะท้อนขนาดฐานผู้ใช้ที่เล็กกว่าในตลาดไทย ไม่ใช่ว่า TikTok Targeting "แคบกว่า" ในทางเทคนิค

### Exclusion Targeting บน TikTok

ตำแหน่งตั้งค่าอยู่ใน Ad Group → Targeting → Excluded Audience (แยกจากส่วน Include) รองรับการ Exclude ทั้ง Custom Audience, Interest Category, และ Behavior เหมือน Facebook

**ประเภทการ Exclude ที่ใช้บ่อยที่สุด:**

1. **Exclude Custom Audience ลูกค้าเดิมออกจาก Prospecting** — Exclude Purchase Custom Audience (30-90 วันตาม Purchase Cycle) จาก Ad Group Prospecting เพื่อไม่เลี้ยงงบซ้ำ
2. **Exclude Ad Group อื่นในแคมเปญเดียวกันที่มี Persona ทับซ้อน** — ใช้ Engagement Audience ของ Ad Group A มา Exclude จาก Ad Group B เพื่อลด Overlap
3. **Exclude Employee/Internal List** — ป้องกันข้อมูล Conversion เทียมจากพนักงานทดสอบ

### เกณฑ์การจัดการ Overlap ระหว่าง Ad Group

TikTok ไม่มี Audience Overlap Tool แบบตรงไปตรงมาเหมือน Facebook (ที่มีเมนู Show Audience Overlap ให้เทียบ % ชัดเจน) วิธีตรวจสอบ Overlap บน TikTok ต้องทำทางอ้อมโดย:

1. ดู Breakdown ผลลัพธ์ของแต่ละ Ad Group ว่ามี Pattern ผิดปกติหรือไม่ (เช่น CPM พุ่งพร้อมกันทั้งสอง Ad Group โดยไม่มีเหตุผลจากภายนอก)
2. ใช้ Custom Audience ของ Ad Group หนึ่งมาดูขนาดเทียบกับอีก Ad Group อย่างคร่าว ๆ (ถ้า Interest & Behavior ที่ตั้งไว้คล้ายกันมาก มักมี Overlap สูงโดยธรรมชาติ)
3. เมื่อสงสัยว่า Overlap สูง ให้ทดลองรวม Ad Group เป็นตัวเดียวแล้วเทียบผลลัพธ์ก่อน-หลัง

### ข้อผิดพลาดคลาสสิกในการ Targeting บน TikTok

1. **ยกยุทธศาสตร์ Audience Size จาก Facebook มาใช้ตรง ๆ** โดยไม่ปรับตัวเลขให้เข้ากับฐานผู้ใช้ TikTok ที่เล็กกว่า ทำให้ตั้ง Audience กว้างเกินความจำเป็นหรือแคบเกินจนไม่มีคนพอ
2. **ไม่ Exclude ลูกค้าเดิมออกจาก Prospecting** เหมือนที่เคยเรียนบน Facebook ทำให้เสียงบซ้ำซ้อน
3. **สร้าง Ad Group จำนวนมากทดสอบ Interest ต่างกันเล็กน้อยโดยไม่ระวัง Overlap** เพราะไม่มี Overlap Tool ตรง ๆ ให้เช็คง่ายเหมือน Facebook จึงมองข้ามปัญหานี้ไปเลย
4. **เชื่อว่า Interest & Behavior ที่ตั้งไว้จะคงประสิทธิภาพตลอดไป** โดยไม่ Refresh หรือทดสอบใหม่ทุก 2-3 เดือน ทั้งที่ TikTok เปลี่ยนเร็วกว่า Facebook มาก
5. **ปล่อย Automated Targeting เต็มที่ตั้งแต่วันแรกของบัญชีใหม่** โดยไม่มี Custom Targeting คู่กันเลย ทำให้ AI ไม่มีจุดอ้างอิงที่ดีพอในช่วงเริ่มต้น
6. **มองข้าม Engagement Audience** เพราะคุ้นเคยกับการพึ่งพา Pixel Data เป็นหลักจาก Facebook ทั้งที่ TikTok มี Engagement Audience ที่มีคุณภาพสูงและใช้งานได้เร็วกว่า (ไม่ต้องรอ Pixel สะสมข้อมูล)

---

## Step 830: Workshop — สร้าง TikTok Audience Library ฉบับสมบูรณ์สำหรับธุรกิจจริง 1 ราย

Step นี้คือ Workshop หลักของ Part นี้ ให้ลงมือทำจริงในบัญชี TikTok Ads Manager ของตัวเองหรือบัญชี Sandbox โดยใช้ธุรกิจเดียวกันหรือธุรกิจใหม่ที่ต้องการฝึก

### สินค้าตัวอย่างที่ใช้ในการฝึก

สมมติเลือกสินค้า: **แบรนด์เสื้อผ้าออกกำลังกายสำหรับผู้หญิง ราคาเฉลี่ยชุดละ 1,200 บาท ขายผ่านเว็บไซต์และ TikTok Shop**

### ขั้นตอนที่ 1 — วางแผนโครงสร้าง Audience Library แบบเต็มรูปแบบ

ก่อนเริ่มสร้างจริง ให้ออกแบบ Audience Library เป็นตารางลำดับชั้นตาม Funnel:

| ชั้น Funnel | ประเภท Audience | ตัวอย่างชื่อ |
|---|---|---|
| Cold (Core/Interest) | Custom Targeting: Interest+Behavior | CORE_FitnessWomen_18-34 |
| Cold (Automated) | Automated Targeting + Suggestion | AUTO_FitnessWomen_Suggestion |
| Warm (Engagement) | Video Views 50%+, Profile Visits | ENG_VideoView50_30d |
| Warm (Website) | Custom Audience: ViewContent/AddToCart | WEB_AddToCart_30d |
| Hot (Website) | Custom Audience: InitiateCheckout minus Purchase | WEB_ICO_NoPurchase_7d |
| Hot (Customer File) | ลูกค้าเดิมที่ซื้อซ้ำ | CUST_RepeatBuyer |
| Scale (Lookalike) | Lookalike จาก Purchase Custom Audience | LAL_Purchase_3pct |
| Exclusion | ลูกค้าเดิม/พนักงาน | EXCL_Purchaser_60d, EXCL_Employee |

### ขั้นตอนที่ 2 — สร้าง Custom Audience จริงทั้ง 4 แหล่ง

1. สร้าง **Website Custom Audience** จาก Pixel Event AddToCart (30 วัน) และ InitiateCheckout (7 วัน)
2. สร้าง **Customer File Audience** จากฐานลูกค้าเดิม (ถ้าไม่มีข้อมูลจริง ให้จำลองไฟล์ทดสอบเพื่อฝึกขั้นตอนอัปโหลด)
3. สร้าง **Engagement Audience** จาก Video Views 50%+ (30 วัน) และ Profile Visits (30 วัน)
4. สร้าง **Lookalike Audience** จาก Customer File หรือ Purchase Custom Audience ระดับความคล้าย 3-5%

### ขั้นตอนที่ 3 — สร้าง Custom Targeting Ad Group สำหรับ Persona เย็น (Cold)

ตั้ง Ad Group ใหม่พร้อม Interest Category "Fitness" + Behavior "Video Interaction: Fitness/Workout 15 วัน" ตาม Persona ที่วางแผนไว้ พร้อม Exclude Custom Audience ลูกค้าเดิม

### ขั้นตอนที่ 4 — สร้าง Automated Targeting Ad Group เทียบคู่

สร้าง Ad Group อีกตัวที่เปิด Automated Targeting พร้อมใส่ Interest & Behavior เดียวกันเป็น Suggestion เพื่อเทียบผลลัพธ์กับ Ad Group Custom Targeting

### ขั้นตอนที่ 5 — บันทึกและเปรียบเทียบ

จดตัวเลข Potential Reach ของทุก Audience ที่สร้าง ลงในตารางเปรียบเทียบ พร้อมเขียนสรุปเชิงกลยุทธ์ตอบคำถาม:

1. Audience ไหนมี Potential Reach เหมาะกับงบประมาณที่มีจริง?
2. Custom Targeting กับ Automated Targeting ควรแบ่งงบสัดส่วนเท่าไหร่สำหรับบัญชีนี้?
3. ถ้างบจำกัดต้องเลือก Custom Audience มาใช้ Retargeting ก่อนแค่ 1 ตัว จะเลือกตัวไหนและเพราะอะไร?
4. Lookalike ที่สร้างควรตั้งระดับความคล้ายเท่าไหร่ให้เหมาะกับงบที่มี?

### Case Study อ้างอิงสำหรับ Workshop นี้

แบรนด์เสื้อผ้าออกกำลังกาย "FitWear" (ชื่อสมมติ) ทำ Workshop แบบเดียวกันนี้จริง พบว่า Engagement Audience จาก Video Views 50%+ (30 วัน) มี Potential Reach เล็กที่สุดในกลุ่ม Warm (ประมาณ 95,000 คน) แต่ให้ CPA ต่ำที่สุดเมื่อนำไป Retarget ด้วย Creative ที่เป็น Testimonial (CPA 180 บาท เทียบกับ Website AddToCart Audience ที่ 240 บาท) เพราะกลุ่มที่ดูวิดีโอจบครึ่งหนึ่งขึ้นไปแสดงความสนใจในระดับ Content ที่สูงกว่าคนที่แค่กด AddToCart แล้วเงียบไป บทเรียนคือ Engagement Audience ที่เป็นเอกลักษณ์ของ TikTok ไม่ควรถูกมองข้ามเพียงเพราะนักยิงแอดคุ้นเคยกับ Pixel-based Audience จาก Facebook มากกว่า

---

## เทคนิคขั้นสูง: การจัดการ Audience Library ในระดับเอเจนซี่/หลายบัญชี

### ปัญหาที่พบเมื่อดูแลหลายบัญชีพร้อมกัน

เอเจนซี่ที่ดูแลลูกค้าหลายรายบน TikKtok มักเจอปัญหาเดียวกับที่เคยเจอบน Facebook Business Manager (Part 011) คือ Audience ที่สร้างไว้ในบัญชีหนึ่งไม่สามารถแชร์ข้าม Business Center ได้โดยตรงถ้าไม่ได้ตั้งค่า Asset Sharing ไว้ล่วงหน้า ทำให้บางทีมสร้าง Audience ซ้ำซ้อนกันในหลายบัญชีโดยไม่รู้ตัว

### แนวทางการจัดระบบที่แนะนำ

1. **ตั้ง Naming Convention ระดับองค์กร** ที่ใช้ Prefix บอกบัญชี/ลูกค้าด้วย เช่น `[ClientCode]_[ประเภท]_[Persona]_[Window]` เพื่อไม่ให้สับสนเมื่อเปิดดูหลายบัญชีสลับกันในวันเดียว
2. **ทำ Audience Registry กลาง** เป็น Sheet ที่บันทึกว่าแต่ละบัญชีมี Audience อะไรบ้าง สร้างจากแหล่งไหน Retention Window เท่าไหร่ อัปเดตล่าสุดเมื่อไหร่ — ป้องกันการสร้างซ้ำและช่วยให้ทีมใหม่เข้าใจโครงสร้างได้เร็ว
3. **กำหนดรอบ Audit Audience ทุกไตรมาส** ตรวจว่า Audience ตัวไหนไม่ได้ใช้งานแล้วควรลบ ตัวไหนควร Refresh (โดยเฉพาะ Lookalike ที่ Pattern เปลี่ยนเร็ว)
4. **แยก Business Center ตามลูกค้าอย่างเคร่งครัด** ไม่ผสม Asset ของลูกค้าคนละรายในบัญชีเดียวกัน แม้จะดูแลโดยทีมเดียวกันก็ตาม เพื่อป้องกันปัญหาความเป็นส่วนตัวของข้อมูลลูกค้าแต่ละราย

### ตารางเปรียบเทียบภาระงานดูแล Audience: TikTok vs Facebook สำหรับเอเจนซี่

| งาน | TikTok | Facebook |
|---|---|---|
| ความถี่ในการ Refresh Lookalike | สูง (ทุก 2-3 เดือน) | ปานกลาง (ทุก 3-6 เดือน) |
| ความถี่ในการทดสอบ Interest/Behavior ใหม่ | สูง (เทรนด์เปลี่ยนเร็ว) | ปานกลาง |
| การตรวจ Overlap | ต้องทำทางอ้อมผ่าน Breakdown (ไม่มี Tool ตรง) | มี Audience Overlap Tool ให้ใช้ตรง |
| การจัดการ Match Rate ต่ำ | ต้องเตรียมข้อมูลหลาย Field เพื่อชดเชย | Match Rate สูงอยู่แล้วโดยธรรมชาติ |

---

## Case Study สรุปท้าย Part: คลินิกทำเล็บพรีเมียมสร้าง Audience Library จากศูนย์จนหา Persona ที่ใช่

คลินิกทำเล็บพรีเมียมแห่งหนึ่งในกรุงเทพฯ เริ่มยิง TikTok Ads โดยใช้ Custom Targeting เดี่ยว ๆ คือ Interest "Beauty & Personal Care" กว้าง ๆ Location กรุงเทพฯ Age 20-40 ผลลัพธ์เดือนแรก CTR 0.9% และ CPA ต่อการทักแชทจองคิวสูงถึง 220 บาท

ทีมงานกลับมาวางแผน Audience Library ใหม่ตามหลักการ Workshop ของ Part นี้ โดยสร้าง Engagement Audience จาก Video Views 75%+ ของวิดีโอที่โชว์ผลงานเล็บจริง (30 วัน) และ Custom Audience จาก Business Account Profile Visits ควบคู่กับการเปิด Automated Targeting เป็น Ad Group เทียบคู่ พบว่า:

| Ad Group | Targeting | CTR | CPA ต่อการจองคิว |
|---|---|---|---|
| เดิม | Custom: Interest กว้าง | 0.9% | 220 บาท |
| ใหม่ 1 | Custom: Interest+Behavior แคบ | 1.6% | 145 บาท |
| ใหม่ 2 | Automated Targeting + Suggestion | 2.1% | 110 บาท |
| ใหม่ 3 (Retarget) | Engagement: Video Views 75%+ | 3.8% | 65 บาท |

ทีมย้ายงบส่วนใหญ่ไปที่ Ad Group ใหม่ 2 และ 3 และใช้ Ad Group ใหม่ 1 เป็น Custom Targeting สำรองสำหรับช่วงที่ Automated Targeting เริ่มอิ่มตัว ผล CPA เฉลี่ยรวมของคลินิกลดลงจาก 220 บาท เหลือ 95 บาทภายในเดือนที่สอง บทเรียนสำคัญคือการมี Audience Library ที่ครบทุกชั้น (Cold/Warm/Hot/Automated) และทดสอบเทียบกันอย่างเป็นระบบ ให้ผลลัพธ์ที่ดีกว่าการยิง Interest เดี่ยว ๆ กว้าง ๆ อย่างมาก

---

## FAQ ที่พบบ่อยเกี่ยวกับ TikTok Audience Targeting

**Q1: TikTok Audience Insights มีเครื่องมือแบบ Audience Insights ของ Facebook ไหม**

TikTok ไม่มีเครื่องมือชื่อเดียวกัน แต่มี **TikTok Creative Center** (เรียนใน Part 081) ที่ให้ข้อมูลเชิง Demographic ของ Trending Hashtags/Sounds ทางอ้อม และมี **Audience Insights ภายใน TikTok Ads Manager** ระดับพื้นฐานที่แสดง Breakdown ของ Ad Group ที่รันจริง (Age/Gender/Location/Placement) ซึ่งเป็นวิธีหลักที่แนะนำให้ใช้ เพราะสะท้อนพฤติกรรมจริงของธุรกิจตัวเอง ไม่ใช่ค่าเฉลี่ยทั่วไป

**Q2: ทำไม Custom Audience ที่สร้างจาก Customer File ใช้เวลานานกว่าจะพร้อมใช้งาน**

การ Hash และจับคู่ข้อมูลกับฐานผู้ใช้ TikTok ใช้เวลาประมวลผลตั้งแต่ 1-24 ชั่วโมงขึ้นอยู่กับขนาดไฟล์และปริมาณงานของระบบในขณะนั้น ควรอัปโหลดล่วงหน้าก่อนวันที่ต้องการเริ่มยิงจริงเสมอ ไม่ควรอัปโหลดแล้วคาดหวังใช้งานได้ทันที

**Q3: ควรใช้ Lookalike จาก Purchase Custom Audience หรือจาก Customer File ดีกว่ากัน**

ถ้ามีทั้งสองแหล่งและมีขนาดใหญ่พอ (1,000+ คน) ทั้งคู่ใช้ได้ดี แต่ Customer File มักให้ Pattern ที่ "สะอาด" กว่าเพราะเป็นข้อมูลที่ธุรกิจยืนยันเองว่าเป็นลูกค้าจริง (ไม่ปนคน Refund หรือ Fraud Order ที่อาจติดมากับ Pixel Event) ในขณะที่ Website Custom Audience อาจปนคน Test Order หรือ Bot Traffic ได้ถ้าเว็บไซต์ไม่มีการป้องกันที่ดี แนะนำให้ Clean ฐานข้อมูล Customer File ก่อนใช้เป็น Source ของ Lookalike เสมอ

**Q4: Interest & Behavior ที่ตั้งไว้ตอนเปิด Automated Targeting มีผลแค่ไหนจริง ๆ**

TikTok ระบุว่า Interest & Behavior ที่ใส่ไว้ตอนเปิด Automated Targeting ทำหน้าที่เป็น "แนวทาง" ให้ AI อ้างอิงในช่วงต้น ไม่ใช่ Hard Constraint เหมือน Custom Targeting ล้วน ๆ ในทางปฏิบัติน้ำหนักของ Suggestion นี้มักลดลงเรื่อย ๆ เมื่อระบบสะสม Conversion Data มากขึ้น คล้ายกับหลักการ Advantage+ Audience Suggestion ของ Facebook ทุกประการ

**Q5: ทำไมบัญชีเราไม่เห็นตัวเลือกปิด Automated Targeting**

เช่นเดียวกับ Facebook ที่ Roll out Advantage+ Audience แบบไม่พร้อมกันทุกบัญชี TikTok ก็ทยอย Roll out การบังคับ Automated Targeting ในบางตลาด/บาง Objective เป็นระยะเช่นกัน ไม่ใช่บั๊ก แต่เป็นการทดสอบและปรับ Roll out ของ TikTok เอง ถ้าบัญชีถูกบังคับเปิด ให้ปรับกลยุทธ์มาที่การใส่ Suggestion ที่ดีที่สุดแทนการพยายามหาทางปิด

**Q6: ธุรกิจที่ขายผ่าน TikTok Shop อย่างเดียว (ไม่มีเว็บไซต์ตัวเอง) จะสร้าง Custom Audience จากอะไรได้บ้าง**

ธุรกิจกลุ่มนี้ยังสร้าง Custom Audience ได้จากหลายแหล่งโดยไม่ต้องพึ่ง Website Pixel เลย คือ (1) Shopping Ads Engagement Audience ที่อิงพฤติกรรม View Product/Add to Cart/Purchase ผ่าน TikTok Shop โดยตรง (2) Engagement Audience จาก Video Views และ Profile Visits (3) Customer File จากฐานข้อมูลลูกค้าที่ TikTok Shop ส่งออกมาให้ (Order History Export) นำมาอัปโหลดเป็น Customer File ได้ (4) Lookalike ที่สร้างต่อจากทั้งสามแหล่งข้างต้น สรุปคือแม้ไม่มีเว็บไซต์ก็ยังมี Audience Library ที่ครบเกือบทุกชั้นได้ เพียงแต่ต้องพึ่งพา On-platform Signal มากกว่าธุรกิจที่มีเว็บไซต์ควบคู่ด้วย

**Q7: Custom Audience ที่สร้างจาก Ad Group หนึ่ง เอาไปใช้กับ Ad Group อื่นในบัญชีเดียวกันได้ไหม**

ได้ Custom Audience ที่สร้างในระดับ Assets ไม่ได้ผูกติดกับ Ad Group ใดเป็นการเฉพาะ สามารถนำไปใช้ Include หรือ Exclude ใน Ad Group ไหนก็ได้ภายในบัญชีเดียวกัน (หรือข้ามบัญชีได้ถ้าตั้งค่า Asset Sharing ผ่าน Business Center ไว้แล้ว) หลักการเดียวกับ Saved Audience/Custom Audience ของ Facebook ที่นำไปใช้ซ้ำได้ในหลาย Ad Set

## Checklist ท้ายบท

- [ ] เข้าใจความแตกต่างของ Core/Demographic Targeting ระหว่าง TikTok กับ Facebook โดยเฉพาะเรื่อง Radius Targeting ที่ TikTok ไม่มี
- [ ] รู้จักหมวด Interest Category และ 3 ประเภทของ Behavior (Video/Creator/Hashtag Interaction) ที่เป็นเอกลักษณ์ของ TikTok
- [ ] เข้าใจว่า TikTok Targeting เป็น Content-Behavior-Based มากกว่า Social-Graph-Based และปรับสัดส่วนความสำคัญของ Creative ให้สูงขึ้นตามนั้น
- [ ] สร้าง Website Custom Audience จาก Pixel/Events API ได้จริง พร้อมเข้าใจเพดาน Retention Window 180 วัน
- [ ] อัปโหลด Customer File Audience ได้จริง และเข้าใจว่า Match Rate ของ TikTok ต่ำกว่า Facebook ตามธรรมชาติ
- [ ] สร้าง Engagement Audience จาก Video Views/Profile Visits ได้จริง และเข้าใจคุณค่าของ Watch Percentage ที่ต่างกัน
- [ ] สร้าง Lookalike Audience จาก Source ที่มีคุณภาพสูง และตั้งระดับความคล้ายให้เหมาะกับงบประมาณ
- [ ] มีกรอบตัดสินใจชัดเจนว่าเมื่อไหร่ใช้ Custom Targeting เมื่อไหร่ปล่อยให้ Automated Targeting ทำงาน
- [ ] มี Exclusion Strategy พื้นฐานอย่างน้อย Exclude ลูกค้าเดิมและพนักงานในทุกแคมเปญ Prospecting
- [ ] มี Audience Library ครบทุกชั้น Funnel (Cold/Warm/Hot/Automated/Exclusion) สำหรับธุรกิจ/ลูกค้าที่ดูแล

## Workshop / แบบฝึกหัด

ทำตาม Step 830 อย่างละเอียดกับสินค้า/บริการของตัวเองหรือของลูกค้า โดยส่งมอบผลงาน 4 ชิ้นตามนี้:

1. **เอกสาร Audience Library แบบตาราง** ครบทุกชั้น Funnel (Cold/Warm/Hot/Automated/Exclusion) พร้อมชื่อ Audience ตาม Naming Convention ที่เป็นระบบ
2. **Custom Audience จริง 4 แหล่งในบัญชี TikTok Ads Manager** (Website, Customer File, Engagement, Lookalike) พร้อม Screenshot ตัวเลข Potential Reach ของแต่ละตัว
3. **Ad Group เทียบคู่ Custom Targeting vs Automated Targeting** พร้อมบันทึกผลลัพธ์เบื้องต้นหลังรันจริงอย่างน้อย 3-7 วัน
4. **ตารางสรุปเชิงกลยุทธ์** ตอบคำถาม 4 ข้อจากขั้นตอนที่ 5 ของ Step 830

โบนัส: ถ้ามีบัญชีที่มี Pixel Data สะสมอยู่แล้ว ให้ทดสอบ Engagement Audience (Video Views 50%+) เทียบกับ Website Custom Audience (AddToCart) แบบ Parallel Test งบเท่ากัน 1 สัปดาห์ แล้วเปรียบเทียบ CPA จริง

## สรุปและเชื่อมไปยัง Part ถัดไป

Part นี้ปูพื้นให้เข้าใจ TikTok Audience Targeting อย่างครบทุกมิติ ตั้งแต่ Core/Demographic Targeting ที่มีข้อจำกัดต่างจาก Facebook ความแตกต่างเชิงกลไกที่ทำให้ TikTok เป็น Content-Behavior-Based มากกว่า Social-Graph-Based ไปจนถึง Custom Audience จากทุกแหล่งข้อมูล (Pixel, Customer File, Engagement) Lookalike Audience และกรอบตัดสินใจระหว่าง Custom Targeting กับ Automated Targeting ทั้งหมดนี้คือรากฐานที่ทำให้ครีเอทีฟที่ผลิตมาอย่างดีใน Section H ไปเจอกลุ่มเป้าหมายที่ใช่จริง

Part ถัดไป (Part 084) จะพาไปเจาะลึก **TikTok Retargeting และ Funnel Strategy** ซึ่งเป็นการนำ Custom Audience และ Engagement Audience ที่เรียนใน Part นี้ไปใช้สร้างระบบ Retargeting แบบเต็มรูปแบบ ตั้งแต่การเลือก Retargeting Window ที่เหมาะกับแต่ละ Event Type การออกแบบ Sequential Messaging ที่เข้ากับสไตล์คอนเทนต์ TikTok ไปจนถึงการวางโครงสร้างแคมเปญ Full-Funnel TOF-MOF-BOF ที่ปรับให้เข้ากับธรรมชาติ Content-first ของแพลตฟอร์มนี้

## อ้างอิง/แหล่งข้อมูลเพิ่มเติม

- TikTok for Business Help Center: หมวด "Audience Targeting" และ "Custom Audiences"
- TikTok for Business: "About Lookalike Audiences" และเอกสารเรื่อง Similarity Level
- TikTok Marketing API Documentation: Custom Audience Endpoint (สำหรับทีมพัฒนาที่ต้องอัปโหลด Customer File ผ่าน API)
- Part 048 ของหลักสูตรนี้ — Facebook Lookalike Audience แบบเจาะลึก (ใช้เทียบหลักการ)
- Part 064 ของหลักสูตรนี้ — ระบบนิเวศ TikTok Ads และความแตกต่างจาก Facebook (พื้นฐานความเข้าใจที่ใช้ต่อใน Part นี้)
- Part 066 ของหลักสูตรนี้ — TikTok Pixel และ Events API (พื้นฐานทางเทคนิคสำหรับ Step 824)
- Part 087 ของหลักสูตรนี้ (Section I) — TikTok Automated Rules และ Smart+ Campaigns (ขยายความเรื่อง Automation ต่อจาก Step 828)
