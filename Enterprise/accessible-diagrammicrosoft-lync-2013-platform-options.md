---
title: Verfügbares Diagramm - Microsoft Lync 2013-Plattformoptionen
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: Dieser Artikel ist eine leicht zugängliche Textversion des Diagramms namens „Microsoft Lync 2013-Plattformoptionen, das unter Technische Diagramme verfügbar ist.
ms.openlocfilehash: a62fb6d1e1ee7fbddb79b0aec4ddafea4b07b4fe
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030599"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>Verfügbares Diagramm – Microsoft Lync 2013-Plattformoptionen

**Zusammenfassung:** Dieser Artikel ist eine leicht zugängliche Textversion des Diagramms namens „Microsoft Lync 2013-Plattformoptionen", das unter [Technische Diagramme](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409) verfügbar ist.
  
Dieses Poster beschreibt, was Unternehmensentscheidungsträger (Business Decision Makers, BDMs) und -architekten über Lync Online- (Office 365) und Lync Server-Bereitstellungen wissen müssen. Es umfasst Folgendes:
  
- Einen Vergleich von vier verschiedenen Bereitstellungsoptionen: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server und vom Anbieter gehostetes Lync Server. 
    
- Zwei Beispielszenarien für die Bereitstellung von Lync 2013.
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Vergleich von vier verschiedenen Bereitstellungen für die Lync 2013-Plattform

Der Vergleich stellt Informationen zu den einzelnen Bereitstellungsoptionen in den folgenden Bereichen bereit: 
  
- Übersicht der verschiedenen Bereitstellungsfeatures
    
- Vorteile des Implementierens der einzelnen Bereitstellungsoptionen
    
- Lizenzierungsanforderungen
    
- Erforderliche Architekturaufgaben
    
- Verantwortlichkeiten der IT-Experten für das Implementieren der einzelnen Bereitstellungsoptionen
    
### <a name="overview"></a>Übersicht

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Effizienzsteigerung und Kostenoptimierung mit Office 365-Plänen für mehrere Mandanten.
  
Das begleitende Diagramm zeigt Lync Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen AD DS-Umgebung (Active Directory-Domänendienste) und dem Azure Active Directory-Mandanten synchronisiert. 
  
Beschreibung von Features und Funktionen:
  
- Software as a Service (SaaS).
    
- Die umfangreiche Funktionspalette ist stets auf dem neuesten Stand.
    
- Umfasst einen Azure Active Directory-Mandanten für Onlinekonten, der mit anderen Anwendungen verwendet werden kann. 
    
- Die Verzeichnissynchronisierung schließt die Synchronisierung von Kontonamen und Kennwörtern zwischen der lokalen AD DS-Umgebung (Active Directory-Domänendienste) und dem Azure Active Directory-Mandanten ein.
    
- Falls einmaliges Anmelden (SSO) eine Anforderung ist, müssen Active Directory-Verbunddienste (AD FS) implementiert werden. 
    
- Clientkommunikation über das Internet ist verschlüsselt und authentifiziert.
    
- Herkömmliche Telefonausrüstung, Telefonfestnetzanbindung (Public Switched Telephone Network, PSTN) und Konnektivität ist über Drittanbieter verfügbar.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (geteilte Domäne)

Sie können die Vorteile von Office 365 mit einer lokalen Bereitstellung von Lync 2013 verbinden.
  
Das zugehörige Diagramm zeigt Office 365 mit Lync Online, wobei einige Benutzer lokal und einige Benutzer online arbeiten. Ein lokal bereitgestellter Edge-Server wird ebenfalls dargestellt.
  
Beschreibung von Features und Funktionen:
  
- Einige Benutzer arbeiten lokal und einige arbeiten online, sie nutzen jedoch die gleiche SIP-Domäne (z. B. contoso.com).
    
- Nutzen der Vorteile der vorhandenen Lync Server 2013-Infrastruktur, einschließlich der Verbindungen mit PSTN.
    
- Einfaches Hinzufügen von neuen Lync Online-Benutzern, die keinen PSTN-Zugriff benötigen.
    
- Langsame Migration vom lokalen Lync zu Lync Online, ganz nach Ihrem Zeitplan.
    
- Integration in andere Office 365-Anwendungen, einschließlich Exchange Online und SharePoint Online.
    
#### <a name="lync-server"></a>Lync Server

Bei dieser Bereitstellung sind Sie für alles zuständig. Das begleitende Diagramm zeigt eine Lync Server-Infrastruktur mit einer lokalen Active Directory-Domänendienste (AD DS)-Umgebung, in der Benutzer lokal arbeiten.
  
Beschreibung von Features und Funktionen:
  
- Planung und Festlegung des Umfangs der Kapazität.
    
- Serverbeschaffung und -einrichtung
    
- Bereitstellung
    
- Horizontale Skalierung, Patching und Betrieb
    
- Sichern von Daten
    
- Verwalten von Failover und Notfallwiederherstellung
    
- Verbinden der Lync Server 2013-Infrastruktur mit PSTN
    
- Integration mit vorhandener Telefonausrüstung, z. B. Private Branch Exchanges (PBXs)
    
#### <a name="provider-hosted-lync-server"></a>Vom Anbieter gehostetes Lync Server

Bei dieser Bereitstellung ist der Anbieter ist für alles zuständig. Das zugehörige Diagramm stellt das Netzwerk eines Anbieters dar, einschließlich der Server und Geräte mit einer Verbindung zur lokalen Umgebung.
  
Beschreibung von Features und Funktionen:
  
- Planung und Festlegung des Umfangs der Kapazität.
    
- Serverbeschaffung und -einrichtung
    
- Bereitstellung
    
- Horizontale Skalierung, Patching und Betrieb
    
- Sichern von Daten
    
- Verwalten von Failover und Notfallwiederherstellung
    
- Integration mit vorhandener Telefonausrüstung, z. B. Private Branch Exchanges (PBXs)
    
- Darüber hinaus kann der Anbieter:
    
  - Server und Geräte im Netzwerk mit einer Verbindung zur lokalen Bereitstellung (durchgehende Linie) installieren,
    
  - Server auf Ihrer lokalen Bereitstellung (die gepunktete Linie) installieren.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Vorteile des Implementierens der einzelnen Bereitstellungsoptionen

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Keine betrieblichen Gemeinkosten für lokale Server oder Serversoftware
    
- Kommunikationsfunktionen von Lync Server 2013 in einem cloudbasierten Dienst.
    
- Zugriff auf teilweise umfangreiche Funktionen im Zusammenhang mit Anwesenheit, Chats, Audio- und Videoanrufen, Onlinebesprechungen und Webkonferenzen
    
- Geografisch verteilte Organisationen oder Organisationen mit hauptsächlich mobilen Mitarbeitern
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (geteilte Domäne)

- Verwenden von Lync Online für Remotebenutzer und die Integration mit Geschäftspartnern
    
- Durchführen einer Migration von Lync (lokal) zu Lync Online
    
- Unterstützen von Remotestandorten ohne Verwendung eines Zweigstellengeräts
    
- Einfaches Hinzufügen von Lync-Unterstützung für neue Geschäftskäufe
    
#### <a name="lync-server"></a>Lync Server

- Private Cloudlösungen.
    
- Hoch angepasste Lösungen.
    
- Ältere Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die nicht von Lync Online unterstützt werden.
    
- Datenschutzeinschränkungen, die eine Synchronisierung von AD DS-Konten mit Office 365 verhindern
    
- Organisationen, die sich Kontrolle über die gesamte Plattform und Lösung wünschen.
    
- Ersetzung der PBX-Anlage mit Lync Enterprise Voice
    
#### <a name="provider-hosted-lync-server"></a>Vom Anbieter gehostetes Lync Server

- Organisationen, die Lync Server-Funktionen benötigen, die Bereitstellung und Wartung aber outsourcen möchten
    
- Anbieter-basierten Lösungen
    
- Hoch angepasste Lösungen.
    
- Ältere Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die nicht von Lync Online unterstützt werden.
    
- Ersetzung der PBX-Anlage mit Lync Enterprise Voice
    
### <a name="license-requirements"></a>Lizenzanforderungen

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Abonnementmodell
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (geteilte Domäne)

- Office 365 - Abonnementmodell Keine weiteren Lizenzen nötig. 
    
- Lokal – Alle lokalen Lizenzen sind gültig. 
    
#### <a name="lync-server"></a>Lync Server

- Serverbetriebssystem
    
- SQL Server
    
- Lync Server 2013-Lizenz
    
- Lync 2013-Clientzugriffslizenz
    
#### <a name="provider-hosted-lync-server"></a>Vom Anbieter gehostetes Lync Server

Die Kosten basieren auf dem Vertrag mit dem Anbieter Ihrer Lync-Lösung.
  
### <a name="architecture-tasks"></a>Architekturaufgaben

In diesem Abschnitt werden die Architekturaufgaben für die einzelnen Bereitstellungsoptionen aufgelistet.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Planen und Entwerfen der Verzeichnissynchronisierung
    
- Sicherstellen von Netzwerkkapazität und -verfügbarkeit durch Firewalls, Proxyserver, Gateways und über WAN-Verbindungen
    
- Beziehen von SSL-Zertifikaten anderer Anbieter zum Ermöglichen einer unternehmensweiten Sicherheit für Office 365-Dienstangebote.
    
- Bestimmen Sie, ob Sie mit Office 365 eine Verbindung über IPv6 (Internet Protocol version 6) herstellen möchten.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (geteilte Domäne)

Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen:
  
- Bestimmen, wie viel Feature-Integration Sie mit lokalen und Onlineversionen von Exchange Server und SharePoint nutzen möchten.
    
- Bei Bedarf bestimmen, welches Proxyservergerät für Anforderungen von Office 365 verwendet werden soll.
    
#### <a name="lync-server"></a>Lync Server

Entwurf der Lync-Umgebung in einer vorhandenen lokalen Umgebung:
  
- Lync-Topologie für Haupt- und Zweigstellen
    
- Server-Hardware, einschließlich Virtualisierung
    
- Integration in Active Directory-Domänendienste (AD DS) und DNS
    
- Lastenausgleich für Lync-Serverpools
    
- Failover und Notfallwiederherstellung
    
#### <a name="provider-hosted-lync-server"></a>Vom Anbieter gehostetes Lync Server

- Bestimmen Sie für eine cloudbasierte Installation die Verbindung zum Netzwerk des Dienstanbieters.
    
- Bestimmen Sie für eine lokale Installation die Platzierung der Lync-Server des Anbieters in Ihrem Netzwerk.
    
- Bestimmen Sie für beide Typen die Integration in AD DS und mit Ihrer PBX-Ausrüstung.
    
### <a name="it-pro-responsibilities"></a>Verantwortlichkeiten von IT-Experten

In diesem Abschnitt werden die Verantwortlichkeiten der IT-Experten für die einzelnen Bereitstellungsoptionen aufgelistet.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Bereitstellen und Verwalten von Lync Online (Office 365):
  
- Implementieren des Verzeichnissynchronisierungsplans.
    
- Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings.
    
- Konfigurieren des Proxys oder der Firewall für die IP-Adressen- und URL-Anforderungen von Office 365
    
- Verwalten der Benutzerkonten und der Lync Online-Einstellungen
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server Hybrid (geteilte Domäne)

Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen:
  
- Konfigurieren Sie, sofern erforderlich, das Proxyservergerät.
    
- Konfigurieren Sie die Integration von Features in lokalen und Onlineversionen von Exchange Server und SharePoint.
    
#### <a name="lync-server"></a>Lync Server

Bereitstellen und Verwalten von Lync Server in einer lokalen Umgebung:
  
- Bereitstellen der Server.
    
- Bereitstellen der Lync-Topologie.
    
- Aktualisieren der Lync-Server
    
- Bedarfsabhängiges Hinzufügen oder Entfernen von Topologieservern anhand auf der Auslastung
    
- Implementieren der Failover- und Notfallwiederherstellungsumgebung
    
#### <a name="provider-hosted-lync-server"></a>Vom Anbieter gehostetes Lync Server

Arbeiten Sie mit dem Anbieter an folgenden Aufgaben:
  
- Integration von Lync Server in Ihrem Netzwerk
    
- Integration von Lync Server mit anderen Microsoft-Produkten und benutzerdefinierten Lösungen
    
- Überwachung der Einhaltung der Anbietervereinbarung zum Servicelevel (SLA)
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Zwei Beispielszenarien für die Bereitstellung von Lync 2013

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Komponenten der Verzeichnissynchronisierung in Microsoft Azure

Die Bereitstellung der Office 365-Verzeichnissynchronisierungskomponenten in Azure erfolgt schneller, da virtuelle Computer bedarfsabhängig bereitgestellt werden können.
  
Das begleitende Diagramm zeigt Lync Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und dem Azure Active Directory-Mandanten synchronisiert.
  
 **Nur Verzeichnissynchronisierungsserver**. Anstatt in Ihrer lokalen Umgebung einen 64-Bit-Verzeichnissynchronisierungsserver bereitzustellen, richten Sie in Azure einen virtuellen Computer ein.
  
 **Verzeichnissynchronisierung und AD FS**. Dank dieser Option können Sie Office 365-Verbundidentitäten unterstützten, ohne Ihrer lokalen Infrastruktur weitere Hardware hinzufügen zu müssen. Bietet außerdem Ausfallsicherheit, wenn die lokale Active Directory-Umgebung nicht verfügbar ist. Die Funktionen dieser Option umfassen Folgendes:
  
- Verzeichnisintegrationskomponenten werden auf virtuellen Azure-Computern ausgeführt.
    
- AD FS wird im Internet über AD FS-Proxys auf virtuellen Azure-Computern veröffentlicht.
    
- Datenverkehr für die Clientauthentifizierung durch Benutzer, die von einem beliebigen Standort aus eine Verbindung herstellen, wird von AD FS-Servern- und Proxys verarbeitet, die auf virtuellen Azure-Computern bereitgestellt sind.
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Lync-Integration mit Exchange und SharePoint in Office 365

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server mit Exchange Online und SharePoint Online

Im zugehörigen Diagramm wird Office 365 mit Exchange Online und SharePoint Online mit einer Verbindung zu einer lokalen Lync Server 2013-Farm dargestellt.
  
Die Vorteile dieser Bereitstellung umfassen Folgendes:
  
- Nutzen des vollständigen Funktionssets von Lync Server 2013
    
- Nutzen der vorhandenen lokalen Telefonausrüstung, z. B. PBXs.
    
- Verwenden von Exchange Online für E-Mails, Entlastung der lokalen E-Mail-Server und des lokalen Speichers
    
- Verwenden von SharePoint Online für die Zusammenarbeit, geringerer Wartungsaufwand der lokalen SharePoint-Server
    
- Verwenden von in Lync, Exchange und SharePoint integrierten Features wie Unified Messaging (UM) in Office 365
    
#### <a name="exchange-server-with-lync-online"></a>Exchange Server mit Lync Online

Im zugehörigen Diagramm wird Office 365 mit Lync Online mit einer Verbindung zu einer lokalen Exchange Server-Farm dargestellt.
  
Die Vorteile dieser Bereitstellung umfassen Folgendes:
  
- Nutzen der vorhandenen Exchange-Infrastruktur
    
- Verwenden von Lync Online für Anwesenheitsinformationen, Chats und Konferenzfunktionen
    

