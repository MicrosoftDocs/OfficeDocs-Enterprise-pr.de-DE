---
title: Bewerten Office 365 Netzwerkkonnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
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
description: Office 365 ist so konzipiert, dass Kunden auf der ganzen Welt eine Verbindung mit dem Dienst über eine Internetverbindung herstellen können. Während sich der Dienst entwickelt, werden Sicherheit, Leistung und Zuverlässigkeit von Office 365 basierend auf Kunden verbessert, die über das Internet eine Verbindung mit dem Dienst herstellen.
ms.openlocfilehash: 3ea80ddccaf9fabbe158a10f0af1d35dbf3a9889
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "34724825"
---
# <a name="assessing-office-365-network-connectivity"></a>Bewerten Office 365 Netzwerkkonnektivität

Office 365 ist so konzipiert, dass Kunden auf der ganzen Welt eine Verbindung mit dem Dienst über eine Internetverbindung herstellen können. Während sich der Dienst entwickelt, werden Sicherheit, Leistung und Zuverlässigkeit von Office 365 basierend auf Kunden verbessert, die über das Internet eine Verbindung mit dem Dienst herstellen.
  
Kunden, die Office 365 verwenden möchten, sollten Ihre vorhandenen und prognostizierten Anforderungen an die Internetkonnektivität als Teil des Bereitstellungsprojekts bewerten. Für die Bereitstellung von Unternehmensklassen ist eine zuverlässige und entsprechend große Internetverbindung ein wichtiger Bestandteil des Verbrauchs von Office 365 Features und-Szenarien.
  
Netzwerk Auswertungen können je nach Größe und Einstellungen von vielen verschiedenen Personen und Organisationen ausgeführt werden. Der Netzwerkbereich der Bewertung kann auch variieren, je nachdem, wo Sie sich im Bereitstellungsprozess befinden. Damit Sie besser verstehen, was zum Durchführen einer Netzwerkbewertung benötigt wird, haben wir einen Leitfaden zur Netzwerkbewertung erstellt, um Ihnen die verfügbaren Optionen näher zu bringen. Mit dieser Bewertung wird bestimmt, welche Schritte und Ressourcen dem Bereitstellungsprojekt hinzugefügt werden müssen, damit Sie Office 365 erfolgreich annehmen können.
  
Eine umfassende Netzwerkbewertung, wie Sie im [Skype Operations Framework](https://www.skypeoperationsframework.com/) vorgeschrieben ist, bietet mögliche Lösungen für Herausforderungen im Zusammenhang mit dem Netzwerk Design und Implementierungsdetails. Die meisten Netzwerkbewertungen deuten darauf hin, dass die Netzwerkkonnektivität zu Office 365 mit [kleineren Konfigurations-oder Entwurfsänderungen](https://aka.ms/manageo365endpoints) an der vorhandenen Netzwerk-und Internet Ausgangs Infrastruktur untergebracht werden kann.

Bei einigen Bewertungen wird darauf hingewiesen, dass die Netzwerkkonnektivität für Office 365 zusätzliche Investitionen in Netzwerkkomponenten erfordert. Beispielsweise Investitionen in WAN-Bandbreite oder optimierte Routinginfrastruktur zur Unterstützung der Internetkonnektivität mit Office 365. Gelegentlich wird in einer Bewertung darauf hingewiesen, dass die Netzwerkverbindung mit Office 365 von den Vorschriften oder Leistungsanforderungen für Szenarien wie [Skype for Business Online Medienqualität](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)beeinflusst wird. Diese zusätzlichen Anforderungen können zu Investitionen in die Infrastruktur für die Internetkonnektivität, die Routing Optimierung und die spezielle direkte Konnektivität führen.
  
> [!NOTE]
> Microsoft Authorization ist für die Verwendung von Express Route für Office 365 erforderlich. Microsoft überprüft alle Kundenanforderungen und autorisiert Express Route nur für Office 365 Nutzung, wenn die regulatorische Anforderung eines Kunden eine direkte Konnektivität erfordert. Wenn Sie solche Anforderungen haben, stellen Sie bitte den Textauszug und den Weblink der von Ihnen interpretierten Richtlinie bereit, damit die direkte Konnektivität im [Express Route für Office 365 Anforderungsformular](https://aka.ms/O365ERReview) zum Starten einer Microsoft-Überprüfung erforderlich ist. Nicht autorisierte Abonnements, die versuchen, Routenfilter für Office 365 zu erstellen, erhalten eine [Fehlermeldung](https://support.microsoft.com/kb/3181709).
  
Wichtige Punkte, die bei der Planung Ihrer Netzwerkbewertung für Office 365 zu berücksichtigen sind:
  
- Office 365 ist ein sicherer, zuverlässiger Dienst mit hoher Leistung, der über das öffentliche Internet ausgeführt wird. Wir investieren weiterhin, um diese Aspekte des Diensts zu verbessern. Alle Office 365 Dienste stehen über Internetkonnektivität zur Verfügung.

- Wir optimieren die Kernaspekte Office 365 wie Verfügbarkeit, globale Reichweite und Leistung für internetbasierte Konnektivität kontinuierlich. Viele Office 365 Dienste nutzen beispielsweise eine wachsende Gruppe von Edge-Knoten mit Internetzugriff. Dieses Edge-Netzwerk bietet die beste Nähe und Leistung für Verbindungen, die über das Internet kommen.

- Bei der Verwendung von Office 365 für alle enthaltenen Dienste wie Skype for Business online sprach-, Video-oder Besprechungsfunktionen müssen Kunden eine End-to-End-Netzwerkbewertung durchführen und die Anforderungen in unserem Skype Operations Framework erfüllen. Diese Kunden haben mehrere Optionen, um bestimmte Anforderungen für Cloud-Konnektivität zu erfüllen, einschließlich Express Route.

Werfen Sie einen Blick auf die Microsoft-Fallstudie [zur Optimierung der Netzwerkleistung für Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Wenn Sie Office 365 bewerten und nicht sicher sind, wo Sie mit ihrer Netzwerkbewertung beginnen oder Herausforderungen im Zusammenfall mit dem Netzwerk Design gefunden haben, die Sie unterstützen müssen, wenden Sie sich an Ihr Microsoft-Konto Team.
  
Lesen Sie außerdem [Office 365 Grundsätze der Netzwerkkonnektivität](https://aka.ms/o365networkingprinciples) , um die Verbindungs Prinzipien für die sichere Verwaltung Office 365 Datenverkehrs und die bestmögliche Leistung zu verstehen. Dieser Artikel hilft Ihnen, die neuesten Anleitungen für die sichere Optimierung Office 365 Netzwerkkonnektivität zu verstehen.

## <a name="the-office-365-network-onboarding-tool"></a>Das Onboarding-Tool für Office 365-Netzwerk

Sie können das Onboarding- [Tool für Office 365-Netzwerk](https://aka.ms/netonboard)verwenden, ein neues Tool für Machbarkeitsstudie (Proof of Concept), um grundlegende Verbindungstests auszuführen, die spezifische Anleitungen für Verbesserungen bei der Netzwerkkonnektivität bieten, die zwischen einem bestimmten Benutzerstandort und Office 365 vorgenommen werden können.

Das Onboarding-Tool für das Netzwerk führt folgende Schritte aus:

- Ermittelt ihren Standort oder Sie können einen Test Speicherort angeben
- Überprüft den Speicherort Ihres Netzwerk Ausstiegs.
- Testet den Netzwerkpfad auf den nächsten Office 365 Dienst Haustür

Das Tool zeigt die folgenden Informationen an:

- Registerkarte "Ergebnisse und Auswirkungen"
  - Der Ort auf der Karte der Haustür des in-use-Diensts
  - Der Ort auf einer Karte mit anderen Dienst Fronttüren, die eine optimale Konnektivität bieten würde
  - Relative Leistung im Vergleich zu anderen Office 365 Kunden in Ihrer Nähe
- Registerkarte "Details und Lösungen"
  - Benutzerstandort nach Ort und Land
  - Netzwerk Ausgangsstandort nach Stadt, Staat und Land
  - Abstand von Benutzer zu Netzwerk Ausgang
  - Front-Door-Standort Office 365 Exchange Online-Dienst
  - Optimale Office 365 Exchange Online Dienst-Haustür (en) für den Benutzerstandort
  - Kunden in ihrer Metro-Region mit besserer Leistung

Sie können Informationen zur Version des Office 365-Netzwerk-Onboarding-Tools lesen und Feedback zum Blogbeitrag [Office 365 Network Performance Tool POC](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102) geben. Informationen zu zukünftigen Updates für dieses Tool und andere Office 365 Netzwerk Updates werden im Blog [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) veröffentlicht.
  
Hier ist ein kurzer Link, den Sie verwenden können, um zurückzukehren: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Siehe auch

[Office 365 Netzwerkkonnektivität (Übersicht)](office-365-networking-overview.md)

[Prinzipien von Office 365-Netzwerkverbindungen](https://aka.ms/o365networkingprinciples)

[Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md)

[URLs und IP-Adressbereiche für Office 365](urls-and-ip-address-ranges.md)

[Office 365 – IP-Adress- und URL-Webdienst](office-365-ip-web-service.md)

[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)
