---
title: Netzwerkkonnektivität zu Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 ist darauf ausgelegt, damit Kunden auf der ganzen Welt Verbindung mit dem Webdienst mit dem Internet verbunden. Weiterentwicklung des Diensts sind die Sicherheit, Leistung und Zuverlässigkeit von Office 365 basierend auf Kunden über das Internet herstellen eine Verbindung mit dem Dienst verbessert.
ms.openlocfilehash: b72b0a4584542e4c8673c7cf009c66aa97c6b81c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540964"
---
# <a name="network-connectivity-to-office-365"></a>Netzwerkkonnektivität zu Office 365

Office 365 ist darauf ausgelegt, damit Kunden auf der ganzen Welt Verbindung mit dem Webdienst mit dem Internet verbunden. Weiterentwicklung des Diensts sind die Sicherheit, Leistung und Zuverlässigkeit von Office 365 basierend auf Kunden über das Internet herstellen eine Verbindung mit dem Dienst verbessert.
  
Planung der Verwendung von Office 365 von Kunden beurteilen ihren vorhandenen und prognostizierten Internet Connectivity Anforderungen als Teil des Bereitstellungsprojekts liegt. Für die Bereitstellung von Enterprise-Klasse ist zuverlässigen und geeigneter Größe Internetkonnektivität Verarbeiten von Office 365-Features und Szenarien eine wichtige Rolle.
  
Testen der Netzwerk können viele verschiedene Personen und Organisationen je nach der Größe und Voreinstellungen ausgeführt werden. Der Netzwerkbereich der Bewertung kann ebenfalls variieren, je nachdem, wo Sie sich am im Bereitstellungsprozess befinden. Um Ihnen dabei helfen, ein besseres Verständnis der was benötigt wird, um eine Bewertung Netzwerk ausführen, haben wir, um die verfügbaren Optionen Verständnis der Leitfaden zur Bewertung Netzwerk erstellt. Diese Bewertung bestimmt Schritte und Ressourcen benötigen, das Bereitstellungsprojekt, damit Sie Office 365 erfolgreich einführen können hinzugefügt werden soll.
  
Eine umfassende Bewertung, wie diese vorgeschriebenen optional die [Skype Operations Framework](https://www.skypeoperationsframework.com/) mögliche Lösungen Netzwerke Design Herausforderungen zusammen mit Implementierungsdetails bereitstellt. Die meisten Netzwerk-Bewertungen werden angegeben, dass die Netzwerkkonnektivität zu Office 365 mit [minor Konfiguration oder entwurfsänderungen](https://aka.ms/manageo365endpoints) mit dem vorhandenen Netzwerk und Internet Ausgang Infrastruktur untergebracht werden kann.

Einige Bewertung werden angegeben, dass die Netzwerkkonnektivität zu Office 365 zusätzliche Investitionen in Netzwerkkomponenten erforderlich ist. Investitionen in WAN-Bandbreite oder optimierte routing-Infrastruktur zur Unterstützung von Internet-Konnektivität mit Office 365. Eine Bewertung wird gelegentlich hingewiesen, dass die Netzwerkkonnektivität zu Office 365 von Vorschriften oder Leistung Anforderungen für Szenarien wie etwa [Skype für Business Online Medienqualität](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)beeinflusst wird. Diese zusätzlichen Anforderungen können zu Investitionen in Internet Connectivity-Infrastruktur, routing Optimierung und spezialisierte direkte Verbindung führen.
  
> [!NOTE]
> Microsoft geändert, wie die Domäne für das Microsoft Peering routing für Azure ExpressRoute überprüft werden. Ab dem 31. Juli 2017 können alle Azure ExpressRoute Kunden Microsoft Peering direkt von der Azure-Verwaltungskonsole oder über PowerShell aktivieren. Nach der Aktivierung von Microsoft Peering kann kundenspezifischen Routefilter empfangen BGP Route Werbung für Dynamics 365 Kundenprojekt Applications (vormals CRM Online) erstellen. Kunden, die Azure ExpressRoute für Office 365 benötigen Überprüfen von Microsoft Routefilter für Office 365 erstellt werden können. Wenden Sie sich an Ihrem Microsoft Account Team um kennen zu lernen, wie Sie eine Überprüfung für die Aktivierung von Office 365 ExpressRoute anfordern. Nicht autorisierte Abonnements für Office 365 Routefilter erstellen möchten, erhalten eine [Fehlermeldung angezeigt](https://support.microsoft.com/kb/3181709).
  
Wichtige zu berücksichtigende Punkte bei der Planung Ihrer Netzwerk zur Bewertung für Office 365
  
- Office 365 ist eine sichere, zuverlässige und hohe Leistung-Dienst, der über das öffentliche Internet ausgeführt wird. Wir weiterhin investieren, um diese Aspekte des Dienstes zu verbessern. Alle Office 365-Dienste werden über Internetkonnektivität verfügbar.

- Wir werden ständig Optimieren der wichtigsten Aspekte von Office 365 wie Verfügbarkeit, global zu erreichen, und Leistung für Internet Connectivity basiert. Viele Office 365-Diensten nutzen beispielsweise eine erweiterbare Menge von edgeknoten mit Internetzugriff. Diese edgenetzwerk bietet die beste Nähe und Leistung auf Verbindungen, die über das Internet stammen.

- Wenn mithilfe von Office 365 für eines der enthalten Diensten wie etwa Skype für Business Sprach-, Video- oder Meeting Onlinefunktionen in Erwägung ziehen, müssen Kunden führen Sie eine Bewertung End-to-End-Netzwerk und unsere Skype Operations Framework-Anforderungen erfüllen. Diese Kunden müssen verschiedene Optionen, um bestimmte Anforderungen für Cloud-Diensten, einschließlich ExpressRoute erfüllen.

Haben Sie eine Aufstellung der Fallstudie Microsofts [Optimieren der Leistung des Netzwerks für Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Wenn Sie Office 365 evaluieren Ihren und nicht stellt sicher, wo Sie Ihr Netzwerk Assessment beginnen oder Netzwerkdesign gefunden haben, benötigen Sie Unterstützung, um zu vermeiden, wenden Sie sich mit Ihrem Microsoft-Konto-Team Arbeit.
  
Lesen Sie auch die [Office 365 Network Connectivity Prinzipien](https://aka.ms/o365networkingprinciples) , um die Konnektivität Prinzipien für sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen. In diesem Artikel helfen Ihnen das Verständnis der neuesten Anleitung zur Optimierung von Office 365-Netzwerkkonnektivität sicher.
  
Hier ist ein kurzer Link zurückkehren können: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Office 365 Netzwerk- und Optimieren der Leistung](network-planning-and-performance.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
  
[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
  
[Verwenden von BGP Communitys in ExpressRoute für Office 365-Bereitstellungsszenarios (Preview)](bgp-communities-in-expressroute.md)
  
[Medienqualität und Konnektivität Leistung des Netzwerks in Skype für Unternehmen Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 Network Connectivity Prinzipien](https://aka.ms/o365networkingprinciples)
