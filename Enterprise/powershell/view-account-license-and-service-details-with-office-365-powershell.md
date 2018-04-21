---
title: Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Erläutert, wie Office 365 PowerShell verwenden, um die Office 365-Dienste zu ermitteln, die Benutzern zugewiesen wurden.
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="594f8-103">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="594f8-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="594f8-104">**Zusammenfassung:** Erläutert, wie Office 365 PowerShell verwenden, um die Office 365-Dienste zu ermitteln, die Benutzern zugewiesen wurden.</span><span class="sxs-lookup"><span data-stu-id="594f8-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="594f8-p101">In Office 365 lizenziert Pläne Lizenzieren von (auch gewählte SKUs oder Office 365-Pläne) gewähren des Benutzerzugriffs auf Office 365-Dienste, die für diese Pläne definiert sind. Ein Benutzer möglicherweise jedoch nicht Zugriff auf alle Dienste, die in eine Lizenz verfügbar sind, die ihnen derzeit zugewiesen ist. Office 365 PowerShell können Sie den Status von Diensten auf Benutzerkonten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="594f8-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="594f8-108">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="594f8-108">Before you begin</span></span>
<span data-ttu-id="594f8-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="594f8-109"></span></span>

- <span data-ttu-id="594f8-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="594f8-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="594f8-112">Verwenden Sie die Befehle `Get-MsolAccountSku` und `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` , die folgende Informationen zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="594f8-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="594f8-113">Die Lizenzierungspläne, die in Ihrer Organisation verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="594f8-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="594f8-114">Die Dienste, die in den einzelnen Lizenzierungsplänen verfügbar sind, und die Reihenfolge, in der sie aufgelistet sind (die Indexnummer).</span><span class="sxs-lookup"><span data-stu-id="594f8-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="594f8-115">Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Dienste finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="594f8-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="594f8-116">Verwenden Sie den Befehl `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` , um die Lizenzen zu erhalten, die ein Benutzer und die Reihenfolge, in zugewiesen sind, sie darstellen (die Indexnummer) aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="594f8-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="594f8-117">Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="594f8-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
<span data-ttu-id="594f8-118"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="594f8-118"></span></span>
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="594f8-119">Die Kurzfassung (Anweisungen ohne Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="594f8-119">The short version (instructions without explanations)</span></span>

<span data-ttu-id="594f8-120">Wenn Sie alle Dienste von Office 365 PowerShell anzuzeigen, denen ein Benutzer zugreifen kann, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="594f8-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="594f8-p103">Dieses Beispiel zeigt die Dienste auf denen der Benutzer BelindaN@litwareinc.com zugreifen kann. Zeigt die Dienste, die alle Lizenzen zugeordnet sind, die ihr Konto zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="594f8-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="594f8-123">Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="594f8-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="594f8-124">Um alle lizenzierten Benutzer zu suchen, die für bestimmte Dienste aktiviert oder deaktiviert wurden, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="594f8-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="594f8-125">In diesen Beispielen werden folgende Informationen verwendet:</span><span class="sxs-lookup"><span data-stu-id="594f8-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="594f8-126">Die Lizenz, die den Zugriff auf die Office 365-Dienste bereitstellt, die wir interessiert sind ist die erste, das alle Benutzer zugeordnet ist (die Indexnummer ist 0).</span><span class="sxs-lookup"><span data-stu-id="594f8-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="594f8-p104">Office 365-Dienste, denen wir interessiert sind Skype für Business Online und Exchange Online. Für die Lizenzen, die den Lizenzierungsplan zugeordnet sind, Skype für Business Online der 6. Dienst aufgeführt ist (die Indexnummer ist 5), und Exchange Online ist der 9. Dienst aufgeführten (die Indexnummer ist 8).</span><span class="sxs-lookup"><span data-stu-id="594f8-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="594f8-129">Dieses Beispiel gibt alle lizenzierten Benutzer, die für Skype für Business Online und Exchange Online aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="594f8-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="594f8-130">Dieses Beispiel gibt alle lizenzierten Benutzer, die für Skype für Business Online oder Exchange Online nicht aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="594f8-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="594f8-131"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="594f8-131"></span></span>
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="594f8-132">Die Langfassung (Anweisungen mit detaillierten Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="594f8-132">The long version (instructions with detailed explanations)</span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="594f8-133">Hier finden Sie die PowerShell für Office 365-Dienste, denen ein Benutzer Zugriff hat</span><span class="sxs-lookup"><span data-stu-id="594f8-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="594f8-p105">Es ist offensichtlich wichtig, dass Sie wissen, welche Benutzer Office 365-Lizenzen ausgestellt wurden und welche Benutzer noch nicht. (Siehe den Artikel [lizenzierte und nicht lizenzierten Benutzer mit Office 365 PowerShell anzeigen](view-licensed-and-unlicensed-users-with-office-365-powershell.md) für Weitere Informationen). Nicht erfahren einfach dadurch, dass eine Office 365-Lizenz Sie jedoch alles über die Funktionen der Benutzer mit Office 365 tatsächlich durchführen kann. Kann er Exchange Online oder Skype für Business Online verwenden? Zugreifen dieser Benutzer kann SharePoint Online? Hat er Zugriff auf Office Professional Plus? Mit einer Lizenz bedeutet, dass der Benutzer auf diese Dienste zugreifen kann. Die für einen Benutzer verfügbaren Funktionen hängen jedoch die Dienste, die auf seinem Lizenz aktiviert wurden.</span><span class="sxs-lookup"><span data-stu-id="594f8-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="594f8-p106">Wie wir ermitteln können, die Office 365-Features hat ein Benutzer Zugriff auf? Dazu müssen Sie einen Befehl wie diesem Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="594f8-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="594f8-144">In diesem Befehl sind wir das Cmdlet **Get-MsolUser** verwenden, um Informationen über das Konto BelindaN@litwareinc.com zurückzugeben. Nachdem wir diese Informationen zurückgegeben haben, wir dann pipe an das **Select-Object** -Cmdlet-Kontodaten bitten und **Select-Object** , das "den Wert der Eigenschaft **Lizenzen** Erweitert":</span><span class="sxs-lookup"><span data-stu-id="594f8-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="594f8-p107">Warum tun wir, die? Nun, weist standardmäßig die **Lizenzen** -Eigenschaft nur uns den Namen des lizenzierungspakets, in dem Belindas Lizenz stammt:</span><span class="sxs-lookup"><span data-stu-id="594f8-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="594f8-147">"Erweitern" die **Lizenzen** -Eigenschaft liefert uns einige zusätzliche Informationen:</span><span class="sxs-lookup"><span data-stu-id="594f8-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="594f8-148">Und klicken Sie dann durch die Erweiterung der **"Servicestatus"** -Eigenschaft erhalten wir noch weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="594f8-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="594f8-149">Dienst Plan \*\*\*</span><span class="sxs-lookup"><span data-stu-id="594f8-149">****Service plan****</span></span>|<span data-ttu-id="594f8-150">****Beschreibung****</span><span class="sxs-lookup"><span data-stu-id="594f8-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="594f8-151">Sway</span><span class="sxs-lookup"><span data-stu-id="594f8-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="594f8-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="594f8-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="594f8-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="594f8-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="594f8-154">Azure-Rechteverwaltung (RMS)</span><span class="sxs-lookup"><span data-stu-id="594f8-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="594f8-155">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="594f8-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="594f8-156">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="594f8-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="594f8-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="594f8-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="594f8-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="594f8-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="594f8-159">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="594f8-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="594f8-p108">Sie sagen, dass das ist zu viel Schreibarbeit? Nun, wenn Ihnen ein wenig Windows PowerShell-abstrusität nichts ausmacht, können Sie Ausführen dieses verkürzte Version des Befehls stattdessen: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="594f8-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="594f8-p109">Für den Fall, dass Sie wissen möchten, wir können "Erweitern" die **Lizenzen** -Eigenschaft, da **Lizenzen** eine mehrwertige Eigenschaft ist: Es wird eine einzelne Eigenschaft, die mehrere Werte gespeichert werden kann. Wenn wir einen Eigenschaftswert erweitert, dem wir einfach ein Drilldown erhalten Sie und diese zusätzlichen Werte, die standardmäßig nicht angezeigt werden auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="594f8-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="594f8-p110">Wie sollen Sie wissen, dass ein Wert eine mehrwertige Eigenschaft ist? Nun, um das herauszufinden, führen Sie einen Befehl wie den folgenden: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> das **Get-Member** -Cmdlet gibt Informationen zu dem Objekt selbst; In diesem Fall Werte Informationen über die Eigenschaft, die ein Benutzerkonto-Objekt bilden. Hier ist was **Get-Member** hat, über die **Lizenzen** -Eigenschaft sagen: > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> Wenn die Eigenschaftendefinition zu Sammlungen etwas angezeigt wird (in diesem Fall `System.Collections.Generic.List`) dann wissen Sie eine mehrwertige Eigenschaft zuständig sind.</span><span class="sxs-lookup"><span data-stu-id="594f8-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="594f8-p111">Was bedeutet alle bedeutet dies? Werfen wir zunächst noch einen Blick auf die Informationen, die vom Cmdlet **Get-MsolUser** zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="594f8-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

<span data-ttu-id="594f8-169">Und betrachten wir auch einen Blick auf die Tabelle, die erklärt, was diese seltsam benannten Dienstpläne wirklich darstellen:</span><span class="sxs-lookup"><span data-stu-id="594f8-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="594f8-170">Dienst Plan \*\*\*</span><span class="sxs-lookup"><span data-stu-id="594f8-170">****Service plan****</span></span>|<span data-ttu-id="594f8-171">****Beschreibung****</span><span class="sxs-lookup"><span data-stu-id="594f8-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="594f8-172">Sway</span><span class="sxs-lookup"><span data-stu-id="594f8-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="594f8-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="594f8-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="594f8-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="594f8-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="594f8-175">Azure-Rechteverwaltung (RMS)</span><span class="sxs-lookup"><span data-stu-id="594f8-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="594f8-176">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="594f8-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="594f8-177">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="594f8-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="594f8-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="594f8-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="594f8-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="594f8-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="594f8-180">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="594f8-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="594f8-p112">Alles klar?  `MCOSTANDARD` ist nur ein interner programming Name für Skype für Online Business während `OFFICESUSBCRIPTION` ist nur der interne programming Name für Office Professional Plus. Es ist nicht das am besten geeignete, was in der ganzen Welt, aber, solange Sie in dieser Tabelle übersichtlich bleiben Sie müssen nicht viele Probleme bei der Arbeit mit Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="594f8-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="594f8-p113">Aber warten: mehr. Wie in den Artikel [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), wenn die **ProvisioningStatus** festgelegt ist, `Success` Dies bedeutet, dass der Dienst vollständig aktiviert wurde. beispielsweise wenn `MCOSTANDARD` auf festgelegt ist `Success` Dies bedeutet, dass der Benutzer Skype für Business Online zugreifen kann. Wenn die **ProvisioningStatus** festgelegt ist, `PendingInput` Dies bedeutet, dass Office 365 die Dienstanfrage; noch verarbeitet wird der Benutzer kann jedoch in der Regel anmelden und auf den Dienst zugreifen, während die Verarbeitung die Anforderung abgeschlossen hat. ( `YAMMER_ENTERPRISE` wird immer angezeigt als `PendingInput`, aber das ist OK:, die einen Benutzer anmeldet Yammer stoppt nicht).</span><span class="sxs-lookup"><span data-stu-id="594f8-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="594f8-188">Benutzer können installieren und aktivieren eine Neuinstallation für Office Professional Plus beim `OFFICESUBSCRIPTION` befindet sich in der `PendingInput` Zustand.</span><span class="sxs-lookup"><span data-stu-id="594f8-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="594f8-189">Und natürlich ist ein Dienst ist festgelegt `Disabled` bedeutet, dass der betreffende Dienst nicht für den Benutzer verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="594f8-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="594f8-190">Suchen Sie nach Benutzern, die Zugriff auf bestimmte Dienste von Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="594f8-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="594f8-p114">In einem separaten Artikel beschrieben haben wir gesehen, wie Sie Office 365 PowerShell verwenden können, um Benutzerzugriff auf Dienste zu deaktivieren. (Wenn Sie diese Artikel verpasst haben, finden Sie unter [Deaktivieren des Zugriffs auf Services mit Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Führt zu einer offensichtlichen Frage: Gibt es eine Möglichkeit zum bestimmen, welche *Benutzer* (d. h., mehrere Benutzer) welche Dienste aktiviert oder deaktiviert haben?</span><span class="sxs-lookup"><span data-stu-id="594f8-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="594f8-p115">Es wurden möchte, dass eine Person, die stellen würde. Um diese Frage zu beantworten, sehen wir uns die Tabelle der Dienste, die wir zunächst auf den Artikel [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) für unsere einzige verfügbare Lizenzierungsplan betrachtet `litwareinc:ENTERPRISEPACK`:</span><span class="sxs-lookup"><span data-stu-id="594f8-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="594f8-196">Dienst Plan \*\*\*</span><span class="sxs-lookup"><span data-stu-id="594f8-196">****Service plan****</span></span>|<span data-ttu-id="594f8-197">****Beschreibung****</span><span class="sxs-lookup"><span data-stu-id="594f8-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="594f8-198">Sway</span><span class="sxs-lookup"><span data-stu-id="594f8-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="594f8-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="594f8-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="594f8-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="594f8-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="594f8-201">Azure-Rechteverwaltung (RMS)</span><span class="sxs-lookup"><span data-stu-id="594f8-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="594f8-202">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="594f8-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="594f8-203">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="594f8-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="594f8-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="594f8-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="594f8-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="594f8-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="594f8-206">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="594f8-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="594f8-p116">Sie erinnern sich möglicherweise, ist die Dienstplan nichts anderes als das interne programming Name für ein Produkt. beispielsweise `OFFICESUBSCRIPTION`, um den ersten Namen, ist der interne programming Name für Office Professional Plus. Wenn `OFFICESUBSCRIPTION` wird als `SUCCESS` auf Dienstplan eines Benutzers, klicken Sie dann das bedeutet, dass der Benutzer berechtigt ist, auf Office Professional Plus zugreifen. Wenn `EXCHANGE_S_ENTERPRISE` aufgeführt ist, als `DISABLED` bedeutet, dass der Benutzer kann nicht Exchange Online verwenden.</span><span class="sxs-lookup"><span data-stu-id="594f8-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="594f8-210">Benutzer können installieren und aktivieren eine Neuinstallation für Office Professional Plus beim `OFFICESUBSCRIPTION` befindet sich in der `PendingInput` Zustand.</span><span class="sxs-lookup"><span data-stu-id="594f8-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="594f8-p117">Jetzt ist die Zeit, in die Reihenfolge, in der die Dienste angezeigt werden, sehr wichtig ist. Windows PowerShell jeder Eintrag in der Liste eine Indexnummer zugewiesen. Der erste Eintrag 0 ist, der nächste Eintrag ist 1 usw.. Die Ergebnisse werden in der folgenden Tabelle beschrieben:</span><span class="sxs-lookup"><span data-stu-id="594f8-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="594f8-215">Indexnummer \*\*\*</span><span class="sxs-lookup"><span data-stu-id="594f8-215">****Index number****</span></span>|<span data-ttu-id="594f8-216">Dienst Plan \*\*\*</span><span class="sxs-lookup"><span data-stu-id="594f8-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="594f8-217">0</span><span class="sxs-lookup"><span data-stu-id="594f8-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="594f8-218">1</span><span class="sxs-lookup"><span data-stu-id="594f8-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="594f8-219">2</span><span class="sxs-lookup"><span data-stu-id="594f8-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="594f8-220">3</span><span class="sxs-lookup"><span data-stu-id="594f8-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="594f8-221">4</span><span class="sxs-lookup"><span data-stu-id="594f8-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="594f8-222">5</span><span class="sxs-lookup"><span data-stu-id="594f8-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="594f8-223">6</span><span class="sxs-lookup"><span data-stu-id="594f8-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="594f8-224">7</span><span class="sxs-lookup"><span data-stu-id="594f8-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="594f8-225">8</span><span class="sxs-lookup"><span data-stu-id="594f8-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="594f8-226">Wie Sie sehen können, `SWAY` der erste Dienst aufgelistet ist, damit es die Indexnummer 0 zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="594f8-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="594f8-p118">Warum 0 und nicht 1? Das ist etwas Programmierung. In Programmiersprachen sagen Indizes Sie wie weit ein Element "vom Anfang des Arrays versetzt ist". Das erste Element *ist* der Anfang des Arrays, damit der Offset gleich 0 ist. Das zweite Element ist 1 Element vom Anfang des Arrays, damit der Offset gleich 1 ist.</span><span class="sxs-lookup"><span data-stu-id="594f8-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="594f8-p119">Versuchen Sie ein Beispiel für ein. Nehmen Sie an, dass wir eine Liste aller lizenzierten Benutzer verwenden möchten, die nicht für Exchange Online aktiviert wurden. Dazu können wir den folgenden Befehl verwenden:</span><span class="sxs-lookup"><span data-stu-id="594f8-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="594f8-p120">Zugegebenermaßen ist, die ein unverständliche professionell gestalteten wenig Befehl, wir kurz erklären, wie es funktioniert. Dies ist tatsächlich eine zweiteiligen-Befehl, und der erste Teil ist ganz einfach: wir das Cmdlet **Get-MsolUser** verwenden, um eine Auflistung aller Office 365-Benutzer zurückzugeben (lizenzierte und nicht lizenzierten):</span><span class="sxs-lookup"><span data-stu-id="594f8-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="594f8-p121">Diese Informationen wird dann an das Cmdlet **Where-Object** geleitet. **Where-Object** wird über die Benutzerkonten und sieht für diese Konten, die beide der folgenden Kriterien erfüllen:</span><span class="sxs-lookup"><span data-stu-id="594f8-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="594f8-p122">Die Eigenschaft **"islicensed"** ist gleich ( `-eq`) `True` ( `$true`). Ermöglicht, die uns zu extrahieren, die nicht lizenzierten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="594f8-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="594f8-p123">Der Wert der **Lizenzen [0]. "Servicestatus" [8]. ProvisioningStatus** -Eigenschaft ist gleich ( `-eq`) `Disabled`. Der wichtige Teil dieser unhandlich Eigenschaftsname ist unsere sofortige Zwecke dies:</span><span class="sxs-lookup"><span data-stu-id="594f8-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="594f8-p124">Die `[8]` stellt die Indexnummer für Exchange Online. (Kaum zu glauben, die aus der Tabelle ein paar Minuten vor betrachten). Was passiert, wenn wir wollten, erhalten alle Benutzer, die für die Skype für Business Online aktiviert? Die Indexnummer für Skype für Business Online ist sicherlich 5, sodass wir diese Syntax verwenden:</span><span class="sxs-lookup"><span data-stu-id="594f8-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="594f8-247">Usw., usw.</span><span class="sxs-lookup"><span data-stu-id="594f8-247">Etc., etc.</span></span>
    
    <span data-ttu-id="594f8-p125">Übrigen `Licenses[0]` gibt an, den Lizenzierungsplan, die wir anzeigen möchten. Da unsere Testdomäne nur eine Lizenzierungsplan hat spielt dies viel keine Rolle. Aber nehmen an, dass wir hatten einen Benutzer, der Lizenzen aus zwei unterschiedlichen lizenzierungspläne zugewiesen wurde. In diesem Fall `Licenses[0]` würde den ersten Lizenzierungsplan darstellen und `Licenses[1]` würde den zweiten Lizenzierungsplan darstellen.</span><span class="sxs-lookup"><span data-stu-id="594f8-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="594f8-252">Verwenden Sie den folgenden Befehl, um die Lizenzen, die einem Benutzer zugewiesen sind, und die Reihenfolge zu suchen, in der sie aufgelistet sind:</span><span class="sxs-lookup"><span data-stu-id="594f8-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="594f8-p126">Sehen Sie, wie das alles funktioniert? Die Indexnummer für Office Professional Plus ist 4. aus diesem Grund gibt dieser Befehl eine Liste von allen Benutzern, die nicht für Office Professional Plus aktiviert wurden:</span><span class="sxs-lookup"><span data-stu-id="594f8-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="594f8-p127">Und was passiert, wenn wir wollten eine Liste der Benutzer, die für Office Professional Plus *aktiviert* wurden? Nun, wenn Sie aktiviert haben und klicken Sie dann Ihre **ServiceStatus** entweder werden `PendingInput` oder `Success`; Anders ausgedrückt, wird der **"Servicestatus"** *nicht* gleich ( `-ne`) `Disabled`. Die bedeutet, dass sich alle wir nutzen unsere vorherigen Befehl, und Ersetzen Sie die `-eq` Operator für die `-ne` Operator:</span><span class="sxs-lookup"><span data-stu-id="594f8-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="594f8-p128">Als die Meldung Fehler auftreten, dass Code wahrscheinlich viele schöne Wettbewerben gewinnen wird nicht. Und Wahrheit gesagt, der Code kann noch mehr abrufen komplizierte. Angenommen Sie, dass wir möchten für Benutzer zu suchen, die für beide Skype für Business Online und Exchange Online aktiviert wurden:</span><span class="sxs-lookup"><span data-stu-id="594f8-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="594f8-p129">Aber keine Sorge zu viel zu wie komplizierter, die aussehen könnte: wichtig ist, dass mit relativ wenig Aufwand Sie diese Informationen abrufen können. Erhalten kann nicht an die gleichen Informationen mithilfe von Office 365 Administrationscenter? Ja, aber, im theoretisch praktisch, No. Um die gleichen Informationen mithilfe von Office 365 Administrationscenter zu erhalten müssten Sie sehen Sie sich die Lizenzierungsinformationen für jeden Benutzer, die jeweils einen Benutzer, und klicken Sie dann manuell nachzuverfolgen, die für *X* aktiviert wurde, und wer hadn't. Funktionieren würde, aber seien wir ehrlich: Wenn Sie mehr als 10 oder 11 Benutzer vorhanden sind, werden Sie nicht möchten, dazu. Es ist zu solchen mühsamen und zeitaufwendigen.</span><span class="sxs-lookup"><span data-stu-id="594f8-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="594f8-267">Die natürlich ist, warum wir Windows PowerShell haben: Windows PowerShell schützt Sie vor aus solchen mühsamen und zeitaufwendigen Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="594f8-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="594f8-268">Es folgt ein Beispiel eines Befehls zum Anzeigen von Dienstinformationen für eine angegebene Gruppe von Diensten durch ihre Lizenzen und ServiceStatus Indizes für ein Abonnement von Office 365 E5 bezeichnet:</span><span class="sxs-lookup"><span data-stu-id="594f8-268">Here's an example of a command for viewing service information for a specified set of services as identified by their Licenses and ServiceStatus indexes for an Office 365 E5 subscription:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

<span data-ttu-id="594f8-269">Dieser Befehl erstellt eine CSV-Datei, die alle Ihre Benutzer und deren Dienst-Status für einen angegebenen Satz von Diensten (Teams, Yammer, AD RMS, OfficePro, Skype, SharePoint und Exchange) anzeigt.</span><span class="sxs-lookup"><span data-stu-id="594f8-269">This command creates a CSV file showing all of your users and their service statuses for a specified set of services (Teams, Yammer, AD RMS, OfficePro, Skype, SharePoint, and Exchange).</span></span>

>[!Note]
><span data-ttu-id="594f8-p130">Sie können in einem Abonnement aus die Liste der Dienste Abrufen der `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` Befehl. In der Ausgabe starten Sie die Nummerierung der mit 0 indiziert. Mit dem vorstehende Befehl ist nur ein Beispiel. Indexnummern für Dienste können mit der Zeit ändern.</span><span class="sxs-lookup"><span data-stu-id="594f8-p130">You can get the list of services in a subscription from the `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` command. In the output, you start numbering the service indexes with 0. The preceding command is just an example. Index numbers for services can change over time.</span></span>
>

  
<span data-ttu-id="594f8-274"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="594f8-274"></span></span>
## <a name="see-also"></a><span data-ttu-id="594f8-275">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="594f8-275">See also</span></span>

<span data-ttu-id="594f8-276">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="594f8-276">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="594f8-277">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="594f8-277">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="594f8-278">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="594f8-278">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="594f8-279">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="594f8-279">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="594f8-280">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="594f8-280">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="594f8-281">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="594f8-281">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="594f8-282">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="594f8-282">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="594f8-283">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="594f8-283">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="594f8-284">Format-List</span><span class="sxs-lookup"><span data-stu-id="594f8-284">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="594f8-285">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="594f8-285">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="594f8-286">Select-Object</span><span class="sxs-lookup"><span data-stu-id="594f8-286">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="594f8-287">Where-Object</span><span class="sxs-lookup"><span data-stu-id="594f8-287">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="594f8-288">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="594f8-288">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]