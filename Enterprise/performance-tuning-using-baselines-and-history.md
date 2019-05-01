---
title: 'Office 365-Leistung optimieren mit Basisplänen und Leistungsverlauf '
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/31/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
ms.collection:
- M365-security-compliance
- Ent_O365
description: Es gibt einige einfache Methoden zum Überprüfen der Verbindungsleistung zwischen Office 365 und Ihrem Unternehmen, mit denen Sie eine grobe Basis ihrer Konnektivität einrichten können. Wenn Sie den Leistungsverlauf ihrer Clientcomputerverbindungen kennen, können Sie Probleme frühzeitig erkennen, erkennen und Vorhersagen.
ms.openlocfilehash: 328b8f66b86f2fc1880b3a9d65f4b9fd63b51d40
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491836"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Office 365-Leistung optimieren mit Basisplänen und Leistungsverlauf 

Es gibt einige einfache Methoden zum Überprüfen der Verbindungsleistung zwischen Office 365 und Ihrem Unternehmen, mit denen Sie eine grobe Basis ihrer Konnektivität einrichten können. Wenn Sie den Leistungsverlauf ihrer Clientcomputerverbindungen kennen, können Sie Probleme frühzeitig erkennen, erkennen und Vorhersagen.
  
Wenn Sie nicht an Leistungsproblemen arbeiten, soll dieser Artikel Ihnen helfen, einige häufige Fragen zu berücksichtigen, wie Sie wissen, dass das Problem, das Sie sehen, ein Leistungsproblem und kein Office 365-Dienst Vorfall ist. Wie können Sie eine gute Leistung langfristig planen? Wie können Sie die Leistung im Auge behalten? Wenn Ihr Team oder Ihre Clients während der Verwendung von Office 365 eine langsame Leistung erkennen, und Sie sich über eine dieser Fragen wundern, lesen Sie weiter.
  
> [!IMPORTANT]
> **Haben Sie jetzt ein Leistungsproblem zwischen Ihrem Client und Office 365?** Führen Sie die im [Plan für die Leistungsproblembehandlung für Office 365](performance-troubleshooting-plan.md)beschriebenen Schritte aus. 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Etwas, was Sie über die Leistung von Office 365 wissen sollten

Office 365 befindet sich in einem dedizierten Microsoft-Netzwerk mit hoher Kapazität, das nicht nur durch Automatisierung, sondern durch reale Personen ständig überwacht wird. Ein Teil der Rolle der Verwaltung der Office 365-Cloud besteht darin, die Leistungsoptimierung einzurichten und dort zu straffen, wo es möglich ist. Da Clients der Office 365-Cloud eine Verbindung über das Internet herstellen müssen, besteht ein kontinuierlicher Aufwand zur Optimierung der Leistung in Office 365-Diensten. Leistungsverbesserungen werden in der Cloud nie wirklich angehalten, und es gibt viele gesammelte Erfahrungen mit der Beibehaltung der Cloud und schnell. Wenn Sie ein Leistungsproblem bei der Verbindung von Ihrem Standort zu Office 365 haben, sollten Sie nicht mit einem Support Fall beginnen und warten. Stattdessen sollten Sie mit der Untersuchung des Problems von "innen nach außen" beginnen. Das heißt, beginnen Sie innerhalb Ihres Netzwerks, und arbeiten Sie Ihren Weg zu Office 365. Bevor Sie einen Fall mit dem Office 365-Support öffnen, können Sie Daten erfassen und Maßnahmen ergreifen, die Ihr Problem untersuchen und beheben können.
  
> [!IMPORTANT]
> Berücksichtigen Sie die Kapazitätsplanung und Grenzen in Office 365. Diese Informationen stellen Sie vor der Kurve, wenn Sie versuchen, ein Leistungsproblem zu beheben. Hier finden Sie einen Link zur [Office 365-Plattformdienst Beschreibung](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). Hierbei handelt es sich um einen zentralen Hub, und alle von Office 365 angebotenen Dienste verfügen über einen Link, der von hier aus zu den eigenen Dienstbeschreibungen wechselt. Wenn Sie beispielsweise die Standardgrenzwerte für SharePoint Online anzeigen möchten, klicken Sie auf [SharePoint Online-Dienstbeschreibung](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx) , und suchen Sie den [Abschnitt SharePoint Online-Grenzwerte](https://go.microsoft.com/fwlink/p/?LinkID=856113). 
  
Stellen Sie sicher, dass Sie in Ihre Problembehandlung eingehen, indem Sie verstehen, dass die Leistung eine gleitende Skalierung ist, dass es nicht darum geht, einen idealisierten Wert zu erreichen und ihn dauerhaft beizubehalten (wenn Sie glauben, dass dies so ist, dann gelegentliche Aufgaben mit hoher Bandbreite wie on-Boarding a große Anzahl von Benutzern oder große Datenmigrationen sind sehr belastend – also planen Sie die Leistungsbeeinträchtigungen. Sie können und sollten über eine ungefähre Vorstellung Ihrer Leistungsziele verfügen, aber viele Variablen werden in die Leistung eingehen, daher variiert die Leistung. Das ist die Art der Leistung. 
  
Bei der Fehlerbehebung bei der Leistung geht es nicht darum, bestimmte Ziele zu erreichen und diese Nummern unbegrenzt beizubehalten, sondern um vorhandene Aktivitäten zu verbessern. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>Wie sieht ein Leistungsproblem aus?

Zunächst müssen Sie sicherstellen, dass das, was Sie erleben, tatsächlich ein Leistungsproblem und kein Dienst Vorfall ist. Ein Leistungsproblem unterscheidet sich von einem Servicevorfall in Office 365. Hier erfahren Sie, wie Sie sie auseinander halten.
  
Wenn der Office 365-Dienst Probleme hat, handelt es sich um einen Servicevorfall. Sie sehen rote oder gelbe Symbole unter **aktuelle Integrität** im Office 365 Admin Center, Sie können auch feststellen, dass die Leistung auf Clientcomputern eine Verbindung mit Office 365. Wenn die aktuelle Integrität beispielsweise ein rotes Symbol meldet und Sie neben **** Exchange Untersuchungen sehen, erhalten Sie möglicherweise auch eine Reihe von Anrufen von Personen in Ihrer Organisation, die sich darüber beschweren, dass Clientpostfächer, die Exchange Online verwenden, schlecht ausgeführt werden. In diesem Fall wird davon ausgegangen, dass Ihre Exchange Online-Leistung nur zu Problemen innerhalb des Diensts wurde. 
  
![Das Office 365 Health Dashboard mit allen Arbeitsauslastungen, die grün angezeigt werden, mit Ausnahme von Exchange, wodurch der Dienst wiederhergestellt wird.](media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
An diesem Punkt sollten Sie, der Office 365-Administrator, die **aktuelle Integrität** überprüfen und dann **Details und Verlauf häufig anzeigen**, um auf dem System auf dem Laufenden zu bleiben. Das **aktuelle Integritäts** Dashboard wurde erstellt, um Sie über Änderungen an und die Probleme im Dienst zu informieren. Die Hinweise und Erläuterungen, die in den Gesundheits Verlauf geschrieben wurden, admin to admin, helfen Ihnen dabei, ihre Auswirkungen zu beurteilen und Sie über die laufende Arbeit zu informieren. 
  
![Ein Bild des Office 365-Integritäts Dashboards, in dem erläutert wird, dass der Exchange Online-Dienst wiederhergestellt wurde und warum.](media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Ein Leistungsproblem ist kein Dienst Vorfall, obwohl Vorfälle zu einer langsamen Leistung führen können. Ein Leistungsproblem sieht wie folgt aus:
  
- Ein Leistungsproblem tritt auf, unabhängig davon, was die **aktuelle Integrität** des Office 365 admin Centers für den Dienst meldet. 
    
-  Ein Verhalten, das früher relativ nahtlos war, dauert lange, oder es wird nie abgeschlossen. 
    
- Sie können das Problem auch replizieren, oder zumindest wissen Sie, dass es geschieht, wenn Sie die richtigen Schritte ausführen.
    
-  Wenn das Problem intermittierend ist, gibt es immer noch ein Muster, beispielsweise wissen Sie, dass von 10:00 AM Sie Anrufe von Benutzern haben, die nicht zuverlässig auf Office 365 zugreifen können, und dass die Anrufe um 12.00 Uhr absterben. 
    
Das klingt wohl vertraut; vielleicht zu vertraut. Wenn Sie wissen, dass es sich um ein Leistungsproblem handelt, wird die Frage "Was tun Sie als nächstes?". Mit dem Rest dieses Artikels können Sie genau feststellen, ob.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Definieren und Testen des Leistungsproblems

Leistungsprobleme treten oft im Laufe der Zeit auf, daher kann es schwierig sein, das eigentliche Problem zu definieren. Sie müssen eine gute Problembeschreibung und eine gute Idee des Problem Kontexts erstellen, und dann müssen Sie wiederholbare Testschritte durchführen, um den Tag zu gewinnen. Andernfalls können Sie ohne eigenes Verschulden verloren gehen. Warum? Nun, hier sind einige Beispiele für Fehler Anweisungen, die nicht genügend Informationen enthalten:
  
- Der Wechsel von meinem Posteingang zu meinem Kalender war früher etwas, das ich nicht bemerkt hatte, und jetzt ist es eine Kaffeepause. Können Sie es wie gewohnt tun?
    
- Das Hochladen meiner Dateien in SharePoint Online dauert ewig. Warum ist es am Nachmittag langsam, aber zu einem anderen Zeitpunkt, ist es schnell? Kann es nicht einfach sein, schnell zu sein?
    
Die obigen Problemaussagen stellen mehrere große Herausforderungen dar. Insbesondere gibt es eine Vielzahl von Mehrdeutigkeiten. Beispiel:
  
- Es ist unklar, wie der Wechsel zwischen Posteingang und Kalender verwendet, um auf dem Laptop zu handeln.
    
- Wenn der Benutzer sagt, "kann es nicht einfach sein", was ist "schnell"?
    
- Wie lange ist "Forever"? Ist das mehrere Sekunden oder Minuten, oder könnte der Benutzer zu Mittagessen gehen, und es wäre noch zehn Minuten nach dem wieder einkehren des Benutzers fertig?
    
All dies liegt daran, dass der Administrator und die Problembehandlung viele Details aus solchen Fehlermeldungen nicht erkennen können. Wenn das Problem beispielsweise begonnen hat; Dass der Benutzer von zu Hause aus arbeitet und immer nur langsames wechseln in einem Heimnetzwerk sieht; Der Benutzer muss mehrere andere RAM-intensive Anwendungen auf dem lokalen Client ausführen, oder der Benutzer führt ein älteres Betriebssystem aus oder hat keine aktuellen Updates ausgeführt.
  
Wenn Benutzer ein Leistungsproblem melden, gibt es viele Informationen, die erfasst werden müssen. Das Sammeln dieser Informationen ist Teil eines Prozesses, der das Problem als Scoping bezeichnet oder es untersucht. Es folgt eine grundlegende Scoping-Liste, die Sie verwenden können, um Informationen zu Ihrem Leistungsproblem zu sammeln. Diese Liste ist nicht vollständig, aber Sie ist ein Ort, an dem Sie einen eigenen starten können: 
  
- Zu welchem Zeitpunkt ist das Problem aufgetreten, und um zu welcher Tageszeit?
    
- Welche Art von Clientcomputer haben Sie verwendet, und wie wird eine Verbindung mit dem Unternehmensnetzwerk hergestellt (VPN, verkabelt, drahtlos)?
    
- Arbeiteten Sie Remote oder waren Sie im Büro?
    
- Haben Sie die gleichen Aktionen auf einem anderen Computer ausprobiert und dasselbe Verhalten festzustellen?
    
- Führen Sie die Schritte durch, die Ihnen Probleme bereiten, damit Sie die von Ihnen ausgeführten Aktionen schreiben können.
    
- Wie langsam ist die Leistung in Sekunden oder Minuten?
    
- Wo in der Welt befinden Sie sich?
    
Einige dieser Fragen sind offensichtlicher als andere. Die meisten jeder verstehen eine Problembehandlung benötigt die genauen Schritte, um das Problem zu reproduzieren. Wie können Sie denn sonst aufzeichnen, was falsch ist, und wie sonst können Sie testen, ob das Problem behoben ist? Nicht so offensichtlich sind beispielsweise "welches Datum und welche Uhrzeit haben Sie das Problem angezeigt?" und "wo in der Welt befinden Sie sich?", Informationen, die im Tandem verwendet werden können. Je nachdem, wann der Benutzer funktioniert hat, kann ein paar Stunden Zeitunterschied bedeuten, dass die Wartung bereits in Teilen des Unternehmensnetzwerks erfolgt. Wenn Ihr Unternehmen beispielsweise über eine hybride Implementierung verfügt, wie eine hybride SharePoint-Suche, die Suchindizes sowohl in SharePoint Online als auch in einer lokalen SharePoint Server 2013-Instanz Abfragen kann, werden möglicherweise Updates in der lokalen Farm ausgeführt. Wenn sich Ihr Unternehmen in der Cloud befindet, kann die Systemwartung das Hinzufügen oder Entfernen von Netzwerkhardware, das Bereitstellen von unternehmensweiten Updates oder das Ändern von DNS-oder anderen Kern Infrastrukturen sein.
  
Wenn Sie ein Leistungsproblem beheben, ist es ein bisschen wie ein Tatort, müssen Sie präzise und aufmerksam sein, um Schlussfolgerungen aus dem Beweis zu ziehen. Zu diesem Zweck müssen Sie eine gute Problem Aussage erhalten, indem Sie Beweise sammeln. Sie sollte den Kontext des Computers, den Kontext des Benutzers, beim Beginn des Problems und die genauen Schritte, die das Leistungsproblem offen legen, einbeziehen. Diese Problem Aussage sollte und bleiben Sie die oberste Seite in Ihren Notizen. Wenn Sie die Problem Anweisung erneut durchlaufen, nachdem Sie die Lösung bearbeitet haben, führen Sie die erforderlichen Schritte aus, um zu testen und zu prüfen, ob das Problem durch die von Ihnen ausgeführten Aktionen gelöst wurde. Dies ist wichtig, um zu wissen, wann Ihre Arbeit dort erledigt ist.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Wissen Sie, wie die Leistung früher ausschaute, als Sie gut war?

Wenn Sie Pech haben, weiß niemand. Niemand hatte Zahlen. Das bedeutet, dass niemand die einfache Frage beantworten kann, "wie viele Sekunden dauerte es, bis ein Posteingang in Office 365?" oder "wie lange hat es verwendet, als die Führungskräfte eine lync Online-Besprechung hatten?", die ein gängiges Szenario für viele Unternehmen ist.
  
Hier fehlt eine Leistungsbasis.
  
Baselines bieten Ihnen einen Kontext für Ihre Leistung. Je nach den Anforderungen Ihres Unternehmens sollten Sie einen Basisplan gelegentlich auf häufige Maßnahmen festlegen. Wenn Sie ein größeres Unternehmen sind, kann Ihr Operations-Team bereits Basispläne für Ihre lokale Umgebung erstellen. Wenn Sie beispielsweise alle Exchange-Server am ersten Montag des Monats und alle SharePoint-Server am dritten Montag Patchen, verfügt Ihr Betriebsteam wahrscheinlich über eine Liste der Aufgaben und Szenarien, die nach dem Patchen ausgeführt werden, um zu prüfen, ob kritische Funktionen Betriebs. Öffnen Sie beispielsweise den Posteingang, klicken Sie auf senden/empfangen, und stellen Sie sicher, dass die Ordner aktualisiert werden, oder navigieren Sie in SharePoint auf der Hauptseite der Website, wechseln Sie zur Seite Unternehmenssuche, und führen Sie eine Suche aus, die Ergebnisse zurückgibt.
  
Wenn Ihre Anwendungen in Office 365 sind, können Sie einige der grundlegenden Baselines Messen, die Sie in Millisekunden von einem Clientcomputer innerhalb Ihres Netzwerks bis zu einem Ausgangspunkt oder dem Punkt, an dem Sie Ihr Netzwerk verlassen, und zu Office 365 ausgehen. Hier sind einige hilfreiche Baselines, die Sie untersuchen und aufzeichnen können:
  
- Identifizieren Sie die Geräte zwischen dem Clientcomputer und dem Ausgangspunkt, beispielsweise Ihrem Proxy Server.
    
  - Sie müssen Ihre Geräte kennen, damit Sie über einen Kontext (IP-Adressen, Gerätetyp usw.) für Leistungsprobleme verfügen.
    
  - Proxy Server sind häufige Ausgangspunkte, sodass Sie überprüfen können, welcher Proxy Server für den Webbrowser festgelegt ist, falls vorhanden.
    
  - Es gibt Drittanbietertools, die Ihr Netzwerk erkennen und zuordnen können, aber die sicherste Möglichkeit, Ihre Geräte zu kennen, besteht darin, ein Mitglied Ihres Netzwerkteams zu Fragen.
    
- Identifizieren Sie Ihren Internet Dienstanbieter (ISP), notieren Sie Ihre Kontaktinformationen, und Fragen Sie, wie viele Stromkreise wie viel Bandbreite Sie haben.
    
- Identifizieren Sie innerhalb Ihres Unternehmens Ressourcen für die Geräte zwischen dem Client und dem Ausgangspunkt, oder identifizieren Sie einen Notfallkontakt, um mit Netzwerkproblemen zu sprechen.
    
Hier sind einige Grundlagen, die einfache Tests mit Tools für Sie berechnen können:
  
- Zeit vom Clientcomputer bis zum Ausgangspunkt in Millisekunden
    
- Zeit von Ihrem Ausstieg Punkt zu Office 365 in Millisekunden
    
- Standort in der Welt des Servers, der die URLS für Office 365 beim Browsen auflöst
    
- Die Geschwindigkeit der DNS-Auflösung Ihres ISP in Millisekunden, Inkonsistenzen bei der Paket Ankunft (Netzwerk Jitter), Upload-und Downloadzeiten in Millisekunden
    
Wenn Sie nicht mit der Ausführung dieser Schritte vertraut sind, werden wir in diesem Artikel ausführlicher erläutert. 
  
## <a name="what-is-a-baseline"></a>Was ist eine Baseline?

Sie kennen die Auswirkungen, wenn es schlecht geht, aber wenn Sie Ihre historischen Leistungsdaten nicht kennen, ist es nicht möglich, einen Kontext dafür zu haben, wie schlimm es geworden ist und wann. Ohne einen Basisplan fehlt Ihnen also der Schlüssel zur Lösung des Puzzles: das Bild im Feld Puzzle. Bei der Leistungsproblembehandlung benötigen Sie einen *Vergleichs* Punkt. Einfache Leistungsbasislinien sind nicht schwer zu übernehmen. Ihr Operations Team kann die Aufgabe haben, diese nach einem Zeitplan auszuführen. Angenommen, Ihre Verbindung sieht wie folgt aus: 
  
![Eine einfache Netzwerk Grafik mit Client-, Proxy-und Office 365-Clouds.](media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Das führt dazu, dass Sie sich mit Ihrem Netzwerkteam unterhalten haben und herausgefunden haben, dass Sie Ihre Firma über einen Proxy Server für das Internet verlassen, und dass der Proxy alle Anforderungen verarbeitet, die Ihr Clientcomputer an die Cloud sendet. In diesem Fall sollten Sie eine vereinfachte Version der Verbindung zeichnen, in der alle dazwischenliegenden Geräte aufgeführt sind. Fügen Sie nun Tools ein, mit denen Sie die Leistung zwischen dem Client, dem Ausgangspunkt (in dem Sie Ihr Netzwerk für das Internet verlassen) und der Office 365-Cloud testen können.
  
![Grundlegendes Netzwerk mit Client-, Proxy-und Cloud-und Tools-Vorschlägen PSPing, TraceTCP und Netzwerkablaufverfolgungen.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Die Optionen werden aufgrund des Umfangs an Fachwissen, den Sie benötigen, um die Leistungsdaten zu finden, als **einfach** und **fortgeschritten** aufgeführt. Eine Netzwerkablaufverfolgung nimmt im Vergleich zu Befehlszeilentools wie PsPing und TraceTCP viel Zeit in Anspruch. Diese beiden Befehlszeilentools wurden ausgewählt, da Sie keine ICMP-Pakete verwenden, die von Office 365 blockiert werden, und weil Sie die Zeit in Millisekunden angeben, die erforderlich ist, um den Clientcomputer oder den Proxy Server (wenn Sie Zugriff haben) zu verlassen und an Office 365 zu gelangen. Jeder einzelne Hop von einem Computer zu einem anderen wird am Ende mit einem Zeitwert, und das ist ideal für Baselines! Ebenso wichtig ist, dass Sie mit diesen Befehlszeilentools eine Portierung auf den Befehl hinzufügen können, dies ist nützlich, da Office 365 über den Anschluss 443 kommuniziert, der von Secure Sockets Layer und Transport Layer Security (SSL und TLS) verwendet wird. Andere Drittanbietertools sind jedoch möglicherweise bessere Lösungen für Ihre Situation. Microsoft unterstützt nicht alle diese Tools, wenn Sie also aus irgendeinem Grund nicht PsPing und TraceTCP arbeiten können, navigieren Sie mit einem Tool wie Netmon zur Netzwerkablaufverfolgung. 
  
Sie können eine Baseline vor Geschäftszeiten, wieder bei starker Nutzung und dann wieder nach Stunden ablegen. Dies führt dazu, dass Sie eine Ordnerstruktur haben, die wie folgt aussieht:
  
![Grafik, die eine Möglichkeit zum Organisieren von Leistungsdaten in Ordnern vorschlägt.](media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
Sie sollten auch eine Benennungskonvention für Ihre Dateien auswählen. Im Folgenden finden Sie einige Beispiele:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf
    
Es gibt viele verschiedene Möglichkeiten, dies zu tun, aber die Verwendung des Formats ** \<DateTime\>\<, was im Test\> geschieht** , ist ein guter Ausgangspunkt. Wenn Sie sich mit diesem Thema beschäftigen, werden Sie viel helfen, wenn Sie versuchen, Probleme zu einem späteren Zeitpunkt zu beheben. Später können Sie sagen: "Ich habe am 8. Februar zwei Spuren genommen, eine gute Leistung und eine schlechte, sodass wir Sie vergleichen können." Dies ist für die Problembehandlung äußerst hilfreich. 
  
Sie müssen über eine organisierte Methode verfügen, um Ihre Verlaufs Grundlagen beizubehalten. In diesem Beispiel wurden mit den einfachen Methoden drei Befehlszeilen Ausgänge erstellt, und die Ergebnisse wurden als Screenshots gesammelt, aber möglicherweise haben Sie stattdessen Netzwerk-Aufnahmedateien. Verwenden Sie die Methode, die für Sie am besten geeignet ist. Speichern Sie Ihre historischen Baselines, und verweisen Sie Sie an Punkten, an denen Sie Änderungen am Verhalten von Onlinediensten bemerken. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Gründe für die Erfassung von Leistungsdaten während eines Pilotprojekts

Es gibt keinen besseren Zeitpunkt für die Erstellung von Baselines als während eines Pilotprojekts des Office 365-Diensts. Ihr Büro hat möglicherweise Tausende von Benutzern, Hunderttausende oder fünf, aber auch mit einer kleinen Anzahl von Benutzern können Sie Tests durchführen, um Leistungsschwankungen zu messen. Bei einem Großunternehmen kann ein repräsentatives Beispiel für mehrere hundert Benutzer, die Office 365 steuern, nach außen auf mehrere Tausende projiziert werden, damit Sie wissen, wo Probleme auftreten können, bevor Sie auftreten.
  
Im Fall eines kleinen Unternehmens, bei dem das on-Boarding bedeutet, dass alle Benutzer gleichzeitig zum Dienst wechseln und kein Pilotprojekt vorhanden ist, halten Sie die Leistung so fest, dass Sie allen Personen, die möglicherweise eine Fehlerbehebung ausführen müssen, Daten zeigen. Wenn Sie beispielsweise feststellen, dass Sie plötzlich in der Zeit, die Sie zum Hochladen einer mittelgroßen Grafik benötigen, in der es sehr schnell vorkommt, zu Fuß um Ihr Gebäude gehen können.
  
## <a name="how-to-collect-baselines"></a>Erfassen von Baselines

Für alle Problem Behandlungspläne müssen Sie diese Dinge mindestens ermitteln:
  
- Der verwendete Clientcomputer (der Computer oder das Gerät, eine IP-Adresse und die Aktionen, die das Problem verursacht haben)
    
- Wo sich der Clientcomputer in der Welt befindet (beispielsweise ob dieser Benutzer in einem VPN zum Netzwerk, Remote oder im Firmenintranet arbeitet)
    
- Der Ausgangspunkt, den der Clientcomputer in Ihrem Netzwerk verwendet (der Punkt, an dem der Datenverkehr Ihr Unternehmen für einen ISP oder das Internet verlässt)
    
 Sie können das Layout Ihres Netzwerks vom Netzwerkadministrator herausfinden. Wenn Sie sich in einem kleinen Netzwerk befinden, sehen Sie sich die Geräte an, die Sie mit dem Internet verbinden, und rufen Sie Ihren ISP an, wenn Sie Fragen zum Layout haben. Erstellen Sie eine Grafik des endgültigen Layouts als Referenz. 
  
Dieser Abschnitt gliedert sich in einfache Befehlszeilentools und-Methoden sowie weitere Optionen für erweiterte Tools. Wir behandeln zunächst einfache Methoden. Wenn Sie im Moment ein Leistungsproblem haben, sollten Sie zu den erweiterten Methoden wechseln und den Aktionsplan zur Behandlung von Leistungsproblemen testen.
  
### <a name="simple-methods"></a>Einfache Methoden

Ziel dieser einfachen Methoden ist es zu lernen, einfache Leistungsbasislinien im Laufe der Zeit zu nutzen, zu verstehen und ordnungsgemäß zu speichern, damit Sie über die Leistung von Office 365 informiert werden. Hier ist das sehr einfache Diagramm für einfache, wie Sie zuvor gesehen haben:
  
![Grundlegendes Netzwerk mit Client-, Proxy-und Cloud-und Tools-Vorschlägen PSPing, TraceTCP und Netzwerkablaufverfolgungen.](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP ist in diesem Screenshot enthalten, da es ein nützliches Tool ist, um in Millisekunden zu zeigen, wie lange eine Anforderung zur Verarbeitung benötigt wird, und wie viele Netzwerkhops oder Verbindungen von einem Computer zum nächsten ausgeführt werden, die von der Anforderung benötigt werden, um ein Ziel zu erreichen. TraceTCP kann auch die Namen der Server angeben, die während des Hops verwendet werden, was für eine Microsoft Office 365-Problembehandlung hilfreich sein kann. > TraceTCP-Befehle können sehr einfach sein, beispielsweise: `tracetcp.exe outlook.office365.com:443`_GT_ _GT_ denken Sie daran, die Nummer der Portierung in den Befehl einzuschließen! > [TraceTCP](http://simulatedsimian.github.io/tracetcp_download.html) ist ein kostenloser Download, aber basiert auf Wincap. Wincap ist ein Tool, das auch von Netmon verwendet und installiert wird. Wir verwenden Netmon auch im Abschnitt Erweiterte Methoden. 
  
 Wenn Sie über mehrere Büros verfügen, müssen Sie auch an jedem dieser Standorte eine Reihe von Daten von einem Client behalten. Dieser Test misst die Wartezeit, bei der es sich in diesem Fall um einen Zahlenwert handelt, der die Zeitspanne zwischen dem Senden einer Anforderung an Office 365 durch den Client und der Antwort von Office 365 auf die Anforderung beschreibt. Die Tests werden innerhalb Ihrer Domäne auf einem Clientcomputer durchgeführt, und es wird erwartet, dass Sie einen Roundtrip zwischen dem Netzwerk, über einen Ausstiegspunkt, über das Internet zu Office 365 und zurückführen. 
  
Es gibt verschiedene Möglichkeiten, den Ausgangspunkt zu behandeln, in diesem Fall den Proxy Server. Sie können eine Ablaufverfolgung zwischen 1 und 2 und dann 2 bis 3 durchführen und dann die Zahlen in Millisekunden addieren, um eine endgültige Gesamtsumme an den Rand Ihres Netzwerks zu erhalten. Sie können auch die Verbindung so konfigurieren, dass der Proxy für Office 365-Adressen umgangen wird. In einem größeren Netzwerk mit einer Firewall, einem Reverseproxy oder einer Kombination dieser beiden müssen Sie möglicherweise Ausnahmen auf dem Proxy Server vornehmen, die den Datenverkehr für viele URLs zulassen. Eine Liste der von Office 365 verwendeten Endpunkte finden Sie unter [office 365-URLs und IP-Adressbereiche](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Wenn Sie einen Authentifizierungs Proxy haben, beginnen Sie mit dem Testen von Ausnahmen für Folgendes:
  
- Ports 80 und 443
    
- TCP und HTTPs
    
- Verbindungen, die für eine dieser URLs ausgehen:
    
- \*. microsoftonline.com
    
- \*. microsoftonline-p.com
    
- \*. SharePoint.com
    
- \*. Outlook.com
    
- \*. lync.com
    
- osub.Microsoft.com
    
Alle Benutzer müssen ohne Proxy Interferenz oder Authentifizierung zu diesen Adressen gelangen. In einem kleineren Netzwerk sollten Sie diese zu ihrer Proxyumgehungsliste in Ihrem Webbrowser hinzufügen. 
  
Um diese zu ihrer Proxyumgehungsliste in Internet Explorer hinzuzufügen, wechseln Sie zu **Extras** \> **Internet Options** \> **Connections** \> **LAN Settings** \> **Advanced**. Auf der Registerkarte Erweitert finden Sie auch den Proxy Server und den Proxy Server-Portierung. Möglicherweise müssen Sie auf das Kontrollkästchen **Proxy Server für LAN verwenden**klicken, um auf die Schaltfläche **erweitert** zuzugreifen. Sie sollten sicherstellen, dass die **Umgehung des Proxyservers für lokale Adressen** überprüft wird. Sobald Sie auf **erweitert**klicken, wird ein Textfeld angezeigt, in das Sie Ausnahmen eingeben können. Trennen Sie die oben aufgeführten Platzhalter-URLs durch Semikolons, zum Beispiel:
  
\*. microsoftonline.com; \*. SharePoint.com
  
Nachdem Sie Ihren Proxy umgangen haben, sollten Sie in der Lage sein, Ping oder PsPing direkt an einer Office 365-URL zu verwenden. Der nächste Schritt besteht darin, ping- **Outlook.office365.com**zu testen. Oder wenn Sie PsPing oder ein anderes Tool verwenden, mit dem Sie dem Befehl eine Portierungs Nummer geben können, PsPing gegen **Portal.microsoftonline.com:443** , um die durchschnittliche Roundtrip-Zeit in Millisekunden anzuzeigen. 
  
Die Roundtrip-Zeit oder RTT ist ein Zahlenwert, der misst, wie lange es dauert, bis eine HTTP-Anforderung an einen Server wie outlook.office365.com gesendet wird, und eine Antwort zurück erhält, die erkennt, dass der Server dies getan hat. Manchmal wird dies als RTT abgekürzt. Dies sollte eine relativ kurze Zeitspanne sein.
  
Sie müssen [PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) oder ein anderes Tool verwenden, das keine ICMP-Pakete verwendet, die von Office 365 blockiert sind, um diesen Test durchzuführen. 
  
 **Verwenden von PsPing zum Abrufen einer allgemeinen Roundtrip-Zeit in Millisekunden direkt aus einer Office 365-URL**
  
1. Führen Sie die folgenden Schritte durch, um eine Eingabeaufforderungen mit erhöhten Rechten auszuführen:
    
1. Klicken Sie auf **Start**.
    
2. Geben Sie im Feld **Suche starten** den Befehl cmd ein, und drücken Sie dann STRG + UMSCHALT + EINGABETASTE.
    
3. Wenn das Dialogfeld **Benutzerkontensteuerung** eingeblendet wird, bestätigen Sie die angegebene Aktion und klicken dann auf **Weiter**.
    
2. Navigieren Sie zu dem Ordner, in dem das Tool (in diesem Fall PsPing) installiert ist, und testen Sie diese Office 365-URLs:
    
  - psping Portal.Office.com:443
    
  - psping Microsoft-My.SharePoint.com:443
    
  - psping Outlook.office365.com:443
    
  - psping www.Yammer.com:443
    
    ![Der PSPing-Befehl wird an microsoft-my.sharepoint.com-Portierung 443.](media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
Stellen Sie sicher, dass Sie die Nummer 443 angeben. Denken Sie daran, dass Office 365 auf einem verschlüsselten Kanal funktioniert. Wenn Sie ohne die PsPing, schlägt Ihre Anforderung fehl. Nachdem Sie Ihre kurze Liste gepingt haben, suchen Sie nach der durchschnittlichen Zeit in Millisekunden (MS). Das möchten Sie aufzeichnen!
  
![Grafik, die eine Abbildung der Client-Proxy-PSPing mit einer Roundtrip-Zeit von 2,8 Millisekunden anzeigt.](media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Wenn Sie mit der Proxyumgehung nicht vertraut sind und es vorziehen, die Schritte Schritt für Schritt durchzuführen, müssen Sie zuerst den Namen Ihres Proxyservers herausfinden. Gehen Sie in Internet Explorer zu **Extras** \> **Internet Options** \> **Connections** \> **LAN Settings** \> **Advanced**. Auf der Registerkarte **erweitert** sehen Sie den aufgeführten Proxy Server. Pingen Sie diesen Proxy Server an einer Eingabeaufforderungen, indem Sie diese Aufgabe ausführen: 
  
 **So Pingen Sie den Proxy Server an und erhalten einen Roundtrip-Wert in Millisekunden für Stufe 1 bis 2**
  
1. Führen Sie die folgenden Schritte durch, um eine Eingabeaufforderungen mit erhöhten Rechten auszuführen:
    
1. Klicken Sie auf **Start**.
    
2. Geben Sie im Feld **Suche starten** den Befehl cmd ein, und drücken Sie dann STRG + UMSCHALT + EINGABETASTE.
    
3. Wenn das Dialogfeld **Benutzerkontensteuerung** eingeblendet wird, bestätigen Sie die angegebene Aktion und klicken dann auf **Weiter**.
    
2. Geben Sie \<Ping den Namen des Proxyservers ein, den Ihr Browser verwendet, oder die IP-Adresse\> des Proxyservers, und drücken Sie dann die EINGABETASTE. Wenn Sie PsPing oder ein anderes Tool installiert haben, können Sie dieses Tool stattdessen verwenden. 
    
    Ihr Befehl kann wie eines dieser Beispiele aussehen: 
    
  - Ping-ourproxy.ourdomain.Industry.Business.com
    
  - Ping-155.55.121.55
    
  - Ping-ourproxy
    
  - psping ourproxy.ourdomain.Industry.Business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy: 80
    
3. Wenn die Ablaufverfolgung beendet das Senden von Testpaketen, erhalten Sie eine kleine Zusammenfassung, die eine durchschnittliche, in Millisekunden, und das ist der Wert, den Sie suchen. Führen Sie einen Screenshot der Ansage aus, und speichern Sie Sie unter Verwendung Ihrer Benennungskonvention. An diesem Punkt kann es auch dazu beitragen, das Diagramm mit dem Wert auszufüllen.
    
Vielleichthaben Sie am frühen Morgen eine Ablaufverfolgung vorgenommen, und Ihr Client kann sich schnell an den Proxy (oder was auch immer der Ausstieg Server ins Internet verlässt) gewöhnen. In diesem Fall können Ihre Nummern wie folgt aussehen:
  
![Grafik, die die Roundtripzeit von einem Client zu einem Proxy von 2,8 Millisekunden anzeigt.](media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Wenn der Clientcomputer einer der wenigen wenigen mit Zugriff auf den Proxy Server (oder-Ausstieg) ist, können Sie den nächsten Testabschnitt ausführen, indem Sie eine Remoteverbindung mit diesem Computer herstellen, indem Sie die Eingabeaufforderungen ausführen, um von dort aus an eine Office 365-URL PsPing. Wenn Sie keinen Zugriff auf diesen Computer haben, können Sie sich mit ihren Netzwerkressourcen in Verbindung setzen, um Hilfe zum nächsten Bein zu erhalten und genaue Zahlen auf diese Weise abzurufen. Wenn dies nicht möglich ist, nehmen Sie eine PsPing gegen die fragliche Office 365-URL, und vergleichen Sie Sie mit der PsPing-oder Ping-Zeit für Ihren Proxy Server. 
  
Wenn Sie beispielsweise 51,84 Millisekunden vom Client zur Office 365-URL haben und Sie 2,8 Millisekunden vom Client zum Proxy (oder Ausgangspunkt) haben, haben Sie 49,04 Millisekunden vom Ausgang zu Office 365. Wenn Sie eine PsPing von 12,25 Millisekunden vom Client zum Proxy während der Höhe des Tages und 62,01 Millisekunden vom Client zur Office 365-URL haben, ist der durchschnittliche Wert für den Proxy Austritt an die Office 365-URL 49,76 Millisekunden.
  
![Zusätzliche Grafik, die den Ping in Millisekunden von Client zu Proxy neben Client zu Office 365 zeigt, sodass die Werte subtrahiert werden können.](media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
Im Hinblick auf die Problembehandlung finden Sie möglicherweise etwas interessantes, nur um diese Baselines beizubehalten. Wenn Sie beispielsweise feststellen, dass Sie in der Regel ungefähr 40 bis 59 Millisekunden Wartezeit vom Proxy-oder Ausstiegspunkt zur Office 365-URL haben und eine Client-zu-Proxy-oder Ausgangs Wartezeit von etwa 3 bis 7 Millisekunden haben (abhängig von der Menge des Netzwerkverkehrs, den Sie sehen g während dieser Tageszeit) dann werden Sie sicher wissen, dass etwas problematisch ist, wenn Ihre letzten drei Client-Proxy-oder Ausgangsbasis Linien eine Wartezeit von 45 Millisekunden aufweisen.
  
### <a name="advanced-methods"></a>Erweiterte Methoden

Wenn Sie wirklich wissen möchten, was mit Ihren Internet Anfragen an Office 365 geschieht, müssen Sie sich mit Netzwerkablaufverfolgungen vertraut machen. Es spielt keine Rolle, welche Tools Sie für diese Ablaufverfolgungen bevorzugen, HTTPWatch, netmon, Message Analyzer, Wireshark, Fiddler, Developer Dashboard Tool oder andere, solange dieses Tool den Netzwerkdatenverkehr erfassen und Filtern kann. In diesem Abschnitt wird angezeigt, dass es vorteilhaft ist, mehr als eines dieser Tools auszuführen, um ein umfassenderes Bild des Problems zu erhalten. Wenn Sie testen, fungieren einige dieser Tools auch als Proxys. Zu den Tools, die im Begleitartikel [Performance Troubleshooting Plan for Office 365](performance-troubleshooting-plan.md)verwendet werden, gehört [Netmon 3,4](https://www.microsoft.com/en-us/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/)oder [wireshark](https://www.wireshark.org/).
  
Das Erstellen einer Leistungsbasislinie ist der einfache Teil dieser Methode, und viele der Schritte sind identisch mit der Behandlung eines Leistungsproblems. Die fortgeschritteneren Methoden zum Erstellen von Baselines für die Leistung erfordern, dass Sie Netzwerkablaufverfolgungen übernehmen und speichern. In den meisten der Beispiele in diesem Artikel wird SharePoint Online verwendet, Sie sollten jedoch eine Liste allgemeiner Aktionen für die Office 365-Dienste entwickeln, die Sie testen und aufzeichnen möchten. Hier ist ein Basis Beispiel:
  
- Basisplan für SPO-* * Schritt 1: * * Durchsuchen der Homepage der SPO-Website und Ausführen einer Netzwerkablaufverfolgung. Speichern Sie die Ablaufverfolgung. 
    
- Basisplan für SPO- **Schritt 2:** suchen Sie nach einem Begriff (beispielsweise Ihrem Firmennamen) über die Unternehmenssuche, und führen Sie eine Netzwerkablaufverfolgung aus. Speichern Sie die Ablaufverfolgung. 
    
- Basisplan für SPO- **Schritt 3:** Hochladen einer umfangreichen Datei in eine SharePoint Online-Dokumentbibliothek und Ausführen einer Netzwerkablaufverfolgung. Speichern Sie die Ablaufverfolgung. 
    
- Basisplan für SPO- **Schritt 4:** Durchsuchen der Homepage der OneDrive-Website und Ausführen einer Netzwerkablaufverfolgung. Speichern Sie die Ablaufverfolgung. 
    
Diese Liste sollte die wichtigsten allgemeinen Aktionen einbeziehen, die Benutzer für SharePoint Online ausführen. Beachten Sie, dass der letzte Schritt zur Ablaufverfolgung von OneDrive for Business einen Vergleich zwischen der Last der SharePoint Online-Homepage (die häufig von Unternehmen angepasst wird) und der OneDrive for Business-Startseite erstellt wird, die selten angepasst wird. Dies ist ein sehr grundlegender Test bei einer langsamen ladenden SharePoint Online-Website. Sie können diese Unterschiede in Ihren Tests aufzeichnen.
  
Wenn Sie sich in einem Leistungsproblem befinden, sind viele der Schritte die gleichen wie beim Erstellen eines Basisplans. Netzwerkablaufverfolgungen werden kritisch, daher behandeln ** wir die nächsten wichtigen Ablaufverfolgungen. 
  
Um ein Leistungsproblem zu beheben, müssen Sie *gerade jetzt* eine Ablaufverfolgung zum Zeitpunkt des Leistungsproblems ausführen. Sie müssen über die geeigneten Tools verfügen, um Protokolle zu sammeln, und Sie benötigen einen Aktionsplan, also eine Liste der Problem Behandlungs Aktionen, die Sie ausführen müssen, um die besten Informationen zu sammeln, die Sie können. Als erstes müssen Sie das Datum und die Uhrzeit des Tests aufzeichnen, damit die Dateien in einem Ordner gespeichert werden können, der das Timing widerspiegelt. Als nächstes beschränken Sie sich auf die Problemschritte selbst. Dies sind die genauen Schritte, die Sie zum Testen verwenden. Vergessen Sie nicht die Grundlagen: Wenn das Problem nur mit Outlook besteht, stellen Sie sicher, dass das Problemverhalten nur in einem Office 365-Dienst auftritt. Wenn Sie den Umfang dieses Problems einschränken, können Sie sich auf die Lösung konzentrieren. 
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

