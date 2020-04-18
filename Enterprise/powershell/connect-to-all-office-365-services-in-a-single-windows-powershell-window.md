---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Zusammenfassung: Verbinden Sie Windows PowerShell mit allen Office 365 Diensten in einem einzelnen Windows PowerShell Fenster.'
ms.openlocfilehash: d47f4dab4938bd02be25525d2912604f676079db
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547753"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster

Wenn Sie Office 365 mithilfe von PowerShell verwalten, können bis zu fünf verschiedene Windows PowerShell Sitzungen gleichzeitig geöffnet sein, die dem Microsoft 365 Admin Center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams und dem Security &amp; Compliance Center entsprechen. Mit fünf verschiedenen Verbindungsmethoden in separaten Windows PowerShell Sitzungen könnte Ihr Desktop wie folgt aussehen:
  
![Fünf Windows PowerShell Konsolen, die gleichzeitig gestartet werden](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Dies ist für die Verwaltung von Office 365 nicht optimal, da Sie keine Daten zwischen diesen fünf Fenstern für die dienstübergreifende Verwaltung austauschen können. In diesem Thema wird beschrieben, wie Sie eine einzelne Instanz von Windows PowerShell verwenden, aus der Sie Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams und dem &amp; Security Compliance Center verwalten können.

>[!Note]
>Dieser Artikel enthält derzeit nur die Befehle zum Herstellen einer Verbindung mit der Office 365 Worldwide (+ gcc)-Cloud. Zusätzliche Hinweise bieten Links zu Artikeln mit Informationen zum Herstellen einer Verbindung mit anderen Office 365 Clouds.
>

## <a name="before-you-begin"></a>Bevor Sie beginnen

Bevor Sie alle Office 365 aus einer einzigen Instanz von Windows PowerShell verwalten können, sollten Sie die folgenden Voraussetzungen erfüllen:
  
- Das Office 365 Arbeits-oder Schulkonto, das Sie für diese Verfahren verwenden, muss Mitglied einer Office 365 Administratorrolle sein. Weitere Informationen finden Sie unter [Informationen zu Administratorrollen von Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Dies ist eine Voraussetzung für Office 365 PowerShell, nicht notwendigerweise für alle anderen Office 365 Dienste.
    
- Sie können folgende 64-Bit-Versionen von Windows verwenden:
    
  - Windows 10
    
  - Windows 8.1 oder Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 oder Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Sie müssen die Microsoft .NET Framework 4.5 installieren. *x* und dann entweder Windows Management Framework 3,0 oder Windows Management Framework 4,0. Weitere Informationen finden Sie unter [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Sie müssen eine 64-Bit-Version von Windows aufgrund der Anforderungen für das Skype for Business Online Modul und eines der Office 365 Module verwenden.
    
- Sie müssen die Module installieren, die für Azure AD, Exchange Online, SharePoint Online, Skype for Business Online und Microsoft Teams erforderlich sind:
    
   - [Azure Active Directory v2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online Management-Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype for Business Online, Windows PowerShell Modul](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Exchange Online PowerShell v2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [Übersicht über Microsoft Teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  Windows PowerShell muss so konfiguriert werden, dass signierte Skripts für Skype for Business Online und das &amp; Security Compliance Center ausgeführt werden. Führen Sie dazu den folgenden Befehl in einer erhöhten Windows PowerShell-Sitzung aus (ein Windows PowerShell Fenster, das Sie durch Auswählen von **als Administrator ausführen**öffnen).
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Verbindungs Schritte bei Verwendung eines Kennworts

Hier finden Sie die Schritte zum Herstellen einer Verbindung mit allen Diensten in einem einzigen PowerShell-Fenster.
  
1. Öffnen Sie Windows PowerShell.
    
2. Führen Sie diesen Befehl aus, und geben Sie die Anmeldeinformationen für Office 365 work oder School Account ein.
    
  ```powershell
  $credential = Get-Credential
  ```

3. Führen Sie diesen Befehl aus, um eine Verbindung mit Azure Active Directory (AD) mithilfe des Azure Active Directory PowerShell for Graph-Moduls herzustellen.
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  Wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden, führen Sie diesen Befehl Alternativ aus.
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
>PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen. Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.
>

4. Führen Sie diese Befehle aus, um eine Verbindung mit SharePoint Online herzustellen. Ersetzen _ \<Sie domainhost>_ durch den tatsächlichen Wert für Ihre Domäne. Für "litwareinc.onmicrosoft.com" ist beispielsweise der _ \<domainhost->_ Wert "litwareinc".
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Führen Sie diese Befehle aus, um eine Verbindung mit Skype for Business Online herzustellen. Eine Warnung zur Erhöhung des `WSMan NetworkDelayms` Werts wird erwartet, wenn Sie das erste Mal eine Verbindung herstellen und ignoriert werden.
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Führen Sie diesen Befehl aus, um eine Verbindung mit Exchange Online herzustellen.
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
>Verwenden Sie den **-ExchangeEnvironmentName-** Parameter, um eine Verbindung mit Exchange Online für Office 365 andere Clouds als weltweit herzustellen. Weitere Informationen finden Sie unter [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) .
>

7. Führen Sie diese Befehle aus, um eine Verbindung mit PowerShell-Teams herzustellen.
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
>Informationen zum Herstellen einer Verbindung mit anderen Microsoft Teams-Clouds als weltweit finden Sie unter [Connect-verläuft](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).
>

8. Führen Sie diese Befehle aus, um eine &amp; Verbindung mit dem Security Compliance Center herzustellen.
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>Informationen zum Herstellen einer Verbindung &amp; mit dem Security Compliance Center für Office 365 andere Clouds als weltweit finden Sie unter [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
>

Im folgenden finden Sie alle Befehle in einem einzigen Block, wenn Sie das Modul Azure Active Directory PowerShell for Graph verwenden. Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Alternativ finden Sie hier alle Befehle in einem einzigen Block, wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden. Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Wenn Sie das Windows PowerShell Fenster schließen möchten, führen Sie diesen Befehl aus, um die aktiven Sitzungen in Skype for Business Online, SharePoint Online, im Security &amp; Compliance Center und in Microsoft Teams zu entfernen:
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Verbindungs Schritte bei Verwendung der mehrstufigen Authentifizierung

Im folgenden finden Sie alle Befehle in einem einzelnen Block zum Herstellen einer Verbindung mit Azure AD, SharePoint Online, Skype for Business, Exchange Online und Teams mithilfe der mehrstufigen Authentifizierung in einem einzigen Fenster mithilfe des Azure Active Directory PowerShell for Graph-Moduls. Geben Sie den Benutzerprinzipalnamen (User Principal Name, UPN) eines Benutzerkontos und den Namen Ihres Domänenhosts an, und führen Sie dann alle gleichzeitig aus.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

Alternativ finden Sie hier alle Befehle, wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

Informationen zum Security &amp; Compliance Center finden Sie unter [Verbinden mit Office 365 Security & Compliance Center PowerShell mithilfe der mehr](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) stufigen Authentifizierung zum Herstellen einer Verbindung mit mehrstufiger Authentifizierung:

## <a name="see-also"></a>Siehe auch

- [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md)
- [Verwalten von SharePoint Online mit Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
