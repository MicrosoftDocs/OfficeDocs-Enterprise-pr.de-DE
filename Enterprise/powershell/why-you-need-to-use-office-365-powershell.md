---
title: Warum Sie Office 365 PowerShell verwenden müssen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
ms.audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Zusammenfassung: Verstehen Sie, warum Sie aus Effizienzgründen oder aus Notwendigkeit Office 365 PowerShell zum Verwalten von Office 365 verwenden müssen.'
ms.openlocfilehash: f63f1a2361b225eed5d771b06b07f00bba26c392
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574099"
---
# <a name="why-you-need-to-use-office-365-powershell"></a>Warum Sie Office 365 PowerShell verwenden müssen

 **Zusammenfassung:** Verstehen Sie, warum Sie aus Effizienzgründen oder aus Notwendigkeit Office 365 PowerShell zum Verwalten von Office 365 verwenden müssen.
  
Mit dem Microsoft 365 Admin Center können Sie nicht nur Ihre Office 365-Benutzerkonten und-Lizenzen verwalten, sondern auch Ihre Office 365-Serverprodukte verwalten: Exchange, Skype for Business Online und SharePoint Online. Sie können diese Elemente jedoch auch mit Office 365 PowerShell-Befehlen verwalten, die eine Befehlszeilen- und Skriptsprachenumgebung für Geschwindigkeit, Automatisierung und zusätzliche Funktionen nutzen.
  
In diesem Artikel werden die Möglichkeiten erläutert, die Sie bei der Verwendung von Office 365 PowerShell zum Verwalten von Office 365 haben.
  
- Office 365 PowerShell kann zusätzliche Informationen aufdecken, die Sie mit dem Microsoft 365 Admin Center nicht sehen können.
    
- Office 365 weist Features auf, die Sie nur mithilfe von Office 365 PowerShell konfigurieren können
    
- Office 365 PowerShell eignet sich hervorragend zum Ausführen von Massenvorgängen.
    
- Office 365 PowerShell eignet sich hervorragend zum Filtern von Daten
    
- Office 365 PowerShell erleichtert das Drucken oder Speichern von Daten.
    
- Office 365 PowerShell ermöglicht eine Verwaltung über Serverprodukte hinweg
    
Bevor Sie beginnen, müssen Sie verstehen, dass es sich bei Office 365 PowerShell um einen Satz von Modulen für Windows PowerShell, eine Befehlszeilenumgebung für Windows-basierte Dienste und -Plattformen handelt. Diese Umgebung erstellt eine Befehlszeilensprache, die mit zusätzlichen Modulen erweitert werden kann und eine Möglichkeit zum Ausführen einfacher oder komplexer Befehle oder Skripts bietet. Nachdem Sie beispielsweise die Office 365 PowerShell-Module installiert und mit Ihrem Office 365-Abonnement verbunden haben, können Sie diesen Befehl ausführen, um alle Benutzerpostfächer für Microsoft Exchange Online aufzulisten:
  
```
Get-Mailbox
```

Das erhalten der Liste der Postfächer kann auch problemlos mit dem Microsoft 365 Admin Center erfolgen, aber die Anzahl der Elemente in allen Listen für alle Websites für alle Ihre Web-Apps kann nicht einfach erledigt werden.
  
Beachten Sie, dass Office 365 PowerShell so konzipiert wurde, dass Sie Ihre Möglichkeiten zur Verwaltung von Office 365 erweitern und verbessern und nicht das Microsoft 365 Admin Center ersetzen kann. Als Office 365-Administrator müssen Sie sich zumindest komfortabel mit der Verwendung von Office 365 PowerShell befassen, da es einige Konfigurationsverfahren gibt, die nur mit Office 365 PowerShell-Befehlen ausgeführt werden können. In diesen Fällen müssen Sie Folgendes verstehen:
  
- Installation der Office 365 PowerShell-Module (nur einmal pro Administratorcomputer).
    
- Verbinden mit Ihrem Office 365-Abonnement (einmal pro PowerShell-Sitzung).
    
- Zusammentragen der erforderlichen Informationen zum Ausführen der erforderlichen Office 365 PowerShell-Befehle.
    
- Erfolgreiches Ausführen der Office 365 PowerShell-Befehle.
    
Nachdem Sie diese grundlegenden Fähigkeiten erlernt haben, müssen Sie Ihre Postfachbenutzer nicht mit dem Befehl **Get-Mailbox** auflisten, und Sie müssen nicht verstehen, wie ein neuer Befehl wie der vorherige erstellt wird, um alle Elemente in allen Listen für alle Standorte für alle Web-Apps zu zählen. Microsoft und die Community von Office 365-Administratoren können Ihnen bei Bedarf dabei behilflich sein.
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>Office 365 PowerShell kann zusätzliche Informationen aufdecken, die Sie mit dem Microsoft 365 Admin Center nicht sehen können.

Das Microsoft 365 Admin Center zeigt viele nützliche Informationen an, aber das bedeutet nicht, dass alle möglichen Informationen angezeigt werden, die Office 365 auf Benutzern, Lizenzen, Postfächern und Websites speichert. Im folgenden finden Sie ein Beispiel für **Benutzer und Gruppen** im Microsoft 365 Admin Center:
  
![Beispiel für die Anzeige von Benutzern und Gruppen im Microsoft 365 Admin Center.](media/o365-powershell-users-and-groups.png)
  
Hier werden für zahlreiche Zwecke die benötigten Informationen angezeigt. Es kann jedoch vorkommen, dass Sie mehr benötigen. Beispielsweise hängen die Office 365-Lizenzierung (und die für einen Benutzer verfügbaren Office 365-Features) teilweise vom geografischen Standort dieses Benutzers ab. Die Richtlinien und Features, die Sie auf einen Benutzer erweitern können, der in den USA lebt, sind möglicherweise nicht die gleichen Richtlinien und Features, die Sie auf einen Benutzer erweitern können der in Indien oder in Belgien lebt. Mit den folgenden Schritten können Sie das Microsoft 365 Admin Center verwenden, um den geografischen Standort eines Benutzers zu ermitteln:
  
1. Doppelklicken Sie auf den **Anzeigenamen** des Benutzers.
    
2. Klicken Sie im Bereich "Benutzereigenschaften" auf **Details**.
    
3. Klicken Sie unter "Details" auf **Zusätzliche Details**.
    
4. Führen Sie einen Bildlauf nach unten bis zu **Land oder Region** aus.
    
     ![Beispiel für die Regionsinformationen für einen Benutzer im Microsoft 365 Admin Center.](media/o365-powershell-usage-location.png)
  
5. Notieren Sie den Anzeigenamen des Benutzers auf einem Blatt Papier, oder kopieren ihn in Editor. 
    
Sie müssen diese Vorgehensweise für jeden Benutzer wiederholen. Bei zahlreichen Benutzern kann dies eine mühsame Aufgabe sein. Mit Office 365 PowerShell können Sie diese Informationen für alle Benutzer mit dem folgenden Befehl anzeigen:
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> Für diesen Befehl müssen Sie das [Windows Azure Active Directory-Modul](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0) installieren. 
  
Nachfolgend sehen Sie ein Beispiel der Anzeige:
  
```
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Benutzer im aktuellen Office 365-Abonnement abrufen (**Get-MsolUser**), dabei jedoch für jeden Benutzer jeweils nur Namen und Standort anzeigen (**Select DisplayName, UsageLocation**)
  
Da Office 365 PowerShell eine Befehlszeilensprache unterstützt, können Sie die vom Befehl **Get-MSolUser** abgerufenen Informationen weiter bearbeiten. Sie möchten vielleicht die Benutzer anhand ihres Standorts sortieren, alle brasilianischen oder alle amerikanischen Benutzer zusammen gruppieren usw. Hier ist der Befehl:
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Nachfolgend sehen Sie ein Beispiel der Anzeige:
  
```
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Benutzer im aktuellen Office 365-Abonnement abrufen, dabei jedoch für jeden Benutzer jeweils nur Namen und Standort anzeigen und die Benutzerliste vorrangig nach Standort und dann erst nach Namen sortieren (**Sort UsageLocation, DisplayName**)
  
Sie können auch eine zusätzliche Filterung verwenden. Wenn Sie beispielsweise nur Informationen zu Benutzern in Brasilien anzeigen möchten, verwenden Sie den folgenden Befehl:
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

Nachfolgend sehen Sie ein Beispiel der Anzeige:
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Benutzer im aktuellen Office 365-Abonnement abrufen, deren Standort Brasilien ist (**Where {$\_.UsageLocation -eq "BR"}**), und für jeden Benutzer Namen und Standort anzeigen
  
 **Ein kurzer Hinweis zu größeren Domänen**
  
Wenn Sie eine sehr große Domäne mit Zehntausenden von Benutzers haben, könnte dies bei einigen Beispielen in diesem Artikel zu "Einschränkungen" kommen. Je nach Computerleistung und verfügbarer Bandbreite möchten Sie zu viel auf einmal. Für große Organisationen bietet es sich daher an, einige dieser Office 365 PowerShell-Befehle auf zwei Befehle aufzuteilen. Dieser einer Befehle gibt beispielsweise alle Benutzerkonten zurück und zeigt den Namen und Standort für jedes Konto an:
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

Das funktioniert auch gut bei kleineren Domänen. In großen Organisationen müssen Sie den Befehl möglicherweise in zwei Befehle aufteilen: Ein Befehl zum Speichern der Benutzerkontoinformationen in einer Variablen und ein anderer Befehl zum Anzeigen der erforderlichen Informationen. Es folgt ein Beispiel:
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


Die Interpretation dieses Satzes von Office 365 PowerShell-Befehlen ist:
- Alle Benutzer im aktuellen Office 365-Abonnement abrufen und die Informationen in einer Variablen mit dem Namen "$x" speichern (**$x = Get-MsolUser**).
- Den Inhalt der Variablen „$x“ anzeigen, dabei aber für jeden Benutzer nur Namen und Standort einschließen (**$x | Select DisplayName, UsageLocation**)
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a>Office 365 weist Features auf, die Sie nur mithilfe von Office 365 PowerShell konfigurieren können

Das Microsoft 365 Admin Center bietet Zugriff auf die gängigsten oder bedeutungsvollsten administrativen Aufgaben, die für die meisten Benutzer gelten. Mit anderen Worten: das Microsoft 365 Admin Center wurde so konzipiert, dass der typische Administrator das Tool verwenden kann, um die gängigsten Verwaltungsaufgaben auszuführen. Mit dieser Definition ist dies der Fall, dass es einige Aufgaben gibt, die nicht mit dem Microsoft 365 Admin Center abgeschlossen werden können.
  
Das Skype for Business Online Admin Center bietet beispielsweise ein paar Optionen zum Erstellen benutzerdefinierter Besprechungseinladungen:
  
![Beispiel für die Anzeige von benutzerdefinierten Besprechungseinladungen im Skype for Business Online Admin Center](media/o365-powershell-meeting-invitation.png)
  
Mit diesen Einstellungen können Sie Besprechungseinladungen eine gewisse persönliche Note und Professionalität verleihen. Besprechungskonfigurationseinstellungen erlauben Ihnen jedoch mehr, als einfach benutzerdefinierte Besprechungseinladungen zu erstellen. Besprechungen ermöglichen standardmäßig beispielsweise Folgendes:
  
- anonymen Benutzern, automatischen Zugang zu jeder Besprechung zu erhalten
    
- Teilnehmern, die Besprechung aufzuzeichnen.
    
- das Festlegen aller Benutzer in Ihrer Organisation als Referenten, wenn sie an der Besprechung teilnehmen.
    
Diese Einstellungen sind im Skype for Business Online Admin Center nicht verfügbar. Sie können sie jedoch über Office 365 PowerShell steuern. Nachfolgend sehen Sie einen Befehl, der diese drei Einstellungen deaktiviert:
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Für diesen Befehl müssen Sie das [Skype for Business Online PowerShell-Modul](https://www.microsoft.com/download/details.aspx?id=39366) installieren. 
  
> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Deaktivieren Sie für die Einstellungen für neue Skype for Business Online-Besprechungen (**Set-CsMeetingConfiguration**), die Möglichkeit, dass anonyme Benutzer automatischen Zugang zu Besprechungen erhalten (**-AdmitAnonymousUsersByDefault $False**), deaktivieren Sie die Möglichkeit, dass Teilnehmer Besprechungen aufzeichnen (**-AllowConferenceRecording $False**), und legen Sie nicht alle Benutzer aus Ihrer Organisation als Referenten fest ( **-DesignateAsPresenter "None"**).
  
Wenn Sie Ihre Meinung ändern und diese Standardeinstellungen wiederherstellen möchten (alle aktiviert), führen Sie den folgenden Befehl aus:
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Dies ist nur ein Beispiel. Es gibt weitere Beispiele, deshalb müssen Sie, als Office 365-Administrator, mit dem Ausführen von Office 365 PowerShell-Befehlen vertraut sein.
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a>Office 365 PowerShell überzeugt beim Ausführen von Massenoperationen

Historisch gesehen sind visuelle Schnittstellen wie das Microsoft 365 Admin Center besonders wertvoll, wenn Sie einen einzelnen Vorgang ausführen müssen. Wenn Sie beispielsweise ein Benutzerkonto deaktivieren müssen, können Sie das Microsoft 365 Admin Center verwenden, um ein Kontrollkästchen schnell zu suchen und zu deaktivieren. Dies kann einfacher sein als einen ähnlichen Vorgang in Office 365 PowerShell durchzuführen.
  
Wenn Sie jedoch viele Dinge oder einige ausgewählte Elemente in einer großen Reihe anderer Dinge ändern müssen, ist das Microsoft 365 Admin Center möglicherweise nicht die beste Zeit. Wenn Sie beispielsweise das Präfix für Tausende von Telefonnummern ändern oder einen bestimmten Benutzer, Ken Myers, von allen SharePoint Online-Websites entfernen müssen, wie würden Sie das im Microsoft 365 Admin Center tun?
  
Beim zweiten Beispiel haben Sie mehrere Hundert SharePoint Online-Standorte und wissen nicht einmal, bei welchen Ken Meyer ein Mitglied ist. Das führt dazu, dass Sie im Microsoft 365 Admin Center starten müssen und dann dieses Verfahren für jede Website ausführen:
  
1. Klicken Sie auf die **URL** des Standorts.
    
2. Klicken Sie im Feld **Websitesammlungs-Eigenschaften** auf den Link **Websiteadresse**, um die Website zu öffnen.
    
3. Klicken Sie auf der Website auf **Freigabe**.
    
4. Klicken Sie im Dialogfeld **Freigabe** auf den Link, der Ihnen alle Benutzer mit Berechtigungen für die Website zeigt:
    
     ![Beispiel der Anzeige der Mitglieder einer SharePoint Online-Website im SharePoint Online Admin Center.](media/o365-powershell-view-permissions.png)
  
5. Klicken Sie im Dialogfeld **Freigegeben für** auf **Erweitert**.
    
6. Führen Sie in der Liste der Benutzer einen Bildlauf nach unten zu Ken Myer durch, wählen Sie ihn aus (angenommen, dass er Berechtigungen für diese Website besitzt), und klicken Sie dann auf **Benutzerberechtigungen entfernen**.
    
Dies kann bei mehreren Hundert Seiten lange dauern.
  
Die Alternative besteht darin, Office 365 PowerShell und den folgenden Befehl zum Entfernen von Ken Myer von allen Standorten zu verwenden:
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Für diesen Befehl müssen Sie [eine Verbindung mit SharePoint Online PowerShell herstellen](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps). 
  
> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle SharePoint-Websites im aktuellen Office 365-Abonnement abrufen (**Get-SPOSite**) und Ken Meyer für jede Website aus der Liste der Benutzer mit Zugriffsberechtigung entfernen (**ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}**)
  
Da Office 365 angewiesen wird, Ken Meyer von jedem Standort, einschließlich derer, in denen er keinen Zugriff hat, zu entfernen, werden für die Standorte, an denen er derzeit nicht über Zugriff verfügt, Fehlermeldungen angezeigt. Wir können eine zusätzliche Bedingung für diesen Befehl verwenden, um Ken Meyer nur von den Standorten zu entfernen, an denen er in der Anmeldeliste vorhanden ist, die aufgeführten Fehler richten jedoch an den Standorten selbst keinen Schaden an. Dieser Befehl kann einige Minuten dauern, bis Hunderte von Websites ausgeführt werden, statt die Arbeitszeiten im Microsoft 365 Admin Center zu überschreiten.
  
Nachfolgend finden Sie ein weiteres Beispiel für eine Massenoperation. Verwenden Sie diesen Befehl, um Bonnie Kearney, einen neuen SharePoint-Administrator, zu allen Standorten in der Organisation hinzuzufügen:
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle SharePoint-Websites im aktuellen Office 365-Abonnement abrufen und den Anmeldenamen von Bonnie Kearney für jede Website zur Gruppe „Mitglieder" hinzufügen, um ihr Zugriff zu gewähren (**Each {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}**)
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a>Office 365 PowerShell eignet sich bestens zum Filtern von Daten

Das Microsoft 365 Admin Center bietet verschiedene Möglichkeiten zum Filtern Ihrer Daten, um eine gezielte Teilmenge von Informationen schnell und einfach zu finden. Mit Exchange können Sie beispielsweise leicht nach praktisch jeder Eigenschaft eines Benutzerpostfachs filtern. Nachfolgend sehen Sie beispielsweise die Liste der Postfächer aller Benutzer, die in Bloomington wohnen:
  
![Beispiel für eine erweiterte Suche im Microsoft 365 Admin Center für die Liste der Postfächer für alle Benutzer, die in der Stadt Bloomington Leben.](media/o365-powershell-advanced-search.png)
  
Im Exchange Admin Center können Sie auch Filterkriterien kombinieren. Sie können beispielsweise nach den Postfächern aller in Bloomington lebenden Personen suchen, die zudem in der Finanzabteilung arbeiten. 
  
Es gibt jedoch Einschränkungen dafür, was mit dem Exchange Admin Center alles möglich ist. Vielleicht möchten Sie beispielsweise die Postfächer aller in Bloomington oder San Diego lebenden Personen suchen oder die Postfächer aller Personen, die nicht in Bloomington leben. 
  
Mit Office 365 PowerShell können Sie mit dem folgenen Befehl eine Liste der Postfächer aller in Bloomington oder San Diego lebenden Personen abrufen:
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

Nachfolgend sehen Sie ein Beispiel der Anzeige:
  
```
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle Benutzer im aktuellen Office 365-Abonnement abrufen, die ein Postfach in San Diego oder ein Postfach in Bloomington haben (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}**), und für jeden dieser Benutzer jeweils Namen und Stadt anzeigen (**Select DisplayName, City**)
  
Verwenden Sie den folgenden Befehl, um alle Postfächer von Benutzern aufzuführen, die überall leben, nur nicht in Bloomington:
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Nachfolgend sehen Sie ein Beispiel der Anzeige:
  
```
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle Benutzer im aktuellen Office 365-Abonnement abrufen, deren Postfach sich nicht in Bloomington befindet (**Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}**), und für jeden dieser Benutzer jeweils Namen und Stadt anzeigen
  
Sie können auch Platzhalterzeichen in Ihren Office 365 PowerShell-Filtern verwenden, um eine Übereinstimmung mit einem Teil eines Namens zu suchen. Angenommen, Sie suchen nach einem Benutzerkonto, und Sie können sich nur daran erinnern, dass der Nachname Anderson oder vielleicht Henderson oder vielleicht aber auch Jorgenson war.
  
Sie können diesen Benutzer im Microsoft 365 Admin Center nachverfolgen, indem Sie das Such Tool verwenden und drei verschiedene Suchvorgänge durchführen:
  
- Eine für  *Anderson* 
    
- Eine für  *Henderson* 
    
- Und eine für  *Jorgenson* 
    
Da alle drei Namen auf "son" enden, können Sie Office 365 PowerShell anweisen, alle Benutzer anzuzeigen, deren Name auf "son" endet. Hier ist der Befehl:
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist: Alle Benutzer im aktuellen Office 365-Abonnement abrufen, aber einen Filter verwenden, damit nur die Benutzer aufgeführt werden, deren Nachname auf "son" endet (**-Filter '{LastName -like "\*son"}'**). Das \* steht für einen beliebigen Satz von Zeichen, im Falle des Nachnamens der Benutzer um Buchstaben.
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a>Office 365 PowerShell erleichtert das Drucken oder Speichern von Daten

Mit dem Microsoft 365 Admin Center können Sie Datenlisten anzeigen. Nachfolgend sehen Sie ein Beispiel im Skype for Business Online Admin Center, bei dem eine Liste von Benutzern angezeigt wird, die für Skype for Business Online aktiviert wurden.
  
![Beispiel für das Skype for Business Online Admin Center, in dem eine Liste von Benutzern angezeigt wird, die für Skype for Business Online aktiviert wurden.](media/o365-powershell-lync-users.png)
  
Um diese Informationen in einer Datei zu speichern, müssen Sie sie kopieren und in ein Dokument oder in Excel einfügen. Für das Kopieren ist auf jeden Fall eine zusätzliche Formatierung erforderlich. Darüber hinaus bietet das Microsoft 365 Admin Center keine Möglichkeit, die angezeigte Liste direkt zu drucken.
  
Glücklicherweise können Sie Office 365 PowerShell verwenden, um die Liste nicht nur anzuzeigen, sondern sie auch in einer Datei zu speichern, damit sie problemlos in Excel importiert werden kann. Nachfolgend sehen Sie einen Beispielbefehl, um Skype for Business Online-Benutzerdaten in einer CSV-Datei (durch Trennzeichen getrennte Datei) zu speichern, die einfach als Tabelle in ein Excel-Arbeitsblatt importiert werden kann.
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Nachfolgend sehen Sie ein Beispiel der Anzeige:
  
![Beispiel für eine Tabelle, die in ein Excel-Arbeitsblatt importiert wurde, mit Skype for Business Online-Benutzerdaten, die als CSV-Datei gespeichert wurden.](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Skype for Business Online-Benutzer im aktuellen Office 365-Abonnement abrufen (**Get-CsOnlineUser**), dabei nur den Benutzernamen, den UPN und den Standort abrufen (**Select DisplayName, UserPrincipalName, UsageLocation**) und anschließend diese Informationen in einer CSV-Datei unter „C:\\Logs\\SfBUsers.csv" speichern (**Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation**)
  
Sie können auch Optionen verwenden, um diese Liste als XML-Datei oder als HTML-Seite zu speichern. Mit zusätzlichen PowerShell-Befehlen könnten Sie die Datei direkt als Excel-Datei mit beliebigen benutzerdefinierten Formatierungen speichern. 
  
Sie können die Ausgabe eines Office 365 PowerShell-Befehls, der eine Liste anzeigt, auch direkt an den Standarddrucker in Windows senden. Nachfolgend sehen Sie einen Beispielbefehl:
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Das gedruckte Dokument sieht wie folgt aus:
  
![Beispiel eines gedruckten Dokuments, das die Ausgabe eines Office 365 PowerShell-Befehls war, der direkt an den Standarddrucker in Windows ausgegeben wurde.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  Die Interpretation dieses Office 365 PowerShell-Befehls ist:  Alle Skype for Business Online-Benutzer im aktuellen Office 365-Abonnement abrufen, nur den Benutzernamen, den Benutzer und den Ort abrufen und diese Informationen dann an den Standard-Windows-Drucker senden ( **Out-Printer** ).
  
Das gedruckte Dokument weist dieselbe einfache Formatierung wie die Anzeige innerhalb des Office 365 PowerShell-Befehlsfensters auf, nachdem Sie jedoch einen Office 365 PowerShell-Befehl erstellt haben, um die gewünschten Informationen aufzulisten, fügen Sie nur **| Out-Printer** am Ende des Befehls hinzu, um eine Hardcopy zu erhalten.
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a>Office 365 PowerShell ermöglicht eine Verwaltung über Serverprodukte hinweg

Die unterschiedlichen Komponenten, aus denen Office 365 besteht, sind so konzipiert, dass sie zusammenarbeiten. Angenommen, Sie fügen einen neuen Benutzer zu Office 365 hinzu und geben dabei Informationen wie die Abteilung und Telefonnummer des Benutzers an. Diese Informationen stehen Ihnen anschließend zur Verfügung, wenn Sie mithilfe eines der Office 365-Serverprodukte auf die Benutzerinformationen zugreifen: Skype for Business Online, Exchange oder SharePoint Online.
  
Hierbei handelt es sich um allgemeine Informationen, die für die ganze Produktsuite gleich sind. Produktspezifische Informationen, wie die zu einem Exchange-Benutzerpostfach, sind in der Regel nicht in der gesamten Suite verfügbar. Wenn Sie beispielsweise wissen möchten, ob das Postfach eines Benutzers aktiviert ist oder nicht, sind diese Informationen nur im Exchange Admin Center verfügbar. 
  
Angenommen, Sie möchten einen Bericht erstellen, in dem die folgenden Informationen für alle Benutzer enthalten sind:
  
- Den Anzeigenamen des Benutzers
    
- Ob der Benutzer für Office 365 lizenziert ist
    
- Ob das Exchange-Postfach des Benutzers aktiviert wurde
    
- Ob der Benutzer für Skype for Business Online aktiviert ist
    
Sie können derzeit nicht das Microsoft 365 Admin Center verwenden, um einen solchen Bericht problemlos zu erstellen. Stattdessen müssen Sie ein separates Dokument erstellen, um die Informationen wie ein Excel-Arbeitsblatt zu speichern und alle Benutzernamen und Lizenzierungsinformationen aus dem Microsoft 365 Admin Center abzurufen, Postfachinformationen aus der Exchange-Verwaltungskonsole abzurufen, Skype for Business Online-Informationen aus dem Skype for Business Online Admin Center, und Sortieren und kombinieren Sie diese Informationen.
  
Die Alternative besteht darin, ein Office 365 PowerShell-Skript zu verwenden, das diesen Bericht für Sie kompiliert.
  
Das folgende Beispielskript ist komplizierter als die bisher in diesem Artikel gezeigten Befehle. Es zeigt jedoch das Potenzial der Verwendung von Office 365 PowerShell zum Erstellen von Ansichten von Informationen, die andernfalls nur sehr schwer zu erstellen sind. Nachfolgend sehen Sie das Skript, das die erforderliche Liste kompilieren und anzeigen kann:
  
```
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

Nachfolgend sehen Sie ein Beispiel der Anzeige:
  
```
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

Die Interpretation dieses Office 365 PowerShell-Skripts ist:  
- Alle Benutzer im aktuellen Office 365-Abonnement abrufen und die Informationen in einer Variablen mit dem Namen "$x" speichern (**$x = Get-MsolUser**).
- Eine Schleife starten, die über alle Benutzer in der Variablen mit dem Namen $x ausgeführt wird (**foreach ($i in $x)**).  
- Eine Variable mit dem Namen $y definieren und die Postfachinformationen des Benutzers darin speichern (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
- Eine neue Eigenschaft zu den Benutzerinformationen mit dem Namen IsMailBoxEnabled hinzufügen und diese als Wert der IsMailBoxEnabled-Eigenschaft des Benutzerpostfachs hinzufügen (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
- Eine Variable mit dem Namen $y definieren und die Skype for Business Online-Informationen des Benutzers darin speichern (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
- Eine neue Eigenschaft mit dem Namen EnabledForSfB zu den Benutzerinformationen hinzufügen und diese auf den Wert der Enabled-Eigenschaft der Skype_for_Business_Online-Informationen des Benutzers festlegen (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
- Die Benutzerliste anzeigen, dabei aber jeweils nur den Namen, den Lizenzstatus und die beiden neuen Eigenschaften einschließen, die angeben, ob das Postfach aktiviert ist und ob der jeweilige Benutzer für Skype for Business Online aktiviert ist (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**)
  
## <a name="see-also"></a>Siehe auch

[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

