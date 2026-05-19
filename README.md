# 🌲 SkillTree — Command Cheat Sheet

เอกสารสรุปคำสั่งและแนวทางการใช้งาน Add-on ทั้งหมดของ **SkillTree** เพื่อเพิ่มประสิทธิภาพการเขียนโค้ด การวางแผน การทดสอบ (QA) และการดูแลระบบ (DevOps) สำหรับสแต็ก **Next.js + NestJS + PostgreSQL** ของคุณ

---

## 🛠️ 1. Setup & Dashboard Commands (การติดตั้งและดูแผงควบคุม)

ชุดคำสั่งสำหรับเริ่มต้นใช้งาน ตรวจเช็คสถานะ และสแกนเลือกดูองค์ประกอบทั้งหมดในคลัง SkillTree:

### 🖥️ Dashboard GUI (แผงควบคุมแบบหน้าจอสวยงาม)

เปิดแอปพลิเคชันหน้าจอเพื่อสแกน ค้นหา และดูประวัติของ Agents, Skills, และ Rules ทั้งหมดแบบเห็นภาพ:

```bash
# รันผ่าน Python (แนะนำ)
python ./ecc_dashboard.py

# หรือรันผ่าน npm
npm run dashboard
```

### ⚡ PowerShell Installation Script (สคริปต์ติดตั้งสำหรับ Windows)

คำสั่งสำหรับคัดลอกไฟล์ Agents, Rules และ Skills ที่เกี่ยวข้องกับโปรเจกต์ของคุณไปเก็บไว้ใน Claude เพื่อเปิดใช้งาน:

```powershell
# ติดตั้งแบบ Minimal (แนะนำ: เบาเครื่อง ไม่ลง hook ส่วนเกิน)
# พร้อมระบุกลุ่ม Add-on ที่เราเลือก (typescript, web, planning, testing, devops)
.\install.ps1 --profile minimal --target claude typescript web planning tdd-workflow e2e-testing deployment-patterns docker-patterns
```

### 📦 Installation Fallback via NPX

ทางเลือกสำหรับติดตั้งด่วนโดยใช้ Node Package Executor:

```powershell
npx ecc-install --profile minimal --target claude typescript web
```

### 🧠 ECC Advisor (ที่ปรึกษาระบบอัจฉริยะ)

หากไม่แน่ใจว่าต้องการใช้ไฟล์ไหนเพิ่มเติม ให้ระบบช่วยค้นหาและแนะนำตัวเลือกที่สอดคล้องกับหัวข้อนั้นๆ:

```powershell
npx ecc consult "typescript react" --target claude
npx ecc consult "postgresql migrations" --target claude
```

---

## 📋 2. Claude Code Slash Commands (คำสั่งสำหรับพิมพ์ในห้องแชท Claude)

หากติดตั้งในระบบเสร็จสมบูรณ์แล้ว คุณสามารถพิมพ์คำสั่งย่อเหล่านี้ลงในแถบแชทของ **Claude Code** ได้โดยตรงเพื่อเรียกใช้งาน Agents และคลังความรู้ (Skills) ทันที:

| คำสั่ง (Slash Command)      | เอเจนต์ที่ทำงานเบื้องหลัง | จุดประสงค์ในการใช้งาน                                                            |
| :-------------------------- | :------------------------ | :------------------------------------------------------------------------------- |
| `/plan "[เป้าหมายฟีเจอร์]"` | `planner`                 | **วางแผน:** ช่วยย่อยฟีเจอร์ใหญ่ออกเป็นทีละ Phase ก่อนลงมือทำ                     |
| `/tdd`                      | `tdd-guide`               | **สร้างเทสก่อนโค้ด:** รันลูปสร้าง Unit/Integration test ให้ผ่านเกณฑ์ 80%         |
| `/e2e`                      | `e2e-runner`              | **ทดสอบการใช้งานจริง:** รันเบราว์เซอร์อัตโนมัติเช็ค Flow หน้าเว็บด้วย Playwright |
| `/code-review`              | `code-reviewer`           | **ตรวจทานโค้ด:** เช็คความสะอาดของโค้ด คุณภาพ และความถูกต้องก่อน Merge            |
| `/build-fix`                | `build-error-resolver`    | **แก้บั๊กเวลา Build:** ช่วยวิเคราะห์และแก้ไข TS/NestJS build error ให้ทันที      |
| `/security-scan`            | `security-reviewer`       | **สแกนความปลอดภัย:** สแกนหาช่องโหว่ (เช่น SQL Injection) และจุดรั่วไหล           |
| `/sessions`                 | -                         | **จัดการประวัติ:** เรียกดูประวัติการพูดคุยของเซสชันที่ผ่านมา                     |
| `/instinct-status`          | -                         | **ดูการเรียนรู้:** ดูแนวทาง/Instincts ที่ Claude เรียนรู้จากคุณในรอบก่อนๆ        |

---

## 📂 3. Recommended Skills & Agents for Your Stack ( Next + Nest + Postgres )

นี่คือรายชื่อโฟลเดอร์หลักในคลัง `C:\Users\HIBC-Sarunpat.s\Desktop\RAM\ECC` ที่คุณดึงไปใช้งาน เพื่อให้ตรงกับโปรเจกต์ของคุณมากที่สุด:

### 🏗️ หมวดการวางแผนและการออกแบบ (Planning & Architecture)

> [!TIP]
> ก่อนเริ่มโค้ดทุกครั้ง แนะนำให้เรียกใช้ตัวช่วยเหล่านี้เพื่อวาง Blueprint ที่แม่นยำ

- **Agent Path:** `agents/planner.md`
- **Skills Paths:**
  - `skills/product-capability/` (แปลงไอเดียจาก PRD ให้พร้อมเอาไปเขียนโค้ด)
  - `skills/search-first/` (ศึกษาข้อมูลเพื่อประเมินความเสี่ยงและวิเคราะห์ Edge Cases ก่อนเขียนโค้ด)

### 💻 หมวดหน้าบ้านและหลังบ้าน (TypeScript & NestJS & Web)

> [!NOTE]
> กฎการเขียนโค้ด โครงสร้าง และสไตล์เพื่อให้ระบบโหลดและตอบสนองได้เสถียรที่สุด

- **Rules Paths:** `rules/typescript/`, `rules/web/`, `rules/common/`
- **Agent Path:** `agents/typescript-reviewer.md`
- **Skills Paths:**
  - `skills/coding-standards/` (มาตรฐานการเขียนโค้ดและระเบียบวินัยที่ดี)
  - `skills/frontend-patterns/` (สำหรับการทำ State และ UI ใน Next.js)
  - `skills/backend-patterns/` (สถาปัตยกรรม API, Dependency Injection ใน NestJS)
  - `skills/nextjs-turbopack/` & `skills/bun-runtime/` (เพื่อความเร็วสูงสุดในการคอมไพล์)

### 🗄️ หมวดจัดการฐานข้อมูล (PostgreSQL Specialist)

> [!IMPORTANT]
> กฎเหล็กในการทำ Database Migrations และลดภาระโหลดของฐานข้อมูล

- **Agent Path:** `agents/database-reviewer.md`
- **Skills Paths:**
  - `skills/postgres-patterns/` (การทำดัชนี Indexing, การจอยตาราง และการจูนคิวรีให้เร็วขึ้น)
  - `skills/database-migrations/` (การทำ Migration แบบย้อนกลับได้ ไม่มีปัญระบบล่มตอนย้ายข้อมูล)
  - `skills/clickhouse-io/` (สำหรับวิเคราะห์ Logs หรือ Big Data เผื่อขยายระบบในอนาคต)

### 🧪 หมวดเขียนเทสและตรวจเช็คคุณภาพ (Tester & QA)

> [!WARNING]
> ป้องกันปัญหา "โค้ดเสร็จแล้วแต่รันจริงพัง" ด้วยระบบเขียนเทสรอบด้าน

- **Agent Paths:**
  - `agents/tdd-guide.md` (รันกระบวนการเขียน Unit/Integration test)
  - `agents/e2e-runner.md` (ทดสอบ Flow การใช้งานบนหน้าจอจริงผ่านเบราว์เซอร์อัตโนมัติ)
  - `agents/silent-failure-hunter.md` (ดักตรวจจับจุดที่ระบบแคช Error ไปซ่อนเงียบๆ)
- **Skills Paths:**
  - `skills/tdd-workflow/` (คู่มือแนวทางการจัดสัดส่วนและ Mock ข้อมูลภายนอก)
  - `skills/e2e-testing/` (การจัดการ Page Object Model เพื่อให้เทสหน้าจอเสถียร)
  - `skills/verification-loop/` (ระบบ Grader เช็คผลลัพธ์ว่าถูกต้องไร้บั๊กชัวร์ๆ)

### 🌀 หมวดดูแลระบบและท่อส่งอัตโนมัติ (DevOps & Docker)

> [!NOTE]
> ช่วยแปลงแอปพลิเคชันของคุณขึ้นสู่ระบบจริงอย่างรวดเร็วและปลอดภัยระดับโลก

- **Skills Paths:**
  - `skills/deployment-patterns/` (วิธียกแอปขึ้นเซิร์ฟเวอร์แบบไร้ Downtime, การตั้งค่า GitHub Actions CI/CD)
  - `skills/docker-patterns/` (การทำ Dockerfile แบบ Multi-stage ที่สลิมและบูสต์เร็วสุดขีด)
