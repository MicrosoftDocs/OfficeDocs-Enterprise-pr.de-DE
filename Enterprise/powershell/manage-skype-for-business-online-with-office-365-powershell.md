---
title: Verwalten von Skype for Business Online mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.'
ms.openlocfilehash: 33c7247686cc8eb308b8db6d4900c89f693004fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068731"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Verwalten von Skype for Business Online mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.
  
Eine der Hauptaufgaben des Skype for Business Online-Administrators ist die Richtlinienverwaltung. Obwohl Sie einige dieser Aufgaben im Office 365 Admin Center ausführen können, sind andere Aufgaben in Office 365 PowerShell viel schneller und einfacher. 

## <a name="before-you-start"></a>Vor der Bereitstellung

Laden Sie das [Skype for Business Online-Connector-Modul](https://www.microsoft.com/en-us/download/details.aspx?id=39366)herunter, installieren Sie es, und starten Sie den Computer neu, wenn Sie dazu aufgefordert werden.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Herstellen einer Verbindung mit einem Skype for Business Online-Administratorkontonamen und Kennwort

1. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Geben Sie im Dialogfeld **Windows PowerShell-Anmelde Informationsanforderung** Ihren Skype for Business Online-Administratorkontonamen und das Kennwort ein, und klicken Sie dann auf **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Herstellen einer Verbindung mit einem Skype for Business Online-Administratorkonto mit mehrstufiger Authentifizierung

1. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Wenn Sie vom Befehl **New-CsOnlineSession** dazu aufgefordert werden, geben Sie Ihren Skype for Business Online-Administratorkontonamen ein.

3. Geben Sie im Dialogfeld **Anmelden bei Ihrem Konto** Ihr Skype for Business Online-Administratorkennwort ein, und klicken Sie dann auf **Anmelden**.

4. Folgen Sie den Anweisungen im Dialogfeld **Anmelden bei Ihrem Konto** , um zusätzliche Authentifizierungsinformationen wie einen Überprüfungscode bereitzustellen, und klicken Sie dann auf **überprüfen**.

Weitere Informationen hierzu finden Sie unter den folgenden Themen:
  
- [Verwalten von Skype for Business Online-Richtlinien mit Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

[Verweise auf das Skype for Business PowerShell-Cmdlet](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

