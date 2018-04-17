---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/10/2018
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
ms.openlocfilehash: ffa603ec50c95f5800315eee07b4d01e058852f3
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="4410c-103">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="4410c-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="4410c-104">**Zusammenfassung:** Anstelle von Verwalten von verschiedenen Office 365-Diensten in separaten Fenstern von PowerShell-Konsole, können Sie eine Verbindung mit allen Office 365-Diensten und über einzelne Konsolenfenster verwalten.</span><span class="sxs-lookup"><span data-stu-id="4410c-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="4410c-p101">Wenn Sie zum Verwalten von Office 365 PowerShell verwenden, ist es möglich, bis zu fünf verschiedene Windows PowerShell-Sitzungen entsprechend der Office 365 Administrationscenter, SharePoint Online, Exchange Online, Skype für Business Online und die Sicherheit &amp;Compliance Center. Mit fünf unterschiedliche Verbindungsmethoden in separaten Windows PowerShell-Sitzungen konnte Ihren Desktop sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="4410c-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Fünf gleichzeitig ausgeführte Windows PowerShell-Konsolen](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="4410c-p102">Dies ist nicht für die Verwaltung von Office 365, da Sie Daten zwischen diesen fünf Windows for Cross-Service-Management austauschen können nicht optimal. In diesem Thema wird beschrieben, wie eine einzelne Instanz von Windows PowerShell verwenden, Sie können aus dem Office 365, Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit verwalten &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="4410c-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="4410c-110">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="4410c-110">Before you begin</span></span>
<span data-ttu-id="4410c-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="4410c-111"></span></span>

<span data-ttu-id="4410c-112">Bevor Sie alle von Office 365 von einer einzigen Instanz von Windows PowerShell verwalten können, sollten Sie die folgenden erforderlichen Komponenten:</span><span class="sxs-lookup"><span data-stu-id="4410c-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="4410c-p103">Office 365 arbeiten oder Schule Konto ein, das Sie für diese Verfahren Anforderungen verwenden, um ein Mitglied einer Office 365-Admin-Rolle sein. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367). Diese eine Voraussetzung für Office 365 PowerShell, was nicht notwendigerweise für alle anderen Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="4410c-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="4410c-116">Sie können folgende 64-Bit-Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="4410c-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="4410c-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="4410c-117">Windows 10</span></span>
    
  - <span data-ttu-id="4410c-118">Windows 8.1 oder Windows 8</span><span class="sxs-lookup"><span data-stu-id="4410c-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="4410c-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="4410c-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="4410c-120">Windows Server 2012 R2 oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4410c-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="4410c-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="4410c-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="4410c-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="4410c-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="4410c-p104">Sie müssen Microsoft .NET Framework 4.5 zu installieren. *X* , und klicken Sie dann entweder das Windows Management Framework 3.0 oder das Windows Management Framework 4.0. Weitere Informationen finden Sie unter [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) und [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="4410c-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="4410c-125">Sie müssen eine 64-Bit-Version von Windows für Business Online Modul und einen der Office 365-Module aufgrund der Anforderungen für die Skype verwenden.</span><span class="sxs-lookup"><span data-stu-id="4410c-125">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="4410c-126">Sie müssen die Module installieren, die für Office 365, SharePoint Online und Skype für Business Online erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="4410c-126">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="4410c-127">Microsoft Online Service Anmelde-Assistent für IT-Experten RTW</span><span class="sxs-lookup"><span data-stu-id="4410c-127">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="4410c-128">Windows Azure Active Directory-Modul für Windows PowerShell (64-Bit-Version) mit dem Befehl **Install-Modul MSOnline** an einer Eingabeaufforderung mit erhöhten Rechten PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4410c-128">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="4410c-129">SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="4410c-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="4410c-130">Skype für Unternehmen Online, Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="4410c-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="4410c-p105">Windows PowerShell zum Ausführen von signierten Skripts für Skype für Business Online, Exchange Online und die Sicherheit konfiguriert werden muss &amp; Compliance Center. Zu diesem Zweck führen Sie den folgenden Befehl in einer Windows PowerShell-Sitzung mit erhöhten Rechten (ein Windows PowerShell-Fenster Sie öffnen, indem Sie **als Administrator ausführen**auswählen).</span><span class="sxs-lookup"><span data-stu-id="4410c-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="4410c-133">Verbindung Schritte aus, wenn Sie ein Kennwort verwenden</span><span class="sxs-lookup"><span data-stu-id="4410c-133">Connection steps when using a password</span></span>
<span data-ttu-id="4410c-134"><a name="ConnStepsPassword"> </a></span><span class="sxs-lookup"><span data-stu-id="4410c-134"></span></span>

<span data-ttu-id="4410c-135">Hier sind die Schritte zum Herstellen einer Verbindung alle Dienste in einem einzelnen PowerShell-Fenster.</span><span class="sxs-lookup"><span data-stu-id="4410c-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="4410c-136">Öffnen Sie Windows PowerShell als Administrator (verwenden Sie **als Administrator ausführen**).</span><span class="sxs-lookup"><span data-stu-id="4410c-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="4410c-137">Führen Sie diesen Befehl, und geben Sie Ihre Office 365 Arbeit oder Schule Kontoanmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="4410c-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="4410c-138">Führen Sie diese Befehle für die Verbindung zu Office 365.</span><span class="sxs-lookup"><span data-stu-id="4410c-138">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="4410c-p106">Führen Sie diese Befehle für die Verbindung mit SharePoint Online. Ersetzen Sie _ \<Domainhost >_ durch den tatsächlichen Wert für Ihre Domäne. Beispiel für `litwareinc.onmicrosoft.com`, die _ \<Domainhost >_ Wert ist `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="4410c-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="4410c-p107">Führen Sie diese Befehle zum Skype für Business Online herstellen. Eine Warnung zur Erhöhung der `WSMan NetworkDelayms` Wert wird erwartet, dass beim ersten verbinden und sollte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="4410c-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="4410c-144">Führen Sie diese Befehle für die Verbindung zu Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="4410c-144">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. <span data-ttu-id="4410c-145">Führen Sie diese Befehle für die Verbindung für die Sicherheit &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="4410c-145">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
  Import-PSSession $SccSession
  ```

<span data-ttu-id="4410c-p108">Unten sehen Sie alle Befehle in einem einzigen Befehlsblock. Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="4410c-p108">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $SccSession
```
<span data-ttu-id="4410c-148">Wenn Sie Windows PowerShell-Fenster schließen möchten, führen Sie diesen Befehl, um die aktiven Sitzungen zu Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit zu entfernen &amp; Compliance Center:</span><span class="sxs-lookup"><span data-stu-id="4410c-148">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="4410c-149">Verbindung Schritte bei Verwendung der mehrstufigen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="4410c-149">Connection steps when using multi-factor authentication</span></span>
<span data-ttu-id="4410c-150"><a name="ConnStepsMFA"> </a></span><span class="sxs-lookup"><span data-stu-id="4410c-150"></span></span>

<span data-ttu-id="4410c-p109">Hier sind alle Befehle in einem Block zur Verbindung von Azure AD, SharePoint Online und Skype für geschäftlich Multi-Factor Authentication in einem einzelnen Fenster verwenden. Geben Sie den Benutzernamen des Benutzerprinzipalnamens (UPN) für eine globale Administratorkonto und Host-Namen Ihrer Domäne, und klicken Sie dann führen Sie alle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="4410c-p109">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
#If you are running Office 365 commands that contain "AzureAd" in their name, use this command:
Connect-AzureAD
#If you are running Office 365 commands that contain "Msol" in their name, comment the preceding command and un-comment the following command:
#Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="4410c-153">Für Exchange Online und die Sicherheit &amp; Compliance Center, finden Sie unter Verbindung mehrstufige Authentifizierung mit den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="4410c-153">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- <span data-ttu-id="4410c-154">[Connect to Exchange Online PowerShell mehrstufige Authentifizierung verwenden](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="4410c-154">[Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell).</span></span>
- [<span data-ttu-id="4410c-155">Verbinden Sie mit Office 365-Sicherheit und Compliance Center PowerShell mehrstufige Authentifizierung verwenden</span><span class="sxs-lookup"><span data-stu-id="4410c-155">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="4410c-156">Beachten Sie, dass in beiden Fällen von separaten Sitzungen des Exchange Online Remote PowerShell-Moduls herstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="4410c-156">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="4410c-157">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="4410c-157">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="4410c-158">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4410c-158">See also</span></span>

- [<span data-ttu-id="4410c-159">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4410c-159">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="4410c-160">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4410c-160">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="4410c-161">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4410c-161">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="4410c-162">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4410c-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="4410c-163">Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365</span><span class="sxs-lookup"><span data-stu-id="4410c-163">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
