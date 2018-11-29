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
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872266"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="ce5a2-103">Entwerfen von Netzwerken für Microsoft-SaaS</span><span class="sxs-lookup"><span data-stu-id="ce5a2-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="ce5a2-104">**Zusammenfassung:** Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="ce5a2-105">Optimieren Ihr Netzwerk für Microsoft SaaS Services erfordert die Konfiguration der internen und Edge-Geräte die verschiedenen Arten von Datenverkehr an Microsoft SaaS Services weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="ce5a2-106">Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste</span><span class="sxs-lookup"><span data-stu-id="ce5a2-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="ce5a2-107">Befolgen Sie diese Schritte, um Ihr Netzwerk für Microsoft SaaS-Dienste zu optimieren:</span><span class="sxs-lookup"><span data-stu-id="ce5a2-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="ce5a2-108">Durchlaufen Sie die **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud Services** in [Gemeinsame Elemente der Microsoft-Cloudkonnektivität](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="ce5a2-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="ce5a2-109">Fügen Sie eine Internet-Verbindung an alle Ihre Büros.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="ce5a2-110">Stellen Sie sicher, dass der Internetdienstanbieter für alle Internet-Verbindungen mit einem lokalen IP-Adresse einen DNS-Server verwenden.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="ce5a2-111">Untersuchen Sie Ihr Netzwerk Hairpins, temporären Zieladressen wie cloudbasierten Sicherheitsdienste und beseitigen Sie, sofern möglich.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="ce5a2-112">Konfigurieren der Edge-Geräten umgehen Verarbeitung für das Optimieren und Kategorien von Microsoft SaaS Datenverkehr zulassen.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="ce5a2-113">Optimieren der Datenverkehr zu Microsofts SaaS-Diensten</span><span class="sxs-lookup"><span data-stu-id="ce5a2-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="ce5a2-114">Es gibt drei Kategorien von Microsoft SaaS Datenverkehr:</span><span class="sxs-lookup"><span data-stu-id="ce5a2-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="ce5a2-115">Optimieren</span><span class="sxs-lookup"><span data-stu-id="ce5a2-115">Optimize</span></span>

  <span data-ttu-id="ce5a2-116">Für die Verbindung mit jedem Microsoft SaaS Service und darstellen über 75 % der Microsoft SaaS Bandbreite, Verbindungen und Menge der Daten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="ce5a2-117">Zulassen</span><span class="sxs-lookup"><span data-stu-id="ce5a2-117">Allow</span></span>

  <span data-ttu-id="ce5a2-118">Erforderlich für Verbindung mit bestimmten Microsoft SaaS Dienste und features sind jedoch nicht als vertraulich Leistung des Netzwerks und Wartezeit, die in der Kategorie optimieren.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="ce5a2-119">Standard</span><span class="sxs-lookup"><span data-stu-id="ce5a2-119">Default</span></span>

  <span data-ttu-id="ce5a2-p101">Darstellen Sie SaaS Microsoft Services und Abhängigkeiten, die kein Optimierung erfordern. Sie können die Standardeinstellung Kategorie Datenverkehr wie normale Datenverkehr im Internet behandeln.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="ce5a2-122">**Abbildung 1: Empfohlene Konfiguration für Microsoft SaaS-Datenverkehr für alle Büros**</span><span class="sxs-lookup"><span data-stu-id="ce5a2-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Abbildung 1: Empfohlene Konfiguration für Microsoft SaaS-Datenverkehr für alle Büros](media/Network-Poster/SaaS1.png)

<span data-ttu-id="ce5a2-124">Abbildung 1 zeigt die empfohlene Konfiguration von allen Büros, einschließlich Zweigstellen und regionalen oder zentralen Unterhaltungen in die:</span><span class="sxs-lookup"><span data-stu-id="ce5a2-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="ce5a2-125">**Standard** -Kategorie sowie allgemeine Internet-Datenverkehr an Büros, die Proxy-Server und andere Geräte Edge zum Schutz vor Sicherheitsrisiken internetbasierten weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="ce5a2-126">**Optimieren** und **Zulassen** Kategorie Datenverkehr wird direkt an den Rand des Microsoft Network Front-End Rechtsklicks am nächsten ist, die die enthält verbinden, Proxy-Server und andere Geräte Edge umgehen Büro weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="ce5a2-127">WAN-Software definiert (SD-WAN) Netzwerkgeräte in Zweigstellen Datenverkehr zu trennen, damit:</span><span class="sxs-lookup"><span data-stu-id="ce5a2-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="ce5a2-128">**Standard** -Kategorie sowie allgemeine Internet-Datenverkehr wird zu einem zentralen / regionalen Office über das WAN-Backbone.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="ce5a2-129">**Optimieren** und **Zulassen** Kategorie-Datenverkehr wird an den Internetdienstanbieter, die Internet-Verbindung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ce5a2-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="ce5a2-130">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="ce5a2-130">For more information, see:</span></span>
  
- [<span data-ttu-id="ce5a2-131">Netzwerk-Konnektivität Prinzipien</span><span class="sxs-lookup"><span data-stu-id="ce5a2-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="ce5a2-132">Netzwerk- und Migrationsplanung für Office 365</span><span class="sxs-lookup"><span data-stu-id="ce5a2-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="ce5a2-133">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ce5a2-133">Next step</span></span>

[<span data-ttu-id="ce5a2-134">Entwerfen von Netzwerken für Microsoft-PaaS</span><span class="sxs-lookup"><span data-stu-id="ce5a2-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="ce5a2-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ce5a2-135">See also</span></span>

[<span data-ttu-id="ce5a2-136">Microsoft-Cloudnetzwerke für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="ce5a2-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="ce5a2-137">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="ce5a2-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

