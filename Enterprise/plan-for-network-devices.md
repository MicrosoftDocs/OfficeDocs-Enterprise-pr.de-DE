---
title: Planen von Netzwerkgeräten, die eine Verbindung zu Office 365-Diensten herstellen
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Zusammenfassung: Beschreibung von Überlegungen zu Netzwerkkapazität, WAN-Beschleunigern und Lastenausgleichsgeräten, die für die Herstellung einer Verbindung zu Office 365 verwendet werden.'
ms.openlocfilehash: c384ba043e64ec83eda74b234937efaf72f29815
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223067"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="c0a04-103">Planen von Netzwerkgeräten, die eine Verbindung zu Office 365-Diensten herstellen</span><span class="sxs-lookup"><span data-stu-id="c0a04-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="c0a04-104">**Zusammenfassung**: Beschreibung von Überlegungen zu Netzwerkkapazität, WAN-Beschleunigern und Lastenausgleichsgeräten, die für die Herstellung einer Verbindung zu Office 365 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c0a04-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="c0a04-p101">Einige Netzwerkhardware möglicherweise Einschränkungen für die Anzahl der gleichzeitigen Sitzungen, die unterstützt werden. Für Organisationen mit mehr als 2.000 Benutzern wird empfohlen, dass sie Netzwerkgeräte überwachen, um sicherzustellen, dass diese den zusätzlichen Office 365-Dienst-Datenverkehr verarbeiten kann. SNMP Simple Network Management Protocol () Software für die Überwachung können Ihnen dabei helfen.</span><span class="sxs-lookup"><span data-stu-id="c0a04-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="c0a04-108">Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="c0a04-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="c0a04-p102">In der lokalen ausgehende Internet-Proxyeinstellungen auch Konnektivität mit Office 365-Dienste für den-Clientanwendungen auswirken. Sie müssen auch der Proxy Netzwerkgeräte zum Zulassen von Verbindungen für Microsoft Cloud Services-URLs und Anwendungen konfigurieren. Jedes Unternehmen ist anders. Wenn Sie eine Vorstellung vom Zweck für wie Microsoft dieser Prozess und Bandbreite verwaltet erhalten möchten bereitstellen wir möchten, [Lesen Sie die Fallstudie](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span><span class="sxs-lookup"><span data-stu-id="c0a04-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="c0a04-113">Die folgenden Skype für Artikel zu Business-Hilfe wurden weitere Informationen zu Skype für Unternehmen:</span><span class="sxs-lookup"><span data-stu-id="c0a04-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="c0a04-114">Problembehandlung bei Skype für Business Anmeldefehlern (Administratoren)</span><span class="sxs-lookup"><span data-stu-id="c0a04-114">Troubleshooting Skype for Business Sign-in Errors (Administrators)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243624)

- [<span data-ttu-id="c0a04-115">Sie können keine Verbindung mit Skype für Unternehmen oder bestimmte Features funktionieren nicht, da eine lokale Firewall die Verbindung blockiert</span><span class="sxs-lookup"><span data-stu-id="c0a04-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="c0a04-116">Obwohl viele dieser Einstellungen Skype für Business-spezifischen sind, ist die allgemeine Anleitung zur Netzwerkkonfiguration für alle Office 365-Dienste hilfreich.</span><span class="sxs-lookup"><span data-stu-id="c0a04-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="c0a04-117">Ermitteln der Netzwerkkapazität</span><span class="sxs-lookup"><span data-stu-id="c0a04-117">Determining Network Capacity</span></span>

<span data-ttu-id="c0a04-p103">Jedes Netzwerkgerät, das in einer Verbindung vorhanden ist, hat eine Kapazitätsgrenze. Dies schließt die Client- und Servernetzwerkadapter, Router, Switches und Hubs ein, die sie verbinden. Ausreichende Netzwerkkapazität bedeutet, dass keines dieser Netzwerkgeräte vollständig ausgelastet ist. Die Überwachung der Netzwerkaktivität ist notwendig, um sicherzustellen, dass die tatsächlichen Lasten an allen Netzwerkgeräten unter der maximalen Kapazität liegen. Die Netzwerkkapazität wirkt sich auf die Leistung des Proxygeräts aus.</span><span class="sxs-lookup"><span data-stu-id="c0a04-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="c0a04-p104">In den meisten Fällen wird die Verbindung Internetbandbreite die Obergrenze für den Datenverkehr. Schwache Leistung während der Spitzenzeiten Datenverkehr wird wahrscheinlich übermäßig viele mithilfe des Internetlinks verursacht. Dies gilt auch für eine Branch Office Szenario, in dem Branch Office Proxy-Server-Computern über eine langsame Netzwerk WAN (Wide Area) mit dem Proxygerät Unternehmenszentrale die Verzweigung verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="c0a04-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="c0a04-p105">Zum Testen der Netzwerkkapazität Überwachen der Netzwerk-Aktivitätsfeeds auf die Netzwerkschnittstelle Proxy. Wenn es sich mehr als 75 % der maximalen Bandbreite einer Netzwerkschnittstelle handelt, erhöhen Sie die Bandbreite der Netzwerkinfrastruktur, die dies nicht der Fall ist. Oder erweiterte Funktionen, wie etwa HTTP-Komprimierung in Betracht.</span><span class="sxs-lookup"><span data-stu-id="c0a04-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="c0a04-129">WAN-Beschleuniger</span><span class="sxs-lookup"><span data-stu-id="c0a04-129">WAN Accelerators</span></span>

<span data-ttu-id="c0a04-p106">Wenn Ihre Organisation wide Area Network (WAN) Acceleration-Proxy-Einheiten verwendet, können Probleme auftreten, wenn Sie die Office 365-Dienste zugreifen. Möglicherweise müssen zur Optimierung Ihrer Netzwerkgeräte oder Geräte, um sicherzustellen, dass Ihre Benutzer beim Zugriff auf Office 365 eine einheitliche Erfahrung haben. Verschlüsseln beispielsweise Office 365-Diensten bestimmter Inhalte für Office 365 und TCP-Header. Das Gerät kann möglicherweise nicht dieser Art von Datenverkehr zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="c0a04-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="c0a04-134">Lesen Sie unsere Support-Anweisung zum [Verwenden von WAN-Optimierung Controller oder/Überprüfung des Datenverkehrs Geräte mit Office 365](https://support.microsoft.com/kb/2690045).</span><span class="sxs-lookup"><span data-stu-id="c0a04-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="c0a04-135">Hardware- und Softwaregeräte für den Lastenausgleich</span><span class="sxs-lookup"><span data-stu-id="c0a04-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="c0a04-p107">Für Ihr Unternehmen empfiehlt sich die Verwendung eines Hardware-Lastenausgleichsmoduls (HLB) oder einer Netzwerk-Lastenausgleich-Lösung (NLB) um Anforderungen an die Server der Active Directory-Verbunddienste (AD FS) und/oder Ihres Hybridservers verteilen zu können. Geräte für den Lastenausgleich steuern den Netzwerkdatenverkehr zu den lokalen Servern. Diese Server sind für die Verfügbarkeit von einmaligen Anmeldungen sowie für die Exchange-Hybridbereitstellung unerlässlich.</span><span class="sxs-lookup"><span data-stu-id="c0a04-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="c0a04-p108">Wir stellen eine softwarebasierte NLB-Lösung in Windows Server integriert. Office 365 unterstützt diese Lösung zum Lastenausgleich zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="c0a04-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="c0a04-141">Firewalls und Proxys</span><span class="sxs-lookup"><span data-stu-id="c0a04-141">Firewalls and proxies</span></span>

<span data-ttu-id="c0a04-142">Weitere Informationen zum Konfigurieren von Firewalls und Proxys für die Verbindung zu Office 365, erfahren Sie mehr über die Geräte und Netzfrequenz Auswahl [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Netzwerkkonnektivität zu Office 365](network-connectivity.md)und [häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) lesen.</span><span class="sxs-lookup"><span data-stu-id="c0a04-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c0a04-143">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c0a04-143">See also</span></span>

[<span data-ttu-id="c0a04-144">Bereitstellung Berater für Office 365-Dienste</span><span class="sxs-lookup"><span data-stu-id="c0a04-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
