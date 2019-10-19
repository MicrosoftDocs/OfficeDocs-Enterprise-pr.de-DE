---
title: URLs und IP-Adressbereiche für Office 365, betrieben von 21Vianet
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/30/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
description: Dieser Artikel bezieht sich auf Office 365, betrieben von 21Vianet in China. In diesem Artikel sind die URLs und IP-Adressbereiche aufgelistet, die von Office 365, betrieben von 21Vianet, verwendet werden.
hideEdit: true
ms.openlocfilehash: 518bf8ead4c91a00242f50f00a95c3522bdca692
ms.sourcegitcommit: 74b6d9fc3ce0873e8564fc4de51fe3afeb122447
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "37318676"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>URLs und IP-Adressbereiche für Office 365, betrieben von 21Vianet

 *Betrifft: Office 365, betrieben von 21Vianet – Small Business-Administrator, Office 365, betrieben von 21Vianet – Administrator*

**Zusammenfassung**: Die folgenden Endpunkte (FQDNs, Ports, URLs, IPv4- und IPv6-Präfixe) gelten für Office 365, betrieben von 21Vianet, und sind für die Bereitstellung von Produktivitätsdiensten nur im Rahmen der genannten Pläne ausgelegt.
  
> [!NOTE]
> Microsoft hat einen REST-basierten Webdienst für die IP-Adress- und FQDN-Einträge auf dieser Seite veröffentlicht. Mithilfe dieses neuen Diensts können Sie Geräte im Netzwerkumkreis konfigurieren und aktualisieren, z. B. Firewalls und Proxyserver. Die Liste mit Endpunkten, die aktuelle Version der Liste oder spezifische Änderungen können heruntergeladen werden. Dieser Dienst ersetzt das mit dieser Seite verknüpfte XML-Dokument, dessen Unterstützung am 2. Oktober 2018 endete. Um diesem neuen Dienst auszuprobieren, wechseln Sie zu [Webdienst](office-365-ip-web-service.md).
  
 **Office 365-Endpunkte:** [Weltweit (einschließlich GCC)](urls-and-ip-address-ranges.md)  | *Office 365, betrieben von 21Vianet* | [Office 365 Deutschland](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Letzte Aktualisierung:** 30.9.2019 – ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement des Änderungsprotokolls](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Download:** alle erforderlichen und optionalen Ziele in einer Liste im [JSON-Format](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> |

Beginnen Sie mit [Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md), um unsere Empfehlungen für das Verwalten der Netzwerkkonnektivität unter Nutzung dieser Daten nachzuvollziehen. Die Endpunktdaten werden am Anfang jedes Monats mit neuen IP-Adressen und URLs aktualisiert, die 30 Tage vor ihrem Inkrafttreten veröffentlicht werden. Dies gibt Kunden, die ihre Updates noch nicht automatisiert haben, die Möglichkeit, ihre Prozesse abzuschließen, bevor neue Verbindungsinformationen erforderlich sind. Endpunkte können darüber hinaus bei Bedarf auch innerhalb eines Monats aktualisiert werden, wenn dies erforderlich ist, um Supporteskalationen, Sicherheitsvorfällen oder sonstigen unmittelbaren Betriebserfordernissen Rechnung zu tragen. Die unten auf dieser Seite dargestellten Daten wurden alle von den REST-basierten Webdiensten generiert. Wenn Sie ein Skript oder ein Netzwerkgerät für den Zugriff auf diese Daten verwenden, sollten Sie direkt zum [Webdienst](office-365-ip-web-service.md) navigieren.

In den Endpunktdaten unten sind Anforderungen für Netzwerkkonnektivität zwischen dem Computer eines Benutzers und Office 365 aufgelistet. Sie umfassen keine Netzwerkverbindungen von Microsoft mit einem Kundennetzwerk, manchmal auch als hybride oder eingehende Netzwerkverbindungen bezeichnet.

Die Endpunkte sind in vier Dienstbereiche unterteilt. Die ersten drei Dienstbereiche können unabhängig voneinander für die Verbindung ausgewählt werden. Der vierte Dienstbereich ist eine häufige Abhängigkeit (auch Microsoft 365 Common und Office genannt), und Sie müssen immer über eine Netzwerkverbindung verfügen.

Dies sind die dargestellten Datenspalten:

- **ID**: Die ID-Nummer der Zeile, auch als Endpunktsatz bezeichnet. Dies ist die ID, die auch vom Webdienst für den Endpunktsatz zurückgegeben wird.

- **Kategorie**: Zeigt, ob der Endpunktsatz als "Optimize" (Optimieren), "Allow" (Zulassen) oder "Default" (Standard) kategorisiert ist. Informationen zu diesen Kategorien und eine Anleitung zu ihrer Verwaltung finden Sie unter [http://aka.ms/pnc](http://aka.ms/pnc). In dieser Spalte sind außerdem die Endpunktsätze aufgelistet, die für Netzwerkkonnektivität erforderlich sind. Für Endpunktsätze, für die keine Netzwerkkonnektivität erforderlich ist, geben wir in diesem Feld Anmerkungen, aus denen hervorgeht, welche Funktionalität durch ein Blockieren des Endpunktsatzes entfallen würde. Wenn Sie einen gesamten Dienstbereich ausschließen, ist für dessen als erforderlich aufgeführte Endpunktsätze keine Konnektivität erforderlich.

- **ER**: Der Wert ist **Yes** (Ja), wenn der Endpunktsatz über Azure ExpressRoute mit Office 365-Routingpräfixen unterstützt wird. Die BGP-Community, die die angegebenen Routingpräfixe enthält, ist dem aufgeführten Dienstbereich zugeordnet. Der Wert **No** (Nein) für ER bedeutet, dass ExpressRoute für den betreffenden Endpunktsatz nicht unterstützt wird. Es sollte jedoch nicht davon ausgegangen werden, dass für einen Endpunktsatz mit **No** für ER keine Routen angekündigt werden.

- **Adressen**: Listet die FQDNs oder Platzhalter-Domänennamen und IP-Adressbereiche für den Endpunktsatz auf. Beachten Sie, dass IP-Adressbereiche im CIDR-Format angegeben sind und viele Einzel-IP-Adressen im angegebenen Netzwerk einschließen können.
 
- **Ports**: Listet die TCP- oder UDP-Ports auf, die zusammen mit den Adressen die Netzwerkendpunkte bilden. Wenn verschiedene Ports aufgeführt sind, fallen Ihnen möglicherweise Doppelungen bei den IP-Adressbereichen auf.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](./includes/office-365-operated-by-21vianet-endpoints.md)]


