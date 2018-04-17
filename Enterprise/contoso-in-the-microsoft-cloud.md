---
title: Contoso in der Microsoft-Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c4a6d625-4938-42cc-87e1-56b7a13c63ef
description: 'Zusammenfassung: Wie in einer fiktiven, aber repräsentativen globalen Organisation mithilfe der Cloudangebote von Microsoft eine cloudeinschließende IT-Infrastruktur eingeführt wurde.'
ms.openlocfilehash: 7807a6b07179e695c28a923f744805558d83e690
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="contoso-in-the-microsoft-cloud"></a><span data-ttu-id="68a0f-103">Contoso in der Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="68a0f-103">Contoso in the Microsoft Cloud</span></span>

 <span data-ttu-id="68a0f-104">**Zusammenfassung:** Wie in einer fiktiven, aber repräsentativen globalen Organisation mithilfe der Cloudangebote von Microsoft eine cloudeinschließende IT-Infrastruktur eingeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="68a0f-104">**Summary:** How a fictional but representative global organization is adopting a cloud-inclusive IT infrastructure with Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="68a0f-p101">Dieser Artikel enthält Links zu einer Reihe von Artikeln, in denen beschrieben wird, wie die Contoso Corporation, ein globaler Mischkonzern im Fertigungsbereich mit Firmensitz in Paris, eine IT-Infrastruktur inklusive Cloud umsetzt und dabei wichtige Designentscheidungen in puncto Netzwerk, Identität und Sicherheit getroffen hat. Außerdem ist darin die Implementierung von Unternehmenscloud-Szenarios und die Lösung von Geschäftsproblemen erläutert. Sie können diesen Artikel auch als zehnseitiges Poster anzeigen und im Tabloid-Format ausdrucken (auch bekannt als Ledger, 11 × 17 oder A3).</span><span class="sxs-lookup"><span data-stu-id="68a0f-p101">This article links you to a set of articles that describe how the Contoso Corporation, a global manufacturing conglomerate with its headquarters in Paris, is embracing a cloud-inclusive IT infrastructure and has addressed major design decisions for networking, identity, and security and how it is implementing enterprise cloud scenarios to address its business problems. You can also view this information as an 11-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="68a0f-107">[![Miniaturbild von Contoso im Microsoft Cloud-Poster.](images/Contoso_Poster/Thumbnail.png)](https://www.microsoft.com/download/details.aspx?id=54427)</span><span class="sxs-lookup"><span data-stu-id="68a0f-107">[![Thumb image of the Contoso in the Microsoft Cloud poster.](images/Contoso_Poster/Thumbnail.png)](https://www.microsoft.com/download/details.aspx?id=54427)</span></span>
  
<span data-ttu-id="68a0f-108">![PDF-Datei](images/Common_Images/PDFIcon.png)[PDF](https://go.microsoft.com/fwlink/p/?linkid=842085)  | ![Visio-Datei](images/Common_Images/VisioIcon.png)[Visio](https://go.microsoft.com/fwlink/p/?linkid=842086)  | ![Seite mit Versionen in zusätzlichen Sprachen anzeigen](images/Common_Images/GlobeIcon.png)[Weitere Sprachen](https://www.microsoft.com/download/details.aspx?id=54427)</span><span class="sxs-lookup"><span data-stu-id="68a0f-108">![PDF file](images/Common_Images/PDFIcon.png)[PDF](https://go.microsoft.com/fwlink/p/?linkid=842085)  | ![Visio file](images/Common_Images/VisioIcon.png)[Visio](https://go.microsoft.com/fwlink/p/?linkid=842086)  | ![See a page with versions in additional languages](images/Common_Images/GlobeIcon.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54427)</span></span>
  
<span data-ttu-id="68a0f-109">Lesen Sie die folgenden Abschnitte:</span><span class="sxs-lookup"><span data-stu-id="68a0f-109">See the following sections:</span></span>
  
- [<span data-ttu-id="68a0f-110">Hybrid Cloud-Übersicht</span><span class="sxs-lookup"><span data-stu-id="68a0f-110">Hybrid cloud overview</span></span>](hybrid-cloud-overview.md)
    
    <span data-ttu-id="68a0f-111">Die Contoso Corporation ist ein globaler Mischkonzern im Bereich Fertigung, Vertrieb und Support mit einem Portfolio aus über 100.000 Produkten.</span><span class="sxs-lookup"><span data-stu-id="68a0f-111">The Contoso Corporation is a global conglomerate manufacturing, sales, and support organization with over 100,000 products.</span></span>
    
- [<span data-ttu-id="68a0f-112">Contosos IT-Infrastruktur und -Anforderungen</span><span class="sxs-lookup"><span data-stu-id="68a0f-112">Contoso's IT infrastructure and needs</span></span>](contoso-it-infrastructure-and-needs.md)
    
    <span data-ttu-id="68a0f-113">Contoso ist dabei, von der lokalen zentralen IT-Infrastruktur auf eine cloudeinschließende Infrastruktur umzustellen, die aus cloudbasierten persönlichen Produktivitätsarbeitslasten, Anwendungen und Hybridszenarien besteht.
</span><span class="sxs-lookup"><span data-stu-id="68a0f-113">Contoso is transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
    
- [<span data-ttu-id="68a0f-114">Netzwerkfunktionen für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="68a0f-114">Networking for the Contoso Corporation</span></span>](networking-for-the-contoso-corporation.md)
    
    <span data-ttu-id="68a0f-115">Zur Optimierung der Leistung cloudbasierter Dienste haben die Netzwerkingenieure von Contoso den Datenverkehr zum Internet-Edge und über das Internet optimiert.</span><span class="sxs-lookup"><span data-stu-id="68a0f-115">For best performance to cloud-based services, Contoso's network engineers optimized traffic to their Internet edge and across the Internet.</span></span>
    
- [<span data-ttu-id="68a0f-116">Identität für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="68a0f-116">Identity for the Contoso Corporation</span></span>](identity-for-the-contoso-corporation.md)
    
    <span data-ttu-id="68a0f-117">Die Identität von Contoso in der Cloudlösung verwendet den lokalen Identitätsanbieter und umfasst eine Authentifizierung im Verbund mit den vorhandenen vertrauenswürdigen Identitätsanbietern von Drittanbietern.</span><span class="sxs-lookup"><span data-stu-id="68a0f-117">Contoso's identity in the cloud solution leverages their on-premises identity provider and includes federated authentication with their existing trusted, third-party identity providers.</span></span>
    
- [<span data-ttu-id="68a0f-118">Abonnements, Lizenzen und Benutzerkonten für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="68a0f-118">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)
    
    <span data-ttu-id="68a0f-119">Contoso verwendet die Hierarchie „Organisation/Abonnements/Lizenzen/Benutzerkonten“, um auf die Cloudangebote von Microsoft zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="68a0f-119">Contoso uses the organization/subscriptions/licenses/user accounts hierarchy to access Microsoft's cloud offerings.</span></span>
    
- [<span data-ttu-id="68a0f-120">Sicherheit für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="68a0f-120">Security for the Contoso Corporation</span></span>](security-for-the-contoso-corporation.md)
    
    <span data-ttu-id="68a0f-121">Für die Umwandlung seiner IT-Infrastruktur in eine cloudeinschließende Infrastruktur hat sich Contoso vergewissert, dass seine lokalen Sicherheitsanforderungen in Microsofts Cloudangeboten unterstützt werden und implementiert sind.</span><span class="sxs-lookup"><span data-stu-id="68a0f-121">When transitioning their IT infrastructure to a cloud-inclusive one, Contoso made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
    
- [<span data-ttu-id="68a0f-122">Enterprise-Szenarien für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="68a0f-122">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
    
    <span data-ttu-id="68a0f-123">Erfahren Sie, wie Contoso mithilfe der Cloudangebote von Microsoft seine Geschäftsanforderungen erfüllen kann.</span><span class="sxs-lookup"><span data-stu-id="68a0f-123">See how Contoso is addressing its business needs with Microsoft's cloud offerings.</span></span>
    
> [!NOTE]
> <span data-ttu-id="68a0f-124">In diesen Artikeln wird die Version vom **September 2017** des Posters „Contoso in der Microsoft-Cloud" widergespiegelt.</span><span class="sxs-lookup"><span data-stu-id="68a0f-124">These articles reflect the **September 2017** release of the Contoso in the Microsoft Cloud poster.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="68a0f-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="68a0f-125">See Also</span></span>

[<span data-ttu-id="68a0f-126">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="68a0f-126">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="68a0f-127">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="68a0f-127">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



