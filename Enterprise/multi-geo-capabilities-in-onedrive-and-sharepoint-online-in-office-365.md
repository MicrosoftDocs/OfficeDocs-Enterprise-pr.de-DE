---
title: Multi-Geo-Funktionen in OneDrive und SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Erweitern Sie Ihre Office 365-Anwesenheit auf mehrere geografische Regionen mit Multi-Geo-Funktionen in OneDrive und SharePoint Online.
ms.openlocfilehash: 3f72158fe05aadfe8a08a5520bf65cd2d0aaa1c6
ms.sourcegitcommit: a81d08c7e8771cb2c232435971e3169d4f7428dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="b3644-103">Multi-Geo-Funktionen in OneDrive und SharePoint Online in Office 365</span><span class="sxs-lookup"><span data-stu-id="b3644-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="b3644-p101">Mit Multi-Geo-Funktionen in OneDrive und SharePoint Online kann Ihrer Organisation die Office 365-Präsenz auf mehreren geografischen Regionen und/oder Ländern innerhalb Ihres vorhandenen Mandanten erweitern. Treten Sie Ihr Microsoft-Konto Team Ihres Unternehmens mit mehreren National für OneDrive for Business Multi-Geo registrieren.</span><span class="sxs-lookup"><span data-stu-id="b3644-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="b3644-106">Mit OneDrive Multi-Geo, können Sie bereitstellen und Speichern von Daten im Ruhezustand in die Geo-Speicherorte, die Sie ausgewählt haben, um Daten vor-Ort-Anforderungen erfüllen und entsperren gleichzeitig Ihre globalen Roll nicht genügend moderne Produktivität Erfahrungen Ihrer Mitarbeiter.</span><span class="sxs-lookup"><span data-stu-id="b3644-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="b3644-107">Sieht aus wie Multi-Geo-Features für Ihre Organisation profitieren können:</span><span class="sxs-lookup"><span data-stu-id="b3644-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="b3644-108">Arbeiten Sie als eine weltweit verbundene Organisation mit einem einzigen Office 365-Mandanten, der mehrere geografische Standorte umfasst.</span><span class="sxs-lookup"><span data-stu-id="b3644-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="b3644-109">Erfüllen Sie die Datenresistenz-Anforderungen, indem Sie Daten im Ruhezustand an einem angegebenen geografischen Standort erstellen und hosten.</span><span class="sxs-lookup"><span data-stu-id="b3644-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="b3644-110">Statten Sie Ihre Satellitenbenutzer mit der gleichen modernen Produktivität aus wie Ihre Benutzer an einem zentralen Ort.</span><span class="sxs-lookup"><span data-stu-id="b3644-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="b3644-111">Bieten Sie Ihren Benutzern die Möglichkeit, den geografischen Standort zu wechseln, während der Zugriff auf ihre Inhalte erhalten bleibt. </span><span class="sxs-lookup"><span data-stu-id="b3644-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="b3644-112">Passen Sie Ihre Freigaberichtlinien dem  jeweiligen geografischen Standort und Ihre Richtlinien zur Verhinderung von Datenlecks dem jeweiligen Unternehmensstandort an.</span><span class="sxs-lookup"><span data-stu-id="b3644-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="b3644-113">Legen Sie für jeden geografischen Speicherort eDiscovery-Manager fest und genehmigen Sie die auf Ihren geografischen Speicherort zugeschnittene Regelung von Rechtsfällen.</span><span class="sxs-lookup"><span data-stu-id="b3644-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="b3644-114">Wählen Sie einmalige URL-Namespaces (z.B. ContosoEUR.sharepoint.com) für Ihre zusätzlichen geografischen Speicherorte. </span><span class="sxs-lookup"><span data-stu-id="b3644-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="b3644-115">Konsolidieren Sie Ihre regionalen lokalen Daten in Ihrem Office 365-Multi-Geo-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="b3644-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="b3644-p102">In einer Konfiguration mit mehreren geografisch besteht aus Ihrem Office 365-Mandanten einen zentralen Speicherort (auch bekannt als dem Standardspeicherort) und einen oder mehrere Satelliten Geo-Speicherorte. Das Kernkonzept von Multi-Geo ist, dass mehrere Standorte hinweg Geo wird ein einzelner Mandant über eine erstrecken. In einem Mandanten Multi-Geo ist die Informationen zu Geo Speicherorte, Gruppen und Benutzerinformationen in Azure Active Directory (AAD) gesteuert. Da Ihre Mandanten Informationen zentral gesteuert und in jedem Standort Geo synchronisiert, enthalten Freigabe und Erfahrung im Zusammenhang mit alle Personen in Ihrem Unternehmen globale zur Förderung des Bekanntheitsgrads.</span><span class="sxs-lookup"><span data-stu-id="b3644-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="b3644-120">Beispielkonfiguration Multi-Geo-Mandanten</span><span class="sxs-lookup"><span data-stu-id="b3644-120">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="b3644-121">Mit einem Multi-Geo-Mandanten kann Contoso, mit einem zentralen Standort in Nordamerika, unter der Dachorganisation Contoso.com eine Erweiterung auf geografische Satellitenstandorte in Europa und Australien durchführen. Benutzern mit bevorzugtem Datenspeicherort in Europa steht OneDrive in Europa zur Verfügung, während OneDrive-Benutzern mit bevorzugtem Datenspeicherort in Nordamerika OneDrive in den USA zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="b3644-121">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Übersicht der ganzen Welt Geo Speicherorte für Contoso und an anderen Standorten verfügbare Geo anzeigen](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="b3644-123">Multi-Geo-Funktionen in drei einfachen Schritten</span><span class="sxs-lookup"><span data-stu-id="b3644-123">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="b3644-124">Die Konfiguration von Multi-Geo ist ganz einfach:</span><span class="sxs-lookup"><span data-stu-id="b3644-124">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="b3644-p103">Arbeiten Sie mit Ihr Kundenteam, die Dienstplan _Multi-Geo-Funktionen in Office 365_ hinzufügen möchten. Sie führt Sie, um die Anzahl der benötigten Lizenzen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b3644-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="b3644-127">Fügen Sie Ihre Satellitenstandorte hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3644-127">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="b3644-128">Konfigurieren Sie Ihre Benutzerkonten für den entsprechenden Speicherort.</span><span class="sxs-lookup"><span data-stu-id="b3644-128">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="b3644-129">Multi-Geo-Status und -Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="b3644-129">Multi-Geo status and availability</span></span>

<span data-ttu-id="b3644-130">OneDrive Multi-Geo wird derzeit in diesen Regionen und Ländern angeboten:</span><span class="sxs-lookup"><span data-stu-id="b3644-130">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="b3644-131">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="b3644-131">Asia-Pacific</span></span>
    
- <span data-ttu-id="b3644-132">Australien</span><span class="sxs-lookup"><span data-stu-id="b3644-132">Australia</span></span>
    
- <span data-ttu-id="b3644-133">Kanada</span><span class="sxs-lookup"><span data-stu-id="b3644-133">Canada</span></span>
    
- <span data-ttu-id="b3644-134">Europäische Union (EMEA)</span><span class="sxs-lookup"><span data-stu-id="b3644-134">European Union (EMEA)</span></span>
    
- <span data-ttu-id="b3644-135">Japan</span><span class="sxs-lookup"><span data-stu-id="b3644-135">Japan</span></span>
    
- <span data-ttu-id="b3644-136">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="b3644-136">United Kingdom</span></span>
    
- <span data-ttu-id="b3644-137">Vereinigte Staaten (Nordamerika)</span><span class="sxs-lookup"><span data-stu-id="b3644-137">United States (North America)</span></span>
    
- <span data-ttu-id="b3644-138">Korea</span><span class="sxs-lookup"><span data-stu-id="b3644-138">Korea</span></span>
      
<span data-ttu-id="b3644-139">Zukünftige geografische Speicherorte:</span><span class="sxs-lookup"><span data-stu-id="b3644-139">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="b3644-140">Frankreich</span><span class="sxs-lookup"><span data-stu-id="b3644-140">France</span></span>
- <span data-ttu-id="b3644-141">Indien</span><span class="sxs-lookup"><span data-stu-id="b3644-141">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="b3644-142">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="b3644-142">Getting started</span></span>

<span data-ttu-id="b3644-p104">Der erste Schritt darin, mit OneDrive for Business Multi-Geo Einstieg [Ihrer OneDrive for Business Multi-Geo-Umgebung planen](plan-for-multi-geo.md). Weiter [Informationen zum Verwalten von einer Umgebung mit mehreren geografisch](administering-a-multi-geo-environment.md) und [wie werden die Benutzer eine Umgebung mit mehreren geografisch bemerken](multi-geo-user-experience.md). Wenn Sie bereit sind, einrichten, OneDrive for Business Multi-Geo, [Konfigurieren Ihres Mandanten für Multi-Geo](multi-geo-tenant-configuration.md), [Verschieben Sie alle vorhandenen OneDrive Websites an die neuen Geo-Speicherorte](move-onedrive-between-geo-locations.md) und [Einrichten der Suche](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="b3644-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
