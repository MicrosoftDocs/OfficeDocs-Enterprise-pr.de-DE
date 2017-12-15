---
title: Verwalten von Skype for Business Online-Richtlinien mit Office 365 PowerShell
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
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell, um die Eigenschaften von Skype for Business Online-Benutzerkonten mithilfe von Richtlinien zu verwalten.'
ms.openlocfilehash: 9b3877d2680b2b36d155cb5dd2a69fa21c972fe3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>Verwalten von Skype for Business Online-Richtlinien mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell, um Ihre Skype für Business Online Benutzerkontoeigenschaften mit Richtlinien verwalten.
  
Um viele Eigenschaften eines Benutzerkontos für Skype for Business Online zu verwalten, müssen Sie diese als Eigenschaften von Richtlinien mit Office 365 PowerShell angeben.
  
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
    
## <a name="manage-user-account-policies"></a>Verwalten von Richtlinien für Benutzerkonten

Viele Eigenschaften von Skype for Business Online-Benutzerkonten werden mithilfe von Richtlinien konfiguriert. Richtlinien sind einfach Sammlungen von Einstellungen, die auf einen oder mehrere Benutzer angewendet werden können. Um sich die Konfiguration einer Richtlinie anzusehen, können Sie diesen Beispielbefehl für die Richtlinie „FederationAndPICDefault" ausführen:
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Sie sollte wiederum wieder dann in etwa so aussehen:
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

In diesem Beispiel legen die Werte in der Richtlinie fest, welche Aktionen ein Benutzer bei der Kommunikation mit Partnerbenutzern ausführen darf bzw. nicht ausführen darf. Beispielsweise muss die Eigenschaft „EnableOutsideAccess" für einen Benutzer auf „true" festgelegt werden, damit er mit Personen außerhalb der Organisation kommunizieren darf. Beachten Sie, dass diese Eigenschaft nicht im Office 365 Admin Center angezeigt wird. Stattdessen wird die Eigenschaft anhand der anderen von Ihnen getroffenen Auswahlvorgänge automatisch auf „true" oder „false" festgelegt. Die beiden anderen relevanten Eigenschaften sind:
  
- **EnableFederationAccess** gibt an, ob der Benutzer mit Personen von Verbunddomänen kommunizieren darf.
    
- **EnablePublicCloudAccess** gibt an, ob der Benutzer mit Windows Live-Benutzern kommunizieren darf.
    
Aus diesem Grund ändern nicht Sie direkt Verbund-bezogene Eigenschaften von Benutzerkonten (z. B. **Set-CsUser-EnableFederationAccess $True**). Stattdessen weisen Sie einem Konto an eine externe Zugriffsrichtlinie, die die gewünschte Eigenschaftswerte vorkonfiguriert ist. Wenn Sie einen Benutzer, Verbundbenutzer und mit Windows Live-Benutzern kommunizieren können möchten, muss mit dem Benutzerkonto eine Richtlinie zugewiesen werden, die diese Arten der Kommunikation ermöglicht.
  
Wenn Sie wissen möchten, ob jemand mit Benutzern außerhalb der Organisation kommunizieren kann, müssen Sie Folgendes tun:
  
- Festlegen, welche externe Zugriffsrichtlinie dem betreffenden Benutzer zugewiesen wird.
    
- Festlegen, welche Funktionen durch diese Richtlinie erlaubt werden.
    
Sie können zu diesem Zweck beispielsweise den folgenden Befehl verwenden:
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Dieser Befehl sucht nach der dem Benutzer zugewiesenen Richtlinie und dann in dieser Richtlinie nach den deaktivierten/aktivierten Funktionen.
  
Beachten Sie, dass es keine Cmdlets zum Erstellen oder Ändern von Richtlinien gibt. Sie müssen die von Office 365 bereitgestellten Richtlinien verwenden. Um sich einen Überblick über die verschiedenen verfügbaren Richtlinien zu verschaffen, verwenden Sie diese Befehle:
  
- Get-CsClientPolicy       
- Get-CsConferencingPolicy        
- Get-CsDialPlan            
- Get-CsExternalAccessPolicy                         
- Get-CsHostedVoicemailPolicy                        
- Get-CsPresencePolicy                               
- Get-CsVoicePolicy                                  

> [!NOTE]
> Ein Skype for Business Online-Wählplan ist jeder Hinsicht mit Ausnahme des Namens eine Richtlinie. Der Name „Wählplan" wurde statt „Wählrichtlinie" oder einem ähnlichen Namen verwendet, um die Abwärtskompatibilität mit Office Communications Server und Exchange sicherzustellen. 
  
Beispiel: Um alle für Sie verfügbaren VoIP-Richtlinien anzuzeigen, verwenden Sie diesen Befehl:
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> Eine Liste aller verfügbaren VoIP-Richtlinien zurückgibt für Sie. Behalten Sie im Hinterkopf, allerdings, die nicht alle Richtlinien für alle Benutzer zugewiesen werden können. Dies ist aufgrund von verschiedenen Einschränkungen im Zusammenhang mit Lizenzierung und geografischen Standort. (So genannte "[Usage Speicherort](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") Wenn Sie möchten wissen, Richtlinien für den externen Zugriff und konferenzrichtlinien, die einem bestimmten Benutzer zugewiesen werden können, verwenden Sie die Befehle, die etwa wie folgt: 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

Der Parameter "ApplicableTo" beschränkt die zurückgegebenen Daten auf Richtlinien, die einem bestimmten Benutzer zugewiesen werden können (zum Beispiel Alex Darrow). Je nach Lizenz- und Verwendungsstandortbeschränkungen kann dies eine Teilmenge aller verfügbaren Richtlinien sein. 
  
In einigen Fällen werden Eigenschaften von Richtlinien nicht mit Office 365 verwendet, während andere nur von Microsoft-Supportmitarbeitern verwaltet werden können. 
  
Bei Skype for Business Online müssen Benutzer über eine Richtlinie verwaltet werden. Wenn eine gültige richtlinienbezogene Eigenschaft leer ist, bedeutet dies, dass der betreffende Benutzer von einer globalen Richtlinie verwaltet wird; dies ist ein Richtlinie, die automatisch auf einen Benutzer angewendet wird, es sei denn, dem Benutzer ist explizit eine benutzerspezifische Richtlinie zugewiesen. Da keine Clientrichtlinie für ein Benutzerkonto angezeigt wird, wird es durch die globale Richtlinie verwaltet. Sie können die globale Clientrichtlinie mit diesem Befehl ermitteln:
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>See also

#### 

[Verwalten von Skype for Business Online mit Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

