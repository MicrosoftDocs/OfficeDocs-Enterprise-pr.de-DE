---
title: Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Verwenden von Office 365 PowerShell zum Hinzufügen oder Entfernen des Zugriffs auf Office 365-Diensten für Benutzer in Ihrer Organisation erläutert."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell

**Zusammenfassung:** Verwenden von Office 365 PowerShell zum Hinzufügen oder Entfernen des Zugriffs auf Office 365-Diensten für Benutzer in Ihrer Organisation erläutert.
  
Wenn ein Office 365-Konto eine Lizenz von einem Lizenzierungsplan zugeordnet ist, sind Office 365-Dienste für den Benutzer über diese Lizenz verfügbar. Sie können jedoch die Office 365-Dienste steuern, die der Benutzer zugreifen kann. Obwohl die Lizenz Zugriff auf SharePoint Online ermöglicht, können Sie beispielsweise Zugriff darauf deaktivieren. Office 365 PowerShell können Sie tatsächlich den Zugriff auf eine beliebige Anzahl von Diensten für deaktivieren:
- ein einzelnes Konto
    
- eine Gruppe von Konten
    
- Alle Konten in Ihrer Organisation.
    
 **Inhalt:** [Die Kurzversion (Anweisungen ohne Erklärungen)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [Die langes Format (Anweisungen mit detaillierten erläuterungen)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Siehe auch](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>Bevor Sie beginnen
<a name="RTT"> </a>

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Verwenden Sie das Cmdlet " **Get-MsolAccountSku** ", um anzuzeigen, Ihrer verfügbaren lizenzierungspläne und die Office 365-Dienste, die in dieser Pläne zur Verfügung stehen. Weitere Informationen finden Sie unter[Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Anzeigen der vor und nach der Ergebnisse der Verfahren in diesem Thema finden Sie unter [Anzeigen von Kontodetails Lizenz und den Dienst mit Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Ein PowerShell-Skript ist verfügbar, die die in diesem Thema beschriebenen Verfahren automatisiert. Insbesondere ermöglicht das Skript anzeigen und Deaktivieren von Diensten in Office 365-Organisation, einschließlich Schlingern. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Schlingern mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.
    
## <a name="the-short-version-instructions-without-explanations"></a>Die Kurzfassung (Anweisungen ohne Erläuterungen)
<a name="ShortVersion"> </a>

In diesem Abschnitt werden die Verfahren kurz und bündig erläutert. Wenn Sie Fragen haben oder weitere Informationen benötigen, können Sie den Rest des Themas lesen.
  
Um Benutzer aus einer einzelnen Lizenzierungsplan Office 365-Dienste zu deaktivieren, führen Sie die folgenden Schritte aus:
  
1. Identifizieren Sie die unerwünschten Dienste in den Lizenzierungsplan mithilfe der folgenden Syntax:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    Dieses Beispiel erstellt ein **LicenseOptions** -Objekt, das in den Lizenzierungsplan mit dem Namen der Office Online und SharePoint Online-Dienste deaktiviert `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Verwenden Sie das **LicenseOptions** -Objekt aus Schritt 1 auf einen oder mehrere Benutzer.
    
  - Wenn Sie ein neues Konto zu erstellen möchten, für das die Dienste deaktiviert sind, verwenden Sie die folgende Syntax:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    In diesem Beispiel wird ein neues Konto für Allie Bellew erstellt, das die Lizenz zuweist und die in Schritt 1 beschriebenen Dienste deaktiviert.
    
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

  - Um die Dienste beschrieben in Schritt 1 für alle vorhandenen lizenzierten Benutzer zu deaktivieren, geben Sie den Namen Ihres Office 365 Plans aus der Anzeige des Cmdlets **Get-MsolAccountSku** (beispielsweise **litwareinc: enterprisepack** ), und führen Sie dann die folgenden Befehle aus:
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - Verwenden Sie eine der folgenden Methoden, um die Dienste für eine Gruppe von vorhandenen Benutzern zu deaktivieren und die Benutzer zu identifizieren:
    
  - **Filtern die anhand eines vorhandenen Attributs Konto Konten** Verwenden Sie dazu die folgende Syntax:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    In diesem Beispiel werden die Dienste für Benutzer in der Vertriebsabteilung in den Vereinigten Staaten deaktiviert.
    
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
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Um Office 365-Diensten für Benutzer zu deaktivieren, während Sie sie an einer Lizenzierungsplan zuweisen, finden Sie unter [Zugriff auf Dienste beim Zuweisen von Benutzerlizenzen deaktivieren](disable-access-to-services-while-assigning-user-licenses.md).
  
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
    
  -  _<UndesirableService>_In diesem Beispiel werden wir Office Online und SharePoint Online verwenden.
    
  -  _<Account>_In diesem Beispiel verwenden wir belindan@litwareinc.com.
    
    Das angepasste Skript sieht wie folgt aus:
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. Speichern Sie das Skript als `RemoveO365Services.ps1` an einem Speicherort, die Sie leicht zu finden. In diesem Beispiel werden wir speichern Sie die Datei in " `C:\\O365 Scripts`".
    
4. Führen Sie das Skript in Office 365 PowerShell mithilfe des folgenden Befehls.
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Um die Effekte eines dieser Verfahren rückgängig zu machen (d. h., die deaktivierten Dienste erneut aktivieren), führen Sie das Verfahren erneut aus, aber verwenden Sie den Wert `$null` für den Parameter _DisabledPlans_ .
  
[Zurück zum Seitenanfang](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>Die Langfassung (Anweisungen mit detaillierten Erläuterungen)
<a name="LongVersion"> </a>

Alle Dienste werden standardmäßig aktiviert, wenn Sie eine Lizenz mithilfe von PowerShell für Office 365 registrieren. Häufig ist eine gute Sache: Dies bedeutet, dass Sie schnell und einfach Lizenzen Benutzern zuweisen können ohne anzugeben, dass jeder Dienst dabei aktiviert werden.
  
Andererseits gilt jedoch es auch, dass Sie möglicherweise die verfügbaren Dienste bestimmte Benutzer beschränken möchten. beispielsweise vielleicht sollten einige Benutzer haben Zugriff auf Office Professional Plus, Skype für Business Online und Exchange Online, aber diese dieselben Benutzer keinen Zugriff auf SharePoint Online oder auf Office Online haben. Kann Konten auf diese Weise werden eingeschränkt? Wie sich herausstellt, können Sie. Um besser erklären, wie dies funktioniert, werfen wir einen zweistufiger Ansatz zum Bekämpfung dieses Problems:
  
1. Weisen Sie dem Benutzer eine Office 365-Lizenz, die automatisch alle Dienste aktiviert.
    
2. Führen Sie dann eine Reihe von Office 365 PowerShell-Befehle, die bestimmte Dienste für diesen Benutzer deaktivieren.
    
Wir haben bereits beachtet Schritt 1: unsere Benutzer (Belinda Newman) hat eine Office 365-Lizenz, die ihr Zugriff auf die Office 365-Dienste bereitstellt. Wir möchten jedoch Belindas Konto ändern, sodass er Zugriff auf SharePoint Online nicht ( `SHAREPOINTENTERPRISE`) oder auf Office Online ( `SHAREPOINTWAC`). Aber wie wir sollen dazu?
  
Hier ist wie. Zunächst werden wir das Cmdlet " **New-MsolLicenseOptions** " verwenden, um ein **LicenseOption** -Objekt erstellen, enthält die Dienste, die wir möchten deaktiviert. Im Fall Belindas wir deaktivieren möchten `SHAREPOINTENTERPRISE` und `SHAREPOINTWAC`, sodass wir diesen Befehl verwenden:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

Sehen Sie, wie das funktioniert? Sie geben den Lizenzierungsplan ( `litwareinc:ENTERPRISEPACK`) und dann jeden der Dienste, die gewünschte deaktiviert, durch ein Komma.
  
> [!NOTE]
> Stellen Sie sicher, dass Sie Ihre neue **LicenseOption** -Objekt in einer Variablen zu speichern. Im vorstehenden Beispiel wir verwendet `$x`, obwohl Sie eine beliebige gültige Variablennamen Windows PowerShell verwenden können. 
  
Nun können wir den folgenden Befehl verwenden, um Belindas Zugriff auf die zwei Dienste zu deaktivieren:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Nichts zu ausgeklügelte hier entweder: wir gerade das Cmdlet " **Set-MsolUserLicense** " aufrufen und nehmen Sie den Parameter _LicenseOptions_ , zusammen mit der Variable ( `$x`), enthält die Pläne wir deaktivieren möchten. Und was wir finden Sie unter jetzt Wenn wir einen Blick auf Belindas Lizenzinformationen mithilfe des Befehls verwenden: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Wir sehen dies:
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

Ziemlich Cool, nicht wahr? Und natürlich wir konnte führen Sie dasselbe auf mehrere Benutzer würden wir an. Diese Befehle deaktivieren beispielsweise dieselben zwei Dienste für alle unsere lizenzierten Benutzer. Geben Sie den Namen Ihres Office 365 Plans aus der Anzeige des Cmdlets **Get-MsolAccountSku** (beispielsweise **litwareinc: enterprisepack** ), und führen Sie diese.
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

Beachten Sie, dass Belinda immer noch eine gültige Office 365-Lizenz verfügt beibehalten; Es handelt es sich, nachdem sie Zugriff auf weniger Services hat. Bevor wir zwei Dienste deaktiviert, konnte Belinda zugreifen Newsfeeds, OneDrive und SharePoint Online Websites:
  
![Benutzer mit SharePoint-Zugriff.](images/o365_powershell_with_sharepoint.png)
  
Jetzt stehen ihr diese Optionen nicht mehr zur Verfügung:
  
![Benutzer ohne SharePoint-Zugriff.](images/o365_powershell_without_sharepoint.png)
  
Was genau das ist, was wir wollten.
  
Und was passiert, wenn wir unsere Meinung später ändern: ist es möglich, diese Dienste wieder aktivieren? Es ist absolut. Um alle Dienste für einen Benutzer wieder zu aktivieren, verwenden Sie diesen Befehl nur das folgenden **LicenseOption** -Objekt erstellt:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Welche dieser Befehl? Beginnen Sie mit der Windows PowerShell-Konstante `$null` bedeutet "nothing". (Oder in etwas mehr technische Sprache, bedeutet einen "null-Wert.") Wie Sie sich erinnern, wenn wir verwenden Sie das Cmdlet " **New-MsolLicenseOptions** " Wir haben, um die Dienste anzugeben, deaktiviert werden soll. In diesem Fall soll keiner Dienste deaktiviert werden. Die möglicherweise führen Sie glauben, dass wir einen Befehl wie den folgenden Befehl verwenden könnten, in dem wir keinen Wert für den _DisabledPlans_ -Parameter angeben:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

Jedoch ist nicht möglich. Stattdessen wird eine Fehlermeldung generiert:
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
Zum Glück für uns, Festlegen des Werts des Parameters auf `$null` funktioniert:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Das bedeutet ganz einfach, dass, wenn wir das Cmdlet " **Set-MsolUserLicense** " ausführen, wir **Set-MsolUserLicense** angeben, dass für Belinda keine Dienste deaktiviert werden sollen:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Und wenn keiner der Dienste deaktiviert ist, heißt das logischerweise, dass alle Dienste aktiviert sind.
  
Nun, Sie verstehen, wie All dies funktioniert, lassen Sie uns zeigen, wie Sie eine Lizenz ausstellen können und Disable-Dienste und alle mit dem gleichen Befehl angegeben. Das klingt ziemlich beeindruckende, aber, um ehrlich zu sein, es ist wirklich nicht darauf: Fügen Sie die _AddLicenses_ und die _LicenseOptions_ -Parameter im gleichen Befehl. Anders ausgedrückt, erstellen Sie zuerst das **LicenseOption** -Objekt:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

Und klicken Sie dann wie bereits erwähnt, Sie verwenden die _AddLicenses_ und die _LicenseOptions_ -Parameter in Ihrem Befehl:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

Dass der Befehl Belinda Newman eine neue Lizenz, aber in welche Skype eine Lizenz für Business Online ausstellt ( `SHAREPOINTWAC`) und SharePoint Online ( `SHAREPOINTENTERPRISE`) sind beide deaktiviert.
  
[Zurück zum Seitenanfang](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>Neu bei Office 365?
<a name="LongVersion"> </a>

||
|:-----|
|![Das kurze Symbol für LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **neu zu Office 365?**         Entdecken Sie kostenlose video Kurse für **Office 365-Administratoren und IT-Experten**, bereitgestellt von LinkedIn Learning. |
   
## <a name="see-also"></a>See also
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
    
[Zurück zum Seitenanfang](disable-access-to-services-with-office-365-powershell.md#RTT)
  

