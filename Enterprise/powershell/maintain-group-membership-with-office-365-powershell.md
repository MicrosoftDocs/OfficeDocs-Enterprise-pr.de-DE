---
title: Verwalten der Gruppenmitgliedschaft mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Hier erfahren Sie, wie Sie Office 365 PowerShell verwenden, um die Mitgliedschaft in Gruppen für Office 365 beizubehalten.
ms.openlocfilehash: 0e6c5f2e27f9d146bb2a053bd3bdb6694fb07276
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004628"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a>Verwalten der Gruppenmitgliedschaft mit Office 365 PowerShell

Sie können Office 365 PowerShell als Alternative zum Microsoft 365 Admin Center verwenden, um die Gruppenmitgliedschaft in Office 365 beizubehalten. 

> [!TIP]
> Zum Generieren von Ready-to-Run PowerShell-Befehlen durch Angabe von Benutzerkonten-und Gruppennamen verwenden Sie diese [Gruppenpflege Microsoft Excel Arbeitsmappe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx). 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module
Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Hinzufügen oder Entfernen von Benutzerkonten als Mitglieder einer Gruppe

**Um ein Benutzerkonto nach seinem UPN hinzuzufügen**, geben Sie den Benutzerprinzipalnamen (User Principal Name, UPN) des Benutzerkontos ein (Beispiel: belindan@contoso.com) und den Gruppen Anzeigenamen, indem Sie die Zeichen "<" und ">" entfernen und diese Befehle im PowerShell-Fenster oder in der PowerShell-integrierten Skriptumgebung (ISE) ausführen.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Wenn Sie ein Benutzerkonto anhand des Anzeigenamens hinzufügen möchten**, geben Sie den Anzeigenamen des Benutzerkontos ein (Beispiel: Belinda Newman) und den Gruppenanzeige Namen, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Wenn Sie ein Benutzerkonto nach seinem UPN entfernen möchten**, füllen Sie das Benutzerkonto UPN (Beispiel: belindan@contoso.com) und den Gruppenanzeige Namen aus, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Wenn Sie ein Benutzerkonto anhand des Anzeigenamens entfernen möchten**, geben Sie den Anzeigenamen des Benutzerkontos ein (Beispiel: Belinda Newman) und den Gruppenanzeige Namen, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Hinzufügen oder Entfernen von Gruppen als Mitglieder einer Gruppe

Sicherheitsgruppen können andere Gruppen als Mitglieder enthalten. Office 365 Gruppen können jedoch nicht. Dieser Abschnitt enthält PowerShell-Befehle zum Hinzufügen oder Entfernen von Gruppen nur für eine Sicherheitsgruppe.

**Um eine Gruppe nach dem Anzeigenamen hinzuzufügen**, geben Sie den Anzeigenamen der hinzuzufügenden Gruppe und den Anzeigenamen der Gruppe ein, die die Mitgliedergruppe enthalten soll, und führen Sie diese Befehle im PowerShell-Fenster oder in PowerShell ISE aus.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Wenn Sie eine Gruppe nach Ihrem Anzeigenamen entfernen möchten**, geben Sie den Anzeigenamen der zu entfernenden Gruppe und den Anzeigenamen der Gruppe ein, die die Mitgliedergruppe enthalten soll, und führen Sie diese Befehle im PowerShell-Fenster oder in PowerShell ISE aus.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Hinzufügen oder Entfernen von Benutzerkonten als Mitglieder einer Gruppe

**Um ein Benutzerkonto nach seinem UPN hinzuzufügen**, geben Sie den Benutzerprinzipalnamen (User Principal Name, UPN) des Benutzerkontos ein (Beispiel: belindan@contoso.com) und den Gruppen Anzeigenamen, indem Sie die Zeichen "<" und ">" entfernen und diese Befehle im PowerShell-Fenster oder in der PowerShell ISE ausführen.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Wenn Sie ein Benutzerkonto anhand des Anzeigenamens hinzufügen möchten**, geben Sie den Anzeigenamen des Benutzerkontos ein (Beispiel: Belinda Newman) und den Gruppenanzeige Namen, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Wenn Sie ein Benutzerkonto nach seinem UPN entfernen möchten**, füllen Sie das Benutzerkonto UPN (Beispiel: belindan@contoso.com) und den Gruppenanzeige Namen aus, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Wenn Sie ein Benutzerkonto anhand des Anzeigenamens entfernen möchten**, geben Sie den Anzeigenamen des Benutzerkontos ein (Beispiel: Belinda Newman) und den Gruppenanzeige Namen, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Hinzufügen oder Entfernen von Gruppen als Mitglieder einer Gruppe

Sicherheitsgruppen können andere Gruppen als Mitglieder enthalten. Office 365 Gruppen können jedoch nicht. Dieser Abschnitt enthält PowerShell-Befehle zum Hinzufügen oder Entfernen von Gruppen nur für eine Sicherheitsgruppe.

**Um eine Gruppe nach dem Anzeigenamen hinzuzufügen**, geben Sie den Anzeigenamen der hinzuzufügenden Gruppe und den Anzeigenamen der Gruppe ein, die die Mitgliedergruppe enthalten soll, und führen Sie diese Befehle im PowerShell-Fenster oder in PowerShell ISE aus.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**Wenn Sie eine Gruppe nach Ihrem Anzeigenamen entfernen möchten**, geben Sie den Anzeigenamen der zu entfernenden Gruppe und den Anzeigenamen der Gruppe ein, die die Mitgliedergruppe enthalten soll, und führen Sie diese Befehle im PowerShell-Fenster oder in PowerShell ISE aus.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

