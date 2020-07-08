---
title: Verwenden von PowerShell zum Ausführen einer mehrstufigen Migration zu Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: 'Zusammenfassung: Hier erfahren Sie, wie Sie Windows PowerShell verwenden, um eine mehrstufige Migration zu Office 365 auszuführen.'
ms.openlocfilehash: ca50edd079e17808c46ff5a956ed2efad34eb322
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052558"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>Verwenden von PowerShell zum Ausführen einer mehrstufigen Migration zu Office 365

Sie können den Inhalt von Benutzerpostfächern aus einem Quell-E-Mail-System mithilfe einer mehrstufigen Migration nach und nach zu Office 365 migrieren.
  
This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.
  
> [!NOTE]
> You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.
  
To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.
  
Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Migrationsschritte

### <a name="step-1-prepare-for-a-staged-migration"></a>Schritt 1: Auf eine mehrstufige Migration vorbereiten

Vor der Migration von Postfächern zu Office 365, mithilfe einer mehrstufigen Migration, müssen Sie einige Änderungen in Ihrer Exchange Umgebung vornehmen.
  
 **Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:
  
- [Exchange 2007: Aktivieren von Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Konfigurieren von Outlook Anywhere mit Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
 **Optional: Stellen Sie sicher, dass Sie eine Verbindung zu Ihrer Exchange Organisation mit Outlook Anywhere** herstellen können. Versuchen Sie eine der folgenden Methoden, um die Verbindungseinstellungen zu testen.
  
- Verwenden Sie Outlook von außerhalb des Unternehmensnetzwerks zur Verbindung mit Ihrem lokalen Exchange-Postfach.
    
- Verwenden Sie die [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) , um die Verbindungseinstellungen zu testen. Verwenden Sie Outlook Anywhere (RPC über HTTP) oder Outlook AutoErmittlung-Tests.
    
- Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).
  
Um die Postfächer zu migrieren, muss der Administrator eine der folgenden Berechtigungen haben:
  
- Ein Mitglied der **Domänen-Admins** -Gruppe in Active Directory in der lokalen Organisation sein.
    
    oder
    
- **FullAccess** -Berechtigung für jedes lokale Postfach und die **WriteProperty** -Berechtigung zum Ändern der **TargetAddress** -Eigenschaft für die lokale Benutzerkonten besitzen.
    
    oder
    
- Die **ReceiveAs** -Berechtigung für die lokale Postfachdatenbank besitzen, in der die Benutzerpostfächer gespeichert sind und die **WriteProperty** -Berechtigung besitzen, um die **TargetAddress** -Eigenschaft für die lokalen Benutzerkonten ändern zu können.
    
Anweisungen zum Festlegen dieser Berechtigungen finden Sie in [Zuweisen von Berechtigungen für die Migration von Postfächern zu Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).
  
 **Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.
  
You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Sie können entweder das Synchronisierungs Tool für Microsoft Azure Active Directory (Azure AD) oder die Microsoft Azure AD Sync Services verwenden, um Ihre lokalen Benutzer in Office 365 zu synchronisieren und zu erstellen. Nach der Migration von Postfächern zu Office 365, verwalten Sie Benutzerkonten in Ihrer lokalen Organisation und sie werden mit Ihrer Office 365 Organisation synchronisiert. Weitere Informationen finden Sie unter [Verzeichnisintegration](https://go.microsoft.com/fwlink/?LinkId=521788).
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Schritt 2: Erstellen einer CSV-Datei für einen Batch der mehrstufigen Migration

After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox. 
  
> [!NOTE]
> There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch. 
  
 **Unterstützte Attribute**
  
The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.
  
|**Attribut**|**Beschreibung**|**Erforderlich?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Gibt die primäre SMTP-E-Mail-Adresse, z. B. pilarp@contoso.com für lokale Postfächer an.  <br/> Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.  <br/> |Erforderlich  <br/> |
|Kennwort  <br/> |The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.  <br/> |Optional  <br/> |
|ForceChangePassword  <br/> |Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. <br/> > [!NOTE]> Wenn Sie eine Lösung für einmaliges Anmelden (SSO) durch die Bereitstellung von Active Directory-Verbunddiensten (AD FS) oder höher in Ihrer lokalen Organisation implementiert haben, verwenden Sie **False** als Wert für das Attribut **ForceChangePassword**.          |Optional  <br/> |
   
 **CSV-Dateiformat**
  
Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.
  
The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row. 
  
Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.
  
> [!NOTE]
> If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file. 
  
### <a name="step-3-create-a-migration-endpoint"></a>Schritt 3: Migrationsendpunkt erstellen
<a name="BK_Endpoint"> </a>

To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
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
> The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.
  
#### <a name="verify-it-worked"></a>Stellen Sie die Funktion sicher

Führen Sie den folgenden Befehl zum Anzeigen von Informationen zum Migrationsendpunkt "StagedEndpoint" in Exchange Online PowerShell aus:
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Schritt 4: Erstellen und starten eines Batches für eine mehrstufige Migration
<a name="BK_Endpoint"> </a>

You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.
  
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

After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox. 
  
Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox. 
  
Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.
    
### <a name="step-6-delete-a-staged-migration-batch"></a>Schritt 6: Löschen eines Batches für die mehrstufige Migration
<a name="BK_Endpoint"> </a>

 After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.
  
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
  
### <a name="step7-assign-licenses-to-office-365-users"></a>Schritt 7: Zuweisen von Lizenzen zu Office 365-Benutzern
<a name="BK_Endpoint"> </a>

Aktivieren von Office 365 Benutzerkonten für die migrierten Konten durch Zuweisen von Lizenzen. Wenn Sie keine Lizenz zuweisen, wird das Postfach deaktiviert, sobald die Karenzzeit (30 Tage) endet. Weitere Informationen zum Zuweisen von Lizenzen im Microsoft 365 Admin Center finden Sie unter [Zuweisen von Lizenzen und Aufheben der Zuweisung von Lizenzen für Office 365 für Unternehmen](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Schritt 8: Aufgaben nach der Migration abschließen
<a name="BK_Postmigration"> </a>

- **Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.
    
    Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:
    
  - **Alias:** autodiscover
    
  - **Ziel:** autodiscover.outlook.com
    
    Weitere Informationen finden Sie unter [Erstellen von DNS-Einträgen für Office 365, wenn Sie Ihre DNS-Einträge verwalten](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.
    
    Weitere Informationen erhalten Sie unter den folgenden Themen:
    
  - [Ändern oder Entfernen von Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Entfernen einer Exchange 2007-Organisation](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Deinstallieren von Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

