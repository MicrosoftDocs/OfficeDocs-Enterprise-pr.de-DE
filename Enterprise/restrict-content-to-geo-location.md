---
title: Inhalte für einen geografischen Standort einschränken
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Erfahren Sie, wie Sie SharePoint-Seiten für einen bestimmten geographischen Standort in einer Multi-Geo-Umgebung einschränken.
ms.openlocfilehash: 42c382abd254afcf74dd6bdd15e4c69f65b64f85
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070991"
---
# <a name="restrict-content-to-a-geo-location"></a><span data-ttu-id="df88f-103">Inhalte für einen geografischen Standort einschränken</span><span class="sxs-lookup"><span data-stu-id="df88f-103">Restrict content to a geo location</span></span>

<span data-ttu-id="df88f-104">Unter bestimmten Umständen können Sie möglicherweise erzwingen, dass eine Seite und Ihre Inhalte an dem geographischen Standort verbleiben, an dem Sie erstellt wurden. Dies ist möglich, indem Sie entweder die Seite daran hindern, verschoben zu werden, oder indem Sie das Zwischenspeichern der Dateiinhalte der Seite an einem anderen geographischen Standort verhindern.</span><span class="sxs-lookup"><span data-stu-id="df88f-104">Under some circumstances you may choose to enforce a site and its file content to remain in the geo location where the site was created, either by preventing the site from being moved or by preventing the caching of the site's file content in another geo location.</span></span>

<span data-ttu-id="df88f-105">Um dies zu tun, verwenden Sie [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet mit dem Parameter **RestrictedToGeo**.</span><span class="sxs-lookup"><span data-stu-id="df88f-105">You can do this by using the [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet with the **RestrictedToGeo** parameter.</span></span> <span data-ttu-id="df88f-106">Dieser Parameter hat einen Standardwert von NULL, aber Sie können ihn wie folgt ändern:</span><span class="sxs-lookup"><span data-stu-id="df88f-106">This parameter has a default value of NULL, but you can change it to one of the following:</span></span>

|<span data-ttu-id="df88f-107">Einschränkung</span><span class="sxs-lookup"><span data-stu-id="df88f-107">Restriction</span></span>|<span data-ttu-id="df88f-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="df88f-108">Description</span></span>|
|:----------|:----------|
|<span data-ttu-id="df88f-109">NoRestriction</span><span class="sxs-lookup"><span data-stu-id="df88f-109">NoRestriction</span></span>|<span data-ttu-id="df88f-110">Die Website kann an einen anderen Geo-Standort verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="df88f-110">The site can be moved to another geo location.</span></span>|
|<span data-ttu-id="df88f-111">BlockMoveOnly</span><span class="sxs-lookup"><span data-stu-id="df88f-111">BlockMoveOnly</span></span>|<span data-ttu-id="df88f-112">Seite kann nicht an einen anderen Geo-Standort verschoben werden, aber Seiteninhalte können an einem anderen geografischen Standort zwischengespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="df88f-112">Site cannot be moved to another geo location, but site content can be cached in other geo locations.</span></span>|
|<span data-ttu-id="df88f-113">BlockFull</span><span class="sxs-lookup"><span data-stu-id="df88f-113">BlockFull</span></span>|<span data-ttu-id="df88f-114">Seite kann nicht an einen anderen Geo-Standort verschoben werden und der gesamte Seiteninhalt wird nicht an anderen geografischen Standorten zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="df88f-114">Site cannot be moved to another geo location, and full file content is not cached in other geo locations.</span></span> <span data-ttu-id="df88f-115">Der Titel der Datei (aus dem Inhalt abgerufen), der Dateiname und andere Eigenschaften der Datei können weiterhin an anderen geographischen Standorten zwischengespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="df88f-115">Files' title (harvested from the content), file name, and other properties of the file can still be cached in other geo-locations.</span></span><br><span data-ttu-id="df88f-116">Inhalte, die vor der Konfiguration als BlockFull auf der Seite gespeichert wurden, können möglicherweise weiterhin an anderen geographischen Standorten zwischengespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="df88f-116">Content stored in the site before it was configured to BlockFull, may continue to be cached in other geo locations.</span></span>|

<span data-ttu-id="df88f-117">Verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="df88f-117">Use the following syntax:</span></span>

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

<span data-ttu-id="df88f-118">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="df88f-118">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
