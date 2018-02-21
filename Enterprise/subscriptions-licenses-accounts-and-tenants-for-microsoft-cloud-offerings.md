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
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Abonnements, Lizenzen, Konten und Mandanten für Microsoft Cloud-angeboten

 **Zusammenfassung:** Verstehen der Beziehungen zwischen Organisationen, Abonnements, Lizenzen, Benutzerkonten und Mandanten über Microsoft Cloud-angeboten.
  
Microsoft bietet eine Hierarchie von Organisationen, Abonnements, Lizenzen und Benutzerkonten für die konsistente Verwendung von Identitäten und Abrechnung über die Cloud-angeboten:
  
- Microsoft Office 365
    
    Finden Sie unter [Geschäftspläne und zu Preisen](https://products.office.com/business/compare-office-365-for-business-plans) für Weitere Informationen.
    
- Microsoft Azure
    
    Weitere Informationen finden Sie unter [Azure Preise](https://azure.microsoft.com/pricing/) .
    
- Microsoft Intune und der Enterprise-Mobilität + Sicherheit (zur Abstimmung)
    
    Weitere Informationen finden Sie unter [Intune Preise](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) .
    
- Microsoft Dynamics 365
    
    Weitere Informationen finden Sie unter [Dynamics 365 Preise](https://dynamics.microsoft.com/) .
    
## <a name="elements-of-the-hierarchy"></a>Elemente der Hierarchie

Dies sind die Elemente der Hierarchie:
  
### <a name="organization"></a>Organisation

Eine Organisation stellt eine Wirtschaftseinheit dar, die Microsoft-Cloudangebote verwendet und in der Regel von einem öffentlichen DNS-Domänennamen (Domain Name System) identifiziert wird, z. B. contoso.com. Die Organisation ist ein Container für Abonnements.
  
### <a name="subscriptions"></a>Abonnements

Ein Abonnement ist eine Vereinbarung mit Microsoft eine oder mehrere Microsoft Cloud-Plattformen oder Dienste, für die Gebühren für fällig basierend auf eine benutzerbasierte Lizenzgebühr oder cloudbasierten Ressourcenverbrauch. Microsoft Software-as a Service (SaaS)-Basis Cloudlösungen (Office 365, Intune/zur Abstimmung und Dynamics 365) Gebühren pro-Benutzer-Lizenz. Microsoft Plattform als Service (PaaS) und als (IaaS) Cloud Dienstangebote (Azure) Servicekosten basierend auf Ressourcenverbrauch Cloud-Infrastruktur.
  
Sie können auch ein Testabonnement verwenden, das Abonnement läuft jedoch nach einem bestimmten Zeitraum oder einem bestimmten Betrag von Verbrauchsgebühren ab. Sie können ein Testabonnement in ein kostenpflichtiges Abonnement umwandeln.
  
Organisationen können mehrere Abonnements für Microsoft Cloud-angeboten haben. Abbildung 1 zeigt ein Beispiel.
  
**Abbildung 1: Beispiel für eine Organisation mehrere Abonnements**

![Eine Beispielorganisation mit mehreren Abonnements für Microsoft Cloud-Angebote.](images/Subscriptions/Subscriptions_Fig1.png)

  
Abbildung 1 zeigt eine einzelne Organisation mit mehreren Office 365-Abonnements, einem Intune-Abonnement, einem Dynamics 365-Abonnement und mehrere Azure-Abonnements.
  
### <a name="licenses"></a>Lizenzen

SaaS Cloudlösungen von Microsoft, eine Lizenz ermöglicht ein bestimmtes Benutzerkonto zu verwenden, die der Cloud-Dienste bietet. Sie werden im Rahmen Ihres Abonnements eine feste monatliche Gebühr erhoben. Administratoren weisen Lizenzen einzelnen Benutzerkonten im Abonnement. Für das Beispiel in Abbildung 2 hat der Contoso Corporation E5 für Office 365 Enterprise-Abonnement mit 100 Lizenzen, wodurch bis zu 100 einzelnen Benutzerkonten E5 Enterprise-Features und Dienste verwendet.
  
**Abbildung 2: Lizenzen innerhalb der SaaS-basierte Abonnements für eine Organisation**

![Ein Beispiel für mehrere Lizenzen innerhalb von Abonnements für auf SaaS-basierende Microsoft Cloud-Angebote.](images/Subscriptions/Subscriptions_Fig2.png)
  
Bei PaaS-basierten Azure-Clouddiensten sind Softwarelizenzen in den Dienstpreis integriert.  
  
Bei IaaS-basierten virtuellen Azure-Computern sind möglicherweise zusätzliche Lizenzen zur Nutzung der Software oder der Anwendung erforderlich, die auf einem virtuellen Computerabbild installiert ist. Einige virtuelle Computerabbilder weisen lizenzierte Versionen der installierten Software auf, und die Kosten sind in dem Minutenpreis für den Server enthalten. Beispiele hierfür sind die virtuellen Computerabbilder für SQL Server 2014 und SQL Server 2016.  
  
Einige virtuelle Computerabbilder verfügen über Testversionen von installierten Anwendungen und benötigen zusätzliche Softwareanwendungslizenzen für die Verwendung über den Testzeitraum hinaus. Auf dem virtuellen Computerabbild der Testversion von SharePoint Server 2016 ist beispielsweise eine Testversion von SharePoint Server 2016 vorinstalliert. Um SharePoint Server 2016 nach dem Ablaufdatum der Testversion weiter zu verwenden, müssen Sie eine Lizenz für SharePoint Server 2016 und Clientlizenzen von Microsoft erwerben. Diese Gebühren fallen separat zum Azure-Abonnement an, und der Minutenpreis für das Ausführen des zugrunde liegenden virtuellen Computers tritt weiterhin zu.
  
### <a name="user-accounts"></a>Benutzerkonten

Benutzerkonten für alle Microsoft Cloud-angeboten werden in einem Mandanten Azure Active Directory (AD) gespeichert, die Benutzerkonten und Gruppen enthält. Ein Azure AD-Mandanten kann Ihrer vorhandenen Windows Azure AD-Konten mit Azure Active Directory verbinden, eine Windows Server-basierten Dienst synchronisiert werden. Dies wird als verzeichnissynchronisierung (DirSync) bezeichnet.
  
Abbildung 3 zeigt ein Beispiel für mehrere Abonnements einer Organisation, die einen allgemeinen Azure AD-Mandanten verwendet, der die Konten der Organisation enthält.
  
**Abbildung 3: Mehrere Abonnements einer Organisation, die den gleichen Azure AD-Mandanten verwenden**

![Eine Beispielorganisation mit mehreren Abonnements, die alle den gleichen Azure AD-Mandanten verwenden.](images/Subscriptions/Subscriptions_Fig3.png)
  
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
    
Mehrere Abonnements für Cloudangebote von Microsoft können denselben Azure AD-Mandanten verwenden, der als gemeinsamer Identitätsanbieter fungiert. Ein zentraler Azure AD-Mandant, der die synchronisierten Konten Ihres lokalen Windows Server AD enthält, stellt eine cloudbasierte IDaaS (Identity-as-a-Service) für Ihre Organisation bereit. Dies ist in Abbildung 4 dargestellt.
  
**Abbildung 4: Synchronisierten lokalen Konten und IDaaS für eine Organisation**

![IDaaS (Identity as a Service) für Ihre Organisation.](images/Subscriptions/Subscriptions_Fig4.png)
  
In Abbildung 4 wird gezeigt, wie ein gemeinsamer Azure AD-Mandant von Microsoft-SaaS-Cloudangeboten, Azure PaaS-Apps und virtuellen Computern in Azure IaaS verwendet wird, die Azure AD-Domänendienste verwenden. Die lokale Windows Server AD-Gesamtstruktur wird mithilfe von Azure AD Connect mit dem Azure AD-Mandanten synchronisiert.
  
Weitere Informationen zu Identitätsintegration über Microsoft Cloud-Angeboten finden Sie unter [Microsoft Cloudidentität für Enterprise-konstruiert](https://aka.ms/cloudarchidentity).
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Kombinieren von Abonnements für mehrere Microsoft-Cloudangebote

Die folgende Tabelle beschreibt, wie Sie mehrere Microsoft-Cloudangebote basierend auf dem Vorhandensein eines Abonnement für einen Typ von Cloudangebot (die Bezeichnungen laufen in der ersten Spalte nach unten) und dem Hinzufügen eines Abonnements für ein anderes Cloudangebot (von links nach rechts) kombinieren können.
  
||**Office 365**|**Azure**|**Intune/zur Abstimmung**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |–  <br/> |Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.  <br/> |Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation aus dem Office 365-Portal hinzu.  <br/> |Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation aus dem Office 365-Portal hinzu.  <br/> |
|**Azure** <br/> |Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.   <br/> |–  <br/> |Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation hinzu.  <br/> |Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.  <br/> |
|**Intune/zur Abstimmung** <br/> |Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.   <br/> |Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.  <br/> |–  <br/> |Sie fügen ein Dynamics 365-Abonnement zu Ihrer Organisation hinzu.  <br/> |
|**Dynamics 365** <br/> |Sie fügen ein Office 365-Abonnement zu Ihrer Organisation hinzu.   <br/> |Sie fügen ein Azure-Abonnement zu Ihrer Organisation aus dem Azure-Portal hinzu.  <br/> |Sie fügen ein Intune/EMS-Abonnement zu Ihrer Organisation hinzu.  <br/> |–  <br/> |
   
Eine einfache Möglichkeit zum Hinzufügen von Abonnements zu Ihrer Organisation für Microsoft SaaS-basierte Dienste erfolgt über das Office 365 Admin Center:
  
1. Melden Sie sich bei Office 365-Portal ([https://portal.office.com](https://portal.office.com)) mit der globale Administratorkonto ein, und klicken Sie dann auf **Admin**.
    
2. Klicken Sie im linken Navigationsbereich der Homepage der **Verwaltungskonsole** auf **Abrechnung**und klicken Sie dann auf **Dienste erwerben**.
    
3. Erwerben Sie Ihre neue Abonnements, auf der Seite **Dienste erwerben** .
    
Das Office 365 Admin Center ordnet die Organisation und den Azure AD-Mandanten Ihres Office 365-Abonnements den neuen Abonnements für SaaS-basierte Cloudangebote zu.
  
So fügen Sie ein Azure-Abonnement mit derselben Organisation und demselben Azure AD-Mandanten wie das Office 365-Abonnement hinzu
  
1. Melden Sie sich bei des Azure-Portals ([https://portal.azure.com](https://portal.azure.com)) mit Ihrem Office 365 globaler Administrator-Konto.
    
2. Klicken Sie im linken Navigationsbereich auf **Abonnements**und klicken Sie dann auf **Hinzufügen**.
    
3. Klicken Sie auf der Seite **Abonnement hinzufügen** wählen Sie ein Angebot, und führen Sie die Zahlungsinformationen und Vereinbarung.
    
Wenn Sie Azure und Office 365-Abonnements separat erworben und den Office 365 Azure AD-Mandanten aus dem Azure-Abonnement aufrufen möchten, finden Sie in [einem Office 365-Mandanten mit einem Azure-Abonnement zuordnen](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).
  
## <a name="see-also"></a>Weitere Artikel

[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Architekturmodelle für SharePoint, Exchange, Skype for Business und Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Hybridlösungen](hybrid-solutions.md)
  
[Abonnements, Lizenzen und Benutzerkonten für die Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



