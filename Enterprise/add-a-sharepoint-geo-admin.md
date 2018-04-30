---
title: Hinzufügen oder Entfernen einer Geo-Administrators
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informationen Sie zum Hinzufügen oder Entfernen von Geo-Administrator in OneDrive for Business Multi-Geo.
ms.openlocfilehash: 7630597654df9ad78619b94fedc9e18d5b0b721e
ms.sourcegitcommit: 886b23f590f6187f7a98c1083a3b49359ec2a5c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="fe273-103">Hinzufügen oder Entfernen von ein Administrator Geo in OneDrive für Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="fe273-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="fe273-p101">Sie können verschiedene Administratoren für jeden Standort Geo konfigurieren, die Ihnen in Ihrem Mandanten. Diese Administratoren haben Zugriff auf die SharePoint Online und OneDrive-Einstellungen, die an ihre Geo-Position spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="fe273-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="fe273-p102">Einige Dienste - wie der Laufzeitspeicher - werden vom zentralen Speicherort verwaltet und auf Satelliten Speicherorte repliziert. Der Administrator Geo für den zentralen Standort hat Zugriff auf diese, während Geo-Admins für Satelliten Speicherorte nicht.</span><span class="sxs-lookup"><span data-stu-id="fe273-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="fe273-108">Globale Administratoren und SharePoint Online-Administratoren weiterhin an allen Speicherorten von Geo auf Einstellungen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="fe273-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="fe273-109">Konfigurieren von Geo-Administratoren</span><span class="sxs-lookup"><span data-stu-id="fe273-109">Configuring geo administrators</span></span>

<span data-ttu-id="fe273-110">Konfigurieren von Geo-Admins ist SharePoint Online-PowerShell-Modul erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fe273-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="fe273-111">Verwenden Sie die [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) für die Verbindung der Verwaltungskonsole des Speicherorts Geo, wo Sie den Geo-Administrator hinzufügen möchten (Z. B. Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="fe273-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="fe273-112">Führen Sie zum Anzeigen der vorhandenen Geo-Admins eines Standorts`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="fe273-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="fe273-113">Hinzufügen eines Benutzers als ein Geo-Administrator</span><span class="sxs-lookup"><span data-stu-id="fe273-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="fe273-114">Führen Sie zum Hinzufügen eines Benutzers als eine Geo-admin`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="fe273-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="fe273-115">Führen Sie zum Entfernen eines Benutzers als eine Geo Admin eines Standorts`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="fe273-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="fe273-116">Hinzufügen einer Gruppe als eine Geo-admin</span><span class="sxs-lookup"><span data-stu-id="fe273-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="fe273-117">Sie können eine Sicherheitsgruppe oder eine e-Mail-aktivierte Sicherheitsgruppe als eine Geo-Portals hinzufügen. (Verteilergruppen und Office 365-Gruppen werden nicht unterstützt.)</span><span class="sxs-lookup"><span data-stu-id="fe273-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="fe273-118">Führen Sie zum Hinzufügen einer Gruppe als eine Geo-admin`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="fe273-118">To add a group as a geo admin, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="fe273-119">Führen Sie zum Entfernen einer Gruppe als eine Geo-admin`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="fe273-119">To remove a group as a geo admin, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="fe273-p103">Beachten Sie, dass nicht alle Sicherheitsgruppen einen Gruppen-Alias verfügen. Wenn Sie eine Sicherheitsgruppe hinzu, die nicht über einen Alias, und führen Sie [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) zum Abrufen einer Liste von Gruppen verfügt möchten, suchen Sie nach der Sicherheitsgruppe ObjectID, und führen Sie:</span><span class="sxs-lookup"><span data-stu-id="fe273-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="fe273-122">Führen Sie zum Entfernen einer Gruppe mithilfe der ObjectID`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="fe273-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="fe273-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fe273-123">See Also</span></span>

[<span data-ttu-id="fe273-124">Hinzufügen von SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="fe273-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="fe273-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="fe273-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="fe273-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="fe273-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="fe273-127">Legen Sie einen Alias (MailNickName) für eine Sicherheitsgruppe</span><span class="sxs-lookup"><span data-stu-id="fe273-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)