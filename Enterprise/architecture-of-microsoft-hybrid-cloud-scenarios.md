---
title: Architektur von Microsoft Hybrid Cloud-Szenarien
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
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: 'Zusammenfassung: Informationen über die Architektur von Microsoft-Hybridcloudangeboten.'
ms.openlocfilehash: 74fc046d1f60b29338e7f12184dec018538ba9da
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123392"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Architektur von Microsoft Hybrid Cloud-Szenarien

 **Zusammenfassung:** Informationen über die Architektur von Microsoft-Hybridcloudangeboten.
  
Verwenden Sie eine architekturbezogene Herangehensweise, wenn Sie Hybridcloudszenarien mit Microsoft-Clouddiensten und -plattformen planen und implementieren.
  
**Abbildung 1: Microsoft-Hybridcloudstack**

![Microsoft Hybridcloudstack](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
Abbildung 1 zeigt den Microsoft-Hybridcloudstack und die Schicht, die lokal, Netzwerk, Identität, Apps, Szenarien und die Kategorie des Clouddiensts (Microsoft SaaS, Azure PaaS und Azure PaaS) enthält.
  
Ebene der Apps und Szenarien hat die bestimmte Hybrid-Cloud-Szenarien, die detailliert sind in den Artikeln dieses Modells. Die Identität, Netzwerk und lokalen Ebenen können gemeinsam die Kategorien von Cloud-Dienst (SaaS, PaaS oder PaaS) sein.
  
- Lokal
    
    Lokale Infrastruktur für Hybridszenarien kann Server für SharePoint, Exchange, Skype for Business und Branchenanwendungen enthalten. Des weiteren kann sie Datenspeicher (Datenbanken, Listen, Dateien) enthalten. Ohne ExpressRoute-Verbindungen muss der Zugriff auf die lokalen Datenspeicher über einen Reverseproxy oder durch Zugriff auf den Server oder die Daten in der DMZ oder dem Extranet gewährt werden.
    
- Netzwerk
    
    Es gibt zwei Optionen für die Verbindung mit Microsoft-Cloud-Plattformen und Dienste: Ihre vorhandenen Internet Pipe und ExpressRoute. Verwenden Sie eine ExpressRoute-Verbindung, wenn vorhersehbare Leistung wichtig ist. Eine Verbindung als ExpressRoute können Sie direkt an Microsoft SaaS-Dienste (Office 365 und Dynamics 365), Azure PaaS-Dienste und Azure IaaS-Dienste eine Verbindung herstellen.
    
- Identität
    
    Je nach Microsoft-Cloudplattform gibt es zwei Möglichkeiten für die Cloudidentitätsinfrastruktur. Integrieren Sie für SaaS und Azure PaaS Ihre lokale Identitätsinfrastruktur in Azure AD oder einen Verbund mit Ihrer lokalen Infrastruktur oder Drittanbieter-Identitätsanbietern. Für in Azure ausgeführte virtuelle Computer können Sie Ihre lokale Identitätsinfrastruktur, z. B. Windows Server AD, auf virtuelle Netzwerke (VNets) erweitern, in denen sich ihre virtuellen Computer befinden.
    
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

