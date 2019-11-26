---
title: Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
audience: ITPro
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
description: 'Zusammenfassung: Verbinden Sie Windows PowerShell mit allen Office 365 Diensten in einem einzelnen Windows PowerShell Fenster.'
ms.openlocfilehash: c8390b3d704fa9df64f147a942891308b1ed825f
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257424"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="a97e8-103">Verbinden mit allen Office 365-Diensten in einem einzigen Windows PowerShell-Fenster</span><span class="sxs-lookup"><span data-stu-id="a97e8-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="a97e8-104">**Zusammenfassung:** Anstatt verschiedene Office 365 Dienste in separaten PowerShell-Konsolenfenstern zu verwalten, können Sie eine Verbindung zu allen Office 365 Diensten herstellen und diese über ein einzelnes Konsolenfenster verwalten.</span><span class="sxs-lookup"><span data-stu-id="a97e8-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="a97e8-105">Wenn Sie Office 365 mithilfe von PowerShell verwalten, können bis zu fünf verschiedene Windows PowerShell Sitzungen gleichzeitig geöffnet sein, die dem Microsoft 365 Admin Center, SharePoint Online, Exchange Online, Skype for Business Online und dem Security &amp; Compliance Center entsprechen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="a97e8-106">Mit fünf verschiedenen Verbindungsmethoden in separaten Windows PowerShell Sitzungen könnte Ihr Desktop wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="a97e8-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Fünf Windows PowerShell Konsolen, die gleichzeitig gestartet werden](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="a97e8-108">Dies ist für die Verwaltung von Office 365 nicht optimal, da Sie keine Daten zwischen diesen fünf Fenstern für die dienstübergreifende Verwaltung austauschen können.</span><span class="sxs-lookup"><span data-stu-id="a97e8-108">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="a97e8-109">In diesem Thema wird beschrieben, wie Sie eine einzelne Instanz von Windows PowerShell verwenden, aus der Sie Office 365, Skype for Business Online, Exchange Online, SharePoint Online und dem &amp; Security Compliance Center verwalten können.</span><span class="sxs-lookup"><span data-stu-id="a97e8-109">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="a97e8-110">Dieser Artikel enthält derzeit nur die Befehle zum Herstellen einer Verbindung mit der Office 365 Worldwide (+ gcc)-Cloud.</span><span class="sxs-lookup"><span data-stu-id="a97e8-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="a97e8-111">Zusätzliche Hinweise bieten Links zu Artikeln mit Informationen zum Herstellen einer Verbindung mit anderen Office 365 Clouds.</span><span class="sxs-lookup"><span data-stu-id="a97e8-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="a97e8-112">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="a97e8-112">Before you begin</span></span>

<span data-ttu-id="a97e8-113">Bevor Sie alle Office 365 aus einer einzigen Instanz von Windows PowerShell verwalten können, sollten Sie die folgenden Voraussetzungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="a97e8-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="a97e8-114">Das Office 365 Arbeits-oder Schulkonto, das Sie für diese Verfahren verwenden, muss Mitglied einer Office 365 Administratorrolle sein.</span><span class="sxs-lookup"><span data-stu-id="a97e8-114">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="a97e8-115">Weitere Informationen finden Sie unter [Informationen zu Administratorrollen von Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="a97e8-115">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="a97e8-116">Dies ist eine Voraussetzung für Office 365 PowerShell, nicht notwendigerweise für alle anderen Office 365 Dienste.</span><span class="sxs-lookup"><span data-stu-id="a97e8-116">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="a97e8-117">Sie können folgende 64-Bit-Versionen von Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="a97e8-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="a97e8-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a97e8-118">Windows 10</span></span>
    
  - <span data-ttu-id="a97e8-119">Windows 8.1 oder Windows 8</span><span class="sxs-lookup"><span data-stu-id="a97e8-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="a97e8-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="a97e8-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="a97e8-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a97e8-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="a97e8-122">Windows Server 2012 R2 oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a97e8-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="a97e8-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="a97e8-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="a97e8-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="a97e8-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="a97e8-125">\*Sie müssen die Microsoft .NET Framework 4.5 installieren. *x* und dann entweder Windows Management Framework 3,0 oder Windows Management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="a97e8-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="a97e8-126">Weitere Informationen finden Sie unter [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="a97e8-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="a97e8-127">Sie müssen eine 64-Bit-Version von Windows aufgrund der Anforderungen für das Skype for Business Online Modul und eines der Office 365 Module verwenden.</span><span class="sxs-lookup"><span data-stu-id="a97e8-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="a97e8-128">Sie müssen die Module installieren, die für Azure AD, SharePoint Online und Skype for Business Online erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="a97e8-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="a97e8-129">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="a97e8-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="a97e8-130">SharePoint Online Management-Shell</span><span class="sxs-lookup"><span data-stu-id="a97e8-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="a97e8-131">Skype for Business Online, Windows PowerShell Modul</span><span class="sxs-lookup"><span data-stu-id="a97e8-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="a97e8-132">Windows PowerShell muss so konfiguriert werden, dass signierte Skripts für Skype for Business Online, Exchange Online und das Security &amp; Compliance Center ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a97e8-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="a97e8-133">Führen Sie dazu den folgenden Befehl in einer erhöhten Windows PowerShell-Sitzung aus (ein Windows PowerShell Fenster, das Sie durch Auswählen von **als Administrator ausführen**öffnen).</span><span class="sxs-lookup"><span data-stu-id="a97e8-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="a97e8-134">Verbindungs Schritte bei Verwendung eines Kennworts</span><span class="sxs-lookup"><span data-stu-id="a97e8-134">Connection steps when using a password</span></span>

<span data-ttu-id="a97e8-135">Hier finden Sie die Schritte zum Herstellen einer Verbindung mit allen Diensten in einem einzigen PowerShell-Fenster.</span><span class="sxs-lookup"><span data-stu-id="a97e8-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="a97e8-136">Öffnen Sie Windows PowerShell als Administrator ( **als Administrator ausführen**).</span><span class="sxs-lookup"><span data-stu-id="a97e8-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="a97e8-137">Führen Sie diesen Befehl aus, und geben Sie die Anmeldeinformationen für das Office 365 work-oder School-Konto ein.</span><span class="sxs-lookup"><span data-stu-id="a97e8-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="a97e8-138">Führen Sie diesen Befehl aus, um eine Verbindung mit Azure Active Directory (AD) mithilfe des Azure Active Directory PowerShell for Graph-Moduls herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="a97e8-139">Wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden, führen Sie diesen Befehl Alternativ aus.</span><span class="sxs-lookup"><span data-stu-id="a97e8-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="a97e8-140">PowerShell Core unterstützt das Microsoft Azure Active Directory Modul für Windows PowerShell Modul und Cmdlets mit **MSOL** nicht in Ihrem Namen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="a97e8-141">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie diese von Windows PowerShell aus ausführen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="a97e8-142">Führen Sie diese Befehle aus, um eine Verbindung mit SharePoint Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-142">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="a97e8-143">Ersetzen _ \<Sie domainhost>_ durch den tatsächlichen Wert für Ihre Domäne.</span><span class="sxs-lookup"><span data-stu-id="a97e8-143">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="a97e8-144">Für "litwareinc.onmicrosoft.com" ist beispielsweise der _ \<domainhost->_ Wert "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="a97e8-144">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="a97e8-145">Führen Sie diese Befehle aus, um eine Verbindung mit Skype for Business Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-145">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="a97e8-146">Eine Warnung zur Erhöhung des `WSMan NetworkDelayms` Werts wird erwartet, wenn Sie das erste Mal eine Verbindung herstellen und ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="a97e8-146">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="a97e8-147">Führen Sie diese Befehle aus, um eine Verbindung mit Exchange Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```powershell
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="a97e8-148">Informationen zum Herstellen einer Verbindung mit Exchange Online für Office 365 andere Clouds als weltweit finden Sie unter [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="a97e8-148">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="a97e8-149">Führen Sie diese Befehle aus, um eine &amp; Verbindung mit dem Security Compliance Center herzustellen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-149">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="a97e8-150">Informationen zum Herstellen einer Verbindung &amp; mit dem Security Compliance Center für Office 365 andere Clouds als weltweit finden Sie unter [Connect to Office 365 Security #a0 Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="a97e8-150">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="a97e8-151">Im folgenden finden Sie alle Befehle in einem einzigen Block, wenn Sie das Modul Azure Active Directory PowerShell for Graph verwenden.</span><span class="sxs-lookup"><span data-stu-id="a97e8-151">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="a97e8-152">Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="a97e8-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
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

<span data-ttu-id="a97e8-153">Alternativ finden Sie hier alle Befehle in einem einzigen Block, wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden.</span><span class="sxs-lookup"><span data-stu-id="a97e8-153">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="a97e8-154">Geben Sie den Namen Ihres Domänenhosts an, und führen Sie alle Befehle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="a97e8-154">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
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

<span data-ttu-id="a97e8-155">Wenn Sie das Windows PowerShell Fenster schließen möchten, führen Sie diesen Befehl aus, um die aktiven Sitzungen in Skype for Business Online, Exchange Online, SharePoint Online und im Security &amp; Compliance Center zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="a97e8-155">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="a97e8-156">Verbindungs Schritte bei Verwendung der mehrstufigen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="a97e8-156">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="a97e8-157">Hier sind alle Befehle in einem einzelnen Block, mit denen Sie eine Verbindung mit Azure AD, SharePoint Online und Skype for Buiness mithilfe der mehrstufigen Authentifizierung in einem einzigen Fenster mithilfe des Azure Active Directory PowerShell for Graph-Moduls herstellen können.</span><span class="sxs-lookup"><span data-stu-id="a97e8-157">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="a97e8-158">Geben Sie den Benutzerprinzipalnamen (User Principal Name, UPN) eines Benutzerkontos und den Namen Ihres Domänenhosts an, und führen Sie dann alle gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="a97e8-158">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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
```

<span data-ttu-id="a97e8-159">Alternativ finden Sie hier alle Befehle, wenn Sie das Microsoft Azure Active Directory Modul für Windows PowerShell Modul verwenden.</span><span class="sxs-lookup"><span data-stu-id="a97e8-159">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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
```

<span data-ttu-id="a97e8-160">Für Exchange Online und das Security &amp; Compliance Center finden Sie unter den folgenden Themen eine Verbindung mit mehrstufiger Authentifizierung:</span><span class="sxs-lookup"><span data-stu-id="a97e8-160">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="a97e8-161">Verbinden mit Exchange Online PowerShell per mehrstufiger Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="a97e8-161">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="a97e8-162">Herstellen einer Verbindung mit Office 365 Security #a0 Compliance Center PowerShell mithilfe der mehrstufigen Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="a97e8-162">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="a97e8-163">Beachten Sie, dass Sie in beiden Fällen eine Verbindung mit separaten Sitzungen des Exchange Online Remote-PowerShell-Moduls herstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="a97e8-163">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="a97e8-164">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a97e8-164">See also</span></span>

- [<span data-ttu-id="a97e8-165">Verbinden mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a97e8-165">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="a97e8-166">Verwalten von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a97e8-166">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="a97e8-167">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a97e8-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="a97e8-168">Verwenden der Windows PowerShell zum Erstellen von Berichten in Office 365</span><span class="sxs-lookup"><span data-stu-id="a97e8-168">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
