---
title: URLs und IP-Adressbereiche für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Summary: Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: 175359f998c4dd695c301540f94e7d7527377ffc
ms.sourcegitcommit: 338e3bcf0a62842fbbb17145b67a4a93f3b90aac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "45091206"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Office 365-URLs und -IP-Adressbereiche

Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).
  
> [!NOTE]
> Im Rahmen der von Microsoft in Reaktion auf die COVID-19-Krise ergriffenen Maßnahmen hat Microsoft beschlossen, ein vorübergehendes Moratorium zu verhängen und die Einführung einiger geplanter Änderungen in Bezug auf URLs und IP-Adressen zu verschieben. Dieses Moratorium dient dazu, es den IT-Teams unserer Kunden zu ermöglichen, mit größtmöglicher Zuversicht und möglichst unkompliziert empfohlene Netzwerkoptimierungen für Office 365-Szenarios zu implementieren, die auf die Telearbeit ausgelegt sind. Vom 24. März 2020 bis zum 30. Juni 2020 werden im Rahmen dieses Moratoriums Änderungen an IP-Bereichen und URLs, die in der Kategorie „Optimieren“ enthalten sind, für wichtige Office 365-Dienste (Exchange Online, SharePoint Online und Microsoft Teams) ausgesetzt. Änderungen innerhalb anderer Endpunktkategorien erfolgen wie üblich. Während dieses Zeitraums können Kunden die Dienstendpunkt-Definitionen für die Office 365-Kategorie „Optimieren“auf statische Weise verwenden, um gezielte Netzwerkoptimierungen (wie Bandbreitenreservierungen oder das Konfigurieren von Split-Tunnel-VPNs) mit minimalem Risiko für die Office 365-Konnektivität aufgrund von Änderungen im Cloud-Netzwerk durchzuführen. Um sicherzustellen, dass keine Dienstunterbrechungen am Ende des Moratoriums auftreten, empfiehlt Microsoft dringend, dass Kunden Änderungsverwaltungs- und/oder Automatisierungsprozesse für Office 365-Dienstendpunkte implementieren, indem Sie die Anweisungen unter [Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md) befolgen.

> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
*Office 365 Weltweit (+GCC)* | [Office 365, betrieben von 21Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Deutschland](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
||||
|:-----|:-----|:-----|
|**Letzte Aktualisierung:** 09.07.2020 – ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement des Änderungsprotokolls](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Download:** alle erforderlichen und optionalen Ziele in einer Liste im [JSON-Format](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> | **Verwendung:** unsere Proxy-[PAC-Dateien](managing-office-365-endpoints.md#pacfiles) <br/> |

 Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.

Endpoint data below lists requirements for connectivity from a user's machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections. See [Additional endpoints](additional-office365-ip-addresses-and-urls.md) for more information.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Dies sind die dargestellten Datenspalten:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as "Optimize", "Allow", or "Default". You can read about these categories and guidance for management of them at [New Office 365 endpoint categories](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
>Empfehlungen zu Yammer-IP-Adressen und -URLs finden Sie [in diesem Blogbeitrag](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).
>

## <a name="related-topics"></a>Verwandte Themen

[Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md)
  
[Problembehandlung bei Office 365-Verbindungen](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Clientkonnektivität](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Netzwerke für die Inhaltsübermittlung](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[IP-Bereiche von Microsoft Azure-Rechenzentren](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Öffentlicher Microsoft IP-Bereich](https://www.microsoft.com/download/details.aspx?id=53602)
