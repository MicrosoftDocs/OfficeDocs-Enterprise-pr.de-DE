---
title: "Entwerfen von Speicher für die Microsoft-Cloud"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "Zusammenfassung: Erfahren Sie, warum Sie Cloudspeicher benötigen, und lernen Sie die Cloudspeicheroptionen von Microsoft und die wichtigsten Speicherszenarios kennen."
ms.openlocfilehash: 3501f6a39498276d02fe4178f701a06dfb6a3e93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="76513-103">Entwerfen von Speicher für die Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="76513-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="76513-104">**Zusammenfassung:** Erfahren Sie, warum Sie Cloudspeicher benötigen, und lernen Sie die Cloudspeicheroptionen von Microsoft und die wichtigsten Speicherszenarios kennen.</span><span class="sxs-lookup"><span data-stu-id="76513-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="76513-105">Das Integrieren Ihres Speichers im Microsoft Cloud Services gibt Ihnen Zugriff auf eine große Bandbreite an Diensten und Cloudplattformoptionen.</span><span class="sxs-lookup"><span data-stu-id="76513-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="76513-106">Warum Cloudspeicher?</span><span class="sxs-lookup"><span data-stu-id="76513-106">Why cloud storage?</span></span>

<span data-ttu-id="76513-107">Es gibt zwei wichtigsten Gründe für die Verwendung von Cloudspeicher.</span><span class="sxs-lookup"><span data-stu-id="76513-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="76513-108">Schnelle Markteinführung</span><span class="sxs-lookup"><span data-stu-id="76513-108">Speed to market:</span></span>
    
  - <span data-ttu-id="76513-109">Schnellere Konfiguration für hohe Verfügbarkeit und Notfallwiederherstellung</span><span class="sxs-lookup"><span data-stu-id="76513-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="76513-110">Keine zu erwerbende Speicherhardware</span><span class="sxs-lookup"><span data-stu-id="76513-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="76513-111">Integrierte Wartung, bereitgestellt durch die Microsoft Cloudangebote</span><span class="sxs-lookup"><span data-stu-id="76513-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="76513-112">An jedem Ort der Welt verfügbar</span><span class="sxs-lookup"><span data-stu-id="76513-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="76513-113">Niedrigere Betriebskosten:</span><span class="sxs-lookup"><span data-stu-id="76513-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="76513-114">Elastizität zum Hoch- und Herunterskalieren Ihrer Speicheranforderungen</span><span class="sxs-lookup"><span data-stu-id="76513-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="76513-115">Keine zu wartende oder migrierende Speicherhardware</span><span class="sxs-lookup"><span data-stu-id="76513-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="76513-116">Integrierte Wartung zur Aufrechterhaltung und Verbesserung der Infrastruktur durch Microsoft</span><span class="sxs-lookup"><span data-stu-id="76513-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="76513-117">Beste Speichersicherheit auf dem Markt mit fortlaufenden Verbesserungen</span><span class="sxs-lookup"><span data-stu-id="76513-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="76513-118">Microsoft-Cloudspeicheroptionen</span><span class="sxs-lookup"><span data-stu-id="76513-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="76513-119">Zur Veranschaulichung der Vielzahl verschiedener Cloudspeicheroptionen verwenden wir eine Konstruktionsanalogie.</span><span class="sxs-lookup"><span data-stu-id="76513-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="76513-120">Schlüsselfertig</span><span class="sxs-lookup"><span data-stu-id="76513-120">Move-in ready</span></span>

<span data-ttu-id="76513-p101">Verwenden Sie diese fertig konfektionierten Lösungen, die mit vorhandenen Diensten gebündelt sind. Sofort und mit einem Minimum an Konfiguration einsetzbar.</span><span class="sxs-lookup"><span data-stu-id="76513-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="76513-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="76513-123">Office 365</span></span>
    
- <span data-ttu-id="76513-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="76513-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="76513-125">OneDrive für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="76513-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="76513-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="76513-126">Dynamics 365</span></span>
    
- <span data-ttu-id="76513-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="76513-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="76513-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="76513-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="76513-129">Yammer Site Sharing</span><span class="sxs-lookup"><span data-stu-id="76513-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="76513-130">Azure Backup</span><span class="sxs-lookup"><span data-stu-id="76513-130">Azure Backup</span></span>
    
<span data-ttu-id="76513-131">Details zu den einzelnen Cloudspeicheroptionen finden Sie unter [Schlüsselfertig](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="76513-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="76513-132">Assemblierung in Maßen erforderlich</span><span class="sxs-lookup"><span data-stu-id="76513-132">Some assembly required</span></span>

<span data-ttu-id="76513-133">Verwenden Sie diese vorhandenen Dienste als Ausgangspunkt für Ihre Speicherlösung mit zusätzlicher Konfiguration oder Codierung für die bedarfsgerechte Passform.</span><span class="sxs-lookup"><span data-stu-id="76513-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="76513-134">Azure Content Delivery Network</span><span class="sxs-lookup"><span data-stu-id="76513-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="76513-135">Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="76513-135">Azure Media Services</span></span>
    
- <span data-ttu-id="76513-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="76513-136">HdInsight</span></span>
    
- <span data-ttu-id="76513-137">Azure Redis Cache</span><span class="sxs-lookup"><span data-stu-id="76513-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="76513-138">Azure SQL-Datenbank</span><span class="sxs-lookup"><span data-stu-id="76513-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="76513-139">SQL Server auf einer Azure-VM</span><span class="sxs-lookup"><span data-stu-id="76513-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="76513-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="76513-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="76513-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="76513-141">StorSimple</span></span>
    
- <span data-ttu-id="76513-142">Azure SQL Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="76513-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="76513-143">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="76513-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="76513-144">Details zu den einzelnen Cloudspeicheroptionen finden Sie unter [Assemblierung in Maßen erforderlich](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="76513-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="76513-145">Von Grund auf neu aufgebaut</span><span class="sxs-lookup"><span data-stu-id="76513-145">Build from the ground up</span></span>

<span data-ttu-id="76513-146">Verwenden Sie diese Speicherbausteine in Kombination mit Codeerstellung, um von Grund auf eigene Speicherlösungen oder Apps zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="76513-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="76513-147">Azure Storage (Files)</span><span class="sxs-lookup"><span data-stu-id="76513-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="76513-148">Azure Storage (Blobs)</span><span class="sxs-lookup"><span data-stu-id="76513-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="76513-149">Azure Storage (Queues)</span><span class="sxs-lookup"><span data-stu-id="76513-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="76513-150">Azure Storage (Tables)</span><span class="sxs-lookup"><span data-stu-id="76513-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="76513-151">Details zu den einzelnen Cloudspeicheroptionen finden Sie unter [Von Grund auf neu aufgebaut](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="76513-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="76513-152">Die wichtigsten Speicherszenarios</span><span class="sxs-lookup"><span data-stu-id="76513-152">Key storage scenarios</span></span>

<span data-ttu-id="76513-153">Dies sind die wichtigen Szenarios, die cloudbasierten Speicher benötigen:</span><span class="sxs-lookup"><span data-stu-id="76513-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="76513-154">Zwischenspeichern von Daten</span><span class="sxs-lookup"><span data-stu-id="76513-154">Cache data</span></span>
    
    <span data-ttu-id="76513-155">Beschleunigen Sie den Zugriff auf häufig verwendete Daten durch Speicherung in einem Hochgeschwindigkeitscache.</span><span class="sxs-lookup"><span data-stu-id="76513-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="76513-156">Zusammenarbeit mit Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="76513-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="76513-157">Erteilen Sie mehreren Benutzern die Berechtigung, den Zugriff auf Daten in einem Cloudspeicher zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="76513-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="76513-158">Verwalten von Daten</span><span class="sxs-lookup"><span data-stu-id="76513-158">Manage data</span></span>
    
    <span data-ttu-id="76513-159">Speichern, verschieben oder löschen Sie interne oder externe Massendaten.</span><span class="sxs-lookup"><span data-stu-id="76513-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="76513-160">Quellcodeverwaltung</span><span class="sxs-lookup"><span data-stu-id="76513-160">Manage source code</span></span>
    
    <span data-ttu-id="76513-161">Laden Sie Anwendungscodedateien in die Cloud hoch, arbeiten Sie gemeinsam daran, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="76513-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="76513-162">Dateisicherung</span><span class="sxs-lookup"><span data-stu-id="76513-162">Backup files</span></span>
    
    <span data-ttu-id="76513-163">Speichern Sie Kopien von internen oder externen Daten an mehreren Cloudspeicherorten.</span><span class="sxs-lookup"><span data-stu-id="76513-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="76513-164">Veröffentlichen von Unternehmenskommunikation</span><span class="sxs-lookup"><span data-stu-id="76513-164">Publish company communications</span></span>
    
    <span data-ttu-id="76513-165">Erstellen Sie einen zentralen Ort für die Veröffentlichung von internen oder externen Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="76513-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="76513-166">Millionenfaches Verteilen von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="76513-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="76513-167">Erstellen Sie Speicher für die Erfassung von Telemetriedaten von Websites, Apps und Geräten.</span><span class="sxs-lookup"><span data-stu-id="76513-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="76513-168">Verwalten/Übermitteln von Videos</span><span class="sxs-lookup"><span data-stu-id="76513-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="76513-169">Speichern und liefern Sie Videoinhalte für Kunden oder Benutzer der Organisation.</span><span class="sxs-lookup"><span data-stu-id="76513-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="76513-170">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="76513-170">Next step</span></span>

<span data-ttu-id="76513-171">Sehen Sie sich die Cloudspeicheroptionen vom Typ „[Schlüsselfertig](move-in-ready.md)" an.</span><span class="sxs-lookup"><span data-stu-id="76513-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="76513-172">See Also</span><span class="sxs-lookup"><span data-stu-id="76513-172">See Also</span></span>

[<span data-ttu-id="76513-173">Microsoft-Cloud-Speicher für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="76513-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="76513-174">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="76513-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="76513-175">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="76513-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


