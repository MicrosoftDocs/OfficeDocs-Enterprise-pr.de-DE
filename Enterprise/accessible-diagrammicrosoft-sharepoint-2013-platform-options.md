---
title: Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms namens Microsoft SharePoint 2013-Plattformoptionen.
ms.openlocfilehash: 4a0b068ffb8abbe11c2286f3daa70c5f62295425
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068601"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen

**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms namens Microsoft SharePoint 2013-Plattformoptionen.
  
Was Entscheidungsträger (BDMs) und Architekten von Unternehmen über Office 365, Microsoft Azure und lokale Bereitstellungen wissen müssen. 
  
Dieses Poster hat zwei Abschnitte: 
  
- Einen Vergleich von vier verschiedenen Bereitstellungen für SharePoint 2013: SharePoint in Office 365, eine Hybride von Office 365 mit einer lokalen Bereitstellung von SharePoint 2013, Azure und einer lokalen Bereitstellung von SharePoint 2013. 
    
- Eine Beschreibung der drei typischen Arbeitsauslastungen, die in Azure verschoben werden sollen. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Vergleich von vier verschiedenen Bereitstellungen für die SharePoint 2013-Plattform

Der Vergleich enthält Informationen zu den einzelnen Bereitstellungsoptionen in den folgenden Bereichen: 
  
- Übersicht der verschiedenen Bereitstellungsfeatures 
    
- Welche Art der Bereitstellung am besten geeignet ist 
    
- Lizenzanforderungen 
    
- Für die Implementierung erforderliche Architekturaufgaben 
    
- IT-Verantwortlichkeiten für die Implementierung 
    
### <a name="overview"></a>Übersicht

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Effizienzsteigerung und Kostenoptimierung mit Office 365-Multitenant-Plänen. 
  
Das begleitende Diagramm zeigt SharePoint Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und dem Azure Active Directory-Mandanten synchronisiert. 
  
Beschreibung der Features: 
  
- Software as a Service (SaaS). 
    
- Der umfangreiche Featuresatz ist stets auf dem neuesten Stand. 
    
- Enthält einen Azure Active Directory-Mandanten (kann mit anderen Anwendungen verwendet werden). 
    
- Die Verzeichnisintegration umfasst das Synchronisieren von Kontonamen und Kennwörtern zwischen der lokalen Active Directory-Umgebung und dem Azure Active Directory-Mandanten. 
    
- Wenn einmaliges Anmelden (Single Sign-on, SSO) erforderlich ist, können Active Directory-Verbunddienste (AD FS) implementiert werden. 
    
- Client Kommunikation über das Internet über den verschlüsselten und authentifizierten Zugriff (Portierung 443). 
    
- Die Datenmigration ist darauf beschränkt, was über das Internet hochgeladen werden kann. 
    
- Anpassungen: Apps für Office, SharePoint und SharePoint Designer 2013. 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Kombinieren Sie die Vorteile von Office 365 mit einer lokalen Bereitstellung von SharePoint 2013. 
  
Das begleitende Diagramm zeigt Office 365 mit SharePoint Online mithilfe von Business Connectivity Services (BCS) zum Herstellen einer Verbindung mit einer lokalen SharePoint Server 2013-Farm. 
  
Wählen Sie aus, welche der folgenden Features integriert werden soll: 
  
SharePoint-Suche 
  
- Benutzer können Suchergebnisse aus beiden Umgebungen anzeigen. 
    
- Extranet-Benutzer können sich Remote mit einem lokalen Active Directory-Konto anmelden und alle verfügbaren hybridfunktionen verwenden. 
    
BCS
  
Von SharePoint Online: Benutzer können Lese-und Schreibvorgänge ausführen. Der BCS-Dienst stellt eine Verbindung zu einer lokalen SharePoint Server 2013-Farm her. Der in der lokalen Farm konfigurierte BCS-Dienst vermittelt die Verbindung mit lokalen OData-Dienstendpunkten. 
  
Duet Enterprise Online 
  
In SharePoint Online können Benutzer Lese-und Schreibvorgänge für ein lokales SAP-System ausführen. 
  
#### <a name="azure"></a>Azure

Nutzen Sie die Cloud, während Sie die vollständige Kontrolle über die Plattform und die Funktionen erhalten. 
  
Das begleitende Diagramm zeigt Azure mit zwei Cloud-Diensten, einer SharePoint 2013-Farm und Windows Server Active Directory mit DNS, die eine Verbindung mit Benutzern über das Internet herstellen oder eine Verbindung mit dem lokalen Active Directory über den VPN-Tunnel herstellen. 
  
Zu den Features gehören: 
  
-  Azure ist eine Plattform, die die Infrastruktur und die APP-Dienste bereitstellt, die zum Hosten einer SharePoint 2013-Farm benötigt werden.
    
- Infrastrukturdienste. 
    
- Beste Native Cloud-Plattform für SQL Server und SharePoint. 
    
- Computing-Ressourcen stehen fast sofort ohne Verpflichtung zur Verfügung. 
    
- Konzentrieren Sie sich auf Anwendungen anstelle von Rechenzentren und Infrastruktur. 
    
- Kostengünstige Entwicklungs-und Testumgebungen. 
    
- Auf SharePoint-Lösungen kann über das Internet zugegriffen werden, oder nur von einer Unternehmensumgebung aus über einen Standort-zu-Standort-VPN-Tunnel. 
    
- Anpassungen sind nicht beschränkt. 
    
#### <a name="on-premises"></a>Lokal

Sie besitzen alles. 
  
Das begleitende Diagramm zeigt eine lokale Umgebung mit Webservern, Anwendungsservern und Active Directory, die mit allen Datenbanken und dedizierten Anwendungsservern für die Suche kommuniziert. 
  
Zu den Features gehören: 
  
- Planung und Festlegung des Umfangs der Kapazität. 
    
- Serverbeschaffung und -einrichtung 
    
- Bereitstellung 
    
- Horizontale Skalierung, Patching und Betrieb 
    
- Sichern von Daten 
    
- Verwalten einer Notfallwiederherstellungsumgebung. 
    
- Anpassungen sind nicht beschränkt. 
    
### <a name="deployment-type-is-best-for---"></a>Der Bereitstellungs ist am besten für. . .

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Sichere externe Freigabe und Zusammenarbeit. (Einmaliges Feature!) 
    
- Intranet – Team Websites, meine Websites und interne Zusammenarbeit. 
    
- Dokumentspeicherung und Versionsverwaltung in der Cloud. 
    
- Grundlegende öffentlich zugängliche Website. 
    
Zusätzliche Features mit dedizierten Office 365-Abonnement Plänen: 
  
- Microsoft Datacenter-Geräte, die für Ihre Organisation dediziert und nicht für andere Organisationen freigegeben sind. 
    
- Jede Kundenumgebung befindet sich in einem physisch getrennten Netzwerk. 
    
- Client Kommunikation über eine IPsec-gesicherte VPN-oder kundeneigene private Verbindung. Die zweistufige Authentifizierung ist optional. 
    
- ITAR-Support Pläne. 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

- Verwenden Sie Office 365 für die externe Freigabe und Zusammenarbeit, statt eine Extranet-Umgebung einzurichten. 
    
- Verschieben Sie meine Websites (OneDrive for Business) in die Cloud, um Benutzern den Zugriff auf Ihre Dateien zu erleichtern. 
    
- Starten Sie neue Teamwebsites in Office 365. 
    
- Integrieren einer Office 365-Website in eine lokale BCS SharePoint-Umgebung. 
    
#### <a name="azure"></a>Azure

- SharePoint für Internet Websites – öffentlich zugängliche Websites. Nutzen Sie Azure AD für Kundenkonten und-Authentifizierung. 
    
- Entwickler-, Test-und Staging-Umgebungen – schnelles Bereitstellen und Aufheben der Bereitstellung von gesamten Umgebungen. 
    
- Hybrid Anwendungen – Anwendungen, die sich über das Rechenzentrum und die Cloud erstrecken. 
    
- Notfallwiederherstellungsumgebung – schnelle Wiederherstellung nach einem Notfall. Nur für die Verwendung bezahlen. 
    
- Farmen, die eine umfassende Berichterstellung oder Überwachung erfordern. 
    
- Web Analytics. 
    
- Datenverschlüsselung im Ruhezustand (Daten werden in den SQL-Datenbanken verschlüsselt). 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Datenverschlüsselung im Ruhezustand (Daten werden in den SQL-Datenbanken verschlüsselt)

- In-Country Farms (wenn sich Daten in einem jurisdiktions Gebiet befinden müssen). 
    
- Komplexe BI-Lösungen, die sich in der nahen Umgebung von BI-Daten befinden müssen. 
    
- Private Cloudlösungen. 
    
- Hoch angepasste Lösungen. 
    
- Legacy Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die in Azure-Infrastrukturdiensten nicht unterstützt werden. 
    
- Datenschutz Einschränkungen, die die Synchronisierung von Active Directory-Konten mit Azure Active Directory (eine Anforderung für Office 365) verhindern. 
    
- Organisationen, die die Kontrolle über die gesamte Plattform und Lösung bevorzugen. 
    
### <a name="license-requirements"></a>Lizenzanforderungen

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Abonnementmodell Keine zusätzlichen Lizenzen erforderlich. 
  
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

- Office 365 - Abonnementmodell Keine weiteren Lizenzen nötig. 
    
- Lokal – Alle lokalen Lizenzen sind gültig. 
    
#### <a name="azure"></a>Azure

-  Azure-Abonnement (beinhaltet das Server Betriebssystem)
    
- SQL Server 
    
- SharePoint 2013-Server Lizenz 
    
- SharePoint 2013-Client Zugriffslizenz 
    
#### <a name="on-premises"></a>Lokal

- Server Betriebssystem 
    
- SQL Server 
    
- SharePoint 2013-Server Lizenz 
    
- SharePoint 2013-Client Zugriffslizenz 
    
### <a name="architecture-tasks"></a>Architekturaufgaben

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Planen und Entwerfen der Verzeichnisintegration. Zwei Optionen. Eine der Optionen kann entweder lokal oder in Azure bereitgestellt werden: Kennwortsynchronisierung (erfordert 1 64-Bit-Server). SSO (erfordert AD FS und mehrere Server). 
    
- Sicherstellen von Netzwerkkapazität und -verfügbarkeit durch Firewalls, Proxyserver, Gateways und über WAN-Verbindungen 
    
- Beziehen von SSL-Zertifikaten anderer Anbieter zum Ermöglichen einer unternehmensweiten Sicherheit für Office 365-Dienstangebote. 
    
- Planen Sie den Mandantennamen, und entwerfen Sie die Architektur und Steuerung der Websitesammlung. 
    
- Planen von Anpassungen, Lösungen und Apps für SharePoint Online. 
    
- Entscheiden Sie, ob Sie mit dem Internet Protokoll 6 (IPv6) eine Verbindung mit Office 365 herstellen möchten. Dies ist jedoch nicht die Regel. 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen: 
  
- Legen Sie fest, wie viele Features integriert werden sollen, und wählen Sie die Hybrid Topologie aus. Siehe dieses Modell Poster: welche Hybrid Topologie sollte ich verwenden? 
    
- Bestimmen Sie bei Bedarf, welches Proxy Server Gerät verwendet werden soll. 
    
#### <a name="azure"></a>Azure

Entwerfen der Azure-Netzwerkumgebung: 
  
- Virtuelles Netzwerk in Azure, einschließlich Subnetzen. 
    
- Domänenumgebung und Integration in lokale Server. 
    
- IP-Adressen und DNS. 
    
- Affinitätsgruppen und Speicherkonten. 
    
Entwerfen der SharePoint-Umgebung in Azure: 
  
- SharePoint-Farmtopologie und logische Architektur. 
    
-  Azure-Verfügbarkeits Sätze und Update Domänen.
    
- Größen der virtuellen Computer. 
    
- Lastenausgleich-Endpunkt. 
    
- Externe Endpunkte für den öffentlichen Zugriff, wenn dies vorzuziehen ist. 
    
- Notfallwiederherstellungsumgebung. 
    
#### <a name="on-premises"></a>Lokal

Entwerfen der SharePoint-Umgebung in einer vorhandenen lokalen Umgebung: 
  
- SharePoint-Farmtopologie und logische Architektur. 
    
- Server Hardware. 
    
- Virtuelle Umgebung, falls verwendet. 
    
- Lastenausgleich. 
    
- Integration in AD DS und DNS. 
    
- Notfallwiederherstellungsumgebung. 
    
### <a name="it-pro-responsibilities"></a>Verantwortlichkeiten für IT-Experten

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Stellen Sie sicher, dass Benutzerarbeitsstationen die Office 365-Client Voraussetzungen erfüllen. 
    
- Implementieren Sie den Verzeichnis Integrationsplan. 
    
- Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings. 
    
- Konfigurieren des Proxys oder der Firewall für die IP-Adressen-und URL-Anforderungen von Office 365. 
    
- Erstellen und Zuweisen von Berechtigungen für Websitesammlungen. 
    
- Implementieren von Anpassungen, Lösungen und Apps für SharePoint Online. 
    
- Überwachen der Netzwerkverfügbarkeit und Identifizieren möglicher Engpässe 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen: 
  
- Konfigurieren Sie, sofern erforderlich, das Proxyservergerät. 
    
- Konfigurieren Sie die hybride Identitäts Verwaltungsinfrastruktur: SSO und Server-zu-Server-Authentifizierung zwischen den beiden Umgebungen. 
    
- Konfigurieren Sie die Integration ausgewählter Features: Search, BCS, Duet Enterprise online. 
    
#### <a name="azure"></a>Azure

Bereitstellen und Verwalten der Azure-und SharePoint-Umgebung: 
  
- Implementieren und Verwalten der Azure-Netzwerkumgebung. 
    
- Bereitstellen der SharePoint-Umgebung 
    
- Aktualisieren Sie SharePoint-Farmserver. 
    
- Hinzufügen oder Herunterfahren virtueller Computer nach Bedarf basierend auf der Farm Auslastung. 
    
- Verringern Sie die Größe der virtuellen Computer bei Bedarf. 
    
- Sichern Sie die SharePoint-Umgebung. 
    
- Implementieren der Notfallwiederherstellungsumgebung und des Protokolls. 
    
#### <a name="on-premises"></a>Lokal

Bereitstellen und Verwalten der SharePoint-Umgebung für lokale Umgebungen: 
  
- Bereitstellungsserver. 
    
- Bereitstellen der SharePoint-Umgebung 
    
- Aktualisieren Sie SharePoint-Farmserver. 
    
- Hinzufügen oder Entfernen von Farmservern nach Bedarf basierend auf der Farm Auslastung. 
    
- Sichern Sie die SharePoint-Umgebung. 
    
- Implementieren der Notfallwiederherstellungsumgebung und des Protokolls. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Drei typische Arbeitsauslastungen für die Migration zu Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 plus-Verzeichniskomponenten in Azure

Das Bereitstellen von Office 365-Verzeichnis Integrationskomponenten in Azure ist schneller, da virtuelle Computerbedarfs abhängig bereitgestellt werden können. 
  
#### <a name="directory-synchronization-server-only"></a>Nur Verzeichnissynchronisierungsserver

Anstatt den 64-Bit-Verzeichnissynchronisierungsserver in Ihrer lokalen Umgebung bereitzustellen, stellen Sie stattdessen einen virtuellen Computer in Azure bereit. 
  
Das begleitende Diagramm zeigt SharePoint Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und dem Azure Active Directory-Mandanten synchronisiert. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Verzeichnissynchronisierung Plus AD FS

Dank dieser Option können Sie Office 365-Verbundidentitäten unterstützten, ohne Ihrer lokalen Infrastruktur weitere Hardware hinzufügen zu müssen. Bietet außerdem Ausfallsicherheit, wenn die lokale Active Directory-Umgebung nicht verfügbar ist. 
  
- Verzeichnis Integrationskomponenten befinden sich in Azure. 
    
- AD FS wird im Internet über AD FS-Proxys in Azure veröffentlicht. 
    
- Der Datenverkehr der Client Authentifizierung für Benutzer, die von einem beliebigen Standort aus eine Verbindung herstellen, wird von AD FS-Servern und Proxys verarbeitet, die in Azure bereitgestellt werden. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Öffentlich zugängliche Internet Website und Azure AD für die Kundenauthentifizierung

Nutzen Sie die Möglichkeit, die Anforderungen problemlos zu skalieren, indem Sie Ihre Internet Website in Azure platzieren. Verwenden Sie Azure AD zum Speichern von Kundenkonten. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Azure-Vorteile für Internet Websites

- Zahlen Sie nur für die benötigten Ressourcen, indem Sie die Anzahl der virtuellen Computer basierend auf der Farm Auslastung skalieren. 
    
- Hinzufügen von Deep Reporting und Web Analytics. 
    
- Konzentrieren Sie sich auf die Entwicklung einer großartigen Website und nicht auf das Erstellen einer Infrastruktur. 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD bietet Identitätsverwaltungs- und Zugriffssteuerungsfunktionen für Clouddienste. Zu den Funktionen zählen ein cloudbasierter Speicher für Verzeichnisdaten und eine Kerngruppe von Identitätsdiensten, einschließlich Anmeldungsprozessen, Authentifizierungsdiensten und AD FS. Die in Azure Ad enthaltenen Identitätsdienste können problemlos in Ihre lokalen Active Directory-Bereitstellungen integriert und von Drittanbieter-Identitätsanbietern vollständig unterstützt werden. 
  
Das begleitende Diagramm zeigt die Konfiguration von Zonen und Authentifizierung, die für Websites mit Internet Zugriff wichtig ist. Das Diagramm zeigt den Azure Active Directory-Mandanten, der eine SharePoint-Farm in Azure mit zwei Zonen enthält: 
  
- Eine Internet Zone, die mit anonymen und authentifizierten Besuchern und Kunden außerhalb des Netzwerks interagiert 
    
- Eine Standardzone mit NTLM für die Durchforstung und Windows-Authentifizierung, die mit Ihrer lokalen Active Directory-Bereitstellung über einen VPN-Tunnel interagiert. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Lokale Farm und Notfallwiederherstellung in Azure

Wählen Sie eine Notfall Wiederherstellungsoption aus, die Ihren geschäftlichen Anforderungen entspricht. Azure bietet Einstiegs Optionen für Unternehmen, die mit der Notfallwiederherstellung und erweiterten Optionen für Unternehmen mit hohen Anforderungen an die Ausfallsicherheit begonnen haben. 
  
#### <a name="cold-standby"></a>Cold Standby

- Die Farm ist vollständig erstellt, aber die virtuellen Computer sind nicht in Betrieb. (Sie zahlen nur, wenn Sie gerade laufen!) 
    
- Zur Verwaltung der Umgebung zählen das Starten der virtuellen Computer von Zeit zu Zeit, das Patchen, aktualisieren und Überprüfen der Umgebung. 
    
- Starten Sie die vollständige Umgebung bei einem Notfall. 
    
#### <a name="warm-standby"></a>Betriebsbereit

- Hierzu gehört eine kleine Farm, die bereitgestellt und betrieben wird. 
    
- Die Farm kann Benutzer sofort bei einem Failover bedienen. 
    
- Skalieren Sie die Farm schnell, um die vollständige Benutzerbasis bereitzustellen. 
    
#### <a name="hot-standby"></a>Hot-Standby

Eine vollständige Farm wird bereitgestellt und im Standbymodus betrieben. 
  
Das begleitende Diagramm zeigt eine lokale Farm, die mit der SharePoint-Notfallwiederherstellungsumgebung in Azure interagiert. Die lokalen Datenbanken verwenden den SQL Server-Protokollversand über den VPN-Tunnel für den Zugriff auf die SharePoint-Notfallwiederherstellungsumgebung, die zwei SQL-Datenbankserver enthält, die die SharePoint-Datenbanken, zwei Web-Front-End-Server und zwei SharePoint Anwendungsserver. 
  

