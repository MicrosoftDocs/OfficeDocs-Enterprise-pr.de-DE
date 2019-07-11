---
title: Verwenden des Seiten Diagnosetools für SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
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
description: Verwenden Sie das Seiten Diagnosetool für SharePoint, um die klassischen Seiten anhand der empfohlenen bewährten Methoden für SharePoint Online zu analysieren.
ms.openlocfilehash: f61d680ab4470429436cd0bb88925c2f1fc63323
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616798"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Verwenden des Seiten Diagnosetools für SharePoint Online

In diesem Artikel wird beschrieben, wie Sie mit dem Seiten Diagnosetool Ihre klassischen Veröffentlichungsseiten und Seiten auf klassischen Teamwebsites anhand einer Teilmenge der empfohlenen Methoden in **SharePoint Online**analysieren können. 
  
Team Websites, für die die Veröffentlichung nicht aktiviert ist, können nicht die CDNs verwenden, aber alle verbleibenden Regeln sind anwendbar. Durch die Veröffentlichung wird ein zusätzlicher Overhead verursacht, sodass die Veröffentlichung nicht aktiviert wird, sondern nur, um die CDN-Funktionalität zu erhalten, da sich dies negativ auf die Seitenladezeiten auswirkt.

**Beachten Sie, dass v 1.05 freigegeben wurde, damit Sie die Erweiterung aktualisieren können, wenn Sie Sie bereits installiert haben**. Wenn Sie sich nicht sicher sind, welche Version Sie haben, klicken Sie auf den Link "Info", um ihn zu überprüfen.
  
> [!IMPORTANT]
> Das Seiten Diagnosetool wird nicht für Dokumentbibliotheken oder System Seiten ausgeführt, da das Tool zum Überprüfen von SharePoint-Website Seiten entwickelt wurde. Eine *AllItems. aspx* -Seite ist eine System Seite. Wenn Sie versuchen, das Tool auf einer System Seite auszuführen, wird eine Meldung angezeigt, die besagt, dass diese Anwendung nur auf SharePoint-Seiten ausgeführt werden sollte. <br/> ![Muss auf einer SharePoint-Seite ausgeführt werden](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>Dies ist kein Fehler im Tool, da es keinen Wert für die Bewertung von Bibliotheken oder System Seiten gibt. Navigieren Sie zu einer nicht-systemeigenen SharePoint-Seite, um das Tool zu verwenden. Wenn dies auf einer SharePoint-Seite auftritt, überprüfen Sie bitte das Master Page, da Kunden gesehen haben, dass die SharePoint-Metatags entfernt werden und die Seite keine SharePoint-Seite mehr ist. Wenn Sie Feedback zum Tool geben möchten, klicken Sie auf die Registerkarte Info, und begeben Sie sich auf den [Link Feedback](https://go.microsoft.com/fwlink/?linkid=874109). 
  
## <a name="install-the-page-diagnostic-tool"></a>Installieren des Seiten Diagnosetools

> [!IMPORTANT]
> Microsoft liest nicht die Daten oder Websites, die Sie besuchen, und wir erfassen keine persönlichen Informationen, Website-oder Download Informationen mit diesem Tool. Die einzigen vom Tool protokollierten Informationen sind der Mandantenname, die Regelanzahl und die Angabe, ob die Option zur Protokollierung der Unterstützung bei der Ausführung des Tools verwendet wurde. Diese Informationen sollen von Microsoft analysiert werden, welche Herausforderungen von unseren Kunden auftreten, und um sicherzustellen, dass die Protokollierungsfunktion für Unterstützung nicht missbraucht wird.

1. Öffnen Sie mithilfe eines Chrome-Browsers den [Link zum Tool](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) direkt, oder öffnen Sie die Suche im [Chrome-Browser](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) -Webstore, und installieren Sie die Browser Erweiterung. Lesen Sie die Datenschutzrichtlinie für Benutzer, die auf der Seite Beschreibung im Store bereitgestellt wird. Wenn Sie das Tool Ihrem Browser hinzufügen, wird der folgende Berechtigungshinweis angezeigt.<br/>![Chrome Store-Berechtigungen](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Dieser Hinweis ist vorhanden, da eine Seite möglicherweise Inhalte von Speicherorten außerhalb von SharePoint enthält, abhängig von den Webparts und Anpassungen auf der Seite. Dies bedeutet, dass das Tool die Anforderungen und Antworten liest, wenn auf die Schaltfläche Start geklickt wird und nur für die aktive SharePoint-Registerkarte, auf der das Tool läuft. Diese Informationen werden vom Webbrowser lokal erfasst und stehen Ihnen über den Link nach JSON exportieren im Tool zur Verfügung. **Die Informationen werden nicht an Microsoft gesendet oder von Microsoft erfasst.** (Das Tool respektiert die Datenschutzrichtlinie von Microsoft, die [hier](https://go.microsoft.com/fwlink/p/?linkid=857875)zugänglich ist.)<br/><br/>Die "Export to JSON"-Funktionalität im Tool ist auch der Grund, warum die Berechtigung "Downloads verwalten" erforderlich ist. Beachten Sie die Datenschutzrichtlinien Ihres Unternehmens, bevor Sie die JSON-Datei außerhalb Ihrer Organisation freigeben, da die Ergebnisse URLs enthalten und als PII (personenbezogene Informationen) klassifiziert werden können.
    
2. (Dies ist optional) Wenn Sie das Tool im Inkognito-Modus von Chrome verwenden möchten, navigieren Sie zur Erweiterung, und klicken Sie auf **in Incognito zulassen**.
    
3. Navigieren Sie zur Seite SharePoint Classic Publishing auf SharePoint Online, die Sie überprüfen möchten. Wir haben für "verzögertes Laden" von Elementen auf Seiten zugelassen; Das **Tool wird daher nicht automatisch angehalten**. Wenn Sie die Sammlung beenden möchten, können Sie auf **Beenden**klicken. (Dies ist beabsichtigt, um alle Szenarien für die Seitenauslastung zu erfüllen.) Bevor Sie auf **Beenden**klicken, stellen Sie sicher, dass die Netzwerk Ablaufverfolgungsdaten abgeschlossen sind. Andernfalls erfolgt eine partielle Ablaufverfolgung. Darüber hinaus ist das Tool eine Browser Erweiterung, und das Öffnen mehrerer Registerkarten oder Fenster lässt nur eine aktive Instanz des Tools gleichzeitig ausführen. Dies ist eine Einschränkung der Erweiterungen im Browser. 
  
4. Klicken Sie auf das Erweiterungs Logo ![Seiten Diagnose für SharePoint-Logo](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) zum Laden des Tools wird das folgende Erweiterungs-Popupfenster angezeigt:<br/> ![Popup für Seiten Diagnosetool](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Start-und Stoppvorgänge befolgten das grundlegende Konzept, wenn Sie auf Start klicken, wird die Seite neu laden und die Sammlung beginnt.

Lesen Sie die folgenden Abschnitte, um mehr über die im Tool bereitgestellten Informationen zu erfahren.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Was im Seiten Diagnosetool angezeigt wird
    
1. Der **Info** -Link enthält allgemeine Anleitungen und Details zum Tool, einschließlich eines Links zu diesem Artikel. Es enthält auch einen direkten Link zu SharePoint-Leistungsempfehlungen, eine Drittanbieter Benachrichtigung und eine Option, um Feedback zum Tool zu geben. 
    
2. Die **Korrelations-ID, SPRequestDuration, SPIISLatency**, **Seitenladezeit**und **URL** -Details sind Informationszwecken und können für einige Zwecke verwendet werden. 
    
  - **CorrelationId** ist ein wichtiges Element beim Arbeiten mit den Microsoft-Support Teams, da es Ihnen ermöglicht, zusätzliche Diagnosedaten zu ziehen. 
    
  - **SPRequestDuration** ist die Serverzeit, die zum Verarbeiten der Seite verwendet wird. Wenn diese Zeit lang ist, bedeutet dies nicht zwangsläufig, dass der Server schlecht ausgeführt wurde, sondern auch die Anzahl der Anrufe und die Last, die von der Seite an den Server gesendet wurden, beispielsweise die strukturelle Navigation, große Bilder, viele API-Aufrufe, die zu längerer Serverzeit beitragen können. . 
    
  - **SPIISLatency** ist die Zeit in Millisekunden, die im Front-End-Server des Webs übernommen wird, wenn die Anforderung zum Laden der Seite empfangen wird. Dies ist ein Indikator für die Wartezeit zum Starten der Verarbeitung der Seite und beinhaltet nicht die Zeit, die für die Antwort der Webanwendung benötigt wird. 
    
  - Bei der **Seitenladezeit** handelt es sich um die Zeit, die von der Seite von der Zeit der Anforderung bis zu dem Zeitpunkt, an dem die Antwort empfangen und vom Browser gelesen wurde, aufgezeichnet wurde. Jeder zusätzliche Zeitaufwand wird durch die Leistung des Computers und die Zeit beeinträchtigt, die der Browser zum Laden benötigt. 
    
  - Die **URL** (Uniform Resource Locator) ist die Webadresse der aktuellen Seite. 
    
3. Auf der [Registerkarte **Diagnose** ](#how-to-use-the-diagnostic-tab) werden die Regeln aufgelistet, und wenn eines davon mit einem roten ![Kreuz](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)markiert ist, werden auf der Seite Probleme identifiziert.<br/>Jede Regel hat ihren eigenen Link "Weitere Informationen", auf den Sie klicken, wenn ein Element rot ist. Damit gelangen Sie zu den Details hinter dieser Regel und zur Behebung des Problems.<br/>![Diagnose: rot-Regel öffnen](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Auf der [Registerkarte **Netzwerkablaufverfolgung** ](#how-to-use-the-network-trace-tab) finden Sie Details zu Seiten Erstellungsanforderungen und-Antworten.

## <a name="how-to-use-the-diagnostic-tab"></a>Verwenden der Registerkarte "Diagnose"

1. **Überprüfen der Ausführung als Standard Benutzer**  Das Überprüfen der Seitenleistung sollte nicht ausgeführt werden, wenn Sie als Dienstkonto, Administrator oder Websitesammlungsadministrator oder ein Konto mit erhöhten Rechten angemeldet sind. Zusätzliche Skripts und Funktionen werden speziell für diese Kontentypen geladen, sodass die Ergebnisse keine echte Darstellung der Seitenleistung darstellen.
    
2. **Überprüfen von Anforderungen an SharePoint**  Die Menge an Daten und Anforderungen, die an den Server gesendet werden, sollte limitiert sein, da eine überladene Seite eine schlechte Leistung verursacht. Mit dieser Überprüfung wird die Anzahl der Anforderungen überprüft, die an SharePoint gestellt werden, und es wird empfohlen, dass die Anforderungen 6 Anforderungen überschreiten. Die meisten Anforderungen sollten zwischengespeichert werden und daher nicht für jede Seitenauslastung aufgerufen werden. Der Cache sollte für mindestens 15 Minuten eingerichtet und verwendet werden, um die Anzahl der Aufrufe einer Seite durch jeden einzelnen Benutzer zu reduzieren. Dies ist ein häufiges Problem, und in den meisten Fällen werden Daten täglich nur geändert, aber die Seite überprüft und holt Daten jedes Mal für jede Seite für jeden Benutzer, die häufig unnötig ist.
    
3. **Überprüfen der Verwendung von CDNs**  Inhalts Übermittlungs Netzwerke (Content Delivery Networks, CDNs) wurden von Microsoft bereitgestellt, und die hier erwähnten sind die SharePoint Online Inhalts Zustellungs Netzwerke. Es gibt mehrere Typen sowie verschiedene CDN-Dienste wie SharePoint CDNs und then CDNs in Azure. [Verwenden Sie die folgenden Anleitungen](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Überprüfen auf große Bildgrößen**  Bilder sollten für das Internet optimiert werden, indem Sie bessere Webtypen wie PNG verwenden. Bildwiedergaben sollten ebenfalls verwendet werden und sind in SharePoint direkt verfügbar. Bilder/Bildwiedergaben, die größer als 100KB sind, werden als nicht optimiert für das Internet hervorgehoben. [Verwenden Sie die folgenden Anleitungen für die Optimierung von Bildern](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Überprüfen der Struktur Navigation**  Die strukturelle Navigation wurde ursprünglich für die lokale Verwendung in SharePoint entwickelt, in der der Objektcache verwendet werden konnte. Die strukturelle Navigation wird für die Verwendung in SharePoint Online nicht empfohlen und sollte in die verwaltete Navigation oder einen benutzerdefinierten Anbieter geändert werden. [Verwenden Sie die folgende Anleitung zur Optimierung der Navigation.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Suchen nach CBQ Webpart** (CBQ-Inhalt nach Abfrage WebPart)  Das Webpart für Inhaltsabfragen generiert eine hohe SQL-Last, wenn es alle Elemente in der Abfrage für jede einzelne Seitenlast für jeden Benutzer durchläuft. Im Gegensatz zu einer lokalen Installation steht kein Cache zur Verfügung, um die Anzahl der Abfragen zu begrenzen, die zum Auffüllen dieses Webpart benötigt werden. CBQ führt zu einer langsamen Leistung und wirkt sich auf die Gesamt Seitenleistung aus, weshalb Sie nicht verwendet werden sollte. Verwenden Sie das Inhaltssuche-Webpart (CSWP) als Ersatz für das Webpart für Inhaltsabfragen. [Verwenden Sie den folgenden Leitfaden im Zusammenhang mit der Inhaltssuche-Webpart](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>Verwenden der Registerkarte "Netzwerkablaufverfolgung"
    
Die Registerkarte **Netzwerkablaufverfolgung** enthält detaillierte Informationen zu den Anforderungen zum Erstellen der Seite sowie den empfangenen Antworten. 

1. **Suchen Sie nach Element Ladezeiten, die als rot gekennzeichnet**sind. Die Leistung der einzelnen Anforderungen und Antworten wird basierend auf ihren Auswirkungen auf die Gesamtleistung der Seite wie folgt farblich codiert:
- Grün: \< 500M
- Gelb: 500-1000ms
- Rot: \> 1000ms
<br/>![Netzwerkablaufverfolgung](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/> Im oben gezeigten Bild bezieht sich das rote Element auf die Standardseite. Es wird immer rot angezeigt, es sei denn, \< die Seite wird in 1000ms (weniger als 1 Sekunde) geladen.

2. **Laden der Test Element Zeiten**. In einigen Fällen wird kein Zeit-oder Farbindikator angezeigt, da die Elemente bereits vom Browser zwischengespeichert wurden. Um dies ordnungsgemäß zu testen, öffnen Sie die Seite, leeren Sie den Browsercache, und klicken Sie dann auf **starten** , um eine "kalte" Seitenlast zu erzwingen und eine echte Reflektion der anfänglichen Seitenlast zu sein. Dies sollte dann mit der "warmen" Seiten Lade verglichen werden, da dies auch dazu beiträgt, zu ermitteln, welche Elemente auf der Seite zwischengespeichert werden. 
    
3. **Freigeben relevanter Details für andere Personen, die bei der Untersuchung von Problemen behilflich sein können** Um die im Tool bereitgestellten Details oder Informationen für Ihre Entwickler oder eine Person mit technischem Support freizugeben, klicken Sie auf in **JSON exportieren** (siehe Abbildung oben). Damit können Sie die Ergebnisse herunterladen, die mit einem JSON-Dateiviewer angezeigt werden.

> [!IMPORTANT]
> Diese Ergebnisse enthalten URLs, die als PII klassifiziert werden können (personenbezogene Informationen). Stellen Sie sicher, dass Sie die Richtlinien Ihrer Organisation befolgen, bevor Sie diese Informationen verteilen. 

## <a name="engaging-with-microsoft-support"></a>Einbindung des Microsoft-Supports
   
Wir haben ein **Feature von Microsoft Support Level** aufgenommen, das nur verwendet werden sollte, wenn Sie direkt an einem Supportfall arbeiten, um Leistung zu erzielen. Die Verwendung dieser Funktion bietet keinen Nutzen für Sie, wenn Sie ohne unser Support Team verwendet wird. Es wird in der Tat dazu führen, dass die Seite deutlich langsamer ausgeführt wird und die fortgesetzte Verwendung des Features als "Missbrauch" des Diensts betrachtet werden kann. Es gibt keine zusätzlichen Informationen bei Verwendung dieses Features im Tool, da die zusätzlichen Informationen zur Protokollierung im Dienst hinzugefügt werden. 

Es wird keine Änderung angezeigt, außer dass Sie benachrichtigt werden, dass Sie sie aktiviert haben und die Leistung der Seite erheblich beeinträchtigt wird, während die Leistung um 2-3 mal langsamer ist, während diese aktiviert ist. Er ist nur für die jeweilige Seite und die aktive Sitzung relevant. Aus diesem Grund sollte dies sparsam und nur dann verwendet werden, wenn Sie sich aktiv mit unserem Support Team beschäftigen.

### <a name="to-enable-the-microsoft-support-level-feature"></a>So aktivieren Sie das Feature "Microsoft Support Level"

1. Öffnen Sie das Seiten Diagnosetool.
2. Drücken Sie auf der Tastatur ALT-UMSCHALT-L. Dadurch wird die **Protokollierung der Supportebene aktivieren**angezeigt. 
3. Aktivieren Sie das Kontrollkästchen, und klicken Sie dann auf **starten** , um die Seite neu zu laden und die ausführliche Protokollierung zur Unterstützung der Analyse zu generieren.<br/>![Support Option aktiviert](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Ein wichtiges Element hierfür ist das CorrelationId, da das Support Team dann diese Nummer verwendet, um die erforderlichen Informationen zu extrahieren. Kopieren Sie die CorrelationId (oben im Seiten Diagnosetool), und stellen Sie diese zur Unterstützung bereit, da Sie die erforderliche Arbeit ohne die vollständige ID nicht ausführen können.
    
## <a name="related-topics"></a>Verwandte Themen

[Optimieren der Leistung von SharePoint Online](tune-sharepoint-online-performance.md)

[Optimieren der Leistung von Office 365](tune-office-365-performance.md)

[Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)
