---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/11/2018
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
description: 'Zusammenfassung: Verbinden Sie Windows PowerShell mit allen Office 365-Diensten in einem einzelnen Windows PowerShell-Fenster.'
ms.openlocfilehash: 44f00364d1f81633e06663770f32e0c9f9e99ed8
ms.sourcegitcommit: 22db89d5b13f7d85e03f35f21f25fa288aadf1b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "25575259"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster

 **Zusammenfassung:** Anstelle von Verwalten von verschiedenen Office 365-Diensten in separaten Fenstern von PowerShell-Konsole, können Sie eine Verbindung mit allen Office 365-Diensten und über einzelne Konsolenfenster verwalten.
  
Wenn Sie zum Verwalten von Office 365 PowerShell verwenden, ist es möglich, bis zu fünf verschiedene Windows PowerShell-Sitzungen entsprechend der Office 365 Administrationscenter, SharePoint Online, Exchange Online, Skype für Business Online und die Sicherheit &amp;Compliance Center. Mit fünf unterschiedliche Verbindungsmethoden in separaten Windows PowerShell-Sitzungen konnte Ihren Desktop sieht folgendermaßen aus:
  
![Fünf gleichzeitig ausgeführte Windows PowerShell-Konsolen](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Dies ist nicht für die Verwaltung von Office 365, da Sie Daten zwischen diesen fünf Windows for Cross-Service-Management austauschen können nicht optimal. In diesem Thema wird beschrieben, wie eine einzelne Instanz von Windows PowerShell verwenden, Sie können aus dem Office 365, Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit verwalten &amp; Compliance Center.

## <a name="before-you-begin"></a>Vorbemerkung

Bevor Sie alle von Office 365 von einer einzigen Instanz von Windows PowerShell verwalten können, sollten Sie die folgenden erforderlichen Komponenten:
  
- Office 365 arbeiten oder Schule Konto ein, das Sie für diese Verfahren Anforderungen verwenden, um ein Mitglied einer Office 365-Admin-Rolle sein. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367). Diese eine Voraussetzung für Office 365 PowerShell, was nicht notwendigerweise für alle anderen Office 365-Dienste.
    
- Sie können folgende 64-Bit-Versionen von Windows verwenden:
    
  - Windows 10
    
  - Windows 8.1 oder Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 oder Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Sie müssen Microsoft .NET Framework 4.5 zu installieren. *X* , und klicken Sie dann entweder das Windows Management Framework 3.0 oder das Windows Management Framework 4.0. Weitere Informationen finden Sie unter [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) und [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Sie müssen eine 64-Bit-Version von Windows für Business Online Modul und einen der Office 365-Module aufgrund der Anforderungen für die Skype verwenden.
    
- Sie müssen die Module installieren, die für Azure AD erforderlich sind SharePoint Online und Skype für Business Online:
    
   - [Azure Active Directory-V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online-Verwaltungsshell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype für Unternehmen Online, Windows PowerShell-Modul](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell zum Ausführen von signierten Skripts für Skype für Business Online, Exchange Online und die Sicherheit konfiguriert werden muss &amp; Compliance Center. Zu diesem Zweck führen Sie den folgenden Befehl in einer Windows PowerShell-Sitzung mit erhöhten Rechten (ein Windows PowerShell-Fenster Sie öffnen, indem Sie **als Administrator ausführen**auswählen).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Verbindung Schritte aus, wenn Sie ein Kennwort verwenden

Hier sind die Schritte zum Herstellen einer Verbindung alle Dienste in einem einzelnen PowerShell-Fenster.
  
1. Öffnen Sie Windows PowerShell als Administrator (verwenden Sie **als Administrator ausführen**).
    
2. Führen Sie diesen Befehl, und geben Sie Ihre Office 365 Arbeit oder Schule Kontoanmeldeinformationen.
    
  ```
  $credential = Get-Credential
  ```

3. Führen Sie diesen Befehl für die Verbindung zu Azure Active Directory (AD) mithilfe von Azure Active Directory PowerShell Graph-Modul.
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  Auch wenn Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell-Modul verwenden, führen Sie diesen Befehl aus.
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. Führen Sie diese Befehle für die Verbindung mit SharePoint Online. Ersetzen Sie _ \<Domainhost >_ durch den tatsächlichen Wert für Ihre Domäne. Zum Beispiel für "litwareinc.onmicrosoft.com" die _ \<Domainhost >_ Wert ist "Litwareinc".
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Führen Sie diese Befehle zum Skype für Business Online herstellen. Eine Warnung zur Erhöhung der `WSMan NetworkDelayms` Wert wird erwartet, dass beim ersten verbinden und sollte ignoriert werden.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Führen Sie diese Befehle für die Verbindung zu Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. Führen Sie diese Befehle für die Verbindung für die Sicherheit &amp; Compliance Center.
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

Hier sind alle Befehle in einem Block, bei Verwendung von Azure Active Directory PowerShell Graph-Modul. Geben Sie den Namen des Domänenhosts, und klicken Sie dann führen Sie alle gleichzeitig aus.
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Auch sind hier alle Befehle in einem Block bei Verwendung das Microsoft Azure Active Directory-Modul für Windows PowerShell-Modul. Geben Sie den Namen des Domänenhosts, und klicken Sie dann führen Sie alle gleichzeitig aus.
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Wenn Sie Windows PowerShell-Fenster schließen möchten, führen Sie diesen Befehl, um die aktiven Sitzungen zu Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit zu entfernen &amp; Compliance Center:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Verbindung Schritte bei Verwendung der mehrstufigen Authentifizierung

Hier sind alle Befehle in einem Block zur Verbindung von Azure AD, SharePoint Online und Skype für geschäftlich Multi-Factor Authentication in einem einzelnen Fenster verwenden. Geben Sie den Benutzernamen des Benutzerprinzipalnamens (UPN) für eine globale Administratorkonto und Host-Namen Ihrer Domäne, und klicken Sie dann führen Sie alle gleichzeitig aus.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Hier werden auch alle Befehle, die bei Verwendung das Microsoft Azure Active Directory-Modul für Windows PowerShell-Modul.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Für Exchange Online und die Sicherheit &amp; Compliance Center, finden Sie unter Verbindung mehrstufige Authentifizierung mit den folgenden Themen:

- [Verbinden mit Exchange Online PowerShell per mehrstufiger Authentifizierung](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Verbinden Sie mit Office 365-Sicherheit und Compliance Center PowerShell mehrstufige Authentifizierung verwenden](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
Beachten Sie, dass in beiden Fällen von separaten Sitzungen des Exchange Online Remote PowerShell-Moduls herstellen müssen.


## <a name="see-also"></a>Siehe auch

- [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md)
- [Verwalten von SharePoint Online mit Office 365 PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
