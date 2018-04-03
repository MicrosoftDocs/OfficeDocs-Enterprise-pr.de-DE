---
title: Hinzufügen oder Entfernen einer Geo-Administrators
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informationen Sie zum Hinzufügen oder Entfernen von Geo-Administrator in OneDrive for Business Multi-Geo.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="eae5f-103">Hinzufügen oder Entfernen von ein Administrator Geo in OneDrive für Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="eae5f-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="eae5f-p101">Sie können verschiedene Administratoren für jeden Standort Geo konfigurieren, die Ihnen in Ihrem Mandanten. Diese Administratoren haben Zugriff auf die SharePoint Online und OneDrive-Einstellungen, die an ihre Geo-Position spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="eae5f-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="eae5f-p102">Einige Dienste - wie der Laufzeitspeicher - werden vom zentralen Speicherort verwaltet und auf Satelliten Speicherorte repliziert. Der Administrator Geo für den zentralen Standort hat Zugriff auf diese, während Geo-Admins für Satelliten Speicherorte nicht.</span><span class="sxs-lookup"><span data-stu-id="eae5f-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="eae5f-108">Globale Administratoren und SharePoint Online-Administratoren weiterhin an allen Speicherorten von Geo auf Einstellungen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="eae5f-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="eae5f-109">Konfigurieren von Geo-Administratoren</span><span class="sxs-lookup"><span data-stu-id="eae5f-109">Configuring geo administrators</span></span>

<span data-ttu-id="eae5f-110">Konfigurieren von Geo-Admins ist SharePoint Online-PowerShell-Modul erforderlich.</span><span class="sxs-lookup"><span data-stu-id="eae5f-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="eae5f-111">Verwenden Sie die [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) für die Verbindung der Verwaltungskonsole des Speicherorts Geo, wo Sie den Geo-Administrator hinzufügen möchten (Z. B. Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="eae5f-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="eae5f-112">Führen Sie zum Hinzufügen eines Benutzers als eine Geo-admin`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="eae5f-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="eae5f-113">Führen Sie zum Anzeigen der vorhandenen Geo-Admins eines Standorts`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="eae5f-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="eae5f-114">Führen Sie zum Entfernen eines Benutzers als eine Geo Admin eines Standorts`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="eae5f-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="eae5f-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="eae5f-115">See Also</span></span>

[<span data-ttu-id="eae5f-116">Hinzufügen von SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="eae5f-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="eae5f-117">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="eae5f-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="eae5f-118">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="eae5f-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)