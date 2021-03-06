---
title: "Hybrid Cloud-Übersicht"
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
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: "Zusammenfassung: Grundlegendes zur Definition und Elementen der Microsoft Hybrid Cloud."
---

# Hybrid Cloud-Übersicht

 **Zusammenfassung:** Grundlegendes zur Definition und Elementen der Microsoft Hybrid Cloud.
  
Für Hybrid Cloud werden Compute- oder Speicherressourcen in Ihrem lokalen Netzwerk und in der Cloud verwendet. Sie können Hybrid Cloud als Weg nutzen, um Ihr Unternehmen und dessen IT-Anforderungen in die Cloud zu migrieren oder Cloudplattformen und -dienste als Bestandteil Ihrer IT-Gesamtstrategie mit Ihrer vorhandenen lokalen Infrastruktur zu kombinieren.
  
## Microsoft Hybrid Cloud

Microsoft Hybrid Cloud besteht aus Geschäftsszenarien, in denen eine Microsoft-Cloudplattform mit einer lokalen Komponente kombiniert ist, also beispielsweise: 
  
- Abrufen von Suchergebnissen aus Inhalten sowohl in einer lokalen SharePoint-Farm als auch in SharePoint Online in Office 365
    
- Eine mobile App, die in Azure ausgeführt wird und einen lokalen Datenspeicher abfragt
    
- Eine Intranet-IT-Arbeitslast, die auf virtuellen Azure-Computern ausgeführt wird
    
**Abbildung 1: Komponenten der Microsoft Hybrid Cloud**

![Komponenten der Microsoft-Hybridcloud](images/65dfb1c6-26be-45c2-ab3d-6d1cd4a0f823.png)
  
Abbildung 1 zeigt die Komponenten der Microsoft Hybrid Cloud, vom lokalen Netzwerk bis zum Satz aus Office 365-, Azure PaaS- und Azure IaaS-Diensten, die über das Internet oder eine ExpressRoute-Verbindung verfügbar sind.
  
Da Microsoft die umfassendste auf dem Markt erhältliche Cloudlösung hat - einschließlich Software as a Service (SaaS), Platform as a Service (PaaS) und Infrastructure as a Service (IaaS) - haben Sie folgende Möglichkeiten:
  
- Nutzen Ihrer vorhandenen lokalen Investitionen, wenn Sie Arbeitslasten und Anwendungen in die Cloud migrieren
    
- Einbinden von Hybrid Cloud-Szenarien in Ihre langfristigen IT-Pläne, etwa wenn es wegen Vorschriften oder Richtlinien nicht zulässig ist, bestimmte Daten oder Arbeitslasten in die Cloud zu verschieben
    
- Erstellen von zusätzlichen Hybridszenarien, die mehrere Microsoft-Clouddienste und -plattformen umfassen
    
Szenarien für Hybrid Cloud mit Microsoft-Clouddiensten unterscheiden sich je nach Plattform.
  
- SaaS
    
    Microsoft SaaS-Dienste umfassen Office 365, Microsoft Intune und Microsoft Dynamics 365. In Hybridcloudszenarien mit Microsoft SaaS werden diese Dienste mit lokalen Diensten und Anwendungen kombiniert. Beispielsweise kann Exchange Online, in Office 365 ausgeführt, in lokale Skype for Business 2015-Bereitstellungen integriert werden.
    
- Azure PaaS
    
    Microsoft Azure PaaS-Dienste ermöglichen Ihnen das Erstellen cloudbasierter Anwendungen. Hybridcloudszenarien mit Azure PaaS-Diensten kombinieren eine Azure PaaS-App mit lokalen Ressourcen oder Anwendungen. Beispielsweise könnte eine Azure PaaS-App sicher die Informationen aus einem lokalen Datenspeicher abfragen, die Benutzern der mobilen App angezeigt werden müssen.
    
- Azure IaaS
    
    Mit Azure IaaS-Diensten können Sie serverbasierte IT-Arbeitslasten in der Cloud, statt im lokalen Rechenzentrum, erstellen und ausführen. Hybridcloudszenarien mit Azure IaaS-Diensten bestehen in der Regel aus einer IT-Arbeitslast, die auf virtuellen Computern mit transparenter Verbindung zum lokalen Netzwerk ausgeführt wird. Lokale Benutzer sehen den Unterschied nicht.
    
## Elemente von Hybrid Cloud

Sie müssen die folgenden Elemente berücksichtigen, wenn Sie Hybridcloudszenarien mit Microsoft-Cloudplattformen und -diensten planen und implementieren.
  
- Netzwerk
    
    Netzwerk für Hybridcloudszenarien beinhaltet die Verbindung mit Microsoft-Cloudplattformen und -diensten sowie ausreichend Bandbreite, um unter Spitzenlast leistungsfähig zu bleiben. Weitere Informationen finden Sie unter [Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md).
    
- Identität
    
    Identität für SaaS- und Azure PaaS-Hybridszenarien kann Azure AD als allgemeinen Identitätsanbieter beinhalten, der mit Ihrem lokalen Windows Server AD synchronisiert oder mit Windows Server AD oder einem anderen Identitätsanbieter zu einem Verbund kombiniert werden kann. Sie können auch Ihre lokale Identitätsinfrastruktur auf Azure IaaS erweitern. Weitere Informationen finden Sie unter [Microsoft-Cloud-Identität für Enterprise-Architekten](microsoft-cloud-identity-for-enterprise-architects.md).
    
- Sicherheit
    
    Sicherheit für Hybridcloudszenarien umfasst Schutz und Verwaltung Ihrer Identitäten, Schutz von Daten, Verwaltung mit Administratorrechten, Berücksichtigung von Bedrohungen und die Implementierung von Governance und Sicherheitsrichtlinien. Weitere Informationen finden Sie unter [Microsoft Cloudsicherheit für Enterprise-Architekten](https://technet.microsoft.com/library/dn919927.aspx#security).
    
- Verwaltung
    
    Verwaltung für Hybridcloudszenarien umfasst die Möglichkeit, Einstellungen, Daten, Konten, Richtlinien und Berechtigungen zu verwalten sowie den gegenwärtigen Status der Elemente aus dem Szenario und dessen Leistung zu überwachen. Sie können auch das gleiche Toolset, etwa Systems Management Server, für die Verwaltung von virtuellen Computern in Azure IaaS verwenden.
    
## See Also

#### 

[Microsoft Hybrid Cloud für Enterprise-Architekten](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
#### 

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)

