# Migration Audit Sheet

**Purpose:** Track record counts and (optionally) key field counts for source vs target. Used for phased volume validation and sign-off evidence.

---

## 1. Record Counts (per object)

Capture **source** and **target** counts after each load. Update "Record Count UpdatedAt" when counts are taken.

| Object (Target API Name) | Source Record Count | Source Count Date | Target Record Count | Target Count Date | Variance | Notes |
|--------------------------|---------------------|-------------------|---------------------|-------------------|----------|-------|
| User | | | | | | |
| Account | | | | | | |
| Contact | | | | | | |
| Opportunity | | | | | | |
| [CustomObject__c] | | | | | | |

**Variance:** Target − Source (or note "OK" / "Investigate").

---

## 2. Field Counts (optional)

For critical fields, you can track how many records have a non-null value (e.g. to ensure required fields were populated).

| Object | Field (API Name) | Source Non-Null Count | Target Non-Null Count | Variance | Notes |
|--------|-------------------|------------------------|------------------------|----------|-------|
| Account | OwnerId | | | | |
| Account | Industry | | | | |
| Contact | AccountId | | | | |

Use this only where it adds value (e.g. key lookups or required fields).

---

## 3. When to Update

- **Build phase:** Create the sheet with object list and column headers (step 15).
- **After each pipeline run:** Update source count (from Source Query), target count (from SOQL/export), and variance.
- **Before Internal and Client sign-off:** All variances resolved or explained.

---

## 4. Template

- **CSV template:** [templates/Migration Audit Sheet - Template.csv](templates/Migration%20Audit%20Sheet%20-%20Template.csv)

Fill one row per object in execution order; add rows for field-level checks if used.
