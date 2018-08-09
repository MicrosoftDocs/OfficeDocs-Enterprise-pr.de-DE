---
title: Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/08/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Erläutert, wie Office 365 PowerShell verwenden, um Zugriff auf Office 365-Diensten für Benutzer in Ihrer Organisation zu deaktivieren.
ms.openlocfilehash: 44b0ed84bb8fd098412c69258834194b2b1eeb2f
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "22196822"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell

**Zusammenfassung:** Erläutert, wie Office 365 PowerShell verwenden, um Zugriff auf Office 365-Diensten für Benutzer in Ihrer Organisation zu deaktivieren.
  
Wenn ein Office 365-Konto eine Lizenz von einem Lizenzierungsplan zugeordnet ist, sind Office 365-Dienste für den Benutzer über diese Lizenz verfügbar. Sie können jedoch die Office 365-Dienste steuern, die der Benutzer zugreifen kann. Obwohl die Lizenz Zugriff auf SharePoint Online ermöglicht, können Sie beispielsweise Zugriff darauf deaktivieren. Office 365 PowerShell können Sie tatsächlich den Zugriff auf eine beliebige Anzahl von Diensten für deaktivieren:

- ein einzelnes Konto
    
- eine Gruppe von Konten
    
- Alle Konten in Ihrer Organisation.
    
## <a name="before-you-begin"></a>Bevor Sie beginnen
<a name="RTT"> </a>

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Verwenden Sie das Cmdlet " **Get-MsolAccountSku** ", um anzuzeigen, Ihrer verfügbaren lizenzierungspläne und die Office 365-Dienste, die in dieser Pläne zur Verfügung stehen. Weitere Informationen finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Anzeigen der vor und nach der Ergebnisse der Verfahren in diesem Thema finden Sie unter [Anzeigen von Kontodetails Lizenz und den Dienst mit Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Ein PowerShell-Skript ist verfügbar, die die in diesem Thema beschriebenen Verfahren automatisiert. Insbesondere ermöglicht das Skript anzeigen und Deaktivieren von Diensten in Office 365-Organisation, einschließlich Schlingern. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Schlingern mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Wenn Sie das Cmdlet **Get-MsolUser** ohne mit dem _Alle_ Parameter verwenden, werden nur die ersten 500 Benutzerkonten zurückgegeben.
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a>Planen von bestimmte Office 365-Diensten für bestimmte Benutzer für die einzelnen Lizenzierung
  
Um eine bestimmte Gruppe von Office 365-Diensten für Benutzer aus einer einzelnen Lizenzierungsplan deaktivieren möchten, führen Sie die folgenden Schritte aus:
  
1. Identifizieren Sie die unerwünschten Dienste in den Lizenzierungsplan mithilfe der folgenden Syntax:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    Das folgende Beispiel erstellt ein **LicenseOptions** -Objekt, das in den Lizenzierungsplan mit dem Namen der Office Online und SharePoint Online-Dienste deaktiviert `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Verwenden Sie das **LicenseOptions**-Objekt aus Schritt 1 für einen oder mehrere Benutzer.
    
  - Wenn Sie ein neues Konto zu erstellen möchten, für das die Dienste deaktiviert sind, verwenden Sie die folgende Syntax:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    Das folgende Beispiel erstellt ein neues Konto für Allie Bellew, die die Lizenz zugewiesen und deaktiviert die Dienste, die in Schritt 1 beschrieben.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    Weitere Informationen zum Erstellen von Benutzerkonten in Office 365 PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Verwenden Sie die folgende Syntax, um die Dienste für einen vorhandenen lizenzierten Benutzer zu deaktivieren:
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    In diesem Beispiel werden die Dienste für den Benutzer „BelindaN@litwareinc.com“ deaktiviert.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Um die Dienste beschrieben in Schritt 1 für alle vorhandenen lizenzierten Benutzer zu deaktivieren, geben Sie den Namen Ihres Office 365 Plans aus der Anzeige des Cmdlets **Get-MsolAccountSku** (beispielsweise **litwareinc: enterprisepack**), und führen Sie dann die folgenden Befehle aus:
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - Verwenden Sie eine der folgenden Methoden, um die Dienste für eine Gruppe von vorhandenen Benutzern zu deaktivieren und die Benutzer zu identifizieren:
    
  - **Filtern die anhand eines vorhandenen Attributs Konto Konten** Verwenden Sie dazu die folgende Syntax:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    Das folgende Beispiel deaktiviert die Dienste für Benutzer in der Abteilung "Sales" in den USA.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Verwenden einer Liste spezieller Konten** Führen Sie dazu die folgenden Schritte aus:
    
1. Erstellen Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    In diesem Beispiel wird die Textdatei C:\\eigene\\Accounts.txt.
    
2. Führen Sie den folgenden Befehl aus:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Um Office 365-Diensten für Benutzer zu deaktivieren, während Sie sie an einer Lizenzierungsplan zuweisen, finden Sie unter [Zugriff auf Dienste beim Zuweisen von Benutzerlizenzen deaktivieren](disable-access-to-services-while-assigning-user-licenses.md).
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a>Bestimmten Office 365-Diensten für Benutzer aus allen lizenzierungspläne
  
Führen Sie die folgenden Schritte, um Office 365-Diensten für Benutzer in allen verfügbaren lizenzierungspläne zu deaktivieren:
  
1. Kopieren Sie dieses Skript, und fügen Sie es in Editor ein.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. Passen Sie die folgenden Werte für Ihre Umgebung an:
    
  -  _<UndesirableService>_ In diesem Beispiel werden wir Office Online und SharePoint Online verwenden.
    
  -  _<Account>_ In diesem Beispiel verwenden wir belindan@litwareinc.com.
    
    Das angepasste Skript sieht wie folgt aus:
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. Speichern Sie das Skript als `RemoveO365Services.ps1` an einem Speicherort, die Sie leicht zu finden. In diesem Beispiel werden wir speichern Sie die Datei in `C:\\O365 Scripts`.
    
4. Führen Sie das Skript in Office 365 PowerShell mithilfe des folgenden Befehls.
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Um die Effekte eines dieser Verfahren rückgängig zu machen (d. h., die deaktivierten Dienste erneut aktivieren), führen Sie das Verfahren erneut aus, aber verwenden Sie den Wert `$null` für den Parameter _DisabledPlans_ .
  
[Nach oben](disable-access-to-services-with-office-365-powershell.md#RTT)



## <a name="new-to-office-365"></a>Neu bei Office 365?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Siehe auch
<a name="SeeAlso"> </a>

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten mit Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Neue MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

