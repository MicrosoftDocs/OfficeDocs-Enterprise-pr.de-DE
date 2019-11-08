---
title: Hinzufügen oder Entfernen eines Geo-Administrators
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: So fügen Sie eine Geo-Administrator in Office 365 Multi-Geo hinzu oder entfernen ihn.
ms.openlocfilehash: d10340b7fe42016710ec953f5b45110e9ea8b901
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030569"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a><span data-ttu-id="22321-103">Fügen Sie einen Geo-Administrator in Office 365 Multi-Geo hinzu oder entfernen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="22321-103">Add or remove a geo administrator in Office 365 Multi-Geo</span></span>

<span data-ttu-id="22321-104">Sie können für jeden geographischen Standort in Ihrem Mandanten einen eigenen Administrator festlegen.</span><span class="sxs-lookup"><span data-stu-id="22321-104">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="22321-105">Dieser Administrator hat Zugriff auf SharePoint Online- und OneDrive-Einstellungen, die für seinen geographischen Standort gelten.</span><span class="sxs-lookup"><span data-stu-id="22321-105">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="22321-106">Einige Dienste – wie Terminologiespeicher – werden an einem zentralen Standort verwaltet und an Satellitenstandorten repliziert.</span><span class="sxs-lookup"><span data-stu-id="22321-106">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="22321-107">Der Geo-Administrator des zentralen Standorts hat Zugriff auf diese, was für Administratoren von Satellitenstandorten nicht gilt.</span><span class="sxs-lookup"><span data-stu-id="22321-107">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="22321-108">Globale Administratoren und SharePoint-Onlineadministratoren haben weiterhin Zugriff auf Einstellungen am zentralen Standort und allen Satellitenstandorten.</span><span class="sxs-lookup"><span data-stu-id="22321-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="22321-109">Konfigurieren von Geo-Administratoren</span><span class="sxs-lookup"><span data-stu-id="22321-109">Configuring geo administrators</span></span>

<span data-ttu-id="22321-110">Für das Konfigurieren von Geo-Administratoren ist das SharePoint Online-PowerShell-Modul erforderlich.</span><span class="sxs-lookup"><span data-stu-id="22321-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="22321-111">Verwenden Sie [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService), um eine Verbindung zum Administrationscenter des geographischen Standorts herzustellen, an dem Sie den Geo-Administrator hinzufügen möchten (zum Beispiel Connect-SPOService https://ContosoEUR-admin.sharepoint.com.))</span><span class="sxs-lookup"><span data-stu-id="22321-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="22321-112">Führen Sie `Get-SPOGeoAdministrator` aus, um die vorhandenen Geo-Administratoren eines Standorts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="22321-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="22321-113">Einen Benutzer als Geo-Administrator hinzufügen</span><span class="sxs-lookup"><span data-stu-id="22321-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="22321-114">Führen Sie `Add-SPOGeoAdministrator -UserPrincipalName <UPN>` aus, um einen Benutzer als Geo-Administrator hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="22321-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="22321-115">Führen Sie `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>` aus, um einen Benutzer als Geo-Administrator zu entfernen</span><span class="sxs-lookup"><span data-stu-id="22321-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="22321-116">Eine Gruppe als Geo-Administrator hinzufügen</span><span class="sxs-lookup"><span data-stu-id="22321-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="22321-117">Sie können eine Sicherheitsgruppe oder eine E-Mail-aktivierte Sicherheitsgruppeals Geo-Administrator hinzufügen. (Verteilergruppen und Office 365-Gruppen werden nicht unterstützt.)</span><span class="sxs-lookup"><span data-stu-id="22321-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="22321-118">Führen Sie `Add-SPOGeoAdministrator -GroupAlias <alias>` aus, um eine Gruppe als Geo-Administrator hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="22321-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="22321-119">Führen Sie `Remove-SPOGeoAdministrator -GroupAlias <alias>` aus, um eine Gruppe als Geo-Administrator zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="22321-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="22321-120">Beachten Sie, dass nicht alle Sicherheitsgruppen einen Gruppenalias besitzen.</span><span class="sxs-lookup"><span data-stu-id="22321-120">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="22321-121">Wenn Sie eine Sicherheitsgruppe hinzufügen möchten, die keinen Alias besitzt, führen Sie [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) aus, um eine Liste der Gruppen anzurufen. Suchen Sie nach der ObjectID Ihrer Sicherheitsgruppe Sie dann Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="22321-121">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="22321-122">Führen Sie `Remove-SPOGeoAdministrator -ObjectID <ObjectID>` aus, um eine Gruppe anhand der ObjectID zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="22321-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="22321-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="22321-123">See Also</span></span>

[<span data-ttu-id="22321-124">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="22321-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="22321-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="22321-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="22321-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="22321-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="22321-127">Legen Sie einen Alias ("MailNickName") für eine Sicherheitsgruppe fest</span><span class="sxs-lookup"><span data-stu-id="22321-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)