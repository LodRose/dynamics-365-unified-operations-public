---
# required metadata

title: Dynamics 365 for Finance and Operations, Enterprise edition 7.2 with platform update 12 for on-premises deployments
description: This topic describes features that are either new or changed in on-premises deployments of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.2 with platform update 12. This deployment option became available in March 2018.
author: sericks007
manager: AnnBe
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2017-11-30 
ms.dyn365.ops.version: Platform update 12 

---

# What's new or changed in on-premises deployments of Dynamics 365 for Finance and Operations, Enterprise edition 7.2 with platform update 12 (March 2018)

[!include[banner](../includes/banner.md)]

This topic describes features that are either new or changed in on-premises deployments of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.2 with platform update 12. This deployment option became available in March 2018.

For more information about platform update 12, see [What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 12](whats-new-platform-update-12.md).

For more resources about on-premises deployments, see [On-premises deployment landing page](../../dev-itpro/deployment/on-premises-deployment-landing-page.md).

## Setup and deployment
Improvements have been made to the setup and deployment process. These improvements significantly reduce the time that is required for deployment. Increased automation and multiple prerequisite validations have also been added to improve reliability. For more information, see [Set up and deploy on-premises environments (Platform update 12)](../../dev-itpro/deployment/setup-deploy-on-premises-pu12.md).

## Servicing
After your on-premises environment is deployed, you can now use Microsoft Dynamics Lifecycle Services (LCS) to apply platform and application updates that Microsoft releases. You can also apply code customizations. Therefore, customers can stay current with the latest set of fixes and take up new customizations without having to reconfigure an existing environment or redeploy the on-premises environment. Additionally, you can now roll back code changes if packages aren't successfully applied. For more information, see [Apply updates to an on-premises deployment](../../dev-itpro/deployment/apply-updates-on-premises.md).

Note that the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) will remain available for environments that were deployed with platform update versions that are earlier than Platform update 12.

## Hotfixes
Hotfixes that you can download from LCS provide additional features for your on-premises deployments of Platform update 12. Be sure to apply the following hotfixes:

- **KB 4091763: Admin toggles for Client connectivity and Skype presence**: This hotfix enables administrators to disable experiences that depend on internet connectivity on client machines.

