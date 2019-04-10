---
title: Hybrid Cloud-Übersicht
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: 'Zusammenfassung: Grundlegendes zur Definition und Elementen der Microsoft Hybrid Cloud.'
ms.openlocfilehash: c048cfeb840bbb03b1886c7053603cfdc84f37ab
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741431"
---
# <a name="hybrid-cloud-overview"></a>Hybrid Cloud-Übersicht

 **Zusammenfassung:** Grundlegendes zur Definition und Elementen der Microsoft Hybrid Cloud.
  
Für Hybrid Cloud werden Compute- oder Speicherressourcen in Ihrem lokalen Netzwerk und in der Cloud verwendet. Sie können Hybrid Cloud als Weg nutzen, um Ihr Unternehmen und dessen IT-Anforderungen in die Cloud zu migrieren oder Cloudplattformen und -dienste als Bestandteil Ihrer IT-Gesamtstrategie mit Ihrer vorhandenen lokalen Infrastruktur zu kombinieren.
  
## <a name="microsoft-hybrid-cloud"></a>Microsoft Hybrid Cloud

Microsoft Hybrid Cloud besteht aus Geschäftsszenarien, in denen eine Microsoft-Cloudplattform mit einer lokalen Komponente kombiniert ist, also beispielsweise:  
  
- Abrufen von Suchergebnissen aus Inhalten sowohl in einer lokalen SharePoint-Farm als auch in SharePoint Online in Office 365
    
- Eine mobile App, die in Azure ausgeführt wird und einen lokalen Datenspeicher abfragt
    
- Eine Intranet-IT-Arbeitslast, die auf virtuellen Azure-Computern ausgeführt wird
    
**Abbildung 1: Komponenten der Microsoft Hybrid Cloud**

![Komponenten der Microsoft-Hybridcloud](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
Abbildung 1 zeigt die Komponenten der Microsoft Hybrid Cloud, vom lokalen Netzwerk bis zum Satz aus Office 365-, Azure PaaS- und Azure IaaS-Diensten, die über das Internet oder eine ExpressRoute-Verbindung verfügbar sind.
  
Da Microsoft die umfassendste auf dem Markt erhältliche Cloudlösung hat – einschließlich Software as a Service (SaaS), Platform as a Service (PaaS) und Infrastructure as a Service (IaaS) – haben Sie folgende Möglichkeiten:
  
- Nutzen Ihrer vorhandenen lokalen Investitionen, wenn Sie Arbeitslasten und Anwendungen in die Cloud migrieren
    
- Einbinden von Hybrid Cloud-Szenarien in Ihre langfristigen IT-Pläne, etwa wenn es wegen Vorschriften oder Richtlinien nicht zulässig ist, bestimmte Daten oder Arbeitslasten in die Cloud zu verschieben
    
- Erstellen von zusätzlichen Hybridszenarien, die mehrere Microsoft-Clouddienste und -plattformen umfassen
    
Szenarien für Hybrid Cloud mit Microsoft-Clouddiensten unterscheiden sich je nach Plattform.
  
- SaaS
    
    Microsoft SaaS-Dienste umfassen Office 365, Microsoft Intune und Microsoft Dynamics 365. In Hybridcloudszenarien mit Microsoft SaaS werden diese Dienste mit lokalen Diensten und Anwendungen kombiniert. Beispielsweise kann Exchange Online mit in Office 365 mit Skype for Business 2019 integriert werden, das lokal bereitgestellt wird.
    
- Azure PaaS
    
    Microsoft Azure PaaS-Dienste ermöglichen Ihnen das Erstellen cloudbasierter Anwendungen. Hybridcloudszenarien mit Azure PaaS-Diensten kombinieren eine Azure PaaS-App mit lokalen Ressourcen oder Anwendungen. Beispielsweise könnte eine Azure PaaS-App sicher die Informationen aus einem lokalen Datenspeicher abfragen, die Benutzern der mobilen App angezeigt werden müssen.
    
- Azure IaaS
    
    Mit Azure IaaS-Diensten können Sie serverbasierte IT-Arbeitslasten in der Cloud, statt im lokalen Rechenzentrum, erstellen und ausführen. Hybridcloudszenarien mit Azure IaaS-Diensten bestehen in der Regel aus einer IT-Arbeitslast, die auf virtuellen Computern mit transparenter Verbindung zum lokalen Netzwerk ausgeführt wird. Lokale Benutzer sehen den Unterschied nicht.
    
## <a name="elements-of-hybrid-cloud"></a>Elemente von Hybrid Cloud

Sie müssen die folgenden Elemente berücksichtigen, wenn Sie Hybridcloudszenarien mit Microsoft-Cloudplattformen und -diensten planen und implementieren.
  
- Netzwerk
    
    Netzwerk für Hybridcloudszenarien beinhaltet die Verbindung mit Microsoft-Cloudplattformen und -diensten sowie ausreichend Bandbreite, um unter Spitzenlast leistungsfähig zu bleiben. Weitere Informationen finden Sie unter [Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md).
    
- Identität
    
    Identity für SaaS-und Azure PaaS-Hybrid Szenarien können Azure AD als allgemeinen Identitätsanbieter, der mit Ihren lokalen Active Directory-Domänendiensten (AD DS) synchronisiert werden kann, oder mit AD DS oder anderen Identitätsanbietern verbunden sein. Sie können auch Ihre lokale Identitätsinfrastruktur auf Azure IaaS erweitern. Weitere Informationen finden Sie unter [Microsoft-Cloud-Identität für Enterprise-Architekten](microsoft-cloud-it-architecture-resources.md#identity).
    
- Sicherheit
    
    Sicherheit für Hybridcloudszenarien umfasst Schutz und Verwaltung Ihrer Identitäten, Schutz von Daten, Verwaltung mit Administratorrechten, Berücksichtigung von Bedrohungen und die Implementierung von Governance und Sicherheitsrichtlinien. Weitere Informationen finden Sie unter [Microsoft Cloudsicherheit für Enterprise-Architekten](microsoft-cloud-it-architecture-resources.md#security).
    
- Verwaltung
    
    Verwaltung für Hybridcloudszenarien umfasst die Möglichkeit, Einstellungen, Daten, Konten, Richtlinien und Berechtigungen zu verwalten sowie den gegenwärtigen Status der Elemente aus dem Szenario und dessen Leistung zu überwachen. Sie können auch das gleiche Toolset, etwa Systems Management Server, für die Verwaltung von virtuellen Computern in Azure IaaS verwenden.
    
## <a name="see-also"></a>Siehe auch

[Microsoft Hybrid Cloud für Enterprise-Architekten](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

