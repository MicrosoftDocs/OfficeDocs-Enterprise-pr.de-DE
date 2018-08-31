---
title: Office 365 Deutschland Endpunkte
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Wenn Ihre Organisation Office 365 verwendet und legt eine Beschränkung auf Computern im Netzwerk aus eine Verbindung mit dem Internet, im folgenden finden Sie die Endpunkte (FQDNs, Ports, URLs und IPv4 und IPv6-Adressbereichen), die Sie einschließen sollte Ihre ausgehende zulassen Listen, um sicherzustellen, dass Ihre Computer können die Office 365 erfolgreich verwenden.
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540714"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="4753e-103">Office 365 Deutschland Endpunkte</span><span class="sxs-lookup"><span data-stu-id="4753e-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="4753e-104">*Betrifft: Office 365 Admin*</span><span class="sxs-lookup"><span data-stu-id="4753e-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="4753e-p101">**Zusammenfassung:** Office 365 erfordert eine Verbindung mit dem Internet. Die folgenden Endpunkte sollten für Kunden mit **Office 365 Deutschland** Pläne nur erreichbar sein.</span><span class="sxs-lookup"><span data-stu-id="4753e-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4753e-p102">Microsoft entwickelt einen REST-basierten Webdienst für die Einträge der IP-Adresse des FQDN auf dieser Seite. Mithilfe dieses neuen Diensts können Sie Geräte im Netzwerkumkreis konfigurieren und aktualisieren, z. B.Firewalls und Proxyserver. Die Liste mit Endpunkten, die aktuelle Version der Liste oder spezifische Änderungen können Sie herunterladen. Dieser Dienst wird irgendwann einmal die Einträge für das XML-Dokument, den RSS-Feed, die IP-Adresse und den FQDN auf dieser Seite ersetzen. Um diesem neuen Dienst auszuprobieren, wechseln Sie zu [Webdienst](managing-office-365-endpoints.md#webservice).</span><span class="sxs-lookup"><span data-stu-id="4753e-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
 <span data-ttu-id="4753e-112">**Office 365-Endpunkten:** [Worldwide (einschließlich GCC)](urls-and-ip-address-ranges.md)   |  [Office 365 von 21 Vianet betrieben](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Deutschland* | [Office 365 US-Regierung DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 US Behörden GCC hoch](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="4753e-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="4753e-113">**Letzte Aktualisierung:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Liste der Änderungen an den Office 365 Deutschland-Endpunkten](office-365-germany-endpoints-change-log.md)</span><span class="sxs-lookup"><span data-stu-id="4753e-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [List of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md)</span></span>||

<span data-ttu-id="4753e-p103">Beginnen Sie mit [Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md) , unsere Empfehlungen zum Verwalten von Netzwerkkonnektivität mithilfe dieser Daten zu verstehen. Endpunkte Daten werden am Anfang des mit neuen IP-Adressen und URLs, die 30 Tage vor aktiv veröffentlicht jeden Monat aktualisiert. Dies ermöglicht Kunden, die nicht noch haben automatische Updates, um ihre Prozesse abschließen, damit die neue Verbindung erforderlich ist. Endpunkte können auch im Monat aktualisiert werden, bei Bedarf Unterstützung schreiben, Sicherheitsvorfälle oder sonstige unmittelbaren betriebsbereiten Anforderungen. Sie können jederzeit auf die [Liste der Änderungen an den Office 365 Deutschland Endpunkten](office-365-germany-endpoints-change-log.md)verweisen.</span><span class="sxs-lookup"><span data-stu-id="4753e-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. You can always refer to the [list of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md).</span></span>

<span data-ttu-id="4753e-p104">Auf dieser Seite unten angezeigten Daten werden alle aus den REST-basierte Web Services generiert. Wenn Sie ein Skript oder ein Netzwerkgerät für die Zugriff auf diese Daten verwenden, sollten Sie direkt mit dem [Webdienst](managing-office-365-endpoints.md#webservice) wechseln.</span><span class="sxs-lookup"><span data-stu-id="4753e-p104">The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="4753e-p105">Unten Endpunktdaten werden Anforderungen für die Konnektivität zwischen dem Computer eines Benutzers zu Office 365 aufgelistet. Es ist nicht Netzwerkverbindungen von Microsoft in einem Kundennetzwerk, manchmal als Hybrid oder eingehende Netzwerkverbindungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="4753e-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="4753e-p106">Die Endpunkte werden in vier Servicebereiche gruppiert. Die ersten drei Servicebereiche können unabhängig voneinander Konnektivität ausgewählt werden. Vierte Servicebereich ist eine allgemeine Abhängigkeit (Microsoft 365 häufige und Office Online genannt) und Netzwerkkonnektivität muss immer besitzen.</span><span class="sxs-lookup"><span data-stu-id="4753e-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="4753e-126">Datenspalten angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="4753e-126">Data columns shown are:</span></span>

- <span data-ttu-id="4753e-p107">**ID**: die ID-Nummer der Zeile, auch bekannt als eine Menge Endpunkt. Diese ID ist identisch mit von den Webdienst für den Endpunkt ein zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="4753e-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="4753e-p108">**Kategorie**: Zeigt an, ob der Endpunkt Satz als "Optimieren", "Zulassen" oder "Standard" kategorisiert wird. Informationen zu diesen Kategorien und Richtlinien für die Verwaltung von ihnen am [http://aka.ms/pnc](http://aka.ms/pnc). Diese Spalte enthält auch der Endpunkt legt Netzwerkkonnektivität verfügen müssen. Für den Endpunkt legt fest, welche nicht erforderlich sind, um über Netzwerkkonnektivität verfügen, bieten wir Notizen in dieses Feld, um anzugeben, welche Funktionalität wäre nicht vorhanden, wenn der Endpunkt Satz ausgeschlossen wird. Wenn Sie einen gesamten Dienst Bereich ausschließen, ist der Endpunkt legt nach Bedarf aufgeführt Konnektivität nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4753e-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="4753e-p109">**ER**: Dies ist **Ja** , wenn der Endpunkt Satz mit Office 365 Route Präfixen über Azure ExpressRoute unterstützt wird. Die BGP-Community, die Route Präfixe dargestellt enthält, ausgerichtet Servicebereich aufgeführt. Wenn ER **keine**ist, bedeutet dies, dass ExpressRoute für diesen Endpoint nicht unterstützt wird. Allerdings sollten nicht angenommen, dass keine Routen für einen Endpunkt Satz bekannt gegeben werden, in dem ER **No**ist.</span><span class="sxs-lookup"><span data-stu-id="4753e-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="4753e-p110">**Adressen**: Listet die FQDNs oder Platzhalter-Domänennamen und IP-Adressbereiche für den Endpunkt ein. Beachten Sie, dass ein IP-Adressbereich befindet sich in CIDR-Format und kann viele einzelne IP-Adressen in das angegebene Netzwerk enthalten.</span><span class="sxs-lookup"><span data-stu-id="4753e-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="4753e-p111">**Ports**: Listet die TCP oder UDP-Ports, die mit der Adressen an, die den Netzwerkendpunkt bilden kombiniert werden. Sie möglicherweise einige Duplikate IP-Adressbereiche fest, in denen es verschiedene Ports aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="4753e-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

