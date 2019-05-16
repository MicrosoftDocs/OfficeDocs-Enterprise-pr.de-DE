---
title: Bewährte Methoden für die Verwendung von Office 365 in einem langsamen Netzwerk
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
audience: End User
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
description: Wäre es nicht nett, wenn Ihre Internet Verbindung immer schnell und nie ausgefallen wäre? Vielleicht wird dieser Tag kommen. Aber in der Zwischenzeit gibt es praktische Möglichkeiten, um ein Netzwerk zu scheuen und trotzdem Ihre tägliche Arbeit zu erledigen.
ms.openlocfilehash: 479947eb2e785ddfdf77fa2715007afd41d20763
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068241"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Bewährte Methoden für die Verwendung von Office 365 in einem langsamen Netzwerk

Wäre es nicht nett, wenn Ihre Internet Verbindung immer schnell und nie ausgefallen wäre? Vielleicht wird dieser Tag kommen. Aber in der Zwischenzeit gibt es praktische Möglichkeiten, um ein Netzwerk zu scheuen und trotzdem Ihre tägliche Arbeit zu erledigen. Office 365 ist zwar ein Cloud-basierter Dienst, bietet aber auch viele Möglichkeiten, mit ihren Inhalten offline zu arbeiten und Ihre Änderungen reibungslos zu synchronisieren. Außerdem ist es manchmal effizienter, mit Inhalten offline zu arbeiten, nur weil Anwendungen schneller ausgeführt werden und die Benutzeroberfläche besser reagiert. Der Punkt ist Folgendes: Office 365 bietet Ihnen das Beste aus beiden Welten. Hier erfahren Sie, wie Sie das nutzen können. 
  
> [!TIP]
> Möchten Sie sehen, wie langsam (oder schnell) Ihre Netzwerkverbindung ist? Testen Sie den [OOKLA-Geschwindigkeitstest](https://www.speedtest.net/) oder die [Netzwerk Geschwindigkeitstest-App](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70). 
     
## <a name="why-is-my-network-so-slow"></a>Warum ist mein Netzwerk so langsam?

Obwohl Sie die Netzwerkleistung selbst nicht steuern können, hilft dies zu verstehen, was hinter den Kulissen passiert. Das Internet ist enorm komplex, aber es gibt einige Konzepte, die Ihnen helfen, die Situation besser zu verstehen. Wenn Sie die bewährten Methoden in diesem Artikel befolgen, können Sie Leistungsprobleme umgehen und die Frustration reduzieren.
  
**Wichtige Faktoren, die sich auf die Netzwerkleistung auswirken**

![Netzwerk Leistungsfaktoren](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **Bandbreite und Wartezeit** Die beiden wichtigsten Maßnahmen zur Netzwerkleistung sind Bandbreite und Wartezeit: 
  
- Bandbreite ist die Rate des Durchsatzes, die in Bits pro Sekunde gemessen wird. Größer ist besser. Bandbreite ist wie eine Wasserpfeife. Je größer die Pipe ist, desto mehr Wasser kann Sie durchsetzen.
    
- Wartezeit ist die Zeit, die für das Abrufen von Inhalten von einem Server oder Dienst zu Ihrem Gerät erforderlich ist und in Millisekunden gemessen wird. Schneller ist besser. Die Wartezeit kann durch eine Reihe von Faktoren wie geringe Bandbreite, eine Verbindung mit geringer Dichte oder Übertragungszeit verursacht werden.
    
 **Häufige Probleme** Neben Bandbreite und Latenz haben andere Probleme Auswirkungen auf die Netzwerkleistung und sind oft unvorhersehbar. Die Netzwerkleistung kann je nach Tageszeit oder physischem Standort schwanken. Das Netzwerk kann verstopft werden, wenn bestimmte Ereignisse eintreten, die die Nutzung des Internets, wie eine Naturkatastrophe oder ein großes öffentliches Ereignis, überwiegen. Die Größe und Komplexität der zu ladenden Seite sowie die Anzahl und Größe der übertragenen Dateien haben einen direkten Einfluss auf die Leistung. Eine WiFi-Verbindung kann vorübergehend abnehmen: Sie rufen beispielsweise eine umfangreiche Konferenz Besprechung mit Tausenden ab, indem Sie alle zur gleichzeitigen Tweet anfordern. 
  
 **Überlegungen für ein Satellitennetzwerk** Ein Satellitennetzwerk ist nützlich, wenn ein terrestrisches Netzwerk nicht möglich ist, beispielsweise das Backcountry, ein Kreuzfahrtschiff oder ein Remote-Wissenschaftsgebiet. Diese Netzwerke basieren auf Satelliten, die in einer geosynchronen Umlaufbahn 22.000 Meilen oberhalb des Äquators positioniert sind. Eine Übertragung ist jedoch tatsächlich 90.000 Meilen lang und daher hat ein Satellitennetzwerk eine langsamere Latenz (500 ms oder mehr) als ein terrestrisches Netzwerk (20 bis 50ms). Unter den bestmöglichen Bedingungen werden Sie diese Wartezeit möglicherweise nicht bemerken, aber für das Herunterladen von umfangreichen Dateien, Streaming-Videos und spielen, werden Sie wahrscheinlich. Ein weiteres Problem ist "Rain Fade", bei dem schweres Wetter, wie Gewitter und Schneestürme, die Satellitenübertragung vorübergehend unterbrechen kann.
  
## <a name="are-you-sure-its-the-network"></a>Sind Sie sicher, dass es das Netzwerk ist?

Wenn Leistungsprobleme auftreten, stellen Sie zunächst sicher, dass Ihr Gerät nicht die eigentliche Ursache des Problems ist. Es gibt zwei Möglichkeiten, die zu einer großen Verbesserung führen können:
  
- Stellen Sie sicher, dass Ihr Gerät gut läuft und es auf Ihrem Computer keine Schadsoftware gibt.
    
- Wenn möglich, kaufen Sie mehr Speicher. Das Hinzufügen von Arbeitsspeicher ist die einfachste und oft effektivste Methode zur Verbesserung der Leistung auf Ihrem Gerät. Es ist besonders hilfreich beim Arbeiten mit umfangreichen Dateien und Videos.
    
Weitere Informationen finden Sie unter [Windows-Leistung und-Wartung](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) und [Tipps zur Verbesserung der PC-Leistung in Windows 10](https://support.microsoft.com/en-za/help/4002019/windows-10-improve-pc-performance).

## <a name="best-practices-for-using-your-browser"></a>Bewährte Methoden für die Verwendung des Browsers

Ihr Browser ist Ihr Gateway zu Office 365, sodass sich dies auf die Leistung auswirken kann, insbesondere mit der Zeit, die zum Laden einer Seite erforderlich ist, und wie oft Sie eine Roundtrip zum Office 365-Dienst ausführen. 
  
 **Allgemeine Browser**
  
Hier einige Vorschläge für Browser im allgemeinen:
  
- Deaktivieren Sie Browser-Add-ons, die sich auf die Leistung auswirken oder die Sie nicht wirklich benötigen.
    
- Vergrößern Sie die Cachegröße für Ihre temporären Internetdateien.
    
-  Nachdem Sie sich bei Ihrem Arbeits-oder Schulkonto angemeldet haben, lassen Sie das Browserfenster den ganzen Tag lang geöffnet. Sie können andere Registerkarten und Fenster öffnen, ohne sich erneut anzumelden. Wenn Sie sich bei einem anderen Konto anmelden müssen, verwenden Sie privates Browsen. 
    
- Nachdem jede Seite heruntergeladen und geöffnet wurde, lassen Sie Sie über Registerkarten geöffnet. Es ist einfach, zwischen Registerkarten zu navigieren und die Seite später am Tag zu verwenden. Aktualisieren Sie eine Seite nur, wenn Sie auf dieser Seite die neuesten Daten benötigen.
    
- Wenn für das Öffnen einer Seite zu lange dauert, beenden Sie den Seiten Download (drücken Sie ESC), und aktualisieren Sie dann die Seite (drücken Sie F5). 
    
-  Reduzieren Sie nach Möglichkeit Roundtrips zu Office 365. Anstatt Listen oder Bibliotheken durchblättern zu müssen, verwenden Sie beispielsweise die Suche, um Dateien in einer umfangreichen Bibliothek zu suchen und in einer Liste zu filtern, um direkt zu den gewünschten Ergebnissen zu gelangen. Sie können auch Ansichten erstellen, die die Ladezeit der Seite minimieren. Weitere Informationen finden Sie unter [Manage umfangreicher Listen und Bibliotheken in Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).
    
- Wenn die Videoleistung schlecht ist, können Sie das Video möglicherweise herunterladen und auf Ihrem Gerät ansehen. Möglicherweise ist ein Download Link verfügbar, oder Sie können mit der rechten Maustaste auf den Link Video klicken und **Ziel speichern**unter auswählen. 
    
 **Browser spezifisch**
  
Hier einige Vorschläge für Ihren spezifischen Browser:
  
- **Internet Explorer** Aktualisieren Sie auf Internet Explorer, Version 11 oder höher, um erhebliche Leistungsverbesserungen gegenüber früheren Versionen zu erzielen. Weitere Informationen finden Sie unter [Troubleshooting Guide for Internet Explorer](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
    
- **Firefox** Weitere Informationen finden Sie unter [Firefox ist langsam oder funktioniert nicht](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging)mehr.
    
- **Safari** Weitere Informationen finden Sie unter [Apple-Safari](https://www.apple.com/safari/).
    
- **Chrome** Weitere Informationen finden Sie in der [Chrome-Hilfe](https://support.google.com/chrome/?hl=en).
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Bewährte Methoden für die Verwendung von Outlook und Outlook Web App

Lesen, schreiben und organisieren von e-Mails ist ein wichtiger Teil des Alltags. Sowohl Outlook als auch Outlook Web App (OWA) bieten Offline-Unterstützung. Eine andere nützliche Alternative ist das Verwenden einer e-Mail-App auf Ihrem Smartphone. Verwenden Sie die folgenden Optionen, die Ihren Anforderungen am besten entsprechen:
  
- Führen Sie ein Upgrade auf die neueste Version von Outlook durch, um erhebliche Leistungsverbesserungen gegenüber früheren Versionen zu erzielen. 
    
-  Mit Outlook Web App können Sie Offline Nachrichten, Kontakte und Kalenderereignisse erstellen, die hochgeladen werden, wenn OWA als nächstes in der Lage ist, eine Verbindung mit Office 365 herzustellen. Weitere Informationen zum Einrichten und Verwenden von OWA im Offlinemodus finden Sie unter [Offline Verwenden von Outlook Web App](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).
    
- In Outlook können Sie im Cache-Modus arbeiten, in dem Sie immer dann automatisch eine Verbindung herstellt. Sie können Outlook Ihr gesamtes Postfach oder nur einen Teil davon herunterladen. Weitere Informationen finden Sie unter [Aktivieren des Exchange-Cache-Modus](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) und [Offline arbeiten in Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633). 
    
- Outlook bietet auch einen Offlinemodus. Um dies zu verwenden, müssen Sie zunächst den zwischengespeicherten Modus einrichten, damit die Informationen Ihres Kontos auf Ihren Computer kopiert werden. Im Offlinemodus versucht Outlook, eine Verbindung mithilfe der Einstellungen für senden und empfangen herzustellen, oder wenn Sie es manuell für die Online Arbeit festlegen. Weitere Informationen finden Sie unter [Offline arbeiten, um datenverbindungsgebühren zu vermeiden](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [senden-und Empfangseinstellungen zu ändern, wenn Sie offline arbeiten](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a), und [Wechseln von Offline arbeiten zu Online](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9). 
    
- Wenn Sie über ein Smartphone verfügen, können Sie es verwenden, um Ihre e-Mails und Kalender über das Netzwerk Ihrer Telefongesellschaft zu selektieren. 
    
> [!NOTE]
> Hier finden Sie einige Anleitungen zur Verwendung von Outlook oder OWA. Wenn der Speicherplatz auf dem Gerät kein Problem ist, verfügt Outlook über einen vollständigen Satz von Features, die für Sie am besten geeignet sind. Wenn auf Ihrem Gerät Speicherplatz ein Problem ist, erwägen Sie die Verwendung von OWA mit einer Teilmenge von Features, aber auch am besten in einer Online-Situation. Natürlich können Sie entweder verwenden, weil Sie gut zusammenarbeiten. 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>Bewährte Methoden für die Verwendung von OneDrive for Business

OneDrive for Business wurde von Grund auf entwickelt, um Online und offline mit Ihren Dateien zu arbeiten. Sobald Sie es eingerichtet haben, erfolgt die Synchronisierung der Änderungen automatisch und zuverlässig, unabhängig davon, wo und wann immer Sie Sie vornehmen. Wenn das Netzwerk langsam ist, können Sie mit der Offline Version der Dateien arbeiten.
  
Die OneDrive for Business-Synchronisierungs-APP wird mit einem SharePoint Online-und Office 365 Business-Abonnement geliefert, oder Sie können die OneDrive for Business Sync-App kostenlos [herunterladen](https://support.microsoft.com/kb/2903984) . Diese APP ist auch schneller als die Verwendung der Befehle **Öffnen im Explorer** oder **hochladen** . Weitere Informationen finden Sie unter [Einrichten des Computers für die Synchronisierung Ihrer OneDrive für Geschäftsdateien in Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).
  
Hier finden Sie einige zusätzliche Anleitungen für die Verwendung der OneDrive for Business-Synchronisierungs-App:
  
- Wenn Sie eine umfangreiche Bibliothek zum ersten Mal synchronisieren, starten Sie die Synchronisierung außerhalb der Öffnungszeiten, beispielsweise über Nacht. 
    
- Sie können das Feature zum [Beenden der Synchronisierung einer Bibliothek mit der OneDrive for Business-App](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) verwenden, um die Synchronisierung von Updates vorübergehend zu beenden. Verwenden Sie dieses Feature jedoch für kurze Zeiträume (beispielsweise ein paar Stunden), um eine hohe Anzahl von Updates zu vermeiden und das Risiko von Zusammenführungskonflikten zu minimieren, wenn mehrere Personen an demselben Dokument arbeiten. 
  
## <a name="best-practices-for-using-onenote"></a>Bewährte Methoden für die Verwendung von OneNote

Jede SharePoint-Teamwebsite verfügt über ein integriertes OneNote-Notizbuch, und Sie können ganz einfach Ihre eigenen erstellen. OneNote ist eine hervorragende Möglichkeit, zeitgerechte Informationen zu sammeln, die Sie täglich benötigen, um Aufgaben zu erledigen. Viele Teams verwenden OneNote beispielsweise als Sammelpunkt für wöchentliche Besprechungen, Projektnotizen, Ideen, Pläne und Statusberichte. Sie können diese unterschiedlichen Informationen mithilfe von Seiten, Abschnitten und Registerkarten ordentlich organisieren.
  
Die Schönheit von OneNote besteht darin, dass Sie von praktisch jedem Gerät, ob Desktop, Laptop, Tablet oder Smartphone, auf die Inhalte zugreifen können. Und Sie müssen sich keine Gedanken über das Speichern oder synchronisieren machen, da OneNote dies für Sie erledigt. 
  
Weitere Informationen finden Sie unter [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Bewährte Methoden für die Verwendung von Skype for Business und lync Online

Im folgenden finden Sie allgemeine Richtlinien für die Verwendung von Skype for Business oder lync online bei einem langsamen Netzwerk:

- Verwenden Sie Sofortnachrichten, wenn Sie können, weil es gut funktioniert in einem langsamen Netzwerk.
    
- Vermeiden Sie Telefonanrufe über ein VPN (virtuelles privates Netzwerk) oder RAS-Verbindungen.
    
- Stellen Sie sicher, dass Ihr Audiogerät genehmigt wurde. Weitere Informationen finden Sie unter [Telefone und Geräte, die für Microsoft lync qualifiziert](https://docs.microsoft.com/skypeforbusiness/lync-cert/ip-phones)sind.
    
-  Wenn Sie PowerPoint in einer Online Präsentation verwenden, verringern Sie die Größe und Komplexität der Folien. Weitere Informationen finden Sie unter [Tipps zur Verbesserung der Leistung Ihrer Präsentation](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).
            
-  Die Video Leistung hängt stark von der Netzwerkleistung ab. Vermeiden Sie die Verwendung von Video, wenn Ihr Netzwerk langsam ist. 

Weitere Informationen finden Sie unter [schlechte Qualität von Audiodaten oder Videos in lync Online](https://support.microsoft.com/kb/2386655)oder [Behandlung von Verbindungsproblemen in Skype for Business](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).
  
## <a name="best-practices-for-using-sharepoint-lists"></a>Bewährte Methoden für die Verwendung von SharePoint-Listen

Das Arbeiten mit Offline Listendaten zum "Scrubben", analysieren oder melden von Daten stellt eine großartige Möglichkeit dar, um die Auswirkungen eines langsamen Netzwerks zu minimieren. Sie können die meisten Listen von Microsoft Access 2019 und Microsoft Access 2016 lesen und schreiben, indem Sie eine Verknüpfung dazu erstellen. Sie können eine Liste auch in eine Excel-Tabelle exportieren, die eine unidirektionale Datenverbindung zwischen der Excel-Tabelle und der Liste erstellt. Erfahren Sie, wie Sie [Offline mit Tabellen arbeiten, die mit SharePoint-Listen verknüpft sind](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e).
  
Weitere Informationen finden Sie im Abschnitt "mehr über das Verwalten umfangreicher Listen" in [Manage umfangreicher Listen und Bibliotheken in Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).
  
## <a name="best-practices-for-customizing-web-pages"></a>Bewährte Methoden für das Anpassen von Webseiten

Wenn Sie eine Webseite anpassen, können Sie versehentlich eine schlechte Leistung bei der Seite verursachen. Eine Reihe von Faktoren kann Auswirkungen haben, beispielsweise die Komplexität und Größe der Seite, die Anzahl der hinzugefügten Webparts, die anfängliche Anzeige Anzahl von Listen-oder Bibliothekselementen und die Art und Weise, wie Sie die Seite codieren.
  
Weitere Informationen finden Sie unter [Tune SharePoint Online Performance](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance).
  
## <a name="best-practices-for-using-project-online"></a>Bewährte Methoden für die Verwendung von Project Online

Die folgenden Richtlinien können die Netzwerkleistung verbessern.
  
- Project Online und SharePoint Online erfordern eine Synchronisierung, was zeitaufwändig sein kann. Wenn Ihre Projektteams niedrige Umsätze aufweisen, deaktivieren Sie die Projektwebsite Synchronisierung, um die Leistung der Projektveröffentlichung und der Projekt Detail Seiten zu verbessern. Begrenzen Sie die Active Directory-Synchronisierung auf Ressourcengruppen, die das System tatsächlich verwenden müssen, und überwachen Sie mögliche Berechtigungsprobleme nach der Synchronisierung von umfangreichen Gruppen. 
    
- Wenn Ihre Organisation Projektwebsites verwendet, erstellen Sie Sie bei Bedarf anstatt automatisch. Dadurch wird die erste Veröffentlichungs Erfahrung beschleunigt, und es werden keine unnötigen Websites und Inhalte erstellt.
    
- Projekt Detail Seiten (PDP) können eine Neuberechnung des gesamten Projekts auslösen und Workflowaktionen starten, die beide leistungsintensive Vorgänge aufweisen können. Vermeiden Sie das Aktualisieren der Kalender Felder (Anfangsdatum, Endtermin, Status Datum und Aktuelles Datum) und der nicht geplanten Felder (Projektname, Beschreibung und Besitzer), um zu vermeiden, dass zwei Aktualisierungsprozesse gleichzeitig auf demselben PDP ausgelöst werden. 
    
- Reduzieren Sie die Anzahl der Webparts und benutzerdefinierten Felder, die auf jeder PDP angezeigt werden. Erstellen Sie eine dedizierte PDP mit den einzigen Feldern, die eine Aktualisierung erfordern, um die Auslastung zu verbessern und Zeit zu sparen. 
    
- Wenn Sie OData für die Berichterstellung verwenden, begrenzen Sie die Menge der Daten, die Sie zur Laufzeit Abfragen, mithilfe der serverseitigen Filterung.
    
Weitere Informationen finden Sie unter [Tune Project Online Performance](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).
  
## <a name="whats-the-best-way-to-report-problems"></a>Was ist der beste Weg, Probleme zu melden?

Microsoft verbessert die Gesamtleistung von Office 365 kontinuierlich, indem es das Netzwerk überwacht, die Bandbreite und Latenz misst, die Seitenladezeit verbessert, die Datenträger-e/a reduziert, die Seiten für eine minimale Download Strategie umgestaltet, die Hardware zu Rechenzentren hinzufügt und Hinzufügen weiterer Rechenzentren. Weitere Informationen zum Überprüfen des aktuellen Status und der BerichtersTELLUNGSprobleme finden Sie unter [Überprüfen der Office 365-Dienst Integrität](https://docs.microsoft.com/office365/enterprise/view-service-health).
  
## <a name="see-also"></a>Siehe auch

[Netzwerkplanung und Leistungsoptimierung für Office 365](network-planning-and-performance.md)
  
[Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)
  
[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

