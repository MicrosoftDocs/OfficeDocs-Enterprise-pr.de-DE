---
title: Hinzufügen oder Entfernen eines Geo-Administrators
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informationen Sie zum Hinzufügen oder Entfernen von Geo-Administrator in OneDrive for Business Multi-Geo.
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849811"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="a246e-103">Hinzufügen oder Entfernen von ein Administrator Geo in OneDrive für Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a246e-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="a246e-p101">Sie können verschiedene Administratoren für jeden Standort Geo konfigurieren, die Ihnen in Ihrem Mandanten. Diese Administratoren haben Zugriff auf die SharePoint Online und OneDrive-Einstellungen, die an ihre Position Geo spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="a246e-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="a246e-p102">Einige Dienste - wie der Laufzeitspeicher - werden vom zentralen Speicherort verwaltet und auf Satelliten Speicherorte repliziert. Der Administrator Geo für den zentralen Standort hat Zugriff auf diese, während Geo-Admins für Satelliten Speicherorte nicht.</span><span class="sxs-lookup"><span data-stu-id="a246e-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="a246e-108">Globale Administratoren und SharePoint Online-Administratoren weiterhin auf Einstellungen in der zentralen Standort und alle Satelliten Speicherorte zugreifen.</span><span class="sxs-lookup"><span data-stu-id="a246e-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="a246e-109">Konfigurieren von Geo-Administratoren</span><span class="sxs-lookup"><span data-stu-id="a246e-109">Configuring geo administrators</span></span>

<span data-ttu-id="a246e-110">Konfigurieren von Geo-Admins ist SharePoint Online-PowerShell-Modul erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a246e-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="a246e-111">Verwenden Sie die [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) für die Verbindung der Verwaltungskonsole des Speicherorts Geo, wo Sie den Geo-Administrator hinzufügen möchten (Z. B. Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="a246e-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="a246e-112">Führen Sie zum Anzeigen der vorhandenen Geo-Admins eines Standorts`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="a246e-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="a246e-113">Hinzufügen eines Benutzers als ein Geo-Administrator</span><span class="sxs-lookup"><span data-stu-id="a246e-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="a246e-114">Führen Sie zum Hinzufügen eines Benutzers als eine Geo-admin`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="a246e-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="a246e-115">Führen Sie zum Entfernen eines Benutzers als eine Geo Admin eines Standorts`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="a246e-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="a246e-116">Hinzufügen einer Gruppe als eine Geo-admin</span><span class="sxs-lookup"><span data-stu-id="a246e-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="a246e-117">Sie können eine Sicherheitsgruppe oder eine e-Mail-aktivierte Sicherheitsgruppe als eine Geo-Portals hinzufügen. (Verteilergruppen und Office 365-Gruppen werden nicht unterstützt.)</span><span class="sxs-lookup"><span data-stu-id="a246e-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="a246e-118">Führen Sie zum Hinzufügen einer Gruppe als Geo-administrator`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="a246e-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="a246e-119">Führen Sie zum Entfernen einer Gruppe als Geo-administrator`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="a246e-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="a246e-p103">Beachten Sie, dass nicht alle Sicherheitsgruppen einen Gruppen-Alias verfügen. Wenn Sie eine Sicherheitsgruppe hinzu, die nicht über einen Alias, und führen Sie [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) zum Abrufen einer Liste von Gruppen verfügt möchten, suchen Sie nach der Sicherheitsgruppe ObjectID, und führen Sie:</span><span class="sxs-lookup"><span data-stu-id="a246e-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="a246e-122">Führen Sie zum Entfernen einer Gruppe mithilfe der ObjectID`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="a246e-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="a246e-123">Zugreifen auf das Administrationscenter für einen bestimmten Geo-Speicherort</span><span class="sxs-lookup"><span data-stu-id="a246e-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="a246e-124">Zum Verwalten von OneDrive-Einstellungen für ihre Geo-Speicherort müssen Administratoren die OneDrive-Verwaltungskonsole direkt mit der folgenden URL-Format zugreifen:</span><span class="sxs-lookup"><span data-stu-id="a246e-124">To administer OneDrive settings for their geo location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="a246e-125">https://admin.onedrive.com/?geo=<*Geo*></span><span class="sxs-lookup"><span data-stu-id="a246e-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="a246e-126">Beispielsweise ist der OneDrive-Verwaltungskonsole für Kanada finden Sie unter: https://admin.onedrive.com/?geo=CAN.</span><span class="sxs-lookup"><span data-stu-id="a246e-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="a246e-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a246e-127">See Also</span></span>

[<span data-ttu-id="a246e-128">Hinzufügen von SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="a246e-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="a246e-129">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="a246e-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="a246e-130">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="a246e-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="a246e-131">Legen Sie einen Alias (MailNickName) für eine Sicherheitsgruppe</span><span class="sxs-lookup"><span data-stu-id="a246e-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)