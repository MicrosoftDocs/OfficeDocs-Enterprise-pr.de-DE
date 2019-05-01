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
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487296"
---
# <a name="designing-networking-for-microsoft-saas"></a>Entwerfen von Netzwerken für Microsoft-SaaS

 **Zusammenfassung:** Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft SaaS-Dienste, einschließlich Office 365, Microsoft Intune und Dynamics 365, optimieren.
  
Die Optimierung Ihres Microsoft SaaS-Services erfordert die Konfiguration von internen und Edge-Geräten, um die verschiedenen Traffickategorien für Microsoft SaaS-Services zu ermitteln.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste

Befolgen Sie diese Schritte, um Ihr Netzwerk für Microsoft SaaS-Dienste zu optimieren:
  
1. Durchlaufen Sie die **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud Services** in [Gemeinsame Elemente der Microsoft-Cloudkonnektivität](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Fügen Sie jeder ihrer Niederlassung eine Internet Verbindung hinzu.
    
3. Stellen Sie sicher, dass die ISPs für alle Internet Verbindungen einen DNS-Server mit einer lokalen IP-Adresse verwenden.
    
4. Untersuchen Sie Ihre Netzwerk-Haarnadeln, Zwischenziele wie Cloud-basierte Sicherheitsdienste, und beseitigen Sie Sie nach Möglichkeit.
    
5. Konfigurieren Sie Ihre edgegeräte, um die Verarbeitung für die Kategorien optimieren und zulassen von Microsoft SaaS-Datenverkehr zu umgehen.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Optimieren des Datenverkehrs zu Microsoft SaaS-Diensten    

Es gibt drei Kategorien von Microsoft SaaS-Datenverkehr:

- Optimieren

  Erforderlich für die Anbindung an jeden Microsoft SaaS-Dienst und stellt mehr als 75% der Microsoft SaaS-Bandbreite, Verbindungen und Datenmenge dar.

- Zulassen

  Für die Konnektivität mit bestimmten Microsoft SaaS-Diensten und-Features erforderlich, Sie sind jedoch nicht so sensibel für die Netzwerkleistung und Wartezeit wie die in der Kategorie optimieren.

- Standard

  Stellen Sie Microsoft SaaS-Dienste und Abhängigkeiten dar, die keine Optimierung erfordern. Sie können den standardmäßigen Kategorien Datenverkehr wie normale Internet Datenverkehr behandeln.


**Abbildung 1: Empfohlene Konfiguration für Microsoft SaaS-Datenverkehr für alle Büros**

![Abbildung 1: Empfohlene Konfiguration für Microsoft SaaS-Datenverkehr für alle Büros](media/Network-Poster/SaaS1.png)

Abbildung 1 zeigt die empfohlene Konfiguration aller Büros, einschließlich Zweigstellen und regionalen oder zentralen, in denen:

- **Standard** Kategorie und allgemeiner Internet Datenverkehr werden an Büros mit Proxyservern und anderen edgegeräte weitergeleitet, um den Schutz vor internetbasierten Sicherheitsrisiken zu gewährleisten.
- **Optimieren** und **zulassen** der Kategorie-Datenverkehr wird direkt an den Rand des Microsoft-Netzwerk-Front-Ends in der Nähe des Büros weitergeleitet, das den Verbindungsbenutzer enthält, wobei Proxy Server und andere edgegeräte umgangen werden.

Software definierte WAN-Geräte (Wide Area Network) in Zweigstellen trennen den Datenverkehr so, dass: 

- Die **Standard** Kategorie und der allgemeine Internet Datenverkehr gehen über das WAN-Backbone an eine zentrale oder regionale Niederlassung. 
- **Optimieren** und **zulassen** der Kategorie-Datenverkehr wird an den ISP gesendet, der die lokale Internet Verbindung bereitstellt.
  
Weitere Informationen finden Sie unter:
  
- [Prinzipien der Netzwerkkonnektivität](https://aka.ms/expressrouteoffice365)

- [Netzwerk- und Migrationsplanung für Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Nächster Schritt

[Entwerfen von Netzwerken für Microsoft-PaaS](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Siehe auch

[Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

