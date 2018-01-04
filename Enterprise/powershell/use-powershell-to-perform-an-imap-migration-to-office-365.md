---
title: "Verwenden von PowerShell zum Ausführen einer IMAP-Migration zu Office 365"
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: "Zusammenfassung: Hier erfahren Sie, wie Sie Windows PowerShell verwenden, um eine IMAP-Migration zu Office 365 auszuführen."
ms.openlocfilehash: 6187207d57723c9c69fa6fdc7885c91de6d5080f
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-an-imap-migration-to-office-365"></a><span data-ttu-id="30b27-103">Verwenden von PowerShell zum Ausführen einer IMAP-Migration zu Office 365</span><span class="sxs-lookup"><span data-stu-id="30b27-103">Use PowerShell to perform an IMAP migration to Office 365</span></span>

 <span data-ttu-id="30b27-104">**Zusammenfassung**: Hier erfahren Sie, wie Sie Windows PowerShell verwenden, um eine IMAP-Migration zu Office 365 auszuführen.</span><span class="sxs-lookup"><span data-stu-id="30b27-104">Summary: Learn how to use Windows PowerShell to perform an IMAP migration to Office 365.</span></span>
  
<span data-ttu-id="30b27-p101">Als Teil des Bereitstellungsprozesses von Office 365 können Sie auswählen, ob Sie die Inhalte von Benutzerpostfächern aus Ihrem IMAP-E-Mail-Dienst (Internet Mail Access Protocol) zu Office 365 migrieren möchten. Dieser Artikel führt Sie durch die Aufgaben für eine IMAP-Migration mithilfe von Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30b27-p101">As part of the process of deploying Office 365, you can choose to migrate the contents of user mailboxes from an Internet Mail Access Protocol (IMAP) email service to Office 365. This article walks you through the tasks for an email IMAP migration by using Exchange Online PowerShell.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="30b27-p102">Sie können auch die Exchange-Verwaltungskonsole zum Durchführen einer IMAP-Migration verwenden. Siehe [Migrieren von IMAP-Postfächern zu Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span><span class="sxs-lookup"><span data-stu-id="30b27-p102">You can also use the Exchange admin center to perform an IMAP migration. See [Migrate your IMAP mailboxes to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="30b27-109">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="30b27-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="30b27-p103">Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2 bis 5 Minuten, um einen Migrationsbatch zu erstellen. Nach dem Start der Migration variiert die Dauer der Migration abhängig von der Anzahl von Postfächern in dem Batch, der Größe der einzelnen Postfächer und Ihrer verfügbaren Netzkapazität. Informationen zu weiteren Faktoren, die sich auf die Dauer der Migration von Postfächern zu Office 365, auswirken, finden Sie unter [Migrationsleistung](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="30b27-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="30b27-p104">Bevor Sie dieses Verfahren bzw. diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Berechtigungen, die Sie benötigen, finden Sie unter dem Eintrag „Migration" in einer Tabelle im Thema [Empfängerberechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="30b27-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="30b27-p105">Um die Exchange Online-PowerShell-Cmdlets zu verwenden, müssen Sie angemeldet sein und die Cmdlets in Ihre lokale Windows PowerShell Sitzung importieren. Finden Sie Anweisungen unter[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShelll](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="30b27-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="30b27-117">Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="30b27-117">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="30b27-118">Folgende Einschränkungen gelten für IMAP-Migrationen:</span><span class="sxs-lookup"><span data-stu-id="30b27-118">The following restrictions apply to IMAP migrations:</span></span>
  
- <span data-ttu-id="30b27-p106">Nur Elemente aus dem Posteingang oder anderen E-Mail-Ordnern eines Benutzers können migriert werden. Sie können keine Kontakte, Kalenderelemente oder Aufgaben migrieren.</span><span class="sxs-lookup"><span data-stu-id="30b27-p106">Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.</span></span>
    
- <span data-ttu-id="30b27-121">Maximal 500.000 Elemente können aus dem Postfach eines Benutzers migriert werden.</span><span class="sxs-lookup"><span data-stu-id="30b27-121">A maximum of 500,000 items can be migrated from a user's mailbox.</span></span>
    
- <span data-ttu-id="30b27-122">Die maximale Nachrichtengröße, die migriert werden kann, beträgt 35 MB.</span><span class="sxs-lookup"><span data-stu-id="30b27-122">The maximum message size that can be migrated is 35 MB.</span></span>
    
## <a name="migration-steps"></a><span data-ttu-id="30b27-123">Migrationsschritte</span><span class="sxs-lookup"><span data-stu-id="30b27-123">Migration steps</span></span>

### <a name="step-1-prepare-for-an-imap-migration"></a><span data-ttu-id="30b27-124">Schritt 1: IMAP-Migration vorbereiten</span><span class="sxs-lookup"><span data-stu-id="30b27-124">Step 1: Prepare for an IMAP migration</span></span>
<span data-ttu-id="30b27-125"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="30b27-125"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="30b27-p107">**Wenn Sie eine Domäne für die IMAP-Organisation haben, fügen Sie sie als akzeptierte Domäne Ihrer Office 365-Organisation hinzu.** Wenn Sie dieselbe Domäne verwenden möchten, die Sie bereits für Ihre Office 365-Postfächer besitzen, müssen Sie sie zunächst als akzeptierte Domäne zu Office 365 hinzufügen. Nach dem Hinzufügen können Sie Ihre Benutzer in Office 365 erstellen. Weitere Informationen finden Sie unter[Überprüfen Ihrer Domäne in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="30b27-p107">**If you have a domain for you IMAP organization, add it as an accepted domain of your Office 365 organization.** If you want to use the same domain you already own for your Office 365 mailboxes, you first have to add it as an accepted domain to Office 365. After you have added it, you can create your users in Office 365. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="30b27-p108">**Fügen Sie die einzelnen Benutzer Office 365 hinzu, damit sie über ein Office 365-Postfach verfügen.** Anweisungen finden Sie unter[Hinzufügen von Benutzern zu Office 365 for Business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span><span class="sxs-lookup"><span data-stu-id="30b27-p108">**Add each user to Office 365 so that they have an Office 365 mailbox.** For instructions, see[Add users to Office 365 for business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span></span>
    
- <span data-ttu-id="30b27-p109">**Abrufen des FQDN des IMAP-Servers**. Sie müssen den vollqualifizierten Domänennamen (FQDN, auch als vollständiger Computername bezeichnet) des IMAP-Servers angeben, von dem Sie Postfachdaten migrieren möchten, wenn Sie einen IMAP-Migrationsendpunkt erstellen. Verwenden Sie einen IMAP-Client oder den Ping-Befehl, um sicherzustellen, dass Sie mit dem FQDN über das Internet mit dem IMAP-Server kommunizieren können.</span><span class="sxs-lookup"><span data-stu-id="30b27-p109">**Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.</span></span>
    
- <span data-ttu-id="30b27-p110">**Konfigurieren der Firewall zum Zulassen von IMAP-Verbindungen**. Sie müssen unter Umständen Ports in der Firewall der Organisation öffnen, in der sich der IMAP-Server befindet, damit Netzwerkdatenverkehr, der während der Migration aus dem Microsoft-Datencenter stammt, in die Organisation gelangen darf, in der sich der IMAP-Server befindet. Eine Liste der IP-Adressen, die von Microsoft-Datencentern verwendet werden, finden Sie unter [Ausgehende IP-Adressen](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span><span class="sxs-lookup"><span data-stu-id="30b27-p110">**Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span></span>
    
- <span data-ttu-id="30b27-p111">**Zuweisen der Administratorkontoberechtigungen für den Zugriff auf Postfächer in der IMAP-Organisation**. Wenn Sie Administratoranmeldeinformationen in der CSV-Datei verwenden, muss das verwendete Konto die erforderlichen Berechtigungen für den Zugriff auf die lokalen Postfächer besitzen. Die für den Zugriff auf Benutzerpostfächer erforderlichen Berechtigungen werden durch den jeweiligen IMAP-Server bestimmt.</span><span class="sxs-lookup"><span data-stu-id="30b27-p111">**Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.</span></span> 
    
- <span data-ttu-id="30b27-p112">**Um die Exchange Online-PowerShell-Cmdlets zu verwenden**, müssen Sie angemeldet sein und die Cmdlets in Ihre lokale Windows PowerShell-Sitzung importieren. Anweisungen finden Sie unter [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="30b27-p112">**To use the Exchange Online PowerShell cmdlets**, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
    
    <span data-ttu-id="30b27-143">Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="30b27-143">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
    
- <span data-ttu-id="30b27-p113">**Überprüfen, ob Sie mit Ihrem IMAP-Server eine Verbindung herstellen können**. Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um die Einstellungen für die Verbindung mit Ihrem IMAP-Server zu testen.</span><span class="sxs-lookup"><span data-stu-id="30b27-p113">**Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.</span></span>
    
  ```
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    <span data-ttu-id="30b27-146">Normalerweise wird für den **Port** -Parameter der Wert 143 für unverschlüsselte oder TLS-Verbindungen (Transport Layer Security) verwendet und der Wert 993 für SSL-Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="30b27-146">For the value of the **Port** parameter, it's typical to use 143 for unencrypted or Transport Layer Security (TLS) connections and to use 993 for SSL connections.</span></span>
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a><span data-ttu-id="30b27-147">Schritt 2: CSV-Datei für einen IMAP-Migrationsbatch erstellen</span><span class="sxs-lookup"><span data-stu-id="30b27-147">Step 2: Create a CSV file for an IMAP migration batch</span></span>
<span data-ttu-id="30b27-148"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="30b27-148"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="30b27-p114">Identifizieren Sie die Gruppe der Benutzer, deren Postfächer Sie in einem IMAP-Migrationsbatch migrieren möchten. Jede Zeile in der CSV-Datei enthält Informationen, die zum Herstellen einer Verbindung mit einem Postfach im IMAP-Messaging-System erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="30b27-p114">Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.</span></span>
  
<span data-ttu-id="30b27-151">Die folgenden Attribute sind für jeden Benutzer erforderlich:</span><span class="sxs-lookup"><span data-stu-id="30b27-151">Here are the required attributes for each user:</span></span> 
  
- <span data-ttu-id="30b27-152">**EmailAddress** gibt die Benutzer-ID für das Office 365-Postfach des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="30b27-152">**EmailAddress** specifies the user ID for the user's Office 365 mailbox.</span></span>
    
- <span data-ttu-id="30b27-153">**UserName** gibt den Anmeldenamen für das Konto an, das für den Zugriff auf das Postfach auf dem IMAP-Server verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="30b27-153">**UserName** specifies the logon name for the account to use to access the mailbox on the IMAP server.</span></span>
    
- <span data-ttu-id="30b27-154">**Password** gibt das Kennwort für das Konto in der Spalte UserName **UserName** an.</span><span class="sxs-lookup"><span data-stu-id="30b27-154">**Password** specifies the password for the account in the **UserName** column.</span></span>
    
<span data-ttu-id="30b27-p115">Das folgende Beispiel zeigt das Format der CSV-Datei. In diesem Beispiel werden drei Postfächer migriert:</span><span class="sxs-lookup"><span data-stu-id="30b27-p115">Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

<span data-ttu-id="30b27-157">Für das Attribut **UserName** können Sie zusätzlich zum Benutzernamen die Anmeldeinformationen eines Kontos verwenden, dem die erforderlichen Berechtigungen für den Zugriff auf Postfächer auf dem IMAP-Server zugewiesen wurden. Es folgen einige spezielle Formate, die für einige IMAP-Server verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="30b27-157">For the **UserName** attribute, in addition to the user name, you can use the credentials of an account that has been assigned the necessary permissions to access mailboxes on the IMAP server, the following are some of the specific formats used for some of the IMAP servers:</span></span>
  
 <span data-ttu-id="30b27-158">**Microsoft Exchange**</span><span class="sxs-lookup"><span data-stu-id="30b27-158">**Microsoft Exchange:**</span></span>
  
<span data-ttu-id="30b27-p116">Wenn Sie E-Mails aus der IMAP-Implementierung für Microsoft Exchange migrieren, verwenden Sie das Format **Domain/Admin_UserName/User_UserName** für das **UserName** -Attribut in der CSV-Datei. Angenommen, Sie migrieren die E-Mails für die Benutzer Terry Adams, Ann Beebe und Paul Cannon von Exchange. Sie haben ein Administrator-E-Mail-Konto, dessen Benutzername mailadmin **mailadmin** und dessen Kennwort P@ssw0rd **P@ssw0rd** lautet. Die CSV-Datei würde dann folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="30b27-p116">If you're migrating email from the IMAP implementation for Microsoft Exchange, use the format **Domain/Admin_UserName/User_UserName** for the **UserName** attribute in the CSV file. Let's say you're migrating email from Exchange for Terry Adams, Ann Beebe, and Paul Cannon. You have a mail administrator account, where the user name is **mailadmin** and the password is **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 <span data-ttu-id="30b27-163">**Dovecot**</span><span class="sxs-lookup"><span data-stu-id="30b27-163">**Dovecot:**</span></span>
  
<span data-ttu-id="30b27-p117">Verwenden Sie für IMAP-Server wie Dovecot-IMAP-Server, die Simple Authentication and Security Layer (SASL) unterstützen, das Format **User_UserName*Admin_UserName**, wobei das Sternchen ( * ) ein konfigurierbares Trennzeichen ist. Angenommen, Sie migrieren die E-Mails derselben Benutzer von einem Dovecot-IMAP-Server mithilfe der Administrator-Anmeldeinformationen **mailadmin** und **P@ssw0rd**. Die CSV-Datei würde dann folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="30b27-p117">For IMAP servers that support Simple Authentication and Security Layer (SASL), such as a Dovecot IMAP server, use the format **User_UserName*Admin_UserName**, where the asterisk ( * ) is a configurable separator character. Let's say you're migrating those same users' email from a Dovecot IMAP server using the administrator credentials **mailadmin** and **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 <span data-ttu-id="30b27-167">**Mirapoint**</span><span class="sxs-lookup"><span data-stu-id="30b27-167">**Mirapoint:**</span></span>
  
<span data-ttu-id="30b27-p118">Wenn Sie E-Mails von einem Mirapoint-Nachrichtenserver migrieren, verwenden Sie das Format **#user@domain#Admin_UserName#** für die Administratoranmeldeinformationen. Zum Migrieren von E-Mails von Mirapoint mithilfe der Administratoranmeldeinformationen mailadmin **mailadmin** und P@ssw0rd **P@ssw0rd** würde die CSV-Datei folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="30b27-p118">If you're migrating email from Mirapoint Message Server, use the format **#user@domain#Admin_UserName#** for the administrator credentials. To migrate email from Mirapoint using the administrator credentials **mailadmin** and **P@ssw0rd**, your CSV file would look like this:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 <span data-ttu-id="30b27-170">**Courier IMAP:**</span><span class="sxs-lookup"><span data-stu-id="30b27-170">**Courier IMAP:**</span></span>
  
<span data-ttu-id="30b27-p119">Auf einigen E-Mail-Quellsystemen, z. B. Courier IMAP, wird die Verwendung von Postfach-Administratoranmeldeinformationen bei der Migration von Postfächern zu Office 365 nicht unterstützt. Stattdessen können Sie Ihr E-Mail-Quellsystem für die Verwendung virtueller freigegebener Ordner einrichten. Mithilfe der virtuellen freigegebenen Ordner können Sie die Postfach-Administratoranmeldeinformationen verwenden, um auf Benutzerpostfächer im E-Mail-Quellsystem zuzugreifen. Weitere Informationen zum Konfigurieren virtueller freigegebener Ordner für Courier IMAP finden Sie unter [Freigegebene Ordner](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span><span class="sxs-lookup"><span data-stu-id="30b27-p119">Some source email systems, such as Courier IMAP, don't support using mailbox admin credentials to migrate mailboxes to Office 365. Instead, you can set up your source email system to use virtual shared folders. By using virtual shared folders, you can use the mailbox admin credentials to access user mailboxes on the source email system. For more information about how to configure virtual shared folders for Courier IMAP, see [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span></span>
  
<span data-ttu-id="30b27-p120">Um Postfächer zu migrieren, nachdem Sie auf dem E-Mail-Quellsystem virtuelle freigegebene Ordner eingerichtet haben, müssen Sie das optionale Attribut **UserRoot** in die Migrationsdatei einfügen. Dieses Attribut gibt das Verzeichnis an, in dem die einzelnen Benutzerpostfächer in der Struktur der virtuellen freigegebenen Ordner im E-Mail-Quellsystem gespeichert sind. Der Pfad zu Terrys Postfach lautet beispielsweise „/users/terry.adams".</span><span class="sxs-lookup"><span data-stu-id="30b27-p120">To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.</span></span>
  
<span data-ttu-id="30b27-178">Beispiel für eine CSV-Datei, die das Attribut **UserRoot** enthält:</span><span class="sxs-lookup"><span data-stu-id="30b27-178">Here's an example of a CSV file that contains the **UserRoot** attribute:</span></span>
  
```
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a><span data-ttu-id="30b27-179">Schritt 3: IMAP-Migrationsendpunkt erstellen</span><span class="sxs-lookup"><span data-stu-id="30b27-179">Step 3: Create an IMAP migration endpoint</span></span>
<span data-ttu-id="30b27-180"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="30b27-180"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="30b27-p121">Um E-Mails erfolgreich zu migrieren, muss Office 365 eine Verbindung zum E-Mail-Quellsystem herstellen und mit ihm kommunizieren. Zu diesem Zweck verwendet Office 365 einen Migrationsendpunkt. Der Migrationsendpunkt definiert außerdem die Anzahl der Postfächer, die gleichzeitig migriert werden, sowie die Anzahl der Postfächer, die gleichzeitig während einer inkrementellen Synchronisierung synchronisiert werden, die alle 24 Stunden auftritt. Um einen Migrationsendpunkt für die IMAP-Migration zu erstellen, [stellen Sie zunächst eine Verbindung mit Exchange Online her](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="30b27-p121">To migrate email successfully, Office 365 needs to connect to and communicate with the source email system. To do this, Office 365 uses a migration endpoint. The migration endpoint also defines the number of mailboxes to migrate simultaneously and the number of mailboxes to synchronize simultaneously during incremental synchronization, which occurs once every 24 hours. To create a migration end point for IMAP migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="30b27-185">Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="30b27-185">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="30b27-186">Zum Erstellen eines IMAP-Migrationsendpunkts namens „IMAPEndpoint“ in Exchange Online PowerShell, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="30b27-186">To create the IMAP migration endpoint called "IMAPEndpoint" in Exchange Online PowerShell, run the following command:</span></span>
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

<span data-ttu-id="30b27-p122">Sie können auch Parameter zum Angeben gleichzeitiger Migrationen, gleichzeitiger inkrementeller Migrationen und des zu verwendenden Ports hinzufügen. Der folgende Exchange Online PowerShell-Befehl erstellt einen IMAP-Migrationsendpunkt namens „IMAPEndpoint", der 50 gleichzeitige Migrationen und bis zu 25 gleichzeitige inkrementelle Synchronisierungen unterstützt. Darüber hinaus wird der Endpunkt für die Verwendung von Port 143 für die TLS-Verschlüsselung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="30b27-p122">You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.</span></span>
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

<span data-ttu-id="30b27-190">Weitere Informationen zu den **New-MigrationEndpoint** -Cmdlets finden Sie unter[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span><span class="sxs-lookup"><span data-stu-id="30b27-190">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="30b27-191">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="30b27-191">Verify it worked</span></span>

<span data-ttu-id="30b27-192">Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den „IMAPEndpoint“ anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="30b27-192">Run the following command in Exchange Online PowerShell to display information about the "IMAPEndpoint":</span></span>
  
```
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a><span data-ttu-id="30b27-193">Schritt 4: Erstellen und Starten eines IMAP-Migrationsbatches</span><span class="sxs-lookup"><span data-stu-id="30b27-193">Step 4: Create and start an IMAP migration batch</span></span>
<span data-ttu-id="30b27-194"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="30b27-194"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="30b27-p123">Sie können das [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439)-Cmdlet verwenden, um einen Migrationsbatch für eine IMAP-Migration zu erstellen. Sie können einen Migrationsbatch erstellen und automatisch durch Einschließen des  _AutoStart_-Parameters starten. Alternativ können Sie den Migrationsbatch erstellen und danach mithilfe des [Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440)-Cmdlets starten.</span><span class="sxs-lookup"><span data-stu-id="30b27-p123">You can use the [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet.</span></span>
  
<span data-ttu-id="30b27-198">Der folgende Exchange Online PowerShell-Befehl startet automatisch den Migrationsbatch namens „IMAPBatch1“ mit den IMAP-Endpunkt namens „IMAPEndpoint“:</span><span class="sxs-lookup"><span data-stu-id="30b27-198">The following Exchange Online PowerShell command will automatically start the migration batch called "IMAPBatch1" using the IMAP endpoint called "IMAPEndpoint":</span></span>
  
```
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\\Users\\Administrator\\Desktop\\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a><span data-ttu-id="30b27-199">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="30b27-199">Verify it worked</span></span>

<span data-ttu-id="30b27-200">Führen Sie das [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)-Cmdlet aus, um Informationen zu „IMAPBatch1" anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="30b27-200">Run the [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

<span data-ttu-id="30b27-201">Sie können auch überprüfen, ob der Batch gestartet wurde, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="30b27-201">You can also verify that the batch has started by running the following command:</span></span>
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="30b27-202">Schritt 5: Weiterleiten Ihrer E-Mails zu Office 365</span><span class="sxs-lookup"><span data-stu-id="30b27-202">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="30b27-203"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="30b27-203"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="30b27-p124">E-Mail-Systeme verwenden einen DNS-Eintrag namens MX-Eintrag, um zu bestimmen, wohin E-Mail-Nachrichten übermittelt werden sollen. Während der Migration von E-Mails hat der MX-Eintrag auf Ihr E-Mail-Quellsystem verwiesen. Da die E-Mail-Migration zu Office 365 jetzt abgeschlossen ist, sollte der MX-Eintrag nun auf Office 365 verweisen. Dadurch wird sichergestellt, dass E-Mails an Ihre Office 365-Postfächer übermittelt werden. Durch Verschieben des MX-Eintrags können Sie Ihr altes E-Mail-System ggf. auch deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="30b27-p124">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="30b27-p125">Für viele DNS-Anbieter gibt es bestimmte Anweisungen zum [Ändern des MX-Eintrags](https://go.microsoft.com/fwlink/p/?LinkId=279163). Wenn Ihr DNS-Anbieter nicht enthalten ist oder wenn Sie allgemeine Anweisungen erhalten möchten, finden Sie entsprechende Informationen unter [Erstellen und Konfigurieren eines DNS-Eintrags für Office 365](https://go.microsoft.com/fwlink/?LinkId=397449).</span><span class="sxs-lookup"><span data-stu-id="30b27-p125">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="30b27-p126">Es kann bis zu 72 Stunden dauern, bis die E-Mail-Systeme der Kunden und Partnern den geänderten MX-Eintrag erkennen. Warten Sie mindestens 72 Stunden, bevor Sie mit dem nächsten Schritt fortfahren: Schritt 6: IMAP-Migrationsbatch löschen.</span><span class="sxs-lookup"><span data-stu-id="30b27-p126">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.</span></span> 
  
### <a name="step-6-delete-imap-migration-batch"></a><span data-ttu-id="30b27-213">Schritt 6: IMAP-Migrationsbatch löschen</span><span class="sxs-lookup"><span data-stu-id="30b27-213">Step 6: Delete IMAP migration batch</span></span>
<span data-ttu-id="30b27-214"><a name="BK_Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="30b27-214"><a name="BK_Step6"> </a></span></span>

<span data-ttu-id="30b27-p127">Nachdem Sie den MX-Eintrag geändert und sichergestellt haben, dass alle E-Mails an die Office 365-Postfächer weitergeleitet werden, benachrichtigen Sie die Benutzer, dass ihre E-Mails zu Office 365 geleitet werden. Danach können Sie den IMAP-Migrationsbatch löschen. Überprüfen Sie Folgendes, bevor Sie den Migrationsbatch löschen.</span><span class="sxs-lookup"><span data-stu-id="30b27-p127">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the IMAP migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="30b27-p128">Alle Benutzer verwenden Office 365-Postfächer. Nachdem der Batch gelöscht wurde, werden E-Mails, die an Postfächer auf dem lokalen Exchange-Server gesendet werden, nicht mehr in die entsprechenden Office 365-Postfächer kopiert.</span><span class="sxs-lookup"><span data-stu-id="30b27-p128">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="30b27-p129">Office 365-Postfächer wurden mindestens einmal nach dem Start des direkten E-Mail-Versands synchronisiert. Stellen Sie hierzu sicher, dass der Wert im Feld „Zeit der letzten Synchronisierung" für den Migrationsbatch jünger als das Datum und die Uhrzeit ist, zu denen das direkte Weiterleiten von E-Mails an Office 365-Postfächer begonnen hat.</span><span class="sxs-lookup"><span data-stu-id="30b27-p129">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="30b27-222">Führen Sie den folgenden Befehl aus, um den Migrationsbatch „IMAPBatch1“ in Exchange Online PowerShell zu löschen:
</span><span class="sxs-lookup"><span data-stu-id="30b27-222">To delete the "IMAPBatch1" migration batch from Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity IMAPBatch1
```

<span data-ttu-id="30b27-223">Weitere Informationen zu dem **Remove-MigrationBatch** -Cmdlet finden Sie unter[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="30b27-223">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="30b27-224">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="30b27-224">Verify it worked</span></span>

<span data-ttu-id="30b27-225">Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den "IMAPBatch1" anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="30b27-225">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch IMAPBatch1"
```

<span data-ttu-id="30b27-226">Der Befehl gibt entweder den Migrationsbatch mit dem Status **Removing** zurück oder einen Fehler, der besagt, dass der Migrationsbatch nicht gefunden werden konnte, was bestätigt, dass er gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="30b27-226">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="30b27-227">Weitere Informationen zu den **Get-MigrationBatch** -Cmdlets finden Sie unter[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="30b27-227">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="30b27-228">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="30b27-228">See also</span></span>

#### 

[<span data-ttu-id="30b27-229">Problembehandlung der IMAP-Migration</span><span class="sxs-lookup"><span data-stu-id="30b27-229">IMAP Migration Troubleshooter</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536482)

