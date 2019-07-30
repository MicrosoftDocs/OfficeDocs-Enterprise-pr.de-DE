---
title: Endpunkte – Office 365 Deutschland
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/29/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Wenn Ihre Organisation Office 365 verwendet und Computer in Ihrem Netzwerk von der Verbindung mit dem Internet einschränkt, finden Sie unten die Endpunkte (FQDNs, Ports, URLs und IPv4-und IPv6-Adressbereiche), die Sie in Ihre ausgehenden Zulassungslisten aufnehmen sollten, um sicherzustellen, dass Ihre Computer können Office 365 erfolgreich verwenden.
hideEdit: true
ms.openlocfilehash: 9b97f9b085dee8ae3866d9cf85a56019167925c6
ms.sourcegitcommit: b9ddc5bf47e4c47c7883180db9ef5ad286d6e2fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "35925117"
---
# <a name="office-365-germany-endpoints"></a>Endpunkte – Office 365 Deutschland

 *Gilt für: Office 365 Administrator*

**Zusammenfassung:** Für Office 365 ist eine Verbindung mit dem Internet erforderlich. Die unten aufgeführten Endpunkte sollten nur für Kunden erreichbar sein, die **Office 365 Deutschland** -Pläne verwenden.
  
> [!NOTE]
> Microsoft hat einen REST-basierten Webdienst für die IP-Adress- und FQDN-Einträge auf dieser Seite veröffentlicht. Mithilfe dieses neuen Diensts können Sie Geräte im Netzwerkumkreis konfigurieren und aktualisieren, z. B. Firewalls und Proxyserver. Die Liste mit Endpunkten, die aktuelle Version der Liste oder spezifische Änderungen können heruntergeladen werden. Dieser Dienst ersetzt das mit dieser Seite verknüpfte XML-Dokument, dessen Unterstützung am 2. Oktober 2018 endete. Um diesem neuen Dienst auszuprobieren, wechseln Sie zu [Webdienst](office-365-ip-web-service.md).
 
 **Office 365-Endpunkte:** [Weltweit (einschließlich GCC)](urls-and-ip-address-ranges.md)  | [Office 365, betrieben von 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Deutschland* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Letzte Aktualisierung:** 07/29/2019- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) - [Änderungsprotokoll Abonnement](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**Download:** alle erforderlichen und optionalen Ziele in einer Liste im [JSON-Format](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> |

Beginnen Sie mit der [Verwaltung Office 365](managing-office-365-endpoints.md) Endpunkte, um unsere Empfehlungen für die Verwaltung der Netzwerkkonnektivität mithilfe dieser Daten zu verstehen. Endpunkte-Daten werden zu Beginn jedes Monats mit neuen IP-Adressen und URLs aktualisiert, die 30 Tage vor der aktiven Veröffentlichung veröffentlicht wurden. Auf diese Weise können Kunden, die noch nicht über automatisierte Updates verfügen, Ihre Prozesse abschließen, bevor neue Verbindungen erforderlich sind. Endpunkte können auch während des Monats bei Bedarf aktualisiert werden, um Support Eskalationen, Sicherheitsvorfälle oder andere unmittelbare betriebliche Anforderungen zu beheben. Sie können sich jederzeit auf das [Abonnement für Änderungsprotokolle](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)berufen.

Die auf dieser Seite unten gezeigten Daten werden aus den Rest-basierten Webdiensten generiert. Wenn Sie für den Zugriff auf diese Daten ein Skript oder ein Netzwerkgerät verwenden, sollten Sie direkt zum [Webdienst](office-365-ip-web-service.md) wechseln.

In den Endpunktdaten unten sind Anforderungen für Netzwerkkonnektivität zwischen dem Computer eines Benutzers und Office 365 aufgelistet. Sie umfassen keine Netzwerkverbindungen von Microsoft mit einem Kundennetzwerk, manchmal auch als hybride oder eingehende Netzwerkverbindungen bezeichnet.

Die Endpunkte sind in vier Dienstbereiche unterteilt. Die ersten drei Dienstbereiche können für die Konnektivität unabhängig ausgewählt werden. Der vierte Dienstbereich ist eine allgemeine Abhängigkeit (Microsoft 365 Common and Office) und muss immer über Netzwerkkonnektivität verfügen.

Dies sind die dargestellten Datenspalten:

- **ID**: Die ID-Nummer der Zeile, auch als Endpunktsatz bezeichnet. Dies ist die ID, die auch vom Webdienst für den Endpunktsatz zurückgegeben wird.

- **Kategorie**: Zeigt, ob der Endpunktsatz als "Optimize" (Optimieren), "Allow" (Zulassen) oder "Default" (Standard) kategorisiert ist. Informationen zu diesen Kategorien und eine Anleitung zu ihrer Verwaltung finden Sie unter [http://aka.ms/pnc](http://aka.ms/pnc). In dieser Spalte sind außerdem die Endpunktsätze aufgelistet, die für Netzwerkkonnektivität erforderlich sind. Für Endpunktsätze, für die keine Netzwerkkonnektivität erforderlich ist, geben wir in diesem Feld Anmerkungen, aus denen hervorgeht, welche Funktionalität durch ein Blockieren des Endpunktsatzes entfallen würde. Wenn Sie einen gesamten Dienstbereich ausschließen, ist für dessen als erforderlich aufgeführte Endpunktsätze keine Konnektivität erforderlich.

- **ER**: Der Wert ist **Yes** (Ja), wenn der Endpunktsatz über Azure ExpressRoute mit Office 365-Routingpräfixen unterstützt wird. Die BGP-Community, die die angegebenen Routingpräfixe enthält, ist dem aufgeführten Dienstbereich zugeordnet. Der Wert **No** (Nein) für ER bedeutet, dass ExpressRoute für den betreffenden Endpunktsatz nicht unterstützt wird. Es sollte jedoch nicht davon ausgegangen werden, dass für einen Endpunktsatz mit **No** für ER keine Routen angekündigt werden.

- **Adressen**: Listet die FQDNs oder Platzhalter-Domänennamen und IP-Adressbereiche für den Endpunktsatz auf. Beachten Sie, dass IP-Adressbereiche im CIDR-Format angegeben sind und viele Einzel-IP-Adressen im angegebenen Netzwerk einschließen können.
 
- **Ports**: Listet die TCP- oder UDP-Ports auf, die zusammen mit den Adressen die Netzwerkendpunkte bilden. Wenn verschiedene Ports aufgeführt sind, fallen Ihnen möglicherweise Doppelungen bei den IP-Adressbereichen auf.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

