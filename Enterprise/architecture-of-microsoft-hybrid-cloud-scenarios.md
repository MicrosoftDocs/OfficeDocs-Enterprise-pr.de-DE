---
title: Architektur von Microsoft Hybrid Cloud-Szenarien
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: 'Zusammenfassung: Informationen über die Architektur von Microsoft-Hybridcloudangeboten.'
ms.openlocfilehash: 513e45629a7092803cc644241d84985a37e43876
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068321"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Architektur von Microsoft Hybrid Cloud-Szenarien

 **Zusammenfassung:** Informationen über die Architektur von Microsoft-Hybridcloudangeboten.
  
Verwenden Sie eine architekturbezogene Herangehensweise, wenn Sie Hybridcloudszenarien mit Microsoft-Clouddiensten und -plattformen planen und implementieren.
  
**Abbildung 1: Microsoft-Hybridcloudstack**

![Microsoft Hybridcloudstack](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
Abbildung 1 zeigt den Microsoft-Hybridcloudstack und die Schicht, die lokal, Netzwerk, Identität, Apps, Szenarien und die Kategorie des Clouddiensts (Microsoft SaaS, Azure PaaS und Azure PaaS) enthält.
  
Die Ebene apps und Szenarien hat die spezifischen Hybrid Cloud-Szenarien, die in den zusätzlichen Artikeln dieses Modells ausführlich erläutert werden. Die Schichten „Identität", „Netzwerk" und „Lokal" können sich über die Kategorien des Clouddiensts (SaaS, PaaS oder PaaS) erstrecken.
  
- Lokal
    
    Lokale Infrastruktur für Hybridszenarien kann Server für SharePoint, Exchange, Skype for Business und Branchenanwendungen enthalten. Des weiteren kann sie Datenspeicher (Datenbanken, Listen, Dateien) enthalten. Ohne ExpressRoute-Verbindungen muss der Zugriff auf die lokalen Datenspeicher über einen Reverseproxy oder durch Zugriff auf den Server oder die Daten in der DMZ oder dem Extranet gewährt werden.
    
- Netzwerk
    
    Es gibt zwei Optionen für die Verbindung zu Microsoft-Cloudplattformen und -Diensten: der vorhandene Internetzugang oder ExpressRoute. Verwenden Sie eine ExpressRoute-Verbindung, wenn vorhersehbare Leistung wichtig ist. Sie können eine Express Route-Verbindung verwenden, um eine direkte Verbindung zu Microsoft Saas-Diensten (Office 365 und Dynamics 365), Azure PaaS-Diensten und Azure IaaS-Diensten herzustellen.
    
- Identität
    
    Je nach Microsoft-Cloudplattform gibt es zwei Möglichkeiten für die Cloudidentitätsinfrastruktur. Integrieren Sie für SaaS und Azure PaaS Ihre lokale Identitätsinfrastruktur in Azure AD oder einen Verbund mit Ihrer lokalen Infrastruktur oder Drittanbieter-Identitätsanbietern. Für VMS, die in Azure laufen, können Sie Ihre lokale Identitätsinfrastruktur, wie etwa Active Directory-Domänendienste (AD DS), auf die virtuellen Netzwerke (VNets) erweitern, in denen sich ihre VMs befinden.
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>Hybridcloudszenarien für den dreiphasigen Prozess der Cloudeinführung

Viele Unternehmen, so auch Microsoft, verwenden eine dreiphasige Herangehensweise zur Einführung der Cloud. Hybridcloudszenarien können in jeder Phase eine Rolle spielen.
  
1. Verschieben von Produktivitätsarbeitslasten in SaaS
    
    Für Produktivitätsarbeitslasten, die aktuell lokal sind oder die lokal bleiben müssen, ermöglichen Hybridszenarien, sie mit ihren Cloudgegenstücken zu kombinieren.
    
2. Entwickeln von neuen und modernen Anwendungen in Azure PaaS
    
    Azure PaaS-Hybridanwendungen können lokale Server- oder Speicherressourcen sicher nutzen.
    
3. Verschieben von vorhandenen Anwendungen in Azure IaaS
    
    Für Aufnehmen-und-Verlagern- sowie Erstellen-in-der-Cloud-Szenarien bieten serverbasierte Anwendungen, die auf virtuellen Azure-Computern ausgeführt werden, einfache Bereitstellung und Skalierung.
    
## <a name="see-also"></a>Siehe auch

[Microsoft Hybrid Cloud für Enterprise-Architekten](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

