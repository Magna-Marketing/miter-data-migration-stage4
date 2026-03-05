# Target Queries and Field Maps

**Purpose:** Define how source columns map to Salesforce fields and how upsert is performed (External ID). Used to build pipeline field maps or Data Loader mappings.

---

## 1. Principles

- **Upsert** on the External ID field (type External Key) on the target object.
- **Field map** = source column → target Salesforce field (per Fields Mapping Sheet).
- **Lookups:** Resolve via User/Record Type/Picklist classification files before or inside the load.

---

## 2. Target Field Map Template (per object)

| Source Column (from Source Query) | Target Field API Name | Transform / Classification |
|----------------------------------|------------------------|-----------------------------|
| source_id | Legacy_Account_Id__c (External ID) | Direct – upsert key |
| account_name | Name | Direct |
| owner_id_source | OwnerId | User Mapping classification |
| created_date | CreatedDate | Direct (retain from source) |
| industry_code | Industry | Picklist Mapping classification |
| … | … | … |

---

## 3. External ID Requirement

- **Every** migrated object must have an External ID field (External Key) on the target.
- In the target map, the column that holds the **source primary key** must map to this External ID field.
- Data Loader / pipeline: use **Upsert** with this field as the external ID key.

---

## 4. What to Document Per Object

| Item | Description |
|------|-------------|
| Target Object API Name | e.g. Account |
| External ID Field | e.g. Legacy_Account_Id__c |
| Full field map | Table or link to Fields Mapping Sheet |
| Classification files used | user-mapping.csv, picklist-mapping.csv, etc. |
| Required target fields | Any field that must be set (defaults if not in source) |

---

## 5. Data Loader Notes

- Choose **Upsert**.
- Select the **External ID** field as the lookup key.
- Map CSV columns to Salesforce fields per the field map.
- Use the ingestion user (automation bypass).

---

## 6. Pipeline Notes (e.g. Azure)

- Transformation step: apply User/Picklist/Record Type mappings from classification files.
- Sink: Salesforce connector (or REST/Bulk API); operation = Upsert; external ID field = as above.
