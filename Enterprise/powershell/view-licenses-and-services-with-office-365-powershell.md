---
title: Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other, O365ITProTrain, LIL_Placement, PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: "Erläutert, wie Sie Office 365 PowerShell, zum Anzeigen von Informationen zu Lizenzierung Pläne, Dienste und Lizenzen, die in Office 365-Organisation verfügbar sind."
ms.openlocfilehash: 50c2d22d35cbf0d38f80515f8013e797d19ae483
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="debef-103">Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="debef-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="debef-104">**Zusammenfassung:** Erläutert, wie Sie Office 365 PowerShell, zum Anzeigen von Informationen zu Lizenzierung Pläne, Dienste und Lizenzen, die in Office 365-Organisation verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="debef-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="debef-105">Jeder Office 365-Abonnement umfasst die folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="debef-105">Every Office 365 subscription consists of the following elements:</span></span>
- <span data-ttu-id="debef-p101">**Lizenzierung von Plänen** Diese werden auch Aslicense Pläne oder Office 365-Pläne bezeichnet. Lizenzierungspläne definieren die Office 365-Dienste, die Benutzern zur Verfügung stehen. Office 365-Abonnement kann mehrere lizenzierungspläne enthalten. Ein Lizenzierungsplan Beispiel wäre Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="debef-p101">**Licensing plans** These are also known aslicense plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="debef-p102">**Dienste** Dies sind auch bekannte Asservice Pläne. Dienste sind die Office 365-Produkte, Features und Funktionen, die in jedem Lizenzierungsplan verfügbar sind beispielsweise Exchange Online und Office Professional Plus. Benutzer können mehrere Lizenzen aus verschiedenen lizenzierungspläne, die Zugriff auf verschiedene Dienste gewähren zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="debef-p102">**Services** These are also known asservice plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="debef-p103">**Lizenzen** Jede Lizenzierungsplan enthält die Anzahl der Lizenzen, die Sie erworben haben. Sie zuweisen Benutzern Lizenzen, sodass diese Office 365-Dienste verwenden können, die durch den Lizenzierungsplan definiert sind. Jedes Benutzerkonto erfordert mindestens eine Lizenz von einem Lizenzierungsplan, damit sie melden Sie sich bei Office 365 und die Dienste verwenden können.</span><span class="sxs-lookup"><span data-stu-id="debef-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="debef-p104">Office 365 PowerShell können Sie Details zu den verfügbaren lizenzierungspläne, Lizenzen und Dienste in Office 365-Organisation anzeigen. Weitere Informationen zu den Produkten, Features und Dienste, die in verschiedenen Office 365-Abonnements verfügbar sind, finden Sie unter [Planen der Office 365-Produkten](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="debef-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="debef-118">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="debef-118">Before you begin</span></span>
<span data-ttu-id="debef-119"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="debef-119"></span></span>

- <span data-ttu-id="debef-p105">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="debef-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="debef-p106">Ein PowerShell-Skript ist verfügbar, die die in diesem Thema beschriebenen Verfahren automatisiert. Insbesondere ermöglicht das Skript anzeigen und Deaktivieren von Diensten in Office 365-Organisation, einschließlich Schlingern. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Schlingern mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="debef-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="debef-125">Anzeigen von Informationen zu Lizenzierungsplänen und den verfügbaren Lizenzen</span><span class="sxs-lookup"><span data-stu-id="debef-125">View information about licensing plans and the available licenses</span></span>
<span data-ttu-id="debef-126"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="debef-126"></span></span>

<span data-ttu-id="debef-127">Um zusammenfassende Informationen zu Ihrer aktuellen Pläne Lizenzierung und den verfügbaren Lizenzen für jeden Plan anzuzeigen, führen Sie in Office 365 PowerShell den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="debef-127">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="debef-128">Die Ergebnisse enthalten die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="debef-128">The results contain the following information:</span></span>
  
- <span data-ttu-id="debef-p107">**AccountSkuId:** Anzeigen der verfügbaren lizenzierungspläne für Ihre Organisation mithilfe der Syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ ist der Wert, der Sie bereitgestellt werden, wenn Sie in Office 365 registriert, und für Ihre Organisation eindeutig ist. Die _<LicensingPlan>_ Wert gilt für alle Benutzer. Beispielsweise in den Wert `litwareinc:ENTERPRISEPACK`, den Namen des Unternehmens ist `litwareinc`, und den Namen der Lizenzierung Plan `ENTERPRISEPACK`, dies ist der Systemname für Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="debef-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="debef-133">**ActiveUnits:** Anzahl der Lizenzen, dass Einkäufe für eine bestimmte Lizenzierungsplan haben.</span><span class="sxs-lookup"><span data-stu-id="debef-133">**ActiveUnits:** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="debef-134">**WarningUnits:** Anzahl der Lizenzen in einer Lizenzierungsplan, die Sie noch nicht erneuert und läuft, die nach der 30-Tage-Nachfrist.</span><span class="sxs-lookup"><span data-stu-id="debef-134">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="debef-135">**ConsumedUnits:** Anzahl der Lizenzen, die Sie den Benutzer aus einer bestimmten Lizenzierungsplan zugewiesen haben.</span><span class="sxs-lookup"><span data-stu-id="debef-135">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="debef-136">Um Details zu Office 365-Dienste anzuzeigen, die in allen Ihre Lizenz Pläne verfügbar sind, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="debef-136">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="debef-p108">Die folgende Tabelle zeigt die Office 365-Dienstplänen und ihren Anzeigenamen für die am häufigsten verwendeten Dienste. Die Liste der Servicepläne kann unterschiedlich sein. Eine vollständige Liste der Dienste und deren Anzeigenamen wenden Sie sich an [Office – Support](https://support.office.com/home/contact).</span><span class="sxs-lookup"><span data-stu-id="debef-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different. For a complete list of service plans and their friendly names, contact [Office Support](https://support.office.com/home/contact).</span></span>
  
|<span data-ttu-id="debef-140">Dienst Plan \*\*\*</span><span class="sxs-lookup"><span data-stu-id="debef-140">****Service plan****</span></span>|<span data-ttu-id="debef-141">Beschreibung \*\*\*</span><span class="sxs-lookup"><span data-stu-id="debef-141">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="debef-142">Sway</span><span class="sxs-lookup"><span data-stu-id="debef-142">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="debef-143">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="debef-143">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="debef-144">Yammer</span><span class="sxs-lookup"><span data-stu-id="debef-144">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="debef-145">Azure-Rechteverwaltung (Rights Management, RMS)</span><span class="sxs-lookup"><span data-stu-id="debef-145">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="debef-146">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="debef-146">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="debef-147">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="debef-147">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="debef-148">Office Online</span><span class="sxs-lookup"><span data-stu-id="debef-148">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="debef-149">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="debef-149">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="debef-150">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="debef-150">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="debef-151">Verwenden Sie die folgende Syntax, um Details zu Office 365-Dienste anzuzeigen, die in einer bestimmten Lizenzierungsplan verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="debef-151">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="debef-152">Dieses Beispiel zeigt die Office 365-Dienste, die in den Lizenzierungsplan litwareinc: enterprisepack (Office 365 Enterprise E3) zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="debef-152">This example shows the Office 365 services that are available in the  litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="debef-153">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="debef-153">New to Office 365?</span></span>
<span data-ttu-id="debef-154"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="debef-154"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="debef-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="debef-155">See also</span></span>
<span data-ttu-id="debef-156"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="debef-156"></span></span>

#### 

[<span data-ttu-id="debef-157">Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="debef-157">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
  
[<span data-ttu-id="debef-158">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="debef-158">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
#### 

[<span data-ttu-id="debef-159">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="debef-159">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

