---
title: Plan zur Problembehandlung für Office 365
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 4/26/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
description: Müssen Sie wissen, die Schritte zum Identifizieren und Beheben von Problemen fällt ab, hängt und langsam zwischen SharePoint Online, OneDrive for Business, Exchange Online oder Skype für Business Online und Ihrer Clientcomputer? Vor dem Aufruf der Unterstützung kann in diesem Artikel Behebung von Leistungsproblemen Office 365 und auch einige der gängigsten Probleme beheben.
ms.openlocfilehash: 629e65fe6d35237f33ae06fdeec380c670cd5e62
ms.sourcegitcommit: 0466a88133a42e2db4245f972cecb371721c9b5d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "23849368"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Plan zur Problembehandlung für Office 365

Müssen Sie wissen, die Schritte zum Identifizieren und Beheben von Problemen fällt ab, hängt und langsam zwischen SharePoint Online, OneDrive for Business, Exchange Online oder Skype für Business Online und Ihrer Clientcomputer? Vor dem Aufruf der Unterstützung kann in diesem Artikel Behebung von Leistungsproblemen Office 365 und auch einige der gängigsten Probleme beheben.
  
Dieser Artikel ist tatsächlich eine Beispiel-Aktion planen, die Sie verwenden können, wertvolle Erfassen von Daten zu Leistungsproblems unverändert passiert. In diesem Artikel sind auch einige Topthemen enthalten.
    
Wenn Sie neu sind in Netzwerk-Leistung und einen langfristig Plan zum Überwachen der Leistung zwischen Clientcomputern und Office 365 vornehmen möchten, sehen Sie sich die [Office 365 Performance tuning und Problembehandlung - Administrator und IT-Spezialisten](performance-tuning-using-baselines-and-history.md).
  
## <a name="sample-performance-troubleshooting-action-plan"></a>Beispiel Leistung zur Problembehandlung Aktivitätsplan

Diese Aktionsplan besteht aus zwei Teilen; eine Vorbereitungsphase und Protokollierung Phasen. Wenn Sie ein Leistungsproblem jetzt haben und Erfassung ist erforderlich, können Sie mit diesem Plan sofort starten.
  
 **Vorbereiten des Clientcomputers**
  
- Hier finden Sie einen Clientcomputer, der das Leistungsproblem reproduzieren kann. Dieser Computer wird im Verlauf der Problembehandlung verwendet werden.
    
- Notieren Sie die Schritte, die dazu führen, das Leistungsproblem dass erfolgen, damit Sie bereit sind, wenn es darum Zeit bis zum Testen geht.
    
- Installieren der Tools zum Sammeln und Aufzeichnen der Informationen:
    
  - Installieren Sie [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865) (oder verwenden Sie eine entsprechende Tool zur netzwerkablaufverfolgung). 
    
  - Installieren Sie die kostenlose grundlegende Edition von [HTTPWatch](https://www.httpwatch.com/download/) (oder verwenden Sie eine gleichwertige Tool zur Netzwerkablaufverfolgung). 
    
  - Verwenden Sie eine Aufzeichnung Bildschirm, oder führen Sie die Schritte-Aufzeichnung (PSR.exe), die mit Windows Vista und höher enthalten ist, um die Schritte aufzeichnen, die Sie während der Tests durchführen.
    
 **Melden Sie sich das Leistungsproblem**
  
- Schließen Sie alle zusätzlichen Internetbrowser.
    
- Starten Sie die Schritte Aufzeichnung oder einer anderen Bildschirm Aufzeichnung.
    
- Starten Sie Ihre Netmon Capture (oder ein Tool zur netzwerkablaufverfolgung).
    
- Löschen Sie den DNS-Cache auf dem Clientcomputer über die Befehlszeile durch Eingabe von Ipconfig/flushdns.
    
- Starten Sie eine neue Browsersitzung und HTTPWatch zu aktivieren.
    
- Optional: Wenn Sie Exchange Online testen, führen Sie das Exchange-Client-Leistung Analyzer Tool in der Office 365-Verwaltungskonsole.
    
- Reproduzieren Sie die genauen Schritte, die das Leistungsproblem verursachen.
    
- Beenden der Netmon oder anderen Tool Trace.
    
- Führen Sie an der Befehlszeile eine Trace Route zu Ihrem Office 365-Abonnement, indem Sie den folgenden Befehl eingeben und dann die EINGABETASTE drücken:
    
    `tracert \< *subscriptionname*  \>.onmicrosoft.com` 
    
- Beenden Sie die Schritte Aufzeichnung, und speichern Sie das Video. Achten Sie darauf, dass Datum und Zeitpunkt der Erfassung und gibt an, ob es Leistung gut oder schlecht zeigt.
    
- Speichern Sie die Ablaufverfolgungsdateien. In diesem Fall müssen Sie Datum und Zeitpunkt der Erfassung und gibt an, ob es Leistung gut oder schlecht zeigt.
    
Wenn Sie nicht mit der Ausführung der in diesem Artikel erwähnten Tools vertraut sind, keine Sorge, da wir die entsprechenden Schritte weiter bereitstellen. Wenn Sie mit der dieser Art von Netzwerk sammelt vertraut sind, können Sie [wie Baselines gesammelt](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), die beschreibt, Filtern und lesen die Protokolle überspringen. 
  
## <a name="flush-the-dns-cache-first"></a>Leeren des DNS-Caches zuerst

Warum? Durch den DNS-Cache leeren beginnen Sie die Tests von vorn. Durch Löschen des Caches, sind Sie den Inhalt der DNS-Auflösung auf die aktuelle Einträge zurücksetzen. Denken Sie daran, dass eine Bereinigung Einträge in der Datei HOSTs nicht entfernt werden. Wenn Sie die Datei Hosteinträge häufig verwenden, sollten Sie diese Einträge in eine Datei in ein anderes Verzeichnis kopieren und leeren Sie die HOST-Datei.
  
 **Leeren Sie den DNS-Auflösungscache**
  
1. Öffnen Sie das Eingabeaufforderungsfenster (entweder **Starten** \> **Ausführen** \> **Cmd** oder **Windows-Taste** \> **Cmd**).
    
2. Geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE:`ipconfig /flushdns`
    
## <a name="netmon"></a>Netmon

Microsoft Netzwerk Monitoring Tool ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) analysiert Pakete, die Datenverkehr zwischen Computern in Netzwerken übergibt. Mithilfe von Netmon verfolgen Datenverkehr mit Office 365 Sie erfassen können, anzeigen, und lesen die Paket-Headern, dazwischenliegende Geräte zu identifizieren, überprüfen Sie auf Netzwerk-Hardware wichtig für Paketverluste gesucht, und führen Sie den Fluss des Datenverkehrs zwischen Computern in Ihrem Unternehmen Netzwerk- und Office 365. Da der eigentliche Text des Datenverkehrs verschlüsselt ist, d. h., es (Reisen an Port 443 über SSL/TLS, Sie können nicht gelesen werden die Dateien gesendet werden. In diesem Fall erhalten Sie eine ungefilterte Trace des Pfads, die das Paket akzeptiert, die Sie hilfreich sein können Sie das Problem Verhalten nachverfolgen.
  
Stellen Sie sicher, dass zu diesem Zeitpunkt keinen Filter angewendet werden. Stattdessen führen Sie die Schritte aus, und führen Sie das Problem vor, bevor Sie die Ablaufverfolgung beenden und speichern.
  
Nach der Installation von Netmon 3.4 Öffnen Sie das Tool, und gehen Sie folgendermaßen vor:
  
 **Nutzen Sie Netzwerkmonitor und reproduzieren Sie das Problem**
  
1. Starten Sie Netmon 3.4.
    
    Es gibt drei Bereiche auf **der Startseite** : **Letzte erfasst wird**, **Wählen Sie Netzwerke**und die erste Schritte mit Microsoft Network Monitor 3.4 **. Beachten Sie**. Das Wählen Netzwerke auch erhalten eine Liste der standardmäßigen Netzwerke Sie von dem Sie erfassen können. Stellen Sie sicher, dass Netzwerkkarten hier ausgewählt sind.
    
2. Klicken Sie am oberen Rand der Seite zum **Starten** **Neuer erfassen** . Dadurch wird eine neue Registerkarte neben der Registerkarte Seite **Starten** namens **erfassen 1**hinzugefügt.
    
    ![Nemon des Benutzers-Schnittstelle mit erfassen neu starten, und Beenden von Schaltflächen hervorgehoben.](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)
  
3. Um den einfachen aufzuzeichnen, klicken Sie auf der Symbolleiste auf **Start** . 
    
4. Reproduzieren Sie die Schritte, die ein Leistungsproblem darstellen.
    
5. Klicken Sie auf **Beenden** \> **Datei** \> **Speichern unter**. Denken Sie daran, das Datum und die Uhrzeit die Angabe einer Zeitzone zu gewähren oder um erwähnen, wenn es fehlerhaft oder eine gute Leistung veranschaulicht.
    
## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) kommt berechnete, und eine kostenlose Edition. Die kostenlose grundlegende Edition deckt alles, was Sie für diesen Test benötigen. HTTPWatch Monitore Netzwerk-Datenverkehr und der Seite des Ladens direkt über das Browserfenster. HTTPWatch ist ein plug-in für Internet Explorer, die Leistung grafisch beschreibt. Die Analyse kann gespeichert und in HTTPWatch Studio angezeigt werden. 
  
> [!NOTE]
> Wenn Sie einen anderen Browser, wie Firefox, Google Chrome, verwenden, oder wenn Sie HTTPWatch in Internet Explorer nicht installieren können, öffnen Sie ein neues Browserfenster, und drücken Sie F12 auf der Tastatur. Das Popup Developer-Tool sollte am unteren Rand der Browser angezeigt werden. Wenn Sie Opera verwenden, drücken Sie STRG + UMSCHALT + I für Web Inspector, klicken Sie dann klicken Sie auf der Registerkarte **Netzwerk** , und abgeschlossen Sie die unten beschriebenen Tests sind. Die Informationen werden geringfügig, aber Ladezeiten werden weiterhin in Millisekunden angezeigt werden. > HTTPWatch ist auch sehr hilfreich bei Problemen mit SharePoint Online Seitenladezeiten. 
  
 **Führen Sie HTTPWatch und reproduzieren Sie das Problem**
  
1. HTTPWatch ist ein Browser-Plug-in, das Tool im Browser Verfügbarmachen geringfügig für die einzelnen Versionen von Internet Explorer. Im Browser Internet Explorer finden Sie in der Regel HTTPWatch unter der Leiste Befehle.</br>Wenn Sie die HTTPWatch-Plug-in im Browserfenster sehen, die Version des Browsers Kontrollkästchen durch Klicken Sie auf Hilfe \> zu, oder klicken Sie in späteren Versionen von Internet Explorer auf die Zahnrad-Symbol und zu Internet Explorer. Um die **Befehle** Leiste zu starten, mit der rechten Maustaste in der Menüleiste in Internet Explorer, und klicken Sie auf **Befehle Leiste**. In der Vergangenheit HTTPWatch wurde verknüpft mit den Befehlen und das Explorer-Leisten, also einmal Sie installieren, wenn das Symbol (auch nach dem Neustart) Überprüfen von **Tools**und Ihrer Symbolleisten für das Symbol nicht sofort angezeigt. Denken Sie daran, dass Symbolleisten angepasst werden können und Optionen für diese hinzugefügt werden können.</br>
    ![Internet Explorer Befehl Symbolleiste HTTPWatch Symbol angezeigt.](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)
  
2. Starten Sie HTTPWatch in einer Internet Explorer-Browserfenster. Es wird an den Browser am unteren Rand das Fenster verankert angezeigt. Klicken Sie auf **Aufzeichnen**.
    
3. Reproduzieren Sie die genauen Schritte das Leistungsproblem beteiligt. Klicken Sie auf die Schaltfläche **Beenden** in HTTPWatch. 
    
4. **Speichern Sie** die HTTPWatch oder **per E-Mail senden**. Denken Sie daran, nennen Sie die Datei so, dass es enthält Datums-und Uhrzeitinformationen und der Angabe, ob Ihr Video veranschaulicht die Leistung gut oder schlecht enthält.</br>![HTTPWatch mit der Netzwerk-Registerkarte für eine Seitenladung der Office 365-Homepage.](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)</br>
    Dieser Screenshot hat ihren Ursprung die Professional-Version von HTTPWatch. Sie können in der Basisversion auf einem Computer mit einem Professional-Version übernommen Spuren öffnen und Lesen sie es. Zusätzlicher Informationen kann in die durch diese Methode verfolgen verfügbar sein.
    
## <a name="problem-steps-recorder"></a>Problem Schritte Aufzeichnung

Schritte Aufzeichnung oder PSR.exe, können Sie Probleme aufzeichnen, wie sie auftreten können. Es ist sehr nützlich und sehr einfache ausführen.
  
 **Führen Sie Problem Schritte Aufzeichnung (PSR.exe) zum Aufzeichnen Ihrer Arbeit**
  
1. Verwenden Sie entweder **Start** \> **Ausführen** \> geben **PSR.exe** \> **OK**, oder klicken Sie auf der **Windows-Taste** \> geben **PSR.exe** \> und drücken Sie dann die EINGABETASTE. 
    
2. Wenn das kleine PSR.exe-Fenster angezeigt wird, klicken Sie auf **Start-Datensatz** und reproduzieren Sie die Schritte, die das Leistungsproblem zu reproduzieren. Bedarf durch Klicken auf **Kommentare hinzufügen**, können Sie Kommentare hinzufügen.
    
3. Klicken Sie auf **Datensatz zu beenden** , wenn Sie die Schritte ausgeführt haben. Wenn das Leistungsproblem eine Seite gerendert wird, warten Sie auf der Seite gerendert werden, bevor Sie die Aufzeichnung beenden. 
    
4. Klicken Sie auf **Speichern**.
    
![Ein Screenshot des Schritte Aufzeichnung oder PSR.exe.](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
Datum und Uhrzeit wird für Sie aufgezeichnet. Dieser links und Ihre a. auf Netzwerkmonitor und HTTPWatch rechtzeitig und hilft bei der Problembehandlung mit doppelter Genauigkeit. Das Datum und die Uhrzeit im Datensatz a. anzeigen können, dass eine Minute übergeben zwischen der Anmeldung und im Browser die URL und die teilweise Rendern der Admin-Website, beispielsweise.
  
## <a name="read-your-traces"></a>Lesen Sie die Spuren

Es ist nicht möglich, alles über Netzwerk und Behandlung von Leistungsproblemen zu vermitteln, die einer Person über einen Artikel wissen muss. Eine gute Leistung erste dauert Erfahrung und wissen, wie Ihr Netzwerk funktioniert und in der Regel ausgeführt wird. Es ist jedoch möglich aufrunden auf eine Liste der häufigsten Probleme und zeigen, wie Tools, die gängigsten Probleme zu beseitigen erleichtern können.
  
Wenn Sie wissen, lesen die netzwerkablaufverfolgung für Ihre Office 365-Websites übernehmen möchten, ist keine bessere Lehrer als Spuren von Seite lädt regelmäßig zu erstellen und erlangen Erfahrung zu lesen. Beispielsweise wenn Sie eine Chance haben, laden Sie Office 365-Dienst und verfolgen Sie des Prozesses. Filtern der Verfolgung für DNS-Datenverkehr, oder suchen Sie die FrameData für den Namen des Diensts, den Sie angegeben haben. Überprüft die Ablaufverfolgung um eine Vorstellung vom Zweck der Schritte zu erhalten, die auftreten, wenn der Dienst geladen wird. So können Sie die hier erfahren Sie, welche normalen Laden der Seite sollte wie folgt aussehen und bei der Problembehandlung, insbesondere zur Umgehung der Leistung sollte Sie fehlerhafte Spuren vergleichen kann lernen Sie die viel.
  
Netmon verwendet Microsoft Intellisense im Feld Filter anzeigen. IntelliSense oder intelligenten Code Abschluss und ist dabei, in dem Sie geben Sie in einem Punkt und alle verfügbare Optionen in ein Dropdown-Auswahlfeld angezeigt werden. Wenn beispielsweise Sie TCP-Fensterskalierung sorgen sind, finden Sie die Möglichkeit, einen Filter (z. B. `.protocol.tcp.window < 100`) über dieses Verfahren.
  
![Screenshot der Netmon darauf hinweist, dass das Feld Anzeigefilter Intellisense verwendet.](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
Netmon Spuren können viel Datenverkehr enthalten. Wenn Sie bereits Erfahrung mit Lesen nicht, ist es wahrscheinlich überfordert Trace beim ersten öffnen können. Der erste Schritt ist das Signal von der Hintergrundgeräusche in die Ablaufverfolgung zu trennen. Sie mit Office 365 getestet, und das ist der Datenverkehr, den Sie anzeigen möchten. Wenn Sie zum Navigieren in Spuren werden verwendet, benötigen Sie möglicherweise nicht in dieser Liste.
  
Datenverkehr zwischen Client und Office 365 Grundsätze über TLS, was bedeutet, dass der Textkörper des Datenverkehrs verschlüsselte und im generischen Netzwerkmonitor nicht gelesen werden. Leistungsanalyse muss nicht die Einzelheiten Informationen in das Paket kennen. Es ist jedoch sehr Paket-Headern und die darin enthaltenen Informationen interessiert.
  
 **Tipps, um eine gute trace**
  
- Kennen Sie den Wert der IPv4 oder IPv6-Adresse des Clientcomputers. Sie können dies über die Befehlszeile abrufen, indem Sie **IPConfig** eingeben und dann die EINGABETASTE drücken. Diese Adresse kennen, können Sie die auf einen Blick erkennen, ob der Datenverkehr in der Verfolgung direkt Ihrer Clientcomputer umfasst. Wenn ein bekannter Proxy vorhanden ist, es ping, und erhalten Sie seine IP-Adresse. 
    
- Leeren Sie den DNS-Auflösungscache und wenn möglich, beenden Sie alle Browser mit Ausnahme der in dem Sie die Tests ausgeführt werden. Wenn Sie nicht möglich sind, beispielsweise wenn Unterstützung einige browserbasiertes Tool verwendet, um den Desktop des Clientcomputers, finden Sie unter bereiten Sie Ihre Trace gefiltert.
    
- Suchen Sie in einer Ablaufverfolgung für beschäftigt den Office 365-Dienst, den Sie verwenden. Wenn Sie des Datenverkehrs vor nie oder selten gesehen haben, ist dies ein Schritt hilfreich, die von anderen Netzwerk Noise das Leistungsproblem trennt. Es gibt einige Methoden zur Verfügung. Direkt vor der Prüfung können Ping oder PsPing, auf die URL der bestimmten Dienst ( `ping outlook.office365.com` und/oder `psping -4 microsoft-my.sharepoint.com:443`, Beispiele). Sie können auch problemlos finden, PsPing in Netzwerkmonitor (anhand des Namens des Prozesses). Die erhalten Sie eines Ort für die Suche zu starten.
    
    Wenn Sie Netmon Tracing nur zum Zeitpunkt des Problems verwenden, ist das zu kein Problem. Um sich selbst auszurichten, verwenden Sie einen Filter wie `ContainsBin(FrameData, ASCII, "office")` oder `ContainsBin(FrameData, ASCII, "outlook")`. Sie können die Framenummer Ihres aus der Ablaufverfolgungsdatei aufzeichnen. Sie sollten auch im Bereich Zusammenfassung Frame ganz nach rechts Blättern und suchen Sie nach der Konversations-ID-Spalte. Es ist eine Zahl, die es für die ID des dieser bestimmten Unterhaltung, die Sie können auch aufzeichnen und sehen Sie sich später isoliert angegeben. Denken Sie daran, um diesen Filter zu entfernen, bevor alle anderen Filtern anwenden.
    
> [!TIP]
> Netmon hat viele nützliche integrierte Filter. Versuchen Sie die Schaltfläche "Load Filter" am oberen Rand der Filterbereich **Anzeigen** . 
  
![Hier finden Sie Ihre IP mithilfe von PSPing an der Befehlszeile auf dem Clientcomputer.](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![Netzwerkmonitor vom Client im gleichen Befehl PSPing durch den Filter TCP angezeigt. Flags.Syn == 1.](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
Machen Sie sich mit Ihren Datenverkehr, und erfahren Sie mehr über die Informationen zu suchen, die Sie benötigen. Beispielsweise erfahren Sie, um zu bestimmen, welche Paket in der Verfolgung den ersten Verweis auf die Office 365-Dienst hat, den Sie verwenden (wie "Outlook").
    
Verbunddiagramme Office 365 Outlook Online als Beispiel, beginnt der Datenverkehr etwa wie folgt:
  
- DNS-Abfragen und DNS-Antwort für outlook.office365.com mit übereinstimmenden QueryIDs. Es ist wichtig, zu beachten, dass die Uhrzeit-Offset für diese Turn-versehen, sowie Where in der ganzen Welt der Office 365 globale DNS sendet die Anforderung für namensauflösung. Im Idealfall, möglich, sondern als halb auf der ganzen Welt lokal. (Dies kann folgen einige DNS-Datenverkehr die online-Anmeldung.)
    
- Eine HTTP GET anfordern, dessen Status Berichten dauerhaft (301) verschoben
    
- RWS Datenverkehr einschließlich RWS verbinden Anforderungen und Antworten verbinden. (Dies ist Remote Winsock Herstellen einer Verbindung für Sie.)
    
- TCP SYN und TCP SYN/Bestätigung Unterhaltung. Ein Großteil der Einstellungen in dieser Unterhaltung die Leistung beeinträchtigen.
    
- Dann eine Reihe von TLS:TLS Datenverkehr ist, in denen die TLS-Handshake und TLS-Zertifikat Unterhaltungen stattfinden. (Beachten Sie, dass die Daten verschlüsselt werden, über den geschützten SSL/TLS).
    
Alle Teile des Datenverkehrs wichtige und verbunden sind, aber kleiner Teile von Trace enthalten Informationen im Hinblick auf die Behandlung von Leistungsproblemen besonders wichtig, damit wir auf diese Bereiche näher erläutert wird. Darüber hinaus da wir genügend Office 365-Leistung bei Microsoft auf Kompilieren einer Top 10 Liste der häufig auftretender Probleme Problembehandlung durchgeführt haben, wir konzentrieren uns diese Probleme und wie Sie die Tools verwenden, die wir ihnen, weiter Stamm haben.
  
Wenn Sie noch nicht installiert alle bereit, die Matrix unten stellt verschiedene Tools verwenden. Sofern möglich. Der Installationspfade werden Links angezeigt. Die Liste enthält allgemeine Tracing Netzwerktools wie [Netmon](https://www.microsoft.com/en-us/download/details.aspx?id=4865) und [Wireshark](https://www.wireshark.org/)verwenden Sie eine beliebige Tracing-Tool, das Sie mit und in denen Sie vertraut sind sind Netzwerkverkehr Filtern vertraut sind. Wenn Sie testen, beachten Sie:
  
-  *Schließen Sie Ihre Browser und Testen mit nur ein Browser ausgeführt* – Dies reduziert den gesamten Datenverkehr Sie erfassen. Dies stellt einen weniger ausgelasteten Trace. 
    
-  *Leeren Sie den DNS-Auflösungscache auf dem Clientcomputer* - Dadurch erhalten Sie vorn beim Starten, um Ihre aufzuzeichnen für eine Bereinigung Trace. 
    
## <a name="some-top-issues"></a>Einige Topthemen

Einige häufig auftretende Probleme, die Sie möglicherweise stoßen und Vorgehensweise finden sie in Ihrem Netzwerk-Trace.

### <a name="tcp-windows-scaling"></a>TCP-Windows-Skalierung

Gefunden in das SYN - möglicherweise SYN/Bestätigung Legacy oder Alterung Hardware nicht TCP Windows Skalierung nutzen.  Ohne ordnungsgemäßen TCP Windows Einstellungen Skalierung füllt Puffers für den 16-Bit in TCP-Headern Millisekunden.  Datenverkehr kann nicht fortgesetzt werden, bis der Client eine Bestätigung, dass die ursprünglichen Daten eingegangen sind empfängt, wodurch Verzögerungen senden.

#### <a name="tools"></a>Tools:

- Netmon
- Wireshark 

#### <a name="what-youre-looking-for"></a>Was Sie suchen:

Suchen Sie nach der SYN - SYN/Bestätigung Datenverkehr in Ihrem Netzwerk-Trace.  Verwenden Sie einen Filter wie in Netmon, `tcp.flags.syn == 1`. Dieser Filter ist in Wireshark identisch.  

![Filter im Netmon oder Wireshark für SYN-Pakete für beide Tools: TCP. Flags.Syn == 1.](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)         
Beachten Sie, dass für jede SYN eine Quelle (Quellport) Portnummer, die der Zielport (Zielport) die zugehörige Danksagung (SYN/Bestätigung) zugeordnet ist. 

Wenn den Skalierung der Windows-Wert, der durch die Verbindung zum Netzwerk verwendet wird, erweitern Sie zuerst das SYN und anschließend das zugehörige SYN/Bestätigung  

![Grafik veranschaulicht, die eine Verfolgung, zum Abrufen der Zeitabstand Quellport, Zielport überein.](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a>TCP-Leerlaufzeit Einstellungen

In der Vergangenheit sind die meisten Umkreisnetzwerke für vorübergehende Verbindungen, was bedeutet, dass Verbindungen im Leerlauf im Allgemeinen gekündigt werden konfiguriert. Im Leerlauf TCP-Sitzungen können durch Proxys und Firewalls an mehr als 100 bis 300 Sekunden beendet werden. Dies ist für Outlook Online problematisch, weil es erstellt und langfristige Verbindungen verwendet, ob sie sich im Leerlauf oder nicht befinden.  

Beim Verbindungen werden vom Proxy beendet oder Firewallgeräten, der Client wird nicht darüber informiert, und ein Versuch zum Verwenden von Outlook Online bedeutet einen Clientcomputer, wiederholt, versucht, die Verbindung, bevor Sie eine neue wiederaufnehmen. Möglicherweise hängt im Produkt, fordert oder geringe Leistung beim Laden der Seite angezeigt.

#### <a name="tools"></a>Tools:

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Wonach Sie suchen:

Betrachten Sie das Feld Uhrzeit-Offset für ein Round-Trip in Netmon aus. Ein Roundtrip ist die Zeit zwischen Client eine Anforderung an den Server gesendet und Empfangen einer Antwort zurück. Zwischen dem Client und Austritt überprüfen (z. B. Client –\> Proxy), oder der Office 365-Client (Client –\> Office 365). Sie können dies in viele andere Arten von Paketen finden Sie unter. 

Beispielsweise kann der Filter in Netmon folgendermaßen aussehen `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`, oder im Wireshark, `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.  

> [!TIP]
> Weiß nicht, ob die IP-Adresse in Ihrem Trace zu Ihrem DNS-Server gehört? Versuchen Sie, Nachschlagen in der Befehlszeile. Klicken Sie auf **Start** \> **Ausführen** \> und geben Sie **cmd ein**, oder drücken Sie **Windows** \> und geben Sie **cmd ein**. Geben Sie an der Eingabeaufforderung `nslookup <the IP address from the network trace>`. Verwenden Sie Nslookup mit Ihrem eigenen Computer IP-Adresse, um zu testen. > Eine Liste der Microsoft IP-Bereichen finden Sie unter [Office 365-URLs und IP-Adressbereiche](https://technet.microsoft.com/en-us/library/hh373144.aspx). 

Wenn ein Fehler auftritt, insbesondere in TLS:TLS Pakete, die den Durchgang von Anwendungsdaten anzeigen erwarten lange Zeit versetzt in diesem Fall (Online Outlook) angezeigt wird (in Netmon finden Sie beispielsweise Daten Anwendungspaketen über `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`). Eine reibungslose Entwicklung in der Zeit sollte über die Sitzung angezeigt werden. Wenn Sie lange Verzögerung angezeigt, wenn Ihr Outlook Online aktualisieren, kann dies ein hohes Maß setzt gesendet werden Ursachen zugrunde liegen. 

### <a name="latencyround-trip-time"></a>Wartezeit/Round Reisedauer 

Wartezeit ist ein Maß, die viel je nach viele Variablen, solche Alterung Geräte aktualisieren, Hinzufügen von eine große Anzahl von Benutzern zu einem Netzwerk und den Prozentsatz der allgemeinen Bandbreite, die anderen Aufgaben auf eine Netzwerkverbindung ändern können. 

Bandbreitenrechnern für Office 365 sind auf dieser Seite [netzwerkplanung und leistungsoptimierung für Office 365](network-planning-and-performance.md) verfügbar.  

Messen die Geschwindigkeit der Verbindung oder die ISP-Verbindung Bandbreite erforderlich? Führen Sie diese Website (oder Websites wie es): [Speedtest offizielle Website](https://www.speedtest.net/)und [Pingtest](http://www.pingtest.net/).

#### <a name="tools"></a>Tools:

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Wonach Sie suchen:

Zum Nachverfolgen von Wartezeit in einer Ablaufverfolgung für profitieren Sie von IP-Adresse des Clientcomputers und die IP-Adresse des DNS-Servers in Office 365 eingetragen haben. Dies ist zum Filtern von einfacher Trace. Wenn Sie eine Verbindung herstellen, benötigen Sie Ihre Client-Computer-IP-Adresse, die Proxy/Ausgang IP-Adresse und die Office 365 DNS-IP-Adresse, um die Arbeit zu erleichtern.  

Eine Ping-Anforderung an outlook.office365.com gesendet wird der Name des Datencenters die Anforderung empfangen informieren, auch wenn Ping *kann* nicht zum Herstellen einer Verbindung mit der Marke aufeinander folgenden ICMP-Pakete senden können. Wenn Sie PsPing (ein kostenloses Tool zum Herunterladen) und den Port (443) spezifisch und vielleicht Verwendung IPv4 (-4) Sie eine durchschnittliche round-trip-Zeit für gesendeten Pakete erhalten. Dies funktioniert dies bei anderen URLs in der Office 365-Dienste wie `psping -4 yourSite.sharepoint.com:443`. Sie können sogar eine Anzahl von Ping zum Abrufen einer größeren Beispiel für die durchschnittliche, versuchen Sie es etwa wie folgt angeben: `psping -4 -n 20 yourSite-my.sharepoint.com:443`.  

> [!NOTE]
> PsPing senden nicht ICMP-Pakete. Es Ping-Signale mit TCP-Pakete über einen bestimmten Port, sodass Sie eine, den Sie kennen verwenden können, geöffnet sein. In Office 365, den geschützten SSL/TLS verwendet wird, wiederholen Sie den Port anfügen: 443 in Ihrer PsPing.

![Screenshot, der einen Ping Auflösen von outlook.office365.com und eine PSPing mit den 443 dieselben Schritte, aber auch eine durchschnittliche Zeit 6.5ms reporting anzeigt.](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)        

Wenn Sie die langsame Leistung Office 365-Seite während der Netzwerk-Trace geladen, sollten Sie eine Netmon oder Wireshark Verfolgung für filtern `DNS`. Dies ist einer der richtige IP-Adressen.  

Hier sind die Schritte durchführen, um Ihre Netmon, um die IP-Adresse (und betrachten Sie DNS-Wartezeit) zu filtern. In diesem Beispiel wird outlook.office365.com verwendet, aber Sie können auch die URL einer SharePoint Online-Mandanten (beispielsweise hithere.sharepoint.com).  

1. Pingen Sie die URL `ping outlook.office365.com` und in den Ergebnissen, notieren Sie sich den Namen und die IP-Adresse des DNS-Servers an die Ping-Anforderung gesendet. 
2. Netzwerk Spur Öffnen der Seite oder erhalten Sie wie folgt der Aktion, die das Leistungsproblem oder, wenn der Ping-Befehl, selbst einen hohen Wartezeit angezeigt Netzwerk verfolgen sie. 
3. Öffnen Sie die Ablaufverfolgung in Netmon und Filter für DNS (dieser Filter auch in Wireshark, ist jedoch zu Fall vertrauliche `-- dns`). Da Sie den Namen des DNS-Servers aus Ihrer Ping kennen können Sie auch weitere statt in Netmon wie folgt filtern: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")` , welche sieht wie dies im Wireshark Dns und Rahmen "Namnorthwest" enthält.</br>Öffnen Sie das Antwortpaket, und klicken Sie im Fenster des Netmon Frame Details auf DNS, um weitere Informationen zu erweitern. In der DNS-Informationen, die Sie die IP-Adresse des DNS-Servers, die die Anforderung zum in Office 365 – hinausgehen finden benötigen Sie diese IP-Adresse für den nächsten Schritt (das PsPing-Tool). Entfernen Sie den Filter, mit der rechten Maustaste auf die DNS-Antwort Netmons Frame sagen \> Unterhaltungen suchen \> DNS, um die DNS-Abfrage und Antwort Side-by-Side finden Sie unter. 
4. Beachten Sie außerdem in Netmon der Uhrzeit-Offset Spalte zwischen dem DNS-Anforderung und Antwort. Im nächsten Schritt, leicht zu installieren und verwenden [PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) kommt Tool in äußerst praktisch, da ICMP häufig auf Firewalls blockiert ist und da PsPing elegante Wartezeit in Millisekunden nachverfolgt werden. PsPing schließt eine TCP-Verbindung mit einer Adresse und Port (in unseren Groß-/Kleinschreibung open Port 443) ab. 
5. Installieren Sie PsPing. 
6. Öffnen Sie ein Eingabeaufforderungsfenster (Starten \> ausführen \> Geben Sie cmd ein, oder Windows-Taste \> Geben Sie cmd ein), und wechseln Sie zu dem Verzeichnis, in dem Sie zum Ausführen des Befehls PsPing PsPing installiert. In meiner Beispielen können Sie sehen, dass ich einen Ordner 'Korrektur' auf der Stammebene der C. vorgenommen Sie können auch für den Schnellzugriff vornehmen. 
7. Geben Sie den Befehl ein, sodass Sie Ihre PsPing für die IP-Adresse des Office 365 DNS-Servers aus der früheren Netzwerkmonitor tätigen – Denken Sie daran, die Portnummer hinzufügen. </br>Anders ausgedrückt, `psping -n 20 132.245.24.82:445`. Dadurch Sie eine Auswahl von 20 Ping und durchschnittliche Wartezeit bei PsPing beendet. 

Wenn Sie über einen Proxyserver zu Office 365 Vorhaben, sind die Schritte etwas unterschiedlich. Würden Sie ersten PsPing auf den Proxyserver eine durchschnittliche Wartezeit in Millisekunden an Proxy/Ausgang und nutzen, und führen Sie dann entweder PsPing für den Proxy, oder auf einem Computer mit einer direkten Internetverbindung, um den fehlenden Wert (eine zu Office 365 und Back) abzurufen.  

Wenn PsPing aus dem Proxy ausgeführt werden soll, müssen Sie zwei Millisekunde Werte: Clientcomputer Proxyserver oder Austritt und Proxy-Server zu Office 365. Und Sie fertig sind. Nun, Werte, trotzdem aufzuzeichnen.  

Wenn Sie PsPing auf einem anderen Clientcomputer, die eine direkte Verbindung mit dem Internet verfügt ausführen, d. h., ohne einen Proxy müssen Sie zwei Millisekunde Werte: Clientcomputer Proxyserver oder Austritt und Clientcomputer zu Office 365. In diesem Fall subtrahiert den Wert des Clientcomputers auf Proxy-Server oder Ausgang, zeigen Sie den Wert des Clientcomputers zu Office 365, und Sie müssen die Zeit Zahlen vom Clientcomputer auf die Proxy-Server oder Ausgang von Proxy-Server oder Ausgang zeigen Sie auf problemlos bewältigen lassen CE 365. 

Jedoch wenn Sie einen Clientcomputer in der betroffener Speicherort finden können, die direkt verbunden ist, oder umgeht den Proxy, können Sie auswählen, um festzustellen, ob das Problem gibt es zunächst reproduziert und testen, danach mit. 

Wartezeit, können Ressourcenverfügbarkeitsdaten in Netzwerkmonitor, diese zusätzlichen Millisekunden oben, hinzufügen, wenn viele in einer bestimmten Sitzung vorhanden sind.  

![Allgemeine Wartezeit in Netmon, wobei die Netmon-Standardspalte für die Zeitdifferenz der Framezusammenfassung hinzugefügt wurde.](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> Ihre IP-Adresse ist möglicherweise anders als die IP-Adressen hier gezeigte, beispielsweise Ihre Ping etwa Weitere 157.56.0.0/16 oder einem ähnlichen Bereich zurückgeben kann. Checken Sie eine Liste von Office 365 verwendete Bereiche [Office 365-URLs und IP-Adressbereiche](https://technet.microsoft.com/en-us/library/hh373144.aspx). 

Denken Sie daran, die alle Knoten zu erweitern (es ist eine Schaltfläche im oberen Bereich für diese), wenn Sie für beispielsweise 132.245 suchen möchten.

### <a name="proxy-authentication"></a>Proxy-Authentifizierung

Dies gilt nur für Sie, wenn Sie über einen Proxyserver Vorhaben. Wenn dies nicht der Fall ist, können Sie diese Schritte überspringen. Wenn ordnungsgemäß funktioniert, sollten Proxyauthentifizierung in Millisekunden, ständig stattfinden. Sie sollten nicht zeitweilige schlechter Leistung während Spitzenzeiten (z. b) finden Sie unter.  

Wenn Proxyauthentifizierung jedes Mal auf, eine neue TCP-Verbindung zu Office 365 zum Abrufen von Informationen zu erstellen ist, müssen Sie über einen Authentifizierungsprozess im Hintergrund übergeben. Ja, beispielsweise beim Wechsel vom Kalender auf E-Mail in Outlook Online, Sie authentifiziert. Und in SharePoint Online, wenn eine Seite-Medien oder der Daten aus mehreren Websites oder Speicherorte, Sie authentifiziert für jeden anderen TCP-Verbindung, die zum Rendern der Daten erforderlich ist.  

In Outlook Online möglicherweise langsam Ladezeiten, wenn Sie zwischen Kalender und Ihr Postfach wechseln oder langsame Seite in SharePoint Online lädt. Es gibt jedoch auch andere nicht aufgelisteten Symptome. 

Proxyauthentifizierung ist eine Einstellung auf Ihrem Ausgang Proxyserver. Wenn sie ein Leistungsproblem mit Office 365 verursacht, finden Sie in Ihrer networking-Team.  

#### <a name="tool"></a>Tool: 

- Netmon
- Wireshark 

#### <a name="what-to-look-for"></a>Wonach Sie suchen:

Proxy-Authentifizierung findet statt, wenn eine neue Sitzung TCP häufig Dateien oder Info vom Server angefordert oder Info angeben, vorhanden sein muss. Beispielsweise können Sie Proxyauthentifizierung um HTTP GET oder HTTP POST-Anforderungen finden Sie unter. Wenn die Frames angezeigt, in dem die Anforderungen in Ihrer Trace Authentifizierung werden, soll, Netmon die Spalte 'NTLMSSP Zusammenfassung' hinzugefügt werden und Filtern `.property.NTLMSSPSummary`. Um herauszufinden, wie lange die Authentifizierung hinzugefügt wird, fügen Sie die Zeit Delta-Spalte. 

So Netmon eine Spalte hinzu: 
1. Mit der rechten Maustaste auf eine Spalte wie Beschreibung. 
2. Klicken Sie auf Spalten auswählen. 
3. Suchen Sie in der Zusammenfassung NTLMSSP und Zeitabstand, und klicken Sie auf Hinzufügen. 
4. Verschieben Sie die neuen Spalten in Place vor oder hinter der Spalte Beschreibung, damit Sie sie Side-by-Side lesen können.
5. Klicken Sie auf "OK". 

Selbst wenn Sie nicht die Spalte hinzufügen, funktioniert der Netmon-Filter. Bei der Problembehandlung ist jedoch viel einfacher, wenn Sie sehen können, welche Phase der Authentifizierung in befinden. 

Wenn gesuchte Instanzen von Proxy-Authentifizierung müssen Sie alle Frames Studie ist NTLM-Abfrage oder eine Nachricht authentifizieren vorhanden ist. Falls erforderlich, mit der rechten Maustaste die bestimmte Datenverkehr und Unterhaltungen suchen \> TCP. Beachten Sie die Zeit Delta-Werte in diese Gespräche. 

![Netmon Trace mit Proxy-Authentifizierung, gefiltert nach Unterhaltung.](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)        

Ein zweites vier Verzögerung in Proxy-Authentifizierung, wie in Wireshark dargestellt. Die Spalte **Zeit Delta aus vorherigen angezeigte Frame** wurde versucht, über das Feld mit demselben Namen in der Frame Detailbereich mit der rechten Maustaste klicken und als Spalte hinzufügen auswählen.<br/> ![In Wireshark kann die Zeitabstand aus vorherigen angezeigte Frame-Spalte erstellt werden, über das Feld mit demselben Namen in der Frame Detailbereich mit der rechten Maustaste klicken und als Spalte hinzufügen auswählen.](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)        

### <a name="dns-performance"></a>DNS-Leistung

Name Resolution funktioniert am besten am häufigsten schnell und wann sie erreicht bald der Client Land möglichst stattfindet. 

Wenn DNS-namensauflösung Übersee stattfindet, können sie Sekunden Seite Lasten hinzufügen. Idealerweise geschieht Auflösung in unter 100 ms. Wenn Sie keinen sollten weitere Untersuchung. 

> [!TIP]
> Nicht sicher, wie in Office 365-Clientkonnektivität funktioniert? Schauen Sie sich die Client-Konnektivität Referenzdokument [hier](https://technet.microsoft.com/en-us/library/dn741250.aspx).           

#### <a name="tools"></a>Tools: 

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Wonach Sie suchen:
Analysieren der DNS-Leistung ist in der Regel von einer anderen Aufgabe für ein Netzwerk-Trace. PsPing ist jedoch auch bei der Entscheidung ein- oder Auschecken möglicherweise hilfreich. 

DNS-Datenverkehr basiert auf TCP und UDP-Anforderungen, und Antworten werden mit einer ID, die mit einer bestimmte Anforderung mit seiner bestimmte Antwort übereinstimmt helfen klar gekennzeichnet. Sehen Sie die DNS-Datenverkehr Wenn beispielsweise SharePoint Online eine Netzwerknamen oder die URL auf einer Webseite verwendet. Als Daumenregel führt die meisten dieser Datenverkehr, ausgenommen bei der Übertragung von Zonen, über UDP. 

In Netmon und Wireshark, ist der einfachste Filter, mit denen Sie die DNS-Datenverkehr betrachten einfach `dns`. Achten Sie darauf, dass Kleinbuchstabe beim Angeben von des Filters verwendet werden. Denken Sie daran, um Ihre DNS-Auflösung-Cache zu leeren, bevor Sie beginnen, auf dem Clientcomputer das Problem zu reproduzieren. Beispielsweise wenn Sie eine SharePoint Online langsame Seite-Auslastung für die Homepage verfügen, sollten Sie beenden Sie alle Browser, öffnen Sie einen neuen Browser, Protokollierung starten, Ihre DNS-Auflösungscache leeren und navigieren Sie zu Ihrer SharePoint Online-Website. Nachdem die gesamte Seite aufgelöst wird, sollten Sie beenden und speichern die Ablaufverfolgung.

![Ein einfacher Filter für DNS in Netmon ist DNS.](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Suchen Sie die zum Zeitpunkt der offset Hier werden soll. Und es kann hilfreich sein, die Spalte **Zeitabstand** Netmon hinzufügen Sie, indem Sie diese Schritte ausführen: 
1. Mit der rechten Maustaste auf eine Spalte wie Beschreibung. 
2. Klicken Sie auf Spalten auswählen. 
3. Suchen Sie Zeitabstand in der Liste, und klicken Sie auf Hinzufügen. 
4. Verschieben Sie die neue Spalte in Place vor oder hinter der Spalte Beschreibung, damit Sie sie Side-by-Side lesen können.
5. Klicken Sie auf "OK". 

Wenn Sie eine Abfrage von Interesse finden, sollten Sie mit der rechten Maustaste in dieser Abfrage im Frame Detailbereich, auswählen von **Unterhaltungen suchen** zu isolieren \> **DNS**. Beachten Sie, dass die Netzwerk Unterhaltungen Systemsteuerung Recht, die bestimmte Unterhaltung in der Protokolldatei der UDP-Datenverkehr verweist. 

![Netzwerkmonitor Outlook Online Arbeitslast gefiltert, indem Sie DNS, und suchen Sie nach Unterhaltungen und dann auf DNS, um die Ergebnisse zu beschränken.](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)        

In Wireshark können Sie eine Spalte für DNS-Zeit vornehmen. Nutzen Ihre Trace (oder öffnen Sie eine Verfolgung) in Wireshark und Filter by `dns`, oder mehr Überlegung `dns.time`. Klicken Sie auf alle DNS-Abfrage, und erweitern Sie im Bereich Details anzeigen, die `Domain Name System (response)` Details. Sehen Sie ein Feld für die Uhrzeit (z. B. ` [Time: 0.001111100 seconds] `. Mit der rechten Maustaste diesmal und wählen Sie **als Spalte anwenden**. Dadurch erhalten eine Spalte **Zeit** Sie für schnellere Sortieren Ihrer Trace. Klicken Sie auf die neue Spalte zu sortieren Werte ein, um das Aufrufen von DNS finden in absteigender benötigte die längste Zeit zum Auflösen. 

[Durchsuchen von SharePoint Online in Wireshark gefiltert nach dns.time (in Kleinbuchstaben), wobei die Zeit aus den Details in eine Spalte übernommen und aufsteigend sortiert wurde.](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Wenn Sie weitere Untersuchung der DNS-Auflösungszeit tun möchten, versuchen Sie es mit einer PsPing gegen den DNS-Port von TCP verwendet (z. B. `psping <IP address of DNS server>:53`). Sehen Sie noch ein Leistungsproblem? Wenn Sie dies tun, wird das Problem eher ein großes Netzwerk Problem als ein bestimmtes Problem die DNS-Anwendung, die Sie hierzu Lösung handelt. Es ist auch erwähnt, in diesem Fall, dass ein Ping an outlook.office365.com mitteilt, wo DNS-namensauflösung für Outlook Online (beispielsweise Outlook-namnorthwest.office365.com) stattfindet.<br/> Wenn das Problem aussieht, um bestimmte DNS werden, kann es wenden Sie sich an Ihre IT-Abteilung DNS-Konfigurationen und DNS-Weiterleitung weiteren Untersuchung des Problems betrachten sein. 

### <a name="proxy-scalability"></a>Proxy-Skalierbarkeit

Dienste wie Outlook Online in Office 365 erteilen Clients mehrere langfristige Verbindungen. Daher kann jeder Benutzer weitere Verbindungen verwenden, die eine längere Lebensdauer erfordern.  

> [!TIP]
> Planen für die Verwendung der Bandbreite, da Sie gerade viel Benutzer zu Office 365 hinzufügen müssen? Versuchen Sie, [Planen der internetbandbreitennutzung für Office 365](https://technet.microsoft.com/en-us/library/hh852542.aspx). Es sind bandbreitenrechnern verfügbar.

#### <a name="tool"></a>Tool:
 
Math  

#### <a name="what-to-look-for"></a>Wonach Sie suchen: 

Es ist kein Netzwerk-Trace oder Problembehandlungstool speziell für diese. Stattdessen basiert es auf Bandbreite Berechnungen Einschränkungen und anderen Variablen zugewiesen.  

### <a name="tcp-max-segment-size"></a>Max-Segmentgröße TCP

In das SYN - SYN/Bestätigung gefunden  Führen Sie dieses Kontrollkästchen in eine beliebige Leistung Netzwerk-Trace, den Sie aufgenommen haben, um sicherzustellen, dass TCP-Pakete konfiguriert sind, um die maximale Datenmenge auszuführen. 

Ziel ist es, eine MSS 1460 Bytes für die Übertragung von Daten finden Sie unter. Wenn Sie einen Proxyserver sind oder Sie NAT verwenden, denken Sie daran, die von Client-zu-Proxy/Ausgang/NAT und von Proxy/Ausgang/NAT zu Office 365 für optimale Ergebnisse dieser Testlauf! Dies sind verschiedene TCP-Sitzungen.

#### <a name="tool"></a>Tool: 

Netmon

#### <a name="what-to-look-for"></a>Wonach Sie suchen:

TCP Max Segmentgröße (MSS) ist eine andere Parameter des 3-Wege-Handshakes in Ihrem Netzwerk-Trace, die bedeutet, dass Sie finden die benötigten Daten in das SYN - Paket SYN/Bestätigung. MSS ist tatsächlich recht einfach zu finden. 

Öffnen Sie Leistung Netzwerk Spuren haben und suchen Sie nach der Verbindung, die Sie wissen möchten, oder, die das Leistungsproblem veranschaulicht. 

> [!NOTE]
> Wenn Sie sich eine Verfolgung sehen und den Datenverkehr an der Unterhaltung relevanten suchen müssen, Filtern Sie, indem die IP-Adresse des Clients oder der IP-Adresse des Proxyservers Austritt oder beides. Wechseln direkt, müssen Sie ping die URL, die Sie für die IP-Adresse von Office 365 in das Ablaufverfolgungsprotokoll und Filtern von dieser testen. 

Betrachten der Verfolgung gebrauchte? Verwenden Sie Filter an sich selbst orientieren. Führen Sie eine Suche basierend auf der URL, z. B. in Netmon, `Containsbin(framedata, ascii, "sphybridExample")`, beachten Sie die Framenummer. 

In Wireshark verwenden, etwa `frame contains "sphybridExample"`. Wenn Sie feststellen, dass Sie Remote Winsock (RWS) Datenverkehr gefunden haben (es kann angezeigt werden als ein [PSH:, Bestätigung] in Wireshark), denken Sie daran, dass RWS verbindet kurz vor relevanten SYN - SYN/ACKs, angezeigt werden, wie weiter oben beschrieben. 

Zu diesem Zeitpunkt können Sie notieren Sie die Rahmennummer, den Filter löschen, klicken Sie auf alle Nachrichten im Fenster Unterhaltungen Netzwerk von Netmon betrachten Sie die nächste SYN 

Wichtiger ist, dass Sie nicht die IP-Adresse Informationen zum Zeitpunkt der Trace erhalten haben, suchen die URL in der Verfolgung (Teil `sphybridExample-my.sharepoint.com`, z. B.), geben Sie zum Filtern nach dem IP-Adressen. 

Ermitteln Sie die Verbindung in der Verfolgung, bei denen Sie interessiert sind. Sie können dies nachholen, indem entweder die Verfolgung von Filterung durch IP-Adressen oder durch Auswählen von bestimmten Unterhaltung-IDs, die über das Netzwerk Unterhaltungen Fenster in Netmon Überprüfung. Wenn Sie das Paket SYN gefunden haben, erweitern Sie TCP (in Netmon) oder Transmission Control Protocol (in Wireshark) im Frame Detailbereich. Erweitern Sie TCP-Optionen und MaxSegementSize. Suchen Sie die zugehörige SYN-Bestätigung Frame und erweitern Sie TCP-Optionen und MaxSegmentSize. Der kleinere der beiden Werte wird die Maximalgröße des Segments sein. In diesem Bild nutzen ich die integrierte Spalte in Netmon TCP Problembehandlung aufgerufen.  

![Netzwerk-Trace in Spalten mit der integrierten Netmon gefiltert.](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

Die integrierte Spalte ist im oberen Bereich des im **Frame** Detailbereich. (Um wieder auf Ihre normalen Ansicht wechseln möchten, klicken Sie erneut auf Spalten, und wählen Sie dann auf Zeitzone.) 

![Position der Dropdownliste mit Spalten für die TCP-Problembehandlungsoption (über der Framezusammenfassung).](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)           
Es folgt ein gefilterter Trace in Wireshark. Es ist ein Filter speziell für die MSS-Wert ( `tcp.options.mss`). Die Rahmen eines SYN, SYN/Bestätigung, Bestätigung Handshake am unteren Rand der gleichbedeutend mit Frame Detailbereich Wireshark verknüpft sind (also 47 Bestätigung, Links zu 46 SYN/Bestätigung, Links zu 43 SYN eingerahmt) zu dieser Art von Arbeit zu erleichtern. 

![Trace gefiltert in Wireshark nach tcp.options.mss für Max Segmentgröße (MSS).](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)         
Wenn Sie selektive Bestätigung überprüfen müssen (im nächsten Thema in dieser Matrix) schließen Sie nicht die Trace!

### <a name="selective-acknowledgment"></a>Selektive Bestätigung

Gefunden in das SYN - SYN/Bestätigung müssen werden gemeldet zugelassene in SYN- und SYN/Bestätigung selektive Bestätigung (SACK) ermöglicht den reibungsloseren erneute Übertragung von Daten, wenn Sie ein Paket oder Pakete verloren gehen. Geräte können dieses Feature deaktivieren, was zu Leistungsproblemen führen kann. 

Wenn Sie einen Proxyserver sind oder Sie NAT verwenden, denken Sie daran, die von Client-zu-Proxy/Ausgang/NAT und von Proxy/Ausgang/NAT zu Office 365 für optimale Ergebnisse dieser Testlauf! Dies sind verschiedene TCP-Sitzungen.

#### <a name="tool"></a>Tool: 

Netmon 

#### <a name="what-to-look-for"></a>Wonach Sie suchen:

Selektive Bestätigung (SACK) ist eine andere Parameter in den SYN-SYN/Bestätigung Handshake ab. Sie können Ihre Trace für SYN - SYN/Bestätigung unterschiedlichste Weise filtern. 

Ermitteln Sie die Verbindung in die Ablaufverfolgung, die Sie sehen, entweder durch die Ablaufverfolgung Scannen Filterung durch IP-Adressen oder interessieren indem Sie auf eine Gesprächs-ID, die über das Netzwerk Unterhaltungen Fenster in Netmon. Wenn Sie das Paket SYN gefunden haben, erweitern Sie in Netmon TCP oder Transmission Control Protocol in Wireshark im Frame Detailbereich. Erweitern Sie TCP-Optionen, und klicken Sie dann SACK. Suchen Sie verwandte SYN-Bestätigung Rahmen und erweitern Sie TCP-Optionen und seine SACK dar. Stellen Sie sicher, dass SACK in SYN- und SYN/Bestätigung zulässig ist Hier erhalten Sie SACK Werte wie in Netmon und Wireshark dargestellt.

![Selektive Bestätigung (SACK) in Netmon Vorkommen von tcp.flags.syn == 1.](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)           <br/> ![SACK gemäß Anzeige in Wireshark mit dem Filter tcp.flags.syn == 1.](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)        

### <a name="dns-geolocation"></a>DNS-Geolocation 

In denen Office 365 in der ganzen Welt versucht aufzulösen rufen Sie den DNS-Effekte Geschwindigkeit der Verbindung. 

In Outlook Online nach Abschluss der ersten DNS-Lookup wird der Speicherort der diese DNS verwendet Verbindung mit der nächsten Rechenzentrum. Sie werden an einen Outlook-Online-CAS-Server verbunden, das Backbonenetzwerk mit dem Rechenzentrum (dC) herstellen, auf dem die Daten gespeichert sind. Dies ist schneller.

Beim Zugreifen auf SharePoint Online, ein Benutzer im Ausland reisen zu ihren aktiven Rechenzentrum weitergeleitet werden sollen, die der Domänencontroller ist, deren Speicherort basiert auf ihre Mandanten SPO, des Home-Base (also einen dC in den USA Wenn den Benutzer, wenn der USA-basierte).  <br/>  Lync online hat aktive Knoten in mehr als einem Domänencontroller zu einem Zeitpunkt. Wenn Anfragen werden wird gesendet für Lync online-Instanzen, Microsoft DNS bestimmen, wo in der ganzen Welt die Anforderung stammt, und Zurückgeben von IP-Adressen aus dem nächsten regionalen dC, auf dem Lync online aktiv ist. 

> [!TIP]
> Erfahren Sie, wie Clients mit Office 365 verbinden müssen? Sehen Sie sich die [Clientkonnektivität](https://technet.microsoft.com/en-us/library/dn741250.aspx) Referenzartikel (und dessen hilfreichen Grafiken).           
#### <a name="tools"></a>Tools:

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Wonach Sie suchen:

Anforderungen für die Auflösung von Namen aus der Client-DNS-Servern an Microsoft DNS-Server sollte in den meisten Fällen Ergebnis im Microsoft-DNS die IP-Adresse eines regionalen Datencenters (dC) zurückgeben. Was bedeutet dies für Sie? Die zentrale befinden sich in Bangalore, Indien, jedoch nicht unterwegs sind in den Vereinigten Staaten, wenn Ihr Browser eine Anforderung für Outlook Online erstellt, sollte Microsoft DNS-Server Sie IP-Adressen in Rechenzentren in den USA – ein regionales Rechenzentrum übergeben. Falls e-Mail in Outlook erforderlich ist, werden diese Daten über Microsoft quick Backbonenetzwerk zwischen den Datencentern übertragen.

DNS funktioniert am schnellsten auf, wenn die Auflösung erreicht bald den Speicherort wie möglich vorgenommen wird. Wenn Sie sich in Europa befinden, möchten Sie wechseln zur Microsoft-DNS in Europa, und (idealerweise) befassen sich mit einem Rechenzentrum in Europa. Leistung von einem Client in Europa DNS- und einem Rechenzentrum in America sein und sollte wird langsamer sein.

Führen Sie das Tool Ping für outlook.office365.com, um zu bestimmen, wo in der ganzen Welt Ihrer DNS-Anforderung weitergeleitet wird. Wenn Sie in Europa sind, sollte eine Antwort von etwa Outlook-emeawest.office365.com angezeigt werden. Erwarten Sie in der amerikanischen Kontinent, etwa Outlook-namnorthwest.office365.com. 

Öffnen Sie das Eingabeaufforderungsfenster auf dem Clientcomputer (über den Start \> ausführen \> Cmd oder Windows-Taste \> Geben Sie cmd ein). Geben Sie Ping outlook.office365.com ein, und drücken Sie die EINGABETASTE. Denken Sie daran,-4 angeben, wenn Sie angeben, um mit IPv4 ping möchten. Sie wird möglicherweise eine Antwort von ICMP-Pakete erhalten möchten, aber den Namen des DNS-an den die Anforderung weitergeleitet wurde sollte angezeigt werden. Wenn Sie sehen möchten versuchen Nummern Wartezeit für diese Verbindung PsPing zur IP-Adresse des Servers, der von Ping zurückgegeben wird.  

![Ping von outlook.office365.com mit Auflösung in outlook-namnorthwest.](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)           
![PSPing zur von der Ping-Befehl mit der durchschnittliche Wartezeit für 28 Millisekunde outlook.office365.com zurückgegebene IP-Adresse.](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)           
### <a name="office-365-application-troubleshooting"></a>Problembehandlung für Office 365 Anwendung

#### <a name="tools"></a>Tools: 

- Netmon
- HTTPWatch
- F12-Konsole im browser

Anwendungsspezifische Problembehandlung in diesem Artikel Netzwerk-spezifischen verwendeten Tools behandelt nicht. Finden Sie Ressourcen, aber Sie *können* [auf dieser Seite](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848)verwenden.
   
## <a name="related-topics"></a>Verwandte Themen

[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  

