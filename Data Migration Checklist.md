# Data Migration Checklist (Plan and Execution)

**Purpose:** Templatized checklist customized per project. Use for both planning and execution; track in Asana (or agreed tool).

---

## Discovery Phase

| # | Task | Owner | Status | Sign-off |
|---|------|--------|--------|----------|
| 1 | Discovery Session(s) – identify scope of objects | | ☐ Not started ☐ Done | |
| 2 | Draft 'Objects Mapping Sheet' to Migrate | | ☐ Not started ☐ Done | |
| 3 | Review and get sign-off on 'Objects' with the Client | | ☐ Not started ☐ Done | Client |
| 4 | Draft 'Data Migration Standards' | | ☐ Not started ☐ Done | |
| 5a | Review and get sign-off on 'Data Migration Standards' | | ☐ Not started ☐ Done | Client |
| 5b | Draft 'Data Migration Object Grouping' charts (order + ingestion method) | | ☐ Not started ☐ Done | |
| 6 | Review and get sign-off on 'Data Migration Object Grouping' charts | | ☐ Not started ☐ Done | Client |
| 7 | Draft 'Fields Mapping Sheets' (all objects) | | ☐ Not started ☐ Done | |
| 8 | Draft 'Classification Files' (user, record type, picklist) | | ☐ Not started ☐ Done | |
| 9 | Review and get sign-off on 'Fields Mapping Sheets' | | ☐ Not started ☐ Done | Client |

---

## Planning Phase

| # | Task | Owner | Status | Sign-off |
|---|------|--------|--------|----------|
| 10 | Draft 'Data Migration Execution Plan' (tools, team, timeline) | | ☐ Not started ☐ Done | |
| 10b | Build Metadata (source/target connections; database tables) | | ☐ Not started ☐ Done | |
| 11 | Review and get sign-off on 'Data Migration Execution Plan' | | ☐ Not started ☐ Done | Client |
| 12 | Draft 'Data Migration Checklist' – customize from template | | ☐ Not started ☐ Done | |
| 13 | Review and sign-off 'Data Migration Checklist' (Internal) | | ☐ Not started ☐ Done | Internal (e.g. bbs) |

---

## Build Phase

| # | Task | Owner | Status | Sign-off |
|---|------|--------|--------|----------|
| 14a | Build Source Queries | | ☐ Not started ☐ Done | |
| 14b | Build Target Queries / Field Maps | | ☐ Not started ☐ Done | |
| 14c | Build Skeleton Pipelines | | ☐ Not started ☐ Done | |
| 14d | Build Validation Queries and Scripts | | ☐ Not started ☐ Done | |
| 15 | Build and Update 'Migration Audit Sheet' (counts) | | ☐ Not started ☐ Done | |
| 16 | Run Pipelines / Data Loader Loads (in object order; backup after each) | | ☐ Not started ☐ Done | |
| 17 | Internal Data Sign-off (phased volume validation) | | ☐ Not started ☐ Done | Internal |
| 18 | Client Data Sign-off | | ☐ Not started ☐ Done | Client (e.g. Joe) |

---

## Execution Order Reminder

- Load objects in the **exact order** in Data Migration Object Groups and Order of Execution.
- **Backup** target after each pipeline run.
- **Upsert** only; External ID as key.
- **Bypass automation** for ingestion user.

---

## Asana

- Create a task (or subtask) for each row above so the full playbook is step-by-step in Asana.
