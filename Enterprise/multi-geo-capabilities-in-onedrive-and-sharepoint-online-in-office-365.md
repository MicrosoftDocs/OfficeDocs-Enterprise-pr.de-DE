---
title: Multi-Geo-Funktionen in OneDrive und SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Erweitern Sie Ihre Office 365-Anwesenheit auf mehrere geografische Regionen mit Multi-Geo-Funktionen in OneDrive und SharePoint Online.
ms.openlocfilehash: 7387b267cbc925916b600a112d6911c97a971c36
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="c682c-103">Multi-Geo-Funktionen in OneDrive und SharePoint Online in Office 365</span><span class="sxs-lookup"><span data-stu-id="c682c-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="c682c-p101">Mit Multi-Geo-Funktionen in OneDrive und SharePoint Online kann Ihr Unternehmen seine Office 365-Präsenz auf mehrere geografische Regionen und/oder Länder innerhalb des vorhandenen Mandanten erweitern. Dieses Feature ist derzeit in der Vorschau. Wenden Sie sich an Ihr Microsoft-Kontoteam, um Ihr multinationales Unternehmen für die OneDrive Multi-Geo-Vorschau anzumelden.</span><span class="sxs-lookup"><span data-stu-id="c682c-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. This feature is currently in preview. Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="c682c-107">Mit OneDrive Multi-Geo, können Sie bereitstellen und Speichern von Daten im Ruhezustand in die Geo-Speicherorte, die Sie ausgewählt haben, um Daten vor-Ort-Anforderungen erfüllen und entsperren gleichzeitig Ihre globalen Roll nicht genügend moderne Produktivität Erfahrungen Ihrer Mitarbeiter.</span><span class="sxs-lookup"><span data-stu-id="c682c-107">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="c682c-108">Sieht aus wie Multi-Geo-Features für Ihre Organisation profitieren können:</span><span class="sxs-lookup"><span data-stu-id="c682c-108">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="c682c-109">Arbeiten Sie als eine weltweit verbundene Organisation mit einem einzigen Office 365-Mandanten, der mehrere geografische Standorte umfasst.</span><span class="sxs-lookup"><span data-stu-id="c682c-109">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="c682c-110">Erfüllen Sie die Datenresistenz-Anforderungen, indem Sie Daten im Ruhezustand an einem angegebenen geografischen Standort erstellen und hosten.</span><span class="sxs-lookup"><span data-stu-id="c682c-110">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="c682c-111">Statten Sie Ihre Satellitenbenutzer mit der gleichen modernen Produktivität aus wie Ihre Benutzer an einem zentralen Ort.</span><span class="sxs-lookup"><span data-stu-id="c682c-111">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="c682c-112">Bieten Sie Ihren Benutzern die Möglichkeit, den geografischen Standort zu wechseln, während der Zugriff auf ihre Inhalte erhalten bleibt. </span><span class="sxs-lookup"><span data-stu-id="c682c-112">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="c682c-113">Passen Sie Ihre Freigaberichtlinien dem  jeweiligen geografischen Standort und Ihre Richtlinien zur Verhinderung von Datenlecks dem jeweiligen Unternehmensstandort an.</span><span class="sxs-lookup"><span data-stu-id="c682c-113">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="c682c-114">Legen Sie für jeden geografischen Speicherort eDiscovery-Manager fest und genehmigen Sie die auf Ihren geografischen Speicherort zugeschnittene Regelung von Rechtsfällen.</span><span class="sxs-lookup"><span data-stu-id="c682c-114">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="c682c-115">Wählen Sie einmalige URL-Namespaces (z.B. ContosoEUR.sharepoint.com) für Ihre zusätzlichen geografischen Speicherorte. </span><span class="sxs-lookup"><span data-stu-id="c682c-115">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="c682c-116">Konsolidieren Sie Ihre regionalen lokalen Daten in Ihrem Office 365-Multi-Geo-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="c682c-116">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="c682c-p102">In einer Konfiguration mit mehreren geografisch besteht aus Ihrem Office 365-Mandanten einen zentralen Speicherort (auch bekannt als dem Standardspeicherort) und einen oder mehrere Satelliten Geo-Speicherorte. Das Kernkonzept von Multi-Geo ist, dass mehrere Standorte hinweg Geo wird ein einzelner Mandant über eine erstrecken. In einem Mandanten Multi-Geo ist die Informationen zu Geo Speicherorte, Gruppen und Benutzerinformationen in Azure Active Directory (AAD) gesteuert. Da Ihre Mandanten Informationen zentral gesteuert und in jedem Standort Geo synchronisiert, enthalten Freigabe und Erfahrung im Zusammenhang mit alle Personen in Ihrem Unternehmen globale zur Förderung des Bekanntheitsgrads.</span><span class="sxs-lookup"><span data-stu-id="c682c-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="c682c-121">Beispielkonfiguration Multi-Geo-Mandanten</span><span class="sxs-lookup"><span data-stu-id="c682c-121">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="c682c-122">Mit einem Multi-Geo-Mandanten kann Contoso, mit einem zentralen Standort in Nordamerika, unter der Dachorganisation Contoso.com eine Erweiterung auf geografische Satellitenstandorte in Europa und Australien durchführen. Benutzern mit bevorzugtem Datenspeicherort in Europa steht OneDrive in Europa zur Verfügung, während OneDrive-Benutzern mit bevorzugtem Datenspeicherort in Nordamerika OneDrive in den USA zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="c682c-122">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Übersicht der ganzen Welt Geo Speicherorte für Contoso und an anderen Standorten verfügbare Geo anzeigen](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="c682c-124">Multi-Geo-Funktionen in drei einfachen Schritten</span><span class="sxs-lookup"><span data-stu-id="c682c-124">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="c682c-125">Die Konfiguration von Multi-Geo ist ganz einfach:</span><span class="sxs-lookup"><span data-stu-id="c682c-125">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="c682c-p103">Arbeiten Sie mit Ihr Kundenteam, die Dienstplan _Multi-Geo-Funktionen in Office 365_ hinzufügen möchten. Sie führt Sie, um die Anzahl der benötigten Lizenzen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c682c-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="c682c-128">Fügen Sie Ihre Satellitenstandorte hinzu.</span><span class="sxs-lookup"><span data-stu-id="c682c-128">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="c682c-129">Konfigurieren Sie Ihre Benutzerkonten für den entsprechenden Speicherort.</span><span class="sxs-lookup"><span data-stu-id="c682c-129">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="c682c-130">Multi-Geo-Status und -Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="c682c-130">Multi-Geo status and availability</span></span>

<span data-ttu-id="c682c-131">OneDrive Multi-Geo wird derzeit in diesen Regionen und Ländern angeboten:</span><span class="sxs-lookup"><span data-stu-id="c682c-131">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="c682c-132">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="c682c-132">Asia-Pacific</span></span>
    
- <span data-ttu-id="c682c-133">Australien</span><span class="sxs-lookup"><span data-stu-id="c682c-133">Australia</span></span>
    
- <span data-ttu-id="c682c-134">Kanada</span><span class="sxs-lookup"><span data-stu-id="c682c-134">Canada</span></span>
    
- <span data-ttu-id="c682c-135">Europäische Union (EMEA)</span><span class="sxs-lookup"><span data-stu-id="c682c-135">European Union (EMEA)</span></span>
    
- <span data-ttu-id="c682c-136">Japan</span><span class="sxs-lookup"><span data-stu-id="c682c-136">Japan</span></span>
    
- <span data-ttu-id="c682c-137">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="c682c-137">United Kingdom</span></span>
    
- <span data-ttu-id="c682c-138">Vereinigte Staaten (Nordamerika)</span><span class="sxs-lookup"><span data-stu-id="c682c-138">United States (North America)</span></span>
    
- <span data-ttu-id="c682c-139">Korea</span><span class="sxs-lookup"><span data-stu-id="c682c-139">Korea</span></span>
      
<span data-ttu-id="c682c-140">Zukünftige geografische Speicherorte:</span><span class="sxs-lookup"><span data-stu-id="c682c-140">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="c682c-141">Frankreich</span><span class="sxs-lookup"><span data-stu-id="c682c-141">France</span></span>
- <span data-ttu-id="c682c-142">Indien</span><span class="sxs-lookup"><span data-stu-id="c682c-142">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="c682c-143">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="c682c-143">Getting started</span></span>

<span data-ttu-id="c682c-p104">Der erste Schritt darin, mit OneDrive for Business Multi-Geo Einstieg [Ihrer OneDrive for Business Multi-Geo-Umgebung planen](plan-for-multi-geo.md). Weiter [Informationen zum Verwalten von einer Umgebung mit mehreren geografisch](administering-a-multi-geo-environment.md) und [wie werden die Benutzer eine Umgebung mit mehreren geografisch bemerken](multi-geo-user-experience.md). Wenn Sie bereit sind, einrichten, OneDrive for Business Multi-Geo, [Konfigurieren Ihres Mandanten für Multi-Geo](multi-geo-tenant-configuration.md), [Verschieben Sie alle vorhandenen OneDrive Websites an die neuen Geo-Speicherorte](move-onedrive-between-geo-locations.md) und [Einrichten der Suche](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="c682c-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
