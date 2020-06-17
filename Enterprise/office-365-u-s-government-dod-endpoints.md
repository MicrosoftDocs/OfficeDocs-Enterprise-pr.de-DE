---
title: Office 365 US Government DoD-Endpunkte
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/16/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
f1.keywords:
- NOCSH
description: 'Zusammenfassung: Office 365 erfordert eine Verbindung mit dem Internet. Die folgenden Endpunkte sollten für Kunden erreichbar sein, die nur Office 365 US Government DoD-Pläne verwenden.'
hideEdit: true
ms.openlocfilehash: 7fc3f0919022903cc2b024b11e9ec17e84431bf0
ms.sourcegitcommit: f2a4b77c8c3932beb1a78bf2f5bf793fefb3fa49
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2020
ms.locfileid: "44747401"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 US Government DoD-Endpunkte

*Gilt für: Office 365 Administrator*

 **Zusammenfassung:** Für Office 365 ist eine Verbindung mit dem Internet erforderlich. Die folgenden Endpunkte sollten für Kunden erreichbar sein, die nur Office 365 US Government DoD-Pläne verwenden.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Office 365-Endpunkte:** [Weltweit (einschließlich GCC)](urls-and-ip-address-ranges.md) | [Office 365, betrieben von 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Deutschland](office-365-germany-endpoints.md) | *Office 365 U.S. Government DoD* | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Letzte Aktualisierung:** 06/16/2020- ![ RSS- ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Änderungsprotokoll Abonnement](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Download:** die vollständige Liste im [JSON-Format](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |

 Beginnen Sie mit der [Verwaltung Office 365 Endpunkte](managing-office-365-endpoints.md) , um unsere Empfehlungen für die Verwaltung der Netzwerkkonnektivität mithilfe dieser Daten zu verstehen. Endpunkte-Daten werden zu Beginn jedes Monats mit neuen IP-Adressen und URLs aktualisiert, die 30 Tage vor der aktiven Veröffentlichung veröffentlicht wurden. Auf diese Weise können Kunden, die noch nicht über automatisierte Updates verfügen, Ihre Prozesse abschließen, bevor neue Verbindungen erforderlich sind. Endpunkte können auch während des Monats bei Bedarf aktualisiert werden, um Support Eskalationen, Sicherheitsvorfälle oder andere unmittelbare betriebliche Anforderungen zu beheben. Die auf dieser Seite unten gezeigten Daten werden aus den Rest-basierten Webdiensten generiert. Wenn Sie für den Zugriff auf diese Daten ein Skript oder ein Netzwerkgerät verwenden, sollten Sie direkt zum [Webdienst](office-365-ip-web-service.md) wechseln.

In den folgenden Endpunkt Daten werden die Anforderungen für die Konnektivität zwischen dem Computer eines Benutzers und Office 365 aufgeführt. Es schließt keine Netzwerkverbindungen von Microsoft in ein Kundennetzwerk ein, die auch als Hybrid-oder eingehende Netzwerkverbindungen bezeichnet werden. Weitere Informationen finden Sie unter [zusätzliche Endpunkte, die nicht im Webdienst enthalten sind](additional-office365-ip-addresses-and-urls.md). 

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Dies sind die dargestellten Datenspalten:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **Er**: Dies ist **Ja** , wenn der Endpunkt Satz über Azure Express Route mit Office 365-Routen Präfixen unterstützt wird. Die BGP-Community, die die angegebenen Routen Präfixe enthält, wird mit dem angegebenen Dienstbereich ausgerichtet. Wenn er **Nein**ist, bedeutet dies, dass Express Route für diese endpunktgruppe nicht unterstützt wird. Es sollte jedoch nicht davon ausgegangen werden, dass keine Routen für einen Endpunkt festgelegt werden, in dem er **nicht ist.** Wenn Sie Azure AD Connect verwenden möchten, lesen Sie den [Abschnitt spezielle Überlegungen](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) , um sicherzustellen, dass Sie über die entsprechende Azure AD Connect-Konfiguration verfügen.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Hinweise zu dieser Tabelle:

- Das Security and Compliance Center (SCC) bietet Unterstützung für Azure Express Route für Office 365. Gleiches gilt für viele Features, die über den SCC verfügbar gemacht werden, wie Berichterstellung, Überwachung, erweiterte eDiscovery, Unified DLP und Datensteuerung. Zwei spezifische Features, PST-Import und eDiscovery-Export, unterstützen derzeit keine Azure-Express Route mit nur Office 365 Routenfiltern aufgrund ihrer Abhängigkeit von Azure-BLOB-Speicher. Um diese Funktionen nutzen zu können, benötigen Sie eine separate Konnektivität mit Azure-BLOB-Speicher mithilfe aller unterstützenden Azure-Verbindungsoptionen, einschließlich Internet Konnektivität oder Azure Express Route mit Azure Public Route Filters. Sie müssen die Einrichtung einer solchen Konnektivität für diese beiden Features auswerten. Das Team für Office 365 Information Protection kennt diese Einschränkung und arbeitet aktiv an der Unterstützung von Azure Express Route für Office 365, die auf Office 365 Routenfilter für beide Features beschränkt sind.

- Es gibt zusätzliche optionale Endpunkte für Microsoft 365-Apps für Unternehmen, die nicht aufgeführt sind und für Benutzer nicht erforderlich sind, um Microsoft 365-Apps für Enterprise-Anwendungen zu starten und Dokumente zu bearbeiten. Optionale Endpunkte werden in Microsoft-Rechenzentren gehostet und verarbeiten, übertragen oder speichern keine Kundendaten. Es wird empfohlen, dass Benutzer Verbindungen mit diesen Endpunkten an den standardmäßigen Internet Ausgangs Perimeter weitergeleitet werden.
