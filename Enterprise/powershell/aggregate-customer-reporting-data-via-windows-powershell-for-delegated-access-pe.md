---
title: "Aggregieren von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "Zusammenfassung: Verwenden Sie Windows PowerShell für Office 365 zum Abrufen von Berichten zu allen Kundenmandanten, und aggregieren Sie die Daten an einem zentralen Speicherort."
ms.openlocfilehash: 89651971424d1b9a494335572d2654d8402ec146
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="b7e3e-103">Aggregieren von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="b7e3e-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="b7e3e-104">**Zusammenfassung:** Verwenden Sie Windows PowerShell für Office 365 zum Abrufen von Berichten zu allen Kundenmandanten, und aggregieren Sie die Daten an einem zentralen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-104">Summary: Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="b7e3e-p101">Standardmäßig verfügt Windows PowerShell für Office 365 nicht über eine integrierte Aggregation von Berichtsdaten mehrerer Kundenmandanten. Sie können jedoch dieses Beispielskript für Windows PowerShell für Office 365 verwenden, um alle Kundenmandanten zu durchlaufen und einzelne Berichte für jeden Kunden abrufen, sodass Sie die Berichtsdaten dann an einem zentralen Speicherort aggregieren können. Als Ergebnis verfügen Sie anschließend über einen einzigen Bericht für alle Ihre Kundenmandanten.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="b7e3e-p102">DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP). Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen. Sie bündeln Office 365-Abonnements in Serviceangeboten für ihre Kunden. Wenn sie ein Office 365-Abonnement verkaufen, erhalten sie automatisch AOBO-Berechtigungen (Administer On Behalf Of, Verwalten im Namen von) für dieKundenmandanten, damit sie diese verwalten und Berichte darüber erstellen können.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="b7e3e-112">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="b7e3e-112">Before you begin</span></span>

<span data-ttu-id="b7e3e-113">Um dieses Skript verwenden zu können, müssen Sie für die folgenden Variablen Ihre eigenen Werte festlegen:</span><span class="sxs-lookup"><span data-stu-id="b7e3e-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="b7e3e-p103">**$UserName**: Der Benutzername des Partneradministrators. Mit diesen Anmeldeinformationen wird die Verbindung zu all Ihren Kundenmandanten hergestellt.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="b7e3e-116">**$OutputFile**: Dies ist die CSV-Datei, in der die Berichtsdaten aggregiert werden.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="b7e3e-117">**$ErrorFile**: Dies ist die Protokolldatei im Textformat zum Aufzeichnen von Fehlern.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="b7e3e-p104">**$ScriptBlock**: Dieses Beispielskript verwendet **Get-MailboxActivityReport** und Parameter (z. B. Anfangs- und Enddaten), damit Sie direkt beginnen können. Wenn Sie andere Berichte erstellen möchten, ersetzen Sie den Namen durch den gewünschten Berichtsnamen sowie die notwendigen Parameter für **Get-MailboxActivityReport**.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="b7e3e-120">Öffnen Sie eine Windows PowerShell-Remotesitzung mit Exchange Online, indem Sie die unter [Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md) aufgeführten Schritte befolgen.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="b7e3e-121">Verwenden von Windows PowerShell zum Aggregieren von Kundenmandantenberichten an einem zentralen Speicherort</span><span class="sxs-lookup"><span data-stu-id="b7e3e-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="b7e3e-122">Kopieren Sie dieses Skript, und fügen Sie es in Editor ein.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. <span data-ttu-id="b7e3e-p105">Speichern Sie das Skript unter GetMailboxActivityReport.ps1 an einem für Sie leicht auffindbaren Speicherort. Speichern Sie Datei zum Beispiel unter „C:\\O365 Scripts".</span><span class="sxs-lookup"><span data-stu-id="b7e3e-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="b7e3e-125">Führen Sie mithilfe der folgenden Syntax das Skript remote in Windows PowerShell aus.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="b7e3e-126">Dieses Beispielskript fügt den aggregierten Bericht in die Datei „ReportOutput.csv“ ein.</span><span class="sxs-lookup"><span data-stu-id="b7e3e-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b7e3e-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b7e3e-127">See also</span></span>

#### 

[<span data-ttu-id="b7e3e-128">Hilfe für Partner</span><span class="sxs-lookup"><span data-stu-id="b7e3e-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="b7e3e-129">Office 365-Berichterstattungswebdienst</span><span class="sxs-lookup"><span data-stu-id="b7e3e-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="b7e3e-130">Berichterstellungs-Cmdlets in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="b7e3e-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

