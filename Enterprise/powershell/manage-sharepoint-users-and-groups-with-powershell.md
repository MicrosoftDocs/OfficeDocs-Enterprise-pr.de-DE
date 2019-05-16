---
title: Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Benutzern,-Gruppen und-Websites.'
ms.openlocfilehash: 194486f539593215b8f8a17c04e3d4f499077c65
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068821"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="2967f-103">Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2967f-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="2967f-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Benutzern,-Gruppen und-Websites.</span><span class="sxs-lookup"><span data-stu-id="2967f-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="2967f-105">Wenn Sie ein SharePoint Online-Administrator sind, der mit umfangreichen Listen von Benutzerkonten oder Gruppen arbeitet und eine einfachere Lösung wünscht, können Sie Office 365 PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="2967f-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="2967f-106">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="2967f-106">Before you begin</span></span>

<span data-ttu-id="2967f-107">Bei den Verfahren in diesem Thema müssen Sie eine Verbindung mit SharePoint Online herstellen.</span><span class="sxs-lookup"><span data-stu-id="2967f-107">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="2967f-108">Weitere Informationen finden Sie unter [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="2967f-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="2967f-109">Abrufen einer Liste von Websites, Gruppen und Benutzern</span><span class="sxs-lookup"><span data-stu-id="2967f-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="2967f-110">Bevor wir mit der Verwaltung von Benutzern und Gruppen beginnen, müssen Sie Listen Ihrer Websites, Gruppen und Benutzer abrufen.</span><span class="sxs-lookup"><span data-stu-id="2967f-110">Before we start to manage users and groups, you need to get lists of your sites, groups, and users.</span></span> <span data-ttu-id="2967f-111">Sie können diese Informationen dann verwenden, um das Beispiel in diesem Artikel zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="2967f-111">You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="2967f-112">Abrufen einer Liste von Websites</span><span class="sxs-lookup"><span data-stu-id="2967f-112">Get a list of sites</span></span>

<span data-ttu-id="2967f-113">Rufen Sie mit diesem Befehl eine Liste der Websites in Ihrem Mandanten ab:</span><span class="sxs-lookup"><span data-stu-id="2967f-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="2967f-114">Abrufen einer Liste von Gruppen</span><span class="sxs-lookup"><span data-stu-id="2967f-114">Get a list of groups</span></span>

<span data-ttu-id="2967f-115">Rufen Sie mit diesem Befehl eine Liste der Gruppen in Ihrem Mandanten ab:</span><span class="sxs-lookup"><span data-stu-id="2967f-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="2967f-116">Abrufen einer Liste von Benutzern</span><span class="sxs-lookup"><span data-stu-id="2967f-116">Get a list of users</span></span>

<span data-ttu-id="2967f-117">Rufen Sie mit diesem Befehl eine Liste der Benutzer in Ihrem Mandanten ab:</span><span class="sxs-lookup"><span data-stu-id="2967f-117">Get a list of the users in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="2967f-118">Hinzufügen eines Benutzers zur Gruppe der Websitesammlungsadministratoren</span><span class="sxs-lookup"><span data-stu-id="2967f-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="2967f-119">Verwenden Sie den Befehl **Set-ehepartnerr** , um einen Benutzer zur Liste der Websitesammlungsadministratoren in einer Websitesammlung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2967f-119">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection.</span></span> <span data-ttu-id="2967f-120">So sieht die Syntax aus:</span><span class="sxs-lookup"><span data-stu-id="2967f-120">This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="2967f-121">Ersetzen Sie zum Verwenden dieser Befehle alle Elemente innerhalb der Anführungszeichen, einschließlich < und >, mit den richtigen Namen.</span><span class="sxs-lookup"><span data-stu-id="2967f-121">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="2967f-122">Dieser Befehlssatz fügt beispielsweise Opal Castillo (Benutzername opalc) die Liste der Websitesammlungsadministratoren in der ContosoTest-Websitesammlung in der Contoso1-Mandantschaft hinzu:</span><span class="sxs-lookup"><span data-stu-id="2967f-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="2967f-123">Sie können diese Befehle Kopieren und in Editor einfügen, die Variablenwerte für $Tenant, $Site und $User auf tatsächliche Werte aus Ihrer Umgebung ändern und diese dann in Ihr SharePoint Online-Verwaltungsshell-Fenster einfügen, um Sie auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2967f-123">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="2967f-124">Hinzufügen eines Benutzers zu anderen Gruppen von Websitesammlungsadministratoren</span><span class="sxs-lookup"><span data-stu-id="2967f-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="2967f-125">In dieser Aufgabe verwenden wir den Befehl **Add-Ehegatten** , um einen Benutzer zu einer SharePoint-Gruppe in einer Websitesammlung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2967f-125">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="2967f-126">Lassen Sie uns beispielsweise die Gruppe "Revisoren" (Benutzername "glenr") zur ContosoTest-Websitesammlung in der Contoso1-Mandantschaft hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="2967f-126">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="2967f-127">Erstellen einer Website Sammlungs Gruppe</span><span class="sxs-lookup"><span data-stu-id="2967f-127">Create a site collection group</span></span>

<span data-ttu-id="2967f-128">Verwenden Sie den Befehl **Set-SPOSiteGroup** , um eine neue SharePoint-Gruppe zu erstellen und der ContosoTest-Websitesammlung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2967f-128">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="2967f-129">Gruppeneigenschaften wie Berechtigungsstufen können später mithilfe des Cmdlets **Set-SPOSiteGroup** aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="2967f-129">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="2967f-130">Beispielsweise können wir die Gruppe "Überwachung" mit Berechtigungen "nur anzeigen" für die Contoso-Test Websitesammlung in der Contoso1-Mandantschaft hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="2967f-130">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="2967f-131">Entfernen von Benutzern aus einer Gruppe</span><span class="sxs-lookup"><span data-stu-id="2967f-131">Remove users from a group</span></span>

<span data-ttu-id="2967f-132">Manchmal müssen Sie einen Benutzer von einer Website oder sogar allen Websites entfernen.</span><span class="sxs-lookup"><span data-stu-id="2967f-132">Sometimes you have to remove a user from a site or even all sites.</span></span> <span data-ttu-id="2967f-133">Vielleicht verschiebt sich der Mitarbeiter von einem Geschäftsbereich zu einem anderen oder verlässt das Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="2967f-133">Perhaps the employee moves from one division to another or leaves the company.</span></span> <span data-ttu-id="2967f-134">Sie können dies für einen Mitarbeiter problemlos auf der Benutzeroberfläche tun, dies ist jedoch nicht einfach, wenn Sie eine vollständige Abteilung von einer Website zu einer anderen verschieben müssen.</span><span class="sxs-lookup"><span data-stu-id="2967f-134">You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="2967f-135">Wenn Sie jedoch die SharePoint Online-Verwaltungsshell und die CSV-Dateien verwenden, ist dies schnell und einfach.</span><span class="sxs-lookup"><span data-stu-id="2967f-135">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="2967f-136">In dieser Aufgabe verwenden Sie Windows PowerShell, um einen Benutzer aus einer Website Sammlungs Sicherheitsgruppe zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="2967f-136">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="2967f-137">Anschließend verwenden Sie eine CSV-Datei und entfernen viele Benutzer aus unterschiedlichen Websites.</span><span class="sxs-lookup"><span data-stu-id="2967f-137">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="2967f-138">Wir verwenden den Befehl **Remove-ehepartnerr** , um einen einzelnen Office 365-Benutzer aus einer Website Sammlungs Gruppe zu entfernen, damit die Befehlssyntax angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2967f-138">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="2967f-139">Die Syntax sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="2967f-139">Here is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="2967f-140">Lassen Sie uns beispielsweise Bobby Overby aus der Gruppe der Website Sammlungs Prüfer in der Contoso-Test Websitesammlung in der Contoso1-Mandantschaft entfernen:</span><span class="sxs-lookup"><span data-stu-id="2967f-140">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="2967f-141">Angenommen, wir wollten Bobby aus allen Gruppen entfernen, in denen er sich gerade befindet.</span><span class="sxs-lookup"><span data-stu-id="2967f-141">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="2967f-142">So gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="2967f-142">Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="2967f-143">Dies ist nur ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="2967f-143">This is just an example.</span></span> <span data-ttu-id="2967f-144">Führen Sie diesen Befehl nur aus, wenn Sie wirklich einen Benutzer aus jeder Gruppe entfernen müssen, beispielsweise wenn der Benutzer das Unternehmen verlässt.</span><span class="sxs-lookup"><span data-stu-id="2967f-144">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="2967f-145">Automatisieren der Verwaltung umfangreicher Listen von Benutzern und Gruppen</span><span class="sxs-lookup"><span data-stu-id="2967f-145">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="2967f-146">Wenn Sie SharePoint-Websites eine hohe Anzahl von Konten hinzufügen und Ihnen Berechtigungen erteilen möchten, können Sie das Microsoft 365 Admin Center, einzelne PowerShell-Befehle oder eine PowerShell-CSV-Datei verwenden.</span><span class="sxs-lookup"><span data-stu-id="2967f-146">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="2967f-147">Die CSV-Datei ist die schnellste Möglichkeit, um diese Aufgabe zu automatisieren.</span><span class="sxs-lookup"><span data-stu-id="2967f-147">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="2967f-148">Der grundlegende Prozess besteht darin, eine CSV-Datei mit Kopfzeilen (Spalten) zu erstellen, die den Parametern entsprechen, die das Windows PowerShell-Skript benötigt.</span><span class="sxs-lookup"><span data-stu-id="2967f-148">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="2967f-149">Sie können eine solche Liste ganz einfach in Excel erstellen und dann als CSV-Datei exportieren.</span><span class="sxs-lookup"><span data-stu-id="2967f-149">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="2967f-150">Anschließend verwenden Sie ein Windows PowerShell-Skript zum Durchlaufen von Datensätzen (Zeilen) in der CSV-Datei, indem Sie die Benutzergruppen und den Websites hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2967f-150">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="2967f-151">Erstellen wir beispielsweise eine CSV-Datei, um eine Gruppe von Websitesammlungen, Gruppen und Berechtigungen zu definieren.</span><span class="sxs-lookup"><span data-stu-id="2967f-151">For example, let’s create a CSV file to define a group of site collections, groups, and permissions.</span></span> <span data-ttu-id="2967f-152">Als Nächstes erstellen wir eine CSV-Datei, um die Gruppen mit Benutzern aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="2967f-152">Next, we will create a CSV file to populate the groups with users.</span></span> <span data-ttu-id="2967f-153">Schließlich erstellen und führen wir ein einfaches Windows PowerShell-Skript aus, das die Gruppen erstellt und auffüllt.</span><span class="sxs-lookup"><span data-stu-id="2967f-153">Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="2967f-154">Die erste CSV-Datei fügt einer oder mehreren Websitesammlungen eine oder mehrere Gruppen hinzu und weist diese Struktur auf:</span><span class="sxs-lookup"><span data-stu-id="2967f-154">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="2967f-155">Header</span><span class="sxs-lookup"><span data-stu-id="2967f-155">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="2967f-156">Element</span><span class="sxs-lookup"><span data-stu-id="2967f-156">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="2967f-157">Hier ist eine Beispieldatei:</span><span class="sxs-lookup"><span data-stu-id="2967f-157">Here is an example file:</span></span>

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="2967f-158">Die zweite CSV-Datei fügt einer oder mehreren Gruppen einen oder mehrere Benutzer hinzu und weist diese Struktur auf:</span><span class="sxs-lookup"><span data-stu-id="2967f-158">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="2967f-159">Header</span><span class="sxs-lookup"><span data-stu-id="2967f-159">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="2967f-160">Element</span><span class="sxs-lookup"><span data-stu-id="2967f-160">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="2967f-161">Hier ist eine Beispieldatei:</span><span class="sxs-lookup"><span data-stu-id="2967f-161">Here is an example file:</span></span>

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

<span data-ttu-id="2967f-162">Für den nächsten Schritt müssen Sie die beiden CSV-Dateien auf Ihrem Laufwerk gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="2967f-162">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="2967f-163">Hier sind Beispielbefehle, die sowohl CSV-Dateien als auch Berechtigungen und Gruppenmitgliedschaften hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="2967f-163">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="2967f-164">Das Skript importiert den Inhalt der CSV-Datei und verwendet die Werte in den Spalten, um die Parameter der Befehle **New-SPOSiteGroup** und **Add-ehegatter** aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="2967f-164">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="2967f-165">In unserem Beispiel speichern wir diese in theO365Admin Ordner auf Laufwerk C, aber Sie können es speichern, wo immer Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="2967f-165">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="2967f-166">Nun entfernen wir eine Gruppe von Personen für mehrere Gruppen an unterschiedlichen Standorten mit derselben CSV-Datei.</span><span class="sxs-lookup"><span data-stu-id="2967f-166">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="2967f-167">Nachfolgend sehen Sie einen Beispielbefehl:</span><span class="sxs-lookup"><span data-stu-id="2967f-167">Here is an example command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="2967f-168">Generieren von Benutzer berichten</span><span class="sxs-lookup"><span data-stu-id="2967f-168">Generate user reports</span></span>

<span data-ttu-id="2967f-169">Möglicherweise möchten Sie einen einfachen Bericht für einige Websites abrufen und die Benutzer für diese Websites, ihre Berechtigungsstufe und andere Eigenschaften anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2967f-169">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties.</span></span> <span data-ttu-id="2967f-170">So sieht die Syntax aus:</span><span class="sxs-lookup"><span data-stu-id="2967f-170">This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="2967f-171">Dadurch werden die Daten für diese drei Websites erfasst und in eine Textdatei auf Ihrem lokalen Laufwerk geschrieben.</span><span class="sxs-lookup"><span data-stu-id="2967f-171">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="2967f-172">Beachten Sie, dass mit dem Parameter-Append neue Inhalte zu einer vorhandenen Datei hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="2967f-172">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="2967f-173">Lassen Sie uns beispielsweise einen Bericht über die ContosoTest-, TeamSite01-und Project01-Websites für den Contoso1-Mandanten ausführen:</span><span class="sxs-lookup"><span data-stu-id="2967f-173">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="2967f-174">Beachten Sie, dass nur die **$Site** -Variable geändert werden musste.</span><span class="sxs-lookup"><span data-stu-id="2967f-174">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="2967f-175">Die **$Tenant** -Variable behält ihren Wert über alle drei Läufe des Befehls bei.</span><span class="sxs-lookup"><span data-stu-id="2967f-175">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="2967f-176">Was geschieht jedoch, wenn Sie dies für jede Website tun möchten?</span><span class="sxs-lookup"><span data-stu-id="2967f-176">However, what if you wanted to do this for every site?</span></span> <span data-ttu-id="2967f-177">Sie können dies tun, ohne alle diese Websites eingeben zu müssen, indem Sie den folgenden Befehl verwenden:</span><span class="sxs-lookup"><span data-stu-id="2967f-177">You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="2967f-178">Dieser Bericht ist relativ einfach, und Sie können weiteren Code hinzufügen, um spezifischere Berichte oder Berichte mit detaillierteren Informationen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2967f-178">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="2967f-179">Dies sollte Ihnen jedoch eine Vorstellung davon vermitteln, wie Sie die SharePoint Online-Verwaltungsshell zum Verwalten von Benutzern in der SharePoint Online-Umgebung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2967f-179">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="2967f-180">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2967f-180">See also</span></span>

[<span data-ttu-id="2967f-181">Herstellen einer Verbindung mit SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="2967f-181">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="2967f-182">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2967f-182">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="2967f-183">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2967f-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2967f-184">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2967f-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

