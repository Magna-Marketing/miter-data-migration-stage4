# Source Queries

**Purpose:** Define and document the SQL (or source-system) queries used to extract data for each object. These feed into pipelines or Data Loader export.

---

## 1. Principles

- **One query (or view) per object** – or one per logical extract (e.g. Account, Account history).
- **Apply filters** exactly as signed off in the Objects Mapping Sheet (Filter column).
- **Include all columns** required by the Fields Mapping Sheet for that object.
- **Use consistent ordering** (e.g. by primary key) for repeatable exports.

---

## 2. Query Template (SQL example)

```sql
-- Object: [Target Object API Name]
-- Source table/view: [schema].[table]
-- Filter (signed off): [description from Objects Mapping Sheet]
-- Last updated: [date]

SELECT
    [source_primary_key]     AS source_id,  -- maps to External ID
    [field1]                 AS [target_or_logical_name],
    [field2]                 AS [target_or_logical_name],
    -- ... all mapped fields
FROM [schema].[table]
WHERE [signed_off_filter_condition]
ORDER BY [source_primary_key];
```

---

## 3. What to Document Per Object

| Item | Description |
|------|-------------|
| Object (Target API Name) | e.g. Account, Contact |
| Source table/view | Schema and name |
| Filter (signed off) | Exact WHERE clause or reference to Objects Mapping Sheet |
| Column list | List or link to Field Mapping sheet |
| Dependencies | If query joins to other tables for lookups (e.g. user mapping) |
| Run order | Same as Data Migration Object Groups and Order of Execution |

---

## 4. Classification Usage

- **User lookups:** Join to user table or use a pre-export user mapping table/view so that OwnerId, CreatedById etc. are resolved (or leave placeholder for pipeline lookup from classification file).
- **Picklist / Record Type:** Either resolve in SQL (join to mapping table) or in pipeline using Classification Files.

---

## 5. Example (Account)

```sql
-- Object: Account
-- Source: legacy_db.dbo.accounts
-- Filter: IsDeleted = 0

SELECT
    account_id          AS source_id,
    name                AS account_name,
    owner_id            AS owner_id_source,
    created_at          AS created_date,
    updated_at          AS last_modified_date,
    industry_code       AS industry_code,
    annual_revenue      AS annual_revenue,
    billing_street      AS billing_street,
    billing_city        AS billing_city,
    billing_state       AS billing_state,
    billing_postal      AS billing_postal_code,
    billing_country     AS billing_country
FROM legacy_db.dbo.accounts
WHERE IsDeleted = 0
ORDER BY account_id;
```

Store the actual query in version control or a shared folder and link from this document or the Execution Plan.
