---
title: Übersicht über Office 365 Netzwerk-Konnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Erläutert, warum Netzwerk Optimierung für SaaS Dienste, die das Ziel der Office 365-Netzwerke, wichtig ist und wie SaaS unterschiedliche Netzwerke aus anderen Arbeitslasten erfordert.
ms.openlocfilehash: 4acaee86136c88e5ac5b3c795f594fb056d15204
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897208"
---
# <a name="office-365-network-connectivity-overview"></a>Übersicht über Office 365 Netzwerk-Konnektivität

Office 365 ist eine verteilte Software-as-a-Service (SaaS) Cloud, die Produktivität und optimierte Zusammenarbeit Szenarien über eine Reihe von Micro-Dienste und Anwendungen bereitstellt. Client-Komponenten von Office 365 wie Outlook, Word und PowerPoint auf Benutzercomputern ausführen und eine Verbindung mit anderen Komponenten von Office 365, die in Microsoft-Rechenzentren ausgeführt. Der wichtigste Faktor, der bestimmt, die Qualität der durch die Office 365-Endbenutzer ist die Zuverlässigkeit des Netzwerks und geringe Wartezeit zwischen Office 365-Clients und Office 365-Dienst Frontklappen.

In diesem Artikel lernen Sie die Ziele der Office 365-Netzwerk, und warum Office 365-Netzwerke erfordert einen anderen Ansatz Optimierung als generische Internet-Datenverkehr.

## <a name="office-365-networking-goals"></a>Office 365-Netzwerke Ziele

Das Ziel der Office 365-Netzwerke ist, durch die Endbenutzer optimieren, indem Sie einen des am wenigsten restriktiven Zugriffs zwischen Clients und der Office 365-Endpunkten am nächsten. Die Qualität des Endbenutzers direkt bezieht sich auf die Leistung und Reaktionsfähigkeit der Anwendung, die der Benutzer verwendet wird. Beispielsweise nutzt die Microsoft-Teams, geringe Latenz, damit Benutzer Anrufe, Konferenzen und-Zusammenarbeit freigegebenen Bildschirm Störung frei sind, und Outlook nutzt umfangreiche Netzwerke Konnektivität für die Sofortsuche-Features, die serverseitige Indizierung und AI nutzen Funktionen.

Das primäre Ziel des Entwurfs sollte Wartezeit zu minimieren, durch die Reduzierung der Roundtripzeit (Zeit) von Clientcomputern zu globalen Microsoft-Netzwerk, öffentliche Netzwerkbackbone Microsofts, die alle Microsoft Rechenzentren mit geringer Latenz sind , Einstiegspunkte für hohe Verfügbarkeit Cloud-Anwendung auf der ganzen Welt verteilt. Erfahren Sie mehr über das Microsoft Global Network unter [wie Microsoft erstellt das schnelle und verlässliche globale Netzwerk](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Optimieren der Leistung von Office 365 Netzwerk muss nicht kompliziert sein. Sie können die bestmögliche Leistung abrufen, indem Sie die folgenden grundlegenden Prinzipien einige:

- Identifizieren von Office 365 des Netzwerkverkehrs
- Zulassen Sie Zweigstelle Ausgang von Office 365 Netzwerkdatenverkehr an das Internet von jedem Standort, auf dem Benutzer eine Verbindung zu Office 365 herstellen,
- Lassen Sie Office 365-Datenverkehr umgehen der Proxys und Paket Prüfung Geräte zu

Weitere Informationen zu Office 365 Network Connectivity Prinzipien finden Sie unter [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Herkömmliche Netzwerkarchitekturen und SaaS

Herkömmliche Netzwerk Architekturprinzipien für Client/Server-Arbeitslasten sind der Annahme entwickelt, die den Datenverkehr zwischen Clients und Endpunkte nicht außerhalb des Firmennetzwerks befinden erweitert. Darüber hinaus in vielen Unternehmensnetzwerken, alle ausgehende internetverbindungen Durchlaufen des Firmennetzwerks befinden, und von einem zentralen Ort egress.

In herkömmlichen Netzwerk-Architekturen höhere Latenz für generische Datenverkehr im Internet ein Kompromiss erforderlich, um das Netzwerk Umkreisnetzwerk Sicherheit zu gewährleisten, und leistungsoptimierung für Datenverkehr im Internet in der Regel umfasst, aktualisieren oder sich eine Skalierung der Equipment Zeitpunkten Ausgang Netzwerk. Dadurch werden jedoch nicht die Anforderungen für eine optimale netzwerkleistung von SaaS-Diensten wie etwa Office 365 behandelt.

## <a name="identifying-office-365-network-traffic"></a>Identifizieren von Office 365 des Netzwerkverkehrs

Wir erleichtern die Office 365-Netzwerkverkehr zu identifizieren und verwalten die Netzwerk-Kennung erleichtern.

- Neue Kategorien von Netzwerkendpunkte um sehr wichtige Netzwerkdatenverkehr von Netzwerkdatenverkehr zu unterscheiden, die nicht durch Internet Wartezeiten beeinflusst wird. Es gibt nur eine begrenzte Anzahl von URLs und unterstützende IP-Adressen in der Kategorie für die wichtigsten "Optimieren".
- Webdienste für die Verwendung von Skripts oder direkten Gerätekonfiguration und Verwaltung von Office 365 Netzwerk Kennung ändern. Änderungen sind verfügbar, aus dem Webdienst oder im RSS-Format oder auf e-Mail mit einer Microsoft Flow-Vorlage.
- [Office 365 Network Partner-Programm](http://aka.ms/Office365NPP) mit Microsoft-Partnern, die die Geräte oder Dienste, die führen Sie die Office 365 Network Connectivity Prinzipien und verfügen über einfache Konfiguration, bereitstellen.

## <a name="securing-office-365-connections"></a>Schützen von Office 365-Verbindungen

Das Ziel der traditionellen Netzwerksicherheit ist das Unternehmensnetzwerk Umkreisnetzwerk vor Eindringlingen und bösartige Angriffe verstärken. Die meisten Unternehmensnetzwerken Netzwerksicherheit für Datenverkehr im Internet mithilfe von Technologien wie Proxyservern, Firewalls, SSL Umbruch zu erzwingen, und prüfen, Tiefe Paketinspektion und Data Loss Prevention-Systeme. Diese Technologien können bieten wichtige Risikominderung für generische Internet Anforderungen jedoch erheblich reduzieren Leistung, Skalierbarkeit und die Qualität des Endbenutzers auf Office 365-Endpunkten angewendet.

Office 365: hilft bei der Erfüllung der Anforderungen Ihrer Organisation für die Content-Sicherheit und Daten Usage Kompatibilität mit integrierter Sicherheit und Governance Features, die speziell für das Office 365-Features und Arbeitslasten. Weitere Informationen zu Office 365-Sicherheit und Compliance finden Sie unter der [Sicherheits-Roadmap für Office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). Weitere Informationen zu Empfehlungen und Support Position Microsofts erweiterte Netzwerk-Lösungen, die für Office 365-Datenverkehr erfahrene Verarbeitung ausführen, finden Sie unter [Verwenden von Drittanbietern Netzwerkgeräte oder Lösungen auf Office 365-Datenverkehr](https://support.microsoft.com/en-us/help/2690045).

## <a name="why-is-office-365-networking-different"></a>Warum ist Office 365 verschiedene Netzwerk?

Office 365 ist für eine optimale Leistung mit Endgeräte-Sicherheit und verschlüsselte Netzwerkverbindungen, eine Reduzierung der erforderlichen Durchsetzung von Umkreisnetzwerk vorgesehen. Office 365 Datencentern befinden sich auf der ganzen Welt und der Dienst ist darauf ausgelegt, verschiedene Methoden zum Verbinden von Clients mit besten verfügbaren Dienstendpunkte verwendet werden. Da von Benutzerdaten und Verarbeitung wird zwischen viele Microsoft-Datencenter verteilt, ist kein einzelnen Netzwerk-Endpunkt, um den Client Computer eine Verbindung herstellen können. Tatsächlich werden Daten und Dienste in Ihrem Office 365-Mandanten dynamisch optimiert, indem das Microsoft Global Network Anpassung an die geografische Standorte aus der durch Endbenutzer zugegriffen wird.

Bei Office 365-Datenverkehr Paketinspektion und zentrale Ausgang fällt bestimmte allgemeine Leistungsprobleme erstellt:

- Hoher Wartezeit kann sehr schlechten Leistung von Video- und Audiostreams und langsame Antwort des Datenabruf, sucht, Zusammenarbeit in Echtzeit, Frei/Gebucht-Kalenderinformationen, im Produkt Inhalte und andere Dienste führen.
- Verbindungen von einem zentralen Standort aus die dynamischen routing-Funktionen des Office 365 globalen Netzwerks egressing, Latenz und Roundtripzeit hinzufügen
- Office 365 Netzwerkdatenverkehr Entschlüsseln von SSL gesichert und erneut verschlüsseln kann dazu führen, dass das Protokollfehler und Sicherheitsrisiko hat

Verkürzen des Netzwerkpfades zur Office 365 Einstiegspunkte durch Zulassen der Datenverkehr von den Clients an so weit wie möglich zu ihrem geografischen Standort egress Connectivity verbessern kann Leistung und der Endbenutzer Erfahrung in Office 365. Es kann auch helfen, um die Auswirkungen der zukünftige Änderungen der Netzwerk-Architektur auf Office 365-Leistung und Zuverlässigkeit zu verringern. Das optimale Connectivity-Modell ist immer Netzwerk Ausgang am Standort des Benutzers, unabhängig davon, ob dies auf dem Unternehmensnetzwerk oder Remotestandorten wie Home, Hotels, Cafés und Flughäfen ist. Generische Datenverkehr im Internet und WAN-basierte corporate Netzwerkdatenverkehr würde separat weitergeleitet und nicht mithilfe des lokalen direkte Ausgang-Objektmodells. Dieses Modell lokalen direkte Ausgang wird in der folgenden Abbildung dargestellt.

![Lokale Ausgang Netzwerkarchitektur](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

Die lokale Ausgang Architektur bietet folgende Vorteile für Office 365 Netzwerkdatenverkehr über das herkömmliche Modell:
  
- Bietet eine optimale Leistung von Office 365 durch Optimieren der Route Länge. Endbenutzer-Verbindungen werden von der Microsoft Global Network _verteilten Service vorderer Klappe_ Infrastruktur dynamisch auf den nächsten Einstiegspunkt in Office 365 weitergeleitet und Datenverkehr wird dann an weitergeleitet, intern Daten- und Endpunkte über von Microsoft Dunkles äußerst geringer Latenz Hochverfügbarkeits-Fiber.
- Reduziert die Belastung Unternehmensnetzwerk-Infrastruktur durch Zulassen der lokalen Ausgang für Office 365-Datenverkehr, Proxys und Datenverkehr Prüfung Geräte zu umgehen.
- Sichert Verbindungen an beiden Enden durch die Nutzung von Client Endpunkt Sicherheit und Cloud-Sicherheitsfeatures, Anwendung von sicherheitstechnologien redundante Netzwerk zu vermeiden.

> [!NOTE]
> Die _verteilte Service vorne Tür_ -Infrastruktur ist das Microsoft Global Network hochverfügbar und skalierbare Netzwerkgrenze mit geografisch verteilten Standorten. Endbenutzer Verbindungen beendet, und leitet sie effizient innerhalb des globalen Microsoft-Netzwerks. Erfahren Sie mehr über das Microsoft Global Network unter [wie Microsoft erstellt das schnelle und verlässliche globale Netzwerk](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Weitere Informationen zum verstehen und Anwenden von Office 365 Network Connectivity Prinzipien finden Sie unter [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Schlussbemerkung

Optimieren der Leistung von Office 365 Netzwerk kommt wirklich nach unten zum Entfernen nicht benötigter Hindernisse. Indem Office 365-Verbindungen als vertrauenswürdige Datenverkehr behandelt, können Sie verhindern, dass Wartezeit von Paketinspektion und die Nachfrage nach Proxy Bandbreite eingeführt. Lokale Verbindungen zwischen Clientcomputern und Office 365-Endpunkten zulassen aktiviert Datenverkehr dynamisch über das globale Microsoft-Netzwerk weitergeleitet werden sollen.

## <a name="related-topics"></a>Verwandte Themen

[Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)

[Office 365 – IP-Adress- und URL-Webdienst](office-365-ip-web-service.md)

[Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md)

[Office 365 – IP-Adress- und URL-Webdienst](office-365-ip-web-service.md)

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)

[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)

[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)

[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)

[Wie Microsoft schnelle und zuverlässige globale Netzwerk erstellt](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
