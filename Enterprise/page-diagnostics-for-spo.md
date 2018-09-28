---
title: Verwenden Sie das Seite-Diagnosetool für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: Verwenden Sie die Seite Diagnose für SharePoint-Tool, um die klassischen Seiten mit empfohlenen best Practices für SharePoint Online zu analysieren.
ms.openlocfilehash: 0fc2e16867b54e644d00c57fbfc41d4f7d042f88
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975163"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Verwenden Sie das Seite-Diagnosetool für SharePoint Online

In diesem Artikel wird beschrieben, wie Sie das Seite Diagnose-Tool verwenden können, um den klassischen Veröffentlichungsseiten und Seiten auf klassische Teamwebsites, gegen eine Teilmenge der empfohlenen Vorgehensweisen in **SharePoint Online**analysieren. 
  
Teamwebsites, die Veröffentlichung aktiviert nicht aufweisen können CDNs verwenden, aber alle verbleibenden Regeln gelten. Veröffentlichung fügt zusätzlichen Aufwand damit nicht aktivieren auf veröffentlichen, um die CDN-Funktionalität zu erhalten, wie er sich negativ auf die Seitenladezeiten auswirkt.
  
> [!IMPORTANT]
> Das Seite-Diagnosetool wird nicht für Dokumentbibliotheken oder, Systemseiten anzeigen, ausführen, wie das Tool zum Überprüfen von SharePoint-Websiteseiten vorgesehen ist. Ein *allitems.aspx* ist eine Seite System. Wenn Sie versuchen, das Tool auf einer Seite System auszuführen, erhalten Sie eine Meldung angezeigt, "diese Anwendung sollte nur ausgeführt werden auf SharePoint-Seiten."<br/> ![Muss auf einer SharePoint-Seite ausgeführt werden](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>Dies ist ein Fehler im Tool nicht, wie bei der Bewertung von Bibliotheken oder Systemseiten kein Wert vorhanden ist. Navigieren Sie zu einer anderen als dem SharePoint-Seite mit dem Tool. Sie Feedback zu erteilen möchten, sollte das Tool Bitte klicken Sie auf der Registerkarte Info und führen Sie den [Feedbacklink geben](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Installieren Sie das Tool Seite Diagnose

> [!IMPORTANT]
> Microsoft kann keine Daten oder besuchten lesen, und wir keine persönlichen Informationen, Website oder Herunterladen von Informationen mit diesem Tool aufzeichnen. Die einzige Information, die von dem Tool angemeldet ist der Name des Mandanten Regel Anzahl von Elementen und gibt an, ob die Protokollierungsoption Unterstützung bei der Ausführung des Tools eingesetzt wird. Diese Informationen sind für Microsoft zu analysieren, welche Probleme sind unsere Kunden auftraten wird und sicherzustellen, dass die Support-Protokollierung-Funktion nicht unberechtigter Verteilung wird ist.

1. Chrome-Browsers verwenden, öffnen Sie den [Link zum Tool](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) direkt oder öffnen Sie die Suche in der [Chrome Browser WebStore](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) und installieren Sie die Browsererweiterung. Überprüfen Sie die Benutzer Datenschutzrichtlinie auf der Beschreibungsseite im Speicher bereitgestellt. Wenn Sie das Tool für Ihren Browser hinzufügen, sehen Sie die folgenden Berechtigungen zu beachten.<br/>![Berechtigungen für den Chrome](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Dieser Hinweis ist vorhanden, da eine Seite Inhalte aus Quellen außerhalb von SharePoint je nach Webparts und Anpassungen auf der Seite enthalten kann. Dies bedeutet, dass das Tool die Anforderungen und Antworten lesen wird beim Klicken auf die Startschaltfläche, und nur für die aktive SharePoint-Registerkarte, wenn das Tool ausgeführt wird. Diese Informationen werden vom Webbrowser lokal erfasst und über den Export in JSON Link im Tool für Sie verfügbar ist. **Die Informationen nicht gesendet oder von Microsoft erfasst.** (Das Tool der Microsoft Privacy-Richtlinie zugänglich [hier](https://go.microsoft.com/fwlink/p/?linkid=857875)berücksichtigt.)<br/><br/>Die Funktionalität "Exportieren in JSON" im Tool ist auch, warum die Berechtigung "Verwalten von Downloads" erforderlich ist. Führen Sie Ihre Datenschutzrichtlinien des Unternehmens, bevor die Freigabe der JSON-Datei außerhalb Ihrer Organisation, wie URLs und, die Ergebnisse enthalten als personenbezogene Informationen (Personally Identifiable Information) klassifiziert werden kann.
    
2. (Dieser Schritt ist optional.) Wenn Sie das Tool im incognito Chrome-Modus verwenden möchten, navigieren Sie zu der Erweiterung, und klicken Sie auf **in Incognito zulassen**.
    
3. Navigieren Sie zu der SharePoint klassische Veröffentlichungsseite auf SharePoint Online, die Sie überprüfen möchten. Wir haben "Verzögerung beim Laden von" erlaubte von Elementen auf Seiten; aus diesem Grund das **Tool wird nicht automatisch beendet**. Sie sollten Auflistung beenden möchten, können Sie **Beenden**klicken. (Dies ist entwurfsbedingt, für alle Seite Load Szenarien abzudecken.) Bevor Sie auf **Beenden**klicken, stellen Sie sicher, dass die Netzwerk-Ablaufverfolgungsdaten abgeschlossen ist. Andernfalls müssen Sie einen partiellen Trace. Darüber hinaus das Tool ist eine Erweiterung des Browsers, und öffnen mehrere Registerkarten oder Windows lässt nur eine aktive Instanz des Tools gleichzeitig ausgeführt werden. Dies ist eine Einschränkung Erweiterungen im Browser. 
  
4. Klicken Sie auf die Erweiterung-logo ![Seite Diagnose für SharePoint-logo](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) So laden Sie das Tool, und Sie werden mit dem folgenden Erweiterung Popup-Fenster angezeigt:<br/> ![Seite-Diagnosetool Popup](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Starten Sie und beenden Sie Vorgänge führen Sie das grundlegende Konzept der beim Klicken auf Start, wird die Seite erneut zu laden, und Auflistung begonnen wird.

Lesen Sie die folgenden Abschnitte, Weitere Informationen über die Angaben im Tool.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Was sehen Sie in der Seite Diagnose-tool
    
1. Der Link **zur** bietet allgemeine Hinweise und Einzelheiten zu dem Tool einschließlich einen Link zu diesem Artikel sichern. Darüber hinaus eine direkte Verknüpfung zu SharePoint leistungsempfehlungen und einer Drittanbieter-Anmerkung zur zu eine Option, um Feedback über das Tool. 
    
2. Die **Korrelations-ID, SPRequestDuration, SPIISLatency**, **Seite des Ladens**und **URL** -Details dienen nur zu Informationszwecken, und einige Zwecken verwendet werden können. 
    
  - **CorrelationID** ist ein wichtiger Faktor beim Arbeiten mit der Microsoft Support-Teams, da sie diese zusätzliche Diagnosedaten pull ermöglicht. 
    
  - **SPRequestDuration** ist der Server Verarbeitungszeit für die Seite. Wenn dieser Zeit lang ist, bedeutet dies nicht unbedingt, dass der Server wurde nicht ordnungsgemäß ausgeführt, aber auch entsprechend die Anzahl von Anrufen und Laden von der Seite auf den Server übertragen z. B. strukturelle Navigation, großen Bilder, viele API-Aufrufe könnte zum Server länger beitragen . 
    
  - **SPIISLatency** ist die Zeit in Millisekunden, die auf dem Front-End-Webserver ausgeführt werden, wenn sie die Anforderung zum Laden der Seite empfängt. Dies ist ein Indikator, der Wartezeit, mit der Verarbeitung der Seite und umfasst nicht die Zeit für die Webanwendung zu reagieren. 
    
  - **Ladezeit der Seite** wird von der Seite auf den Zeitpunkt, den die Antwort erhalten und vom Browser gelesen wurde, von dem Zeitpunkt der Anforderung erfasste Zeit. Zusätzliche jederzeit ist betroffen, durch die Leistung des Computers und der Zeitaufwand für das Browser geladen werden. 
    
  - Die **URL** (Uniform Resource Locator) ist die Webadresse der aktuellen Seite. 
    
3. Die [ **Diagnose** Registerkarte](#how-to-use-the-diagnostic-tab) werden die Regeln aufgelistet, und wenn sie mit einem roten markiert ![schneidet](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), und klicken Sie dann auf der Seite identifiziert Probleme vorliegen.<br/>Jede Regel verfügt über einen eigenen Link "Weitere Informationen", die Sie klicken Sie auf, wenn ein Element Rot ist. Gelangen, die Sie zur Hintergrundinformationen zu dieser Regel und wie Sie das Problem zu beheben.<br/>![Diagnose Red - Regel öffnen](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Bietet eine [ **Netzwerk-Trace** Registerkarte](#how-to-use-the-network-trace-tab) Details zur Seite Anforderungen und-Antworten erstellen.

## <a name="how-to-use-the-diagnostic-tab"></a>So verwenden Sie die Registerkarte Diagnose

1. **Kontrollkästchen Ausführung als Standardbenutzer**  Überprüfen die Seite Leistung sollten nicht ausgeführt werden, ein Dienstkonto, Administrator oder Websitesammlungsadministrator oder ein Konto mit erhöhten Rechten angemeldet. Zusätzliche Skripts und Funktionen werden speziell für diese Typen von Konten, geladen, sodass die Ergebnisse keine echte Darstellung der Seite Leistung.
    
2. **Überprüfen von Anfragen an SharePoint**  Die Menge an Daten und Anforderungen an den Server sollten beschränkt werden, eine Seite überladene Leistungseinbußen kommen wird. Diese Prüfung überprüft, ob die Anzahl der Anfragen an SharePoint und wird darauf hinzuweisen, wenn die Anfragen 6 Anforderungen überschreiten. Die meisten Anfragen sollte zwischengespeichert und daher nicht bei jedem Laden der Seite aufgerufen werden soll. Cache eingerichtet werden soll, und Reduzieren von Anrufen zu einer Seite von jedem Benutzer mit mindestens 15 Minuten verwendet. Dies ist ein allgemeines Problem und in den meisten Fällen Daten ändert nur täglich jedoch die Seite überprüft und ruft Daten jedes Mal für jede Seite für jeden Benutzer, die häufig nicht erforderlich ist.
    
3. **Überprüfen Sie mithilfe von CDNs**  Hier sind die SharePoint Online Content Delivery Networks wurden von Microsoft und diejenigen genannten Content Delivery Networks (CDNs) bereitgestellt. Es sind mehrere Typen sowie andere CDN-Diensten wie SharePoint CDNs, und klicken Sie dann CDNs in Azure verfügbar. [Verwenden Sie die folgende Anleitung](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Überprüfen Sie für großes Bildgrößen**  Bilder sollten durch die Nutzung von besserer Web Types wie PNG für Web optimiert werden. Bilddarstellungen sollten auch verwendet werden und direkt in SharePoint verfügbar ist. Bilder / bilddarstellungen größer als 100kb hervorgehoben wird nicht für Web optimiert. [Verwendung der folgenden Richtlinien für die Optimierung Bilder](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Überprüfen Sie für die strukturelle Navigation**  Strukturelle Navigation wurde ursprünglich für die Verwendung in lokale SharePoint-entwickelt, in dem Objektcache genutzt werden kann. Strukturelle Navigation wird nicht empfohlen, für die Verwendung in SharePoint Online und verwaltete Navigation oder einen benutzerdefinierten Anbieter geändert werden soll. [Verwenden Sie die folgende Hinweise zum Optimieren der Navigation.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Überprüfen Sie CBQ-WebPart** (CBQ - Inhalt-nach-Abfrage-WebPart)  Das Inhalt-nach-Abfrage-WebPart generiert eine hohe SQL Last, wie sie alle Elemente in der Abfrage bei jedem Laden der Seite für jeden Benutzer durchläuft. Im Gegensatz zu einer lokalen Installation ist kein Cache zur Begrenzung der Anzahl der Abfragen, die zum Auffüllen dieses WebPart benötigt. Als solche CBQ langsam und wirkt sich auf die Seite gesamtleistung aus diesem Grund sollten nicht genutzt werden. Verwenden Sie die Content Search-WebPart (CSWP) als Ersatz für die Content-Abfrage-WebPart. [Verwenden Sie die folgende Hinweise, die im Zusammenhang mit der Content Search-WebPart](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>So verwenden Sie die Registerkarte Netzwerk-Trace
    
Die Registerkarte **Netzwerk-Trace** bietet ausführliche Informationen zu den Anforderungen der Seite als auch die Antworten empfangen erstellen. 

1. **Suchen Sie nach dem Element Ladezeiten als rot gekennzeichneten**. Die Leistung von jeder Anforderung und Antwort sind farblich, basierend auf deren Einfluss auf die Leistung der gesamten Seite wie folgt:
- Grün: \< 500 ms
- Gelb: 500-1000 MS
- Rot: \> 1000 MS
<br/>![Netzwerk-Trace](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/>Im oben gezeigten Bild bezieht sich auf der Standardseite das rote Element. Es wird immer rot angezeigt, es sei denn, die Seite vollständig geladen \< 1000 ms (weniger als 1 Sekunde).

2. **Test-Element Ladezeiten**. In einigen Fällen wird kein Indikator Zeit oder Farbe, da die Elemente bereits vom Browser zwischengespeichert wurden. Um dies ordnungsgemäß zu testen, öffnen Sie die Seite, deaktivieren Sie Browser-Cache und klicken Sie dann auf **Starten** , die eine Last "kalt" Seite erzwungen wird und eine true Reflektion des ersten Laden der Seite ist. Dies sollte klicken Sie dann auf die Seite "warm" Load verglichen werden, wie, die auch helfen zu bestimmen, welche Elemente auf der Seite zwischengespeichert werden. 
    
3. **Freigabe umfassen relevante Informationen für andere Personen, die helfen, Probleme zu untersuchen**. Klicken Sie auf **Exportieren in JSON** , (wie in der obigen Abbildung dargestellt), um zum Freigeben von der Details oder Metriken im Tool mit der Entwickler oder ein Mitarbeiter des technischen Supports. Aktivieren, die Sie zum Laden Sie die Ergebnisse, die mit einer JSON Dateiviewer angezeigt werden können.

> [!IMPORTANT]
> Diese Ergebnisse die URLs enthalten, und, die als personenbezogene Informationen (Personally Identifiable Information) klassifiziert werden können. Stellen Sie sicher, dass Sie Ihrer Organisation Richtlinien zu befolgen, bevor Sie diese Informationen verteilen. 

## <a name="engaging-with-microsoft-support"></a>Zusammenarbeit mit Microsoft-Support
   
Wir haben ein **Feature von Microsoft Support-Stufe** enthalten, die beim Arbeiten direkt auf einer Supportanfrage aus Leistungsgründen nur genutzt werden sollte. Nutzen dieses Feature bietet keine Vorteile bei ohne unserem Supportteam verwendet wird. Erleichtern der Seite wesentlich langsamer ausführen tatsächlich und fortgesetzte Einsatz der Funktion "Missbrauch" des Diensts angesehen werden kann. Es sind keine weiteren Informationen beim Verwenden dieser Funktion in das Tool, sobald die zusätzliche Informationen die Protokollierung im Dienst hinzugefügt wird. 

Keine Änderung ist sichtbar, außer dass Sie benachrichtigt werden, dass Sie aktiviert haben und Ihre Seite Leistung deutlich durch verringert wird 2 - 3 Mal langsamer während, aktiviert ist. Es wird nur für bestimmte Seite und aktiven Sitzung relevant sein. Aus diesem Grund sollte dies nur selten verwendet werden und nur, wenn aktiv anderweitig mit unserem Supportteam.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Aktivieren Sie das Feature Microsoft Support-Stufe

1. Öffnen Sie das Seite Diagnose-Tool.
2. Drücken Sie auf der Tastatur l ALT, UMSCHALT-. Dadurch wird das **Aktivieren der Unterstützung der Protokollierung**angezeigt. 
3. Aktivieren Sie das Kontrollkästchen, und klicken Sie dann auf **Starten** , um die Seite und zum Generieren von ausführliche Protokollierung für den Support zur Analyse.<br/>![Support-Option aktiviert](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Wichtige Elemente für diese ist die CorrelationID, wie das Supportteam Sie danach diese Nummer verwenden, um die erforderlichen Informationen zu extrahieren. Kopieren Sie die CorrelationID (am oberen Rand der Seite-Diagnosetool) und Bereitstellen Sie, die zur Unterstützung von, wie sie die erforderliche arbeiten, ohne die vollständige-ID nicht möglich
    
## <a name="related-topics"></a>Verwandte Themen

[Optimieren der Leistung von SharePoint Online](tune-sharepoint-online-performance.md)

[Optimieren der Leistung von Office 365](tune-office-365-performance.md)

[Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)
