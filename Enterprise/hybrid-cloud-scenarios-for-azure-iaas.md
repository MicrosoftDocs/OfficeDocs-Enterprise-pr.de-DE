---
title: "Hybrid Cloud-Szenarien für Azure IaaS"
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
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "Zusammenfassung: Grundlegendes zu den Hybrid-Architektur und Szenarien für Microsoft Infrastruktur als Dienst (IaaS)-Cloud-angeboten in Azure basiert."
ms.openlocfilehash: 66024c708cb4fbc904de18f27077871d52f0e70c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Hybrid Cloud-Szenarien für Azure IaaS

 **Zusammenfassung:** Grundlegendes zur Hybrid-Architektur und Szenarien für die Microsoft-Infrastruktur als Dienst (IaaS)-Cloud-angeboten in Azure basiert.
  
Erweitern Sie Ihre lokale Computing- und Identitätsinfrastruktur in die Cloud, indem Sie IT-Arbeitslasten hosten, die in standortübergreifenden virtuellen Azure-Netzwerken (VNets) ausgeführt werden.  
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Architektur für Azure IaaS-Hybridszenario

Abbildung 1 zeigt die Architektur der IaaS-basierten Hybridszenarien von Microsoft in Azure.
  
**Abbildung 1: Microsoft IaaS-basierte Hybrid-Szenarien in Azure**

![Microsoft IaaS-basierte Hybridszenarien in Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS.png)
  
Für jede Schicht der Architektur:
  
- Apps und Szenarien
    
    Eine IT-Arbeitslast ist üblicherweise eine mehrstufige hochverfügbare Anwendung, die aus virtuellen Azure-Computern besteht.
    
- Identität
    
    Fügen Sie, um lokale Authentifizierung zu ermöglichen, Identitätsserver, etwa Windows Server Active Directory-Domänencontroller, zur Gruppe der Server hinzu, die in Azure VNets (virtuelle Netzwerke) ausgeführt werden.
    
- Netzwerk
    
    Verwenden Sie entweder eine VPN-Verbindung zwischen Standorten über das Internet oder eine ExpressRoute-Verbindung mit privatem Peering zu Azure IaaS.
    
- Lokal
    
    Enthält Identitätsserver, die mit in Azure ausgeführten Identitätsservern synchronisiert werden. Kann auch Ressourcen enthalten, auf die in Azure ausgeführte virtuelle Computer zugreifen können, z. B. Speicher und Systemverwaltungsinfrastruktur.
    
## <a name="dirsync-server-for-office-365"></a>DirSync-Server für Office 365

Ein Beispiel für die Ausweitung Ihrer Computing- und Identitätsinfrastruktur auf die Cloud ist die Ausführung Ihres Verzeichnissynchronisierungsservers (DirSync-Server) in einem Azure-VNet wie in Abbildung 2 dargestellt.
  
**Abbildung 2: Dirsync-Server für Office 365 in Azure IaaS**

![DirSync-Server für Office 365 in Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_DirSync.png)
  
In Abbildung 2 hostet einer lokalen Netzwerk eine Windows Azure AD-Infrastruktur mit einer Proxyserver und Router den Rand. Der Router eine Verbindung mit einer Azure Gateway am Rand eines Azure VNet mit einer Standort-zu-Standort-VPN- oder ExpressRoute-Verbindung. Innerhalb der VNet führt ein Dirsync-Server Azure Active Directory verbinden.
  
Ein DirSync-Server für Office 365 synchronisiert die Liste der Konten in Windows Server AD mit dem Azure AD-Mandanten eines Office 365-Abonnements.
  
DirSync-Server sind Windows-basierte Server, auf denen Azure AD Connect ausgeführt wird. Wenn Sie Ihren DirSync-Server in einem virtuellen Netzwerk (VNet) in Azure IaaS bereitstellen, ermöglicht das eine beschleunigte Ressourcenbereitstellung und eine Reduzierung der Anzahl lokaler Server in Ihrer Organisation.
  
Der DirSync-Server fragt regelmäßig Änderungen von Windows Server AD ab und synchronisiert diese Änderungen mit dem Office 365-Abonnement
  
Weitere Informationen finden Sie unter [Bereitstellen von Office 365 DirSync in Azure](https://technet.microsoft.com/library/dn635310.aspx).
  
## <a name="line-of-business-lob-application"></a>Branchenanwendung

Abbildung 3 zeigt die Konfiguration einer serverbasierten Branchenanwendung, die in Azure IaaS ausgeführt wird.
  
**Abbildung 3: LOB-Anwendung in Azure IaaS**

![Serverbasierte Branchenanwendung in Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_Ex.png)
  
In Abbildung 3 sehen Sie ein lokales Netzwerk, das eine Identitätsinfrastruktur und Benutzer hostet. Das Netzwerk ist über ein Standort-zu-Standort-VPN oder eine ExpressRoute-Verbindung mit einem Azure IaaS-Gateway verbunden. Azure IaaS hostet ein virtuelles Netzwerk mit den Servern der Branchenanwendung.
  
Sie können erstellen LOB-Anwendungen, die auf Azure VMs, die sich auf Subnetze mit einer Azure-VNet in einer Azure-Rechenzentrum (auch bekannt als Speicherort) befinden.
  
Da Sie im Grundsatz Ihre lokale Infrastruktur auf Azure erweitern, müssen Sie Ihren virtuellen Netzwerken (VNets) einen eindeutigen privaten Adressraum zuweisen und Ihre lokalen Routingtabellen aktualisieren, damit Erreichbarkeit jedes VNets sichergestellt ist.
  
Sobald es Verbindungen mit diesen virtuellen Computern gibt, können diese über Remotedesktopverbindungen oder mit Ihrer Systemverwaltungssoftware genau so verwaltet werden wie Ihre lokalen Server.
  
Durch Konfigurieren von öffentlich verfügbar gemachten Ports können auch mobile oder Remotebenutzer über das Internet auf diese virtuellen Computer zugreifen.
  
Eine Konfiguration Nachweis der Machbarkeit finden Sie unter [simulierten standortübergreifenden virtuelles Netzwerk in Azure](simulated-cross-premises-virtual-network-in-azure.md).
  
Attribute von Branchenanwendungen, die auf virtuellen Azure-Computern gehostet werden, sind folgende:
  
- Mehrere Stufen
    
    Für normale Branchenanwendungen wird ein mehrstufiger Ansatz verwendet. Gruppen von Servern erledigen Identitäts-, Datenbank-, Anwendungs- und Logikverarbeitung und stellen Front-End-Webserver für Mitarbeiter- oder Kundenzugriff bereit.  
    
- Hohe Verfügbarkeit
    
    Übliche Branchenanwendungen bieten Hochverfügbarkeit, indem auf jeder Stufe mehrere Server verwendet werden. Azure IaaS bietet eine SLA von 99,9 % zu Betriebszeit für Server in Azure-Verfügbarkeitssets.  
    
- Lastverteilung
    
    Um die Last des Netzwerkdatenverkehrs auf mehrere Server auf einer Schicht zu verteilen, können Sie einen internetbezogenen oder einen internen Azure-Lastenausgleich (Load Balancer) verwenden. Alternativ können Sie ein dediziertes Lastenausgleichsgerät verwenden, das aus dem Azure Marketplace verfügbar ist.
    
- Sicherheit
    
    Um Server vor unerwünschtem eingehenden Datenverkehr aus dem Internet zu schützen, können Sie Azure-Netzwerksicherheitsgruppen verwenden. Sie können zulässigen oder zurückgewiesenen Datenverkehr für ein Subnetz oder die Netzwerkschnittstelle eines einzelnen virtuellen Computers definieren.
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>SharePoint Server 2016-Farm in Azure

Ein Beispiel für eine hoch verfügbare Multi-Tier-Branchenanwendung in Azure ist eine SharePoint Server 2016-Farm wie in Abbildung 4 dargestellt.
  
**Abbildung 4: Eine hohe Verfügbarkeit 2016 für SharePoint Server-Farm in Azure IaaS**

![Hoch verfügbare SharePoint Server 2016-Farm in Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_SP2016.png)
  
In Abbildung 4 hostet ein lokales Netzwerk eine Identitätsinfrastruktur und Benutzer. Das Netzwerk ist über ein Standort-zu-Standort-VPN oder eine ExpressRoute-Verbindung mit einem Azure IaaS-Gateway verbunden. Das Azure-VNet enthält die Server der SharePoint Server 2016-Farm. Dabei sind die Front-End-Server, die Anwendungsserver, der SQL Server-Cluster und die Domänencontroller jeweils auf unterschiedlichen Stufen (Tiers) platziert.
  
In einer solchen Konfiguration haben die Branchenanwendungen in Azure die folgenden Attribute:  
  
- Stufen
    
    Server mit verschiedenen Rollen innerhalb der Farm Erstellen der Ebenen und jede Ebene hat ein eigenen Subnetz.
    
- Hohe Verfügbarkeit
    
    Hohe Verfügbarkeit wird erreicht, indem Sie auf jeder Stufe mindestens zwei Server implementieren und alle Server einer Stufe in derselben Verfügbarkeitsgruppe platzieren.
    
- Lastverteilung
    
    Die internen Load Balancer in Azure verteilen den eingehenden Clientwebverkehr an die Front-End-Server (WEB1 und WEB2) und die Listener-IP-Adresse des SQL Server-Clusters (SQL1, SQL2 und MN1).
    
- Sicherheit
    
    Mithilfe von Netzwerksicherheitsgruppen können Sie für jedes Subnetz festlegen, welcher eingehende und ausgehende Datenverkehr erlaubt ist.
    
Gehen Sie für eine erfolgreiche Implementierung wie folgt vor:
  
1. Evaluieren und experimentieren
    
    Finden Sie unter [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) zu verstehen, die Vorteile der Ausführung von SharePoint Server 2016 in Azure.
    
    Finden Sie unter [Intranet SharePoint Server 2016 in Azure Test-/Umgebung](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) zum Erstellen einer simulierten Test-/-Umgebung
    
2. Entwerfen
    
    Finden Sie unter [Entwerfen einer SharePoint Server 2016 Farm in Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) , um einen Vorgang zum Bestimmen des Satz von Azure IaaS-Netzwerke, Compute und Storage-Elemente zum Hosten Ihrer Farm und ihrer Einstellungen für die schrittweise.
    
3. Bereitstellen
    
    Finden Sie unter [Bereitstellen von SharePoint Server 2016 mit SQL Server AlwaysOn Availability Groups in Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) schrittweise durchlaufen die End-to-End-Konfiguration der Farm, die hohe Verfügbarkeit in fünf Phasen.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identitätsverbund für Office 365 in Azure

Ein weiteres Beispiel für eine mehrstufige, hochverfügbar LOB-Anwendung in Azure ist Identitätsverbund für Office 365.
  
**Abbildung 5: Eine hohe Verfügbarkeit Identitätsverbund-Infrastruktur für Office 365 in Azure IaaS**

![Die Endkonfiguration für die hochverfügbare Office 365-Verbundauthentifizierungsinfrastruktur in Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_ADFS.png)
  
In Abbildung 5 hostet einer lokalen Netzwerk eine Identitätsinfrastruktur und Benutzer. Es ist mit einem Azure IaaS-Gateway mit einer Standort-zu-Standort-VPN- oder ExpressRoute Verbindung verbunden. Der Azure-VNet enthält Web Proxy-Server, Active Directory-Verbunddienste (AD FS) Server und Windows Server Active Directory (AD)-Domänencontroller.
  
In einer solchen Konfiguration haben die Branchenanwendungen in Azure die folgenden Attribute: 
  
- **Ebenen:** Ebenen für Web-Proxyserver, AD FS-Server und Windows Server Active Directory-Domänencontroller sind vorhanden.
    
- **Verteilung laden:** Ein externe Azure System zum Lastenausgleich verteilt die eingehenden Clientanforderungen für die Authentifizierung an der Webproxys und eine interne Azure System zum Lastenausgleich verteilt authentifizierungsanforderungen an die AD FS-Server.
    
Gehen Sie für eine erfolgreiche Implementierung wie folgt vor:
  
1. Evaluieren und experimentieren
    
    Finden Sie unter [Federated Identität für die Office 365-Umgebung](federated-identity-for-your-office-365-dev-test-environment.md) Test-/eine simulierten Test-/Umgebung für Verbundauthentifizierung mit Office 365 erstellen.
    
2. Bereitstellen
    
    Finden Sie unter [Deploy hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) schrittweise durchlaufen die End-to-End-Konfiguration die hohe Verfügbarkeit AD FS-Infrastruktur in fünf Phasen.
    
Weitere Informationsquellen:
  
- [Architektur von Cloud-Hybridumgebungen](https://gallery.technet.microsoft.com/Architecting-Hybrid-Cloud-a7dc9f24/file/147475/1/Architecting%20Hybrid%20Cloud%20Environments%20V1.docx)
    
- [Erweitern Sie dem Kurs Cloud Microsoft Virtual Academy Your Datacenter](https://mva.microsoft.com/en-US/training-courses/extend-your-datacenter-to-the-cloud-13908?l=7fG3tAouB_7100115881)
    
- [Entwerfen und Erstellen einer LOB-Anwendung in Azure](https://techcommunity.microsoft.com/t5/CAAB-Cloud-Adoption-Advisory/EXTRA-November-2016-Webinar/m-p/30058#M41)
    
## <a name="see-also"></a>Weitere Artikel

[Microsoft Hybrid Cloud für Enterprise-Architekten](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)



