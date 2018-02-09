---
title: "Abonnements, Lizenzen und Benutzerkonten für die Contoso Corporation"
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
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 'Zusammenfassung: Verstehen der Struktur der Contoso Cloud-Abonnements, Lizenzen, Benutzerkonten und Mandanten.'
ms.openlocfilehash: 6e62fbbc0f52019e5d233fc73992b000952344f5
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="14e02-103">Abonnements, Lizenzen und Benutzerkonten für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="14e02-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="14e02-104">**Zusammenfassung:** Verstehen der Struktur der Contoso Cloud-Abonnements, Lizenzen, Benutzerkonten und Mandanten.</span><span class="sxs-lookup"><span data-stu-id="14e02-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="14e02-105">Um eine durchgängige Verwendung von Identitäten und Abrechnung für alle Cloudangebote anzubieten, stellt Microsoft eine Hierarchie aus Organisation/Abonnements/Lizenzen/Benutzerkonten bereit.
</span><span class="sxs-lookup"><span data-stu-id="14e02-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="14e02-106">Organisation</span><span class="sxs-lookup"><span data-stu-id="14e02-106">Organization</span></span>
    
    <span data-ttu-id="14e02-107">Die Geschäftseinheit, die Microsoft-Cloudangebote verwendet und üblicherweise durch einen öffentlichen DNS-Domänennamen identifiziert wird, z. B. „contoso.com“.
</span><span class="sxs-lookup"><span data-stu-id="14e02-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="14e02-108">Abonnements</span><span class="sxs-lookup"><span data-stu-id="14e02-108">Subscriptions</span></span>
    
    <span data-ttu-id="14e02-p101">Für Microsoft SaaS cloud-angeboten (Office 365, Intune/zur Abstimmung und Dynamics 365), ist ein Abonnement ein bestimmtes Produkt und eine erworbenen Reihe von Benutzerlizenzen. Azure ermöglicht ein Abonnement für die Abrechnung des verbrauchten Clouddiensten für die Organisation.</span><span class="sxs-lookup"><span data-stu-id="14e02-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="14e02-111">Lizenzen</span><span class="sxs-lookup"><span data-stu-id="14e02-111">Licenses</span></span>
    
    <span data-ttu-id="14e02-p102">SaaS Microsoft Cloud-angeboten ermöglicht eine Lizenz ein bestimmtes Benutzerkonto Cloud-Dienste verwenden. Für Azure werden Softwarelizenzen erstellt in Preisen, aber in einigen Fällen, die müssen Sie zusätzliche Software-Lizenzen erwerben.</span><span class="sxs-lookup"><span data-stu-id="14e02-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="14e02-114">Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="14e02-114">User accounts</span></span>
    
    <span data-ttu-id="14e02-115">Benutzerkonten werden in einem Azure AD-Mandanten gespeichert und können aus einem lokalen Identitätsanbieter, z. B. Windows Server Active Directory, synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="14e02-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="14e02-116">Contoso Struktur</span><span class="sxs-lookup"><span data-stu-id="14e02-116">Contoso's structure</span></span>

<span data-ttu-id="14e02-117">Contoso hat die folgende Struktur für die Organisation und ihre Abonnements, Lizenzen, Konten und Mandanten bestimmt:</span><span class="sxs-lookup"><span data-stu-id="14e02-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="14e02-118">**Abbildung 1: Contoso Organisation, Abonnements, Lizenzen, Benutzerkonten und Mandanten**</span><span class="sxs-lookup"><span data-stu-id="14e02-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Organisation, Abonnements, Lizenzen, Benutzerkonten und Mandanten von Contoso](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="14e02-120">Abbildung 1 zeigt, wie die Contoso-Organisation mehrere Abonnements umfasst und an einen allgemeinen Azure AD-Mandanten gebunden ist, der die aus der Windows Server Active Directory-Gesamtstruktur "contoso.com" synchronisierten Benutzerkonten enthält.</span><span class="sxs-lookup"><span data-stu-id="14e02-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="14e02-121">**Organisation** Der Contoso Corporation wird durch seine öffentlichen Domäne namens "contoso.com" identifiziert.</span><span class="sxs-lookup"><span data-stu-id="14e02-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="14e02-122">**Abonnements und Lizenzen** Der Contoso Corporation wird Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="14e02-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="14e02-123">Das Office 365 Enterprise E3 Produkt mit 5.000 Lizenzen</span><span class="sxs-lookup"><span data-stu-id="14e02-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="14e02-124">Das Produkt Office 365 Enterprise E5 mit 200 Lizenzen</span><span class="sxs-lookup"><span data-stu-id="14e02-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="14e02-125">Das Produkt zur Abstimmung mit 5.000 Lizenzen</span><span class="sxs-lookup"><span data-stu-id="14e02-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="14e02-126">Das Produkt Dynamics 365 mit 100 Lizenzen</span><span class="sxs-lookup"><span data-stu-id="14e02-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="14e02-127">Mehrere Azure-Abonnements auf Basis von Regionen</span><span class="sxs-lookup"><span data-stu-id="14e02-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="14e02-128">**Benutzerkonten** Ein allgemeiner Azure AD-Mandanten enthält die Liste der Benutzerkonten und Gruppen verwendet von allen Contoso Abonnements, mit Ausnahme von Test-/Azure-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="14e02-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="14e02-129">Für Contoso-Mandanten:</span><span class="sxs-lookup"><span data-stu-id="14e02-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="14e02-p103">Für SaaS Cloud-angeboten wird der Mandanten der regionalen Standort, an die Bereitstellung von Clouddiensten Server befinden. Contoso ausgewählt haben, die Europäische Region zum Hosten der Office 365 und zur Abstimmung Dynamics 365-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="14e02-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="14e02-p104">Azure PaaS-Diensten und apps und IaaS IT Arbeitslasten können Mandanten in Azure-Rechenzentrum auf der ganzen Welt haben. Ein Azure AD-Mandanten ist eine bestimmte Instanz von Azure Active Directory-Konten und Gruppen enthält.</span><span class="sxs-lookup"><span data-stu-id="14e02-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="14e02-134">Der allgemeine Azure AD-Mandanten, der die synchronisierten Konten für die Contoso Windows Server Active Directory-Gesamtstruktur enthält bietet IDaaS Cloudlösungen von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="14e02-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="14e02-135">Weitere Informationen finden Sie unter [Abonnements, Lizenzen, Konten, und Mandanten für Microsoft Cloud-angeboten](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span><span class="sxs-lookup"><span data-stu-id="14e02-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="14e02-136">Contoso Azure-Abonnements</span><span class="sxs-lookup"><span data-stu-id="14e02-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="14e02-137">Abbildung 2 zeigt den hierarchischen Entwurf Contosos Azure-Abonnements:</span><span class="sxs-lookup"><span data-stu-id="14e02-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="14e02-138">**Abbildung 2: Contoso Struktur für Azure-Abonnements**</span><span class="sxs-lookup"><span data-stu-id="14e02-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Struktur für Azure-Abonnements von Contoso](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="14e02-140">Contoso nimmt die oberste Position ein, basierend auf seinem Enterprise Agreement mit Microsoft.</span><span class="sxs-lookup"><span data-stu-id="14e02-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="14e02-141">Es gibt eine Gruppe von Konten, die unterschiedlichen Regionen der Contoso Corporation auf der ganzen Welt basierend auf den Domänen der Contoso Windows Server Active Directory-Gesamtstruktur entspricht.</span><span class="sxs-lookup"><span data-stu-id="14e02-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="14e02-142">In den einzelnen Bereichen müssen Sie einen oder mehrere Abonnements basierend auf den Bereich Entwicklung, testen und Produktion Erfordernissen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="14e02-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="14e02-p105">Jedes Azure-Abonnement kann einem einzelnen Azure AD-Mandanten zugeordnet werden, der Benutzerkonten und Gruppen für die Authentifizierung und Autorisierung bei Azure-Diensten enthält.
 Für Produktionsabonnements wird der allgemeine Contoso Azure AD-Mandant verwendet.</span><span class="sxs-lookup"><span data-stu-id="14e02-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="14e02-145">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="14e02-145">See Also</span></span>

[<span data-ttu-id="14e02-146">Contoso in der Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="14e02-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="14e02-147">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="14e02-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="14e02-148">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="14e02-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




