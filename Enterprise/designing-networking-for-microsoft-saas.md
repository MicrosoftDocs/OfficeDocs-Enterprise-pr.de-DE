---
title: "Entwerfen von Netzwerken für Microsoft-SaaS"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "Zusammenfassung: Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren."
ms.openlocfilehash: 432789d03f5208a379dc2ab4f17f38f95223e10d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-saas"></a>Entwerfen von Netzwerken für Microsoft-SaaS

 **Zusammenfassung:** Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren.
  
Für die Optimierung Ihres Netzwerks für Microsoft-SaaS-Dienste ist eine sorgfältige Analyse von Internet-Edge, Ihrer Clientgeräte und IT-Standardvorgänge erforderlich.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste

Befolgen Sie diese Schritte, um Ihr Netzwerk für Microsoft SaaS-Dienste zu optimieren:
  
1. Durchlaufen Sie die **Schritte zum Vorbereiten von Ihr Netzwerks für Microsoft Cloud Services** -Abschnitt in [Allgemeine Elemente von Microsoft-Cloud-Diensten](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Optimieren Sie Ihren Internetausgang für Microsoft SaaS-Dienste mithilfe der Proxyserverempfehlungen.
    
3. Optimieren Sie Ihren Internetdurchsatz mithilfe der Empfehlungen für Näherung und Standort.
    
4. Optimieren Sie mithilfe der Überlegungen zur Clientnutzung die Leistung Ihrer Clientcomputer und des Intranets, in dem diese sich befinden.
    
5. Optimieren Sie je nach Bedarf die Leistung von Datenmigrationen und Synchronisierungen mithilfe der Überlegungen zu IT-Abläufen.
    
## <a name="internet-edge-considerations"></a>Überlegungen zu Internet-Edge

Nachfolgend finden Sie einige Punkte, die Sie bei der Optimierung Ihres Internet-Edges und Durchsatzes für Microsoft SaaS-Dienste berücksichtigen sollten.
  
**Abbildung 1: Verbindungsoptionen für Microsoft SaaS-Dienste**

![Abbildung 1: Verbindungsoptionen für Microsoft SaaS-Dienste](images/Network_Poster/SaaS1.png)
  
In Abbildung 1 ist ein lokales Netzwerk dargestellt, das über eine Internetpipe oder ExpressRoute eine Verbindung zu Microsoft SaaS-Diensten herstellt.
  
Hier sind einige Empfehlungen zur Optimierung Ihres Proxyservers:
  
- Konfigurieren der Webclients mithilfe von WPAD, PAC oder GPO
    
- Verwenden Sie keine SSL-Abfangfunktion.
    
- Verwenden Sie eine PAC-Datei, um den Proxy für DNS-Namen des Microsoft SaaS-Diensts zu umgehen.
    
- Lassen Sie den Datenverkehr für die CRL/OCSP-Überprüfung zu.
    
Nachfolgend finden sind einige Proxyserverengpässe, die Sie überprüfen müssen:
  
- Unzureichende permanente Verbindungen (Outlook)
    
- Nicht genügend Kapazität
    
- Ausführen von Auswertungen außerhalb des Netzwerks
    
- Anfordern einer Authentifizierung
    
- Keine Unterstützung für UDP-Datenverkehr (Skype for Business)
    
Hier sind einige Empfehlungen im Hinblick auf Näherung und Standort:
  
- Leiten Sie Ihren Internetverkehr nicht über das private WAN.
    
- Verwenden von bereichsinternem DNS und Internetdatenfluss für Benutzer außerhalb des Bereichs
    
- Verwenden von ExpressRoute für hohe Bandbreite für Office 365 und gleichzeitige Konnektivität mit Azure-Diensten
    
Nachfolgend finden Sie die ausgehenden Ports, die für Office 365-Datenverkehr erforderlich sind:
  
- TCP 80 (für CRL/OCSP-Überprüfungen)
    
- TCP 443
    
- UDP 3478
    
- TCP 5223
    
- TCP 50000-59999
    
- UDP 50000-59999
    
## <a name="client-usage-considerations"></a>Überlegungen zur Clientnutzung

Konfigurieren Sie zuerst die Gruppe der Dienste, die Ihre Kunden verwenden, z. B.:
  
- Azure Active Directory
    
- Office 365
    
  - Office-Clientanwendungen
    
  - SharePoint Online
    
  - Exchange Online
    
  - Skype for Business
    
- Microsoft Intune
    
- Dynamics 365
    
Ermitteln Sie für die Clientcomputer Folgendes:
  
- Maximale Anzahl zu einem beliebigen Zeitpunkt (Tageszeit, Jahreszeit, höchste und niedrigste Auslastung)
    
- Gesamte für Spitzen benötigte Bandbreite
    
- Wartezeit für Internetausgangsgerät
    
- Ursprungsland verglichen mit Land der Rechenzentrumszusammenstellung
    
Prüfen Sie für jeden Typ von Client (PC, Smartphone, Tablet), die aktuelle Version von Folgendem:
  
- Betriebssystem
    
- Internetbrowser
    
- TCP/IP-Stack
    
- Netzwerkhardware
    
- Betriebssystemtreiber für Netzwerkhardware
    
- Updates und Patches sind installiert
    
Optimieren Sie außerdem den Durchsatz der Intranetverbindung (kabelgestützt, kabellos oder VPN).
  
Weitere Informationen finden Sie unter [NAT-Unterstützung für Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).
  
Die neuesten Empfehlungen zur Verwendung von ExpressRoute mit Office 365 finden Sie unter [ExpressRoute für Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).
  
Gehen Sie folgendermaßen Sie vor, um die Intranetleistung zu optimieren:
  
- Verwenden Sie Tools, um Roundtripzeiten (RTTs) für Ihre Internetausgangsgeräte (PsPing, Ping, Tracert, TraceTCP, Network Monitor) zu messen.
    
- Führen Sie eine Ausgangsanalyse mithilfe von Flussprotokollen durch.
    
- Führen Sie Analysen für Zwischengeräte (Alter, Gesundheit usw.) durch.
    
Weitere Informationen finden Sie unter der [PsPing-Tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).
  
## <a name="it-operations-considerations"></a>Überlegungen zu IT-Abläufen

Nachfolgend finden Sie einige Punkte, die beim Arbeiten mit einer IT-Arbeitslast in einem Microsoft SaaS-Dienst zu berücksichtigen sind.
  
### <a name="one-time-migrations"></a>Einmalige Migrationen

Beispiele für einmalige Migration sind Massendatenübertragungen für Cloudbasierte Anwendungen oder Archivspeicher.
  
So optimieren Sie Ihr Netzwerk für einmalige Migrationen:
  
- Vermeiden Sie Spitzenzeiten bei der Netzwerkauslastung und Zeiten, in denen der Computer gepatcht wird.
    
- Bevor Sie mit der tatsächlichen Migration beginnen, sollten Migrationen über Basislinien und Pilotversuche verfügen, die Netzwerkintegrität sollte bewertet und Probleme sollten behoben werden.
    
- Führen Sie Abschlussgespräche für zukünftige Migrationen durch.
    
### <a name="ongoing-synchronizations"></a>Laufende Synchronisierungen

Beispiele für laufende Synchronisierungen sind Verzeichnisinformationen, Einstellungen oder Dateien.
  
So optimieren Sie Ihr Netzwerk für laufende Synchronisierungen:
  
- Stellen Sie sicher, dass ein System für die Überwachung der Netzwerkbandbreite vorhanden ist, lösen Sie gesammelte Fehler oder verwerfen Sie sie.
    
- Verwenden Sie die Ergebnisse der Bandbreitenüberwachung, um festzustellen, ob Netzwerkänderungen erforderlich sind (zentral hochskalieren, horizontal hochskalieren, neue Schaltkreise oder das Hinzufügen von Geräten).
    
Weitere Informationen finden Sie unter:
  
- [Netzwerk- und Migrationsplanung für Office 365](https://aka.ms/tune)
    
- [Microsoft Virtual Academy-Kurs für die Office 365-Leistungsverwaltung](https://aka.ms/o365perf)
    
- [ExpressRoute für Office 365](https://aka.ms/expressrouteoffice365)
    
## <a name="see-also"></a>See Also

[Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)



