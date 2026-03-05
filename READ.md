# Data Migration Playbook – Salesforce

Step-by-step playbook for Salesforce data migrations: **Discovery → Planning → Build**, with client and internal sign-offs at each phase.

---

## Flow (high level)

1. **Discovery** – Scope objects → Objects Mapping Sheet → sign-off → Data Migration Standards → sign-off → Object Grouping → sign-off → Fields Mapping Sheets + Classification Files → sign-off.
2. **Planning** – Data Migration Execution Plan (+ Build Metadata) → sign-off → Data Migration Checklist → internal sign-off.
3. **Build** – Source/Target/Validation queries → Pipelines → Migration Audit Sheet → Run loads (in order; backup after each) → Internal Data Sign-off → Client Data Sign-off.

Detailed flow matches the attached playbook diagram and the **Data Migration Checklist**.

---

## Documents (index)

| Document | Description |
|----------|-------------|
| [Objects Mapping Sheet](Objects%20Mapping%20Sheet.md) | List of objects to migrate; source/target metadata; dependencies; filter. Template + example in `templates/` and `examples/`. |
| [1. Data Migration Standards](1.%20Data%20Migration%20Standards.md) | Rules: External ID, backup, bypass automation, upsert, classification files, load order, sign-offs, phased validation, Asana. |
| [Data Migration Object Groups and Order of Execution](Data%20Migration%20Object%20Groups%20and%20Order%20of%20Execution.md) | Object groups, load order, ingestion method (Data Loader, Azure, Manual). |
| [Fields Mapping Sheets](Fields%20Mapping%20Sheets.md) | Source → target field mappings per object. Template + example in `templates/` and `examples/`. |
| [Classification Files](Classification%20Files.md) | User, Record Type, and Picklist mapping CSVs. Templates and examples in `templates/` and `examples/`. |
| [2. Data Migration Plan](2.%20Data%20Migration%20Plan.md) | Execution Plan: tools, team, timeline, metadata (connections, tables), Asana. |
| [3. Data Migration Checklist](3.%20Data%20Migration%20Checklist.md) | Plan and execution checklist (Discovery, Planning, Build); use in Asana. |
| [execution/Source Queries](execution/Source%20Queries.md) | How to define and document source extraction queries. |
| [execution/Target Queries and Field Maps](execution/Target%20Queries%20and%20Field%20Maps.md) | Target field mapping and upsert (External ID). |
| [execution/Validation Queries](execution/Validation%20Queries.md) | Count and integrity validation after each load. |
| [execution/Queries to Compare Field Values](execution/Queries%20to%20Compare%20Field%20Values.md) | Field-level comparison (source vs target). |
| [Migration Audit Sheet](Migration%20Audit%20Sheet.md) | Record (and optional field) counts – source vs target. Template in `templates/`. |
| [FAQ - Procedure](FAQ%20-%20Procedure.md) | Common questions and procedures. |

---

## Key standards (summary)

- **External ID** (External Key) on every target object; all loads are **upsert**.
- **Backup** target after each pipeline run.
- **Bypass automation** for the ingestion user.
- **Classification files** for User, Record Type, and Picklist mappings.
- **Load order** per Object Grouping document; no reordering without sign-off.
- **Multiple sign-offs** (e.g. Joe, bbs) as in Execution Plan.
- **Phased volume validation** and **Migration Audit Sheet** updated after each load.
- **Asana:** all tasks created step-by-step from the checklist.

---

## Folders

- **templates/** – Blank CSV templates for Objects, Fields, Object Order, Classification, Audit Sheet.
- **examples/** – Example CSVs for each.
- **execution/** – Guides for Source, Target, Validation, and Compare queries.
