---
title: "Verwenden von PowerShell zum Ausführen einer mehrstufigen Migration zu Office 365"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: "Zusammenfassung: Hier erfahren Sie, wie Sie Windows PowerShell verwenden, um eine mehrstufige Migration zu Office 365 auszuführen."
ms.openlocfilehash: 5143b039937389d965386de0e09f4f59db071c86
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>Verwenden von PowerShell zum Ausführen einer mehrstufigen Migration zu Office 365

 **Zusammenfassung:** Hier erfahren Sie, wie Sie Windows PowerShell verwenden, um eine mehrstufige Migration zu Office 365 auszuführen.
  
Sie können den Inhalt von Benutzerpostfächern aus einem Quell-E-Mail-System mithilfe einer mehrstufigen Migration nach und nach zu Office 365 migrieren.
  
Dieser Artikel führt Sie durch die Aufgaben im Zusammenhang mit einer mehrstufigen E-Mail-Migration mit Exchange Online PowerShell. Das Thema [Was Sie über eine mehrstufige E-Mail-Migration zu Office 365 wissen müssen](https://go.microsoft.com/fwlink/p/?LinkId=536487), gibt Ihnen eine Übersicht über den Migrationsvorgang. Wenn Sie mit dem Inhalt dieses Artikels vertraut sind, verwenden Sie ihn, um mit der Migration der Postfächer von einem E-Mail-System zu einem anderen zu beginnen.
  
> [!NOTE]
> Sie können auch mit der Exchange-Verwaltungskonsole eine mehrstufige Migration durchführen. [Ausführen einer mehrstufigen Migration von E-Mails zu Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2 bis 5 Minuten, um einen Migrationsbatch zu erstellen. Nach dem Start der Migration variiert die Dauer der Migration abhängig von der Anzahl von Postfächern in dem Batch, der Größe der einzelnen Postfächer und Ihrer verfügbaren Netzkapazität. Informationen zu weiteren Faktoren, die sich auf die Dauer der Migration von Postfächern zu Office 365, auswirken, finden Sie unter [Migrationsleistung](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Bevor Sie dieses Verfahren bzw. diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Berechtigungen, die Sie benötigen, finden Sie unter dem Eintrag "Migration" unter dem Thema [Empfängerberechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Um die Exchange Online-PowerShell-Cmdlets zu verwenden, müssen Sie angemeldet sein und die Cmdlets in Ihre lokale Windows PowerShell Sitzung importieren. Finden Sie Anweisungen unter[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShelll](https://go.microsoft.com/fwlink/p/?LinkId=534121).
  
Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Migrationsschritte

### <a name="step-1-prepare-for-a-staged-migration"></a>Schritt 1: Auf eine mehrstufige Migration vorbereiten

Vor der Migration von Postfächern zu Office 365, mithilfe einer mehrstufigen Migration, müssen Sie einige Änderungen in Ihrer Exchange Umgebung vornehmen.
  
 **Konfigurieren Sie Outlook Anywhere auf Ihrem lokalen Exchange Server**. Der E-Mail-Migrationsdienst verwendet Outlook Anywhere (auch bekannt als RPC über HTTP), um eine Verbindung mit Ihrem lokalen Exchange Server herzustellen. Informationen zum Einrichten von Outlook Anywhere für Exchange Server 2007 und Exchange 2003 finden Sie im Folgenden:
  
- [Exchange 2007: Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Konfigurieren von Outlook Anywhere mit Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> Sie müssen ein Zertifikat verwenden, das von einer vertrauenswürdigen Zertifizierungsstelle (CA) mit Ihrer Outlook Anywhere-Konfiguration erstellt wurde. Outlook Anywhere kann nicht mit einem selbstsignierten Zertifikat konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren von SSL für Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
 **Optional: Stellen Sie sicher, dass Sie eine Verbindung zu Ihrer Exchange Organisation mit Outlook Anywhere** herstellen können. Versuchen Sie eine der folgenden Methoden, um die Verbindungseinstellungen zu testen.
  
- Verwenden Sie Outlook von außerhalb des Unternehmensnetzwerks zur Verbindung mit Ihrem lokalen Exchange-Postfach.
    
- Verwenden Sie die [Microsoft Exchange-Remoteverbindungsuntersuchung]((https://www.testexchangeconnectivity.com/)) zum Testen der Verbindungseinstellungen. Verwenden Sie Outlook Anywhere (RPC über HTTP) oder Outlook AutoErmittlung-Tests.
    
- Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Festlegen von Berechtigungen** Das lokale Benutzerkonto, mit dem Sie eine Verbindung zu Ihrer lokalen Exchange Organisation (auch als Migrationsadministrator bezeichnet) herstellen möchten, muss die erforderlichen Berechtigungen besitzen, um auf die lokalen Postfächer zuzugreifen, die Sie zu Office 365 migrieren möchten. Dieses Benutzerkonto wird verwendet, wenn Sie sich mit Ihrem E-Mail-System durch das Erstellen eines Migrationsendpunkts im laufenden Prozess ([Schritt 3: Migrationsendpunkt erstellen](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ) verbinden.
  
Um die Postfächer zu migrieren, muss der Administrator eine der folgenden Berechtigungen haben:
  
- Ein Mitglied der **Domänen-Admins** -Gruppe in Active Directory in der lokalen Organisation sein.
    
    oder
    
- **FullAccess** -Berechtigung für jedes lokale Postfach und die **WriteProperty** -Berechtigung zum Ändern der **TargetAddress** -Eigenschaft für die lokale Benutzerkonten besitzen.
    
    oder
    
- Die **ReceiveAs** -Berechtigung für die lokale Postfachdatenbank besitzen, in der die Benutzerpostfächer gespeichert sind und die **WriteProperty** -Berechtigung besitzen, um die **TargetAddress** -Eigenschaft für die lokalen Benutzerkonten ändern zu können.
    
Anweisungen zum Festlegen dieser Berechtigungen finden Sie in [Zuweisen von Berechtigungen für die Migration von Postfächern zu Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).
  
 **Deaktivieren von Unified Messaging (UM)** Wenn UM für die lokalen Postfächer aktiviert ist, die Sie migrieren, deaktivieren Sie UM vor der Migration. Aktivieren Sie UM für die Postfächer nach Abschluss der Migration. Weitere Anleitungen finden Sie unter[Deaktivieren von Unified Messaging](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Verwenden Sie zum Erstellen neuer Benutzer in Office 365 Verzeichnissynchronisierung.** Verwenden Sie Verzeichnissynchronisierung, um alle lokalen Benutzer in Ihrer Office 365-Organisation zu erstellen.
  
Sie müssen die Benutzer nach der Erstellung lizenzieren. Sie haben 30 Tage zum Hinzufügen von Lizenzen, nachdem die Benutzer erstellt wurden. Weitere Informationen zum Hinzufügen von Lizenzen finden Sie unter [Schritt 8: Aufgaben nach der Migration abschließen](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Sie können entweder das Microsoft Azure Active Directory Synchronisierungs-Tool oder die Microsoft Azure Active Directory-Synchronisierungsdienste (AAD Sync) verwenden, um Ihre lokalen Benutzer in Office 365 zu synchronisieren oder zu erstellen. Nach der Migration von Postfächern zu Office 365, verwalten Sie Benutzerkonten in Ihrer lokalen Organisation und sie werden mit Ihrer Office 365 Organisation synchronisiert. Weitere Informationen finden Sie unter [Verzeichnisintegration](https://go.microsoft.com/fwlink/?LinkId=521788).
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Schritt 2: Erstellen einer CSV-Datei für einen Batch der mehrstufigen Migration

Nachdem Sie die Benutzer identifiziert haben, deren lokale Postfächer Sie zu Office 365 migrieren möchten, verwenden Sie eine durch Trennzeichen getrennte Datei (CSV), um einen Migrationsbatch zu erstellen. Jede Zeile der CSV-Datei - verwendet von Office 365 zum Ausführen der Migration - enthält Informationen über ein lokales Postfach. 
  
> [!NOTE]
> Es gibt keine Beschränkung der Anzahl von Postfächern, die Sie mit einer mehrstufigen Migration zu Office 365 migrieren können. Die CSV-Datei für einen Migrationsbatch kann maximal 2.000 Zeilen enthalten. Erstellen Sie zum Migrieren von mehr als 2.000 Postfächern zusätzliche CSV-Dateien und verwenden Sie jede Datei, um einen neuen Migrationsbatch zu erstellen. 
  
 **Unterstützte Attribute**
  
Die CSV-Datei für eine mehrstufige Migration unterstützt die folgenden drei Attribute. Jede Zeile der CSV-Datei entspricht einem Postfach und muss einen Wert für jedes dieser Attribute enthalten.
  
|**Attribut**|**Beschreibung**|**Erforderlich?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Gibt die primäre SMTP-E-Mail-Adresse, z. B. pilarp@contoso.com für lokale Postfächer an.  <br/> Verwenden Sie die primäre SMTP-Adresse für lokale Postfächer und keine Benutzer-IDs aus der Office 365. Wenn die lokale Domäne beispielsweise "contoso.com" lautet, aber die Office 365-E-Mail-Domäne "service.contoso.com" benannt wurde, verwenden Sie den Domänennamen "contoso.com" für E-Mail-Adressen in der CSV-Datei.  <br/> |Erforderlich  <br/> |
|Kennwort  <br/> |Das festzulegende Kennwort für das neue Office 365 Postfach. Alle Kennworteinschränkungen, die auf die Office 365-Organisation angewendet wurden, gelten auch für die in der CSV-Datei enthaltenen Kennwörter.  <br/> |Optional  <br/> |
|ForceChangePassword  <br/> |Gibt an, ob ein Benutzer das Kennwort ändern muss, wenn er sich das erste Mal am neuen Office 365-Postfach anmeldet. Verwenden Sie **True** oder **False** als Wert für diesen Parameter. <br/> > [!NOTE]> Wenn Sie eine Lösung für einmaliges Anmelden (SSO) durch die Bereitstellung von Active Directory-Verbunddiensten (AD FS) oder höher in Ihrer lokalen Organisation implementiert haben, verwenden Sie **False** als Wert für das Attribut **ForceChangePassword**.          |Optional  <br/> |
   
 **CSV-Dateiformat**
  
Das folgende Beispiel zeigt das Format der CSV-Datei. In diesem Beispiel werden drei lokale Postfächer zu Office 365 migriert.
  
In der ersten Zeile (auch als Kopfzeile bezeichnet) der CSV-Datei sind die Namen der Attribute oder Felder aufgelistet, die in den folgenden Zeilen angegeben werden. Die einzelnen Attributnamen werden jeweils durch ein Komma getrennt.
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Die Zeilen unter der Kopfzeile stellen einen Benutzer dar und enthalten die Informationen, die zum Migrieren des Postfachs des Benutzers verwendet werden. Die Attributwerte in jeder einzelnen Zeile müssen die gleiche Reihenfolge aufweisen wie die Attributnamen in der Kopfzeile. 
  
Sie können einen beliebigen Text-Editor oder eine Anwendung wie Excel zum Erstellen der CSV-Datei verwenden. Speichern Sie die Datei als CSV- oder TXT-Datei.
  
> [!NOTE]
> Wenn die CSV-Datei Nicht-ASCII-Zeichen oder Sonderzeichen enthält, muss sie mit UTF-8-Codierung oder einer anderen Unicode-Codierung gespeichert werden. Abhängig von der Anwendung kann es leichter sein, die CSV-Datei mit UTF-8-Codierung oder einer anderen Unicode-Codierung zu speichern, wenn das Systemgebietsschema des Computers der in der CSV-Datei verwendeten Sprache entspricht. 
  
### <a name="step-3-create-a-migration-endpoint"></a>Schritt 3: Migrationsendpunkt erstellen
<a name="BK_Endpoint"> </a>

Zum erfolgreichen Migrieren von E-Mails muss Office 365 mit dem Quell-E-Mail-System verbunden sein und kommunizieren. Zu diesem Zweck wird in Office 365 ein Migrationsendpunkt verwendet. Zum Erstellen eines Migrationsendpunkts von Outlook Anywhere durch die Verwendung von PowerShell, für eine mehrstufige Migration, stellen Sie zuerst eine [Verbindung mit Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121) her. 
  
Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Zum Erstellen eines Migrationsendpunkts von Outlook Anywhere, bezeichnet als "StagedEndpoint" in Exchange Online PowerShell, führen Sie den folgenden Befehl aus:
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Weitere Informationen zu den **New-MigrationEndpoint** -Cmdlets finden Sie unter[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).
  
> [!NOTE]
> Beim Cmdlet **New-MigrationEndpoint** können Sie mit der Option **-TargetDatabase** eine von dem Dienst zu verwendende Datenbank angeben. Andernfalls wird nach dem Zufallsprinzip eine Datenbank aus dem Active Directory-Verbunddienste (AD FS) 2.0-Standort zugewiesen, in dem sich das Verwaltungspostfach befindet.
  
#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Führen Sie den folgenden Befehl zum Anzeigen von Informationen zum Migrationsendpunkt "StagedEndpoint" in Exchange Online PowerShell aus:
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Schritt 4: Erstellen und starten eines Batches für eine mehrstufige Migration
<a name="BK_Endpoint"> </a>

Sie können das **New-MigrationBatch** -Cmdlet in Exchange Online PowerShell verwenden, um einen Migrationsbatch für eine Übernahmemigration zu erstellen. Sie können einen Migrationsbatch erstellen und diesen automatisch starten, indem Sie den Parameter _AutoStart_ verwenden. Alternativ können Sie den Migrationsbatch erstellen und später mithilfe des **Start-MigrationBatch** -Cmdlets manuell starten. In diesem Beispiel wird ein Migrationsbatch namens "StagedBatch1" erstellt und verwendet den Migrationsendpunkt, der im vorherigen Schritt erstellt wurde.
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

In diesem Beispiel wird auch ein Migrationsbatch namens "StagedBatch1" erstellt und verwendet den Migrationsendpunkt, der im vorherigen Schritt erstellt wurde. Da der Parameter  _AutoStart_ nicht verwendet wird, muss der Migrationsbatch manuell im Migrationsdashboard gestartet werden oder mithilfe des **Start-MigrationBatch** -Cmdlets . Wie bereits erwähnt, kann immer nur ein Übernahmemigrationsbatch ausgeführt werden.
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den "StagedBatch1" anzuzeigen:
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Sie können auch überprüfen, ob der Batch gestartet wurde, indem Sie den folgenden Befehl ausführen:
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Weitere Informationen zu den **Get-MigrationBatch** -Cmdlets finden Sie unter[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Schritt 5: Konvertieren lokaler Postfächer in E-Mail-aktivierte Benutzer
<a name="BK_Endpoint"> </a>

Nachdem Sie einen Batch Postfächer erfolgreich migriert haben, benötigen Sie eine Methode, damit die Benutzer auf ihre E-Mail zugreifen können. Ein Benutzer, dessen Postfach migriert wurden, hat jetzt sowohl ein lokales Postfach als auch eins in Office 365. Benutzer mit einem Postfach in Office 365, werden keine neue E-Mail-Nachrichten in ihrem lokalen Postfach empfangen. 
  
Da die Migration noch nicht abgeschlossen ist, können Sie noch nicht alle Benutzer für ihre E-Mails an Office 365 weiterleiten. Was also tun Sie für diese Personen, die beide haben? Sie können die lokalen Postfächer ändern, die Sie bereits zu E-Mail-aktivierte Benutzer migriert haben. Wenn Sie von einem Postfach zu einem E-Mail-aktivierten Benutzer wechseln, können Sie den Benutzer für seine E-Mails anstatt zu seinem lokalen Postfach an Office 365weiterleiten. 
  
Ein weiterer wichtiger Grund für die Konvertierung der lokalen Postfächer in E-Mail-aktivierte Benutzer besteht darin, dass die Proxyadressen aus den Office 365-Postfächern durch Kopieren zu den E-Mail-aktivierten Benutzern behalten werden. So können Sie Cloud-basierte Benutzer mithilfe von Active Directory von der lokalen Organisation aus verwalten. Außerdem verbleiben die zu E-Mail-aktivierten Benutzern kopierten Proxyadressen, sollten Sie entscheiden, die lokale Exchange Server-Organisation nach der Migration aller Postfächer zu Office 365 außer Betrieb zu setzen, in Ihrem lokalen Active Directory.
  
Weitere Informationen und Skripts zum Konvertieren von Postfächern in E-Mail-aktivierte Benutzer finden Sie in folgenden Themen:
  
- [Konvertieren von Exchange 2007-Postfächern in E-Mail-aktivierte Benutzer](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [Konvertieren von Exchange 2003-Postfächern in E-Mail-aktivierte Benutzer](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a>Schritt 6: Löschen eines Batches für die mehrstufige Migration
<a name="BK_Endpoint"> </a>

 Nachdem alle Postfächer in einem Migrationsbatch erfolgreich migriert wurden und Sie die lokalen Postfächer im Batch in E-Mail-aktivierte Benutzer konvertiert haben, können Sie einen Batch der mehrstufigen Migration löschen. Stellen Sie sicher, dass E-Mails an die Office 365-Postfächer im Migrationsbatch weitergeleitet werden. Wenn Sie einen Batch für die mehrstufige Migration löschen, bereinigt der Migrationsdienst alle zum Migrationsbatch gehörenden Datensätze und löscht den Migrationsbatch.
  
Führen Sie den folgenden Befehl aus, um den Migrationsbatch "StagedBatch1" in Exchange Online PowerShell zu löschen.
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

Weitere Informationen zu dem **Remove-MigrationBatch** -Cmdlet finden Sie unter[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den "IMAPBatch1" anzuzeigen:
  
```
Get-MigrationBatch StagedBatch1
```

Der Befehl gibt entweder den Migrationsbatch mit dem Status **Removing** zurück oder einen Fehler, der besagt, dass der Migrationsbatch nicht gefunden werden konnte, was bestätigt, dass er gelöscht wurde.
  
Weitere Informationen zu den **Get-MigrationBatch** -Cmdlets finden Sie unter[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step7-assign-licenses-to-office-365-users"></a>Schritt 7: Zuweisen von Lizenzen zu Office 365-Benutzern
<a name="BK_Endpoint"> </a>

Aktivieren von Office 365 Benutzerkonten für die migrierten Konten durch Zuweisen von Lizenzen. Wenn Sie keine Lizenz zuweisen, wird das Postfach nach Ablauf der Kulanzzeit (30 Tage) deaktiviert. Weitere Informationen zum Zuweisen von Lizenzen im Office 365 Admin Center finden Sie unter [Zuweisen von Lizenzen und Aufheben der Zuweisung von Lizenzen für Office 365 für Unternehmen](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Schritt 8: Aufgaben nach der Migration abschließen
<a name="BK_Postmigration"> </a>

- **Erstellen Sie einen AutoErmittlung-DNS-Eintrag, damit Benutzer problemlos auf ihre Postfächer zugreifen können.** Nachdem alle lokalen Postfächer zu Office 365 migriert wurden, können Sie einen AutoErmittlung-DNS-Eintrag für Ihre Office 365-Organisation konfigurieren, damit Benutzer mit Outlook und mobilen Clients problemlos eine Verbindung mit ihren neuen Office 365-Postfächern herstellen können. Dieser neue DNS-Datensatz für die AutoErmittlung muss denselben Namespace verwenden, den Sie für die Office 365-Organisation verwenden. Wenn der Namespace für die Cloud-basierte Organisation beispielsweise "cloud.contoso.com" lautet, müssen Sie den DNS-Datensatz "autodiscover.cloud.contoso.com" für die AutoErmittlung erstellen.
    
    Office 365 wird ein CNAME-Eintrag für die Implementierung des AutoErmittlungsdiensts für Outlook und mobile Clients verwendet. Der CNAME-Eintrag für die AutoErmittlung muss folgende Informationen enthalten:
    
  - **Alias:** autodiscover
    
  - **Ziel:** autodiscover.outlook.com
    
    Weitere Informationen finden Sie unter [Erstellen von DNS-Einträgen für Office 365, wenn Sie Ihre DNS-Einträge verwalten](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Außerbetriebsetzung der lokalen Exchange Server.** Nachdem Sie sichergestellt haben, dass alle E-Mails direkt an die Office 365-Postfächer weitergeleitet werden, und Sie nicht mehr Ihre lokale E-Mail-Organisation verwalten müssen bzw. keine Implementierung einer Lösung für einmaliges Anmelden planen, können Sie Exchange von Ihren Servern deinstallieren und Ihre lokale Exchange-Organisation entfernen.
    
    Weitere Informationen erhalten Sie unter den folgenden Themen:
    
  - [Ändern oder Entfernen von Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Entfernen einer Exchange 2007-Organisation](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Deinstallieren von Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

