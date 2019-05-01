---
title: Kapazitätsplanung und Auslastungstests für SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: In diesem Artikel wird beschrieben, wie Sie in SharePoint Online bereitstellen können, ohne herkömmliche Auslastungstests durchzuführen, da dies nicht zulässig ist.
ms.openlocfilehash: 615ad96f4fcf3ac939785e3aafb32956f5661e36
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490216"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Kapazitätsplanung und Auslastungstests für SharePoint Online.

In diesem Artikel wird beschrieben, wie Sie SharePoint Online ohne herkömmliche Auslastungstests bereitstellen können, da Auslastungstests in SharePoint Online nicht zulässig sind. SharePoint Online ist ein clouddienst, der die Auslastungs-, Integritäts-und Gesamtlasten Verteilung im Dienst von Microsoft verwaltet.
  
Der beste Ansatz zur Sicherstellung des Erfolgs der Einführung Ihrer Website besteht darin, grundlegende Prinzipien, Praktiken und Empfehlungen zu befolgen, die unten hervorgehoben werden.
  
Bei lokalen Umgebungen werden Auslastungstests verwendet, um die Skalierungs Annahme zu überprüfen und schließlich den Endpunkt einer Farm zu finden. durch Sättigung mit Belastung. Bei SharePoint Online müssen wir die Dinge anders machen. Da es sich um eine Umgebung mit mehreren Mandanten handelt, müssen alle Mandanten in derselben Farm geschützt werden, sodass Auslastungstests automatisch eingeschränkt werden. Dies führt zu enttäuschenden und potenziell irreführenden Ergebnissen, wenn Sie versuchen, Ihre Umgebung zu laden.
  
Einer der Hauptvorteile von SharePoint Online über eine lokale Bereitstellung ist die Elastizität der Cloud. Unsere großflächige Umgebung ist so eingerichtet, dass Millionen von Benutzern täglich gewartet werden, daher ist es wichtig, dass wir die Kapazität effektiv bewältigen, indem Sie Farmen ausbalancieren und erweitern. Der Artikel behandelt auch Vorgehensweisen für Sie zu verwenden, die keine Auslastungstests beinhalten, aber die folgenden Richtlinien enthalten, die Sie für einen erfolgreichen Start einrichten. 
  
Während das Wachstum für jeden einzelnen Mandanten in einer Farm unvorhersehbar ist, ist die aggregierte Summe der Anforderungen im Laufe der Zeit vorhersehbar. Durch die Ermittlung der Wachstumstrends in SharePoint Online können wir zukünftige Erweiterungen planen.
  
Um die Kapazität effizient zu nutzen und unerwartete Zuwächse zu bewältigen, haben wir in jeder Farm Automatisierung, die das Front-End-laden überwacht und bei Bedarf skaliert. Es gibt mehrere Metriken, die bei einer der wichtigsten CPU-Auslastung verwendet werden, die als Signal zum Skalieren von Front-End-Servern dient. Darüber hinaus empfehlen wir einen phasenweisen/Wave-Ansatz, da SQL-Umgebungen entsprechend der Auslastung und der Nachfrage skaliert werden und die Phasen und Wellen die korrekte Verteilung der Auslastung und des Wachstums ermöglichen. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>Wie plane ich einen Website Start?

### <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimieren von Seiten anhand der empfohlenen Richtlinien
Seiten aus einer lokalen Bereitstellung sollten nicht einfach in SharePoint Online übernommen werden, ohne Sie anhand der empfohlenen Richtlinien für SharePoint Online zu überprüfen.

Einige wichtige Faktoren sollten berücksichtigt werden:
- Lokale Bereitstellungen können herkömmliche serverseitige Caches wie Objektcache nutzen, aber mit den Unterschieden in der Topologie in der Cloud stehen diese Optionen nicht zur Verfügung.
- Alle Seiten/Features/Anpassungen, die für die Cloud-Nutzung verwendet werden, sollten für mehrere Standorte optimiert werden, sodass Benutzer in unterschiedlichen Bereichen oder Regionen über eine konsistente Erfahrung verfügen. Cloud bietet Optimierungen wie Content Delivery Networks (CDN) zur Optimierung für eine verteilte Benutzerbasis.

Bei klassischen Veröffentlichungsseiten in SharePoint Online können Sie die Chrome-Erweiterung für das [Seiten Diagnosetool](https://aka.ms/perftool) verwenden, die bei der Analyse der von Benutzern verwendeten Hauptzielseiten behilflich ist.
F12-Entwicklertools im Browser oder [Fiddler](https://www.telerik.com/download/fiddler) können verwendet werden, um die Gewichtung der Seite zu überprüfen, und die Anzahl der Aufrufe und Elemente, die sich auf die gesamte Seitenlast auswirken, sollte überprüft und optimiert werden. Eine Liste mit Empfehlungen, einschließlich der Verwendung von Inhalts Bereitstellungs Netzwerken und anderen Optimierungen, können Sie im Artikel [Tune SharePoint Online-Leistung](https://aka.ms/tuneSPO) durchführen.

### <a name="wave--phase-approach"></a>Wave/Phase-Ansatz
Der herkömmliche Big Bang-Ansatz für Website Starts ermöglicht nicht effektiv die Überprüfung, ob Anpassungen, externe Quellen, Dienste oder Prozesse im richtigen Umfang getestet wurden. SharePoint as a Service skaliert ihre Kapazität auch basierend auf der Nutzung und der vorhergesagten Nutzung, und während wir Sie nicht über Ihren Website Start informieren müssen, sollten Sie die folgenden Richtlinien befolgen, um den Erfolg sicherzustellen.
  
Wie in der folgenden Abbildung dargestellt, ist die Anzahl der Benutzer, die eingeladen werden, deutlich höher als die, die die Website tatsächlich verwenden. Dieses Bild zeigt eine Strategie zum Rollout einer Freigabe. Diese Methode hilft bei der Identifizierung von Möglichkeiten zur Verbesserung der SharePoint-Website, bevor die Mehrheit der Benutzer Sie sehen. Außerdem kann ein Rollout angehalten werden, wenn Probleme in einer der Phasen/Wellen auftreten, wodurch die potenzielle Anzahl betroffener Benutzer eingeschränkt wird.
  
![Diagramm mit eingeladenen und aktiven Benutzern](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
In der Pilotphase empfiehlt es sich, Feedback von Benutzern zu erhalten, die von der Organisation als vertrauenswürdig eingestuft werden. Auf diese Weise kann gemessen werden, wie das System verwendet wird und wie es ausgeführt wird.
  
Sammeln Sie während jeder der Wellen ein Feedback der Benutzer zu den Features und zur Leistung bei jeder Bereitstellungs Welle. Dies hat den Vorteil, dass Sie das System langsam einführen und Verbesserungen vornehmen, wenn das System mehr nutzt. Dies ermöglicht es uns auch, auf die erhöhte Auslastung zu reagieren, da die Website für immer mehr Benutzer eingeführt wird.
