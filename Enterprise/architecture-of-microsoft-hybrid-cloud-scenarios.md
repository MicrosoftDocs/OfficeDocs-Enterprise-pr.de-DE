---
title: "Architektur von Microsoft Hybrid Cloud-Szenarien"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2016
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Zusammenfassung: Informationen über die Architektur von Microsoft-Hybridcloudangeboten."
---

# Architektur von Microsoft Hybrid Cloud-Szenarien

 **Zusammenfassung:** Informationen über die Architektur von Microsoft-Hybridcloudangeboten.
  
Verwenden Sie eine architekturbezogene Herangehensweise, wenn Sie Hybridcloudszenarien mit Microsoft-Clouddiensten und -plattformen planen und implementieren.
  
**Abbildung 1: Microsoft-Hybridcloudstack**

![Microsoft Hybridcloudstack](images/11a2c362-da62-452d-874b-8c729938ba41.png)
  
Abbildung 1 zeigt den Microsoft-Hybridcloudstack und die Schicht, die lokal, Netzwerk, Identität, Apps, Szenarien und die Kategorie des Clouddiensts (Microsoft SaaS, Azure PaaS und Azure PaaS) enthält.
  
Die Schicht „Apps und Szenarien" enthält die spezifischen Hybridcloudszenarien, die in den zusätzlichen Artikeln dieses Modells detailliert erläutert werden. Die Schichten „Identität", „Netzwerk" und „Lokal" können sich über die Kategorien des Clouddiensts (SaaS, PaaS oder PaaS) erstrecken.
  
- Lokal
    
    Lokale Infrastruktur für Hybridszenarien kann Server für SharePoint, Exchange, Skype for Business und Branchenanwendungen enthalten. Des weiteren kann sie Datenspeicher (Datenbanken, Listen, Dateien) enthalten. Ohne ExpressRoute-Verbindungen muss der Zugriff auf die lokalen Datenspeicher über einen Reverseproxy oder durch Zugriff auf den Server oder die Daten in der DMZ oder dem Extranet gewährt werden.
    
- Netzwerk
    
    Es gibt zwei Optionen für die Verbindung zu Microsoft-Cloudplattformen und -Diensten: der vorhandene Internetzugang oder ExpressRoute. Verwenden Sie eine ExpressRoute-Verbindung, wenn vorhersehbare Leistung wichtig ist. Sie können eine ExpressRoute-Verbindung verwenden, um eine direkte Verbindung mit Microsoft SaaS-Diensten (Office 365 und Dynamics 365), Azure PaaS-Diensten und Azure PaaS-Diensten herzustellen.
    
- Identität
    
    Je nach Microsoft-Cloudplattform gibt es zwei Möglichkeiten für die Cloudidentitätsinfrastruktur. Integrieren Sie für SaaS und Azure PaaS Ihre lokale Identitätsinfrastruktur in Azure AD oder einen Verbund mit Ihrer lokalen Infrastruktur oder Drittanbieter-Identitätsanbietern. Für in Azure ausgeführte virtuelle Computer können Sie Ihre lokale Identitätsinfrastruktur, z. B. Windows Server AD, auf virtuelle Netzwerke (VNets) erweitern, in denen sich ihre virtuellen Computer befinden.
    
## Hybridcloudszenarien für den dreiphasigen Prozess der Cloudeinführung

Viele Unternehmen, so auch Microsoft, verwenden eine dreiphasige Herangehensweise zur Einführung der Cloud. Hybridcloudszenarien können in jeder Phase eine Rolle spielen.
  
1. Verschieben von Produktivitätsarbeitslasten in SaaS
    
    Für Produktivitätsarbeitslasten, die aktuell lokal sind oder die lokal bleiben müssen, ermöglichen Hybridszenarien, sie mit ihren Cloudgegenstücken zu kombinieren.
    
2. Entwickeln von neuen und modernen Anwendungen in Azure PaaS
    
    Azure PaaS-Hybridanwendungen können lokale Server- oder Speicherressourcen sicher nutzen.
    
3. Verschieben von vorhandenen Anwendungen in Azure IaaS
    
    Für Aufnehmen-und-Verlagern- sowie Erstellen-in-der-Cloud-Szenarien bieten serverbasierte Anwendungen, die auf virtuellen Azure-Computern ausgeführt werden, einfache Bereitstellung und Skalierung.
    
## See Also

#### 

[Microsoft Hybrid Cloud für Enterprise-Architekten](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
#### 

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)

