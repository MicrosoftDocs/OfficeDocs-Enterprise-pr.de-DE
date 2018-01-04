---
title: "Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Informationen zur Verwendung von Office 365 PowerShell zum Löschen und Wiederherstellen von Office 365-Benutzerkonten"
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a><span data-ttu-id="0afe0-103">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0afe0-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="0afe0-104">**Zusammenfassung:** Informationen zur Verwendung von Office 365 PowerShell zum Löschen und Wiederherstellen von Office 365-Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="0afe0-104">Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts</span></span>
  
<span data-ttu-id="0afe0-p101">Wenn Sie Office 365 PowerShell zum Löschen eines Benutzerkontos verwenden, wird das Konto nicht endgültig gelöscht. Sie können das gelöschte Benutzerkonto innerhalb von 30 Tagen wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="0afe0-p101">When you use Office 365 PowerShell to delete a user account, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="0afe0-107">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="0afe0-107">Before you begin</span></span>

- <span data-ttu-id="0afe0-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="0afe0-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="0afe0-110">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="0afe0-110">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="0afe0-111">Sie können den Zugriff auf einzelne Benutzerkonten mit Office 365 PowerShell blockieren.</span><span class="sxs-lookup"><span data-stu-id="0afe0-111">Use Office 365 PowerShell to block access to individual user accounts</span></span>
<span data-ttu-id="0afe0-112"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="0afe0-112"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="0afe0-113">Wenn Sie ein Benutzerkonto löschen möchten, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="0afe0-113">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="0afe0-114">In diesem Beispiel wird das Benutzerkonto „BelindaN@litwareinc.com“ gelöscht.</span><span class="sxs-lookup"><span data-stu-id="0afe0-114">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="0afe0-115">Wenn Sie ein gelöschtes Benutzerkonto innerhalb der Nachfrist von 30 Tagen wiederherstellen möchten, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="0afe0-115">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="0afe0-116">In diesem Beispiel wird das gelöschte Benutzerkonto „BelindaN@litwareinc.com“ wiederhergestellt.</span><span class="sxs-lookup"><span data-stu-id="0afe0-116">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="0afe0-117">**Hinweise:**</span><span class="sxs-lookup"><span data-stu-id="0afe0-117">**Notes:**</span></span>
  
- <span data-ttu-id="0afe0-118">Um die Liste der gelöschten Benutzer anzuzeigen, die wiederhergestellt werden können, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="0afe0-118">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="0afe0-119">Wenn der ursprüngliche Benutzerprinzipalnamen des Benutzerkontos durch ein anderes Konto verwendet wird, verwenden Sie den  _NewUserPrincipalName_-Parameter anstelle von  _UserPrincipalName_, um einen anderen Benutzerprinzipalnamen anzugeben, wenn Sie das Benutzerkonto wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="0afe0-119">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a><span data-ttu-id="0afe0-120">Entfernen eines Benutzerkontos mit dem Azure Active Directory V2 PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="0afe0-120">Use the Azure Active Directory V2 PowerShell module to remove a user account</span></span>
<span data-ttu-id="0afe0-121"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="0afe0-121"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="0afe0-p103">Um das Cmdlet **Remove-AzureADUser** aus dem Azure Active Directory V2 PowerShell-Modul zu verwenden, müssen Sie zunächst eine Verbindung zu Ihrem Abonnement herstellen. Die Anweisungen finden Sie unter[Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="0afe0-p103">To use the **Remove-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="0afe0-124">Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="0afe0-124">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <Account>
```

<span data-ttu-id="0afe0-125">In diesem Beispiel wird das Benutzerkonto „fabricec@litwareinc.com“ entfernt.</span><span class="sxs-lookup"><span data-stu-id="0afe0-125">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="0afe0-126">Der Parameter **-ObjectID** im Cmdlet **Remove-AzureAD** akzeptiert entweder den Kontonamen, der auch als Benutzerprinzipalname bezeichnet wird, oder die Objekt-ID des Kontos.</span><span class="sxs-lookup"><span data-stu-id="0afe0-126">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="0afe0-127">Um den Kontonamen basierend auf dem Namen des Benutzers anzuzeigen, verwenden Sie die folgenden Befehle:</span><span class="sxs-lookup"><span data-stu-id="0afe0-127">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="0afe0-128">In diesem Beispiel wird der Kontoname für den Benutzer namens Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0afe0-128">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="0afe0-129">Um einen Kontonamen basierend auf dem Namen des Benutzers zu entfernen, verwenden Sie die folgenden Befehle:</span><span class="sxs-lookup"><span data-stu-id="0afe0-129">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a><span data-ttu-id="0afe0-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0afe0-130">See also</span></span>
<span data-ttu-id="0afe0-131"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="0afe0-131"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="0afe0-132">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0afe0-132">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="0afe0-133">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0afe0-133">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0afe0-134">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0afe0-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0afe0-135">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0afe0-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0afe0-136">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0afe0-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="0afe0-137">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="0afe0-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="0afe0-138">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="0afe0-138">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="0afe0-139">Remove-MsolUser</span><span class="sxs-lookup"><span data-stu-id="0afe0-139">Remove-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [<span data-ttu-id="0afe0-140">Restore-MsolUser</span><span class="sxs-lookup"><span data-stu-id="0afe0-140">Restore-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [<span data-ttu-id="0afe0-141">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="0afe0-141">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

