---
title: Bereitstellen der Office 365-Verzeichnissynchronisierung in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Zusammenfassung: Bereitstellen von Azure AD Connect auf einem virtuellen Computer in Azure, um Konten zwischen dem lokalen Verzeichnis und dem Azure AD-Mandanten Ihres Office 365-Abonnements zu synchronisieren.'
ms.openlocfilehash: 31a72d027acd274c9908a7e63e83843bce9cec71
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="78df8-103">Bereitstellen der Office 365-Verzeichnissynchronisierung in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="78df8-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="78df8-104">**Zusammenfassung:**: Bereitstellen von Azure AD Connect auf einem virtuellen Computer in Azure, um Konten zwischen dem lokalen Verzeichnis und dem Azure AD-Mandanten Ihres Office 365-Abonnements zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="78df8-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="78df8-p101">Azure Active Directory (AD) Connect (früher als Directory-Synchronisierungstool oder DirSync.exe-Tool bezeichnet) ist eine Serveranwendung, die Sie auf einem einer Domäne beigetretenen Server zum Synchronisieren Ihrer lokalen Windows Server Active Directory-Benutzer mit dem Azure Active Directory-Mandanten Ihres Office 365-Abonnements installieren. Sie können Azure AD Connect auf einem lokalen Server installieren, doch wir empfehlen aus den folgenden Gründen die Installation auf einem virtuellen Computer in Azure:</span><span class="sxs-lookup"><span data-stu-id="78df8-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="78df8-107">Sie können Cloud-basierte Server schneller bereitstellen und konfigurieren und so die Dienste Ihren Benutzern schneller zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="78df8-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="78df8-108">Azure bietet eine bessere Verfügbarkeit von Websites mit weniger Aufwand.</span><span class="sxs-lookup"><span data-stu-id="78df8-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="78df8-109">Sie können die Anzahl der lokalen Server in Ihrer Organisation verringern.</span><span class="sxs-lookup"><span data-stu-id="78df8-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="78df8-p102">Diese Lösung erfordert Konnektivität zwischen dem lokalen Netzwerk und Ihrem virtuellen Azure-Netzwerk. Weitere Informationen finden Sie unter [Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="78df8-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="78df8-p103">Dieser Artikel beschreibt die Synchronisierung einer einzelnen Domäne in einer einzelnen Gesamtstruktur. Azure AD Connect synchronisiert alle Windows Server AD-Domänen in Ihrer Active Directory-Gesamtstruktur mit Office 365. Wenn Sie mehrere Active Directory-Gesamtstrukturen haben, die mit Office 365 synchronisiert werden sollen, finden Sie unter [Synchronisierung des aus mehreren Gesamtstrukturen bestehenden Verzeichnisses mit Szenario für einmaliges Anmelden](https://go.microsoft.com/fwlink/p/?LinkId=393091) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="78df8-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="78df8-p104">Office 365 verwendet für seinen Verzeichnisdienst Azure Active Directory (Azure AD). Ihr Office 365-Abonnement umfasst einen Azure AD-Mandanten. Dieser Mandant kann auch für die Verwaltung der Identitäten Ihrer Organisation mit anderen Cloud-Workloads, einschließlich anderer SaaS-Anwendungen und Apps, in Azure verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="78df8-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="78df8-118">Übersicht über die Bereitstellung der Office 365-Verzeichnissynchronisierung in Windows Azure</span><span class="sxs-lookup"><span data-stu-id="78df8-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="78df8-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="78df8-119"><a name="Overview"> </a></span></span>

<span data-ttu-id="78df8-120">Das folgende Diagramm zeigt Azure AD Connect, das auf einem virtuellen Computer in Azure (der Verzeichnissynchronisierungsserver) ausgeführt wird, der eine lokale Windows Server AD-Gesamtstruktur mit einem Office 365-Abonnement synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="78df8-120">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Azure AD Connect-Tool auf einem virtuellen Computer in Azure beim Synchronisieren von lokalen Konten mit dem Azure AD-Mandanten eines Office 365-Abonnements mit Datenfluss](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="78df8-p105">In diesem Diagramm gibt es zwei Netzwerke, die über eine Standort-zu-Standort-VPN- oder ExpressRoute-Verbindung verbunden sind. Es gibt ein lokales Netzwerk, in dem Windows Server AD-Domänencontroller enthalten sind, und ein virtuelles Azure-Netzwerk mit einem Verzeichnissynchronisierungsserver, einem virtuellen Computer mit ausgeführtem [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Es gibt zwei Hauptdatenströme, die vom Verzeichnissynchronisierungsserver stammen:</span><span class="sxs-lookup"><span data-stu-id="78df8-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="78df8-125">Azure AD Connect fragt einen Domänencontroller im lokalen Netzwerk auf Änderungen an Benutzerkonten und Kennwörtern ab.</span><span class="sxs-lookup"><span data-stu-id="78df8-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="78df8-p106">Azure AD Connect sendet die Änderungen an Konten und Kennwörtern an die Azure AD-Instanz Ihres Office 365-Abonnements. Da der Verzeichnissynchronisierungsserver in einem erweiterten Teil Ihres lokalen Netzwerks vorhanden ist, werden diese Änderungen über den lokalen Netzwerkproxyserver gesendet.</span><span class="sxs-lookup"><span data-stu-id="78df8-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="78df8-p107">Diese Lösung beschreibt die Synchronisierung einer einzelnen Active Directory-Domäne in einer einzelnen Active Directory-Gesamtstruktur. Azure AD Connect synchronisiert alle Active Directory-Domänen in Ihrer Active Directory-Gesamtstruktur mit Office 365. Wenn Sie mehrere Active Directory-Gesamtstrukturen haben, die mit Office 365 synchronisiert werden sollen, finden Sie unter [Synchronisierung des aus mehreren Gesamtstrukturen bestehenden Verzeichnisses mit Szenario für einmaliges Anmelden](https://go.microsoft.com/fwlink/p/?LinkId=393091) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="78df8-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="78df8-p108">In beiden Fällen wird der Datenverkehr, der von auf dem virtuellen Azure-Computer ausgeführtem Azure AD Connect stammt, an ein Gateway im virtuellen Netzwerk in Azure weitergeleitet, das anschließend den Datenverkehr über die Standort-zu-Standort-VPN- oder die ExpressRoute-Verbindung an das VPN-Gatewaygerät im lokalen Netzwerk weiterleitet. Die Routinginfrastruktur des lokalen Netzwerks leitet dann den Datenverkehr an sein Ziel, z. B. einen Domänencontroller oder einen Proxyserver, weiter.</span><span class="sxs-lookup"><span data-stu-id="78df8-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="78df8-133">Es gibt bei der Bereitstellung dieser Lösung zwei wichtige Schritte:</span><span class="sxs-lookup"><span data-stu-id="78df8-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="78df8-p109">Erstellen eines virtuellen Azure-Netzwerks und Einrichten einer Standort-zu-Standort-VPN-Verbindung mit dem lokalen Netzwerk. Weitere Informationen finden Sie unter [Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="78df8-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="78df8-p110">Installieren von [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) auf einem einer Domäne beigetretenen virtuellen Computer in Azure und Synchronisieren des lokalen Windows Server AD mit Office 365. Dies umfasst:</span><span class="sxs-lookup"><span data-stu-id="78df8-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="78df8-138">Erstellen eines Virtueller Azure-Computer zum Ausführen von Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="78df8-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="78df8-139">Installieren und Konfigurieren von [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="78df8-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="78df8-p111">Für das Konfigurieren von Azure AD Connect sind die Anmeldeinformationen (Benutzername und Kennwort) eines Azure AD-Administratorkontos und eines Windows Server AD-Unternehmensadministratorkontos erforderlich. Azure AD Connect wird sofort ausgeführt und kann weiterhin fortlaufend die lokale Windows Server AD-Gesamtstruktur mit Office 365 synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="78df8-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="78df8-142">Bevor Sie diese Lösung in der Produktion bereitstellen, richten Sie diese Konfiguration anhand der Anweisungen unter [Verzeichnissynchronisierung für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md) als Nachweis der Wirksamkeit oder für Demonstrations- oder Erprobungszwecke ein.</span><span class="sxs-lookup"><span data-stu-id="78df8-142">Before you deploy this solution in production, use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="78df8-143">Wenn die Konfiguration von Azure AD Connect abgeschlossen ist,werden die Anmeldeinformationen für das Windows Server AD-Unternehmensadministratorkonto nicht gespeichert.</span><span class="sxs-lookup"><span data-stu-id="78df8-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="78df8-p112">In dieser Lösung wird das Synchronisieren einer einzelnen Windows Server AD-Gesamtstruktur mit Office 365 beschrieben. Die in diesem Artikel beschriebene Topologie stellt nur eine Möglichkeit zur Implementierung dieser Lösung dar. Die Topologie Ihrer Organisation kann basierend auf den jeweiligen Netzwerkanforderungen und Sicherheitsaspekten anders sein.</span><span class="sxs-lookup"><span data-stu-id="78df8-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="78df8-147">Planen des Hostens eines Verzeichnissynchronisierungsservers für Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="78df8-147">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="78df8-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="78df8-148"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="78df8-149">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="78df8-149">Prerequisites</span></span>

<span data-ttu-id="78df8-150">Lesen Sie die folgenden Voraussetzungen für diese Lösung, ehe Sie mit diesem Vorgang beginnen:</span><span class="sxs-lookup"><span data-stu-id="78df8-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="78df8-151">Überprüfen Sie die dazugehörigen Planungsinhalte in [Planen des virtuellen Azure-Netzwerks](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span><span class="sxs-lookup"><span data-stu-id="78df8-151">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="78df8-152">Stellen Sie sicher, dass alle [Voraussetzungen](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) für die Konfiguration des virtuellen Azure-Netzwerks erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="78df8-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="78df8-p113">Halten Sie ein Office 365-Abonnement mit Active Directory-Integrationsfeature vor. Informationen zu Office 365-Abonnements finden Sie auf der [Seite zu Office 365-Abonnements](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span><span class="sxs-lookup"><span data-stu-id="78df8-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span></span>
    
- <span data-ttu-id="78df8-155">Stellen Sie einen Virtueller Azure-Computer bereit, auf dem Azure AD Connect zum Synchronisieren Ihrer lokalen Windows Server AD-Gesamtstruktur mit Office 365 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="78df8-155">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="78df8-156">Sie benötigen die Anmeldeinformationen (Namen und Kennwörter) für das Windows Server AD-Unternehmensadministratorkonto und ein Azure Active Directory-Administratorkonto.</span><span class="sxs-lookup"><span data-stu-id="78df8-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="78df8-157">Entwurfsannahmen für die Lösungsarchitektur</span><span class="sxs-lookup"><span data-stu-id="78df8-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="78df8-158">In der folgenden Liste werden die für diese Lösung getroffenen Design-Entscheidungen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="78df8-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="78df8-p114">Diese Lösung verwendet ein einzelnes virtuelles Azure-Netzwerk mit einer einzelnen Standort-zu-Standort-VPN-Verbindung. Das virtuelle Azure-Netzwerk hostet ein einzelnes Subnetz, das einen Server, den Verzeichnissynchronisierungsserver mit ausgeführtem Azure AD Connect, enthält.</span><span class="sxs-lookup"><span data-stu-id="78df8-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="78df8-161">Im lokalen Netzwerk sind ein Domänencontroller und DNS-Server vorhanden.</span><span class="sxs-lookup"><span data-stu-id="78df8-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="78df8-p115">Azure Active Directory verbinden führt Hash kennwortsynchronisierung anstelle von einmaliges Anmelden. Sie müssen keinen für die Bereitstellung einer Active Directory-Verbunddienste (AD FS)-Infrastruktur. Finden Sie unter [auswählen die richtige Authentifizierungsmethode für Ihre Azure Active Directory-Identität hybridlösung](http://aka.ms/auth-options), um weitere Informationen über kennwortsynchronisierung Hash und Optionen für einmaliges Anmelden.</span><span class="sxs-lookup"><span data-stu-id="78df8-p115">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="78df8-p116">Es folgen einige weitere Entwurfsoptionen, die Sie berücksichtigen sollten, wenn Sie diese Lösung in Ihrer Umgebung bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="78df8-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="78df8-167">Wenn es in einem vorhandenen virtuellen Azure-Netzwerk DNS-Server gibt, bestimmen Sie, ob der Verzeichnissynchronisierungsserver diese für die Namensauflösung anstelle der DNS-Server im lokalen Netzwerk verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="78df8-167">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="78df8-p117">Wenn es Domänencontroller in einem vorhandenen virtuellen Azure-Netzwerk gibt, bestimmen Sie, ob die Konfiguration von Active Directory-Standorten und-Diensten ggf. eine bessere Option für Sie ist. Der Verzeichnissynchronisierungsserver kann die Domänencontroller im virtuellen Azure-Netzwerk anstatt die Domänencontroller im lokalen Netzwerk abfragen, um nach Änderungen an Benutzerkonten und Kennwörtern zu suchen.</span><span class="sxs-lookup"><span data-stu-id="78df8-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="78df8-170">Fahrplan für die Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="78df8-170">Deployment roadmap</span></span>
<span data-ttu-id="78df8-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="78df8-171"><a name="DeploymentRoadmap"> </a></span></span>

<span data-ttu-id="78df8-172">Das Bereitstellen von Azure AD Connect auf einem virtuellen Computer in Azure umfasst drei Phasen:</span><span class="sxs-lookup"><span data-stu-id="78df8-172">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="78df8-173">Phase 1: Erstellen und Konfigurieren des virtuellen Azure-Netzwerks</span><span class="sxs-lookup"><span data-stu-id="78df8-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="78df8-174">Phase 2: Erstellen und Konfigurieren des virtuellen Azure-Computers</span><span class="sxs-lookup"><span data-stu-id="78df8-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="78df8-175">Phase 3: Installieren und Konfigurieren von Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="78df8-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="78df8-176">Nach der Bereitstellung müssen Sie auch Orte und Lizenzen für die neuen Benutzerkonten in Office 365 zuweisen.</span><span class="sxs-lookup"><span data-stu-id="78df8-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="78df8-177">Der [Verzeichnissynchronisierungsserver im Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) enthält alle Azure PowerShell-Blöcke zum Erstellen dieser Lösung, die Diagramme im Microsoft PowerPoint- und Visio-Format sowie eine Microsoft Excel-Konfigurationsarbeitsmappe, die Azure PowerShell-Befehlsblöcke erstellt, die an Ihre Einstellungen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="78df8-177">The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="78df8-178">Phase 1: Erstellen und Konfigurieren des virtuellen Azure-Netzwerks</span><span class="sxs-lookup"><span data-stu-id="78df8-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="78df8-179">Zum Erstellen und Konfigurieren des virtuellen Azure-Netzwerks durchlaufen Sie [Phase 1: Vorbereitung Ihres lokalen Netzwerks](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) und [Phase 2: Erstellen des standortübergreifenden virtuellen Azure-Netzwerks](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) im Fahrplan für die Bereitstellung von [Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="78df8-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="78df8-180">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="78df8-180">This is your resulting configuration.</span></span>
  
![Phase 1 des Verzeichnissynchronisierungsservers für Office 365, gehostet in Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="78df8-182">Diese Abbildung zeigt ein lokales Netzwerk, das über eine Standort-zu-Standort-VPN- oder ExpressRoute-Verbindung mit einem virtuellen Azure-Netzwerk verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="78df8-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="78df8-183">Phase 2: Erstellen und Konfigurieren des virtuellen Azure-Computers</span><span class="sxs-lookup"><span data-stu-id="78df8-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="78df8-p118">Erstellen Sie den virtuellen Computer in Azure anhand der Anweisungen unter [Erstellen Ihres ersten virtuellen Windows-Computers im Azure-Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Verwenden Sie die folgenden Einstellungen:</span><span class="sxs-lookup"><span data-stu-id="78df8-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="78df8-p119">Wählen Sie im Bereich **Grundlagen** das gleiche Abonnement, den gleichen Ort und die gleiche Ressourcengruppe als virtuelles Netzwerk aus. Bewahren Sie den Benutzernamen und das Kennwort an einem sicheren Ort auf. Sie benötigen diese Informationen später für die Verbindung mit dem virtuellen Computer.</span><span class="sxs-lookup"><span data-stu-id="78df8-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="78df8-189">Wählen Sie im Bereich zum Auswählen einer **Größe** die Größe **A2 Standard** aus.</span><span class="sxs-lookup"><span data-stu-id="78df8-189">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="78df8-p120">Wählen Sie im Bereich **Einstellungen** im Abschnitt **Speicher** den Speichertyp **Standard** aus. Wählen Sie im Abschnitt **Netzwerk** den Namen des virtuellen Netzwerks und das Subnetz zum Hosten des Verzeichnissynchronisierungsservers (nicht das Gateway-Subnetz). Alle anderen Einstellungen bleiben bei ihren Standardwerten.</span><span class="sxs-lookup"><span data-stu-id="78df8-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="78df8-193">Stellen Sie sicher, dass der Verzeichnissynchronisierungsserver DNS ordnungsgemäß verwendet. Überprüfen Sie dazu Ihr internes DNS, und vergewissern Sie sich, dass für den virtuellen Computer ein Adresseintrag (A-Datensatz) mit seiner IP-Adresse hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="78df8-193">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="78df8-p121">Befolgen Sie die Anweisungen unter [Herstellen einer Verbindung mit dem virtuellen Computer und Anmelden](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on), um über eine Remotedesktopverbindung eine Verbindung mit dem Verzeichnissynchronisierungsserver herzustellen. Fügen Sie den virtuellen Computer nach dem Anmelden der lokalen Windows Server AD-Domäne hinzu.</span><span class="sxs-lookup"><span data-stu-id="78df8-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="78df8-p122">Damit Azure AD Connect auf Internetressourcen zugreifen kann, müssen Sie den Verzeichnissynchronisierungsserver für die Verwendung des lokalen Netzwerkproxyservers konfigurieren. Wenden Sie sich für mögliche zusätzlichen Konfigurationsschritte an Ihren Netzwerkadministrator.</span><span class="sxs-lookup"><span data-stu-id="78df8-p122">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="78df8-198">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="78df8-198">This is your resulting configuration.</span></span>
  
![Phase 2 des Verzeichnissynchronisierungsservers für Office 365, gehostet in Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="78df8-200">Diese Abbildung zeigt den virtuellen Computer des Verzeichnissynchronisierungsservers im lokalen virtuellen Azure-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="78df8-200">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="78df8-201">Phase 3: Installieren und Konfigurieren von Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="78df8-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="78df8-202">Gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="78df8-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="78df8-p123">Stellen Sie mithilfe einer Remotedesktopverbindung mit einem Windows Server AD-Domänenkonto, das über lokale Administratorberechtigungen verfügt, eine Verbindung mit dem Verzeichnissynchronisierungsserver her. Siehe [Herstellen einer Verbindung mit dem virtuellen Computer und Anmelden](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span><span class="sxs-lookup"><span data-stu-id="78df8-p123">Connect to the directory sync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="78df8-205">Öffnen Sie auf dem Verzeichnissynchronisierungsserver den Artikel [Einrichten der Verzeichnissynchronisierung in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846), und führen Sie die dort beschriebenen Schritte für die Verzeichnissynchronisierung mit Kennworthashsynchronisierung aus.</span><span class="sxs-lookup"><span data-stu-id="78df8-205">From the directory sync server, open the [Set up directory synchronization in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="78df8-p124">Setup erstellt das Konto **AAD_xxxxxxxxxxxx** in der Organisationseinheit (OU) Lokale Benutzer. Verschieben oder entfernen Sie dieses Konto nicht, da dann die Synchronisierung misslingt.</span><span class="sxs-lookup"><span data-stu-id="78df8-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="78df8-208">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="78df8-208">This is your resulting configuration.</span></span>
  
![Phase 3 des Verzeichnissynchronisierungsservers für Office 365, gehostet in Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="78df8-210">Diese Abbildung zeigt den Verzeichnissynchronisierungsserver mit Azure AD Connect im lokalen virtuellen Azure-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="78df8-210">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="78df8-211">Zuweisen von Orten und Lizenzen zu Benutzern in Office 365</span><span class="sxs-lookup"><span data-stu-id="78df8-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="78df8-p125">Azure AD Connect fügt Ihrem Office 365-Abonnement Konten vom lokalen Windows Server AD hinzu. Damit sich Benutzer jedoch bei Office 365 anmelden und die Dienste verwenden können, müssen die Konten mit einem Speicherort und Lizenzen konfiguriert werden. Befolgen Sie diese Schritte, um den entsprechenden Benutzerkonten den Ort hinzuzufügen und die Lizenzen für sie zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="78df8-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="78df8-214">Melden Sie sich auf der [Office 365-Portalseite](https://portal.office.com) an, und klicken Sie dann auf **Administrator**.</span><span class="sxs-lookup"><span data-stu-id="78df8-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="78df8-215">Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="78df8-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="78df8-216">Aktivieren Sie in der Liste der Benutzerkonten das Kontrollkästchen neben dem zu aktivierenden Benutzer.</span><span class="sxs-lookup"><span data-stu-id="78df8-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="78df8-217">Klicken Sie auf der Seite für den Benutzer auf **Bearbeiten** für **Produktlizenzen**.</span><span class="sxs-lookup"><span data-stu-id="78df8-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="78df8-218">Wählen Sie auf der Seite **Produktlizenzen** unter **Speicherort** einen Speicherort für den Benutzer aus, und aktivieren Sie dann die entsprechenden Lizenzen für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="78df8-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="78df8-219">Wenn Sie fertig sind, klicken Sie auf **Speichern**, und klicken Sie dann zweimal auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="78df8-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="78df8-220">Kehren Sie zu Schritt 3 zurück, um weitere Benutzer zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="78df8-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="78df8-221">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="78df8-221">See Also</span></span>

<span data-ttu-id="78df8-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="78df8-222"><a name="DeploymentRoadmap"> </a></span></span>

[<span data-ttu-id="78df8-223">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="78df8-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="78df8-224">Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="78df8-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="78df8-225">Herunterladen von Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="78df8-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="78df8-226">Einrichten der Verzeichnissynchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="78df8-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="78df8-227">Verzeichnissynchronisierungsserver in Azure Deployment Kit</span><span class="sxs-lookup"><span data-stu-id="78df8-227">Directory Synchronization server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



