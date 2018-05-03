---
title: Erkennen und Warten von Outlook-Regeln und benutzerdefinierte Formulare Injektionen-Angriffen in Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: Erfahren Sie, wie erkennen und Warten der Outlook-Regeln und benutzerdefinierte Formulare Injektionen Angriffen in Office 365
ms.openlocfilehash: d0f54a0dc47d7a3602a7b4ce57a04c83d15d9301
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks-in-office-365"></a>Erkennen und Warten von Outlook-Regeln und benutzerdefinierte Formulare Injektionen Angriffen in Office 365

**Zusammenfassung** Informationen Sie zum Erkennen und Warten der Outlook-Regeln und benutzerdefinierte Formulare Injektionen Angriffen in Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Was ist der Outlook-Regeln und benutzerdefinierte Formulare Einfügung Angriff?
Nachdem ein Angreifer verfügt über ein Konto in Ihrer Instanz generiertes und im abgerufen, werden es jetzt testen und richten Sie eine Möglichkeit in bleiben oder eine Möglichkeit, ähnliche erhalten, nachdem sie entdeckt und entfernt werden. Einrichten einer Dauerhaftigkeit wird aufgerufen. Zwei Methoden, um dies möglich sind ausnutzen Outlook-Regeln oder indem er benutzerdefinierte Formulare in Outlook einfügt. In beiden Fällen wird die Regel oder Formular synchronisiert aus der Cloud-Dienst auf dem Desktopclient so eine vollständige Formatierung und erneute Installieren der Clientsoftware nicht den Einfügung Mechanismus auszuschließen. Dies liegt daran, wenn die Outlook-Client-Software auf das Postfach in der Cloud unterbricht es die Regeln und Formulare aus der Cloud wieder heruntergeladen. Nachdem Sie die Regeln und Formulare vorhanden sind, verwendet der Angreifer diese zum Ausführen von Remote- oder benutzerdefinierten Code in der Regel um Malware auf dem lokalen Computer zu installieren. Schadsoftware, klicken Sie dann erneut entwendet Anmeldeinformationen oder anderen unerlaubten Aktivität ausführt. Hier die gute Nachricht ist, wenn Sie Ihre Clients gepatcht auf die neueste Version beibehalten, Sie keine anfällig für die Bedrohung als aktuellen Outlook-Client-Standardwerte beide Mechanismen blockieren. 

Die Angriffe führen Sie in der Regel diese Muster:

Die Regeln-Exploits
1. Der Angreifer entwendet den Benutzernamen und das Kennwort eines Ihrer Benutzer.
2. Der Angreifer anmeldet klicken Sie dann mit dem Benutzer Exchange-Postfach. Das Postfach kann entweder in Exchange sein online oder in Exchange lokalen.
3. Der Angreifer erstellt eine Weiterleitungsregel klicken Sie dann in das Postfach, das ausgelöst wird, wenn das Postfach eine e-Mail-Nachricht empfängt, die den Kriterien der Regel entspricht. Den Kriterien der Regel und den Inhalt der Trigger e-Mail sind speziell auf miteinander zugeschnitten.
4. Der Angreifer sendet die Trigger e-Mail dem Benutzer, die ihr Postfach normalerweise verwendet wird.
5. Wenn die e-Mail-Nachricht empfangen wird, wird die Regel ausgelöst. Die Aktion der Regel ist in der Regel zum Starten einer Anwendung auf einem Remoteserver (WebDAV).
6. Die Anwendung installiert normalerweise Schadsoftware, wie etwa [Powershell Empire](https://www.powershellempire.com/), lokal auf dem Computer des Benutzers.
7. Die Malware kann sich der Angreifer erneut stehlen der Benutzername und Kennwort oder andere Anmeldeinformationen vom lokalen Computer und andere böswilligen Aktivitäten ausführen.

Die Forms-Exploits
1. Der Angreifer entwendet den Benutzernamen und das Kennwort eines Ihrer Benutzer.
2. Der Angreifer dann melden Sie sich mit dem Benutzer Exchange-Postfach. Das Postfach kann entweder in Exchange sein online oder in Exchange lokalen.
3. Der Angreifer ist dann erstellt eine benutzerdefinierte e-Mail-Formularvorlage und fügt es in das Postfach des Benutzers.  Das benutzerdefinierte Formular wird ausgelöst, wenn das Postfach eine e-Mail erhält, die das Postfach das benutzerdefinierte Formular laden erforderlich sind. Das benutzerdefinierte Formular und das Format der e-Mail sind speziell auf miteinander zugeschnitten.
4. Der Angreifer sendet die Trigger e-Mail für den Benutzer, der ihr Postfach normalerweise verwendet wird.
5. Wenn die e-Mail-Nachricht empfangen wird, wird das Formular geladen. Das Formular startet eine Anwendung auf einem Remoteserver (WebDAV).
6. Die Anwendung installiert normalerweise Schadsoftware, wie etwa [Powershell Empire](https://www.powershellempire.com/), lokal auf dem Computer des Benutzers.
7. Die Malware kann sich der Angreifer erneut stehlen der Benutzername und Kennwort oder andere Anmeldeinformationen vom lokalen Computer und andere böswilligen Aktivitäten ausführen.


## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Welche eine Regeln und benutzerdefinierte Formulare Einfügung Angriff mit Office 365 aussehen könnte?

Persistenz Mechanismen sind wahrscheinlich nicht von den Benutzern bemerkt wird und in einigen Fällen möglicherweise für sie nicht sichtbar.  In diesem Artikel erfahren Sie, wie eine die sieben Anzeichen (Indikatoren Kompromiss) unten aufgeführten gesucht. Wenn Sie diese gefunden haben, müssen Sie Wiederherstellungsschritte berücksichtigen.

- Indikatoren für die Gefährdung der Regeln
    - Regelaktion ist das Starten einer Anwendung.
    - Regel verweist auf eine EXE-Datei, ZIP oder URL.
    - Suchen Sie auf dem lokalen Computer nach neuen gestartet, die aus der Outlook-PID stammen.
- Manipulieren von Indikatoren für die benutzerdefinierte Formulare 
    - Benutzerdefiniertes Formular vorhanden als eigene Nachrichtenklasse gespeichert.
    - Nachrichtenklasse enthält ausführbaren Code.
    - In der Regel im Ordner Posteingang oder Bibliothek für persönliche Formulare gespeichert.
    - Formular heißt IPM. Beachten Sie. [benutzerdefinierter Name].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Schritte zum Suchen nach diesem Angriff auf Anzeichen und zu bestätigen
Eine der folgenden beiden Methoden können Sie um den Angriff zu bestätigen.
- Untersuchen Sie manuell die Regeln und Formularen für jedes Postfach mithilfe des Outlook-Clients.  Diese Methode ist gründliche, aber Sie können nur Postfachbenutzer zu einem Zeitpunkt, sehr zeitaufwendig sein kann, überprüfen, wenn viele Benutzer zu überprüfen.  Sie können auch eine Verletzung des Computers führen, die Sie das Kontrollkästchen ausgeführt werden.
- Verwenden Sie das [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell-Skript, um automatisch alle die e-Mail-Weiterleitung von Regeln und benutzerdefinierte Formulare für alle Benutzer in Ihrer Instanz zu speichern. Dies ist die schnellste und sicherste Methode mit den geringsten Aufwand.


### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Bestätigen Sie die Regeln Angriff mithilfe des Outlook-Clients
1. Öffnen Sie den Benutzer Outlook-Client als der Benutzer.  Der Benutzer kann Ihre Hilfe untersuchen die Regeln für ihre Postfächer benötigen.
2. Finden Sie Artikel für die Verfahren zum Öffnen der Regeln-Schnittstelle in den 2007, 2010 oder 2013-Versionen von Outlook [e-Mail-Nachrichten mithilfe von Regeln verwalten](https://support.office.com/en-us/article/manage-email-messages-by-using-rules-c24f5dea-9465-4df4-ad17-a50704d66c59#ID0EAABAAA=2010) .
3. Suchen Sie nach Regeln, die der Benutzer nicht selbst erstellt haben, oder unerwarteten Regeln oder Regeln mit verdächtigen Namen.
4. Suchen Sie in der Beschreibung der Regel für Regelaktionen, Start- und die Anwendung oder verweisen auf ein. EXE. ZIP-Datei oder eine URL starten.
5. Suchen Sie nach allen neuen Prozessen, die beginnen mit der Outlook-Prozess-ID.  [Hier finden Sie die Prozess-ID](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/finding-the-process-id)finden Sie unter.

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Schritte zum Bestätigen des Forms-Angriffs mithilfe des Outlook-Clients
1. Öffnen Sie den Outlook-Client des Benutzers als der Benutzer.
2. Führen Sie die Schritte im [Anzeigen der Registerkarte Entwicklertools](https://support.office.com/en-us/article/show-the-developer-tab-e1192344-5e56-4d45-931b-e5fd9bea2d45) für die Benutzer-Version von Outlook aus.
3. Öffnen Sie die Entwicklerregisterkarte jetzt sichtbar für in Outlook, und klicken Sie auf **ein Formular entwerfen**.
4. Wählen Sie aus der Liste **Suchen In** den **Posteingang** aus. Suchen Sie nach benutzerdefinierten Formularen.  Benutzerdefinierte Formulare sind selten genug, dass wenn Sie benutzerdefinierte Formulare in allen verfügen, wichtig, einen genaueren ist.
5. Untersuchen Sie alle benutzerdefinierten Formulare, insbesondere solche, die als ausgeblendet gekennzeichnet.
6. Öffnen Sie benutzerdefinierte Formulare, und klicken Sie in der Gruppe **Formular** auf **Code anzeigen** , um herauszufinden, was beim Laden des Formulars ausgeführt wird.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Schritte zum Bestätigen des Regeln und Formulare Angriffs von PowerShell
Die einfachste Möglichkeit zum Überprüfen einer Regeln oder benutzerdefinierte Formulare Angriff das [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell-Skript ausgeführt wird.  Dieses Skript stellt eine Verbindung mit jedem Postfach in Ihrem Mandanten und speichert alle Regeln und Formularen in zwei CSV-Dateien.

#### <a name="pre-requisites"></a>Voraussetzungen
Sie müssen über die ein globaler Administratorrechte zum Ausführen des Skripts, da das Skript auf jedes Postfach des Mandanten, lesen die Regeln und Formulare stellt eine Verbindung her.

1. Melden Sie sich bei dem Computer, auf dem Sie das Skript aus mit lokalen Administratorrechten ausgeführt werden.
2. Laden Sie oder kopieren Sie das Get-AllTenantRulesAndForms.ps1-Skript aus GitHub in einen Ordner auf dem Sie es ausgeführt werden.  Das Skript werden zwei Datumsstempel Dateien in diesem Ordner, MailboxFormsExport-jjjj-mm-dd.csv und MailboxRulesExport-jjjj-mm-dd.csv erstellen.
3. Öffnen Sie eine Instanz der PowerShell als Administrator, und öffnen Sie den Ordner, den, dem Sie das Skript gespeichert haben.
4. Führen folgende PowerShell-Befehlszeile wie folgt aus `.\Get-AllTenantRulesAndForms.ps1`.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Interpretieren der Ausgabe

MailboxRulesExport -*jjjj-mm-tt*CSV – untersuchen Sie die Regeln (eine pro Zeile) für die Aktion Bedingungen, die Anwendungen oder ausführbare Dateien enthalten.
- ActionType (Spalte A) – Wenn Sie den Wert "ID_ACTION_CUSTOM", finden Sie in die Regel ist wahrscheinlich böswilligen Absichten.
- IsPotentiallyMalicious (Spalte D) – Wenn dieser Wert "true" festgelegt ist, ist die Regel wahrscheinlich böswilligen Absichten.
- ActionCommand (Spalte G) – Hier werden eine Anwendung oder eine Datei mit einer .exe, Erweiterung ".zip" oder einen Eintrag, der auf eine URL, das nicht vorhanden sein verweist, die Regel wahrscheinlich ist böswilligen Absichten.

MailboxFormsExport -*jjjj-mm-tt*CSV – ist die Verwendung von benutzerdefinierten Formularen im Allgemeinen selten.  Wenn Sie einer in dieser Arbeitsmappe enthalten ist, öffnen Sie das Postfach des Benutzers und überprüfen Sie das Formular selbst.  Falls Ihre Organisation nicht es absichtlich erstellt haben, ist es wahrscheinlich böswilligen Absichten.



## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Zum Beenden und Warten von Outlook-Regeln und Formulare-Angriff
Wenn Sie auf Anzeichen für einen der folgenden Angriffe finden, Remediation einfache, einfach die Regel oder das Formular aus dem Postfach löschen. Sie führen Sie mit dem Outlook-Client oder mithilfe von remote-PowerShell, um Regeln zu entfernen.

### <a name="using-outlook"></a>Verwenden von Outlook
1. Identifizieren Sie die Geräte, die der Benutzer mit Outlook verwendet hat.  Sie müssen alle potenzielle Malware bereinigt werden.  Lassen Sie den Benutzer anmelden und e-Mail verwenden, bis alle Geräte bereinigt werden nicht zu.
2. Führen Sie die Schritte in [Löschen Sie eine Regel](https://support.office.com/en-us/article/Delete-a-rule-2F0E7139-F696-4422-8498-44846DB9067F) für jedes Gerät aus.
3. Wenn Sie über das Vorhandensein von anderen Malware nicht sicher sind, können Sie formatieren und alle Software auf dem Gerät erneut installieren.  Für mobile Geräte können Sie den Hersteller, um das Zurücksetzen des Geräts auf das Bild Factory Schritte.
4. Installieren Sie die aktuellsten Versionen von Outlook.  Denken Sie daran, dass die aktuelle Version von Outlook standardmäßig beide Arten von diesem Angriff blockiert.
5. Nachdem alle offline Kopien des Postfachs entfernt wurden, Zurücksetzen Sie des Kennworts für den Benutzer (verwenden Sie eine hohe Qualität), und führen Sie die Schritte im [Setup mehrstufige Authentifizierung für Office 365-Benutzer](https://support.office.com/en-us/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6) , wenn mehrstufiger Authentifizierung das noch nicht aktiviert wurde. Dadurch wird sichergestellt, dass die Anmeldeinformationen des Benutzers nicht mit anderen Mitteln (beispielsweise Phishing oder das Kennwort erneut verwenden) verfügbar gemacht werden.

### <a name="using-powershell"></a>Verwenden von PowerShell
Es gibt zwei remote PowerShell-Cmdlets, entfernen oder Deaktivieren von gefährlicher Regeln verwendet werden können. Befolgen Sie die Schritte aus.
 
Schritte für Postfächer, die auf einem Exchange-Server sind

1. Verbinden Sie mit dem Exchange-Server mithilfe von remote PowerShell. Führen Sie die Schritte in [Verbindung mit Exchange-Servern mithilfe von remote-PowerShell herstellen](https://docs.microsoft.com/en-us/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell?view=exchange-ps).
2. Wenn Sie eine einzelne Regel, die mehrere Regeln oder alle Regeln aus einem Postfach verwenden Sie das [Cmdlet Remove-Posteingangsregel ](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)- vollständig entfernen möchten verwenden Sie diese Option, um vollständig entfernen eine, mehrere oder alle Regeln aus dem Postfach.
3. Wenn Sie die Regel beibehalten möchten, und dessen Inhalt zur weiteren Untersuchung verwenden Sie das [Cmdlet Disable-InboxRule](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx). 

Schritte für Postfächer in Exchange Online
1. Führen Sie die Schritte in [Verbindung mit Exchange Online mithilfe von PowerShell herstellen](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).
2.  Wenn Sie eine einzelne Regel vollständig entfernen möchten, verwenden Sie mehrere Regeln oder alle Regeln aus einem Postfach mit dem [Cmdlet "Remove-Posteingangsregel"](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps).
3.  Wenn Sie die Regel beibehalten möchten, und dessen Inhalt zur weiteren Untersuchung verwenden Sie das [Cmdlet Disable-InboxRule](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx). 

## <a name="how-to-minimize-future-attacks"></a>Gewusst wie: zukünftige Angriffe zu minimieren.

### <a name="first-protect-your-accounts"></a>Erste: Schützen von Konten

Die Regeln und Formulare-Exploits werden nur von einem Angreifer verwendet, nachdem sie Diebstahl oder generiertes eines des Benutzers Konten haben. Daher ist der erste Schritt zu verhindern, dass diese Exploits gegen Ihre Organisation Ihre Benutzerkonten aggressiv schützen.  Einige der am häufigsten verwendeten Methoden, dass Konten verletzt werden sind über Phishing oder [Kennwort sind](http://www.dabcc.com/microsoft-defending-against-password-spray-attacks/) -Angriffe.



Die beste Möglichkeit so schützen Sie Ihre Benutzerkonten und insbesondere Ihre Administratorkonten wird [mehrstufige Authentifizierung für Office 365-Benutzer eingerichtet](https://support.office.com/en-us/article/set-up-multi-factor-authentication-for-office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).  Sie sollten auch Schritte ausführen:
<ol>
    <li>Überwachen Sie, wie Ihre Benutzerkonten <a href="https://docs.microsoft.com/en-us/azure/active-directory/active-directory-view-access-usage-reports">aufgerufen und verwendet</a>werden. Sie möglicherweise nicht die anfängliche Verletzung verhindern, aber Sie werden die Dauer und die Auswirkungen der Verletzung verkürzen, indem sie früher erkennen. Sie können diese verwenden: <a href="https://support.office.com/en-us/article/overview-of-office-365-cloud-app-security-81f0ee9a-9645-45ab-ba56-de9cbccab475">Office 365 Cloud App-Sicherheitsrichtlinien</a> für Konten und Warnung ungewöhnliche Aktivitäten zu überwachen.<ol type="a">
            <li><b>Mehrere fehlgeschlagene Anmeldeversuche</b> Diese Richtlinie profiles der Umgebung und Trigger Benachrichtigungen, wenn Benutzer mehrere Anmeldung Aktivitäten in einer einzigen Sitzung in Bezug auf die Gelernte Baseline ausführen, die ein versuchte Verletzung angeben kann.</li>
            <li><b>Kann nicht Reisen</b> - Diese Richtlinie profiles Ihrer Umgebung und Warnungen ausgelöst wird, wenn Aktivitäten aus der gleichen Benutzer an unterschiedlichen Standorten innerhalb eines Zeitraums erkannt werden, die kürzer als die erwartete Zeit zwischen den beiden Standorten ist. Dies kann bedeuten, dass ein anderer Benutzer die gleichen Anmeldeinformationen verwendet wird. Erkennen von diesem abweichendem Verhalten erfordert einen Zeitraum anfänglichen Learning sieben Tage in denen sie einen neuen Benutzer Aktivität Muster lernen.</li>
            <li><b>Ungewöhnlicher imitiert Aktivität (pro Benutzer)</b> - Diese Richtlinie profiles Ihrer Umgebung und Warnungen ausgelöst wird, wenn Benutzer mehrere angenommener Aktivitäten in einer einzigen Sitzung in Bezug auf die geplante gelernt haben, ausführen, die ein versuchte Verletzung angeben kann.</li>
        </ol>
    </li>
    <li>Nutzen Sie ein Tool wie der <a href="https://securescore.office.com/">Office 365 Secure Score</a> Konto Sicherheitskonfigurationen und Verhaltensweisen verwalten. 
    </li>
</ol> 

### <a name="second-keep-your-outlook-clients-current"></a>Zweite: Stand Ihrer Outlook-clients
Vollständig aktualisiert und Patches Versionen von Outlook 2013 und 2016 deaktivieren die Aktion "Anwendung starten" Rule-Formular standardmäßig.  Dadurch wird sichergestellt, dass auch wenn ein Angreifer das Konto Recyclings, die Regel und Formular Aktionen blockiert werden.  Sie können die neuesten Updates und Sicherheitspatches mithilfe der Schritte in der [Installation von Office-Updates](https://support.office.com/en-us/article/Install-Office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5)installieren.

Hier sind die Patch-Versionen für Ihr Outlook 2013 und 2016 Clients:
- Outlook 2013: 15.0.4937.1000 oder höher
- Outlook-2016: 16.0.4534.1001 oder höher

Weitere Informationen zu den einzelnen Sicherheitspatches finden Sie unter:

- [Sicherheitspatch für Outlook 2013](https://support.microsoft.com/en-us/help/3191938) 
- [Outlook 2016 Sicherheitspatch](https://support.microsoft.com/en-us/help/3191883)

### <a name="third-monitor-your-outlook-clients"></a>Dritte: Überwachen von Outlook-clients
Beachten Sie, dass selbst bei der neuesten Patches und Updates installiert sind, es ist möglich, dass ein Angreifer zum Ändern der Konfiguration lokalen Computer, um das Verhalten der "Anwendung starten" wieder zu aktivieren. Sie können [Erweiterte Gruppenrichtlinienverwaltung](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/agpm/) zum Überwachen und Erzwingen von lokalen Richtlinien auf den Clients verwenden.  
Sie können, um festzustellen, ob "Anwendung starten" durch eine Überschreibung in der Registrierung erneut aktiviert wurde mit den Informationen in [der Registrierung des Systems mit 64-Bit-Versionen von Windows anzeigen](https://support.microsoft.com/en-us/help/305097/how-to-view-the-system-registry-by-using-64-bit-versions-of-windows).  Überprüfen Sie die folgenden Unterschlüssel: 

- Outlook 2016: HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\
- Outlook 2013: HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\

Suchen Sie nach dem Schlüssel EnableUnsafeClientMailRules. Wenn es vorhanden ist und auf 1 festgelegt ist, der Outlook-Sicherheitspatch überschrieben wurde, und der Computer ist anfällig für Formular-Regeln Angriffe. Wenn der Wert 0 ist, wird die Aktion "Anwendung starten" deaktiviert.  Wenn die neuesten Patches und aktualisierte Version von Outlook installiert ist, und dieser Registrierungsschlüssel nicht vorhanden ist, ist ein System nicht anfällig für diese Angriffe.

Benutzer mit lokalen Exchange-Installationen sollten blockieren ältere Versionen von Outlook die keine Patches verfügbar sind. Details zu diesem Vorgang finden Sie im Artikel [Konfigurieren von Outlook-Client blockieren](https://technet.microsoft.com/en-us/library/dd335207(v=exchg.150).aspx).

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Sichern von Office 365 wie eine pro Sicherheit im Internet
Ihr Office 365-Abonnement verfügt über eine leistungsstarke Reihe von Sicherheitsfunktionen, die Sie verwenden können, um Ihre Daten und Ihre Benutzer zu schützen.  Verwendung der [Wegweiser für Office 365-Sicherheit: Top-Prioritäten für den ersten 30 Tagen 90 Tage und darüber hinaus](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) zur Implementierung von Microsoft empfohlene bewährte Methoden zum Sichern Ihrer Office 365-Mandanten.
- Aufgaben in den ersten 30 Tagen ausgeführt.  Diesen sofort einen Einfluss darauf haben und klein sind für die Benutzer.
- Aufgaben in 90 Tage ausgeführt. Diese erfordern etwas mehr Zeit zum Planen und implementieren, aber Ihre Sicherheitsstatus erheblich verbessert.
- Mehr als 90 Tage. Erstellen Sie diese Verbesserungen in Ihrer ersten 90 Tage Arbeit.

## <a name="see-also"></a>Siehe auch:
- [Bösartige Outlook-Regeln](https://silentbreaksecurity.com/malicious-outlook-rules/) nach SilentBreak Sicherheit Post zu Regeln Vektor bietet eine detaillierte Prüfung dafür, wie Sie die Outlook-Regeln. 
- [MAPI über HTTP und Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) im Sensepost Blog zur Mailrule Pwnage erläutert das Hilfsprogramm Lineal, mit denen Sie Postfächer über Outlook-Regeln nutzen kann.
- [Outlook-Formulare und nutzt](https://sensepost.com/blog/2017/outlook-forms-and-shells/) im Blog Sensepost zu Formularen Bedrohung Vektor. 
- [Ruler-Codebasis](https://github.com/sensepost/ruler)
- [Indikatoren für Kompromiss Lineal](https://github.com/sensepost/notruler/blob/master/iocs.md)