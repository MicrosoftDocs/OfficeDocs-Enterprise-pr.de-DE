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
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Abonnements, Lizenzen, Konten und Mandanten für Microsoft-Cloud-Angebote

 **Zusammenfassung:** Lernen Sie die Beziehungen von Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über die Microsoft-Cloudangebote hinweg kennen.
  
Microsoft stellt eine Hierarchie von Organisationen, Abonnements, Lizenzen und Benutzerkonten für die konsistente Verwendung von Identitäten und die Abrechnung über seine Cloudangebote hinweg bereit.
  
- Microsoft Office 365
- Microsoft Azure
- Microsoft Intune und Enterprise Mobility + Security (EMS)
- Microsoft Dynamics 365

[Microsoft 365](https://docs.microsoft.com/microsoft-365/) kombiniert Office 365, EMS und Windows 10 Enterprise in einem einzigen Abonnement und einer Reihe integrierter Dienste.

## <a name="elements-of-the-hierarchy"></a>Elemente der Hierarchie

Dies sind die Elemente der Hierarchie:
  
### <a name="organization"></a>Organization (Organisation)

Eine Organisation stellt eine Wirtschaftseinheit dar, die Microsoft-Cloudangebote verwendet und in der Regel von einem oder mehreren öffentlichen DNS-Domänennamen (Domain Name System) identifiziert wird, z. B. contoso.com. Die Organisation ist ein Container für Abonnements.
  
### <a name="subscriptions"></a>Abonnements

Ein Abonnement ist eine Vereinbarung mit Microsoft zur Verwendung einer oder mehrerer Cloudplattformen oder -dienste, für die basierend auf einer Lizenzgebühr pro Benutzer oder einem cloudbasierten Ressourcenverbrauch Kosten anfallen. 

- Bei den SaaS-basierten (Software-as-a-Service) Cloudangeboten von Microsoft (Office 365, Intune/EMS und Dynamics 365) werden Lizenzgebühren pro Benutzer abgerechnet. 
- Bei den PaaS- und IaaS-Cloudangeboten (Platform-as-a-Service; Infrastructure-as-a-Service) von Microsoft (Azure) wird basierend auf dem Ressourcenverbrauch in der Cloud abgerechnet.
 
Sie können auch ein Testabonnement verwenden, das Abonnement läuft jedoch nach einem bestimmten Zeitraum oder einem bestimmten Betrag von Verbrauchsgebühren ab. Sie können ein Testabonnement in ein kostenpflichtiges Abonnement umwandeln.
  
Organisationen können mehrere Abonnements für die Cloudangebote von Microsoft haben. Abbildung 1 zeigt eine einzelne Organisation mit mehreren Office 365-Abonnements, einem Intune-Abonnement, einem Dynamics 365-Abonnement und mehreren Azure-Abonnements.

**Abbildung 1: Beispiel für eine Organisation mit mehreren Abonnements**

![Eine Beispielorganisation mit mehreren Abonnements für Microsoft Cloud-Angebote.](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a>Lizenzen

Bei den SaaS-Cloudangeboten von Microsoft ermöglicht eine Lizenz einem bestimmten Benutzerkonto, die Dienste des Cloudangebots zu nutzen. Ihnen wird eine feste monatliche Gebühr als Teils Ihres Abonnements in Rechnung gestellt. Administratoren weisen Lizenzen einzelnen Benutzerkonten in dem Abonnement zu. Für das Beispiel in Abbildung 2 verfügt die Contoso Corporation über ein Office 365 Enterprise E5-Abonnement mit 100 Lizenzen, mit dem bis zu 100 einzelne Benutzerkonten die Features und Dienste von Office 365 Enterprise E5 nutzen können.
  
**Abbildung 2: Lizenzen innerhalb der SaaS-basierten Abonnements für eine Organisation**

![Ein Beispiel für mehrere Lizenzen innerhalb von Abonnements für auf SaaS-basierende Microsoft-Cloudangebote.](media/Subscriptions/Subscriptions-Fig2.png)
  
Bei PaaS-basierten Azure-Clouddiensten sind Softwarelizenzen in den Dienstpreis integriert.
  
Bei IaaS-basierten virtuellen Azure-Computern sind möglicherweise zusätzliche Lizenzen zur Nutzung der Software oder der Anwendung erforderlich, die auf einem virtuellen Computerabbild installiert ist. Einige virtuelle Computerabbilder weisen lizenzierte Versionen der installierten Software auf, und die Kosten sind in dem Minutenpreis für den Server enthalten. Beispiele hierfür sind die virtuellen Computerabbilder für SQL Server 2014 und SQL Server 2016. 
  
Einige virtuelle Computerabbilder verfügen über Testversionen von installierten Anwendungen und benötigen zusätzliche Softwareanwendungslizenzen für die Verwendung über den Testzeitraum hinaus. Auf dem virtuellen Computerabbild der Testversion von SharePoint Server 2016 ist beispielsweise eine Testversion von SharePoint Server 2016 vorinstalliert. Um SharePoint Server 2016 nach dem Ablaufdatum der Testversion weiter zu verwenden, müssen Sie eine Lizenz für SharePoint Server 2016 und Clientlizenzen von Microsoft erwerben. Diese Gebühren fallen separat zum Azure-Abonnement an, und der Minutenpreis für das Ausführen des zugrunde liegenden virtuellen Computers tritt weiterhin zu.
  
### <a name="user-accounts"></a>Benutzerkonten

Benutzerkonten für alle Microsoft-Cloudangebote werden in einem Azure AD-Mandanten (Azure AD) gespeichert, der Benutzerkonten und -gruppen enthält. Ein Azure AD-Mandant kann mit Ihren vorhandenen Active Directory Domain Services (AD DS)-Konten mithilfe von Azure AD Connect, einem Windows Server-basierten Dienst, synchronisiert werden. Dies wird als Verzeichnissynchronisation oder DirSync bezeichnet.
  
Abbildung 3 zeigt ein Beispiel für mehrere Abonnements einer Organisation, die einen allgemeinen Azure AD-Mandanten verwendet, der die Konten der Organisation enthält.
  
**Abbildung 3: Mehrere Abonnements einer Organisation, die den gleichen Azure AD-Mandanten verwenden**

![Eine Beispielorganisation mit mehreren Abonnements, die alle den gleichen Azure AD-Mandanten verwenden.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Mandanten

Bei SaaS-Cloudangeboten ist der Mandant die regionale Stelle, an der sich die Server befinden, die Clouddienste bereitstellen. Die Contoso Corporation hat beispielsweise Europa als Region zum Hosten ihrer Office 365-, EMS- und Dynamics 365-Mandanten für die 15.000 Mitarbeiter in der Zentrale in Paris festgelegt.
  
Azure PaaS-Dienste und in Azure IaaS gehostete VM-basierte Arbeitslasten können Mandanten in einem beliebigen Azure-Rechenzentrum auf der ganzen Welt haben. Sie geben das Azure-Rechenzentrum an, das als Standort bezeichnet wird, wenn Sie die Azure PaaS-App oder den Dienst bzw. das Element einer IaaS-IT-Arbeitslast erstellen.
  
Bei einem Azure AD-Mandanten handelt es sich um eine bestimmte Instanz von Azure AD, die Konten und Gruppen enthält. Kostenpflichtige oder Testabonnements von Office 365, Dynamics 365 oder Intune/EMS enthalten einen kostenlosen Azure AD-Mandanten. Dieser Azure AD-Mandant enthält keine anderen Azure-Dienste und ist nicht das gleiche wie ein Azure-Testabonnement oder ein kostenpflichtiges Azure-Abonnement.
  
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
  
In Abbildung 4 wird gezeigt, wie ein gemeinsamer Azure AD-Mandant von Microsoft-SaaS-Cloudangeboten, Azure PaaS-Apps und virtuellen Computern in Azure IaaS verwendet wird, die Azure AD-Domänendienste verwenden. Die lokale AD DS-Gesamtstruktur wird mithilfe von Azure AD Connect mit dem Azure AD-Mandanten synchronisiert.
  
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
  
