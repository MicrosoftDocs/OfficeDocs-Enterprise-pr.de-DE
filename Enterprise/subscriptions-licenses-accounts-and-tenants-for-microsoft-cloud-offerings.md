---
title: "Abonnements, Lizenzen, Konten und Mandanten für Microsoft Cloud-angeboten"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: "Zusammenfassung: Grundlegendes zu den Beziehungen zwischen Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über Microsoft Cloud-angeboten."
ms.openlocfilehash: a1bcc040d046e4e5674f16432aeffb0a34b9031b
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="a7c25-103">Abonnements, Lizenzen, Konten und Mandanten für Microsoft Cloud-angeboten</span><span class="sxs-lookup"><span data-stu-id="a7c25-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="a7c25-104">**Zusammenfassung:** Verstehen der Beziehungen zwischen Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über Microsoft Cloud-angeboten.</span><span class="sxs-lookup"><span data-stu-id="a7c25-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="a7c25-105">Microsoft bietet eine Hierarchie von Organisationen, Abonnements, Lizenzen und Benutzerkonten für die konsistente Verwendung von Identitäten und Abrechnung über die Cloud-angeboten:</span><span class="sxs-lookup"><span data-stu-id="a7c25-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="a7c25-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="a7c25-106">Microsoft Office 365</span></span>
    
    <span data-ttu-id="a7c25-107">Finden Sie unter [Geschäftspläne und zu Preisen](https://products.office.com/business/compare-office-365-for-business-plans) für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="a7c25-107">See [business plans and pricing](https://products.office.com/business/compare-office-365-for-business-plans) for more information.</span></span>
    
- <span data-ttu-id="a7c25-108">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a7c25-108">Microsoft Azure</span></span>
    
    <span data-ttu-id="a7c25-109">Weitere Informationen finden Sie unter [Azure Preise](https://azure.microsoft.com/pricing/) .</span><span class="sxs-lookup"><span data-stu-id="a7c25-109">See [Azure pricing](https://azure.microsoft.com/pricing/) for more information.</span></span>
    
- <span data-ttu-id="a7c25-110">Microsoft Intune und der Enterprise-Mobilität + Sicherheit (zur Abstimmung)</span><span class="sxs-lookup"><span data-stu-id="a7c25-110">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
    
    <span data-ttu-id="a7c25-111">Weitere Informationen finden Sie unter [Intune Preise](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) .</span><span class="sxs-lookup"><span data-stu-id="a7c25-111">See [Intune pricing](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) for more information.</span></span>
    
- <span data-ttu-id="a7c25-112">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a7c25-112">Microsoft Dynamics 365</span></span>
    
    <span data-ttu-id="a7c25-113">Weitere Informationen finden Sie unter [Dynamics 365 Preise](https://dynamics.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="a7c25-113">See [Dynamics 365 pricing](https://dynamics.microsoft.com/) for more information.</span></span>
    
## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="a7c25-114">Elemente der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="a7c25-114">Elements of the hierarchy</span></span>

<span data-ttu-id="a7c25-115">Dies sind die Elemente der Hierarchie:</span><span class="sxs-lookup"><span data-stu-id="a7c25-115">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="a7c25-116">Organisation</span><span class="sxs-lookup"><span data-stu-id="a7c25-116">Organization</span></span>

<span data-ttu-id="a7c25-117">Eine Organisation stellt eine Wirtschaftseinheit dar, die Microsoft-Cloudangebote verwendet und in der Regel von einem öffentlichen DNS-Domänennamen (Domain Name System) identifiziert wird, z. B. contoso.com. Die Organisation ist ein Container für Abonnements.</span><span class="sxs-lookup"><span data-stu-id="a7c25-117">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by a public Domain Name System (DNS) domain name such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="a7c25-118">Abonnements</span><span class="sxs-lookup"><span data-stu-id="a7c25-118">Subscriptions</span></span>

<span data-ttu-id="a7c25-p101">Ein Abonnement ist eine Vereinbarung mit Microsoft eine oder mehrere Microsoft Cloud-Plattformen oder Dienste, für die Gebühren für fällig basierend auf eine benutzerbasierte Lizenzgebühr oder cloudbasierten Ressourcenverbrauch. Microsoft Software-as a Service (SaaS)-Basis Cloudlösungen (Office 365, Intune/zur Abstimmung und Dynamics 365) Gebühren pro-Benutzer-Lizenz. Microsoft Plattform als Service (PaaS) und als (IaaS) Cloud Dienstangebote (Azure) Servicekosten basierend auf Ressourcenverbrauch Cloud-Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p101">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption. Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees. Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
  
<span data-ttu-id="a7c25-p102">Sie können auch ein Testabonnement verwenden, das Abonnement läuft jedoch nach einem bestimmten Zeitraum oder einem bestimmten Betrag von Verbrauchsgebühren ab. Sie können ein Testabonnement in ein kostenpflichtiges Abonnement umwandeln.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="a7c25-p103">Organisationen können mehrere Abonnements für Microsoft Cloud-angeboten haben. Abbildung 1 zeigt ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p103">Organizations can have multiple subscriptions for Microsoft's cloud offerings. Figure 1 shows an example.</span></span>
  
<span data-ttu-id="a7c25-126">**Abbildung 1: Beispiel für eine Organisation mehrere Abonnements**</span><span class="sxs-lookup"><span data-stu-id="a7c25-126">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Eine Beispielorganisation mit mehreren Abonnements für Microsoft Cloud-Angebote.](images/Subscriptions/Subscriptions_Fig1.png)

  
<span data-ttu-id="a7c25-128">Abbildung 1 zeigt eine einzelne Organisation mit mehreren Office 365-Abonnements, einem Intune-Abonnement, einem Dynamics 365-Abonnement und mehrere Azure-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="a7c25-128">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>
  
### <a name="licenses"></a><span data-ttu-id="a7c25-129">Lizenzen</span><span class="sxs-lookup"><span data-stu-id="a7c25-129">Licenses</span></span>

<span data-ttu-id="a7c25-p104">SaaS Cloudlösungen von Microsoft, eine Lizenz ermöglicht ein bestimmtes Benutzerkonto zu verwenden, die der Cloud-Dienste bietet. Sie werden im Rahmen Ihres Abonnements eine feste monatliche Gebühr erhoben. Administratoren weisen Lizenzen einzelnen Benutzerkonten im Abonnement. Für das Beispiel in Abbildung 2 hat der Contoso Corporation E5 für Office 365 Enterprise-Abonnement mit 100 Lizenzen, wodurch bis zu 100 einzelnen Benutzerkonten E5 Enterprise-Features und Dienste verwendet.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p104">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering. You are charged a fixed monthly fee as part of your subscription. Administrators assign licenses to individual user accounts in the subscription. For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="a7c25-134">**Abbildung 2: Lizenzen innerhalb der SaaS-basierte Abonnements für eine Organisation**</span><span class="sxs-lookup"><span data-stu-id="a7c25-134">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Ein Beispiel für mehrere Lizenzen innerhalb von Abonnements für auf SaaS-basierende Microsoft Cloud-Angebote.](images/Subscriptions/Subscriptions_Fig2.png)
  
<span data-ttu-id="a7c25-136">Bei PaaS-basierten Azure-Clouddiensten sind Softwarelizenzen in den Dienstpreis integriert.  </span><span class="sxs-lookup"><span data-stu-id="a7c25-136">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="a7c25-p105">Bei IaaS-basierten virtuellen Azure-Computern sind möglicherweise zusätzliche Lizenzen zur Nutzung der Software oder der Anwendung erforderlich, die auf einem virtuellen Computerabbild installiert ist. Einige virtuelle Computerabbilder weisen lizenzierte Versionen der installierten Software auf, und die Kosten sind in dem Minutenpreis für den Server enthalten. Beispiele hierfür sind die virtuellen Computerabbilder für SQL Server 2014 und SQL Server 2016. </span><span class="sxs-lookup"><span data-stu-id="a7c25-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="a7c25-p106">Einige virtuelle Computerabbilder verfügen über Testversionen von installierten Anwendungen und benötigen zusätzliche Softwareanwendungslizenzen für die Verwendung über den Testzeitraum hinaus. Auf dem virtuellen Computerabbild der Testversion von SharePoint Server 2016 ist beispielsweise eine Testversion von SharePoint Server 2016 vorinstalliert. Um SharePoint Server 2016 nach dem Ablaufdatum der Testversion weiter zu verwenden, müssen Sie eine Lizenz für SharePoint Server 2016 und Clientlizenzen von Microsoft erwerben. Diese Gebühren fallen separat zum Azure-Abonnement an, und der Minutenpreis für das Ausführen des zugrunde liegenden virtuellen Computers tritt weiterhin zu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trail expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="a7c25-144">Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="a7c25-144">User accounts</span></span>

<span data-ttu-id="a7c25-p107">Benutzerkonten für alle Microsoft Cloud-angeboten werden in einem Mandanten Azure Active Directory (AD) gespeichert, die Benutzerkonten und Gruppen enthält. Ein Azure AD-Mandanten kann Ihrer vorhandenen Windows Azure AD-Konten mit Azure Active Directory verbinden, eine Windows Server-basierten Dienst synchronisiert werden. Dies wird als verzeichnissynchronisierung (DirSync) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p107">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (AD) tenant, which contains user accounts and groups. An Azure AD tenant can be synchronized with your existing Windows Server AD accounts using Azure AD Connect, a Windows server-based service. This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="a7c25-148">Abbildung 3 zeigt ein Beispiel für mehrere Abonnements einer Organisation, die einen allgemeinen Azure AD-Mandanten verwendet, der die Konten der Organisation enthält.</span><span class="sxs-lookup"><span data-stu-id="a7c25-148">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="a7c25-149">**Abbildung 3: Mehrere Abonnements einer Organisation, die den gleichen Azure AD-Mandanten verwenden**</span><span class="sxs-lookup"><span data-stu-id="a7c25-149">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![Eine Beispielorganisation mit mehreren Abonnements, die alle den gleichen Azure AD-Mandanten verwenden.](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="a7c25-151">Mandanten</span><span class="sxs-lookup"><span data-stu-id="a7c25-151">Tenants</span></span>

<span data-ttu-id="a7c25-p108">Bei SaaS-Cloudangeboten ist der Mandant die regionale Stelle, an der sich die Server befinden, die Clouddienste bereitstellen. Die Contoso Corporation hat beispielsweise Europa als Region zum Hosten ihrer Office 365-, EMS- und Dynamics 365-Mandanten für die 15.000 Mitarbeiter in der Zentrale in Paris festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p108">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="a7c25-p109">Azure PaaS-Dienste und in Azure IaaS gehostete VM-basierte Arbeitslasten können Mandanten in einem beliebigen Azure-Rechenzentrum auf der ganzen Welt haben. Sie geben das Azure-Rechenzentrum an, das als Standort bezeichnet wird, wenn Sie die Azure PaaS-App oder den Dienst bzw. das Element einer IaaS-IT-Arbeitslast erstellen.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="a7c25-p110">Bei einem Azure AD-Mandanten handelt es sich um eine bestimmte Instanz von Azure AD, die Konten und Gruppen enthält. Kostenpflichtige oder Testabonnements von Office 365, Dynamics 365 oder Intune/EMS enthalten einen kostenlosen Azure AD-Mandanten. Dieser Azure AD-Mandant enthält keine anderen Azure-Dienste und ist nicht das gleiche wie ein Azure-Testabonnement oder ein kostenpflichtiges Azure-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p110">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="a7c25-159">Zusammenfassung der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="a7c25-159">Summary of the hierarchy</span></span>

<span data-ttu-id="a7c25-160">Es folgt eine kurze Wiederholung:</span><span class="sxs-lookup"><span data-stu-id="a7c25-160">Here is a quick recap:</span></span>
  
- <span data-ttu-id="a7c25-161">Eine Organisation kann mehrere Abonnements haben.</span><span class="sxs-lookup"><span data-stu-id="a7c25-161">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="a7c25-162">Ein Abonnement kann mehrere Lizenzen haben.</span><span class="sxs-lookup"><span data-stu-id="a7c25-162">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="a7c25-163">Lizenzen können einzelnen Benutzerkonten zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="a7c25-163">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="a7c25-164">Benutzerkonten werden in einem Azure AD-Mandanten gespeichert.</span><span class="sxs-lookup"><span data-stu-id="a7c25-164">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="a7c25-165">Im Folgenden finden Sie ein Beispiel für die Beziehung von Organisationen, Abonnements, Lizenzen und Benutzerkonten:</span><span class="sxs-lookup"><span data-stu-id="a7c25-165">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="a7c25-166">Eine durch ihre öffentlichen Domänennamen identifizierte Organisation.</span><span class="sxs-lookup"><span data-stu-id="a7c25-166">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="a7c25-167">Ein Office 365 Enterprise E3-Abonnement mit Benutzerlizenzen.</span><span class="sxs-lookup"><span data-stu-id="a7c25-167">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="a7c25-168">Ein Office 365 Enterprise E5-Abonnement mit Benutzerlizenzen.</span><span class="sxs-lookup"><span data-stu-id="a7c25-168">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="a7c25-169">Ein EMS-Abonnement mit Benutzerlizenzen.</span><span class="sxs-lookup"><span data-stu-id="a7c25-169">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="a7c25-170">Ein Dynamics 365-Abonnement mit Benutzerlizenzen.</span><span class="sxs-lookup"><span data-stu-id="a7c25-170">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="a7c25-171">Mehrere Azure-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="a7c25-171">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="a7c25-172">Die Benutzerkonten der Organisation in einem gemeinsamen Azure AD-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="a7c25-172">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="a7c25-p111">Mehrere Abonnements für Cloudangebote von Microsoft können denselben Azure AD-Mandanten verwenden, der als gemeinsamer Identitätsanbieter fungiert. Ein zentraler Azure AD-Mandant, der die synchronisierten Konten Ihres lokalen Windows Server AD enthält, stellt eine cloudbasierte IDaaS (Identity-as-a-Service) für Ihre Organisation bereit. Dies ist in Abbildung 4 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p111">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider. A central Azure AD tenant that contains the synchronized accounts of your on-premises Windows Server AD provides cloud-based Identity as a Service (IDaaS) for your organization. This is shown in Figure 4.</span></span>
  
<span data-ttu-id="a7c25-176">**Abbildung 4: Synchronisierten lokalen Konten und IDaaS für eine Organisation**</span><span class="sxs-lookup"><span data-stu-id="a7c25-176">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![IDaaS (Identity as a Service) für Ihre Organisation.](images/Subscriptions/Subscriptions_Fig4.png)
  
<span data-ttu-id="a7c25-p112">In Abbildung 4 wird gezeigt, wie ein gemeinsamer Azure AD-Mandant von Microsoft-SaaS-Cloudangeboten, Azure PaaS-Apps und virtuellen Computern in Azure IaaS verwendet wird, die Azure AD-Domänendienste verwenden. Die lokale Windows Server AD-Gesamtstruktur wird mithilfe von Azure AD Connect mit dem Azure AD-Mandanten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="a7c25-p112">Figure 4 shows how a common Azure AD tenant is utilized by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="a7c25-180">Weitere Informationen zu Identitätsintegration über Microsoft Cloud-Angeboten finden Sie unter [Microsoft Cloudidentität für Enterprise-konstruiert](https://aka.ms/cloudarchidentity).</span><span class="sxs-lookup"><span data-stu-id="a7c25-180">For more information about identity integration across Microsoft's cloud offerings, see [Microsoft Cloud Identity for Enterprise Architects](https://aka.ms/cloudarchidentity).</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="a7c25-181">Kombinieren von Abonnements für mehrere Microsoft-Cloudangebote</span><span class="sxs-lookup"><span data-stu-id="a7c25-181">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="a7c25-182">Die folgende Tabelle beschreibt, wie Sie mehrere Microsoft-Cloudangebote basierend auf dem Vorhandensein eines Abonnement für einen Typ von Cloudangebot (die Bezeichnungen laufen in der ersten Spalte nach unten) und dem Hinzufügen eines Abonnements für ein anderes Cloudangebot (von links nach rechts) kombinieren können.</span><span class="sxs-lookup"><span data-stu-id="a7c25-182">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="a7c25-183">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="a7c25-183">**Office 365**</span></span>|<span data-ttu-id="a7c25-184">**Azure**</span><span class="sxs-lookup"><span data-stu-id="a7c25-184">**Azure**</span></span>|<span data-ttu-id="a7c25-185">**Intune/zur Abstimmung**</span><span class="sxs-lookup"><span data-stu-id="a7c25-185">**Intune/EMS**</span></span>|<span data-ttu-id="a7c25-186">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="a7c25-186">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a7c25-187">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="a7c25-187">**Office 365**</span></span> <br/> |<span data-ttu-id="a7c25-188">–</span><span class="sxs-lookup"><span data-stu-id="a7c25-188">NA</span></span>  <br/> |<span data-ttu-id="a7c25-189">Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-189">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="a7c25-190">Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation aus dem Office 365-Portal hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-190">You add an Intune/EMS subscription to your organization from the Office 365 portal.</span></span>  <br/> |<span data-ttu-id="a7c25-191">Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation aus dem Office 365-Portal hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-191">You add a Dynamics 365 subscription to your organization from the Office 365 portal.</span></span>  <br/> |
|<span data-ttu-id="a7c25-192">**Azure**</span><span class="sxs-lookup"><span data-stu-id="a7c25-192">**Azure**</span></span> <br/> |<span data-ttu-id="a7c25-193">Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu. </span><span class="sxs-lookup"><span data-stu-id="a7c25-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="a7c25-194">–</span><span class="sxs-lookup"><span data-stu-id="a7c25-194">NA</span></span>  <br/> |<span data-ttu-id="a7c25-195">Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-195">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="a7c25-196">Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="a7c25-197">**Intune/zur Abstimmung**</span><span class="sxs-lookup"><span data-stu-id="a7c25-197">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="a7c25-198">Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu. </span><span class="sxs-lookup"><span data-stu-id="a7c25-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="a7c25-199">Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="a7c25-200">–</span><span class="sxs-lookup"><span data-stu-id="a7c25-200">NA</span></span>  <br/> |<span data-ttu-id="a7c25-201">Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-201">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="a7c25-202">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="a7c25-202">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="a7c25-203">Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu. </span><span class="sxs-lookup"><span data-stu-id="a7c25-203">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="a7c25-204">Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-204">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="a7c25-205">Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-205">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="a7c25-206">–</span><span class="sxs-lookup"><span data-stu-id="a7c25-206">NA</span></span>  <br/> |
   
<span data-ttu-id="a7c25-207">Eine einfache Möglichkeit zum Hinzufügen von Abonnements zu Ihrer Organisation für Microsoft SaaS-basierte Dienste erfolgt über das Office 365 Admin Center:</span><span class="sxs-lookup"><span data-stu-id="a7c25-207">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the Office 365 Admin center:</span></span>
  
1. <span data-ttu-id="a7c25-208">Melden Sie sich bei Office 365-Portal ([https://portal.office.com](https://portal.office.com)) mit der globale Administratorkonto ein, und klicken Sie dann auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="a7c25-208">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with your global administrator account, and then click **Admin**.</span></span>
    
2. <span data-ttu-id="a7c25-209">Klicken Sie im linken Navigationsbereich der Homepage der **Verwaltungskonsole** auf **Abrechnung**und klicken Sie dann auf **Dienste erwerben**.</span><span class="sxs-lookup"><span data-stu-id="a7c25-209">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="a7c25-210">Erwerben Sie Ihre neue Abonnements, auf der Seite **Dienste erwerben** .</span><span class="sxs-lookup"><span data-stu-id="a7c25-210">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="a7c25-211">Das Office 365 Admin Center ordnet die Organisation und den Azure AD-Mandanten Ihres Office 365-Abonnements den neuen Abonnements für SaaS-basierte Cloudangebote zu.</span><span class="sxs-lookup"><span data-stu-id="a7c25-211">The Office 365 Admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="a7c25-212">So fügen Sie ein Azure-Abonnement mit derselben Organisation und demselben Azure AD-Mandanten wie das Office 365-Abonnement hinzu</span><span class="sxs-lookup"><span data-stu-id="a7c25-212">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="a7c25-213">Melden Sie sich bei des Azure-Portals ([https://portal.azure.com](https://portal.azure.com)) mit Ihrem Office 365 globaler Administrator-Konto.</span><span class="sxs-lookup"><span data-stu-id="a7c25-213">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="a7c25-214">Klicken Sie im linken Navigationsbereich auf **Abonnements**und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a7c25-214">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="a7c25-215">Klicken Sie auf der Seite **Abonnement hinzufügen** wählen Sie ein Angebot, und führen Sie die Zahlungsinformationen und Vereinbarung.</span><span class="sxs-lookup"><span data-stu-id="a7c25-215">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="a7c25-216">Wenn Sie Azure und Office 365-Abonnements separat erworben und den Office 365 Azure AD-Mandanten aus dem Azure-Abonnement aufrufen möchten, finden Sie in [einem Office 365-Mandanten mit einem Azure-Abonnement zuordnen](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).</span><span class="sxs-lookup"><span data-stu-id="a7c25-216">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Associate an Office 365 tenant with an Azure subscription](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a7c25-217">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="a7c25-217">See Also</span></span>

[<span data-ttu-id="a7c25-218">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="a7c25-218">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="a7c25-219">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="a7c25-219">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a7c25-220">Architekturmodelle für SharePoint, Exchange, Skype for Business und Lync</span><span class="sxs-lookup"><span data-stu-id="a7c25-220">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="a7c25-221">Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="a7c25-221">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="a7c25-222">Abonnements, Lizenzen und Benutzerkonten für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="a7c25-222">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



