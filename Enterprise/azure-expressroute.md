---
title: Azure ExpressRoute für Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Hier erfahren Sie, wie Azure ExpressRoute mit Office 365 verwendet wird und wie Sie die Netzwerk-Implementierung Projektplan, die ausgeführt werden müssen, wenn Sie für die Verwendung mit Office 365 Azure ExpressRoute bereitstellen.
ms.openlocfilehash: 5a82576b541e27c70bca490ff8dfe887ee879c83
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540758"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute für Office 365

Hier erfahren Sie, wie Azure ExpressRoute mit Office 365 verwendet wird und wie Sie die Netzwerk-Implementierung Projektplan, die ausgeführt werden müssen, wenn Sie für die Verwendung mit Office 365 Azure ExpressRoute bereitstellen. Infrastruktur und Plattform in Azure ausgeführten Dienste werden häufig durch die Adressierung Netzwerkaspekte Architektur und Leistung profitieren. Es wird ExpressRoute für Azure in diesen Fällen empfohlen. Software-as-Dienstangebote informieren, wie Office 365 und Dynamics 365, um sichere und zuverlässige über das Internet zugegriffen werden erstellt wurden. Entsprechend sollten nur ExpressRoute für diese Anwendungen in bestimmten Szenarien. Sie können über Internet-Leistung und Sicherheit, und wenn Sie im Artikel [zu Office 365 Netzwerkkonnektivität](network-connectivity.md)Azure ExpressRoute für Office 365 sollten lesen.

> [!NOTE]
> Starten der 31. Juli 2017, können Sie Microsoft Peering direkt aus der Azure-Verwaltungskonsole oder mithilfe von PowerShell aktivieren. Nachdem Microsoft Peering aktiviert haben, können Sie die Routefilter an, um bestimmte BGP Route ankündigen empfangen erstellen. Sie benötigen die Berechtigung zum Erstellen von Filtern für Office 365 und können Dynamics 365 Kundenprojekt Applications (vormals CRM Online) Filter können Sie jederzeit erstellen. Sprechen Sie mit Ihrem Microsoft Account Team über den Prozess, der Autorisierung zum Erstellen von Filtern für Office 365-Route zu erhalten. Nicht autorisierter Abonnements für Office 365 Routefilter erstellen möchten erhalten eine [Fehlermeldung](https://support.microsoft.com/kb/3181709)

Sie können nun eine direkte Netzwerkverbindung zu Office 365 für den ausgewählten Netzwerkverkehr für Office 365 hinzufügen. Azure ExpressRoute bietet eine direkte Verbindung, vorhersehbare Leistung und mit einer Betriebszeit von 99,95 % SLA für die Microsoft-Netzwerkkomponenten kommt. Sie können weiterhin eine Internet-Verbindung für Dienste erforderlich, die über Azure ExpressRoute unterstützt werden.

## <a name="planning-azure-expressroute-for-office-365"></a>Planen von Azure ExpressRoute für Office 365

Zusätzlich zum Internet Connectivity können Sie eine Teilmenge der Office 365 Datenverkehr über eine direkte Verbindung weitergeleitet werden, die Vorhersagbarkeit und eine 99,95 % Betriebszeit Vereinbarung zum SERVICELEVEL für die Microsoft-Netzwerkkomponenten bietet. Azure ExpressRoute bietet diese dedizierten Netzwerkverbindung zu Office 365 und anderen Microsoft-Cloud-Diensten.

Unabhängig davon, ob Sie eine vorhandene MPLS WAN verfügen kann Ihre Netzwerkarchitektur in drei verschiedene Arten ExpressRoute hinzugefügt werden. über einen unterstützten Cloud Exchange Co-Location Anbieter einen Ethernet-Point-Verbindung Provider aus, oder über ein MPLS-Verbindung-Anbieter. Sehen Sie, welche [Anbieter in Ihrer Region verfügbar sind](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Die direkte Verbindung ExpressRoute aktivieren auf die Anwendung in beschriebenen [Was Office 365-Diensten sind enthalten?](azure-expressroute.md#BKMK_WhatDoIGet) unten. Netzwerkverkehr für andere Anwendungen und Dienste werden weiterhin im Internet zu durchlaufen.

Berücksichtigen Sie folgende high Level Netzplandiagramm, das Office 365-Kunde einen normalerweise eine Verbindung mit Microsoft Rechenzentren über das Internet für den Zugriff auf alle Microsoft-Programme wie Office 365, Windows Update und TechNet angezeigt wird. Kunden verwenden einen ähnliche Netzwerkpfad, unabhängig davon, ob sie von einem lokalen Netzwerk oder aus einem unabhängigen Internetzugang verbinden.

![Office 365-Netzwerkkonnektivität](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Betrachten Sie nun das aktualisierte Diagramm einen Office 365-Kunden, der im Internet und die ExpressRoute wird verwendet stellt, um zu Office 365 herzustellen. Beachten Sie, dass einige Verbindungen wie öffentliche DNS und Content Delivery Network Knoten weiterhin die Verbindung mit dem öffentlichen Internet erforderlich. Beachten Sie auch die Kunden-Benutzer, die nicht in ihre ExpressRoute verbundenen Building eine Verbindung herstellen über das Internet befinden.

![Office 365-Konnektivität mit ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Möchten Sie noch weitere Informationen? Hier erfahren Sie, wie [Verwalten des Netzwerkverkehrs mit Azure ExpressRoute für Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) und erfahren Sie mehr zum [Konfigurieren von Azure ExpressRoute für Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). Wir haben auch eine 10 Teil [Azure ExpressRoute für Office 365-Schulung](https://channel9.msdn.com/series/aer) Reihe auf Channel 9, unterstützen die Konzepte mehr sorgfältig erläutern aufgezeichnet.

([Azure ExpressRoute für Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>Welche Office 365-Diensten sind enthalten?
<a name="BKMK_WhatDoIGet"> </a>

Die folgende Tabelle enthält die Office 365-Dienste, die über ExpressRoute unterstützt werden. Überprüfen Sie den [Office 365-Endpunkten Artikel](https://aka.ms/o365endpoints) , um zu verstehen, welche Netzwerk-Anforderungen für diese Anwendungen Internetkonnektivität erfordern.

|**Applikationen enthalten**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Eingegangen<sup>1</sup> <br/> |
|Skype für Business Online<sup>1</sup> <br/> |
|SharePoint Online –<sup>1</sup> <br/> OneDrive for Business-<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|Portal- und freigegebene<sup>1</sup> <br/> Azure Active Directory-<sup>1</sup> <br/> AAD verbinden<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup> Jede dieser Anwendungen über Internetkonnektivität über ExpressRoute nicht unterstützt, finden Sie weitere Informationen im [Office 365-Endpunkten Artikel](https://aka.ms/o365endpoints) .

Die Dienste, die nicht mit ExpressRoute für Office 365 integriert werden sind Downloads für Office 365 ProPlus-Clients, lokalen Identity Provider-Anmeldung und Office 365 (von 21 Vianet betrieben)-Dienst in China.

([Azure ExpressRoute für Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>Implementieren von ExpressRoute für Office 365

Implementieren von ExpressRoute erfordert die Einbeziehung der Netzwerk- und Besitzer und erfordert, dass erfordert sorgfältige Planung, um zu bestimmen, die neuen [routing Netzwerkarchitektur](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandbreitenanforderungen, sich Sicherheit kann, hohen Verfügbarkeit implementiert, Und so weiter. Um ExpressRoute zu implementieren, müssen Sie Folgendes ausführen:

1. Verstehen Sie die Notwendigkeit, die bei der Planung zu Office 365 Connectivity ExpressRoute erfüllt. Verstehen, welche Anwendungen im Internet oder ExpressRoute verwendet werden soll und Ihre Netzwerkkapazität vollständig planen, Sicherheit und hohe Verfügbarkeit muss im Kontext der Verwendung von Internet- und ExpressRoute für Office 365-Datenverkehr.

2. Bestimmen der Ausgang und Peers Speicherorte für Internet- und ExpressRoute Datenverkehr<sup>1</sup>.

3. Legen Sie die Kapazität im Internet und ExpressRoute Verbindungen erforderlich.

4. Verfügen Sie einen Plan für die Implementierung von Sicherheit und andere Umkreisnetzwerk Steuerelemente<sup>1</sup>.

5. Haben Sie ein gültiges Microsoft Azure-Konto, um ExpressRoute zu abonnieren.

6. Wählen Sie ein Connectivity-Modell und ein [Anbieter genehmigt](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Denken Sie daran, Kunden können mehrere Connectivity-Modelle auswählen oder Partner und der Partner muss nicht dieselbe sein wie den vorhandenen Netzwerkanbieter.

7. Umleiten von Datenverkehr an ExpressRoute vor der Bereitstellung zu überprüfen.

8. Optional können Sie [QoS zu implementieren](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) und Erweiterung von regionalen auswerten.

<sup>1</sup> Unter Leistungsgesichtspunkten wichtig. Hier Entscheidungen können Wartezeit, für die Anwendungen wie Skype für Unternehmen wichtig ist, erheblich beeinträchtigen.

Verwenden Sie für Weitere Verweise unsere [routing-Handbuch](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) zusätzlich zu der [ExpressRoute-Dokumentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).

Um ExpressRoute für Office 365 kaufen, müssen Sie einen oder mehrere [Anbieter genehmigt](https://azure.microsoft.com/documentation/articles/expressroute-locations/) , so stellen Sie die gewünschte Anzahl und Größe Circuits mit einem ExpressRoute Premium-Abonnement bereit entwickelt. Es sind keine zusätzlichen Lizenzen von Office 365 kaufen.

Nachfolgend finden Sie ein kurzer Link, zurückkehren verwendet werden können:[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

Bereit zu Anmeldung für [ExpressRoute für Office 365](https://aka.ms/ert)?

([Azure ExpressRoute für Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>Verwandte Themen
<a name="BKMK_End"> </a>

[Netzwerkkonnektivität zu Office 365](network-connectivity.md)

[Verwalten von ExpressRoute für Office 365-Diensten](managing-expressroute-for-connectivity.md)

[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)

[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)

[Implementieren von ExpressRoute für Office 365](implementing-expressroute.md)

[Verwenden von BGP Communitys in ExpressRoute für Office 365-Bereitstellungsszenarios (Preview)](bgp-communities-in-expressroute.md)

[Medienqualität und Konnektivität Leistung des Netzwerks in Skype für Unternehmen Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Office 365 Performance tuning mit Baselines und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)

[Leistungsbezogene Problembehandlung Plan für Office 365](performance-troubleshooting-plan.md)

[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Office 365 Netzwerk- und Optimieren der Leistung](network-planning-and-performance.md)
