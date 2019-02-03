---
title: Zuweisen von Rollen zu Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Zusammenfassung: Verwenden von Office 365 PowerShell zum Zuweisen von Rollen zu Benutzerkonten.'
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690436"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c7365-103">Zuweisen von Rollen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7365-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c7365-104">Mit Office 365 PowerShell können Sie schnell und einfach Rollen zu Benutzerkonten zuweisen.</span><span class="sxs-lookup"><span data-stu-id="c7365-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c7365-105">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="c7365-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c7365-106">[Verbinden Sie zunächst Ihren Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) mithilfe eines globalen Administratorkontos.</span><span class="sxs-lookup"><span data-stu-id="c7365-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="c7365-p101">Als Nächstes ermitteln Sie den Anmeldenamen des Benutzerkontos, das Sie zu einer Rolle hinzufügen möchten (Beispiel: fredsm@contoso.com). Dies wird auch als der Benutzerprinzipalname (User Principal Name, UPN) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c7365-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="c7365-p102">Als Nächstes bestimmen Sie den Namen der Rolle. Verwenden Sie den folgenden Befehl, um die Rollen aufzulisten, die Sie mit PowerShell zuweisen können.</span><span class="sxs-lookup"><span data-stu-id="c7365-p102">Next, determine the name of the role. Use this command to list the roles that you can assign with PowerShell.</span></span>

````
Get-AzureADDirectoryRole
````

<span data-ttu-id="c7365-111">Als Nächstes geben Sie den Anmelde- und Rollennamen ein, und führen die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="c7365-111">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="c7365-112">Hier ein Beispiel für einen abgeschlossenen Befehlssatz:</span><span class="sxs-lookup"><span data-stu-id="c7365-112">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="c7365-113">Verwenden Sie diese Befehle zum Anzeigen der Liste der Benutzernamen für eine bestimmte Rolle.</span><span class="sxs-lookup"><span data-stu-id="c7365-113">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c7365-114">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7365-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c7365-115">[Verbinden Sie zunächst Ihren Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) mithilfe eines globalen Administratorkontos.</span><span class="sxs-lookup"><span data-stu-id="c7365-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="c7365-116">Bei einer einzelnen Rollenänderung</span><span class="sxs-lookup"><span data-stu-id="c7365-116">For a single role change</span></span>

<span data-ttu-id="c7365-117">Legen Sie Folgendes fest:</span><span class="sxs-lookup"><span data-stu-id="c7365-117">Determine the following:</span></span>
  
- <span data-ttu-id="c7365-118">Das Benutzerkonto, das Sie konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c7365-118">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="c7365-p103">Beim Angeben des Benutzerkontos müssen Sie seinen Anzeigenamen bestimmen. Verwenden Sie den folgenden Befehl, um eine vollständige Liste der Konten abzurufen:</span><span class="sxs-lookup"><span data-stu-id="c7365-p103">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c7365-p104">Mit diesem Befehl wird der Anzeigename der Benutzerkonten nach Anzeigename sortiert angezeigt, jeweils einer auf einem Bildschirm. Sie können die Liste mit dem **Where** -Cmdlets weiter eingrenzen. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c7365-p104">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c7365-124">Mit diesem Befehl werden nur die Benutzerkonten angezeigt, deren Anzeigename mit „John“ beginnt.</span><span class="sxs-lookup"><span data-stu-id="c7365-124">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="c7365-125">Die Rolle, die Sie zuweisen möchten.</span><span class="sxs-lookup"><span data-stu-id="c7365-125">The role you want to assign.</span></span>
    
    <span data-ttu-id="c7365-126">Um die Liste der verfügbaren Rollen anzuzeigen, die Benutzerkonten zugeordnet werden können, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="c7365-126">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c7365-127">Nachdem Sie den Anzeigenamen des Kontos und den Namen der Rolle bestimmt haben, verwenden Sie die folgenden Befehle, um dem Konto die Rolle zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="c7365-127">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="c7365-p105">Kopieren Sie die Befehle, und fügen Sie sie in Editor ein. Ersetzen Sie in den **$dispName**- und **$roleName**-Variablen die Beschreibung durch die entsprechenden Werte, entfernen Sie die Zeichen „\<" und „>", und lassen Sie die Anführungszeichen stehen. Kopieren Sie die geänderten Zeilen, und fügen Sie sie in das Fenster „Windows Azure Active Directory-Modul für Windows PowerShell", um sie auszuführen. Alternativ können Sie die Windows PowerShell ISE (Integrated Script Environment) verwenden.</span><span class="sxs-lookup"><span data-stu-id="c7365-p105">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="c7365-132">Hier ein Beispiel für einen abgeschlossenen Befehlssatz:</span><span class="sxs-lookup"><span data-stu-id="c7365-132">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="c7365-133">Bei mehreren Rollenänderungen</span><span class="sxs-lookup"><span data-stu-id="c7365-133">For multiple role changes</span></span>

<span data-ttu-id="c7365-134">Legen Sie Folgendes fest:</span><span class="sxs-lookup"><span data-stu-id="c7365-134">Determine the following:</span></span>
  
- <span data-ttu-id="c7365-135">Die Benutzerkonten, die Sie konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c7365-135">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="c7365-p106">Beim Angeben des Benutzerkontos müssen Sie seinen Anzeigenamen bestimmen. Verwenden Sie den folgenden Befehl, um eine Liste der Konten abzurufen:</span><span class="sxs-lookup"><span data-stu-id="c7365-p106">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c7365-p107">Mit diesem Befehl wird der Anzeigename der Benutzerkonten nach Anzeigename sortiert angezeigt, jeweils einer auf einem Bildschirm. Sie können die Liste mit dem **Where**-Cmdlets weiter eingrenzen. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c7365-p107">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="c7365-141">Mit diesem Befehl werden nur die Benutzerkonten angezeigt, deren Anzeigename mit „John“ beginnt.</span><span class="sxs-lookup"><span data-stu-id="c7365-141">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="c7365-142">Rollen, die Sie jedem Benutzerkonto zuweisen möchten.</span><span class="sxs-lookup"><span data-stu-id="c7365-142">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="c7365-143">Um die Liste der verfügbaren Rollen anzuzeigen, die Benutzerkonten zugeordnet werden können, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="c7365-143">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="c7365-p108">Erstellen Sie im nächsten Schritt eine durch Trennzeichen getrennte Textdatei (CSV) mit Anzeigenamen und Rollennamen. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c7365-p108">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="c7365-146">Geben Sie anschließend den Speicherort der CSV-Datei an, und führen Sie die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.</span><span class="sxs-lookup"><span data-stu-id="c7365-146">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="c7365-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c7365-147">See also</span></span>

- [<span data-ttu-id="c7365-148">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7365-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="c7365-149">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7365-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="c7365-150">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7365-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
