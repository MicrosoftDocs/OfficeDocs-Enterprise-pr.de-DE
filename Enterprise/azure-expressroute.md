---
title: Azure ExpressRoute für Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
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
description: Erfahren Sie, wie Azure Express Route mit Office 365 verwendet wird und wie Sie das Netzwerk Implementierungsprojekt planen, das bei der Bereitstellung von Azure Express Route für die Verwendung mit Office 365 erforderlich ist.
ms.openlocfilehash: c8cff4ef85c4383ba04829cf3cf8da3a1bc36715
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490351"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute für Office 365

Erfahren Sie, wie Azure Express Route mit Office 365 verwendet wird und wie Sie das Netzwerk Implementierungsprojekt planen, das bei der Bereitstellung von Azure Express Route für die Verwendung mit Office 365 erforderlich ist. Infrastruktur-und Plattformdienste, die in Azure laufen, profitieren häufig durch die Berücksichtigung der Netzwerkarchitektur und der Leistungsüberlegungen. In diesen Fällen wird Express Route für Azure empfohlen. Software as a Service Offerings wie Office 365 und Dynamics 365 wurden für den sicheren und zuverlässigen Zugriff über das Internet entwickelt. Sie können sich über die Leistung und Sicherheit im Internet informieren und wenn Sie Azure Express Route für Office 365 im Artikel [Netzwerkkonnektivität zu office 365](network-connectivity.md)berücksichtigen.

> [!NOTE]
> Microsoft-Autorisierung ist erforderlich, um Express Route für Office 365 zu verwenden. Microsoft prüft alle Kundenanforderungen und autorisiert Express Route für Office 365-Nutzung, wenn die behördliche Anforderung eines Kunden eine direkte Anbindung vorschreibt. Wenn Sie solche Anforderungen haben, geben Sie den Textauszug und den Weblink zu der von Ihnen interpretierten Verordnung an, um zu sagen, dass im [Express Route für Office 365-Anforderungsformular](https://aka.ms/O365ERReview) eine direkte Verbindung erforderlich ist, um eine Microsoft-Überprüfungen zu beginnen. Nicht autorisierte Abonnements, die versuchen, Routenfilter für Office 365 zu erstellen, erhalten eine [Fehlermeldung](https://support.microsoft.com/kb/3181709). 

Sie können nun eine direkte Netzwerkverbindung zu Office 365 für ausgewählten Office 365-Netzwerkdatenverkehr hinzufügen. Azure Express Route bietet eine direkte Verbindung, eine vorhersagbare Leistung und eine Uptime-SLA von 99,95% für die Microsoft-Netzwerkkomponenten. Für Dienste, die über Azure Express Route nicht unterstützt werden, ist weiterhin eine Internetverbindung erforderlich.

## <a name="planning-azure-expressroute-for-office-365"></a>Planen von Azure Express Route für Office 365

Zusätzlich zur Internetanbindung können Sie eine Teilmenge Ihres Office 365-Netzwerkverkehrs über eine direkte Verbindung weiterleiten, die Vorhersehbarkeit und eine SLA von 99,95% für die Microsoft-Netzwerkkomponenten bietet. Azure Express Route bietet Ihnen diese dedizierte Netzwerkverbindung zu Office 365 und anderen Microsoft Cloud-Diensten.

Unabhängig davon, ob Sie über ein vorhandenes MPLS-WAN verfügen, kann Express Route Ihrer Netzwerkarchitektur auf drei Arten hinzugefügt werden: über einen unterstützten Cloud-Co-Location-Anbieter, einen Ethernet-Punkt-zu-Punkt-Verbindungsanbieter oder einen MPLS-Verbindungsanbieter. Erfahren Sie, welche [Anbieter in Ihrer Region verfügbar sind](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Die direkte Express Route-Verbindung ermöglicht die Verbindung mit den Anwendungen, die in [welchen Office 365-Diensten enthalten sind](azure-expressroute.md#BKMK_WhatDoIGet) . Der Netzwerkdatenverkehr für alle anderen Anwendungen und Dienste wird weiterhin über das Internet durchlaufen.

Betrachten Sie das folgende allgemeine Netzwerkdiagramm, das zeigt, wie ein typischer Office 365-Kunde eine Verbindung zu den Microsoft-Rechenzentren über das Internet für den Zugriff auf alle Microsoft-Anwendungen wie Office 365, Windows Update und TechNet herstellt. Kunden verwenden einen ähnlichen Netzwerkpfad, unabhängig davon, ob die Verbindung von einem lokalen Netzwerk oder von einer unabhängigen Internetverbindung hergestellt wird.

![Office 365-Netzwerkkonnektivität](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Sehen Sie sich das aktualisierte Diagramm an, das einen Office 365-Kunden darstellt, der sowohl das Internet als auch Express Route zum Herstellen einer Verbindung mit Office 365 verwendet. Beachten Sie, dass einige Verbindungen wie öffentliche DNS-und Inhalts BereitstellungsNetzwerk Knoten weiterhin die öffentliche Internetverbindung erfordern. Beachten Sie außerdem, dass die Benutzer des Kunden, die sich nicht in Ihrem Express Route verbundenen Gebäude befinden, über das Internet eine Verbindung herstellen.

![Office 365-Konnektivität mit Express Route](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Sie möchten noch weitere Informationen? Erfahren Sie, wie [Sie Ihren Netzwerkdatenverkehr mit Azure Express Route für office 365 verwalten](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) und wie Sie [Azure express route für Office 365 konfigurieren](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). Wir haben auch eine 10-teilige [Azure Express Route für Office 365-Schulungs](https://channel9.msdn.com/series/aer) Reihe auf Kanal 9 aufgezeichnet, um die Konzepte genauer zu erläutern.

([Azure Express Route für Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>Welche Office 365-Dienste sind enthalten?
<a name="BKMK_WhatDoIGet"> </a>

In der folgenden Tabelle sind die Office 365-Dienste aufgeführt, die über Express Route unterstützt werden. Lesen Sie den [Artikel Office 365 Endpoint](https://aka.ms/o365endpoints) , um zu verstehen, welche Netzwerkanforderungen für diese Anwendungen eine Internetverbindung erfordern.

|**Anwendungen enthalten**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> EinTauchen<sup>1</sup> <br/> |
|Skype for Business Online<sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive für Unternehmen<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|Portal und Shared<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD Connect<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup> Jede dieser Anwendungen verfügt über Express Route, die nicht unterstützt werden, finden Sie im [Artikel Office 365](https://aka.ms/o365endpoints) Endpoints Weitere Informationen.

Die Dienste, die nicht in Express Route für Office 365 enthalten sind, sind Office 365 proPlus-Clientdownloads, lokale Identitätsanbieter-Anmeldung und Office 365 (betrieben von 21 vianet)-Dienst in China.

([Azure Express Route für Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>Implementieren von ExpressRoute für Office 365

Die Implementierung von Express Route erfordert die Einbindung von Netzwerk-und Anwendungsbesitzern und erfordert sorgfältige Planung der neuen [Netzwerkrouting Architektur](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), der Bandbreitenanforderungen, bei denen Sicherheit implementiert wird, hohe Verfügbarkeit, Und so weiter. Zum Implementieren von Express Route müssen Sie Folgendes tun:

1. Vollständiges Verständnis der Anforderungen, die Express Route in Ihrer Office 365-Konnektivitäts Planung erfüllt. Verstehen Sie, welche Anwendungen das Internet oder Express Route verwenden, und planen Sie vollständig Ihre Anforderungen an die Netzwerkkapazität, Sicherheit und hohe Verfügbarkeit im Zusammenhang mit der Verwendung von Internet und Express Route für Office 365-Datenverkehr.

2. Bestimmen Sie die Ausstiegs-und Peering-Speicherorte für Internet-und Express Route-Datenverkehr<sup>1</sup>.

3. Bestimmen Sie die erforderliche Kapazität für die Internet-und Express Route-Verbindungen.

4. Sie haben einen Plan für die Implementierung von Sicherheit und anderen standardmäßigen Perimeter-Steuerelementen<sup>1</sup>.

5. Sie haben ein gültiges Microsoft Azure-Konto zum Abonnieren von Express Route.

6. Wählen Sie ein Verbindungsmodell und einen [genehmigten Anbieter](https://azure.microsoft.com/documentation/articles/expressroute-locations/)aus. Beachten Sie, dass Kunden mehrere Verbindungs Modelle oder Partner auswählen können, und der Partner muss nicht mit dem vorhandenen Netzwerkanbieter identisch sein.

7. ÜberPrüfen der Bereitstellung vor dem lenken des Datenverkehrs an Express Route.

8. Optional: [QoS implementieren](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) und regionale Erweiterung auswerten.

<sup>1</sup> Wichtige Überlegungen zur Leistung. Entscheidungen können sich drastisch auf die Wartezeit auswirken, was für Anwendungen wie Skype for Business von entscheidender Bedeutung ist.

Weitere Referenzen finden Sie neben der [Express Route-Dokumentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)in unserem [Routing-Leitfaden](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) .

Um Express Route für Office 365 zu erwerben, müssen Sie mit einem oder mehreren genehmigten [Anbietern](https://azure.microsoft.com/documentation/articles/expressroute-locations/) zusammenarbeiten, um die gewünschte Anzahl und Größe der Schaltungen mit einem Express Route Premium-Abonnement bereitzustellen. Es gibt keine zusätzlichen Lizenzen, die von Office 365 erworben werden können.

Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

Möchten Sie sich für [Express Route für Office 365](https://aka.ms/ert)anmelden?

([Azure Express Route für Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>Verwandte Themen

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)

[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)

[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)

[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)

[Implementierung von ExpressRoute für Office 365](implementing-expressroute.md)

[Verwenden von BGP-Communities in Express Route für Office 365-Szenarien (Preview)](bgp-communities-in-expressroute.md)

[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)

[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)

[URLs und IP-Adressbereiche von Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)
