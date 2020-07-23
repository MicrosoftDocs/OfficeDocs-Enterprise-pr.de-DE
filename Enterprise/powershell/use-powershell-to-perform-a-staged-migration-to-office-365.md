---
title: Verwenden von PowerShell zum Durchführen einer mehrstufigen Migration zu Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 'Zusammenfassung: Hier erfahren Sie, wie Sie mit Windows PowerShell eine mehrstufige Migration zu Microsoft 365 durchführen.'
ms.openlocfilehash: bc21ec403b0c6daa3fe2411f8f4fea790dd5e71c
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229791"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Verwenden von PowerShell zum Durchführen einer mehrstufigen Migration zu Microsoft 365

*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*

Sie können die Inhalte von Benutzerpostfächern aus einem Quell-e-Mail-System mithilfe einer mehrstufigen Migration zu Microsoft 365 migrieren.
  
In diesem Artikel werden die Aufgaben im Zusammenhang mit einer mehrstufigen e-Mail-Migration mithilfe Exchange Online PowerShell erläutert. Das Thema, [was Sie über eine mehrstufige e-Mail-Migration wissen müssen](https://go.microsoft.com/fwlink/p/?LinkId=536487), bietet einen Überblick über den Migrationsprozess. Wenn Sie mit dem Inhalt dieses Artikels vertraut sind, verwenden Sie diese, um mit der Migration von Postfächern von einem e-Mail-System zu einem anderen zu beginnen.
  
> [!NOTE]
> Sie können auch das Exchange Admin Center verwenden, um eine mehrstufige Migration durchzuführen. Weitere Informationen finden Sie unter [Durchführen einer mehrstufigen Migration von e-Mails zu Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2-5 Minuten zum Erstellen eines Migrationsbatches. Nach dem Start des Migrationsbatches variiert die Dauer der Migration je nach der Anzahl der Postfächer im Batch, der Größe jedes Postfachs und der verfügbaren Netzwerkkapazität. Informationen zu anderen Faktoren, die sich auf die Dauer der Migration von Postfächern zu Microsoft 365 auswirken, finden Sie unter [Migrationsleistung](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Bevor Sie dieses Verfahren bzw. diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Berechtigungen, die Sie benötigen, finden Sie unter dem Eintrag "Migration" unter dem Thema [Empfängerberechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Um die Exchange Online-PowerShell-Cmdlets zu verwenden, müssen Sie angemeldet sein und die Cmdlets in Ihre lokale Windows PowerShell Sitzung importieren. Finden Sie Anweisungen unter[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShelll](https://go.microsoft.com/fwlink/p/?LinkId=534121).
  
Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Migrationsschritte

### <a name="step-1-prepare-for-a-staged-migration"></a>Schritt 1: Auf eine mehrstufige Migration vorbereiten

Bevor Sie Postfächer mithilfe einer mehrstufigen Migration zu Microsoft 365 migrieren, müssen Sie einige Änderungen an Ihrer Exchange-Umgebung vornehmen.
  
 **Konfigurieren Sie Outlook Anywhere auf Ihrem lokalen Exchange Server**. Der E-Mail-Migrationsdienst verwendet Outlook Anywhere (auch bekannt als RPC über HTTP), um eine Verbindung mit Ihrem lokalen Exchange Server herzustellen. Informationen zum Einrichten von Outlook Anywhere für Exchange Server 2007 und Exchange 2003 finden Sie im Folgenden:
  
- [Exchange 2007: Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Konfigurieren von Outlook Anywhere mit Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> Sie müssen ein Zertifikat verwenden, das von einer vertrauenswürdigen Zertifizierungsstelle (CA) mit Ihrer Outlook Anywhere-Konfiguration erstellt wurde. Outlook Anywhere kann nicht mit einem selbstsignierten Zertifikat konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren von SSL für Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
 **Optional: Stellen Sie sicher, dass Sie eine Verbindung zu Ihrer Exchange Organisation mit Outlook Anywhere** herstellen können. Versuchen Sie eine der folgenden Methoden, um die Verbindungseinstellungen zu testen.
  
- Verwenden Sie Outlook von außerhalb des Unternehmensnetzwerks zur Verbindung mit Ihrem lokalen Exchange-Postfach.
    
- Verwenden Sie die [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) , um die Verbindungseinstellungen zu testen. Verwenden Sie die Tests Outlook Anywhere (RPC über HTTP) oder Outlook-AutoErmittlung.
    
- Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Festlegen von Berechtigungen** Das lokale Benutzerkonto, das Sie zum Herstellen einer Verbindung mit Ihrer lokalen Exchange-Organisation (auch als Migrations Administrator bezeichnet) verwenden, muss über die erforderlichen Berechtigungen für den Zugriff auf die lokalen Postfächer verfügen, die Sie zu Microsoft 365 migrieren möchten. Dieses Benutzerkonto wird verwendet, wenn Sie eine Verbindung mit Ihrem e-Mail-System herstellen, indem Sie einen Migrations Endpunkt später in diesem Verfahren erstellen ([Schritt 3: Erstellen eines Migrations Endpunkts](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).
  
Um die Postfächer zu migrieren, muss der Administrator eine der folgenden Berechtigungen haben:
  
- Ein Mitglied der **Domänen-Admins** -Gruppe in Active Directory in der lokalen Organisation sein.
    
    oder
    
- **FullAccess** -Berechtigung für jedes lokale Postfach und die **WriteProperty** -Berechtigung zum Ändern der **TargetAddress** -Eigenschaft für die lokale Benutzerkonten besitzen.
    
    oder
    
- Die **ReceiveAs** -Berechtigung für die lokale Postfachdatenbank besitzen, in der die Benutzerpostfächer gespeichert sind und die **WriteProperty** -Berechtigung besitzen, um die **TargetAddress** -Eigenschaft für die lokalen Benutzerkonten ändern zu können.
    
Anweisungen zum Festlegen dieser Berechtigungen finden Sie unter Zuweisen von [Berechtigungen zum Migrieren von Postfächern zu Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).
  
 **Deaktivieren von Unified Messaging (UM)** Wenn UM für die lokalen Postfächer aktiviert ist, die Sie migrieren, deaktivieren Sie UM vor der Migration. Aktivieren Sie UM für die Postfächer nach Abschluss der Migration. Weitere Anleitungen finden Sie unter[Deaktivieren von Unified Messaging](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Verwenden Sie die Verzeichnissynchronisierung, um neue Benutzer in Microsoft 365 zu erstellen.** Sie verwenden die Verzeichnissynchronisierung, um alle lokalen Benutzer in Ihrer Microsoft 365-Organisation zu erstellen.
  
Sie müssen die Benutzer nach der Erstellung lizenzieren. Sie haben 30 Tage zum Hinzufügen von Lizenzen, nachdem die Benutzer erstellt wurden. Weitere Informationen zum Hinzufügen von Lizenzen finden Sie unter [Schritt 8: Aufgaben nach der Migration abschließen](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Sie können entweder das Synchronisierungs Tool für Microsoft Azure Active Directory (Azure AD) oder die Microsoft Azure AD Sync Services verwenden, um Ihre lokalen Benutzer in Microsoft 365 zu synchronisieren und zu erstellen. Nachdem Postfächer zu Microsoft 365 migriert wurden, verwalten Sie Benutzerkonten in Ihrer lokalen Organisation und werden mit Ihrer Microsoft 365-Organisation synchronisiert. Weitere Informationen finden Sie unter[Verzeichnis Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Schritt 2: Erstellen einer CSV-Datei für einen Batch der mehrstufigen Migration

Nachdem Sie die Benutzer identifiziert haben, deren lokale Postfächer nach Microsoft 365 migriert werden sollen, verwenden Sie eine CSV-Datei (Comma Separated Value), um einen Migrationsbatch zu erstellen. Jede Zeile in der CSV-Datei, die von Microsoft 365 zum Ausführen der Migration verwendet wird, enthält Informationen über ein lokales Postfach. 
  
> [!NOTE]
> Es gibt keinen Grenzwert für die Anzahl der Postfächer, die Sie mithilfe einer mehrstufigen Migration zu Microsoft 365 migrieren können. Die CSV-Datei für einen Migrationsbatch kann maximal 2.000 Zeilen enthalten. Um mehr als 2.000 Postfächer zu migrieren, erstellen Sie zusätzliche CSV-Dateien, und verwenden Sie jede Datei, um einen neuen Migrationsbatch zu erstellen. 
  
 **Unterstützte Attribute**
  
Die CSV-Datei für eine mehrstufige Migration unterstützt die folgenden drei Attribute. Jede Zeile der CSV-Datei entspricht einem Postfach und muss einen Wert für jedes dieser Attribute enthalten.
  
|**Attribut**|**Beschreibung**|**Erforderlich?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Gibt die primäre SMTP-E-Mail-Adresse, z. B. pilarp@contoso.com für lokale Postfächer an.  <br/> Verwenden Sie die primäre SMTP-Adresse für lokale Postfächer und keine Benutzer-IDs von Microsoft 365. Wenn die lokale Domäne beispielsweise contoso.com heißt, die Microsoft 365-e-Mail-Domäne jedoch den Namen Service.contoso.com hat, verwenden Sie den contoso.com-Domänennamen für e-Mail-Adressen in der CSV-Datei.  <br/> |Erforderlich  <br/> |
|Kennwort  <br/> |Das Kennwort, das für das neue Postfach von Microsoft 365 festgelegt werden soll. Alle Kennworteinschränkungen, die auf Ihre Microsoft 365-Organisation angewendet werden, gelten auch für die Kennwörter, die in der CSV-Datei enthalten sind.  <br/> |Optional  <br/> |
|ForceChangePassword  <br/> |Gibt an, ob ein Benutzer das Kennwort ändern muss, wenn er sich das erste Mal bei seinem neuen Microsoft 365-Postfach anmeldet. Verwenden Sie für den Wert dieses Parameters **true** oder **false** .<br/> > [!NOTE]> Wenn Sie eine Lösung für einmaliges Anmelden (SSO) durch die Bereitstellung von Active Directory-Verbunddiensten (AD FS) oder höher in Ihrer lokalen Organisation implementiert haben, verwenden Sie **False** als Wert für das Attribut **ForceChangePassword**.          |Optional  <br/> |
   
 **CSV-Dateiformat**
  
Hier ist ein Beispiel für das Format für die CSV-Datei. In diesem Beispiel werden drei lokale Postfächer zu Microsoft 365 migriert.
  
In der ersten Zeile (auch als Kopfzeile bezeichnet) der CSV-Datei sind die Namen der Attribute oder Felder aufgelistet, die in den folgenden Zeilen angegeben werden. Die einzelnen Attributnamen werden jeweils durch ein Komma getrennt.
  
```powershell
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

Um e-Mails erfolgreich zu migrieren, muss Microsoft 365 eine Verbindung herstellen und mit dem Quell-e-Mail-System kommunizieren. Zu diesem Zwecke verwendet Microsoft 365 einen Migrations Endpunkt. Zum Erstellen eines Outlook Anywhere-Migrations Endpunkts mit PowerShell für die mehrstufige Migration stellen [Sie zunächst eine Verbindung mit Exchange Online her](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Zum Erstellen eines Migrationsendpunkts von Outlook Anywhere, bezeichnet als "StagedEndpoint" in Exchange Online PowerShell, führen Sie den folgenden Befehl aus:
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Weitere Informationen zu den **New-MigrationEndpoint** -Cmdlets finden Sie unter[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).
  
> [!NOTE]
> Beim Cmdlet **New-MigrationEndpoint** können Sie mit der Option **-TargetDatabase** eine von dem Dienst zu verwendende Datenbank angeben. Andernfalls wird nach dem Zufallsprinzip eine Datenbank aus dem Active Directory-Verbunddienste (AD FS) 2.0-Standort zugewiesen, in dem sich das Verwaltungspostfach befindet.
  
#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Führen Sie den folgenden Befehl zum Anzeigen von Informationen zum Migrationsendpunkt "StagedEndpoint" in Exchange Online PowerShell aus:
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Schritt 4: Erstellen und starten eines Batches für eine mehrstufige Migration
<a name="BK_Endpoint"> </a>

Sie können das **New-MigrationBatch** -Cmdlet in Exchange Online PowerShell verwenden, um einen Migrationsbatch für eine Übernahmemigration zu erstellen. Sie können einen Migrationsbatch erstellen und diesen automatisch starten, indem Sie den Parameter _AutoStart_ verwenden. Alternativ können Sie den Migrationsbatch erstellen und später mithilfe des **Start-MigrationBatch** -Cmdlets manuell starten. In diesem Beispiel wird ein Migrationsbatch namens "StagedBatch1" erstellt und verwendet den Migrationsendpunkt, der im vorherigen Schritt erstellt wurde.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

In diesem Beispiel wird auch ein Migrationsbatch namens "StagedBatch1" erstellt und verwendet den Migrationsendpunkt, der im vorherigen Schritt erstellt wurde. Da der Parameter  _AutoStart_ nicht verwendet wird, muss der Migrationsbatch manuell im Migrationsdashboard gestartet werden oder mithilfe des **Start-MigrationBatch** -Cmdlets . Wie bereits erwähnt, kann immer nur ein Übernahmemigrationsbatch ausgeführt werden.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den "StagedBatch1" anzuzeigen:
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Sie können auch überprüfen, ob der Batch gestartet wurde, indem Sie den folgenden Befehl ausführen:
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Weitere Informationen zu den **Get-MigrationBatch** -Cmdlets finden Sie unter[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Schritt 5: Konvertieren lokaler Postfächer in E-Mail-aktivierte Benutzer
<a name="BK_Endpoint"> </a>

Nachdem Sie einen Batch von Postfächern erfolgreich migriert haben, müssen Sie eine Möglichkeit haben, Benutzern das Abrufen Ihrer e-Mails zu ermöglichen. Ein Benutzer, dessen Postfach migriert wurde, verfügt nun über ein lokales Postfach und eines in Microsoft 365. Benutzer mit einem Postfach in Microsoft 365 werden keine neuen e-Mails mehr in Ihrem lokalen Postfach empfangen. 
  
Da Sie nicht mit ihren Migrationen fertig sind, sind Sie noch nicht dazu in der Lage, alle Benutzer zu Microsoft 365 für Ihre e-Mails zu leiten. Was tun Sie also für die Menschen, die beides haben? Sie können die lokalen Postfächer ändern, die Sie bereits in e-Mail-aktivierte Benutzer migriert haben. Wenn Sie von einem Postfach zu einem e-Mail-aktivierten Benutzer wechseln, können Sie den Benutzer an Microsoft 365 für Ihre e-Mails verweisen, anstatt zu Ihrem lokalen Postfach zu gehen. 
  
Ein weiterer wichtiger Grund für das Konvertieren lokaler Postfächer in e-Mail-aktivierte Benutzer besteht darin, Proxyadressen aus den Microsoft 365-Postfächern beizubehalten, indem Proxyadressen an die e-Mail-aktivierten Benutzer kopiert werden. Auf diese Weise können Sie Cloud-basierte Benutzer aus Ihrer lokalen Organisation mithilfe von Active Directory verwalten. Wenn Sie sich entscheiden, Ihre lokale Exchange Server Organisation außer Betrieb zu nehmen, nachdem alle Postfächer zu Microsoft 365 migriert wurden, verbleiben die Proxyadressen, die Sie in die e-Mail-aktivierten Benutzer kopiert haben, in Ihrer lokalen Active Directory.
    
### <a name="step-6-delete-a-staged-migration-batch"></a>Schritt 6: Löschen eines Batches für die mehrstufige Migration
<a name="BK_Endpoint"> </a>

 Nachdem alle Postfächer in einem Migrationsbatch erfolgreich migriert wurden und Sie die lokalen Postfächer im Batch in E-Mail-aktivierte Benutzer konvertiert haben, können Sie einen Batch der mehrstufigen Migration löschen. Stellen Sie sicher, dass die e-Mails an die Microsoft 365-Postfächer im Migrationsbatch weitergeleitet werden. Wenn Sie einen Batch für die mehrstufige Migration löschen, bereinigt der Migrationsdienst alle zum Migrationsbatch gehörenden Datensätze und löscht den Migrationsbatch.
  
Führen Sie den folgenden Befehl aus, um den Migrationsbatch "StagedBatch1" in Exchange Online PowerShell zu löschen.
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Weitere Informationen zu dem **Remove-MigrationBatch** -Cmdlet finden Sie unter[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den "IMAPBatch1" anzuzeigen:
  
```powershell
Get-MigrationBatch StagedBatch1
```

Der Befehl gibt entweder den Migrationsbatch mit dem Status **Removing** zurück oder einen Fehler, der besagt, dass der Migrationsbatch nicht gefunden werden konnte, was bestätigt, dass er gelöscht wurde.
  
Weitere Informationen zu den **Get-MigrationBatch** -Cmdlets finden Sie unter[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Steps: Zuweisen von Lizenzen zu Microsoft 365-Benutzern
<a name="BK_Endpoint"> </a>

Aktivieren Sie Microsoft 365-Benutzerkonten für die migrierten Konten durch Zuweisen von Lizenzen. Wenn Sie keine Lizenz zuweisen, wird das Postfach deaktiviert, sobald die Karenzzeit (30 Tage) endet. Informationen zum Zuweisen einer Lizenz im Microsoft 365 Admin Center finden Sie unter [zuweisen oder](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)Aufheben der Zuweisung von Lizenzen.
  
### <a name="step-8-complete-post-migration-tasks"></a>Schritt 8: Aufgaben nach der Migration abschließen
<a name="BK_Postmigration"> </a>

- **Erstellen Sie einen AutoErmittlung-DNS-Eintrag, damit Benutzer problemlos auf ihre Postfächer zugreifen können.** Nachdem alle lokalen Postfächer zu Microsoft 365 migriert wurden, können Sie einen Auto Ermittlungs-DNS-Eintrag für Ihre Microsoft 365-Organisation konfigurieren, um Benutzern die einfache Verbindung mit ihren neuen Microsoft 365-Postfächern mit Outlook und mobilen Clients zu ermöglichen. In diesem neuen DNS-Eintrag für die AutoErmittlung muss derselbe Namespace verwendet werden, den Sie für Ihre Microsoft 365-Organisation verwenden. Wenn der Namespace für die Cloud-basierte Organisation beispielsweise "cloud.contoso.com" lautet, müssen Sie den DNS-Datensatz "autodiscover.cloud.contoso.com" für die AutoErmittlung erstellen.
    
    Microsoft 365 verwendet einen CNAME-Eintrag, um den AutoErmittlungsdienst für Outlook und Mobile Clients zu implementieren. Der CNAME-Eintrag für die AutoErmittlung muss folgende Informationen enthalten:
    
  - **Alias:** autodiscover
    
  - **Ziel:** autodiscover.outlook.com
    
    Weitere Informationen finden Sie unter [Hinzufügen von DNS-Einträgen zum Verbinden Ihrer Domäne](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Nehmen Sie lokale Exchange-Server außer Betrieb.** Nachdem Sie überprüft haben, dass alle e-Mails direkt an die Microsoft 365-Postfächer weitergeleitet werden und Sie Ihre lokale e-Mail-Organisation nicht mehr warten müssen oder keine SSO-Lösung implementieren möchten, können Sie Exchange von ihren Servern deinstallieren und Ihre lokale Exchange-Organisation entfernen.
    
    Weitere Informationen erhalten Sie unter den folgenden Themen:
    
  - [Ändern oder Entfernen von Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Entfernen einer Exchange 2007-Organisation](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Deinstallieren von Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

