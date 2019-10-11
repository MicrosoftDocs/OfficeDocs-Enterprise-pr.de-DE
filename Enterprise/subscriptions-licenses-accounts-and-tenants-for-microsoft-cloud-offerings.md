---
title: Abonnements, Lizenzen, Konten und Mandanten für Microsoft-Cloud-Angebote
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Zusammenfassung: Lernen Sie die Beziehungen von Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über die Microsoft-Cloudangebote hinweg kennen.'
ms.openlocfilehash: 5c0bd0ad10dc1ddfdcb13d09010c69f4e8b5a75a
ms.sourcegitcommit: 2e6fadb5b2b16619ad141b6293d3466460720cb4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2019
ms.locfileid: "37428132"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="5c6df-103">Abonnements, Lizenzen, Konten und Mandanten für Microsoft-Cloud-Angebote</span><span class="sxs-lookup"><span data-stu-id="5c6df-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="5c6df-104">**Zusammenfassung:** Lernen Sie die Beziehungen von Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über die Microsoft-Cloudangebote hinweg kennen.</span><span class="sxs-lookup"><span data-stu-id="5c6df-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="5c6df-105">Microsoft stellt eine Hierarchie von Organisationen, Abonnements, Lizenzen und Benutzerkonten für die konsistente Verwendung von Identitäten und die Abrechnung über seine Cloudangebote hinweg bereit.</span><span class="sxs-lookup"><span data-stu-id="5c6df-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="5c6df-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="5c6df-106">Microsoft Office 365</span></span>
- <span data-ttu-id="5c6df-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="5c6df-107">Microsoft Azure</span></span>
- <span data-ttu-id="5c6df-108">Microsoft Intune und Enterprise Mobility + Security (EMS)</span><span class="sxs-lookup"><span data-stu-id="5c6df-108">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
- <span data-ttu-id="5c6df-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5c6df-109">Microsoft Dynamics 365</span></span>

<span data-ttu-id="5c6df-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) kombiniert Office 365, EMS und Windows 10 Enterprise in einem einzigen Abonnement und einer Reihe integrierter Dienste.</span><span class="sxs-lookup"><span data-stu-id="5c6df-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) combines Office 365, EMS, and Windows 10 Enterprise into a single subscription and set of integrated services.</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="5c6df-111">Elemente der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="5c6df-111">Elements of the hierarchy</span></span>

<span data-ttu-id="5c6df-112">Dies sind die Elemente der Hierarchie:</span><span class="sxs-lookup"><span data-stu-id="5c6df-112">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="5c6df-113">Organization (Organisation)</span><span class="sxs-lookup"><span data-stu-id="5c6df-113">Organization</span></span>

<span data-ttu-id="5c6df-p101">Eine Organisation stellt eine Wirtschaftseinheit dar, die Microsoft-Cloudangebote verwendet und in der Regel von einem oder mehreren öffentlichen DNS-Domänennamen (Domain Name System) identifiziert wird, z. B. contoso.com. Die Organisation ist ein Container für Abonnements.</span><span class="sxs-lookup"><span data-stu-id="5c6df-p101">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="5c6df-116">Abonnements</span><span class="sxs-lookup"><span data-stu-id="5c6df-116">Subscriptions</span></span>

<span data-ttu-id="5c6df-117">Ein Abonnement ist eine Vereinbarung mit Microsoft zur Verwendung einer oder mehrerer Cloudplattformen oder -dienste, für die basierend auf einer Lizenzgebühr pro Benutzer oder einem cloudbasierten Ressourcenverbrauch Kosten anfallen.</span><span class="sxs-lookup"><span data-stu-id="5c6df-117">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="5c6df-118">Bei den SaaS-basierten (Software-as-a-Service) Cloudangeboten von Microsoft (Office 365, Intune/EMS und Dynamics 365) werden Lizenzgebühren pro Benutzer abgerechnet.</span><span class="sxs-lookup"><span data-stu-id="5c6df-118">Microsoft’s Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="5c6df-119">Bei den PaaS- und IaaS-Cloudangeboten (Platform-as-a-Service; Infrastructure-as-a-Service) von Microsoft (Azure) wird basierend auf dem Ressourcenverbrauch in der Cloud abgerechnet.</span><span class="sxs-lookup"><span data-stu-id="5c6df-119">Microsoft’s Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="5c6df-p102">Sie können auch ein Testabonnement verwenden, das Abonnement läuft jedoch nach einem bestimmten Zeitraum oder einem bestimmten Betrag von Verbrauchsgebühren ab. Sie können ein Testabonnement in ein kostenpflichtiges Abonnement umwandeln.</span><span class="sxs-lookup"><span data-stu-id="5c6df-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="5c6df-122">Organisationen können mehrere Abonnements für die Cloudangebote von Microsoft haben.</span><span class="sxs-lookup"><span data-stu-id="5c6df-122">Organizations can have multiple subscriptions for Microsoft’s cloud offerings.</span></span> <span data-ttu-id="5c6df-123">Abbildung 1 zeigt eine einzelne Organisation mit mehreren Office 365-Abonnements, einem Intune-Abonnement, einem Dynamics 365-Abonnement und mehreren Azure-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="5c6df-123">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="5c6df-124">**Abbildung 1: Beispiel für eine Organisation mit mehreren Abonnements**</span><span class="sxs-lookup"><span data-stu-id="5c6df-124">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Eine Beispielorganisation mit mehreren Abonnements für Microsoft Cloud-Angebote.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a><span data-ttu-id="5c6df-126">Lizenzen</span><span class="sxs-lookup"><span data-stu-id="5c6df-126">Licenses</span></span>

<span data-ttu-id="5c6df-127">Bei den SaaS-Cloudangeboten von Microsoft ermöglicht eine Lizenz einem bestimmten Benutzerkonto, die Dienste des Cloudangebots zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="5c6df-127">For Microsoft’s SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="5c6df-128">Ihnen wird eine feste monatliche Gebühr als Teils Ihres Abonnements in Rechnung gestellt.</span><span class="sxs-lookup"><span data-stu-id="5c6df-128">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="5c6df-129">Administratoren weisen Lizenzen einzelnen Benutzerkonten in dem Abonnement zu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-129">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="5c6df-130">Für das Beispiel in Abbildung 2 verfügt die Contoso Corporation über ein Office 365 Enterprise E5-Abonnement mit 100 Lizenzen, mit dem bis zu 100 einzelne Benutzerkonten die Features und Dienste von Office 365 Enterprise E5 nutzen können.</span><span class="sxs-lookup"><span data-stu-id="5c6df-130">For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="5c6df-131">**Abbildung 2: Lizenzen innerhalb der SaaS-basierten Abonnements für eine Organisation**</span><span class="sxs-lookup"><span data-stu-id="5c6df-131">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Ein Beispiel für mehrere Lizenzen innerhalb von Abonnements für auf SaaS-basierende Microsoft-Cloudangebote.](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="5c6df-133">Bei PaaS-basierten Azure-Clouddiensten sind Softwarelizenzen in den Dienstpreis integriert.</span><span class="sxs-lookup"><span data-stu-id="5c6df-133">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="5c6df-p105">Bei IaaS-basierten virtuellen Azure-Computern sind möglicherweise zusätzliche Lizenzen zur Nutzung der Software oder der Anwendung erforderlich, die auf einem virtuellen Computerabbild installiert ist. Einige virtuelle Computerabbilder weisen lizenzierte Versionen der installierten Software auf, und die Kosten sind in dem Minutenpreis für den Server enthalten. Beispiele hierfür sind die virtuellen Computerabbilder für SQL Server 2014 und SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="5c6df-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="5c6df-p106">Einige virtuelle Computerabbilder verfügen über Testversionen von installierten Anwendungen und benötigen zusätzliche Softwareanwendungslizenzen für die Verwendung über den Testzeitraum hinaus. Auf dem virtuellen Computerabbild der Testversion von SharePoint Server 2016 ist beispielsweise eine Testversion von SharePoint Server 2016 vorinstalliert. Um SharePoint Server 2016 nach dem Ablaufdatum der Testversion weiter zu verwenden, müssen Sie eine Lizenz für SharePoint Server 2016 und Clientlizenzen von Microsoft erwerben. Diese Gebühren fallen separat zum Azure-Abonnement an, und der Minutenpreis für das Ausführen des zugrunde liegenden virtuellen Computers tritt weiterhin zu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trail expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="5c6df-141">Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="5c6df-141">User accounts</span></span>

<span data-ttu-id="5c6df-142">Benutzerkonten für alle Microsoft-Cloudangebote werden in einem Azure AD-Mandanten (Azure AD) gespeichert, der Benutzerkonten und -gruppen enthält.</span><span class="sxs-lookup"><span data-stu-id="5c6df-142">User accounts for all of Microsoft’s cloud offerings are stored in an Azure Active Directory (AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="5c6df-143">Ein Azure AD-Mandant kann mit Ihren vorhandenen Active Directory Domain Services (AD DS)-Konten mithilfe von Azure AD Connect, einem Windows Server-basierten Dienst, synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="5c6df-143">An Azure AD tenant can be synchronized with your existing Windows Server AD accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="5c6df-144">Dies wird als Verzeichnissynchronisation oder DirSync bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5c6df-144">This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="5c6df-145">Abbildung 3 zeigt ein Beispiel für mehrere Abonnements einer Organisation, die einen allgemeinen Azure AD-Mandanten verwendet, der die Konten der Organisation enthält.</span><span class="sxs-lookup"><span data-stu-id="5c6df-145">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="5c6df-146">**Abbildung 3: Mehrere Abonnements einer Organisation, die den gleichen Azure AD-Mandanten verwenden**</span><span class="sxs-lookup"><span data-stu-id="5c6df-146">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![Eine Beispielorganisation mit mehreren Abonnements, die alle den gleichen Azure AD-Mandanten verwenden.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="5c6df-148">Mandanten</span><span class="sxs-lookup"><span data-stu-id="5c6df-148">Tenants</span></span>

<span data-ttu-id="5c6df-p108">Bei SaaS-Cloudangeboten ist der Mandant die regionale Stelle, an der sich die Server befinden, die Clouddienste bereitstellen. Die Contoso Corporation hat beispielsweise Europa als Region zum Hosten ihrer Office 365-, EMS- und Dynamics 365-Mandanten für die 15.000 Mitarbeiter in der Zentrale in Paris festgelegt.</span><span class="sxs-lookup"><span data-stu-id="5c6df-p108">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="5c6df-p109">Azure PaaS-Dienste und in Azure IaaS gehostete VM-basierte Arbeitslasten können Mandanten in einem beliebigen Azure-Rechenzentrum auf der ganzen Welt haben. Sie geben das Azure-Rechenzentrum an, das als Standort bezeichnet wird, wenn Sie die Azure PaaS-App oder den Dienst bzw. das Element einer IaaS-IT-Arbeitslast erstellen.</span><span class="sxs-lookup"><span data-stu-id="5c6df-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="5c6df-p110">Bei einem Azure AD-Mandanten handelt es sich um eine bestimmte Instanz von Azure AD, die Konten und Gruppen enthält. Kostenpflichtige oder Testabonnements von Office 365, Dynamics 365 oder Intune/EMS enthalten einen kostenlosen Azure AD-Mandanten. Dieser Azure AD-Mandant enthält keine anderen Azure-Dienste und ist nicht das gleiche wie ein Azure-Testabonnement oder ein kostenpflichtiges Azure-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="5c6df-p110">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="5c6df-156">Zusammenfassung der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="5c6df-156">Summary of the hierarchy</span></span>

<span data-ttu-id="5c6df-157">Es folgt eine kurze Wiederholung:</span><span class="sxs-lookup"><span data-stu-id="5c6df-157">Here is a quick recap:</span></span>
  
- <span data-ttu-id="5c6df-158">Eine Organisation kann mehrere Abonnements haben.</span><span class="sxs-lookup"><span data-stu-id="5c6df-158">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="5c6df-159">Ein Abonnement kann mehrere Lizenzen haben.</span><span class="sxs-lookup"><span data-stu-id="5c6df-159">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="5c6df-160">Lizenzen können einzelnen Benutzerkonten zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="5c6df-160">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="5c6df-161">Benutzerkonten werden in einem Azure AD-Mandanten gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5c6df-161">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="5c6df-162">Im Folgenden finden Sie ein Beispiel für die Beziehung von Organisationen, Abonnements, Lizenzen und Benutzerkonten:</span><span class="sxs-lookup"><span data-stu-id="5c6df-162">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="5c6df-163">Eine durch ihre öffentlichen Domänennamen identifizierte Organisation.</span><span class="sxs-lookup"><span data-stu-id="5c6df-163">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="5c6df-164">Ein Office 365 Enterprise E3-Abonnement mit Benutzerlizenzen.</span><span class="sxs-lookup"><span data-stu-id="5c6df-164">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="5c6df-165">Ein Office 365 Enterprise E5-Abonnement mit Benutzerlizenzen.</span><span class="sxs-lookup"><span data-stu-id="5c6df-165">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="5c6df-166">Ein EMS-Abonnement mit Benutzerlizenzen.</span><span class="sxs-lookup"><span data-stu-id="5c6df-166">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="5c6df-167">Ein Dynamics 365-Abonnement mit Benutzerlizenzen.</span><span class="sxs-lookup"><span data-stu-id="5c6df-167">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="5c6df-168">Mehrere Azure-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="5c6df-168">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="5c6df-169">Die Benutzerkonten der Organisation in einem gemeinsamen Azure AD-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="5c6df-169">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="5c6df-170">Mehrere Abonnements für Cloudangebote von Microsoft können denselben Azure AD-Mandanten verwenden, der als gemeinsamer Identitätsanbieter fungiert.</span><span class="sxs-lookup"><span data-stu-id="5c6df-170">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="5c6df-171">Ein zentraler Azure AD-Mandant, der die synchronisierten Konten Ihrer lokalen AD DS enthält, stellt eine cloudbasierte IDaaS (Identity-as-a-Service) für Ihre Organisation bereit.</span><span class="sxs-lookup"><span data-stu-id="5c6df-171">A central Azure AD tenant that contains the synchronized accounts of your on-premises Windows Server AD provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="5c6df-172">**Abbildung 4: Synchronisierte lokale Konten und IDaaS für eine Organisation**</span><span class="sxs-lookup"><span data-stu-id="5c6df-172">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![IDaaS (Identity as a Service) für Ihre Organisation.](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="5c6df-p112">In Abbildung 4 wird gezeigt, wie ein gemeinsamer Azure AD-Mandant von Microsoft-SaaS-Cloudangeboten, Azure PaaS-Apps und virtuellen Computern in Azure IaaS verwendet wird, die Azure AD-Domänendienste verwenden. Die lokale AD DS-Gesamtstruktur wird mithilfe von Azure AD Connect mit dem Azure AD-Mandanten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="5c6df-p112">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="5c6df-176">Kombinieren von Abonnements für mehrere Microsoft-Cloudangebote</span><span class="sxs-lookup"><span data-stu-id="5c6df-176">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="5c6df-177">Die folgende Tabelle beschreibt, wie Sie mehrere Microsoft-Cloudangebote basierend auf dem Vorhandensein eines Abonnement für einen Typ von Cloudangebot (die Bezeichnungen laufen in der ersten Spalte nach unten) und dem Hinzufügen eines Abonnements für ein anderes Cloudangebot (von links nach rechts) kombinieren können.</span><span class="sxs-lookup"><span data-stu-id="5c6df-177">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="5c6df-178">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="5c6df-178">**Office 365**</span></span>|<span data-ttu-id="5c6df-179">**Azure**</span><span class="sxs-lookup"><span data-stu-id="5c6df-179">**Azure**</span></span>|<span data-ttu-id="5c6df-180">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="5c6df-180">**Intune/EMS**</span></span>|<span data-ttu-id="5c6df-181">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="5c6df-181">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="5c6df-182">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="5c6df-182">**Office 365**</span></span> <br/> |<span data-ttu-id="5c6df-183">–</span><span class="sxs-lookup"><span data-stu-id="5c6df-183">NA</span></span>  <br/> |<span data-ttu-id="5c6df-184">Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-184">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="5c6df-185">Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation aus dem Microsoft 365 Admin Center hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-185">You add an Intune/EMS subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |<span data-ttu-id="5c6df-186">Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation aus dem Microsoft 365 Admin Center hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-186">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="5c6df-187">**Azure**</span><span class="sxs-lookup"><span data-stu-id="5c6df-187">**Azure**</span></span> <br/> |<span data-ttu-id="5c6df-188">Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-188">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="5c6df-189">–</span><span class="sxs-lookup"><span data-stu-id="5c6df-189">NA</span></span>  <br/> |<span data-ttu-id="5c6df-190">Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-190">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="5c6df-191">Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-191">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="5c6df-192">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="5c6df-192">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="5c6df-193">Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="5c6df-194">Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-194">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="5c6df-195">–</span><span class="sxs-lookup"><span data-stu-id="5c6df-195">NA</span></span>  <br/> |<span data-ttu-id="5c6df-196">Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="5c6df-197">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="5c6df-197">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="5c6df-198">Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="5c6df-199">Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="5c6df-200">Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-200">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="5c6df-201">NV</span><span class="sxs-lookup"><span data-stu-id="5c6df-201">NA</span></span>  <br/> |
   
<span data-ttu-id="5c6df-202">Eine einfache Möglichkeit zum Hinzufügen von Abonnements zu Ihrer Organisation für Microsoft SaaS-basierte Dienste erfolgt über das Admin Center:</span><span class="sxs-lookup"><span data-stu-id="5c6df-202">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the Office 365 Admin center:</span></span>
  
1. <span data-ttu-id="5c6df-203">Melden Sie sich mit Ihrem globalen Administratorkonto beim Microsoft 365 Admin Center ([https://admin.microsoft.com](https://admin.microsoft.com)) an.</span><span class="sxs-lookup"><span data-stu-id="5c6df-203">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="5c6df-204">Klicken Sie im linken Navigationsbereich der **Admin Center**-Startseite auf **Abrechnung** und dann auf **Dienste kaufen**.</span><span class="sxs-lookup"><span data-stu-id="5c6df-204">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="5c6df-205">Erwerben Sie auf der Seite **Dienste kaufen** Ihre neuen Abonnements.</span><span class="sxs-lookup"><span data-stu-id="5c6df-205">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="5c6df-206">Das Admin Center ordnet die Organisation und den Azure AD-Mandanten Ihres Office 365-Abonnements den neuen Abonnements für SaaS-basierte Cloudangebote zu.</span><span class="sxs-lookup"><span data-stu-id="5c6df-206">The Office 365 Admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="5c6df-207">So fügen Sie ein Azure-Abonnement mit derselben Organisation und demselben Azure AD-Mandanten wie das Office 365-Abonnement hinzu</span><span class="sxs-lookup"><span data-stu-id="5c6df-207">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="5c6df-208">Melden Sie sich mit Ihrem globalen Office 365-Administratorkonto beim Azure-Portal ([https://portal.azure.com](https://portal.azure.com)) an.</span><span class="sxs-lookup"><span data-stu-id="5c6df-208">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="5c6df-209">Klicken Sie im linken Navigationsbereich auf **Abonnements** und dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="5c6df-209">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="5c6df-210">Wählen Sie auf der Seite **Abonnement hinzufügen** ein Angebot aus, und schließen Sie die Bezahlung und die Vereinbarung ab.</span><span class="sxs-lookup"><span data-stu-id="5c6df-210">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="5c6df-211">Wenn Sie die Abonnements für Azure und Office 365 einzeln erworben haben und den Office 365 Azure AD-Mandanten von Ihrem Azure-Abonnement aus aufrufen möchten, finden Sie entsprechende Anweisungen unter [Hinzufügen eines vorhandenen Azure-Abonnements zu Ihrem Azure Active Directory-Mandanten](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span><span class="sxs-lookup"><span data-stu-id="5c6df-211">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Associate an Office 365 tenant with an Azure subscription](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="5c6df-212">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5c6df-212">See also</span></span>

[<span data-ttu-id="5c6df-213">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="5c6df-213">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="5c6df-214">Architekturmodelle für SharePoint, Exchange, Skype for Business und Lync</span><span class="sxs-lookup"><span data-stu-id="5c6df-214">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="5c6df-215">Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="5c6df-215">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="5c6df-216">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="5c6df-216">Next step</span></span>

[<span data-ttu-id="5c6df-217">Bewerten der Office 365-Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="5c6df-217">Office 365 network connectivity principles</span></span>](assessing-network-connectivity.md)
  
