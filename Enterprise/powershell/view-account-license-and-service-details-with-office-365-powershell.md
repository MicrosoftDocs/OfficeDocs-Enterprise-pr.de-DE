---
title: Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Erläutert, wie Office 365 PowerShell verwenden, um die Office 365-Dienste zu ermitteln, die Benutzern zugewiesen wurden.
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell

**Zusammenfassung:** Erläutert, wie Office 365 PowerShell verwenden, um die Office 365-Dienste zu ermitteln, die Benutzern zugewiesen wurden.
  
In Office 365 lizenziert Pläne Lizenzieren von (auch gewählte SKUs oder Office 365-Pläne) gewähren des Benutzerzugriffs auf Office 365-Dienste, die für diese Pläne definiert sind. Ein Benutzer möglicherweise jedoch nicht Zugriff auf alle Dienste, die in eine Lizenz verfügbar sind, die ihnen derzeit zugewiesen ist. Office 365 PowerShell können Sie den Status von Diensten auf Benutzerkonten anzuzeigen. 

## <a name="before-you-begin"></a>Bevor Sie beginnen
<a name="RTT"> </a>

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Verwenden Sie die Befehle `Get-MsolAccountSku` und `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` , die folgende Informationen zu erhalten:
    
  - Die Lizenzierungspläne, die in Ihrer Organisation verfügbar sind.
    
  - Die Dienste, die in den einzelnen Lizenzierungsplänen verfügbar sind, und die Reihenfolge, in der sie aufgelistet sind (die Indexnummer).
    
     Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Dienste finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Verwenden Sie den Befehl `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` , um die Lizenzen zu erhalten, die ein Benutzer und die Reihenfolge, in zugewiesen sind, sie darstellen (die Indexnummer) aufgeführt.
    
- Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.
    
<a name="ShortVersion"> </a>
## <a name="the-short-version-instructions-without-explanations"></a>Die Kurzfassung (Anweisungen ohne Erläuterungen)

Wenn Sie alle Dienste von Office 365 PowerShell anzuzeigen, denen ein Benutzer zugreifen kann, verwenden Sie die folgende Syntax:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Dieses Beispiel zeigt die Dienste auf denen der Benutzer BelindaN@litwareinc.com zugreifen kann. Zeigt die Dienste, die alle Lizenzen zugeordnet sind, die ihr Konto zugewiesen sind.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Um alle lizenzierten Benutzer zu suchen, die für bestimmte Dienste aktiviert oder deaktiviert wurden, verwenden Sie die folgende Syntax:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

In diesen Beispielen werden folgende Informationen verwendet:
  
- Die Lizenz, die den Zugriff auf die Office 365-Dienste bereitstellt, die wir interessiert sind ist die erste, das alle Benutzer zugeordnet ist (die Indexnummer ist 0).
    
- Office 365-Dienste, denen wir interessiert sind Skype für Business Online und Exchange Online. Für die Lizenzen, die den Lizenzierungsplan zugeordnet sind, Skype für Business Online der 6. Dienst aufgeführt ist (die Indexnummer ist 5), und Exchange Online ist der 9. Dienst aufgeführten (die Indexnummer ist 8).
    
Dieses Beispiel gibt alle lizenzierten Benutzer, die für Skype für Business Online und Exchange Online aktiviert sind.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Dieses Beispiel gibt alle lizenzierten Benutzer, die für Skype für Business Online oder Exchange Online nicht aktiviert ist.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<a name="LongVersion"> </a>
## <a name="the-long-version-instructions-with-detailed-explanations"></a>Die Langfassung (Anweisungen mit detaillierten Erläuterungen)

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>Hier finden Sie die PowerShell für Office 365-Dienste, denen ein Benutzer Zugriff hat

Es ist offensichtlich wichtig, dass Sie wissen, welche Benutzer Office 365-Lizenzen ausgestellt wurden und welche Benutzer noch nicht. (Siehe den Artikel [lizenzierte und nicht lizenzierten Benutzer mit Office 365 PowerShell anzeigen](view-licensed-and-unlicensed-users-with-office-365-powershell.md) für Weitere Informationen). Nicht erfahren einfach dadurch, dass eine Office 365-Lizenz Sie jedoch alles über die Funktionen der Benutzer mit Office 365 tatsächlich durchführen kann. Kann er Exchange Online oder Skype für Business Online verwenden? Zugreifen dieser Benutzer kann SharePoint Online? Hat er Zugriff auf Office Professional Plus? Mit einer Lizenz bedeutet, dass der Benutzer auf diese Dienste zugreifen kann. Die für einen Benutzer verfügbaren Funktionen hängen jedoch die Dienste, die auf seinem Lizenz aktiviert wurden.
  
Wie wir ermitteln können, die Office 365-Features hat ein Benutzer Zugriff auf? Dazu müssen Sie einen Befehl wie diesem Befehl ausführen:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

In diesem Befehl sind wir das Cmdlet **Get-MsolUser** verwenden, um Informationen über das Konto BelindaN@litwareinc.com zurückzugeben. Nachdem wir diese Informationen zurückgegeben haben, wir dann pipe an das **Select-Object** -Cmdlet-Kontodaten bitten und **Select-Object** , das "den Wert der Eigenschaft **Lizenzen** Erweitert":
  
 `Select-Object -ExpandProperty Licenses`
  
Warum tun wir, die? Nun, weist standardmäßig die **Lizenzen** -Eigenschaft nur uns den Namen des lizenzierungspakets, in dem Belindas Lizenz stammt:
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

"Erweitern" die **Lizenzen** -Eigenschaft liefert uns einige zusätzliche Informationen:
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

Und klicken Sie dann durch die Erweiterung der **"Servicestatus"** -Eigenschaft erhalten wir noch weitere Informationen:
  
|Dienst Plan ***|****Beschreibung****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure-Rechteverwaltung (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
> [!NOTE]
> Sie sagen, dass das ist zu viel Schreibarbeit? Nun, wenn Ihnen ein wenig Windows PowerShell-abstrusität nichts ausmacht, können Sie Ausführen dieses verkürzte Version des Befehls stattdessen: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
Für den Fall, dass Sie wissen möchten, wir können "Erweitern" die **Lizenzen** -Eigenschaft, da **Lizenzen** eine mehrwertige Eigenschaft ist: Es wird eine einzelne Eigenschaft, die mehrere Werte gespeichert werden kann. Wenn wir einen Eigenschaftswert erweitert, dem wir einfach ein Drilldown erhalten Sie und diese zusätzlichen Werte, die standardmäßig nicht angezeigt werden auf dem Bildschirm.
  
> [!NOTE]
> Wie sollen Sie wissen, dass ein Wert eine mehrwertige Eigenschaft ist? Nun, um das herauszufinden, führen Sie einen Befehl wie den folgenden: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> das **Get-Member** -Cmdlet gibt Informationen zu dem Objekt selbst; In diesem Fall Werte Informationen über die Eigenschaft, die ein Benutzerkonto-Objekt bilden. Hier ist was **Get-Member** hat, über die **Lizenzen** -Eigenschaft sagen: > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> Wenn die Eigenschaftendefinition zu Sammlungen etwas angezeigt wird (in diesem Fall `System.Collections.Generic.List`) dann wissen Sie eine mehrwertige Eigenschaft zuständig sind. 
  
Was bedeutet alle bedeutet dies? Werfen wir zunächst noch einen Blick auf die Informationen, die vom Cmdlet **Get-MsolUser** zurückgegeben:
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

Und betrachten wir auch einen Blick auf die Tabelle, die erklärt, was diese seltsam benannten Dienstpläne wirklich darstellen:
  
|Dienst Plan ***|****Beschreibung****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure-Rechteverwaltung (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Alles klar?  `MCOSTANDARD` ist nur ein interner programming Name für Skype für Online Business während `OFFICESUSBCRIPTION` ist nur der interne programming Name für Office Professional Plus. Es ist nicht das am besten geeignete, was in der ganzen Welt, aber, solange Sie in dieser Tabelle übersichtlich bleiben Sie müssen nicht viele Probleme bei der Arbeit mit Office 365-Dienste.
  
Aber warten: mehr. Wie in den Artikel [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), wenn die **ProvisioningStatus** festgelegt ist, `Success` Dies bedeutet, dass der Dienst vollständig aktiviert wurde. beispielsweise wenn `MCOSTANDARD` auf festgelegt ist `Success` Dies bedeutet, dass der Benutzer Skype für Business Online zugreifen kann. Wenn die **ProvisioningStatus** festgelegt ist, `PendingInput` Dies bedeutet, dass Office 365 die Dienstanfrage; noch verarbeitet wird der Benutzer kann jedoch in der Regel anmelden und auf den Dienst zugreifen, während die Verarbeitung die Anforderung abgeschlossen hat. ( `YAMMER_ENTERPRISE` wird immer angezeigt als `PendingInput`, aber das ist OK:, die einen Benutzer anmeldet Yammer stoppt nicht).
  
> [!IMPORTANT]
> Benutzer können installieren und aktivieren eine Neuinstallation für Office Professional Plus beim `OFFICESUBSCRIPTION` befindet sich in der `PendingInput` Zustand.
  
Und natürlich ist ein Dienst ist festgelegt `Disabled` bedeutet, dass der betreffende Dienst nicht für den Benutzer verfügbar ist.
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>Suchen Sie nach Benutzern, die Zugriff auf bestimmte Dienste von Office 365 PowerShell

In einem separaten Artikel beschrieben haben wir gesehen, wie Sie Office 365 PowerShell verwenden können, um Benutzerzugriff auf Dienste zu deaktivieren. (Wenn Sie diese Artikel verpasst haben, finden Sie unter [Deaktivieren des Zugriffs auf Services mit Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Führt zu einer offensichtlichen Frage: Gibt es eine Möglichkeit zum bestimmen, welche *Benutzer* (d. h., mehrere Benutzer) welche Dienste aktiviert oder deaktiviert haben?
  
Es wurden möchte, dass eine Person, die stellen würde. Um diese Frage zu beantworten, sehen wir uns die Tabelle der Dienste, die wir zunächst auf den Artikel [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) für unsere einzige verfügbare Lizenzierungsplan betrachtet `litwareinc:ENTERPRISEPACK`:
  
|Dienst Plan ***|****Beschreibung****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure-Rechteverwaltung (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Sie erinnern sich möglicherweise, ist die Dienstplan nichts anderes als das interne programming Name für ein Produkt. beispielsweise `OFFICESUBSCRIPTION`, um den ersten Namen, ist der interne programming Name für Office Professional Plus. Wenn `OFFICESUBSCRIPTION` wird als `SUCCESS` auf Dienstplan eines Benutzers, klicken Sie dann das bedeutet, dass der Benutzer berechtigt ist, auf Office Professional Plus zugreifen. Wenn `EXCHANGE_S_ENTERPRISE` aufgeführt ist, als `DISABLED` bedeutet, dass der Benutzer kann nicht Exchange Online verwenden.
  
> [!IMPORTANT]
> Benutzer können installieren und aktivieren eine Neuinstallation für Office Professional Plus beim `OFFICESUBSCRIPTION` befindet sich in der `PendingInput` Zustand.
  
Jetzt ist die Zeit, in die Reihenfolge, in der die Dienste angezeigt werden, sehr wichtig ist. Windows PowerShell jeder Eintrag in der Liste eine Indexnummer zugewiesen. Der erste Eintrag 0 ist, der nächste Eintrag ist 1 usw.. Die Ergebnisse werden in der folgenden Tabelle beschrieben:
  
|Indexnummer ***|Dienst Plan ***|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
Wie Sie sehen können, `SWAY` der erste Dienst aufgelistet ist, damit es die Indexnummer 0 zugewiesen wird.
  
> [!CAUTION]
> Warum 0 und nicht 1? Das ist etwas Programmierung. In Programmiersprachen sagen Indizes Sie wie weit ein Element "vom Anfang des Arrays versetzt ist". Das erste Element *ist* der Anfang des Arrays, damit der Offset gleich 0 ist. Das zweite Element ist 1 Element vom Anfang des Arrays, damit der Offset gleich 1 ist.
  
Versuchen Sie ein Beispiel für ein. Nehmen Sie an, dass wir eine Liste aller lizenzierten Benutzer verwenden möchten, die nicht für Exchange Online aktiviert wurden. Dazu können wir den folgenden Befehl verwenden:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Zugegebenermaßen ist, die ein unverständliche professionell gestalteten wenig Befehl, wir kurz erklären, wie es funktioniert. Dies ist tatsächlich eine zweiteiligen-Befehl, und der erste Teil ist ganz einfach: wir das Cmdlet **Get-MsolUser** verwenden, um eine Auflistung aller Office 365-Benutzer zurückzugeben (lizenzierte und nicht lizenzierten):
  
```
Get-MsolUser
```

Diese Informationen wird dann an das Cmdlet **Where-Object** geleitet. **Where-Object** wird über die Benutzerkonten und sieht für diese Konten, die beide der folgenden Kriterien erfüllen:
  
- Die Eigenschaft **"islicensed"** ist gleich ( `-eq`) `True` ( `$true`). Ermöglicht, die uns zu extrahieren, die nicht lizenzierten Benutzer.
    
- Der Wert der **Lizenzen [0]. "Servicestatus" [8]. ProvisioningStatus** -Eigenschaft ist gleich ( `-eq`) `Disabled`. Der wichtige Teil dieser unhandlich Eigenschaftsname ist unsere sofortige Zwecke dies:
    
     `ServiceStatus[8]`
    
    Die `[8]` stellt die Indexnummer für Exchange Online. (Kaum zu glauben, die aus der Tabelle ein paar Minuten vor betrachten). Was passiert, wenn wir wollten, erhalten alle Benutzer, die für die Skype für Business Online aktiviert? Die Indexnummer für Skype für Business Online ist sicherlich 5, sodass wir diese Syntax verwenden:
    
     `ServiceStatus[5]`
    
    Usw., usw.
    
    Übrigen `Licenses[0]` gibt an, den Lizenzierungsplan, die wir anzeigen möchten. Da unsere Testdomäne nur eine Lizenzierungsplan hat spielt dies viel keine Rolle. Aber nehmen an, dass wir hatten einen Benutzer, der Lizenzen aus zwei unterschiedlichen lizenzierungspläne zugewiesen wurde. In diesem Fall `Licenses[0]` würde den ersten Lizenzierungsplan darstellen und `Licenses[1]` würde den zweiten Lizenzierungsplan darstellen.
    
    Verwenden Sie den folgenden Befehl, um die Lizenzen, die einem Benutzer zugewiesen sind, und die Reihenfolge zu suchen, in der sie aufgelistet sind:
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

Sehen Sie, wie das alles funktioniert? Die Indexnummer für Office Professional Plus ist 4. aus diesem Grund gibt dieser Befehl eine Liste von allen Benutzern, die nicht für Office Professional Plus aktiviert wurden:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

Und was passiert, wenn wir wollten eine Liste der Benutzer, die für Office Professional Plus *aktiviert* wurden? Nun, wenn Sie aktiviert haben und klicken Sie dann Ihre **ServiceStatus** entweder werden `PendingInput` oder `Success`; Anders ausgedrückt, wird der **"Servicestatus"** *nicht* gleich ( `-ne`) `Disabled`. Die bedeutet, dass sich alle wir nutzen unsere vorherigen Befehl, und Ersetzen Sie die `-eq` Operator für die `-ne` Operator:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

Als die Meldung Fehler auftreten, dass Code wahrscheinlich viele schöne Wettbewerben gewinnen wird nicht. Und Wahrheit gesagt, der Code kann noch mehr abrufen komplizierte. Angenommen Sie, dass wir möchten für Benutzer zu suchen, die für beide Skype für Business Online und Exchange Online aktiviert wurden:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Aber keine Sorge zu viel zu wie komplizierter, die aussehen könnte: wichtig ist, dass mit relativ wenig Aufwand Sie diese Informationen abrufen können. Erhalten kann nicht an die gleichen Informationen mithilfe von Office 365 Administrationscenter? Ja, aber, im theoretisch praktisch, No. Um die gleichen Informationen mithilfe von Office 365 Administrationscenter zu erhalten müssten Sie sehen Sie sich die Lizenzierungsinformationen für jeden Benutzer, die jeweils einen Benutzer, und klicken Sie dann manuell nachzuverfolgen, die für *X* aktiviert wurde, und wer hadn't. Funktionieren würde, aber seien wir ehrlich: Wenn Sie mehr als 10 oder 11 Benutzer vorhanden sind, werden Sie nicht möchten, dazu. Es ist zu solchen mühsamen und zeitaufwendigen.
  
Die natürlich ist, warum wir Windows PowerShell haben: Windows PowerShell schützt Sie vor aus solchen mühsamen und zeitaufwendigen Aufgaben.
  
Es folgt ein Beispiel eines Befehls zum Anzeigen von Dienstinformationen für eine angegebene Gruppe von Diensten durch ihre Lizenzen und ServiceStatus Indizes für ein Abonnement von Office 365 E5 bezeichnet:
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

Dieser Befehl erstellt eine CSV-Datei, die alle Ihre Benutzer und deren Dienst-Status für einen angegebenen Satz von Diensten (Teams, Yammer, AD RMS, OfficePro, Skype, SharePoint und Exchange) anzeigt.

>[!Note]
>Sie können in einem Abonnement aus die Liste der Dienste Abrufen der `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` Befehl. In der Ausgabe starten Sie die Nummerierung der mit 0 indiziert. Mit dem vorstehende Befehl ist nur ein Beispiel. Indexnummern für Dienste können mit der Zeit ändern.
>

  
<a name="SeeAlso"> </a>
## <a name="see-also"></a>Siehe auch

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten mit Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Neu bei Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]