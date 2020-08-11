---
title: Verwenden von PowerShell zum Ausführen einer mehrstufigen Migration zu Microsoft 365
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
ms.custom: seo-marvel-apr2020
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: Erfahren Sie, wie Sie mithilfe von PowerShell Inhalte aus einem Quell-e-Mail-System mit einer mehrstufigen Migration zu Microsoft 365 im Laufe der Zeit migrieren.
ms.openlocfilehash: a50966f65bbec5e4b453c4caf02e4b89fa7d04b5
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606211"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a><span data-ttu-id="82ac5-103">Verwenden von PowerShell zum Ausführen einer mehrstufigen Migration zu Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="82ac5-103">Use PowerShell to perform a staged migration to Microsoft 365</span></span>

<span data-ttu-id="82ac5-104">*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="82ac5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="82ac5-105">Sie können die Inhalte von Benutzerpostfächern aus einem Quell-e-Mail-System mithilfe einer mehrstufigen Migration zu Microsoft 365 migrieren.</span><span class="sxs-lookup"><span data-stu-id="82ac5-105">You can migrate the contents of user mailboxes from a source email system to Microsoft 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="82ac5-p101">In diesem Artikel werden die Aufgaben im Zusammenhang mit einer mehrstufigen e-Mail-Migration mithilfe Exchange Online PowerShell erläutert. Das Thema, [was Sie über eine mehrstufige e-Mail-Migration wissen müssen](https://go.microsoft.com/fwlink/p/?LinkId=536487), bietet einen Überblick über den Migrationsprozess. Wenn Sie mit dem Inhalt dieses Artikels vertraut sind, verwenden Sie diese, um mit der Migration von Postfächern von einem e-Mail-System zu einem anderen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="82ac5-p102">Sie können auch das Exchange Admin Center verwenden, um eine mehrstufige Migration durchzuführen. Weitere Informationen finden Sie unter [Durchführen einer mehrstufigen Migration von e-Mails zu Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="82ac5-111">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="82ac5-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="82ac5-p103">Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 2-5 Minuten zum Erstellen eines Migrationsbatches. Nach dem Start des Migrationsbatches variiert die Dauer der Migration je nach der Anzahl der Postfächer im Batch, der Größe jedes Postfachs und der verfügbaren Netzwerkkapazität. Informationen zu anderen Faktoren, die sich auf die Dauer der Migration von Postfächern zu Microsoft 365 auswirken, finden Sie unter [Migrationsleistung](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="82ac5-p104">Bevor Sie dieses Verfahren bzw. diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Berechtigungen, die Sie benötigen, finden Sie unter dem Eintrag "Migration" unter dem Thema [Empfängerberechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="82ac5-p105">Um die Exchange Online-PowerShell-Cmdlets zu verwenden, müssen Sie angemeldet sein und die Cmdlets in Ihre lokale Windows PowerShell Sitzung importieren. Finden Sie Anweisungen unter[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShelll](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="82ac5-119">Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="82ac5-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="82ac5-120">Migrationsschritte</span><span class="sxs-lookup"><span data-stu-id="82ac5-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="82ac5-121">Schritt 1: Auf eine mehrstufige Migration vorbereiten</span><span class="sxs-lookup"><span data-stu-id="82ac5-121">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="82ac5-122">Bevor Sie Postfächer mithilfe einer mehrstufigen Migration zu Microsoft 365 migrieren, müssen Sie einige Änderungen an Ihrer Exchange-Umgebung vornehmen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-122">Before you migrate mailboxes to Microsoft 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="82ac5-p106">**Konfigurieren Sie Outlook Anywhere auf Ihrem lokalen Exchange Server**. Der E-Mail-Migrationsdienst verwendet Outlook Anywhere (auch bekannt als RPC über HTTP), um eine Verbindung mit Ihrem lokalen Exchange Server herzustellen. Informationen zum Einrichten von Outlook Anywhere für Exchange Server 2007 und Exchange 2003 finden Sie im Folgenden:</span><span class="sxs-lookup"><span data-stu-id="82ac5-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="82ac5-125">Exchange 2007: Aktivieren von Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="82ac5-125">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="82ac5-126">Konfigurieren von Outlook Anywhere mit Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="82ac5-126">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="82ac5-p107">Sie müssen ein Zertifikat verwenden, das von einer vertrauenswürdigen Zertifizierungsstelle (CA) mit Ihrer Outlook Anywhere-Konfiguration erstellt wurde. Outlook Anywhere kann nicht mit einem selbstsignierten Zertifikat konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren von SSL für Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="82ac5-130">**Optional: Stellen Sie sicher, dass Sie eine Verbindung zu Ihrer Exchange Organisation mit Outlook Anywhere** herstellen können. Versuchen Sie eine der folgenden Methoden, um die Verbindungseinstellungen zu testen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-130">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="82ac5-131">Verwenden Sie Outlook von außerhalb des Unternehmensnetzwerks zur Verbindung mit Ihrem lokalen Exchange-Postfach.</span><span class="sxs-lookup"><span data-stu-id="82ac5-131">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="82ac5-p108">Verwenden Sie die [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) , um die Verbindungseinstellungen zu testen. Verwenden Sie die Tests Outlook Anywhere (RPC über HTTP) oder Outlook-AutoErmittlung.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p108">Use the [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="82ac5-134">Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="82ac5-134">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="82ac5-p109">**Festlegen von Berechtigungen** Das lokale Benutzerkonto, das Sie zum Herstellen einer Verbindung mit Ihrer lokalen Exchange-Organisation (auch als Migrations Administrator bezeichnet) verwenden, muss über die erforderlichen Berechtigungen für den Zugriff auf die lokalen Postfächer verfügen, die Sie zu Microsoft 365 migrieren möchten. Dieses Benutzerkonto wird verwendet, wenn Sie eine Verbindung mit Ihrem e-Mail-System herstellen, indem Sie einen Migrations Endpunkt später in diesem Verfahren erstellen ([Schritt 3: Erstellen eines Migrations Endpunkts](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Microsoft 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="82ac5-137">Um die Postfächer zu migrieren, muss der Administrator eine der folgenden Berechtigungen haben:</span><span class="sxs-lookup"><span data-stu-id="82ac5-137">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="82ac5-138">Ein Mitglied der **Domänen-Admins** -Gruppe in Active Directory in der lokalen Organisation sein.</span><span class="sxs-lookup"><span data-stu-id="82ac5-138">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="82ac5-139">oder</span><span class="sxs-lookup"><span data-stu-id="82ac5-139">or</span></span>
    
- <span data-ttu-id="82ac5-140">**FullAccess** -Berechtigung für jedes lokale Postfach und die **WriteProperty** -Berechtigung zum Ändern der **TargetAddress** -Eigenschaft für die lokale Benutzerkonten besitzen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-140">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="82ac5-141">oder</span><span class="sxs-lookup"><span data-stu-id="82ac5-141">or</span></span>
    
- <span data-ttu-id="82ac5-142">Die **ReceiveAs** -Berechtigung für die lokale Postfachdatenbank besitzen, in der die Benutzerpostfächer gespeichert sind und die **WriteProperty** -Berechtigung besitzen, um die **TargetAddress** -Eigenschaft für die lokalen Benutzerkonten ändern zu können.</span><span class="sxs-lookup"><span data-stu-id="82ac5-142">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="82ac5-143">Anweisungen zum Festlegen dieser Berechtigungen finden Sie unter Zuweisen von [Berechtigungen zum Migrieren von Postfächern zu Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span><span class="sxs-lookup"><span data-stu-id="82ac5-143">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="82ac5-p110">**Deaktivieren von Unified Messaging (UM)** Wenn UM für die lokalen Postfächer aktiviert ist, die Sie migrieren, deaktivieren Sie UM vor der Migration. Aktivieren Sie UM für die Postfächer nach Abschluss der Migration. Weitere Anleitungen finden Sie unter[Deaktivieren von Unified Messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="82ac5-p111">**Verwenden Sie die Verzeichnissynchronisierung, um neue Benutzer in Microsoft 365 zu erstellen.** Sie verwenden die Verzeichnissynchronisierung, um alle lokalen Benutzer in Ihrer Microsoft 365-Organisation zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p111">**Use directory synchronization to create new users in Microsoft 365.** You use directory synchronization to create all the on-premises users in your Microsoft 365 organization.</span></span>
  
<span data-ttu-id="82ac5-p112">Sie müssen die Benutzer nach der Erstellung lizenzieren. Sie haben 30 Tage zum Hinzufügen von Lizenzen, nachdem die Benutzer erstellt wurden. Weitere Informationen zum Hinzufügen von Lizenzen finden Sie unter [Schritt 8: Aufgaben nach der Migration abschließen](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="82ac5-p113">Sie können entweder das Synchronisierungs Tool für Microsoft Azure Active Directory (Azure AD) oder die Microsoft Azure AD Sync Services verwenden, um Ihre lokalen Benutzer in Microsoft 365 zu synchronisieren und zu erstellen. Nachdem Postfächer zu Microsoft 365 migriert wurden, verwalten Sie Benutzerkonten in Ihrer lokalen Organisation und werden mit Ihrer Microsoft 365-Organisation synchronisiert. Weitere Informationen finden Sie unter[Verzeichnis Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span><span class="sxs-lookup"><span data-stu-id="82ac5-p113">You can use either the Microsoft Azure Active Directory (Azure AD) Synchronization Tool or the Microsoft Azure AD Sync Services  to synchronize and create your on-premises users in Microsoft 365. After mailboxes are migrated to Microsoft 365, you manage user accounts in your on-premises organization, and they're synchronized with your Microsoft 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="82ac5-155">Schritt 2: Erstellen einer CSV-Datei für einen Batch der mehrstufigen Migration</span><span class="sxs-lookup"><span data-stu-id="82ac5-155">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="82ac5-p114">Nachdem Sie die Benutzer identifiziert haben, deren lokale Postfächer nach Microsoft 365 migriert werden sollen, verwenden Sie eine CSV-Datei (Comma Separated Value), um einen Migrationsbatch zu erstellen. Jede Zeile in der CSV-Datei, die von Microsoft 365 zum Ausführen der Migration verwendet wird, enthält Informationen über ein lokales Postfach.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p114">After you identify the users whose on-premises mailboxes you want to migrate to Microsoft 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Microsoft 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="82ac5-p115">Es gibt keinen Grenzwert für die Anzahl der Postfächer, die Sie mithilfe einer mehrstufigen Migration zu Microsoft 365 migrieren können. Die CSV-Datei für einen Migrationsbatch kann maximal 2.000 Zeilen enthalten. Um mehr als 2.000 Postfächer zu migrieren, erstellen Sie zusätzliche CSV-Dateien, und verwenden Sie jede Datei, um einen neuen Migrationsbatch zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p115">There isn't a limit for the number of mailboxes that you can migrate to Microsoft 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="82ac5-161">**Unterstützte Attribute**</span><span class="sxs-lookup"><span data-stu-id="82ac5-161">**Supported attributes**</span></span>
  
<span data-ttu-id="82ac5-p116">Die CSV-Datei für eine mehrstufige Migration unterstützt die folgenden drei Attribute. Jede Zeile der CSV-Datei entspricht einem Postfach und muss einen Wert für jedes dieser Attribute enthalten.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="82ac5-164">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="82ac5-164">**Attribute**</span></span>|<span data-ttu-id="82ac5-165">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="82ac5-165">**Description**</span></span>|<span data-ttu-id="82ac5-166">**Erforderlich?**</span><span class="sxs-lookup"><span data-stu-id="82ac5-166">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="82ac5-167">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="82ac5-167">EmailAddress</span></span>  <br/> |<span data-ttu-id="82ac5-168">Gibt die primäre SMTP-E-Mail-Adresse, z. B. pilarp@contoso.com für lokale Postfächer an.</span><span class="sxs-lookup"><span data-stu-id="82ac5-168">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="82ac5-p117">Verwenden Sie die primäre SMTP-Adresse für lokale Postfächer und keine Benutzer-IDs von Microsoft 365. Wenn die lokale Domäne beispielsweise contoso.com heißt, die Microsoft 365-e-Mail-Domäne jedoch den Namen Service.contoso.com hat, verwenden Sie den contoso.com-Domänennamen für e-Mail-Adressen in der CSV-Datei.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Microsoft 365. For example, if the on-premises domain is named contoso.com but the Microsoft 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="82ac5-171">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="82ac5-171">Required</span></span>  <br/> |
|<span data-ttu-id="82ac5-172">Kennwort</span><span class="sxs-lookup"><span data-stu-id="82ac5-172">Password</span></span>  <br/> |<span data-ttu-id="82ac5-p118">Das Kennwort, das für das neue Postfach von Microsoft 365 festgelegt werden soll. Alle Kennworteinschränkungen, die auf Ihre Microsoft 365-Organisation angewendet werden, gelten auch für die Kennwörter, die in der CSV-Datei enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p118">The password to be set for the new Microsoft 365 mailbox. Any password restrictions that are applied to your Microsoft 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="82ac5-175">Optional</span><span class="sxs-lookup"><span data-stu-id="82ac5-175">Optional</span></span>  <br/> |
|<span data-ttu-id="82ac5-176">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="82ac5-176">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="82ac5-p119">Gibt an, ob ein Benutzer das Kennwort ändern muss, wenn er sich das erste Mal bei seinem neuen Microsoft 365-Postfach anmeldet. Verwenden Sie für den Wert dieses Parameters **true** oder **false** .</span><span class="sxs-lookup"><span data-stu-id="82ac5-p119">Specifies whether a user must change the password the first time they sign in to their new Microsoft 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="82ac5-179">> [!NOTE]> Wenn Sie eine Lösung für einmaliges Anmelden (SSO) durch die Bereitstellung von Active Directory-Verbunddiensten (AD FS) oder höher in Ihrer lokalen Organisation implementiert haben, verwenden Sie **False** als Wert für das Attribut **ForceChangePassword**.</span><span class="sxs-lookup"><span data-stu-id="82ac5-179">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="82ac5-180">Optional</span><span class="sxs-lookup"><span data-stu-id="82ac5-180">Optional</span></span>  <br/> |
   
 <span data-ttu-id="82ac5-181">**CSV-Dateiformat**</span><span class="sxs-lookup"><span data-stu-id="82ac5-181">**CSV file format**</span></span>
  
<span data-ttu-id="82ac5-p120">Hier ist ein Beispiel für das Format für die CSV-Datei. In diesem Beispiel werden drei lokale Postfächer zu Microsoft 365 migriert.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Microsoft 365.</span></span>
  
<span data-ttu-id="82ac5-p121">In der ersten Zeile (auch als Kopfzeile bezeichnet) der CSV-Datei sind die Namen der Attribute oder Felder aufgelistet, die in den folgenden Zeilen angegeben werden. Die einzelnen Attributnamen werden jeweils durch ein Komma getrennt.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="82ac5-p122">Die Zeilen unter der Kopfzeile stellen einen Benutzer dar und enthalten die Informationen, die zum Migrieren des Postfachs des Benutzers verwendet werden. Die Attributwerte in jeder einzelnen Zeile müssen die gleiche Reihenfolge aufweisen wie die Attributnamen in der Kopfzeile.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="82ac5-p123">Sie können einen beliebigen Text-Editor oder eine Anwendung wie Excel zum Erstellen der CSV-Datei verwenden. Speichern Sie die Datei als CSV- oder TXT-Datei.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="82ac5-p124">Wenn die CSV-Datei Nicht-ASCII-Zeichen oder Sonderzeichen enthält, muss sie mit UTF-8-Codierung oder einer anderen Unicode-Codierung gespeichert werden. Abhängig von der Anwendung kann es leichter sein, die CSV-Datei mit UTF-8-Codierung oder einer anderen Unicode-Codierung zu speichern, wenn das Systemgebietsschema des Computers der in der CSV-Datei verwendeten Sprache entspricht.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="82ac5-192">Schritt 3: Migrationsendpunkt erstellen</span><span class="sxs-lookup"><span data-stu-id="82ac5-192">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="82ac5-193"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="82ac5-193"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="82ac5-p125">Um e-Mails erfolgreich zu migrieren, muss Microsoft 365 eine Verbindung herstellen und mit dem Quell-e-Mail-System kommunizieren. Zu diesem Zwecke verwendet Microsoft 365 einen Migrations Endpunkt. Zum Erstellen eines Outlook Anywhere-Migrations Endpunkts mit PowerShell für die mehrstufige Migration stellen [Sie zunächst eine Verbindung mit Exchange Online her](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="82ac5-p125">To migrate email successfully, Microsoft 365 needs to connect and communicate with the source email system. To do this, Microsoft 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="82ac5-197">Eine vollständige Liste der Migrationsbefehle finden Sie unter [Verschiebungs- und Migrations-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="82ac5-197">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="82ac5-198">Zum Erstellen eines Migrationsendpunkts von Outlook Anywhere, bezeichnet als "StagedEndpoint" in Exchange Online PowerShell, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="82ac5-198">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="82ac5-199">Weitere Informationen zu den **New-MigrationEndpoint** -Cmdlets finden Sie unter[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span><span class="sxs-lookup"><span data-stu-id="82ac5-199">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="82ac5-p126">Beim Cmdlet **New-MigrationEndpoint** können Sie mit der Option **-TargetDatabase** eine von dem Dienst zu verwendende Datenbank angeben. Andernfalls wird nach dem Zufallsprinzip eine Datenbank aus dem Active Directory-Verbunddienste (AD FS) 2.0-Standort zugewiesen, in dem sich das Verwaltungspostfach befindet.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="82ac5-202">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="82ac5-202">Verify it worked</span></span>

<span data-ttu-id="82ac5-203">Führen Sie den folgenden Befehl zum Anzeigen von Informationen zum Migrationsendpunkt "StagedEndpoint" in Exchange Online PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="82ac5-203">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="82ac5-204">Schritt 4: Erstellen und starten eines Batches für eine mehrstufige Migration</span><span class="sxs-lookup"><span data-stu-id="82ac5-204">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="82ac5-205"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="82ac5-205"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="82ac5-p127">Sie können das **New-MigrationBatch** -Cmdlet in Exchange Online PowerShell verwenden, um einen Migrationsbatch für eine Übernahmemigration zu erstellen. Sie können einen Migrationsbatch erstellen und diesen automatisch starten, indem Sie den Parameter _AutoStart_ verwenden. Alternativ können Sie den Migrationsbatch erstellen und später mithilfe des **Start-MigrationBatch** -Cmdlets manuell starten. In diesem Beispiel wird ein Migrationsbatch namens "StagedBatch1" erstellt und verwendet den Migrationsendpunkt, der im vorherigen Schritt erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="82ac5-p128">In diesem Beispiel wird auch ein Migrationsbatch namens "StagedBatch1" erstellt und verwendet den Migrationsendpunkt, der im vorherigen Schritt erstellt wurde. Da der Parameter  _AutoStart_ nicht verwendet wird, muss der Migrationsbatch manuell im Migrationsdashboard gestartet werden oder mithilfe des **Start-MigrationBatch** -Cmdlets . Wie bereits erwähnt, kann immer nur ein Übernahmemigrationsbatch ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="82ac5-213">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="82ac5-213">Verify it worked</span></span>

<span data-ttu-id="82ac5-214">Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den "StagedBatch1" anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="82ac5-214">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="82ac5-215">Sie können auch überprüfen, ob der Batch gestartet wurde, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="82ac5-215">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="82ac5-216">Weitere Informationen zu den **Get-MigrationBatch** -Cmdlets finden Sie unter[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="82ac5-216">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="82ac5-217">Schritt 5: Konvertieren lokaler Postfächer in E-Mail-aktivierte Benutzer</span><span class="sxs-lookup"><span data-stu-id="82ac5-217">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="82ac5-218"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="82ac5-218"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="82ac5-p129">Nachdem Sie einen Batch von Postfächern erfolgreich migriert haben, müssen Sie eine Möglichkeit haben, Benutzern das Abrufen Ihrer e-Mails zu ermöglichen. Ein Benutzer, dessen Postfach migriert wurde, verfügt nun über ein lokales Postfach und eines in Microsoft 365. Benutzer mit einem Postfach in Microsoft 365 werden keine neuen e-Mails mehr in Ihrem lokalen Postfach empfangen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Microsoft 365. Users who have a mailbox in Microsoft 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="82ac5-p130">Da Sie nicht mit ihren Migrationen fertig sind, sind Sie noch nicht dazu in der Lage, alle Benutzer zu Microsoft 365 für Ihre e-Mails zu leiten. Was tun Sie also für die Menschen, die beides haben? Sie können die lokalen Postfächer ändern, die Sie bereits in e-Mail-aktivierte Benutzer migriert haben. Wenn Sie von einem Postfach zu einem e-Mail-aktivierten Benutzer wechseln, können Sie den Benutzer an Microsoft 365 für Ihre e-Mails verweisen, anstatt zu Ihrem lokalen Postfach zu gehen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Microsoft 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Microsoft 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="82ac5-p131">Ein weiterer wichtiger Grund für das Konvertieren lokaler Postfächer in e-Mail-aktivierte Benutzer besteht darin, Proxyadressen aus den Microsoft 365-Postfächern beizubehalten, indem Proxyadressen an die e-Mail-aktivierten Benutzer kopiert werden. Auf diese Weise können Sie Cloud-basierte Benutzer aus Ihrer lokalen Organisation mithilfe von Active Directory verwalten. Wenn Sie sich entscheiden, Ihre lokale Exchange Server Organisation außer Betrieb zu nehmen, nachdem alle Postfächer zu Microsoft 365 migriert wurden, verbleiben die Proxyadressen, die Sie in die e-Mail-aktivierten Benutzer kopiert haben, in Ihrer lokalen Active Directory.</span><span class="sxs-lookup"><span data-stu-id="82ac5-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Microsoft 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Microsoft 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="82ac5-229">Schritt 6: Löschen eines Batches für die mehrstufige Migration</span><span class="sxs-lookup"><span data-stu-id="82ac5-229">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="82ac5-230"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="82ac5-230"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="82ac5-231">Nachdem alle Postfächer in einem Migrationsbatch erfolgreich migriert wurden und Sie die lokalen Postfächer im Batch in E-Mail-aktivierte Benutzer konvertiert haben, können Sie einen Batch der mehrstufigen Migration löschen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-231">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span></span> <span data-ttu-id="82ac5-232">Stellen Sie sicher, dass die e-Mails an die Microsoft 365-Postfächer im Migrationsbatch weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="82ac5-232">Be sure to verify that mail is being forwarded to the Microsoft 365 mailboxes in the migration batch.</span></span> <span data-ttu-id="82ac5-233">Wenn Sie einen Batch für die mehrstufige Migration löschen, bereinigt der Migrationsdienst alle zum Migrationsbatch gehörenden Datensätze und löscht den Migrationsbatch.</span><span class="sxs-lookup"><span data-stu-id="82ac5-233">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="82ac5-234">Führen Sie den folgenden Befehl aus, um den Migrationsbatch "StagedBatch1" in Exchange Online PowerShell zu löschen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-234">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="82ac5-235">Weitere Informationen zu dem **Remove-MigrationBatch** -Cmdlet finden Sie unter[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="82ac5-235">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="82ac5-236">Stellen Sie die Funktion sicher</span><span class="sxs-lookup"><span data-stu-id="82ac5-236">Verify it worked</span></span>

<span data-ttu-id="82ac5-237">Führen Sie den folgenden Befehl in Exchange Online PowerShell aus, um Informationen über den "IMAPBatch1" anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="82ac5-237">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="82ac5-238">Der Befehl gibt entweder den Migrationsbatch mit dem Status **Removing** zurück oder einen Fehler, der besagt, dass der Migrationsbatch nicht gefunden werden konnte, was bestätigt, dass er gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="82ac5-238">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="82ac5-239">Weitere Informationen zu den **Get-MigrationBatch** -Cmdlets finden Sie unter[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="82ac5-239">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-microsoft-365-users"></a><span data-ttu-id="82ac5-240">Steps: Zuweisen von Lizenzen zu Microsoft 365-Benutzern</span><span class="sxs-lookup"><span data-stu-id="82ac5-240">Step7: Assign licenses to Microsoft 365 users</span></span>
<span data-ttu-id="82ac5-241"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="82ac5-241"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="82ac5-242">Aktivieren Sie Microsoft 365-Benutzerkonten für die migrierten Konten durch Zuweisen von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-242">Activate Microsoft 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="82ac5-243">Wenn Sie keine Lizenz zuweisen, wird das Postfach deaktiviert, sobald die Karenzzeit (30 Tage) endet.</span><span class="sxs-lookup"><span data-stu-id="82ac5-243">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="82ac5-244">Informationen zum Zuweisen einer Lizenz im Microsoft 365 Admin Center finden Sie unter [zuweisen oder](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)Aufheben der Zuweisung von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-244">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="82ac5-245">Schritt 8: Aufgaben nach der Migration abschließen</span><span class="sxs-lookup"><span data-stu-id="82ac5-245">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="82ac5-246"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="82ac5-246"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="82ac5-247">**Erstellen Sie einen AutoErmittlung-DNS-Eintrag, damit Benutzer problemlos auf ihre Postfächer zugreifen können.**</span><span class="sxs-lookup"><span data-stu-id="82ac5-247">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="82ac5-248">Nachdem alle lokalen Postfächer zu Microsoft 365 migriert wurden, können Sie einen Auto Ermittlungs-DNS-Eintrag für Ihre Microsoft 365-Organisation konfigurieren, um Benutzern die einfache Verbindung mit ihren neuen Microsoft 365-Postfächern mit Outlook und mobilen Clients zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-248">After all on-premises mailboxes are migrated to Microsoft 365, you can configure an Autodiscover DNS record for your Microsoft 365 organization to enable users to easily connect to their new Microsoft 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="82ac5-249">In diesem neuen DNS-Eintrag für die AutoErmittlung muss derselbe Namespace verwendet werden, den Sie für Ihre Microsoft 365-Organisation verwenden.</span><span class="sxs-lookup"><span data-stu-id="82ac5-249">This new Autodiscover DNS record has to use the same namespace that you're using for your Microsoft 365 organization.</span></span> <span data-ttu-id="82ac5-250">Wenn der Namespace für die Cloud-basierte Organisation beispielsweise "cloud.contoso.com" lautet, müssen Sie den DNS-Datensatz "autodiscover.cloud.contoso.com" für die AutoErmittlung erstellen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-250">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="82ac5-251">Microsoft 365 verwendet einen CNAME-Eintrag, um den AutoErmittlungsdienst für Outlook und Mobile Clients zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="82ac5-251">Microsoft 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="82ac5-252">Der CNAME-Eintrag für die AutoErmittlung muss folgende Informationen enthalten:</span><span class="sxs-lookup"><span data-stu-id="82ac5-252">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="82ac5-253">**Alias:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="82ac5-253">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="82ac5-254">**Ziel:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="82ac5-254">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="82ac5-255">Weitere Informationen finden Sie unter [Hinzufügen von DNS-Einträgen zum Verbinden Ihrer Domäne](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="82ac5-255">For more information, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="82ac5-256">**Nehmen Sie lokale Exchange-Server außer Betrieb.**</span><span class="sxs-lookup"><span data-stu-id="82ac5-256">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="82ac5-257">Nachdem Sie überprüft haben, dass alle e-Mails direkt an die Microsoft 365-Postfächer weitergeleitet werden und Sie Ihre lokale e-Mail-Organisation nicht mehr warten müssen oder keine SSO-Lösung implementieren möchten, können Sie Exchange von ihren Servern deinstallieren und Ihre lokale Exchange-Organisation entfernen.</span><span class="sxs-lookup"><span data-stu-id="82ac5-257">After you've verified that all email is being routed directly to the Microsoft 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="82ac5-258">Weitere Informationen erhalten Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="82ac5-258">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="82ac5-259">Ändern oder Entfernen von Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="82ac5-259">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="82ac5-260">Entfernen einer Exchange 2007-Organisation</span><span class="sxs-lookup"><span data-stu-id="82ac5-260">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="82ac5-261">Deinstallieren von Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="82ac5-261">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

