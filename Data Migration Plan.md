# Data Migration Execution Plan

**Purpose:** Single plan that defines tools, team, ownership, timeline, and metadata (connections/tables). Based on Objects Mapping, Data Migration Standards, and Object Grouping.

**When to use:** Draft in Planning phase after Field Mappings sign-off; get client sign-off before building checklist and pipelines.

---

## 1. Scope Summary

| Item | Reference |
|------|-----------|
| Objects in scope | Objects Mapping Sheet |
| Load order | Data Migration Object Groups and Order of Execution |
| Standards | Data Migration Standards document |

---

## 2. Tools to Migrate

| Tool | Use Case | Objects / Notes |
|------|----------|------------------|
| Data Loader | Manual/small loads; User; one-off | User, [list] |
| Azure Data Factory / Synapse | Automated pipelines; bulk | Account, Contact, Opportunity, [list] |
| Manual / Spreadsheet | Exceptions | [if any] |
| Other | [Specify] | [list] |

---

## 3. Team, Ownership and Responsibilities

| Role | Name | Responsibility |
|------|------|-----------------|
| Client Comms | [Name] | Status updates; client sign-offs; scope decisions |
| Build | [Name] | Source/target queries; pipelines; Data Loader config |
| Data Validation | [Name] | Validation queries; Migration Audit Sheet; phased volume checks |
| Sign-off (Client) | [e.g. Joe] | Client sign-off on deliverables and data |
| Sign-off (Internal) | [e.g. bbs] | Internal sign-off on checklist and data |

---

## 4. Timeline

| Phase | Start | End | Key Deliverables |
|-------|--------|-----|-------------------|
| Discovery | [Date] | [Date] | Objects, Standards, Grouping, Field Mappings signed off |
| Planning | [Date] | [Date] | Execution Plan and Checklist signed off |
| Build | [Date] | [Date] | Queries, pipelines, audit sheet ready |
| Execution | [Date] | [Date] | All loads run; backups; phased validation |
| Sign-off | [Date] | [Date] | Internal then Client Data Sign-off |

---

## 5. Build Metadata

Document the following so the build team can implement:

| Item | Description |
|------|-------------|
| **Source connection** | e.g. SQL Server connection string / key vault ref; read-only user |
| **Target connection** | Salesforce org (sandbox/production); ingestion user; endpoint |
| **Database / tables** | Source database name; key tables per object (or views) |
| **Classification files path** | Folder or repo path for user, record type, picklist CSVs |
| **Backup procedure** | How and where target backup is taken after each pipeline run |

---

## 6. Asana (or Project Tool)

- All playbook tasks must be created **step-by-step in Asana** (or agreed tool).
- Map each step from the Data Migration Checklist to a task/subtask so progress is traceable.

---

## 7. Sign-off

**Client sign-off on Data Migration Execution Plan:**

Signed: _______________________ Date: _______
