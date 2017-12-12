---
title: "Gemeinsame Elemente der Microsoft-Cloudkonnektivität"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/10/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "Zusammenfassung: Informationen zu gemeinsamen Elementen der Netzwerkinfrastruktur und zu Vorbereitungen des Netzwerks."
---

# Gemeinsame Elemente der Microsoft-Cloudkonnektivität

 **Zusammenfassung:** Informationen zu gemeinsamen Elementen der Netzwerkinfrastruktur und zu Vorbereitungen des Netzwerks.
  
Die Integration Ihres Netzwerks in die Microsoft-Cloud bietet optimalen Zugriff auf eine Vielzahl von Diensten.
  
## Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud-Dienste
<a name="steps"> </a>

Für Ihr lokales Netzwerk:
  
1. Analysieren Sie Ihre Clientcomputer, und optimieren Sie die Netzwerkhardware, Softwaretreiber, Protokolleinstellungen und Internetbrowser.
    
2. Analysieren Sie Ihr lokales Netzwerk im Hinblick auf Wartezeiten und optimales Routing an das Internet-Edgegerät.
    
3. Analysieren Sie die Kapazität und Leistung Ihres Internet-Edgegeräts, und optimieren Sie es im Hinblick auf höheren Datenverkehr.
    
Für Ihre Internetverbindung.
  
1. Analysieren Sie die Wartezeit zwischen dem Internet-Edgegerät (z. B. die externe Firewall) und den regionalen Standorten des Microsoft Cloud-Diensts, mit dem Sie eine Verbindung herstellen.
    
2. Analysieren Sie die Kapazität und die Nutzung Ihrer aktuellen Internetverbindung, und fügen Sie Kapazität hinzu, falls erforderlich. Fügen Sie alternativ eine ExpressRoute-Verbindung hinzu.
    
## Optionen für Microsoft-Cloudkonnektivität
<a name="steps"> </a>

Verwenden Sie Ihre vorhandene Internetpipe oder eine ExpressRoute-Verbindung mit Office 365, Azure und Dynamics 365.
  
**Abbildung 1: Optionen für Microsoft-Cloudkonnektivität**

![Abbildung 1:  Optionen für Microsoft-Cloudkonnektivität](images/594b3a80-2c32-4402-bdee-e85cd25c0b2f.png)
  
In Abbildung 1 wird gezeigt, wie ein lokales Netzwerk mithilfe der vorhandenen Internetpipe oder ExpressRoute mit Microsoft-Cloudangeboten verbunden werden kann. Die Internetpipe stellt ein Umkreisnetzwerk dar und kann die folgenden Komponenten aufweisen:
  
- **Interne Firewall:** Eine Grenze zwischen Ihrem vertrauenswürdigen Netzwerk und einem nicht vertrauenswürdigen Netzwerk. Führt eine Filterung des Datenverkehrs (basierend auf Regeln) und eine Überwachung aus.
    
- **Externe Arbeitslast:** Websites oder andere Arbeitslasten, die externen Benutzern im Internet zur Verfügung gestellt werden.
    
- **Proxyserver:** Dienstanforderungen für Webinhalte im Auftrag von Intranetbenutzern. Ein Reverse-Proxy lässt unerwünschte eingehende Anfragen zu.
    
- **Externe Firewall:** Lässt ausgehenden Datenverkehr und angegebenen eingehenden Datenverkehr zu. Kann eine Adressübersetzung durchführen.
    
- **WAN-Verbindung zum Internetdienstanbieter:** Eine anbieterbasierte Verbindung zu einem ISP, der mit dem Internet für Konnektivität und Routing auf der gleichen Ebene steht.
    
## In allen Microsoft-Cloud-Diensten gemeinsame Netzwerkbereiche
<a name="steps"> </a>

Sie müssen diese Netzwerkbereiche berücksichtigen, wenn Sie einen der Clouddienste von Microsoft einführen.
  
- **Intranetleistung:** Die Leistung von internetbasierten Ressourcen wird beeinträchtigt, wenn das Intranet, einschließlich Clientcomputern, nicht optimiert ist.
    
- **Edgegeräte:** Geräte am Rand Ihres Netzwerks sind Ausgangspunkte und können NATs (Network Adress Translators), Proxyserver (einschließlich Reverse-Proxys, Firewalls, Angriffserkennungssysteme oder eine Kombination daraus umfassen.
    
- **Internetverbindung:** Die WAN-Verbindung zu Ihrem Internetdienstanbieter und das Internet sollten über ausreichend Kapazität für Höchstlasten verfügen. Sie können auch eine ExpressRoute-Verbindung verwenden.
    
- **Internet-DNS:** A-, AAAA-, CNAME-, MX-, PTR- und andere Datensätze, um die Microsoft-Cloud oder die in der Cloud gehosteten Dienste zu suchen. Beispielsweise benötigen Sie möglicherweise einen CNAME-Eintrag für Ihre in Azure PaaS gehostete App.
    
## See Also
<a name="steps"> </a>

#### 

[Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
#### 

[Enterprise-Cloud-Roadmap: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)

