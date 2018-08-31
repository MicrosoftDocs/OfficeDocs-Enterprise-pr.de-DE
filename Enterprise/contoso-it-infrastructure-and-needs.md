---
title: >
  Contosos IT-Infrastruktur und -Anforderungen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: 'Zusammenfassung: Hier erfahren Sie die grundlegende Struktur des Contoso lokale IT-Infrastruktur und wie die Geschäftsabläufe durch Cloudlösungen von Microsoft erfüllt werden können muss.'
ms.openlocfilehash: e500aa1f3105c1e605d0d3c1d5f66651acb82b34
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915730"
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="a7dc7-103">Contosos IT-Infrastruktur und -Anforderungen
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="a7dc7-104">**Zusammenfassung:** Verstehen der grundlegenden Struktur des Contoso lokale IT-Infrastruktur und wie die Geschäftsabläufe durch Cloudlösungen von Microsoft erfüllt werden können muss.</span><span class="sxs-lookup"><span data-stu-id="a7dc7-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="a7dc7-105">Contoso ist dabei, von der lokalen zentralen IT-Infrastruktur auf eine cloudeinschließende Infrastruktur umzustellen, die aus cloudbasierten persönlichen Produktivitätsarbeitslasten, Anwendungen und Hybridszenarien besteht.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="a7dc7-106">Contosos vorhandene IT-Infrastruktur
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="a7dc7-107">Contoso nutzt eine weitestgehend zentrale lokale IT-Infrastruktur mit Anwendungsrechenzentren in der Pariser Zentrale.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="a7dc7-108">**Abbildung 1: Contosos vorhandene IT-Infrastruktur
**</span><span class="sxs-lookup"><span data-stu-id="a7dc7-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![<span data-ttu-id="a7dc7-109">Contosos vorhandene IT-Infrastruktur
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-109">Contoso's existing IT infrastructure</span></span>](media/Contoso-Poster/Existing-IT.png)
  
<span data-ttu-id="a7dc7-110">Abbildung 1 zeigt eine Unternehmenszentrale mit Anwendungsrechenzentren, einer DMZ und Internet.</span><span class="sxs-lookup"><span data-stu-id="a7dc7-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="a7dc7-111">Geben Contoso DMZ verschiedene Sätze von Servern:</span><span class="sxs-lookup"><span data-stu-id="a7dc7-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="a7dc7-112">Remotezugriff auf das Contoso-Intranet und Webproxyfunktion für Mitarbeiter in der Pariser Zentrale</span><span class="sxs-lookup"><span data-stu-id="a7dc7-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="a7dc7-113">Hosting der öffentlichen Contoso-Website, über die Kunden Produkte, Teile oder Zubehör bestellen können</span><span class="sxs-lookup"><span data-stu-id="a7dc7-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="a7dc7-114">Hosting für das Contoso-Partnerextranet für die Kommunikation und Zusammenarbeit mit Partnern</span><span class="sxs-lookup"><span data-stu-id="a7dc7-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="a7dc7-115">Contoso geschäftlichen Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a7dc7-115">Contoso's business needs</span></span>

<span data-ttu-id="a7dc7-116">Nachfolgend sehen Sie die Geschäftsanforderungen von Contoso in der Reihenfolge ihrer Priorität:</span><span class="sxs-lookup"><span data-stu-id="a7dc7-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="a7dc7-117">Einhalten von regionalen gesetzlichen Vorschriften</span><span class="sxs-lookup"><span data-stu-id="a7dc7-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="a7dc7-118">Um Strafen zu verhindern und gute Beziehungen zu lokalen Behörden beizubehalten, muss Contoso die Einhaltung von Vorschriften zur Datenspeicherung- und -verschlüsselung sicherstellen.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="a7dc7-119">Verbessern der Verwaltung von Lieferanten und Partnern
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="a7dc7-p101">Das Partnerextranet ist in die Jahre gekommen und teuer in der Wartung. Contoso möchte es durch eine cloudbasierte Lösung ersetzen, für die Verbundauthentifizierung verwendet wird.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="a7dc7-122">Verbessern von Produktivität, Geräteverwaltung und Zugriff für Mobilmitarbeiter
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="a7dc7-123">Contoso Mobile-only Belegschaft wird erweitert und benötigt Gerätemanagement zum Schutz des geistigen Eigentums und effizienter Zugriff auf Ressourcen zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="a7dc7-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="a7dc7-124">Verkleinern der Remotezugriffsinfrastruktur
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="a7dc7-125">Durch Verschieben von Ressourcen, auf die häufig von Remotearbeitskräften zugegriffen wird, in die Cloud spart Contoso Geld, indem die Kosten für Wartung und Support der Remotezugriffslösung verringert werden.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="a7dc7-126">Verkleinern von lokalen Rechenzentren

</span><span class="sxs-lookup"><span data-stu-id="a7dc7-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="a7dc7-127">Die Contoso-Rechenzentren umfassen Hunderte von Servern, von denen einige für ältere oder Archivierungsfunktionen genutzt werden, was dazu führt, dass IT-Mitarbeiter davon abgehalten werden, Arbeitslasten mit hohem Geschäftswert zu betreuen.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="a7dc7-128">Vergrößern der Berechnungs- und Speicherressourcen für Quartalsabschlüsse
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="a7dc7-129">Quartalsabschlüsse und Prognoseverarbeitung zusammen mit Bestandsverwaltung erfordern kurzfristig mehr Server und Speicher.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="a7dc7-130">Zuordnen Contosos Business muss Cloudlösungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="a7dc7-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="a7dc7-131">Basierend auf einer Analyse der Microsoft-Cloudangebote hat die IT-Abteilung von Contoso die folgende Zuordnung festgelegt:</span><span class="sxs-lookup"><span data-stu-id="a7dc7-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="a7dc7-132">**Software as a Service (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="a7dc7-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="a7dc7-133">**Plattform als Dienst (Azure PaaS)**</span><span class="sxs-lookup"><span data-stu-id="a7dc7-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="a7dc7-134">**Infrastructure as a Service (Azure IaaS)**</span><span class="sxs-lookup"><span data-stu-id="a7dc7-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="a7dc7-135">**Office 365:** Hauptanwendungen für persönliche und Gruppenproduktivität in der Cloud.</span><span class="sxs-lookup"><span data-stu-id="a7dc7-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="a7dc7-136">Geschäftsanforderungen: 1 3 5</span><span class="sxs-lookup"><span data-stu-id="a7dc7-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="a7dc7-137">Hosten von Verkaufs- und Supportdokumenten sowie Informationssystemen mit cloudbasierten Apps.



</span><span class="sxs-lookup"><span data-stu-id="a7dc7-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="a7dc7-138">Geschäftliche Anforderung: 3</span><span class="sxs-lookup"><span data-stu-id="a7dc7-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="a7dc7-139">Verschieben von Archivierungs und Legacysystemen auf cloudbasierte Server.





</span><span class="sxs-lookup"><span data-stu-id="a7dc7-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="a7dc7-140">Geschäftliche Anforderung: 5</span><span class="sxs-lookup"><span data-stu-id="a7dc7-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="a7dc7-p102">**Dynamics 365:** Verwenden einer cloudbasierten Kunden- und Lieferantenverwaltung. Entfernen des Partnerextranets aus der DMZ.</span><span class="sxs-lookup"><span data-stu-id="a7dc7-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="a7dc7-143">Geschäftliche Anforderung: 2</span><span class="sxs-lookup"><span data-stu-id="a7dc7-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="a7dc7-144">Mobile Anwendungen sind cloudbasiert, statt von Pariser Datenzentren bereitgestellt zu werden.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="a7dc7-145">Geschäftliche Anforderungen: 3 4</span><span class="sxs-lookup"><span data-stu-id="a7dc7-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="a7dc7-146">Migrieren von wenig verwendeten Apps und Daten aus lokalen Rechenzentren.</span><span class="sxs-lookup"><span data-stu-id="a7dc7-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="a7dc7-147">Geschäftliche Anforderung: 5</span><span class="sxs-lookup"><span data-stu-id="a7dc7-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="a7dc7-148">**Intune/zur Abstimmung:** Verwalten von iOS und Android-Geräte.</span><span class="sxs-lookup"><span data-stu-id="a7dc7-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="a7dc7-149">Geschäftliche Anforderung: 3</span><span class="sxs-lookup"><span data-stu-id="a7dc7-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="a7dc7-150">Hinzufügen von temporären Servern und temporärem Speicher für Anforderungen aus einem Quartalsabschluss.
</span><span class="sxs-lookup"><span data-stu-id="a7dc7-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="a7dc7-151">Geschäftliche Anforderung: 6</span><span class="sxs-lookup"><span data-stu-id="a7dc7-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="a7dc7-152">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a7dc7-152">See Also</span></span>

[<span data-ttu-id="a7dc7-153">Contoso in der Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="a7dc7-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="a7dc7-154">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="a7dc7-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="a7dc7-155">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="a7dc7-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


