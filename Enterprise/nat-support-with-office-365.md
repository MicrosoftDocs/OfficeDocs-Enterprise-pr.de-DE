---
title: NAT-Unterstützung in Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Zusammenfassung: Hier erhalten Sie ausführliche Informationen dazu, wie Sie die richtige Anzahl Clients einschätzen, die Sie pro IP-Adresse mit der Netzwerkadressübersetzung (Network Address Translation, NAT) in Ihrem Unternehmen verwenden können.'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540704"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="bc6bc-103">NAT-Unterstützung in Office 365</span><span class="sxs-lookup"><span data-stu-id="bc6bc-103">NAT support with Office 365</span></span>

 <span data-ttu-id="bc6bc-104">**Zusammenfassung:** Hier erhalten Sie ausführliche Informationen dazu, wie Sie die richtige Anzahl Clients einschätzen, die Sie pro IP-Adresse mit der Netzwerkadressübersetzung (Network Address Translation, NAT) in Ihrem Unternehmen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="bc6bc-105">Bisher vorgeschlagene Hinweise, dass die maximale Anzahl von Exchange-Clients, die Sie pro IP-Adresse verwenden sollten, Verbindung mit Office 365 etwa 2.000 Clients pro Netzwerkports war.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="bc6bc-106">Gründe für die Verwendung von NAT</span><span class="sxs-lookup"><span data-stu-id="bc6bc-106">Why use NAT?</span></span>

<span data-ttu-id="bc6bc-107">Mithilfe von NAT können Tausende Benutzer in einem Unternehmensnetzwerk "wenige öffentlich routingfähige IP-Adressen gemeinsam nutzen".</span><span class="sxs-lookup"><span data-stu-id="bc6bc-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="bc6bc-p101">Die meisten Unternehmensnetzwerke verwenden einen privaten (RFC1918) IP-Adressraum. Private Adressräume werden durch die IANA (Internet Assigned Numbers Authority) zugewiesen und sind ausschließlich für Netzwerke bestimmt, die nicht direkt vom und zum Internet routen.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="bc6bc-p102">Um Internetzugriff auf Geräte auf einem privaten IP-Adressraum zu ermöglichen, verwenden Sie Organisationen Gateway-Technologien wie Firewalls und Proxys, die Netzwerkadressübersetzung (NAT) oder Port Address Translation (PAT) Services bereitstellen. Diese Gateways stellen Datenverkehr von interne Geräte mit dem Internet (einschließlich Office 365) angezeigt werden, von einer oder mehreren öffentlich routingfähige IP-Adressen kommen. Jede ausgehende Verbindung von einem internen Gerät wird in einer anderen Quelle TCP-Port auf die öffentliche IP-Adresse übersetzt.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="bc6bc-113">Warum müssen Sie so viele Verbindungen zu Office 365 gleichzeitig geöffnet haben?</span><span class="sxs-lookup"><span data-stu-id="bc6bc-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="bc6bc-p103">Outlook kann acht oder mehr Verbindungen öffnen (in Situationen, in denen Add-Ins, freigegebene Kalender, Postfächer etc. vorhanden sind). Auf einem Windows-basierten NAT-Gerät sind höchstens 64.000 Ports verfügbar. Daher beträgt die Höchstzahl 8.000 Benutzer pro IP-Adresse. Bitte beachten Sie, dass die Anzahl der verfügbaren Ports bei Kunden, die kein Windows-basiertes Betriebssystem für NAT verwenden, abhängig von NAT-Gerät oder -Software ist. In einem solchen Szenario liegt die Höchstzahl der Ports ggf. unter 64.000. Die Verfügbarkeit der Ports ist außerdem abhängig von weiteren Faktoren: So beansprucht Windows 4.000 Ports für sich, wodurch die Anzahl der verfügbaren Ports auf 60.000 reduziert wird. Zudem besteht die Möglichkeit, dass weitere Anwendungen, die zur gleichen Zeit eine Verbindung aufbauen – z. B. Internet Explorer – ebenfalls Ports in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="bc6bc-119">Berechnung der Höchstzahl an unterstützten Geräten für eine einzelne öffentliche IP-Adresse mit Office 365</span><span class="sxs-lookup"><span data-stu-id="bc6bc-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="bc6bc-p104">Um die maximale Anzahl der Geräte hinter einer einzelnen öffentlichen IP-Adresse zu ermitteln, sollten Sie den Netzwerkverkehr zum Bestimmen der Spitzenlast Port-Auslastung pro Client überwachen. Darüber hinaus sollte Spitzenlast-Faktor beträgt die Verwendung von Port (mindestens 4) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="bc6bc-122">**Anhand der folgenden Formel berechnet die Anzahl der unterstützten Geräte pro IP-Adresse:**</span><span class="sxs-lookup"><span data-stu-id="bc6bc-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="bc6bc-123">Höchstanzahl unterstützter Geräte hinter einer einzelnen öffentlichen IP-Adresse = (64.000 – eingeschränkte Ports) / (Spitzenlast Port-Nutzung + Spitzenlast-Faktor)</span><span class="sxs-lookup"><span data-stu-id="bc6bc-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="bc6bc-124">**Wenn beispielsweise die folgenden true haben:**</span><span class="sxs-lookup"><span data-stu-id="bc6bc-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="bc6bc-125">**Eingeschränkte Ports:** 4.000 für das Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="bc6bc-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="bc6bc-126">**Spitzenlast Port-Nutzung:** 6 pro Gerät</span><span class="sxs-lookup"><span data-stu-id="bc6bc-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="bc6bc-127">**Spitzenfaktor:** 4</span><span class="sxs-lookup"><span data-stu-id="bc6bc-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="bc6bc-128">Klicken Sie dann die Höchstzahl an unterstützten Geräten für eine einzelne öffentliche IP-Adresse = (64.000-4.000) / (6 + 4) = 6.000</span><span class="sxs-lookup"><span data-stu-id="bc6bc-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="bc6bc-p105">Mit der Veröffentlichung von Office 365-hosting enthalten in den Updates von September 2011 für Microsoft Office Outlook 2007 oder vom November 2011 für Microsoft Outlook 2010 oder einem neueren Update, die Anzahl der Verbindungen von Outlook (sowohl Office Outlook 2007 mit Service pack 2 und Outlook 2010-Paket) zu Exchange kann so wenige als 2 sein. Sie müssen Faktor in den verschiedenen Betriebssystemen Benutzerverhaltensweisen, und so weiter, um die minimale und maximale Anzahl von Ports zu ermitteln, die Ihr Netzwerk bei Spitzenbelastungen erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="bc6bc-131">Wenn Sie mehrere Geräte hinter einer einzelnen öffentlichen IP-Adresse unterstützen möchten, führen Sie die folgenden Schritte durch, um die maximale Anzahl von Geräten bewerten, die unterstützt werden können:</span><span class="sxs-lookup"><span data-stu-id="bc6bc-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="bc6bc-p106">Überwachen des Netzwerkverkehrs Spitzenlast Port-Auslastung pro Client bestimmen. Sie sollten diese Daten zu erfassen:</span><span class="sxs-lookup"><span data-stu-id="bc6bc-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="bc6bc-134">Von mehreren geografischen Orten aus</span><span class="sxs-lookup"><span data-stu-id="bc6bc-134">From multiple locations</span></span>
    
- <span data-ttu-id="bc6bc-135">Für mehrere Geräte</span><span class="sxs-lookup"><span data-stu-id="bc6bc-135">From multiple devices</span></span>
    
- <span data-ttu-id="bc6bc-136">Zu mehreren Zeitpunkten</span><span class="sxs-lookup"><span data-stu-id="bc6bc-136">At multiple times</span></span>
    
<span data-ttu-id="bc6bc-137">Verwenden Sie die oben angegebene Formel, um die Höchstzahl der Nutzer pro IP-Adresse in deren jeweiligen Umgebung zu errechnen.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="bc6bc-p107">Es gibt verschiedene Methoden zum Verteilen der Clientlast auf Weitere öffentliche IP-Adressen. Strategien zur Verfügung, abhängig von der Funktionen des Unternehmens-Gateway-Lösung. Die einfachste Lösung ist Ihre Benutzeradressraum segmentieren und "zuweisen" statisch eine Anzahl von IP-Adressen an jedes Gateway. Eine andere Möglichkeit, die viele Gateway-Geräte bieten ist die Möglichkeit, einen Pool von IP-Adressen verwenden. Die Vorteile der Adresspool ist, es ist sehr viel dynamischen und mit weitaus geringerer Wahrscheinlichkeit Anpassung erforderlich ist, wenn Ihre Benutzerbasis wächst.</span><span class="sxs-lookup"><span data-stu-id="bc6bc-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bc6bc-143">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bc6bc-143">See also</span></span>

[<span data-ttu-id="bc6bc-144">Verwalten von Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="bc6bc-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="bc6bc-145">Häufig gestellte Fragen zu Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="bc6bc-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

