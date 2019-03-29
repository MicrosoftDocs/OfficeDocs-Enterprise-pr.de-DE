---
title: Office 365 Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Erweitern Sie Ihre Office 365-Präsenz auf mehrere geografische Regionen mit Office 365 Multi-Geo.
ms.openlocfilehash: e216f61806ea5d648519ac7217acf7dbaddd1419
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934006"
---
# <a name="office-365-multi-geo"></a><span data-ttu-id="a031b-103">Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a031b-103">Video: Introducing Office 365 Multi-Geo</span></span>

<span data-ttu-id="a031b-104">Mit Office 365 Multi-Geo kann Ihr Unternehmen seine Office 365-Präsenz auf mehrere geografische Regionen und/oder Länder innerhalb des vorhandenen Mandanten erweitern.</span><span class="sxs-lookup"><span data-stu-id="a031b-104">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="a031b-105">Wenden Sie sich an Ihr Microsoft-Kontoteam, um Ihr multinationales Unternehmen für Office 365 Multi-Geo anzumelden.</span><span class="sxs-lookup"><span data-stu-id="a031b-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="a031b-106">Mit Office 365 Multi-Geo können Sie ruhende Daten an den Datenresistenz-Anforderungen entsprechenden geografischen Speicherorten bereitstellen und speichern und gleichzeitig die globale Bereitstellung moderner Produktivitätserfahrungen für Ihre Mitarbeiter in Gang setzen.</span><span class="sxs-lookup"><span data-stu-id="a031b-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="a031b-107">Video: Einführung in Multi-Geo in Office 365</span><span class="sxs-lookup"><span data-stu-id="a031b-107">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="a031b-108">In einer Multi-Geo-Umgebung verfügt Ihr Office 365-Mandant über einen zentralen Standort (an dem Ihr Office 365-Abonnement ursprünglich bereitgestellt wurde) und über einen oder mehrere Satellitenstandort(e).</span><span class="sxs-lookup"><span data-stu-id="a031b-108">In a Multi-Geo environment, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="a031b-109">Die Informationen über geografische Standorte, Gruppen und Benutzer eines Multi-Geo-Mandanten werden in Azure Active Directory (AAD) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="a031b-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="a031b-110">Da Ihre Mandanteninformationen zentral verwaltet und an jedem geografischen Speicherort synchronisiert werden, wird das globale Bewusstsein durch das Teilen von Informationen und Erfahrungen im gesamten Unternehmen erhöht.</span><span class="sxs-lookup"><span data-stu-id="a031b-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![Screenshot der Multi-Geo-Zuordnung aus der SharePoint-Admin Center](media/multi-geo-world-map.png)

<span data-ttu-id="a031b-112">Beachten Sie, dass Office 365 Multi-Geo nicht in erster Linie zur Leistungsoptimierung entwickelt wurde, sondern zur Einhaltung von Datenaufbewahrungsrichtlinien.</span><span class="sxs-lookup"><span data-stu-id="a031b-112">Note that Office 365 Multi-Geo is not designed for performance optimization cases, it is designed to meet data residency requirements. For information about performance optimization for Office 365, see Network planning and performance tuning for Office 365 or contact your support group.</span></span> <span data-ttu-id="a031b-113">Informationen zur Leistungsoptimierung vom Office 365 finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) oder kontaktieren Sie Ihre Supportgruppe.</span><span class="sxs-lookup"><span data-stu-id="a031b-113">Note that Office 365 Multi-Geo is not designed for performance optimization cases, it is designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="a031b-114">Terminologie</span><span class="sxs-lookup"><span data-stu-id="a031b-114">Terminology</span></span>

<span data-ttu-id="a031b-115">Dies sind die wichtigsten Begriffe für die Beschreibung von Office 365 Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="a031b-115">Here are the key terms used in describing Office 365 Multi-Geo:</span></span>

- <span data-ttu-id="a031b-116">**Zentraler Standort** – Der geografische Standort, an dem Ihr Mandant ursprünglich bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="a031b-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="a031b-117">**Geo-Administrator** – Ein Administrator, der einen oder mehrere der angegebenen Satellitenstandorte verwalten kann.</span><span class="sxs-lookup"><span data-stu-id="a031b-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="a031b-118">**Geo-Code** – Eine Code aus drei Buchstaben für einen bestimmten Geo-Standort.</span><span class="sxs-lookup"><span data-stu-id="a031b-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="a031b-119">**Geo-Standort** – Ein geografischer Standort, der in einem Multi-Geo-Mandanten verwendet werden kann, um Daten zu hosten, einschließlich Exchange-Postfächer und OneDrive- und SharePoint-Seiten.</span><span class="sxs-lookup"><span data-stu-id="a031b-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="a031b-120">**Bevorzugter Datenspeicherort (PLD)** – Eine vom Administrator festgelegte Benutzereigenschaft, die angibt, an welchem geographischen Standort das Exchange-Postfach des Benutzers und OneDrive bereitgestellt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a031b-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="a031b-121">Der PLD gibt außerdem an, wo vom Benutzer erstellte SharePoint-Seiten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a031b-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="a031b-122">**Satelliten-Standort** – Der geographische Standort, an dem die Geo-fähigen Office 365-Arbeitslasten (SharePoint, OneDrive und Exchange) in einem Multi-Geo-Mandanten aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="a031b-122">**Satellite location** – The geo locations where the geo-aware Office 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="a031b-123">**Mandant** – Darstellung einer Organisation in der Office 365-Cloud, mit der in der Regel eine oder mehrere Domäne(n) verknüpft ist/sind (zum Beispiel contoso.com).</span><span class="sxs-lookup"><span data-stu-id="a031b-123">Tenant – An organization's representation in the Office 365 cloud which typically has one or more domains associated with it (for example, .</span></span>

## <a name="office-365-multi-geo-availability"></a><span data-ttu-id="a031b-124">Verfügbarkeit von Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a031b-124">Office 365 Multi-Geo availability</span></span>

<span data-ttu-id="a031b-125">Office 365 Multi-Geo wird derzeit in diesen Regionen und Ländern angeboten:</span><span class="sxs-lookup"><span data-stu-id="a031b-125">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="a031b-126">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="a031b-126">Getting started</span></span>

<span data-ttu-id="a031b-127">Gehen Sie folgendermaßen vor, um mit Multi-Geo loszulegen:</span><span class="sxs-lookup"><span data-stu-id="a031b-127">Follow these steps to get started:</span></span>

1. <span data-ttu-id="a031b-p105">Arbeiten Sie mit Ihrem Kontoteam zusammen, um den Serviceplan für _Multi-Geo-Funktionen in Office 365_ hinzuzufügen. Das Team unterstützt Sie beim Hinzufügen der benötigten Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="a031b-p105">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>

   <span data-ttu-id="a031b-130">Bevor Sie mit der Verwendung von Office 365 Muli-Geo beginnen können, muss Ihr Exchange Online-Mandant durch Microsoft für die Unterstützung von Multi-Geo konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="a031b-130">Before you can start using Office 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="a031b-131">Dieser einmalige Konfigurationsprozess wird ausgelöst, nach dem Sie den Service-Plan für *Multi-Geo Capabilities in Office 365* bestellt haben und die Lizenzen in Ihrem Mandanten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a031b-131">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Office 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="a031b-132">Sie erhalten im [Office 365-Nachrichtencenter](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) Benachrichtigungen, sobald Ihre Multi-Geo-Lizenzen angewendet werden und können dann mit dem Konfigurieren und Verwenden Ihrer Office 365 Multi-Geo-Funktionen beginnen.</span><span class="sxs-lookup"><span data-stu-id="a031b-132">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Office 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="a031b-133">Lesen Sie den Abschnitt [Planen Ihrer Multi-Geo-Umgebung](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="a031b-133">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="a031b-134">Erfahren Sie mehr über das [Verwalten einer Multi-Geo-Umgebung](administering-a-multi-geo-environment.md) und darüber, [wie Ihre Benutzer die Umgebung erleben](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="a031b-134">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="a031b-135">Wenn Sie für die Einrichtung von Office 365 Multi-Geo bereit sind, [konfigurieren Sie Ihren Mandanten für Multi-Geo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a031b-135">When you are ready to set up Office 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="a031b-136">[Einrichten der Suche](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="a031b-136">[Set up people search](configure-search-for-multi-geo.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="a031b-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a031b-137">See also</span></span>

[<span data-ttu-id="a031b-138">Aka.ms/GoMultiGeo </span><span class="sxs-lookup"><span data-stu-id="a031b-138">Aka.ms/GoMultiGeo </span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="a031b-139">Multi-Geo-Funktionen in OneDrive und SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a031b-139">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365.md)

[<span data-ttu-id="a031b-140">Multi-Geo-Funktionen in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="a031b-140">NoteFor information on Multi-Geo Capabilities, see Multi-Geo Capabilities in Exchange Online.</span></span>](multi-geo-capabilities-in-exchange-online.md)
