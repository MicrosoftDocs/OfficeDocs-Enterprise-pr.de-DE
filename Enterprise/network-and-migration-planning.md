---
title: Netzwerk- und Migrationsplanung für Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Enthält Links zu Informationen über das Netzwerk planen und testen und Migration zu Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223057"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="fcd19-103">Netzwerk- und Migrationsplanung für Office 365</span><span class="sxs-lookup"><span data-stu-id="fcd19-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="fcd19-104">Dieser Artikel enthält Links zu Informationen über das Netzwerk planen und testen und Migration zu Office 365.</span><span class="sxs-lookup"><span data-stu-id="fcd19-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="fcd19-105">Bevor Sie Office 365 zum ersten Mal bereitstellen oder zu Office 365 migrieren, können Sie anhand der Informationen in diesen Themen die benötigte Bandbreite einschätzen und dann testen bzw. prüfen, ob Sie über ausreichend Bandbreite für die Bereitstellung von oder Migration zu Office 365 verfügen.</span><span class="sxs-lookup"><span data-stu-id="fcd19-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="fcd19-106">Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="fcd19-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![Finden Sie unter Microsoft Cloud Netzwerk konstruiert Enterprise-Poster](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="fcd19-108">Die Schritte zur Optimierung Ihres Netzwerks für Office 365 und anderen Microsoft-Cloud-Plattformen und Dienste finden Sie unter Details des Posters [Microsoft Cloud Networking für Enterprise-konstruiert](https://aka.ms/cloudarchnetworking) .</span><span class="sxs-lookup"><span data-stu-id="fcd19-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="fcd19-109">Schätzen der Anforderungen an die Netzwerkbandbreite</span><span class="sxs-lookup"><span data-stu-id="fcd19-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="fcd19-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="fcd19-110"></span></span>

<span data-ttu-id="fcd19-p101">Verwendung von Office 365, kann die Nutzung in Ihrer Organisation Internet Netzfrequenz erhöhen. Es ist wichtig, um festzustellen, ob die aktuell verfügbare Bandbreite genügt, um die geschätzte Erhöhung behandeln nach Office 365 vollständig bereitgestellt wird, während Sie verlassen mindestens 20 % Kapazität zum Verarbeiten von der höchsten Auslastung von Tagen.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="fcd19-113">Um die Bandbreite zu schätzen, verwenden Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="fcd19-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="fcd19-p102">Bewerten Sie die Anzahl von Clients, die jeder Ausgang Internet verwendet wird. Können Sie unser Multi-TBit Netzwerk möglichst die Verbindung wie möglich verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="fcd19-p103">Bestimmen Sie, welche Office 365-Dienste und Features für die Verwendung von Clients zur Verfügung stehen. Sie müssen wahrscheinlich Personengruppen mit anderen Diensten oder Verwendungsprofile.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="fcd19-p104">Messen Sie die Netzwerkverwendung für eine Pilotgruppe von Clients. Stellen Sie sicher, dass die pilot-Clients für die verschiedenen Profile von Personen in der Organisation als auch verschiedene geografische Standorte repräsentativ sind. Sie können Cross-Kontrollkästchen Ihre Ergebnisse für unsere alten Rechner für [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)und [Skype für Unternehmen](https://go.microsoft.com/fwlink/p/?LinkId=321551) oder der [Fallstudie](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) , die wir in unseren eigenen Netzwerk ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="fcd19-121">Verwenden Sie die Maße von der Pilotgruppe, um die gesamte Organisation Anforderungen Schlussfolgerungen ziehen, und Testen Sie erneut um Einschätzung vor dem Durchführen von Änderungen an Ihrem Netzwerk überprüfen.</span><span class="sxs-lookup"><span data-stu-id="fcd19-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="fcd19-122">Testen des vorhandenen Netzwerks</span><span class="sxs-lookup"><span data-stu-id="fcd19-122">Test your existing network</span></span>
<span data-ttu-id="fcd19-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="fcd19-123"></span></span>

 <span data-ttu-id="fcd19-p105">**Netzwerk-Tools.** Testen Sie und überprüfen Sie die Internetbandbreite zum Download, hochladen und Wartezeit Integritätsregeln bestimmen. Diese Tools helfen Ihnen beim bestimmen die Funktionen des Netzwerks für die Migration sowie Sie vollständig bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="fcd19-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Nachricht Analyzer ist ein effizientes Tool für die Problembehandlung bei Netzwerkprobleme. Nachricht Analyzer erfasst, anzeigt und analysiert IP-basierten messaging-Datenverkehr und Systemnachrichten. Nachricht Analyzer können Sie auch importieren, aggregieren und Analysieren von Daten aus Protokoll- und Ablaufverfolgungsprotokoll-Dateien.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="fcd19-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): testet die Konnektivität in Ihrer Exchange Online-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="fcd19-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="fcd19-131">Verwenden Sie die [Microsoft-Support und Recovery-Assistenten für Office 365](https://diagnostics.office.com/#/Download?env=SOC) , um Outlook und Office 365 Probleme zu beheben.</span><span class="sxs-lookup"><span data-stu-id="fcd19-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="fcd19-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="fcd19-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="fcd19-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="fcd19-133"></span></span>

<span data-ttu-id="fcd19-134">Architekturprinzipien Sie etwas genauer diesen bewährten Methoden für Weitere Informationen zum Verbessern der Ihre Office 365-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="fcd19-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="fcd19-p107">Helfen Ihren Benutzern sofort beginnen möchten? Tipps zur Verwendung von Office 365, einschließlich SharePoint Online, Exchange Online und Lync Online, wenn Ihr Netzwerk ist nicht einfach zusammenarbeiten, finden Sie unter [bewährte Methoden für die Verwendung von Office 365 bei langsamen Netzwerken](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . In diesem Artikel links out zu Lasten von Inhalten auf TechNet und Support.office.com für Ihre Office 365-Erfahrung optimieren und enthält Informationen über die einfache Verfahren zum Anpassen von Webseiten und wie Sie Ihre Einstellungen für Internet Explorer für die beste Office 365-Erfahrung festlegen.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="fcd19-p108">Lesen Sie [Office 365 Network Connectivity Prinzipien](https://aka.ms/o365networkingprinciples) , um die Konnektivität Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen. In diesem Artikel helfen Ihnen das Verständnis der neuesten Anleitung zur Optimierung von Office 365-Netzwerkkonnektivität sicher.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="fcd19-p109">Verbessern der e-Mail-migrationsleistung durch sorgfältige Planung und Verwaltung des Zeitplans für die Windows-Updates. Sie können Ihren Clientcomputern in Batches aktualisieren und stellen Sie sicher, dass alle Clientcomputer vor der Migration zu Office 365 ein, um die Verwendung der Netzwerkbandbreite Weise aktualisiert werden. Weitere Informationen finden Sie unter [Manuelles Aktualisieren und Konfigurieren von Desktopcomputern für Office 365 für die neuesten Updates](https://support.microsoft.com/gp/office-2013-365-update).</span><span class="sxs-lookup"><span data-stu-id="fcd19-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="fcd19-p110">Office 365 Netzwerkdatenverkehr führt am besten, wenn es als vertrauenswürdigen Internetdienst behandelt und einen Großteil der traditionellen Filter- und Überprüfung, die auf den Netzwerkverkehr zu nicht vertrauenswürdigen Internetdienste einige Organisationen setzen umgehen zulässig. Dies umfasst in der Regel ausgehende Verarbeitung wie Proxy Benutzerauthentifizierung und Paketinspektion als auch lokale Ausgang an das Internet mit den richtigen Network Address Translation (NAT) und ausreichende Bandbreitenkapazität, die erhöhte behandeln sicherstellen entfernen Netzwerk-Anfragen. Weitere Anleitungen zum Konfigurieren des Netzwerks zur Verarbeitung von Office 365 als vertrauenswürdigen Internetdienst in Ihrem Netzwerk finden Sie unter [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span><span class="sxs-lookup"><span data-stu-id="fcd19-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="fcd19-p111">Sicherzustellen Sie [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Der zusätzliche Datenverkehr zu Office 365 erzeugt einen Anstieg der ausgehenden Proxyverbindungen als auch einen Anstieg beim sicheren Datenverkehr über TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="fcd19-p112">Wenn Ihre ausgehenden Proxys Benutzerauthentifizierung langsame Verbindung oder ein Funktionalitätsverlust auftreten können erfordern. Die Authentifizierungsanforderung für die Office 365-Domänen umgehen kann diesen Aufwand reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="fcd19-p113">Wenn Sie eine große Anzahl an freigegebenen Kalendern und Postfächern besitzen, stellen Sie möglicherweise einen Anstieg der Anzahl an Verbindungen von Outlook zu Exchange fest. So kann der Outlook-Client z. B. für jeden freigegebenen Kalender in Verwendung bis zu zwei zusätzliche Verbindungen öffnen. Stellen Sie in diesem Fall sicher, dass der Zugangsproxy die Verbindungen verarbeiten kann, oder umgehen Sie den Proxy für Verbindungen zu Office 365 für Outlook.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="fcd19-p114">Bestimmen Sie die maximale Anzahl von unterstützten Geräten für eine öffentliche IP-Adresse und zum Lastenausgleich über mehrere IP-Adressen. Weitere Informationen finden Sie unter [NAT-Unterstützung mit Office 365](nat-support-with-office-365.md).</span><span class="sxs-lookup"><span data-stu-id="fcd19-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="fcd19-p115">Wenn beim Überprüfen von ausgehender Verbindungen von Computern in Ihrem Netzwerk die Umgehung dieser Filter auf die Office 365-Domänen und die Leistung verbessert wird. Darüber hinaus umgehen häufig ausgehende Prüfung entfällt die Notwendigkeit einer einzelnen Internet Ausgang und ermöglicht lokalen Internet Ausgang für Office 365 bestimmt Netzwerk Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="fcd19-p116">Einige Kunden Hier finden Sie internen Netzwerkeinstellungen Leistung auswirken können. Netzwerk-Einstellungen wie die maximale Größe der Übertragungseinheit, Auto-Verhandlung oder automatische Erkennung und suboptimalen Routen mit dem Internet sind allgemeine Orte zum Suchen.</span><span class="sxs-lookup"><span data-stu-id="fcd19-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="fcd19-159">Netzwerkplanung für Office 365 – Referenz</span><span class="sxs-lookup"><span data-stu-id="fcd19-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="fcd19-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="fcd19-160"></span></span>

<span data-ttu-id="fcd19-161">Diese Themen enthalten ausführliche Referenzinformationen für Office 365-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="fcd19-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="fcd19-162">Verwalten von Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="fcd19-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="fcd19-163">Client-Konnektivität</span><span class="sxs-lookup"><span data-stu-id="fcd19-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="fcd19-164">Die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="fcd19-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="fcd19-165">Externe Domain Name System-Einträge für Office 365</span><span class="sxs-lookup"><span data-stu-id="fcd19-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="fcd19-166">IPv6-Unterstützung in Office 365-Diensten</span><span class="sxs-lookup"><span data-stu-id="fcd19-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="fcd19-167">Office 365 Network Connectivity Prinzipien</span><span class="sxs-lookup"><span data-stu-id="fcd19-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="fcd19-168">Microsoft Virtual Academy: Die Verwaltung Office 365 Leistung</span><span class="sxs-lookup"><span data-stu-id="fcd19-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="fcd19-169">Office 365-video-Netzwerke häufig gestellte Fragen (FAQS)</span><span class="sxs-lookup"><span data-stu-id="fcd19-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="fcd19-170">Planen von Netzwerkgeräten, die eine Verbindung zu Office 365-Diensten herstellen</span><span class="sxs-lookup"><span data-stu-id="fcd19-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="fcd19-171">Bereitstellung Berater für Office 365-Dienste</span><span class="sxs-lookup"><span data-stu-id="fcd19-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

