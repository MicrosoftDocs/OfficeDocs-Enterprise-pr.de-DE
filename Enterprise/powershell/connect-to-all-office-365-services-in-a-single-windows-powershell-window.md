---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Zusammenfassung: Verbinden Sie Windows PowerShell mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster.'
ms.openlocfilehash: 3f6153d5ea8b88d8c6853dbbe597f2cf7cc62fab
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573969"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster

 **Zusammenfassung:** Anstatt verschiedene Office 365-Dienste in separaten PowerShell-Konsolenfenstern zu verwalten, können Sie eine Verbindung mit allen Office 365-Diensten herstellen und diese über ein einzelnes Konsolenfenster verwalten.
  
Wenn Sie PowerShell zum Verwalten von Office 365 verwenden, können bis zu fünf verschiedene Windows PowerShell-Sitzungen gleichzeitig geöffnet sein, entsprechend dem Microsoft 365 Admin Center, SharePoint Online, Exchange Online, Skype for Business Online und der Sicherheits &amp; Compliance Center. Mit fünf verschiedenen Verbindungsmethoden in separaten Windows PowerShell-Sitzungen könnte Ihr Desktop wie folgt aussehen:
  
![Fünf Windows PowerShell-Konsolen, die gleichzeitig ausgeführt werden](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Dies ist nicht optimal für die Verwaltung von Office 365, da Sie keine Daten zwischen diesen fünf Fenstern für die dienstübergreifende Verwaltung austauschen können. In diesem Thema wird beschrieben, wie Sie eine einzelne Instanz von Windows PowerShell verwenden, über die Sie Office 365, Skype for Business Online, Exchange Online, SharePoint Online und &amp; das Security Compliance Center verwalten können.

>[!Note]
>Dieser Artikel enthält derzeit nur die Befehle zum Herstellen einer Verbindung mit der Office 365 Worldwide (+ GCC)-Cloud. Zusätzliche Hinweise enthalten Links zu Artikeln mit Informationen zum Herstellen einer Verbindung mit den anderen Office 365-Clouds.
>

## <a name="before-you-begin"></a>Bevor Sie beginnen

Bevor Sie den gesamten Office 365 von einer einzigen Instanz von Windows PowerShell aus verwalten können, sollten Sie die folgenden Voraussetzungen berücksichtigen:
  
- Das Office 365-Arbeits-oder Schulkonto, das Sie für diese Verfahren verwenden, muss Mitglied einer Office 365-Administratorrolle sein. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367). Dies ist eine Voraussetzung für Office 365 PowerShell, nicht unbedingt für alle anderen Office 365-Dienste.
    
- Sie können folgende 64-Bit-Versionen von Windows verwenden:
    
  - Windows 10
    
  - Windows 8.1 oder Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 oder Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Sie müssen Microsoft .NET Framework 4,5 installieren. *x* und dann entweder Windows management Framework 3,0 oder Windows management Framework 4,0. Weitere Informationen finden Sie unter [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) und [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Sie müssen eine 64-Bit-Version von Windows aufgrund der Anforderungen für das Skype for Business Online-Modul und eines der Office 365-Module verwenden.
    
- Sie müssen die Module installieren, die für Azure AD, SharePoint Online und Skype for Business Online erforderlich sind:
    
   - [Azure Active Directory v2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online-Verwaltungsshell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype for Business Online, Windows PowerShell-Modul](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell muss so konfiguriert werden, dass signierte Skripts für Skype for Business Online, Exchange Online und das Security &amp; Compliance Center ausgeführt werden. Führen Sie dazu den folgenden Befehl in einer erhöhten Windows PowerShell-Sitzung aus (ein Windows PowerShell-Fenster, das Sie durch Auswählen von **als Administrator ausführen**öffnen).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Verbindungs Schritte bei Verwendung eines Kennworts

Hier sind die Schritte zum Herstellen einer Verbindung mit allen Diensten in einem einzelnen PowerShell-Fenster.
  
1. Öffnen Sie Windows PowerShell als Administrator (verwenden Sie **als Administrator ausführen**).
    
2. Führen Sie diesen Befehl aus, und geben Sie Ihre Office 365-Arbeits-oder Schulkonto Anmeldeinformationen ein.
    
  ```
  $credential = Get-Credential
  ```

3. Führen Sie diesen Befehl aus, um eine Verbindung mit Azure Active Directory (AD) mithilfe des Azure Active Directory PowerShell für Graph-Moduls herzustellen.
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  Wenn Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell verwenden, führen Sie diesen Befehl Alternativ aus.
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. Führen Sie diese Befehle aus, um eine Verbindung mit SharePoint Online herzustellen. Ersetzen _ \<Sie domainhost>_ durch den tatsächlichen Wert für Ihre Domäne. beispiel: bei "litwareinc.onmicrosoft.com" lautet der _ \<wert domainhost>_ "litwareinc".
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Führen Sie diese Befehle aus, um eine Verbindung mit Skype for Business Online herzustellen. Bei der ersten Verbindung wird `WSMan NetworkDelayms` eine Warnung zur Erhöhung des Werts erwartet, und Sie sollten ignoriert werden.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Führen Sie diese Befehle aus, um eine Verbindung mit Exchange Online herzustellen.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
>Informationen zum Herstellen einer Verbindung mit Exchange Online für Office 365-Clouds außer weltweit finden Sie unter [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
>

7. Führen Sie diese Befehle aus, um eine &amp; Verbindung mit dem Security Compliance Center herzustellen.
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>Informationen zum Herstellen einer Verbindung &amp; mit dem Security Compliance Center für Office 365-Clouds außer weltweit finden Sie unter [connect to Office 365 Security _AMP_ Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
>

Im folgenden werden alle Befehle in einem einzelnen Block angezeigt, wenn das Azure Active Directory PowerShell für Graph-Modul verwendet wird. Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Alternativ dazu finden Sie im folgenden alle Befehle in einem einzelnen Block, wenn Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell verwenden. Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Wenn Sie bereit sind, das Windows PowerShell-Fenster zu schließen, führen Sie diesen Befehl aus, um die aktiven Sitzungen zu Skype for Business Online, Exchange Online, SharePoint Online &amp; und dem Security Compliance Center zu entfernen:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Verbindungs Schritte bei Verwendung der mehrstufigen Authentifizierung

Hier sind alle Befehle in einem einzelnen Block, mit denen eine Verbindung mit Azure AD, SharePoint Online und Skype for Buiness mithilfe der mehrstufigen Authentifizierung in einem einzelnen Fenster mithilfe des Azure Active Directory PowerShell für Graph-Moduls hergestellt werden kann. Geben Sie den Benutzerprinzipalnamen (UPN) eines Benutzerkontos und ihren Domänenhost Namen an, und führen Sie alle gleichzeitig aus.

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Alternativ dazu finden Sie hier alle Befehle, wenn Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell verwenden.

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Informationen zu Exchange Online und zum &amp; Security Compliance Center finden Sie in den folgenden Themen zum Herstellen einer Verbindung mit mehrstufiger Authentifizierung:

- [Verbinden mit Exchange Online PowerShell per mehrstufiger Authentifizierung](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Herstellen einer Verbindung mit Office 365 Security & Compliance Center PowerShell mithilfe der mehrstufigen Authentifizierung](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
Beachten Sie, dass in beiden Fällen eine Verbindung über separate Sitzungen des Remote-PowerShell-Moduls von Exchange Online hergestellt werden muss.


## <a name="see-also"></a>Siehe auch

- [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md)
- [Verwalten von SharePoint Online mit Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
