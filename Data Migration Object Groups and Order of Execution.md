# Data Migration Object Groups and Order of Execution

**Purpose:** Define object groups, load order, and ingestion method for each object. Ensures parent objects load before children and reduces dependency errors.

**When to use:** Draft after sign-off on Objects and Data Migration Standards; get client sign-off before Field Mappings and Execution Plan.

---

## 1. What This Document Contains

- **Object grouping** (e.g. Group 1: Foundation, Group 2: Core CRM, Group 3: Transactions).
- **Order of execution** (sequence number per object).
- **Ingestion method** per object: Data Loader, Azure (pipeline), Manual, Other.
- **ID mappings / External ID usage** (which field is used as upsert key).

---

## 2. Order of Execution Chart (Table)

Load objects **in the exact order** listed. Do not skip or reorder without a plan change and sign-off.

| Order | Group | Object (Target API Name) | Ingestion Method | External ID Field | Notes |
|-------|--------|---------------------------|------------------|-------------------|--------|
| 1 | Foundation | User | Data Loader / Manual | (Salesforce Id) | Users first; no dependency |
| 2 | Foundation | Account | Azure / Data Loader | Legacy_Account_Id__c | After User |
| 3 | Core | Contact | Azure / Data Loader | Legacy_Contact_Id__c | After Account, User |
| 4 | Core | Opportunity | Azure / Data Loader | Legacy_Opportunity_Id__c | After Account, Contact, User |
| 5 | Custom | CustomObject__c | Azure / Data Loader | Source_Id__c | After [list dependencies] |

*Replace with your project’s objects and methods.*

---

## 3. Visual Order-of-Execution Diagram (Concept)

```
[User] → [Account] → [Contact] → [Opportunity] → [CustomObject__c]
  1         2            3              4                  5
```

- Arrows indicate dependency (load in direction of arrow).
- Numbers are the execution order.

---

## 4. Ingestion Methods

| Method | When to Use |
|--------|-------------|
| **Data Loader** | Small volumes; one-off or manual loads; objects with simple mappings. |
| **Azure (Pipeline)** | Large volumes; repeatable runs; complex transforms or multiple sources. |
| **Manual** | Data entry or spreadsheet load where automation is not used. |
| **Other** | Document in Notes (e.g. MuleSoft, custom ETL). |

---

## 5. Dependency Rules

- **Parent before child:** e.g. Account before Contact, Contact before Opportunity.
- **Lookup/Master-Detail:** The object that is *referenced* (e.g. Account) must be loaded before the object that *references* it (e.g. Contact).
- Align **Object Dependency** and **Related Object Fields** from the Objects Mapping Sheet with this order.

---

## 6. Sign-off Checklist (Client)

- [ ] All migrated objects appear in the chart.
- [ ] Order respects dependencies.
- [ ] Ingestion method per object is agreed.
- [ ] External ID field per object is confirmed.

---

## 7. Template

A blank template is in [templates/Object Groups and Order - Template.csv](templates/Object%20Groups%20and%20Order%20-%20Template.csv). Fill it per project and keep this document (or a linked diagram) in sync.
