---
title: Verwalten von Skype for Business Online mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.'
ms.openlocfilehash: f490131491a026961b0a5db312df5780483eadd9
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319236"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Verwalten von Skype for Business Online mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.
  
Eine der wichtigsten Aufgaben des Skype für Business Online-Administrator ist Richtlinien verwalten. Obwohl Sie einige dieser Aufgaben im Office 365 Admin Center ausführen können, sind andere Aufgaben viel schneller und einfacher in Office 365 PowerShell. 

## <a name="before-you-start"></a>Vor der Bereitstellung

Herunterladen und Installieren der [Skype Business Online Connector-Modul](https://www.microsoft.com/en-us/download/details.aspx?id=39366), und starten Sie den Computer neu, wenn Sie aufgefordert werden.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Eine Verbindung über einen Skype für Business Online-Administrator-Kontonamen und das Kennwort

1. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. Klicken Sie im Dialogfeld **Windows PowerShell anmelden** Geben Sie Ihre Skype für Business Online-Administrator-Kontonamen und das Kennwort ein, und klicken Sie dann auf **OK**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Eine Verbindung über einen Skype für Business Online Administratorkonto mit mehrstufige Authentifizierung

1. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Bei Aufforderung durch den Befehl **New-CsOnlineSession** Geben Sie Ihre Skype Business Online-Administrator Konto ein.

3. **Melden Sie sich bei Ihrem Konto** im Dialogfeld Geben Sie Ihre Skype Business Online Administratorkennwort ein, und klicken Sie dann auf **Anmelden**.

4. Befolgen Sie die Anweisungen im Dialogfeld **Melden Sie sich bei Ihrem Konto** zusätzliche Authentifizierungsinformationen, beispielsweise einen Überprüfungscode bereitstellen, und klicken Sie dann auf **Verify**.

Weitere Informationen hierzu finden Sie in den folgenden Themen:
  
- [Verwalten von Skype for Business Online-Richtlinien mit Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>See also

[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

