---
title: Multi-Geo-Funktionen in OneDrive und SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Erweitern Sie Ihre Office 365-Präsenz auf mehrere geografische Regionen mit Multi-Geo-Funktionen in OneDrive und SharePoint Online.
ms.openlocfilehash: c6648dc8a0b225105e408fc082f6bb4d1a1b4930
ms.sourcegitcommit: 2f138e0733266ab4b179bbe882c734500118dde1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "24012735"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="de7df-103">Multi-Geo-Funktionen in OneDrive und SharePoint Online in Office 365</span><span class="sxs-lookup"><span data-stu-id="de7df-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="de7df-p101">Mit Multi-Geo-Funktionen in OneDrive und SharePoint Online kann Ihr Unternehmen seine Office 365-Präsenz auf mehrere geografische Regionen und/oder Länder innerhalb des vorhandenen Mandanten erweitern. Wenden Sie sich an Ihr Microsoft-Kontoteam, um Ihr multinationales Unternehmen für Multi-Geo in OneDrive for Business anzumelden.</span><span class="sxs-lookup"><span data-stu-id="de7df-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="de7df-106">Mit Multi-Geo in OneDrive können Sie ruhende Daten an den Datenaufbewahrungsanforderungen entsprechenden geografischen Standorten bereitstellen und speichern und gleichzeitig die globale Bereitstellung moderner Produktivitätserfahrungen für Ihre Mitarbeiter in Gang setzen.</span><span class="sxs-lookup"><span data-stu-id="de7df-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="de7df-107">Vorteile von Multi-Geo-Funktionen für Ihre Organisation:</span><span class="sxs-lookup"><span data-stu-id="de7df-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="de7df-108">Arbeiten Sie als eine weltweit verbundene Organisation mit einem einzigen Office 365-Mandanten, der mehrere geografische Standorte umfasst.</span><span class="sxs-lookup"><span data-stu-id="de7df-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="de7df-109">Erfüllen Sie die Datenresistenz-Anforderungen, indem Sie Daten im Ruhezustand an einem angegebenen geografischen Standort erstellen und hosten.</span><span class="sxs-lookup"><span data-stu-id="de7df-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="de7df-110">Statten Sie Ihre Satellitenbenutzer mit der gleichen modernen Produktivität aus wie Ihre Benutzer an einem zentralen Ort.</span><span class="sxs-lookup"><span data-stu-id="de7df-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="de7df-111">Bieten Sie Ihren Benutzern die Möglichkeit, den geografischen Standort zu wechseln, während der Zugriff auf ihre Inhalte erhalten bleibt. </span><span class="sxs-lookup"><span data-stu-id="de7df-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="de7df-112">Passen Sie Ihre Freigaberichtlinien dem  jeweiligen geografischen Standort und Ihre Richtlinien zur Verhinderung von Datenlecks dem jeweiligen Unternehmensstandort an.</span><span class="sxs-lookup"><span data-stu-id="de7df-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="de7df-113">Legen Sie für jeden geografischen Speicherort eDiscovery-Manager fest und genehmigen Sie die auf Ihren geografischen Speicherort zugeschnittene Regelung von Rechtsfällen.</span><span class="sxs-lookup"><span data-stu-id="de7df-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="de7df-114">Wählen Sie einmalige URL-Namespaces (z.B. ContosoEUR.sharepoint.com) für Ihre zusätzlichen geografischen Speicherorte. </span><span class="sxs-lookup"><span data-stu-id="de7df-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="de7df-115">Konsolidieren Sie Ihre regionalen lokalen Daten in Ihrem Office 365-Multi-Geo-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="de7df-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="de7df-p102">In einer Multi-Geo-Konfiguration besteht Ihr Office 365-Mandant aus einem zentralen Standort (auch Standardstandort genannt) und einem oder mehreren Geo-Satellitenstandorten. Das Hauptkonzept von Multi-Geo besteht darin, dass ein einziger Mandant mehrere geografische Standorte umfasst. Die Informationen über geografische Standorte, Gruppen und Benutzer eines Multi-Geo-Mandanten werden in Azure Active Directory (AAD) verwaltet. Da Ihre Mandanteninformationen zentral verwaltet und an jedem geografischen Standort synchronisiert werden, wird das globale Bewusstsein durch das Teilen von Informationen und Erfahrungen im gesamten Unternehmen erhöht.</span><span class="sxs-lookup"><span data-stu-id="de7df-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="de7df-120">Video: Einführung in Multi-Geo in Office 365</span><span class="sxs-lookup"><span data-stu-id="de7df-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="de7df-121">Multi-Geo-Funktionen in drei einfachen Schritten</span><span class="sxs-lookup"><span data-stu-id="de7df-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="de7df-122">Die Konfiguration von Multi-Geo ist ganz einfach:</span><span class="sxs-lookup"><span data-stu-id="de7df-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="de7df-p103">Arbeiten Sie mit Ihrem Kontoteam zusammen, um den Serviceplan für _Multi-Geo-Funktionen in Office 365_ hinzuzufügen. Das Team unterstützt Sie beim Hinzufügen der benötigten Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="de7df-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="de7df-125">Fügen Sie Ihre Satellitenstandorte hinzu.</span><span class="sxs-lookup"><span data-stu-id="de7df-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="de7df-126">Konfigurieren Sie Ihre Benutzerkonten für den entsprechenden Speicherort.</span><span class="sxs-lookup"><span data-stu-id="de7df-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="de7df-127">Multi-Geo-Status und -Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="de7df-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="de7df-128">OneDrive Multi-Geo wird derzeit in diesen Regionen und Ländern angeboten:</span><span class="sxs-lookup"><span data-stu-id="de7df-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="de7df-129">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="de7df-129">Asia-Pacific</span></span>
    
- <span data-ttu-id="de7df-130">Australien</span><span class="sxs-lookup"><span data-stu-id="de7df-130">Australia</span></span>
    
- <span data-ttu-id="de7df-131">Kanada</span><span class="sxs-lookup"><span data-stu-id="de7df-131">Canada</span></span>
    
- <span data-ttu-id="de7df-132">Europäische Union (EMEA)</span><span class="sxs-lookup"><span data-stu-id="de7df-132">European Union (EMEA)</span></span>

- <span data-ttu-id="de7df-133">Frankreich</span><span class="sxs-lookup"><span data-stu-id="de7df-133">France</span></span>
    
- <span data-ttu-id="de7df-134">Japan</span><span class="sxs-lookup"><span data-stu-id="de7df-134">Japan</span></span>
    
- <span data-ttu-id="de7df-135">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="de7df-135">United Kingdom</span></span>
    
- <span data-ttu-id="de7df-136">Vereinigte Staaten (Nordamerika)</span><span class="sxs-lookup"><span data-stu-id="de7df-136">United States (North America)</span></span>
    
- <span data-ttu-id="de7df-137">Korea</span><span class="sxs-lookup"><span data-stu-id="de7df-137">Korea</span></span>
      
<span data-ttu-id="de7df-138">Zukünftige geografische Speicherorte:</span><span class="sxs-lookup"><span data-stu-id="de7df-138">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="de7df-139">Indien</span><span class="sxs-lookup"><span data-stu-id="de7df-139">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="de7df-140">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="de7df-140">Getting started</span></span>

<span data-ttu-id="de7df-p104">Der erste Schritt bei Multi-Geo in OneDrive for Business besteht in der [Planung der Multi-Geo-Umgebung in OneDrive for Business](plan-for-multi-geo.md). Informieren Sie sich als Nächstes [über die Verwaltung einer Multi-Geo-Umgebung](administering-a-multi-geo-environment.md) und [die Benutzererfahrung in einer Multi-Geo-Umgebung](multi-geo-user-experience.md). Wenn Sie zum Einrichten von Multi-Geo in OneDrive for Business sind, [konfigurieren Sie Ihren Mandanten für Multi-Geo](multi-geo-tenant-configuration.md), [verschieben Sie dann alle vorhandenen OneDrive-Websites an die neuen geografischen Standorte](move-onedrive-between-geo-locations.md), und [richten Sie die Suche ein](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="de7df-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
