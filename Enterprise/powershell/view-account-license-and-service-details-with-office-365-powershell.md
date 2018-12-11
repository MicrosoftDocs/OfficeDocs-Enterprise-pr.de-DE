---
title: Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
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
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213952"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="74507-103">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="74507-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="74507-104">**Zusammenfassung:** Erläutert, wie Office 365 PowerShell verwenden, um die Office 365-Dienste zu ermitteln, die Benutzern zugewiesen wurden.</span><span class="sxs-lookup"><span data-stu-id="74507-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="74507-p101">In Office 365 lizenziert Pläne Lizenzieren von (auch gewählte SKUs oder Office 365-Pläne) gewähren des Benutzerzugriffs auf Office 365-Dienste, die für diese Pläne definiert sind. Ein Benutzer möglicherweise jedoch nicht Zugriff auf alle Dienste, die in eine Lizenz verfügbar sind, die ihnen derzeit zugewiesen ist. Office 365 PowerShell können Sie den Status von Diensten auf Benutzerkonten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="74507-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="74507-108">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="74507-108">Before you begin</span></span>

- <span data-ttu-id="74507-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="74507-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="74507-111">Verwenden Sie die Befehle `Get-MsolAccountSku` und `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` , die folgende Informationen zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="74507-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="74507-112">Die Lizenzierungspläne, die in Ihrer Organisation verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="74507-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="74507-113">Die Dienste, die in den einzelnen Lizenzierungsplänen verfügbar sind, und die Reihenfolge, in der sie aufgelistet sind (die Indexnummer).</span><span class="sxs-lookup"><span data-stu-id="74507-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="74507-114">Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Dienste finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="74507-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="74507-115">Verwenden Sie den Befehl `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` , um die Lizenzen zu erhalten, die ein Benutzer und die Reihenfolge, in zugewiesen sind, sie darstellen (die Indexnummer) aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="74507-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="74507-116">Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="74507-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="74507-117">So zeigen Sie Dienste für ein Benutzerkonto an</span><span class="sxs-lookup"><span data-stu-id="74507-117">To view services for a user account</span></span>

<span data-ttu-id="74507-118">Um die Office 365-Dienste anzuzeigen, denen ein Benutzer zugreifen kann, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="74507-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="74507-p103">Dieses Beispiel zeigt die Dienste auf denen der Benutzer BelindaN@litwareinc.com zugreifen kann. Zeigt die Dienste, die alle Lizenzen zugeordnet sind, die ihr Konto zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="74507-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="74507-121">Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="74507-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="74507-122">Um alle Dienste für einen Benutzer anzuzeigen, die *mehrere Lizenzen*zugewiesen wurde, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="74507-122">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a><span data-ttu-id="74507-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="74507-123">See also</span></span>

<span data-ttu-id="74507-124">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="74507-124">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="74507-125">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="74507-125">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="74507-126">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="74507-126">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="74507-127">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="74507-127">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="74507-128">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="74507-128">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="74507-129">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="74507-129">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="74507-130">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="74507-130">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="74507-131">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="74507-131">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="74507-132">Format-List</span><span class="sxs-lookup"><span data-stu-id="74507-132">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="74507-133">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="74507-133">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="74507-134">Select-Object</span><span class="sxs-lookup"><span data-stu-id="74507-134">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="74507-135">Where-Object</span><span class="sxs-lookup"><span data-stu-id="74507-135">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="74507-136">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="74507-136">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]