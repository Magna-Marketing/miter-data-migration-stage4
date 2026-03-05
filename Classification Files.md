# Classification Files

**Purpose:** CSV files that map source values to target values for picklists, users, record types, and similar reference data. Used during ETL to transform and resolve IDs/values.

**When to use:** Draft alongside or after Field Mappings; referenced by Source/Target queries and pipelines.

---

## 1. Types of Classification Files

| Type | Purpose | Typical Columns |
|------|---------|------------------|
| **User Mappings** | Map source user id/email to Salesforce User Id | Source User Id, Source Email, Target User Id (Salesforce Id) |
| **Record Type Mappings** | Map source type/code to Salesforce RecordTypeId | Source Record Type, Source Code, Target RecordTypeId |
| **Picklist Mappings** | Map source picklist value to target API value | Object, Field, Source Value, Target Value (API name) |

---

## 2. User Mappings

- **Use for:** OwnerId, CreatedById, LastModifiedById, custom lookups to User.
- **Default user:** If source user not in target, use the agreed default (see Data Migration Standards). Include that default in this file.

**Template:** [templates/classification-user-mapping.csv](templates/classification-user-mapping.csv)  
**Example:** [examples/classification-user-mapping.csv](examples/classification-user-mapping.csv)

---

## 3. Record Type Mappings

- **Use for:** RecordTypeId when source system has types that map to Salesforce Record Types.
- Include object name if the same file is used for multiple objects.

**Template:** [templates/classification-record-type-mapping.csv](templates/classification-record-type-mapping.csv)  
**Example:** [examples/classification-record-type-mapping.csv](examples/classification-record-type-mapping.csv)

---

## 4. Picklist Mappings

- **Use for:** Any picklist or multi-picklist where source values differ from target API values.
- One row per (Object, Field, Source Value) → Target Value.

**Template:** [templates/classification-picklist-mapping.csv](templates/classification-picklist-mapping.csv)  
**Example:** [examples/classification-picklist-mapping.csv](examples/classification-picklist-mapping.csv)

---

## 5. Naming and Location

- Store in a dedicated folder (e.g. `classification-files/`) and document path in the Data Migration Execution Plan.
- Naming: e.g. `user-mapping.csv`, `record-type-mapping.csv`, `picklist-mapping.csv` or per-object picklists.

---

## 6. Maintenance

- Update classification files when new users, record types, or picklist values are added.
- Version or date the files if re-runs are performed (e.g. in filename or Execution Plan).
