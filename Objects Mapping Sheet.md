# Objects Mapping Sheet

**Purpose:** List all objects identified during discovery/scoping for migration, with source/target metadata and dependencies.

**When to use:** Draft during Discovery (after Discovery Session(s)); get client sign-off before proceeding to Field Mappings and Object Grouping.

---

## Column Definitions

| Column | Description |
|--------|-------------|
| **Object Type** | Metadata or Data |
| **Source - Object Name** | Display name in source system |
| **Source - Object API Name** | API name in source (e.g. table or entity name) |
| **Source - Standard / Custom** | Standard or Custom |
| **Source - Record Counts** | Current record count |
| **Source - Record Count UpdatedAt** | Date when count was captured |
| **Object Dependency** | Parent objects this object depends on (load order) |
| **Related Object Fields** | Lookup/Master-Detail fields that reference other objects |
| **Target - Object Name** | Display name in Salesforce |
| **Target - Object API Name** | Salesforce API name (e.g. `Account`, `CustomObject__c`) |
| **Target - Standard / Custom** | Standard or Custom |
| **Target - Record Counts** | Expected/actual count in target (post-migration) |
| **Target - Record Count UpdatedAt** | Date when target count was captured |
| **Filter** | Source filter criteria (e.g. WHERE clause or filter description). Must be client sign-off. |
| **Field Mapping Tab** | Link or reference to the Fields Mapping Sheet for this object |
| **Notes** | Any migration-specific notes |

---

## Sign-off Checklist (Client)

- [ ] All objects to migrate are listed
- [ ] Object Dependency and Related Object Fields reviewed; items **not** included in migration marked in **red**
- [ ] Target objects confirmed
- [ ] Filter column reviewed and signed off

---

## Template and Example

- **Template:** [templates/Objects Mapping Sheet - Template.csv](templates/Objects%20Mapping%20Sheet%20-%20Template.csv)
- **Example:** [examples/Objects Mapping Sheet - Example.csv](examples/Objects%20Mapping%20Sheet%20-%20Example.csv)
