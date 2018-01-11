---
title: Von Grund auf neu aufgebaut
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
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "Zusammenfassung: Informieren Sie sich auf dem Satz von Cloud Speicher Bausteine, zu denen Sie zum Erstellen Ihrer eigenen Speicherdienst oder eine bestimmte Lösung verwenden können."
ms.openlocfilehash: eabf38e0ccef3335b2d198a33f5622d0d449589a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="f7f7e-103">Von Grund auf neu aufgebaut</span><span class="sxs-lookup"><span data-stu-id="f7f7e-103">Build from the ground up</span></span>

 <span data-ttu-id="f7f7e-104">**Zusammenfassung:** Rufen Sie die Details zu den Satz von Cloud Speicher Bausteine, zu denen Sie zum Erstellen Ihrer eigenen Speicherdienst oder eine bestimmte Lösung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="f7f7e-105">Speicherlösungen vom Typ „Von Grund auf neu aufgebaut“ haben folgende Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="f7f7e-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="f7f7e-106">Können Sie Ihre eigene speicherlösung von Grund auf zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="f7f7e-107">Erfordert die Programmierung mithilfe der REST-APIs.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="f7f7e-108">Geben Sie die optimale Anpassung und Flexibilität.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="f7f7e-109">In den folgenden Abschnitten werden die Details der einzelnen „Von Grund auf neu aufgebaut“-Speicheroptionen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="f7f7e-110">Azure Storage (Files)</span><span class="sxs-lookup"><span data-stu-id="f7f7e-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="f7f7e-111">Features</span><span class="sxs-lookup"><span data-stu-id="f7f7e-111">Features</span></span>

- <span data-ttu-id="f7f7e-112">Vereinfacht das Verbringen von Legacyanwendungen in die Cloud</span><span class="sxs-lookup"><span data-stu-id="f7f7e-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="f7f7e-113">Bevorzugt Blobspeicher für neue Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="f7f7e-114">Kann aus einem virtuellen Azure-Computer eingebunden werden</span><span class="sxs-lookup"><span data-stu-id="f7f7e-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="f7f7e-115">Kann lokal mit SMB 3.0 eingebunden werden</span><span class="sxs-lookup"><span data-stu-id="f7f7e-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="f7f7e-116">Funktioniert mit Linux und Windows</span><span class="sxs-lookup"><span data-stu-id="f7f7e-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="f7f7e-117">Unterstützt keine Azure AD-basierte Authentifizierung oder ACLs (Azure-Speicher-Konto-Schlüsseln Authentifizierung und autorisierten Zugriff auf die Dateifreigabe bereitstellen)</span><span class="sxs-lookup"><span data-stu-id="f7f7e-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="f7f7e-118">Häufige Verwendungsweisen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-118">Common uses</span></span>

- <span data-ttu-id="f7f7e-119">Migrieren von Legacyanwendungen in die Cloud, die auf Dateifreigaben beruhen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="f7f7e-120">Gemeinsam verwendete Entwicklungs- und Testtools</span><span class="sxs-lookup"><span data-stu-id="f7f7e-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="f7f7e-121">Verteilte Apps können Protokolle, Diagnosedaten und Absturzabbilder speichern</span><span class="sxs-lookup"><span data-stu-id="f7f7e-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="f7f7e-122">Grundlegende Speicherszenarien</span><span class="sxs-lookup"><span data-stu-id="f7f7e-122">Key storage scenarios</span></span>

- <span data-ttu-id="f7f7e-123">Dateisicherung</span><span class="sxs-lookup"><span data-stu-id="f7f7e-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="f7f7e-124">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-124">Resources</span></span>

<span data-ttu-id="f7f7e-125">Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="f7f7e-126">Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="f7f7e-127">Azure Storage (Blobs)</span><span class="sxs-lookup"><span data-stu-id="f7f7e-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="f7f7e-128">Features</span><span class="sxs-lookup"><span data-stu-id="f7f7e-128">Features</span></span>

- <span data-ttu-id="f7f7e-129">Jedes Storage-Konto kann bis zu 500 TB enthalten (ein Abonnement kann mehrere Speicherkonten müssen)</span><span class="sxs-lookup"><span data-stu-id="f7f7e-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="f7f7e-130">Speicherkonten sind in Containern organisiert, die Blobs enthalten können und auf die Sicherheit angewendet werden kann</span><span class="sxs-lookup"><span data-stu-id="f7f7e-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="f7f7e-131">Blockblobs sind für das Streamen und Speichern von Cloudobjekten mit bis zu 200 GB optimiert</span><span class="sxs-lookup"><span data-stu-id="f7f7e-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="f7f7e-132">Seitenblobs sind für das Darstellen von PaaS-Datenträgern bis zu 1 TB optimiert und unterstützen ungeordnete Schreibvorgänge</span><span class="sxs-lookup"><span data-stu-id="f7f7e-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="f7f7e-133">Anfügeblobs sind für Anfügevorgänge bis zu 195 GB optimiert</span><span class="sxs-lookup"><span data-stu-id="f7f7e-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="f7f7e-134">Premium Storage bietet aufgrund von SSD-Speicher schnellere IOPS</span><span class="sxs-lookup"><span data-stu-id="f7f7e-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="f7f7e-135">Häufige Verwendungsweisen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-135">Common uses</span></span>

- <span data-ttu-id="f7f7e-136">Sicherungen von Dateien, Computern, Datenbanken und Geräte Bildern und Text für Webanwendungen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="f7f7e-137">Konfigurationsdaten für Cloudanwendungen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="f7f7e-138">Große Datenmengen, wie etwa Protokolle und andere große Datasets</span><span class="sxs-lookup"><span data-stu-id="f7f7e-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="f7f7e-139">Azure verwendet Blobspeicher für seine eigenen Dienste, wie HDInsight und Datenträger von virtuellen Computern</span><span class="sxs-lookup"><span data-stu-id="f7f7e-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="f7f7e-140">Grundlegende Speicherszenarien</span><span class="sxs-lookup"><span data-stu-id="f7f7e-140">Key storage scenarios</span></span>

- <span data-ttu-id="f7f7e-141">Verwalten von Daten</span><span class="sxs-lookup"><span data-stu-id="f7f7e-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="f7f7e-142">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-142">Resources</span></span>

<span data-ttu-id="f7f7e-143">Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="f7f7e-144">Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="f7f7e-145">Azure Storage (Queues)</span><span class="sxs-lookup"><span data-stu-id="f7f7e-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="f7f7e-146">Features</span><span class="sxs-lookup"><span data-stu-id="f7f7e-146">Features</span></span>

- <span data-ttu-id="f7f7e-147">Speicherkonten können eine beliebige Anzahl Warteschlangen enthalten</span><span class="sxs-lookup"><span data-stu-id="f7f7e-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="f7f7e-148">Warteschlangen können eine beliebige Anzahl Nachrichten enthalten (bis das Speicherkonto voll ist)</span><span class="sxs-lookup"><span data-stu-id="f7f7e-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="f7f7e-149">Nachrichten in Warteschlangen werden nach 7 Tagen automatisch gelöscht, wenn sie nicht abgerufen und von einer Anwendung gelöscht werden</span><span class="sxs-lookup"><span data-stu-id="f7f7e-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="f7f7e-150">Nachrichten können bis zu 64 KB groß sein.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="f7f7e-151">Auf Speicherkontoebene gesichert</span><span class="sxs-lookup"><span data-stu-id="f7f7e-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="f7f7e-152">Warteschlangen sind für die Übergabe von Steuerungsnachrichten vorgesehen, nicht von Rohdaten</span><span class="sxs-lookup"><span data-stu-id="f7f7e-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="f7f7e-153">Häufige Verwendungsweisen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-153">Common uses</span></span>

- <span data-ttu-id="f7f7e-154">Erstellen eines Backlogs der Arbeit für die asynchrone Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="f7f7e-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="f7f7e-155">Verarbeiten von Protokollnachrichten</span><span class="sxs-lookup"><span data-stu-id="f7f7e-155">Processing log messages</span></span>
    
- <span data-ttu-id="f7f7e-156">Entkoppeln von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="f7f7e-157">Grundlegende Speicherszenarien</span><span class="sxs-lookup"><span data-stu-id="f7f7e-157">Key storage scenarios</span></span>

- <span data-ttu-id="f7f7e-158">Verteilen von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="f7f7e-159">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-159">Resources</span></span>

<span data-ttu-id="f7f7e-160">Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="f7f7e-161">Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="f7f7e-162">Azure Storage (Tables)</span><span class="sxs-lookup"><span data-stu-id="f7f7e-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="f7f7e-163">Features</span><span class="sxs-lookup"><span data-stu-id="f7f7e-163">Features</span></span>

- <span data-ttu-id="f7f7e-164">Optimal für teilstrukturierte Datasets geeignet</span><span class="sxs-lookup"><span data-stu-id="f7f7e-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="f7f7e-165">Normalerweise geringere Kosten als traditionelles SQL</span><span class="sxs-lookup"><span data-stu-id="f7f7e-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="f7f7e-166">Sehr schnell, wenn Abfragen für Schlüssel beeinträchtigt, wenn Wert Abfragen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="f7f7e-167">Hochgradig skalierbar; beliebige Mengen von Tabellen bis zur Grenze des Speicherkontos</span><span class="sxs-lookup"><span data-stu-id="f7f7e-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="f7f7e-168">Zugriff über REST-API, eingeschränktes oData-Protokoll, .NET</span><span class="sxs-lookup"><span data-stu-id="f7f7e-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="f7f7e-169">Werte müssen serialisiert werden</span><span class="sxs-lookup"><span data-stu-id="f7f7e-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="f7f7e-170">Häufige Verwendungsweisen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-170">Common uses</span></span>

- <span data-ttu-id="f7f7e-171">Benutzerdaten für Webanwendungen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-171">User data for web applications</span></span>
    
- <span data-ttu-id="f7f7e-172">Adressbücher</span><span class="sxs-lookup"><span data-stu-id="f7f7e-172">Address books</span></span>
    
- <span data-ttu-id="f7f7e-173">Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="f7f7e-174">Grundlegende Speicherszenarien</span><span class="sxs-lookup"><span data-stu-id="f7f7e-174">Key storage scenarios</span></span>

- <span data-ttu-id="f7f7e-175">Verwalten von Daten</span><span class="sxs-lookup"><span data-stu-id="f7f7e-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="f7f7e-176">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-176">Resources</span></span>

<span data-ttu-id="f7f7e-177">Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="f7f7e-178">Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="f7f7e-179">Microsoft Azure Storage-Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="f7f7e-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="f7f7e-180">Beachten Sie beim Entwerfen Ihrer benutzerdefinierten Speicherlösung mit Azure Storage Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f7f7e-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="f7f7e-181">Nutzen Sie mehrere Speicherkonten, um größere Skalierbarkeit zu erzielen, entweder in Richtung Größe (> 100 TB) oder Durchsatz (> 5.000 Operationen pro Sekunde).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="f7f7e-182">Planen Sie die Möglichkeit zum Hinzufügen weiterer Speicherkonten als Änderung der Konfiguration, nicht des Codes.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="f7f7e-183">Wählen Sie sorgfältig Partitionierungsfunktionen für Tabellenspeicher aus, um das gewünschte Maß an Einfüge- und Abfrageleistung zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="f7f7e-184">Wählen Sie kurze Spaltennamen für Tabelleneigenschaften aus, da die Metadaten (Eigenschaftsnamen) In-Band gespeichert werden (die Spaltennamen werden bei der maximalen Zeilengröße von 1 MB berücksichtigt).</span><span class="sxs-lookup"><span data-stu-id="f7f7e-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="f7f7e-185">Führen Sie nach Möglichkeit Batchvorgänge im Speicher aus.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="f7f7e-186">Speichern Sie Informationen in der Konfigurationsdatenbank konsequent in einem verteilten Cache zwischen.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="f7f7e-187">Wenn Anwendungsleistung oder Zuverlässigkeit von der Verfügbarkeit eines bestimmten Datensegments im Cache abhängt, sollte Ihre Anwendung eingehende Anforderungen bis zum Abschluss der Vorauffüllung des Caches abweisen.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="f7f7e-188">Partitionieren Sie die Daten entweder vertikal (nach Tabellen) oder horizontal (über mehrere Shards segmentierte Tabellen), um die Auslastung auf mehrere Datenbanken zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="f7f7e-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="f7f7e-189">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="f7f7e-189">See Also</span></span>

[<span data-ttu-id="f7f7e-190">Microsoft-Cloud-Speicher für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="f7f7e-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="f7f7e-191">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="f7f7e-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f7f7e-192">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="f7f7e-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



