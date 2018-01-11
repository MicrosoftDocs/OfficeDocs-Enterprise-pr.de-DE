---
title: "Hybrid Cloud-Szenarien für Microsoft SaaS (Office 365)"
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
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Zusammenfassung: Grundlegendes zur Hybrid-Architektur und Szenarien für Microsofts SaaS-basierte cloud-angeboten (Office 365)."
ms.openlocfilehash: 63126d694817f8323494e584f1f497a1a732c678
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Hybrid Cloud-Szenarien für Microsoft SaaS (Office 365)

 **Zusammenfassung:** Grundlegendes zur Hybrid-Architektur und Szenarien für Microsofts SaaS-basierte cloud-angeboten (Office 365).
  
Kombinieren Sie lokale Bereitstellungen von Exchange, SharePoint oder Skype for Business mit ihren Gegenstücken in Office 365 als Bestandteile einer Cloudmigrations- oder langfristigen Integrationsstrategie.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Architektur für Microsoft SaaS-Hybridszenarien

Abbildung 1 zeigt die Architektur der SaaS-basierten Hybridszenarien von Microsoft für Office 365.
  
**Abbildung 1: Microsoft SaaS-basierte hybridszenarien für Office 365**

![Microsoft SaaS-basierte Hybridszenarien für Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
Für jede Schicht der Architektur:
  
- Apps und Szenarien
    
    Es gibt eine Vielzahl von SaaS-basierten Hybridszenarien, in denen es sich um Office-Serverprodukte und deren Office 365-Gegenstücke dreht:
    
  - Exchange-Server in Kombination mit Exchange Online (Exchange Server-Hybridbereitstellung)
    
  - Skype for Business Server in Kombination mit Skype for Business Online und den neuen Cloud-PBX- und Cloud Connector Edition-Szenarien
    
  - SharePoint Server 2016 oder SharePoint Server 2013 in Kombination mit SharePoint Online (mehrere Szenarien)
    
    Es gibt auch Exchange Online mit lokaler Skype for Business Server-Bereitstellung, ein produktübergreifendes Hybridszenario.
    
- Identität
    
    Kann Verzeichnissynchronisierung mit lokaler Windows Server AD-Umgebung enthalten. Alternativ können Sie Azure AD für einen Verbund mit einem Drittanbieter-Identitätsdrittanbieter konfigurieren.
    
- Netzwerk
    
    Besteht aus Ihrem vorhandenen Internetzugang oder einer ExpressRoute-Verbindung mit Microsoft-Peering für Office 365 oder Dynamics 365.
    
- Lokal
    
    Kann aus vorhandenen Servern für Exchange, SharePoint und Skype for Business bestehen, die auf ihre neuesten Versionen aktualisiert sein sollten. Sie können diese dann für Hybridszenarien mit ihren Office 365-Gegenstücken kombinieren.
    
Richten Sie Ihre eigene [Office 365 Dev/Test-Umgebung](office-365-dev-test-environment.md).
  
## <a name="skype-for-business-2015-hybrid"></a>Skype for Business 2015 Hybrid

Skype für Business 2015 hybride können Sie eine vorhandene lokale Bereitstellung mit Skype für Business Online zu kombinieren. Einige Benutzer werden lokal und einige Benutzer online verwaltet werden, aber die Benutzer freigeben Session Initiation Protocol (SIP) derselben Domäne, z. B. "contoso.com". Diese hybridkonfiguration können Sie lokal Migration zu Office 365 im Laufe der Zeit im Terminplan. Skype für Business 2015 kann auch mit Exchange Online integriert werden.
  
**Abbildung 2: Skype Business 2015 hybridkonfiguration**

![Die Skype for Business 2015-Hybridkonfiguration](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
Abbildung 2 zeigt die Skype hybridkonfiguration Business 2015, bestehend aus einer lokalen Skype für Business 2015 Front-End-Pool und Edge Server zum Kommunizieren mit Skype für Business Online in Office 365.
  
Weitere Informationen finden Sie unter:
  
- [Planen von hybridkonnektivität zwischen Skype für Business Server und Skype für Business Online](https://technet.microsoft.com/library/jj205403.aspx)
    
- [Unterstützte hybridkonfigurationen für Skype für Business Server 2015](https://technet.microsoft.com/library/jj945633.aspx)
    
- [Skype für hybride Business](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Cloud-PBX mit Skype for Business Server

Cloud-PBX mit Skype for Business Server ermöglicht es Ihnen, eine vorhandene lokale Skype for Business Server-Bereitstellung in eine Topologie mit lokaler PSTN-Konnektivität (Public Switched Telephone Network) zu überführen.  
  
**Abbildung 3: Cloud Nebenstellenanlage mit Skype für Business Server**

![Cloud-PBX mit Skype for Business Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
Abbildung 3 zeigt die Cloud-Nebenstellenanlage mit Skype für Business Server-Konfiguration, bestehend aus einem lokalen, vorhandene PBX oder Telekommunikation Gateway, einen Skype für Business Server und dem PSTN der Microsoft-Cloud-Nebenstellenanlage in Office 365, einschließlich Skype für Unternehmen verbunden Online.
  
Benutzer im Unternehmen, die in der Cloud gehostet werden, können private PBX-Dienste (Private Branch Exchange, Nebenstellenanlage) aus der Microsoft-Cloud empfangen, wozu Signalisierung und Voicemail gehören, aber Festnetzanbindung (Freizeichen) wird über Enterprise-VoIP aus Ihrer lokalen Skype for Business Server-Bereitstellung bereitgestellt.
  
Dies ist ein gutes Beispiel für eine Hybridkonfiguration, die Ihnen eine schrittweise Migration zu einem cloudbasierten Dienst ermöglicht. Sie können die Sprachfunktionen der Benutzer beibehalten, wenn Sie diese zu Skype for Business Online verschieben. Sie können Ihre Benutzer in Ihrem eigenen Tempo verschieben. Die Sprachfunktionen werden unabhängig davon, wo die Benutzer gehostet sind, beibhelaten.  
  
Weitere Informationen finden Sie unter [Planen der hybridkonnektivität zwischen Skype für Business Server und Skype für Business Online oder Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).
  
Wenn Sie noch keine Lync Server- oder Skype for Business Server-Bereitstellung haben, können Sie Skype for Business Cloud Connector Edition verwenden. Dies ist eine Gruppe von konfektionierten virtuellen Computern, in denen lokale Festnetzanbindung (PSTN-Konnektivität) mit Cloud-PBX implementiert ist.
  
Weitere Informationen finden Sie unter [Planen von Skype für Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).
  
## <a name="sharepoint-hybrid"></a>SharePoint-Hybridlösung

In einer SharePoint-Hybridlösung wird SharePoint Online in Office 365 mit Ihrer lokalen SharePoint-Farm kombiniert, um das Beste aus beiden zu verbinden.
  
**Abbildung 4: Die SharePoint-hybridkonfiguration**

![Die SharePoint-Hybridkonfiguration](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
Abbildung 4 zeigt die SharePoint-hybridkonfiguration, bestehend aus einer lokalen SharePoint-Farm zum Kommunizieren mit SharePoint Online in Office 365.
  
SharePoint-Hybridszenarien:
  
- [Hybrid-OneDrive für Unternehmen](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [Hybrid-Teamwebsites](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [Hybride Extranet B2B](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [Hybridsuche](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [Hybrid-Profile](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [Hybride Personenauswahl](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    Es ist einfach, Hybridszenarien mit den Assistenten zu aktivieren, mit denen die Hybridkonfiguration automatisiert wird und die aus dem SharePoint Online Admin Center in Office 365 verfügbar sind.
    
- [Startprogramm für Extensible Hybrid-app](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    Ermöglicht es Benutzern, Office 365-Video- und Delve-Apps und -Oberflächen auf den Seiten ihrer lokalen SharePoint-Farm anzuzeigen und zu verwenden.
    
Diese SharePoint-Hybridszenarien sind mit Ausnahme von „Das erweiterbare Hybrid-Startprogramm für Apps“ alle sowohl für SharePoint 2016- als auch für SharePoint 2013-Benutzer verfügbar.
  
Weitere Informationen finden Sie unter [SharePoint-Hybridlösung](http://hybrid.office.com/sharepoint/).
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 Hybrid

Mit Exchange Server 2016 Hybrid können Sie von den Vorteilen von Exchange Online in Office 365 für Onlinebenutzer profitieren, während lokale Benutzer weiterhin die vorhandene Exchange Server-Infrastruktur nutzen.  
  
**Abbildung 5: Die hybridkonfiguration Exchange 2016**

![Die Exchange 2016-Hybridkonfiguration](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
Abbildung 5 zeigt die Exchange-2016 hybridkonfiguration bestehend aus lokalen Exchange-Postfachserver mit Exchange Online Protection und Postfächer in Office 365 kommunizieren.
  
Einige Benutzer haben einen lokalen E-Mail-Server, und einige Benutzer verwenden Exchange Online, aber für alle Benutzer wird derselbe E-Mail-Adressraum genutzt.  
  
Diese Hybridkonfiguration ermöglicht Folgendes:
  
- Nutzt Ihre vorhandene Exchange Server-Infrastruktur, während Sie zu Exchange Online über einen Zeitraum, nach Ihrem Zeitplan Migration.
    
- Sie können Remotestandorte unterstützen, ohne in eine Zweigstelleninfrastruktur zu investieren.
    
- Sie können aus dem Internet eingehende E-Mails über Exchange Online Protection in Office 365 weiterleiten.
    
- Es können die Anforderungen von multinationalen Unternehmen erfüllt werden, die Filialen haben, für die lokales Speichern von Daten erforderlich ist.
    
Sie können diese Hybridkonfiguration auch mit anderen Microsoft Office 365-Anwendungen kombinieren, einschließlich Skype for Business Online und SharePoint Online.
  
Weitere Informationen finden Sie unter [Hybridbereitstellungen in Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) und [Exchange Hybrid](http://hybrid.office.com/exchange/).
  
## <a name="see-also"></a>Weitere Artikel

[Microsoft Hybrid Cloud für Enterprise-Architekten](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)



