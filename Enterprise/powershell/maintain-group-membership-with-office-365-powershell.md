---
title: Verwalten der Microsoft 365-Gruppenmitgliedschaft mit PowerShell
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Erfahren Sie, wie Sie mithilfe von PowerShell die Mitgliedschaft in Microsoft 365-Gruppen beibehalten.
ms.openlocfilehash: f75587c9c50a1fce3a5abfb00ddba2845318e9c4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230651"
---
# <a name="maintain-microsoft-365-group-membership-with-powershell"></a><span data-ttu-id="eab8e-103">Verwalten der Microsoft 365-Gruppenmitgliedschaft mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="eab8e-103">Maintain Microsoft 365 group membership with PowerShell</span></span>

<span data-ttu-id="eab8e-104">*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="eab8e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="eab8e-105">Sie können PowerShell für Microsoft 365 als Alternative zum Microsoft 365 Admin Center verwenden, um die Gruppenmitgliedschaft in Microsoft 365 beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="eab8e-105">You can use PowerShell for Microsoft 365 as an alternative to the Microsoft 365 admin center to maintain group membership in Microsoft 365.</span></span> 

> [!TIP]
> <span data-ttu-id="eab8e-106">Zum Generieren von Ready-to-Run PowerShell-Befehlen durch Angabe von Benutzerkonten-und Gruppennamen verwenden Sie diese [Gruppenpflege Microsoft Excel Arbeitsmappe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span><span class="sxs-lookup"><span data-stu-id="eab8e-106">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="eab8e-107">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="eab8e-107">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="eab8e-108">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="eab8e-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="eab8e-109">Hinzufügen oder Entfernen von Benutzerkonten als Mitglieder einer Gruppe</span><span class="sxs-lookup"><span data-stu-id="eab8e-109">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="eab8e-110">**Um ein Benutzerkonto nach seinem UPN hinzuzufügen**, geben Sie den Benutzerprinzipalnamen (User Principal Name, UPN) des Benutzerkontos ein (Beispiel: belindan@contoso.com) und den Gruppen Anzeigenamen, indem Sie die Zeichen "<" und ">" entfernen und diese Befehle im PowerShell-Fenster oder in der PowerShell-integrierten Skriptumgebung (ISE) ausführen.</span><span class="sxs-lookup"><span data-stu-id="eab8e-110">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="eab8e-111">**Wenn Sie ein Benutzerkonto anhand des Anzeigenamens hinzufügen möchten**, geben Sie den Anzeigenamen des Benutzerkontos ein (Beispiel: Belinda Newman) und den Gruppenanzeige Namen, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-111">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="eab8e-112">**Wenn Sie ein Benutzerkonto nach seinem UPN entfernen möchten**, füllen Sie das Benutzerkonto UPN (Beispiel: belindan@contoso.com) und den Gruppenanzeige Namen aus, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-112">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="eab8e-113">**Wenn Sie ein Benutzerkonto anhand des Anzeigenamens entfernen möchten**, geben Sie den Anzeigenamen des Benutzerkontos ein (Beispiel: Belinda Newman) und den Gruppenanzeige Namen, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-113">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="eab8e-114">Hinzufügen oder Entfernen von Gruppen als Mitglieder einer Gruppe</span><span class="sxs-lookup"><span data-stu-id="eab8e-114">Add or remove groups as members of a group</span></span>

<span data-ttu-id="eab8e-115">Sicherheitsgruppen können andere Gruppen als Mitglieder enthalten.</span><span class="sxs-lookup"><span data-stu-id="eab8e-115">Security groups can contain other groups as members.</span></span> <span data-ttu-id="eab8e-116">Microsoft 365-Gruppen können jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="eab8e-116">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="eab8e-117">Dieser Abschnitt enthält PowerShell-Befehle zum Hinzufügen oder Entfernen von Gruppen nur für eine Sicherheitsgruppe.</span><span class="sxs-lookup"><span data-stu-id="eab8e-117">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="eab8e-118">**Um eine Gruppe nach dem Anzeigenamen hinzuzufügen**, geben Sie den Anzeigenamen der hinzuzufügenden Gruppe und den Anzeigenamen der Gruppe ein, die die Mitgliedergruppe enthalten soll, und führen Sie diese Befehle im PowerShell-Fenster oder in PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-118">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="eab8e-119">**Wenn Sie eine Gruppe nach Ihrem Anzeigenamen entfernen möchten**, geben Sie den Anzeigenamen der zu entfernenden Gruppe und den Anzeigenamen der Gruppe ein, die die Mitgliedergruppe enthalten soll, und führen Sie diese Befehle im PowerShell-Fenster oder in PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-119">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="eab8e-120">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eab8e-120">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="eab8e-121">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="eab8e-121">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="eab8e-122">Hinzufügen oder Entfernen von Benutzerkonten als Mitglieder einer Gruppe</span><span class="sxs-lookup"><span data-stu-id="eab8e-122">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="eab8e-123">**Um ein Benutzerkonto nach seinem UPN hinzuzufügen**, geben Sie den Benutzerprinzipalnamen (User Principal Name, UPN) des Benutzerkontos ein (Beispiel: belindan@contoso.com) und den Gruppen Anzeigenamen, indem Sie die Zeichen "<" und ">" entfernen und diese Befehle im PowerShell-Fenster oder in der PowerShell ISE ausführen.</span><span class="sxs-lookup"><span data-stu-id="eab8e-123">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="eab8e-124">**Wenn Sie ein Benutzerkonto anhand des Anzeigenamens hinzufügen möchten**, geben Sie den Anzeigenamen des Benutzerkontos ein (Beispiel: Belinda Newman) und den Gruppenanzeige Namen, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-124">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="eab8e-125">**Wenn Sie ein Benutzerkonto nach seinem UPN entfernen möchten**, füllen Sie das Benutzerkonto UPN (Beispiel: belindan@contoso.com) und den Gruppenanzeige Namen aus, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-125">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="eab8e-126">**Wenn Sie ein Benutzerkonto anhand des Anzeigenamens entfernen möchten**, geben Sie den Anzeigenamen des Benutzerkontos ein (Beispiel: Belinda Newman) und den Gruppenanzeige Namen, und führen Sie diese Befehle im PowerShell-Fenster oder in der PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-126">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="eab8e-127">Hinzufügen oder Entfernen von Gruppen als Mitglieder einer Gruppe</span><span class="sxs-lookup"><span data-stu-id="eab8e-127">Add or remove groups as members of a group</span></span>

<span data-ttu-id="eab8e-128">Sicherheitsgruppen können andere Gruppen als Mitglieder enthalten.</span><span class="sxs-lookup"><span data-stu-id="eab8e-128">Security groups can contain other groups as members.</span></span> <span data-ttu-id="eab8e-129">Microsoft 365-Gruppen können jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="eab8e-129">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="eab8e-130">Dieser Abschnitt enthält PowerShell-Befehle zum Hinzufügen oder Entfernen von Gruppen nur für eine Sicherheitsgruppe.</span><span class="sxs-lookup"><span data-stu-id="eab8e-130">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="eab8e-131">**Um eine Gruppe nach dem Anzeigenamen hinzuzufügen**, geben Sie den Anzeigenamen der hinzuzufügenden Gruppe und den Anzeigenamen der Gruppe ein, die die Mitgliedergruppe enthalten soll, und führen Sie diese Befehle im PowerShell-Fenster oder in PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-131">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="eab8e-132">**Wenn Sie eine Gruppe nach Ihrem Anzeigenamen entfernen möchten**, geben Sie den Anzeigenamen der zu entfernenden Gruppe und den Anzeigenamen der Gruppe ein, die die Mitgliedergruppe enthalten soll, und führen Sie diese Befehle im PowerShell-Fenster oder in PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="eab8e-132">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="eab8e-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="eab8e-133">See also</span></span>

[<span data-ttu-id="eab8e-134">Verwalten von Microsoft 365-Benutzerkonten,-Lizenzen und-Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="eab8e-134">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="eab8e-135">Verwalten von Microsoft 365 mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="eab8e-135">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="eab8e-136">Erste Schritte mit PowerShell für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="eab8e-136">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

