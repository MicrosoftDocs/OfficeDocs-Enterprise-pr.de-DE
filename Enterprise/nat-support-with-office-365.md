---
title: NAT-Unterstützung mit Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Zusammenfassung: enthält Informationen dazu, wie Sie die korrekte Anzahl von Clients, die Sie pro IP-Adresse in Ihrer Organisation verwenden können, mithilfe von Netzwerkadressübersetzung (Network Address Translation, NAT) annähern.'
ms.openlocfilehash: bdbf108163c7b22fd6d7583436af5f0ed655784c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069881"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="13149-103">NAT-Unterstützung mit Office 365</span><span class="sxs-lookup"><span data-stu-id="13149-103">NAT support with Office 365</span></span>

 <span data-ttu-id="13149-104">**Zusammenfassung:** Enthält ausführliche Informationen dazu, wie Sie die richtige Anzahl von Clients, die Sie pro IP-Adresse in Ihrer Organisation verwenden können, mithilfe von Netzwerkadressübersetzung (Network Address Translation, NAT) annähern.</span><span class="sxs-lookup"><span data-stu-id="13149-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="13149-105">Bisher wurde empfohlen, dass die maximale Anzahl von Exchange-Clients, die Sie pro IP-Adresse zum Herstellen einer Verbindung mit Office 365 verwenden sollten, ungefähr 2.000 Clients pro Netzwerkport war.</span><span class="sxs-lookup"><span data-stu-id="13149-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="13149-106">Gründe für die Verwendung von NAT</span><span class="sxs-lookup"><span data-stu-id="13149-106">Why use NAT?</span></span>

<span data-ttu-id="13149-107">Durch die Verwendung von NAT können Tausende von Personen in einem Unternehmensnetzwerk einige öffentlich routingfähige IP-Adressen freigeben.</span><span class="sxs-lookup"><span data-stu-id="13149-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="13149-108">Die meisten Unternehmensnetzwerke verwenden einen privaten (RFC1918) IP-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="13149-108">Most corporate networks use private (RFC1918) IP address space.</span></span> <span data-ttu-id="13149-109">Privater Adressraum wird von der Internet Assigned Numbers Authority (IANA) zugewiesen und soll ausschließlich für Netzwerke bestimmt werden, die nicht direkt an das und aus dem globalen Internet weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="13149-109">Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="13149-110">Um Internet Zugriff auf Geräte in einem privaten IP-Adressraum bereitzustellen, verwenden Organisationen Gateway-Technologien wie Firewalls und Proxys, die die Netzwerkadressübersetzung (NAT) oder Pat-Dienste (Port Address Translation) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="13149-110">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services.</span></span> <span data-ttu-id="13149-111">Diese Gateways stellen den Datenverkehr von internen Geräten zum Internet (einschließlich Office 365) scheinbar aus einer oder mehreren öffentlich routingfähigen IP-Adressen her.</span><span class="sxs-lookup"><span data-stu-id="13149-111">These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses.</span></span> <span data-ttu-id="13149-112">Jede ausgehende Verbindung von einem internen Gerät wird in einen anderen TCP-Quellanschluss der öffentlichen IP-Adresse übersetzt.</span><span class="sxs-lookup"><span data-stu-id="13149-112">Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="13149-113">Warum müssen Sie so viele Verbindungen zu Office 365 gleichzeitig öffnen?</span><span class="sxs-lookup"><span data-stu-id="13149-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="13149-114">Outlook kann acht oder mehr Verbindungen öffnen (in Situationen, in denen Add-Ins, freigegebene Kalender, Postfächer usw. vorhanden sind).</span><span class="sxs-lookup"><span data-stu-id="13149-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span></span> <span data-ttu-id="13149-115">Da für ein Windows-basiertes NAT-Gerät maximal 64.000 Ports verfügbar sind, können maximal 8.000 Benutzer hinter einer IP-Adresse liegen, bevor die Ports erschöpft sind.</span><span class="sxs-lookup"><span data-stu-id="13149-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span></span> <span data-ttu-id="13149-116">Beachten Sie, dass die insgesamt verfügbaren Ports davon abhängen, welche NAT-Geräte oder-Software verwendet werden, wenn Kunden nicht-Windows-Betriebssystembasierte Geräte für NAT verwenden.</span><span class="sxs-lookup"><span data-stu-id="13149-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span></span> <span data-ttu-id="13149-117">In diesem Szenario kann die maximale Anzahl von Ports kleiner als 64.000 sein.</span><span class="sxs-lookup"><span data-stu-id="13149-117">In this scenario, the maximum number of ports could be less than 64,000.</span></span> <span data-ttu-id="13149-118">Die Verfügbarkeit von Ports wird auch von anderen Faktoren beeinflusst, wie beispielsweise der Windows-Beschränkung von 4.000-Ports für die eigene Verwendung, wodurch die Gesamtzahl der verfügbaren Ports auf 60.000 reduziert wird. möglicherweise gibt es andere Anwendungen wie Internet Explorer, die gleichzeitig eine Verbindung herstellen können. , die zusätzliche Ports erfordern.</span><span class="sxs-lookup"><span data-stu-id="13149-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="13149-119">Berechnen der maximal unterstützten Geräte hinter einer einzelnen öffentlichen IP-Adresse mit Office 365</span><span class="sxs-lookup"><span data-stu-id="13149-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="13149-120">Wenn Sie die maximale Anzahl von Geräten hinter einer einzelnen öffentlichen IP-Adresse ermitteln möchten, sollten Sie den Netzwerkdatenverkehr überwachen, um den maximalen Port Verbrauch pro Client zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="13149-120">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="13149-121">Außerdem sollte ein Peak-Faktor für die Verwendung der Portierung verwendet werden (mindestens 4).</span><span class="sxs-lookup"><span data-stu-id="13149-121">Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="13149-122">**Verwenden Sie die folgende Formel, um die Anzahl unterstützter Geräte pro IP-Adresse zu berechnen:**</span><span class="sxs-lookup"><span data-stu-id="13149-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="13149-123">Maximal unterstützte Geräte hinter einer einzelnen öffentlichen IP-Adresse = (64.000-restricted Ports)/(Peak Port Verbrauch + Spitzen Faktor)</span><span class="sxs-lookup"><span data-stu-id="13149-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="13149-124">**Wenn beispielsweise Folgendes zutrifft:**</span><span class="sxs-lookup"><span data-stu-id="13149-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="13149-125">**Eingeschränkte Ports:** 4.000 für das Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="13149-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="13149-126">**Maximaler Stromverbrauch:** 6 pro Gerät</span><span class="sxs-lookup"><span data-stu-id="13149-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="13149-127">**Höchstwert:** 4</span><span class="sxs-lookup"><span data-stu-id="13149-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="13149-128">Dann werden die maximal unterstützten Geräte hinter einer einzelnen öffentlichen IP-Adresse = (64.000-4000)/(6 + 4) = 6.000</span><span class="sxs-lookup"><span data-stu-id="13149-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="13149-129">Mit der Version von Office 365 Hosting Pack, die in den Updates vom September 2011 für Microsoft Office Outlook 2007 oder November 2011 für Microsoft Outlook 2010 oder einem späteren Update enthalten ist, ist die Anzahl der Verbindungen von Outlook (sowohl Office Outlook 2007 mit Dienst Pack 2 und Outlook 2010) an Exchange kann nur 2 sein.</span><span class="sxs-lookup"><span data-stu-id="13149-129">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2.</span></span> <span data-ttu-id="13149-130">Sie müssen die unterschiedlichen Betriebssysteme, Benutzerverhalten usw. berücksichtigen, um die Mindest-und Höchstzahl der Ports zu ermitteln, die Ihr Netzwerk am höchsten ist.</span><span class="sxs-lookup"><span data-stu-id="13149-130">You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="13149-131">Wenn Sie mehr Geräte hinter einer einzelnen öffentlichen IP-Adresse unterstützen möchten, führen Sie die folgenden Schritte aus, um die maximale Anzahl von Geräten zu bewerten, die unterstützt werden können:</span><span class="sxs-lookup"><span data-stu-id="13149-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="13149-132">Überwachen des Netzwerkdatenverkehrs zur Bestimmung des Spitzen Port Verbrauchs pro Client</span><span class="sxs-lookup"><span data-stu-id="13149-132">Monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="13149-133">Sie sollten diese Daten erfassen:</span><span class="sxs-lookup"><span data-stu-id="13149-133">You should collect this data:</span></span>
  
- <span data-ttu-id="13149-134">Von mehreren Standorten</span><span class="sxs-lookup"><span data-stu-id="13149-134">From multiple locations</span></span>
    
- <span data-ttu-id="13149-135">Von mehreren Geräten</span><span class="sxs-lookup"><span data-stu-id="13149-135">From multiple devices</span></span>
    
- <span data-ttu-id="13149-136">Mehrmals</span><span class="sxs-lookup"><span data-stu-id="13149-136">At multiple times</span></span>
    
<span data-ttu-id="13149-137">Verwenden Sie die vorhergehende Formel, um die maximalen Benutzer pro IP-Adresse zu berechnen, die in Ihrer Umgebung unterstützt werden können.</span><span class="sxs-lookup"><span data-stu-id="13149-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="13149-138">Es gibt verschiedene Methoden zum Verteilen der Clientauslastung über zusätzliche öffentliche IP-Adressen.</span><span class="sxs-lookup"><span data-stu-id="13149-138">There are various methods for distributing client load across additional public IP addresses.</span></span> <span data-ttu-id="13149-139">Verfügbare Strategien hängen von den Funktionen der Unternehmens Gateway-Lösung ab.</span><span class="sxs-lookup"><span data-stu-id="13149-139">Strategies available depend on the capabilities of the corporate gateway solution.</span></span> <span data-ttu-id="13149-140">Die einfachste Lösung besteht darin, ihren Benutzeradressraum zu segmentieren und jedem Gateway statisch eine Reihe von IP-Adressen zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="13149-140">The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway.</span></span> <span data-ttu-id="13149-141">Eine weitere Alternative, die viele Gateway-Geräte bieten, ist die Möglichkeit, einen Pool von IP-Adressen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="13149-141">Another alternative that many gateway devices offer is the ability to use a pool of IP addresses.</span></span> <span data-ttu-id="13149-142">Der Vorteil des Adresspools besteht darin, dass er viel dynamischer ist und weniger wahrscheinlich ist, dass eine Anpassung erforderlich ist, wenn die Benutzerbasis wächst.</span><span class="sxs-lookup"><span data-stu-id="13149-142">The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="13149-143">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="13149-143">See also</span></span>

[<span data-ttu-id="13149-144">Verwalten von Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="13149-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="13149-145">Häufig gestellte Fragen zu Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="13149-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

