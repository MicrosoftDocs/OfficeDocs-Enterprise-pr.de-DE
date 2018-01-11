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
ms.custom: 
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "Zusammenfassung: Verwenden Sie Windows PowerShell für Office 365 zum Abrufen von Berichten zu allen Kundenmandanten, und aggregieren Sie die Daten an einem zentralen Speicherort."
ms.openlocfilehash: 825f0519b97522f664c34462c441d190cac4bb8e
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>Aggregieren von Kundenberichtsdaten über Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)

 **Zusammenfassung:** Verwenden Sie Windows PowerShell für Office 365 zum Abrufen von Berichten zu allen Kundenmandanten, und aggregieren Sie die Daten an einem zentralen Speicherort.
  
Standardmäßig verfügt Windows PowerShell für Office 365 nicht über eine integrierte Aggregation von Berichtsdaten mehrerer Kundenmandanten. Sie können jedoch dieses Beispielskript für Windows PowerShell für Office 365 verwenden, um alle Kundenmandanten zu durchlaufen und einzelne Berichte für jeden Kunden abrufen, sodass Sie die Berichtsdaten dann an einem zentralen Speicherort aggregieren können. Als Ergebnis verfügen Sie anschließend über einen einzigen Bericht für alle Ihre Kundenmandanten. 
  
DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP). Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen. Sie bündeln Office 365-Abonnements in Serviceangeboten für ihre Kunden. Wenn sie ein Office 365-Abonnement verkaufen, erhalten sie automatisch AOBO-Berechtigungen (Administer On Behalf Of, Verwalten im Namen von) für dieKundenmandanten, damit sie diese verwalten und Berichte darüber erstellen können.
## <a name="before-you-begin"></a>Bevor Sie beginnen:

Um dieses Skript verwenden zu können, müssen Sie für die folgenden Variablen Ihre eigenen Werte festlegen:
  
- **$UserName**: Der Benutzername des Partneradministrators. Mit diesen Anmeldeinformationen wird die Verbindung zu all Ihren Kundenmandanten hergestellt.
    
- **$OutputFile**: Dies ist die CSV-Datei, in der die Berichtsdaten aggregiert werden.
    
- **$ErrorFile**: Dies ist die Protokolldatei im Textformat zum Aufzeichnen von Fehlern.
    
- **$ScriptBlock**: Dieses Beispielskript verwendet **Get-MailboxActivityReport** und Parameter (z. B. Anfangs- und Enddaten), damit Sie direkt beginnen können. Wenn Sie andere Berichte erstellen möchten, ersetzen Sie den Namen durch den gewünschten Berichtsnamen sowie die notwendigen Parameter für **Get-MailboxActivityReport**.
    
- Öffnen Sie eine Windows PowerShell-Remotesitzung mit Exchange Online, indem Sie die unter [Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md) aufgeführten Schritte befolgen.
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>Verwenden von Windows PowerShell zum Aggregieren von Kundenmandantenberichten an einem zentralen Speicherort

1. Kopieren Sie dieses Skript, und fügen Sie es in Editor ein.
    
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

2. Speichern Sie das Skript unter GetMailboxActivityReport.ps1 an einem für Sie leicht auffindbaren Speicherort. Speichern Sie Datei zum Beispiel unter „C:\\O365 Scripts". 
    
3. Führen Sie mithilfe der folgenden Syntax das Skript remote in Windows PowerShell aus.
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

Dieses Beispielskript fügt den aggregierten Bericht in die Datei „ReportOutput.csv“ ein.
  
## <a name="see-also"></a>Siehe auch

#### 

[Hilfe für Partner](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Office 365-Berichterstattungswebdienst](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Berichterstellungs-Cmdlets in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)

