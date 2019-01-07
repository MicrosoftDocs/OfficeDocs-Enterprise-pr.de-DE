---
title: Löschen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Informationen zur Verwendung von Office 365 PowerShell zum Löschen von Office 365-Benutzerkonten
ms.openlocfilehash: 0b882f3bdf9070c83baffaca65a7c80c98cd4ed9
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546466"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="ddebc-103">Löschen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddebc-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="ddebc-104">**Zusammenfassung:** Informationen zur Verwendung von Office 365 PowerShell zum Löschen von Office 365-Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ddebc-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="ddebc-105">Sie können Office 365 PowerShell verwenden, um ein Benutzerkonto zu löschen.</span><span class="sxs-lookup"><span data-stu-id="ddebc-105">You can use the Office 365 admin center to create a new user account.</span></span>

   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ddebc-106">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="ddebc-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ddebc-107">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ddebc-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="ddebc-108">Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="ddebc-108">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="ddebc-109">In diesem Beispiel wird das Benutzerkonto „fabricec@litwareinc.com“ entfernt.</span><span class="sxs-lookup"><span data-stu-id="ddebc-109">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="ddebc-110">Der Parameter **-ObjectID** im Cmdlet **Remove-AzureAD** akzeptiert entweder den Kontoanmeldenamen, der auch als Benutzerprinzipalname bezeichnet wird, oder die Objekt-ID des Kontos.</span><span class="sxs-lookup"><span data-stu-id="ddebc-110">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="ddebc-111">Um den Kontonamen basierend auf dem Namen des Benutzers anzuzeigen, verwenden Sie die folgenden Befehle:</span><span class="sxs-lookup"><span data-stu-id="ddebc-111">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ddebc-112">In diesem Beispiel wird der Kontoname für den Benutzer namens Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ddebc-112">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ddebc-113">Um einen Kontonamen basierend auf dem Anzeigenamen des Benutzers zu entfernen, verwenden Sie die folgenden Befehle:</span><span class="sxs-lookup"><span data-stu-id="ddebc-113">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ddebc-114">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddebc-114">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="ddebc-p101">Wenn Sie ein Benutzerkonto mit dem Microsoft Azure AD-Modul für Windows PowerShell löschen, wird das Konto nicht endgültig gelöscht. Sie können das gelöschte Benutzerkonto innerhalb von 30 Tagen wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="ddebc-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="ddebc-117">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ddebc-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="ddebc-118">Wenn Sie ein Benutzerkonto löschen möchten, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="ddebc-118">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="ddebc-119">In diesem Beispiel wird das Benutzerkonto „BelindaN@litwareinc.com“ gelöscht.</span><span class="sxs-lookup"><span data-stu-id="ddebc-119">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="ddebc-120">Wenn Sie ein gelöschtes Benutzerkonto innerhalb der Nachfrist von 30 Tagen wiederherstellen möchten, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="ddebc-120">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="ddebc-121">In diesem Beispiel wird das gelöschte Benutzerkonto „BelindaN@litwareinc.com“ wiederhergestellt.</span><span class="sxs-lookup"><span data-stu-id="ddebc-121">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="ddebc-122">**Hinweise:**</span><span class="sxs-lookup"><span data-stu-id="ddebc-122">**Notes:**</span></span>
  
- <span data-ttu-id="ddebc-123">Um die Liste der gelöschten Benutzer anzuzeigen, die wiederhergestellt werden können, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ddebc-123">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="ddebc-124">Wenn der ursprüngliche Benutzerprinzipalnamen des Benutzerkontos durch ein anderes Konto verwendet wird, verwenden Sie den _NewUserPrincipalName_-Parameter anstelle von _UserPrincipalName_, um einen anderen Benutzerprinzipalnamen anzugeben, wenn Sie das Benutzerkonto wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="ddebc-124">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="ddebc-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ddebc-125">See also</span></span>

[<span data-ttu-id="ddebc-126">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddebc-126">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ddebc-127">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddebc-127">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ddebc-128">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddebc-128">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

