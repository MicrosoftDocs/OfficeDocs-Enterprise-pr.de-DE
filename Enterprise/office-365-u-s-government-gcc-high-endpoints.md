---
title: US-Regierung GCC hohe Office 365-Endpunkten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
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
ms.openlocfilehash: eb1ac47ad8317b46ce19106e8eeab5dae3c25432
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540960"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>US-Regierung GCC hohe Office 365-Endpunkten

 *Betrifft: Office 365 Admin*

**Zusammenfassung:** Office 365 erfordert eine Verbindung mit dem Internet. Die folgenden Endpunkte sollten für Kunden mit Office 365 US-Regierung GCC hohe Pläne nur erreichbar sein.
  
> [!NOTE]
> Microsoft entwickelt einen REST-basierten Webdienst für die Einträge der IP-Adresse des FQDN auf dieser Seite. Mithilfe dieses neuen Diensts können Sie Geräte im Netzwerkumkreis konfigurieren und aktualisieren, z. B.Firewalls und Proxyserver. Die Liste mit Endpunkten, die aktuelle Version der Liste oder spezifische Änderungen können Sie herunterladen. Dieser Dienst wird irgendwann einmal die Einträge für das XML-Dokument, den RSS-Feed, die IP-Adresse und den FQDN auf dieser Seite ersetzen. Um diesem neuen Dienst auszuprobieren, wechseln Sie zu [Webdienst](managing-office-365-endpoints.md#webservice).
  
 **Office 365-Endpunkten:** [Worldwide (einschließlich GCC)](urls-and-ip-address-ranges.md)  |  [Office 365 von 21 Vianet betrieben](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Deutschland](office-365-germany-endpoints.md)  | [Office 365 US-Regierung DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 US Behörden GCC hoch* |
  
|||
|:-----|:-----|
|**Letzte Aktualisierung:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Änderungsprotokoll-Abonnement](https://aka.ms/usendpointrss) <br/> |**Herunterladen:** die vollständige Liste im [XML-Format](https://aka.ms/usdefenseendpoints) <br/> |
   
 Beginnen Sie mit [Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md) , unsere Empfehlungen zum Verwalten von Netzwerkkonnektivität mithilfe dieser Daten zu verstehen. Endpunkte Daten werden am Anfang des mit neuen IP-Adressen und URLs, die 30 Tage vor aktiv veröffentlicht jeden Monat aktualisiert. Dies ermöglicht Kunden, die nicht noch haben automatische Updates, um ihre Prozesse abschließen, damit die neue Verbindung erforderlich ist. Endpunkte können auch im Monat aktualisiert werden, bei Bedarf Unterstützung schreiben, Sicherheitsvorfälle oder sonstige unmittelbaren betriebsbereiten Anforderungen. Auf dieser Seite unten angezeigten Daten werden alle aus den REST-basierte Web Services generiert. Wenn Sie ein Skript oder ein Netzwerkgerät für die Zugriff auf diese Daten verwenden, sollten Sie direkt mit dem [Webdienst](managing-office-365-endpoints.md#webservice) wechseln.

Unten Endpunktdaten werden Anforderungen für die Konnektivität zwischen dem Computer eines Benutzers zu Office 365 aufgelistet. Es ist nicht Netzwerkverbindungen von Microsoft in einem Kundennetzwerk, manchmal als Hybrid oder eingehende Netzwerkverbindungen enthalten.

Die Endpunkte werden in vier Servicebereiche gruppiert. Die ersten drei Servicebereiche können unabhängig voneinander Konnektivität ausgewählt werden. Vierte Servicebereich ist eine allgemeine Abhängigkeit (Microsoft 365 häufige und Office Online genannt) und Netzwerkkonnektivität muss immer besitzen.

Datenspalten angezeigt werden:

- **ID**: die ID-Nummer der Zeile, auch bekannt als eine Menge Endpunkt. Diese ID ist identisch mit von den Webdienst für den Endpunkt ein zurückgegeben wird.

- **Kategorie**: Zeigt an, ob der Endpunkt Satz als "Optimieren", "Zulassen" oder "Standard" kategorisiert wird. Informationen zu diesen Kategorien und Richtlinien für die Verwaltung von ihnen am [http://aka.ms/pnc](http://aka.ms/pnc). Diese Spalte enthält auch der Endpunkt legt Netzwerkkonnektivität verfügen müssen. Für den Endpunkt legt fest, welche nicht erforderlich sind, um über Netzwerkkonnektivität verfügen, bieten wir Notizen in dieses Feld, um anzugeben, welche Funktionalität wäre nicht vorhanden, wenn der Endpunkt Satz ausgeschlossen wird. Wenn Sie einen gesamten Dienst Bereich ausschließen, ist der Endpunkt legt nach Bedarf aufgeführt Konnektivität nicht erforderlich.

- **ER**: Dies ist **Ja** , wenn der Endpunkt Satz mit Office 365 Route Präfixen über Azure ExpressRoute unterstützt wird. Die BGP-Community, die Route Präfixe dargestellt enthält, ausgerichtet Servicebereich aufgeführt. Wenn ER **keine**ist, bedeutet dies, dass ExpressRoute für diesen Endpoint nicht unterstützt wird. Allerdings sollten nicht angenommen, dass keine Routen für einen Endpunkt Satz bekannt gegeben werden, in dem ER **No**ist. Wenn Sie planen, Azure AD-Verbindung verwenden, lesen Sie den [Abschnitt besondere Aspekte](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) , um sicherzustellen, dass die entsprechende Konfiguration von Azure Active Directory verbinden.

- **Adressen**: Listet die FQDNs oder Platzhalter-Domänennamen und IP-Adressbereiche für den Endpunkt ein. Beachten Sie, dass ein IP-Adressbereich befindet sich in CIDR-Format und kann viele einzelne IP-Adressen in das angegebene Netzwerk enthalten.
 
- **Ports**: Listet die TCP oder UDP-Ports, die mit der Adressen an, die den Netzwerkendpunkt bilden kombiniert werden. Sie möglicherweise einige Duplikate IP-Adressbereiche fest, in denen es verschiedene Ports aufgeführt sind.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Hinweise zu dieser Tabelle:

- Sicherheit und Compliance Center (SCC) bietet Unterstützung für Azure ExpressRoute für Office 365. Dies gilt für viele Funktionen, die durch die SCC wie Berichte, Überwachung, erweiterte eDiscovery, Unified DLP und Governance Daten verfügbar gemacht werden. Zwei bestimmte Features PST-Import und Export, eDiscovery unterstützt derzeit nicht Azure ExpressRoute mit nur Office 365 Routefilter aufgrund der Abhängigkeit Azure BLOB-Speicher. Um diese Features nutzen zu können, benötigen Sie separate Konnektivität mit Azure BLOB-Speicher mit jeder unterstützt Azure Konnektivitätsoptionen, einschließlich Internetkonnektivität oder Azure ExpressRoute mit Azure öffentlichen Filtern der Route. Sie müssen solche Konnektivität für beide diese Features bewerten. Das Office 365 Information Protection Team arbeitet, um Unterstützung für Azure ExpressRoute für Office 365 als begrenzt Filter für Office 365 Routen für beide diese Features Unterlagen aktiv und diese Einschränkung kennt.

- Es sind zusätzliche optionale Endpunkte für Office 365 ProPlus, die nicht aufgeführt sind, und für Benutzer Office 365 ProPlus-Anwendungen starten und Bearbeiten von Dokumenten sind nicht erforderlich. Optional Endpunkte werden in Microsoft-Rechenzentren gehostet und verarbeiten, übertragen, oder nicht Kundendaten zu speichern. Es wird empfohlen, dass benutzerverbindungen mit dieser Endpunkte an die standardmäßige Internet Ausgang Umkreisnetzwerk weitergeleitet werden.

