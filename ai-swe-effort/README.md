# AI SWE Workflow & Effort Scaling Plugin (`ai-swe-effort`)

ปลั๊กอินที่ผสานแนวคิดของ **`open-effort`** (Dynamic Effort Scaling, Auto-Escalation, Status Band, Main Flow) เข้ากับ **`ai-swe-workflow`** ที่พัฒนาต่อยอดให้ใช้ได้กับ**ทุกโปรเจกต์และทุก Tech Stack (Universal / Project-Agnostic)** พร้อมระบบทีมเอเจนท์ (Multi-Agent Team), ไฟล์กระดานสถานะกลาง (`docs/AGENT_SYNC.md`) และการสื่อสารระหว่างเอเจนท์ (`send_message`)

## ฟีเจอร์หลัก

1. **ทำงานอัตโนมัติทันทีที่เปิดปลั๊กอิน (`rules/AGENTS.md`):**
   - ไม่ต้องคอยพิมพ์พรอมต์สั่งทุกครั้ง
   - แสดง **Status Band** บรรทัดแรกของคำตอบเสมอ: `⚡ [Effort: LOW|MEDIUM|HIGH|XHIGH] | [Stage: 1-GRILL..5-RETRO] | [Team: ...] | [Sync: docs/AGENT_SYNC.md] | [Retry: 0/3]`
   - ตอบภาษาไทยกระชับ ตรงประเด็น ใช้ศัพท์เทคนิคภาษาอังกฤษตามมาตรฐาน Software Engineer
2. **ไฟล์กลางประสานงาน (`docs/AGENT_SYNC.md`) & การคุยกันระหว่างเอเจนท์:**
   - **Shared Blackboard (`docs/AGENT_SYNC.md`):** สร้างและอัปเดตไฟล์กลางในโฟลเดอร์ `docs/` ของโปรเจกต์โดยอัตโนมัติ เพื่อบันทึกว่าเอเจนท์ตัวไหนทำอะไรไปแล้ว กำลังแก้ไฟล์ไหนอยู่ (ป้องกันการแก้ทับกัน) และส่งต่อข้อมูลที่ค้นพบให้เอเจนท์ตัวอื่นรู้เรื่องทันที (ดูแม่แบบที่ `skills/ai-swe-workflow/resources/AGENT_SYNC.template.md`)
   - **Direct Agent Messaging (`invoke_subagent` + `send_message`):** หัวหน้าทีม (`Lead`) และ `Subagent` สามารถส่งข้อความคุยโต้ตอบและสั่งงานต่อเนื่องผ่าน `conversationId` ได้โดยตรงโดยไม่ต้องสร้างเอเจนท์ใหม่ซ้ำซ้อน
3. **แบ่งทีมและประหยัด Token อัตโนมัติ (Multi-Agent Team & Token Optimization):**
   - **Lead Architect (Argon/Pro):** วางแผนและตัดสินใจเรื่องยาก
   - **Codebase Scout (`flash_lite`/`flash`):** สำรวจไฟล์และอ่าน JSON/API Spec ขนาดใหญ่แทนแชทหลัก
   - **Builder Worker (`flash`):** เขียนโค้ดย่อยและอัปเดต mock ตามแผน
   - **QA Verifier:** รันตรวจสอบ Type-check / Lint / Test จริง
4. **ทำงานตามลำดับ 5 ขั้นตอน & ไต่ระดับอัตโนมัติเมื่อเกิดปัญหา:**
   - เรียงลำดับ `1-GRILL` → `2-PLAN` (พร้อม Safety Gate สำหรับงาน High-Impact) → `3-EXECUTE` → `4-VERIFY` → `5-RETRO`
   - รายงานผลทุกครั้งที่เปลี่ยนขั้น และหากรันตรวจไม่ผ่าน 3 ครั้งติดต่อกัน (`Retry 3/3`) จะขยับระดับ Effort ขึ้น 1 ขั้นพร้อมดึงงานกลับมาให้โมเดลหลักวิเคราะห์รากปัญหาใหม่ทันที
