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
description: 'Zusammenfassung: Verbinden Sie mit Office 365-Organisation mithilfe von PowerShell für Office 365 Admin Center Aufgaben über die Befehlszeile ausführen.'
ms.openlocfilehash: d9bee7060f599120d2d6036c45b44e485ea9a0bd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849891"
---
# <a name="connect-to-office-365-powershell"></a>Verbinden mit Office 365 PowerShell

 **Zusammenfassung:** Verbinden Sie mit Office 365-Organisation mit Office 365 PowerShell Verwaltungsaufgaben über die Befehlszeile ausführen.
  
Office 365 PowerShell können Sie Ihre Office 365-Einstellungen über die Befehlszeile zu verwalten. Herstellen einer Verbindung mit Office 365 PowerShell ist ein einfacher Vorgang, in dem Sie die erforderliche Software installieren und dann verbinden mit Office 365-Organisation. 

Es gibt zwei Versionen von PowerShell-Modul, mit denen Sie eine Verbindung mit Office 365 sowie zur Verwaltung von Benutzerkonten, Gruppen und Lizenzen:

- Azure Active Directory-PowerShell für Diagramm (Cmdlets include **AzureAD** in ihrem Namen) 
- Microsoft Azure Active Directory-Modul für Windows PowerShell (Cmdlets include **MSol** in ihrem Namen) 

Ab dem Datum des Artikels ersetzen Azure Active Directory PowerShell Graph-Modul nicht vollständig in die Microsoft Azure Active Directory-Modul für Windows PowerShell-Modul für Benutzer-, Gruppen- und Lizenz Verwaltung-Cmdlets die Funktionalität . In vielen Fällen müssen Sie beide Versionen verwenden. Sie können beide Versionen sicher auf demselben Computer installieren.

> [!TIP]
> **Neue PowerShell?** Finden Sie ein [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), bereitgestellt von LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

- Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten
    
- Sie können folgende Versionen von Windows verwenden:
    
  - 10 Windows, Windows 8.1, Windows 8 oder Windows 7 Servicepack 1 (SP1) 
    
  - WindowsServer 2019, WindowsServer 2016, Windows Server 2012 R2, WindowsServer 2012 oder Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Verwenden Sie eine 64-Bit-Version von Windows. Unterstützung für 32-Bit-Version, die Microsoft Azure Active Directory-Modul für Windows PowerShell wurde im Oktober des 2014 eingestellt.
    
-  Diese Verfahren sind für Benutzer vorgesehen, die ein Office 365-Administratorrolle angehören. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Kontaktaufnahme mit Azure Active Directory PowerShell Graph-Modul

Befehle im Modul [Azure Active Directory PowerShell für Diagramm](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) enthalten **AzureAD** in ihrem Cmdlet-Namen.

Verwenden Sie für Prozeduren, die die neuen in Azure Active Directory PowerShell-Cmdlets für Diagramm Modul erforderlich ist diese Schritte zum Installieren des Moduls und Verbinden mit Office 365-Abonnements.

>[!Note]
>Finden Sie Informationen über die Unterstützung für verschiedene Versionen von Microsoft Windows [Azure Active Directory-PowerShell-Modul Diagramm](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .
>

### <a name="step-1-install-required-software"></a>Schritt 1: Installieren der erforderlichen Software

Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.
  
1. Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).
    
2. Führen Sie im Befehlsfenster **Administrator: Windows PowerShell** den folgenden Befehl aus:
    
  ```
  Install-Module -Name AzureAD
  ```

Falls Sie gefragt werden, ob Sie ein Modul aus einem nicht vertrauenswürdigen Repository installieren möchten: Geben Sie **Y** ein, und drücken Sie die EINGABETASTE.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Schritt 2: Verbinden Sie mit Azure AD für Ihre Office 365-Abonnements

Zum Verbinden von Azure AD für Ihr Office 365-Abonnement mit einen Kontonamen und ein Kennwort oder mit *Multi-Factor Authentication (mehrstufiger Authentifizierung das)* führen Sie einen der folgenden Befehle aus einer Windows PowerShell-Eingabeaufforderung (es ist nicht erforderlich, werden mit erhöhten Rechten).

|||
|:-------|:-----|
| **Office 365-cloud** | **Befehl** |
| Office 365 weltweit (+ GCC) | `Connect-AzureAD` |
| Office 365, die vom Dienst 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Deutschland | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 US-Regierung Verteidigungsministeriums oder Office 365 US-Regierung GCC hoch | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Klicken Sie im Dialogfeld **Anmeldung bei Ihrem Konto** Geben Sie Ihren Office 365 Arbeit oder Schule Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **OK**.

Wenn Sie mit mehrstufiger Authentifizierung das nutzen, befolgen Sie die Anweisungen in den Dialogfeldern zusätzliche Weitere Authentifizierungsinformationen, beispielsweise einen Überprüfungscode bereitstellen.


Nach dem anschließen, können Sie die neuen Cmdlets für die [Azure Active Directory PowerShell Graph-Modul](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)verwenden.
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kontaktaufnahme mit dem Microsoft Azure Active Directory-Moduls für Windows PowerShell

Befehle in der Microsoft Azure Active Directory-Modul für Windows PowerShell enthalten **Msol** in ihrem Cmdlet-Namen.
    
### <a name="step-1-install-required-software"></a>Schritt 1: Installieren der erforderlichen Software

Diese Schritte sind auf Ihrem Computer nur einmal erforderlich, nicht jedes Mal, wenn Sie eine Verbindung herstellen. Allerdings müssen Sie wahrscheinlich in regelmäßigen Abständen neuere Versionen der Software installieren.
  
1.  Installieren Sie die 64-Bit-Version des Microsoft Online Services-Anmeldeassistenten: [Microsoft Online Services - Anmeldeassistenten für IT-Experten RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installieren Sie die Microsoft Azure Active Directory-Modul für Windows PowerShell mit der folgenden Schritte aus:
    
  - Öffnen Sie eine Windows PowerShell-Eingabeaufforderung mit erhöhten Rechten (d. h., führen Sie Windows PowerShell als Administrator aus).
  - Führen Sie den Befehl **MSOnline Modul installieren** .
  - Wenn aufgefordert, den NuGet-Anbieter installieren, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.
  - Wenn Sie aufgefordert werden, installieren Sie das Modul aus PSGallery, geben Sie **Y** ein, und drücken Sie die EINGABETASTE.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Schritt 2: Verbinden Sie mit Azure AD für Ihre Office 365-Abonnements

Zum Verbinden von Azure AD für Ihr Office 365-Abonnement mit einen Kontonamen und ein Kennwort oder mit *Multi-Factor Authentication (mehrstufiger Authentifizierung das)* führen Sie einen der folgenden Befehle aus einer Windows PowerShell-Eingabeaufforderung (es ist nicht erforderlich, werden mit erhöhten Rechten).

|||
|:-------|:-----|
| **Office 365-cloud** | **Befehl** |
| Office 365 weltweit (+ GCC) | `Connect-MsolService` |
| Office 365, die vom Dienst 21 Vianet | `Connect-MsolService -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Deutschland | `Connect-MsolService -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 US-Regierung Verteidigungsministeriums oder Office 365 US-Regierung GCC hoch | `Connect-MsolService -AzureEnvironmentName USGovernment` |
|||

Klicken Sie im Dialogfeld **Anmeldung bei Ihrem Konto** Geben Sie Ihren Office 365 Arbeit oder Schule Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **OK**.

Wenn Sie mit mehrstufiger Authentifizierung das nutzen, befolgen Sie die Anweisungen in den Dialogfeldern zusätzliche Weitere Authentifizierungsinformationen, beispielsweise einen Überprüfungscode bereitstellen.

### <a name="how-do-you-know-this-worked"></a>Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn Sie keine Fehler erhalten, verbunden Sie erfolgreich. Ein schneller Test ein Office 365-Cmdlet ausgeführt wird – beispielsweise **Get-MsolUser** – und die Ergebnisse anzuzeigen.
  
Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:
  
- **Ein allgemeines Problem ist ein ungültiges Kennwort**. Führen Sie Schritt2 erneut aus. und achten Sie besonders auf den Benutzernamen und das Kennwort, die Sie eingeben.
    
- * *Der Microsoft Azure Active Directory-Modul für Windows PowerShell erfordert, dass Microsoft .NET Framework 3.5.* X * Feature wird auf Ihrem Computer ** aktiviert. Ist es wahrscheinlich, dass auf Ihrem Computer eine neuere Version installiert ist (beispielsweise 4 oder 4.5.* X *), aber rückwärts Kompatibilität mit älteren Versionen von .NET Framework aktiviert oder deaktiviert werden kann. Weitere Informationen finden Sie unter den folgenden Themen:
    
  - Windows Server 2012 oder Windows Server 2012 R2 finden Sie unter [.NET Framework 3.5 mithilfe der Rollen hinzufügen und den Assistenten Features aktivieren](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Windows 7 oder Windows Server 2008 R2 finden Sie unter [der Azure Active Directory Modul für Windows PowerShell kann nicht geöffnet werden](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - 10 für Windows, Windows 8.1 und Windows 8 finden Sie unter [Installieren von .NET Framework 3.5 auf 10 Windows, Windows 8.1-und Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
- **Ihrer Version von der Microsoft Azure Active Directory-Modul für Windows PowerShell möglicherweise nicht mehr aktuell.** Führen Sie den folgenden Befehl in Office 365 PowerShell oder der Microsoft Azure Active Directory-Modul für Windows PowerShell, um zu überprüfen:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Wenn die Versionsnummer zurückgegeben niedriger als der Wert 1.0.8070.2 ist, deinstallieren Sie die Microsoft Azure Active Directory-Modul für Windows PowerShell, und installieren Sie die neueste Version über den Link in Schritt 1.
    
- **Wenn Sie eine Verbindung Fehlermeldung angezeigt wird, finden Sie unter in diesem Thema:** ["Connect-MsolService: Ausnahme vom Typ ausgelöst wurde" Fehler](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    

## <a name="see-also"></a>Siehe auch

- [Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
- [Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Verbinden-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

