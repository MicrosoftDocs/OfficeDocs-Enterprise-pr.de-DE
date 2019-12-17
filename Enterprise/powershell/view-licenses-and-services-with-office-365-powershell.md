---
title: Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: In diesem Artikel wird erläutert, wie Sie mithilfe von Office 365 PowerShell Informationen zu den Lizenzierungsplänen, Diensten und Lizenzen anzeigen können, die in Ihrer Office 365-Organisation verfügbar sind.
ms.openlocfilehash: d212a79be127dabae52993cb8cfd21fb848b3aad
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072157"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="e87e7-103">Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e87e7-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="e87e7-104">Jedes Office 365-Abonnement besteht aus den folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="e87e7-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="e87e7-p101">**Lizenzierungspläne**: Diese werden auch als Lizenzpläne oder Office 365-Pläne bezeichnet. Lizenzierungspläne definieren die Office 365-Dienste, die für Benutzer verfügbar sind. Ihr Office 365-Abonnement kann mehrere Lizenzierungspläne enthalten. Ein Beispiel für einen Lizenzierungsplan ist Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="e87e7-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e87e7-p102">**Dienste**: Sie werden auch als Servicepläne bezeichnet. Dienste sind die Office 365-Produkte, -Features und -Funktionen, die jeweils in den verschiedenen Lizenzierungsplänen inbegriffen sind, zum Beispiel Exchange Online und Office Professional Plus. Benutzern können mehrere verschiedene Lizenzen aus unterschiedlichen Lizenzierungsplänen zugewiesen sein, über die sie Zugriff auf unterschiedliche Dienste haben.</span><span class="sxs-lookup"><span data-stu-id="e87e7-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="e87e7-p103">**Lizenzen**: Ein Lizenzierungsplan enthält die Anzahl von Lizenzen, die Sie erworben haben. Die Lizenzen weisen Sie Benutzern zu, damit sie die im Lizenzierungsplan definierten Office 365-Dienste nutzen können. Einem Benutzerkonto muss mindestens eine (1) Lizenz aus einem Lizenzierungsplan zugewiesen sein, damit der Benutzer sich mit dem Konto bei Office 365 anmelden und die Dienste nutzen kann.</span><span class="sxs-lookup"><span data-stu-id="e87e7-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="e87e7-p104">Sie können Office 365 PowerShell verwenden, um Details zu den verfügbaren Lizenzierungsplänen, Lizenzen und Diensten in Ihrer Office 365-Organisation anzuzeigen. Weitere Informationen dazu, welche Produkte, Features und Dienste in den verschiedenen Office 365-Abonnements verfügbar sind, finden Sie unter [Optionen zum Office 365-Plan](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="e87e7-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e87e7-117">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="e87e7-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e87e7-118">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e87e7-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="e87e7-119">Führen Sie den folgenden Befehl aus, um zusammenfassende Informationen zu Ihren aktuellen Lizenzierungs Plänen und den verfügbaren Lizenzen für jeden Plan anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="e87e7-119">To view summary information about your current licensing plans and the available licenses for each plan, run this command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="e87e7-120">Die Ergebnisse enthalten:</span><span class="sxs-lookup"><span data-stu-id="e87e7-120">The results contain:</span></span>
  
- <span data-ttu-id="e87e7-p105">**SkuPartNumber:** Zeigt die verfügbaren Lizenzierungspläne für Ihre Organisation an. `ENTERPRISEPACK` ist z. B. der Name des Lizenzplans für Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="e87e7-p105">**SkuPartNumber:** Shows the available licensing plans for your organization. For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e87e7-123">**Enabled:**: Gibt die Anzahl der Lizenzen an, die Sie im Rahmen eines spezifischen Lizenzierungsplans erworben haben.</span><span class="sxs-lookup"><span data-stu-id="e87e7-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="e87e7-124">**ConsumedUnits**: Gibt die Anzahl der Lizenzen an, die Sie Benutzern aus einem bestimmten Lizenzierungsplan zugewiesen haben.</span><span class="sxs-lookup"><span data-stu-id="e87e7-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="e87e7-125">Zeigen Sie zunächst eine Liste Ihrer Lizenzierungspläne an, um Details zu allen verfügbaren Office 365-Diensten in Ihrem gesamten Lizenzplanbestand anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e87e7-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="e87e7-126">Speichern Sie dann die Informationen zu den Lizenzplänen in einer Variablen.</span><span class="sxs-lookup"><span data-stu-id="e87e7-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="e87e7-127">Zeigen Sie die Dienste in einem spezifischen Lizenzplan an.</span><span class="sxs-lookup"><span data-stu-id="e87e7-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="e87e7-128">\<Index > ist eine ganze Zahl, die die Zeilennummer des Lizenzplans aus der Anzeige des `Get-AzureADSubscribedSku | Select SkuPartNumber`-Befehls minus 1 angibt.</span><span class="sxs-lookup"><span data-stu-id="e87e7-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="e87e7-129">Wenn die Anzeige des `Get-AzureADSubscribedSku | Select SkuPartNumber`-Befehls z.B. folgendermaßen lautet:</span><span class="sxs-lookup"><span data-stu-id="e87e7-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="e87e7-130">Lautet der Befehl zum Anzeigen der Dienste für den Plan ENTERPRISEPREMIUM folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="e87e7-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="e87e7-p106">ENTERPRISEPREMIUM ist die dritte Zeile. Aus diesem Grund wird der Indexwert mit (3 - 1) oder 2 angegeben.</span><span class="sxs-lookup"><span data-stu-id="e87e7-p106">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="e87e7-133">Eine vollständige Liste von Lizenzplänen (auch bezeichnet als Produktnamen), deren enthaltenen Serviceplänen und die entsprechenden Anzeigenamen finden Sie unter [Produktnamen und Serviceplanbezeichner für die Lizenzierung](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="e87e7-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e87e7-134">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e87e7-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e87e7-135">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e87e7-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="e87e7-p107">Ein PowerShell-Skript steht zur Verfügung, das die in diesem Thema erläuterten Verfahren automatisiert. Insbesondere ermöglicht das Skript Ihnen das Anzeigen und Deaktivieren von Diensten in Ihrer Office 365-Organisation, einschließlich Sway. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Sway mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e87e7-p107">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="e87e7-139">Führen Sie den folgenden Befehl aus, um eine Übersicht über Ihre aktuellen Lizenzierungspläne und die in den einzelnen Plänen verfügbaren Lizenzen anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="e87e7-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="e87e7-140">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="e87e7-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e87e7-141">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="e87e7-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="e87e7-142">Die Ergebnisse enthalten die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="e87e7-142">The results contain the following information:</span></span>
  
- <span data-ttu-id="e87e7-143">**AccountSkuId:** Zeigen Sie die verfügbaren Lizenzierungs Pläne für Ihre Organisation mithilfe `<CompanyName>:<LicensingPlan>`der Syntax an.</span><span class="sxs-lookup"><span data-stu-id="e87e7-143">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="e87e7-144">CompanyName>ist der Wert, den Sie bei der Registrierung in Office 365 angegeben haben und der für Ihre Organisation eindeutig ist. _ \<_</span><span class="sxs-lookup"><span data-stu-id="e87e7-144">_\<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="e87e7-145">Der Wert für _ \<LicensingPlan>_ ist für jeden identisch.</span><span class="sxs-lookup"><span data-stu-id="e87e7-145">The _\<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="e87e7-146">Beispielsweise ist `litwareinc:ENTERPRISEPACK` `litwareinc`in dem Wert der Name des Unternehmens und der Name `ENTERPRISEPACK`des Lizenzierungs Plans, bei dem es sich um den Systemnamen für Office 365 Enterprise E3 handelt.</span><span class="sxs-lookup"><span data-stu-id="e87e7-146">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="e87e7-147">**ActiveUnits**: Gibt die Anzahl der Lizenzen an, die Sie im Rahmen eines spezifischen Lizenzierungsplans erworben haben.</span><span class="sxs-lookup"><span data-stu-id="e87e7-147">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="e87e7-148">**WarningUnits**: Gibt die Anzahl der Lizenzen in einem Lizenzierungsplan an, die Sie nicht verlängert haben und die nach der 30-tägigen Toleranzperiode ablaufen werden.</span><span class="sxs-lookup"><span data-stu-id="e87e7-148">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="e87e7-149">**ConsumedUnits**: Gibt die Anzahl der Lizenzen an, die Sie Benutzern aus einem bestimmten Lizenzierungsplan zugewiesen haben.</span><span class="sxs-lookup"><span data-stu-id="e87e7-149">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="e87e7-150">Führen Sie den folgenden Befehl aus, um Details zu allen verfügbaren Office 365-Diensten in Ihrem gesamten Lizenzplanbestand anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="e87e7-150">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="e87e7-p110">In der folgenden Tabelle sind die Office 365-Servicepläne und Anzeigenamen der beliebtesten Dienste aufgeführt. Ihre individuelle Serviceplanliste sieht möglicherweise anders aus.</span><span class="sxs-lookup"><span data-stu-id="e87e7-p110">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="e87e7-153">**Dienstplan**</span><span class="sxs-lookup"><span data-stu-id="e87e7-153">**Service plan**</span></span>|<span data-ttu-id="e87e7-154">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="e87e7-154">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="e87e7-155">Sway</span><span class="sxs-lookup"><span data-stu-id="e87e7-155">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="e87e7-156">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e87e7-156">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="e87e7-157">Yammer</span><span class="sxs-lookup"><span data-stu-id="e87e7-157">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="e87e7-158">Azure-Rechteverwaltung (Rights Management, RMS)</span><span class="sxs-lookup"><span data-stu-id="e87e7-158">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="e87e7-159">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="e87e7-159">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="e87e7-160">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="e87e7-160">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="e87e7-161">Büro</span><span class="sxs-lookup"><span data-stu-id="e87e7-161">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="e87e7-162">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e87e7-162">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="e87e7-163">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="e87e7-163">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="e87e7-164">Eine vollständige Liste von Lizenzplänen (auch bezeichnet als Produktnamen), deren enthaltenen Serviceplänen und die entsprechenden Anzeigenamen finden Sie unter [Produktnamen und Serviceplanbezeichner für die Lizenzierung](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="e87e7-164">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="e87e7-165">Verwenden Sie die folgende Syntax, um Details zu den Office 365-Diensten anzuzeigen, die in einem spezifischen Lizenzierungsplan verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="e87e7-165">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="e87e7-166">Dieses Beispiel zeigt die Office 365-Dienste, die im Lizenzierungsplan litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="e87e7-166">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a><span data-ttu-id="e87e7-167">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e87e7-167">See also</span></span>

[<span data-ttu-id="e87e7-168">Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e87e7-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e87e7-169">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e87e7-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e87e7-170">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e87e7-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
