# FAQ – Data Migration Playbook (Procedure)

**Purpose:** Common questions and procedures for running a Salesforce data migration using this playbook.

---

## 1. In what order do we do things?

Follow the **three phases** in order:

1. **Discovery** – Discovery sessions → Objects Mapping Sheet → sign-off → Data Migration Standards → sign-off → Object Grouping → sign-off → Fields Mapping Sheets + Classification Files → sign-off.
2. **Planning** – Data Migration Execution Plan + Build Metadata → sign-off → Data Migration Checklist → internal sign-off.
3. **Build** – Source Queries → Target Queries/Field Maps → Skeleton Pipelines → Validation Queries → Migration Audit Sheet → Run pipelines (in object order, backup after each) → Internal Data Sign-off → Client Data Sign-off.

The diagram in the playbook (and the Checklist) shows this flow step-by-step.

---

## 2. Why do we need an External ID on every target object?

We use **upsert** for all loads. Upsert requires a unique key to match existing records. The External ID (type External Key) holds the source system’s primary key so we can update existing rows on re-runs and avoid duplicates.

---

## 3. Why backup after each pipeline run?

So we can restore the target org to a known good state if a later load causes issues, without re-running all prior loads.

---

## 4. Why bypass automation for the ingestion user?

So workflow rules, process builder, flows, and triggers do not run during the load. That avoids duplicate emails, auto-assignments, and other side effects that can corrupt data or complicate validation.

---

## 5. What if a source user doesn’t exist in the target?

Per **Data Migration Standards**, we assign those records to an agreed **default user** (e.g. "Data Migration" or "Data Steward"). The default is documented in the Execution Plan and in the **User Mapping** classification file (e.g. Is Default = Y).

---

## 6. What are Classification Files?

CSV files that map source values to target values:

- **User Mappings** – source user → Salesforce User Id (and default user for unknowns).
- **Record Type Mappings** – source type/code → Salesforce RecordTypeId.
- **Picklist Mappings** – source picklist value → target API value.

They are used during the load (in queries or in the pipeline) to resolve lookups and picklists.

---

## 7. Can we change the load order of objects?

No, not without a plan change. Objects must be loaded in the **exact order** in the Data Migration Object Groups and Order of Execution document (parent before child). Any change requires update to that document and sign-off.

---

## 8. Who signs off?

- **Client:** Objects, Data Migration Standards, Object Grouping, Field Mappings, Execution Plan, and final Client Data Sign-off (e.g. Joe).
- **Internal:** Data Migration Checklist (before build) and Internal Data Sign-off after loads (e.g. bbs). Multiple sign-offs as defined in the Execution Plan.

---

## 9. What is Phased Volume Validation?

After each object (or each pipeline run), we compare **source vs target record counts** (and optionally run field-level comparison). We record results in the **Migration Audit Sheet** and resolve variances before moving to the next object. This avoids finding count issues only at the end.

---

## 10. Where do we track tasks?

All playbook tasks must be created **step-by-step in Asana** (or the agreed project tool) so the full flow is traceable and assignable.

---

## 11. Where do I find the template for [document]?

- **Objects:** [Objects Mapping Sheet.md](Objects%20Mapping%20Sheet.md) and `templates/Objects Mapping Sheet - Template.csv`
- **Fields:** [Fields Mapping Sheets.md](Fields%20Mapping%20Sheets.md) and `templates/Fields Mapping Sheet - Template.csv`
- **Classification:** [Classification Files.md](Classification%20Files.md) and `templates/classification-*.csv`
- **Object order:** [Data Migration Object Groups and Order of Execution.md](Data%20Migration%20Object%20Groups%20and%20Order%20of%20Execution.md) and `templates/Object Groups and Order - Template.csv`
- **Audit:** [Migration Audit Sheet.md](Migration%20Audit%20Sheet.md) and `templates/Migration Audit Sheet - Template.csv`

---

## 12. What do we do if validation shows a count variance?

1. Record the variance in the Migration Audit Sheet.
2. Investigate (logs, failed rows, filters).
3. Fix data or mapping and re-run that object’s load if needed.
4. Do not proceed to the next object until the variance is resolved or explicitly accepted with client approval.
