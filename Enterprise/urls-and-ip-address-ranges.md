---
title: URLs und IP-Adressbereiche für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/29/2019
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Zusammenfassung: Office 365 erfordert eine Internetverbindung. Die unten aufgeführten Endpunkte sollten für Kunden, die Office 365-Pläne verwenden, einschließlich Government Community Cloud (GCC), erreichbar sein.'
hideEdit: true
ms.openlocfilehash: 98748ade517d6da85429e91bc5fdac0702528598
ms.sourcegitcommit: 2f172a784d2f6b29c7cf80c0dbca271ab494d514
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2019
ms.locfileid: "33867740"
---
# <a name="office-365-urls-and-ip-address-ranges"></a><span data-ttu-id="20081-104">URLs und IP-Adressbereiche für Office 365</span><span class="sxs-lookup"><span data-stu-id="20081-104">Office 365 URLs and IP address ranges</span></span>

 <span data-ttu-id="20081-p102">**Zusammenfassung:** Office 365 erfordert eine Internetverbindung. Die unten aufgeführten Endpunkte sollten für Kunden, die Office 365-Pläne verwenden, einschließlich Government Community Cloud (GCC), erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="20081-p102">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).</span></span>
  
> [!NOTE]
> <span data-ttu-id="20081-p103">Microsoft hat einen REST-basierten Webdienst für die IP-Adress- und FQDN-Einträge auf dieser Seite veröffentlicht. Mithilfe dieses neuen Diensts können Sie Geräte im Netzwerkumkreis konfigurieren und aktualisieren, z. B. Firewalls und Proxyserver. Die Liste mit Endpunkten, die aktuelle Version der Liste oder spezifische Änderungen können heruntergeladen werden. Dieser Dienst ersetzt das mit dieser Seite verknüpfte XML-Dokument, dessen Unterstützung am 2. Oktober 2018 endete. Um diesem neuen Dienst auszuprobieren, wechseln Sie zu [Webdienst](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="20081-p103">Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).</span></span>
  
<span data-ttu-id="20081-112">*Office 365 Weltweit (+GCC)* | [Office 365, betrieben von 21Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Deutschland](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span><span class="sxs-lookup"><span data-stu-id="20081-112">*Office 365 Worldwide (+GCC)* | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="20081-113">**Letzte Aktualisierung:** 29.04.2019 – ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement des Änderungsprotokolls](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="20081-113">**Last updated:** 04/29/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span> <br/> |<span data-ttu-id="20081-114">**Download:** alle erforderlichen und optionalen Ziele in einer Liste im [JSON-Format](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="20081-114">**Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list.</span></span>  <br/> | <span data-ttu-id="20081-115">**Verwendung:** unsere Proxy-[PAC-Dateien](managing-office-365-endpoints.md#pacfiles)</span><span class="sxs-lookup"><span data-stu-id="20081-115">**Use:** our proxy [PAC files](managing-office-365-endpoints.md#pacfiles)</span></span> <br/> |
   
 <span data-ttu-id="20081-p104">Beginnen Sie mit [Managing Office 365 endpoints](managing-office-365-endpoints.md) (Verwalten von Office 365-Endpunkten), um unsere Empfehlungen für das Verwalten der Netzwerkkonnektivität unter Nutzung dieser Daten nachzuvollziehen. Die Endpunktdaten werden am Anfang jedes Monats mit neuen IP-Adressen und URLs aktualisiert, die 30 Tage vor ihrem Inkrafttreten veröffentlicht werden. Dies gibt Kunden, die ihre Updates noch nicht automatisiert haben, die Möglichkeit, ihre Prozesse abzuschließen, bevor neue Verbindungsinformationen erforderlich sind. Endpunkte können darüber hinaus bei Bedarf auch innerhalb eines Monats aktualisiert werden, wenn dies erforderlich ist, um Supporteskalationen, Sicherheitsvorfällen oder sonstigen unmittelbaren Betriebserfordernissen Rechnung zu tragen. Die unten auf dieser Seite dargestellten Daten wurden alle von den REST-basierten Webdiensten generiert. Wenn Sie ein Skript oder ein Netzwerkgerät für den Zugriff auf diese Daten verwenden, sollten Sie direkt zum [Webdienst](office-365-ip-web-service.md) navigieren.</span><span class="sxs-lookup"><span data-stu-id="20081-p104">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="20081-p105">In den Endpunktdaten unten sind Anforderungen für Netzwerkkonnektivität zwischen dem Computer eines Benutzers und Office 365 aufgelistet. Sie umfassen keine Netzwerkverbindungen von Microsoft mit einem Kundennetzwerk, manchmal auch als hybride oder eingehende Netzwerkverbindungen bezeichnet. Weitere Informationen finden Sie unter [Zusätzliche Endpunkte](additional-office365-ip-addresses-and-urls.md).</span><span class="sxs-lookup"><span data-stu-id="20081-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="20081-p106">Die Endpunkte sind in vier Dienstbereichen zusammengefasst. Die ersten drei Dienstbereiche können zu Konnektivitätszwecken unabhängig voneinander ausgewählt werden. Beim vierten Dienstbereich besteht eine gemeinsame Abhängigkeit (als Microsoft 365 Common und Office Online bezeichnet); er muss immer über Netzwerkkonnektivität verfügen.</span><span class="sxs-lookup"><span data-stu-id="20081-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="20081-128">Dies sind die dargestellten Datenspalten:</span><span class="sxs-lookup"><span data-stu-id="20081-128">Data columns shown are:</span></span>

- <span data-ttu-id="20081-p107">**ID**: Die ID-Nummer der Zeile, auch als Endpunktsatz bezeichnet. Dies ist die ID, die auch vom Webdienst für den Endpunktsatz zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="20081-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="20081-p108">**Kategorie**: Zeigt, ob der Endpunktsatz als "Optimize" (Optimieren), "Allow" (Zulassen) oder "Default" (Standard) kategorisiert ist. Informationen zu diesen Kategorien und eine Anleitung zu ihrer Verwaltung finden Sie unter [http://aka.ms/pnc](http://aka.ms/pnc). In dieser Spalte sind außerdem die Endpunktsätze aufgelistet, die für Netzwerkkonnektivität erforderlich sind. Für Endpunktsätze, für die keine Netzwerkkonnektivität erforderlich ist, geben wir in diesem Feld Anmerkungen, aus denen hervorgeht, welche Funktionalität durch ein Blockieren des Endpunktsatzes entfallen würde. Wenn Sie einen gesamten Dienstbereich ausschließen, ist für dessen als erforderlich aufgeführte Endpunktsätze keine Konnektivität erforderlich.</span><span class="sxs-lookup"><span data-stu-id="20081-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="20081-p109">**ER**: Der Wert ist **Yes** (Ja), wenn der Endpunktsatz über Azure ExpressRoute mit Office 365-Routingpräfixen unterstützt wird. Die BGP-Community, die die angegebenen Routingpräfixe enthält, ist dem aufgeführten Dienstbereich zugeordnet. Der Wert **No** (Nein) für ER bedeutet, dass ExpressRoute für den betreffenden Endpunktsatz nicht unterstützt wird. Es sollte jedoch nicht davon ausgegangen werden, dass für einen Endpunktsatz mit **No** für ER keine Routen angekündigt werden.</span><span class="sxs-lookup"><span data-stu-id="20081-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="20081-p110">**Adressen**: Listet die FQDNs oder Platzhalter-Domänennamen und IP-Adressbereiche für den Endpunktsatz auf. Beachten Sie, dass IP-Adressbereiche im CIDR-Format angegeben sind und viele Einzel-IP-Adressen im angegebenen Netzwerk einschließen können.</span><span class="sxs-lookup"><span data-stu-id="20081-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="20081-p111">**Ports**: Listet die TCP- oder UDP-Ports auf, die zusammen mit den Adressen die Netzwerkendpunkte bilden. Wenn verschiedene Ports aufgeführt sind, fallen Ihnen möglicherweise Doppelungen bei den IP-Adressbereichen auf.</span><span class="sxs-lookup"><span data-stu-id="20081-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
><span data-ttu-id="20081-144">Empfehlungen zu Yammer-IP-Adressen und -URLs finden Sie [in diesem Blogbeitrag](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).</span><span class="sxs-lookup"><span data-stu-id="20081-144">For recommendations on Yammer IP addresses and URLs, see [this blog post](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).</span></span>
>


## <a name="related-topics"></a><span data-ttu-id="20081-145">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="20081-145">Related Topics</span></span>

[<span data-ttu-id="20081-146">Verwalten von Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="20081-146">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="20081-147">Problembehandlung bei Office 365-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="20081-147">Troubleshooting Office 365 connectivity</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[<span data-ttu-id="20081-148">Clientkonnektivität</span><span class="sxs-lookup"><span data-stu-id="20081-148">Client connectivity</span></span>](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[<span data-ttu-id="20081-149">Netzwerke für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="20081-149">Content delivery networks</span></span>](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[<span data-ttu-id="20081-150">IP-Bereiche von Microsoft Azure-Rechenzentren</span><span class="sxs-lookup"><span data-stu-id="20081-150">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="20081-151">Öffentlicher Microsoft IP-Bereich</span><span class="sxs-lookup"><span data-stu-id="20081-151">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)

