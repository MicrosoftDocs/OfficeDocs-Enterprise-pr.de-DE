---
title: "Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Microsoft SharePoint 2013-Plattformoptionen“."
ms.openlocfilehash: 9cd282cc723376f85fe2cbc5a439ee24fd2ab883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen

**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen Microsoft SharePoint 2013-Plattformoptionen.
  
Was Entscheidungsträger (BDMs) und konstruiert zu Office 365, Microsoft Azure und lokale Bereitstellungen wissen müssen. 
  
Dieses Poster hat zwei Abschnitte: 
  
- Einen Vergleich der vier verschiedenen Bereitstellungen für SharePoint 2013: SharePoint im Office 365, einer hybriden von Office 365 mit einer lokalen Bereitstellung von SharePoint 2013, Azure und einer lokalen Bereitstellung von SharePoint 2013. 
    
- Eine Beschreibung der drei typische Arbeitslasten in Azure verschieben. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Vergleich von vier verschiedenen Bereitstellungen für die SharePoint 2013-Plattform

Der Vergleich stellt Informationen zu den einzelnen Bereitstellungsoptionen in den folgenden Bereichen bereit: 
  
- Übersicht der verschiedenen Bereitstellungsfeatures 
    
- Vorteile der einzelnen Arten der Bereitstellung  
    
- Lizenzanforderungen 
    
- Für die Implementierung erforderliche Architekturaufgaben  
    
- Verantwortlichkeiten von IT-Experten für die Implementierung  
    
### <a name="overview"></a>Übersicht

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Mehr Effizienz und Optimierung für Kosten mit mandantenfähigen Office 365-Pläne. 
  
Das zugehörige Diagramm zeigt SharePoint Online mit einer Azure Active Directory-Instanz, Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und den Mandanten Azure Active Directory synchronisiert. 
  
Beschreibung der Features: 
  
- Software as a Service (SaaS). 
    
- Die umfangreiche Funktionspalette ist stets auf dem neuesten Stand.  
    
- Enthält ein Azure Active Directory-Mandanten (kann mit einer anderen Anwendung verwendet werden). 
    
- Verzeichnisintegration umfasst Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und den Mandanten Azure Active Directory synchronisiert. 
    
- Falls einmaliges Anmelden (SSO) eine Anforderung ist, können Active Directory-Verbunddienste (Active Directory Federation Services, AD FS) implementiert werden.   
    
- Clientkommunikation über das Internet über verschlüsselten und authentifizierten Zugriff (Port 443).  
    
- Die Datenmigration ist darauf beschränkt, was über das Internet hochgeladen werden kann.  
    
- Anpassungen: Apps für Office, SharePoint und SharePoint Designer 2013.  
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Kombiniert die Vorteile von Office 365 mit einer lokalen Bereitstellung von SharePoint 2013. 
  
Das zugehörige Diagramm zeigt die Office 365 mit SharePoint Online mit Business Connectivity Services (BCS) für die Verbindung zu einer lokalen SharePoint Server 2013-Farm. 
  
Wählen Sie aus, welche der folgenden Features integriert werden sollen:  
  
SharePoint-Suche 
  
- Benutzer können Suchergebnisse aus beiden Umgebungen anzeigen.   
    
- Extranet-Benutzer können sich remote mit einem lokalen Active Directory-Konto anmelden und die gesamte Hybridfunktionalität nutzen.  
    
BCS
  
Aus SharePoint Online: Benutzer können Lese- und Schreibvorgänge ausführen. Der BCS-Dienst stellt eine Verbindung mit einer lokalen SharePoint Server 2013-Farm her. Der für die lokale Farm konfigurierte BCS-Dienst vermittelt die Verbindung mit den lokalen OData-Dienstendpunkten.   
  
Duet Enterprise Online 
  
Aus SharePoint Online können Benutzer Lese- und Schreibvorgänge für ein lokales SAP-System ausführen.  
  
#### <a name="azure"></a>Azure

Kommen Sie in den Genuss der Cloud, ohne die volle Kontrolle über die Plattform und Features zu verlieren.   
  
Das zugehörige Diagramm zeigt Azure, die zwei Clouddiensten, einer SharePoint 2013-Farm und Windows Server Active Directory mit DNS Herstellen einer Verbindung mit Benutzern über das Internet oder Herstellen einer Verbindung mit der lokalen Active Directory über VPN-Tunnels enthält. 
  
Zu den Features zählen:  
  
-  Azure ist eine Plattform, die die zum Hosten einer SharePoint 2013-Farm erforderlichen Infrastruktur und app-Dienste bereitstellt.
    
- Infrastrukturdienste: 
    
- Beste systemeigene Cloudplattform für SQL Server und SharePoint.  
    
- EDV-Ressourcen stehen nahezu unverzüglich ohne Verpflichtung zur Verfügung.  
    
- Schwerpunkt auf Anwendungen, nicht auf Rechenzentren und Infrastruktur.  
    
- Kostengünstige Entwicklungs- und Testumgebungen.  
    
- Der Zugriff auf SharePoint-Lösungen kann über das Internet ermöglicht oder über einen VPN-Tunnel zwischen Standorten auf eine Unternehmensumgebung beschränkt werden.  
    
- Anpassungen sind nicht eingeschränkt.  
    
#### <a name="on-premises"></a>Lokal

Ihre Zuständigkeit gilt für alles.   
  
Das begleitende Diagramm zeigt eine lokale Umgebung mit Webservern, Anwendungsservern und Active Directory, das für die Suche mit allen Datenbanken und dedizierten Anwendungsservern kommuniziert.  
  
Zu den Features zählen:  
  
- Planung und Festlegung des Umfangs der Kapazität 
    
- Serverbeschaffung und -einrichtung 
    
- Bereitstellung 
    
- Horizontale Skalierung, Patching und Betrieb 
    
- Sichern von Daten 
    
- Vorhalten einer Umgebung für die Notfallwiederherstellung 
    
- Anpassungen sind nicht eingeschränkt.  
    
### <a name="deployment-type-is-best-for---"></a>Vorteile der Bereitstellungsarten

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Sichere externe Freigabe von Daten und Zusammenarbeit. (besonderes Feature!)  
    
- Intranet – Teamwebsites, Meine Websites und interne Zusammenarbeit.  
    
- Dokumentspeicherung und -versionsverwaltung in der Cloud.  
    
- Einfache öffentlich zugängliche Website.  
    
Zusätzliche Features mit Office 365 dedizierte Abonnementpläne: 
  
- Microsoft-Rechenzentrumssysteme, die Ihrer Organisation fest zugeordnet sind und nicht mit anderen Organisationen gemeinsam genutzt werden.   
    
- Jede Kundenumgebung befindet sich in einem physisch getrennten Netzwerk.  
    
- Clientkommunikation über ein mit IPSec geschütztes VPN oder eine private Verbindung in der Zuständigkeit des Kunden. Zweistufige Authentifizierung ist optional.  
    
- Pläne mit ITAR-Unterstützung.  
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

- Verwenden von Office 365 für externe Freigabe und Zusammenarbeit anstelle der Einrichtung einer Extranetumgebung. 
    
- Verschieben Sie „Meine Websites“ (OneDrive for Business) in die Cloud, damit Benutzer remote einfacher auf ihre Dateien zugreifen können.   
    
- Starten Sie neue Teamwebsites in Office 365. 
    
- Integrieren von Office 365-Website in lokalen BCS-SharePoint-Umgebung. 
    
#### <a name="azure"></a>Azure

- SharePoint für Internetwebsites – öffentliche facing Websites. Nutzen Sie die Vorteile von Azure Active Directory für Kundenkonten und Authentifizierung. 
    
- Entwicklungs-, Test- und Stagingumgebungen – Schnelle In- und Außerbetriebnahme ganzer Umgebungen.  
    
- Hybridanwendungen – Anwendungen können sich in Ihrem Rechenzentrum und der Cloud befinden.  
    
- Umgebung für die Notfallwiederherstellung – Schnelle Wiederherstellung nach einem Notfall. Rein nutzungsabhängige Zahlung.  
    
- Farmen, für die eine umfassende Berichterstellung und Überwachung erforderlich sind.  
    
- Web Analytics. 
    
- Verschlüsselung gespeicherter Daten (in den SQL-Datenbanken).  
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Verschlüsselung gespeicherter Daten (in den SQL-Datenbanken)

- Auf Landesgrenzen beschränkte Farmen (wenn sich die Daten in einem bestimmten Rechtsraum befinden müssen).  
    
- Komplexe BI-Lösungen, die sich in der Nähe von BI-Daten befinden müssen.  
    
- Private Cloudlösungen.  
    
- Hoch angepasste Lösungen. 
    
- Legacy-Lösungen mit Drittanbieter-Komponenten, die abhängig von Hardware und Software, die nicht auf Azure Infrastructure Services unterstützt werden. 
    
- Private-Einschränkungen, die Synchronisierung von Active Directory-Benutzerkonten mit Azure Active Directory (eine Voraussetzung für Office 365) zu verhindern. 
    
- Organisationen, die Kontrolle über die gesamte Plattform und Lösung bevorzugen. 
    
### <a name="license-requirements"></a>Lizenzanforderungen

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

Abonnementmodell. Keine weiteren Lizenzen nötig.  
  
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

- Office 365 - Abonnementmodell Keine weiteren Lizenzen nötig. 
    
- Lokal - Alle lokalen Lizenzen sind gültig. 
    
#### <a name="azure"></a>Azure

-  Azure-Abonnement (umfasst das Serverbetriebssystem)
    
- SQL Server 
    
- SharePoint 2013-Serverlizenz 
    
- SharePoint 2013-Clientzugriffslizenz 
    
#### <a name="on-premises"></a>Lokal

- Serverbetriebssystem 
    
- SQL Server 
    
- SharePoint 2013-Serverlizenz 
    
- SharePoint 2013-Clientzugriffslizenz 
    
### <a name="architecture-tasks"></a>Architekturaufgaben

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Verzeichnisintegration planen und entwerfen. Zwei Optionen. Mit beiden Optionen bereitgestellt werden kann, lokal oder in Azure: Kennwort Sync (erfordert eine 64-Bit-Server). SSO (AD FS und mehreren Servern erfordert). 
    
- Sicherstellen von Netzwerkkapazität und -verfügbarkeit durch Firewalls, Proxyserver, Gateways und über WAN-Verbindungen 
    
- Beziehen von SSL-Zertifikaten anderer Anbieter zum Ermöglichen einer unternehmensweiten Sicherheit für Office 365-Dienstangebote 
    
- Planen des Mandantennamens, Entwerfen von Architektur und Steuerung der Websitesammlung.  
    
- Planen von Anpassungen, Lösungen und Apps für SharePoint Online.  
    
- Entscheiden Sie, ob Sie über das Internetprotokoll 6 (IPv6) mit Office 365 verbinden möchten. Dies wird nicht empfohlen. 
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Zusätzlich zu Aufgaben für sowohl Office 365- als auch lokale Umgebungen: 
  
- Bestimmen Sie, wie viele Features integriert werden sollen, und wählen Sie die Hybridtopologie. Siehe das Poster dieses Modells: Welche Hybridtopologie soll ich verwenden?  
    
- Bestimmen Sie, falls erforderlich, welches Proxyservergerät verwendet werden soll.  
    
#### <a name="azure"></a>Azure

Entwerfen Sie die Netzwerkumgebung auf Azure: 
  
- Virtuelles Netzwerk in Azure, einschließlich Subnetze. 
    
- Domänenumgebung und Integration mit lokalen Servern.  
    
- IP-Adressen und DNS.  
    
- Affinitätsgruppen und Speicherkonten.  
    
Entwerfen der SharePoint-Umgebung in Azure: 
  
- Topologie und logische Architektur der SharePoint-Farm.  
    
-  Azure verfügbarkeitssätze und Domänen aktualisieren.
    
- Festlegen der Größen virtueller Computer.   
    
- Endpunkt mit Lastenausgleich.  
    
- Nach Wunsch externe Endpunkte für öffentlichen Zugriff.   
    
- Notfallwiederherstellungsumgebung.  
    
#### <a name="on-premises"></a>Lokal

Entwerfen der SharePoint-Umgebung in einer vorhandenen lokalen Umgebung:  
  
- Topologie und logische Architektur der SharePoint-Farm.  
    
- Server-Hardware. 
    
- Virtuelle Umgebung, falls verwendet.  
    
- Lastenausgleich. 
    
- Integration in AD DS und DNS.   
    
- Notfallwiederherstellungsumgebung.  
    
### <a name="it-pro-responsibilities"></a>Verantwortlichkeiten von IT-Experten

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 in Office 365

- Stellen Sie sicher, dass Benutzerarbeitsstationen Office 365-clientvoraussetzungen erfüllen. 
    
- Implementieren des Verzeichnisintegrationsplans. 
    
- Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings. 
    
- Konfigurieren der Proxy oder der Firewall für Office 365-IP-Adresse und URL-Anforderungen. 
    
- Erstellen und Zuweisen von Berechtigungen zu Websitesammlungen.  
    
- Implementieren von Anpassungen, Lösungen und Apps für SharePoint Online.  
    
- Überwachen der Netzwerkverfügbarkeit und Bestimmen möglicher Engpässe.  
    
#### <a name="hybrid-with-office-365"></a>Hybrid mit Office 365

Zusätzlich zu Aufgaben für sowohl Office 365- als auch lokale Umgebungen: 
  
- Konfigurieren Sie, sofern erforderlich, das Proxyservergerät. 
    
- Konfigurieren Sie die hybride Identitätsverwaltungsinfrastruktur: Einmaliges Anmelden und Server-zu-Server-Authentifizierung zwischen den beiden Umgebungen.  
    
- Konfigurieren Sie die Integration der gewählten Features: Suche, BCS, Duet Enterprise Online.  
    
#### <a name="azure"></a>Azure

Bereitstellen und Verwalten von Azure und SharePoint-Umgebung: 
  
- Implementieren und Verwalten von Azure Netzwerkumgebung. 
    
- Bereitstellen der SharePoint-Umgebung. 
    
- Aktualisieren der SharePoint-Farmserver.  
    
- Bedarfsabhängiges Hinzufügen oder Herunterfahren virtueller Computer basierend auf der Farmauslastung.  
    
- Erhöhen oder Verringern der Größe virtueller Computer den Anforderungen entsprechend.  
    
- Sichern der SharePoint-Umgebung. 
    
- Implementieren der Umgebung und des Protokolls für die Notfallwiederherstellung.  
    
#### <a name="on-premises"></a>Lokal

Bereitstellen und Verwalten der lokalen SharePoint-Umgebung:  
  
- Bereitstellen von Servern. 
    
- Bereitstellen der SharePoint-Umgebung. 
    
- Aktualisieren der SharePoint-Farmserver.  
    
- Bedarfsabhängiges Hinzufügen oder Entfernen von Farmservern basierend auf der Farmauslastung.  
    
- Sichern der SharePoint-Umgebung. 
    
- Implementieren der Umgebung und des Protokolls für die Notfallwiederherstellung.  
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Drei typische Arbeitslasten in Azure verschieben

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 plus Verzeichniskomponenten in Azure

Bereitstellen von Office 365-verzeichnisintegrationskomponenten in Azure ist schneller, da es bei Bedarf virtuellen Computern bereitstellen können. 
  
#### <a name="directory-synchronization-server-only"></a>Nur Verzeichnissynchronisierungsserver

Die 64-Bit-Directory-Synchronisierungsserver in Ihrer lokalen Umgebung bereitstellen möchten, stellen Sie einen virtuellen Computer in Azure stattdessen bereit. 
  
Das zugehörige Diagramm zeigt SharePoint Online mit einer Azure Active Directory-Instanz, Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und den Mandanten Azure Active Directory synchronisiert. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Verzeichnissynchronisierung plus AD FS

Diese Option können Sie Office 365 federated Identitäten (SSO) ohne Hardware in Ihrer lokalen Infrastruktur zu unterstützen. Es bietet auch Flexibilität, wenn die lokale Active Directory-Umgebung nicht verfügbar ist. 
  
- Verzeichnisintegrationskomponenten befinden sich im Azure. 
    
- AD FS ist mit dem Internet über AD FS-Proxys in Azure veröffentlicht. 
    
- Clientauthentifizierungsdatenverkehr für Benutzer, die von einer beliebigen Position verbinden wird von AD FS-Servern und -Proxys, die auf Azure bereitgestellten behandelt. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Öffentliche Internetwebsite und Azure AD für benutzerdefinierte Authentifizierung

Nutzen Sie die Möglichkeit, problemlos Anforderung skaliert durch Ihre Website in Azure platzieren. Verwenden Sie zum Speichern von Kundenkonten Azure AD. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Azure Vorteile für Internetsites

- Zahlen Sie nur für die Ressourcen, die Sie benötigen, indem Sie die Anzahl der virtuellen Computer abhängig von der Farmauslastung skalieren.  
    
- Fügen Sie eine umfassende Berichterstellung und Web Analytics hinzu. 
    
- Konzentrieren Sie sich auf die Entwicklung einer überzeugenden Website und nicht auf die Einrichtung von Infrastruktur. 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD bietet Funktionen Identity Management und Zugriff für Steuerelement für Cloud-Dienste. Merkmale ein Cloud-basierten-Speichers für Directory-Daten und eine Kerngruppe von Identitätsdienste, einschließlich Benutzereingriffe, Authentifizierungsdienste und AD FS. Der Identitätsdienste, die mit Azure AD enthalten sind einfache Integration mit Ihrer lokalen Active Directory-Bereitstellungen und Drittanbieter-Identitätsanbieter vollständig unterstützt. 
  
Das zugehörige Diagramm veranschaulicht die Konfiguration von Zonen und Authentifizierung, die für das Internet gerichtete Websites wichtig sind. Das Diagramm zeigt die Azure Active Directory-Instanz, einer SharePoint-Farm auf Azure mit zwei Zonen enthält: 
  
- Eine Internetzone, die mit anonymen und authentifizierten Besuchern und Kunden außerhalb des Netzwerks interagiert  
    
- Eine Standardzone, die NTLM für die Durchforstung und Windows-Authentifizierung umfasst, die mit Ihrer lokalen Active Directory-Bereitstellung über einen VPN Tunnel interagiert.   
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Lokale Farm plus Disaster Recovery in Azure

Wählen Sie eine Disaster Recovery-Option, die Ihren geschäftlichen Anforderungen entspricht. Azure bietet Einstiegs-Optionen für Unternehmen, die erste Schritte mit Disaster Recovery und erweiterte Optionen für Unternehmen mit hoher Resiliency Requirements. 
  
#### <a name="cold-standby"></a>Verzögert betriebsbereit

- Die Farm ist vollständig erstellt, aber die virtuellen Computer beendet werden. (Sie Zahlen nur, wenn ihnen ausgeführt wird.) 
    
- Zur Verwaltung der Umgebung zählen das Starten der virtuellen Computer in regelmäßigen Abständen, das Einspielen von Patches und Updates sowie das Überprüfen der Umgebung. 
    
- Starten Sie die vollständige Umgebung bei einem Notfall. 
    
#### <a name="warm-standby"></a>Bedingt betriebsbereit

- Dies umfasst eine kleine Farm, die bereitgestellt ist und ausgeführt wird.   
    
- Die Farm kann bei einem Failover sofort die Benutzer unterstützen.   
    
- Skalieren Sie die Farm rasch horizontal, um den gesamten Benutzerstamm zu unterstützen.  
    
#### <a name="hot-standby"></a>Unmittelbar betriebsbereit

Eine vollständig dimensionierte Farm ist bereitgestellt und wird im Standby-Modus ausgeführt. 
  
Das zugehörige Diagramm zeigt eine Interaktion mit der SharePoint-Notfallwiederherstellungsumgebung in Azure lokale Farm. Die lokalen Datenbanken mithilfe von SQL Server-Protokollversand über VPN-Tunnels die Wiederherstellung der SharePoint-Umgebung zugreifen, die zwei SQL-Datenbankserver enthält, die die SharePoint-Datenbanken, zwei Web-Front-End-Servern und zwei SharePoint enthalten Anwendungsserver. 
  

