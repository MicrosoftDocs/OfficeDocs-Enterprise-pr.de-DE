---
title: Verwenden des Seiten Diagnosetools für SharePoint Online
ms.author: krowley
author: kccross
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
description: Verwenden Sie das Tool Seiten Diagnose für SharePoint, um Ihre klassischen Seiten anhand der empfohlenen bewährten Methoden für SharePoint Online zu analysieren.
ms.openlocfilehash: a188b5dbe52a92cd536ef7145534288345b74c22
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069511"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>Verwenden des Seiten Diagnosetools für SharePoint Online

In diesem Artikel wird beschrieben, wie Sie mit dem Seiten Diagnosetool Ihre klassischen Veröffentlichungsseiten und Seiten auf klassischen Teamwebsites anhand einer Teilmenge der empfohlenen Methoden in **SharePoint Online**analysieren können. 
  
Team Websites, für die die Veröffentlichung nicht aktiviert ist, können nicht CDNs verwenden, aber alle verbleibenden Regeln gelten. Bei der Veröffentlichung wird zusätzlicher Overhead hinzugefügt, sodass die Veröffentlichung nicht nur zum Abrufen der CDN-Funktionalität aktiviert wird, da sich dies negativ auf die Seitenladezeiten auswirkt.

**Beachten Sie, dass v 1.05 veröffentlicht wurde, damit Sie Ihre Erweiterung aktualisieren können, wenn Sie Sie bereits installiert haben**. Wenn Sie unsicher sind, welche Version Sie haben, klicken Sie auf den Link "Info", um Sie zu überprüfen.
  
> [!IMPORTANT]
> Das Seiten Diagnosetool wird nicht für Dokumentbibliotheken oder System Seiten ausgeführt, da das Tool zum Überarbeiten von SharePoint-Website Seiten entworfen wurde. Eine *AllItems. aspx* -Seite ist eine System Seite. Wenn Sie versuchen, das Tool auf einer System Seite auszuführen, erhalten Sie eine Meldung, die lautet: "diese Anwendung sollte nur auf SharePoint-Seiten ausgeführt werden." <br/> ![Muss auf einer SharePoint-Seite ausgeführt werden](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>Dies ist kein Fehler im Tool, da es bei der Bewertung von Bibliotheken oder System Seiten keinen Wert gibt. Navigieren Sie zu einer nicht-System-SharePoint-Seite, um das Tool zu verwenden. Wenn dies auf einer SharePoint-Seite auftritt, überprüfen Sie die Master Page, da Kunden die SharePoint-Metatags entfernt haben und die Seite dann nicht mehr eine SharePoint-Seite ist. Wenn Sie Feedback zu dem Tool geben möchten, klicken Sie auf die Registerkarte Info, und folgen Sie dem [Link Feedback](https://go.microsoft.com/fwlink/?linkid=874109)senden. 
  
## <a name="install-the-page-diagnostic-tool"></a>Installieren des Seiten Diagnosetools

> [!IMPORTANT]
> Microsoft liest die von Ihnen besuchten Daten oder Websites nicht, und wir erfassen keine persönlichen Informationen, Website-oder Download Informationen mit diesem Tool. Die einzigen vom Tool protokollierten Informationen sind der Mandantenname, die Regelanzahl und die Angabe, ob die Support Protokollierungsoption beim Ausführen des Tools verwendet wurde. Diese Informationen sind für Microsoft zu analysieren, welche Herausforderungen von unseren Kunden erlebt werden und um sicherzustellen, dass die Support Protokollierungsfunktion nicht missbraucht wird.

1. Öffnen Sie mithilfe eines Chrome-Browsers den [Link zum Tool](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) direkt, oder öffnen Sie die Suche im [Chrome-Browser Webstore](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) , und installieren Sie die Browser Erweiterung. Lesen Sie die auf der Seite Beschreibung im Store bereitgestellte Benutzerdaten Schutzrichtlinie. Wenn Sie das Tool zu Ihrem Browser hinzufügen, wird der folgende Berechtigungshinweis angezeigt.<br/>![Chrome Store-Berechtigungen](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   Dieser Hinweis ist vorhanden, da eine Seite Inhalte von Orten außerhalb von SharePoint abhängig von den Webparts und Anpassungen auf der Seite enthalten kann. Dies bedeutet, dass das Tool die Anforderungen und Antworten liest, wenn auf die Schaltfläche Start geklickt wird, und nur für die aktive SharePoint-Registerkarte, auf der das Tool läuft. Diese Informationen werden lokal vom Webbrowser erfasst und stehen Ihnen über den Link in JSON exportieren im Tool zur Verfügung. **Die Informationen werden nicht von Microsoft gesendet oder erfasst.** (Das Tool respektiert die [hier](https://go.microsoft.com/fwlink/p/?linkid=857875)zugängliche Microsoft-Datenschutzrichtlinie.)<br/><br/>Die "nach JSON exportieren"-Funktionalität im Tool ist auch der Grund, warum die Berechtigung "Ihre Downloads verwalten" erforderlich ist. Befolgen Sie die Datenschutzrichtlinien Ihres Unternehmens, bevor Sie die JSON-Datei außerhalb Ihrer Organisation freigeben, da die Ergebnisse URLs enthalten und als PII klassifiziert werden können (personenbezogene Daten).
    
2. (Optional) Wenn Sie das Tool im Chrome Incognito-Modus verwenden möchten, navigieren Sie zur Erweiterung, und klicken Sie auf **in inkognito zulassen**.
    
3. Navigieren Sie zur Seite "klassische Veröffentlichung von SharePoint Online", die Sie überarbeiten möchten. Wir haben "verzögertes Laden" von Elementen auf Seiten zugelassen; Daher wird das **Tool nicht automatisch angehalten**. Wenn Sie die Sammlung beenden möchten, können Sie auf **Beenden**klicken. (Dies ist beabsichtigt, um alle Seiten Lade Szenarien zu berücksichtigen.) Stellen Sie vor dem Klicken auf **Beenden**sicher, dass die Netzwerk Ablaufverfolgungsdaten abgeschlossen sind. Andernfalls haben Sie eine teilweise Ablaufverfolgung. Darüber hinaus ist das Tool eine Browser Erweiterung, und das Öffnen mehrerer Registerkarten oder Fenster ermöglicht nur die gleichzeitige Ausführung einer aktiven Instanz des Tools. Dies ist eine Einschränkung der Erweiterungen im Browser. 
  
4. Klicken Sie auf das Erweiterungs Logo. ![Seiten Diagnose für SharePoint-Logo](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) um das Tool zu laden, wird das folgende Erweiterungs-Popupfenster angezeigt:<br/> ![Popup für Seiten Diagnosetool](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>Start-und Stoppvorgänge folgen dem Grundkonzept, wenn Sie auf Start klicken, wird die Seite erneut geladen, und die Sammlung beginnt.

Lesen Sie die folgenden Abschnitte, um mehr über die im Tool bereitgestellten Informationen zu erfahren.

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>Was im Tool für die Seiten Diagnose angezeigt wird
    
1. Der **Info** -Link enthält allgemeine Hinweise und Details zum Tool einschließlich eines Links zu diesem Artikel. Sie beinhaltet auch einen direkten Link zu SharePoint-Leistungsempfehlungen, eine Benachrichtigung durch einen Drittanbieter und eine Option, um Feedback zum Tool zu geben. 
    
2. Die **Korrelations-ID, SPRequestDuration, SPIISLatency**, **Seitenladezeit**und **URL** -Details sind informativ und können für einige Zwecke verwendet werden. 
    
  - **CorrelationId** ist ein wichtiges Element beim Arbeiten mit Microsoft-Support Teams, da es Ihnen ermöglicht, zusätzliche Diagnosedaten abzurufen. 
    
  - **SPRequestDuration** ist die Serverzeit, die zum Verarbeiten der Seite verwendet wird. Wenn diese Zeit lang ist, bedeutet dies nicht zwangsläufig, dass der Server schlecht ausgeführt wurde, sondern auch die Anzahl der Aufrufe und die von der Seite auf den Server geladenen Lasten widerspiegeln kann, beispielsweise strukturelle Navigation, große Bilder, viele API-Aufrufe, die zu längeren Serverzeiten beitragen können. . 
    
  - **SPIISLatency** ist die Zeit in Millisekunden, die auf dem Web-Front-End-Server verwendet wird, wenn die Anforderung zum Laden der Seite empfangen wird. Dies ist ein Indikator für die Wartezeit, um mit der Verarbeitung der Seite zu beginnen, und enthält nicht die Zeit, die für die Antwort der Webanwendung benötigt wird. 
    
  - Bei der **Seitenladezeit** handelt es sich um die Zeit, die von der Seite vom Zeitpunkt der Anforderung an die Uhrzeit aufgezeichnet wurde, zu der die Antwort vom Browser empfangen und gelesen wurde. Jeder zusätzliche Zeitpunkt wird durch die Leistung des Computers und die Ladezeit des Browsers beeinflusst. 
    
  - Die **URL** (Uniform Resource Locator) ist die Webadresse der aktuellen Seite. 
    
3. Auf der [Registerkarte **Diagnose** ](#how-to-use-the-diagnostic-tab) werden die Regeln aufgelistet, und wenn eine von Ihnen mit einem ![roten](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)Kreuz gekennzeichnet ist, werden auf der Seite Probleme identifiziert.<br/>Jede Regel hat ihren eigenen Link "Weitere Informationen", auf den Sie klicken, wenn ein Element rot ist. Dadurch gelangen Sie zu den Details hinter dieser Regel und zur Behebung des Problems.<br/>![Diagnose rot – Regel öffnen](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. Eine [Registerkarte **Netzwerkablaufverfolgung** ](#how-to-use-the-network-trace-tab) enthält Details zu Seiten Erstellungsanforderungen und-Antworten.

## <a name="how-to-use-the-diagnostic-tab"></a>Verwenden der Registerkarte "Diagnose"

1. **Überprüfen der Standard Benutzerführung**  Die Überprüfung der Seitenleistung sollte nicht durchgeführt werden, wenn Sie als Dienstkonto, Administrator oder Websitesammlungsadministrator oder ein beliebiges Konto mit erhöhten Rechten angemeldet sind. Zusätzliche Skripts und Funktionen werden speziell für diese Kontentypen geladen, sodass die Ergebnisse keine wirkliche Darstellung der Seitenleistung darstellen.
    
2. **Überprüfen von Anforderungen an SharePoint**  Die Menge an Daten und Anforderungen, die an den Server gesendet werden, sollte eingeschränkt werden, da bei einer überladenen Seite eine schlechte Leistung auftritt. Bei dieser Überprüfung wird die Anzahl der Anforderungen überprüft, die an SharePoint vorgenommen werden, und es wird empfohlen, wenn die Anforderungen 6 Anforderungen überschreiten. Die meisten Anforderungen sollten zwischengespeichert werden und daher nicht für jede Seitenauslastung aufgerufen werden. Der Cache sollte für mindestens 15 Minuten eingerichtet und verwendet werden, um die Anzahl der Aufrufe einer Seite für jeden Benutzer zu reduzieren. Dies ist ein häufiges Problem, und in den meisten Fällen werden Daten nur täglich geändert, aber die Seite prüft und ruft Daten jedes Mal für jede Seite für jeden Benutzer ab, was oft nicht erforderlich ist.
    
3. **Überprüfen der Verwendung von CDNs**  Content-Zustellungs Netzwerke (CDNs) wurden von Microsoft bereitgestellt, und die folgenden sind die SharePoint Online-Content-Zustellungs Netzwerke. Es stehen mehrere Typen sowie unterschiedliche CDN-Dienste wie SharePoint CDNs und dann CDNs in Azure zur Verfügung. [Verwenden Sie die folgenden Anweisungen](https://go.microsoft.com/fwlink/?linkid=873250).
    
4. **Auf große Bildgrößen prüfen**  Bilder sollten für Web optimiert werden, indem Sie bessere Webtypen wie PNG verwenden. Bilddarstellungen sollten ebenfalls verwendet werden und sind in SharePoint direkt verfügbar. Bilder/Bilddarstellungen, die größer als 100KB sind, werden als nicht optimiert für Web hervorgehoben. [Verwenden Sie die folgenden Anweisungen, um Bilder zu optimieren](https://go.microsoft.com/fwlink/?linkid=873251).
    
5. **Überprüfen der strukturellen Navigation**  Die strukturelle Navigation war ursprünglich für die Verwendung in SharePoint-lokal vorgesehen, in dem der Objektcache verwendet werden konnte. Die strukturelle Navigation wird nicht für die Verwendung in SharePoint Online empfohlen und sollte in die verwaltete Navigation oder einen benutzerdefinierten Anbieter geändert werden. [Verwenden Sie die folgenden Anweisungen, um die Navigation zu optimieren.](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **Nach CBQ Webpart suchen** (CBQ-Inhaltsabfrage-Webpart)  Das Webpart für Inhaltsabfragen generiert eine hohe SQL-Auslastung, wenn alle Elemente in der Abfrage für jeden seitenladevorgang für jeden Benutzer durchlaufen werden. Anders als bei einer lokalen Installation ist kein Cache verfügbar, um die Anzahl der zum Auffüllen dieses Webpart erforderlichen Abfragen zu begrenzen. Als solche cbq führt langsam und wirkt sich auf die gesamte Seite Leistung, weshalb Sie nicht verwendet werden sollte. Verwenden Sie die Inhaltssuche Webpart (Inhaltssuche) als Ersatz für die Inhaltsabfrage Webpart. [Verwenden Sie die folgenden Anweisungen im Zusammenhang mit der Inhaltssuche Webpart](https://go.microsoft.com/fwlink/?linkid=873245).

## <a name="how-to-use-the-network-trace-tab"></a>Verwenden der Registerkarte "Netzwerkablaufverfolgung"
    
Die Registerkarte **Netzwerkablaufverfolgung** enthält detaillierte Informationen zu den Anforderungen zum Erstellen der Seite sowie zu den empfangenen Antworten. 

1. **Suchen Sie nach Element Ladezeiten, die als rot gekennzeichnet**sind. Die Leistung der einzelnen Anforderungen und Antworten basiert auf den Auswirkungen auf die Gesamtleistung der Seite wie folgt:
- Grün: \< 500M
- Gelb: 500-1000ms
- Rot: \> 1000ms
<br/>![Netzwerkablaufverfolgung](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/> Im oben gezeigten Bild bezieht sich das rote Element auf die Standardseite. Es wird immer rot angezeigt, es sei denn, \< die Seite wird in 1000ms geladen (weniger als 1 Sekunde).

2. **Ladezeiten für Test Elemente**. In einigen Fällen gibt es keinen Zeit-oder Farbindikator, da die Elemente bereits vom Browser zwischengespeichert wurden. Um dies richtig zu testen, öffnen Sie die Seite, löschen Sie den Browsercache, und klicken Sie dann auf **starten** , da dies zu einer "Cold"-Seiten Lade führt und eine echte Reflexion der anfänglichen Seitenbelastung darstellt. Dieser sollte dann mit der "warmen" Seiten Lade verglichen werden, sodass auch bestimmt wird, welche Elemente auf der Seite zwischengespeichert werden. 
    
3. **Teilen Sie relevante Details mit anderen Personen, die Probleme untersuchen können**. Wenn Sie die Details oder Informationen, die im Tool bereitgestellt werden, für Ihre Entwickler oder eine technische Support Person freigeben möchten, klicken Sie auf **nach JSON exportieren** (siehe Abbildung oben). , Mit dem Sie die Ergebnisse herunterladen können, die mit einem JSON-Dateibetrachter angezeigt werden können.

> [!IMPORTANT]
> Diese Ergebnisse enthalten URLs und können als PII klassifiziert werden (personenbezogene Informationen). Stellen Sie sicher, dass Sie die Richtlinien Ihrer Organisation befolgen, bevor Sie diese Informationen verteilen. 

## <a name="engaging-with-microsoft-support"></a>Einbindung des Microsoft-Supports
   
Wir haben eine **Microsoft Support Level-Funktion** integriert, die nur verwendet werden sollte, wenn Sie direkt an einem Supportfall für die Leistung arbeiten. Wenn Sie diese Funktion verwenden, haben Sie keinen Vorteil, wenn Sie ohne unser Support-Team verwendet werden. Dadurch wird die Seite deutlich langsamer ausgeführt, und die Fortsetzung der Verwendung des Features kann als "Missbrauch" des Diensts betrachtet werden. Es gibt keine zusätzlichen Informationen, wenn Sie diese Funktion im Tool verwenden, da die zusätzlichen Informationen der Protokollierung im Dienst hinzugefügt werden. 

Es wird keine Änderung angezeigt, mit der Ausnahme, dass Sie benachrichtigt werden, dass Sie sie aktiviert haben, und die Leistung Ihrer Seite erheblich um 2-3 mal langsamer wird, während die Leistung aktiviert ist. Sie ist nur für die jeweilige Seite und die aktive Sitzung relevant. Aus diesem Grund sollte dies sparsam und nur dann verwendet werden, wenn Sie aktiv mit unserem Support Team zusammenarbeiten.

### <a name="to-enable-the-microsoft-support-level-feature"></a>So aktivieren Sie die Microsoft Support Level-Funktion

1. Öffnen Sie das Seiten Diagnosetool.
2. Drücken Sie auf der Tastatur Alt-Shift-L. Auf diese Weise wird die **Protokollierung der Supportstufe aktivieren**angezeigt. 
3. Aktivieren Sie das Kontrollkästchen, und klicken Sie dann auf **starten** , um die Seite neu zu laden und die ausführliche Protokollierung für die zu analysierenden Unterstützung zu generieren.<br/>![Aktivierte Support Option](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
Ein wichtiges Element hierfür ist die CorrelationId, da das Support Team diese Nummer dann verwendet, um die benötigten Informationen zu extrahieren. Kopieren Sie die CorrelationId (oben im Tool für die Seiten Diagnose), und stellen Sie sicher, dass Sie die erforderliche Arbeit ohne die vollständige ID nicht ausführen können.
    
## <a name="related-topics"></a>Verwandte Themen

[Optimieren der Leistung von SharePoint Online](tune-sharepoint-online-performance.md)

[Optimieren der Leistung von Office 365](tune-office-365-performance.md)

[Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)
