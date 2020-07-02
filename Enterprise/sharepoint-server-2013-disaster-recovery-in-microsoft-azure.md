---
title: SharePoint Server 2013 - Notfallwiederherstellung in Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 'Summary: Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.'
ms.openlocfilehash: 101d87b1a25d2b3ac8a7ae29832e52c805ecdc4c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998167"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>SharePoint Server 2013 – Notfallwiederherstellung in Microsoft Azure

 Mithilfe von Azure können Sie eine Umgebung für die Notfallwiederherstellung für Ihre lokale SharePoint-Farm erstellen. Dieser Artikel beschreibt das Entwerfen und Implementieren dieser Lösung.

 **Schauen Sie sich das Video zur Übersicht über die Notfallwiederherstellung in SharePoint Server 2013 an**.
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.
  
Verwenden Sie diesen Artikel mit dem folgenden Lösungsmodell: **SharePoint-Notfallwiederherstellung in Microsoft Azure**.
  
[![SharePoint-Notfallwiederherstellungsvorgang zu Azure](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Verwenden von Azure Infrastructure Services für Notfallwiederherstellung

Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.
  
Die Verwendung von Azure-Infrastrukturdienste bietet folgende Vorteile:
  
- **Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.
    
- **Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.
    
- **Niedrigere Rechenzentrumsanforderungen** Verwenden Sie Azure-Infrastrukturdienste, statt in ein sekundäres Rechenzentrum in einer anderen Region zu investieren.
    
There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.
  
**Tabelle: Wiederherstellungsumgebungen**

|**Typ der Wiederherstellungsumgebung**|**Beschreibung**|
|:-----|:-----|
|Unmittelbar betriebsbereit  <br/> |Eine vollständig dimensionierte Farm ist bereitgestellt, die aktualisiert und im Standby-Modus ausgeführt wird.  <br/> |
|Bedingt betriebsbereit  <br/> |Die Farm ist bereitgestellt, und virtuelle Computer werden ausgeführt und aktualisiert.  <br/> Zur Wiederherstellung gehören das Anfügen von Inhaltsdatenbanken, Bereitstellen von Dienstanwendungen und Durchforsten von Inhalten.  <br/> Die Farm kann eine kleinere Version der Produktionsfarm sein und anschließend für den gesamten Benutzerstamm horizontal hochskaliert werden.  <br/> |
|Verzögert betriebsbereit  <br/> |Die Farm ist vollständig erstellt, aber die virtuellen Computer sind nicht in Betrieb.  <br/> Zur Verwaltung der Umgebung zählen das Starten der virtuellen Computer in regelmäßigen Abständen, das Einspielen von Patches und Updates sowie das Überprüfen der Umgebung.  <br/> Starten Sie die vollständige Umgebung bei einem Notfall.  <br/> |
   
It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.
  
The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.
  
Weitere Informationen zur Notfallwiederherstellung finden Sie unter [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) und [Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).
  
## <a name="solution-description"></a>Beschreibung der Lösung

Die betriebsbereite Standby-Lösung für die Notfallwiederherstellung erfordert die folgende Umgebung:
  
- Eine lokale SharePoint-Produktionsfarm
    
- Eine SharePoint-Farm in Azure für die Wiederherstellung
    
- Eine Standort-zu-Standort-VPN-Verbindung zwischen den beiden Umgebungen
    
Die folgende Abbildung zeigt diese drei Elemente.
  
**Abbildung: Elemente einer betriebsbereiten Standby-Lösung in Windows Azure**

![Elemente einer verzögert betriebsbereiten SharePoint-Standbylösung in Windows Azure](media/AZarch-AZWarmStndby.png)
  
Der SQL Server-Protokollversand mit DFS-Replikation (Distributed File System Replication) dient zum Kopieren von Datenbanksicherungen und Transaktionsprotokollen in die Wiederherstellungsfarm in Azure: 
  
- DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.
    
- Protokolle werden in SQL Server in der Wiederherstellungsumgebung in Azure wiedergegeben.
    
- Sie fügen SharePoint-Inhaltsdatenbanken erst per Protokollversand an die Wiederherstellungsumgebung an, wenn ein Wiederherstellungsvorgang durchgeführt wird.
    
Führen Sie die folgenden Schritte aus, um die Farm wiederherzustellen:
  
1. Beenden Sie den Protokollversand.
    
2. Lassen Sie keinen Datenverkehr zur primären Farm mehr zu.
    
3. Geben Sie die letzten Transaktionsprotokolle wieder.
    
4. Fügen Sie die Inhaltsdatenbanken an die Farm an.
    
5. Stellen Sie Dienstanwendungen aus der replizierten Services-Datenbanken wieder her.
    
6. Aktualisieren Sie DNS-Einträge (Domain Name System) so, dass sie auf die Wiederherstellungsfarm zeigen.
    
7. Starten Sie eine vollständige Durchforstung.
    
We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.
  
Nachdem eine Wiederherstellung erfolgt ist, bietet Ihnen diese Lösung die in der folgenden Tabelle aufgeführten Elemente.
  
**Tabelle: Wiederherstellungsziele der Lösung**

|**Element**|**Beschreibung**|
|:-----|:-----|
|Websites und Inhalte  <br/> |Websites und Inhalte sind in der Wiederherstellungsumgebung verfügbar.  <br/> |
|Eine neue Instanz der Suche  <br/> |In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.  <br/> |
|Dienste  <br/> | Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started. <br/>  Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover: <br/>  Sammlung von Verwendungs- und Integritätsdaten <br/>  Statusdienst <br/>  Word-Automatisierung <br/>  Alle anderen Dienste, die keine Datenbank verwenden <br/> |
   
You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.
  
**Tabelle: Andere Elemente, die von MCS oder einem Partner betreut werden können**

|**Element**|**Beschreibung**|
|:-----|:-----|
|Synchronisieren benutzerdefinierter Farmlösungen  <br/> |Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.  <br/> |
|Verbindungen mit lokalen Datenquellen  <br/> |Es ist möglicherweise unpraktisch, Verbindungen mit Back-End-Datensystemen zu replizieren, z. B. mit Sicherungsdomänencontrollern und Inhaltsquellen für die Suche.  <br/> |
|Wiederherstellungsszenarien für die Suchfunktion  <br/> |Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.  <br/> |
   
Bei den Anleitungen in diesem Artikel wird davon ausgegangen, dass die lokale Farm bereits entworfen wurde und bereitgestellt ist.
  
## <a name="detailed-architecture"></a>Detaillierte Architektur

Im Idealfall ist die Konfiguration der Wiederherstellungsfarm in Azure identisch mit der lokalen Produktionsfarm, einschließlich der folgenden Einstellungen:
  
- Dieselbe Zuordnung von Serverrollen
    
- Dieselbe Konfiguration von Anpassungen
    
- Dieselbe Konfiguration der Suchkomponenten
    
The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.
  
Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.
  
This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.
  
### <a name="warm-standby-environments"></a>Betriebsbereite Standby-Umgebungen

In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.
  
Die folgende Abbildung zeigt eine Notfallwiederherstellungslösung aus einer lokalen SharePoint-Farm in eine Azure-basierten SharePoint-Farm, die als betriebsbereite Standby-Umgebung konfiguriert ist.
  
**Abbildung: Topologie und zentrale Elemente einer Produktionsfarm und einer betriebsbereiten Standby-Wiederherstellungsfarm**

![Topologie einer SharePoint-Farm und betriebsbereite Wiederherstellungsfarm](media/AZarch-AZWarmStndby.png)
  
Inhalt dieses Diagramms:
  
- Es sind zwei Umgebungen nebeneinander dargestellt: die lokale SharePoint-Farm und die betriebsbereite Standby-Farm in Azure.
    
- Jede Umgebung umfasst eine Dateifreigabe.
    
- Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.
    
- The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.
    
- DFSR kopiert Dateien aus der Dateifreigabe in der lokalen Umgebung in die Dateifreigabe in der Azure-Umgebung.
    
- Beim Protokollversand werden die Protokolle aus der Dateifreigabe der Azure-Umgebung im primären Replikat in der AlwaysOn-Verfügbarkeitsgruppe in SQL Server in der Wiederherstellungsumgebung wiedergegeben.
    
### <a name="cold-standby-environments"></a>Verzögert betriebsbereite Standby-Umgebungen

In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:
  
- Die Dateifreigabe
    
- Der primäre Datenbankserver
    
- Mindestens ein virtueller Computer mit Windows Server Active Directory-Domänendienste und DNS
    
The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.
  
**Abbildung: Verzögert betriebsbereite Standby-Wiederherstellungsfarm mit ausgeführten virtuellen Computern**

![Elemente einer betriebsbereiten SharePoint-Standbylösung in Windows Azure](media/AZarch-AZColdStndby.png)
  
Nach einem Failover zu einer verzögert betriebsbereiten Standby-Umgebung werden alle virtuellen Computer gestartet, und das Verfahren zum Erreichen von Hochverfügbarkeit der Datenbankserver muss konfiguriert werden, wie z. B. SQL Server AlwaysOn-Verfügbarkeitsgruppen.
  
Wenn mehrere Speichergruppen implementiert sind (Datenbanken sind auf mehrere SQL Server-Hochverfügbarkeitsätze verteilt), muss die primäre Datenbank für jede Speichergruppe für die Annahme der Protokolle der jeweiligen Speichergruppe ausgeführt werden.
  
### <a name="skills-and-experience"></a>Kompetenz und Erfahrung

Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:
  
- [Übersicht über DFS-Namespaces und DFS-Replikation](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Windows Server-Failoverclustering (WSFC) mit SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [Sichern und Wiederherstellen von SQL Server-Datenbanken](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [Übersicht über die SharePoint 2013-Installation und -Konfiguration](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.
  
In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.
  
## <a name="disaster-recovery-roadmap"></a>Fahrplan für die Notfallwiederherstellung

![Bildliche Darstellung der Roadmap für eine SharePoint-Notfallwiederherstellung.](media/Azure-DRroadmap.png)
  
Dieser Fahrplan setzt vorausgesetzt, dass Sie bereits eine SharePoint Server 2013-Farm in der Produktion bereitgestellt haben.
  
**Tabelle: Fahrplan für die Notfallwiederherstellung**

|**Phase**|**Beschreibung**|
|:-----|:-----|
|Phase 1  <br/> |Entwerfen der Umgebung für die Notfallwiederherstellung  <br/> |
|Phase 2  <br/> |Erstellen des virtuellen Azure-Netzwerks und der VPN-Verbindung  <br/> |
|Phase 3  <br/> |Bereitstellen von Active Directory und Domain Name Services im virtuellen Azure-Netzwerk  <br/> |
|Phase 4  <br/> |Bereitstellen der SharePoint-Wiederherstellungsfarm in Azure  <br/> |
|Phase 5  <br/> |Einrichten der DFS-Replikation zwischen den Farmen  <br/> |
|Phase 6  <br/> |Einrichten des Protokollversands zur Wiederherstellungsfarm  <br/> |
|Phase 7  <br/> | Validate failover and recovery solutions. This includes the following procedures and technologies: <br/>  Beenden des Protokollversands <br/>  Wiederherstellen der Sicherungen <br/>  Durchforsten von Inhalten <br/>  Wiederherstellen von Diensten <br/>  Verwalten von DNS-Einträgen <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>Phase 1: Entwerfen der Umgebung für die Notfallwiederherstellung

Befolgen Sie die Anleitungen unter [Microsoft Azure-Architekturen für SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) für den Entwurf der Umgebung für die Notfallwiederherstellung, einschließlich der SharePoint-Wiederherstellungsfarm. Sie können die Grafiken in der [SharePoint-Notfallwiederherstellungslösung in Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio-Datei verwenden, um den Entwurfsprozess zu starten. Es wird empfohlen, dass Sie die gesamte Umgebung vor Beginn der Arbeit in der Azure-Umgebung entwerfen.
  
Zusätzlich zur Anleitung unter [Microsoft Azure-Architekturen für SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) für das Entwerfen des virtuellen Netzwerks, der VPN-Verbindung, von Active Directory und der SharePoint-Farm müssen Sie der Azure-Umgebung eine Dateifreigaberolle hinzufügen.
  
To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups. 
  
> [!NOTE]
> It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870). 
  
**Abbildung: Platzierung eines Dateiservers, der für eine Notfallwiederherstellungslösung verwendet wird**

![Zeigt eine Dateifreigabe-VM, die demselben Clouddienst hinzugefügt wurde, der die SharePoint-Datenbankserverrollen enthält.](media/AZenv-FSforDFSRandWSFC.png)
  
In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.
  
If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.
  
When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.
  
Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Phase 2: Erstellen des virtuellen Azure-Netzwerks und der VPN-Verbindung

[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:
  
- Planen des privaten IP-Adressbereichs des Virtual Networks
    
- Planen der Änderungen der Routinginfrastruktur für das Virtual Network
    
- Planen von Firewallregeln für ein- und ausgehenden Datenverkehr des lokalen VPN-Geräts
    
- Erstellen des standortübergreifenden virtuellen Netzwerks in Azure
    
- Konfigurieren des Routings zwischen Ihrem lokalen Netzwerk und Virtual Networks
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Phase 3: Bereitstellen von Active Directory und Domain Name Services für das virtuelle Azure-Netzwerk

Diese Phase umfasst die Bereitstellung von Windows Server Active Directory und DNS für das Virtual Network in einem Hybridszenario (wie unter [Microsoft Azure-Architekturen für SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) und in der folgenden Abbildung beschrieben).
  
**Abbildung 4: Hybride Active Directory-Domänenkonfiguration**

![Zwei virtuelle Computer, die im virtuellen Azure-Netzwerk und im SharePoint-Farm Subnetz bereitgestellt werden, sind Replikatdomänencontroller und DNS-Server](media/AZarch-HyADdomainConfig.png)
  
In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.
  
Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.
  
Ausführliche Anleitungen zum Einrichten eines Domänencontrollers in Azure finden Sie unter [Installieren eines Active Directory-Replikatdomänencontrollers in Azure Virtual Networks](https://go.microsoft.com/fwlink/p/?LinkId=392687).
  
Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Phase 4: Bereitstellen der SharePoint-Wiederherstellungsfarm in Azure

Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.
  
Befolgen Sie die folgenden Methoden, die wir beim Erstellen unserer Umgebung für eine Machbarkeitsstudie entwickelt haben:
  
- Erstellen virtueller Computer mithilfe des Azure-Portals oder mithilfe von PowerShell.
    
- Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.
    
- Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.
    
- If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.
    
- Verwenden Sie eine Benennungskonvention für die virtuellen Computer.
    
- Achten Sie darauf, in welchem Rechenzentrum die virtuellen Computern bereitgestellt werden.
    
- Das Feature der automatische Skalierung in Azure wird für SharePoint-Rollen nicht unterstützt.
    
- Konfigurieren Sie keine Elemente in der Farm, die wiederhergestellt werden, z. B. Websitesammlungen. 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Phase 5: Einrichten der DFS-Replikation zwischen den Farmen

To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.
  
Führen Sie im Dashboard Server-Manager die folgenden Schritte aus:
  
- Konfigurieren Sie den lokalen Server.
    
- Starten Sie den **** Assistenten zum Hinzufügen von Rollen und Features.
    
- Öffnen Sie den Knoten **Datei- und Speicherdienste**.
    
- Wählen Sie **DFS-Namespaces** und **DFS-Replikation** aus.
    
- Klicken Sie auf **Weiter**, um den Assistenten abzuschließen.
    
Die folgende Tabelle enthält Links zu DFSR-Referenzartikeln und -Blogbeiträgen.
  
**Tabelle: Referenzartikel für DFSR**

|**Titel**|**Beschreibung**|
|:-----|:-----|
|[Replikation](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |TechNet-Thema zur DFS-Verwaltung mit Links für die Replikation  <br/> |
|[DFS-Replikation: Überlebensleitfaden](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |Wiki mit Links zu DFS-Informationen  <br/> |
|[DFS-Replikation: Häufig gestellte Fragen](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |TechNet-Thema zur DFS-Replikation  <br/> |
|[Jose Barretos Blog](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |Blog eines leitenden Programmmanagers aus dem File Server-Team von Microsoft  <br/> |
|[Das Storage-Team bei Microsoft - File Cabinet Blog](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |Blog zu Dateidiensten und Speicherfeatures in Windows Server  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Phase 6: Einrichten des Protokollversands zur Wiederherstellungsfarm

Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping). 
  
> [!IMPORTANT]
> Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121). 
  
## <a name="phase-7-validate-failover-and-recovery"></a>Phase 7: Überprüfen von Failover und Wiederherstellung

The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.
  
The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.
  
### <a name="stop-log-shipping"></a>Beenden des Protokollversands

You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>Wiederherstellen der Sicherungen

Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):
  
- The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.
    
- All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.
    
To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.
  
In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).
  
### <a name="crawl-the-content-source"></a>Durchforsten der Inhaltsquelle

You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.
  
Um eine vollständige Durchforstung zu starten, führen Sie die folgenden Schritte aus:
  
1. Wechseln Sie in der SharePoint 2013-Zentraladministration zu **Anwendungsverwaltung** > **Dienstanwendungen** > **Dienstanwendungen verwalten**, und klicken Sie dann auf die Suchdienstanwendung, die durchforstet werden soll.
    
2. Klicken Sie auf der Seite **Suchverwaltung** auf **Inhaltsquellen**, zeigen Sie auf die gewünschte Inhaltsquelle, klicken Sie auf den Pfeil und dann auf **Vollständige Durchforstung starten**.
    
### <a name="recover-farm-services"></a>Wiederherstellen von Farmdiensten

Die folgende Tabelle zeigt die Vorgehensweise beim Wiederherstellen von Diensten von Datenbanken mit Protokollversand, die Dienste, die zwar Datenbanken haben, deren Wiederherstellung mit Protokollversand jedoch nicht empfohlen wird, und die Dienste ohne Datenbanken.
  
> [!IMPORTANT]
> Beim Wiederherstellen einer lokalen SharePoint-Datenbank in der Azure-Umgebung werden keine SharePoint-Dienste wiederhergestellt, die Sie nicht bereits manuell in Azure installiert haben. 
  
**Tabelle: Referenz der Dienstanwendungsdatenbanken**

|**Stellen Sie diese Dienste aus Datenbanken mit Protokollversand wieder her**|**Diese Dienste haben Datenbanken, aber es wird empfohlen, diese Dienste zu starten, ohne ihre Datenbanken wiederherzustellen**|**Diese Dienste speichern keine Daten in Datenbanken. Starten Sie diese Dienste nach dem Failover**|
|:-----|:-----|:-----|
| Maschineller Übersetzungsdienst <br/>  Verwalteter Metadatendienst <br/>  Secure Store Service <br/>  User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.) <br/>  Microsoft SharePoint Foundation-Abonnementeinstellungendienst <br/> | Sammlung von Verwendungs- und Integritätsdaten <br/>  Statusdienst <br/>  Word-Automatisierung <br/> | Excel Services <br/>  PerformancePoint-Dienste <br/>  PowerPoint-Konvertierung <br/>  Visio-Grafikdienst <br/>  Arbeitsverwaltung <br/> |
   
Das folgende Beispiel zeigt, wie der verwaltete Metadatendienst aus einer Datenbank wiederhergestellt wird.
  
This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.
  
Verwenden Sie zuerst  `New-SPMetadataServiceApplication`, und geben Sie dann den Parameter  `DatabaseName` mit dem Namen der wiederhergestellten Datenbank an.
  
Konfigurieren Sie als Nächstes die neue verwaltete Metadatendienstanwendung auf dem sekundären Server wie folgt:
  
- Name: Verwalteter Metadatendienst
    
- Datenbankserver: Der Datenbanknamen aus dem versendeten Transaktionsprotokoll
    
- Datenbankname:Managed_Metadata_DB
    
- Anwendungspool: SharePoint-Dienstanwendungen 
    
### <a name="manage-dns-records"></a>Verwalten von DNS-Einträgen

Sie müssen DNS-Einträge manuell so erstellen, dass sie auf Ihre SharePoint-Farm zeigen.
  
In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails. 
  
Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `https://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.
  
Für den externen Zugriff auf Ihre SharePoint-Farm können Sie einen Hosteintrag auf einem externen DNS-Server mit der gleichen URL erstellen, die Clients in Ihrem Intranet verwenden (beispielsweise `https://sharepoint.contoso.com` ), die auf eine externe IP-Adresse in Ihrer Firewall verweist. (Eine bewährte Methode in diesem Beispiel ist das Einrichten von Split-DNS, sodass der interne DNS-Server für autorisierend ist `contoso.com` und Anforderungen direkt an den SharePoint-Farm Cluster weiterleitet, anstatt DNS-Anforderungen an Ihren externen DNS-Server weiterzuleiten.) Anschließend können Sie die externe IP-Adresse der internen IP-Adresse des lokalen Clusters zuordnen, damit die Clients die gesuchten Ressourcen finden.
  
Von hier aus können Sie auf verschiedene Szenarien für die Notfallwiederherstellung stoßen:
  
 **Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.
  
 **Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.
  
Wenn Sie Websitesammlungen mit Hostnamen verwenden, wie in der [Website Sammlungs Architektur mit Hostnamen und der Bereitstellung (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment)empfohlen, können mehrere Websitesammlungen von derselben Webanwendung in Ihrer SharePoint-Farm mit eindeutigen DNS-Namen (beispielsweise `https://sales.contoso.com` und `https://marketing.contoso.com` ) gehostet werden. In diesem Fall können Sie DNS-Einträge für jede Websitesammlung erstellen, die auf die IP-Adresse Ihres Clusters zeigen. Sobald eine Anforderung Ihre SharePoint-Web-Front-End-Server erreicht, übernehmen sie das Weiterleiten jeder Anforderung zur gewünschten Websitesammlung.
  
## <a name="microsoft-proof-of-concept-environment"></a>Microsoft-Umgebung für Machbarkeitsstudie

We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.
  
Die folgende Tabelle beschreibt die virtuellen Hyper-V-Computer, die wir für die lokale Testumgebung erstellt und konfiguriert haben.
  
**Tabelle: Virtuelle Computer für lokalen Test**

|**Servername**|**Rolle**|**Konfiguration**|
|:-----|:-----|:-----|
|DC1  <br/> |Domänencontroller mit Active Directory  <br/> |Zwei Prozessoren  <br/> Von 512 MB bis 4 GB RAM  <br/> 1 x 127-GB-Festplatte  <br/> |
|RRAS  <br/> |Mit der Rolle "Routing- und RAS-Dienst (RRAS)" konfigurierter Server  <br/> |Zwei Prozessoren  <br/> 2-8 GB RAM  <br/> 1 x 127-GB-Festplatte  <br/> |
|FS1  <br/> |Dateiserver mit Freigaben für Sicherungen und einem Endpunkt für DFSR  <br/> |Vier Prozessoren  <br/> 2-12 GB RAM  <br/> 1 x 127-GB-Festplatte  <br/> 1 x 1-TB-Festplatte (SAN)  <br/> 1 x 750-GB-Festplatte  <br/> |
|SP-WFE1, SP-WFE2  <br/> |Front-End-Webserver  <br/> |Vier Prozessoren  <br/> 16 GB RAM  <br/> |
|SP-APP1, SP-APP2, SP-APP3  <br/> |Anwendungsserver  <br/> |Vier Prozessoren  <br/> 2-16 GB RAM  <br/> |
|SP-SQL-HA1, SP-SQL-HA2  <br/> |Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.  <br/> |Vier Prozessoren  <br/> 2-16 GB RAM  <br/> |
   
Die folgende Tabelle beschreibt die Laufwerkskonfigurationen der virtuellen Hyper-V-Computer, die wir für die Front-End-Webserver und Anwendungsserver für die lokale Testumgebung erstellt und konfiguriert haben.
  
**Tabelle: Laufwerksanforderungen an die virtuellen Computer für die Front-End-Web- und Anwendungsserver in der lokalen Testumgebung**

|**Laufwerksbuchstabe**|**Größe**|**Name des Verzeichnisses**|**Pfad**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Systemlaufwerk  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |Protokolllaufwerk (40 GB)  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |80  <br/> |Seite (36 GB)  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA  <br/> |
   
The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.
  
**Tabelle: Laufwerksanforderungen an die virtuellen Computer für die Datenbankserver in der lokalen Testumgebung**

|**Laufwerksbuchstabe**|**Größe**|**Name des Verzeichnisses**|**Pfad**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Datenstammverzeichnis  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500  <br/> |Benutzerdatenbankverzeichnis  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |500  <br/> |Protokollverzeichnis der Benutzerdatenbank  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|G  <br/> |500  <br/> |Temporäres Datenbankverzeichnis  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|H  <br/> |500  <br/> |Temporäres Datenbankprotokollverzeichnis  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
   
### <a name="setting-up-the-test-environment"></a>Einrichten der Testumgebung

During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.
  
Wir haben unsere Testumgebung in den folgenden drei Phasen bereitgestellt:
  
- Einrichten der Infrastruktur der Hybridumgebung
    
- Bereitstellen der Server
    
- Bereitstellen der SharePoint-Farmen
    
#### <a name="set-up-the-hybrid-infrastructure"></a>Einrichten der Infrastruktur der Hybridumgebung

This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.
  
#### <a name="provision-the-servers"></a>Bereitstellen der Server

In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.
  
#### <a name="deploy-the-sharepoint-farms"></a>Bereitstellen der SharePoint-Farmen

The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.
  
We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance. 
  
> [!NOTE]
> Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)
  
Wir haben die Farm erstellt und weitere Server in der folgenden Reihenfolge hinzugefügt:
  
- SP-SQL-HA1 und SP-SQL-HA2 bereitgestellt.
    
- AlwaysOn konfiguriert und die drei Verfügbarkeitsgruppen für die Farm erstellt. 
    
- SP-APP1 zum Hosten der Zentraladministration bereitgestellt.
    
- SP-WFE1 und SP-WFE2 zum Hosten des verteilten Caches bereitgestellt. 
    
Wir haben den Parameter  _skipRegisterAsDistributedCachehost_ bei der Ausführung von **psconfig.exe** an der Befehlszeile angegeben. Weitere Informationen finden Sie unter [Planen von Feeds und des Diensts für den verteilten Cache in SharePoint Server 2013](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service). 
  
Wir haben die folgenden Schritte in der Wiederherstellungsumgebung wiederholt:
  
- AZ-SQL-HA1 und AZ-SQL-HA2 bereitgestellt.
    
- AlwaysOn konfiguriert und die drei Verfügbarkeitsgruppen für die Farm erstellt.
    
- AZ-APP1 zum Hosten der Zentraladministration bereitgestellt.
    
- AZ-WFE1 und AZ-WFE2 zum Hosten des verteilten Caches bereitgestellt.
    
After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.
  
Die folgende Tabelle beschreibt die virtuellen Computer, Subnetze und Verfügbarkeitsätze, die wir für unsere Wiederherstellungsfarm eingerichtet haben.
  
**Tabelle: Infrastruktur der Wiederherstellungsfarm**

|**Servername**|**Rolle**|**Konfiguration**|**Subnetz**|**Verfügbarkeitssatz**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Domänencontroller mit Active Directory  <br/> |Zwei Prozessoren  <br/> Von 512 MB bis 4 GB RAM  <br/> 1 x 127-GB-Festplatte  <br/> |sp-ADservers  <br/> ||
|AZ-SP-FS  <br/> |Dateiserver mit Freigaben für Sicherungen und einem Endpunkt für DFSR  <br/> | A5-Konfiguration: <br/>  Zwei Prozessoren <br/>  14 GB RAM <br/>  1 x 127-GB-Festplatte <br/>  1 x 135-GB-Festplatte <br/>  1 x 127-GB-Festplatte <br/>  1 x 150-GB-Festplatte <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
|AZ-WFE1, AZ -WFE2  <br/> |Front-End-Webserver  <br/> | A5-Konfiguration: <br/>  Zwei Prozessoren <br/>  14 GB RAM <br/>  1 x 127-GB-Festplatte <br/> |sp-webservers  <br/> |WFE_SET  <br/> |
|AZ -APP1, AZ -APP2, AZ -APP3  <br/> |Anwendungsserver  <br/> | A5-Konfiguration: <br/>  Zwei Prozessoren <br/>  14 GB RAM <br/>  1 x 127-GB-Festplatte <br/> |sp-applicationservers  <br/> |APP_SET  <br/> |
|AZ -SQL-HA1, AZ -SQL-HA2  <br/> |Datenbankserver und die primären und sekundären Replikate für AlwaysOn-Verfügbarkeitsgruppen  <br/> | A5-Konfiguration: <br/>  Zwei Prozessoren <br/>  14 GB RAM <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>Betriebliche Vorgänge

Nachdem das Testteam die Farmumgebungen stabilisiert und Funktionstests abgeschlossen hatte, begann es mit den folgenden betrieblichen Vorgängen zum Konfigurieren der lokalen Wiederherstellungsumgebung:
  
- Konfigurieren vollständiger und differenzieller Sicherungen
    
- Konfigurieren von DFSR auf den Dateiservern, die Transaktionsprotokolle zwischen der lokalen Umgebung und der Azure-Umgebung übertragen
    
- Konfigurieren des Protokollversands auf dem primären Datenbankserver
    
- Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.
    
### <a name="databases"></a>Datenbanken

Für unsere Failovertests haben wir die folgenden Datenbanken verwendet: 
  
- WSS_Content
    
- ManagedMetadata
    
- Profile DB
    
- Sync DB
    
- Social DB
    
- Content Type Hub (eine Datenbank für einen dedizierten Inhaltstyp-Veröffentlichungshub)
    
## <a name="troubleshooting-tips"></a>Tipps zur Problembehandlung

In diesem Abschnitt werden die Probleme, die während der Tests aufgetreten sind, und die dazugehörigen Lösungen erläutert. 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Bei Verwenden des Terminologiespeicher-Verwaltungstools ist der folgende Fehler aufgetreten: "Verwalteter Metadatenspeicher oder Verbindung derzeit nicht verfügbar."

Stellen Sie sicher, dass das von der Webanwendung verwendete Anwendungspoolkonto über die Berechtigung "Lesezugriff auf den Terminologiespeicher" verfügt.
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Benutzerdefinierte Ausdruckssätze stehen in der Websitesammlung nicht zur Verfügung

Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Der Windows PowerShell-Befehl Get-ADForest erzeugt den folgenden Fehler: "Die Benennung Get-ADForest wurde nicht als Name eines Cmdlets, einer Funktion, einer Skriptdatei oder eines ausführbaren Programms erkannt."

When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Erstellen der Verfügbarkeitsgruppe missling beim Starten der "AlwaysOn_health"-XEvent-Sitzung auf <server name>

Stellen Sie sicher, dass beide Knoten Ihres Failoverclusters den Status "In Betrieb" und nicht "Angehalten" oder "Beendet" haben. 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server-Protokollversandauftrag misslingt mit dem Fehler "Zugriff verweigert" beim Versuch, eine Verbindung mit der Dateifreigabe herzustellen

Stellen Sie sicher, dass der SQL Server-Agent mit Netzwerkanmeldeinformationen und nicht mit den Standardanmeldeinformationen ausgeführt wird.
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>Der SQL Server-Protokollversandauftrag war erfolgreich, es wurden aber keine Dateien kopiert.

This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Verwalteter Metadatendienst (oder anderer SharePoint-Dienst) wird nach der Installation nicht automatisch gestartet

Je nach Leistung und aktueller Last Ihrer SharePoint-Server kann das Starten von Diensten mehrere Minuten dauern. Klicken Sie für den Dienst manuell auf **Starten**, und räumen Sie genügend Zeit für den Start ein, während Sie gelegentlich den Bildschirm Dienste auf dem Server aktualisieren, um den Status zu überwachen. Für den Fall, dass der Dienst beendet bleibt, aktivieren Sie die SharePoint-Diagnoseprotokollierung, versuchen, den Dienst neu zu starten, und überprüfen dann das Protokoll auf Fehler. Weitere Informationen finden Sie unter [Konfigurieren der Diagnoseprotokollierung in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Nach dem Ändern von DNS auf die Azure-Failoverumgebung verwenden Clientbrowser weiterhin die alte IP-Adresse für die SharePoint-Website.

Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Zusätzliche Ressourcen

[Unterstützte Hochverfügbarkeits- und Notfallwiederherstellungsoptionen für SharePoint-Datenbanken](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[Konfigurieren von SQL Server 2012 AlwaysOn-Verfügbarkeitsgruppen für SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>Siehe auch

[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.yml)



