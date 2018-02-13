---
title: Verbinden mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Zusammenfassung: Verbinden Sie mit Office 365-Organisation mit Office 365 PowerShell Aufgaben in Office 365 Admin Center über die Befehlszeile ausführen."
ms.openlocfilehash: 2f51c68acf55239c7d47f9b617a8a72965ead79d
ms.sourcegitcommit: 7ed9108846227ca883cb5113543a165704d9bbc8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2018
---
# <a name="connect-to-office-365-powershell"></a>Verbinden mit Office 365 PowerShell

 **Zusammenfassung:** Verbinden Sie mit Office 365-Organisation mit Office 365 PowerShell Office 365-Verwaltungsaufgaben über die Befehlszeile ausführen.
  
Office 365 PowerShell können Sie Ihre Office 365-Einstellungen über die Befehlszeile zu verwalten. Herstellen einer Verbindung mit Office 365 PowerShell ist ein einfacher dreistufiger Prozess, in dem Sie Installieren der erforderlichen Software, die erforderliche Software ausführen und dann verbinden mit Office 365-Organisation. 

Beachten Sie, dass diese Verbindung Anweisungen die gleichen, die im Thema [Azure ActiveDirectory (MSOnline sind)](https://go.microsoft.com/fwlink/p/?LinkId=528113).
  
> [!TIP]
> **Neue PowerShell?** Finden Sie ein [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), bereitgestellt von LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

- Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten
    
- Sie können folgende Versionen von Windows verwenden:
    
  - 10 Windows, Windows 8.1, Windows 8 oder Windows 7 Service Pack 1 (SP1) 
    
  - WindowsServer 2016, Windows Server 2012 R2, WindowsServer 2012 oder Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Verwenden Sie eine 64-Bit-Version von Windows. Unterstützung für 32-Bit-Version, die Microsoft Azure Active Directory-Modul für Windows PowerShell wurde im Oktober des 2014 eingestellt.
    
-  Office 365 arbeiten oder Schule Konto ein, das Sie für diese Verfahren Anforderungen verwenden, um ein Mitglied einer Office 365-Admin-Rolle sein. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kontaktaufnahme mit dem Microsoft Azure Active Directory-Moduls für Windows PowerShell

Befehle in der Microsoft Azure Active Directory-Modul für Windows PowerShell enthalten **Msol** in ihrem Cmdlet-Namen.
    
### <a name="step-1-install-required-software"></a>Schritt 1: Installieren der erforderlichen Software

Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.
  
1.  Installieren Sie die 64-Bit-Version des Microsoft Online Services-Anmeldeassistenten: [Microsoft Online Services - Anmeldeassistenten für IT-Experten RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installieren Sie die die Microsoft Azure Active Directory-Modul für Windows PowerShell mit der folgenden Schritte aus:
    
  - Öffnen Sie eine PowerShell-Eingabeaufforderung auf Administratorebene.
  - Führen Sie den Befehl **MSOnline Modul installieren** .
  - Wenn aufgefordert, den NuGet-Anbieter installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.
  - Wenn Sie aufgefordert werden, installieren Sie das Modul aus PSGallery, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.
  - Schließen Sie nach der Installation das PowerShell-Befehlsfenster.
    
### <a name="step-2-connect-to-your-office-365-subscription"></a>Schritt 2: Verbinden Sie mit Office 365-Abonnements
<a name="step3"> </a>

So verbinden Sie mit nur einem *Kontonamen und das Kennwort*:
  
1. Führen Sie eine Windows PowerShell-Eingabeaufforderung aus.
2. Führen Sie im Befehlsfenster **Windows PowerShell** die folgenden Befehle ein:
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. Klicken Sie im Dialogfeld **Windows PowerShell anmelden** Geben Sie Ihren Office 365 Arbeit oder Schule Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **OK**.
    
Zum Herstellen der Verbindung mit *Multi-Factor Authentication (mehrstufiger Authentifizierung das)*:
  
1. Führen Sie eine Windows PowerShell-Eingabeaufforderung aus.
2. Führen Sie im Befehlsfenster **Microsoft Azure Active Directory-Modul für Windows PowerShell** den folgenden Befehl ein.
    
```
Connect-MsolService
```

3. Klicken Sie im Dialogfeld **Azure Active Directory PowerShell** Geben Sie Ihren Office 365 Arbeit oder Schule Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
4. Befolgen Sie die Anweisungen im Dialogfeld **Azure Active Directory PowerShell** zusätzliche Authentifizierungsinformationen, beispielsweise einen Überprüfungscode bereitstellen, und klicken Sie dann auf **Anmelden**.
    
### <a name="how-do-you-know-this-worked"></a>Woher wissen Sie, dass dieses Verfahren erfolgreich war?
<a name="step3"> </a>

Wenn Sie keine Fehler erhalten, verbunden Sie erfolgreich. Ein schneller Test ein Office 365-Cmdlet ausgeführt wird – beispielsweise **Get-MsolUser** – und die Ergebnisse anzuzeigen.
  
Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:
  
- **Ein allgemeines Problem ist ein ungültiges Kennwort**. Führen Sie Schritt 3 erneut aus. und achten Sie besonders auf den Benutzernamen und das Kennwort, die Sie eingeben.
    
- **Die Microsoft Azure Active Directory-Modul für Windows PowerShell erfordert, dass Microsoft .NET Framework 3.5. _X_ -Funktion ist auf Ihrem Computer aktiviert**. Es ist wahrscheinlich, dass auf Ihrem Computer eine neuere Version installiert (beispielsweise 4 oder 4.5. hat ( _X_), aber rückwärts Kompatibilität mit älteren Versionen von .NET Framework aktiviert oder deaktiviert werden kann. Weitere Informationen finden Sie unter den folgenden Themen:
    
  - Windows Server 2012 oder Windows Server 2012 R2 finden Sie unter [.NET Framework 3.5 mithilfe der Rollen hinzufügen und den Assistenten Features aktivieren](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Windows 8 oder Windows 8.1 finden Sie unter [Installieren von .NET Framework 3.5 unter Windows 8 oder 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - Windows 7 oder Windows Server 2008 R2 finden Sie unter [der Azure Active Directory Modul für Windows PowerShell kann nicht geöffnet werden](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **Ihrer Version von der Microsoft Azure Active Directory-Modul für Windows PowerShell möglicherweise nicht mehr aktuell.** Führen Sie den folgenden Befehl in Office 365 PowerShell oder der Microsoft Azure Active Directory-Modul für Windows PowerShell, um zu überprüfen:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Wenn die Versionsnummer zurückgegeben niedriger als der Wert 1.0.8070.2 ist, deinstallieren Sie die Microsoft Azure Active Directory-Modul für Windows PowerShell, und installieren Sie die neueste Version über den Link in Schritt 1.
    
- **Wenn Sie eine Verbindung Fehlermeldung angezeigt wird, finden Sie unter in diesem Thema:** ["Connect-MsolService: Ausnahme vom Typ ausgelöst wurde" Fehler](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>Herstellen einer Verbindung mit dem Azure Active Directory V2 PowerShell-Modul.
<a name="ConnectV2"> </a>

Befehle im Azure Active Directory V2 PowerShell-Modul enthalten "AzureAD" in ihrem Cmdlet-Namen.

Verwenden Sie für Prozeduren, die die neuen Cmdlets im [Azure Active Directory V2 PowerShell-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)erfordern diese Schritte zum Installieren des Moduls und Verbinden mit Office 365-Abonnements.

### <a name="step-1-install-required-software"></a>Schritt 1: Installieren der erforderlichen Software

Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.

  
1. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).
    
2. In der **Administrator: Windows PowerShell** Befehlsfenster, und führen Sie diesen Befehl:
    
  ```
  Install-Module -Name AzureAD 
  ```

Wenn Sie aufgefordert werden, zum Installieren eines Moduls aus einer nicht vertrauenswürdigen Repository, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.


### <a name="step-2-connect-to-office-365"></a>Schritt 2: Verbinden Sie mit Office 365

Die Verbindung zum Office 365-Abonnement mit einem *Kontonamen und das Kennwort*:
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

Klicken Sie im Dialogfeld **Windows PowerShell anmelden** Geben Sie Ihren Office 365 Arbeit oder Schule Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **OK**.
    
Die Verbindung zum Office 365-Abonnement mit *Multi-Factor Authentication (mehrstufiger Authentifizierung das)*:

```
Connect-AzureAD
```

Klicken Sie im Dialogfeld **Azure Active Directory PowerShell** Geben Sie Ihren Office 365 Arbeit oder Schule Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
Befolgen Sie die Anweisungen im Dialogfeld **Azure Active Directory PowerShell** zusätzliche Authentifizierungsinformationen, beispielsweise einen Überprüfungscode bereitstellen, und klicken Sie dann auf **Anmelden**.
    
Nach dem anschließen, können Sie die neuen Cmdlets für die [Azure Active Directory V2 PowerShell-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)verwenden.
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)

[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[Verbinden-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

