---
title: "Weiterentwickeln Ihres Netzwerks für Cloudkonnektivität"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: "Zusammenfassung: Grundlegende Informationen darüber, warum für die Cloudakzeptanz ein neuer Ansatz für Investitionen in die Netzwerkinfrastruktur erforderlich ist."
ms.openlocfilehash: 18b4e5e10094a43f0d2b10cd0f01684f2352a0a8
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>Weiterentwickeln Ihres Netzwerks für Cloudkonnektivität

 **Zusammenfassung:** Grundlegende Informationen darüber, warum für die Cloudakzeptanz ein neuer Ansatz für Investitionen in die Netzwerkinfrastruktur erforderlich ist.
  
Cloudmigration ändert das Volumen und die Art des Datenverkehrs innerhalb und außerhalb eines Unternehmensnetzwerks. Sie hat ebenfalls Auswirkungen auf Ansätze zur Reduzierung von Sicherheitsrisiken.
  
- Vor der Cloud
    
    Die meisten Investitionen in Netzwerkinfrastruktur dienten dem Zweck, eine verfügbare, zuverlässige und leistungsfähige Konnektivität für lokale Rechenzentren sicherzustellen. Für viele Organisationen war die Internetkonnektiviät für den internen Geschäftsbetrieb nicht entscheidend. Netzwerkgrenzen dienten hauptsächlich der Abwehr von Sicherheitsrisiken.
    
- Nach der Cloud
    
    Aufgrund der neuen und migrierten Produktivität und IT-Arbeitslasten, die in der Cloud ausgeführt werden, verlagern sich die Infrastrukturinvestitionen von lokalen Rechenzentren hin zu Internetkonnektivität, die für den internen Geschäftsbetrieb nun entscheidend ist. Aufgrund der Verbundkonnektivität verlagert sich die Sicherheitsstrategie auf das Schützen von Identitäten und Daten, während sich diese durch das Netzwerk und Konnektivitätspunkte hin zu Microsoft-Clouddiensten bewegen.
    
Investitionen in die Netzwerkinfrastruktur beginnen mit der Konnektivität. Zusätzliche Investitionen sind von der Kategorie des Clouddiensts abhängig.
  
- **Software as a Service (SaaS)** Microsoft SaaS-Dienste umfassen Office 365, Microsoft Intune und Microsoft Dynamics 365. Die erfolgreiche Akzeptanz von SaaS-Diensten durch Benutzer ist von einer hochverfügbaren und leistungsfähigen Konnektivität mit dem Internet oder direkt von Microsoft-Clouddiensten abhängig.
    
    Die Netzwerkarchitektur konzentriert sich auf eine zuverlässige, redundante Konnektivität und eine hohe Bandbreite. Laufende Investitionen umfassen eine Leistungsüberwachung und -optimierung.
    
- **Azure Platform as a Service (PaaS)** Zusätzlich zu den Investitionen für Microsoft SaaS-Dienste muss für PaaS-Anwendungen mit mehreren Standorten oder Anwendungen, die geografisch verteilt sind, möglicherweise Azure Traffic Manager zum Verteilen des Clientdatenverkehrs entwickelt werden. Laufende Investitionen umfassen eine Überwachung der Leistung und der Datenverkehrverteilung sowie Failover-Tests.
    
- **Azure Infrastructure as a Service (IaaS)** Zusätzlich zu den Investitionen für Microsoft SaaS- und PaaS-Dienste müssen für das Ausführen von IT-Arbeitslasten in IaaS virtuelle Azure-Netzwerke entwickelt und konfiguriert werden, in denen virtuelle Computer gehostet werden und die Konnektivität mit Anwendungen sichergestellt ist, die darauf ausgeführt werden, sowie Routing, IP-Adressierung, DNS und Lastenausgleich. Laufende Investitionen umfassen eine Leistungs- und Sicherheitsüberwachung sowie Problembehandlung.
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>Bereiche für Netzwerkinvestitionen für Erfolg in der Cloud

Große Organisationen profitieren von einem methodischen Ansatz zur Optimierung des Netzwerkdurchsatzes über Ihr Intranet und mit dem Internet. Sie können vielleicht auch von einer ExpressRoute-Verbindung profitieren.
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>Optimieren der Intranetkonnektivität mit Ihrem Umkreisnetzwerk

Im Laufe der Jahre haben viele Organisationen die Intranetkonnektivität und Leistung für Anwendungen optimiert, die in lokalen Rechenzentren ausgeführt werden. Aufgrund der Produktivität und IT-Arbeitslasten, die in der Microsoft-Cloud ausgeführt werden, muss durch zusätzliche Investitionen eine hohe Konnektivitätsverfügbarkeit sichergestellt werden und gewährleistet sein, dass die Datenverkehrleistung zwischen Ihrem Umkreisnetzwerk und Ihren Intranetbenutzern optimal ist.
  
### <a name="optimize-throughput-at-your-edge-network"></a>Optimieren des Durchsatzes in Ihrem Umkreisnetzwerk

Da ein immer größerer Teil Ihres täglichen Produktivitätsverkehrs in die Cloud geht, sollten Sie die Systeme in Ihrem Umkreisnetzwerk sorgfältig prüfen, um sicherzustellen, dass diese auf dem neuesten Stand sind, hohe Verfügbarkeit bieten und über ausreichende Kapazitäten für Spitzenlasten verfügen.
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>Verwenden Sie ExpressRoute für eine hohe SLA mit Azure, Office 365 und Dynamics 365

Sie können zwar die aktuelle Internetverbindung Ihres Umkreisnetzwerks verwenden, der Datenverkehr zu und von Microsoft-Clouddiensten muss aber die Pipe mit anderem Intranetdatenverkehr gemeinsam verrenden, der ins Internet führt. Darüber hinaus unterliegt Ihr Datenverkehr an Microsoft-Clouddienste der Überlastung durch Internetdatenverkehr.
  
Verwenden Sie für eine hohe SLA und optimale Leistung ExpressRoute, eine dedizierte WAN-Verbindung zwischen Ihrem Netzwerk und Azure, Office 365, Dynamics 365 oder alle drei Optionen. 
  
Über ExpressRoute können Sie Ihren vorhandenen Netzwerkdienstanbieter für eine dedizierte Verbindung nutzen. Ressourcen, die über ExpressRoute verbunden werden, werden angezeigt, als wären Sie in Ihrem WAN, auch bei geografisch verteilten Organisationen.
  
Weitere Informationen finden Sie unter [ExpressRoute für Microsoft-Cloudkonnektivität](expressroute-for-microsoft-cloud-connectivity.md).
  
## <a name="scope-of-network-investments"></a>Umfang von Netzwerkinvestitionen

Der Umfang von Netzwerkinvestitionen ist von der Kategorie des Clouddiensts abhängig. Investitionen über die Microsoft-Cloud hinweg maximieren die Investitionen von Netzwerkteams. Investitionen für IaaS-Dienste treffen beispielsweise auf alle Investitionsbereiche zu.
  
|||||
|:-----|:-----|:-----|:-----|
|Investitionsbereich  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|Entwerfen einer zuverlässigen, redundanten und leistungsfähigen Konnektivität mit großer Bandbreite  <br/> |Trifft zu  <br/> |Trifft zu  <br/> |Trifft zu  <br/> |
|Überwachen und Optimieren des Internetdurchsatzes für Leistung  <br/> |Trifft zu  <br/> |Trifft zu  <br/> |Trifft zu  <br/> |
|Behandeln von Problemen mit Internetkonnektivität und Durchsatz  <br/> |Trifft zu  <br/> |Trifft zu  <br/> |Trifft zu  <br/> |
|Entwickeln von Azure Traffic Manager derart, dass ein Lastenausgleich des Datenverkehrs auf unterschiedliche Endpunkte ausgeführt wird  <br/> ||Trifft zu  <br/> |Trifft zu  <br/> |
|Entwerfen einer zuverlässigen, redundanten und leistungsfähigen Konnektivität mit virtuellen Azure-Netzwerken  <br/> |||Trifft zu  <br/> |
|Entwerfen einer sicheren Konnektivität mit virtuellen Azure-Computern  <br/> |||Trifft zu  <br/> |
|Entwerfen und Implementieren von Routing zwischen lokalen Speicherorten und virtuellen Netzwerken  <br/> |||Trifft zu  <br/> |
|Entwerfen und Implementieren eines Lastenausgleich für interne Arbeitslasten und Arbeitslasten im Internet  <br/> |||Trifft zu  <br/> |
|Behandeln von Problemen mit der Konnektivität virtueller Computer und dem Durchsatz  <br/> |||Trifft zu  <br/> |
   
## <a name="see-also"></a>Weitere Artikel

[Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md)
  
[ExpressRoute für Microsoft-Cloudkonnektivität](expressroute-for-microsoft-cloud-connectivity.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger]((https://sway.com/FJ2xsyWtkJc2taRD))



