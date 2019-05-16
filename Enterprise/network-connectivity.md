---
title: Netzwerkkonnektivität mit Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
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
description: Office 365 wurde entwickelt, um Kunden auf der ganzen Welt das Herstellen einer Verbindung mit dem Dienst über eine Internetverbindung zu ermöglichen. Während sich der Dienst entwickelt, werden die Sicherheit, Leistung und Zuverlässigkeit von Office 365 basierend auf Kunden verbessert, die das Internet verwenden, um eine Verbindung mit dem Dienst herzustellen.
ms.openlocfilehash: 4510cb073c0fde64abc4ee796a55d7ef32662f8c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069871"
---
# <a name="network-connectivity-to-office-365"></a>Netzwerkkonnektivität mit Office 365

Office 365 wurde entwickelt, um Kunden auf der ganzen Welt das Herstellen einer Verbindung mit dem Dienst über eine Internetverbindung zu ermöglichen. Während sich der Dienst entwickelt, werden die Sicherheit, Leistung und Zuverlässigkeit von Office 365 basierend auf Kunden verbessert, die das Internet verwenden, um eine Verbindung mit dem Dienst herzustellen.
  
Kunden, die Office 365 verwenden möchten, sollten im Rahmen des Bereitstellungsprojekts Ihre vorhandenen und prognostizierten Internet Verbindungsanforderungen bewerten. Für die Bereitstellung von Enterprise-Klassen ist eine zuverlässige und entsprechend dimensionierte Internetkonnektivität ein wichtiger Teil der Nutzung von Office 365-Features und-Szenarien.
  
Netzwerk Auswertungen können von vielen verschiedenen Personen und Organisationen abhängig von ihrer Größe und ihren Präferenzen durchgeführt werden. Der Netzwerkbereich der Bewertung kann auch abhängig davon variieren, wo Sie sich in Ihrem Bereitstellungsprozess befinden. Damit Sie besser verstehen, was für die Durchführung einer Netzwerkbewertung erforderlich ist, haben wir einen Leitfaden zur Netzwerkbewertung erstellt, der Ihnen hilft, die Ihnen zur Verfügung stehenden Optionen zu verstehen. Diese Bewertung bestimmt, welche Schritte und Ressourcen dem Bereitstellungsprojekt hinzugefügt werden müssen, damit Sie Office 365 erfolgreich einführen können.
  
Eine umfassende Netzwerkbewertung, wie Sie im [Skype Operations Framework](https://www.skypeoperationsframework.com/) vorgeschrieben ist, bietet mögliche Lösungen für Herausforderungen beim Netzwerk Design sowie Implementierungsdetails. Die meisten Netzwerkbewertungen deuten darauf hin, dass die Netzwerkkonnektivität zu Office 365 mit [geringfügigen Konfigurations-oder Entwurfsänderungen](https://aka.ms/manageo365endpoints) an der vorhandenen Netzwerk-und Internet Ausgangs Infrastruktur untergebracht werden kann.

Einige Bewertungen deuten darauf hin, dass die Netzwerkkonnektivität zu Office 365 zusätzliche Investitionen in Netzwerkkomponenten erfordert. Beispielsweise Investitionen in WAN-Bandbreite oder eine optimierte Routinginfrastruktur zur Unterstützung der Internetkonnektivität mit Office 365. Gelegentlich wird durch eine Bewertung angegeben, dass die Netzwerkkonnektivität zu Office 365 von Regeln oder Leistungsanforderungen für Szenarien wie [Skype for Business Online Media Quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)beeinflusst wird. Diese zusätzlichen Anforderungen können zu Investitionen in die Internet Verbindungsinfrastruktur, Routing Optimierung und spezialisierte direkte Konnektivität führen.
  
> [!NOTE]
> Microsoft-Autorisierung ist erforderlich, um Express Route für Office 365 zu verwenden. Microsoft prüft jede Kundenanfrage und autorisiert nur Express Route für Office 365-Nutzung, wenn die behördliche Anforderung eines Kunden eine direkte Anbindung vorschreibt. Wenn Sie solche Anforderungen haben, geben Sie den Textauszug und den Weblink zu der von Ihnen interpretierten Verordnung an, um zu sagen, dass im [Express Route für Office 365-Anforderungsformular](https://aka.ms/O365ERReview) eine direkte Verbindung erforderlich ist, um eine Microsoft-Überprüfungen zu beginnen. Nicht autorisierte Abonnements, die versuchen, Routenfilter für Office 365 zu erstellen, erhalten eine [Fehlermeldung](https://support.microsoft.com/kb/3181709).
  
Wichtige Punkte bei der Planung Ihrer Netzwerkbewertung für Office 365:
  
- Office 365 ist ein sicherer, zuverlässiger, leistungsstarker Dienst, der über das öffentliche Internet ausgeführt wird. Wir investieren weiterhin, um diese Aspekte des Diensts zu verbessern. Alle Office 365-Dienste sind über Internetkonnektivität verfügbar.

- Wir optimieren ständig die wichtigsten Aspekte von Office 365 wie Verfügbarkeit, globale Reichweite und Leistung für internetbasierte Konnektivität. Beispielsweise nutzen zahlreiche Office 365-Dienste eine wachsende Anzahl von internetseitigen Edge-Knoten. Dieses Edge-Netzwerk bietet die beste Umgebung und Leistung für Verbindungen über das Internet.

- Bei der Verwendung von Office 365 für einen der enthaltenen Dienste wie Skype for Business online-sprach-, Video-oder Besprechungsfunktionen müssen Kunden eine End-to-End-Netzwerkbewertung abschließen und die Anforderungen mit Skype Operations Framework erfüllen. Diese Kunden haben verschiedene Optionen, um bestimmte Anforderungen an die Cloud-Konnektivität zu erfüllen, einschließlich Express Route.

Werfen Sie einen Blick auf die Microsoft-Fallstudie [zur Optimierung der Netzwerkleistung für Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Wenn Sie Office 365 auswerten und sich nicht sicher sind, wo Sie mit der Netzwerkbewertung beginnen oder Netzwerk Design Herausforderungen gefunden haben, die Sie unterstützen müssen, sollten Sie mit Ihrem Microsoft-Konto Team zusammenarbeiten.
  
Lesen Sie außerdem [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) , um die Verbindungs Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und die bestmögliche Leistung zu verstehen. Dieser Artikel hilft Ihnen, die neuesten Richtlinien für die sichere Optimierung der Office 365-Netzwerkkonnektivität zu verstehen.
  
Hier ist ein kurzer Link, den Sie verwenden können, um zurückzukehren: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
  
[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
  
[Verwenden von BGP-Communities in Express Route für Office 365-Szenarien (Preview)](bgp-communities-in-expressroute.md)
  
[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[URLs und IP-Adressbereiche für Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Prinzipien von Office 365-Netzwerkverbindungen](https://aka.ms/o365networkingprinciples)
