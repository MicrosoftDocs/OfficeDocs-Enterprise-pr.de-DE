---
title: Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell, um benutzerspezifische Kommunikationseinstellungen mit Skype for Business Online-Richtlinien zuzuweisen.'
ms.openlocfilehash: 91916b41ba420a204ecabb27eea2e451a91f6f25
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell pro Benutzer für die Netzwerkkommunikation mit Skype für Business Online Richtlinien zuweisen.
  
Die Verwendung von Office 365 PowerShell ist eine effiziente Methode, um benutzerspezifische Kommunikationseinstellungen mit Skype for Business Online-Richtlinien zuzuweisen.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen:

Bereiten Sie sich mithilfe dieser Anweisungen auf die Ausführung der Befehle vor (überspringen Sie die Schritte, die Sie bereits ausgeführt haben):
  
1. Laden Sie das [Connector-Modul für Skype for Business Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366) herunter, und installieren Sie es.
    
2. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus: 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
Wenn Sie dazu aufgefordert werden, geben Sie den Namen und das Kennwort Ihres Skype for Business Online-Administratorkontos ein.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Aktualisieren externer Kommunikationseinstellungen für ein Benutzerkonto

Angenommen, Sie möchten Einstellungen für die externe Kommunikation für ein Benutzerkonto ändern. Sie möchten z. B. festlegen, dass Alex mit Partnerbenutzern kommunizieren darf (EnableFederationAccess = True), jedoch nicht mit Windows Live-Benutzern (EnablePublicCloudAccess = False). Hierzu müssen Sie zwei Schritte ausführen:
  
1. Suchen Sie nach eine externe Zugriffsrichtlinie, die unsere Kriterien erfüllt.
    
2. Weisen Sie Alex diese externe Zugriffsrichtlinie ist.
    
> [!NOTE]
>  Sie können keine benutzerdefinierte Richtlinie an alle Erstellen eigener. Dies liegt daran Skype für Business Online keine benutzerdefinierte Richtlinien erstellen kann. Stattdessen müssen Sie eine der Richtlinien zuweisen, die speziell für Office 365 erstellt wurden. Die Richtlinien der zuvor erstellten umfassen: 4 verschiedene Client-Richtlinien, 224 verschiedene Conferencing-Richtlinien, 5 verschiedene Wählpläne, 5 verschiedene externe Zugriffsrichtlinien, 1 gehostete Voicemail-Richtlinie und 4 verschiedene Voice-Richtlinien.
  
Woher wissen Sie, welche externe Zugriffsrichtlinie Sie Alex zuweisen müssen? Der folgende Befehl gibt alle externen Zugriffsrichtlinien zurück, in denen „EnableFederationAccess" auf „True" und „EnablePublicCloudAccess" auf „False" festgelegt ist:
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Funktionsweise des Befehls wird alle Richtlinien zurückzugeben, die zwei Kriterien erfüllen: die EnableFederationAccess-Eigenschaft auf True festgelegt ist, und die Richtlinie EnablePublicCloudAccess auf False festgelegt ist. Dieser Befehl gibt wiederum eine Richtlinie, die unsere Kriterien (FederationOnly) zurück. Es folgt ein Beispiel:
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> Die Richtlinienidentität besagt „Tag:FederationOnly". Wie sich zeigt, ist das Präfix „Tag:" ein Übertrag aus einer früheren Vorabversion für Microsoft Lync 2013. Beim Zuweisen von Richtlinien zu Benutzern sollten Sie das Präfix „Tag:" löschen und nur den Richtliniennamen verwenden: FederationOnly. 
  
Nachdem wir Sie wissen, welche Richtlinie Sie Alex zuweisen müssen, können Sie die Richtlinie mithilfe des Cmdlets [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) zuweisen: Hier ein Beispiel:
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Das Zuweisen einer Richtlinie ist ganz einfach: Sie geben einfach die Identität des Benutzers und den Namen der zuzuweisenden Richtlinie an. 
  
Und bei Richtlinien und Richtlinienzuweisungen sind Sie nicht darauf beschränkt, mit nur jeweils einem einzelnen Benutzerkonto zu arbeiten. Angenommen beispielsweise, Sie benötigen eine Liste aller Benutzer, die mit Partnerbenutzern und Windows Live-Benutzern kommunizieren dürfen. Wir wissen bereits, dass diesen Benutzern die externe Benutzerzugriffsrichtlinie „FederationAndPICDefault" zugewiesen wurde. Da wir dies wissen, können Sie eine Liste all dieser Benutzer anzeigen, indem Sie den folgenden einfachen Befehl ausführen:
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Anders gesagt, wir können alle Benutzer anzeigen, bei denen die ExternalAccessPolicy-Eigenschaft auf FederationAndPICDefault festgelegt ist. (Und zum Einschränken der am Bildschirm angezeigten Informationsmenge können Sie das Select-Object-Cmdlet verwenden, um nur die Anzeigenamen der Benutzer anzuzeigen). 
  
Um alle Benutzerkonten so zu konfigurieren, dass sie die gleiche Richtlinie verwenden, geben Sie diesen Befehl ein:
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Dieser Befehl verwendet „Get-CsOnlineUser", um eine Sammlung aller Benutzer zurückzugeben, die für Lync aktiviert wurden. Anschließend werden alle diese Informationen an „Grant-CsExternalAccessPolicy" gesendet, das die Richtlinie „FederationAndPICDefault" jedem Benutzer in der Sammlung zuweist.
  
Ein weiteres Beispiel: Angenommen, Sie haben Alex zuvor die Richtlinie „FederationAndPICDefault" zugewiesen, haben aber nun Ihre Meinung geändert und möchten, dass er von der globalen externen Zugriffsrichtlinie verwaltet wird. Sie können die globale Richtlinie niemandem explizit zuweisen. Sie wird nur verwendet, wenn keine andere benutzerspezifische Richtlinie zugewiesen ist. Wenn Sie also möchten, dass Alex von der globalen Richtlinie verwaltet wird, müssen Sie die Zuweisung aller zuvor zugewiesenen benutzerspezifischen Richtlinien wieder  *aufheben*  . Hier ein Beispielbefehl:
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Dieser Befehl legt den Namen der Alex zugewiesenen externen Zugriffsrichtlinie auf einen Nullwert ($Null) fest. Null bedeutet „nichts". Anders ausgedrückt, Alex wird keine externe Zugriffsrichtlinie zugewiesen. Wenn einem Benutzer keine externe Zugriffsrichtlinie zugewiesen ist, wird der Benutzer von der globalen Richtlinie verwaltet.
  
Verwenden Sie zum Deaktivieren eines Benutzerkontos mithilfe von Windows PowerShell die Azure Active Directory-Cmdlets Alexs Skype für Business Online-Lizenz entfernen. Weitere Informationen finden Sie unter [Zugriff auf Dienste mit Office 365 PowerShell deaktivieren](assign-licenses-to-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>See also

#### 

[Verwalten von Skype for Business Online mit Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

