---
title: "Translate product names and properties into multiple languages (Dynamics 365 for Sales, Enterprise edition) | MicrosoftDocs"
ms.custom: ""
ms.date: "2017-08-31"
ms.reviewer: ""
ms.service: "crm-online"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "Dynamics 365 (online)"
  - "Dynamics 365 Version 9.x"
ms.assetid: 6eb8263b-b8a0-4d8b-8383-956d380a203d
caps.latest.revision: 21
ms.author: "shujoshi"
manager: "brycho"
---
# Translate product names and properties into multiple languages (Sales, Enterprise)
When you sell your products in different regions, it is important that you translate significant product details into multiple languages. Help sales agents find things they need easily by making all the relevant details like cross-sell or upsell suggestions, or properties, available to them in their preferred language.   
  
<a name="bkmk_Export"></a>   
## Step 1: Export data for translation  
  
1.  [!INCLUDE[proc_permissions_admin_cust_mgr_vp_sales_ceo](../includes/proc-permissions-admin-cust-mgr-vp-sales-ceo.md)]  
  
    ###### Check your security role  
  
    -   [!INCLUDE[proc_follow_steps_in_link](../includes/proc-follow-steps-in-link.md)]  
  
    -   [!INCLUDE[proc_dont_have_correct_permissions](../includes/proc-dont-have-correct-permissions.md)]  
  
2.  [!INCLUDE[proc_settings_datamanagement](../includes/proc-settings-datamanagement.md)]  
  
3.  Click **Export Field Translations**.  
  
4.  In the **Export Field Translations** dialog box, click **OK**.  
  
     All product fields that are marked as localizable by default will be exported. Your internal developers can mark the fields as localizable. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] Work with localizable attributes.  
  
5.  Save the .zip file to your local computer.  
  
     Exported text is saved as a compressed file that contains a CrmFieldTranslations.xml that you can open by using [!INCLUDE[pn_microsoft_excel](../includes/pn-microsoft-excel.md)]. You can send this file to a linguistic expert, translation agency, or localization firm.  
  
<a name="bkmk_Import"></a>   
## Step 2: Import translated data  
 When you get the localized data back from translation, import it into [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)].  
  
> [!IMPORTANT]
>  It is important to provision the language packs first. If you import translated values for languages that aren’t provisioned in the organization, they’ll be discarded. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [Install or upgrade Language Packs for Microsoft Dynamics CRM](https://technet.microsoft.com/library/hh699674.aspx)  
  
1.  [!INCLUDE[proc_permissions_mgr_vp_ceo_busmgr_sysadmin_syscust](../includes/proc-permissions-mgr-vp-ceo-busmgr-sysadmin-syscust.md)]  
  
    ###### Check your security role  
  
    -   [!INCLUDE[proc_follow_steps_in_link](../includes/proc-follow-steps-in-link.md)]  
  
    -   [!INCLUDE[proc_dont_have_correct_permissions](../includes/proc-dont-have-correct-permissions.md)]  
  
2.  [!INCLUDE[proc_settings_datamanagement](../includes/proc-settings-datamanagement.md)]  
  
3.  Click **Import Field Translations**.  
  
4.  In the **Field Translation Import Jobs** page, on the Action toolbar, click **Import Field Translations**.  
  
5.  In the **Import Translated Text** dialog box, click **Browse**, and select the file that you’ve received from your translation agency.  
  
6.  Click **Import**.  
  
     This starts the import job. You can check the status to see if the import has succeeded or failed.  
  
 After you’ve imported the translated text, users in your organization will see the data in their preferred language. If a value for the preferred language does not exist, the results will be shown in the user’s base language.  
  
<a name="bkmk_LanguageSelection"></a>   
## Selection of language in different scenarios  
 This section explains how the duplicate detection and workflow logic affect translation in [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)]:  
  
-   Calculated fields logic, including conditional clauses, uses only the base language. The behavior of workflows and portable business logic is similar to [!INCLUDE[pn_sdk](../includes/pn-sdk.md)]. The label for the user’s preferred language (user interface language) is used if present. Otherwise, the base language is used.  
  
-   When a record is created or updated, duplicates are detected from the localizable fields (attributes) that are in the base language. Creating or updating a localizable field is not applicable in a non-base language.  
  
-   During data import,  
  
    -   For updating or creating records through import, when import is executed in base language, only the labels in the base language are used for duplication detection.  
  
    -   When import is executed in non-base language, import fails because update can’t be performed in a non-base language.  
  
-   When you run duplicate detection in the base language, only the base language is used in conditional clauses.  
  
-   When you run duplicate detection job in the preferred language, label in the preferred language is used first. When preferred language is not available, it uses the base language.  
  
### See also  
 [Set up a product catalog: Walkthrough](Set%20up%20a%20product%20catalog:%20Walkthrough.md)   
 [Set up duplicate detection rules to keep your data clean](../admin/set-up-duplicate-detection-rules-keep-data-clean.md)