---
title: Hybrid Cloud-Szenarien für Microsoft SaaS (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Zusammenfassung: Grundlegendes zur Hybrid-Architektur und Szenarien für Microsofts SaaS-basierte cloud-angeboten (Office 365).'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123412"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Hybrid Cloud-Szenarien für Microsoft-SaaS (Office 365)

 **Zusammenfassung:** Grundlegendes zur Hybrid-Architektur und Szenarien für Microsofts SaaS-basierte cloud-angeboten (Office 365).
  
Kombinieren Sie lokale Bereitstellungen von Exchange, SharePoint oder Skype for Business mit ihren Gegenstücken in Office 365 als Bestandteile einer Cloudmigrations- oder langfristigen Integrationsstrategie.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Architektur für Microsoft SaaS-Hybridszenarien

Abbildung 1 zeigt die Architektur der SaaS-basierten Hybridszenarien von Microsoft für Office 365.
  
**Abbildung 1: Microsoft SaaS-basierte Hybridszenarien für Office 365**

![Microsoft SaaS-basierte Hybridszenarien für Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
Für jede Schicht der Architektur:
  
- Apps und Szenarien
    
    Es gibt eine Vielzahl von SaaS-basierten Hybridszenarien, in denen es sich um Office-Serverprodukte und deren Office 365-Gegenstücke dreht:
    
  - Exchange-Server in Kombination mit Exchange Online (Exchange Server-Hybridbereitstellung)
    
  - Skype for Business Server in Kombination mit Skype for Business Online und den neuen Cloud-PBX- und Cloud Connector Edition-Szenarien
    
  - SharePoint Server 2019, 2016 für SharePoint Server oder SharePoint Server 2013 in Kombination mit SharePoint Online (mehrere Szenarien)
    
    Es gibt auch Exchange Online mit lokaler Skype for Business Server-Bereitstellung, ein produktübergreifendes Hybridszenario.
    
- Identität
    
    Kann Verzeichnissynchronisierung mit lokaler Windows Server AD-Umgebung enthalten. Alternativ können Sie Azure AD für einen Verbund mit einem Drittanbieter-Identitätsdrittanbieter konfigurieren.
    
- Netzwerk
    
    Besteht aus Ihrem vorhandenen Internetzugang oder einer ExpressRoute-Verbindung mit Microsoft-Peering für Office 365 oder Dynamics 365.
    
- Lokal
    
    Kann aus vorhandenen Servern für Exchange, SharePoint und Skype for Business bestehen, die auf ihre neuesten Versionen aktualisiert sein sollten. Sie können diese dann für Hybridszenarien mit ihren Office 365-Gegenstücken kombinieren.
    
Richten Sie Ihre eigene Office 365-Umgebung Test-/, finden Sie unter [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Skype für hybride Business

Skype für hybride Business können Sie eine vorhandene lokale Bereitstellung mit Skype für Business Online zu kombinieren. Einige Benutzer werden lokal und einige Benutzer online verwaltet werden, aber die Benutzer freigeben Session Initiation Protocol (SIP) derselben Domäne, z. B. "contoso.com". Diese hybridkonfiguration können Sie lokal Migration zu Office 365 im Laufe der Zeit im Terminplan. Skype für Unternehmen kann auch mit [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)integriert werden.
  
**Abbildung 2: Skype Business hybridkonfiguration**

![Die Skype Business hybridkonfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
Abbildung 2 zeigt die Skype Business hybridkonfiguration, bestehend aus einer lokalen Skype für Business Front-End-Pool und Edge Server zum Kommunizieren mit Skype für Business Online in Office 365.
  
Weitere Informationen finden Sie unter [Planen von hybridkonnektivität zwischen Skype für Business Server und Skype für Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>Cloud-PBX mit Skype for Business Server

Übergang von einer vorhandenen Skype für Business Server lokale Bereitstellung zu einer Topologie mit lokalen (Public Switched Telephone Network, PSTN) Konnektivität ermöglicht Cloud Nebenstellenanlage mit Skype für Business Server. 
  
**Abbildung 3: Cloud-PBX mit Skype for Business Server**

![Cloud-PBX mit Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
Abbildung 3 zeigt die Cloud-Nebenstellenanlage mit Skype für Business Server-Konfiguration, bestehend aus einem lokalen, vorhandene PBX oder Telekommunikation Gateway, einen Skype für Business Server und dem PSTN der Microsoft-Cloud-Nebenstellenanlage in Office 365, einschließlich Skype für Unternehmen verbunden Online.
  
Benutzer im Unternehmen, die in der Cloud gehostet werden, können private PBX-Dienste (Private Branch Exchange, Nebenstellenanlage) aus der Microsoft-Cloud empfangen, wozu Signalisierung und Voicemail gehören, aber Festnetzanbindung (Freizeichen) wird über Enterprise-VoIP aus Ihrer lokalen Skype for Business Server-Bereitstellung bereitgestellt.
  
Dies ist ein hervorragendes Beispiel eine hybridkonfiguration, die schrittweise Migration mit einem cloudbasierten Dienst ermöglicht. Sie können Ihrer Benutzer Sprachfunktionen beibehalten, wenn Sie beginnen, die sie in Skype für Business Online zu verschieben. Sie können die Benutzer an das Tempo, wissen, dass ihre VoIP-Funktionen Nein weiterhin Fachgebiet zur verschieben, wo sie verwaltet werden. 
  
Weitere Informationen finden Sie unter [Planen von hybridkonnektivität zwischen Skype für Business Server und Skype für Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Wenn Sie noch keine Lync Server- oder Skype for Business Server-Bereitstellung haben, können Sie Skype for Business Cloud Connector Edition verwenden. Dies ist eine Gruppe von konfektionierten virtuellen Computern, in denen lokale Festnetzanbindung (PSTN-Konnektivität) mit Cloud-PBX implementiert ist.
  
Weitere Informationen finden Sie unter [Planen von Skype für Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>SharePoint-Hybridlösung

In einer SharePoint-Hybridlösung wird SharePoint Online in Office 365 mit Ihrer lokalen SharePoint-Farm kombiniert, um das Beste aus beiden zu verbinden.
  
**Abbildung 4: Die SharePoint-Hybridkonfiguration**

![Die SharePoint-Hybridkonfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
Abbildung 4 zeigt die SharePoint-hybridkonfiguration, bestehend aus einer lokalen SharePoint-Farm zum Kommunizieren mit SharePoint Online in Office 365.
  
SharePoint-Hybridszenarien:
  
- [OneDrive for Business-Hybridbereitstellung](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [Hybride Extranet B2B](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Hybridsuche](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Hybridprofile](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Hybride Personenauswahl](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    Es ist einfach, Hybridszenarien mit den Assistenten zu aktivieren, mit denen die Hybridkonfiguration automatisiert wird und die aus dem SharePoint Online Admin Center in Office 365 verfügbar sind.
    
- [Das erweiterbare Hybrid-App-Startfeld](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Ermöglicht es Benutzern, Office 365-Video- und Delve-Apps und -Oberflächen auf den Seiten ihrer lokalen SharePoint-Farm anzuzeigen und zu verwenden.
    
Diese SharePoint-Hybridszenarien sind mit Ausnahme von „Das erweiterbare Hybrid-Startprogramm für Apps“ alle sowohl für SharePoint 2016- als auch für SharePoint 2013-Benutzer verfügbar.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 Hybrid

Mit Exchange Server 2016 Hybrid können Sie von den Vorteilen von Exchange Online in Office 365 für Onlinebenutzer profitieren, während lokale Benutzer weiterhin die vorhandene Exchange Server-Infrastruktur nutzen.  
  
**Abbildung 5: Die Exchange 2016-Hybridkonfiguration**

![Die Exchange 2016-Hybridkonfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
Abbildung 5 zeigt die Exchange-2016 hybridkonfiguration bestehend aus lokalen Exchange-Postfachserver mit Exchange Online Protection und Postfächer in Office 365 kommunizieren.
  
Einige Benutzer haben einen lokalen E-Mail-Server, und einige Benutzer verwenden Exchange Online, aber für alle Benutzer wird derselbe E-Mail-Adressraum genutzt.  
  
Diese Hybridkonfiguration ermöglicht Folgendes:
  
- Sie können Ihre vorhandene Exchange Server-Infrastruktur nutzen, während Sie nach und nach gemäß Ihrem Zeitplan zu Exchange Online migrieren.



    
- Sie können Remotestandorte unterstützen, ohne in eine Zweigstelleninfrastruktur zu investieren.
    
- Sie können aus dem Internet eingehende E-Mails über Exchange Online Protection in Office 365 weiterleiten.
    
- Es können die Anforderungen von multinationalen Unternehmen erfüllt werden, die Filialen haben, für die lokales Speichern von Daten erforderlich ist.
    
Sie können diese Hybridkonfiguration auch mit anderen Microsoft Office 365-Anwendungen kombinieren, einschließlich Skype for Business Online und SharePoint Online.
  
Weitere Informationen finden Sie unter [Hybridbereitstellungen in Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>Siehe auch

[Microsoft Hybrid Cloud für Enterprise-Architekten](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

