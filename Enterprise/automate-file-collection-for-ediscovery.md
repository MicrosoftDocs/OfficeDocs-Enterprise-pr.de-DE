---
title: "Automatisieren der Dateisammlung für eDiscovery"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
description: "Zusammenfassung: Erfahren Sie, wie Sie die Dateisammlung von Benutzercomputern für eDiscovery automatisieren."
ms.openlocfilehash: bb93bed80ec95511c6bbf4307d1f0c9e1d4f82cb
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="automate-file-collection-for-ediscovery"></a>Automatisieren der Dateisammlung für eDiscovery

 **Zusammenfassung:** Erfahren Sie, wie Sie die Dateisammlung von Benutzercomputern für eDiscovery automatisieren.
  
Alle Unternehmen können sich Rechtsstreitigkeiten oder anderen Arten von Rechtsverfahren gegenübersehen. Zwar bemühen sich Rechtsabteilungen darum, dieses Risiko zu senken, jedoch sind Rechtsstreitigkeiten ein Bestandteil des Geschäftslebens. Wenn sich ein Unternehmen einem Rechtsverfahren gegenübersieht, muss es dem Gericht und dem gegnerischen Anwalt durch Legal Discovery alle relevanten Dokumente zur Verfügung stellen. 
  
eDiscovery ist der Prozess, durch den Unternehmen die relevanten Dokumente, die im elektronischen Format vorliegen, erfassen, durchsuchen, identifizieren, aufbewahren, filtern und zur Verfügung stellen. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online und Exchange Online können große Mengen an Inhalten aufweisen. Je nach Version können diese Produkte eDiscovery und In-Situ-Speicher unterstützen (Lync über Exchange Server), was Rechtsabteilungen dabei hilft, die für einen bestimmten Fall wichtigsten Inhalte zu indizieren, zu identifizieren, zu archivieren und zu filtern.
  
Viele Dokumente werden auf den lokalen Computern der Benutzer (Verwalter) gespeichert und nicht an einem zentralen Ort. Dadurch wird es SharePoint 2013 im Prinzip unmöglich gemacht, zu suchen, und was nicht durchsucht werden kann, kann auch nicht in eDiscovery einbezogen werden. Diese Lösung zeigt Ihnen, wie Anmeldeskripts, System Center Orchestrator 2012 R2 und Windows PowerShell für Exchange Server verwendet werden, um die Identifizierung und Sammlung von Dokumenten von Benutzercomputern zu automatisieren.
  
## <a name="what-this-solution-does"></a>Funktionsweise dieser Lösung

Diese Lösung verwendet eine globale Sicherheitsgruppe, eine Gruppenrichtlinie und ein Windows PowerShell-Skript zum Auffinden, Inventarisieren und Erfassen von Inhalten und persönlichen Speicherdateien (Personal Storage Files, PST) von Outlook von lokalen Computern von Benutzern in einer verborgenen Dateifreigabe. Von dort können die PST-Dateien entweder in Exchange Server 2013 oder Exchange Online importiert werden. Alle Dateien werden dann anhand eines System Center Orchestrator 2012 R2-Runbooks zwecks langfristiger Speicherung und Indizierung durch SharePoint 2013 zu einer anderen Dateifreigabe in Microsoft Azure verschoben. Sie verwenden dann eDiscovery-Zentren in der lokalen SharePoint Online-Bereitstellung oder in SharePoint Online, wie Sie es regelmäßig zur Durchführung von eDiscovery tun. 
  
> [!IMPORTANT]
> Diese Lösung verwendet Robocopy, um Dateien auf den Computern von Verwaltern auf eine zentrale Dateifreigabe zu kopieren. Da Robocopy keine geöffneten oder gesperrten Dateien kopiert, werden alle Dateien, einschließlich PST-Dateien, die der Verwalter geöffnet hat, nicht erfasst. Diese müssen manuell erfasst werden. Diese Lösung stellt eine Liste bereit, in der explizit die Dateien, die nicht kopiert werden können, sowie der vollständige Pfad zu den einzelnen Dateien identifiziert werden. 
  
Das folgende Diagramm führt Sie durch alle Schritte und Elemente der Lösung.
  
![Übersicht über die automatische Dateierfassungslösung](images/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|****Legende****||
|:-----|:-----|
|![Magenta-Beschriftung 1](images/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|Erstellen Sie ein Gruppenrichtlinienobjekt (Group Policy Object, GPO), und ordnen Sie es dem Sammlungsanmeldeskript zu.  <br/> |
|![Magenta-Beschriftung 2](images/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| Konfigurieren Sie den GPO-Sicherheitsfilter, um das GPO nur auf die Gruppe der Verwalter anzuwenden. <br/> |
|![Magenta-Beschriftung 3](images/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Ein Verwalter meldet sich an, und das GPO wird ausgeführt und ruft das Sammlungsanmeldeskript auf.  <br/> |
|![Magenta-Beschriftung 4](images/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|Das Sammlungsanmeldeskript inventarisiert alle lokal verbundenen Laufwerke auf dem Computer des Verwalters, indem es nach den gewünschten Dateien sucht und ihren Speicherort aufzeichnet.  <br/> |
|![Magenta-Beschriftung 5](images/4bf8898c-44ad-4524-b983-70175804eb85.png)|Das Sammlungsanmeldeskript kopiert die inventarisierten Dateien in eine verborgene Dateifreigabe auf dem Staging Server.  <br/> |
|![Magenta-Beschriftung 6](images/99589726-0c7e-406b-a276-44301a135768.png)| (Option A) Führen Sie das PST-Importskript manuell aus, um die gesammelten PST-Dateien in Exchange Server 2013 zu importieren. <br/> |
|![Magenta-Beschriftung 7](images/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Option B) Importieren Sie die gesammelten PST-Dateien mithilfe des Office 365-Importtools und -prozesses in Exchange Online ein.  <br/> |
|![Magenta-Beschriftung 8](images/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Verschieben Sie alle gesammelten Dateien zur langfristigen Speicherung mit dem MoveToColdStorageSystem Center Orchestrator 2012 R2-Runbook in eine Azure-Dateifreigabe. <br/> |
|![Magenta-Beschriftung 9](images/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Indexieren Sie die Dateien in der Cold Storage-Dateifreigabe mit SharePoint 2013.  <br/> |
|![Magenta-Beschriftung 10](images/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Führen Sie eDiscovery für Inhalte in Cold Storage und im lokalen Exchange Server 2013 durch.  <br/> |
|![Magenta-Beschriftung 11](images/e59ab403-2f19-497a-92a5-549846dded66.png)|Führen Sie eDiscovery für Inhalte in Office 365 durch.  <br/> |
   
## <a name="prerequisites"></a>Voraussetzungen

Die Konfiguration dieser Lösung erfordert viele Elemente, von denen die meisten wahrscheinlich für eDiscovery vorhanden und konfiguriert sind. Für Elemente, die Sie nicht besitzen oder für die eine spezifische Konfiguration erforderlich ist, stellen wir Ihnen Links zur Verfügung, anhand derer Sie die Standardkonfiguration vornehmen können. Vor der Konfiguration der Lösung selbst, muss die Standardkonfiguration stehen.
  
### <a name="base-configuration"></a>Standardkonfiguration

|**Element**|**Link**|
|:-----|:-----|
|Active Directory-Domänendienste (AD DS)-Domäne  <br/> ||
|Internetkonnektivität von Ihrem lokalen Netzwerk aus  <br/> ||
|SQL Server 2012 zur Unterstützung von SharePoint 2013 und System Center Orchestrator 2012 R2  <br/> |[Bereitstellen von System Center 2012 - Orchestrator](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| (lokal oder Azure-basiert) für (erforderlich für Option A) <br/> ||
|Lokaler Dateifreigabenserver für Staging  <br/> ||
|Lokaler Exchange Server 2013 für PST-Import aus Option A  <br/> |CU5 (15.913.22) ist verfügbar unter [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[Bereitstellen von System Center 2012 - Orchestrator](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Office 365 (E3-Plan) mit Exchange Online und SharePoint Online (für Option B erforderlich)  <br/> |Informationen zur Anmeldung für ein Office 365-E3-Abonnement finden Sie unter [Abonnement für Office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).  <br/> |
|Azure-Abonnement mit einem virtuellen Computer  <br/> |Informationen zum Registrieren für ein Azure-Abonnement finden Sie unter [Anmelden bei Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010). <br/> |
|Eine VPN-Verbindung zwischen Ihrem lokalen Netzwerk und Ihrem Azure-Abonnement  <br/> |Informationen zum Einrichten eines VPN-Tunnels zwischen Ihrem Azure-Abonnement und Ihrem lokalen Netzwerk finden Sie unter [Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|SharePoint 2013eDiscovery ist zum Durchsuchen von SharePoint und Exchange Server 2013 sowie optional Lync Server 2013 konfiguriert  <br/> |Informationen zum Konfigurieren von eDiscovery auf diese Weise finden Sie unter [Konfigurieren von eDiscovery in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) und[Testumgebungsanleitung: Konfigurieren von eDiscovery für eine Testumgebung mit Exchange-, Lync-, SharePoint- und Windows-Dateifreigaben](https://go.microsoft.com/fwlink/p/?LinkId=393130).  <br/> |
|eDiscovery in Office 365 für SharePoint Online und Exchange Online  <br/> |Informationen zum Konfigurieren von eDiscovery in Office 365 finden Sie unter [Einrichten eines eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).  <br/> |
   
## <a name="configure-the-environment"></a>Konfigurieren der Umgebung

Nachdem nun die Basiskonfiguration steht, können Sie mit der Konfiguration der eigentlichen Lösung fortfahren. 
  
### <a name="staging-file-share"></a>Staging-Dateifreigabe

1. Erstellen Sie in der lokalen Domäne eine globale Sicherheitsgruppe mit dem Namen Custodians.
    
2. Erstellen Sie eine verborgene Dateifreigabe für die Dateien, die auf den Computern von Verwaltern erfasst werden. Dabei sollte es sich um einen lokalen Server handeln. Erstellen Sie beispielsweise auf einem Server namens Staging eine Dateifreigabe mit dem Namen Cases$. Das **$** ist erforderlich, um eine verborgene Freigabe zu erstellen.
    
3. Legen Sie die folgenden Freigabeberechtigungen fest:
    
  - Verwalter: Lesen, Ändern
    
  - Administratoren: Vollzugriff
    
  - Vertrauenswürdiges Exchange-Teilsystem: Lesen, Ändern
    
4. Öffnen Sie die Registerkarte **Sicherheit**, fügen Sie die Gruppe der Verwalter hinzu, und klicken Sie auf **Erweitert**. Legen Sie die folgenden Berechtigungen für die Gruppe der Verwalter fest:
    
  - **Typ: Verweigern**
    
  - **Gilt für: Diesen Ordner, Unterordner und Dateien**
    
5. Klicken Sie auf **Erweiterte Berechtigungen**, und wählen Sie Folgendes aus:
    
  - **Attribute lesen**
    
  - **Erweiterte Attribute lesen**
    
  - **Leseberechtigungen**
    
6. Testen Sie den Zugriff auf die Dateifreigabe „Cases$“ folgendermaßen:
    
1. Fügen Sie der Gruppe „Verwalter“ einen Benutzer hinzu.
    
2. Platzieren Sie eine Datei im Ordner „Cases$“.
    
3. Navigieren Sie als Benutzer zu dem Stagingserver, beispielsweise zur Freigabe \\\\Staging, um zu sehen, welche Freigaben verfügbar sind. Die Freigabe **Cases$** sollte nicht aufgeführt sein.
    
4. Geben Sie manuell den vollständigen Pfad zu der Freigabe „Cases$“ in Explorer ein. Dadurch sollte die Freigabe „Cases$“ geöffnet werden.
    
5. Versuchen Sie, die Datei zu öffnen, die Sie zuvor in der Freigabe platziert haben. Dies sollte fehlschlagen.
    
### <a name="logon-script"></a>Anmeldeskript

1. Kopieren Sie dieses Windows PowerShell-Skript, und fügen Sie es in Editor ein:
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\\\staging\\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_Log"
$CasePSTLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\\\\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. Speichern Sie das Skript unter CollectionScript.ps1 an einem für Sie leicht auffindbaren Speicherort, z. B. C:\\AFCScripts.
    
3. Verwenden Sie die Funktion „Gehe zu...“ in Editor, und nehmen Sie bei Bedarf die folgenden Änderungen vor:
    
|**Zeilennummer**|**Zu änderndes Element**|**Erforderlich/optional**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** -Variable. Beziehen Sie alle Dateityperweiterungen ein, die das Skript inventarisieren und in der Matrixvariable sammeln soll.<br/> |Optional  <br/> |
|76 und 77  <br/> |Ändern Sie die Auslegung der **$CaseNo** -Variable entsprechend Ihren Anforderungen. Das Skript erfasst das aktuelle Datum und die aktuelle Uhrzeit und fügt den Benutzernamen an.<br/> |Optional  <br/> |
|80  <br/> |Die **$CaseRootLocation** -Variable muss auf die Sammlungsdateifreigabe Ihrer Stagingserver festgelegt werden. Beispielsweise **\\\\Staging\\Cases$**.  <br/> |Erforderlich  <br/> |
   
4. Platzieren Sie die Datei „CollectionScript.ps1“ in die Netlogon-Dateifreigabe auf einem Domänencontroller. 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>Konfigurieren des Gruppenrichtlinienobjekts für das Anmeldeskript und die Verwaltergruppe

1. Konfigurieren Sie ein Anmeldeskript für die Gruppe „Verwalter", indem Sie die Schritte im Abschnitt „Zuweisen von Benutzeranmeldeskripts" im Thema [Verwenden von Skripts zum Starten, Herunterfahren, Anmelden und Abmelden in der Gruppenrichtlinie](https://go.microsoft.com/fwlink/p/?LinkId=614844) befolgen.
    
2. Entfernen Sie authentifizierte Benutzer aus der **Sicherheitsfilterung**, und fügen Sie die Verwaltergruppe hinzu.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>PST-Import, Option A, Skript für Exchange Server 2013

1.  Kopieren Sie das folgende Windows PowerShell-Skript, und fügen Sie es in Editor ein:
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\\PSTImport.ps1 \\\\FileShare\\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. Speichern Sie das Skript unter PSTImportScript.ps1 an einem für Sie leicht auffindbaren Speicherort. Erstellen Sie beispielsweise der Einfachheit halber einen Ordner auf Ihrem Stagingserver mit dem Namen\\\\Staging\\AFCScripts, und speichern Sie es dort.
    
3. Verwenden Sie die Funktion „Gehe zu...“ in Editor, und nehmen Sie bei Bedarf die folgenden Änderungen vor:
    
|**Zeilennummer**|**Zu änderndes Element**|**Erforderlich/optional**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** markiert die Postfachordner, in die PST-Dateien importiert werden. Ändern Sie dies bei Bedarf.<br/> |Optional  <br/> |
|17  <br/> |**$ConnectionUri** muss auf Ihrem eigenen Server festgelegt sein. <br/> > [!IMPORTANT]> Stellen Sie sicher, dass Ihre **$ConnectionUri** auf einen Speicherort „http://" und nicht „https://" zeigt. Mit „https://" funktioniert es nicht.          |Erforderlich  <br/> |
   
4. Stellen Sie sicher, dass das Exchange-Konto „Vertrauenswürdiges Teilsystem" Lese-, Schreib- und Ausführberechtigungen für die Freigabe \\\\Staging\\Cases$ aufweist.
    
5. Das PST-Importskript erfordert die folgenden zwei Eingabeparameter:
    
  - **$SourcePath** Der Speicherort der zu importierenden PST-Dateien, z. B. „\\\\Staging\\Cases$".
    
  - **$MailboxAlias** Der Alias des Zielpostfachs, in dem die importierten E-Mail-Elemente empfangen werden.
    
6. Wenn Sie beispielsweise alle PST-Dateien aus dem Pfad \\\\Staging\\Cases$ in ein Postfach mit dem Alias eDiscoveryMailbox importieren möchten, führen Sie das Skript wie folgt aus: `\\\\staging\\AFCscripts\\PSTImportScript.ps1 \\\\Staging\\cases$ eDiscoveryMailbox`
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST-Import, Option B, für Exchange Online

-  Erstellen Sie die Postfachstruktur, in der die importierten PST-Dateien platziert werden sollen. Weitere Informationen zum Erstellen eines Benutzerpostfachs in Exchange Online finden Sie unter[Erstellen von Benutzerpostfächern in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Cold Storage

1. Erstellen Sie eine Dateifreigabe auf dem Virtueller Azure-Computer, in der alle gesammelten Dateien platziert werden sollen, z. B. \\\\AZFile1\\ContentColdStorage.
    
2. Gewähren Sie dem Standardkonto für den Inhaltszugriff mindestens Leseberechtigungen für die Freigabe und alle Unterordner und Dateien. Weitere Informationen zum Konfigurieren der SharePoint 2013-Suche finden Sie unter [Erstellen und Konfigurieren einer Suchdienstanwendung in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. Wenn Sie beabsichtigen, PST-Dateien aus \\\\AZFile1\\ContentColdStorage zu importieren, gewähren Sie dem vertrauenswürdigen Teilsystem von Exchange Lese-, Schreib- und Ausführberechtigungen für die Freigabe.
    
### <a name="orchestrator"></a>Orchestrator

1. Laden Sie das [ MoveToColdStorage-Runbook](https://go.microsoft.com/fwlink/?LinkId=616095) aus dem Microsoft Download Center herunter.
    
2. Öffnen Sie den **Runbook Designer**, und klicken Sie im Bereich **Verbindungen** auf den Ordner, in den Sie das Runbook importieren möchten. Klicken Sie auf das Menü **Aktionen** und dann auf **Importieren**. Das Dialogfeld **Importieren** wird angezeigt.
    
3. Geben Sie im Feld **Dateispeicherort** den Pfad und Dateinamen des zu importierenden Runbooks ein, oder klicken Sie auf die drei Punkte ( **...**), um die zu importierende Datei zu suchen. 
    
4. Wählen Sie **Runbooks importieren** und **Verschlüsselte Orchestrator-Daten importieren**. Deaktivieren Sie **Zähler**, **Zeitpläne**, **Variablen**, **Computergruppen**, **Globale Konfigurationen importieren** und **Vorhandene globale Konfigurationen überschreiben**.
    
5. Klicken Sie auf **Fertig stellen**.
    
6. Bearbeiten Sie das Runbook **MoveFilesToColdStorage** wie folgt:
    
1. Aktivität **Datei verschieben** - Legen Sie den **Quelldatei**-Pfad auf die Sammlungsdateifreigabe fest, z. B. \\\\Staging\\cases$. Legen Sie den **Zielordner** auf die Cold Storage-Dateifreigabe in Azure fest, z. B. \\\\AZFile1\\ContentColdStorage. Wählen Sie **Datei mit eindeutigem Namen erstellen** aus.
    
2. Aktivität **Ordner löschen** - Legen Sie **Pfad:** auf die Sammlungsdateifreigabe fest, z. B. \\\\Staging\\cases$\\*, und wählen Sie **Alle Dateien und Unterordner löschen**. 
    
7. Stellen Sie das Runbook **MoveToColdStorage** anhand der Verfahren unter[Bereitstellen von Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120) bereit.
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Lokale SharePoint-Suche für Cold Storage

1. Erstellen Sie eine neue Inhaltsquelle in Ihrer SharePoint 2013-Farm für die Cold Storage-Freigabe in Azure, z. B. \\\\AZFile1\\ContentColdStorage. Weitere Informationen zum Verwalten von Inhaltsquellen finden Sie unter [Hinzufügen, Bearbeiten oder Löschen einer Inhaltsquelle in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004).
    
2. Starten Sie eine vollständige Durchforstung. Weitere Informationen finden Sie unter [Starten, Unterbrechen, Fortsetzen oder Anhalten von Durchforstungen in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Verwenden der Lösung

Es gibt fünf wichtige Schritte bei der Verwendung dieser Lösung, vorausgesetzt, Sie möchten die PST-Dateien nicht sowohl in Exchange Server 2013 als auch Exchange Online importieren. Dieser Abschnitt enthält Informationen zu sämtlichen Verfahren. Die primäre Interaktion mit der Lösung besteht in Folgendem:
  
1. Verwalten Sie die Benutzermitgliedschaft in der Gruppe der Verwalter.
    
2. Fehler
    
3. Verwalten des PST-Importvorgangs.
    
4. Verschieben der Sammlungsdateien in Cold Storage.
    
Alle anderen Schritte sind nicht spezifisch für diese Lösung. Sie sind standardmäßige administrative Aufgaben, die Sie für SharePoint 2013, Office 365 und Azure ausführen. Es gibt Elemente, für die diese Lösung keine Anleitung bietet und die Sie basierend auf den Anforderungen Ihres Unternehmens ausarbeiten müssen. Dazu gehören Folgende:
  
1. Überwachen Ihrer eDiscovery-Fälle und welche Verwalter welchen Fällen zugeordnet sind.
    
2. Nachverfolgen, welche Gruppen von Dateisammlungen welchem eDiscovery-Fall zugeordnet sind.
    
3. Koordinieren des Timings des Imports und der Schritte für das Verschieben in Cold Storage.
    
4. Verwalten des in Azure verbrauchten Dateispeicherplatzes.
    
5. Verwalten der Postfächer, in die die PST-Dateien importiert werden.
    
6. Sicherung und Wiederherstellung aller lokalen Daten.
    
### <a name="custodian-management"></a>Verwaltung von Verwaltern

- Um die automatische Dateisammlung für einen einzelnen Benutzer zu starten, fügen sie diese der Verwaltergruppe hinzu. Bei der nächsten Anmeldung des Benutzers wird das Anmeldeskript ausgeführt, dass der Verwaltergruppe über eine Gruppenrichtlinie zugewiesen wurde. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Überwachen der Dateiauflistung und Prüfen der Protokolldateien

1. Schauen Sie sich die Sammlungsdateifreigabe an, z. B.\\\\Staging\\cases$\\*, für den Sammlungsordner des Benutzers. Der Name des Ordners wird folgendermaßen formatiert:  *yyyyMMddHHmm_UserName*  .
    
2. Wenn die Sammlung abgeschlossen ist, öffnen Sie den Sammlungsordner, und navigieren Sie zum Ordner _Log. Im Ordner _Log finden Sie Folgendes:
    
  - Eine XML-Datei für jedes lokale Laufwerk auf dem Computer des Benutzers, z. B. **A.xml**, **C.xml**. Diese Dateien enthalten die Bestandslaufwerke, nach denen sie benannt sind, und sie werden für den robocopy-Vorgang verwendet.
    
    > [!NOTE]
    > Das Sammlungsskript erstellt nur für die Dateitypen einen Eintrag in der Bestandsdatei, die Sie im Skript selbst definiert haben. Es erstellt nicht für jede Datei auf dem Computer des Benutzers einen Bestandseintrag. 
  
  - Eine Protokolldatei mit dem Namen FileCopyErrors.log für jede Sammlungsausführung. Diese Datei enthält eine Auflistung der Dateien, die robocopy nicht in die Sammlungsdateifreigabe kopieren konnte, z. B. \\\\Staging\\cases$\\*. Sie müssen dies überprüfen und entscheiden, welche Aktionen für diese ausgelassenen Dateien ausgeführt werden sollen. In der Regel müssen Sie sie entweder manuell sammeln, wenn Sie sie benötigen, oder Sie entscheiden, dass sie nicht erforderlich sind und daher aus der Sammlung weggelassen werden können.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>PST-Import, Option A, für Exchange Server 2013

1. Melden Sie sich am Server an, der die Sammlungsdateifreigabe hostet, z. B. **Staging**, und öffnen Sie Windows PowerShell. Weitere Informationen zum Starten von Windows PowerShell finden Sie unter[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Legen Sie die Ausführungsrichtlinie auf uneingeschränkt fest. Geben Sie  `Set-ExecutionPolicy Unrestricted -Scope Process` in Windows PowerShell ein, und drücken Sie die EINGABETASTE.
    
3. Führen Sie die Datei „PSTImportScript.ps1" aus, und geben Sie die Parameter **$SourcePath** und **$MailboxAlias** an. Weitere Informationen zum Ausführen von Windows PowerShell-Skripts finden Sie unter[Ausführen von Skripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Überprüfen Sie die Ausgabe auf Fehler.
    
5. Bevor Sie versuchen, eine gleichnamige PST-Datei in dasselbe Postfach zu importieren, müssen Sie die Anforderung für den Postfachimport entfernen. Führen Sie dazu den folgenden Befehl aus:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Sie werden aufgefordert, jede einzelne Anforderung aus der Warteschlange zu entfernen. Reagieren Sie je nach Bedarf.
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST-Import, Option B, für Exchange Online

- Um die gesammelten PST-Dateien in Exchange Online zu platzieren, befolgen Sie die Verfahren im Abschnitt „Importieren von Dateien in Office 365 über den Netzwerkupload" unter [Office 365-Importdienst](https://go.microsoft.com/fwlink/p/?LinkId=614938).
    
### <a name="move-to-cold-storage"></a>Verschieben in Cold Storage

1. Führen Sie das Runbook **MoveToColdStorage** anhand der Verfahren unter[Bereitstellen von Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123) aus.
    
2. Schauen Sie sich die Azure-Dateifreigabe an, die Sie für die langfristige Speicherung verwenden, z. B. \\\\AZFile1\\ContentColdStorage, und die lokale Sammlungsdateifreigabe, z. B. \\\\Staging\\cases$. Die Dateien und Ordner sollten in der Cold Storage-Dateifreigabe eingeblendet und in der Sammlungsdateifreigabe ausgeblendet werden.
    
### <a name="ediscovery"></a>eDiscovery

1. Lassen Sie entweder zu, dass die vollständige Durchforstung der Cold Storage-Dateifreigabe wie geplant ausgeführt wird, oder initiieren Sie eine Durchforstung. Weitere Informationen zum Starten vollständiger oder inkrementeller Durchforstungen finden Sie unter [Starten, Unterbrechen, Fortsetzen oder Anhalten von Durchforstungen in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Erstellen Sie einen eDiscovery-Fall in SharePoint 2013, wenn Sie Option A für den PST-Dateiimport verwendet haben, oder erstellen Sie einen eDiscovery-Fall in SharePoint Online, wenn Sie Option B verwendet haben.
    

