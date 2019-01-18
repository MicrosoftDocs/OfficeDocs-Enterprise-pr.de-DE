---
title: US-Regierung GCC hohe Office 365-Endpunkten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/17/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Wenn Ihre Organisation Office 365 verwendet und legt eine Beschränkung auf Computern im Netzwerk aus eine Verbindung mit dem Internet, im folgenden finden Sie die Endpunkte (FQDNs, Ports, URLs, IPv4 und IPv6-Adressbereichen), die Sie einschließen sollte Ihre ausgehende zulassen Listen, um sicherzustellen, dass Ihre Computer können die Office 365 erfolgreich verwenden.
hideEdit: true
ms.openlocfilehash: 5c849775c8fd55d9e4196ebad6c55cdf56d2ab60
ms.sourcegitcommit: 0c4f50aa55699b8390038efbb8b50dbe10f3eefe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "28723382"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>US-Regierung GCC hohe Office 365-Endpunkten

 *Betrifft: Office 365 Admin*

**Zusammenfassung:** Office 365 erfordert eine Verbindung mit dem Internet. Die folgenden Endpunkte sollten für Kunden mit Office 365 US-Regierung GCC hohe Pläne nur erreichbar sein.
  
> [!NOTE]
> Microsoft hat einen REST-basierten Webdienst für die IP-Adress- und FQDN-Einträge auf dieser Seite veröffentlicht. Mithilfe dieses neuen Diensts können Sie Geräte im Netzwerkumkreis konfigurieren und aktualisieren, z. B. Firewalls und Proxyserver. Die Liste mit Endpunkten, die aktuelle Version der Liste oder spezifische Änderungen können heruntergeladen werden. Dieser Dienst ersetzt das mit dieser Seite verknüpfte XML-Dokument, dessen Unterstützung am 2. Oktober 2018 endete. Um diesem neuen Dienst auszuprobieren, wechseln Sie zu [Webdienst](office-365-ip-web-service.md).
  
 **Office 365-Endpunkte:** [Weltweit (einschließlich GCC)](urls-and-ip-address-ranges.md) | [Office 365, betrieben von 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Deutschland](office-365-germany-endpoints.md)  | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |
  
|||
|:-----|:-----|
|**Letzte Aktualisierung:** 01/17/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Änderungsprotokoll-Abonnement](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Herunterladen:** die vollständige Liste im [JSON-Format](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Beginnen Sie mit [Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md) , unsere Empfehlungen zum Verwalten von Netzwerkkonnektivität mithilfe dieser Daten zu verstehen. Endpunkte Daten werden am Anfang des mit neuen IP-Adressen und URLs, die 30 Tage vor aktiv veröffentlicht jeden Monat aktualisiert. Auf diese Weise können Kunden, die nicht noch haben automatische Updates, um ihre Prozesse abschließen, damit die neue Verbindung erforderlich ist. Endpunkte können auch im Monat aktualisiert werden, bei Bedarf Unterstützung schreiben, Sicherheitsvorfälle oder sonstige unmittelbaren betriebsbereiten Anforderungen. Auf dieser Seite unten angezeigten Daten werden alle aus den REST-basierte Web Services generiert. Wenn Sie ein Skript oder ein Netzwerkgerät für die Zugriff auf diese Daten verwenden, sollten Sie direkt mit dem [Webdienst](office-365-ip-web-service.md) wechseln.

In den Endpunktdaten unten sind Anforderungen für Netzwerkkonnektivität zwischen dem Computer eines Benutzers und Office 365 aufgelistet. Sie umfassen keine Netzwerkverbindungen von Microsoft mit einem Kundennetzwerk, manchmal auch als hybride oder eingehende Netzwerkverbindungen bezeichnet.

Die Endpunkte sind in vier Dienstbereichen zusammengefasst. Die ersten drei Dienstbereiche können zu Konnektivitätszwecken unabhängig voneinander ausgewählt werden. Beim vierten Dienstbereich besteht eine gemeinsame Abhängigkeit (als Microsoft 365 Common und Office Online bezeichnet); er muss immer über Netzwerkkonnektivität verfügen.

Dies sind die dargestellten Datenspalten:

- **ID**: Die ID-Nummer der Zeile, auch als Endpunktsatz bezeichnet. Dies ist die ID, die auch vom Webdienst für den Endpunktsatz zurückgegeben wird.

- **Kategorie**: Zeigt, ob der Endpunktsatz als "Optimize" (Optimieren), "Allow" (Zulassen) oder "Default" (Standard) kategorisiert ist. Informationen zu diesen Kategorien und eine Anleitung zu ihrer Verwaltung finden Sie unter [http://aka.ms/pnc](http://aka.ms/pnc). In dieser Spalte sind außerdem die Endpunktsätze aufgelistet, die für Netzwerkkonnektivität erforderlich sind. Für Endpunktsätze, für die keine Netzwerkkonnektivität erforderlich ist, geben wir in diesem Feld Anmerkungen, aus denen hervorgeht, welche Funktionalität durch ein Blockieren des Endpunktsatzes entfallen würde. Wenn Sie einen gesamten Dienstbereich ausschließen, ist für dessen als erforderlich aufgeführte Endpunktsätze keine Konnektivität erforderlich.

- **ER**: Dies ist **Ja** , wenn der Endpunkt Satz mit Office 365 Route Präfixen über Azure ExpressRoute unterstützt wird. Die BGP-Community, die Route Präfixe dargestellt enthält, ausgerichtet Servicebereich aufgeführt. Wenn ER **keine**ist, bedeutet dies, dass ExpressRoute für diesen Endpoint nicht unterstützt wird. Allerdings sollten nicht angenommen, dass keine Routen für einen Endpunkt Satz bekannt gegeben werden, in dem ER **No**ist. Wenn Sie planen, Azure AD-Verbindung verwenden, lesen Sie den [Abschnitt besondere Aspekte](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) , um sicherzustellen, dass die entsprechende Konfiguration von Azure Active Directory verbinden.

- **Adressen**: Listet die FQDNs oder Platzhalter-Domänennamen und IP-Adressbereiche für den Endpunktsatz auf. Beachten Sie, dass IP-Adressbereiche im CIDR-Format angegeben sind und viele Einzel-IP-Adressen im angegebenen Netzwerk einschließen können.
 
- **Ports**: Listet die TCP- oder UDP-Ports auf, die zusammen mit den Adressen die Netzwerkendpunkte bilden. Wenn verschiedene Ports aufgeführt sind, fallen Ihnen möglicherweise Doppelungen bei den IP-Adressbereichen auf.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Hinweise zu dieser Tabelle:

- Sicherheit und Compliance Center (SCC) bietet Unterstützung für Azure ExpressRoute für Office 365. Dies gilt für viele Funktionen, die durch die SCC wie Berichte, Überwachung, erweiterte eDiscovery, Unified DLP und Governance Daten verfügbar gemacht werden. Zwei bestimmte Features PST-Import und Export, eDiscovery unterstützt derzeit nicht Azure ExpressRoute mit nur Office 365 Routefilter aufgrund der Abhängigkeit Azure BLOB-Speicher. Um diese Features nutzen zu können, benötigen Sie separate Konnektivität mit Azure BLOB-Speicher mit jeder unterstützt Azure Konnektivitätsoptionen, einschließlich Internetkonnektivität oder Azure ExpressRoute mit Azure öffentlichen Filtern der Route. Sie müssen solche Konnektivität für beide diese Features bewerten. Das Office 365 Information Protection Team arbeitet, um Unterstützung für Azure ExpressRoute für Office 365 als begrenzt Filter für Office 365 Routen für beide diese Features Unterlagen aktiv und diese Einschränkung kennt.

- Es sind zusätzliche optionale Endpunkte für Office 365 ProPlus, die nicht aufgeführt sind, und für Benutzer Office 365 ProPlus-Anwendungen starten und Bearbeiten von Dokumenten sind nicht erforderlich. Optional Endpunkte werden in Microsoft-Rechenzentren gehostet und verarbeiten, übertragen, oder nicht Kundendaten zu speichern. Es wird empfohlen, dass benutzerverbindungen mit dieser Endpunkte an die standardmäßige Internet Ausgang Umkreisnetzwerk weitergeleitet werden.

