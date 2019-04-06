---
title: Deaktivieren des Zugriffs auf Dienste während des Zuweisens von Benutzerlizenzen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: In diesem Artikel erfahren Sie, wie Sie Benutzerkonten Lizenzen zuweisen und gleichzeitig bestimmte Servicepläne mit Office 365 PowerShell deaktivieren.
ms.openlocfilehash: c93f54fcd5716a0ea53290c24a2594b8bc63cecf
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001848"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="89c60-103">Deaktivieren des Zugriffs auf Dienste während des Zuweisens von Benutzerlizenzen</span><span class="sxs-lookup"><span data-stu-id="89c60-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="89c60-104">**Zusammenfassung:** In diesem Artikel erfahren Sie, wie Sie Benutzerkonten Lizenzen zuweisen und gleichzeitig bestimmte Servicepläne mit Office 365 PowerShell deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="89c60-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="89c60-p101">Im Lieferumfang von Office 365-Abonnements sind Servicepläne für einzelne Dienste enthalten. Office 365-Administratoren müssen häufig bestimmte Pläne deaktivieren, wenn Sie Benutzern Lizenzen zuweisen. Mit den Anweisungen in diesem Artikel können Sie eine Office 365-Lizenz zuweisen und gleichzeitig bestimmte Servicepläne mithilfe der PowerShell für ein bestimmtes Benutzerkonto oder mehrere Benutzerkonten deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="89c60-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>


## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="89c60-108">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="89c60-108">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="89c60-109">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="89c60-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="89c60-110">Führen Sie als nächstes den folgenden Befehl aus, um Ihre aktuellen Abonnements anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="89c60-110">Next, run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="89c60-111">In dem vom  `Get-MsolAccountSku`-Befehl zurückgegebenen Ergebnis gilt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="89c60-111">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="89c60-p102">**AccountSkuId** ist ein Abonnement für Ihre Organisation im Format: \<Organisationsname>:\<Abonnement>. \< OrganizationName> ist der Wert, den Sie bei der Registrierung bei Office 365 angegeben haben. Dieser ist für Ihre Organisation eindeutig. Der \<Subscription>-Wert gilt für ein bestimmtes Abonnement. Beispiel: Für litwareinc:ENTERPRISEPACK ist der litwareinc der Name der Organisation und ENTERPRISEPACK (Office 365 Enterprise E3) ist der Name des Abonnements.</span><span class="sxs-lookup"><span data-stu-id="89c60-p102">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="89c60-116">**ActiveUnits** ist die Anzahl der Lizenzen, die Sie für das Abonnement erworben haben.</span><span class="sxs-lookup"><span data-stu-id="89c60-116">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="89c60-117">**WarningUnits** gibt die Anzahl der Lizenzen in einem Abonnement an, die Sie nicht verlängert haben und die nach der 30-tägigen Toleranzperiode ablaufen werden.</span><span class="sxs-lookup"><span data-stu-id="89c60-117">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="89c60-118">**ConsumedUnits** ist die Anzahl der Lizenzen, die Sie Benutzern für das Abonnement zugeordnet haben.</span><span class="sxs-lookup"><span data-stu-id="89c60-118">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="89c60-p103">Beachten Sie das AccountSkuId-Objekt für Ihr Office 365-Abonnement, das die Benutzer enthält, die Sie lizenzieren möchten. Stellen Sie außerdem sicher, dass genügend Lizenzen zum Zuweisen verfügbar sind (subtrahieren Sie **ConsumedUnits** von **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="89c60-p103">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="89c60-121">Führen Sie dann diesen Befehl aus, um detaillierte Informationen zu den Office 365-Serviceplänen anzuzeigen, die in allen Ihren Abonnements zur Verfügung stehen:</span><span class="sxs-lookup"><span data-stu-id="89c60-121">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="89c60-122">Anhand der vom Befehl zurückgegebenen Ausgabe können Sie bestimmen, welche Servicepläne Sie beim Zuweisen von Lizenzen an Benutzer deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="89c60-122">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="89c60-123">Hier ist eine unvollständige Liste der Servicepläne und der entsprechenden Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="89c60-123">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="89c60-p104">In der folgenden Tabelle sind die Office 365-Servicepläne und Anzeigenamen der beliebtesten Dienste aufgeführt. Ihre individuelle Serviceplanliste sieht möglicherweise anders aus.</span><span class="sxs-lookup"><span data-stu-id="89c60-p104">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="89c60-126">**Dienstplan**</span><span class="sxs-lookup"><span data-stu-id="89c60-126">**Service plan**</span></span>|<span data-ttu-id="89c60-127">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="89c60-127">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="89c60-128">Sway</span><span class="sxs-lookup"><span data-stu-id="89c60-128">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="89c60-129">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="89c60-129">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="89c60-130">Yammer</span><span class="sxs-lookup"><span data-stu-id="89c60-130">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="89c60-131">Azure-Rechteverwaltung (Rights Management, RMS)</span><span class="sxs-lookup"><span data-stu-id="89c60-131">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="89c60-132">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="89c60-132">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="89c60-133">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="89c60-133">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="89c60-134">Office Online</span><span class="sxs-lookup"><span data-stu-id="89c60-134">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="89c60-135">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="89c60-135">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="89c60-136">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="89c60-136">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="89c60-137">Eine vollständige Liste von Lizenzplänen (auch bezeichnet als Produktnamen), deren enthaltenen Serviceplänen und die entsprechenden Anzeigenamen finden Sie unter [Produktnamen und Serviceplanbezeichner für die Lizenzierung](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="89c60-137">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="89c60-138">Nachdem Sie festgelegt haben, dass AccountSkuId und die Servicepläne deaktiviert werden sollen, können Sie einem einzelnen oder mehreren Benutzern Lizenzen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="89c60-138">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="89c60-139">Für einen einzelnen Benutzer</span><span class="sxs-lookup"><span data-stu-id="89c60-139">For a single user</span></span>

<span data-ttu-id="89c60-p105">Geben Sie für einen einzelnen Benutzer den Benutzerprinzipalnamen des Bneutzerkontos, die AccountSkuId und die Liste der zu deaktivierenden Servicepläne ein, und entfernen Sie den erläuternden Text sowie die Zeichen „\<" und „>". Führen Sie anschließend die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.</span><span class="sxs-lookup"><span data-stu-id="89c60-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="89c60-142">Hier ein Beispiel für einen Befehlsblock für das Konto namens „belindan@contoso.com“, für contoso:ENTERPRISEPACK-Lizenz, und die zu deaktivierenden Servicepläne lauten: RMS_S_ENTERPRISE, SCHLINGERN, INTUNE_O365 und YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="89c60-142">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

### <a name="for-multiple-users"></a><span data-ttu-id="89c60-143">Für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="89c60-143">For multiple users</span></span>

<span data-ttu-id="89c60-p106">Erstellen Sie zum Ausführen dieser Aufgabe eine CSV-Textdatei mit den UserPrincipalName- und UsageLocation-Feldern. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="89c60-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="89c60-146">Geben Sie als Nächstes den Speicherort für die CSV-Eingabe- und CSV-Ausgabedateien, die Konto-SKU-ID und die Liste der zu deaktivierenden Servicepläne ein, und führen Sie anschließend die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.</span><span class="sxs-lookup"><span data-stu-id="89c60-146">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
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
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="89c60-147">Dieser PowerShell-Befehlsblock:</span><span class="sxs-lookup"><span data-stu-id="89c60-147">This PowerShell command block:</span></span>
  
- <span data-ttu-id="89c60-148">Zeigt den Benutzerprinzipalnamen für jeden Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="89c60-148">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="89c60-149">Weist jedem Benutzer die angepassten Lizenzen zu.</span><span class="sxs-lookup"><span data-stu-id="89c60-149">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="89c60-150">Erstellt eine CSV-Datei mit allen Benutzern, die verarbeitet wurden, und zeigt den Status ihrer Lizenz an.</span><span class="sxs-lookup"><span data-stu-id="89c60-150">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="89c60-151">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="89c60-151">See also</span></span>

[<span data-ttu-id="89c60-152">Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89c60-152">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="89c60-153">Deaktivieren des Zugriffs auf Sway mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89c60-153">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="89c60-154">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89c60-154">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="89c60-155">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89c60-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

