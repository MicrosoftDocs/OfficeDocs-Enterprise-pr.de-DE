---
title: Hybrid Cloud-Szenarien für Azure PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Zusammenfassung: Grundlegende Informationen zur Hybrid-Architektur und -szenarien für PaaS-basierte Cloudangebote von Microsoft in Azure.'
ms.openlocfilehash: e60bc92eed45e5d29fe0be80320dee65b8325028
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915010"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Hybrid Cloud-Szenarien für Azure PaaS

 **Zusammenfassung:** Grundlegende Informationen zur Hybrid-Architektur und -szenarien für PaaS-basierte Cloudangebote von Microsoft in Azure.
  
Kombinieren Sie lokale Daten oder Computingressourcen mit neuen oder konvertierten Anwendungen, die in Azure PaaS ausgeführt werden und Cloudleistung, -zuverlässigkeit und -skalierung nutzen sowie bessere Unterstützung für mobile Benutzer bieten können. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Architektur für Azure PaaS-Hybridszenario

Abbildung 1 zeigt die Architektur der PaaS-basierten Hybridszenarien von Microsoft in Azure.
  
**Abbildung 1: Microsoft PaaS-basierte Hybridszenarien in Azure**

![Microsoft PaaS-basierte Hybridszenarien in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
Für jede Schicht der Architektur:
  
- Apps und Szenarien
    
    Eine hybride PaaS-Anwendung wird in Azure ausgeführt und nutzt lokale Compute- oder Speicherressourcen.
    
- Identität
    
    Besteht entweder aus einer Verzeichnissynchronisierung oder aus einem Partnerverbund mit einem Drittanbieter-Identitätsanbieter.
    
- Netzwerk
    
    Besteht aus Ihrem vorhandenen Internetzugang oder einer ExpressRoute-Verbindung mit öffentlichem Peering zu Azure PaaS. Sie müssen eine Möglichkeit für die Azure PaaS-Anwendung für den Zugriff auf die lokale Compute- oder Speicherressource hinzufügen.
    
- Lokal
    
    Besteht aus der Identitäts- und Sicherheitsinfrastruktur sowie vorhandenen branchenspezifischen Anwendungen oder Datenbankserver, auf die eine Azure PaaS-Anwendung sicher zugreifen kann.
    
## <a name="azure-paas-hybrid-application"></a>Azure PaaS-Hybridanwendung

Abbildung 2 zeigt die Konfiguration einer Hybridanwendung, die in Azure ausgeführt wird.
  
**Abbildung 2: Azure PaaS-basierte Hybridanwendung**

![Azure PaaS-basierte Hybridanwendung](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
In Abbildung 2 werden Speicher oder Apps auf Servern und in einer DMZ mit einem Proxyserver in einem lokalen Netzwerk gehostet. Das Netzwerk ist über das Internet oder eine ExpressRoute-Verbindung mit PaaS Azure-Diensten verbunden.
  
Eine Organisation kann seine Compute- oder Speicherressourcen wie folgt für die Azure PaaS-Hybridanwendung zugänglich machen:
  
- Durch Hosten der Ressource auf Servern in der DMZ
    
- Durch Hosten eines Reverseproxyservers in der DMZ, der authentifizierte, eingehende, HTTPS-basierte Anforderungen an die Ressource zulässt, die sich im lokalen System befindet
    
Die Azure-App kann Anmeldeinformationen verwenden von:
  
- Azure AD, das mit Ihrem lokalen Identitätsanbieter, z. B. Windows Server Active Directory, synchronisiert werden kann
    
- Einem Drittanbieter-Identitätsanbieter
    
### <a name="example-azure-paas-hybrid-application"></a>Azure PaaS-Hybridanwendung als Beispiel

Abbildung 3 zeigt ein Beispiel für eine Hybridanwendung, die in Azure ausgeführt wird.
  
**Abbildung 3: Ein Beispiel für eine Azure PaaS-basierte Hybridanwendung**

![Ein Beispiel für eine Azure PaaS-basierte Hybridanwendung](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
In Abbildung 3 wird eine Branchenanwendung in einem lokalen Netzwerk gehostet. Azure PaaS hostet eine benutzerdefinierte mobile App. Ein Smartphone im Internet greift auf die benutzerdefinierte mobile App in Azure zu, von wo wiederum Datenanforderungen an die lokale Branchenanwendung gesendet werden.
  
Diese Azure PaaS-Beispielhybridanwendung ist eine benutzerdefinierte mobile App, die aktuelle Kontaktinformationen zu Mitarbeitern bereitstellt. Das End-to-End-Hybridszenario besteht aus:
  
- Einer Smartphone-App, die überprüfte lokale Anmeldeinformationen erfordert, damit sie ausgeführt werden kann
    
- Einer benutzerdefinierten mobilen App, die in Azure PaaS ausgeführt wird und Informationen zu bestimmten Mitarbeitern anhand von Abfragen anfordert, die von der Smartphone-App eines Benutzers stammen
    
- Einem Reverseproxyserver in der DMZ, der die benutzerdefinierte mobile App überprüft und die Anforderung weiterleitet
    
- Einer Branchenanwendungs-Serverfarm, die die Kontaktanforderung entsprechend den Berechtigungen verarbeitet, die das Konto des Benutzers hat
    
Da der lokale Identitätsanbieter mit Azure Active Directory synchronisiert wurde, können sowohl die benutzerdefinierte mobile App als auch die Branchen-App den Kontonamen des anfordernden Benutzers überprüfen.
  
## <a name="stretch-database-with-sql-server-2016"></a>Stretch-Datenbank mit SQL Server 2016

Stretch-Datenbank ist ein Feature von SQL Server-2016, das es Ihnen ermöglicht, archivierte („kalte“) Daten, z. B. abgeschlossene Geschäftsdaten in einer umfangreichen Tabelle, die Kundenbestellinformationen enthält, transparent und sicher in eine SQL Stretch-Datenbank in Azure zu verschieben.
  
Wird der Inhalt einer SQL Server-Instanz, einer Datenbank oder sogar einer einzelnen Tabelle in einer Stretch-Datenbank verwendet, ist er eine Kombination aus lokalen Daten auf dem Server mit SQL Server 2016 und Remotedaten in Azure. Daten, die zur Verwendung in einer Stretch-Datenbank auswählbar geworden sind, werden von SQL Server 2016 automatisch in Azure verschoben.
  
In Abbildung 4 wird Stretch-Datenbank mit SQL Server 2016 dargestellt.
  
**Abbildung 4: Stretch-Datenbank mit SQL Server 2016**

![Stretch-Datenbank mit SQL Server 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-SQL.png)
  
In Abbildung 4 wird ein Server mit SQL Server 2016 mit einer kleinen lokalen Datenbank in einem lokalen Netzwerk gehostet. Azure PaaS hostet eine Instanz von Azure SQL Server Stretch-Datenbank mit dem gestreckten Teil der Datenbank. T-SQL-Abfragen von lokalen Benutzern, die an den lokalen SQL-Server gesendet werden, werden sicher an die Azure SQL Stretch-Datenbank weitergeleitet, welche die Ergebnisse für den anfordernden Benutzer zurückgibt.
  
  

Benutzerabfragen, die Verlaufsdaten enthalten, werden transparent an die Azure SQL Stretch-Datenbank weitergeleitet. Die Abfragen müssen nicht neu geschrieben werden, obwohl die Tabelle gestreckt ist. 


  
Stretch-Datenbank stellt eine kostengünstige Möglichkeit für langfristige Speicherung und transparenten Zugriff auf Verlaufsdaten. Außerdem können hiermit Leistungs- und Verfügbarkeitsprobleme behoben werden, die auftreten, wenn die Tabellen sehr umfangreich sind.
  
Weitere Informationen finden Sie unter [Stretch-Datenbank](https://msdn.microsoft.com/library/dn935011.aspx).
  
## <a name="see-also"></a>Siehe auch

[Microsoft Hybrid Cloud für Enterprise-Architekten](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)



