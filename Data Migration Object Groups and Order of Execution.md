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

## 2. Objects to Be Migrated (Authoritative List)

The following objects are in scope to migrate:

- Lead
- Opportunity
- Campaign
- CampaignMember
- CampaignMemberStatus
- Discount__c
- Revenue_History__c
- Sales_Order__c
- OpportunityContactRole
- OpportunityTeamMember
- Dealer_Asset__c
- Account_Role__c
- Builder_Metrics__c
- docebo_Course_Enrollment__c
- docebo_LP_Enrollment__c
- Marketing_Development_Allocation__c
- Marketing_Development_Budget__c
- Marketing_Development_Claim__c
- Marketing_Development_Fund__c
- Marketing_Development_Request__c
- Opportunity_Dealers__c
- OpportunitySplit
- Quote_Request__c
- Related_Account__c
- Request_Line_Item__c
- DiscountArchive__b

Note: The **Order of Execution** table below should include every object above once grouping/order are finalized.

---

## 3. Order of Execution Chart (Table)

Load objects **in the exact order** listed. Do not skip or reorder without a plan change and sign-off.

| Order | Group | Object (Target API Name) | Ingestion Method | External ID Field | Notes |
|-------|--------|---------------------------|------------------|-------------------|--------|
| 1 | Group 1 | User | SF Data Loader | TBD | Diagram: `User → Group` |
| 2 | Group 1 | Group | SF Data Loader | TBD | After `User`; diagram: `Group → OpportunitySplitType` |
| 3 | Group 1 | OpportunitySplitType | SF Data Loader | TBD | After `Group` |
| 4 | Group 1 | Lead_RecordType | UI | TBD | No dependency shown in diagram |
| 5 | Group 1 | Opportunity_RecordType | UI | TBD | No dependency shown in diagram |
| 6 | Group 1 | Campaign_RecordType | UI | TBD | No dependency shown in diagram |
| 7 | Group 1 | Account | SF Data Loader | TBD | Diagram: `Account → (Update) Account → Contact` |
| 8 | Group 1 | Account (Update) | SF Data Loader | TBD | After `Account` insert |
| 9 | Group 1 | Contact | Data Factory | TBD | After `Account (Update)`; diagram: `Contact → Related_Account__c` |
| 10 | Group 1 | Related_Account__c | Data Factory | TBD | After `Contact` |
| 11 | Group 1 | Builder_Metrics__c | UI | TBD | No dependency shown in diagram |
| 12 | Group 1 | docebo_LP_Enrollment__c | Data Factory | TBD | Diagram: `docebo_LP_Enrollment__c → docebo_Course_Enrollment__c` |
| 13 | Group 1 | docebo_Course_Enrollment__c | Data Factory | TBD | After `docebo_LP_Enrollment__c` |
| 14 | Group 1 | Lead | UI | TBD | No dependency shown in diagram |
| 15 | Group 1 | Campaign | UI | TBD | Diagram: `Campaign → (Update) Campaign → CampaignMember → CampaignMemberStatus` |
| 16 | Group 1 | Campaign (Update) | UI | TBD | After `Campaign` insert |
| 17 | Group 1 | CampaignMember | Data Factory | TBD | After `Campaign (Update)` |
| 18 | Group 1 | CampaignMemberStatus | UI | TBD | After `CampaignMember` |
| 19 | Group 1 | Pricebook2 | SF Data Loader | TBD | Diagram: `Pricebook2 → Product2 → PricebookEntry` |
| 20 | Group 1 | Product2 | UI | TBD | After `Pricebook2` |
| 21 | Group 1 | PricebookEntry | SF Data Loader | TBD | After `Product2` |
| 22 | Group 1 | Opportunity | Data Factory | TBD | Diagram: `Opportunity → (Update) Opportunity → OpportunityContactRole → OpportunityTeamMember → Opportunity_Dealers__c → OpportunitySplit` |
| 23 | Group 1 | Opportunity (Update) | Data Factory | TBD | After `Opportunity` insert |
| 24 | Group 1 | OpportunityContactRole | Data Factory | TBD | After `Opportunity (Update)` |
| 25 | Group 1 | OpportunityTeamMember | Data Factory | TBD | After `OpportunityContactRole` |
| 26 | Group 1 | Opportunity_Dealers__c | Data Factory | TBD | After `OpportunityTeamMember` |
| 27 | Group 1 | OpportunitySplit | Data Factory | TBD | After `Opportunity_Dealers__c` |
| 28 | Group 1 | Quote_Request__c | SF Data Loader | TBD | Diagram: `Quote_Request__c → Request_Line_Item__c` |
| 29 | Group 1 | Request_Line_Item__c | SF Data Loader | TBD | After `Quote_Request__c` |
| 30 | Group 1 | Dealer_Asset__c | SF Data Loader | TBD | Diagram: `Dealer_Asset__c → Revenue_History__c → Sales_Order__c → Discount__c` |
| 31 | Group 1 | Revenue_History__c | UI | TBD | After `Dealer_Asset__c` |
| 32 | Group 1 | Sales_Order__c | Data Factory | TBD | After `Revenue_History__c` |
| 33 | Group 1 | Discount__c | Data Factory | TBD | After `Sales_Order__c` |
| 34 | Group 1 | Account_Role__c | UI | TBD | No dependency shown in diagram |
| 35 | Group 1 | DiscountArchive__b | Data Factory | TBD | No dependency shown in diagram |

This table is derived from the current Group 1 diagram. Update **Ingestion Method** and **External ID Field** as decisions are finalized.

---

## 4. Visual Order-of-Execution Diagram (Concept)

Reference links:

- [Lucidchart flow](https://lucid.app/lucidchart/aafbca0e-adb5-4abe-8a17-f64d0439e001/edit?viewport_loc=-1401%2C-460%2C4095%2C1567%2CO1eC2VujR56J&invitationId=inv_2311de17-9796-4ef9-9f5e-05fa369c21a2)
- [Discovery Sheet (Google Sheet)](https://docs.google.com/spreadsheets/d/1lA_l1GvnI3x9kp3G8qPTxg0deQAV8f9U3hdGDa_cSKk/edit?usp=sharing)

```
[User] → [Group] → [OpportunitySplitType]

[Account] → [Account (Update)] → [Contact] → [Related_Account__c]

[docebo_LP_Enrollment__c] → [docebo_Course_Enrollment__c]

[Campaign] → [Campaign (Update)] → [CampaignMember] → [CampaignMemberStatus]

[Pricebook2] → [Product2] → [PricebookEntry]

[Opportunity] → [Opportunity (Update)] → [OpportunityContactRole] → [OpportunityTeamMember] → [Opportunity_Dealers__c] → [OpportunitySplit]

[Quote_Request__c] → [Request_Line_Item__c]

[Dealer_Asset__c] → [Revenue_History__c] → [Sales_Order__c] → [Discount__c]

[Account_Role__c]

[Builder_Metrics__c]

[Lead_RecordType]   [Opportunity_RecordType]   [Campaign_RecordType]

[Lead]   [DiscountArchive__b]
```

- Arrows indicate dependency (load in direction of arrow).
- Numbers are the execution order.

---

## 5. Ingestion Methods

| Method | When to Use |
|--------|-------------|
| **SF Data Loader** | Load **pink** objects from the flow (manual/operational runs where Data Loader is the chosen tool). |
| **UI** | Insert **blue** objects from the flow (manual setup/configuration or controlled UI inserts). |
| **Data Factory** | Load **black** objects from the flow (queried/extracted and ingested via Data Factory pipelines). |
| **Other** | Document in Notes (e.g. MuleSoft, custom ETL). |

---

## 6. Dependency Rules

- **Parent before child:** e.g. Account before Contact, Contact before Opportunity.
- **Lookup/Master-Detail:** The object that is *referenced* (e.g. Account) must be loaded before the object that *references* it (e.g. Contact).
- Align **Object Dependency** and **Related Object Fields** from the Objects Mapping Sheet with this order.

---

## 7. Sign-off Checklist (Client)

- [ ] All migrated objects appear in the chart.
- [ ] Order respects dependencies.
- [ ] Ingestion method per object is agreed.
- [ ] External ID field per object is confirmed.

---

## 8. Template

A blank template is in [templates/Object Groups and Order - Template.csv](templates/Object%20Groups%20and%20Order%20-%20Template.csv). Fill it per project and keep this document (or a linked diagram) in sync.
