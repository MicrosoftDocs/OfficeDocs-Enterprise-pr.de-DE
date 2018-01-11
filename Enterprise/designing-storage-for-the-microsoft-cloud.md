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
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "Zusammenfassung: Erfahren Sie, warum Sie Cloudspeicher benötigen, und lernen Sie die Cloudspeicheroptionen von Microsoft und die wichtigsten Speicherszenarios kennen."
ms.openlocfilehash: 199e385ea0238e8fb27c04153faf177df07e1025
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="e1ead-103">Entwerfen von Speicher für die Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="e1ead-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="e1ead-104">**Zusammenfassung:** Erfahren Sie, warum Sie Cloudspeicher benötigen, und lernen Sie die Cloudspeicheroptionen von Microsoft und die wichtigsten Speicherszenarios kennen.</span><span class="sxs-lookup"><span data-stu-id="e1ead-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="e1ead-105">Das Integrieren Ihres Speichers im Microsoft Cloud Services gibt Ihnen Zugriff auf eine große Bandbreite an Diensten und Cloudplattformoptionen.</span><span class="sxs-lookup"><span data-stu-id="e1ead-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="e1ead-106">Warum Cloudspeicher?</span><span class="sxs-lookup"><span data-stu-id="e1ead-106">Why cloud storage?</span></span>

<span data-ttu-id="e1ead-107">Es gibt zwei wichtigsten Gründe für die Verwendung von Cloudspeicher.</span><span class="sxs-lookup"><span data-stu-id="e1ead-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="e1ead-108">Schnelle Markteinführung</span><span class="sxs-lookup"><span data-stu-id="e1ead-108">Speed to market:</span></span>
    
  - <span data-ttu-id="e1ead-109">Schnellere Konfiguration für hohe Verfügbarkeit und Notfallwiederherstellung</span><span class="sxs-lookup"><span data-stu-id="e1ead-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="e1ead-110">Keine zu erwerbende Speicherhardware</span><span class="sxs-lookup"><span data-stu-id="e1ead-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="e1ead-111">Integrierte Wartung, bereitgestellt durch die Microsoft Cloudangebote</span><span class="sxs-lookup"><span data-stu-id="e1ead-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="e1ead-112">An jedem Ort der Welt verfügbar</span><span class="sxs-lookup"><span data-stu-id="e1ead-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="e1ead-113">Niedrigere Betriebskosten:</span><span class="sxs-lookup"><span data-stu-id="e1ead-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="e1ead-114">Elastizität zum Hoch- und Herunterskalieren Ihrer Speicheranforderungen</span><span class="sxs-lookup"><span data-stu-id="e1ead-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="e1ead-115">Keine zu wartende oder migrierende Speicherhardware</span><span class="sxs-lookup"><span data-stu-id="e1ead-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="e1ead-116">Integrierte Wartung zur Aufrechterhaltung und Verbesserung der Infrastruktur durch Microsoft</span><span class="sxs-lookup"><span data-stu-id="e1ead-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="e1ead-117">Beste Speichersicherheit auf dem Markt mit fortlaufenden Verbesserungen</span><span class="sxs-lookup"><span data-stu-id="e1ead-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="e1ead-118">Microsoft-Cloudspeicheroptionen</span><span class="sxs-lookup"><span data-stu-id="e1ead-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="e1ead-119">Zur Veranschaulichung der Vielzahl verschiedener Cloudspeicheroptionen verwenden wir eine Konstruktionsanalogie.</span><span class="sxs-lookup"><span data-stu-id="e1ead-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="e1ead-120">Schlüsselfertig</span><span class="sxs-lookup"><span data-stu-id="e1ead-120">Move-in ready</span></span>

<span data-ttu-id="e1ead-p101">Verwenden Sie diese fertig konfektionierten Lösungen, die mit vorhandenen Diensten gebündelt sind. Sofort und mit einem Minimum an Konfiguration einsetzbar.</span><span class="sxs-lookup"><span data-stu-id="e1ead-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="e1ead-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="e1ead-123">Office 365</span></span>
    
- <span data-ttu-id="e1ead-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="e1ead-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="e1ead-125">OneDrive für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="e1ead-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="e1ead-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="e1ead-126">Dynamics 365</span></span>
    
- <span data-ttu-id="e1ead-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="e1ead-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="e1ead-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="e1ead-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="e1ead-129">Yammer Site Sharing</span><span class="sxs-lookup"><span data-stu-id="e1ead-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="e1ead-130">Azure Backup</span><span class="sxs-lookup"><span data-stu-id="e1ead-130">Azure Backup</span></span>
    
<span data-ttu-id="e1ead-131">Details zu den einzelnen Cloudspeicheroptionen finden Sie unter [Schlüsselfertig](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="e1ead-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="e1ead-132">Assemblierung in Maßen erforderlich</span><span class="sxs-lookup"><span data-stu-id="e1ead-132">Some assembly required</span></span>

<span data-ttu-id="e1ead-133">Verwenden Sie diese vorhandenen Dienste als Ausgangspunkt für Ihre Speicherlösung mit zusätzlicher Konfiguration oder Codierung für die bedarfsgerechte Passform.</span><span class="sxs-lookup"><span data-stu-id="e1ead-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="e1ead-134">Azure Content Delivery Network</span><span class="sxs-lookup"><span data-stu-id="e1ead-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="e1ead-135">Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="e1ead-135">Azure Media Services</span></span>
    
- <span data-ttu-id="e1ead-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="e1ead-136">HdInsight</span></span>
    
- <span data-ttu-id="e1ead-137">Azure Redis Cache</span><span class="sxs-lookup"><span data-stu-id="e1ead-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="e1ead-138">Azure SQL-Datenbank</span><span class="sxs-lookup"><span data-stu-id="e1ead-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="e1ead-139">SQL Server auf einer Azure-VM</span><span class="sxs-lookup"><span data-stu-id="e1ead-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="e1ead-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="e1ead-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="e1ead-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="e1ead-141">StorSimple</span></span>
    
- <span data-ttu-id="e1ead-142">Azure SQL Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="e1ead-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="e1ead-143">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="e1ead-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="e1ead-144">Details zu den einzelnen Cloudspeicheroptionen finden Sie unter [Assemblierung in Maßen erforderlich](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="e1ead-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="e1ead-145">Von Grund auf neu aufgebaut</span><span class="sxs-lookup"><span data-stu-id="e1ead-145">Build from the ground up</span></span>

<span data-ttu-id="e1ead-146">Verwenden Sie diese Speicherbausteine in Kombination mit Codeerstellung, um von Grund auf eigene Speicherlösungen oder Apps zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e1ead-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="e1ead-147">Azure Storage (Files)</span><span class="sxs-lookup"><span data-stu-id="e1ead-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="e1ead-148">Azure Storage (Blobs)</span><span class="sxs-lookup"><span data-stu-id="e1ead-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="e1ead-149">Azure Storage (Queues)</span><span class="sxs-lookup"><span data-stu-id="e1ead-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="e1ead-150">Azure Storage (Tables)</span><span class="sxs-lookup"><span data-stu-id="e1ead-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="e1ead-151">Details zu den einzelnen Cloudspeicheroptionen finden Sie unter [Von Grund auf neu aufgebaut](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="e1ead-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="e1ead-152">Grundlegende Speicherszenarien</span><span class="sxs-lookup"><span data-stu-id="e1ead-152">Key storage scenarios</span></span>

<span data-ttu-id="e1ead-153">Dies sind die wichtigen Szenarios, die cloudbasierten Speicher benötigen:</span><span class="sxs-lookup"><span data-stu-id="e1ead-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="e1ead-154">Zwischenspeichern von Daten</span><span class="sxs-lookup"><span data-stu-id="e1ead-154">Cache data</span></span>
    
    <span data-ttu-id="e1ead-155">Beschleunigen Sie den Zugriff auf häufig verwendete Daten durch Speicherung in einem Hochgeschwindigkeitscache.</span><span class="sxs-lookup"><span data-stu-id="e1ead-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="e1ead-156">Zusammenarbeit mit Teammitgliedern</span><span class="sxs-lookup"><span data-stu-id="e1ead-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="e1ead-157">Erteilen Sie mehreren Benutzern die Berechtigung, den Zugriff auf Daten in einem Cloudspeicher zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="e1ead-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="e1ead-158">Verwalten von Daten</span><span class="sxs-lookup"><span data-stu-id="e1ead-158">Manage data</span></span>
    
    <span data-ttu-id="e1ead-159">Speichern, verschieben oder löschen Sie interne oder externe Massendaten.</span><span class="sxs-lookup"><span data-stu-id="e1ead-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="e1ead-160">Quellcodeverwaltung</span><span class="sxs-lookup"><span data-stu-id="e1ead-160">Manage source code</span></span>
    
    <span data-ttu-id="e1ead-161">Laden Sie Anwendungscodedateien in die Cloud hoch, arbeiten Sie gemeinsam daran, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="e1ead-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="e1ead-162">Dateisicherung</span><span class="sxs-lookup"><span data-stu-id="e1ead-162">Backup files</span></span>
    
    <span data-ttu-id="e1ead-163">Speichern Sie Kopien von internen oder externen Daten an mehreren Cloudspeicherorten.</span><span class="sxs-lookup"><span data-stu-id="e1ead-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="e1ead-164">Veröffentlichen von  Unternehmenskommunikation</span><span class="sxs-lookup"><span data-stu-id="e1ead-164">Publish company communications</span></span>
    
    <span data-ttu-id="e1ead-165">Erstellen Sie einen zentralen Ort für die Veröffentlichung von internen oder externen Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="e1ead-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="e1ead-166">Millionenfaches Verteilen von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="e1ead-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="e1ead-167">Erstellen Sie Speicher für die Erfassung von Telemetriedaten von Websites, Apps und Geräten.</span><span class="sxs-lookup"><span data-stu-id="e1ead-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="e1ead-168">Verwalten/Übermitteln von Videos</span><span class="sxs-lookup"><span data-stu-id="e1ead-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="e1ead-169">Speichern und liefern Sie Videoinhalte für Kunden oder Benutzer der Organisation.</span><span class="sxs-lookup"><span data-stu-id="e1ead-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="e1ead-170">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="e1ead-170">Next step</span></span>

<span data-ttu-id="e1ead-171">Sehen Sie sich die Cloudspeicheroptionen vom Typ „[Schlüsselfertig](move-in-ready.md)" an.</span><span class="sxs-lookup"><span data-stu-id="e1ead-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1ead-172">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="e1ead-172">See Also</span></span>

[<span data-ttu-id="e1ead-173">Microsoft-Cloud-Speicher für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="e1ead-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="e1ead-174">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="e1ead-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="e1ead-175">[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="e1ead-175">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>


