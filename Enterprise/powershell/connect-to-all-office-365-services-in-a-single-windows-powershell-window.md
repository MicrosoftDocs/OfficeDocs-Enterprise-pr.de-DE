---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="e191c-103">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="e191c-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="e191c-104">**Zusammenfassung:** Anstelle von Verwalten von verschiedenen Office 365-Diensten in separaten Fenstern von PowerShell-Konsole, können Sie eine Verbindung mit allen Office 365-Diensten und über einzelne Konsolenfenster verwalten.</span><span class="sxs-lookup"><span data-stu-id="e191c-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="e191c-p101">Wenn Sie zum Verwalten von Office 365 PowerShell verwenden, ist es möglich, bis zu fünf verschiedene Windows PowerShell-Sitzungen entsprechend der Office 365 Administrationscenter, SharePoint Online, Exchange Online, Skype für Business Online und die Sicherheit &amp;Compliance Center. Mit fünf unterschiedliche Verbindungsmethoden in separaten Windows PowerShell-Sitzungen konnte Ihren Desktop sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="e191c-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Fünf gleichzeitig ausgeführte Windows PowerShell-Konsolen](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="e191c-p102">Dies ist nicht für die Verwaltung von Office 365, da Sie Daten zwischen diesen fünf Windows for Cross-Service-Management austauschen können nicht optimal. In diesem Thema wird beschrieben, wie eine einzelne Instanz von Windows PowerShell verwenden, Sie können aus dem Office 365, Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit verwalten &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="e191c-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="e191c-110">In diesem Artikel wird gerade aktualisiert, um das Azure Active Directory V2 PowerShell-Modul verwenden und für die mehrstufige Authentifizierung (mehrstufiger Authentifizierung das).</span><span class="sxs-lookup"><span data-stu-id="e191c-110">This article is in the process of being updated to use the Azure Active Directory V2 PowerShell module and for multifactor authentication (MFA).</span></span>
>
  
## <a name="before-you-begin"></a><span data-ttu-id="e191c-111">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="e191c-111">Before you begin</span></span>
<span data-ttu-id="e191c-112"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="e191c-112"></span></span>

<span data-ttu-id="e191c-113">Bevor Sie alle von Office 365 von einer einzigen Instanz von Windows PowerShell verwalten können, sollten Sie die folgenden erforderlichen Komponenten:</span><span class="sxs-lookup"><span data-stu-id="e191c-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="e191c-p103">Office 365 arbeiten oder Schule Konto ein, das Sie für diese Verfahren Anforderungen verwenden, um ein Mitglied einer Office 365-Admin-Rolle sein. Weitere Informationen finden Sie unter [Informationen zu Office 365-Administratorrollen](https://go.microsoft.com/fwlink/p/?LinkId=532367). Diese eine Voraussetzung für Office 365 PowerShell, was nicht notwendigerweise für alle anderen Office 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="e191c-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="e191c-117">Sie können folgende 64-Bit-Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="e191c-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="e191c-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="e191c-118">Windows 10</span></span>
    
  - <span data-ttu-id="e191c-119">Windows 8.1 oder Windows 8</span><span class="sxs-lookup"><span data-stu-id="e191c-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="e191c-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="e191c-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="e191c-121">Windows Server 2012 R2 oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e191c-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="e191c-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="e191c-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="e191c-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="e191c-123">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="e191c-p104">Sie müssen Microsoft .NET Framework 4.5 zu installieren. *X* , und klicken Sie dann entweder das Windows Management Framework 3.0 oder das Windows Management Framework 4.0. Weitere Informationen finden Sie unter [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) und [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="e191c-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="e191c-126">Sie müssen eine 64-Bit-Version von Windows für Business Online Modul und einen der Office 365-Module aufgrund der Anforderungen für die Skype verwenden.</span><span class="sxs-lookup"><span data-stu-id="e191c-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="e191c-127">Sie müssen die Module installieren, die für Office 365, SharePoint Online und Skype für Business Online erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="e191c-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="e191c-128">Microsoft Online Service Anmelde-Assistent für IT-Experten RTW</span><span class="sxs-lookup"><span data-stu-id="e191c-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="e191c-129">Windows Azure Active Directory-Modul für Windows PowerShell (64-Bit-Version) mit dem Befehl **Install-Modul MSOnline** an einer Eingabeaufforderung mit erhöhten Rechten PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e191c-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="e191c-130">SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="e191c-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="e191c-131">Skype für Unternehmen Online, Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="e191c-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="e191c-p105">Windows PowerShell zum Ausführen von signierten Skripts für Skype für Business Online, Exchange Online und die Sicherheit konfiguriert werden muss &amp; Compliance Center. Zu diesem Zweck führen Sie den folgenden Befehl in einer Windows PowerShell-Sitzung mit erhöhten Rechten (ein Windows PowerShell-Fenster Sie öffnen, indem Sie **als Administrator ausführen**auswählen).</span><span class="sxs-lookup"><span data-stu-id="e191c-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a><span data-ttu-id="e191c-134">Verbindung Schritte</span><span class="sxs-lookup"><span data-stu-id="e191c-134">Connection steps</span></span>
<span data-ttu-id="e191c-135"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="e191c-135"></span></span>

<span data-ttu-id="e191c-136">Hier sind die Schritte zum Herstellen einer Verbindung alle Dienste in einem einzelnen PowerShell-Fenster.</span><span class="sxs-lookup"><span data-stu-id="e191c-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="e191c-137">Öffnen Sie Windows PowerShell als Administrator (verwenden Sie **als Administrator ausführen**).</span><span class="sxs-lookup"><span data-stu-id="e191c-137">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="e191c-138">Führen Sie diesen Befehl, und geben Sie Ihre Office 365 Arbeit oder Schule Kontoanmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="e191c-138">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="e191c-139">Führen Sie diese Befehle für die Verbindung zu Office 365.</span><span class="sxs-lookup"><span data-stu-id="e191c-139">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="e191c-p106">Führen Sie diese Befehle für die Verbindung mit SharePoint Online. Ersetzen Sie _ \<Domainhost >_ durch den tatsächlichen Wert für Ihre Domäne. Beispiel für `litwareinc.onmicrosoft.com`, die _ \<Domainhost >_ Wert ist `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="e191c-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="e191c-p107">Führen Sie diese Befehle zum Skype für Business Online herstellen. Eine Warnung zur Erhöhung der `WSMan NetworkDelayms` Wert wird erwartet, dass beim ersten verbinden und sollte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="e191c-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="e191c-145">Führen Sie diese Befehle für die Verbindung zu Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="e191c-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="e191c-146">Führen Sie diese Befehle für die Verbindung für die Sicherheit &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="e191c-146">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="e191c-p108">Nach Textpräfix "cc" *Alle* Sicherheit hinzugefügt &amp; Compliance Center-Cmdlet-Namen, damit Sie Cmdlets ausführen können in Exchange Online und die Sicherheit vorhanden sind, &amp; Compliance Center in der gleichen Windows PowerShell-Sitzung. Beispielsweise wird **Get-RoleGroup** **Get-CcRoleGroup** in das Wertpapier &amp; Compliance Center.</span><span class="sxs-lookup"><span data-stu-id="e191c-p108">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="e191c-p109">Unten sehen Sie alle Befehle in einem einzigen Befehlsblock. Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="e191c-p109">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```
<span data-ttu-id="e191c-151">Wenn Sie Windows PowerShell-Fenster schließen möchten, führen Sie diesen Befehl, um die aktiven Sitzungen zu Skype für Business Online, Exchange Online, SharePoint Online und die Sicherheit zu entfernen &amp; Compliance Center:</span><span class="sxs-lookup"><span data-stu-id="e191c-151">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a><span data-ttu-id="e191c-152">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="e191c-152">New to Office 365?</span></span>
<span data-ttu-id="e191c-153"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="e191c-153"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="e191c-154">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e191c-154">See also</span></span>

- [<span data-ttu-id="e191c-155">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e191c-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="e191c-156">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e191c-156">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="e191c-157">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e191c-157">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="e191c-158">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e191c-158">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="e191c-159">Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365</span><span class="sxs-lookup"><span data-stu-id="e191c-159">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
