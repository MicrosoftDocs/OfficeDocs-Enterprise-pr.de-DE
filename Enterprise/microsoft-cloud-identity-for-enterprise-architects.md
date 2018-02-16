---
title: "Microsoft-Cloud-Identität für Enterprise-Architekten"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: O365ITProTrain, Strat_O365_Enterprise, Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "Zusammenfassung: Entwerfen Sie Ihre Identitätslösung für Microsoft Cloud-Dienste und -Plattformen."
ms.openlocfilehash: 08dfb843128839fc6f8b70373335f64b44133ff1
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2018
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="beed3-103">Microsoft-Cloud-Identität für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="beed3-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="beed3-104">**Zusammenfassung:** Entwerfen Sie Ihre Identitätslösung für Microsoft Cloud-Dienste und -Plattformen.</span><span class="sxs-lookup"><span data-stu-id="beed3-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="beed3-p101">Dieser Artikel beschreibt, was IT-Architekten über das Entwerfen der Identität für Organisationen wissen müssen, die Microsoft Cloud-Dienste und -Plattformen verwenden. Sie können diesen Artikel auch als fünfseitiges Poster anzeigen und im Tabloid-Format (auch bekannt als Ledger, 11 x 17 oder A3) drucken.</span><span class="sxs-lookup"><span data-stu-id="beed3-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="beed3-107">[![Miniaturbild für Microsoft-Cloud-Identitätsmodell](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="beed3-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="beed3-108">![PDF-Datei](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio-Datei](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![Seite mit Versionen in zusätzlichen Sprachen anzeigen](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Weitere Sprachen](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="beed3-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="beed3-109">Sie sehen auch alle Modelle der [Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md) und können[Microsoft Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture) durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="beed3-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="beed3-p102">Dieser Artikel spiegelt die Version vom Januar 2016 des Posters **Microsoft-Cloud-Identität für Enterprise-Architekten** wider. Er enthält nicht die Änderungen für die Posterversion vom April 2016 oder spätere Versionen des Posters.</span><span class="sxs-lookup"><span data-stu-id="beed3-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="beed3-112">Entwerfen von Identität für die Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="beed3-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="beed3-p103">Durch das Integrieren von Identitäten in die Microsoft-Cloud erhalten Sie Zugriff auf eine Vielzahl von Diensten und Cloud-Plattformoptionen. Es gibt zwei Hauptoptionen:</span><span class="sxs-lookup"><span data-stu-id="beed3-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="beed3-p104">Sie können in Microsoft Azure Active Directory (AD) integrieren. Dies umfasst das Synchronisieren Ihrer lokalen Konten mit Azure AD, der Identitätsanbieter für die Microsoft-Cloud.</span><span class="sxs-lookup"><span data-stu-id="beed3-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="beed3-117">Sie können Ihre lokale Active Directory Domain Services (AD DS)-Umgebung auf virtuelle Computer erweitern, die unter Microsoft Azure-Infrastrukturdiensten ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="beed3-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![Optionen beim Entwerfen von Identitäten in der Cloud](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="beed3-119">**Abbildung 1: Optionen beim Entwerfen von Identitäten in der Cloud**</span><span class="sxs-lookup"><span data-stu-id="beed3-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="beed3-120">Abbildung 1 zeigt Azure AD als Identitätsanbieter für Microsoft SaaS-Dienste (Software as a Service) und Azure PaaS-Anwendungen (Platform as a Service) und wie Geschäftsanwendungen lokale AD DS verwenden können.</span><span class="sxs-lookup"><span data-stu-id="beed3-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="beed3-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="beed3-121">Azure Active Directory</span></span>

<span data-ttu-id="beed3-p105">Microsoft Azure AD ist der in der Cloud gehostete Identitäts- und Zugriffsverwaltungsdienst von Microsoft. Es befindet sich im Zentrum der Microsoft-Cloud-Dienste und -Plattformen. Das Integrieren in Azure AD ermöglicht den Zugriff auf alle Microsoft SaaS-Dienste mit Ihrem aktuellen Benutzerkonten und Kennwörtern. Diese Integration stellt außerdem eine Cloud-basierte Identität für Azure PaaS-Anwendungen bereit.</span><span class="sxs-lookup"><span data-stu-id="beed3-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="beed3-126">Azure AD ist kein Ersatz für lokale AD DS für große Organisationen oder für Windows-basierte virtuelle Computer, die unter Azure-IaaS (Infrastructure as a Service) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="beed3-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="beed3-127">Es gibt drei Azure AD-Editionen: Kostenlos, Basic und Premium.</span><span class="sxs-lookup"><span data-stu-id="beed3-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="beed3-128">**Kostenlos**</span><span class="sxs-lookup"><span data-stu-id="beed3-128">**Free**</span></span> <br/> |<span data-ttu-id="beed3-129">**Basic**</span><span class="sxs-lookup"><span data-stu-id="beed3-129">**Basic**</span></span> <br/> |<span data-ttu-id="beed3-130">**Premium**</span><span class="sxs-lookup"><span data-stu-id="beed3-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="beed3-131">Verwalten von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="beed3-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="beed3-132">Synchronisieren mit lokalen Verzeichnissen</span><span class="sxs-lookup"><span data-stu-id="beed3-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="beed3-133">Einmaliges Anmelden in Azure, Office 365 und Tausenden von anderen gängigen SaaS-Anwendungen, z. B. Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox und mehr</span><span class="sxs-lookup"><span data-stu-id="beed3-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="beed3-134">Enthält alle Features der kostenlosen Edition plus:</span><span class="sxs-lookup"><span data-stu-id="beed3-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="beed3-135">Unternehmensbranding</span><span class="sxs-lookup"><span data-stu-id="beed3-135">Company branding</span></span> <br/>  <span data-ttu-id="beed3-136">Gruppenbasierter Anwendungszugriff</span><span class="sxs-lookup"><span data-stu-id="beed3-136">Group-based application access</span></span> <br/>  <span data-ttu-id="beed3-137">Zurücksetzen von Kennwörtern durch den Benutzer</span><span class="sxs-lookup"><span data-stu-id="beed3-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="beed3-138">Unternehmens-SLA von 99,9 %</span><span class="sxs-lookup"><span data-stu-id="beed3-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="beed3-139">Enthält alle Features der kostenlosen und der Basic-Edition plus:</span><span class="sxs-lookup"><span data-stu-id="beed3-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="beed3-140">Gruppenverwaltung durch den Benutzer</span><span class="sxs-lookup"><span data-stu-id="beed3-140">Self-service group management</span></span> <br/>  <span data-ttu-id="beed3-141">	Erweiterte Sicherheitsberichte und Warnungen</span><span class="sxs-lookup"><span data-stu-id="beed3-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="beed3-142">	Mehrstufige Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="beed3-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="beed3-143">Zurücksetzen von Kennwörtern mit Write-Back in lokale AD DS</span><span class="sxs-lookup"><span data-stu-id="beed3-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="beed3-144">Bidirektionale Synchronisierung mit dem Azure AD Connect-Tool </span><span class="sxs-lookup"><span data-stu-id="beed3-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="beed3-145">Azure AD-Anwendungsproxy</span><span class="sxs-lookup"><span data-stu-id="beed3-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="beed3-146">	Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="beed3-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="beed3-147">Weitere Informationen zu Versionen finden Sie unter [Azure Active Directory-Editionen](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span><span class="sxs-lookup"><span data-stu-id="beed3-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="beed3-148">Option 1: Integration in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="beed3-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="beed3-p106">Die meisten Organisationen synchronisieren einen Standardsatz aus Objekten und Attributen mit ihrem Azure AD-Mandanten. Das Azure AD Connect-Tool synchronisiert Ihre Konten zwischen den lokalen AD DS und einem Azure AD-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="beed3-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![Integrieren in Azure AD](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="beed3-152">**Abbildung 2: Integrieren in Azure AD**</span><span class="sxs-lookup"><span data-stu-id="beed3-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="beed3-p107">Abbildung 2 zeigt, wie das Azure AD Connect-Tool AD DS-Änderungen abruft und an Ihren Azure AD-Mandanten sendet. In diesem Fall ist Ihr Azure AD-Mandant ein in der Cloud gehostetes Duplikat unverzichtbarer Inhalte aus dem lokalen Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="beed3-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="beed3-p108">Viele Organisationen verwenden AD DS als lokalen Identitätsanbieter. Sie können lokal einen anderen Typ von Identitätsanbieter (z. B. einen, der LDAP verwendet) verwenden und diesen mit Azure AD synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="beed3-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="beed3-157">Option 2: Erweitern von AD DS auf Azure</span><span class="sxs-lookup"><span data-stu-id="beed3-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="beed3-p109">Das Erweitern von AD DS auf virtuelle Computer, auf denen Azure-Infrastrukturdienste ausgeführt werden, unterstützt andere Lösungen und Anwendungen als die Synchronisierung mit Azure AD. Es folgen zwei:</span><span class="sxs-lookup"><span data-stu-id="beed3-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="beed3-160">Unterstützt die Cloud-basierten Lösungen, die die NTLM- oder Kerberos-Authentifizierung oder virtuelle Computer in der AD DS-Domäne erfordern.</span><span class="sxs-lookup"><span data-stu-id="beed3-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="beed3-161">Fügt weiteres Integrationspotenzial für Cloud-Dienste und -Anwendungen für Microsoft Cloud-Dienste und -Plattformen hinzu.</span><span class="sxs-lookup"><span data-stu-id="beed3-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![Erweitern von AD DS in Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="beed3-163">**Abbildung 3: Erweitern von AD DS auf Azure**</span><span class="sxs-lookup"><span data-stu-id="beed3-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="beed3-p110">Abbildung 3 zeigt einen AD DS-Domänencontroller, der mit einem virtuellen Azure-Netzwerk über ein lokales VPN-Gerät und ein Azure VPN-Gateway verbunden ist. Das virtuelle Azure-Netzwerk enthält Server für eine LOB-Anwendung und eigene AD DS-Domänencontroller.</span><span class="sxs-lookup"><span data-stu-id="beed3-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="beed3-166">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="beed3-166">More Information</span></span>

- [<span data-ttu-id="beed3-167">Das Synchronisieren Ihres Verzeichnisses mit Office 365 ist ein Kinderspiel</span><span class="sxs-lookup"><span data-stu-id="beed3-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="beed3-168">Infografik: Cloud-Identitäts- und Zugriffsverwaltung</span><span class="sxs-lookup"><span data-stu-id="beed3-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="beed3-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="beed3-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="beed3-170">Integrieren der lokalen AD DS-Konten in Microsoft Azure AD</span><span class="sxs-lookup"><span data-stu-id="beed3-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="beed3-171">Durch die Synchronisierung Ihrer lokalen AD DS-Konten mit Azure AD können Ihre Benutzer ihre lokalen AD DS-Konten für den Zugriff auf Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="beed3-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="beed3-172">Alle Microsoft-SaaS-Dienste (Office 365, Microsoft Intune und Dynamics CRM Online)</span><span class="sxs-lookup"><span data-stu-id="beed3-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="beed3-173">Die in Azure PaaS ausgeführten Anwendungen</span><span class="sxs-lookup"><span data-stu-id="beed3-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="beed3-174">Es gibt zwei Möglichkeiten zum Konfigurieren dieser Integration:</span><span class="sxs-lookup"><span data-stu-id="beed3-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="beed3-175">Verzeichnis- und Kennwortsynchronisierung</span><span class="sxs-lookup"><span data-stu-id="beed3-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="beed3-176">Verbund und einmaliges Anmelden</span><span class="sxs-lookup"><span data-stu-id="beed3-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="beed3-p111">Beginnen Sie mit der einfachsten Option, die Ihren Anforderungen entspricht. Sie können bei Bedarf zwischen diesen Optionen wechseln.</span><span class="sxs-lookup"><span data-stu-id="beed3-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="beed3-179">Das Verwenden von Nur-Cloud-Konten (ohne Integration in die lokalen AD DS) wird für große Organisationen nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="beed3-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="beed3-180">Verzeichnis- und Kennwortsynchronisierung</span><span class="sxs-lookup"><span data-stu-id="beed3-180">Directory and password synchronization</span></span>

<span data-ttu-id="beed3-181">Dies ist die einfachste Option und erfordert nur einen Server, der das Azure AD Connect-Tool ausführt.</span><span class="sxs-lookup"><span data-stu-id="beed3-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![Konfiguration für die Verzeichnis- und Kennwortsynchronisierung](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="beed3-183">**Abbildung 4: Konfiguration für die Verzeichnis- und Kennwortsynchronisierung**</span><span class="sxs-lookup"><span data-stu-id="beed3-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="beed3-p112">Abbildung 4 zeigt ein lokales oder privates Cloud-Rechenzentrum mit einem AD DS-Domänencontroller. Ein Server, auf dem das Azure AD Connect-Tool ausgeführt wird, synchronisiert die Liste der Kontonamen mit Azure AD.</span><span class="sxs-lookup"><span data-stu-id="beed3-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="beed3-186">Mit dieser Option geschieht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="beed3-186">With this option:</span></span>
  
- <span data-ttu-id="beed3-p113">Benutzerkonten werden von Ihren lokalen AD DS (oder einem anderen Identitätsanbieter) mit Ihrem Azure AD-Mandanten synchronisiert. Das lokale Verzeichnis bleibt die maßgebliche Quelle für Konten, und Sie verwalten alle Kontoänderungen von dort aus.</span><span class="sxs-lookup"><span data-stu-id="beed3-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="beed3-189">Azure AD führt alle Authentifizierungen für Microsoft SaaS-basierte Dienste und Azure PaaS-Anwendungen aus.</span><span class="sxs-lookup"><span data-stu-id="beed3-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="beed3-190">Sie können auch die Synchronisierung für mehrere AD DS-Gesamtstrukturen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="beed3-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="beed3-191">Mit Kennwortsynchronisierung:</span><span class="sxs-lookup"><span data-stu-id="beed3-191">With password synchronization:</span></span>
  
- <span data-ttu-id="beed3-192">Benutzer werden aufgefordert, ein Kennwort einzugeben, wenn sie auf Cloud-Dienste zugreifen. Dabei handelt es sich um dasselbe Kennwort, das sie für lokale Ressourcen verwenden.</span><span class="sxs-lookup"><span data-stu-id="beed3-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="beed3-p114">Benutzerkennwörter werden nie als Klartext an Azure AD gesendet. Stattdessen wird ein Hash des Kennworts verwendet. Der Kennworthash kann kryptografisch nicht entschlüsselt oder durch Reverse Engineering zurückentwickelt werden, um das Klartextkennwort zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="beed3-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="beed3-196">Mit mehrstufiger Authentifizierung (Multi-Factor Authentication, MFA):</span><span class="sxs-lookup"><span data-stu-id="beed3-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="beed3-197">Sie können die mit Office 365 angeboten grundlegenden MFA-Features nutzen.</span><span class="sxs-lookup"><span data-stu-id="beed3-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="beed3-198">Azure PaaS-Anwendungsentwickler können den Azure-Dienst für die mehrstufige Authentifizierung nutzen.</span><span class="sxs-lookup"><span data-stu-id="beed3-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="beed3-199">Verzeichnissynchronisation bietet keine Integration in lokale MFA-Lösungen.</span><span class="sxs-lookup"><span data-stu-id="beed3-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="beed3-200">Verbund und einmaliges Anmelden</span><span class="sxs-lookup"><span data-stu-id="beed3-200">Federation and single sign-on</span></span>

<span data-ttu-id="beed3-201">Diese Option erfordert zusätzliche Server und Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="beed3-201">This option requires additional servers and infrastructure.</span></span> 
  
![Erforderliche Server für die Verbundauthentifzierung](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="beed3-203">**Abbildung 5: Erforderliche Server für die Verbundauthentifzierung**</span><span class="sxs-lookup"><span data-stu-id="beed3-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="beed3-p115">Abbildung 5 zeigt die Komponenten für die Verbundauthentifizierung. Azure AD kontaktiert einen Webanwendungsproxy, der die Authentifizierungsanforderung an einen AD FS-Server (Active Directory Federation Services) weiterleitet, der die Anforderung zur Auswertung und Antwort an einen AD DS-Domänencontroller weiterleitet. Ein Server, auf dem das Azure AD Connect-Tool ausgeführt wird, synchronisiert die Liste der Kontonamen aus AD DS mit Azure AD.</span><span class="sxs-lookup"><span data-stu-id="beed3-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="beed3-207">Der Verbund stellt diese zusätzlichen Unternehmensfunktionen bereit:</span><span class="sxs-lookup"><span data-stu-id="beed3-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="beed3-208">Alle Authentifizierungsanfragen, die an Azure AD gesendet werden, werden an den lokalen Identitätsanbieter über AD FS weitergeleitet und dort ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="beed3-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="beed3-209">Funktioniert mit Microsoft-fremden Identitätsanbietern.</span><span class="sxs-lookup"><span data-stu-id="beed3-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="beed3-210">Die Synchronisierung von Kennworthashes kann als Anmeldungssicherung für die Verbundanmeldung fungieren (z. B. wenn die Verbundauthentifizierung fehlschlägt).</span><span class="sxs-lookup"><span data-stu-id="beed3-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="beed3-211">Verwenden Sie den Verbund in folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="beed3-211">Use federation if:</span></span>
  
- <span data-ttu-id="beed3-p116">Einmaliges Anmelden ist erforderlich. Mit dem einmaligen Anmelden werden Benutzer nicht aufgefordert, beim Zugriff auf einen Cloud-Dienst Anmeldeinformationen (Benutzername oder Kennwort) einzugeben.</span><span class="sxs-lookup"><span data-stu-id="beed3-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="beed3-214">AD FS wurde bereits bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="beed3-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="beed3-215">Sie verwenden einen Identitätsdrittanbieter.</span><span class="sxs-lookup"><span data-stu-id="beed3-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="beed3-216">Sie verwenden Forefront Identity Manager 2010 R2 (bietet keine Unterstützung für die Synchronisierung von Kennworthashes).</span><span class="sxs-lookup"><span data-stu-id="beed3-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="beed3-217">Sie haben eine integrierte lokale Smartcard oder eine andere MFA-Lösung.</span><span class="sxs-lookup"><span data-stu-id="beed3-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="beed3-218">Sie benötigen Anmeldungsüberwachung und/oder Deaktivierung von Konten.</span><span class="sxs-lookup"><span data-stu-id="beed3-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="beed3-219">Ihre Organisation benötigt Clientanmeldeeinschränkungen basierend auf Netzwerkspeicherort oder Arbeitsstunden.</span><span class="sxs-lookup"><span data-stu-id="beed3-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="beed3-220">Sie müssen die Federal Information Processing Standards (FIPS) einhalten.</span><span class="sxs-lookup"><span data-stu-id="beed3-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="beed3-221">Die Verbundauthentifizierung erfordert eine größere Investition in die lokale Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="beed3-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="beed3-p117">Der Internetzugriff auf die lokalen Servern über eine Unternehmensfirewall muss möglich sein. Microsoft empfiehlt die Verwendung von Web Application Proxy-Servern, die in Ihrer Netzwerkumgebung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="beed3-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="beed3-224">Erfordert Hardware, Lizenzen und Betrieb für AD FS-Server, AD FS-Proxy- oder Web Application Proxy-Server, Firewalls und Lastenausgleich.</span><span class="sxs-lookup"><span data-stu-id="beed3-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="beed3-225">Verfügbarkeit und Leistung sind wichtig, um sicherzustellen, dass Benutzer auf Office 365 und andere Cloud-Anwendungen zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="beed3-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="beed3-226">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="beed3-226">More Information</span></span>

- [<span data-ttu-id="beed3-227">Das Synchronisieren Ihres Verzeichnisses mit Office 365 ist ein Kinderspiel</span><span class="sxs-lookup"><span data-stu-id="beed3-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="beed3-228">Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="beed3-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="beed3-229">Mehrstufige Authentifizierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="beed3-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="beed3-230">Mehrstufige Azure-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="beed3-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="beed3-231">TechEd 2014: Verzeichnisintegration: Erstellen eines Verzeichnis mit Active Directory und Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="beed3-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="beed3-232">Erweitern von AD DS auf Azure</span><span class="sxs-lookup"><span data-stu-id="beed3-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="beed3-233">Das Erweitern von AD DS auf Azure ist der erste Schritt zur Unterstützung der LOB-Anwendungen, die auf virtuellen Computern in Azure-Infrastrukturdiensten ausgeführt werden, und stellt Folgendes bereit:</span><span class="sxs-lookup"><span data-stu-id="beed3-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="beed3-234">Unterstützung für Cloud-basierte Lösungen, die die NTLM- oder Kerberos-Authentifizierung oder virtuelle Computer in der AD DS-Domäne erfordern.</span><span class="sxs-lookup"><span data-stu-id="beed3-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="beed3-235">Zusätzliches Integrationspotenzial für Cloud-Dienste und -Anwendungen. Kann jederzeit hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="beed3-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![Erweitern von AD DS zu einem virtuellen Azure-Netzwerk](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="beed3-237">**Abbildung 6: Erweitern von AD DS auf ein virtuelles Azure-Netzwerk**</span><span class="sxs-lookup"><span data-stu-id="beed3-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="beed3-p118">Abbildung 6 zeigt ein lokales oder privates Cloud-Rechenzentrum, bei dem AD DS mit einem virtuellen Azure-Netzwerk über eine Site-to-Site-VPN oder ExpressRoute-Verbindung verbunden ist. Das virtuelle Azure-Netzwerk enthält Server für eine LOB-Anwendung und eigene AD DS-Domänencontroller. Diese Konfiguration ist eine Hybridbereitstellung aus lokalen AD DS und Azure-Infrastrukturdiensten. Sie erfordert Folgendes:</span><span class="sxs-lookup"><span data-stu-id="beed3-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="beed3-242">ein virtuelles Azure-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="beed3-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="beed3-243">Eine Verbindung zwischen einem VPN-Gerät oder -Router und einem Azure VPN-Gateway.</span><span class="sxs-lookup"><span data-stu-id="beed3-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="beed3-244">Das Verwenden eines Teils Ihres lokalen IP-Adressraums für die virtuellen Computer im virtuellen Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="beed3-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="beed3-245">Das Bereitstellen von mindestens einem Domänencontroller im virtuellen Netzwerk, der als Server für den globalen Katalog dient (verringert den ausgehenden Datenverkehr über die VPN-Verbindung).</span><span class="sxs-lookup"><span data-stu-id="beed3-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="beed3-246">Diese Identitätsarchitektur unterstützt eine andere Gruppe von Lösungen und Abwendungen im Vergleich zur Synchronisierung mit Azure AD.</span><span class="sxs-lookup"><span data-stu-id="beed3-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="beed3-247">Optionen für die lokale Verbindung zu Azure</span><span class="sxs-lookup"><span data-stu-id="beed3-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="beed3-248">Um Ihr lokales Netzwerk mit einem virtuellen Azure-Netzwerk zu verbinden, können Sie Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="beed3-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="beed3-249">Eine Site-to-Site-VPN-Verbindung, die 1 bis 10 Sites (einschließlich anderer virtueller Azure-Netzwerke) mit einem einzelnen virtuellen Azure-Netzwerk verbinden kann.</span><span class="sxs-lookup"><span data-stu-id="beed3-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="beed3-p119">ExpressRoute, eine private, sichere WAN-Verbindung zu Azure über ein Partnernetzwerk und einen Rechenzentrums-Dienstanbieter. ExpressRoute-Verbindungen können verbesserte Zuverlässigkeit, höhere Bandbreite und geringere Latenzen bieten.</span><span class="sxs-lookup"><span data-stu-id="beed3-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="beed3-252">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="beed3-252">More Information</span></span>

- [<span data-ttu-id="beed3-253">Standortübergreifende Konnektivität für virtuelle Netzwerke</span><span class="sxs-lookup"><span data-stu-id="beed3-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="beed3-254">ExpressRoute - Technische Übersicht</span><span class="sxs-lookup"><span data-stu-id="beed3-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="beed3-255">Richtlinien für die Bereitstellung von Windows Server Active Directory auf virtuellen Computern in Azure</span><span class="sxs-lookup"><span data-stu-id="beed3-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="beed3-256">Integrieren von Anwendungen in Cloud-Identitäten</span><span class="sxs-lookup"><span data-stu-id="beed3-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="beed3-p120">Beim Entwerfen und Entwickeln von Anwendungen, die in der Cloud ausgeführt werden, sollten Sie auf die Konsistenz der Benutzererfahrung für den Authentifizierungsprozess achten, einschließlich den erforderlichen Anmeldeinformationen. Wenn Sie z. B. Windows-Anmeldeinformationen für Azure AD oder erweiterte AD DS verwenden, stellen Sie sicher, dass sich Benutzer schnell authentifizieren und auf ihre Aufgaben konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="beed3-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![Integrieren von Anwendungen in Cloud-Identitäten](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="beed3-260">**Abbildung 7: Integrieren von Anwendungen in Cloud-Identitäten**</span><span class="sxs-lookup"><span data-stu-id="beed3-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="beed3-261">Abbildung 7 zeigt drei Optionen für die Integration Ihrer Anwendung in Cloud-Identitäten.</span><span class="sxs-lookup"><span data-stu-id="beed3-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="beed3-262">Registrieren Sie Ihre in der Cloud gehosteten Anwendungen bei Azure AD.</span><span class="sxs-lookup"><span data-stu-id="beed3-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="beed3-p121">Informationen finden Sie im MSDN-Artikel [Integrieren von Anwendungen in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). Auf diese Weise können Sie Azure AD zum Authentifizieren des Zugriffs auf Ihre PaaS-Anwendung verwenden und es Benutzern oder Administratoren ermöglichen, Rechte für den Zugriff auf Anwendungsinhalte von anderen Cloud-Diensten aus, z. B. Office 365, zu gewähren. Weitere Details und Codebeispiele finden Sie im MSDN-Artikel [Authentifizierungsszenarien für Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span><span class="sxs-lookup"><span data-stu-id="beed3-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="beed3-266">Anwendungen, die eine programmgesteuerte Authentifizierung für den Zugriff auf eine Anwendung benötigen, die durch AD SD, AD FS unter Windows Server 2012 R2 oder Azure AD gesichert ist, können Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="beed3-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="beed3-267">Die [Azure AD-Diagramm-API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="beed3-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="beed3-268">Active Directory-Authentifizierungsbibliothek (ADAL)</span><span class="sxs-lookup"><span data-stu-id="beed3-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="beed3-p122">Die Azure AD-Diagramm-API unterstützt OAuth und OpenID Connect. Sie funktioniert auch mit PaaS-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="beed3-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="beed3-p123">Konfigurieren Sie lokale Anwendungen oder LOB-Anwendungen, die auf virtuellen Computern in einem virtuellen Azure-Netzwerk ausgeführt werden, für die direkte Verwendung der Windows-Authentifizierung (NTLM oder Kerberos). Dies bietet die beste Lösung für Benutzer und erfordert den geringsten Konfigurationsaufwand für Serveranwendungsentwickler.</span><span class="sxs-lookup"><span data-stu-id="beed3-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="beed3-273">Beispiel für die Anwendungsintegration</span><span class="sxs-lookup"><span data-stu-id="beed3-273">Application integration example</span></span>

<span data-ttu-id="beed3-p124">Eine Organisation erstellt eine ASP.NET-Anwendung, die einen REST-Endpunkt bereitstellt, von dem andere Anwendungen die neuesten Vertriebsdaten abrufen können. Der Zugriff auf diesen REST-Endpunkt wird mit Azure AD gesichert. Anwendungen müssen Anmeldeinformationen bereitstellen, die von Azure AD authentifiziert werden können, bevor die ASP.NET-Anwendung die angeforderten Daten sendet. Andere Entwickler in der Organisation können ihre eigenen Anwendungen schreiben, in denen die Vertriebsdaten aus dem REST-Endpunkt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="beed3-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="beed3-p125">Zum Authentifizieren bei Azure AD und zum Abrufen von Daten verwaltet ADAL den Benutzerauthentifizierungsprozess und übergibt das Zugriffstoken an die Anwendung, sodass es für den Zugriff auf die Vertriebsdaten verwendet werden kann. ADAL entfernt einen großen Teil der Komplexität des Abrufens und Analysierens von Token, OAuth-Abläufen und anderen Elementen. ADAL ist eine weitere Technologielösung, die sich schnell verändert, sodass Entwickler die aktuelle Version auf NuGet suchen sollten.</span><span class="sxs-lookup"><span data-stu-id="beed3-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="beed3-281">Bereitstellen von Verzeichniskomponenten in Azure</span><span class="sxs-lookup"><span data-stu-id="beed3-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="beed3-p126">Sie können Verzeichniskomponenten, z. B. Server für die Synchronisierung von Kennwörtern oder Verbundauthentifizierung, in einem virtuellen Azure-Netzwerk statt in einem lokalen Rechenzentrum bereitstellen. Bedenken Sie die Vorteile, insbesondere, wenn Sie planen, AD DS auf Azure zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="beed3-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="beed3-284">Es folgen die Verzeichniskomponenten, die in einem virtuellen Azure-Netzwerk eingesetzt werden können:</span><span class="sxs-lookup"><span data-stu-id="beed3-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="beed3-285">Azure AD Connect-Tool</span><span class="sxs-lookup"><span data-stu-id="beed3-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="beed3-286">Komponenten der Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="beed3-286">Federated authentication components</span></span>
    
- <span data-ttu-id="beed3-287">Eine eigenständige AD DS-Umgebung</span><span class="sxs-lookup"><span data-stu-id="beed3-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="beed3-288">AD Connect-Tool</span><span class="sxs-lookup"><span data-stu-id="beed3-288">AD Connect tool</span></span>

<span data-ttu-id="beed3-p127">Das Azure AD Connect-Tool kann in der Cloud in einem virtuellen Azure-Netzwerk gehostet werden. Bedenken Sie diese Vorteile der Bereitstellung dieser Arbeitslast in Azure:</span><span class="sxs-lookup"><span data-stu-id="beed3-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="beed3-291">Potenziell schnellere Bereitstellung und niedrigere Betriebskosten</span><span class="sxs-lookup"><span data-stu-id="beed3-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="beed3-292">Erhöhte Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="beed3-292">Increased availability</span></span>
    
![In Azure-Infrastrukturdiensten ausgeführtes AD Connect-Tool](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="beed3-294">**Abbildung 8: Das AD Connect-Tool unter Azure**</span><span class="sxs-lookup"><span data-stu-id="beed3-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="beed3-p128">Abbildung 8 zeigt das AD Connect-Tool, das auf einem virtuellen Computer in einem virtuellen Azure-Netzwerk ausgeführt wird und einen lokalen AD DS-Domänencontroller nach Kontoänderungen abfragt und diese Änderungen dann an Office 365 sendet. Diese Lösung funktioniert mit:</span><span class="sxs-lookup"><span data-stu-id="beed3-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="beed3-297">Office 365-Diensten.</span><span class="sxs-lookup"><span data-stu-id="beed3-297">Office 365 services.</span></span>
    
- <span data-ttu-id="beed3-298">Azure PaaS-Anwendungen, die über das Internet verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="beed3-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="beed3-299">LOB-Anwendungen in Azure, die von lokalen Umgebungen aus über die Site-to-Site-VPN- oder ExpressRoute-Verbindung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="beed3-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="beed3-300">Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="beed3-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="beed3-301">Infrastruktur der Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="beed3-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="beed3-302">Wenn Sie AD FS noch nicht lokal bereitgestellt haben, sollten Sie diese Vorteile der Bereitstellung dieser Arbeitsbelastung in Azure bedenken:</span><span class="sxs-lookup"><span data-stu-id="beed3-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="beed3-303">Bietet Autonomie für die Authentifizierung bei Cloud-Diensten (keine lokalen Abhängigkeiten)</span><span class="sxs-lookup"><span data-stu-id="beed3-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="beed3-304">Reduziert Server und Tools, die lokal gehostet werden</span><span class="sxs-lookup"><span data-stu-id="beed3-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="beed3-305">Verwendet ein Site-to-Site-VPN-Gateway auf einem Failovercluster mit zwei Knoten für die Verbindung mit Azure (neu)</span><span class="sxs-lookup"><span data-stu-id="beed3-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="beed3-306">Verwendet ACLs, um sicherzustellen, dass Web Application Proxy-Server nur mit AD FS, nicht direkt mit Domänencontrollern oder anderen Servern kommunizieren können</span><span class="sxs-lookup"><span data-stu-id="beed3-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![Bereitstellen einer Infrastruktur für die Verbundauthentifizierung in Azure](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="beed3-308">**Abbildung 9: Bereitstellen einer Infrastruktur für die Verbundauthentifizierung in Azure**</span><span class="sxs-lookup"><span data-stu-id="beed3-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="beed3-p129">Abbildung 9 zeigt eine Reihe von lokalen Domänencontrollern, die AD DS-Informationen mit einer Reihe von Domänencontrollern in einem virtuellen Azure-Netzwerk replizieren. Das auf einem Server im virtuellen Azure-Netzwerk ausgeführte Azure AD Connect-Tool fragt den lokalen Domänencontroller nach Änderungen ab und sendet diese Änderungen an Azure AD. Eingehende Authentifizierungsanforderungen an Azure AD von Microsoft SaaS-Diensten, Azure PaaS-Anwendungen und anderen Cloud-Anwendungen werden an einen externen Lastenausgleich weitergeleitet, der die Anforderung an eine Gruppe von Web Application Proxy-Servern weiterleitet. Die Web Application Proxy-Server leiten die Anforderung an einen internen Lastenausgleich weiter, der die Anforderung an eine Gruppe von AD FS-Servern weiterleitet. Die AD FS-Server leiten dann die Anforderung an einen Domänencontroller weiter, um die gesendeten Anmeldeinformationen zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="beed3-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="beed3-314">Diese Lösung funktioniert mit:</span><span class="sxs-lookup"><span data-stu-id="beed3-314">This solution works with:</span></span>
  
- <span data-ttu-id="beed3-315">Programme, die Kerberos erfordern</span><span class="sxs-lookup"><span data-stu-id="beed3-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="beed3-316">Alle Microsoft SaaS-Dienste</span><span class="sxs-lookup"><span data-stu-id="beed3-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="beed3-317">Anwendungen in Azure, die Internetzugang haben</span><span class="sxs-lookup"><span data-stu-id="beed3-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="beed3-318">Anwendungen in Azure IaaS oder PaaS, die Authentifizierung mit einer Gruppe von Konten in den AD DS Ihrer Organisation erfordern</span><span class="sxs-lookup"><span data-stu-id="beed3-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="beed3-319">Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="beed3-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="beed3-320">Eigenständige AD DS-Umgebung in einem virtuellen Azure-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="beed3-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="beed3-p130">Sie müssen eine Cloud-Anwendung nicht immer in Ihre lokale Umgebung integrieren. Eine eigenständige AD DS-Domäne in einem virtuellen Azure-Netzwerk unterstützt beispielsweise Anwendungen, die öffentlich zugänglich sind, z. B. Internetwebsites.</span><span class="sxs-lookup"><span data-stu-id="beed3-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![Eine eigenständige AD DS-Umgebung für eine serverbasierte Anwendung](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="beed3-324">**Abbildung 10: Eine eigenständige AD DS-Umgebung für eine serverbasierte Anwendung**</span><span class="sxs-lookup"><span data-stu-id="beed3-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="beed3-p131">Abbildung 10 zeigt ein virtuelles Azure-Netzwerk, das eine Reihe von AD DS-Servern hostet, die AD DS- und DNS-Dienste mit einer Reihe von Servern bereitstellt, die eine Anwendung hosten. Diese Lösung funktioniert mit:</span><span class="sxs-lookup"><span data-stu-id="beed3-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="beed3-327">Websites und Anwendungen, die das Internet nutzen</span><span class="sxs-lookup"><span data-stu-id="beed3-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="beed3-328">Anwendungen, die NTLM- oder Kerberos-Authentifizierung erfordern</span><span class="sxs-lookup"><span data-stu-id="beed3-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="beed3-329">Anwendungen, die auf Windows-basierten Servern, die AD DS erfordern, ausgeführt werden</span><span class="sxs-lookup"><span data-stu-id="beed3-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="beed3-330">Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="beed3-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="beed3-331">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="beed3-331">See Also</span></span>

[<span data-ttu-id="beed3-332">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="beed3-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="beed3-333">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="beed3-333">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



