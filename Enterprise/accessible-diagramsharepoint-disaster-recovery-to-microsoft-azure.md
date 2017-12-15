---
title: "Zugängliches Diagramm – SharePoint-Notfallwiederherstellung in Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „SharePoint-Notfallwiederherstellung in Microsoft Azure“."
ms.openlocfilehash: 2babb1910b0cd8dcbfe4cc0bf32de7c714c05fc0
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>Zugängliches Diagramm – SharePoint-Notfallwiederherstellung in Microsoft Azure

**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen SharePoint Disaster Recovery in Microsoft Azure.
  
Dieses Poster zeigt Beispiele von Architekturen zum Erstellen einer Wiederherstellungsumgebung in Azure.  
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>Lokale Umgebung mit einer Azure-Wiederherstellungsumgebung

Das Diagramm zeigt ein Architekturbeispiel für die Produktionsumgebung einer lokalen Umgebung, die Azure für die Wiederherstellung verwendet.  
  
### <a name="on-premises-production-environment"></a>Lokale Produktionsumgebung

Das zugehörige Diagramm zeigt eine Liveproduktionsumgebung mit vier Serverebenen in einer Serverfarm.  
  
#### <a name="tier-1"></a>Ebene 1

Diese Ebene enthält zwei Server für Front-End-Dienste und Abfrageverarbeitung. Eine Indexpartition stellt ein Replikat der beiden Server bereit.  
  
#### <a name="tier-2"></a>Ebene 2

Diese Ebene enthält zwei Servern für verteilten Cache.  
  
#### <a name="tier-3"></a>Ebene 3

Diese Ebene enthält gibt drei Server. Jeder Server bietet die folgenden Dienste:  
  
- Back-End-Dienste  
    
- Administrator 
    
- Workflow-Manager 
    
- Durchforstung 
    
- Inhaltsverarbeitung 
    
- Analyse 
    
#### <a name="tier-4"></a>Ebene 4

Diese Ebene enthält zwei Server. Beide Server haben drei Verfügbarkeitsgruppen, wie nachfolgend erläutert:  
  
- Verfügbarkeitsgruppe 1 stellt Suchfunktionen bereit.  
    
- Verfügbarkeitsgruppe 2 stellt Inhalte, Konfiguration und Dienstanwendungen bereit.  
    
- Verfügbarkeitsgruppe 3 stellte Inhalte bereit.  
    
Diese Ebene enthält auch einen Dateifreigabeserver. Die Server der Ebene 4 kommunizieren per Protokollversand mit diesem Server. Dieser Server kommuniziert seinerseits durch DFS-Replikation (DFSR, Distributed File System Replication) mit einem Dateifreigabeserver in der betriebsbereiten Azure-Wiederherstellungsumgebung, wie im folgenden Abschnitt beschrieben.  
  
### <a name="azure-recovery-environment"></a>Azure-Wiederherstellungsumgebung

#### <a name="warm-standby-environment-running-virtual-machines"></a>Betriebsbereite Umgebung, in der virtuelle Computer ausgeführt werden

Das zugehörige Diagramm zeigt die lokale Umgebung, die in der Azure-Wiederherstellungsumgebung genau repliziert wird. Der Dateifreigabeserver in dieser Umgebung ist durch DFSR mit der lokalen Umgebung verknüpft. DFSR überträgt Protokolle über den Dateifreigabeserver aus der Produktionsumgebung in die Wiederherstellungsumgebung.  
  
### <a name="overview"></a>Übersicht

Die notfallwiederherstellungsumgebung einer lokalen SharePoint 2013-Farm kann in Azure gehostet werden. 
  
-   Azure-Infrastrukturdienste stellt ein sekundäres Datencenter zur Verfügung. 
    
- Zahlen Sie nur für die Ressourcen, die Sie tatsächlich nutzen.  
    
- Kleine Wiederherstellungsfarmen können nach einem Notfall horizontal hochskaliert werden, um Skalierungs- und Kapazitätsziele zu erreichen.  
    
Die Wiederherstellungsfarm in Azure ist so konfiguriert, dass sie so identisch wie möglich mit der lokalen Produktionsfarm ist.  
  
- Gleiche Zuordnung von Serverrollen 
    
- Gleiche Konfiguration von Anpassungen  
    
- Gleiche Konfiguration von Suchfunktionen (diese können sich auf einer kleinere Version der Produktionsfarm befinden)  
    
Protokollversand und DFSR werden verwendet, um Datenbanksicherungen und Transaktionsprotokolle in die Azure-Farm zu kopieren.  
  
- DFSR überträgt Protokolle aus der Produktionsumgebung in die Wiederherstellungsumgebung. In einem WAN-Szenario ist DFSR effizienter als das direkte Versenden der Protokolle an den sekundären Server in Azure.  
    
- Protokolle werden auf den Azure-basierten SQL Server-Computern wiedergegeben.  
    
- Die per Protokollversand verschickten Datenbanken werden erst dann an die Farm angefügt, wenn eine Wiederherstellung ausgeführt wird. 
    
Failoververfahren:  
  
1. Beenden Sie den Protokollversand. 
    
2. Lassen Sie keinen Datenverkehr zur primären Farm mehr zu. 
    
3. Geben Sie die letzten Transaktionsprotokolle wieder. 
    
4. Fügen Sie die Inhaltsdatenbanken an die Farm an. 
    
5. Starten Sie eine vollständige Durchforstung. 
    
6. Stellen Sie Dienstanwendungen aus der replizierten Services-Datenbanken wieder her. 
    
Zu den Wiederherstellungszielen dieser Lösung gehören:  
  
- Websites und Inhalte 
    
- Suche (erneut durchforstet, kein Suchverlauf)  
    
- Dienste
    
Zusätzliche Punkte, die von Microsoft Consulting Services oder einem Partner übernommen werden können:  
  
- Synchronisieren benutzerdefinierter Farmlösungen 
    
- Verbindungen mit lokalen Datenquellen (Business Data Connectivity (BDC) und Suchinhaltsquellen)  
    
- Wiederherstellungsszenarien für die Suchfunktion 
    
- Recovery Time Objectives (RTO, angestrebte Wiederherstellungsdauer) Recovery Point Objectives (RPO, angestrebter Wiederherstellungszeitpunkt) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>Verzögert betriebsbereite Umgebung, in der virtuelle Computer ausgeführt werden

Verzögert betriebsbereite Umgebungen brauchen länger für den Start, sind jedoch kostengünstiger.  
  
- Die Farm ist vollständig erstellt, aber die virtuellen Computer werden nach Erstellung der Farm angehalten. Sie zahlen nur Verarbeitungskosten, wenn die virtuellen Computer ausgeführt werden, es fallen jedoch Speicher- und Netzwerkübertragungskosten an.  
    
- Bei einem Notfall werden alle virtuellen Computer in der Farm gestartet und repariert.  
    
- Sicherungen und Transaktionsprotokolle werden auf die Farmdatenbanken angewendet.  
    
In der folgenden Liste werden zusätzliche Verfahren für verzögert betriebsbereite Umgebungen beschrieben:  
  
- Schalten Sie virtuelle Computer regelmäßig ein, um die Umgebung zu reparieren, zu aktualisieren und zu überprüfen.  
    
- Führen Sie Verfahren zum Aktualisieren von DNS- und IP-Adressen aus.  
    
- Richten Sie SQL AlwaysOn nach einem Failover ein.  
    
Das zugehörige Diagramm zeigt eine replizierte Wiederherstellungsumgebung auf virtuellen Computern. Nach einem Failover zu einer verzögert betriebsbereiten Umgebung werden alle virtuellen Computer gestartet, und die Verfügbarkeitsgruppen werden mithilfe von Wiedergabeprotokollen konfiguriert, um die Datenbankserver verfügbar zu machen.  
  
## <a name="sharepoint-recovery-environment-in-azure"></a>SharePoint-Wiederherstellungsumgebung in Azure

Entwerfen und erstellen Sie die Failoverumgebung in Azure.  
  
- Erstellen Sie ein virtuelles Netzwerk in Microsoft Azure.  
    
- Verbinden Sie das lokale Netzwerk über eine Standort-zu-Standort-VPN-Verbindung mit dem virtuellen Netzwerk in Azure. Diese Verbindung verwendet ein dynamisches Gateway in Azure.  
    
- Stellen Sie mindestens einen Domänencontroller für das virtuelle Azure-Netzwerk bereit, und konfigurieren Sie diesen für die Arbeit mit der lokalen Domäne. Diese Domänencontroller sind Katalogserver.  
    
- Passen Sie die SharePoint-Farm für Clouddienste und Verfügbarkeitsgruppen an.   
    
- Stellen Sie die SharePoint-Farm sowie einen Dateiserver zum Hosten von Dateifreigaben bereit.  
    
- Richten Sie Protokollversand und DFSR zwischen der lokalen Umgebung und der Azure-basierten Wiederherstellungsumgebung ein.  
    
Das zugehörige Diagramm zeigt die lokale Umgebung und das virtuelle Azure-Netzwerk mit den folgenden Features:  
  
### <a name="on-premises-environment"></a>Lokale Umgebung

- Windows Server 2012 RRAS  
    
- Active Directory-Server 
    
Die Schnittstelle zwischen dem lokalen Netzwerk und dem virtuellen Azure-Netzwerk bildet ein VPN-Gateway (virtuelles privates Netzwerk).  
  
### <a name="azure-virtual-network"></a>Virtuelles Azure-Netzwerk

Das VPN-Gateway hat eine Schnittstelle mit einem aktiven VPN-Gatewaysubnetz.  
  
Das virtuelle Azure-Netzwerk enthält drei Clouddienste:  
  
- Der erste Clouddienst verfügt über zwei Active Directory- und DNS-Server mit einer Verfügbarkeitsgruppe.  
    
- Der zweite Cloud-Dienst hat drei Gruppen von Servern: zwei verteilten Cache Server mit einer Verfügbarkeit. Zwei Front-End-Server mit einer Verfügbarkeit. Drei Back-End-Server mit einer Verfügbarkeit.
    
- Der dritte Clouddienst verfügt über drei Datenbankserver mit einer Verfügbarkeitsgruppe. Einer dieser Datenbankserver ist eine Dateifreigabe für den Protokollversand und ein dritter Knoten einer Knotenmehrheit für SQL Server AlwaysOn.  
    
### <a name="build-the-ad-ds-hybrid-environment"></a>Erstellen der AD DS-Hybridumgebung

Die Konfiguration von AD DS für diese Lösung ist ein Hybridbereitstellungsszenario, in dem AD DS teilweise lokal und teilweise auf virtuellen Azure-Computern bereitgestellt wird.  
  
Wichtig – Lesen Sie vor dem Bereitstellen von AD DS in Azure die Richtlinien für die Bereitstellung von Windows Server Active Directory auf virtuellen Computern in Azure (http://msdn.microsoft.com/de-de/library/windowsazure/jj156090.aspx).  
  
Vollständige Anweisungen zum Entwerfen und Bereitstellen von Active Directory-Umgebungen finden Sie unter http://TechNet.Microsoft.com.  
  
Diese Referenzarchitektur enthält zwei virtuelle Computer, die als Domänencontroller konfiguriert sind. Jeder ist wie folgt konfiguriert:  
  
- Größe: klein  
    
- Betriebssystem: Windows Server 2012   
    
- Rolle: AD DS-Domänencontroller, der als globaler Katalogserver ausgewiesen ist. Diese Konfiguration reduziert den ausgehenden Datenverkehr über die VPN-Verbindung. In einer Umgebung mit mehreren Domänen mit einer hohen Änderungsrate konfigurieren Sie die Domänencontroller lokal so, dass sie nicht mit den globalen Katalogservern in Azure synchronisiert werden.   
    
- Datenträger: Platzieren Sie die AD DS-Datenbank, Protokolle und SYSVOL auf Azure-Datenträgern. Platzieren Sie sie nicht auf dem Datenträger mit dem Betriebssystem oder den temporären Datenträgern, die von Azure bereitgestellt werden. Dies ist wichtig. 
    
- Rolle: Installieren und konfigurieren Sie Windows DNS auf den Domänencontrollern.  
    
- IP-Adressen: Verwenden Sie dynamische IP-Adressen. Dazu müssen Sie ein virtuelles Azure-Netzwerk erstellen.  
    

