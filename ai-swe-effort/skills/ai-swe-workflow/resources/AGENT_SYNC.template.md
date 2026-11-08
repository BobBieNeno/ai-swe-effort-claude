# 📋 Agent Sync & Project Handoff Board (`docs/AGENT_SYNC.md`)

> ไฟล์กลางสำหรับติดตามความคืบหน้า แบ่งหน้าที่ และส่งต่องานระหว่างเอเจนท์ทั้งหมดในโปรเจกต์ (จัดการโดยปลั๊กอิน `ai-swe-effort`)

## 1. สถานะงานปัจจุบัน (Current Session Status)
- **หัวข้องาน (Active Goal):** `<ระบุเป้าหมายงานปัจจุบัน>`
- **ระดับความซับซ้อน (Effort Level):** `LOW | MEDIUM | HIGH | XHIGH`
- **ขั้นตอนปัจจุบัน (Current Stage):** `1-GRILL | 2-PLAN | 3-EXECUTE | 4-VERIFY | 5-RETRO`
- **จำนวนครั้งที่ลองแก้ (Retry Count):** `0/3`
- **อัปเดตล่าสุด:** `<YYYY-MM-DD HH:mm>`

---

## 2. ตารางแบ่งหน้าที่ทีมเอเจนท์ (Multi-Agent Roster & File Locks)

| บทบาท (Role) | โมเดล (Model) | Conversation ID / Link | งานที่รับผิดชอบ (Assigned Task) | ไฟล์ที่กำลังแตะ (Locked/Target Files) | สถานะ (Status) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Lead Architect** | Primary (Argon/Pro) | `main` | วางแผน Architecture, ตัดสินใจจุดเสี่ยง, ตรวจรวม | `docs/AGENT_SYNC.md` | ⏳ กำลังทำงาน |
| **Scout-1** | `flash_lite` / `flash` | `[Scout-1](conversation://<id>)` | สำรวจ pattern เดิมและ API spec | *(Read-only)* | ✅ เสร็จแล้ว |
| **Builder-1** | `flash` | `[Builder-1](conversation://<id>)` | พัฒนาส่วนที่ได้รับมอบหมาย | `<ระบุไฟล์>` | ⏳ กำลังทำงาน |
| **QA Verifier** | `flash` / Primary | `main` | รัน type-check, lint, test, mock verify | *(Verification)* | ⏸️ รอคิว |

---

## 3. ข้อมูลกลางที่ค้นพบ & การส่งต่องาน (Shared Context & Handoff Notes)
*(บันทึกสิ่งที่ Scout หรือ Builder ค้นพบ เพื่อให้เอเจนท์ตัวอื่นนำไปใช้ต่อได้ทันทีโดยไม่ต้องค้นหาซ้ำ)*

- **Project Conventions & Tech Stack:**
  - `<เช่น ใช้ TanStack Query ที่ src/lib/query, Custom components ที่ src/components>`
- **API Contracts / Shared Types ที่ตกลงกัน:**
  - `<ระบุชื่อ interface, endpoint path, หรือโครงสร้างข้อมูลที่เชื่อมระหว่างเอเจนท์>`
- **ข้อความส่งต่อถึงเอเจนท์ตัวถัดไป (Handoff Instructions):**
  - `<เช่น Builder-1 สร้าง hook เสร็จแล้วที่ไฟล์ X ให้ Builder-2 นำไปผูกกับหน้า UI ที่ไฟล์ Y ได้เลย>`

---

## 4. บันทึกความคืบหน้าและปัญหาระหว่างขั้นตอน (Stage Checkpoints & Issue Log)

- **[Stage 1 - GRILL]:** `<สรุปผลการวิเคราะห์โจทย์และสำรวจระบบเดิม>`
- **[Stage 2 - PLAN]:** `<สรุปแผนงานและการยืนยัน Safety Gate (ถ้ามี)>`
- **[Stage 3 - EXECUTE]:** `<สรุปไฟล์ที่แก้ไขและการอัปเดต Mock>`
- **[Stage 4 - VERIFY]:** `<ผลการรัน Type-check / Lint / Test>`
- **[Stage 5 - RETRO]:** `<สรุปการส่งมอบงานและข้อควรระวัง>`

### ⚠️ ประวัติปัญหาและการแก้ไข (Incident & Escalation Log)
- *(ว่าง — หากเกิดปัญหาจะบันทึก Stage, สาเหตุรากฐาน, Retry N/3 และการไต่ระดับ Effort ที่นี่)*
