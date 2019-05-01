---
title: Entwerfen von Netzwerken für Microsoft-SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Zusammenfassung: Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487296"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="2d5f4-103">Entwerfen von Netzwerken für Microsoft-SaaS</span><span class="sxs-lookup"><span data-stu-id="2d5f4-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="2d5f4-104">**Zusammenfassung:** Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="2d5f4-105">Die Optimierung Ihres Microsoft SaaS-Services erfordert die Konfiguration von internen und Edge-Geräten, um die verschiedenen Traffickategorien für Microsoft SaaS-Services zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="2d5f4-106">Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste</span><span class="sxs-lookup"><span data-stu-id="2d5f4-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="2d5f4-107">Befolgen Sie diese Schritte, um Ihr Netzwerk für Microsoft SaaS-Dienste zu optimieren:</span><span class="sxs-lookup"><span data-stu-id="2d5f4-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="2d5f4-108">Durchlaufen Sie die **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud Services** in [Gemeinsame Elemente der Microsoft-Cloudkonnektivität](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="2d5f4-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="2d5f4-109">Fügen Sie jeder ihrer Niederlassung eine Internet Verbindung hinzu.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="2d5f4-110">Stellen Sie sicher, dass die ISPs für alle Internet Verbindungen einen DNS-Server mit einer lokalen IP-Adresse verwenden.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="2d5f4-111">Untersuchen Sie Ihre Netzwerk-Haarnadeln, Zwischenziele wie Cloud-basierte Sicherheitsdienste, und beseitigen Sie Sie nach Möglichkeit.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="2d5f4-112">Konfigurieren Sie Ihre edgegeräte, um die Verarbeitung für die Kategorien optimieren und zulassen von Microsoft SaaS-Datenverkehr zu umgehen.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="2d5f4-113">Optimieren des Datenverkehrs zu Microsoft SaaS-Diensten</span><span class="sxs-lookup"><span data-stu-id="2d5f4-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="2d5f4-114">Es gibt drei Kategorien von Microsoft SaaS-Datenverkehr:</span><span class="sxs-lookup"><span data-stu-id="2d5f4-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="2d5f4-115">Optimieren</span><span class="sxs-lookup"><span data-stu-id="2d5f4-115">Optimize</span></span>

  <span data-ttu-id="2d5f4-116">Erforderlich für die Anbindung an jeden Microsoft SaaS-Dienst und stellt mehr als 75% der Microsoft SaaS-Bandbreite, Verbindungen und Datenmenge dar.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="2d5f4-117">Zulassen</span><span class="sxs-lookup"><span data-stu-id="2d5f4-117">Allow</span></span>

  <span data-ttu-id="2d5f4-118">Für die Konnektivität mit bestimmten Microsoft SaaS-Diensten und-Features erforderlich, Sie sind jedoch nicht so sensibel für die Netzwerkleistung und Wartezeit wie die in der Kategorie optimieren.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="2d5f4-119">Standard</span><span class="sxs-lookup"><span data-stu-id="2d5f4-119">Default</span></span>

  <span data-ttu-id="2d5f4-120">Stellen Sie Microsoft SaaS-Dienste und Abhängigkeiten dar, die keine Optimierung erfordern.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="2d5f4-121">Sie können den standardmäßigen Kategorien Datenverkehr wie normale Internet Datenverkehr behandeln.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="2d5f4-122">**Abbildung 1: Empfohlene Konfiguration für Microsoft SaaS-Datenverkehr für alle Büros**</span><span class="sxs-lookup"><span data-stu-id="2d5f4-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Abbildung 1: Empfohlene Konfiguration für Microsoft SaaS-Datenverkehr für alle Büros](media/Network-Poster/SaaS1.png)

<span data-ttu-id="2d5f4-124">Abbildung 1 zeigt die empfohlene Konfiguration aller Büros, einschließlich Zweigstellen und regionalen oder zentralen, in denen:</span><span class="sxs-lookup"><span data-stu-id="2d5f4-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="2d5f4-125">**Standard** Kategorie und allgemeiner Internet Datenverkehr werden an Büros mit Proxyservern und anderen edgegeräte weitergeleitet, um den Schutz vor internetbasierten Sicherheitsrisiken zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="2d5f4-126">**Optimieren** und **zulassen** der Kategorie-Datenverkehr wird direkt an den Rand des Microsoft-Netzwerk-Front-Ends in der Nähe des Büros weitergeleitet, das den Verbindungsbenutzer enthält, wobei Proxy Server und andere edgegeräte umgangen werden.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="2d5f4-127">Software definierte WAN-Geräte (Wide Area Network) in Zweigstellen trennen den Datenverkehr so, dass:</span><span class="sxs-lookup"><span data-stu-id="2d5f4-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="2d5f4-128">Die **Standard** Kategorie und der allgemeine Internet Datenverkehr gehen über das WAN-Backbone an eine zentrale oder regionale Niederlassung.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="2d5f4-129">**Optimieren** und **zulassen** der Kategorie-Datenverkehr wird an den ISP gesendet, der die lokale Internet Verbindung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="2d5f4-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="2d5f4-130">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="2d5f4-130">For more information, see:</span></span>
  
- [<span data-ttu-id="2d5f4-131">Prinzipien der Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="2d5f4-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="2d5f4-132">Netzwerk- und Migrationsplanung für Office 365</span><span class="sxs-lookup"><span data-stu-id="2d5f4-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="2d5f4-133">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="2d5f4-133">Next step</span></span>

[<span data-ttu-id="2d5f4-134">Entwerfen von Netzwerken für Microsoft-PaaS</span><span class="sxs-lookup"><span data-stu-id="2d5f4-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="2d5f4-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2d5f4-135">See also</span></span>

[<span data-ttu-id="2d5f4-136">Microsoft-Cloudnetzwerke für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="2d5f4-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="2d5f4-137">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="2d5f4-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

