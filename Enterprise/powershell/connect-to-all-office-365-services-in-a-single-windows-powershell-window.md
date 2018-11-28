---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/27/2018
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
ms.openlocfilehash: 5635cf8b03490c2b2f811f22c231c271d5204552
ms.sourcegitcommit: 65de707bd1c389eea48767a68c31032dd5198359
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "26706689"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="2379c-103">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="2379c-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="2379c-104">**Zusammenfassung:** Anstelle von Verwalten von verschiedenen Office 365-Diensten in separaten Fenstern von PowerShell-Konsole, können Sie eine Verbindung mit allen Office 365-Diensten und über einzelne Konsolenfenster verwalten.</span><span class="sxs-lookup"><span data-stu-id="2379c-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="2379c-p101">Wenn Sie zum Verwalten von Office 365 PowerShell verwenden, ist es möglich, bis zu fünf verschiedene Windows PowerShell-Sitzungen entsprechend der Office 365 Administrationscenter, SharePoint Online, Exchange Online, Skype für Business Online und die Sicherheit &amp;Compliance Center. Mit fünf unterschiedliche Verbindungsmethoden in separaten Windows PowerShell-Sitzungen konnte Ihren Desktop sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="2379c-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Fünf gleichzeitig ausgeführte Windows PowerShell-Konsolen](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="2379c-p102">Dies ist nicht für die Verwaltung von Office 365, da Sie Daten zwischen diesen fünf Windows for Cross-Service-Management austauschen können nicht optimal. In diesem Thema wird beschrieben, wie eine einzelne Instanz von Windows PowerShell verwenden, Sie können aus dem Office 365, Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit verwalten &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="2379c-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="2379c-p103">Dieser Artikel enthält derzeit nur die Befehle, um die Verbindung mit der Office 365 weltweit (+ GCC) Cloud. Zusätzliche Hinweise enthalten Links zu Artikeln mit Informationen zum Herstellen einer Verbindung mit anderen Office 365 Wolken.</span><span class="sxs-lookup"><span data-stu-id="2379c-p103">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud. Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="2379c-112">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="2379c-112">Before you begin</span></span>

<span data-ttu-id="2379c-113">Bevor Sie alle von Office 365 von einer einzigen Instanz von Windows PowerShell verwalten können, sollten Sie die folgenden erforderlichen Komponenten:</span><span class="sxs-lookup"><span data-stu-id="2379c-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="2379c-p104">Office 365 arbeiten oder Schule Konto ein, das Sie für diese Verfahren Anforderungen verwenden, um ein Mitglied einer Office 365-Admin-Rolle sein. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367). Diese eine Voraussetzung für Office 365 PowerShell, was nicht notwendigerweise für alle anderen Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="2379c-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="2379c-117">Sie können folgende 64-Bit-Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="2379c-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="2379c-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="2379c-118">Windows 10</span></span>
    
  - <span data-ttu-id="2379c-119">Windows 8.1 oder Windows 8</span><span class="sxs-lookup"><span data-stu-id="2379c-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="2379c-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="2379c-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="2379c-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="2379c-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="2379c-122">Windows Server 2012 R2 oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2379c-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="2379c-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="2379c-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="2379c-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="2379c-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="2379c-p105">\*Sie müssen Microsoft .NET Framework 4.5 zu installieren. *X* , und klicken Sie dann entweder das Windows Management Framework 3.0 oder das Windows Management Framework 4.0. Weitere Informationen finden Sie unter [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) und [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="2379c-p105">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="2379c-127">Sie müssen eine 64-Bit-Version von Windows für Business Online Modul und einen der Office 365-Module aufgrund der Anforderungen für die Skype verwenden.</span><span class="sxs-lookup"><span data-stu-id="2379c-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="2379c-128">Sie müssen die Module installieren, die für Azure AD erforderlich sind SharePoint Online und Skype für Business Online:</span><span class="sxs-lookup"><span data-stu-id="2379c-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="2379c-129">Azure Active Directory-V2</span><span class="sxs-lookup"><span data-stu-id="2379c-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="2379c-130">SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="2379c-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="2379c-131">Skype für Unternehmen Online, Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="2379c-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="2379c-p106">Windows PowerShell zum Ausführen von signierten Skripts für Skype für Business Online, Exchange Online und die Sicherheit konfiguriert werden muss &amp; Compliance Center. Zu diesem Zweck führen Sie den folgenden Befehl in einer Windows PowerShell-Sitzung mit erhöhten Rechten (ein Windows PowerShell-Fenster Sie öffnen, indem Sie **als Administrator ausführen**auswählen).</span><span class="sxs-lookup"><span data-stu-id="2379c-p106">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="2379c-134">Verbindung Schritte aus, wenn Sie ein Kennwort verwenden</span><span class="sxs-lookup"><span data-stu-id="2379c-134">Connection steps when using a password</span></span>

<span data-ttu-id="2379c-135">Hier sind die Schritte zum Herstellen einer Verbindung alle Dienste in einem einzelnen PowerShell-Fenster.</span><span class="sxs-lookup"><span data-stu-id="2379c-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="2379c-136">Öffnen Sie Windows PowerShell als Administrator (verwenden Sie **als Administrator ausführen**).</span><span class="sxs-lookup"><span data-stu-id="2379c-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="2379c-137">Führen Sie diesen Befehl, und geben Sie Ihre Office 365 Arbeit oder Schule Kontoanmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="2379c-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="2379c-138">Führen Sie diesen Befehl für die Verbindung zu Azure Active Directory (AD) mithilfe von Azure Active Directory PowerShell Graph-Modul.</span><span class="sxs-lookup"><span data-stu-id="2379c-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="2379c-139">Auch wenn Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell-Modul verwenden, führen Sie diesen Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="2379c-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="2379c-p107">Führen Sie diese Befehle für die Verbindung mit SharePoint Online. Ersetzen Sie _ \<Domainhost >_ durch den tatsächlichen Wert für Ihre Domäne. Zum Beispiel für "litwareinc.onmicrosoft.com" die _ \<Domainhost >_ Wert ist "Litwareinc".</span><span class="sxs-lookup"><span data-stu-id="2379c-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="2379c-p108">Führen Sie diese Befehle zum Skype für Business Online herstellen. Eine Warnung zur Erhöhung der `WSMan NetworkDelayms` Wert wird erwartet, dass beim ersten verbinden und sollte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="2379c-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="2379c-145">Führen Sie diese Befehle für die Verbindung zu Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="2379c-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

>[!Note]
><span data-ttu-id="2379c-146">Für eine Verbindung zu Exchange Online für Office 365 Wolken als Worldwide, finden Sie unter [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="2379c-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="2379c-147">Führen Sie diese Befehle für die Verbindung für die Sicherheit &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="2379c-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="2379c-148">Verbindung mit der Sicherheit &amp; Compliance Center für Office 365 Wolken als Worldwide, finden Sie unter [Connect to Office 365-Sicherheit und Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="2379c-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="2379c-p109">Hier sind alle Befehle in einem Block, bei Verwendung von Azure Active Directory PowerShell Graph-Modul. Geben Sie den Namen des Domänenhosts, und klicken Sie dann führen Sie alle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="2379c-p109">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="2379c-p110">Auch sind hier alle Befehle in einem Block bei Verwendung das Microsoft Azure Active Directory-Modul für Windows PowerShell-Modul. Geben Sie den Namen des Domänenhosts, und klicken Sie dann führen Sie alle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="2379c-p110">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="2379c-153">Wenn Sie Windows PowerShell-Fenster schließen möchten, führen Sie diesen Befehl, um die aktiven Sitzungen zu Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit zu entfernen &amp; Compliance Center:</span><span class="sxs-lookup"><span data-stu-id="2379c-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="2379c-154">Verbindung Schritte bei Verwendung der mehrstufigen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="2379c-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="2379c-p111">Hier sind alle Befehle in einem Block zur Verbindung von Azure AD, SharePoint Online und Skype für geschäftlich Multi-Factor Authentication in einem einzelnen Fenster verwenden. Geben Sie den Benutzernamen des Benutzerprinzipalnamens (UPN) für eine globale Administratorkonto und Host-Namen Ihrer Domäne, und klicken Sie dann führen Sie alle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="2379c-p111">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="2379c-157">Hier werden auch alle Befehle, die bei Verwendung das Microsoft Azure Active Directory-Modul für Windows PowerShell-Modul.</span><span class="sxs-lookup"><span data-stu-id="2379c-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="2379c-158">Für Exchange Online und die Sicherheit &amp; Compliance Center, finden Sie unter Verbindung mehrstufige Authentifizierung mit den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="2379c-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="2379c-159">Verbinden mit Exchange Online PowerShell per mehrstufiger Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="2379c-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="2379c-160">Verbinden Sie mit Office 365-Sicherheit und Compliance Center PowerShell mehrstufige Authentifizierung verwenden</span><span class="sxs-lookup"><span data-stu-id="2379c-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="2379c-161">Beachten Sie, dass in beiden Fällen von separaten Sitzungen des Exchange Online Remote PowerShell-Moduls herstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="2379c-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="2379c-162">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2379c-162">See also</span></span>

- [<span data-ttu-id="2379c-163">Verbinden mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2379c-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="2379c-164">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2379c-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="2379c-165">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2379c-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="2379c-166">Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365</span><span class="sxs-lookup"><span data-stu-id="2379c-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
