---
title: Deaktivieren des Zugriffs auf Dienste während des Zuweisens von Benutzerlizenzen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: In diesem Artikel erfahren Sie, wie Sie Benutzerkonten Lizenzen zuweisen und gleichzeitig bestimmte Servicepläne mit Office 365 PowerShell deaktivieren.
ms.openlocfilehash: a00a1af02aeb69f7d69f9f9fc998202ac7c53291
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004668"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="7496d-103">Deaktivieren des Zugriffs auf Dienste während des Zuweisens von Benutzerlizenzen</span><span class="sxs-lookup"><span data-stu-id="7496d-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="7496d-p101">Im Lieferumfang von Office 365-Abonnements sind Servicepläne für einzelne Dienste enthalten. Office 365-Administratoren müssen häufig bestimmte Pläne deaktivieren, wenn Sie Benutzern Lizenzen zuweisen. Mit den Anweisungen in diesem Artikel können Sie eine Office 365-Lizenz zuweisen und gleichzeitig bestimmte Servicepläne mithilfe der PowerShell für ein bestimmtes Benutzerkonto oder mehrere Benutzerkonten deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="7496d-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="7496d-107">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="7496d-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="7496d-108">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="7496d-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="7496d-109">Als nächstes Listen Sie die Lizenz Pläne für Ihren Mandanten mit diesem Befehl auf.</span><span class="sxs-lookup"><span data-stu-id="7496d-109">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="7496d-110">Rufen Sie als nächstes den Anmeldenamen des Kontos ab, für das Sie eine Lizenz hinzufügen möchten, die auch als Benutzerprinzipalname (User Principal Name, UPN) bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="7496d-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="7496d-111">Kompilieren Sie als nächstes eine Liste der zu aktivierende Dienste.</span><span class="sxs-lookup"><span data-stu-id="7496d-111">Next, compile a list of services to enable.</span></span> <span data-ttu-id="7496d-112">Eine vollständige Liste von Lizenzplänen (auch bezeichnet als Produktnamen), deren enthaltenen Serviceplänen und die entsprechenden Anzeigenamen finden Sie unter [Produktnamen und Serviceplanbezeichner für die Lizenzierung](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="7496d-112">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="7496d-113">Geben Sie für den folgenden Befehlsblock den Benutzerprinzipalnamen des Benutzerkontos, die SKU-Teilnummer und die Liste der Dienstpläne ein, um den erläuternden Text sowie die \< und > Zeichen zu aktivieren und zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="7496d-113">For the command block below, fill in the user principal name of the user account, the SKU part number, and the list of service plans to enable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="7496d-114">Führen Sie anschließend die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.</span><span class="sxs-lookup"><span data-stu-id="7496d-114">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7496d-115">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7496d-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7496d-116">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="7496d-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="7496d-117">Führen Sie als nächstes den folgenden Befehl aus, um Ihre aktuellen Abonnements anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="7496d-117">Next, run this command to see your current subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="7496d-118">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="7496d-118">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="7496d-119">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="7496d-119">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="7496d-120">In dem vom  `Get-MsolAccountSku`-Befehl zurückgegebenen Ergebnis gilt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7496d-120">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="7496d-p105">**AccountSkuId** ist ein Abonnement für Ihre Organisation im Format: \<Organisationsname>:\<Abonnement>. \< OrganizationName> ist der Wert, den Sie bei der Registrierung bei Office 365 angegeben haben. Dieser ist für Ihre Organisation eindeutig. Der \<Subscription>-Wert gilt für ein bestimmtes Abonnement. Beispiel: Für litwareinc:ENTERPRISEPACK ist der litwareinc der Name der Organisation und ENTERPRISEPACK (Office 365 Enterprise E3) ist der Name des Abonnements.</span><span class="sxs-lookup"><span data-stu-id="7496d-p105">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="7496d-125">**ActiveUnits** ist die Anzahl der Lizenzen, die Sie für das Abonnement erworben haben.</span><span class="sxs-lookup"><span data-stu-id="7496d-125">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="7496d-126">**WarningUnits** gibt die Anzahl der Lizenzen in einem Abonnement an, die Sie nicht verlängert haben und die nach der 30-tägigen Toleranzperiode ablaufen werden.</span><span class="sxs-lookup"><span data-stu-id="7496d-126">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="7496d-127">**ConsumedUnits** ist die Anzahl der Lizenzen, die Sie Benutzern für das Abonnement zugeordnet haben.</span><span class="sxs-lookup"><span data-stu-id="7496d-127">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="7496d-p106">Beachten Sie das AccountSkuId-Objekt für Ihr Office 365-Abonnement, das die Benutzer enthält, die Sie lizenzieren möchten. Stellen Sie außerdem sicher, dass genügend Lizenzen zum Zuweisen verfügbar sind (subtrahieren Sie **ConsumedUnits** von **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="7496d-p106">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="7496d-130">Führen Sie dann diesen Befehl aus, um detaillierte Informationen zu den Office 365-Serviceplänen anzuzeigen, die in allen Ihren Abonnements zur Verfügung stehen:</span><span class="sxs-lookup"><span data-stu-id="7496d-130">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="7496d-131">Anhand der vom Befehl zurückgegebenen Ausgabe können Sie bestimmen, welche Servicepläne Sie beim Zuweisen von Lizenzen an Benutzer deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="7496d-131">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="7496d-132">Hier ist eine unvollständige Liste der Servicepläne und der entsprechenden Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="7496d-132">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="7496d-p107">In der folgenden Tabelle sind die Office 365-Servicepläne und Anzeigenamen der beliebtesten Dienste aufgeführt. Ihre individuelle Serviceplanliste sieht möglicherweise anders aus.</span><span class="sxs-lookup"><span data-stu-id="7496d-p107">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="7496d-135">**Dienstplan**</span><span class="sxs-lookup"><span data-stu-id="7496d-135">**Service plan**</span></span>|<span data-ttu-id="7496d-136">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="7496d-136">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="7496d-137">Sway</span><span class="sxs-lookup"><span data-stu-id="7496d-137">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="7496d-138">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7496d-138">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="7496d-139">Yammer</span><span class="sxs-lookup"><span data-stu-id="7496d-139">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="7496d-140">Azure-Rechteverwaltung (Rights Management, RMS)</span><span class="sxs-lookup"><span data-stu-id="7496d-140">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="7496d-141">Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="7496d-141">Office 365 ProPlus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="7496d-142">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="7496d-142">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="7496d-143">Office</span><span class="sxs-lookup"><span data-stu-id="7496d-143">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="7496d-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7496d-144">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="7496d-145">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="7496d-145">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="7496d-146">Eine vollständige Liste von Lizenzplänen (auch bezeichnet als Produktnamen), deren enthaltenen Serviceplänen und die entsprechenden Anzeigenamen finden Sie unter [Produktnamen und Serviceplanbezeichner für die Lizenzierung](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="7496d-146">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="7496d-147">Nachdem Sie festgelegt haben, dass AccountSkuId und die Servicepläne deaktiviert werden sollen, können Sie einem einzelnen oder mehreren Benutzern Lizenzen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="7496d-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="7496d-148">Für einen einzelnen Benutzer</span><span class="sxs-lookup"><span data-stu-id="7496d-148">For a single user</span></span>

<span data-ttu-id="7496d-p108">Geben Sie für einen einzelnen Benutzer den Benutzerprinzipalnamen des Bneutzerkontos, die AccountSkuId und die Liste der zu deaktivierenden Servicepläne ein, und entfernen Sie den erläuternden Text sowie die Zeichen „\<" und „>". Führen Sie anschließend die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.</span><span class="sxs-lookup"><span data-stu-id="7496d-p108">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

<span data-ttu-id="7496d-151">Hier ein Beispiel für einen Befehlsblock für das Konto namens „belindan@contoso.com“, für contoso:ENTERPRISEPACK-Lizenz, und die zu deaktivierenden Servicepläne lauten: RMS_S_ENTERPRISE, SCHLINGERN, INTUNE_O365 und YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="7496d-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a><span data-ttu-id="7496d-152">Für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="7496d-152">For multiple users</span></span>

<span data-ttu-id="7496d-p109">Erstellen Sie zum Ausführen dieser Aufgabe eine CSV-Textdatei mit den UserPrincipalName- und UsageLocation-Feldern. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7496d-p109">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="7496d-155">Geben Sie als Nächstes den Speicherort für die CSV-Eingabe- und CSV-Ausgabedateien, die Konto-SKU-ID und die Liste der zu deaktivierenden Servicepläne ein, und führen Sie anschließend die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.</span><span class="sxs-lookup"><span data-stu-id="7496d-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="7496d-156">Dieser PowerShell-Befehlsblock:</span><span class="sxs-lookup"><span data-stu-id="7496d-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="7496d-157">Zeigt den Benutzerprinzipalnamen für jeden Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="7496d-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="7496d-158">Weist jedem Benutzer die angepassten Lizenzen zu.</span><span class="sxs-lookup"><span data-stu-id="7496d-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="7496d-159">Erstellt eine CSV-Datei mit allen Benutzern, die verarbeitet wurden, und zeigt den Status ihrer Lizenz an.</span><span class="sxs-lookup"><span data-stu-id="7496d-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="7496d-160">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7496d-160">See also</span></span>

[<span data-ttu-id="7496d-161">Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7496d-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="7496d-162">Deaktivieren des Zugriffs auf Sway mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7496d-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="7496d-163">Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7496d-163">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="7496d-164">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7496d-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
