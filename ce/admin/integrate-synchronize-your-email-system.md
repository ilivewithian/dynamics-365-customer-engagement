---
title: "Integrate (synchronize) your email system with Dynamics 365 Customer Engagement | MicrosoftDocs"
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
ms.assetid: 6804d996-86b2-4fb0-aed9-21fbdde0bab5
caps.latest.revision: 26
author: "jimholtz"
ms.author: "jimholtz"
manager: "brycho"
---
# Integrate (synchronize) your email system
One of the main reasons people use [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.  
  
 To store email and other messaging records in [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)], you need to synchronize your email system with [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)]. There are two ways to do this:  
  
- server-side synchronization  
  
- [!INCLUDE[pn_crm_for_outlook_full](../includes/pn-crm-for-outlook-full.md)] (includes a synchronization agent)  
  
> [!IMPORTANT]
>  -   In previous versions of Dynamics CRM, you could also use the Email Router to synchronize records. The Email Router has been deprecated as of the [!INCLUDE[pn_crm_9_0_0_online](../includes/pn-crm-9-0-0-online.md)].  We strongly recommend that you migrate all email routing functionality to use  server-side synchronization. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [Migrate settings from the Email Router to server-side synchronization](../admin/migrate-settings-email-router-server-side-synchronization.md)  
> -   Internet Message Access Protocol (IMAP) email servers are not currently supported by server-side synchronization or the Email Router.  
  
<a name="ServerSideSync"></a>   
## When to use server-side synchronization  
 server-side synchronization is the preferred synchronization method for the following reasons:  
  
- **Enables [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)]**. With [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] (not the same thing as [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]), [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] information appears  next to a user’s [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] email messages or appointments. They can view information about contacts and leads stored in [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] and add [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] contacts directly from an email message. They can also link email, appointment, and contact records  to new or existing [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] records, such as opportunity, account, or case records. [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] is very simple to deploy and it works with [!INCLUDE[pn-outlook-short](../includes/pn-outlook-short.md)] on the web (included in [!INCLUDE[pn_MS_Office_365](../includes/pn-ms-office-365.md)])  the [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] desktop client, and [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] mobile. [Learn more about Dynamics 365 App for Outlook](http://go.microsoft.com/fwlink/p/?LinkID=613099).  
  
- **Enables [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] folder tracking**. With folder tracking, users can simply drag email to an [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] folder to track it automatically in [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)]. Folder tracking works on any mobile device that supports [!INCLUDE[pn_Microsoft_Exchange](../includes/pn-microsoft-exchange.md)], which means users can track email from just about any device. [Learn more about folder tracking](http://go.microsoft.com/fwlink/p/?LinkID=533918).  
  
- **Automatic synchronization**. When you synchronize records with server-side synchronization, the synchronization happens automatically at the server level. This isn’t true if you synchronize records with [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]. In this case, the user has to have [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] open to synchronize records.  
  
- **Enables multiple scenarios, including hybrid scenarios**. You can use server-side synchronization to connect:  
  
    - [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] to [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]  
  
    - [!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] to [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises)  
  
    - [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] Server (on-premises) to [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises)  
  
    - [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] Server (on-premises) to [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]  
  
- **Synchronize appointments, contacts, and tasks**. In addition to email, you can synchronize [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] appointments, contacts, and tasks.  
  
- **Synchronize with [!INCLUDE[pn_POP3_short](../includes/pn-pop3-short.md)] email servers**. You can use server-side synchronization to synchronize [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] with Gmail, [!INCLUDE[pn_outlook_com](../includes/pn-outlook-com.md)], Yahoo, and other [!INCLUDE[pn_POP3_short](../includes/pn-pop3-short.md)] email servers. Note, however, that you can’t synchronize appointments, contacts, and tasks with [!INCLUDE[pn_POP3_short](../includes/pn-pop3-short.md)] email servers.  
  
- **Integrated mailbox management and resource utilization**. You can use the server-side synchronization performance dashboard to quickly monitor mailbox performance across the organization. You can also troubleshoot errors through error logging and reporting.  
  
 [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [Integrate your email system using server-side synchronization](../admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks.md)  
  
<a name="Outlook"></a>   
## When to use Dynamics 365 for Outlook  
 [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)], the legacy add-in for [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)], is a full [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] client that includes offline capabilities.  However, as of the [!INCLUDE[pn_crm_9_0_0_online](../includes/pn-crm-9-0-0-online.md)], the preferred way to use [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] and [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] together is to use [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] paired with server-side synchronization.  
  
 If you do use [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)], server-side synchronization isn't required since [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] has its own synchronization agent that runs on the user’s computer, but it’s best to do the synchronization through server-side synchronization for the reasons mentioned in the previous section. [Help and Training: Learn more about Dynamics 365 for Outlook](http://go.microsoft.com/fwlink/p/?LinkID=524751)  
  
### See also  
 [Integrate your email system using server-side synchronization](../admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks.md)   
 [Troubleshooting and monitoring server-side synchronization issues](../admin/troubleshooting-monitoring-server-side-synchronization.md)   
 [Deploy Dynamics 365 App for Outlook](../admin/deploy-dynamics-365-app-for-outlook.md)   
 [Set up Dynamics 365 for Outlook](../admin/install-outlook.md)   
 [Migrate settings from the Email Router to server-side synchronization](../admin/migrate-settings-email-router-server-side-synchronization.md)