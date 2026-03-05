# Validation Queries

**Purpose:** Queries and scripts used to validate that record counts and data integrity are correct after each load (phased volume validation).

---

## 1. Principles

- Run validation **after each object** (or each pipeline run) before proceeding.
- Compare **source vs target** counts per object (and optionally per key segment).
- Use the **Migration Audit Sheet** to record counts and flag variances.

---

## 2. What to Validate

| Check | Description |
|-------|-------------|
| **Record count** | Total rows in source (with signed-off filter) vs total rows in target for that object |
| **Key fields not null** | External ID, required fields – count of rows where they are null |
| **Duplicate external ID** | No duplicate External ID values in target (would indicate upsert issues) |

---

## 3. Source Count Query (example)

```sql
-- Record count for: Account
-- Must match Objects Mapping Sheet filter

SELECT COUNT(*) AS source_count
FROM legacy_db.dbo.accounts
WHERE IsDeleted = 0;
```

---

## 4. Target Count (Salesforce)

- **SOQL** (e.g. in Dev Console or script):

```sql
SELECT COUNT() FROM Account WHERE Legacy_Account_Id__c != null
```

- Or use a report / export to CSV and count rows. Document the exact query or method so it is repeatable.

---

## 5. Validation Script / Checklist

- For each object:
  1. Run source count query → record in Migration Audit Sheet.
  2. Run target count (SOQL or export) → record in Migration Audit Sheet.
  3. Compare; if variance, investigate before next object.
  4. Optionally: run "Queries to Compare Field Values" for a sample (see that document).

Store validation queries in version control and link from this document or the Execution Plan.
