---
title: Verwenden von PowerShell zum Ausführen einer IMAP-Migration zu Microsoft 365
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: 'Zusammenfassung: Hier erfahren Sie, wie Sie mit Windows PowerShell eine IMAP-Migration zu Microsoft 365 durchführen.'
ms.openlocfilehash: fa53fd1829121bb697277805e4f07d25ec2179b9
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229771"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a><span data-ttu-id="63dfc-103">Verwenden von PowerShell zum Ausführen einer IMAP-Migration zu Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="63dfc-103">Use PowerShell to perform an IMAP migration to Microsoft 365</span></span>

<span data-ttu-id="63dfc-104">*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="63dfc-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="63dfc-p101">Im Rahmen des Bereitstellungsprozesses von Microsoft 365 können Sie die Inhalte von Benutzerpostfächern von einem IMAP-e-Mail-Dienst (Internet Mail Access Protocol) zu Microsoft 365 migrieren. In diesem Artikel werden die Aufgaben für eine IMAP-e-Mail-Migration mithilfe Exchange Online PowerShell erläutert.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p101">As part of the process of deploying Microsoft 365, you can choose to migrate the contents of user mailboxes from an Internet Mail Access Protocol (IMAP) email service to Microsoft 365. This article walks you through the tasks for an email IMAP migration by using Exchange Online PowerShell.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="63dfc-p102">Sie können auch das Exchange Admin Center verwenden, um eine IMAP-Migration durchzuführen. Weitere Informationen finden Sie unter [Migrieren von IMAP-Postfächern](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p102">You can also use the Exchange admin center to perform an IMAP migration. See [Migrate your IMAP mailboxes](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="63dfc-109">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="63dfc-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="63dfc-p103">Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2-5 Minuten zum Erstellen eines Migrationsbatches. Nach dem Start des Migrationsbatches variiert die Dauer der Migration je nach der Anzahl der Postfächer im Batch, der Größe jedes Postfachs und der verfügbaren Netzwerkkapazität. Informationen zu anderen Faktoren, die sich auf die Dauer der Migration von Postfächern zu Microsoft 365 auswirken, finden Sie unter [Migrationsleistung](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="63dfc-p104">Bevor Sie dieses Verfahren bzw. diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Berechtigungen, die Sie benötigen, finden Sie unter dem Eintrag „Migration" in einer Tabelle im Thema [Empfängerberechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="63dfc-p105">Um die Exchange Online-PowerShell-Cmdlets zu verwenden, müssen Sie angemeldet sein und die Cmdlets in Ihre lokale Windows PowerShell Sitzung importieren. Finden Sie Anweisungen unter[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShelll](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="63dfc-117">Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="63dfc-117">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="63dfc-118">Folgende Einschränkungen gelten für IMAP-Migrationen:</span><span class="sxs-lookup"><span data-stu-id="63dfc-118">The following restrictions apply to IMAP migrations:</span></span>
  
- <span data-ttu-id="63dfc-p106">Nur Elemente aus dem Posteingang oder anderen E-Mail-Ordnern eines Benutzers können migriert werden. Sie können keine Kontakte, Kalenderelemente oder Aufgaben migrieren.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p106">Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.</span></span>
    
- <span data-ttu-id="63dfc-121">Maximal 500.000 Elemente können aus dem Postfach eines Benutzers migriert werden.</span><span class="sxs-lookup"><span data-stu-id="63dfc-121">A maximum of 500,000 items can be migrated from a user's mailbox.</span></span>
    
- <span data-ttu-id="63dfc-122">Die maximale Nachrichtengröße, die migriert werden kann, beträgt 35 MB.</span><span class="sxs-lookup"><span data-stu-id="63dfc-122">The maximum message size that can be migrated is 35 MB.</span></span>
    
## <a name="migration-steps"></a><span data-ttu-id="63dfc-123">Migrationsschritte</span><span class="sxs-lookup"><span data-stu-id="63dfc-123">Migration steps</span></span>

### <a name="step-1-prepare-for-an-imap-migration"></a><span data-ttu-id="63dfc-124">Schritt 1: IMAP-Migration vorbereiten</span><span class="sxs-lookup"><span data-stu-id="63dfc-124">Step 1: Prepare for an IMAP migration</span></span>
<span data-ttu-id="63dfc-125"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="63dfc-125"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="63dfc-p107">**Wenn Sie eine Domäne für Ihre IMAP-Organisation haben, fügen Sie Sie als akzeptierte Domäne Ihrer Microsoft 365-Organisation hinzu.** Wenn Sie dieselbe Domäne verwenden möchten, die Sie bereits für Ihre Microsoft 365-Postfächer besitzen, müssen Sie Sie zunächst als akzeptierte Domäne zu Microsoft 365 hinzufügen. Nachdem Sie das Programm hinzugefügt haben, können Sie Ihre Benutzer in Microsoft 365 erstellen. Weitere Informationen finden Sie unter[Überprüfen Ihrer Domäne](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p107">**If you have a domain for you IMAP organization, add it as an accepted domain of your Microsoft 365 organization.** If you want to use the same domain you already own for your Microsoft 365 mailboxes, you first have to add it as an accepted domain to Microsoft 365. After you have added it, you can create your users in Microsoft 365. For more information, see[Verify your domain](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="63dfc-p108">**Fügen Sie jeden Benutzer zu Microsoft 365 hinzu, sodass er über ein Postfach verfügt.** Anweisungen finden Sie unter[Hinzufügen von Benutzern zu Microsoft 365 for Business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p108">**Add each user to Microsoft 365 so that they have a mailbox.** For instructions, see[Add users to Microsoft 365 for business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span></span>
    
- <span data-ttu-id="63dfc-p109">**Abrufen des FQDN des IMAP-Servers**. Sie müssen den vollqualifizierten Domänennamen (FQDN, auch als vollständiger Computername bezeichnet) des IMAP-Servers angeben, von dem Sie Postfachdaten migrieren möchten, wenn Sie einen IMAP-Migrationsendpunkt erstellen. Verwenden Sie einen IMAP-Client oder den Ping-Befehl, um sicherzustellen, dass Sie mit dem FQDN über das Internet mit dem IMAP-Server kommunizieren können.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p109">**Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.</span></span>
    
- <span data-ttu-id="63dfc-p110">**Konfigurieren der Firewall zum Zulassen von IMAP-Verbindungen**. Sie müssen unter Umständen Ports in der Firewall der Organisation öffnen, in der sich der IMAP-Server befindet, damit Netzwerkdatenverkehr, der während der Migration aus dem Microsoft-Datencenter stammt, in die Organisation gelangen darf, in der sich der IMAP-Server befindet. Eine Liste der IP-Adressen, die von Microsoft-Datencentern verwendet werden, finden Sie unter [Ausgehende IP-Adressen](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p110">**Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span></span>
    
- <span data-ttu-id="63dfc-p111">**Zuweisen der Administratorkontoberechtigungen für den Zugriff auf Postfächer in der IMAP-Organisation**. Wenn Sie Administratoranmeldeinformationen in der CSV-Datei verwenden, muss das verwendete Konto die erforderlichen Berechtigungen für den Zugriff auf die lokalen Postfächer besitzen. Die für den Zugriff auf Benutzerpostfächer erforderlichen Berechtigungen werden durch den jeweiligen IMAP-Server bestimmt.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p111">**Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.</span></span> 
    
- <span data-ttu-id="63dfc-p112">**Um die Exchange Online-PowerShell-Cmdlets zu verwenden**, müssen Sie angemeldet sein und die Cmdlets in Ihre lokale Windows PowerShell-Sitzung importieren. Anweisungen finden Sie unter [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p112">**To use the Exchange Online PowerShell cmdlets**, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
    
    <span data-ttu-id="63dfc-143">Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="63dfc-143">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
    
- <span data-ttu-id="63dfc-p113">**Überprüfen, ob Sie mit Ihrem IMAP-Server eine Verbindung herstellen können**. Führen Sie in Exchange Online PowerShell den folgenden Befehl aus, um die Einstellungen für die Verbindung mit Ihrem IMAP-Server zu testen.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p113">**Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.</span></span>
    
  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    <span data-ttu-id="63dfc-146">Normalerweise wird für den **Port** -Parameter der Wert 143 für unverschlüsselte oder TLS-Verbindungen (Transport Layer Security) verwendet und der Wert 993 für SSL-Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="63dfc-146">For the value of the **Port** parameter, it's typical to use 143 for unencrypted or Transport Layer Security (TLS) connections and to use 993 for SSL connections.</span></span>
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a><span data-ttu-id="63dfc-147">Schritt 2: CSV-Datei für einen IMAP-Migrationsbatch erstellen</span><span class="sxs-lookup"><span data-stu-id="63dfc-147">Step 2: Create a CSV file for an IMAP migration batch</span></span>
<span data-ttu-id="63dfc-148"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="63dfc-148"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="63dfc-p114">Identifizieren Sie die Gruppe der Benutzer, deren Postfächer Sie in einem IMAP-Migrationsbatch migrieren möchten. Jede Zeile in der CSV-Datei enthält Informationen, die zum Herstellen einer Verbindung mit einem Postfach im IMAP-Messaging-System erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p114">Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.</span></span>
  
<span data-ttu-id="63dfc-151">Die folgenden Attribute sind für jeden Benutzer erforderlich:</span><span class="sxs-lookup"><span data-stu-id="63dfc-151">Here are the required attributes for each user:</span></span> 
  
- <span data-ttu-id="63dfc-152">**Email** -e-Mail gibt die Benutzer-ID für das Microsoft 365-Postfach des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="63dfc-152">**EmailAddress** specifies the user ID for the user's Microsoft 365 mailbox.</span></span>
    
- <span data-ttu-id="63dfc-153">**UserName** gibt den Anmeldenamen für das Konto an, das für den Zugriff auf das Postfach auf dem IMAP-Server verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="63dfc-153">**UserName** specifies the logon name for the account to use to access the mailbox on the IMAP server.</span></span>
    
- <span data-ttu-id="63dfc-154">**Password** gibt das Kennwort für das Konto in der Spalte UserName **UserName** an.</span><span class="sxs-lookup"><span data-stu-id="63dfc-154">**Password** specifies the password for the account in the **UserName** column.</span></span>
    
<span data-ttu-id="63dfc-p115">Das folgende Beispiel zeigt das Format der CSV-Datei. In diesem Beispiel werden drei Postfächer migriert:</span><span class="sxs-lookup"><span data-stu-id="63dfc-p115">Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

<span data-ttu-id="63dfc-157">Für das Attribut **UserName** können Sie zusätzlich zum Benutzernamen die Anmeldeinformationen eines Kontos verwenden, dem die erforderlichen Berechtigungen für den Zugriff auf Postfächer auf dem IMAP-Server zugewiesen wurden. Es folgen einige spezielle Formate, die für einige IMAP-Server verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="63dfc-157">For the **UserName** attribute, in addition to the user name, you can use the credentials of an account that has been assigned the necessary permissions to access mailboxes on the IMAP server, the following are some of the specific formats used for some of the IMAP servers:</span></span>
  
 <span data-ttu-id="63dfc-158">**Microsoft Exchange**</span><span class="sxs-lookup"><span data-stu-id="63dfc-158">**Microsoft Exchange:**</span></span>
  
<span data-ttu-id="63dfc-p116">Wenn Sie E-Mails aus der IMAP-Implementierung für Microsoft Exchange migrieren, verwenden Sie das Format **Domain/Admin_UserName/User_UserName** für das **UserName** -Attribut in der CSV-Datei. Angenommen, Sie migrieren die E-Mails für die Benutzer Terry Adams, Ann Beebe und Paul Cannon von Exchange. Sie haben ein Administrator-E-Mail-Konto, dessen Benutzername mailadmin **mailadmin** und dessen Kennwort P@ssw0rd **P@ssw0rd** lautet. Die CSV-Datei würde dann folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="63dfc-p116">If you're migrating email from the IMAP implementation for Microsoft Exchange, use the format **Domain/Admin_UserName/User_UserName** for the **UserName** attribute in the CSV file. Let's say you're migrating email from Exchange for Terry Adams, Ann Beebe, and Paul Cannon. You have a mail administrator account, where the user name is **mailadmin** and the password is **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 <span data-ttu-id="63dfc-163">**Dovecot**</span><span class="sxs-lookup"><span data-stu-id="63dfc-163">**Dovecot:**</span></span>
  
<span data-ttu-id="63dfc-p117">Verwenden Sie für IMAP-Server wie Dovecot-IMAP-Server, die Simple Authentication and Security Layer (SASL) unterstützen, das Format **User_UserName\*Admin_UserName**, wobei das Sternchen (\*) ein konfigurierbares Trennzeichen ist. Angenommen, Sie migrieren die E-Mails derselben Benutzer von einem Dovecot-IMAP-Server mithilfe der Administrator-Anmeldeinformationen **mailadmin** und **P@ssw0rd**. Die CSV-Datei würde dann folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="63dfc-p117">For IMAP servers that support Simple Authentication and Security Layer (SASL), such as a Dovecot IMAP server, use the format **User_UserName\*Admin_UserName**, where the asterisk ( \* ) is a configurable separator character. Let's say you're migrating those same users' email from a Dovecot IMAP server using the administrator credentials **mailadmin** and **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 <span data-ttu-id="63dfc-167">**Mirapoint**</span><span class="sxs-lookup"><span data-stu-id="63dfc-167">**Mirapoint:**</span></span>
  
<span data-ttu-id="63dfc-p118">Wenn Sie E-Mails von einem Mirapoint-Nachrichtenserver migrieren, verwenden Sie das Format **#user@domain#Admin_UserName#** für die Administratoranmeldeinformationen. Zum Migrieren von E-Mails von Mirapoint mithilfe der Administratoranmeldeinformationen mailadmin **mailadmin** und P@ssw0rd **P@ssw0rd** würde die CSV-Datei folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="63dfc-p118">If you're migrating email from Mirapoint Message Server, use the format **#user@domain#Admin_UserName#** for the administrator credentials. To migrate email from Mirapoint using the administrator credentials **mailadmin** and **P@ssw0rd**, your CSV file would look like this:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 <span data-ttu-id="63dfc-170">**Courier IMAP:**</span><span class="sxs-lookup"><span data-stu-id="63dfc-170">**Courier IMAP:**</span></span>
  
<span data-ttu-id="63dfc-p119">Einige Quell-e-Mail-Systeme wie Courier IMAP unterstützen keine Postfachadministrator-Anmeldeinformationen zum Migrieren von Postfächern nach Microsoft 365. Stattdessen können Sie Ihr Quell-e-Mail-System für die Verwendung virtueller freigegebener Ordner einrichten. Durch die Verwendung virtueller freigegebener Ordner können Sie die Postfachadministrator-Anmeldeinformationen für den Zugriff auf Benutzerpostfächer im Quell-e-Mail-System verwenden. Weitere Informationen zum Konfigurieren virtueller freigegebener Ordner für Courier IMAP finden Sie unter [freigegebene Ordner](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p119">Some source email systems, such as Courier IMAP, don't support using mailbox admin credentials to migrate mailboxes to Microsoft 365. Instead, you can set up your source email system to use virtual shared folders. By using virtual shared folders, you can use the mailbox admin credentials to access user mailboxes on the source email system. For more information about how to configure virtual shared folders for Courier IMAP, see [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span></span>
  
<span data-ttu-id="63dfc-p120">Um Postfächer zu migrieren, nachdem Sie auf dem E-Mail-Quellsystem virtuelle freigegebene Ordner eingerichtet haben, müssen Sie das optionale Attribut **UserRoot** in die Migrationsdatei einfügen. Dieses Attribut gibt das Verzeichnis an, in dem die einzelnen Benutzerpostfächer in der Struktur der virtuellen freigegebenen Ordner im E-Mail-Quellsystem gespeichert sind. Der Pfad zu Terrys Postfach lautet beispielsweise „/users/terry.adams".</span><span class="sxs-lookup"><span data-stu-id="63dfc-p120">To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.</span></span>
  
<span data-ttu-id="63dfc-178">Beispiel für eine CSV-Datei, die das Attribut **UserRoot** enthält:</span><span class="sxs-lookup"><span data-stu-id="63dfc-178">Here's an example of a CSV file that contains the **UserRoot** attribute:</span></span>
  
```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a><span data-ttu-id="63dfc-179">Schritt 3: IMAP-Migrationsendpunkt erstellen</span><span class="sxs-lookup"><span data-stu-id="63dfc-179">Step 3: Create an IMAP migration endpoint</span></span>
<span data-ttu-id="63dfc-180"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="63dfc-180"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="63dfc-p121">Um e-Mails erfolgreich zu migrieren, muss Microsoft 365 eine Verbindung mit dem Quell-e-Mail-System herstellen und mit ihm kommunizieren. Zu diesem Zwecke verwendet Microsoft 365 einen Migrations Endpunkt. Der Migrations Endpunkt definiert außerdem die Anzahl der gleichzeitig zu migrierenden Postfächer sowie die Anzahl der Postfächer, die bei der inkrementellen Synchronisierung gleichzeitig synchronisiert werden, was einmal alle 24 Stunden auftritt. Um einen Migrations Endpunkt für die IMAP-Migration zu erstellen, stellen Sie zunächst eine [Verbindung mit Exchange Online her](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="63dfc-p121">To migrate email successfully, Microsoft 365 needs to connect to and communicate with the source email system. To do this, Microsoft 365 uses a migration endpoint. The migration endpoint also defines the number of mailboxes to migrate simultaneously and the number of mailboxes to synchronize simultaneously during incremental synchronization, which occurs once every 24 hours. To create a migration end point for IMAP migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="63dfc-185">Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="63dfc-185">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="63dfc-186">Zum Erstellen eines IMAP-Migrationsendpunkts namens „IMAPEndpoint“ in Exchange Online PowerShell, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="63dfc-186">To create the IMAP migration endpoint called "IMAPEndpoint" in Exchange Online PowerShell, run the following command:</span></span>
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

<span data-ttu-id="63dfc-p122">Sie können auch Parameter zum Angeben gleichzeitiger Migrationen, gleichzeitiger inkrementeller Migrationen und des zu verwendenden Ports hinzufügen. Der folgende Exchange Online PowerShell-Befehl erstellt einen IMAP-Migrationsendpunkt namens „IMAPEndpoint", der 50 gleichzeitige Migrationen und bis zu 25 gleichzeitige inkrementelle Synchronisierungen unterstützt. Darüber hinaus wird der Endpunkt für die Verwendung von Port 143 für die TLS-Verschlüsselung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p122">You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.</span></span>
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

<span data-ttu-id="63dfc-190">Weitere Informationen zu den **New-MigrationEndpoint** -Cmdlets finden Sie unter[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span><span class="sxs-lookup"><span data-stu-id="63dfc-190">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="63dfc-191">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="63dfc-191">Verify it worked</span></span>

<span data-ttu-id="63dfc-192">Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den „IMAPEndpoint“ anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="63dfc-192">Run the following command in Exchange Online PowerShell to display information about the "IMAPEndpoint":</span></span>
  
```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a><span data-ttu-id="63dfc-193">Schritt 4: Erstellen und Starten eines IMAP-Migrationsbatches</span><span class="sxs-lookup"><span data-stu-id="63dfc-193">Step 4: Create and start an IMAP migration batch</span></span>
<span data-ttu-id="63dfc-194"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="63dfc-194"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="63dfc-p123">Sie können das [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439)-Cmdlet verwenden, um einen Migrationsbatch für eine IMAP-Migration zu erstellen. Sie können einen Migrationsbatch erstellen und automatisch durch Einschließen des  _AutoStart_-Parameters starten. Alternativ können Sie den Migrationsbatch erstellen und danach mithilfe des [Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440)-Cmdlets starten.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p123">You can use the [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet.</span></span>
  
<span data-ttu-id="63dfc-198">Der folgende Exchange Online PowerShell-Befehl startet automatisch den Migrationsbatch namens „IMAPBatch1“ mit den IMAP-Endpunkt namens „IMAPEndpoint“:</span><span class="sxs-lookup"><span data-stu-id="63dfc-198">The following Exchange Online PowerShell command will automatically start the migration batch called "IMAPBatch1" using the IMAP endpoint called "IMAPEndpoint":</span></span>
  
```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a><span data-ttu-id="63dfc-199">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="63dfc-199">Verify it worked</span></span>

<span data-ttu-id="63dfc-200">Führen Sie das [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)-Cmdlet aus, um Informationen zu „IMAPBatch1" anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="63dfc-200">Run the [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

<span data-ttu-id="63dfc-201">Sie können auch überprüfen, ob der Batch gestartet wurde, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="63dfc-201">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a><span data-ttu-id="63dfc-202">Schritt 5: weiterleiten Ihrer e-Mail an Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="63dfc-202">Step 5: Route your email to Microsoft 365</span></span>
<span data-ttu-id="63dfc-203"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="63dfc-203"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="63dfc-p124">E-Mail-Systeme verwenden einen DNS-Eintrag namens MX-Eintrag, um herauszufinden, wo e-Mails zugestellt werden sollen. Während des e-Mail-Migrationsvorgangs zeigte ihr MX-Eintrag auf Ihr Quell-e-Mail-System. Nachdem die e-Mail-Migration zu Microsoft 365 abgeschlossen ist, ist es an der Zeit, Ihren MX-Eintrag auf Microsoft 365 zu richten. Dadurch kann sichergestellt werden, dass e-Mails an Ihre Microsoft 365-Postfächer gesendet werden. Wenn Sie den MX-Eintrag verschieben, können Sie auch Ihr altes e-Mail-System deaktivieren, wenn Sie fertig sind.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p124">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Microsoft 365 is complete, it's time to point your MX record at Microsoft 365. This helps make sure that email is delivered to your Microsoft 365 mailboxes. By moving the MX record, you can also turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="63dfc-p125">Für viele DNS-Anbieter gibt es spezielle Anweisungen zum Ändern Ihres MX-Eintrags. Wenn Ihr DNS-Anbieter nicht enthalten ist oder Sie eine Vorstellung von den allgemeinen Anweisungen erhalten möchten, werden auch [Allgemeine Anweisungen](https://go.microsoft.com/fwlink/?LinkId=397449) für den MX-Eintrag bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p125">For many DNS providers, there are specific instructions to change your MX record. If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="63dfc-p126">Es kann bis zu 72 Stunden dauern, bis die E-Mail-Systeme der Kunden und Partnern den geänderten MX-Eintrag erkennen. Warten Sie mindestens 72 Stunden, bevor Sie mit dem nächsten Schritt fortfahren: Schritt 6: IMAP-Migrationsbatch löschen.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p126">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.</span></span> 
  
### <a name="step-6-delete-imap-migration-batch"></a><span data-ttu-id="63dfc-213">Schritt 6: IMAP-Migrationsbatch löschen</span><span class="sxs-lookup"><span data-stu-id="63dfc-213">Step 6: Delete IMAP migration batch</span></span>
<span data-ttu-id="63dfc-214"><a name="BK_Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="63dfc-214"><a name="BK_Step6"> </a></span></span>

<span data-ttu-id="63dfc-p127">Nachdem Sie den MX-Eintrag geändert und sichergestellt haben, dass alle e-Mails an Microsoft 365-Postfächer weitergeleitet werden, Benachrichtigen Sie die Benutzer, dass Ihre e-Mail-Nachrichten an Microsoft 365 gesendet werden. Anschließend können Sie den IMAP-Migrationsbatch löschen. Überprüfen Sie Folgendes, bevor Sie den Migrationsbatch löschen.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p127">After you change the MX record and verify that all email is being routed to Microsoft 365 mailboxes, notify the users that their mail is going to Microsoft 365. After this, you can delete the IMAP migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="63dfc-p128">Alle Benutzer verwenden Microsoft 365-Postfächer. Nach dem Löschen des Batches werden e-Mails, die an Postfächer im lokalen Exchange Server gesendet werden, nicht in die entsprechenden Microsoft 365-Postfächer kopiert.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p128">All users are using Microsoft 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Microsoft 365 mailboxes.</span></span>
    
- <span data-ttu-id="63dfc-p129">Microsoft 365-Postfächer wurden mindestens einmal synchronisiert, nachdem e-Mails direkt an Sie gesendet wurden. Stellen Sie dazu sicher, dass der Wert im Feld zuletzt synchronisierte Zeit für den Migrationsbatch aktueller ist als die Weiterleitung von e-Mails direkt an Microsoft 365-Postfächer.</span><span class="sxs-lookup"><span data-stu-id="63dfc-p129">Microsoft 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Microsoft 365 mailboxes.</span></span>
    
<span data-ttu-id="63dfc-222">Führen Sie den folgenden Befehl aus, um den Migrationsbatch „IMAPBatch1“ in Exchange Online PowerShell zu löschen:
</span><span class="sxs-lookup"><span data-stu-id="63dfc-222">To delete the "IMAPBatch1" migration batch from Exchange Online PowerShell, run the following command:</span></span>
  
```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

<span data-ttu-id="63dfc-223">Weitere Informationen zu dem **Remove-MigrationBatch** -Cmdlet finden Sie unter[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="63dfc-223">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="63dfc-224">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="63dfc-224">Verify it worked</span></span>

<span data-ttu-id="63dfc-225">Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den "IMAPBatch1" anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="63dfc-225">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch IMAPBatch1"
```

<span data-ttu-id="63dfc-226">Der Befehl gibt entweder den Migrationsbatch mit dem Status **Removing** zurück oder einen Fehler, der besagt, dass der Migrationsbatch nicht gefunden werden konnte, was bestätigt, dass er gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="63dfc-226">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="63dfc-227">Weitere Informationen zu den **Get-MigrationBatch** -Cmdlets finden Sie unter[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="63dfc-227">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="63dfc-228">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="63dfc-228">See also</span></span>

[<span data-ttu-id="63dfc-229">Problembehandlung der IMAP-Migration</span><span class="sxs-lookup"><span data-stu-id="63dfc-229">IMAP Migration Troubleshooter</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536482)

