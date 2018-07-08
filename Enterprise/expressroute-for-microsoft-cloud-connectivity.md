---
title: ExpressRoute für Microsoft-Cloudkonnektivität
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/03/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Zusammenfassung: Verstehen Sie, wie Sie mit ExpressRoute schnellere und zuverlässigere Verbindungen zu Microsoft-Clouddiensten und -Plattformen erzielen können.'
ms.openlocfilehash: 55ac09e3c3cf65649d24d67ea79e185808d83cdb
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188113"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a>ExpressRoute für Microsoft-Cloudkonnektivität

 **Zusammenfassung:** Verstehen Sie, wie Sie mit ExpressRoute schnellere und zuverlässigere Verbindungen zu Microsoft-Clouddiensten und -Plattformen erzielen können.
  
ExpressRoute bietet eine private, dedizierte Netzwerkverbindung mit hohem Durchsatz mit der Microsoft Cloud.
  
## <a name="expressroute-to-the-microsoft-cloud"></a>ExpressRoute in die Microsoft-Cloud

Nachfolgend finden Sie den Netzwerkpfad zur Microsoft-Cloud ohne ExpressRoute-Verbindung.
  
**Abbildung 1: Der Netzwerkpfad ohne ExpressRoute**

![Abbildung 1: Der Netzwerkpfad ohne ExpressRoute](images/Network_Poster/ExpressRoute.png)
  
Abbildung 1 zeigt den typischen Pfad zwischen einem lokalen Netzwerk und der Microsoft Cloud. Das lokale Netzwerk-Edge stellt über einen WAN-Link zu einem Internetdienstanbieter eine Verbindung zum Internet her. Der Datenverkehr bewegt dann sich über das Internet an den Rand der Microsoft Cloud. Cloud-Angebote innerhalb der Microsoft Cloud umfassen Office 365, Microsoft Azure, Microsoft Intune und Dynamics 365. Benutzer einer Organisation können sich im lokalen Netzwerk oder im Internet befinden.
  
Ohne eine ExpressRoute-Verbindung ist der einzige Teil des Datenverkehrpfads in die Microsoft Cloud, den Sie steuern können (und der eine Beziehung zu dem Dienstanbieter hat), der Link zwischen dem lokalen Netzwerk-Edge und dem Internetdienstanbieter. 
  
Der Pfad zwischen Ihrem Internetdienstanbieter und dem Rand der Microsoft Cloud ist ein umfassendes Übermittlungssystem im Internet, das Ausfällen, Überlastungen und einer Überwachung durch böswillige Benutzer unterliegt.
  
Benutzer im Internet, z. B. Roaming- oder Remotebenutzer, senden ihren Datenverkehr über das Internet an die Microsoft Cloud.
  
Nachfolgend finden Sie die Netzwerkpfade zur Microsoft Cloud mit ExpressRoute-Verbindung.
  
**Abbildung 2: Die Netzwerkpfade ohne ExpressRoute**

![Abbildung 2: Die Netzwerkpfade ohne ExpressRoute](images/Network_Poster/ExpressRoute_post.png)
  
Abbildung 2 zeigt zwei Netzwerkpfade. Der Datenverkehr zu Microsoft Intune bewegt sich über denselben Pfad wie normaler Internetverkehr. Datenverkehr zu Office 365, Microsoft Azure und Dynamics 365 bewegt sich über die ExpressRoute-Verbindung, ein dedizierter Pfad zwischen dem Rand des lokalen Netzwerks und dem Rand der Microsoft Cloud.
  
Eine Verbindung ExpressRoute Sie jetzt-Steuerelements über eine Beziehung mit Ihrem Dienstanbieter haben, über den gesamten Datenverkehr Pfad von der Kante des Microsoft cloud Edge. Diese Verbindung kann vorhersehbare Leistung und einen [99,95 % Betriebszeit SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)anbieten.
  
Sie können sich nun auf vorhersehbaren Durchsatz und planbare Wartezeit basierend auf der Verbindung Ihres Dienstanbieters für Office 365-, Azure- und Dynamics 365-Dienste verlassen. ExpressRoute-Verbindungen mit Microsoft Intune werden derzeit nicht unterstützt.
  
Datenverkehr, der über die ExpressRoute-Verbindung gesendet wird, unterliegt nicht mehr Internetausfällen, Überlastungen und Überwachungen.
  
Benutzer im Internet, z. B. Roaming- oder Remotebenutzer, senden ihren Datenverkehr nach wie vor über das Internet an die Microsoft Cloud. Eine Ausnahme stellt der Datenverkehr zu einer Branchenanwendung im Intranet dar, die in Azure IaaS gehostet wird, der über die ExpressRoute-Verbindung über eine Remotezugriffverbindung an das lokale Netzwerk gesendet wird.
  
Selbst bei einer ExpressRoute-Verbindung wird ein Teil des Datenverkehrs nach wie vor über das Internet gesendet, z. B. DNS-Abfragen, Überprüfungen der Zertifikatssperrliste und CDN-Anfragen (Content Delivery Netzwerk, Netzwerk für die Inhaltsübermittlung).
  
Weitere Informationen finden Sie in den folgenden Ressourcen:
  
- [ExpressRoute für Office 365](https://aka.ms/expressrouteoffice365)
    
- [ExpressRoute für Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a>Vorteile von ExpressRoute für Azure

Nachfolgend finden Sie einige der Vorteile der Verwendung von ExpressRoute für Azure-basierte Clouddienste:
  
- **Vorhersagbare Leistung:** Mit einem dedizierten Pfad am Rand der Microsoft Cloud unterliegt Ihre Leistung nicht Ausfällen von Internetdienstanbietern und Überlastungen. Sie können Ihre Anbieter im Hinblick auf eine Durchsatz- und Wartezeit-SLA für die Microsoft Cloud zur Verantwortung ziehen.
    
- **Datenschutz für Ihren Datenverkehr:** Verkehr, der über die dedizierte ExpressRoute-Verbindung gesendet wird, unterliegt nicht der Internetüberwachung oder Paketerfassung und Analyse durch böswillige Benutzer. Diese Verbindung ist so sicher wie die Verwendung von MPLS-basierten WAN-Links.
    
- **Verbindungen mit hohem Durchsatz:** Dank einer umfassenden Unterstützung von ExpressRoute-Verbindungen durch Exchange-Anbieter und Netzwerkdienstanbieter können Sie einen Link mit bis zu 10 Gbit/s zur Microsoft Cloud erreichen.
    
- **Niedrigere Kosten für einige Konfigurationen:** Obwohl ExpressRoute-Verbindungen zusätzliche Kosten bedeuten, kann eine einzige ExpressRoute-Verbindung in einigen Fällen weniger kosten als eine Steigerung Ihrer Internetkapazität an mehreren Standorten Ihrer Organisation, um einen angemessenen Durchsatz zu Microsoft-Clouddiensten bereitzustellen.
    
Eine ExpressRoute-Verbindung ist nicht in jeder Konfiguration eine Garantie für höhere Leistung. Es ist möglich, dass über eine ExpressRoute-Verbindung mit niedriger Bandbreite eine niedrigere Leistung erzielt wird als mit einer Internetverbindung mit hoher Bandbreite, die sich nicht weit von einem regionalen Microsoft-Rechenzentrum befindet.
  
Die neuesten Empfehlungen zur Verwendung von ExpressRoute mit Office 365 finden Sie unter [ExpressRoute für Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).
  
## <a name="expressroute-connectivity-models"></a>ExpressRoute-Verbindungsmodelle

Tabelle 1 zeigt die drei primären Verbindungsmodelle für ExpressRoute-Verbindungen.
  
|**Co-Location bei einem Cloud Exchange**|**Punkt-zu-Punkt-Ethernet**|**n:n-Verbindung (IP VPN)**|
|:-----|:-----|:-----|
|![ExpressRoute-Konnektivitätsmodell: Zusammengestellt bei einem Cloud-Austausch](images/Network_Poster/ER_Conn1.png)|![ExpressRoute-Konnektivitätsmodell: Punkt-zu-Punkt-Ethernet](images/Network_Poster/ER_Conn2.png)|![ExpressRoute-Konnektivitätsmodell: N:n-Verbindung (IP-VPN)](images/Network_Poster/ER_Conn3.png)|
|Wenn Sie sich in einer Einrichtung mit einem Cloud Exchange befinden, können Sie virtuelle Querverbindungen zur Microsoft Cloud über den Ethernet Exchange des Co-Location-Anbieters bestellen.  <br/> |Sie können Ihre lokalen Rechenzentren über einen Punkt-zu-Punkt-Ethernet-Link mit der Microsoft Cloud verbinden.  <br/> |Wenn Sie bereits einen IP VPN (MLPS)-Anbieter verwenden, um die Websites Ihrer Organisation zu verbinden, fungiert eine ExpressRoute-Verbindung zur Microsoft Cloud wie ein weiterer Standort in Ihrem privaten WAN.  <br/> |
   
 **Tabelle 1: ExpressRoute-Verbindungsmodelle**
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a>ExpressRoute-Peeringbeziehungen zu Microsoft-Clouddiensten

Eine einzelne ExpressRoute-Verbindung unterstützt bis zu drei verschiedene BGP-Peeringbeziehungen (Border Gateway Protocol) zu unterschiedlichen Teilen der Microsoft Cloud. BPG verwendet Peeringbeziehungen, um Vertrauensstellungen einzurichten und Routinginformationen auszutauschen.
  
**Abbildung 3: Die drei verschiedenen BGP-Beziehungen in einer einzigen ExpressRoute-Verbindung**

![Abbildung 3: Die drei verschiedenen BGP-Beziehungen in einer einzigen ExpressRoute-Verbindung](images/Network_Poster/ERPeering.png)
  
Abbildung 3 zeigt eine ExpressRoute-Verbindung aus einem lokalen Netzwerk. Die ExpressRoute-Verbindung enthält drei logische Peeringbeziehungen. Eine Microsoft-Peeringbeziehung besteht zu Microsoft SaaS-Diensten, einschließlich Office 365 und Dynamcs CRM Online. Eine öffentliche Peeringbeziehung besteht zu Azure PaaS-Diensten. Eine private Peeringbeziehung besteht zu Azure IaaS und zu einem virtuellen Netzwerkgateway, auf dem virtuelle Computer gehostet werden.
  
Die Microsoft-BGP-Peeringbeziehung: 
  
- Besteht zwischen einem Router in Ihrem Ukreisnetzwerk und den öffentlichen Adressen von Office 365 und Dynamics 365-Diensten. 
    
- Unterstützt die bidirektional initiierte Kommunikation.
    
Die öffentliche BGP-Beziehung:
  
- Besteht zwischen einem Router in Ihrem Umkreisnetzwerk und den öffentlichen IP-Adressen von Azure-Diensten.
    
- Unterstützt nur die unidirektional initiierte Kommunikation von lokalen Systemen. Die Peeringbeziehung unterstützt keine Kommunikation, die von Azure PaaS-Diensten initiiert wird.
    
Die private BGP-Peeringbeziehung:
  
- Besteht zwischen einem Router am Rand des Unternehmensnetzwerks und den privaten IP-Adressen, die Ihren Azure VNets zugewiesen sind.
    
- Unterstützt die bidirektional initiierte Kommunikation.
    
- Ist eine Erweiterung Ihres Organisationsnetzwerks in die Microsoft Cloud, die über eine intern konsistente Adresse und Routing verfügt.
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a>Beispiel der Anwendungsbereitstellung und für den Fluss des Datenverkehrs mit ExpressRoute

Wie sich Datenverkehr über ExpressRoute-Verbindungen hinweg und innerhalb der Microsoft Cloud bewegt ist eine Funktion der Routen an den Hops des Pfads zwischen der Quelle und dem Ziel sowie des Anwendungsverhaltens. Nachfolgend finden Sie ein Beispiel für eine Anwendung, die auf einem virtuellen Azure-Computer ausgeführt wird, der auf eine lokale SharePoint-Farm über eine Standort-zu-Standort-VPN-Verbindung zugreift.
  
**Abbildung 4: Eine Anwendung auf einem virtuellen Azure-Computer, der auf eine lokale SharePoint-Farm zugreift**

![Abbildung 4: Eine Anwendung auf einem virtuellen Azure-Computer, der auf eine lokale SharePoint-Farm zugreift](images/Network_Poster/ER_App_Flow1.png)

  
Abbildung 4 zeigt eine lokale SharePoint-Farm, eine Standort-zu-Standort-VPN-Verbindung zwischen dem lokalen Netzwerk und einem virtuellen Netzwerk in Azure IaaS, einen Anwendungsserver, der als ein virtueller Azure IaaS-Computer ausgeführt wird, und den Datenverkehr zwischen dem Anwendungsserver und der SharePoint-Farm.
  
Die Anwendung sucht die IP-Adresse der SharePoint-Farm mithilfe der lokalen DNS, und der gesamte Datenverkehr läuft über die Standort-zu-Standort-VPN-Verbindung.
  
Diese Organisation hat ihre lokale SharePoint-Farm zu SharePoint Online in Office 365 migriert und eine ExpressRoute-Verbindung bereitgestellt.
  
**Abbildung 5: Verschieben der lokalen SharePoint-Farm zu SharePoint Online**

![Abbildung 5: Verschieben der lokalen SharePoint-Farm zu SharePoint Online](images/Network_Poster/Hairpin1.png)
  
Abbildung 5 zeigt das Hinzufügen einer ExpressRoute-Verbindung mit Peeringbeziehungen zu Microsoft SaaS und Office 365 und zu Azure IaaS, das den Anwendungsserver in einem virtuellen Netzwerk enthält. Die lokale SharePoint-Farm wurde nach Office 365 migriert.
  
Mit der Microsoft-Peeringbeziehung und der privaten Peeringbeziehung:
  
- Vom virtuellen Azure-Netzwerkgateway stehen lokale Standorte über die ExpressRoute-Verbindung zur Verfügung.
    
- Aus dem Office 365-Abonnement stehen öffentliche IP-Adressen von Edgegeräten, z. B. Proxyserver, über die ExpressRoute-Verbindung zur Verfügung.
    
- vom Rand des lokalen Netzwerks stehen die privaten IP-Adressen von Azure VNet und die öffentlichen IP-Adressen von Office 365 über die ExpressRoute-Verbindung zur Verfügung.
    
Wenn die Anwendung auf die URLs von SharePoint Online zugreift, wird der Datenverkehr über die ExpressRoute-Verbindung an einen Proxyserver am Rand weitergeleitet. 
  
Wenn der Proxyserver die IP-Adresse von SharePoint Online gefunden hat, wird der Datenverkehr wieder über die ExpressRoute-Verbindung zurückgeleitet. Antwortdatenverkehr wird über den umgekehrten Pfad übermittelt.
  
**Abbildung 6: Datenfluss, wenn die SharePoint-Farm zu SharePoint Online in Office 365 migriert wurde**

![Abbildung 6: Datenfluss, wenn die SharePoint-Farm zu SharePoint Online in Office 365 migriert wurde](images/Network_Poster/Hairpin2.png)

  
Abbildung 6 zeigt, wie der Datenverkehr zwischen dem Anwendungsserver und SharePoint Online in Office 365 über die private Peeringbeziehung vom Anwendungsserver an den Rand des lokalen Netzwerks und dann vom Rand über die Microsoft-Peeringbeziehung zu Office 365 fließt.
  
Das Ergebnis ist das so genannte „Hair Pinning“, eine Konsequenz des Routing- und Anwendungsverhaltens.
  
## <a name="expressroute-and-microsofts-cloud-network"></a>ExpressRoute und Microsoft Cloud-Netzwerk

ExpressRoute-Verbindungen sind in zwei unterschiedlichen Versionen verfügbar: ExpressRoute und ExpressRoute Premium.
  
### <a name="expressroute"></a>ExpressRoute

Die Art und Weise, wie sich Datenverkehr zwischen Ihrem Organisationsnetzwerk und einem Microsoft-Rechenzentrum bewegt, ist eine Kombination von Folgendem:
  
- Ihren Standorten.
    
- Den Microsoft Cloud-Peeringstandorten (die physischen Standorte, die mit dem Microsoft-Edge verbunden werden sollen).
    
- Den Standorten der Microsoft-Rechenzentren.
    
Die Standorte der Microsoft-Rechenzentren und der Cloud-Peeringbeziehungen sind alle mit dem Microsoft Cloud-Netzwerk verbunden.
  
Wenn Sie eine ExpressRoute-Verbindung mit einem Microsoft Cloud-Peeringstandort erstellen, werden Sie mit dem Microsoft Cloud-Netzwerk und allen Microsoft-Rechenzentrumstandorten auf demselben Kontinent verbunden. Der Datenverkehr zwischen dem Cloud-Peeringstandort und dem Microsoft-Zielrechenzentrum erfolgt über das Microsoft Cloud-Netzwerk.
  
Dies kann zu einer nicht optimalen Übermittlung an lokale Microsoft-Rechenzentren für das n:n-Verbindungsmodell führen.
  
**Abbildung 7: Beispiel für ein geografisch verteiltes Unternehmen, das eine einzelne ExpressRoute-Verbindung verwendet.**

![Abbildung 7: Beispiel für ein geografisch verteiltes Unternehmen, das eine einzelne ExpressRoute-Verbindung verwendet.](images/Network_Poster/MSNet1.png)
  
Abbildung 7 zeigt eine Organisation mit zwei Standorten, Standort 1 im Nordwesten der USA, und Standort 2 im Nordosten. Diese sind durch einen n: n-WAN-Anbieter verbunden. Diese Organisation verfügt auch über eine ExpressRoute-Verbindung zu einem Microsoft-Peeringstandort an der Westküste. Datenverkehr von Standort 2 im Nordosten, der an ein Rechenzentrum an der Ostküste gerichtet ist, muss den gesamten Weg über das WAN der Organisation an die Westküste, an den Microsoft-Peeringstandort und dann zurück über das gesamte Land über das Microsoft Cloud-Netzwerk an das Rechenzentrum an der Ostküste zurücklegen.
  
Verwenden Sie für eine optimale Übermittlung mehrere ExpressRoute-Verbindungen mit regionalen Microsoft Cloud-Peeringstandorten. 
  
**Abbildung 8: Die Verwendung mehrerer ExpressRoute-Verbindungen für optimale Übermittlung an regionale Rechenzentren**

![Abbildung 8: Die Verwendung mehrerer ExpressRoute-Verbindungen für optimale Übermittlung an regionale Rechenzentren](images/Network_Poster/MSNet2.png)
  
Abbildung 8 zeigt dieselbe Organisation mit zwei ExpressRoute-Verbindungen, eine für jeden Standort, mit regional lokalen Microsoft-Peeringstandorten. In dieser Konfiguration geht Datenverkehr von Standort 2 im Nordosten, der an ein Rechenzentrum an der Ostküste gerichtet ist, direkt zu einem Peeringstandort an der Ostküste, zum Microsoft Cloud-Netzwerk und dann zu dem Rechenzentrum an der Ostküste.
  
Vorteile mehrerer ExpressRoute-Verbindungen:
  
- Eine bessere Leistung für regional lokale Microsoft-Rechenzentrumsstandorte.
    
- Höhere Verfügbarkeit in der Microsoft Cloud, wenn eine lokale ExpressRoute-Verbindung nicht mehr verfügbar ist.
    
Dies eignet sich für Organisationen, die sich auf dem gleichen Kontinent befinden. Datenverkehr an Microsoft-Rechenzentren außerhalb des Kontinents, auf dem sich die Organisation befindet, läuft jedoch über das Internet.
  
Für interkontinentalen Datenverkehr über das Microsoft Cloud-Netzwerk müssen Sie die ExpressRoute Premium-Verbindungen verwenden.
  
### <a name="expressroute-premium"></a>ExpressRoute Premium

Für Organisationen, die global über Kontinente verteilt sind, können Sie ExpressRoute Premium verwenden. 
  
Mit ExpressRoute Premium können Sie alle Microsoft-Rechenzentren auf allen Kontinenten von einem beliebigen Microsoft-Peeringstandort auf einem beliebigen Kontinent erreichen. Der Datenverkehr zwischen Kontinenten erfolgt über das Microsoft Cloud-Netzwerk.
  
Vorteile mehrerer ExpressRoute Premium-Verbindungen:
  
- Eine bessere Leistung für kontinental lokale Microsoft-Rechenzentrumsstandorte.
    
- Höhere Verfügbarkeit in der globalen Microsoft Cloud, wenn eine lokale ExpressRoute-Verbindung nicht mehr verfügbar ist.
    
ExpressRoute Premium ist für Office 365-basierte ExpressRoute-Verbindungen erforderlich. Für Unternehmen mit mindestens 500 lizenzierten Benutzern fallen jedoch keine zusätzlichen Kosten an.
  
**Abbildung 9: Das weltweite Microsoft Cloud-Netzwerk**

![Abbildung 9: Das weltweite Microsoft Cloud-Netzwerk](images/Network_Poster/MSNet3.png)
  
Abbildung 9 zeigt ein logisches Diagramm des weltweiten Microsoft Cloud-Netzwerks mit Netzwerken, die sich über die Kontinente und Regionen der Welt und deren Zwischenverbindungen erstrecken. Da sich auf jedem Kontinent ein Teil des Microsoft Cloud-Netzwerks befindet, erstellt ein globales Unternehmen ExpressRoute Premium-Verbindungen von seinen regionalen Zweigstellen zu lokalen Microsoft-Peeringstandorten.
  
Bei einer regionalen Niederlassung bewegt sich entsprechender Office 365-Datenverkehr folgendermaßen:
  
- Datenverkehr an kontinentale Office 365-Rechenzentren bewegt sich über das Microsoft Cloud-Netzwerk innerhalb des Kontinents.
    
- Datenverkehr an Office 365-Rechenzentren auf einem anderen Kontinent bewegt sich über das interkontinentale Microsoft Cloud-Netzwerk.
    
Weitere Informationen finden Sie unter:
  
- [Schulung zu Azure ExpressRoute für Office 365](https://channel9.msdn.com/series/aer/)
    
- [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune)
    
- [Office 365-Leistungsverwaltung](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a>ExpressRoute-Optionen

Sie können auch die folgenden Optionen in Ihre ExpressRoute-Bereitstellung integrieren:
  
- **Sicherheit an Ihrem Edge:** Um erweiterte Sicherheit für den Datenverkehr bereitzustellen, der über die ExpressRoute-Verbindung gesendet und empfangen wird, z. B. die Überprüfung von Datenverkehr oder Angriffserkennung/Schadsoftwareerkennung, platzieren Sie Ihre Sicherheitsgeräte im Datenverkehrpfad innerhalb Ihres Umkreisnetzwerks oder an der Grenze Ihres Intranets.
    
    Internetverkehr für virtuelle Computer Um zu verhindern, dass virtuelle Azure-Computer Datenverkehr direkt mit Internetstandorten initiieren, kündigen Sie die Standardroute zu Microsoft an. Datenverkehr an das Internet wird über die ExpressRoute-Verbindung und über Ihre lokalen Proxyserver geleitet. Datenverkehr von virtuellen Azure-Computern an Azure PaaS-Dienste oder Office 365 wird zurück über die ExpressRoute-Verbindung geleitet.
    
- **WAN-Optimierungen:** Sie können WAN-Optimierungen auf beiden Seiten einer privaten Peeringverbindung für ein standortübergreifendes virtuelles Azure-Netzwerk (VNet) bereitstellen. Verwenden Sie innerhalb des Azure VNet ein Netzwerkgerät für die WAN-Optimierung aus dem Azure Marketplace sowie benutzerdefiniertes Routing, um den Verkehr über das Gerät zu leiten.
    
- **Dienstqualität:** Verwenden Sie DSCP-Werte (Differentiated Services Code Point) in der IPv4-Kopfzeile des Datenverkehrs, um diesen für Sprach-, Video-/interaktive oder eine umfassende Übermittlung zu markieren. Dies ist besonders wichtig für die Microsoft-Peeringbeziehung und Skype for Business Online-Datenverkehr.
    
Weitere Informationen finden Sie in den folgenden Ressourcen:
  
- [ExpressRoute für Office 365](https://aka.ms/expressrouteoffice365)
    
- [Schulung zu Azure ExpressRoute für Office 365](https://channel9.msdn.com/series/aer/)
    
- [ExpressRoute für Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a>Nächster Schritt

[Entwerfen von Netzwerken für Microsoft-SaaS](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a>Siehe auch

[Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)



