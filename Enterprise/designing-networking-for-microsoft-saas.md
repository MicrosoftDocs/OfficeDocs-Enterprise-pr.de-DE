---
title: Entwerfen von Netzwerken für Microsoft-SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Zusammenfassung: Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872266"
---
# <a name="designing-networking-for-microsoft-saas"></a>Entwerfen von Netzwerken für Microsoft-SaaS

 **Zusammenfassung:** Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren.
  
Optimieren Ihr Netzwerk für Microsoft SaaS Services erfordert die Konfiguration der internen und Edge-Geräte die verschiedenen Arten von Datenverkehr an Microsoft SaaS Services weitergeleitet.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste

Befolgen Sie diese Schritte, um Ihr Netzwerk für Microsoft SaaS-Dienste zu optimieren:
  
1. Durchlaufen Sie die **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud Services** in [Gemeinsame Elemente der Microsoft-Cloudkonnektivität](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Fügen Sie eine Internet-Verbindung an alle Ihre Büros.
    
3. Stellen Sie sicher, dass der Internetdienstanbieter für alle Internet-Verbindungen mit einem lokalen IP-Adresse einen DNS-Server verwenden.
    
4. Untersuchen Sie Ihr Netzwerk Hairpins, temporären Zieladressen wie cloudbasierten Sicherheitsdienste und beseitigen Sie, sofern möglich.
    
5. Konfigurieren der Edge-Geräten umgehen Verarbeitung für das Optimieren und Kategorien von Microsoft SaaS Datenverkehr zulassen.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Optimieren der Datenverkehr zu Microsofts SaaS-Diensten    

Es gibt drei Kategorien von Microsoft SaaS Datenverkehr:

- Optimieren

  Für die Verbindung mit jedem Microsoft SaaS Service und darstellen über 75 % der Microsoft SaaS Bandbreite, Verbindungen und Menge der Daten erforderlich.

- Zulassen

  Erforderlich für Verbindung mit bestimmten Microsoft SaaS Dienste und features sind jedoch nicht als vertraulich Leistung des Netzwerks und Wartezeit, die in der Kategorie optimieren.

- Standard

  Darstellen Sie SaaS Microsoft Services und Abhängigkeiten, die kein Optimierung erfordern. Sie können die Standardeinstellung Kategorie Datenverkehr wie normale Datenverkehr im Internet behandeln.


**Abbildung 1: Empfohlene Konfiguration für Microsoft SaaS-Datenverkehr für alle Büros**

![Abbildung 1: Empfohlene Konfiguration für Microsoft SaaS-Datenverkehr für alle Büros](media/Network-Poster/SaaS1.png)

Abbildung 1 zeigt die empfohlene Konfiguration von allen Büros, einschließlich Zweigstellen und regionalen oder zentralen Unterhaltungen in die:

- **Standard** -Kategorie sowie allgemeine Internet-Datenverkehr an Büros, die Proxy-Server und andere Geräte Edge zum Schutz vor Sicherheitsrisiken internetbasierten weitergeleitet wird.
- **Optimieren** und **Zulassen** Kategorie Datenverkehr wird direkt an den Rand des Microsoft Network Front-End Rechtsklicks am nächsten ist, die die enthält verbinden, Proxy-Server und andere Geräte Edge umgehen Büro weitergeleitet.

WAN-Software definiert (SD-WAN) Netzwerkgeräte in Zweigstellen Datenverkehr zu trennen, damit: 

- **Standard** -Kategorie sowie allgemeine Internet-Datenverkehr wird zu einem zentralen / regionalen Office über das WAN-Backbone. 
- **Optimieren** und **Zulassen** Kategorie-Datenverkehr wird an den Internetdienstanbieter, die Internet-Verbindung bereitstellen.
  
Weitere Informationen finden Sie unter:
  
- [Netzwerk-Konnektivität Prinzipien](https://aka.ms/expressrouteoffice365)

- [Netzwerk- und Migrationsplanung für Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Nächster Schritt

[Entwerfen von Netzwerken für Microsoft-PaaS](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Siehe auch

[Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

