---
title: BYOK pricing and restrictions
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: TBD
author: Cabailey
---
# BYOK pricing and restrictions

Organization that have an IT-managed Azure subscription can use BYOK and log its usage at no extra charge. Organizations that use RMS for individuals cannot use BYOK and logging because they do not have a tenant administrator to configure these features.

> [!NOTE]
> For more information about RMS for individuals, see [RMS for Individuals and Azure Rights Management](rms-for-individuals-and-azure-rights-management.md).

![](./media/RMS_BYOK_noExchange.png)

BYOK and logging work seamlessly with every application that integrates with Azure RMS. This includes cloud services such as SharePoint Online, on-premises servers that run Exchange and SharePoint that work with Azure RMS by using the RMS connector, and client applications such as Office 2013. You will get key usage logs regardless of which application makes requests of Azure RMS.

There is one exception: Currently, **Azure RMS BYOK is not compatible with Exchange Online**.  If you want to use Exchange Online, we recommend that you deploy Azure RMS in the default key management mode now, where Microsoft generates and manages your key. You have the option to move to BYOK later, for example, when Exchange Online does support Azure RMS BYOK. However, if you cannot wait, another option is to deploy Azure RMS with BYOK now, with reduced RMS functionality for Exchange Online (unprotected emails and unprotected attachments remain fully functional):

-   Protected emails or protected attachments in Outlook Web Access cannot be displayed.

-   Protected emails on mobile devices that use Exchange ActiveSync IRM cannot be displayed.

-   Transport decryption (for example, to scan for malware) and journal  decryption is not possible, so protected emails and protected attachments will be skipped.

-   Transport protection rules and data loss prevention (DLP) that enforce IRM policies is not possible, so RMS protection cannot be applied by using these methods.

-   Server-based search for protected emails, so protected emails will be skipped.

When you use Azure RMS BYOK with reduced RMS functionality for Exchange Online, RMS will work with email clients in Outlook on Windows and Mac, and on other email clients that don't use Exchange ActiveSync IRM.

If you are migrating to Azure RMS from AD RMS, you might have imported your key as a trusted publishing domain (TPD) to Exchange Online (also called BYOK in Exchange terminology, which is separate from Azure RMS BYOK). In this scenario, you must remove the TPD from Exchange Online to avoid conflicting templates and policies. For more information, see [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) from the Exchange Online cmdlets library.

Sometimes, the Azure RMS BYOK  exception for Exchange Online is not a problem in practice. For example, organizations that need BYOK and logging run their data applications (Exchange, SharePoint, Office) on-premises, and use Azure RMS for functionality that is not easily available with on-premises AD RMS (for example, collaboration with other companies and access from mobile clients). Both BYOK and logging work well in this scenario and allow the organization to have full control over their Azure RMS subscription.

## Next steps

If you've made the decision to manage your own key, go to [Implementing bring your own key (BYOK)](implementing-your-azure-rights-management-tenant-key.md).

If you've decided to stay with the default configuration where Microsoft manages your tenant key, see the [Next steps]((planning-and-implementing-your-azure-rights-management-tenant-key.md#BKMK_NextSteps) section of the Planning and implementing your Azure Rights Management tenant key article.
