---
description: Run the 5-Stage Universal AI SWE Workflow with Dynamic Effort Scaling, Team Roles, and docs/AGENT_SYNC.md
---

Execute the Universal AI SWE Workflow × Open-Effort pipeline for the user's request:
1. Display the Status Band on line 1: `⚡ [Effort: LOW|MEDIUM|HIGH|XHIGH] | [Stage: 1-GRILL..5-RETRO] | [Team: Lead / Scout(haiku) / Builder(sonnet) / QA] | [Sync: docs/AGENT_SYNC.md] | [Retry: 0/3]`
2. Check/update `docs/AGENT_SYNC.md` and follow the 5 sequential stages (`1-GRILL` -> `2-PLAN` -> `3-EXECUTE` -> `4-VERIFY` -> `5-RETRO`).
3. Enforce the Human Decision Gate on all High-Impact Legal (PDPA/Audit/License), Security (OWASP/Auth/RBAC), Financial, and Database tasks before writing code.
