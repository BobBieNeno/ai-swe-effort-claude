# AI SWE Workflow & Effort Scaling Plugin (`ai-swe-effort`)

ปลั๊กอินที่ผสานแนวคิดของ **`open-effort`** (Dynamic Effort Scaling, Auto-Escalation, Status Band, Main Flow) เข้ากับ **`ai-swe-workflow`** ที่พัฒนาต่อยอดให้ใช้ได้กับ**ทุกโปรเจกต์และทุก Tech Stack (Universal / Project-Agnostic)** พร้อมระบบทีมเอเจนท์ (Multi-Agent Team), ไฟล์กระดานสถานะกลาง (`docs/AGENT_SYNC.md`) และการสื่อสารระหว่างเอเจนท์ (`send_message`)

---

## 🚀 วิธีการติดตั้ง (Installation)

### 1. ติดตั้งเฉพาะโปรเจกต์ (Project Scope - แนะนำ)
หากต้องการใช้เฉพาะโปรเจกต์ใดโปรเจกต์หนึ่ง โดยไม่ให้กระทบการตั้งค่า Global ให้เปิด Terminal ที่โฟลเดอร์โปรเจกต์นั้นแล้วรัน:

```bash
# เพิ่ม Marketplace
claude plugin marketplace add BobBieNeno/ai-swe-effort-claude

# ติดตั้งเฉพาะโปรเจกต์ปัจจุบัน
claude plugin install ai-swe-effort@ai-swe-effort --scope project
```

หรือหากกำลังเปิดเซสชัน **Claude Code** อยู่ สามารถพิมพ์คำสั่ง:
```bash
/plugin marketplace add BobBieNeno/ai-swe-effort-claude
/plugin install ai-swe-effort@ai-swe-effort --scope project
```

### 2. ติดตั้งแบบ Global (ทุกโปรเจกต์)
```bash
claude plugin marketplace add BobBieNeno/ai-swe-effort-claude
claude plugin install ai-swe-effort@ai-swe-effort
```

### 3. ติดตั้งผ่าน Claude Desktop App
1. ไปที่ **Settings** → **Customize** → **Plugins**
2. คลิก **+ Add** → **Add marketplace**
3. พิมพ์ `BobBieNeno/ai-swe-effort-claude` แล้วกด **Sync**
4. ค้นหา **ai-swe-effort** แล้วกด **Add/Install**

---

## 🌟 ฟีเจอร์หลัก (Key Features)

1. **ทำงานอัตโนมัติทันทีที่เปิดปลั๊กอิน (`rules/AGENTS.md` / `CLAUDE.md`):**
   - แสดง **Status Band** บรรทัดแรกของคำตอบเสมอ: `⚡ [Effort: LOW|MEDIUM|HIGH|XHIGH] | [Stage: 1-GRILL..5-RETRO] | [Team: ...] | [Sync: docs/AGENT_SYNC.md] | [Retry: 0/3]`
   - โหมดตอบกระชับแบบ Caveman 2.0 สไตล์ Technical Thai-English (ตัดคำฟุ่มเฟือย แต่คงความถูกต้อง 100%)
2. **ไฟล์กลางประสานงาน (`docs/AGENT_SYNC.md`) & การสื่อสารระหว่างเอเจนท์:**
   - **Shared Blackboard (`docs/AGENT_SYNC.md`):** บันทึกสถานะงาน ไฟล์ที่กำลังแก้ และข้อมูลที่ค้นพบ เพื่อให้เอเจนท์และผู้ใช้เข้าใจตรงกัน
   - **Direct Agent Messaging:** รองรับโปรโตคอลสื่อสารและส่งต่องานระหว่างเอเจนท์
3. **แบ่งทีมและประหยัด Token อัตโนมัติ (Multi-Agent Team & Token Optimization):**
   - **Lead Architect:** วางแผน ออกแบบสถาปัตยกรรม และตัดสินใจเรื่องยาก
   - **Codebase Scout:** สำรวจไฟล์ อ่าน JSON/API Spec ขนาดใหญ่แทนแชทหลัก
   - **Builder Worker:** เขียนโค้ดย่อยและอัปเดต mock ตามแผน
   - **QA Verifier:** รันตรวจสอบ Type-check / Lint / Test จริง
4. **ทำงานตามลำดับ 5 ขั้นตอน (5-Stage Sequential Pipeline):**
   - `1-GRILL` → `2-PLAN` (Safety Gate สำหรับงาน High-Impact) → `3-EXECUTE` → `4-VERIFY` → `5-RETRO`
5. **Safety Gate (ความปลอดภัย & กฎหมาย):**
   - หยุดขออนุมัติจากผู้ใช้ก่อนเสมอ เมื่องานกระทบ Security, PDPA/PII, Financial Calculation, Database Migration, หรือ Breaking API Contract
