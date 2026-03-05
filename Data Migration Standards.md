# Data Migration Standards

**Purpose:** Define the rules and standards followed for every Salesforce data migration. These standards must be reviewed and signed off by the client before build.

---

## 1. Target System – External ID

- **Every target object** used for migration must have an **External ID** field (type: **External Key**).
- This field stores the source system’s primary key and is used for **upsert** operations.
- Naming convention: e.g. `Legacy_[Object]_Id__c` or `Source_Id__c` (align with client naming).

---

## 2. Backups

- Take a **backup of the target (Salesforce) org** after **each pipeline run** (or after each major object load).
- Backups must be retained per project/retention policy and agreed with the client.

---

## 3. Ingestion User and Automation

- Use a dedicated **ingestion/migration user** for all loads.
- **Bypass all automation** (workflow rules, process builder, flows, triggers) for this user.
- Achieve this via:
  - A dedicated migration profile/permission set with automation bypass where available, or
  - Context/user-based bypass logic in automation, or
  - Temporarily disabling automation during load windows (with change control).

---

## 4. Load Operation

- **All load actions are upsert** (no insert-only unless explicitly agreed).
- Upsert key = External ID field on the target object.

---

## 5. Classification Files

- Gather and maintain **Classification Files** (CSVs) where needed:
  - **User Mappings** (source user → target Salesforce User Id)
  - **Record Type Mappings** (source type/code → target RecordTypeId)
  - **Picklist Mappings** (source value → target API value)
- Location and naming must be documented in the Data Migration Execution Plan.

---

## 6. Load Order

- Load objects in the **exact order** specified in the **Data Migration Object Grouping and Order of Execution** document.
- Do not change order without plan update and sign-off.

---

## 7. Audit and System Fields

- **Enable system audit fields** where applicable (e.g. "Track Field History").
- **Retain CreatedDate and LastModifiedDate** from the source system where the target platform supports it (e.g. via API or data load with appropriate permissions).

---

## 8. Users Not in Target System

- Define a rule for records whose **owner or related user does not exist** in the target:
  - Option A: Assign to a designated **default migration user** (e.g. "Data Migration" or integration user).
  - Option B: Assign to a specific business user (e.g. "Data Steward").
  - Option C: Leave blank if allowed; otherwise use default.
- Document the chosen approach and the default user(s) in the Execution Plan and in User Mapping classification file.

---

## 9. Sign-offs

- **Multiple sign-offs** are required at defined stages:
  - Client sign-off: Objects, Data Migration Standards, Object Grouping, Field Mappings, Execution Plan.
  - Internal sign-off: Data Migration Checklist (before build), Internal Data Sign-off (after loads), then Client Data Sign-off.
- Sign-off roles (e.g. Joe, bbs) and names must be listed in the Execution Plan.

---

## 10. Phased Volume Validation

- Perform **phased volume validation**:
  - Validate record and field counts after each object or group (per Migration Audit Sheet).
  - Resolve variances before proceeding to the next phase or object.

---

## 11. Tooling and Asana

- Use the tools specified in the **Data Migration Execution Plan** (e.g. Data Loader, Azure Data Factory, manual loads).
- All tasks must be created and tracked **step-by-step in Asana** (or agreed project tool) so that the playbook flow is traceable.

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | | | Initial draft |

**Client sign-off:** _______________________ Date: _______
