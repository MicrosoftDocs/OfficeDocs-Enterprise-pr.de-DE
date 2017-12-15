---
title: Zuweisen von Rollen zu Benutzerkonten mit Office 365 PowerShell
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Zusammenfassung: Informationen zum Verwenden von Office 365 PowerShell und des Add-MsolRoleMember -Cmdlets zum Zuweisen von Rollen zu Benutzerkonten.'
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c1abd-103">Zuweisen von Rollen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1abd-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="c1abd-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell und das Cmdlet **Add-MsolRoleMember** Benutzerkonten Rollen zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="c1abd-104">**Summary:** Use Office 365 PowerShell and the **Add-MsolRoleMember** cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="c1abd-105">Sie können schnell und einfach Rollen-Benutzerkonten mit Office 365 PowerShell durch das Identifizieren von Anzeigename den Namen des Benutzerkontos und den Namen des Rollen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="c1abd-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="c1abd-106">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="c1abd-106">Before you begin</span></span>

<span data-ttu-id="c1abd-p101">Für die Verfahren in diesem Thema müssen Sie mithilfe eines globalen Administratorkontos eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c1abd-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="c1abd-109">Bei einer einzelnen Rollenänderung</span><span class="sxs-lookup"><span data-stu-id="c1abd-109">For a single role change</span></span>

<span data-ttu-id="c1abd-110">Legen Sie Folgendes fest:</span><span class="sxs-lookup"><span data-stu-id="c1abd-110">Determine the following:</span></span>
  
- <span data-ttu-id="c1abd-111">Das Benutzerkonto, das Sie konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c1abd-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="c1abd-p102">Um das Benutzerkonto angeben, müssen Sie den Anzeigenamen ermitteln. Wenn Sie eine vollständige Liste Konten erhalten möchten, verwenden Sie diesen Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="c1abd-p102">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c1abd-p103">Mit diesem Befehl wird der Anzeigename der Benutzerkonten nach Anzeigename sortiert angezeigt, jeweils einer auf einem Bildschirm. Sie können die Liste mit dem **Where** -Cmdlets weiter eingrenzen. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c1abd-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c1abd-117">Mit diesem Befehl werden nur die Benutzerkonten angezeigt, deren Anzeigename mit „John" beginnt.</span><span class="sxs-lookup"><span data-stu-id="c1abd-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="c1abd-118">Die Rolle, die Sie zuweisen möchten.</span><span class="sxs-lookup"><span data-stu-id="c1abd-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="c1abd-119">Um die Liste der verfügbaren Rollen anzuzeigen, die Benutzerkonten zugeordnet werden können, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="c1abd-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c1abd-120">Nachdem Sie den Anzeigenamen des Kontos und den Namen der Rolle bestimmt haben, verwenden Sie die folgenden Befehle, um dem Konto die Rolle zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="c1abd-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="c1abd-p104">Kopieren Sie die Befehle aus, und fügen sie in Notepad ein. Ersetzen Sie den Text der Beschreibung für die Variablen **$dispName** und **$roleName** mit ihren Werten, entfernen Sie die \< und > Zeichen, und lassen Sie die Anführungszeichen. Kopieren Sie die geänderten Zeilen, und fügen Sie sie in das Windows Azure Active Directory-Modul für Windows PowerShell-Fenster ausführen. Alternativ können Sie die Windows PowerShell Integrated Skript Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="c1abd-p104">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="c1abd-125">Hier ein Beispiel für einen abgeschlossenen Befehlssatz:</span><span class="sxs-lookup"><span data-stu-id="c1abd-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="c1abd-126">Bei mehreren Rollenänderungen</span><span class="sxs-lookup"><span data-stu-id="c1abd-126">For multiple role changes</span></span>

<span data-ttu-id="c1abd-127">Legen Sie Folgendes fest:</span><span class="sxs-lookup"><span data-stu-id="c1abd-127">Determine the following:</span></span>
  
- <span data-ttu-id="c1abd-128">Die Benutzerkonten, die Sie konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c1abd-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="c1abd-p105">Beim Angeben des Benutzerkontos müssen Sie seinen Anzeigenamen bestimmen. Verwenden Sie den folgenden Befehl, um eine Liste der Konten abzurufen:</span><span class="sxs-lookup"><span data-stu-id="c1abd-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c1abd-p106">Mit diesem Befehl wird der Anzeigename des alle Ihre Benutzerkonten, sortiert nach den Anzeigenamen, ein Fenster zu einem Zeitpunkt aufgeführt. Sie können die Liste auf einer kleineren Gruppe mithilfe des Cmdlets **, in dem** filtern. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c1abd-p106">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c1abd-134">Mit diesem Befehl werden nur die Benutzerkonten angezeigt, deren Anzeigename mit „John" beginnt.</span><span class="sxs-lookup"><span data-stu-id="c1abd-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="c1abd-135">Rollen, die Sie jedem Benutzerkonto zuweisen möchten.</span><span class="sxs-lookup"><span data-stu-id="c1abd-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="c1abd-136">Um die Liste der verfügbaren Rollen anzuzeigen, die Benutzerkonten zugeordnet werden können, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="c1abd-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c1abd-p107">Erstellen Sie im nächsten Schritt eine durch Trennzeichen getrennte Textdatei (CSV) mit Anzeigenamen und Rollennamen. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c1abd-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="c1abd-139">Geben Sie anschließend den Speicherort der CSV-Datei an, und führen Sie die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.</span><span class="sxs-lookup"><span data-stu-id="c1abd-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="c1abd-140">See also</span><span class="sxs-lookup"><span data-stu-id="c1abd-140">See also</span></span>

#### 

[<span data-ttu-id="c1abd-141">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1abd-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c1abd-142">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1abd-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c1abd-143">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1abd-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

[<span data-ttu-id="c1abd-144">Add-MsolRoleMember</span><span class="sxs-lookup"><span data-stu-id="c1abd-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)

