# Queries to Compare Field Values

**Purpose:** Compare specific field values between source and target for a sample (or full set) of records to ensure data fidelity beyond record counts.

---

## 1. When to Use

- After load of an object, for **phased volume validation**.
- When record counts match but you need to confirm that **field-level** data is correct.
- Can be run on a **sample** (e.g. 100 records) or on **full set** if volume is small.

---

## 2. Approach

1. **Export from source:** Key fields + External ID (or source primary key) for the object.
2. **Export from target:** Same key fields + External ID, filtered by same logical set (e.g. all migrated records).
3. **Compare:** Join on External ID (or source key); compare field-by-field; report mismatches or nulls.

---

## 3. Source Export (example – Account)

```sql
SELECT
    account_id          AS source_id,
    name                AS name,
    industry_code       AS industry,
    annual_revenue      AS annual_revenue,
    billing_city        AS billing_city
FROM legacy_db.dbo.accounts
WHERE IsDeleted = 0
ORDER BY account_id;
```

Export to CSV: `source_account_compare.csv`.

---

## 4. Target Export (Salesforce)

- **SOQL** or Data Loader export:

```sql
SELECT Id, Legacy_Account_Id__c, Name, Industry, AnnualRevenue, BillingCity
FROM Account
WHERE Legacy_Account_Id__c != null
ORDER BY Legacy_Account_Id__c
```

Export to CSV: `target_account_compare.csv`.

---

## 5. Comparison

- **Tool:** Excel (VLOOKUP/match), script (Python/SQL), or dedicated diff tool.
- **Logic:** For each `source_id` = `Legacy_Account_Id__c`, compare:
  - Name, Industry, AnnualRevenue, BillingCity (and any other critical fields).
- **Output:** List of Ids (or External IDs) where any compared field differs, plus summary counts (e.g. "3 records with mismatch on Industry").

---

## 6. Document Per Object

- Which fields are compared.
- Sample size (if sampling).
- Where comparison results are stored (e.g. Migration Audit Sheet or separate report).
