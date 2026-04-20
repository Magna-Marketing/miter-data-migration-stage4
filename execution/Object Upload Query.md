# Account

**Account**

```sql
SELECT
    PGTIAccount."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERParentAccount."Id" AS "ParentId",
    MITERDealerAccount."Id" AS "Dealer__c",
    MITERBuilderAccount."Id" AS "Builder__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    CASE
        WHEN MITERAccountExecutive."Id" IS NOT NULL THEN MITERAccountExecutive."Id"
    END AS "Account_Executive__c",
    CASE
        WHEN MITERAccountDirector."Id" IS NOT NULL THEN MITERAccountDirector."Id"
    END AS "Account_Director__c",
    CASE
        WHEN MITERAccountRep."Id" IS NOT NULL THEN MITERAccountRep."Id"
    END AS "Account_Rep__c",
    CASE
        WHEN MITERRegionalSalesManager."Id" IS NOT NULL THEN MITERRegionalSalesManager."Id"
    END AS "Account_Regional_Sales_Manager__c",
    CASE
        WHEN MITERArchRep."Id" IS NOT NULL THEN MITERArchRep."Id"
    END AS "Arch_Rep__c",
    CASE
        WHEN MITERFSSRRep."Id" IS NOT NULL THEN MITERFSSRRep."Id"
    END AS "FSSR__c",
    CASE
        WHEN MITERCoOwner."Id" IS NOT NULL THEN MITERCoOwner."Id"
    END AS "Co_Owner__c",
    CASE
        WHEN MITERSalesRep."Id" IS NOT NULL THEN MITERSalesRep."Id"
    END AS "SalesRep__c",
    CASE
        WHEN MITERInsideSalesRep."Id" IS NOT NULL THEN MITERInsideSalesRep."Id"
    END AS "Inside_Sales_Rep__c",
    CASE
        WHEN MITEROutsideSalesRep."Id" IS NOT NULL THEN MITEROutsideSalesRep."Id"
    END AS "Outside_Sales_Rep__c",
    CASE
        WHEN MITERVPSalesRep."Id" IS NOT NULL THEN MITERVPSalesRep."Id"
    END AS "VP_Sales_Rep__c",
    PGTIAccount."Name",
    PGTIAccount."AccountNumber",
    PGTIAccount."AccountSource",
    PGTIAccount."Account_Source__c",
    PGTIAccount."Account_Status__c",
    PGTIAccount."Active__c",
    PGTIAccount."Active_Inactive_Flag__c",
    PGTIAccount."AnnualRevenue",
    PGTIAccount."Annual_Revenue_Goal__c",
    PGTIAccount."Phone",
    PGTIAccount."Website",
    PGTIAccount."Industry",
    PGTIAccount."Description",
    PGTIAccount."BillingStreet",
    PGTIAccount."BillingCity",
    PGTIAccount."BillingState",
    PGTIAccount."BillingPostalCode",
    PGTIAccount."BillingCountry",
    PGTIAccount."ShippingStreet",
    PGTIAccount."ShippingCity",
    PGTIAccount."ShippingState",
    PGTIAccount."ShippingPostalCode",
    PGTIAccount."ShippingCountry",
    PGTIAccount."Dealer_Status__c",
    PGTIAccount."Dealer_Segment__c",
    PGTIAccount."Division__c",
    PGTIAccount."Region__c",
    PGTIAccount."Status__c",
    PGTIAccount."Type",
    PGTIAccount."Type__c",
    PGTIAccount."ClientID__c",
    PGTIAccount."PGT_A_Number__c",
    PGTIAccount."Supplier_Custom_ID__c",
    PGTIAccount."Sales_Rep_Code__c",
    PGTIAccount."Territory__c",
    PGTIAccount."Zone__c",
    PGTIAccount."CreatedDate",
    PGTIAccount."LastModifiedDate",
    PGTIAccount."LastActivityDate",
    PGTIAccount."AR_16_30__c" AS "zzAR_16_30__c",
    PGTIAccount."AR_1_15__c" AS "zzAR_1_15__c",
    PGTIAccount."AR_31_60__c" AS "zzAR_31_60__c",
    PGTIAccount."AR_61_90__c" AS "zzAR_61_90__c",
    PGTIAccount."AR_91__c" AS "zzAR_91__c",
    PGTIAccount."AR_Current__c" AS "zzAR_Current__c",
    PGTIAccount."AR_Disputed__c" AS "zzAR_Disputed__c",
    PGTIAccount."AR_MOA__c" AS "zzAR_MOA__c",
    PGTIAccount."Account_Do_not_Contact__c" AS "Do_not_Contact__c",
    PGTIAccount."Account_Do_not_Email__c" AS "Do_not_Email__c",
    PGTIAccount."Account_Do_not_Mail__c" AS "Do_not_Mail__c",
    PGTIAccount."DL_Appt_Set__c" AS "Appt_Set__c",
    PGTIAccount."DL_Duplicate__c" AS "Duplicate__c",
    PGTIAccount."DL_New__c" AS "New__c",
    PGTIAccount."DL_Not_Interested__c" AS "Not_Interested__c",
    PGTIAccount."DL_Sold__c" AS "Sold__c",
    PGTIAccount."LeadMatch_Sold_Leads__c" AS "Sold_Leads__c",
    PGTIAccount."LeadMatch_Total_Leads__c" AS "Total_Leads__c"

FROM stg4_pgti."Account" PGTIAccount

LEFT JOIN stg4_miter."Account" MITERParentAccount ON PGTIAccount."ParentId" = MITERParentAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERDealerAccount ON PGTIAccount."Dealer__c" = MITERDealerAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERBuilderAccount ON PGTIAccount."Builder__c" = MITERBuilderAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIAccount."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIAccount."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIAccount."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERAccountExecutive ON PGTIAccount."Account_Executive__c" = MITERAccountExecutive."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERAccountDirector ON PGTIAccount."Account_Director__c" = MITERAccountDirector."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERAccountRep ON PGTIAccount."Account_Rep__c" = MITERAccountRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERRegionalSalesManager ON PGTIAccount."Account_Regional_Sales_Manager__c" = MITERRegionalSalesManager."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERArchRep ON PGTIAccount."Arch_Rep__c" = MITERArchRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERFSSRRep ON PGTIAccount."FSSR__c" = MITERFSSRRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCoOwner ON PGTIAccount."Co_Owner__c" = MITERCoOwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERSalesRep ON PGTIAccount."SalesRep__c" = MITERSalesRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERInsideSalesRep ON PGTIAccount."Inside_Sales_Rep__c" = MITERInsideSalesRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROutsideSalesRep ON PGTIAccount."Outside_Sales_Rep__c" = MITEROutsideSalesRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERVPSalesRep ON PGTIAccount."VP_Sales_Rep__c" = MITERVPSalesRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTIAccount."Id" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

WHERE
    MITERAccount."PGTI_Salesforce_Ext_Id__c" IS NULL
    AND PGTIAccount."IsPersonAccount" = 'False';


```

# Contact

**Contact**

```sql
SELECT
    PGTIContact."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAccount."Id" AS "AccountId",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    CASE
        WHEN MITERVPSalesRep."Id" IS NOT NULL THEN MITERVPSalesRep."Id"
        ELSE '005UT000001c35xYAA'
    END AS "VP_Sales_Rep__c",
    MITERReportsTo."Id" AS "ReportsToId",
    PGTIContact."FirstName",
    PGTIContact."LastName",
    PGTIContact."MiddleName",
    PGTIContact."Suffix",
    PGTIContact."Salutation",
    PGTIContact."Email",
    PGTIContact."Phone",
    PGTIContact."MobilePhone",
    PGTIContact."HomePhone",
    PGTIContact."OtherPhone",
    PGTIContact."Fax",
    PGTIContact."Title",
    PGTIContact."Department",
    PGTIContact."Description",
    PGTIContact."MailingStreet",
    PGTIContact."MailingCity",
    PGTIContact."MailingState",
    PGTIContact."MailingPostalCode",
    PGTIContact."MailingCountry",
    PGTIContact."LeadSource",
    PGTIContact."ContactSource",
    PGTIContact."Active_Inactive_Flag__c",
    PGTIContact."Contact_Role__c",
    PGTIContact."Role__c",
    PGTIContact."Title_Role__c",
    PGTIContact."Title__c",
    PGTIContact."COI_Status_Level__c",
    PGTIContact."COI_Total_Pts__c",
    PGTIContact."COI_Sales_Growth_Pts__c",
    PGTIContact."COI_Sales_Volume_Pts__c",
    PGTIContact."COI_Training_Completed_Pts__c",
    PGTIContact."COI_Voice_Program_Pts__c",
    PGTIContact."COI_Pays_Within_Terms_Pts__c",
    PGTIContact."COI_Years_of_Partnership_Pts__c",
    PGTIContact."Categories_Served__c",
    PGTIContact."Certifications__c",
    PGTIContact."Commercial__c",
    PGTIContact."Commercial_Industry_COI__c",
    PGTIContact."Custom_Industry_COI__c",
    PGTIContact."VP_Industry_COI__c",
    PGTIContact."HasOptedOutOfEmail",
    PGTIContact."HasOptedOutOfFax",
    PGTIContact."DoNotCall",
    PGTIContact."Birthdate",
    PGTIContact."pi__created_date__c",
    PGTIContact."pi__conversion_date__c",
    PGTIContact."pi__last_activity__c",
    PGTIContact."pi__first_activity__c",
    PGTIContact."pi__Pardot_Last_Scored_At__c",
    PGTIContact."pi__campaign__c",
    PGTIContact."pi__comments__c",
    PGTIContact."pi__score__c",
    PGTIContact."pi__grade__c",
    PGTIContact."pi__url__c",
    PGTIContact."pi__utm_campaign__c",
    PGTIContact."pi__utm_content__c",
    PGTIContact."pi__utm_medium__c",
    PGTIContact."pi__utm_source__c",
    PGTIContact."pi__utm_term__c",
    PGTIContact."pi__first_touch_url__c",
    PGTIContact."pi__first_search_term__c",
    PGTIContact."pi__first_search_type__c",
    PGTIContact."Inactive__c",
    PGTIContact."Duplicate__c",
    PGTIContact."isTestRecord__c",
    PGTIContact."Marketing_Contact__c",
    PGTIContact."Client_ID__c",
    PGTIContact."Supplier_Contact_Custom_ID__c",
    PGTIContact."Contact_ID__c",
    PGTIContact."Website__c",
    PGTIContact."Work_Phone__c",
    PGTIContact."Notes__c"

FROM stg4_pgti."Contact" PGTIContact

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTIContact."AccountId" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIContact."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIContact."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIContact."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERVPSalesRep ON PGTIContact."VP_Sales_Rep__c" = MITERVPSalesRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Contact" MITERReportsTo ON PGTIContact."ReportsToId" = MITERReportsTo."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Contact" MITERContact ON PGTIContact."Id" = MITERContact."PGTI_Salesforce_Ext_Id__c"

WHERE
    PGTIContact."IsPersonAccount" = 'False'
    AND MITERContact."PGTI_Salesforce_Ext_Id__c" IS NULL;



```

# Related\_Account\_\_c

**Related\_Account\_\_c**

```sql

SELECT
    PGTIRelatedAccount."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERPrimaryAccount."Id" AS "Primary_Account__c",
    MITERRelatedAccount."Id" AS "Related_Account__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIRelatedAccount."Primary_Account_Type__c",
    PGTIRelatedAccount."Related_Account_Type__c"

FROM stg4_pgti."Related_Account__c" PGTIRelatedAccount

LEFT JOIN stg4_miter."Account" MITERPrimaryAccount ON PGTIRelatedAccount."Primary_Account__c" = MITERPrimaryAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERRelatedAccount ON PGTIRelatedAccount."Related_Account__c" = MITERRelatedAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIRelatedAccount."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIRelatedAccount."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIRelatedAccount."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Related_Account__c" MITERTgtRelatedAccount ON PGTIRelatedAccount."Id" = MITERTgtRelatedAccount."PGTI_Salesforce_Ext_Id__c"

WHERE MITERTgtRelatedAccount."PGTI_Salesforce_Ext_Id__c" IS NULL;


```

# docebo\_Course\_Enrollment\_\_c

**docebo\_Course\_Enrollment\_\_c**

```sql
SELECT
    PGTICourseEnrollment."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERContact."Id" AS "Contact__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTICourseEnrollment."Name",
    PGTICourseEnrollment."CreatedDate",
    PGTICourseEnrollment."IsDeleted",
    PGTICourseEnrollment."Docebo_Course_Code__c",
    PGTICourseEnrollment."Docebo_Course_ID__c",
    PGTICourseEnrollment."Docebo_Course_Title__c",
    PGTICourseEnrollment."Docebo_Deleted__c",
    PGTICourseEnrollment."Docebo_Score__c",
    PGTICourseEnrollment."Docebo_User_ID__c",
    PGTICourseEnrollment."Docebo_Username__c",
    PGTICourseEnrollment."Enrollment_Date__c",
    PGTICourseEnrollment."Ext_Enrollment_ID__c",
    PGTICourseEnrollment."LastActivityDate",
    PGTICourseEnrollment."LastModifiedDate",
    PGTICourseEnrollment."LastReferencedDate",
    PGTICourseEnrollment."LastViewedDate",
    PGTICourseEnrollment."Status__c",
    PGTICourseEnrollment."Unenrollment_Date__c"

FROM stg4_pgti."docebo_Course_Enrollment__c" PGTICourseEnrollment

LEFT JOIN stg4_miter."Contact" MITERContact ON PGTICourseEnrollment."Contact__c" = MITERContact."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTICourseEnrollment."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTICourseEnrollment."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTICourseEnrollment."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."docebo_Course_Enrollment__c" MITERCourseEnrollment ON PGTICourseEnrollment."Id" = MITERCourseEnrollment."PGTI_Salesforce_Ext_Id__c"

WHERE MITERCourseEnrollment."PGTI_Salesforce_Ext_Id__c" IS NULL;

```

# docebo\_LP\_Enrollment\_\_c

**docebo\_LP\_Enrollment\_\_c**

```sql
SELECT
    PGTILPEnrollment."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERContact."Id" AS "Contact__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTILPEnrollment."Name",
    PGTILPEnrollment."CreatedDate",
    PGTILPEnrollment."IsDeleted",
    PGTILPEnrollment."Docebo_Deleted__c",
    PGTILPEnrollment."Docebo_User_ID__c",
    PGTILPEnrollment."Docebo_Username__c",
    PGTILPEnrollment."Enrollment_Date__c",
    PGTILPEnrollment."Ext_Enrollment_ID__c",
    PGTILPEnrollment."LastActivityDate",
    PGTILPEnrollment."LastModifiedDate",
    PGTILPEnrollment."LastReferencedDate",
    PGTILPEnrollment."LastViewedDate",
    PGTILPEnrollment."Status__c",
    PGTILPEnrollment."Unenrollment_Date__c",
    PGTILPEnrollment."Completed_Date__c",
    PGTILPEnrollment."Course_Count__c",
    PGTILPEnrollment."LP_Code__c",
    PGTILPEnrollment."LP_ID__c",
    PGTILPEnrollment."LP_Title__c",
    PGTILPEnrollment."Percent_Complete__c"

FROM stg4_pgti."docebo_LP_Enrollment__c" PGTILPEnrollment

LEFT JOIN stg4_miter."Contact" MITERContact ON PGTILPEnrollment."Contact__c" = MITERContact."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTILPEnrollment."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTILPEnrollment."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTILPEnrollment."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."docebo_LP_Enrollment__c" MITERLPEnrollment ON PGTILPEnrollment."Id" = MITERLPEnrollment."PGTI_Salesforce_Ext_Id__c"

WHERE MITERLPEnrollment."PGTI_Salesforce_Ext_Id__c" IS NULL;


```

# Opportunity

**Opportunity**

```sql
SELECT
    PGTIOpportunity."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAccount."Id" AS "AccountId",
    MITERCampaign."Id" AS "CampaignId",
    MITERPricebook."Id" AS "Pricebook2Id",
    MITERContact."Id" AS "ContactId",
    MITERPartnerAccount."Id" AS "PartnerAccountId",
    MITERBuilderAccount."Id" AS "Builder__c",
    MITERDealerAccount."Id" AS "Primary_Dealer__c",
    MITERArchitectContact."Id" AS "Architect_Contact__c",
    MITERDealerContact."Id" AS "Dealer_Contact__c",
    MITERBuilderContact."Id" AS "Builder_Contact__c",
    MITERProduct."Id" AS "Product__c",
    MITERArchitectAccount."Name" AS "Architect_Account__c",
    MITERParentOpportunity."Id" AS "Plant_Approval_Opportunity_Id__c",
    PGTIOpportunity."Start_Date__c" AS "Target_Start_Date__c",
    PGTIOpportunity."Job_Name__c",
    PGTIOpportunity."Job_Site_State__c" AS "Job_Site_State_Province__c",
    PGTIOpportunity."Project_Type__c" AS "Type_of_Project__c",
    PGTIOpportunity."Discount_Approved__c" AS "SYS_Discount_Approved__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    CASE
        WHEN MITEROutsideRep1."Id" IS NOT NULL THEN MITEROutsideRep1."Id"
    END AS "Outside_Rep_1__c",
    CASE
        WHEN MITEROutsideRep2."Id" IS NOT NULL THEN MITEROutsideRep2."Id"
    END AS "Outside_Rep_2__c",
    CASE
        WHEN MITERInsideRep1."Id" IS NOT NULL THEN MITERInsideRep1."Id"
    END AS "Inside_Rep_1__c",
    CASE
        WHEN MITERInsideRep2."Id" IS NOT NULL THEN MITERInsideRep2."Id"
    END AS "Inside_Rep_2__c",
    CASE
        WHEN MITERArchRep."Id" IS NOT NULL THEN MITERArchRep."Id"
    END AS "Arch_Rep__c",
    CASE
        WHEN MITERFSSRRep."Id" IS NOT NULL THEN MITERFSSRRep."Id"
    END AS "FSSR__c",
    CASE
        WHEN MITERCoOwner."Id" IS NOT NULL THEN MITERCoOwner."Id"
    END AS "Co_Owner__c",
    PGTIOpportunity."Name",
    PGTIOpportunity."Description",
    PGTIOpportunity."StageName",
    PGTIOpportunity."Amount",
    PGTIOpportunity."Probability",
    PGTIOpportunity."ExpectedRevenue",
    PGTIOpportunity."TotalOpportunityQuantity",
    PGTIOpportunity."CloseDate",
    PGTIOpportunity."Awarded_Date__c",
    PGTIOpportunity."Type",
    PGTIOpportunity."NextStep",
    PGTIOpportunity."LeadSource",
    PGTIOpportunity."IsClosed",
    PGTIOpportunity."IsWon",
    PGTIOpportunity."ForecastCategory",
    PGTIOpportunity."ForecastCategoryName",
    PGTIOpportunity."HasOpportunityLineItem",
    PGTIOpportunity."IsSplit",
    PGTIOpportunity."CreatedDate",
    PGTIOpportunity."LastModifiedDate",
    PGTIOpportunity."LastActivityDate",
    PGTIOpportunity."Quote_Name__c",
    PGTIOpportunity."Status__c",
    PGTIOpportunity."Creation_Date__c",
    PGTIOpportunity."Expiration_Date__c",
    PGTIOpportunity."Order_Date__c",
    PGTIOpportunity."Total_Dealer_Price__c",
    PGTIOpportunity."Total_Dealer_Quote_Discount__c",
    PGTIOpportunity."Total_Dealer_SH__c",
    PGTIOpportunity."Total_Dealer_H__c",
    PGTIOpportunity."TotalDealerMisc__c",
    PGTIOpportunity."TotalDealerTax__c",
    PGTIOpportunity."Quote_ID__c",
    PGTIOpportunity."Client_ID__c",
    PGTIOpportunity."Quote_Order_Number__c",
    PGTIOpportunity."Project_Number__c",
    PGTIOpportunity."Region__c",
    PGTIOpportunity."Division__c",
    PGTIOpportunity."Opportunity_Address__c",
    PGTIOpportunity."Community_Name__c",
    PGTIOpportunity."Project_Value__c",
    PGTIOpportunity."Project_Name__c",
    PGTIOpportunity."Prospect_Start_Date__c",
    PGTIOpportunity."Community_Website__c"

FROM stg4_pgti."Opportunity" PGTIOpportunity

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTIOpportunity."AccountId" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Campaign" MITERCampaign ON PGTIOpportunity."CampaignId" = MITERCampaign."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Pricebook2" MITERPricebook ON PGTIOpportunity."Pricebook2Id" = MITERPricebook."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Contact" MITERContact ON PGTIOpportunity."ContactId" = MITERContact."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERPartnerAccount ON PGTIOpportunity."PartnerAccountId" = MITERPartnerAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERBuilderAccount ON PGTIOpportunity."Builder__c" = MITERBuilderAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERDealerAccount ON PGTIOpportunity."Primary_Dealer__c" = MITERDealerAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERArchitectAccount ON PGTIOpportunity."Architect__c" = MITERArchitectAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Opportunity" MITERParentOpportunity ON PGTIOpportunity."Parent_Opportunity__c" = MITERParentOpportunity."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Contact" MITERArchitectContact ON PGTIOpportunity."Architect_Contact__c" = MITERArchitectContact."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Contact" MITERDealerContact ON PGTIOpportunity."Dealer_Contact__c" = MITERDealerContact."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Contact" MITERBuilderContact ON PGTIOpportunity."Builder_Contact__c" = MITERBuilderContact."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Product2" MITERProduct ON PGTIOpportunity."Product__c" = MITERProduct."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIOpportunity."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIOpportunity."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIOpportunity."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROutsideRep1 ON PGTIOpportunity."Outside_Rep_1__c" = MITEROutsideRep1."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROutsideRep2 ON PGTIOpportunity."Outside_Rep_2__c" = MITEROutsideRep2."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERInsideRep1 ON PGTIOpportunity."Inside_Rep_1__c" = MITERInsideRep1."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERInsideRep2 ON PGTIOpportunity."Inside_Rep_2__c" = MITERInsideRep2."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERArchRep ON PGTIOpportunity."Arch_Rep__c" = MITERArchRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERFSSRRep ON PGTIOpportunity."FSSR__c" = MITERFSSRRep."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCoOwner ON PGTIOpportunity."Co_Owner__c" = MITERCoOwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Opportunity" MITEROpportunity ON PGTIOpportunity."Id" = MITEROpportunity."PGTI_Salesforce_Ext_Id__c"

WHERE
    MITEROpportunity."PGTI_Salesforce_Ext_Id__c" IS NULL
    AND MITERAccount."Id" IS NOT NULL
    AND PGTIOpportunity."CreatedDate" >= TIMESTAMP '2024-01-01 00:00:00';




```

# OpportunityContactRole

**OpportunityContactRole**

```sql
SELECT
    PGTIOppConRole."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERContact."Id" AS "ContactId",
    MITEROpportunity."Id" AS "OpportunityId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIOppConRole."IsDeleted",
    PGTIOppConRole."IsPrimary",
    PGTIOppConRole."Role",
    PGTIOppConRole."CreatedDate",
    PGTIOppConRole."LastModifiedDate"

FROM stg4_pgti."OpportunityContactRole" PGTIOppConRole

LEFT JOIN stg4_miter."Contact" MITERContact ON PGTIOppConRole."ContactId" = MITERContact."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Opportunity" MITEROpportunity ON PGTIOppConRole."OpportunityId" = MITEROpportunity."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIOppConRole."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIOppConRole."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."OpportunityContactRole" MITEROppConRole ON PGTIOppConRole."Id" = MITEROppConRole."PGTI_Salesforce_Ext_Id__c"

WHERE MITEROppConRole."PGTI_Salesforce_Ext_Id__c" IS NULL;

```

# OpportunityTeamMember

**OpportunityTeamMember**

```sql

SELECT
    PGTIOppTeamMember."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITEROpportunity."Id" AS "OpportunityId",
    CASE
        WHEN MITERUser."Id" IS NOT NULL THEN MITERUser."Id"
        ELSE '005UT000001c35xYAA'
    END AS "UserId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIOppTeamMember."Add_Default_Team__c",
    PGTIOppTeamMember."CreatedDate",
    PGTIOppTeamMember."IsDeleted",
    PGTIOppTeamMember."Email_del__c",
    PGTIOppTeamMember."LastModifiedDate",
    PGTIOppTeamMember."OpportunityAccessLevel",
    PGTIOppTeamMember."Name",
    PGTIOppTeamMember."TeamMemberRole",
    PGTIOppTeamMember."Title",
    PGTIOppTeamMember."PhotoUrl"

FROM stg4_pgti."OpportunityTeamMember" PGTIOppTeamMember

LEFT JOIN stg4_miter."Opportunity" MITEROpportunity ON PGTIOppTeamMember."OpportunityId" = MITEROpportunity."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERUser ON PGTIOppTeamMember."UserId" = MITERUser."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIOppTeamMember."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIOppTeamMember."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."OpportunityTeamMember" MITEROppTeamMember ON PGTIOppTeamMember."Id" = MITEROppTeamMember."PGTI_Salesforce_Ext_Id__c"

WHERE MITEROppTeamMember."PGTI_Salesforce_Ext_Id__c" IS NULL;

```

# Opportunity\_Dealers\_\_c

**Opportunity\_Dealers\_\_c**

```sql
SELECT
    PGTIOppDealers."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAccount."Id" AS "Dealer__c",
    MITEROpportunity."Id" AS "Opportunity__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIOppDealers."CreatedDate",
    PGTIOppDealers."IsDeleted",
    PGTIOppDealers."LastModifiedDate",
    PGTIOppDealers."Primary__c"

FROM stg4_pgti."Opportunity_Dealers__c" PGTIOppDealers

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTIOppDealers."Dealer__c" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Opportunity" MITEROpportunity ON PGTIOppDealers."Opportunity__c" = MITEROpportunity."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIOppDealers."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIOppDealers."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIOppDealers."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Opportunity_Dealers__c" MITEROppDealers ON PGTIOppDealers."Id" = MITEROppDealers."PGTI_Salesforce_Ext_Id__c"

WHERE MITEROppDealers."PGTI_Salesforce_Ext_Id__c" IS NULL;


```

# Sales\_Order\_\_c

**Sales\_Order\_\_c**

```sql
SELECT
    PGTISalesOrder."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAccount."Id" AS "Account__c",
    MITERCommercialOpp."Id" AS "Commercial_Opportunity__c",
    MITERSEBUOpp."Id" AS "SEBU_Opportunity__c",
    MITERDealerAsset."Id" AS "Dealer_Asset__c",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTISalesOrder."Bill_To__c",
    PGTISalesOrder."Brand__c",
    PGTISalesOrder."Brand_Account__c",
    PGTISalesOrder."Discount_Price_As__c",
    PGTISalesOrder."Entered_By__c",
    PGTISalesOrder."Job_Name__c",
    PGTISalesOrder."Invoice_Date__c",
    PGTISalesOrder."Invoice_Number__c",
    PGTISalesOrder."Order_Date__c",
    PGTISalesOrder."Order_Total__c",
    PGTISalesOrder."Order_Type__c",
    PGTISalesOrder."Project_Number__c",
    PGTISalesOrder."Quote_Number__c",
    PGTISalesOrder."Region__c",
    PGTISalesOrder."Sales_Order_Number__c",
    PGTISalesOrder."Sales_Order_Unique_ID__c",
    PGTISalesOrder."Ship_Date__c",
    PGTISalesOrder."Ship_To__c",
    PGTISalesOrder."Ship_To_PO__c",
    PGTISalesOrder."Ship_Via__c",
    PGTISalesOrder."Sold_To__c",
    PGTISalesOrder."Suffix__c",
    PGTISalesOrder."Territory__c"

FROM stg4_pgti."Sales_Order__c" PGTISalesOrder

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTISalesOrder."Account__c" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Opportunity" MITERCommercialOpp ON PGTISalesOrder."Commercial_Opportunity__c" = MITERCommercialOpp."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Opportunity" MITERSEBUOpp ON PGTISalesOrder."SEBU_Opportunity__c" = MITERSEBUOpp."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Dealer_Asset__c" MITERDealerAsset ON PGTISalesOrder."Dealer_Asset__c" = MITERDealerAsset."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTISalesOrder."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTISalesOrder."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Sales_Order__c" MITERSalesOrder ON PGTISalesOrder."Id" = MITERSalesOrder."PGTI_Salesforce_Ext_Id__c"

WHERE MITERSalesOrder."PGTI_Salesforce_Ext_Id__c" IS NULL;


```

# Discount\_\_c

**Discount\_\_c**

```sql
SELECT
    PGTIDiscount."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAccount."Id" AS "Account__c",
    MITERDealerAsset."Id" AS "Dealer_Asset__c",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIDiscount."Account_Discount_Id__c",
    PGTIDiscount."Bill_To__c",
    PGTIDiscount."Brand__c",
    PGTIDiscount."Company__c",
    PGTIDiscount."Discount_Amount__c",
    PGTIDiscount."Discount_Name__c",
    PGTIDiscount."Discount_Unique_Id__c",
    PGTIDiscount."DZW__c",
    PGTIDiscount."End_Date__c",
    PGTIDiscount."Impact_Type__c",
    PGTIDiscount."Material_Type__c",
    PGTIDiscount."Model_Type__c",
    PGTIDiscount."Parent_Product__c",
    PGTIDiscount."Price_As__c",
    PGTIDiscount."Price_Category_Code__c",
    PGTIDiscount."Product_Family__c",
    PGTIDiscount."Quotrac_DB_Id__c",
    PGTIDiscount."Series__c",
    PGTIDiscount."Ship_To__c",
    PGTIDiscount."Start_Date__c",
    PGTIDiscount."Status__c"

FROM stg4_pgti."Discount__c" PGTIDiscount

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTIDiscount."Account__c" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Dealer_Asset__c" MITERDealerAsset ON PGTIDiscount."Dealer_Asset__c" = MITERDealerAsset."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIDiscount."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIDiscount."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Discount__c" MITERDiscount ON PGTIDiscount."Id" = MITERDiscount."PGTI_Salesforce_Ext_Id__c"

WHERE MITERDiscount."PGTI_Salesforce_Ext_Id__c" IS NULL;


```

# DiscountArchive\_\_b

**DiscountArchive\_\_b**

```sql
SELECT
    PGTIDiscountArchive."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAccount."Id" AS "Account__c",
    MITERDealerAsset."Id" AS "DealerAsset__c",
    PGTIDiscountArchive."Account_Discount_Id__c",
    PGTIDiscountArchive."BillTo__c",
    PGTIDiscountArchive."Brand__c",
    PGTIDiscountArchive."Company__c",
    PGTIDiscountArchive."DiscountPercent__c",
    PGTIDiscountArchive."DiscountAmount__c",
    PGTIDiscountArchive."DiscountId__c",
    PGTIDiscountArchive."DiscountName__c",
    PGTIDiscountArchive."DiscountUniqueId__c",
    PGTIDiscountArchive."DZW__c",
    PGTIDiscountArchive."EndDate__c",
    PGTIDiscountArchive."ImpactType__c",
    PGTIDiscountArchive."MaterialType__c",
    PGTIDiscountArchive."ModelType__c",
    PGTIDiscountArchive."MultiplierPercent__c",
    PGTIDiscountArchive."Name__c",
    PGTIDiscountArchive."ParentProduct__c",
    PGTIDiscountArchive."PGTIDealerId__c",
    PGTIDiscountArchive."PriceAs__c",
    PGTIDiscountArchive."PriceCategoryCode__c",
    PGTIDiscountArchive."ProductFamily__c",
    PGTIDiscountArchive."ProductName__c",
    PGTIDiscountArchive."QuotracDBId__c",
    PGTIDiscountArchive."Series__c",
    PGTIDiscountArchive."ShipTo__c",
    PGTIDiscountArchive."StartDate__c",
    PGTIDiscountArchive."Status__c"

FROM stg4_pgti."DiscountArchive__b" PGTIDiscountArchive

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTIDiscountArchive."Account__c" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Dealer_Asset__c" MITERDealerAsset ON PGTIDiscountArchive."DealerAsset__c" = MITERDealerAsset."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."DiscountArchive__b" MITERDiscountArchive ON PGTIDiscountArchive."Id" = MITERDiscountArchive."PGTI_Salesforce_Ext_Id__c"

WHERE MITERDiscountArchive."PGTI_Salesforce_Ext_Id__c" IS NULL;

```

# Performance\_Card\_\_c

**Performance\_Card\_\_c**

```sql
SELECT
    PGTIPerformanceCard."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAssignedTo."Id" AS "Assigned_To__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIPerformanceCard."Name",
    PGTIPerformanceCard."IsActive__c",
    PGTIPerformanceCard."IsOpen__c",
    PGTIPerformanceCard."Territory__c",
    PGTIPerformanceCard."Start_Date__c",
    PGTIPerformanceCard."End_Date__c"

FROM stg4_pgti."Performance_Card__c" PGTIPerformanceCard

LEFT JOIN stg4_miter."User" MITERAssignedTo ON PGTIPerformanceCard."Assigned_To__c" = MITERAssignedTo."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIPerformanceCard."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIPerformanceCard."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIPerformanceCard."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Performance_Card__c" MITERPerformanceCard ON PGTIPerformanceCard."Id" = MITERPerformanceCard."PGTI_Salesforce_Ext_Id__c"

WHERE MITERPerformanceCard."PGTI_Salesforce_Ext_Id__c" IS NULL;

```

# Survey\_\_c

**Survey\_\_c**

```sql
SELECT
    PGTISurvey."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAccount."Id" AS "Account__c",
    MITERDealerAccount."Id" AS "Name_of_dealer_visited__c",
    MITERPerformanceCard."Id" AS "Performance_Card__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTISurvey."PercentOfBusiness__c",
    PGTISurvey."Brands__c",
    PGTISurvey."Competitor_Feedback__c",
    PGTISurvey."CreatedDate",
    PGTISurvey."IsDeleted",
    PGTISurvey."Dealers_primary_customer_type__c",
    PGTISurvey."Entry_Difficulty__c",
    PGTISurvey."ETP_Year__c",
    PGTISurvey."External_Account_Owner__c",
    PGTISurvey."Internal_Feedback_Buckets__c",
    PGTISurvey."Feedback_from_dealer_during_visit__c",
    PGTISurvey."How_did_you_interact_with_your_dealer__c",
    PGTISurvey."Internal_Feedback_Disposition__c",
    PGTISurvey."LastActivityDate",
    PGTISurvey."LastModifiedDate",
    PGTISurvey."LastReferencedDate",
    PGTISurvey."LastViewedDate",
    PGTISurvey."Notify_Sales_Support__c",
    PGTISurvey."Percent_of_Business__c",
    PGTISurvey."Prospect_Type__c",
    PGTISurvey."Repair_Service_Offered__c",
    PGTISurvey."Sales_Order_Line_Number__c",
    PGTISurvey."Sales_order_numbers_related_to_feedback__c",
    PGTISurvey."Showroom_Improvement__c",
    PGTISurvey."Status__c"

FROM stg4_pgti."Survey__c" PGTISurvey

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTISurvey."Account__c" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Account" MITERDealerAccount ON PGTISurvey."Name_of_dealer_visited__c" = MITERDealerAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Performance_Card__c" MITERPerformanceCard ON PGTISurvey."Performance_Card__c" = MITERPerformanceCard."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTISurvey."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTISurvey."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTISurvey."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Survey__c" MITERSurvey ON PGTISurvey."Id" = MITERSurvey."PGTI_Salesforce_Ext_Id__c"

WHERE MITERSurvey."PGTI_Salesforce_Ext_Id__c" IS NULL;


```

# Marketing\_Development\_Budget\_\_c

**Marketing\_Development\_Budget\_\_c**

```sql
SELECT
    PGTIMarketingDevBudget."Id" AS "PGTI_Salesforce_Ext_Id__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIMarketingDevBudget."Name",
    PGTIMarketingDevBudget."Budget_Allocated__c",
    PGTIMarketingDevBudget."Budget_Total__c",
    PGTIMarketingDevBudget."Start_Date__c",
    PGTIMarketingDevBudget."End_Date__c"

FROM stg4_pgti."Marketing_Development_Budget__c" PGTIMarketingDevBudget

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIMarketingDevBudget."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIMarketingDevBudget."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIMarketingDevBudget."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Marketing_Development_Budget__c" MITERMarketingDevBudget ON PGTIMarketingDevBudget."Id" = MITERMarketingDevBudget."PGTI_Salesforce_Ext_Id__c"

WHERE MITERMarketingDevBudget."PGTI_Salesforce_Ext_Id__c" IS NULL;

```

# Marketing\_Development\_Allocation\_\_c

**Marketing\_Development\_Allocation\_\_c**

```sql
SELECT
    PGTIMarketingDevAllocation."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERMarketingDevBudget."Id" AS "Budget__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIMarketingDevAllocation."Allocation_Total__c",
    PGTIMarketingDevAllocation."Type__c"

FROM stg4_pgti."Marketing_Development_Allocation__c" PGTIMarketingDevAllocation

LEFT JOIN stg4_miter."Marketing_Development_Budget__c" MITERMarketingDevBudget ON PGTIMarketingDevAllocation."Budget__c" = MITERMarketingDevBudget."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIMarketingDevAllocation."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIMarketingDevAllocation."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIMarketingDevAllocation."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Marketing_Development_Allocation__c" MITERMarketingDevAllocation ON PGTIMarketingDevAllocation."Id" = MITERMarketingDevAllocation."PGTI_Salesforce_Ext_Id__c"

WHERE MITERMarketingDevAllocation."PGTI_Salesforce_Ext_Id__c" IS NULL;
```

# Marketing\_Development\_Fund\_\_c

**Marketing\_Development\_Fund\_\_c**

```sql
SELECT
    PGTIMarketingDevFund."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERAccount."Id" AS "Account__c",
    MITERContact."Id" AS "Marketing_Contact__c",
    MITERMarketingDevAllocation."Id" AS "Marketing_Development_Allocation__c",
    CASE
        WHEN MITEROwner."Id" IS NOT NULL THEN MITEROwner."Id"
        ELSE '005UT000001c35xYAA'
    END AS "OwnerId",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIMarketingDevFund."Activity_Description__c",
    PGTIMarketingDevFund."isApproved__c",
    PGTIMarketingDevFund."Approved_Date__c",
    PGTIMarketingDevFund."Event_Start_Date__c",
    PGTIMarketingDevFund."Event_End_Date__c",
    PGTIMarketingDevFund."Expected_Start_Date__c",
    PGTIMarketingDevFund."Expected_End_Date__c",
    PGTIMarketingDevFund."Expected_Attendance__c",
    PGTIMarketingDevFund."Funds_Approved__c",
    PGTIMarketingDevFund."Funds_Requested__c",
    PGTIMarketingDevFund."Marketing_Activities__c",
    PGTIMarketingDevFund."Marketing_Activity__c",
    PGTIMarketingDevFund."Other_Marketing_Activities__c",
    PGTIMarketingDevFund."Other_Target_Market_Segments__c",
    PGTIMarketingDevFund."Target_Market_Segments__c",
    PGTIMarketingDevFund."Projected_Revenue__c",
    PGTIMarketingDevFund."Status__c"

FROM stg4_pgti."Marketing_Development_Fund__c" PGTIMarketingDevFund

LEFT JOIN stg4_miter."Account" MITERAccount ON PGTIMarketingDevFund."Account__c" = MITERAccount."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Contact" MITERContact ON PGTIMarketingDevFund."Marketing_Contact__c" = MITERContact."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Marketing_Development_Allocation__c" MITERMarketingDevAllocation ON PGTIMarketingDevFund."Marketing_Development_Allocation__c" = MITERMarketingDevAllocation."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITEROwner ON PGTIMarketingDevFund."OwnerId" = MITEROwner."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIMarketingDevFund."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIMarketingDevFund."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Marketing_Development_Fund__c" MITERMarketingDevFund ON PGTIMarketingDevFund."Id" = MITERMarketingDevFund."PGTI_Salesforce_Ext_Id__c"

WHERE MITERMarketingDevFund."PGTI_Salesforce_Ext_Id__c" IS NULL;

```

# Marketing\_Development\_Request\_\_c

**Marketing\_Development\_Request\_\_c**

```sql
SELECT
    PGTIMarketingDevRequest."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERMarketingDevAllocation."Id" AS "Marketing_Development_Allocation__c",
    MITERMarketingDevFund."Id" AS "Marketing_Development_Fund__c",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIMarketingDevRequest."Funds_Approved__c"

FROM stg4_pgti."Marketing_Development_Request__c" PGTIMarketingDevRequest

LEFT JOIN stg4_miter."Marketing_Development_Allocation__c" MITERMarketingDevAllocation ON PGTIMarketingDevRequest."Marketing_Development_Allocation__c" = MITERMarketingDevAllocation."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Marketing_Development_Fund__c" MITERMarketingDevFund ON PGTIMarketingDevRequest."Marketing_Development_Fund__c" = MITERMarketingDevFund."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIMarketingDevRequest."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIMarketingDevRequest."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Marketing_Development_Request__c" MITERMarketingDevRequest ON PGTIMarketingDevRequest."Id" = MITERMarketingDevRequest."PGTI_Salesforce_Ext_Id__c"

WHERE MITERMarketingDevRequest."PGTI_Salesforce_Ext_Id__c" IS NULL;


```

# Marketing\_Development\_Claim\_\_c

**Marketing\_Development\_Claim\_\_c**

```sql
SELECT
    PGTIMarketingDevClaim."Id" AS "PGTI_Salesforce_Ext_Id__c",
    MITERMarketingDevAllocation."Id" AS "Marketing_Development_Allocation__c",
    MITERMarketingDevFund."Id" AS "Marketing_Development_Fund__c",
    CASE
        WHEN MITERCreatedBy."Id" IS NOT NULL THEN MITERCreatedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "CreatedById",
    CASE
        WHEN MITERLastModifiedBy."Id" IS NOT NULL THEN MITERLastModifiedBy."Id"
        ELSE '005UT000001c35xYAA'
    END AS "LastModifiedById",
    PGTIMarketingDevClaim."AdFrom__c",
    PGTIMarketingDevClaim."AdTo__c",
    PGTIMarketingDevClaim."Claim_Amount_Approved__c",
    PGTIMarketingDevClaim."Claim_Amount_Requested__c",
    PGTIMarketingDevClaim."Claim_Number__c",
    PGTIMarketingDevClaim."Claim_Status__c",
    PGTIMarketingDevClaim."Credit_Memo_Number__c",
    PGTIMarketingDevClaim."Invoice_Number__c",
    PGTIMarketingDevClaim."Media_Company_Name__c",
    PGTIMarketingDevClaim."Media_Desc__c",
    PGTIMarketingDevClaim."Paid_Amount__c",
    PGTIMarketingDevClaim."Process_Date__c",
    PGTIMarketingDevClaim."Program_Start_Date__c",
    PGTIMarketingDevClaim."Program_End_Date__c"

FROM stg4_pgti."Marketing_Development_Claim__c" PGTIMarketingDevClaim

LEFT JOIN stg4_miter."Marketing_Development_Allocation__c" MITERMarketingDevAllocation ON PGTIMarketingDevClaim."Marketing_Development_Allocation__c" = MITERMarketingDevAllocation."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Marketing_Development_Fund__c" MITERMarketingDevFund ON PGTIMarketingDevClaim."Marketing_Development_Fund__c" = MITERMarketingDevFund."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERCreatedBy ON PGTIMarketingDevClaim."CreatedById" = MITERCreatedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."User" MITERLastModifiedBy ON PGTIMarketingDevClaim."LastModifiedById" = MITERLastModifiedBy."PGTI_Salesforce_Ext_Id__c"

LEFT JOIN stg4_miter."Marketing_Development_Claim__c" MITERMarketingDevClaim ON PGTIMarketingDevClaim."Id" = MITERMarketingDevClaim."PGTI_Salesforce_Ext_Id__c"

WHERE MITERMarketingDevClaim."PGTI_Salesforce_Ext_Id__c" IS NULL;

```

