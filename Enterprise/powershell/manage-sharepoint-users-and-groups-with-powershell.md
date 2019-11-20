---
title: Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell, um SharePoint Online-Benutzer,-Gruppen und-Websites zu verwalten.'
ms.openlocfilehash: e011946fa46455d1c1eba2bdff565bd55ec875bf
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747620"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="465df-103">Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="465df-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

<span data-ttu-id="465df-104">Wenn Sie ein SharePoint Online Administrator sind, der mit umfangreichen Listen mit Benutzerkonten oder Gruppen arbeitet und eine einfachere Verwaltung wünscht, können Sie Office 365 PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="465df-104">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="465df-105">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="465df-105">Before you begin</span></span>

<span data-ttu-id="465df-106">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit SharePoint Online herstellen.</span><span class="sxs-lookup"><span data-stu-id="465df-106">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="465df-107">Anweisungen finden Sie unter [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) .</span><span class="sxs-lookup"><span data-stu-id="465df-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="465df-108">Abrufen einer Liste von Websites, Gruppen und Benutzern</span><span class="sxs-lookup"><span data-stu-id="465df-108">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="465df-109">Bevor wir mit der Verwaltung von Benutzern und Gruppen beginnen, müssen Sie Listen mit Websites, Gruppen und Benutzern abrufen.</span><span class="sxs-lookup"><span data-stu-id="465df-109">Before we start to manage users and groups, you need to get lists of your sites, groups, and users.</span></span> <span data-ttu-id="465df-110">Anschließend können Sie diese Informationen verwenden, um das Beispiel in diesem Artikel zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="465df-110">You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="465df-111">Abrufen einer Liste von Websites</span><span class="sxs-lookup"><span data-stu-id="465df-111">Get a list of sites</span></span>

<span data-ttu-id="465df-112">Rufen Sie mit dem folgenden Befehl eine Liste der Websites in Ihrem Mandanten ab:</span><span class="sxs-lookup"><span data-stu-id="465df-112">Get a list of the sites in your tenant with this command:</span></span>

```powershell
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="465df-113">Abrufen einer Liste von Gruppen</span><span class="sxs-lookup"><span data-stu-id="465df-113">Get a list of groups</span></span>

<span data-ttu-id="465df-114">Rufen Sie mit dem folgenden Befehl eine Liste der Gruppen in Ihrem Mandanten ab:</span><span class="sxs-lookup"><span data-stu-id="465df-114">Get a list of the groups in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="465df-115">Abrufen einer Liste von Benutzern</span><span class="sxs-lookup"><span data-stu-id="465df-115">Get a list of users</span></span>

<span data-ttu-id="465df-116">Rufen Sie mit dem folgenden Befehl eine Liste der Benutzer in Ihrem Mandanten ab:</span><span class="sxs-lookup"><span data-stu-id="465df-116">Get a list of the users in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="465df-117">Hinzufügen eines Benutzers zur Gruppe "Websitesammlungsadministratoren"</span><span class="sxs-lookup"><span data-stu-id="465df-117">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="465df-118">Verwenden Sie den Befehl **Gruppe-ehegatter** , um einen Benutzer zur Liste der Websitesammlungsadministratoren in einer Websitesammlung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="465df-118">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection.</span></span> <span data-ttu-id="465df-119">So sieht die Syntax aus:</span><span class="sxs-lookup"><span data-stu-id="465df-119">This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="465df-120">Um diese Befehle zu verwenden, ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der #a0 und #a1 Zeichen, durch die richtigen Namen ersetzen.</span><span class="sxs-lookup"><span data-stu-id="465df-120">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="465df-121">Beispielsweise fügt dieser Befehlssatz Opal Castillo (Benutzername opalc) die Liste der Websitesammlungsadministratoren für die ContosoTest-Websitesammlung in der Contoso1-Mandantschaft hinzu:</span><span class="sxs-lookup"><span data-stu-id="465df-121">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="465df-122">Sie können diese Befehle Kopieren und in Editor einfügen, die Variablenwerte für $Tenant, $Site und $User auf Istwerte aus Ihrer Umgebung ändern und diese dann in das SharePoint Online Verwaltungsshell-Fenster einfügen, um Sie auszuführen.</span><span class="sxs-lookup"><span data-stu-id="465df-122">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-groups"></a><span data-ttu-id="465df-123">Hinzufügen eines Benutzers zu anderen Website Sammlungsgruppen</span><span class="sxs-lookup"><span data-stu-id="465df-123">Add a user to other site collection groups</span></span>

<span data-ttu-id="465df-124">In dieser Aufgabe verwenden wir den **Add-Ehepartner-** Befehl, um einer SharePoint-Gruppe in einer Websitesammlung einen Benutzer hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="465df-124">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="465df-125">Lassen Sie uns beispielsweise Glen weit verbreitet (Benutzername glenr) der Gruppe "Auditors" in der ContosoTest-Websitesammlung in der Contoso1-Mandantschaft hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="465df-125">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="465df-126">Erstellen einer Website Sammlungs Gruppe</span><span class="sxs-lookup"><span data-stu-id="465df-126">Create a site collection group</span></span>

<span data-ttu-id="465df-127">Verwenden Sie den Befehl **New-SPOSiteGroup** , um eine neue SharePoint-Gruppe zu erstellen und Sie der ContosoTest-Websitesammlung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="465df-127">You use the **New-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="465df-128">Gruppeneigenschaften wie Berechtigungsstufen können später mithilfe des Cmdlets " **SPOSiteGroup** " aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="465df-128">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="465df-129">Lassen Sie uns beispielsweise die Gruppe "Auditors" mit Berechtigungen "nur anzeigen" für die Contoso-Test Websitesammlung in der Contoso1-Mandantschaft hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="465df-129">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="465df-130">Entfernen von Benutzern aus einer Gruppe</span><span class="sxs-lookup"><span data-stu-id="465df-130">Remove users from a group</span></span>

<span data-ttu-id="465df-131">Manchmal müssen Sie einen Benutzer aus einer Website oder sogar aus allen Websites entfernen.</span><span class="sxs-lookup"><span data-stu-id="465df-131">Sometimes you have to remove a user from a site or even all sites.</span></span> <span data-ttu-id="465df-132">Vielleicht bewegt sich der Mitarbeiter von einer Abteilung in eine andere oder verlässt das Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="465df-132">Perhaps the employee moves from one division to another or leaves the company.</span></span> <span data-ttu-id="465df-133">Sie können dies für einen Mitarbeiter problemlos in der Benutzeroberfläche durchführen, dies ist jedoch nicht leicht möglich, wenn Sie eine vollständige Abteilung von einer Website zu einer anderen migrieren müssen.</span><span class="sxs-lookup"><span data-stu-id="465df-133">You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="465df-134">Durch die Verwendung der SharePoint Online-Verwaltungsshell und CSV-Dateien ist dies jedoch schnell und einfach.</span><span class="sxs-lookup"><span data-stu-id="465df-134">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="465df-135">In dieser Aufgabe verwenden Sie Windows PowerShell, um einen Benutzer aus einer Sicherheitsgruppe für Websitesammlungen zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="465df-135">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="465df-136">Anschließend verwenden Sie eine CSV-Datei und entfernen viele Benutzer aus unterschiedlichen Websites.</span><span class="sxs-lookup"><span data-stu-id="465df-136">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="465df-137">Wir verwenden den Befehl **Remove-ehegatter** , um einen einzelnen Office 365-Benutzer aus einer Website Sammlungs Gruppe zu entfernen, damit die Befehlssyntax angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="465df-137">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="465df-138">Hier sehen Sie, wie die Syntax aussieht:</span><span class="sxs-lookup"><span data-stu-id="465df-138">Here is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="465df-139">Lassen Sie uns beispielsweise Bobby Overby aus der Gruppe "Website Sammlungs Prüfer" in der Contoso-Test Websitesammlung in der Contoso1-Mandantschaft entfernen:</span><span class="sxs-lookup"><span data-stu-id="465df-139">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="465df-140">Angenommen, wir wollten Bobby aus allen Gruppen entfernen, in denen er sich gerade befindet.</span><span class="sxs-lookup"><span data-stu-id="465df-140">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="465df-141">Hier ist die Vorgehensweise:</span><span class="sxs-lookup"><span data-stu-id="465df-141">Here is how we would do that:</span></span>

```powershell
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="465df-142">Dies ist nur ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="465df-142">This is just an example.</span></span> <span data-ttu-id="465df-143">Sie sollten diesen Befehl nicht ausführen, es sei denn, Sie müssen wirklich einen Benutzer aus jeder Gruppe entfernen, beispielsweise wenn der Benutzer das Unternehmen verlässt.</span><span class="sxs-lookup"><span data-stu-id="465df-143">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="465df-144">Automatisieren der Verwaltung umfangreicher Listen von Benutzern und Gruppen</span><span class="sxs-lookup"><span data-stu-id="465df-144">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="465df-145">Wenn Sie eine große Anzahl von Konten zu SharePoint-Websites hinzufügen und Ihnen Berechtigungen erteilen möchten, können Sie das Microsoft 365 Admin Center, einzelne PowerShell-Befehle oder PowerShell als CSV-Datei verwenden.</span><span class="sxs-lookup"><span data-stu-id="465df-145">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="465df-146">Von diesen Optionen ist die CSV-Datei die schnellste Möglichkeit, diese Aufgabe zu automatisieren.</span><span class="sxs-lookup"><span data-stu-id="465df-146">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="465df-147">Der grundlegende Prozess besteht darin, eine CSV-Datei mit Kopfzeilen (Spalten) zu erstellen, die den Parametern entspricht, die das Windows PowerShell Skript benötigt.</span><span class="sxs-lookup"><span data-stu-id="465df-147">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="465df-148">Sie können eine solche Liste ganz einfach in Excel erstellen und dann als CSV-Datei exportieren.</span><span class="sxs-lookup"><span data-stu-id="465df-148">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="465df-149">Anschließend verwenden Sie ein Windows PowerShelles Skript zum Durchlaufen von Datensätzen (Zeilen) in der CSV-Datei und zum Hinzufügen der Benutzer zu Gruppen und den Gruppen zu Websites.</span><span class="sxs-lookup"><span data-stu-id="465df-149">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="465df-150">Erstellen wir beispielsweise eine CSV-Datei zum Definieren einer Gruppe von Websitesammlungen, Gruppen und Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="465df-150">For example, let’s create a CSV file to define a group of site collections, groups, and permissions.</span></span> <span data-ttu-id="465df-151">Als Nächstes erstellen wir eine CSV-Datei, mit der die Gruppen mit Benutzern aufgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="465df-151">Next, we will create a CSV file to populate the groups with users.</span></span> <span data-ttu-id="465df-152">Schließlich erstellen und führen wir ein einfaches Windows PowerShell-Skript aus, mit dem die Gruppen erstellt und aufgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="465df-152">Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="465df-153">In der ersten CSV-Datei wird mindestens eine Gruppe zu einer oder mehreren Websitesammlungen hinzugefügt und diese Struktur erhalten:</span><span class="sxs-lookup"><span data-stu-id="465df-153">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="465df-154">Header</span><span class="sxs-lookup"><span data-stu-id="465df-154">Header:</span></span>

```powershell
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="465df-155">Element</span><span class="sxs-lookup"><span data-stu-id="465df-155">Item:</span></span>

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="465df-156">Hier ist eine Beispieldatei:</span><span class="sxs-lookup"><span data-stu-id="465df-156">Here is an example file:</span></span>

```powershell
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

<span data-ttu-id="465df-157">Die zweite CSV-Datei fügt einer oder mehreren Gruppen einen oder mehrere Benutzer hinzu und weist diese Struktur auf:</span><span class="sxs-lookup"><span data-stu-id="465df-157">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="465df-158">Header</span><span class="sxs-lookup"><span data-stu-id="465df-158">Header:</span></span>

```powershell
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="465df-159">Element</span><span class="sxs-lookup"><span data-stu-id="465df-159">Item:</span></span>

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="465df-160">Hier ist eine Beispieldatei:</span><span class="sxs-lookup"><span data-stu-id="465df-160">Here is an example file:</span></span>

```powershell
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

<span data-ttu-id="465df-161">Für den nächsten Schritt müssen Sie die beiden CSV-Dateien auf Ihrem Laufwerk gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="465df-161">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="465df-162">Im folgenden finden Sie Beispielbefehle, die sowohl CSV-Dateien verwenden als auch Berechtigungen und Gruppenmitgliedschaften hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="465df-162">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="465df-163">Das Skript importiert den Inhalt der CSV-Datei und verwendet die Werte in den Spalten, um die Parameter der Befehle **New-SPOSiteGroup** und **Add-ehegatter** aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="465df-163">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="465df-164">In unserem Beispiel speichern wir diese in theO365Admin Ordner auf Laufwerk C, aber Sie können Sie speichern, wo immer Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="465df-164">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="465df-165">Nun können wir eine Gruppe von Personen für mehrere Gruppen in verschiedenen Websites mit derselben CSV-Datei entfernen.</span><span class="sxs-lookup"><span data-stu-id="465df-165">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="465df-166">Nachfolgend sehen Sie einen Beispielbefehl:</span><span class="sxs-lookup"><span data-stu-id="465df-166">Here is an example command:</span></span>

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="465df-167">Generieren von Benutzer berichten</span><span class="sxs-lookup"><span data-stu-id="465df-167">Generate user reports</span></span>

<span data-ttu-id="465df-168">Möglicherweise möchten Sie einen einfachen Bericht für einige Websites erhalten und die Benutzer für diese Websites, ihre Berechtigungsstufe und andere Eigenschaften anzeigen.</span><span class="sxs-lookup"><span data-stu-id="465df-168">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties.</span></span> <span data-ttu-id="465df-169">So sieht die Syntax aus:</span><span class="sxs-lookup"><span data-stu-id="465df-169">This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="465df-170">Dadurch werden die Daten für diese drei Standorte erfasst und in eine Textdatei auf Ihrem lokalen Laufwerk geschrieben.</span><span class="sxs-lookup"><span data-stu-id="465df-170">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="465df-171">Beachten Sie, dass mit dem Parameter – Append neue Inhalte zu einer vorhandenen Datei hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="465df-171">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="465df-172">Lassen Sie uns beispielsweise einen Bericht über die ContosoTest-, TeamSite01-und Project01-Websites für den Contoso1-Mandanten ausführen:</span><span class="sxs-lookup"><span data-stu-id="465df-172">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="465df-173">Beachten Sie, dass nur die **$Site** Variable geändert werden musste.</span><span class="sxs-lookup"><span data-stu-id="465df-173">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="465df-174">Die **$Tenant** -Variable behält ihren Wert über alle drei Ausführungen des Befehls bei.</span><span class="sxs-lookup"><span data-stu-id="465df-174">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="465df-175">Was jedoch, wenn Sie dies für jede Website tun wollten?</span><span class="sxs-lookup"><span data-stu-id="465df-175">However, what if you wanted to do this for every site?</span></span> <span data-ttu-id="465df-176">Sie können dies tun, ohne alle diese Websites mithilfe dieses Befehls eingeben zu müssen:</span><span class="sxs-lookup"><span data-stu-id="465df-176">You can do this without having to type all those websites by using this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="465df-177">Dieser Bericht ist ziemlich einfach, und Sie können weitere Code hinzufügen, um spezifischere Berichte oder Berichte zu erstellen, die detailliertere Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="465df-177">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="465df-178">Dies sollte Ihnen jedoch eine Vorstellung davon geben, wie Sie die SharePoint Online-Verwaltungsshell zum Verwalten von Benutzern in der SharePoint Online Umgebung verwenden.</span><span class="sxs-lookup"><span data-stu-id="465df-178">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="465df-179">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="465df-179">See also</span></span>

[<span data-ttu-id="465df-180">Herstellen einer Verbindung mit SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="465df-180">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="465df-181">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="465df-181">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="465df-182">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="465df-182">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="465df-183">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="465df-183">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

