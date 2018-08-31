---
title: Abonnements, Lizenzen und Benutzerkonten für die Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 'Zusammenfassung: Verstehen der Struktur der Contoso Cloud-Abonnements, Lizenzen, Benutzerkonten und Mandanten.'
ms.openlocfilehash: cd196e0800f6a39973f4c5c82001ed3e9c330fee
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915510"
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>Abonnements, Lizenzen und Benutzerkonten für die Contoso Corporation

 **Zusammenfassung:** Verstehen der Struktur der Contoso Cloud-Abonnements, Lizenzen, Benutzerkonten und Mandanten.
  
Um eine durchgängige Verwendung von Identitäten und Abrechnung für alle Cloudangebote anzubieten, stellt Microsoft eine Hierarchie aus Organisation/Abonnements/Lizenzen/Benutzerkonten bereit.

  
- Organisation
    
    Die Geschäftseinheit, die Microsoft-Cloudangebote verwendet und üblicherweise durch einen öffentlichen DNS-Domänennamen identifiziert wird, z. B. „contoso.com“.

    
- Abonnements
    
    Für Microsoft SaaS cloud-angeboten (Office 365, Intune/zur Abstimmung und Dynamics 365), ist ein Abonnement ein bestimmtes Produkt und eine erworbenen Reihe von Benutzerlizenzen. Azure ermöglicht ein Abonnement für die Abrechnung des verbrauchten Clouddiensten für die Organisation.
    
- Lizenzen
    
    SaaS Microsoft Cloud-angeboten ermöglicht eine Lizenz ein bestimmtes Benutzerkonto Cloud-Dienste verwenden. Für Azure werden Softwarelizenzen erstellt in Preisen, aber in einigen Fällen, die müssen Sie zusätzliche Software-Lizenzen erwerben.
    
- Benutzerkonten
    
    Benutzerkonten werden in einem Azure AD-Mandanten gespeichert und können aus einem lokalen Identitätsanbieter, z. B. Windows Server Active Directory, synchronisiert werden.
    
## <a name="contosos-structure"></a>Contoso Struktur

Contoso hat die folgende Struktur für die Organisation und ihre Abonnements, Lizenzen, Konten und Mandanten bestimmt:
  
**Abbildung 1: Organisation, Abonnements, Lizenzen, Benutzerkonten und Mandanten von Contoso**

![Organisation, Abonnements, Lizenzen, Benutzerkonten und Mandanten von Contoso](media/Contoso-Poster/Subscriptions.png)
  
Abbildung 1 zeigt, wie die Contoso-Organisation mehrere Abonnements umfasst und an einen allgemeinen Azure AD-Mandanten gebunden ist, der die aus der Windows Server Active Directory-Gesamtstruktur "contoso.com" synchronisierten Benutzerkonten enthält.
  
- **Organisation** Der Contoso Corporation wird durch seine öffentlichen Domäne namens "contoso.com" identifiziert.
    
  - **Abonnements und Lizenzen** Der Contoso Corporation wird Folgendes verwenden:
    
  - Das Office 365 Enterprise E3 Produkt mit 5.000 Lizenzen
    
  - Das Produkt Office 365 Enterprise E5 mit 200 Lizenzen
    
  - Das Produkt zur Abstimmung mit 5.000 Lizenzen
    
  - Das Produkt Dynamics 365 mit 100 Lizenzen

    
  - Mehrere Azure-Abonnements auf Basis von Regionen
    
  - **Benutzerkonten** Ein allgemeiner Azure AD-Mandanten enthält die Liste der Benutzerkonten und Gruppen verwendet von allen Contoso Abonnements, mit Ausnahme von Test-/Azure-Abonnements.
    
Für Contoso-Mandanten:
  
- Für SaaS-Cloudangebote ist der Mandant der regionale Standort, an dem sich die Server befinden, von denen Clouddienste bereitgestellt werden. Contoso hat entschieden, dass seine Office 365-, EMS- und Dynamics-365-Mandanten in der Region Europa gehostet werden sollen. 
    
- Azure PaaS-Diensten und apps und IaaS IT Arbeitslasten können Mandanten in Azure-Rechenzentrum auf der ganzen Welt haben. Ein Azure AD-Mandanten ist eine bestimmte Instanz von Azure Active Directory-Konten und Gruppen enthält.
    
- Der allgemeine Azure AD-Mandanten, der die synchronisierten Konten für die Contoso Windows Server Active Directory-Gesamtstruktur enthält bietet IDaaS Cloudlösungen von Microsoft.
    
Weitere Informationen finden Sie unter [Abonnements, Lizenzen, Konten, und Mandanten für Microsoft Cloud-angeboten](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).
  
## <a name="contosos-azure-subscriptions"></a>Contoso Azure-Abonnements

Abbildung 2 zeigt den hierarchischen Entwurf der Azure-Abonnements von Contoso 



  
**Abbildung 2: Struktur für Azure-Abonnements von Contoso**

![Struktur für Azure-Abonnements von Contoso](media/Contoso-Poster/Subscriptions-Nested.png)
  
- Contoso nimmt die oberste Position ein, basierend auf seinem Enterprise Agreement mit Microsoft.
    
- Es gibt eine Gruppe von Konten, die unterschiedlichen Regionen der Contoso Corporation auf der ganzen Welt basierend auf den Domänen der Contoso Windows Server Active Directory-Gesamtstruktur entspricht.
    
- In den einzelnen Bereichen müssen Sie einen oder mehrere Abonnements basierend auf den Bereich Entwicklung, testen und Produktion Erfordernissen vorhanden sind.
    
Jedes Azure-Abonnement kann einem einzelnen Azure AD-Mandanten zugeordnet werden, der Benutzerkonten und Gruppen für die Authentifizierung und Autorisierung bei Azure-Diensten enthält.
 Für Produktionsabonnements wird der allgemeine Contoso Azure AD-Mandant verwendet.
  
## <a name="see-also"></a>Siehe auch

[Contoso in der Microsoft-Cloud](contoso-in-the-microsoft-cloud.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)




