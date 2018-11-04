---
title: Endpunkte für Office 365 Deutschland
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
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
ms.openlocfilehash: 080f37d8f8cc6ad201ec9fd65489072c0ec1e585
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933112"
---
# <a name="office-365-germany-endpoints"></a>Endpunkte für Office 365 Deutschland

 *Betrifft: Office 365 Admin*

**Zusammenfassung:** Office 365 erfordert eine Verbindung mit dem Internet. Die folgenden Endpunkte sollten für Kunden mit **Office 365 Deutschland** Pläne nur erreichbar sein.
  
> [!NOTE]
> Microsoft hat einen REST-Webdienst für die IP-Adresse und den FQDN-Einträge auf dieser Seite veröffentlicht. Dieser neue Dienst helfen Ihnen beim Konfigurieren und Aktualisieren von Umkreisnetzwerk Netzwerkgeräte wie beispielsweise durch Firewalls und Proxyserver. Sie können die Liste der Endpunkte, die aktuelle Version der Liste oder bestimmter Änderungen herunterladen. Dieser Dienst wird das XML-Dokument verknüpft auf dieser Seite auf 2 Oktober 2018 veraltet wurde ersetzt. Wenn Sie diese neuen Dienst testen möchten, wechseln Sie zur [-Webdienst](office-365-ip-web-service.md).
  
 **Office 365-Endpunkte:** [Weltweit (einschließlich GCC)](urls-and-ip-address-ranges.md)  | [Office 365, betrieben von 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Deutschland* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Letzte Aktualisierung:** 11/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Änderungsprotokoll-Abonnement](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**Herunterladen:** alle erforderlichen und optionalen Ziele in einer Liste mit [JSON formatiert](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) .  <br/> |

Beginnen Sie mit [Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md) , unsere Empfehlungen zum Verwalten von Netzwerkkonnektivität mithilfe dieser Daten zu verstehen. Endpunkte Daten werden am Anfang des mit neuen IP-Adressen und URLs, die 30 Tage vor aktiv veröffentlicht jeden Monat aktualisiert. Auf diese Weise können Kunden, die nicht noch haben automatische Updates, um ihre Prozesse abschließen, damit die neue Verbindung erforderlich ist. Endpunkte können auch im Monat aktualisiert werden, bei Bedarf Unterstützung schreiben, Sicherheitsvorfälle oder sonstige unmittelbaren betriebsbereiten Anforderungen. Sie können jederzeit auf die [Log-Abonnement ändern](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)verweisen.

Auf dieser Seite unten angezeigten Daten werden alle aus den REST-basierte Web Services generiert. Wenn Sie ein Skript oder ein Netzwerkgerät für die Zugriff auf diese Daten verwenden, sollten Sie direkt mit dem [Webdienst](office-365-ip-web-service.md) wechseln.

In den Endpunktdaten unten sind Anforderungen für Netzwerkkonnektivität zwischen dem Computer eines Benutzers und Office 365 aufgelistet. Sie umfassen keine Netzwerkverbindungen von Microsoft mit einem Kundennetzwerk, manchmal auch als hybride oder eingehende Netzwerkverbindungen bezeichnet.

Die Endpunkte sind in vier Dienstbereichen zusammengefasst. Die ersten drei Dienstbereiche können zu Konnektivitätszwecken unabhängig voneinander ausgewählt werden. Beim vierten Dienstbereich besteht eine gemeinsame Abhängigkeit (als Microsoft 365 Common und Office Online bezeichnet); er muss immer über Netzwerkkonnektivität verfügen.

Dies sind die dargestellten Datenspalten:

- **ID**: Die ID-Nummer der Zeile, auch als Endpunktsatz bezeichnet. Dies ist die ID, die auch vom Webdienst für den Endpunktsatz zurückgegeben wird.

- **Kategorie**: Zeigt, ob der Endpunktsatz als "Optimize" (Optimieren), "Allow" (Zulassen) oder "Default" (Standard) kategorisiert ist. Informationen zu diesen Kategorien und eine Anleitung zu ihrer Verwaltung finden Sie unter [http://aka.ms/pnc](http://aka.ms/pnc). In dieser Spalte sind außerdem die Endpunktsätze aufgelistet, die für Netzwerkkonnektivität erforderlich sind. Für Endpunktsätze, für die keine Netzwerkkonnektivität erforderlich ist, geben wir in diesem Feld Anmerkungen, aus denen hervorgeht, welche Funktionalität durch ein Blockieren des Endpunktsatzes entfallen würde. Wenn Sie einen gesamten Dienstbereich ausschließen, ist für dessen als erforderlich aufgeführte Endpunktsätze keine Konnektivität erforderlich.

- **ER**: Der Wert ist **Yes** (Ja), wenn der Endpunktsatz über Azure ExpressRoute mit Office 365-Routingpräfixen unterstützt wird. Die BGP-Community, die die angegebenen Routingpräfixe enthält, ist dem aufgeführten Dienstbereich zugeordnet. Der Wert **No** (Nein) für ER bedeutet, dass ExpressRoute für den betreffenden Endpunktsatz nicht unterstützt wird. Es sollte jedoch nicht davon ausgegangen werden, dass für einen Endpunktsatz mit **No** für ER keine Routen angekündigt werden.

- **Adressen**: Listet die FQDNs oder Platzhalter-Domänennamen und IP-Adressbereiche für den Endpunktsatz auf. Beachten Sie, dass IP-Adressbereiche im CIDR-Format angegeben sind und viele Einzel-IP-Adressen im angegebenen Netzwerk einschließen können.
 
- **Ports**: Listet die TCP- oder UDP-Ports auf, die zusammen mit den Adressen die Netzwerkendpunkte bilden. Wenn verschiedene Ports aufgeführt sind, fallen Ihnen möglicherweise Doppelungen bei den IP-Adressbereichen auf.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

