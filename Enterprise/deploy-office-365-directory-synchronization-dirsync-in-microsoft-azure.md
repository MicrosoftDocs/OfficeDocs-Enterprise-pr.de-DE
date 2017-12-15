---
title: Bereitstellen der Office 365-Verzeichnissynchronisierung (DirSync) in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Zusammenfassung: Bereitstellung von Azure Active Directory verbinden (DirSync) auf einem virtuellen Computer in Azure Konten zwischen Ihrer lokalen Verzeichnis und die Azure AD-Mandanten Ihres Office 365-Abonnements zu synchronisieren.'
ms.openlocfilehash: c6ee337c49092ac5d2b3d30a54fc33b3f3e2bb58
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure"></a>Bereitstellen der Office 365-Verzeichnissynchronisierung (DirSync) in Microsoft Azure

 **Zusammenfassung:** Bereitstellen von Azure AD Connect (DirSync) auf einem virtuellen Computer in Azure, um Konten zwischen dem lokalen Verzeichnis und dem Azure AD-Mandanten Ihres Office 365-Abonnements zu synchronisieren.
  
Azure Active Directory (AD) Connect (früher als Directory-Synchronisierungstool oder DirSync.exe-Tool bezeichnet) ist eine Serveranwendung, die Sie auf einem einer Domäne beigetretenen Server zum Synchronisieren Ihrer lokalen Windows Server Active Directory-Benutzer mit dem Azure Active Directory-Mandanten Ihres Office 365-Abonnements installieren. Sie können Azure AD Connect auf einem lokalen Server installieren, doch wir empfehlen aus den folgenden Gründen die Installation auf einem virtuellen Computer in Azure:
  
- Sie können Cloud-basierte Server schneller bereitstellen und konfigurieren und so die Dienste Ihren Benutzern schneller zur Verfügung stellen.
    
- Azure bietet eine bessere Verfügbarkeit von Websites mit weniger Aufwand.
    
- Sie können die Anzahl der lokalen Server in Ihrer Organisation verringern.
    
> [!IMPORTANT]
> Diese Lösung erfordert Konnektivität zwischen dem lokalen Netzwerk und Ihrem virtuellen Azure-Netzwerk. Weitere Informationen finden Sie unter [Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!IMPORTANT]
> Dieser Artikel beschreibt die Synchronisierung einer einzelnen Domäne in einer einzelnen Gesamtstruktur. Azure AD Connect synchronisiert alle Windows Server AD-Domänen in Ihrer Active Directory-Gesamtstruktur mit Office 365. Wenn Sie mehrere Active Directory-Gesamtstrukturen haben, die mit Office 365 synchronisiert werden sollen, finden Sie unter [Synchronisierung des aus mehreren Gesamtstrukturen bestehenden Verzeichnisses mit Szenario für einmaliges Anmelden](https://go.microsoft.com/fwlink/p/?LinkId=393091) weitere Informationen. 
  
> [!NOTE]
> Office 365 verwendet für seinen Verzeichnisdienst Azure Active Directory (Azure AD). Ihr Office 365-Abonnement umfasst einen Azure AD-Mandanten. Dieser Mandant kann auch für die Verwaltung der Identitäten Ihrer Organisation mit anderen Cloud-Workloads, einschließlich anderer SaaS-Anwendungen und Apps, in Azure verwendet werden. 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a>Übersicht über die Bereitstellung der Office 365-Verzeichnissynchronisierung in Windows Azure
<a name="Overview"> </a>

Das folgende Diagramm zeigt Azure AD Connect, das auf einem virtuellen Computer in Azure (der DirSync-Server) ausgeführt wird, der eine lokale Windows Server AD-Gesamtstruktur mit einem Office 365-Abonnement synchronisiert.
  
![Azure AD Connect-Tool auf einem virtuellen Computer in Azure beim Synchronisieren von lokalen Konten mit dem Azure AD-Mandanten eines Office 365-Abonnements mit Datenfluss](images/CP_DirSyncOverview.png)
  
In diesem Diagramm gibt es zwei Netzwerke, die über eine Standort-zu-Standort-VPN- oder ExpressRoute-Verbindung verbunden sind. Es gibt ein lokales Netzwerk, in dem Windows Server AD-Domänencontroller enthalten sind, und ein virtuelles Azure-Netzwerk mit einem DirSync-Server, einem virtuellen Computer mit ausgeführtem [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Es gibt zwei Hauptdatenströme, die vom DirSync-Server stammen:
  
-  Azure AD Connect fragt einen Domänencontroller im lokalen Netzwerk auf Änderungen an Benutzerkonten und Kennwörtern ab.
    
-  Azure AD Connect sendet die Änderungen an Konten und Kennwörtern an die Azure AD-Instanz Ihres Office 365-Abonnements. Da der DirSync-Server in einem erweiterten Teil Ihres lokalen Netzwerks vorhanden ist, werden diese Änderungen über den lokalen Netzwerkproxyserver gesendet.
    
> [!NOTE]
> Diese Lösung beschreibt die Synchronisierung einer einzelnen Active Directory-Domäne in einer einzelnen Active Directory-Gesamtstruktur. Azure AD Connect synchronisiert alle Active Directory-Domänen in Ihrer Active Directory-Gesamtstruktur mit Office 365. Wenn Sie mehrere Active Directory-Gesamtstrukturen haben, die mit Office 365 synchronisiert werden sollen, finden Sie unter [Synchronisierung des aus mehreren Gesamtstrukturen bestehenden Verzeichnisses mit Szenario für einmaliges Anmelden](https://go.microsoft.com/fwlink/p/?LinkId=393091) weitere Informationen. 
  
In beiden Fällen wird der Datenverkehr, der von auf dem virtuellen Azure-Computer ausgeführtem Azure AD Connect stammt, an ein Gateway im virtuellen Netzwerk in Azure weitergeleitet, das anschließend den Datenverkehr über die Standort-zu-Standort-VPN- oder die ExpressRoute-Verbindung an das VPN-Gatewaygerät im lokalen Netzwerk weiterleitet. Die Routinginfrastruktur des lokalen Netzwerks leitet dann den Datenverkehr an sein Ziel, z. B. einen Domänencontroller oder einen Proxyserver, weiter.
  
Es gibt bei der Bereitstellung dieser Lösung zwei wichtige Schritte:
  
1. Erstellen eines virtuellen Azure-Netzwerks und Einrichten einer Standort-zu-Standort-VPN-Verbindung mit dem lokalen Netzwerk. Weitere Informationen finden Sie unter [Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Installieren von [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) auf einem einer Domäne beigetretenen virtuellen Computer in Azure und Synchronisieren des lokalen Windows Server AD mit Office 365. Dies umfasst:
    
    Erstellen eines Virtueller Azure-Computer zum Ausführen von Azure AD Connect.
    
    Installieren und Konfigurieren von [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).
    
    Für das Konfigurieren von Azure AD Connect sind die Anmeldeinformationen (Benutzername und Kennwort) eines Azure AD-Administratorkontos und eines Windows Server AD-Unternehmensadministratorkontos erforderlich. Azure AD Connect wird sofort ausgeführt und kann weiterhin fortlaufend die lokale Windows Server AD-Gesamtstruktur mit Office 365 synchronisieren.
    
Bevor Sie diese Lösung in der Produktion bereitstellen, richten Sie diese Konfiguration anhand der Anweisungen unter [DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md) als Nachweis der Wirksamkeit oder für Demonstrations- oder Erprobungszwecke ein.
  
> [!IMPORTANT]
> Wenn die Konfiguration von Azure AD Connect abgeschlossen ist,werden die Anmeldeinformationen für das Windows Server AD-Unternehmensadministratorkonto nicht gespeichert. 
  
> [!NOTE]
> In dieser Lösung wird das Synchronisieren einer einzelnen Windows Server AD-Gesamtstruktur mit Office 365 beschrieben. Die in diesem Artikel beschriebene Topologie stellt nur eine Möglichkeit zur Implementierung dieser Lösung dar. Die Topologie Ihrer Organisation kann basierend auf den jeweiligen Netzwerkanforderungen und Sicherheitsaspekten anders sein. 
  
## <a name="plan-for-hosting-a-dirsync-server-for-office-365-in-azure"></a>Planen des Hostens eines DirSync-Servers für Office 365 in Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Voraussetzungen

Lesen Sie die folgenden Voraussetzungen für diese Lösung, ehe Sie mit diesem Vorgang beginnen:
  
- Überprüfen Sie die dazugehörigen Planungsinhalte in [Planen des virtuellen Azure-Netzwerks](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).
    
- Stellen Sie sicher, dass alle [Voraussetzungen](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) für die Konfiguration des virtuellen Azure-Netzwerks erfüllt sind.
    
- Halten Sie ein Office 365-Abonnement mit Active Directory-Integrationsfeature vor. Informationen zu Office 365-Abonnements finden Sie auf der [Seite zu Office 365-Abonnements](https://go.microsoft.com/fwlink/p/?LinkId=394278).
    
- Stellen Sie einen Virtueller Azure-Computer bereit, auf dem Azure AD Connect zum Synchronisieren Ihrer lokalen Windows Server AD-Gesamtstruktur mit Office 365 ausgeführt wird.
    
    Sie benötigen die Anmeldeinformationen (Namen und Kennwörter) für das Windows Server AD-Unternehmensadministratorkonto und ein Azure Active Directory-Administratorkonto.
    
### <a name="solution-architecture-design-assumptions"></a>Entwurfsannahmen für die Lösungsarchitektur

In der folgenden Liste werden die für diese Lösung getroffenen Design-Entscheidungen beschrieben.
  
- Diese Lösung verwendet ein einzelnes virtuelles Azure-Netzwerk mit einer einzelnen Standort-zu-Standort-VPN-Verbindung. Das virtuelle Azure-Netzwerk hostet ein einzelnes Subnetz, das einen Server, den DirSync-Server mit ausgeführtem Azure AD Connect, enthält. 
    
- Im lokalen Netzwerk sind ein Domänencontroller und DNS-Server vorhanden.
    
- Azure AD Connect wird für die Kennwortsynchronisierung anstatt für das einmalige Anmelden verwendet. Sie müssen keine Infrastruktur für Active Directory-Verbunddienste (AD FS) bereitstellen. Weitere Informationen zu Optionen für einmaliges Anmelden und Kennwortsynchronisierung finden Sie unter [Ermitteln des zu verwendenden Verzeichnisintegrationsszenarios](https://go.microsoft.com/fwlink/p/?LinkId=393094).
    
Es folgen einige weitere Entwurfsoptionen, die Sie berücksichtigen sollten, wenn Sie diese Lösung in Ihrer Umgebung bereitstellen:
  
- Wenn es in einem vorhandenen virtuellen Azure-Netzwerk DNS-Server gibt, bestimmen Sie, ob der DirSync-Server diese für die Namensauflösung anstelle der DNS-Server im lokalen Netzwerk verwenden soll.
    
- Wenn es Domänencontroller in einem vorhandenen virtuellen Azure-Netzwerk gibt, bestimmen Sie, ob die Konfiguration von Active Directory-Standorten und-Diensten ggf. eine bessere Option für Sie ist. Der DirSync-Server kann die Domänencontroller im virtuellen Azure-Netzwerk anstatt die Domänencontroller im lokalen Netzwerk abfragen, um nach Änderungen an Benutzerkonten und Kennwörtern zu suchen.
    
## <a name="deployment-roadmap"></a>Fahrplan für die Bereitstellung
<a name="DeploymentRoadmap"> </a>

Das Bereitstellen von Azure AD Connect auf einem virtuellen Computer in Azure umfasst drei Phasen:
  
- Phase 1: Erstellen und Konfigurieren des virtuellen Azure-Netzwerks
    
- Phase 2: Erstellen und Konfigurieren des virtuellen Azure-Computers
    
- Phase 3: Installieren und Konfigurieren von Azure AD Connect
    
Nach der Bereitstellung müssen Sie auch Orte und Lizenzen für die neuen Benutzerkonten in Office 365 zuweisen.
  
> [!TIP]
> Der [DirSync-Server im Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) enthält alle Azure PowerShell-Blöcke zum Erstellen dieser Lösung, die Diagramme im Microsoft PowerPoint- und Visio-Format sowie eine Microsoft Excel-Konfigurationsarbeitsmappe, die Azure PowerShell-Befehlsblöcke erstellt, die an Ihre Einstellungen angepasst sind.
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Phase 1: Erstellen und Konfigurieren des virtuellen Azure-Netzwerks

Führen Sie zum Erstellen und Konfigurieren des Azure-virtuellen Netzwerks, [Phase 1: Vorbereiten von Ihrem lokalen Netzwerk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) und [Phase 2: Erstellen Sie das virtuelle Netzwerk standortübergreifenden in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in der Bereitstellung Übersicht über [einer lokalen Netzwerk zu verbinden einer Microsoft Azure-virtuelles Netzwerk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Phase 1 des DirSync-Servers für Office 365, gehostet in Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Diese Abbildung zeigt ein lokales Netzwerk, das über eine Standort-zu-Standort-VPN- oder ExpressRoute-Verbindung mit einem virtuellen Azure-Netzwerk verbunden ist.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Phase 2: Erstellen und Konfigurieren des virtuellen Azure-Computers

Erstellen Sie den virtuellen Computer in Azure anhand der Anweisungen unter [Erstellen Ihres ersten virtuellen Windows-Computers im Azure-Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Verwenden Sie die folgenden Einstellungen:
  
- Wählen Sie im Bereich **Grundlagen** das gleiche Abonnement, den gleichen Ort und die gleiche Ressourcengruppe als virtuelles Netzwerk aus. Bewahren Sie den Benutzernamen und das Kennwort an einem sicheren Ort auf. Sie benötigen diese Informationen später für die Verbindung mit dem virtuellen Computer.
    
- Wählen Sie im Bereich zum Auswählen einer **Größe** die Größe **A2 Standard** aus.
    
- Wählen Sie im Bereich **Einstellungen** im Abschnitt **Speicher** den Speichertyp **Standard** aus. Wählen Sie im Abschnitt **Netzwerk** den Namen des virtuellen Netzwerks und das Subnetz zum Hosten des DirSync-Servers (nicht das Gateway-Subnetz). Alle anderen Einstellungen bleiben bei ihren Standardwerten.
    
Stellen Sie sicher, dass der DirSync-Server DNS ordnungsgemäß verwendet. Überprüfen Sie dazu Ihr internes DNS, und vergewissern Sie sich, dass für den virtuellen Computer ein Adresseintrag (A-Datensatz) mit seiner IP-Adresse hinzugefügt wurde. 
  
Befolgen Sie die Anweisungen unter [Herstellen einer Verbindung mit dem virtuellen Computer und Anmelden](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on), um über eine Remotedesktopverbindung eine Verbindung mit dem DirSync-Server herzustellen. Fügen Sie den virtuellen Computer nach dem Anmelden der lokalen Windows Server AD-Domäne hinzu.
  
Damit Azure AD Connect auf Internetressourcen zugreifen kann, müssen Sie den DirSync-Server für die Verwendung des lokalen Netzwerkproxyservers konfigurieren. Wenden Sie sich für mögliche zusätzlichen Konfigurationsschritte an Ihren Netzwerkadministrator.
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Phase 2 des DirSync-Servers für Office 365, gehostet in Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Diese Abbildung zeigt den virtuellen Computer des DirSync-Servers im lokalen virtuellen Azure-Netzwerk.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Phase 3: Installieren und Konfigurieren von Azure AD Connect

Gehen Sie wie folgt vor:
  
1. Stellen Sie mithilfe einer Remotedesktopverbindung mit einem Windows Server AD-Domänenkonto, das über lokale Administratorberechtigungen verfügt, eine Verbindung mit dem DirSync-Server her. Siehe [Herstellen einer Verbindung mit dem virtuellen Computer und Anmelden](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).
    
2. Öffnen Sie auf dem DirSync-Server den Artikel [Einrichten der Verzeichnissynchronisierung in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846), und führen Sie die dort beschriebenen Schritte für die Verzeichnissynchronisierung mit Kennwortsynchronisierung aus.
    
> [!CAUTION]
> Setup erstellt das Konto **AAD_xxxxxxxxxxxx** in der Organisationseinheit (OU) Lokale Benutzer. Verschieben oder entfernen Sie dieses Konto nicht, da dann die Synchronisierung misslingt.
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Phase 3 des DirSync-Servers für Office 365, gehostet in Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Diese Abbildung zeigt den DirSync-Server mit Azure AD Connect im lokalen virtuellen Azure-Netzwerk.
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a>Zuweisen von Orten und Lizenzen zu Benutzern in Office 365

Azure AD Connect fügt Ihrem Office 365-Abonnement Konten vom lokalen Windows Server AD hinzu. Damit sich Benutzer jedoch bei Office 365 anmelden und die Dienste verwenden können, müssen die Konten mit einem Speicherort und Lizenzen konfiguriert werden. Befolgen Sie diese Schritte, um den entsprechenden Benutzerkonten den Ort hinzuzufügen und die Lizenzen für sie zu aktivieren:
  
1. Melden Sie sich auf der [Office 365-Portalseite](https://portal.office.com) an, und klicken Sie dann auf **Administrator**.
    
2. Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
3. Aktivieren Sie in der Liste der Benutzerkonten das Kontrollkästchen neben dem zu aktivierenden Benutzer.
    
4. Klicken Sie auf der Seite für den Benutzer auf **Bearbeiten** für **Produktlizenzen**.
    
5. Wählen Sie auf der Seite **Produktlizenzen** unter **Speicherort** einen Speicherort für den Benutzer aus, und aktivieren Sie dann die entsprechenden Lizenzen für den Benutzer.
    
6. Wenn Sie fertig sind, klicken Sie auf **Speichern**, und klicken Sie dann zweimal auf **Schließen**.
    
7. Kehren Sie zu Schritt 3 zurück, um weitere Benutzer zu bearbeiten.
    
## <a name="see-also"></a>See Also

<a name="DeploymentRoadmap"> </a>

[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
  
[Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Herunterladen von Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Einrichten der Verzeichnissynchronisierung in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[DirSync-Server im Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



