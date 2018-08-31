---
title: Client-Konnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Zusammenfassung: Erläutert, wie Clientcomputer je nach Standort des Clientcomputers und des Office 365-Mandantenrechenzentrums eine Verbindung zu Office 365-Mandaten herstellen.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223037"
---
# <a name="client-connectivity"></a><span data-ttu-id="d7aae-103">Client-Konnektivität</span><span class="sxs-lookup"><span data-stu-id="d7aae-103">Client connectivity</span></span>

 <span data-ttu-id="d7aae-104">**Zusammenfassung:** Erläutert, wie Clientcomputer je nach Standort des Clientcomputers und des Office 365-Mandantenrechenzentrums eine Verbindung zu Office 365-Mandaten herstellen.</span><span class="sxs-lookup"><span data-stu-id="d7aae-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="d7aae-p101">Office 365 befindet sich in Microsoft-Rechenzentren auf der ganzen Welt, das hilfreich, halten Sie den Dienst einrichten und betreiben, auch wenn es in einer Region, wie ein Erdbeben oder eines Stromausfalls ein ernstes Problem auftritt ist. Beim Herstellen der Verbindung zu Ihrem Office 365-Mandanten werden die Clientverbindung in die entsprechenden Rechenzentrum geleitet, wo Ihre Mandanten gehostet wird. Die Regeln, die bestimmen, wo Ihre Mandanten gehostet werden können, werden von Ihrer Vereinbarung mit Microsoft definiert. Die Regeln, die bestimmen, wie der Client die Daten aus diesem Speicherort Datacenter erwirbt hängen die Architektur des Diensts, den Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="d7aae-p102">Wenn Sie Office 365-Portal anmelden, sind Sie beispielsweise normalerweise mit dem nächsten Rechenzentrum an den Client verbunden und dann je nach dem Dienst weitergeleitet, mit denen Sie weiter. Wenn Sie e-Mail starten, die erste Verbindung zum Anzeigen der Benutzeroberfläche kann weiterhin stammen aus der nächsten Rechenzentrum, aber möglicherweise eine zweite Verbindung zwischen den nächsten Rechenzentrum und dem Rechenzentrum, wo sich Ihrem Mandanten befindet, um anzuzeigen, dass Sie, was in der e-Mails Sie lesen, geöffnet werden. Microsoft arbeitet mit einem der oberen zehn Netzwerke in der ganzen Welt resultierendes in fast unglaublich schnell Datacenter-an-Datacenter-Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="d7aae-112">Nachdem Sie den Artikel gelesen haben, Sie wahrscheinlich kennen Warum bieten wir [Office 365-URLs und IP-Adressbereiche](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) nicht pro Rechenzentrum, sie sind einfach zu miteinander verknüpft und miteinander zu stellen, die Sie machbare abhängig.</span><span class="sxs-lookup"><span data-stu-id="d7aae-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="d7aae-p103">Wenn Sie Azure ExpressRoute für Office 365 verwenden, in den meisten Fällen die Verbindung über eine private Verbindung zu Office 365 statt der hier beschriebenen öffentliche Verbindung gelangen. Die Prinzipien zur wie Clients eine Verbindung herstellen sind korrekt. Weitere Informationen zu [Azure ExpressRoute für Office 365](azure-expressroute.md).</span><span class="sxs-lookup"><span data-stu-id="d7aae-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="d7aae-116">Lesen Sie für weitere Tiefe auf Skype für Business Netzwerk Anforderungen Artikel [Medienqualität und Leistung des Netzwerks Connectivity in Skype für Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span><span class="sxs-lookup"><span data-stu-id="d7aae-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="d7aae-117">Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="d7aae-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="d7aae-p104">Wir müssen Sie Kundendaten also sichere und private in unseren Rechenzentren verwalten. Einzelheiten über die Schritte, die zum Verwalten von Privacy nehmen wir sind im [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383)enthalten.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="d7aae-120">Herstellen einer Verbindung mit dem nächsten Rechenzentrum</span><span class="sxs-lookup"><span data-stu-id="d7aae-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="d7aae-p105">Dies ist die am häufigsten verwendeten Typ der Verbindung, und es wird von den Office 365-Portal und Exchange Online verwendet. In dieser Situation Wenn Clients versuchen, eine Verbindung zu Office 365 herzustellen, DNS-Abfrage des Computers bestimmt die Region der Welt, die, der Ihren Computer stammt, und Office 365 leitet die Anforderung an den nächsten Rechenzentrum.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="d7aae-123">Verbindungen zum Portal bei der nächsten Rechenzentrum beendet, und der Clientcomputer erhält Informationen zu dem Mandanten des Clients von diesem Standort.</span><span class="sxs-lookup"><span data-stu-id="d7aae-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="d7aae-p106">Exchange Online geht einen Schritt weiter. Nach der Clientcomputer mit der nächsten Rechenzentrum verbunden ist, ein Exchange-Server in Datencenter stellt eine Verbindung mit dem Rechenzentrum der Mandanten tatsächlich gespeichert, wie in dargestellt ist die *wie funktioniert dies funktioniert im Abschnitt* unten. Exchange Online-Server in der nächsten Rechenzentrum und den Proxy der Anforderungen vom Clientcomputer an den Postfachserver. Dies beschleunigt die Erfahrung für den Clientcomputer durch Verschieben den schwierigsten zum Abrufen von e-Mail-Nachrichten und Kalenderelemente mit dem Microsoft-Netzwerk ein.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="d7aae-128">Wie funktioniert dies für standard-Cloud-angeboten?</span><span class="sxs-lookup"><span data-stu-id="d7aae-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="d7aae-p107">Dieser Verbindungsprozess ist standard für starken Datenverkehr hochwertiger Webanwendungen wie Office 365. In diesem Abschnitt werden die notwendigen und auch die Schritte im Prozess. Wenn der Client-Computer nicht im selben Bereich als den Mandanten ist, sieht die Verbindung viel anders je nach den Dienst, den, dem der Client eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="d7aae-p108">Dieses Diagramm zeigt einen Kunden in Nordamerika einen Mandanten ein standard Office 365-Angebot mit. In diesem Szenario die anfordernden Person hat in Europa getunnelt und Office 365 aus diesem Speicherort verwendet.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="d7aae-134">Der Clientcomputer fordert die lokalen DNS-Server für die Office 365 zugeordnete IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d7aae-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d7aae-135">Lokalen DNS-Server des Clientcomputers bitten Sie die Microsoft-DNS-Servern für die Office 365 zugeordnete IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d7aae-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d7aae-136">Microsoft DNS-Server zurückgeben der regionalen Servername (basierend auf den Speicherort der Client-DNS-Server) und der Clientcomputer wiederholen Sie die Schritte 1 und 2, um die IP-Adresse des regionalen Rechenzentrums Office 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d7aae-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d7aae-137">Der Clientcomputer stellt eine Verbindung zu der IP-Adresse des regionalen Rechenzentrums her.</span><span class="sxs-lookup"><span data-stu-id="d7aae-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="d7aae-138">Exchange Online-Servern herstellen eine Verbindung mit dem aktiven Rechenzentrum her, auf dem der Mandant des Kunden befindet.</span><span class="sxs-lookup"><span data-stu-id="d7aae-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Nächstes regionales Rechenzentrum](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="d7aae-140">Cloud diese Arbeit für souveräne wie angeboten?</span><span class="sxs-lookup"><span data-stu-id="d7aae-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="d7aae-p109">Diese Verbindung ist für unabhängigen Cloud-Angeboten wie etwa Office 365 vom Dienst 21 Vianet etwas unterschiedlich. Mit dem in einer unabhängigen Instanz von Office 365-Mandanten sind die nächsten Office 365-Servern, die Portal-Verbindungen akzeptieren die Server innerhalb der unabhängigen Region, in dem der Mandant befindet. In ähnlicher Weise werden Kunden, die Zugriff auf SharePoint Online in unseren unabhängigen Cloud oder standard Dienstangebote auf Front-End-Server weitergeleitet, in dem der Mandant befindet. Finden Sie unter Herstellen einer Verbindung mit dem aktiven Rechenzentrum unten.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="d7aae-145">Der Clientcomputer fordert die lokalen DNS-Server für die Office 365 zugeordnete IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d7aae-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d7aae-146">Lokalen DNS-Server des Clientcomputers bitten Sie die Microsoft-DNS-Servern für die Office 365 zugeordnete IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d7aae-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d7aae-147">Microsoft DNS-Server zurückgeben der regionalen Servername (basierend auf den Speicherort der Client-DNS-Server) und der Clientcomputer wiederholen Sie die Schritte 1 und 2, um die IP-Adresse des regionalen Rechenzentrums Office 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d7aae-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d7aae-148">Der Clientcomputer stellt eine Verbindung zu der IP-Adresse des regionalen Rechenzentrums her.</span><span class="sxs-lookup"><span data-stu-id="d7aae-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="d7aae-149">Exchange Online-Servern herstellen eine Verbindung mit dem aktiven Rechenzentrum her, auf dem der Mandant des Kunden befindet.</span><span class="sxs-lookup"><span data-stu-id="d7aae-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Nächstes regionales US-Rechenzentrum](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="d7aae-151">Herstellen einer Verbindung mit dem aktiven Rechenzentrum</span><span class="sxs-lookup"><span data-stu-id="d7aae-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="d7aae-p110">Herstellen einer Verbindung mit dem aktiven Rechenzentrum ist für das schwerer Daten übertragen Arbeitslasten und wird derzeit von SharePoint Online verwendet. Wenn Clients die Verbindung zu Office 365, versuchen, wird ihrem Browser in dieser Situation auf dem aktiven Rechenzentrum für ihre SharePoint Online-Mandanten umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="d7aae-154">Wie funktioniert das?</span><span class="sxs-lookup"><span data-stu-id="d7aae-154">How does this work?</span></span>

<span data-ttu-id="d7aae-p111">Wenn der Client-Computer mit SharePoint Online von einer anderen Region herstellt, wird die Verbindung in das aktive SharePoint Online-Rechenzentrum umgeleitet. In diesem Szenario wird der Kunde einen Standard anbietet, was die verbleibenden lokalen Portal Verbindungen und die SharePoint Online Verbindungen weitergeleitet werden dem aktiven Rechenzentrum verwendet.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="d7aae-157">Der Clientcomputer fordert die lokalen DNS-Server für die Office 365 zugeordnete IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d7aae-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d7aae-158">Lokalen DNS-Server des Clientcomputers bitten Sie die Microsoft-DNS-Servern für die Office 365 zugeordnete IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d7aae-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d7aae-159">Microsoft DNS-Server zurückgeben des Servernamens das aktive SharePoint Online-Rechenzentrum (basierend auf den Speicherort der Office 365-Mandanten des Clients), und der Clientcomputer wiederholen Sie die Schritte 1 und 2, um die IP-Adresse des aktiven Office 365 Datencenters abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d7aae-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="d7aae-160">Der Clientcomputer stellt eine Verbindung zu der IP-Adresse des aktiven Rechenzentrums her.</span><span class="sxs-lookup"><span data-stu-id="d7aae-160">The client computer connects to the active datacenter IP address.</span></span>

![Aktives US-Rechenzentrum](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="d7aae-162">Herstellen einer Verbindung über virtuelle private Netzwerke (VPNs)</span><span class="sxs-lookup"><span data-stu-id="d7aae-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="d7aae-p112">Diese Art von Verbindung gilt nur, wenn ein virtuelles privates Netzwerk (VPN) von den Clientcomputern verwendet wird. In der Praxis Verhalten von Office 365 wird nicht geändert, einfach, da ein VPN verwendet wird, aber VPNs im Allgemeinen steuern zum werden, wie Clientcomputer Verbindungen zu Office 365 und in der Regel die Ergebnisse einer beeinträchtigter Oberfläche einrichten, sodass es ist wichtig, behandelt.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="d7aae-165">Wie funktioniert das?</span><span class="sxs-lookup"><span data-stu-id="d7aae-165">How does this work?</span></span>

<span data-ttu-id="d7aae-p113">Wenn der Clientcomputer eine VPN-Verbindung mit einer Unternehmenszentrale in einer anderen Region herstellt, werden die DNS-Server an, die von Office anstelle der DNS-Server am Standort des Clientcomputers verwendet. In den meisten Fällen wird diese zusätzliche Verbindung über VPN die Office 365-Erfahrung beeinträchtigt. Office 365-Dienste sind auf ungefähr in der Endbenutzer möglichst Kunden Verbindungen als optimiert. Viele Dienste nutzen die Azure edgenetzwerk, Content Delivery Networks und zuverlässige Netzwerkkapazität im Microsoft-Netzwerk zum Übermitteln von möglichen benutzerumgebung bei Netzwerk-Anforderungen für Office 365-Dienste wie ungefähr in der Client-Computer vorgenommen werden wie möglich.</span><span class="sxs-lookup"><span data-stu-id="d7aae-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="d7aae-170">Der Clientcomputer fordert den VPN-DNS Servern für die Office 365 zugeordnete IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d7aae-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d7aae-171">VPN-DNS-Server des Clientcomputers bitten Sie die Microsoft-DNS-Servern für die Office 365 zugeordnete IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d7aae-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d7aae-172">Microsoft DNS-Server zurückgeben der regionalen Servername (basierend auf den Speicherort der VPN-DNS-Server) und der Client-Computer wiederholen Sie die Schritte 1 und 2, um die IP-Adressinformationen des regionalen Rechenzentrums Office 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d7aae-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d7aae-173">Der Clientcomputer stellt eine Verbindung her in das Rechenzentrum IP-Adresse, die an der Niederlassung am nächsten ist, wenn sie eine VPN-Verbindung hergestellt.</span><span class="sxs-lookup"><span data-stu-id="d7aae-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![VPN-Datencenterkonnektivität](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="d7aae-175">Nachfolgend finden Sie ein kurzer Link, zurückkehren verwendet werden können:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="d7aae-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d7aae-176">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d7aae-176">See also</span></span>

[<span data-ttu-id="d7aae-177">Verwalten von Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="d7aae-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="d7aae-178">Netzwerkkonnektivität zu Office 365</span><span class="sxs-lookup"><span data-stu-id="d7aae-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
