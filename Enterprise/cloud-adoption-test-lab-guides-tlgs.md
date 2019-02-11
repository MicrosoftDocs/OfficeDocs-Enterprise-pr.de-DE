---
title: Testen von Office 365 mit Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/23/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Zusammenfassung: Verwenden Sie die folgenden Testumgebungsanleitungen zur Cloudakzeptanz, um Demo-, Wirksamkeitsnachweis- oder Entwicklungs-/Testumgebungen für Office 365, Dynamics 365 und Office Server-Produkte einzurichten.'
ms.openlocfilehash: df4729c93f3665bdfe072102f2952d7432ad22f0
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897238"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>Testen von Office 365 mit Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz

 **Zusammenfassung:** Verwenden Sie die folgenden Testumgebungsanleitungen zur Cloudakzeptanz, um Demo-, Wirksamkeitsnachweis- oder Entwicklungs-/Testumgebungen für Office 365, Dynamics 365 und Office Server-Produkte einzurichten.
  
Mithilfe von Testumgebungsanleitungen können Sie sich schnell mit Microsoft-Produkten vertraut machen. Sie eignen sich besonders für Situationen, in denen Sie eine Technologie oder Konfiguration bewerten müssen, bevor Sie entscheiden, ob sie die richtige für Sie ist oder bevor Sie sie für Ihre Benutzer einführen. Diese praktische Erfahrung erweitert Ihre Kenntnisse der Bereitstellungsanforderungen neuer Produkte oder Lösungen, sodass Sie besser planen können, wie diese in der Produktionsumgebung gehostet werden sollen.
  
Leitfäden zu Test Lab (Test Lab Guides, TLG) ermöglichen auch die Erstellung repräsentativer Umgebungen zum Entwickeln und Testen von Anwendungen, auch als Entwicklungs-/Testumgebungen bezeichnet.
  
![Testumgebungsanleitungen in der Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Sehen Sie sich diese zusätzlichen Ressourcen an, bevor Sie loslegen:
  
- Sehen Sie sich die Microsoft Virtual Academy-Sitzung [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) an (nur 22 Minuten).
    
- Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
    
## <a name="office-365-devtest-environment"></a>Office 365-Entwicklungs-/Testumgebung

Verwenden Sie die folgenden Artikel zum Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung:
  
- [Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
    
    Erstellen eines vereinfachten Intranets, das in Microsoft Azure-Infrastrukturdiensten ausgeführt wird. Dies ist ein optionaler Schritt, wenn Sie eine simulierte Unternehmenskonfiguration erstellen möchten.
    
- [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
    
    Erstellen eines Office 365 Enterprise E5-Testabonnements, vom Computer aus oder einem vereinfachten Intranet, das in Azure-Infrastrukturdiensten ausgeführt wird.
    
- [DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md)
    
    Installation und Konfiguration von Azure AD Connect für die Verzeichnissynchronisierung mit Kennwortsynchronisierung. Dies ist ein optionaler Schritt, wenn Sie eine simulierte Unternehmenskonfiguration erstellen möchten.
    
Verwenden Sie die folgenden Artikel für Ihre Office 365-Entwicklungs-/Testumgebung, um Unternehmensfeatures von Office 365 zu veranschaulichen:
  
- [Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Konfigurieren und testen Sie die sekundäre Authentifizierung mithilfe einer Textnachricht, die an Ihr Smartphone für ein Konto in Ihrem Office 365-Abonnement gesendet wird.
    
- [Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Konfigurieren und veranschaulichen Sie die Verbundauthentifizierung mit den Konten einer Windows Server Active Directory-Domäne.
    
- [Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Konfigurieren und Vorführen von Office 365 Cloud App Security, das Ihnen das Erstellen von Richtlinien ermöglicht, die verdächtige Aktivitäten in Ihrem Office 365-Abonnement überwachen und Sie ggf. informieren.
    
- [Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Konfigurieren und Vorführen von Advanced Threat Protection (ATP), ein Feature von Exchange Online Protection (EOP), das Ihnen hilft, Schadsoftware von Ihrer E-Mail fernzuhalten.
    
- [Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Hinzufügen von Beispieldaten und Vorführen von Advanced eDiscovery, das Ihnen ermöglicht, die in Office 365 gespeicherten Daten schnell zu suchen und zu analysieren, einschließlich E-Mails und Dokumente.
    
- [Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Veranschaulichen, wie Sie Office 365 Information Rights Management verwenden können, um die Daten in vertraulichen Dokumenten auch dann zu schützen, wenn sie versehentlich in den falschen Dokumentordnern veröffentlicht werden.
    
- [Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Veranschaulichen Sie, wie der Azure Information Protection(AIP)-Client zum Klassifizieren von Dokumenten mit verschiedenen Sicherheitsstufen verwendet werden kann.
    
- [Isolierte SharePoint Online-Teamwebsite in Ihrer Office 365-Entwicklungs-/Testumgebung](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Veranschaulichen, wie eine SharePoint Online-Teamwebsite erstellt wird, die aufgrund von vertraulichen oder streng vertraulichen Ressourcen vom Rest der Organisation isoliert ist.
    
## <a name="the-microsoft-365-enterprise-test-environment"></a>Die Microsoft 365 Enterprise-Testumgebung

Erstellen Sie anhand der [folgenden Artikel](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) eine Testumgebung für [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/).
 
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365- und Dynamics 365-Entwicklungs-/Testumgebung

Hinzufügen eines Dynamics 365-Testabonnements und Testen von Office 365- und integrierten Dynamics 365-Unternehmensfeatures und -Szenarien mit den folgenden Artikeln:
  
- [Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](office-365-and-dynamics-365-dev-test-environment.md)
    
    Hinzufügen eines Dynamics 365-Testabonnements und von Dynamics 365-Lizenzen und -Berechtigungen zu Benutzerkonten
    
- [Exchange Online-Integration für Ihre Office 365 und Dynamics 365-Entwicklungs-/Testumgebung](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Nehmen Sie die Konfiguration vor, und demonstrieren Sie dann, wie Office 365 und Dynamics 365 in Exchange Online-Postfächern zusammenarbeiten.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>Die One Microsoft Cloud-Entwicklungs-/Testumgebung

Erstellen Sie eine Entwicklungs-/Testumgebung, die alle Microsoft-Cloudangebote enthält: Office 365, Azure, EMS und Dynamics 365. Schrittweise Anweisungen finden Sie unter [Die One Microsoft Cloud-Entwicklungs-/Testumgebung](the-one-microsoft-cloud-dev-test-environment.md).
  
## <a name="simulated-cross-premises-devtest-environments"></a>Simulierte standortübergreifende Entwicklungs-/Testumgebung

Unter Verwendung der folgenden Artikel können Sie eine standortübergreifende Entwicklungs-/Testumgebung erstellen, die ein virtuelles Azure-Netzwerk und ein simuliertes standortübergreifendes Netzwerk umfasst.
  
- [Simuliertes standortübergreifendes virtuelles Netzwerk in Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Erstellen eines simulierten Intranets, das mit einem virtuellen Azure-Netzwerk in einer Hybrid-Cloud-Konfiguration verbunden ist.
    
- [Entwicklungs-/Testumgebung von Intranet SharePoint Server 2016 in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Erstellen Sie eine SharePoint Server 2016-Farm mit einem einzigen Server im virtuellen Azure-Netzwerk, und testen Sie die Konnektivität und Verwaltung vom simulierten standortübergreifenden Netzwerk aus.
    
## <a name="additional-cloud-based-devtest-environments"></a>Zusätzliche cloudbasierte Entwicklungs-/Testumgebungen

In den folgenden Themen finden Sie zusätzliche cloudbasierte Entwicklungs-/Testumgebungen, die Sie in Azure-Infrastrukturdiensten erstellen können:
  
- [SharePoint Server 2016-Entwicklungs-/Testumgebung in Azure](https://technet.microsoft.com/library/mt723354.aspx)
    
    Erstellen einer SharePoint Server 2016-Farm mit einem einzigen Server in Azure-Infrastrukturdiensten.
    
- [Exchange 2016-Entwicklungs-/Testumgebung in Azure](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Erstellen eines einzelnen Exchange 2016-Servers in Azure-Infrastrukturdiensten.
    
- [SharePoint Server 2013 dev/test environments in Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Erstellen von einfachen und hochverfügbaren SharePoint Server 2013-Farmen in Azure-Infrastrukturdiensten.
    
## <a name="see-also"></a>Siehe auch

[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Architekturmodelle für SharePoint, Exchange, Skype for Business und Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Hybridlösungen](hybrid-solutions.md)


