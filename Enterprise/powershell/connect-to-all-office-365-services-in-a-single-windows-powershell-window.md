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
ms.openlocfilehash: 47fd2be814b446cf12b136e359cdadc9374a7ab6
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208806"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="a0b7a-103">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="a0b7a-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="a0b7a-104">Wenn Sie Office 365 mithilfe von PowerShell verwalten, können bis zu fünf verschiedene Windows PowerShell Sitzungen gleichzeitig geöffnet sein, die dem Microsoft 365 Admin Center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams und dem Security &amp; Compliance Center entsprechen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="a0b7a-105">Mit fünf verschiedenen Verbindungsmethoden in separaten Windows PowerShell Sitzungen könnte Ihr Desktop wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="a0b7a-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Fünf Windows PowerShell Konsolen, die gleichzeitig gestartet werden](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="a0b7a-107">Dies ist für die Verwaltung von Office 365 nicht optimal, da Sie keine Daten zwischen diesen fünf Fenstern für die dienstübergreifende Verwaltung austauschen können.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="a0b7a-108">In diesem Thema wird beschrieben, wie Sie eine einzelne Instanz von Windows PowerShell verwenden, aus der Sie Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams und dem Security &amp; Compliance Center verwalten können.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="a0b7a-109">Dieser Artikel enthält derzeit nur die Befehle zum Herstellen einer Verbindung mit der Office 365 Worldwide (+ gcc)-Cloud.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="a0b7a-110">Zusätzliche Hinweise bieten Links zu Artikeln mit Informationen zum Herstellen einer Verbindung mit anderen Office 365 Clouds.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="a0b7a-111">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="a0b7a-111">Before you begin</span></span>

<span data-ttu-id="a0b7a-112">Bevor Sie alle Office 365 aus einer einzigen Instanz von Windows PowerShell verwalten können, sollten Sie die folgenden Voraussetzungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="a0b7a-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="a0b7a-113">Das Office 365 Arbeits-oder Schulkonto, das Sie für diese Verfahren verwenden, muss Mitglied einer Office 365 Administratorrolle sein.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="a0b7a-114">Weitere Informationen finden Sie unter [Informationen zu Administratorrollen von Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="a0b7a-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="a0b7a-115">Dies ist eine Voraussetzung für Office 365 PowerShell, nicht notwendigerweise für alle anderen Office 365 Dienste.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="a0b7a-116">Sie können folgende 64-Bit-Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="a0b7a-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="a0b7a-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a0b7a-117">Windows 10</span></span>
    
  - <span data-ttu-id="a0b7a-118">Windows 8.1 oder Windows 8</span><span class="sxs-lookup"><span data-stu-id="a0b7a-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="a0b7a-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="a0b7a-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="a0b7a-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a0b7a-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="a0b7a-121">Windows Server 2012 R2 oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a0b7a-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="a0b7a-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="a0b7a-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="a0b7a-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="a0b7a-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="a0b7a-124">\*Sie müssen die Microsoft .NET Framework 4.5 installieren. *x* und dann entweder Windows Management Framework 3,0 oder Windows Management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="a0b7a-125">Weitere Informationen finden Sie unter [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="a0b7a-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="a0b7a-126">Sie müssen eine 64-Bit-Version von Windows aufgrund der Anforderungen für das Skype for Business Online Modul und eines der Office 365 Module verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="a0b7a-127">Sie müssen die Module installieren, die für Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online und Microsoft Teams erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="a0b7a-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="a0b7a-128">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="a0b7a-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="a0b7a-129">SharePoint Online Management-Shell</span><span class="sxs-lookup"><span data-stu-id="a0b7a-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="a0b7a-130">Skype for Business Online, Windows PowerShell Modul</span><span class="sxs-lookup"><span data-stu-id="a0b7a-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="a0b7a-131">Exchange Online PowerShell v2</span><span class="sxs-lookup"><span data-stu-id="a0b7a-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="a0b7a-132">Übersicht über Microsoft Teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0b7a-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="a0b7a-133">Windows PowerShell muss so konfiguriert werden, dass signierte Skripts für Skype for Business Online und das Security &amp; Compliance Center ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="a0b7a-134">Führen Sie dazu den folgenden Befehl in einer erhöhten Windows PowerShell-Sitzung aus (ein Windows PowerShell Fenster, das Sie durch Auswählen von **als Administrator ausführen**öffnen).</span><span class="sxs-lookup"><span data-stu-id="a0b7a-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="a0b7a-135">Verbindungs Schritte bei Verwendung eines Kennworts</span><span class="sxs-lookup"><span data-stu-id="a0b7a-135">Connection steps when using a password</span></span>

<span data-ttu-id="a0b7a-136">Hier finden Sie die Schritte zum Herstellen einer Verbindung mit allen Diensten in einem einzigen PowerShell-Fenster.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="a0b7a-137">Öffnen Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="a0b7a-138">Führen Sie diesen Befehl aus, und geben Sie die Anmeldeinformationen für Office 365 work oder School Account ein.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="a0b7a-139">Führen Sie diesen Befehl aus, um mithilfe des Azure Active Directory PowerShell for Graph-Moduls eine Verbindung mit Azure AD herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="a0b7a-140">Wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden, führen Sie diesen Befehl Alternativ aus.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="a0b7a-141">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="a0b7a-142">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="a0b7a-143">Führen Sie diese Befehle aus, um eine Verbindung mit SharePoint Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="a0b7a-144">Ersetzen Sie _ \< domainhost>_ durch den tatsächlichen Wert für Ihre Domäne.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="a0b7a-145">Für "litwareinc.onmicrosoft.com" ist beispielsweise der _ \< domainhost->_ Wert "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="a0b7a-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="a0b7a-146">Führen Sie diese Befehle aus, um eine Verbindung mit Skype for Business Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="a0b7a-147">Eine Warnung zur Erhöhung des `WSMan NetworkDelayms` Werts wird erwartet, wenn Sie das erste Mal eine Verbindung herstellen und ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="a0b7a-148">Führen Sie diesen Befehl aus, um eine Verbindung mit Exchange Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="a0b7a-149">Verwenden Sie den **-ExchangeEnvironmentName-** Parameter, um eine Verbindung mit Exchange Online für Office 365 andere Clouds als weltweit herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="a0b7a-150">Weitere Informationen finden Sie unter [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) .</span><span class="sxs-lookup"><span data-stu-id="a0b7a-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="a0b7a-151">Führen Sie diese Befehle aus, um eine Verbindung mit PowerShell-Teams herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="a0b7a-152">Informationen zum Herstellen einer Verbindung mit anderen Microsoft Teams-Clouds als weltweit finden Sie unter [Connect-verläuft](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="a0b7a-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="a0b7a-153">Führen Sie diese Befehle aus, um eine Verbindung mit dem Security &amp; Compliance Center herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="a0b7a-154">Informationen zum Herstellen einer Verbindung mit dem Security &amp; Compliance Center für Office 365 andere Clouds als weltweit finden Sie unter [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="a0b7a-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="a0b7a-155">Im folgenden finden Sie alle Befehle in einem einzigen Block, wenn Sie das Modul Azure Active Directory PowerShell for Graph verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="a0b7a-156">Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="a0b7a-157">Alternativ finden Sie hier alle Befehle in einem einzigen Block, wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="a0b7a-158">Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="a0b7a-159">Wenn Sie das Windows PowerShell Fenster schließen möchten, führen Sie diesen Befehl aus, um die aktiven Sitzungen in Skype for Business Online, SharePoint Online, im Security &amp; Compliance Center und in Microsoft Teams zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="a0b7a-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="a0b7a-160">Verbindungs Schritte bei Verwendung der mehrstufigen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="a0b7a-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="a0b7a-161">Im folgenden finden Sie alle Befehle in einem einzelnen Block zum Herstellen einer Verbindung mit Azure AD, SharePoint Online, Skype for Business, Exchange Online und Teams mithilfe der mehrstufigen Authentifizierung in einem einzigen Fenster mithilfe des Azure Active Directory PowerShell for Graph-Moduls.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="a0b7a-162">Geben Sie den Benutzerprinzipalnamen (User Principal Name, UPN) eines Benutzerkontos und den Namen Ihres Domänenhosts an, und führen Sie dann alle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="a0b7a-163">Alternativ finden Sie hier alle Befehle, wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0b7a-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="a0b7a-164">Informationen zum Security &amp; Compliance Center finden Sie unter [Verbinden mit Office 365 Security & Compliance Center PowerShell mithilfe der mehr](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) stufigen Authentifizierung zum Herstellen einer Verbindung mit mehrstufiger Authentifizierung:</span><span class="sxs-lookup"><span data-stu-id="a0b7a-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="a0b7a-165">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="a0b7a-165">See also</span></span>

- [<span data-ttu-id="a0b7a-166">Verbinden mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0b7a-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="a0b7a-167">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0b7a-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="a0b7a-168">Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0b7a-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="a0b7a-169">Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365</span><span class="sxs-lookup"><span data-stu-id="a0b7a-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
