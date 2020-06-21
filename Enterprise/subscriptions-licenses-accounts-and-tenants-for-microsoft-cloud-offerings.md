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
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Zusammenfassung: Lernen Sie die Beziehungen von Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über die Microsoft-Cloudangebote hinweg kennen.'
ms.openlocfilehash: ad4307b2725fa37f6b28540b92895fc78f097c6c
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735963"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Abonnements, Lizenzen, Konten und Mandanten für Microsoft-Cloud-Angebote

 **Zusammenfassung:** Lernen Sie die Beziehungen von Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über die Microsoft-Cloudangebote hinweg kennen.
  
Microsoft stellt eine Hierarchie von Organisationen, Abonnements, Lizenzen und Benutzerkonten für die konsistente Verwendung von Identitäten und die Abrechnung über seine Cloudangebote hinweg bereit.
  
- Microsoft Office 365
- Microsoft Azure
- Microsoft InTune und Enterprise Mobility + Security (EMS)
- Microsoft Dynamics 365

[Microsoft 365](https://docs.microsoft.com/microsoft-365/) kombiniert Office 365, EMS und Windows 10 Enterprise in einem einzigen Abonnement und einer Reihe integrierter Dienste.

## <a name="elements-of-the-hierarchy"></a>Elemente der Hierarchie

Dies sind die Elemente der Hierarchie:
  
### <a name="organization"></a>Organization (Organisation)

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>Abonnements

Ein Abonnement ist eine Vereinbarung mit Microsoft zur Verwendung einer oder mehrerer Cloudplattformen oder -dienste, für die basierend auf einer Lizenzgebühr pro Benutzer oder einem cloudbasierten Ressourcenverbrauch Kosten anfallen. 

- Bei den SaaS-basierten (Software-as-a-Service) Cloudangeboten von Microsoft (Office 365, Intune/EMS und Dynamics 365) werden Lizenzgebühren pro Benutzer abgerechnet. 
- Bei den PaaS- und IaaS-Cloudangeboten (Platform-as-a-Service; Infrastructure-as-a-Service) von Microsoft (Azure) wird basierend auf dem Ressourcenverbrauch in der Cloud abgerechnet.
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
Organisationen können mehrere Abonnements für die Cloudangebote von Microsoft haben. Abbildung 1 zeigt eine einzelne Organisation mit mehreren Office 365-Abonnements, einem Intune-Abonnement, einem Dynamics 365-Abonnement und mehreren Azure-Abonnements.

**Abbildung 1: Beispiel für eine Organisation mit mehreren Abonnements**

![Eine Beispielorganisation mit mehreren Abonnements für Microsoft Cloud-Angebote.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a>Lizenzen

Bei den SaaS-Cloudangeboten von Microsoft ermöglicht eine Lizenz einem bestimmten Benutzerkonto, die Dienste des Cloudangebots zu nutzen. Ihnen wird eine feste monatliche Gebühr als Teils Ihres Abonnements in Rechnung gestellt. Administratoren weisen Lizenzen einzelnen Benutzerkonten in dem Abonnement zu. Für das Beispiel in Abbildung 2 verfügt die Contoso Corporation über ein Office 365 Enterprise E5-Abonnement mit 100 Lizenzen, mit dem bis zu 100 einzelne Benutzerkonten die Features und Dienste von Office 365 Enterprise E5 nutzen können.
  
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

For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.
  
### <a name="summary-of-the-hierarchy"></a>Zusammenfassung der Hierarchie

Es folgt eine kurze Wiederholung:
  
- Eine Organisation kann mehrere Abonnements haben.
    
  - Ein Abonnement kann mehrere Lizenzen haben.
    
  - Lizenzen können einzelnen Benutzerkonten zugewiesen werden.
    
  - Benutzerkonten werden in einem Azure AD-Mandanten gespeichert.
    
Im Folgenden finden Sie ein Beispiel für die Beziehung von Organisationen, Abonnements, Lizenzen und Benutzerkonten:
  
- Eine durch ihre öffentlichen Domänennamen identifizierte Organisation.
    
  - Ein Office 365 Enterprise E3-Abonnement mit Benutzerlizenzen.
    
    Ein Office 365 Enterprise E5-Abonnement mit Benutzerlizenzen.
    
    Ein EMS-Abonnement mit Benutzerlizenzen.
    
    Ein Dynamics 365-Abonnement mit Benutzerlizenzen.
    
    Mehrere Azure-Abonnements.
    
  - Die Benutzerkonten der Organisation in einem gemeinsamen Azure AD-Mandanten.
    
Mehrere Abonnements für Cloudangebote von Microsoft können denselben Azure AD-Mandanten verwenden, der als gemeinsamer Identitätsanbieter fungiert. Ein zentraler Azure AD-Mandant, der die synchronisierten Konten Ihrer lokalen AD DS enthält, stellt eine cloudbasierte IDaaS (Identity-as-a-Service) für Ihre Organisation bereit. 
  
**Abbildung 4: Synchronisierte lokale Konten und IDaaS für eine Organisation**

![IDaaS (Identity as a Service) für Ihre Organisation.](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Kombinieren von Abonnements für mehrere Microsoft-Cloudangebote

Die folgende Tabelle beschreibt, wie Sie mehrere Microsoft-Cloudangebote basierend auf dem Vorhandensein eines Abonnement für einen Typ von Cloudangebot (die Bezeichnungen laufen in der ersten Spalte nach unten) und dem Hinzufügen eines Abonnements für ein anderes Cloudangebot (von links nach rechts) kombinieren können.
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |–  <br/> |Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.  <br/> |Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation aus dem Microsoft 365 Admin Center hinzu.  <br/> |Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation aus dem Microsoft 365 Admin Center hinzu.  <br/> |
|**Azure** <br/> |Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.  <br/> |–  <br/> |Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation hinzu.  <br/> |Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.  <br/> |
|**Intune/EMS** <br/> |Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.  <br/> |Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.  <br/> |–  <br/> |Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.  <br/> |
|**Dynamics 365** <br/> |Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.  <br/> |Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.  <br/> |Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation hinzu.  <br/> |NV  <br/> |
   
Eine einfache Möglichkeit zum Hinzufügen von Abonnements zu Ihrer Organisation für Microsoft SaaS-basierte Dienste erfolgt über das Admin Center:
  
1. Melden Sie sich mit Ihrem globalen Administratorkonto beim Microsoft 365 Admin Center ([https://admin.microsoft.com](https://admin.microsoft.com)) an.
    
2. Klicken Sie im linken Navigationsbereich der **Admin Center**-Startseite auf **Abrechnung** und dann auf **Dienste kaufen**.
    
3. Erwerben Sie auf der Seite **Dienste kaufen** Ihre neuen Abonnements.
    
Das Admin Center ordnet die Organisation und den Azure AD-Mandanten Ihres Office 365-Abonnements den neuen Abonnements für SaaS-basierte Cloudangebote zu.
  
So fügen Sie ein Azure-Abonnement mit derselben Organisation und demselben Azure AD-Mandanten wie das Office 365-Abonnement hinzu
  
1. Melden Sie sich mit Ihrem globalen Office 365-Administratorkonto beim Azure-Portal ([https://portal.azure.com](https://portal.azure.com)) an.
    
2. Klicken Sie im linken Navigationsbereich auf **Abonnements** und dann auf **Hinzufügen**.
    
3. Wählen Sie auf der Seite **Abonnement hinzufügen** ein Angebot aus, und schließen Sie die Bezahlung und die Vereinbarung ab.
    
Wenn Sie die Abonnements für Azure und Office 365 einzeln erworben haben und den Office 365 Azure AD-Mandanten von Ihrem Azure-Abonnement aus aufrufen möchten, finden Sie entsprechende Anweisungen unter [Hinzufügen eines vorhandenen Azure-Abonnements zu Ihrem Azure Active Directory-Mandanten](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>Siehe auch

[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Architekturmodelle für SharePoint, Exchange, Skype for Business und Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Hybridlösungen](hybrid-solutions.md)

## <a name="next-step"></a>Nächster Schritt

[Bewerten der Office 365-Netzwerkkonnektivität](assessing-network-connectivity.md)
  
