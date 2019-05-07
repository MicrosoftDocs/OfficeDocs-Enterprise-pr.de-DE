---
title: Verbinden mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Zusammenfassung: Stellen Sie mithilfe von Office 365 PowerShell eine Verbindung mit Ihrer Office 365-Organisation her, um Aufgaben des Verwaltungs Centers über die Befehlszeile auszuführen.'
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639776"
---
# <a name="connect-to-office-365-powershell"></a>Verbinden mit Office 365 PowerShell

 **Zusammenfassung:** Stellen Sie mithilfe von Office 365 PowerShell eine Verbindung mit Ihrer Office 365-Organisation her, um Verwaltungsaufgaben über die Befehlszeile auszuführen.
  
Mit Office 365 PowerShell können Sie Ihre Office 365-Einstellungen über die Befehlszeile verwalten. Das Herstellen einer Verbindung mit Office 365 PowerShell ist ein einfacher Vorgang, bei dem Sie die erforderliche Software installieren und dann eine Verbindung mit Ihrer Office 365-Organisation herstellen. 

Es gibt zwei Versionen des PowerShell-Moduls, die Sie zum Herstellen einer Verbindung mit Office 365 und zum Verwalten von Benutzerkonten, Gruppen und Lizenzen verwenden:

- Azure Active Directory PowerShell für Graph (Cmdlets schließen **AzureAD** in Ihrem Namen ein) 
- Microsoft Azure Active Directory-Modul für Windows PowerShell (Cmdlets schließen **MSol** in Ihrem Namen ein) 

Ab dem Datum dieses Artikels ersetzt das Modul Azure Active Directory PowerShell für Graph nicht vollständig die Funktionalität in den Cmdlets des Microsoft Azure Active Directory-Moduls für Windows PowerShell-Modul für Benutzer-, Gruppen-und Lizenzverwaltung. . In vielen Fällen müssen beide Versionen verwendet werden. Beide Versionen können problemlos auf demselben Computer installiert werden.

> [!TIP]
> **Neu bei PowerShell?** Sehen Sie sich eine [Video Übersicht über PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)an, die Ihnen von LinkedIn Learning präsentiert wird. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

- Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten
    
- Sie können folgende Versionen von Windows verwenden:
    
  - Windows 10, Windows 8,1, Windows 8 oder Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Verwenden Sie eine 64-Bit-Version von Windows. Unterstützung für die 32-Bit-Version das Microsoft Azure Active Directory-Modul für Windows PowerShell wurde im Oktober 2014 eingestellt.
    
-  Diese Verfahren sind für Benutzer gedacht, die Mitglieder einer Office 365-Administratorrolle sind. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Herstellen einer Verbindung mit dem Azure Active Directory PowerShell für Graph-Modul

Befehle im [Azure Active Directory PowerShell für Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) -Modul haben **AzureAD** in Ihrem Cmdlet-Namen.

Verfahren, für die die neuen Cmdlets im Azure Active Directory PowerShell für Graph-Modul erforderlich sind, finden Sie in den folgenden Schritten, um das Modul zu installieren und eine Verbindung mit Ihrem Office 365-Abonnement herzustellen.

>[!Note]
>Informationen zur Unterstützung verschiedener Versionen von Microsoft Windows finden Sie unter [Azure Active Directory PowerShell für Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .
>

### <a name="step-1-install-required-software"></a>Schritt 1: Installieren der erforderlichen Software

Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.
  
1. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).
    
2. Führen Sie im Befehlsfenster **Administrator: Windows PowerShell** den folgenden Befehl aus:
    
  ```
  Install-Module -Name AzureAD
  ```

Falls Sie gefragt werden, ob Sie ein Modul aus einem nicht vertrauenswürdigen Repository installieren möchten: Geben Sie **Y** ein, und drücken Sie die EINGABETASTE.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Schritt 2: Herstellen einer Verbindung mit Azure AD für Ihr Office 365-Abonnement

Wenn Sie eine Verbindung mit Azure AD für Ihr Office 365-Abonnement mit einem Kontonamen und Kennwort oder mit mehrstufiger *Authentifizierung (Multi-Factor Authentication, MFA)* herstellen möchten, führen Sie einen dieser Befehle an einer Windows PowerShell-Eingabeaufforderungen aus (er muss nicht erhöht werden).

|||
|:-------|:-----|
| **Office 365 Cloud** | **Befehl** |
| Office 365 Worldwide (+ gcc) | `Connect-AzureAD` |
| Office 365, betrieben von 21 vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Deutschland | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 u.s. Government DoD und Office 365 u.s. Government gcc High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Geben Sie im Dialogfeld in **Ihr Konto anmelden** den Benutzernamen und das Kennwort Ihres Office 365-Kontos ein, und klicken Sie dann auf **OK**.

Wenn Sie MFA verwenden, befolgen Sie die Anweisungen in den zusätzlichen Dialogfeldern, um weitere Authentifizierungsinformationen wie einen Überprüfungscode bereitzustellen.


Nachdem Sie eine Verbindung hergestellt haben, können Sie die neuen Cmdlets für das [Azure Active Directory PowerShell für Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)verwenden.
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Herstellen einer Verbindung mit dem Microsoft Azure Active Directory-Modul für Windows PowerShell

Befehle im Microsoft Azure Active Directory-Modul für Windows PowerShell haben **MSOL** in Ihrem Cmdlet-Namen.
    
### <a name="step-1-install-required-software"></a>Schritt 1: Installieren der erforderlichen Software

Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.
  
1.  Installieren Sie die 64-Bit-Version des Microsoft Online Services-Anmelde-Assistenten: [Microsoft Online Services-Anmelde-Assistent für IT-Experten RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installieren Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell mit den folgenden Schritten:
    
  - Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).
  - Führen Sie den **MSOnline-Befehl install-module** aus.
  - Wenn Sie aufgefordert werden, den NuGet-Anbieter zu installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.
  - Wenn Sie aufgefordert werden, das Modul von PSGallery zu installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Schritt 2: Herstellen einer Verbindung mit Azure AD für Ihr Office 365-Abonnement

Wenn Sie eine Verbindung mit Azure AD für Ihr Office 365-Abonnement mit einem Kontonamen und Kennwort oder mit mehrstufiger *Authentifizierung (Multi-Factor Authentication, MFA)* herstellen möchten, führen Sie einen dieser Befehle an einer Windows PowerShell-Eingabeaufforderungen aus (er muss nicht erhöht werden).

|||
|:-------|:-----|
| **Office 365 Cloud** | **Befehl** |
| Office 365 Worldwide (+ gcc) | `Connect-MsolService` |
| Office 365, betrieben von 21 vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Deutschland | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 u.s. Government DoD und Office 365 u.s. Government gcc High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

Geben Sie im Dialogfeld in **Ihr Konto anmelden** den Benutzernamen und das Kennwort Ihres Office 365-Kontos ein, und klicken Sie dann auf **OK**.

Wenn Sie MFA verwenden, befolgen Sie die Anweisungen in den zusätzlichen Dialogfeldern, um weitere Authentifizierungsinformationen wie einen Überprüfungscode bereitzustellen.

### <a name="how-do-you-know-this-worked"></a>Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn Sie keine Fehlermeldungen erhalten, wurde die Verbindung erfolgreich hergestellt. Ein kurzer Test besteht darin, ein Office 365-Cmdlet auszuführen, beispielsweise **Get-MsolUser** , und die Ergebnisse anzuzeigen.
  
Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:
  
- **Ein häufiges Problem ist ein falsches Kennwort**. Führen Sie Schritt 2 erneut aus. und achten Sie auf den Benutzernamen und das Kennwort, die Sie eingeben.
    
- * *Das Microsoft Azure Active Directory-Modul für Windows PowerShell erfordert, dass Microsoft .NET Framework 3,5.* x * Feature ist auf Ihrem Computer aktiviert * *. Es ist wahrscheinlich, dass auf Ihrem Computer eine neuere Version installiert ist (beispielsweise 4 oder 4,5.* x *), aber Abwärtskompatibilität mit älteren Versionen von .NET Framework kann aktiviert oder deaktiviert werden. Weitere Informationen hierzu finden Sie in den folgenden Themen:
    
  - Informationen zu Windows Server 2012 oder Windows Server 2012 R2 finden Sie unter [Aktivieren von .NET Framework 3,5 mithilfe des Assistenten zum Hinzufügen von Rollen und Features](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Unter Windows 7 oder Windows Server 2008 R2 finden Sie Informationen zum [Öffnen des Azure Active Directory-Moduls für Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370) .

  - Informationen zu Windows 10, Windows 8,1 und Windows 8 finden Sie unter [Installieren von .NET Framework 3,5 unter Windows 10, Windows 8,1 und Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10) .

  
- **Möglicherweise ist Ihre Version des Microsoft Azure Active Directory-Moduls für Windows PowerShell veraltet.** Führen Sie den folgenden Befehl in Office 365 PowerShell oder das Microsoft Azure Active Directory-Modul für Windows PowerShell aus:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Wenn die zurückgegebene Versionsnummer niedriger als der Wert 1.0.8070.2 ist, deinstallieren Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell, und installieren Sie die neueste Version über den Link in Schritt 1.
    
- **Wenn ein Verbindungsfehler angezeigt wird, finden Sie weitere Informationen unter diesem Thema:** [Fehler "Connect-MsolService: Exception of type"](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    

## <a name="see-also"></a>Siehe auch

- [Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
- [Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

