---
title: Deaktivieren des Zugriffs auf Dienste während des Zuweisens von Benutzerlizenzen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: In diesem Artikel erfahren Sie, wie Sie Benutzerkonten Lizenzen zuweisen und gleichzeitig bestimmte Servicepläne mit Office 365 PowerShell deaktivieren.
ms.openlocfilehash: 7567d84490cdb3db7c149a51c4f2f04d39cad9ce
ms.sourcegitcommit: def3e311db9322e469753bac59ff03624349b140
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>Deaktivieren des Zugriffs auf Dienste während des Zuweisens von Benutzerlizenzen

**Zusammenfassung:** In diesem Artikel erfahren Sie, wie Sie Benutzerkonten Lizenzen zuweisen und gleichzeitig bestimmte Servicepläne mit Office 365 PowerShell deaktivieren.
  
Im Lieferumfang von Office 365-Abonnements sind Servicepläne für einzelne Dienste enthalten. Office 365-Administratoren müssen häufig bestimmte Pläne deaktivieren, wenn Sie Benutzern Lizenzen zuweisen. Mit den Anweisungen in diesem Artikel können Sie eine Office 365-Lizenz zuweisen und gleichzeitig bestimmte Servicepläne mithilfe der PowerShell für ein bestimmtes Benutzerkonto oder mehrere Benutzerkonten deaktivieren.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen

Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>Erfassen von Informationen über Abonnements und Servicepläne

Führen Sie diesen Befehl aus, um Ihre aktuellen Abonnements abzurufen:
  
```
Get-MsolAccountSku
```

In dem vom  `Get-MsolAccountSku`-Befehl zurückgegebenen Ergebnis gilt Folgendes:
  
- **AccountSkuId** ist ein Abonnement für Ihre Organisation im Format: \<Organisationsname>:\<Abonnement>. \< OrganizationName> ist der Wert, den Sie bei der Registrierung bei Office 365 angegeben haben. Dieser ist für Ihre Organisation eindeutig. Der \<Subscription>-Wert gilt für ein bestimmtes Abonnement. Beispiel: Für litwareinc:ENTERPRISEPACK ist der litwareinc der Name der Organisation und ENTERPRISEPACK (Office 365 Enterprise E3) ist der Name des Abonnements.
    
- **ActiveUnits** ist die Anzahl der Lizenzen, die Sie für das Abonnement erworben haben.
    
- **WarningUnits** gibt die Anzahl der Lizenzen in einem Abonnement an, die Sie nicht verlängert haben und die nach der 30-tägigen Toleranzperiode ablaufen werden.
    
- **ConsumedUnits** ist die Anzahl der Lizenzen, die Sie Benutzern für das Abonnement zugeordnet haben.
    
Beachten Sie das AccountSkuId-Objekt für Ihr Office 365-Abonnement, das die Benutzer enthält, die Sie lizenzieren möchten. Stellen Sie außerdem sicher, dass genügend Lizenzen zum Zuweisen verfügbar sind (subtrahieren Sie **ConsumedUnits** von **ActiveUnits** ).
  
Führen Sie dann diesen Befehl aus, um detaillierte Informationen zu den Office 365-Serviceplänen anzuzeigen, die in allen Ihren Abonnements zur Verfügung stehen:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Anhand der vom Befehl zurückgegebenen Ausgabe können Sie bestimmen, welche Servicepläne Sie beim Zuweisen von Lizenzen an Benutzer deaktivieren möchten.
  
Hier ist eine unvollständige Liste der Servicepläne und der entsprechenden Office 365-Dienste.
  
|**Dienstplan**|**Beschreibung**|
|:-----|:-----|
|SWAY  <br/> |Sway  <br/> |
|INTUNE_O365  <br/> |Verwaltung mobiler Geräte in Office 365  <br/> |
|YAMMER_ENTERPRISE  <br/> |Yammer  <br/> |
|RMS_S_ENTERPRISE  <br/> |Azure-Rechteverwaltung (Rights Management, RMS)  <br/> |
|OFFICESUBSCRIPTION  <br/> |Office Professional Plus  <br/> |
|MCOSTANDARD  <br/> |Skype for Business Online  <br/> |
|SHAREPOINTWAC  <br/> |Office Online  <br/> |
|SHAREPOINTENTERPRISE  <br/> |SharePoint Online  <br/> |
|EXCHANGE_S_ENTERPRISE  <br/> |Exchange Online Plan 2  <br/> |
   
Nachdem Sie festgelegt haben, dass AccountSkuId und die Servicepläne deaktiviert werden sollen, können Sie einem einzelnen oder mehreren Benutzern Lizenzen zuweisen.
  
## <a name="for-a-single-user"></a>Für einen einzelnen Benutzer

Geben Sie für einen einzelnen Benutzer den Benutzerprinzipalnamen des Bneutzerkontos, die AccountSkuId und die Liste der zu deaktivierenden Servicepläne ein, und entfernen Sie den erläuternden Text sowie die Zeichen „\<" und „>". Führen Sie anschließend die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

Hier ein Beispiel für einen Befehlsblock für das Konto namens „belindan@contoso.com“, für contoso:ENTERPRISEPACK-Lizenz, und die zu deaktivierenden Servicepläne lauten: RMS_S_ENTERPRISE, SCHLINGERN, INTUNE_O365 und YAMMER_ENTERPRISE:
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a>Für mehrere Benutzer

Erstellen Sie zum Ausführen dieser Aufgabe eine CSV-Textdatei mit den UserPrincipalName- und UsageLocation-Feldern. Hier ein Beispiel:
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Geben Sie als Nächstes den Speicherort für die CSV-Eingabe- und CSV-Ausgabedateien, die Konto-SKU-ID und die Liste der zu deaktivierenden Servicepläne ein, und führen Sie anschließend die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Dieser PowerShell-Befehlsblock:
  
- Zeigt den Benutzerprinzipalnamen für jeden Benutzer an.
    
- Weist jedem Benutzer die angepassten Lizenzen zu.
    
- Erstellt eine CSV-Datei mit allen Benutzern, die verarbeitet wurden, und zeigt den Status ihrer Lizenz an.
    
## <a name="see-also"></a>Siehe auch

[Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)
  
[Deaktivieren des Zugriffs auf Sway mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)
  
[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)

