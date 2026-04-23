## สรุปข้อมูลที่มีอยู่

ข้อมูลของคุณคือ **แบบสอบถามงานวิจัย** เรื่อง **"อิทธิพลของอินฟลูเอนเซอร์ต่อความตั้งใจซื้อเครื่องสำอางออนไลน์ของ Gen Z ในกรุงเทพฯ"**

### โครงสร้างข้อมูล
| ส่วน | คอลัมน์ | เนื้อหา |
|------|---------|---------|
| คำถามคัดกรอง | 1-4 | อยู่ กทม.?, เป็น Gen Z?, เคยซื้อเครื่องสำอาง? |
| **ข้อมูลทั่วไป** | 5-9 | เพศ, อายุ, การศึกษา, อาชีพ, รายได้ |
| **พฤติกรรม** | 10-15 | ความถี่ซื้อ, เวลาตัดสินใจ, ช่องทาง, งบประมาณ |
| **ตัวแปรอิสระ (Likert 1-5)** | 16-41 | 6 ด้าน: Informative, Entertainment, Expertise, Trustworthiness, Attractiveness, Similarity |
| **ตัวแปรตาม (Likert 1-5)** | 42-46 | ความตั้งใจซื้อ (Purchase Intention) 5 ข้อ |

- **จำนวนข้อมูลที่ใช้ได้จริง: ~60 คน** (จาก 999 แถว มีแถวว่างเยอะ)
- Likert scale: ค่า 2-5 (ไม่มีใครตอบ 1 เลย)

---

## สิ่งที่คุณสามารถทำได้ (Step-by-Step ตั้งแต่ 0)

### ระดับ 1: เตรียมข้อมูล (ต้องทำก่อนวิเคราะห์ทุกอย่าง)

#### Step 1.1 — ทำความสะอาดข้อมูล
ข้อมูลมีแถวว่างเยอะมาก (937 แถว) ต้องเอาออกก่อน

**ใน SPSS:**
1. เปิดไฟล์ `File → Import Data → Excel` เลือกไฟล์ `ข้อมูลแบบสอบถาม.xlsx`
2. ลบแถวที่ไม่มีข้อมูล: `Data → Select Cases → If condition is satisfied`
3. เขียนเงื่อนไข: ตัวแปร "เพศ" ไม่เท่ากับค่าว่าง
4. เหลือข้อมูลประมาณ 60 คน

#### Step 1.2 — ตั้งค่าตัวแปรใน Variable View
ไปที่แท็บ **Variable View** แล้วตั้งค่าทุกตัวแปร:

| ตัวแปร | Type | Measure | Values |
|--------|------|---------|--------|
| เพศ | Numeric | Nominal | 1=ชาย, 2=หญิง |
| อายุ | Numeric | Ordinal | 1=14-18, 2=19-24, 3=25-29 |
| การศึกษา | Numeric | Ordinal | 1=ต่ำกว่าป.ตรี, 2=ป.ตรี, 3=ป.โท |
| อาชีพ | Numeric | Nominal | 1=นักศึกษา, 2=พนักงาน, 3=อิสระ |
| รายได้ | Numeric | Ordinal | 1=<5000, 2=5001-15000, 3=>15000 |
| ข้อ Likert ทั้งหมด | Numeric | Scale | 1=น้อยที่สุด ... 5=มากที่สุด |

**สำคัญมาก:** ข้อมูลปัจจุบันเป็น Text (เช่น "2.หญิง") ต้อง **Recode** เป็นตัวเลขก่อน:
- `Transform → Recode into Different Variables`
- เปลี่ยน "1.ชาย" → 1, "2.หญิง" → 2 เป็นต้น

---

### ระดับ 2: วิเคราะห์สถิติเชิงพรรณนา (Descriptive Statistics)

#### Step 2.1 — วิเคราะห์ข้อมูลทั่วไปของผู้ตอบ (Frequency)
**จุดประสงค์:** รู้ว่าผู้ตอบแบบสอบถามเป็นใครบ้าง

```
Analyze → Descriptive Statistics → Frequencies
→ ใส่ตัวแปร: เพศ, อายุ, การศึกษา, อาชีพ, รายได้
→ OK
```
**ผลที่ได้:** ตารางแสดง จำนวน (N) และ เปอร์เซ็นต์ (%) เช่น หญิง 80%, ชาย 20%

#### Step 2.2 — วิเคราะห์ค่าเฉลี่ยรายด้าน (Descriptives / Mean)
**จุดประสงค์:** รู้ว่าผู้ตอบให้ความสำคัญกับปัจจัยอะไรมากที่สุด

```
Analyze → Descriptive Statistics → Descriptives
→ ใส่ข้อ Likert ทั้งหมด (คอลัมน์ 16-46)
→ Options: เลือก Mean, Std. Deviation, Min, Max
→ OK
```
**ผลที่ได้:** ค่าเฉลี่ย ($\bar{x}$) และส่วนเบี่ยงเบนมาตรฐาน (S.D.) ของแต่ละข้อ

**การแปลผล Likert 5 ระดับ:**
| ค่าเฉลี่ย | ความหมาย |
|-----------|----------|
| 1.00-1.80 | น้อยที่สุด |
| 1.81-2.60 | น้อย |
| 2.61-3.40 | ปานกลาง |
| 3.41-4.20 | มาก |
| 4.21-5.00 | มากที่สุด |

---

### ระดับ 3: ทดสอบคุณภาพเครื่องมือ

#### Step 3.1 — Cronbach's Alpha (ความเชื่อมั่น)
**จุดประสงค์:** ทดสอบว่าแบบสอบถามมีความน่าเชื่อถือหรือไม่

```
Analyze → Scale → Reliability Analysis
→ ใส่ข้อคำถามรายด้าน (เช่น ด้าน Informative 5 ข้อ)
→ Model: Alpha
→ Statistics: เลือก "Scale if item deleted"
→ OK
```
**ต้องทำ 7 ครั้ง** (6 ด้านตัวแปรอิสระ + 1 ด้านตัวแปรตาม):

| ด้าน | จำนวนข้อ |
|------|---------|
| 3.1 Informative Value | 5 ข้อ |
| 3.2 Entertainment Value | 4 ข้อ |
| 3.3 Expertise | 3 ข้อ |
| 3.4 Trustworthiness | 5 ข้อ |
| 3.5 Attractiveness | 5 ข้อ |
| 3.6 Similarity | 4 ข้อ |
| 4.1 Purchase Intention | 5 ข้อ |

**เกณฑ์:** Alpha $\geq$ 0.70 = ผ่าน (ยิ่งใกล้ 1.00 ยิ่งดี)

---

### ระดับ 4: ทดสอบสมมติฐาน (Inferential Statistics)

#### Step 4.1 — Pearson Correlation (สหสัมพันธ์)
**จุดประสงค์:** ดูว่าแต่ละด้านมีความสัมพันธ์กับ Purchase Intention หรือไม่

**ก่อนทำ:** ต้อง Compute ค่าเฉลี่ยรายด้านก่อน
```
Transform → Compute Variable
→ Target Variable: mean_informative
→ Numeric Expression: MEAN(ข้อ3.1.1, ข้อ3.1.2, ข้อ3.1.3, ข้อ3.1.4, ข้อ3.1.5)
→ OK
```
ทำซ้ำสำหรับทั้ง 6 ด้าน + Purchase Intention

**จากนั้น:**
```
Analyze → Correlate → Bivariate
→ ใส่ค่าเฉลี่ยทุกด้าน + Purchase Intention
→ Pearson, Two-tailed
→ OK
```

**การแปลผล:**
| ค่า r | ระดับความสัมพันธ์ |
|-------|-----------------|
| 0.00-0.25 | น้อยมาก |
| 0.26-0.50 | น้อย |
| 0.51-0.75 | ปานกลาง |
| 0.76-1.00 | มาก |

ดูค่า **Sig. (2-tailed)** — ถ้า < 0.05 แสดงว่ามีนัยสำคัญทางสถิติ

#### Step 4.2 — Multiple Regression (การถดถอยพหุคูณ)
**จุดประสงค์:** ดูว่าปัจจัยไหนมีอิทธิพลต่อ Purchase Intention มากที่สุด **(นี่คือหัวใจของงานวิจัย)**

```
Analyze → Regression → Linear
→ Dependent: mean_purchase_intention
→ Independent(s): mean_informative, mean_entertainment,
   mean_expertise, mean_trustworthiness,
   mean_attractiveness, mean_similarity
→ Method: Enter (หรือ Stepwise)
→ Statistics: เลือก Estimates, Model fit, Collinearity diagnostics
→ OK
```

**ผลที่ได้:**
- $R^2$ = ตัวแปรอิสระอธิบายตัวแปรตามได้กี่ %
- **Beta ($\beta$)** = ค่าน้ำหนักมาตรฐาน — ยิ่งสูง ยิ่งมีอิทธิพลมาก
- **Sig.** < 0.05 = ปัจจัยนั้นมีอิทธิพลอย่างมีนัยสำคัญ
- **VIF** < 10 = ไม่มีปัญหา Multicollinearity

---

### ระดับ 5: วิเคราะห์เปรียบเทียบ (เพิ่มเติม ถ้าต้องการ)

#### Step 5.1 — Independent Samples t-test
**จุดประสงค์:** เปรียบเทียบความตั้งใจซื้อระหว่าง **ชาย vs หญิง**
```
Analyze → Compare Means → Independent Samples T Test
→ Test Variable: mean_purchase_intention
→ Grouping Variable: เพศ (Define Groups: 1, 2)
→ OK
```

#### Step 5.2 — One-Way ANOVA
**จุดประสงค์:** เปรียบเทียบความตั้งใจซื้อระหว่าง **กลุ่มอายุ 3 กลุ่ม**
```
Analyze → Compare Means → One-Way ANOVA
→ Dependent: mean_purchase_intention
→ Factor: อายุ
→ Post Hoc: Scheffe หรือ LSD
→ OK
```

---

### ระดับ 6: สร้างกราฟ
```
Graphs → Chart Builder
→ เลือก Bar Chart สำหรับข้อมูลทั่วไป (เพศ, อายุ)
→ เลือก Clustered Bar สำหรับเปรียบเทียบค่าเฉลี่ยรายด้าน
```

---

## ลำดับการทำงานที่แนะนำ (Checklist)

| ลำดับ | สิ่งที่ต้องทำ | เครื่องมือ SPSS |
|-------|-------------|----------------|
| 1 | นำเข้าข้อมูล Excel | File → Import Data → Excel |
| 2 | ลบแถวว่าง / ทำความสะอาด | Data → Select Cases |
| 3 | Recode ข้อความเป็นตัวเลข | Transform → Recode |
| 4 | ตั้งค่า Variable View | Variable View tab |
| 5 | Frequency ข้อมูลทั่วไป | Analyze → Frequencies |
| 6 | ค่าเฉลี่ย + S.D. รายข้อ | Analyze → Descriptives |
| 7 | Cronbach's Alpha 7 ด้าน | Analyze → Scale → Reliability |
| 8 | Compute ค่าเฉลี่ยรายด้าน | Transform → Compute Variable |
| 9 | Correlation | Analyze → Correlate → Bivariate |
| 10 | Multiple Regression | Analyze → Regression → Linear |
| 11 | t-test / ANOVA (เสริม) | Analyze → Compare Means |
| 12 | สร้างกราฟ | Graphs → Chart Builder |

---

## ข้อควรระวัง

1. **ข้อมูลยังน้อย (~60 คน)** — สำหรับ Multiple Regression ที่มี 6 ตัวแปรอิสระ ควรมีอย่างน้อย 60-120 คน (10-20 เท่าของตัวแปรอิสระ) คุณอยู่ที่ขอบล่างพอดี ถ้าเก็บเพิ่มได้จะดีมาก
2. **ข้อมูลเป็น Text** — ต้อง Recode เป็นตัวเลขก่อนวิเคราะห์ทุกอย่าง
3. **ไม่มีใครตอบ Likert = 1** — อาจหมายความว่ามี response bias ให้บันทึกเป็นข้อจำกัดของงานวิจัย
4. **แถวว่างเยอะมาก (937/999)** — Google Form อาจมีปัญหา ให้ตรวจสอบว่าการตั้งค่า validation ถูกต้อง

ต้องการให้ช่วยทำขั้นตอนไหนเพิ่มเติม หรืออยากให้สร้าง syntax SPSS สำเร็จรูปก็บอกได้เลย 

