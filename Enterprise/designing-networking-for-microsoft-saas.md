---
title: "Entwerfen von Netzwerken für Microsoft-SaaS"
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Zusammenfassung: Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren."
ms.openlocfilehash: e4d83f9ab88408b3eb5ca98379bbc709ec8f31a7
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="18694-103">Entwerfen von Netzwerken für Microsoft-SaaS</span><span class="sxs-lookup"><span data-stu-id="18694-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="18694-104">**Zusammenfassung:** Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren.</span><span class="sxs-lookup"><span data-stu-id="18694-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="18694-105">Für die Optimierung Ihres Netzwerks für Microsoft-SaaS-Dienste ist eine sorgfältige Analyse von Internet-Edge, Ihrer Clientgeräte und IT-Standardvorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="18694-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="18694-106">Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste</span><span class="sxs-lookup"><span data-stu-id="18694-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="18694-107">Befolgen Sie diese Schritte, um Ihr Netzwerk für Microsoft SaaS-Dienste zu optimieren:</span><span class="sxs-lookup"><span data-stu-id="18694-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="18694-108">Durchlaufen Sie die **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud Services** in [Gemeinsame Elemente der Microsoft-Cloudkonnektivität](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="18694-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="18694-109">Optimieren Sie Ihren Internetausgang für Microsoft SaaS-Dienste mithilfe der Proxyserverempfehlungen.</span><span class="sxs-lookup"><span data-stu-id="18694-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="18694-110">Optimieren Sie Ihren Internetdurchsatz mithilfe der Empfehlungen für Näherung und Standort.</span><span class="sxs-lookup"><span data-stu-id="18694-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="18694-111">Optimieren Sie mithilfe der Überlegungen zur Clientnutzung die Leistung Ihrer Clientcomputer und des Intranets, in dem diese sich befinden.</span><span class="sxs-lookup"><span data-stu-id="18694-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="18694-112">Optimieren Sie je nach Bedarf die Leistung von Datenmigrationen und Synchronisierungen mithilfe der Überlegungen zu IT-Abläufen.</span><span class="sxs-lookup"><span data-stu-id="18694-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="18694-113">Überlegungen zu Internet-Edge</span><span class="sxs-lookup"><span data-stu-id="18694-113">Internet edge considerations</span></span>

<span data-ttu-id="18694-114">Nachfolgend finden Sie einige Punkte, die Sie bei der Optimierung Ihres Internet-Edges und Durchsatzes für Microsoft SaaS-Dienste berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="18694-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="18694-115">**Abbildung 1: Verbindungsoptionen für Microsoft SaaS-Dienste**</span><span class="sxs-lookup"><span data-stu-id="18694-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![Abbildung 1: Verbindungsoptionen für Microsoft SaaS-Dienste](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="18694-117">In Abbildung 1 ist ein lokales Netzwerk dargestellt, das über eine Internetpipe oder ExpressRoute eine Verbindung zu Microsoft SaaS-Diensten herstellt.</span><span class="sxs-lookup"><span data-stu-id="18694-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="18694-118">Hier sind einige Empfehlungen zur Optimierung Ihres Proxyservers:</span><span class="sxs-lookup"><span data-stu-id="18694-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="18694-119">Konfigurieren der Webclients mithilfe von WPAD, PAC oder GPO</span><span class="sxs-lookup"><span data-stu-id="18694-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="18694-120">Verwenden Sie keine SSL-Abfangfunktion.</span><span class="sxs-lookup"><span data-stu-id="18694-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="18694-121">Verwenden Sie eine PAC-Datei, um den Proxy für DNS-Namen des Microsoft SaaS-Diensts zu umgehen.</span><span class="sxs-lookup"><span data-stu-id="18694-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="18694-122">Lassen Sie den Datenverkehr für die CRL/OCSP-Überprüfung zu.</span><span class="sxs-lookup"><span data-stu-id="18694-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="18694-123">Nachfolgend finden sind einige Proxyserverengpässe, die Sie überprüfen müssen:</span><span class="sxs-lookup"><span data-stu-id="18694-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="18694-124">Unzureichende permanente Verbindungen (Outlook)</span><span class="sxs-lookup"><span data-stu-id="18694-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="18694-125">Nicht genügend Kapazität</span><span class="sxs-lookup"><span data-stu-id="18694-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="18694-126">Ausführen von Auswertungen außerhalb des Netzwerks</span><span class="sxs-lookup"><span data-stu-id="18694-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="18694-127">Anfordern einer Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="18694-127">Requiring authentication</span></span>
    
- <span data-ttu-id="18694-128">Keine Unterstützung für UDP-Datenverkehr (Skype for Business)</span><span class="sxs-lookup"><span data-stu-id="18694-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="18694-129">Hier sind einige Empfehlungen im Hinblick auf Näherung und Standort:</span><span class="sxs-lookup"><span data-stu-id="18694-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="18694-130">Leiten Sie Ihren Internetverkehr nicht über das private WAN.</span><span class="sxs-lookup"><span data-stu-id="18694-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="18694-131">Verwenden von bereichsinternem DNS und Internetdatenfluss für Benutzer außerhalb des Bereichs</span><span class="sxs-lookup"><span data-stu-id="18694-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="18694-132">Verwenden von ExpressRoute für hohe Bandbreite für Office 365 und gleichzeitige Konnektivität mit Azure-Diensten</span><span class="sxs-lookup"><span data-stu-id="18694-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="18694-133">Nachfolgend finden Sie die ausgehenden Ports, die für Office 365-Datenverkehr erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="18694-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="18694-134">TCP 80 (für CRL/OCSP-Überprüfungen)</span><span class="sxs-lookup"><span data-stu-id="18694-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="18694-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="18694-135">TCP 443</span></span>
    
- <span data-ttu-id="18694-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="18694-136">UDP 3478</span></span>
    
- <span data-ttu-id="18694-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="18694-137">TCP 5223</span></span>
    
- <span data-ttu-id="18694-138">TCP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="18694-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="18694-139">UDP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="18694-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="18694-140">Überlegungen zur Clientnutzung</span><span class="sxs-lookup"><span data-stu-id="18694-140">Client usage considerations</span></span>

<span data-ttu-id="18694-141">Konfigurieren Sie zuerst die Gruppe der Dienste, die Ihre Kunden verwenden, z. B.:</span><span class="sxs-lookup"><span data-stu-id="18694-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="18694-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="18694-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="18694-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="18694-143">Office 365</span></span>
    
  - <span data-ttu-id="18694-144">Office-Clientanwendungen</span><span class="sxs-lookup"><span data-stu-id="18694-144">Office client apps</span></span>
    
  - <span data-ttu-id="18694-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="18694-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="18694-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="18694-146">Exchange Online</span></span>
    
  - <span data-ttu-id="18694-147">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="18694-147">Skype for Business</span></span>
    
- <span data-ttu-id="18694-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="18694-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="18694-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="18694-149">Dynamics 365</span></span>
    
<span data-ttu-id="18694-150">Ermitteln Sie für die Clientcomputer Folgendes:</span><span class="sxs-lookup"><span data-stu-id="18694-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="18694-151">Maximale Anzahl zu einem beliebigen Zeitpunkt (Tageszeit, Jahreszeit, höchste und niedrigste Auslastung)</span><span class="sxs-lookup"><span data-stu-id="18694-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="18694-152">Gesamte für Spitzen benötigte Bandbreite</span><span class="sxs-lookup"><span data-stu-id="18694-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="18694-153">Wartezeit für Internetausgangsgerät</span><span class="sxs-lookup"><span data-stu-id="18694-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="18694-154">Ursprungsland verglichen mit Land der Rechenzentrumszusammenstellung</span><span class="sxs-lookup"><span data-stu-id="18694-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="18694-155">Prüfen Sie für jeden Typ von Client (PC, Smartphone, Tablet), die aktuelle Version von Folgendem:</span><span class="sxs-lookup"><span data-stu-id="18694-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="18694-156">Betriebssystem </span><span class="sxs-lookup"><span data-stu-id="18694-156">Operating system</span></span>
    
- <span data-ttu-id="18694-157">Internetbrowser</span><span class="sxs-lookup"><span data-stu-id="18694-157">Internet browser</span></span>
    
- <span data-ttu-id="18694-158">TCP/IP-Stack</span><span class="sxs-lookup"><span data-stu-id="18694-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="18694-159">Netzwerkhardware</span><span class="sxs-lookup"><span data-stu-id="18694-159">Network hardware</span></span>
    
- <span data-ttu-id="18694-160">Betriebssystemtreiber für Netzwerkhardware</span><span class="sxs-lookup"><span data-stu-id="18694-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="18694-161">Updates und Patches sind installiert</span><span class="sxs-lookup"><span data-stu-id="18694-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="18694-162">Optimieren Sie außerdem den Durchsatz der Intranetverbindung (kabelgestützt, kabellos oder VPN).</span><span class="sxs-lookup"><span data-stu-id="18694-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="18694-163">Weitere Informationen finden Sie unter [NAT-Unterstützung für Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span><span class="sxs-lookup"><span data-stu-id="18694-163">For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span></span>
  
<span data-ttu-id="18694-164">Die neuesten Empfehlungen zur Verwendung von ExpressRoute mit Office 365 finden Sie unter [ExpressRoute für Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="18694-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
<span data-ttu-id="18694-165">Gehen Sie folgendermaßen Sie vor, um die Intranetleistung zu optimieren:</span><span class="sxs-lookup"><span data-stu-id="18694-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="18694-166">Verwenden Sie Tools, um Roundtripzeiten (RTTs) für Ihre Internetausgangsgeräte (PsPing, Ping, Tracert, TraceTCP, Network Monitor) zu messen.</span><span class="sxs-lookup"><span data-stu-id="18694-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="18694-167">Führen Sie eine Ausgangsanalyse mithilfe von Flussprotokollen durch.</span><span class="sxs-lookup"><span data-stu-id="18694-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="18694-168">Führen Sie Analysen für Zwischengeräte (Alter, Gesundheit usw.) durch.</span><span class="sxs-lookup"><span data-stu-id="18694-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="18694-169">Weitere Informationen finden Sie unter der [PsPing-Tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span><span class="sxs-lookup"><span data-stu-id="18694-169">For more information, see the [PsPing tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="18694-170">Überlegungen zu IT-Abläufen</span><span class="sxs-lookup"><span data-stu-id="18694-170">IT operations considerations</span></span>

<span data-ttu-id="18694-171">Nachfolgend finden Sie einige Punkte, die beim Arbeiten mit einer IT-Arbeitslast in einem Microsoft SaaS-Dienst zu berücksichtigen sind.</span><span class="sxs-lookup"><span data-stu-id="18694-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="18694-172">Einmalige Migrationen</span><span class="sxs-lookup"><span data-stu-id="18694-172">One-time migrations</span></span>

<span data-ttu-id="18694-173">Beispiele für einmalige Migration sind Massendatenübertragungen für Cloudbasierte Anwendungen oder Archivspeicher.</span><span class="sxs-lookup"><span data-stu-id="18694-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="18694-174">So optimieren Sie Ihr Netzwerk für einmalige Migrationen:</span><span class="sxs-lookup"><span data-stu-id="18694-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="18694-175">Vermeiden Sie Spitzenzeiten bei der Netzwerkauslastung und Zeiten, in denen der Computer gepatcht wird.</span><span class="sxs-lookup"><span data-stu-id="18694-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="18694-176">Bevor Sie mit der tatsächlichen Migration beginnen, sollten Migrationen über Basislinien und Pilotversuche verfügen, die Netzwerkintegrität sollte bewertet und Probleme sollten behoben werden.</span><span class="sxs-lookup"><span data-stu-id="18694-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="18694-177">Führen Sie Abschlussgespräche für zukünftige Migrationen durch.</span><span class="sxs-lookup"><span data-stu-id="18694-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="18694-178">Laufende Synchronisierungen</span><span class="sxs-lookup"><span data-stu-id="18694-178">Ongoing synchronizations</span></span>

<span data-ttu-id="18694-179">Beispiele für laufende Synchronisierungen sind Verzeichnisinformationen, Einstellungen oder Dateien.</span><span class="sxs-lookup"><span data-stu-id="18694-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="18694-180">So optimieren Sie Ihr Netzwerk für laufende Synchronisierungen:</span><span class="sxs-lookup"><span data-stu-id="18694-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="18694-181">Stellen Sie sicher, dass ein System für die Überwachung der Netzwerkbandbreite vorhanden ist, lösen Sie gesammelte Fehler oder verwerfen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="18694-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="18694-182">Verwenden Sie die Ergebnisse der Bandbreitenüberwachung, um festzustellen, ob Netzwerkänderungen erforderlich sind (zentral hochskalieren, horizontal hochskalieren, neue Schaltkreise oder das Hinzufügen von Geräten).</span><span class="sxs-lookup"><span data-stu-id="18694-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="18694-183">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="18694-183">For more information, see:</span></span>
  
- [<span data-ttu-id="18694-184">Netzwerk- und Migrationsplanung für Office 365</span><span class="sxs-lookup"><span data-stu-id="18694-184">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="18694-185">Microsoft Virtual Academy-Kurs für die Office 365-Leistungsverwaltung</span><span class="sxs-lookup"><span data-stu-id="18694-185">Office 365 Performance Management Microsoft Virtual Academy course</span></span>](https://aka.ms/o365perf)
    
- [<span data-ttu-id="18694-186">ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="18694-186">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)

## <a name="next-step"></a><span data-ttu-id="18694-187">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="18694-187">Next step</span></span>

[<span data-ttu-id="18694-188">Entwerfen von Netzwerken für Microsoft-PaaS</span><span class="sxs-lookup"><span data-stu-id="18694-188">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="18694-189">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="18694-189">See also</span></span>

[<span data-ttu-id="18694-190">Microsoft-Cloudnetzwerke für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="18694-190">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="18694-191">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="18694-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="18694-192">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="18694-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



