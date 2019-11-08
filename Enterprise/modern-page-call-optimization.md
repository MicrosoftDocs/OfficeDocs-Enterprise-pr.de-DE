---
title: Das Optimieren von Seiten ruft moderne und klassische Veröffentlichungswebsiteseiten von SharePoint Online auf
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Erfahren Sie, wie Sie moderne und klassische Veröffentlichungswebsiteseiten in SharePoint Online optimieren können, indem Sie die Anzahl der Aufrufe von SharePoint Online-Service-Endpunkten begrenzen.
ms.openlocfilehash: 1219e1a1362264fb3cd1dc6bd4843eec39d84041
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031280"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Das Optimieren von Seiten ruft moderne und klassische Veröffentlichungswebsiteseiten von SharePoint Online auf

Sowohl moderne als auch klassische SharePoint Online VVeröffentlichungswebsiteseiten enthalten Links, die Daten von SharePoint-Funktionen und CDNs laden (oder anrufen). Je mehr Aufrufe von einer Seite gemacht werden, desto länger dauert das Laden der Seite. Dies wird als **vom Endverbraucher wahrgenommene Latenzzeit** oder **EUPL** bezeichnet.

Dieser Artikel beschreibt, wie Sie die Anzahl und Auswirkung von Aufrufen auf externe Endpunkte von Ihren modernen und klassischen Veröffentlichungswebsiteseiten bestimmen und wie Sie deren Auswirkungen auf die vom Endbenutzer wahrgenommene Latenzzeit begrenzen können.

>[!NOTE]
>Weitere Informationen zur Leistung in modernen SharePoint Online-Portalen finden Sie unter [Leistung in der modernen SharePoint-Umgebung](https://docs.microsoft.com/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a>Verwenden Sie das Tool „Seitendiagnose für SharePoint“, um die Seitenaufrufe zu analysieren

Das **Tool für die Seitendiagnose für SharePoint** ist eine Browser-Erweiterung für Chrome und [Microsoft Edge Version 77 oder höher](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8), mit denen Sie SharePoint sowohl moderne als auch klassische Veröffentlichungswebsiteseiten analysieren können. Das Tool stellt für jede analysierte Seite einen Bericht bereit, in dem die Leistung der Seite anhand einer definierten Gruppe von Leistungskriterien dargestellt wird. Für Informationen und zur Installation der Seitendiagnose für SharePoint-Tools, besuchen Sie[Verwenden des Seitendiagnose-Tools für SharePoint Online](page-diagnostics-for-spo.md).

Wenn Sie eine SharePoint-Website Seite mit dem Tool „Seitendiagnose für SharePoint“ analysieren, finden Sie Informationen zu externen Aufrufen im **Anforderungen für SharePoint** Ergebnis im Bereich_Diagnosetests_. Die Zeile wird grün angezeigt, wenn die Standortseite weniger als die Grundwert-Nummer der Aufrufe enthält, und rot, wenn die Seite die Grundwert-Nummer überschreitet. Die Grundwert-Nummer ist für moderne und klassische Seiten unterschiedlich, da klassische Seiten HTTP1.1 und moderne Seiten HTTP2.0 verwenden:

- Moderne Seiten der Website sollten nicht mehr als **25** Aufrufe enthalten.
- Klassische Veröffentlichungsseiten sollten nicht mehr als **6** Aufrufe enthalten.

Mögliche Ergebnisse beinhalten:

- **Aktion erforderlich** (rot): Die Seite überschreitet den Grundwert der Anfragen.
- **Keine Aktion erforderlich** (grün): Die Seite enthält weniger als den Grundwert der Anfragen.

Wenn das Ergebnis **Anforderungen für SharePoint** im Abschnitt **Aktion erforderlich** erscheint, können Sie auf das Ergebnis klicken, um Details zu erhalten, einschließlich der Gesamtzahl der Aufrufe auf der Seite und einer Liste der URLs.

![Anforderungen für SharePoint-Ergebnisse](media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a>Beheben von Leistungsproblemen im Zusammenhang mit zu vielen Aufrufen auf einer Seite

Wenn eine Seite zu viele Aufrufe enthält, können Sie anhand der Liste der URLs in den Ergebnissen der **Anforderungen für Sharepoint** feststellen, ob es sich um wiederholte Aufrufe, Aufrufe, die gebündelt werden sollen, oder Aufrufe handelt, die Daten zurückgeben, die zwischengespeichert werden sollen.

**Die Batchverarbeitung von REST-Aufrufen** kann dazu beitragen, den Verwaltungsaufwand zu verringern. Weitere Informationen über die Batchverarbeitung von API-Aufrufen finden Sie unter [Erstellen von Batchanforderungen mit den REST-APIs](https://docs.microsoft.com/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).

**Die Verwendung eines Caches** zum Speichern der Ergebnisse eines API-Aufrufs kann die Leistung einer warmen Anforderung verbessern, indem der Client die zwischengespeicherten Daten verwenden kann, anstatt für jeden nachfolgenden Seitenaufruf einen zusätzlichen Aufruf zu tätigen. Je nach Geschäftsanforderung gibt es verschiedene Möglichkeiten, diese Lösung anzugehen. Wenn die Daten für alle Benutzer gleich sind, ist die Verwendung eines Middle-Tier-Caching-Dienstes wie [_Azure Redis_Cache](https://azure.microsoft.com/services/cache/) eine gute Option, um den API-Verkehr mit einer Website deutlich zu reduzieren, da die Benutzer die Daten vom Caching-Dienst statt direkt vom SPO anfordern würden. Die einzigen SPO-Aufrufe, die benötigt werden, sind das Aktualisieren des Middle-Tier-Cache. Wenn die Daten je nach Benutzer variieren, kann es sinnvoll sein, einen clientseitigen Cache wie LocalStorage oder sogar ein Cookie zu implementieren. Dies reduziert dennoch das Anrufvolumen, indem nachfolgende Anforderungen durch den gleichen Benutzer für die Cachedauer beseitigt werden, ist aber weniger effizient als ein spezieller Caching-Dienst. PnP ermöglicht es Ihnen, LocalStorage mit geringem Entwicklungsaufwand zu nutzen.

Bevor Sie Seitenrevisionen zur Behebung von Leistungsproblemen durchführen, notieren Sie sich die Ladezeit der Seite in den Analyseergebnissen. Führen Sie das Tool nach Ihrer Revision erneut aus, um zu sehen, ob das neue Ergebnis innerhalb des Grenzwertes liegt, und überprüfen Sie die Ladezeit der neuen Seite, um festzustellen, ob eine Verbesserung vorliegt.

![Ergebnisse der Seitenladezeiten](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Die Seitenladezeit kann aufgrund einer Vielzahl von Faktoren wie Netzwerklast, Tageszeit und anderen vorübergehenden Schwierigkeiten variieren. Sie sollten die Seitenladezeit einige Male vor und nach der Durchführung von Änderungen testen, um einen Mittelwert zu berechnen.

## <a name="related-topics"></a>Verwandte Themen

[Optimieren der Leistung von SharePoint Online](tune-sharepoint-online-performance.md)

[Optimieren der Leistung von Office 365](tune-office-365-performance.md)

[Leistung in der modernen SharePoint-Oberfläche](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)

[Verwenden des Office 365 Content Delivery Network (CDN) mit SharePoint Online](use-office-365-cdn-with-spo.md)
