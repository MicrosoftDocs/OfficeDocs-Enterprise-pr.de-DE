---
title: Löschen von Microsoft 365-Benutzerkonten mit PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Informationen zur Verwendung von PowerShell für Microsoft 365 zum Löschen von Benutzerkonten.
ms.openlocfilehash: 62d9dee2e6b0d2054116e5e5f005b5928112186d
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230711"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="5b780-103">Löschen von Microsoft 365-Benutzerkonten mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b780-103">Delete Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="5b780-104">Sie können PowerShell für Microsoft 365 verwenden, um ein Benutzerkonto zu löschen.</span><span class="sxs-lookup"><span data-stu-id="5b780-104">You can use PowerShell for Microsoft 365 to delete a user account.</span></span>
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5b780-105">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="5b780-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5b780-106">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="5b780-106">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="5b780-107">Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="5b780-107">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="5b780-108">In diesem Beispiel wird das Benutzerkonto „fabricec@litwareinc.com“ entfernt.</span><span class="sxs-lookup"><span data-stu-id="5b780-108">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="5b780-109">Der Parameter **-objectID** im Cmdlet **Remove-AzureADUser** akzeptiert entweder den Anmeldenamen des Kontos, der auch als Benutzerprinzipalname bezeichnet wird, oder die Objekt-ID des Kontos.</span><span class="sxs-lookup"><span data-stu-id="5b780-109">The **-ObjectID** parameter in the **Remove-AzureADUser** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="5b780-110">Um den Kontonamen basierend auf dem Namen des Benutzers anzuzeigen, verwenden Sie die folgenden Befehle:</span><span class="sxs-lookup"><span data-stu-id="5b780-110">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5b780-111">In diesem Beispiel wird der Kontoname für den Benutzer namens Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5b780-111">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5b780-112">Um einen Kontonamen basierend auf dem Anzeigenamen des Benutzers zu entfernen, verwenden Sie die folgenden Befehle:</span><span class="sxs-lookup"><span data-stu-id="5b780-112">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5b780-113">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b780-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5b780-p101">Wenn Sie ein Benutzerkonto mit dem Microsoft Azure AD-Modul für Windows PowerShell löschen, wird das Konto nicht endgültig gelöscht. Sie können das gelöschte Benutzerkonto innerhalb von 30 Tagen wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="5b780-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="5b780-116">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5b780-116">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="5b780-117">Wenn Sie ein Benutzerkonto löschen möchten, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="5b780-117">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
><span data-ttu-id="5b780-118">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="5b780-118">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="5b780-119">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="5b780-119">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="5b780-120">In diesem Beispiel wird das Benutzerkonto „BelindaN@litwareinc.com“ gelöscht.</span><span class="sxs-lookup"><span data-stu-id="5b780-120">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="5b780-121">Wenn Sie ein gelöschtes Benutzerkonto innerhalb der Nachfrist von 30 Tagen wiederherstellen möchten, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="5b780-121">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="5b780-122">In diesem Beispiel wird das gelöschte Benutzerkonto „BelindaN@litwareinc.com“ wiederhergestellt.</span><span class="sxs-lookup"><span data-stu-id="5b780-122">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="5b780-123">**Hinweise:**</span><span class="sxs-lookup"><span data-stu-id="5b780-123">**Notes:**</span></span>
  
- <span data-ttu-id="5b780-124">Um die Liste der gelöschten Benutzer anzuzeigen, die wiederhergestellt werden können, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="5b780-124">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="5b780-125">Wenn der ursprüngliche Benutzerprinzipalnamen des Benutzerkontos durch ein anderes Konto verwendet wird, verwenden Sie den _NewUserPrincipalName_-Parameter anstelle von _UserPrincipalName_, um einen anderen Benutzerprinzipalnamen anzugeben, wenn Sie das Benutzerkonto wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="5b780-125">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="5b780-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5b780-126">See also</span></span>

[<span data-ttu-id="5b780-127">Verwalten von Microsoft 365-Benutzerkonten,-Lizenzen und-Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b780-127">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5b780-128">Verwalten von Microsoft 365 mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b780-128">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5b780-129">Erste Schritte mit PowerShell für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="5b780-129">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
