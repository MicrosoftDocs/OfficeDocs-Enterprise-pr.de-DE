---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
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
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern."
ms.openlocfilehash: 88628a78179605c734cd1d3f114a8a1dcb712376
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:**  Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern.
  
Lizenzieren von Benutzerkonten in Office 365 ist wichtig, da Benutzer keine Office 365-Dienste verwendet werden, bis ihr Konto lizenziert wurden. Office 365 PowerShell können Sie nicht lizenzierten Konten, insbesondere mehrere Konten effizient Lizenzen zuweisen. 

## <a name="before-you-begin"></a>Bevor Sie beginnen:
<a name="RTT"> </a>

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Verwenden Sie das Cmdlet " **Get-MsolAccountSku** ", um die verfügbaren lizenzierungspläne und die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen in Ihrer Organisation anzuzeigen. Die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen ist **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Diensten finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Führen Sie den Befehl aus, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen,`Get-MsolUser -All -UnlicensedUsersOnly`
    
- Sie können nur für Benutzerkonten Lizenzen zuweisen, die die **usagelocation-Wert angegeben** -Eigenschaft auf einen gültigen ISO 3166-1 Alpha-2-Ländercode festgelegt haben. Beispielsweise uns für die USA und FR für Frankreich. Einige Office 365-Dienste sind in bestimmten Ländern nicht verfügbar. Weitere Informationen finden Sie unter [About Lizenz Einschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Führen Sie den Befehl aus, um Konten suchen, die nicht über ein **usagelocation-Wert angegeben** Wert verfügen, `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Um den **usagelocation-Wert angegeben** Wert für ein Konto festzulegen, verwenden Sie die Syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Beispielsweise `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Wenn Sie das Cmdlet **Get-MsolUser** ohne Verwenden der `-All` -Parameter, die nur die ersten 500 Benutzerkonten zurückgegeben werden.
    
## <a name="the-short-version-instructions-without-explanations"></a>Die Kurzfassung (Anweisungen ohne Erläuterungen)
<a name="ShortVersion"> </a>

In diesem Abschnitt werden die Verfahren ohne ausführliche Erläuterung. Wenn Sie Fragen haben oder Weitere Informationen wünschen, können Sie den Rest des Themas lesen.
  
Wenn Sie einem Benutzer eine Lizenz zuweisen möchten, verwenden Sie die folgende Syntax in Office 365 PowerShell:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

In diesem Beispiel wird eine Lizenz aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan (Office 365 Enterprise E3) für den nicht lizenzierten Benutzer `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Wenn Sie mehreren nicht lizenzierten Benutzern eine Lizenz zuweisen möchten, verwenden Sie die folgende Syntax:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Notizen**
  
- Sie können einem Benutzer nicht mehrere Lizenzen aus dem gleichen Lizenzierungsplan zuweisen.
    
- Wenn Sie nicht über genügend verfügbaren Lizenzen verfügen, werden die Lizenzen für Benutzer in der Reihenfolge zugewiesen, die sie vom Cmdlet **Get-MsolUser** zurückgegeben werden, bis die verfügbaren Lizenzen Neige zur.
    
In diesem Beispiel wird die Lizenzen aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan (Office 365 Enterprise E3) für alle nicht lizenzierten Benutzer.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

In diesem Beispiel werden dieselben Lizenzen den nicht lizenzierten Benutzern in der Vertriebsabteilung in den USA zugewiesen.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Die Langfassung (Anweisungen mit detaillierten Erläuterungen)
<a name="LongVersion"> </a>

Wie im Artikel [lizenzierte und nicht lizenzierten Benutzer mit Office 365 PowerShell anzeigen](view-licensed-and-unlicensed-users-with-office-365-powershell.md)bereits erwähnt, ist es möglich, dass Benutzer über gültige Office 365-Benutzerkonten verfügen, aber wer haben keine Office 365-Lizenz ausgestellt. Das bedeutet, dass gültiges Konto oder kein gültiges Konto, die Benutzer nicht bei Office 365 anmelden können. Und wenn Sie sich nicht anmelden können, Sie können nicht nutzen aller Office 365-Dienste.
  
Im genannten Artikel wird auch darauf hingewiesen, dass mit dem folgenden Befehl eine Liste nicht lizenzierter Benutzerkonten zurückgegeben werden kann:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Dieser Befehl gibt Informationen über alle Benutzer, die derzeit nicht für Office 365 lizenziert sind:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

Wie Sie sehen können, haben wir einen nicht lizenzierten Benutzer: Belinda Newman. Wie gehen wir zum Zuweisen von Belinda einer Office 365-Lizenzvertrags?
  
Zunächst einmal werden wir das Cmdlet " **Get-MsolAccountSku** " im Artikel [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)beschriebene ausführen:
  
```
Get-MsolAccountSku
```

Dieser Befehl gibt Daten wie diese zurück:
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

Warum ausführen wir **Get-MsolAccountSku** ? ("Sku", für den Fall, dass Sie wissen möchten, ist kurz für "SKU." Für unsere Zwecke, die gerade Business sprechen ist-für "Produkt".) Es gibt zwei Gründe, warum es **Get-MsolAccountSku**ausgeführt wurde. Zunächst müssen wir stellen Sie sicher, dass wir tatsächlich eine Lizenz zuweisen Belinda haben. Haben wir keinerlei Lizenzen, die wir ihr zuweisen können? So bestimmen Sie, dass wir nehmen Sie den Wert der **ActiveUnits** -Eigenschaft (25) und die Werte der **WarningUnits** (0) und Eigenschaften **ConsumedUnits** (24 subtrahiert):
  
 `25 - 0 - 24 = 1`
  
Die **ActiveUnits** -Eigenschaft gibt an, wie viele Lizenzen wir erworben haben, und der kombinierte Wert **WarningUnits** und **ConsumedUnits** gibt an, wie viele Lizenzen gerade verwendet werden. Wenn wir die Anzahl der Lizenzen, die bereits subtrahiert für gesprochen, von der Anzahl der Lizenzen, die wir erworben haben, wissen wir, wie viele Lizenzen noch verfügbar sind. Wie Glück sie besitzen, haben wir eine Lizenz für den Vertrieb verfügbar:
  
 `25 - 0 - 24 = 1`
  
Zweitens, um Belinda eine neue Lizenz zuweisen wir wissen den Namen des unsere Lizenzierungsplan müssen (d. h., müssen wir die **AccountSkuId** wissen). In diesem Fall ist, die einfach: Wir haben nur eine einzelne Lizenzierungsplan ( `litwareinc:ENTERPRISEPACK`). Beachten Sie jedoch, dass es für eine Organisation mehrere lizenzierungspläne möglich ist. In diesem Fall würde **Get-MsolAccountSku** zwei unterschiedliche **AccountSkuIds**zurückgeben, und müssen Sie den richtigen Lizenzierungsplan wählen Sie bei der Zuweisung von Lizenzen. Jetzt werden jedoch wir einfachsten Fall festgelegt, und davon ausgegangen, dass wir nur einen Lizenzierungsplan haben.
  
*Klicken Sie dann so wie wir Belinda Newman eine neue Lizenz zuweisen?* So:
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Ist Sie Schritte: Rufen Sie einfach das **Set-MsolUserLicense** -Cmdlet, um sicherzustellen, dass Sie den Parameter _UserPrincipalName_ für den Benutzer und den richtigen Lizenzierungsplan angeben.
  
Wenn **Set-MsolUserLicense** abgeschlossen ist, wird etwa Folgendes sehen Sie auf dem Bildschirm angezeigt:
  
 `PS C:\\windows\\system32>`
  
Es wird nicht mit anderen Worten, aussehen wie etwas geschehen ist. Zum bestätigen, dass der Benutzer eine Lizenz zugewiesen wurde, führen Sie einen Befehl ähnlich dem folgenden:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

Wenn alles erwartungsgemäß funktioniert, sollten Sie sehen, dass die Eigenschaft von Belindas "islicensed" nun auf True festgelegt ist:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! Sicherheitshinweis] gute Frage: Was passiert, wenn ein Fehler aufgetreten und haben versucht, einem Benutzer eine Lizenz zuweisen, die bereits über eine Lizenz verfügt? Erhalten Sie zwei Lizenzen zu einem einzelnen Benutzer erteilen? > Die schnelle Antwort? No; Office 365 wird nicht mehr als eine Lizenz für den gleichen Benutzer zuweisen kann. (Das ist sicherlich mehr als eine Lizenz aus den gleichen Lizenzierungsplan,.) Wenn Sie versuchen, das Ihre Befehl schlägt fehl, wobei die folgende Fehlermeldung angezeigt: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> zugegebenermaßen, wird diese Fehlermeldung geringfügig irreführende: die Lizenz nicht wirklich ungültig ist, wird nur zu einem Benutzer zugewiesen wird, die bereits *verfügt über* eine Lizenz. Aber reserviert, Fehlermeldung wichtig ist, dass ein Benutzer mit mehreren Lizenzen landen wird nicht.
  
Wie Sie gerade gesehen haben, ist es sehr einfach zu verwendenden Office 365 PowerShell einen einzelnen Benutzer eine Lizenz zugewiesen. Führt zu einer offensichtlichen Frage: wäre es nicht genauso einfach, vielleicht sogar noch einfacher, um das Office 365 Administrationscenter verwenden, um einen einzelnen Benutzer eine Lizenz zugewiesen? Nun, vielleicht; Dies hängt, teilweise gibt an, ob Sie besser damit vertraut, mithilfe von Windows PowerShell oder komfortabler im Office 365 Admin Center sind. In der Windows PowerShell das beste, ist jedoch, wenn Sie mehrere Lizenzen für mehrere Benutzer zuweisen möchten. Mit diesem Befehl weist beispielsweise eine Office 365-Lizenz zu einer der Benutzer, die nicht bereits über eine Lizenz verfügen:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Im vorstehenden Befehl verwenden wir **Get-MsolUser** und der _UnlicensedUsersOnly_ -Parameter, um eine Auflistung aller nicht lizenzierter Benutzerkonten zurückzugeben. Wir übergeben dieser Auflistung dann an das Cmdlet **Set-MsolUserLicense** ; **Set-MsolUserLicense** weist wiederum eine Lizenz (übernommen aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan) für jeden Benutzer in der Auflistung.
  
AH, aber was passiert, wenn haben Sie 5 nicht lizenzierten Benutzer jedoch nur eine Lizenz verfügbar? In diesem Fall erhalten **Set-MsolUserLicense** verfügbare Lizenz für dem ersten Benutzer, die von **Get-MsolUser**zurückgegeben. **Set-MsolUserLicense** wird dann verlässliche versucht, die anderen vier Benutzer eine Lizenz zuweisen, aber alle vier dieser Versuche fehl und die folgende Fehlermeldung angezeigt:
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
Set-MsolUserLicense wird nicht mit anderen Worten, fehl. Stattdessen weisen sie, wie viele Lizenzen wie möglich. Nur dann fehl.
  
Versuchen Sie ein weiteres Beispiel an. Vielleicht möchten Sie alle Benutzer in der Abteilung Sales eine Lizenz zuweisen. Kein Problem:
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Oder wenn Sie wirklich raffiniert sein und Fehlermeldungen sowie die Verarbeitungslast auf dem Rechner auf einem Minimum halten möchten, weisen Sie einfach den nicht lizenzierten Benutzern aus der Sales-Abteilung eine Lizenz zu:
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Nachdem alle besteht keine Points Lizenzbenutzer, die bereits über eine Lizenz verfügen möchten. Wie bereits erwähnt, ist nicht möglich.
  
Hier ist ein weiteres Beispiel. Vielleicht möchten Sie alle Benutzer der USA lizenzieren, die derzeit nicht über ein Office 365-Lizenz verfügen. In diesem Fall:
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Und so weiter und so weiter.
  
> [!NOTE]
> Wie lange dauert es, einen Befehl auszuführen, der für alle nicht lizenzierten Benutzer sagen, Lizenzen ausgibt? Das ist schwierig zu sagen: das hängt alles von der Anzahl der Benutzer die Geschwindigkeit der Verbindung zum Netzwerk muss. Wenn Sie ein paar Hundert Benutzern-Lizenz verfügen, dadurch Sie nach vernünftigem Ermessen schnell gelangen wird (d. h., sollte nicht dauert länger als ein oder zwei Minuten). Wenn Sie haben werden 10.000 Benutzer um die Lizenz zu offensichtlich etwas länger dauern. Aber nicht in der Nähe so lange dauert 10.000 Benutzern Lizenzen zuweisen, indem Sie im Office 365 Admin Center. 
  
Als wir zu diesem Thema sind, sollten Sie sich für Achten Sie beim Zuweisen von Lizenzen Sie müssen: Wenn ein Benutzer keinen Wert für die Eigenschaft **usagelocation-Wert angegeben** konfiguriert nicht möglich, die diesem Benutzer eine Office 365-Lizenz zuweisen. Stattdessen erhalten eine Fehlermeldung wie die folgende Sie:
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
Etwas Kreisverkehrs verwenden weist diese Fehlermeldung uns, dass der betreffende Benutzer ein **usagelocation-Wert angegeben**nicht zugewiesen wurde. Wie Sie vielleicht, ist die **usagelocation-Wert angegeben** -Eigenschaft (die gibt an, die Region oder jedes Land, in dem der Benutzer in der Regel Office 365 verwendet) äußerst wichtig. Warum? Dies liegt daran die für einen Benutzer verfügbaren Dienste nicht nur lizenzierungspakets abhängen, das Sie aber auch auf, in dem der Benutzer befindet sich erworben haben: aufgrund von lokalen Richtlinien und Vorschriften, einige Dienste möglicherweise nicht für einige Benutzer verfügbar. Wenn ein Benutzer ein **usagelocation-Wert angegeben**hat, kann Office 365 nicht wissen, welche Dienste rechtskräftig für diesen Benutzer verfügbar gemacht werden können. Daher Office 365 kann nicht bieten keine Dienste, die diesem Benutzer mindestens nicht, bis der **usagelocation-Wert angegeben** angegeben wurde.
  
> [!NOTE]
> Wenn Sie ein Benutzerkonto konfigurieren wissen Sie sofort Wenn Lizenz Einschränkungen den angegebenen Teil der ganzen Welt zugeordnet sind. Beispielsweise, wenn Sie die **usagelocation-Wert angegeben** für einen lizenzierten Benutzer Iran ändern ( `IR`), der Befehl schlägt fehl, mit dieser Fehlermeldung: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> Dies liegt daran Office 365 nicht für Benutzer im Iran derzeit verfügbar ist. Weitere Informationen finden Sie unter [About Lizenz Einschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730). Office 365 wird zum, die zwei Buchstaben Ländercodes erzeugt, von der International Organization for Standardization (ISO) verwendet. Diese Codes finden Sie auf der [ISO-Website](https://go.microsoft.com/fwlink/p/?LinkId=84073). 
  
Wenn Sie überprüfen möchten besteht aus ein bestimmten Benutzer ein **usagelocation-Wert angegeben** , können Sie einen Befehl wie den folgenden verwenden:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

Alternativ können Sie eine Liste aller Benutzer zurückgegeben, die nicht mit dem folgenden Befehl ein **usagelocation-Wert angegeben** haben:
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> Wenn Sie einer Lizenz für einen Benutzer diesen Benutzer zuweisen, wird standardmäßig Zugriff auf alle Office 365-Dienste erhalten, die über Zugriff auf Ihre Organisation verfügt. Angenommen, wenn Sie Lizenzen für Office 365 Enterprise E3 erworben haben, wird Ihre neu lizenzierten Benutzer automatisch Zugriff auf Dienste wie Exchange Online, Skype für Business Online und SharePoint Online erteilt werden. Wenn Sie ein Benutzer Zugriff auf diese Dienste beschränken möchten (beispielsweise sollten Sie einen Benutzer den Zugriff auf SharePoint Online, wird jedoch *nicht* zu Exchange Online und Skype für Business Online) dann finden Sie im Artikel [Disable-Zugriff auf Dienste mit Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md). 
  
## <a name="new-to-office-365"></a>Neu bei Office 365?

||
|:-----|
|![Das kurze Symbol für LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **neu zu Office 365?**         Entdecken Sie kostenlose video Kurse für [Office 365-Administratoren und IT-Experten](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), bereitgestellt von LinkedIn Learning. |
   
## <a name="see-also"></a>Weitere Artikel
<a name="SeeAlso"> </a>

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten mit Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

