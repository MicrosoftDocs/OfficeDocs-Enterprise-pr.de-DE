---
title: "Verwenden von PowerShell zum Ausführen einer Übernahmemigration zu Office 365"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: "Zusammenfassung: Verwenden Sie Windows PowerShell zum Ausführen einer Übernahmemigration zu Office 365."
ms.openlocfilehash: be5a3587538c32589c20fe6d27d69a84e0b8e7db
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>Verwenden von PowerShell zum Ausführen einer Übernahmemigration zu Office 365

 **Zusammenfassung:** Verwenden Sie Windows PowerShell zum Ausführen einer Übernahmemigration zu Office 365.
  
Sie können den Inhalt von Benutzerpostfächern aus einem Quell-E-Mail-System mithilfe einer gleichzeitigen Übernahmemigration zu Office 365 migrieren. Dieser Artikel führt Sie durch die Aufgaben für eine E-Mail-Übernahmemigration mithilfe von Exchange Online PowerShell. 
  
Im Thema [Wichtige Informationen zur E-Mail-Übernahmemigration zu Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688) erhalten Sie eine Übersicht über den Migrationsvorgang. Wenn Sie mit dem Inhalt dieses Artikels vertraut sind, verwenden Sie die Informationen, um Postfächer von einem E-Mail-System zu einem anderen zu migrieren.
  
> [!NOTE]
> Sie können auch die Exchange-Verwaltungskonsole zum Durchführen einer Übernahmemigration verwenden. Siehe [Durchführen einer Übernahmemigration von E-Mails zu Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2 bis 5 Minuten, um einen Migrationsbatch zu erstellen. Nach dem Start der Migration variiert die Dauer der Migration abhängig von der Anzahl von Postfächern in dem Batch, der Größe der einzelnen Postfächer und Ihrer verfügbaren Netzkapazität. Informationen zu weiteren Faktoren, die sich auf die Dauer der Migration von Postfächern zu Office 365, auswirken, finden Sie unter [Migrationsleistung](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Bevor Sie dieses Verfahren bzw. diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Berechtigungen, die Sie benötigen, finden Sie unter dem Eintrag „Migration" in einer Tabelle im Thema [Empfängerberechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Um die Exchange Online-PowerShell-Cmdlets zu verwenden, müssen Sie angemeldet sein und die Cmdlets in Ihre lokale Windows PowerShell Sitzung importieren. Finden Sie Anweisungen unter[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShelll](https://go.microsoft.com/fwlink/p/?LinkId=534121).
  
Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Migrationsschritte

### <a name="step-1-prepare-for-a-cutover-migration"></a>Schritt 1: Übernahmemigration vorbereiten
<a name="BK_Step1"> </a>

- **Hinzufügen der lokalen Exchange-Organisation als akzeptierte Domäne Ihrer Office 365-Organisation** Der Migrationsdienst verwendet die SMTP-Adresse Ihrer lokalen Postfächer, um die Microsoft Online Services-Benutzer-ID und -E-Mail-Adresse für die neuen Office 365-Postfächer zu erstellen. Die Migration scheitert, wenn es sich bei der Exchange-Domäne nicht um eine akzeptierte Domäne oder die primäre Domäne der Office 365-Organisation handelt. Weitere Informationen finden Sie unter[Überprüfen Ihrer Domäne in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Konfigurieren von Outlook Anywhere auf dem lokalen Exchange-Server** Der E-Mail-Migrationsdienst verwendet RPC über HTTP oder Outlook Anywhere, um eine Verbindung mit dem lokalen Exchange-Server herzustellen. Informationen zum Einrichten von Outlook Anywhere für Exchange 2010, Exchange 2007 und Exchange 2003 finden Sie unter den folgenden Themen:
    
  - [Exchange 2010: Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007: Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003: Bereitstellungsszenarien für RPC über HTTP](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Konfigurieren von Outlook Anywhere mit Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > Die Outlook Anywhere-Konfiguration muss mit einem Zertifikat einer vertrauenswürdigen Zertifizierungsstelle konfiguriert werden. Outlook Anywhere kann nicht mit einem selbstsignierten Zertifikat konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren von SSL für Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
- **Sicherstellen, dass mit Outlook Anywhere eine Verbindung mit der Exchange-Organisation hergestellt werden kann** Sie können eine der folgenden Methoden verwenden, um die Verbindungseinstellungen zu testen:
    
  - Verwenden Sie Microsoft Outlook von außerhalb Ihre Firmennetzwerks, um eine Verbindung mit Ihrem lokalen Exchange-Postfach herzustellen.
    
  - Verwenden Sie die Microsoft [Exchange-Remoteverbindungsuntersuchung]((https://www.testexchangeconnectivity.com/)) zum Testen der Verbindungseinstellungen. Verwenden Sie die Outlook Anywhere- (RPC über HTTP)- oder Outlook-AutoErmittlungs-Tests.
    
  - Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Zuweisen der erforderlichen Berechtigungen für das lokale Benutzerkonto für den Zugriff auf Postfächer in der Exchange-Organisation** Das lokale Benutzerkonto, das Sie für die Verbindung Ihrer lokalen Exchange-Organisation verwenden (auchMigrationsadministrator genannt) muss über die erforderlichen Berechtigungen für den Zugriff auf die lokalen Postfächer verfügen, die Sie zu Office 365 migrieren möchten. Dieses Benutzerkonto wird zur Erstellung eines Migrationsendpunkts zu Ihrer lokalen Organisation verwendet.
    
    Die folgende Liste zeigt die Administratorrechte an, die erforderlich sind, um Postfächer mithilfe einer Übernahmemigration zu migrieren. Es gibt drei mögliche Optionen.
    
  - Der Migrationsadministrator muss Mitglied der Gruppe **Domänen-Admins** in Active Directory in der lokalen Organisation sein.
    
    – oder –
    
  - Dem Migrationsadministrator muss die Berechtigung **FullAccess** für jedes lokale Postfach zugewiesen werden.
    
    – oder –
    
  - Dem Migrationsadministrator muss die Berechtigung **Receive As** für die lokale Postfachdatenbank zugewiesen werden, in der die Benutzerpostfächer gespeichert sind.
    
- **Deaktivieren von Unified Messaging** Wenn die zu migrierenden lokalen Postfächer für Unified Messaging (UM) aktiviert sind, müssen Sie vor der Migration UM in den Postfächern deaktivieren. Nach Abschluss der Migration können Sie UM dann für die Postfächer wieder aktivieren.
    
- **Sicherheitsgruppen und Stellvertretungen** Da der E-Mail-Migrationsdienst nicht erkennen kann, ob lokale Active Directory-Gruppen Sicherheitsgruppen sind, kann er keine migrierten Gruppen als Sicherheitsgruppen in Office 365 bereitstellen. Wenn Sie im Office 365-Mandanten Sicherheitsgruppen verwenden möchten, müssen Sie zunächst eine leere E-Mail-aktivierte Sicherheitsgruppe im Office 365-Mandanten bereitstellen, bevor Sie die Übernahmemigration beginnen. Zudem werden bei dieser Migrationsmethode nur Postfächer, E-Mail-Benutzer, E-Mail-Kontakte und E-Mail-aktivierte Gruppen verschoben. Wenn irgendein anderes Active Directory-Objekt, z. B. ein nicht zu Office 365 migrierter Benutzer, als Manager oder Stellverteter einem zu migrierenden Objekt zugewiesen ist, muss es vor der Migration aus diesem Objekt entfernt werden.
    
### <a name="step-2-create-a-migration-endpoint"></a>Schritt 2: Migrationsendpunkt erstellen
<a name="BK_Step2"> </a>

Um E-Mails erfolgreich zu migrieren, muss Office 365 eine Verbindung zum Quell-E-Mail-System herstellen und mit ihm kommunizieren. Zu diesem Zweck verwendet Office 365 einen Migrationsendpunkt. Um einen Outlook Anywhere-Migrationsendpunkt für die Übernahmemigration zu erstellen, [stellen Sie zunächst eine Verbindung mit Exchange Online her](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:
  
```
$Credentials = Get-Credential
```

Dabei wird das Cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) verwendet, um die Einstellungen für die Verbindung mit dem lokalen Exchange-Server abzurufen und zu testen. Anschließend werden diese Verbindungseinstellungen zum Erstellen des Migrationsendpunkts verwendet.
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> Beim Cmdlet **New-MigrationEndpoint** können Sie mit der Option **-TargetDatabase** eine von dem Dienst zu verwendende Datenbank angeben. Andernfalls wird nach dem Zufallsprinzip eine Datenbank aus dem Active Directory-Verbunddienste (AD FS) 2.0-Standort zugewiesen, in dem sich das Verwaltungspostfach befindet.
  
#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Führen Sie den folgenden Befehl zum Anzeigen von Informationen zum Migrationsendpunkt „CutoverEndpoint“ in Exchange Online PowerShell aus:
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Schritt 3: Übernahmemigrationsbatch erstellen
<a name="BK_Step3"> </a>

Sie können das **New-MigrationBatch** -Cmdlet in Exchange Online PowerShell verwenden, um einen Migrationsbatch für eine Übernahmemigration zu erstellen. Sie können einen Migrationsbatch erstellen und diesen automatisch starten, indem Sie den _AutoStart_-Parameter verwenden. Alternativ können Sie den Migrationsbatch erstellen und später mithilfe des **Start-MigrationBatch** -Cmdlets manuell starten. In diesem Beispiel wird ein Migrationsbatch namens „CutoverBatch" erstellt und der im vorherigen Schritt erstellte Migrationsendpunkt verwendet.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

In diesem Beispiel wird auch ein Migrationsbatch namens „CutoverBatch" erstellt und verwendet den Migrationsendpunkt, der im vorherigen Schritt erstellt wurde. Da der Parameter  _AutoStart_ nicht verwendet wird, muss der Migrationsbatch manuell im Migrationsdashboard gestartet werden oder mithilfe des **Start-MigrationBatch** -Cmdlets . Wie bereits erwähnt, kann immer nur ein Übernahmemigrationsbatch ausgeführt werden.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Um zu überprüfen, ob Sie erfolgreich einen Migrationsbatch für eine Übernahmemigration erstellt haben, führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen zum neuen Migrationsbatch anzuzeigen:
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Schritt 4: Übernahmemigrationsbatch starten
<a name="BK_Step4"> </a>

Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um den Migrationsbatch zu starten. Dadurch wird ein Migrationsbatch namens „CutoverBatch“ erstellt.
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Wenn ein Migrationsbatch erfolgreich gestartet wurde, lautet sein Status im Migrationsdashboard Synchronisierung. Führen Sie den folgenden Befehl aus, um zu überprüfen, ob ein Migrationsbatch erfolgreich mithilfe von Exchange Online PowerShell gestartet wurde:
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>Schritt 5: Weiterleiten Ihrer E-Mails zu Office 365
<a name="BK_Step5"> </a>

E-Mail-Systeme verwenden einen DNS-Eintrag namens MX-Eintrag, um zu bestimmen, wohin E-Mail-Nachrichten übermittelt werden sollen. Während der Migration von E-Mails hat der MX-Eintrag auf Ihr E-Mail-Quellsystem verwiesen. Da die E-Mail-Migration zu Office 365 jetzt abgeschlossen ist, sollte der MX-Eintrag nun auf Office 365 verweisen. Dadurch wird sichergestellt, dass E-Mails an Ihre Office 365-Postfächer übermittelt werden. Durch Verschieben des MX-Eintrags können Sie Ihr altes E-Mail-System ggf. auch deaktivieren. 
  
Für viele DNS-Anbieter gibt es bestimmte Anweisungen zum [Ändern des MX-Eintrags](https://go.microsoft.com/fwlink/p/?LinkId=279163). Wenn Ihr DNS-Anbieter nicht enthalten ist oder wenn Sie allgemeine Anweisungen erhalten möchten, finden Sie entsprechende Informationen unter [Erstellen und Konfigurieren eines DNS-Eintrags für Office 365](https://go.microsoft.com/fwlink/?LinkId=397449).
  
Es kann bis zu 72 Stunden dauern, bis die E-Mail-Systeme der Kunden und Partnern den geänderten MX-Eintrag erkennen. Warten Sie mindestens 72 Stunden, bevor Sie mit dem nächsten Schritt fortfahren: [Schritt 6: Übernahmemigrationsbatch löschen](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>Schritt 6: Übernahmemigrationsbatch löschen
<a name="Bk_step6"> </a>

Nachdem Sie den MX-Eintrag geändert und sichergestellt haben, dass alle E-Mails an die Office 365-Postfächer weitergeleitet werden, benachrichtigen Sie die Benutzer, dass ihre E-Mails zu Office 365 geleitet werden. Danach können Sie den Übernahmemigrationsbatch löschen. Überprüfen Sie Folgendes, bevor Sie den Migrationsbatch löschen.
  
- Alle Benutzer verwenden Office 365-Postfächer. Nachdem der Batch gelöscht wurde, werden E-Mails, die an Postfächer auf dem lokalen Exchange-Server gesendet werden, nicht mehr in die entsprechenden Office 365-Postfächer kopiert.
    
- Office 365-Postfächer wurden mindestens einmal nach dem Start des direkten E-Mail-Versands synchronisiert. Stellen Sie hierzu sicher, dass der Wert im Feld „Zeit der letzten Synchronisierung" für den Migrationsbatch jünger als das Datum und die Uhrzeit ist, zu denen das direkte Weiterleiten von E-Mails an Office 365-Postfächer begonnen hat.
    
Führen Sie den folgenden Befehl aus, um den Migrationsbatch „CutoverBatch“ in Exchange Online PowerShell zu löschen:
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Abschnitt 7: Zuweisen von Benutzerlizenzen
<a name="BK_Step7"> </a>

 **Aktivieren Sie Office 365-Benutzerkonten für die migrierten Konten durch Zuweisen von Lizenzen.** Wenn Sie keine Lizenz zuweisen, wird das Postfach nach Ablauf der Kulanzzeit (30 Tage) deaktiviert. Weitere Informationen zum Zuweisen von Lizenzen im Office 365 Admin Center finden Sie unter[Zuweisen von Lizenzen und Aufheben der Zuweisung von Lizenzen für Office 365 Business](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Schritt 8: Aufgaben nach der Migration abschließen
<a name="BK_Step8"> </a>

- **Erstellen Sie einen AutoErmittlung-DNS-Eintrag, damit Benutzer problemlos auf ihre Postfächer zugreifen können.** Nachdem alle lokalen Postfächer zu Office 365 migriert wurden, können Sie einen AutoErmittlung-DNS-Eintrag für Ihre Office 365-Organisation konfigurieren, damit Benutzer mit Outlook und mobilen Clients problemlos eine Verbindung mit ihren neuen Office 365-Postfächern herstellen können. Dieser neue DNS-Datensatz für die AutoErmittlung muss denselben Namespace verwenden, den Sie für die Office 365-Organisation verwenden. Wenn der Namespace für die Cloud-basierte Organisation beispielsweise "cloud.contoso.com" lautet, müssen Sie den DNS-Datensatz "autodiscover.cloud.contoso.com" für die AutoErmittlung erstellen.
    
    Wenn Sie Exchange Server weiterhin verwenden, müssen Sie sicherstellen, dass der DNS CNAME-Eintrag für die AutoErmittlung im internen und externen DNS nach der Migration auf Office 365 verweist, damit der Outlook-Client eine Verbindung mit dem richtigen Postfach herstellen kann.
    
    > [!NOTE]
    >  In Exchange 2007, Exchange 2010 und Exchange 2013 sollten Sie auch  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` auf `Null` festlegen. 
  
    Office 365 wird ein CNAME-Eintrag für die Implementierung des AutoErmittlungsdiensts für Outlook und mobile Clients verwendet. Der CNAME-Eintrag für die AutoErmittlung muss folgende Informationen enthalten:
    
  - **Alias:** autodiscover
    
  - **Ziel:** autodiscover.outlook.com
    
    Weitere Informationen finden Sie unter [Erstellen von DNS-Einträgen für Office 365, wenn Sie Ihre DNS-Einträge verwalten](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Außerbetriebsetzung der lokalen Exchange Server.** Nachdem Sie sichergestellt haben, dass alle E-Mails direkt an die Office 365-Postfächer weitergeleitet werden, und Sie nicht mehr Ihre lokale E-Mail-Organisation verwalten müssen bzw. keine Implementierung einer Lösung für einmaliges Anmelden (SSO) planen, können Sie Exchange von Ihren Servern deinstallieren und Ihre lokale Exchange-Organisation entfernen.
    
    Weitere Informationen erhalten Sie unter den folgenden Themen:
    
  - [Ändern oder Entfernen von Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Entfernen einer Exchange 2007-Organisation](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Deinstallieren von Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

