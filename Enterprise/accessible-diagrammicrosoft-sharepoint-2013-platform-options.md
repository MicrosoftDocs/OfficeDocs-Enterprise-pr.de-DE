---
title: Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- SPO_Content
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
f1.keywords:
- NOCSH
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Microsoft SharePoint 2013 Plattformoptionen.
ms.openlocfilehash: 100645b8de8487497eca4a2581523818e18834b3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843876"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen

**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Microsoft SharePoint 2013 Plattformoptionen.
  
Was Business decision makers (BDMs) und Architekten über Office 365, Microsoft Azure und lokale Bereitstellungen wissen müssen. 
  
Dieses Poster besteht aus zwei Abschnitten: 
  
- Ein Vergleich von vier verschiedenen Bereitstellungen für SharePoint 2013: SharePoint in Office 365, eine Kombination aus Office 365 mit einer lokalen Bereitstellung von SharePoint 2013, Azure und einer lokalen Bereitstellung von SharePoint 2013. 
    
- Eine Beschreibung von drei typischen Arbeitsauslastungen, die zu Azure migriert werden sollen. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Vergleich von vier verschiedenen Bereitstellungen für die SharePoint 2013 Plattform

Der Vergleich enthält Informationen zu den einzelnen Bereitstellungsoptionen im Zusammenhang mit den folgenden Bereichen: 
  
- Übersicht der verschiedenen Bereitstellungsfeatures 
    
- Vorteile der einzelnen Bereitstellungstypen 
    
- Lizenzanforderungen 
    
- Für die Implementierung erforderliche Architekturaufgaben 
    
- Verantwortlichkeiten für IT-Experten für die Implementierung 
    
### <a name="overview"></a>Übersicht

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Steigern Sie die Effizienz und optimieren Sie die Kosten mit Office 365 mehr Mandanten Plänen. 
  
Das zugehörige Diagramm zeigt SharePoint Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory Umgebung und dem Azure Active Directory-Mandanten synchronisiert. 
  
Beschreibung der Features: 
  
- Software as a Service (SaaS). 
    
- Die umfangreiche Funktionsgruppe ist immer auf dem neuesten Stand. 
    
- Enthält einen Azure Active Directory-Mandanten (kann mit anderen Anwendungen verwendet werden). 
    
- Die Verzeichnisintegration umfasst das Synchronisieren von Kontonamen und Kennwörtern zwischen der lokalen Active Directory Umgebung und dem Azure Active Directory-Mandanten. 
    
- Wenn einmaliges Anmelden (Single Sign-on, SSO) erforderlich ist, können Active Directory Verbunddienste (AD FS) implementiert werden. 
    
- Client Kommunikation über das Internet über einen verschlüsselten und authentifizierten Zugriff (Port 443). 
    
- Die Datenmigration ist auf das, was über das Internet hochgeladen werden kann, limitiert. 
    
- Anpassungen: Apps für Office, SharePoint und SharePoint Designer 2013. 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Kombinieren Sie die Vorteile von Office 365 mit einer lokalen Bereitstellung von SharePoint 2013. 
  
Das zugehörige Diagramm zeigt Office 365 mit SharePoint Online mit Business Connectivity Services (BCS) eine Verbindung mit einer lokalen SharePoint Server 2013 Farm herstellen. 
  
Wählen Sie aus, welche der folgenden Features integriert werden sollen: 
  
SharePoint-Suche 
  
- Benutzer können Suchergebnisse aus beiden Umgebungen anzeigen. 
    
- Extranet-Benutzer können sich Remote mit einem lokalen Active Directory-Konto anmelden und alle verfügbaren hybridfunktionen verwenden. 
    
BCS
  
Von SharePoint Online: Benutzer können Lese-und Schreibvorgänge ausführen. Der BCS-Dienst stellt eine Verbindung mit einer lokalen SharePoint Server 2013 Farm her. Der in der lokalen Farm konfigurierte BCS-Dienst vermittelt die Verbindung mit lokalen OData-Dienstendpunkten. 
  
Duet Enterprise Online 
  
In SharePoint Online können Benutzer Lese-und Schreibvorgänge für ein lokales SAP-System ausführen. 
  
#### <a name="azure"></a>Azure

Nutzen Sie die Cloud, und behalten Sie die vollständige Kontrolle über die Plattform und die Funktionen zur Verfügung. 
  
Das begleitende Diagramm zeigt Azure, die zwei Cloud-Dienste, eine SharePoint 2013 Farm und Windows Server-Active Directory mit DNS-Verbindung mit Benutzern über das Internet oder eine Verbindung zu lokalen Active Directory über VPN-Tunnel enthält. 
  
Zu den Features gehören: 
  
-  Azure ist eine Plattform, die die Infrastruktur und die APP-Dienste bereitstellt, die zum Hosten einer SharePoint 2013 Farm erforderlich sind.
    
- Infrastrukturdienste. 
    
- Beste Native Cloud-Plattform für SQL Server und SharePoint. 
    
- Computing-Ressourcen stehen fast sofort ohne Verpflichtung zur Verfügung. 
    
- Konzentrieren Sie sich auf Anwendungen anstelle von Rechenzentren und Infrastruktur. 
    
- Günstige Entwicklungs-und Testumgebungen. 
    
- Auf SharePoint-Lösungen kann über das Internet zugegriffen werden oder nur über eine Unternehmensumgebung über einen Standort-zu-Standort-VPN-Tunnel zugänglich sein. 
    
- Anpassungen sind nicht limitiert. 
    
#### <a name="on-premises"></a>Lokal

Sie besitzen alles. 
  
Das begleitende Diagramm zeigt eine lokale Umgebung mit Webservern, Anwendungsservern und Active Directory, die mit allen Datenbanken und dedizierten Anwendungsservern für die Suche kommunizieren. 
  
Zu den Features gehören: 
  
- Planung und Festlegung des Umfangs der Kapazität. 
    
- Serverbeschaffung und -einrichtung 
    
- Bereitstellung 
    
- Horizontale Skalierung, Patching und Betrieb 
    
- Sichern von Daten 
    
- Verwalten einer Notfallwiederherstellungsumgebung 
    
- Anpassungen sind nicht limitiert. 
    
### <a name="deployment-type-is-best-for---"></a>Der Bereitstellungs eignet sich am besten für. . .

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Sichere externe Freigabe und Zusammenarbeit. (Einzigartiges Feature!) 
    
- Intranet – Team Websites, meine Websites und interne Zusammenarbeit. 
    
- Dokumentieren Sie Speicherung und Versionsverwaltung in der Cloud. 
    
- Grundlegende Website mit öffentlichem Standard. 
    
Zusätzliche Features mit Office 365 dedizierten Abonnement Plänen: 
  
- Microsoft-Rechenzentrumsgeräte, die für Ihre Organisation reserviert sind und nicht für eine andere Organisation freigegeben sind. 
    
- Jede Kundenumgebung befindet sich in einem physisch getrennten Netzwerk. 
    
- Client Kommunikation über ein IPSec-gesichertes VPN oder eine private privat Verbindung im Kundenbesitz. Die zweistufige Authentifizierung ist optional. 
    
- ITAR-Support Pläne. 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

- Verwenden Sie Office 365 für die externe Freigabe und Zusammenarbeit, anstatt eine Extranet-Umgebung einzurichten. 
    
- Stellen Sie meine Websites (OneDrive für Unternehmen) in die Cloud ein, um Benutzern den Remotezugriff auf Ihre Dateien zu erleichtern. 
    
- Starten Sie neue Teamwebsites in Office 365. 
    
- Integrieren einer Office 365 Website in eine lokale BCS SharePoint-Umgebung. 
    
#### <a name="azure"></a>Azure

- SharePoint für Internet Websites – öffentliche gegenüberliegende Websites. Nutzen Sie Azure AD für Kundenkonten und-Authentifizierung. 
    
- Entwickler-, Test-und Staging-Umgebungen – schnelles Bereitstellen und Aufheben der Bereitstellung ganzer Umgebungen. 
    
- Hybrid Anwendungen – Anwendungen, die sich auf Ihr Rechenzentrum und die Cloud erstrecken. 
    
- Notfallwiederherstellungsumgebung – schnelle Wiederherstellung nach einem Notfall. Zahlen Sie nur für die Verwendung. 
    
- Farmen, die eine umfassende Berichterstellung oder Überwachung erfordern. 
    
- Webanalyse. 
    
- Datenverschlüsselung im Ruhezustand (Daten werden in den SQL-Datenbanken verschlüsselt). 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Datenverschlüsselung im Ruhezustand (Daten werden in den SQL-Datenbanken verschlüsselt)

- In-Country-Farmen (wenn sich Daten innerhalb eines Gerichtsstands befinden müssen). 
    
- Komplexe BI-Lösungen, die sich in der Nähe von BI-Daten befinden müssen. 
    
- Private Cloudlösungen. 
    
- Hoch angepasste Lösungen. 
    
- Ältere Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die in Azure-Infrastrukturdiensten nicht unterstützt werden. 
    
- Datenschutz Einschränkungen, die die Synchronisierung von Active Directory Konten mit Azure Active Directory verhindern (Voraussetzung für Office 365). 
    
- Organisationen, die die Steuerung der gesamten Plattform und Lösung bevorzugen. 
    
### <a name="license-requirements"></a>Lizenzanforderungen

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Abonnementmodell Keine zusätzlichen Lizenzen erforderlich. 
  
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

- Office 365 - Abonnementmodell Keine weiteren Lizenzen nötig. 
    
- Lokal – Alle lokalen Lizenzen sind gültig. 
    
#### <a name="azure"></a>Azure

-  Azure-Abonnement (enthält das Server Betriebssystem)
    
- SQL Server 
    
- SharePoint 2013 Server Lizenz 
    
- SharePoint 2013 Client Zugriffslizenz 
    
#### <a name="on-premises"></a>Lokal

- Server-Betriebssystem 
    
- SQL Server 
    
- SharePoint 2013 Server Lizenz 
    
- SharePoint 2013 Client Zugriffslizenz 
    
### <a name="architecture-tasks"></a>Architekturaufgaben

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Planen und Entwerfen der Verzeichnisintegration. Zwei Optionen. Beide Optionen können lokal oder in Azure bereitgestellt werden: Kennwortsynchronisierung (erfordert 1 64-Bit-Server). SSO (erfordert AD FS und mehrere Server). 
    
- Sicherstellen von Netzwerkkapazität und -verfügbarkeit durch Firewalls, Proxyserver, Gateways und über WAN-Verbindungen 
    
- Beziehen von SSL-Zertifikaten anderer Anbieter zum Ermöglichen einer unternehmensweiten Sicherheit für Office 365-Dienstangebote. 
    
- Planen Sie den Mandantennamen, und entwerfen Sie die Architektur der Websitesammlung und die Steuerung. 
    
- Planen von Anpassungen, Lösungen und Apps für SharePoint Online. 
    
- Entscheiden Sie, ob Sie über das Internet Protocol 6 (IPv6) eine Verbindung mit Office 365 herstellen möchten. Dies ist jedoch nicht die Regel. 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen: 
  
- Bestimmen Sie, wie viel Funktionsintegration Sie wünschen, und wählen Sie die Hybrid Topologie aus. Siehe dieses Modell Poster: welche Hybrid Topologie sollte ich verwenden? 
    
- Ermitteln Sie bei Bedarf, welches Proxy Server Gerät verwendet wird. 
    
#### <a name="azure"></a>Azure

Entwerfen der Azure-Netzwerkumgebung: 
  
- Virtuelles Netzwerk in Azure, einschließlich Subnetze. 
    
- Domänenumgebung und Integration in lokale Server. 
    
- IP-Adressen und DNS. 
    
- Affinitätsgruppen und Speicherkonten. 
    
Entwerfen der SharePoint-Umgebung in Azure: 
  
- SharePoint-Farmtopologie und logische Architektur. 
    
-  Azure-Verfügbarkeits Sätze und Aktualisieren von Domänen.
    
- Größen für virtuelle Computer. 
    
- Lastenausgleich-Endpunkt. 
    
- Externe Endpunkte für den öffentlichen Zugriff, falls dies vorzuziehen ist. 
    
- Notfallwiederherstellungsumgebung. 
    
#### <a name="on-premises"></a>Lokal

Entwerfen der SharePoint-Umgebung in einer vorhandenen lokalen Umgebung: 
  
- SharePoint-Farmtopologie und logische Architektur. 
    
- Server Hardware. 
    
- Virtuelle Umgebung (sofern verwendet). 
    
- Lastenausgleich. 
    
- Integration in AD DS und DNS. 
    
- Notfallwiederherstellungsumgebung. 
    
### <a name="it-pro-responsibilities"></a>Verantwortlichkeiten für IT-Experten

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Stellen Sie sicher, dass Benutzerarbeitsstationen Office 365 Client Voraussetzungen erfüllen. 
    
- Implementieren Sie den Verzeichnis Integrationsplan. 
    
- Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings. 
    
- Konfigurieren Sie den Proxy oder die Firewall für Office 365 IP-Adressen-und URL-Anforderungen. 
    
- Erstellen Sie Berechtigungen für Websitesammlungen, und weisen Sie diese zu. 
    
- Implementieren von Anpassungen, Lösungen und Apps für SharePoint Online. 
    
- Überwachen der Netzwerkverfügbarkeit und Identifizieren möglicher Engpässe 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen: 
  
- Konfigurieren Sie, sofern erforderlich, das Proxyservergerät. 
    
- Konfigurieren der Hybriden Identitäts Verwaltungsinfrastruktur: SSO und Server-zu-Server-Authentifizierung zwischen den beiden Umgebungen. 
    
- Konfigurieren Sie die Integration ausgewählter Features: Search, BCS, Duet Enterprise online. 
    
#### <a name="azure"></a>Azure

Bereitstellen und Verwalten der Azure-und SharePoint-Umgebung: 
  
- Implementieren und Verwalten der Azure-Netzwerkumgebung. 
    
- Stellen Sie die SharePoint-Umgebung bereit. 
    
- Aktualisieren von SharePoint-Farmservern 
    
- Hinzufügen oder Herunterfahren virtueller Computer bei Bedarf basierend auf der Farm Nutzung. 
    
- Erweitern oder verringern der Größe virtueller Computer bei Bedarf. 
    
- Sichern Sie die SharePoint-Umgebung. 
    
- Implementieren der Notfallwiederherstellungsumgebung und des Protokolls. 
    
#### <a name="on-premises"></a>Lokal

Bereitstellen und Verwalten der SharePoint-Umgebung in lokalen Umgebungen: 
  
- Bereitstellungsserver. 
    
- Stellen Sie die SharePoint-Umgebung bereit. 
    
- Aktualisieren von SharePoint-Farmservern 
    
- Hinzufügen oder Entfernen von Farmservern bei Bedarf basierend auf der Farm Nutzung. 
    
- Sichern Sie die SharePoint-Umgebung. 
    
- Implementieren der Notfallwiederherstellungsumgebung und des Protokolls. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Drei typische Arbeitsauslastungen für die Umstellung auf Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 plus Verzeichniskomponenten in Azure

Die Bereitstellung Office 365 Verzeichnis Integrationskomponenten in Azure ist schneller, da virtuelle Computer bei Bedarf bereitgestellt werden können. 
  
#### <a name="directory-synchronization-server-only"></a>Nur Verzeichnissynchronisierungsserver

Anstatt den 64-Bit-Verzeichnissynchronisierungsserver in Ihrer lokalen Umgebung bereitzustellen, müssen Sie stattdessen einen virtuellen Computer in Azure bereitstellen. 
  
Das zugehörige Diagramm zeigt SharePoint Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory Umgebung und dem Azure Active Directory-Mandanten synchronisiert. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Verzeichnissynchronisierung Plus AD FS

Dank dieser Option können Sie Office 365-Verbundidentitäten unterstützten, ohne Ihrer lokalen Infrastruktur weitere Hardware hinzufügen zu müssen. Bietet außerdem Ausfallsicherheit, wenn die lokale Active Directory-Umgebung nicht verfügbar ist. 
  
- Verzeichnis Integrationskomponenten befinden sich in Azure. 
    
- AD FS wird im Internet über AD FS-Proxys in Azure veröffentlicht. 
    
- Der Client Authentifizierungsdatenverkehr wird für Benutzer, die von einem beliebigen Standort aus eine Verbindung herstellen, von AD FS-Servern und Proxys verarbeitet, die in Azure bereitgestellt werden. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Öffentliche Internet Website und Azure AD für die Kundenauthentifizierung

Nutzen Sie die Möglichkeit, die Anforderungen einfach zu skalieren, indem Sie Ihre Internet Website in Azure platzieren. Verwenden Sie Azure AD zum Speichern von Kundenkonten. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Azure-Vorteile für Internet Websites

- Zahlen Sie nur für die Ressourcen, die Sie benötigen, indem Sie die Anzahl der virtuellen Computer basierend auf der Farm Nutzung skalieren. 
    
- Fügen Sie Deep Reporting und Webanalyse hinzu. 
    
- Konzentrieren Sie sich auf die Entwicklung einer großartigen Website statt auf die Erstellung von Infrastruktur. 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD bietet Identitätsverwaltungs- und Zugriffssteuerungsfunktionen für Clouddienste. Zu den Funktionen zählen ein cloudbasierter Speicher für Verzeichnisdaten und eine Kerngruppe von Identitätsdiensten, einschließlich Anmeldungsprozessen, Authentifizierungsdiensten und AD FS. Die in Azure Ad enthaltenen Identitätsdienste können problemlos in Ihre lokalen Active Directory-Bereitstellungen integriert werden und Drittanbieter-Identitätsanbieter vollständig unterstützen. 
  
Das begleitende Diagramm zeigt die Konfiguration von Zonen und Authentifizierung, die für mit dem Internet verbundene Standorte wichtig ist. Das Diagramm zeigt den Azure Active Directory-Mandanten, der eine SharePoint-Farm in Azure mit zwei Zonen enthält: 
  
- Eine Internet Zone, die mit anonymen und authentifizierten Besuchern und Kunden außerhalb des Netzwerks interagiert 
    
- Eine Standardzone, die NTLM für die Durchforstung und Windows-Authentifizierung enthält, die mit Ihrer lokalen Active Directory-Bereitstellung über einen VPN-Tunnel interagiert. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Lokale Farm und Notfallwiederherstellung in Azure

Wählen Sie eine Notfall Wiederherstellungsoption, die Ihren geschäftlichen Anforderungen entspricht. Azure bietet Einstiegs Optionen für Unternehmen, die erste Schritte mit der Notfallwiederherstellung und erweiterte Optionen für Unternehmen mit hohen Ausfall Sicherheitsanforderungen. 
  
#### <a name="cold-standby"></a>Kalt-Standby

- Die Farm ist vollständig erstellt, aber die virtuellen Computer sind nicht in Betrieb. (Sie zahlen nur, wenn Sie in Betrieb sind!) 
    
- Das aufrecht erhalten der Umgebung umfasst das Starten der virtuellen Computer von Zeit zu Zeit, das Patchen, aktualisieren und Überprüfen der Umgebung. 
    
- Starten Sie die vollständige Umgebung bei einem Notfall. 
    
#### <a name="warm-standby"></a>Warm-Standby

- Dies umfasst eine kleine Farm, die bereitgestellt wird und aktiv ist. 
    
- Die Farm kann Benutzern unmittelbar im Fall eines Failovers zur Verfügung stehen. 
    
- Schnelles Skalieren der Farm, um die gesamte Benutzerbasis zu bedienen 
    
#### <a name="hot-standby"></a>Hot Standby

Eine vollständige Farm wird bereitgestellt und wird im Standbymodus gestartet. 
  
Das begleitende Diagramm zeigt eine lokale Farm, die mit der SharePoint-Notfallwiederherstellungsumgebung in Azure interagiert. Die lokalen Datenbanken verwenden SQL Server Protokollversand über den VPN-Tunnel für den Zugriff auf die SharePoint-Notfallwiederherstellungsumgebung, die zwei SQL-Datenbankserver enthält, die die SharePoint-Datenbanken, zwei Front-End-Server und zwei SharePoint enthalten Anwendungsserver 
  

