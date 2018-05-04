---
title: Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Zusammenfassung: Verwenden von Office 365 PowerShell zum Verwalten von SharePoint Online-Benutzer, Gruppen und Websites.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="3f8f0-103">Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f8f0-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="3f8f0-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Benutzer, Gruppen und Websites.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="3f8f0-105">Wenn Sie eine SharePoint Online sind, funktioniert mit umfangreichen Listen von Benutzerkonten oder-Gruppen und einfacher Verwaltung möchte, können Sie Office 365 PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="3f8f0-106">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-106">Before you begin</span></span>

<span data-ttu-id="3f8f0-p101">Die Verfahren in diesem Thema müssen Sie mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="3f8f0-109">Abrufen einer Liste von Websites, Gruppen und Benutzern</span><span class="sxs-lookup"><span data-stu-id="3f8f0-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="3f8f0-p102">Bevor wir mit der Verwaltung von Benutzern und Gruppen beginnen, müssen Sie Listen Ihrer Websites, Gruppen und Benutzer abrufen. Sie können anhand dieser Informationen dann das Beispiel in diesem Artikel durcharbeiten.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="3f8f0-112">Abrufen einer Liste von Websites ab</span><span class="sxs-lookup"><span data-stu-id="3f8f0-112">Get a list of sites</span></span>

<span data-ttu-id="3f8f0-113">Rufen Sie eine Liste der Websites in Ihrem Mandanten mit dem folgenden Befehl ab:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="3f8f0-114">Abrufen einer Liste von Gruppen</span><span class="sxs-lookup"><span data-stu-id="3f8f0-114">Get a list of groups</span></span>

<span data-ttu-id="3f8f0-115">Rufen Sie eine Liste der Gruppen in Ihrem Mandanten mit dem folgenden Befehl ab:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="3f8f0-116">Abrufen einer Liste von Benutzern</span><span class="sxs-lookup"><span data-stu-id="3f8f0-116">Get a list of users</span></span>

<span data-ttu-id="3f8f0-117">Rufen Sie eine Liste der Benutzer in Ihrem Mandanten mit dem folgenden Befehl ab:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="3f8f0-118">Hinzufügen eines Benutzers zur Gruppe der Websitesammlungsadministratoren</span><span class="sxs-lookup"><span data-stu-id="3f8f0-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="3f8f0-p103">Verwenden Sie den **Set-SPOUser** -Befehl zum Hinzufügen eines Benutzers zur Liste der Websitesammlungs-Administratoren für eine Websitesammlung. Dies ist die Syntax wie sieht:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="3f8f0-121">In diesem Beispiel Variablen verwendet, um Werte zu speichern und Notizen im Skript hat (beispielsweise "<!--This is the Tenant Name…-->") können Sie sehen, was diese Werte werden soll.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="3f8f0-122">Wird beispielsweise dieser Reihe von Befehlen Opal Castillo (User Name Opalc) die Liste der Websitesammlungs-Administratoren für die Websitesammlung ContosoTest des Mandanten contoso1:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="3f8f0-123">Sie können diese Befehle tatsächlich ausschneiden und in Notepad einfügen, die Variablenwerte für $tenant, $site und $user in tatsächliche Werte aus Ihrer Umgebung ändern, und dies dann in Ihr Windows SharePoint Online-Verwaltungsshellfenster einfügen.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="3f8f0-124">Hinzufügen eines Benutzers zu anderen Gruppen von Websitesammlungsadministratoren</span><span class="sxs-lookup"><span data-stu-id="3f8f0-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="3f8f0-p104">Für diese Aufgabe wird den **Add-SPOUser** -Befehl verwendet, um einen Benutzer einer SharePoint-Gruppe für eine Websitesammlung hinzuzufügen. Dies ist die Syntax wie sieht:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="3f8f0-127">Beispielsweise fügen Sie Glen voller (User Name Glenr) der Gruppe Auditoren für die Websitesammlung ContosoTest des Mandanten contoso1:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="3f8f0-128">Erstellen einer Websitesammlungsgruppe</span><span class="sxs-lookup"><span data-stu-id="3f8f0-128">Create a site collection group</span></span>

<span data-ttu-id="3f8f0-p105">Sie verwenden den Befehl **Set-SPOSiteGroup** Erstellen einer neuen SharePoint-Gruppe und für die Websitesammlung ContosoTest hinzufügen. Dies ist die Syntax wie sieht:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> <span data-ttu-id="3f8f0-p106">Sie müssen eine beliebige Zeichenfolge mit Leerzeichen in Anführungszeichen setzen. Gruppe Eigenschaften wie Berechtigungsstufen, können später mit dem **Set-SPOSiteGroup** -Cmdlet aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="3f8f0-133">Beispielsweise wir die Gruppe Auditoren mit Leserechten Berechtigungen für die Websitesammlung Contoso Test des Mandanten contoso1 hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="3f8f0-134">Entfernen von Benutzern aus einer Gruppe</span><span class="sxs-lookup"><span data-stu-id="3f8f0-134">Remove users from a group</span></span>

<span data-ttu-id="3f8f0-p107">Manchmal müssen Sie einen Benutzer aus einer Seite oder sogar aus allen Websites entfernen. Vielleicht wechselt der Mitarbeiter in einen anderen Bereich oder verlässt das Unternehmen. Bei nur einem Mitarbeiter können Sie dazu problemlos die Benutzeroberfläche verwenden. Aber das Ganze ist nicht so leicht, wenn Sie einen ganzen Bereich von einer Website zu einer anderen umziehen müssen.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="3f8f0-p108">Verwenden Sie die SharePoint Online-Verwaltungsshell und CSV-Dateien, ist dies jedoch schnell und einfach. Windows PowerShell verwenden Sie für diese Aufgabe um aus einer Website Auflistung Sicherheitsgruppe einen Benutzer zu entfernen. Sie können eine CSV-Datei verwenden, und Entfernen von vielen Benutzern von verschiedenen Standorten.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="3f8f0-p109">Wir können den Befehl **Remove-SPOUser** verwenden, um einen einzelnen Office 365-Benutzer aus einer Websitegruppe-Auflistung entfernen, damit wir die Befehlssyntax sehen können. Hier wird die Syntax wie sieht:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

<span data-ttu-id="3f8f0-143">Beispielsweise sollen Bobby Overby aus der Gruppe der Prüfer in der Contoso Test-Websitesammlung in der contoso1-Instanz entfernt:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="3f8f0-p110">Angenommen, wir möchten Bobby aus allen Gruppen entfernen, in denen er derzeit Mitglied ist. Wir würden dazu folgendermaßen vorgehen:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="3f8f0-p111">Hiermit wird nur gezeigt, wie Sie dies tun. Sie sollten diesen Befehl nur ausführen, wenn Sie einen Benutzer wirklich aus allen Gruppen entfernen müssen, z. B. wenn der Benutzer das Unternehmen verlässt.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="3f8f0-148">Automatisieren der Verwaltung umfangreicher Listen mit Benutzern und Gruppen</span><span class="sxs-lookup"><span data-stu-id="3f8f0-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="3f8f0-p112">Sie können eine große Anzahl von Konten zu SharePoint-Websites hinzufügen, und erteilen sie Berechtigungen, die Office 365 Administrationscenter, einzelne PowerShell-Befehle oder PowerShell verwenden eine CSV-Datei. Mit diesen Optionen wird die CSV-Datei die schnellste Möglichkeit, diese Aufgabe automatisieren.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="3f8f0-p113">Die grundlegende Vorgehensweise ist eine CSV-Datei erstellen, die Kopfzeilen (Spalten) verfügt, die die Parameter entsprechen, die das Windows PowerShell-Skript muss. Sie können auf einfache Weise eine solche Liste in Excel erstellen und anschließend als eine CSV-Datei zu exportieren. Klicken Sie dann, verwenden Sie ein Windows PowerShell-Skript durchlaufen Datensätze (Zeilen) in der CSV-Datei hinzufügen von Benutzern zu Gruppen auf Websites und Gruppen.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="3f8f0-p114">Erstellen wir als Beispiel eine CSV-Datei, um eine Gruppe von Websitesammlungen, Gruppen und Berechtigungen zu definieren. Als Nächstes erstellen wir eine CSV-Datei, um die Gruppen mit Benutzern aufzufüllen. Anschließend erstellen wir ein einfaches Windows PowerShell-Skript, das die Gruppen erstellt und auffüllt, und führen es aus.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="3f8f0-157">Die erste CSV-Datei fügt einer oder mehreren Websitesammlungen eine oder mehrere Gruppen hinzu und weist diese Struktur auf:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="3f8f0-158">Kopfzeile:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="3f8f0-159">Artikel:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="3f8f0-160">Es folgt eine Beispieldatei:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-160">Here is an example file:</span></span>

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

<span data-ttu-id="3f8f0-161">Die zweite CSV-Datei fügt einer oder mehreren Gruppen einen oder mehrere Benutzer hinzu und weist diese Struktur auf:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="3f8f0-162">Kopfzeile:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="3f8f0-163">Artikel:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="3f8f0-164">Es folgt eine Beispieldatei:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-164">Here is an example file:</span></span>

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

<span data-ttu-id="3f8f0-p115">Im nächsten Schritt müssen Sie die beiden CSV-Dateien auf Ihrem Laufwerk speichern. Hier sind die Befehle, die beide CSV-Dateien verwenden und Berechtigungen und Gruppenmitgliedschaft hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="3f8f0-p116">Das Skript den Inhalt der CSV-Datei importiert, und die Werte in den Spalten (in Fettschrift) verwendet, um die Parameter der Befehle **New-SPOSiteGroup** und **Add-SPOUser** auffüllen. In unserem Beispiel werden wir dies auf Laufwerk C gespeichert, jedoch können Sie es speichern, wo Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="3f8f0-p117">Als nächsten Schritt entfernen wir mehrere Personen, die sich in verschiedenen Gruppen in unterschiedlichen Websites befinden, mithilfe derselben CSV-Datei. Hier ist der Befehl:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="3f8f0-171">Erstellen von Benutzerberichten</span><span class="sxs-lookup"><span data-stu-id="3f8f0-171">Generate user reports</span></span>

<span data-ttu-id="3f8f0-p118">Sie möchten vielleicht einen einfachen Bericht für einige Websites erstellen und die Benutzer für diese Websites, deren Berechtigungsebene und weitere Eigenschaften anzeigen. So sieht die Syntax aus:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="3f8f0-p119">Dadurch wird Code die Daten für diese drei Standorte und in einer Textdatei auf dem lokalen Laufwerk zu schreiben. Beachten Sie, dass der Parameter – Append werden neue Inhalte zu einer vorhandenen Datei hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="3f8f0-176">Angenommen, wir führen einen Bericht auf den Websites ContosoTest, TeamSite01 und Project01 für den Mandanten „Contoso 1“ aus.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="3f8f0-p120">Beachten Sie, dass wir hatten, nur die **$site** -Variable zu ändern. Die Variable **$tenant** hält seinen Wert über alle drei Textläufe des Befehls.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="3f8f0-p121">Was wäre, wenn Sie den Bericht für jede Website erstellen wollen würden? Sie müssen dazu nicht alle diese Website eingeben, sondern können diesen Befehl verwenden:</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="3f8f0-p122">In diesem Bericht ist relativ einfach, und Sie können weitere Code zum Erstellen von genauere Berichte oder Berichte, die enthalten ausführlichere Informationen hinzufügen. Aber diese Weise erhalten Sie eine Vorstellung vom Zweck der Verwendung von SharePoint Online-Verwaltungsshell zum Verwalten von Benutzern in der SharePoint Online-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="3f8f0-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="3f8f0-183">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3f8f0-183">See also</span></span>

[<span data-ttu-id="3f8f0-184">Verbinden Sie mit SharePoint Online-PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f8f0-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="3f8f0-185">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f8f0-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="3f8f0-186">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f8f0-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3f8f0-187">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f8f0-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

