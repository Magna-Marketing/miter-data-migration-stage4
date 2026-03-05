# Fields Mapping Sheets

**Purpose:** Document source-to-target field mappings for each object. One sheet (or tab) per object, aligned with the Objects Mapping Sheet.

**When to use:** Draft after sign-off on Objects and Object Grouping; get client sign-off before building Execution Plan and pipelines.

---

## Column Definitions

| Column | Description |
|--------|-------------|
| **Source - Field Label** | Display name in source system |
| **Source - Field API Name** | API/column name in source |
| **Source - Data Type** | e.g. Text, Number, Date, Lookup |
| **Target - Field Label** | Salesforce field label |
| **Target - Field API Name** | Salesforce API name (e.g. `Name`, `AccountId`, `Legacy_Account_Id__c`) |
| **Target - Data Type** | Salesforce data type |
| **Transform / Notes** | (Optional) Formula, lookup from classification file, or mapping rule |

---

## Rules

- **External ID:** The target External ID field (used for upsert) must be mapped from the source primary key.
- **Lookups:** Map to target Salesforce Id; source key → use classification or prior load to resolve Id.
- **Picklists:** Use Classification File (picklist mapping) to translate source value → target API value.
- **Users:** Use User Mapping classification to resolve OwnerId, CreatedById, etc.
- **Record Types:** Use Record Type Mapping classification where applicable.

---

## Sign-off Checklist (Client)

- [ ] Every required target field has a source mapping or default.
- [ ] Transforms and classification references are documented.
- [ ] No unmapped required fields (or explicit "Leave blank" / default agreed).

---

## Templates and Examples

- **Template:** [templates/Fields Mapping Sheet - Template.csv](templates/Fields%20Mapping%20Sheet%20-%20Template.csv)
- **Example (Account):** [examples/Fields Mapping Sheet - Account Example.csv](examples/Fields%20Mapping%20Sheet%20-%20Account%20Example.csv)

Create one sheet per object; name consistently (e.g. `Fields Mapping - Account.csv`).
