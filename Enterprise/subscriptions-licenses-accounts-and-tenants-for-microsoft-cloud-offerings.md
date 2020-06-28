---
title: Abonnements, Lizenzen, Konten und Mandanten für Microsoft-Cloud-Angebote
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Zusammenfassung: Lernen Sie die Beziehungen von Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über die Microsoft-Cloudangebote hinweg kennen.'
ms.openlocfilehash: 52857196f53a44196c96f60bd70564f5e3221b80
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906268"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Abonnements, Lizenzen, Konten und Mandanten für Microsoft-Cloud-Angebote

Microsoft stellt eine Hierarchie von Organisationen, Abonnements, Lizenzen und Benutzerkonten für die konsistente Verwendung von Identitäten und die Abrechnung über seine Cloudangebote hinweg bereit.
  
- Microsoft 365 und Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>Elemente der Hierarchie

Dies sind die Elemente der Hierarchie:
  
### <a name="organization"></a>Organization (Organisation)

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>Abonnements

Ein Abonnement ist eine Vereinbarung mit Microsoft zur Verwendung einer oder mehrerer Cloudplattformen oder -dienste, für die basierend auf einer Lizenzgebühr pro Benutzer oder einem cloudbasierten Ressourcenverbrauch Kosten anfallen. 

- Microsoft-basierte Cloud-Angebote für Software as a Service (SaaS) (Microsoft 365 und Dynamics 365) Kosten pro Benutzer-Lizenzgebühren. 
- Bei den PaaS- und IaaS-Cloudangeboten (Platform-as-a-Service; Infrastructure-as-a-Service) von Microsoft (Azure) wird basierend auf dem Ressourcenverbrauch in der Cloud abgerechnet.
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
Organisationen können mehrere Abonnements für die Cloudangebote von Microsoft haben. Abbildung 1 zeigt eine einzelne Organisation mit mehreren Microsoft 365-Abonnements, einem Dynamics 365-Abonnement und mehreren Azure-Abonnements.

**Abbildung 1: Beispiel für eine Organisation mit mehreren Abonnements**

![Eine Beispielorganisation mit mehreren Abonnements für Microsoft Cloud-Angebote.](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>Lizenzen

Bei den SaaS-Cloudangeboten von Microsoft ermöglicht eine Lizenz einem bestimmten Benutzerkonto, die Dienste des Cloudangebots zu nutzen. Ihnen wird eine feste monatliche Gebühr als Teils Ihres Abonnements in Rechnung gestellt. Administratoren weisen Lizenzen einzelnen Benutzerkonten in dem Abonnement zu. Für das Beispiel in Abbildung 2 verfügt die Contoso Corporation über ein Microsoft 365 E5-Abonnement mit 100-Lizenzen, mit dem bis zu 100 einzelne Benutzerkonten für die Verwendung von Microsoft 365 E5-Features und-Diensten verwendet werden können.
  
**Abbildung 2: Lizenzen innerhalb der SaaS-basierten Abonnements für eine Organisation**

![Ein Beispiel für mehrere Lizenzen innerhalb von Abonnements für auf SaaS-basierende Microsoft-Cloudangebote.](media/Subscriptions/Subscriptions-Fig2.png)
  
Bei PaaS-basierten Azure-Clouddiensten sind Softwarelizenzen in den Dienstpreis integriert.
  
For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016. 
  
Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.
  
### <a name="user-accounts"></a>Benutzerkonten

Benutzerkonten für alle Microsoft-Cloudangebote werden in einem Azure AD-Mandanten (Azure AD) gespeichert, der Benutzerkonten und -gruppen enthält. Ein Azure AD-Mandant kann mit Ihren vorhandenen Active Directory Domain Services (AD DS)-Konten mithilfe von Azure AD Connect, einem Windows Server-basierten Dienst, synchronisiert werden. Dies wird als Verzeichnissynchronisierung bezeichnet.
  
Abbildung 3 zeigt ein Beispiel für mehrere Abonnements einer Organisation, die einen allgemeinen Azure AD-Mandanten verwendet, der die Konten der Organisation enthält.
  
**Abbildung 3: Mehrere Abonnements einer Organisation, die den gleichen Azure AD-Mandanten verwenden**

![Eine Beispielorganisation mit mehreren Abonnements, die alle den gleichen Azure AD-Mandanten verwenden.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Mandanten

Bei SaaS-Cloudangeboten ist der Mandant die regionale Stelle, an der sich die Server befinden, die Clouddienste bereitstellen. Beispielsweise wählte die Contoso Corporation die Europäische Region aus, um Ihre Microsoft 365-, EMS-und Dynamics 365-Mandanten für die 15.000 Mitarbeiter in Ihrem Pariser Hauptsitz zu hosten.
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
Bei einem Azure AD-Mandanten handelt es sich um eine bestimmte Instanz von Azure AD, die Konten und Gruppen enthält. Kostenpflichtige oder Testabonnements von Microsoft 365 oder Dynamics 365 umfassen einen kostenlosen Azure AD Mandanten. Dieser Azure AD-Mandant enthält keine anderen Azure-Dienste und ist nicht das gleiche wie ein Azure-Testabonnement oder ein kostenpflichtiges Azure-Abonnement.
  
### <a name="summary-of-the-hierarchy"></a>Zusammenfassung der Hierarchie

Es folgt eine kurze Wiederholung:
  
- Eine Organisation kann mehrere Abonnements haben.
    
  - Ein Abonnement kann mehrere Lizenzen haben.
    
  - Lizenzen können einzelnen Benutzerkonten zugewiesen werden.
    
  - Benutzerkonten werden in einem Azure AD-Mandanten gespeichert.
    
Im Folgenden finden Sie ein Beispiel für die Beziehung von Organisationen, Abonnements, Lizenzen und Benutzerkonten:
  
- Eine durch ihre öffentlichen Domänennamen identifizierte Organisation.
    
  - Ein Microsoft 365 E3-Abonnement mit Benutzerlizenzen.
    
    Ein Microsoft 365 E5-Abonnement mit Benutzerlizenzen.
    
    Ein Dynamics 365-Abonnement mit Benutzerlizenzen.
    
    Mehrere Azure-Abonnements.
    
  - Die Benutzerkonten der Organisation in einem gemeinsamen Azure AD-Mandanten.
    
Mehrere Abonnements für Cloudangebote von Microsoft können denselben Azure AD-Mandanten verwenden, der als gemeinsamer Identitätsanbieter fungiert. Ein zentraler Azure AD-Mandant, der die synchronisierten Konten Ihrer lokalen AD DS enthält, stellt eine cloudbasierte IDaaS (Identity-as-a-Service) für Ihre Organisation bereit. 
  
**Abbildung 4: Synchronisierte lokale Konten und IDaaS für eine Organisation**

![IDaaS (Identity as a Service) für Ihre Organisation.](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Kombinieren von Abonnements für mehrere Microsoft-Cloudangebote

Die folgende Tabelle beschreibt, wie Sie mehrere Microsoft-Cloudangebote basierend auf dem Vorhandensein eines Abonnement für einen Typ von Cloudangebot (die Bezeichnungen laufen in der ersten Spalte nach unten) und dem Hinzufügen eines Abonnements für ein anderes Cloudangebot (von links nach rechts) kombinieren können.
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |–  <br/> |Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.  <br/> |Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation aus dem Microsoft 365 Admin Center hinzu.  <br/> |
|**Azure** <br/> |Sie fügen Ihrem Unternehmen ein Microsoft 365-Abonnement hinzu.  <br/> |–  <br/> |Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.  <br/> |
|**Dynamics 365** <br/> |Sie fügen Ihrem Unternehmen ein Microsoft 365-Abonnement hinzu.  <br/> |Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.  <br/> |–  <br/> |
   
Eine einfache Möglichkeit zum Hinzufügen von Abonnements zu Ihrer Organisation für Microsoft SaaS-basierte Dienste erfolgt über das Admin Center:
  
1. Melden Sie sich mit Ihrem globalen Administratorkonto beim Microsoft 365 Admin Center ([https://admin.microsoft.com](https://admin.microsoft.com)) an.
    
2. Klicken Sie im linken Navigationsbereich der **Admin Center**-Startseite auf **Abrechnung** und dann auf **Dienste kaufen**.
    
3. Erwerben Sie auf der Seite **Dienste kaufen** Ihre neuen Abonnements.
    
Das Admin Center weist die Organisation und Azure AD Mandanten Ihres Microsoft 365-Abonnements den neuen Abonnements für SaaS-basierte Cloud-Angebote zu.
  
So fügen Sie ein Azure-Abonnement mit derselben Organisation und Azure AD Mandanten wie Ihr Microsoft 365-Abonnement hinzu:
  
1. Melden Sie sich beim Azure-Portal ( [https://portal.azure.com](https://portal.azure.com) ) mit ihrem globalen Administratorkonto von Microsoft 365 an.
    
2. Klicken Sie im linken Navigationsbereich auf **Abonnements** und dann auf **Hinzufügen**.
    
3. Wählen Sie auf der Seite **Abonnement hinzufügen** ein Angebot aus, und schließen Sie die Bezahlung und die Vereinbarung ab.
    
Wenn Sie Azure-und Microsoft 365-Abonnements separat erworben haben und von Ihrem Azure-Abonnement auf den Microsoft 365 Azure AD-Mandanten zugreifen möchten, lesen Sie die Anweisungen unter [Hinzufügen eines vorhandenen Azure-Abonnements zu Ihrem Azure Active Directory-Mandanten](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>Siehe auch

[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Architekturmodelle für SharePoint, Exchange, Skype for Business und Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Hybridlösungen](hybrid-solutions.md)

## <a name="next-step"></a>Nächster Schritt

[Bewerten der Microsoft 365-Netzwerkkonnektivität](assessing-network-connectivity.md)
  
